---
title: "Installing IRCU &amp; GNUWorld on any linux platform"
date: 2012-03-05
forum: Installation &amp; Upgrades
---

### Post by bG1988 on 2012-03-05
sudo apt-get install - the command for ubuntu 
yum -y install - the command for centos/debian 

First, we type: 

linux:/root# sudo apt-get install byacc 
linux:/root# sudo apt-get install flex 
linux:/root# sudo apt-get install screen 
linux:/root# adduser 
linux:/root# gnuworld  

After that you press the "enter" button twice, 
and choose a password. 

Now download and configure ircu 

Download ircd 

linux:/root# su - gnuworld 
linux:/gnuworld# wget [http://gnuworld.ircu.org/ircu2.10.12.14.tar.gz](http://gnuworld.ircu.org/ircu2.10.12.14.tar.gz) 
linux:/gnuworld# tar -zxvf ircu2.10.12.14.tar.gz 
linux:/gnuworld# cd ircu2.10.12.14 
linux:/gnuworld/ircu2.10.12.14# ./configure 
linux:/gnuworld/ircu2.10.12.14# make 
linux:/gnuworld/ircu2.10.12.14# make install 
linux:/gnuworld/ircu2.10.12.14# cd .. 
linux:/gnuworld/lib# cd lib 
linux:/gnuworld/lib# wget [http://gnuworld.ircu.org/ircd.motd](http://gnuworld.ircu.org/ircd.motd) 
linux:/gnuworld/lib# wget [http://gnuworld.ircu.org/ircd.conf](http://gnuworld.ircu.org/ircd.conf) 
linux:/gnuworld/lib# cd .. 
linux:/gnuworld# cd bin 
linux:/gnuworld/bin# ./ircd 
linux:/gnuworld# exit  

We go back to our root user 

Check if the TCL installed 


linux:/root# /usr/bin/updatedb 
linux:/root# locate tclConfig.sh  

If it has been installed, the response should be: 

/usr/lib/tclConfig.sh 

linux:/root# grep TCL_VERSION /usr/lib/tclConfig.sh  

The reply has to show the 8.0 version, or a higher one. 

If you don't have the TCL installed: 

linux:/root# wget [http://gnuworld.ircu.org/tcl8.4.13-src.tar.gz](http://gnuworld.ircu.org/tcl8.4.13-src.tar.gz) 
linux:/root# tar -xzf tcl8.4.13-src.tar.gz 
linux:/root# cd tcl8.4.13-src/unix/ 
linux:/root/tcl8.4.13-src/unix/# ./configure 
linux:/root/tcl8.4.13-src/unix/# make 
linux:/root/tcl8.4.13-src/unix/# make install 
linux:/root/tcl8.4.13-src/unix/# cd .. 
linux:/root/tcl8.4.13-src/# cd .. 
linux:/root# ln -s /usr/local/lib/tclConfig.sh /usr/lib  

How we install POSTGRESQL :  

linux:/root# wget [http://gnuworld.ircu.org/postgresql-8.1.4.tar.gz](http://gnuworld.ircu.org/postgresql-8.1.4.tar.gz) 
linux:/root# tar -xzf postgresql-8.1.4.tar.gz 
linux:/root# sudo apt-get install readline 
linux:/root# sudo apt-get install zlib 
linux:/root# cd postgresql-8.1.4 
linux:/root/postgresql-8.1.4# ./configure --with-CXX --enable-multibyte --with-tclconfig=/usr/lib --without-tk 
linux:/root/postgresql-8.1.4# ln -s /usr/bin/make /usr/bin/gmake 
linux:/root/postgresql-8.1.4# sudo apt-get install gmake 
linux:/root/postgresql-8.1.4# sudo apt-get install gcc 
linux:/root/postgresql-8.1.4# sudo apt-get install g++ 
linux:/root/postgresql-8.1.4# sudo apt-get install automake 
linux:/root/postgresql-8.1.4# gmake --version 
linux:/root/postgresql-8.1.4# gmake 
linux:/root/postgresql-8.1.4# gmake install 
linux:/root/postgresql-8.1.4# vim /etc/ld.so.conf  

