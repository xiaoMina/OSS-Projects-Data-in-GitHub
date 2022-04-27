#  Health Evaluation and Assessment Method for Open Source Software Projects in GitHub
create GHTorrent MySql database
First, you need load GHTorrent to your local computer. Step is as follows:
	
	(a)download ghtorrent dataset:
		site: https://www.ghtorrent.org/downloads.html
	
	(b)decompress the dataset：
		tar zxvf mysql-2018-06-01.tar.gz
	
	(c)connect to the mysql database, create a new database and user (you can replace 'ghtorrentuser','ghtorrentpassword' with others):
		mysql -u root -p
		create user 'ghtorrentuser'@'localhost' identified by 'ghtorrentpassword';
		create user 'ghtorrentuser'@'*' identified by 'ghtorrentpassword';
		create database ghtorrent_restore;
		grant all privileges on ghtorrent_restore.* to 'ghtorrentuser'@'localhost';
		grant all privileges on ghtorrent_restore.* to 'ghtorrentuser'@'*';
		grant file on *.* to 'ghtorrentuser'@'localhost';
	
	(d)import the decompressed data into the database ghtorrent_restore:
		cd mysql-2018-06-01
		./ght-restore-mysql -u ghtorrentuser -d ghtorrent_restore -p ghtorrentpassword . 
	
	(e)if you want to visit database remotely, then:
		CREATE USER 'ystian'@'%' IDENTIFIED BY '123456';
		GRANT select ON ghtorrent_restore.* TO 'ystian'@'%'


