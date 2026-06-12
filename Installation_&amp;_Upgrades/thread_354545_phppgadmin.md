---
title: "phppgadmin"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by allyson on 2007-02-06
Hi all,

I am running Edgy Eft.

A few months I successfully installed the whole "LAMP" installation by following these instructions:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
Everything works fine.

Yesterday I successfully installed postgreSQL using apt-get, and I can connect with and make new databases using pgadmin (also installed via apt-get). However, I am used to the phpMyAdmin interface, so thought I would also install phppgadmin and see what it was like. I successfully ran the apt-get and it is installed, and then I ran the following commands:
```
sudo ln -s /usr/share/phppgadmin /var/www/phppgadmin
sudo /etc/init.d/apache2 restart
```
However, whenever I try to load [http://localhost/phppgadmin/](http://localhost/phppgadmin/), I get the following message:
> Your PHP installation does not support PostgreSQL. You need to recompile PHP using the --with-pgsql configure option.

I don't know how to recompile, as I installed everything with apt-get. Can anyone help?

Thanks very much!

---

### Post by apjone on 2007-02-06
try 
dpkg-reconfigure php5 --with-pgsql 

or what ever your php packe is called

as root or sudo

---

### Post by allyson on 2007-02-06
Thanks for your idea. When I tried it, I got the following error message:

> $ sudo dpkg-reconfigure php5 --with-pgsql 
Password:
Unknown option: with-pgsql
Usage: dpkg-reconfigure [options] packages
  -a, --all                     Reconfigure all packages.
  -u, --unseen-only             Show only not yet seen questions.
        --default-priority      Use default priority instead of low.
        --force                 Force reconfiguration of broken packages.
  -f, --frontend                Specify debconf frontend to use.
  -p, --priority                Specify minimum priority question to show.
        --terse                 Enable terse mode.

However, before I looked up the dpkg command, I had a look at my Synaptic to see what php apps were installed.

It turns out that the apt-get that got the phppgadmin actually retrieved the php4-pgsql module rather than the php5-pgsql module. I have php5, so I removed the former and added the latter, restarted the apache server and now phppgadmin is working!

thanks very much for all your help!

---

### Post by apjone on 2007-02-06
hey great news, and thanks for posting how you fixed it.

---

### Post by peterroots on 2007-08-06
I had exactly the same problem, though I installed apache, postgresql, phppgadmin at the same time using adept (in kubuntu) - all the packages installed and including the php5 module for postgresql.
I tried the dpkg-reconfigure php5 --with-pgsql which did not know what pgsql was either.
After much gnashing of teeth and muttering 'if ubuntu is for humans they must be darn odd looking etc etc' i restarted apache
Sometimes its the simplest of things that work and are so blindingly obvious you just don't see them!!
Mind you I can't log into the server with the default postgres user and pw
Ho Hum!
Finally got into the server with phppgadmin!
I had created a database and user from the command line.
I had edited the user postgres (system admin->user management) and given it a password I knew
in a terminal i changed user
    su - postgres
and entered my newly created password
then I created a database
   createdb outkafe
and a user
  create user outkafe
THIS was my mistake, I had created a user with no password and phppgadmin won't let you log in with a passwordless user
by running psql (as user postgres) I was able to use 
  alter user outkafe with password '****';
  NB the ' before and after the password are essential it seems as is the final ;

---