When we edit it, we press "a" 
and add: /usr/local/pgsql/lib  
Now, press "ESC" 
and type :wq 

Installing pgtclsh 

linux:/root# wget [http://gnuworld.ircu.org/pgtcl1.5.tar.gz](http://gnuworld.ircu.org/pgtcl1.5.tar.gz) 
linux:/root# tar -zxvf pgtcl1.5.tar.gz 
linux:/root# cd pgtcl1.5 
linux:/root/pgtcl1.5# export PG_CONFIG=/usr/local/pgsql/bin/pg_config 
linux:/root/pgtcl1.5# ./configure --with-tcl=/usr/lib/  --prefix=/usr/local/pgsql --exec-prefix=/usr/local/pgsql  --with-postgres-lib=/usr/local/pgsql/lib 
linux:/root/pgtcl1.5# gmake 
linux:/root/pgtcl1.5# cd generic 
linux:/root/pgtcl1.5/generic# vim pgtclAppInit.c 


When we edit it, again, we press "a" (without the " " ) 

Modify the line: :#include <libpgtcl.h> in #include "libpgtcl.h"  
Press "ESC" 
Type :wq (again). 

linux:/root/pgtcl1.5/generic# cd .. 
linux:/root/pgtcl1.5# gmake pgtclsh 
linux:/root/pgtcl1.5# gmake install 
linux:/root/pgtcl1.5# mv pgtclsh /usr/local/pgsql/bin 
linux:/root/pgtcl1.5# mv libpgtcl1.5.so /usr/local/pgsql/lib 
linux:/root/pgtcl1.5# updatedb 
linux:/root/pgtcl1.5# ldconfig 
linux:/root/pgtcl1.5# /usr/local/pgsql/bin/pgtclsh  

The reply would have to be: 

root@Shadow:/home/catalin/Server/pgtcl1.5# /usr/local/pgsql/bin/pgtclsh 
%  

Creating the database: 

linux:/root# mkdir /usr/local/pgsql/data 
linux:/root# chown gnuworld /usr/local/pgsql/data 
linux:/root# su - gnuworld 
linux:/home/gnuworld$ /usr/local/pgsql/bin/initdb -D /usr/local/pgsql/data 
linux:/home/gnuworld$ /usr/local/pgsql/bin/postmaster -S -B 64 -N 32 -i -D /usr/local/pgsql/data -o -F -h 127.0.0.1 
linux:/home/gnuworld$ exit  

Configuring APACHE and PHP and other needed libraries: 

linux:/root# sudo apt-get install apache2 
linux:/root# sudo apt-get install mysql 
linux:/root# sudo apt-get install phpmyadmin 
linux:/root# sudo apt-get install aptitude 
linux:/root# sudo apt-get install cvs 
linux:/root# sudo apt-get install perl5 libnet-ssleay-perl 
linux:/root# sudo apt-get install curl libcurl3 libcurl3-dev php5-curl 
linux:/root# sudo apt-get install curl-ssl php5-gd 
linux:/root# sudo apt-get install php5-dev php5-pgsql  

Configuring GNUWORLD and WEBSITE: 

linux:/root# sudo apt-get install libpqxx-3.0 libpqxx3-dev libpqxx-dev 


If this doesn't work, try: 

linux:/root# sudo apt-get install libpqxx-3.0 libpqxx3-dev 
linux:/root# ls /usr/include/postgresql/libpq-fe.h 
linux:/root# su - gnuworld 
linux:/gnuworld# wget [http://gnuworld.ircu.org/gnuworld-hlds.tgz](http://gnuworld.ircu.org/gnuworld-hlds.tgz) 
linux:/gnuworld# wget [http://gnuworld.ircu.org/arhiva-website.tgz](http://gnuworld.ircu.org/arhiva-website.tgz) 
linux:/gnuworld# tar -zxvf gnuworld-hlds.tgz 
linux:/gnuworld# cd gnuworld 
linux:/gnuworld/gnuworld# ./configure  --enable-modules=ccontrol,cservice,chanfix,clientExample,cloner,dronescan,gnutes  t,nickserv,openchanfix,scanner,snoop,stats  --with-pgsql-home=/usr/local/pgsql  --with-extra-includes=/usr/include/postgresql/ 
linux:/gnuworld/gnuworld# gmake 
linux:/gnuworld/gnuworld# gmake install 
linux:/gnuworld/gnuworld# cd doc 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/createdb cservice 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/createlang -L /usr/local/pgsql/lib plpgsql cservice 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql cservice < cservice.sql 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql cservice < cservice.config.sql 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql cservice < languages.sql 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql cservice < language_table.sql 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql cservice < greeting.sql 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql cservice < cservice.help.sql 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql cservice < cservice.web.sql 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/createdb local_db 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql local_db < local_db.sql 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql cservice < cservice.addme.sql 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/createdb ccontrol 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql ccontrol < ccontrol.sql 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql ccontrol < ccontrol.help.sql 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql ccontrol < ccontrol.addme.sql 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql ccontrol < ccontrol.commands.sql 
linux:/gnuworld/gnuworld/doc$ cd .. 
linux:/gnuworld/gnuworld$ /usr/local/pgsql/bin/createdb chanfix 
linux:/gnuworld/gnuworld$ cd mod.openchanfix/doc 
linux:/gnuworld/gnuworld/mod.chanfix/doc$ /usr/local/pgsql/bin/psql chanfix < chanfix.sql  

Here, you edit GNUWorld.example.conf in whatever you want for the network, and cservice.example.conf  

linux:/gnuworld/gnuworld/bin$ screen -A -m -d -S bin ./gnuworld -c -f GNUWorld.example.conf 
linux:/gnuworld/gnuworld/bin$ screen -r bin 

Press Ctrl + A + D = to exit the screen 

The result: 

To log into X you have to use: 
/msg [email]X@services.undernet.org[/email] login Admin temPass 
-X- AUTHENTICATION SUCCESSFULL AS Admin! 

A few more things, and we are done. 

linux:/home/gnuworld$ tar -zxvf arhiva-website.tgz 
linux:/home/gnuworld$ cd website/php_includes 

Here we have the config.inc file, which we can freely edit in the way we want it, 
but you must NOT forget to add // at the begining of the following line : 
    //die("<h2><b>Error</b>: Edit website/php_includes/config.inc file !</h2>"); 


We now have Apache, pgsql and the others installed. 
Our last command took us here: 

linux:/home/gnuworld/gnuworld$ exit 
linux:/root# cd /var/www 
linux:/var/www# chmod 711 ~gnuworld 
linux:/var/www# chmod 711 ~gnuworld/website 
linux:/var/www# chmod 755 ~gnuworld/website/php_includes 
linux:/var/www# chmod 644 ~gnuworld/website/php_includes/config.inc 
linux:/var/www# chmod 755 ~gnuworld/website/docs/gnuworld/ 
linux:/var/www# ln -s /home/gnuworld/website/docs/gnuworld live  

[http://localhost/live](http://localhost/live) or [http://127.0.0.1/live](http://127.0.0.1/live) sau [http://ip/live](http://ip/live)  

We thank: 

**_*-  bG - For coding above and beyond the call of duty*_**           
**_*-  SadSoul - For coding above and beyond the call of duty:*_** 
**_*-  Shadow - For coding above and beyond the call of duty  *_**  
**_*- angelutza - For Translating above.*_**[B][U][I] 
- LD-  It`s always a pleasure[/I][/U][/B][FONT=arial]_._ 
[/FONT]***_-  sony -  It`s always a pleasure._*** 
[B][I][U] 
-  Ciprian -  It`s always a pleasure.[/U][/I][/B] 
[B][I][U] 
-  DenSpike - For the complete C++ experience, it's not over until the codes elegant

Reports: [email]support@ircu.org[/email]
[/U][/I][/B]

---

### Post by bG1988 on 2012-08-14
sudo apt-get install - the command for ubuntu 
yum -y install - the command for centos/debian 

First, we type: 

linux:/root# sudo apt-get install byacc 
linux:/root# sudo apt-get install flex 
linux:/root# sudo apt-get install screen 
linux:/root# adduser ircu
 

After that you press the "enter" button twice, 
and choose a password. 

Now download and configure ircu 

Download ircd 

linux:/root# su - ircu
linux:/gnuworld# wget [http://gnuworld.ircu.org/ircu2.10.12.14.tar.gz](http://gnuworld.ircu.org/ircu2.10.12.14.tar.gz) 
linux:/gnuworld# tar -zxvf ircu2.10.12.14.tar.gz 
linux:/gnuworld# cd ircu2.10.12.14 
linux:/gnuworld/ircu2.10.12.14# ./configure 
linux:/gnuworld/ircu2.10.12.14# make 
linux:/gnuworld/ircu2.10.12.14# make install 
linux:/gnuworld/ircu2.10.12.14# cd .. 
linux:/gnuworld/lib# cd lib 
linux:/gnuworld/lib# wget [http://gnuworld.ircu.org/ircd.motd](http://gnuworld.ircu.org/ircd.motd) 
linux:/gnuworld/lib# wget [http://gnuworld.ircu.org/ircd.conf](http://gnuworld.ircu.org/ircd.conf) 
linux:/gnuworld/lib# cd .. 
linux:/gnuworld# cd bin 
linux:/gnuworld/bin# ./ircd 
linux:/gnuworld# exit 

We go back to our root user 

Check if the TCL installed 


linux:/root# /usr/bin/updatedb 
linux:/root# locate tclConfig.sh 

If it has been installed, the response should be: 

/usr/lib/tclConfig.sh 

linux:/root# grep TCL_VERSION /usr/lib/tclConfig.sh 

The reply has to show the 8.0 version, or a higher one. 

If you don't have the TCL installed: 

linux:/root# wget [http://gnuworld.ircu.org/tcl8.4.13-src.tar.gz](http://gnuworld.ircu.org/tcl8.4.13-src.tar.gz) 
linux:/root# tar -xzf tcl8.4.13-src.tar.gz 
linux:/root# cd tcl8.4.13-src/unix/ 
linux:/root/tcl8.4.13-src/unix/# ./configure 
linux:/root/tcl8.4.13-src/unix/# make 
linux:/root/tcl8.4.13-src/unix/# make install 
linux:/root/tcl8.4.13-src/unix/# cd .. 
linux:/root/tcl8.4.13-src/# cd .. 
linux:/root# ln -s /usr/local/lib/tclConfig.sh /usr/lib 

How we install POSTGRESQL : 

linux:/root# wget [http://gnuworld.ircu.org/postgresql-8.1.4.tar.gz](http://gnuworld.ircu.org/postgresql-8.1.4.tar.gz) 
linux:/root# tar -xzf postgresql-8.1.4.tar.gz 
linux:/root# sudo apt-get install readline 
linux:/root# sudo apt-get install zlib 
linux:/root# cd postgresql-8.1.4 
linux:/root/postgresql-8.1.4# ./configure --with-CXX --enable-multibyte --with-tclconfig=/usr/lib --without-tk --without-readline --without-zlib
linux:/root/postgresql-8.1.4# ln -s /usr/bin/make /usr/bin/gmake 
linux:/root/postgresql-8.1.4# sudo apt-get install gmake 
linux:/root/postgresql-8.1.4# sudo apt-get install gcc 
linux:/root/postgresql-8.1.4# sudo apt-get install g++ 
linux:/root/postgresql-8.1.4# sudo apt-get install automake 
linux:/root/postgresql-8.1.4# gmake --version 
linux:/root/postgresql-8.1.4# gmake 
linux:/root/postgresql-8.1.4# gmake install 
linux:/root/postgresql-8.1.4# vim /etc/ld.so.conf 

When we edit it, we press "a" 
and add: /usr/local/pgsql/lib 
Now, press "ESC" 
and type :wq 

Installing pgtclsh 

linux:/root# wget [http://gnuworld.ircu.org/pgtcl1.5.tar.gz](http://gnuworld.ircu.org/pgtcl1.5.tar.gz) 
linux:/root# tar -zxvf pgtcl1.5.tar.gz 
linux:/root# cd pgtcl1.5 
linux:/root/pgtcl1.5# export PG_CONFIG=/usr/local/pgsql/bin/pg_config 
linux:/root/pgtcl1.5# ./configure --with-tcl=/usr/lib/ --prefix=/usr/local/pgsql --exec-prefix=/usr/local/pgsql --with-postgres-lib=/usr/local/pgsql/lib 
linux:/root/pgtcl1.5# gmake 
linux:/root/pgtcl1.5# cd generic 
linux:/root/pgtcl1.5/generic# vim pgtclAppInit.c 


When we edit it, again, we press "a" (without the " " ) 

Modify the line: :#include <libpgtcl.h> in #include "libpgtcl.h" 
Press "ESC" 
Type :wq (again). 

linux:/root/pgtcl1.5/generic# cd .. 
linux:/root/pgtcl1.5# gmake pgtclsh 
linux:/root/pgtcl1.5# gmake install 
linux:/root/pgtcl1.5# mv pgtclsh /usr/local/pgsql/bin 
linux:/root/pgtcl1.5# mv libpgtcl1.5.so /usr/local/pgsql/lib 
linux:/root/pgtcl1.5# updatedb 
linux:/root/pgtcl1.5# ldconfig 
linux:/root/pgtcl1.5# /usr/local/pgsql/bin/pgtclsh 

The reply would have to be: 

root@ircu:/home/ircu/Server/pgtcl1.5# /usr/local/pgsql/bin/pgtclsh 
% 

Creating the database: 

linux:/root# mkdir /usr/local/pgsql/data 
linux:/root# chown gnuworld /usr/local/pgsql/data 
linux:/root# su - gnuworld 
linux:/home/gnuworld$ /usr/local/pgsql/bin/initdb -D /usr/local/pgsql/data 
linux:/home/gnuworld$ /usr/local/pgsql/bin/postmaster -S -B 64 -N 32 -i -D /usr/local/pgsql/data -o -F -h 127.0.0.1 
linux:/home/gnuworld$ exit 

Configuring APACHE and PHP and other needed libraries: 

linux:/root# sudo apt-get install apache2 
linux:/root# sudo apt-get install mysql 
linux:/root# sudo apt-get install phpmyadmin 
linux:/root# sudo apt-get install aptitude 
linux:/root# sudo apt-get install cvs 
linux:/root# sudo apt-get install perl5 libnet-ssleay-perl 
linux:/root# sudo apt-get install curl libcurl3 libcurl3-dev php5-curl 
linux:/root# sudo apt-get install curl-ssl php5-gd 
linux:/root# sudo apt-get install php5-dev php5-pgsql 

Configuring GNUWORLD and WEBSITE: 

linux:/root# sudo apt-get install libpqxx-3.0 libpqxx3-dev libpqxx-dev 


If this doesn't work, try: 

linux:/root# sudo apt-get install libpqxx-3.0 libpqxx3-dev 
linux:/root# ls /usr/include/postgresql/libpq-fe.h 
linux:/root# su - gnuworld 
linux:/gnuworld# wget [http://gnuworld.ircu.org/gnuworld.tgz](http://gnuworld.ircu.org/gnuworld.tgz) 
linux:/gnuworld# wget [http://gnuworld.ircu.org/gnuwebsite.tgz](http://gnuworld.ircu.org/gnuwebsite.tgz) 
linux:/gnuworld# tar xzvf gnuworld.tgz 
linux:/gnuworld# cd gnuworld 
linux:/gnuworld# chmod +x *
linux:/gnuworld/gnuworld# ./configure --enable-modules=ccontrol,cservice,chanfix,clientExample,cloner,dronescan,gnutest,nickserv,openchanfix,scanner,snoop,stats --with-pgsql-home=/usr/local/pgsql --with-extra-includes=/usr/include/postgresql/ 
linux:/gnuworld/gnuworld# gmake 
linux:/gnuworld/gnuworld# gmake install 
linux:/gnuworld/gnuworld# cd doc 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/createdb cservice 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/createlang -L /usr/local/pgsql/lib plpgsql cservice 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql cservice < cservice.sql 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql cservice < cservice.config.sql 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql cservice < languages.sql 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql cservice < language_table.sql 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql cservice < greeting.sql 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql cservice < cservice.help.sql 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql cservice < cservice.web.sql 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/createdb local_db 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql local_db < local_db.sql 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql cservice < cservice.addme.sql 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/createdb ccontrol 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql ccontrol < ccontrol.sql 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql ccontrol < ccontrol.help.sql 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql ccontrol < ccontrol.addme.sql 
linux:/gnuworld/gnuworld/doc$ /usr/local/pgsql/bin/psql ccontrol < ccontrol.commands.sql 
linux:/gnuworld/gnuworld/doc$ cd .. 
linux:/gnuworld/gnuworld$ /usr/local/pgsql/bin/createdb chanfix 
linux:/gnuworld/gnuworld$ cd mod.openchanfix/doc 
linux:/gnuworld/gnuworld/mod.chanfix/doc$ /usr/local/pgsql/bin/psql chanfix < chanfix.sql 
linux:/gnuworld/gnuworld/mod.chanfix/doc$ cd ..
linux:/gnuworld/gnuworld/mod.chanfix$ cd ..
linux:/gnuworld/gnuworld$ cd bin 

Here, you edit GNUWorld.example.conf in whatever you want for the network, and cservice.example.conf 

After you finished edit on the files:

linux:/gnuworld/gnuworld$ ln -s /usr/lib/libpq.so.5 /usr/lib/libpq.so.4

If you are on x86_64 machine (64bit) you must also do this:

ln -s /usr/lib64/libpq.so.5 /usr/lib64/libpq.so.4

linux:/gnuworld/gnuworld/bin$ screen -A -m -d -S bin ./gnuworld -c -f GNUWorld.example.conf 
linux:/gnuworld/gnuworld/bin$ screen -r bin 

Press Ctrl + A + D = to exit the screen 

The result: 

To log into X you have to use: 
/msg [email]X@services.ircu.org[/email] login Admin temPass 
-X- AUTHENTICATION SUCCESSFULL AS Admin! 

A few more things, and we are done. 

linux:/home/gnuworld$ tar xzvf gnuwebsite.tgz 
linux:/home/gnuworld$ cd website/php_includes 

Here we have the config.inc file, which we can freely edit in the way we want it, 
but you must NOT forget to add // at the begining of the following line : 
//die("<h2><b>Error</b>: Edit website/php_includes/config.inc file !</h2>"); 


We now have Apache, pgsql and the others installed. 
Our last command took us here: 

linux:/home/gnuworld/gnuworld$ exit 
linux:/root# cd /var/www 
linux:/var/www# chmod 711 ~gnuworld 
linux:/var/www# chmod 711 ~gnuworld/website 
linux:/var/www# chmod 755 ~gnuworld/website/php_includes 
linux:/var/www# chmod 644 ~gnuworld/website/php_includes/config.inc 
linux:/var/www# chmod 755 ~gnuworld/website/docs/gnuworld/ 
linux:/var/www# ln -s /home/gnuworld/website/docs/gnuworld live 

[http://localhost/live](http://localhost/live) or [http://127.0.0.1/live](http://127.0.0.1/live) sau [http://ip/live](http://ip/live) 

If you get a PHP error do this:
linux:/var/www# nano /etc/php5/apache2/php.ini

Find the line : register_globals That looks like this:
register_globals = Off

Edit the line to :
 
register_globals = On

After you finished save and:

linux:/var/www# service apache2 restart

We thank: 

- bG - For coding above and beyond the call of duty 
- SadSoul - For coding above and beyond the call of duty: 
- rec - For coding above and beyond the call of duty: 
- Shadow - For coding above and beyond the call of duty

---

### Post by dabadone on 2013-03-18
> **bG1988 said:**
> sudo apt-get install - the command for ubuntu 
yum -y install - the command for centos/debian 



If for some reason yum fails on debian, you can try to double click the setup.exe file. It's as useless as yum {/sarcasm}

---

### Post by dabadone on 2013-03-18
You might also notice how you only need gcc/gcc-c++ only after you compiled ircu and tcl, but NEVER before configuring postgresql. Again... {/sarcasm}

---

