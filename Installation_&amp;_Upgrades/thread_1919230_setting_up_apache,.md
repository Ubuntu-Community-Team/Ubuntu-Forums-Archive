---
title: "setting up apache,"
date: 2012-02-02
forum: Installation &amp; Upgrades
---

### Post by jamstir on 2012-02-02
Hi guys.. i trying again to set up apache and have hit on a problem of.. i dont know what or where to stick how and when. lol 

Here, where i am.

I took the download and advice from here.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

I have followed and got as far as here.
Finally, we restart Apache2: 

sudo /etc/init.d/apache2 restart*If you have not created /home/user/public_html/, you will receive an warning message* 
To test the new site, create a file in /home/user/public_html/: 

echo '<b>Hello! It is working!</b>' > /home/user/public_html/index.htmlFinally, browse to [http://localhost/](http://localhost/)

What i cant work out is...     "TO TEST THE NEW SITE, CREATED A FILE IN   / HOME/USER/PUBLIC_HTML

WHERE??????
I have tried to find the path, and i cant find a folder names that.
Sudu tells me apache is up and working ,, but when i go to  [http://localhost/](http://localhost/)   i still get the      IT WORKS.
Should this still be telling me this?

jam@jam-desktop:~$ sudo apt-get install tasksel
[sudo] password for jam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
tasksel is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
jam@jam-desktop:~$ sudo tasksel install lamp-server
jam@jam-desktop:~$ apache2
apache2: bad user name ${APACHE_RUN_USER}
jam@jam-desktop:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                         [ OK ] 
jam@jam-desktop:~$ sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/mysite 
jam@jam-desktop:~$ gksudo gedit /etc/apache2/sites-available/mysite
jam@jam-desktop:~$ sudo a2dissite default && sudo a2ensite mysite
Site default already disabled
Site mysite already enabled
jam@jam-desktop:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                 ... waiting                                                             [ OK ]
jam@jam-desktop:~$ 

Everything looks good so far, but i really dont want to move on without knowing where to stick a file in where  home/user/bla/bla/bla.. lol

Any help would be great.  Now its time for a movie.

Thanks guys.

---

### Post by Lars Noodén on 2012-02-02
If you have activated [mod_userdir](http://httpd.apache.org/docs/2.2/mod/mod_userdir.html) then you can *also* place files in /home/user/public_html (or whatever you have set it to look for.)

Otherwise, the XHTML files need to get placed in /var/www

---

### Post by linuxsyst on 2012-02-02
... ok open terminal write ```
1st: sudo -s (or sudo bash)

```
then if you want graphic or text mode? graphic write ```
gksudo nautilus
```, if text then do it with cd (go to root of the system with /../ in root do ```
cd var/www
``` and you will see index.html file and edit it with text editor (vm or nano etc.)
back to graphic open the file browser (nautilus) and go to root then var/www and you see the index.html file edit it with any program 
note: you need to write gksudo nautilus because you need to be root to edit var folder 

hope I helped you

---

### Post by jamstir on 2012-02-02
mod _ userdir i looking into and reading.. thank you.

 linuxsyst    tried to do what you said and got this


jam@jam-desktop:~$ sudo bash
[sudo] password for jam: 
root@jam-desktop:~# cd var/www
bash: cd: var/www: No such file or directory
root@jam-desktop:~# exit
exit
jam@jam-desktop:~$ 

Any other way??
Stuck..  I like ubuntu, but i feel this is turning out to be more of a hobby than getting things to work. I have only really started playing with linux in the past 4 weeks, talking with a friend of mine, he tells me keep at it,, it will come.. hahah Hate asking for his help cause he works on pc,s from home for other people and i really need to learn for myself.

---

### Post by jamstir on 2012-02-02
Thanks for helping, i may have found a problem,  i am being told one thing but seem to have a problem doing it that way, but doing the right way, leads me to another problem.

I first went to look at the var/www   and going by seeing that.. i was told this was wrong, in that place i should have..    [I] /home/user/public_html/,

Now because i put this in its right place, now i get a warning!!!
[/I]

jam@jam-desktop:~$ gksudo gedit /etc/apache2/sites-available/mysite
jam@jam-desktop:~$ sudo a2dissite default && sudo a2ensite mysite
Site default already disabled
Site mysite already enabled
jam@jam-desktop:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                Warning: DocumentRoot [/home.user/public_html] does not exist
 ... waiting Warning: DocumentRoot [/home.user/public_html] does not exist
                                                                         [ OK ]
jam@jam-desktop:~$ 

So do i have to make a file in the directory name it    /home.user/public_html  ???

Here,s the way its set in::;

<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /home.user/public_html
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /home/user/public_html/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

I just over looking something, or not looking.. hahaha.

---

### Post by jamstir on 2012-02-03
I changed the  DocumentRoot [/home.user/public_html] does not exist

To...   document root   /documents/public_html                    and made a folder in document root folder being..  public_html.
But still not finding it.

---

### Post by Lars Noodén on 2012-02-03
DocumentRoot has to point to a directory that exists.  If it points to /var/www, then /var/www must exist.  If it points to /documents/public_html, then /documents/public_html  must exist.  

Also for you to edit XHTML documents in the directory, you have to have write permissions.  If you are going to be the only user, then you can just assign ownership to yourself:

```

sudo chown jamstir /documents/public_html

```

---

### Post by jamstir on 2012-02-03
ooooo guys your not going to belief this one.. hahahaha  i think i drink to much.. lol

I have tried to set the path up in apache, and set up folders and all kinds of things. none seem to be working.
I have read everything i can find and words that i don,t understand i have goggled, i have sat on youtube listening people ramble on about god only knows. If this was xp i would have it done last year, but i have been told that ububtu and the way you can change programs is much better to set up your own server.

I started all this by trying to load XAMPP,  which everyone says its 2 easy steps, however using the steps to install xampp kept getting me  child tar not found bla bla bla...

I did some home work on    /opt... and ended up installing something else though su command #.

I had Xammp sitting on my desktop and i extracted it from there after taken Apache off ubunbtu, i then cut and paste the file from xampp into   /opt by opening it in root.

Then i tried to open Xampp..  once again i failed.. hahahah  just by chance, and i mean it was by chance, i went to su and typed..   
sudo /opt/lampp/lampp start

and just look at what happened. 

jam@jam-desktop:~$ sudo /opt/lampp/lampp start
[sudo] password for jam: 
Starting XAMPP for Linux 1.7.7...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Another MySQL daemon is already running.
XAMPP: Starting ProFTPD...
XAMPP for Linux started.
jam@jam-desktop:~$ 

This has been 3 days sitting here learning, at at last i can say.. ITS ALIVE. hahah
Thanks for the help, am sure i will have more questions to come.

---

### Post by Lars Noodén on 2012-02-03
> **jamstir said:**
> 
This has been 3 days sitting here learning, at at last i can say.. ITS ALIVE. hahah
Thanks for the help, am sure i will have more questions to come.

Ok.  So this wasn't an Apache issue as much as it was a problem with XAMPP.  It's basically a crutch for systems still on Windows, and there are a lot of drawbacks to trying to use XAMPP on Linux.  One is that the security updates have to be done manually and don't get the benefit of the package manager (Software Center).

If you would like help taking down XAMPP and setting up Apache the easy way, we can do that, too.  

Out of curiosity what steered you to XAMPP instead of using the kit that Ubuntu provides?

---

### Post by jamstir on 2012-02-03
At the start i tried the ubuntu package, got so far and ran out of my  own ideas as to the problems i hit, some of these problems i can assure  you is the lack of brain matter i have  using ubuntu linux. Coming from  XP to linux i thought would be easy as any problem i ever hit with XP  got sorted in a matter of an hour.
Due to wanting my own web site and hosting  i was told linux is the way forward.

I really hate being stuck and not knowing a way around, seems with linux  there,s many ways around problems some cause other problems with other  programs. The other day i was going to throw this machine out the window  buy a house in the country and start raising cattle. lol

I have been told the best way to learn ubuntu is to be told what to do  and see it first hand, but i find this hard to belief from what i have  went though so far in order to install certain things you need to have  on maybe other programs, one thing that helps other,s maybe dont work  for someone else cause there missing something.

Where i got to now on XAMPP is loading the first trail page of my web  site made by Kompozer, the problem i have now is not understanding why  when i took the file out and set it on desktop, why does localhost still  display it? The file has been removed from the folder and i restarted  XAMPP.

One other problem i have is with mysql,  i got the download of ubuntu  and it worked fine, not that i had changed anything in there, but i new  it was up and working, when i took down xampp it failed to boot the  mysql package that came with xampp due to having it already running. So  therefore i thought it best to remove the package i got running and try  and install it from xampp, this is not working to well.. lol  after some  more reading i found out i not need to remove it, it would have been  fine there as it was. 

If you really want to help me to get a good linux system set up i would  advice a complete fresh install of 11.04 and take it from there, that  way i can follow and learn as we go though the motions. 
The only thing i really want is a web site build and hosted from this  old machine i got, i moved to China Shenzhen around a year ago and  bought a single core 2g 80 slow hard drive when i got here. I have  however bought a new motherboard and ram and slowly getting parts send  from HK to here to build a dual  boot system.
Therefore this machine and all that will be on it will be the web site and when i return home i can still upload to it and change things as needed.

Ok, time for a movie.. here from you soon.. Thanks.

---

### Post by Lars Noodén on 2012-02-03
Thanks.  

To install the regular Apache, you can use Synaptic or the Software Center or apt-get:

```

sudo apt-get install apache2

```

That gives you by default one virtual host.  The configuration for the one virtual host will be in /etc/apache2/sites-available/default  That is where any changes to the configuration should go. 

The web pages for the one virtual host will be in /var/www

Here is one way of setting the permissions in /var/www so that you can write to the directories.  It will give write access to members of the group 'webmasters' 
 
```

sudo addgroup webmasters

sudo gpasswd --add jamstir  webmasters

sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;

sudo find /var/www -type f -exec chmod g=rws  "{}" \;

```

You can find very detailed explanations of the programs by looking at the manual pages.  Don't worry, they will seem like a lot at the beginning, but they will grow on you.

```

man apache2ctl
man addgroup
man gpasswd
man chgrp
man find
man man

```

perl is already included in the default install of Ubuntu.  [PHP5](apt://php5) and [MySQL](apt://mysql-server) can be added the same way as Apache2 was.

---

### Post by jamstir on 2012-02-04
Well its sunday today, i not working today got go meet with future Chinese inlaws.
Come monday i will remove Xampp and follow your instructions, however i know i going to hit problems hahaaha.

I still cant understand why in apache it cant find the path i put in, i made a document root being  public_html folder.
So the full path was.     home/jam/documents/public_html

I had changed to mysite and the document root and the directory by going into    gksudo gedit /etc/apache2/sites-available/mysite

All i got was no such directory, but i was looking at it. hahaha

Anyway, until monday, will post up any problems here, hope i can get it working.
Thanks again for your help.

---

### Post by Lars Noodén on 2012-02-05
Excellent.  When you set to work on Monday, one of the first things to do would be to make copies of the unchanged configuration files.  That way when you want to roll back to a fresh start, it is just a matter of copying from the backup.

---

### Post by jamstir on 2012-02-06
UPDATE..

Hey, well i got completely rid of Xampp and installed Apache 2.2, when i started it up it went to mysite instead of the default site, i found this not to be a problem and managed to get it back to the default being   var/www.

I then tried to take down mysql, i will work on this as the sudo apt-get failed to start the download.

I then tried to throw a trail web page into the file /www and found i had no write permission, once again i tried the command lines that you gave me, and done worked for some odd reason.. i searched around this site and found away to get around it, but i feel this was a bad way because anyone can write to it, so if i got hacked.. oppsss there,s the web site being hacked along with my computer which is the server.

Can you help me in setting up a user name that can only write to that file /www  i sort of lost as to how to go about this unless i spend the next 10 years reading.. lol

The file that was in var/www was a root file and i really dont know how i got around this.. but i did and have got the localhost showing the file i put into it.

And of the top of your head.. do you or can you confirm what i read, that the first page of any web site should be named index_html....     this being the first one that gets looked at when someone goggle,s your site.??

I really happy at the stage i got at today and seem to be finding ways around things for myself.
For now i will work on getting mysql installed and see if i can get a user control panel made for apache just to turn of and on would be great than going to terminal all the time.

Thanks..

---

### Post by Lars Noodén on 2012-02-06
Here's a recipe for setting file permissions.  It's one of many ways of accomplishing the same thing.

```

sudo addgroup webmasters
sudo gpasswd --add jamstir webmasters


sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;

sudo find /var/www -type f -exec chmod g=rws  "{}" \;

```

As far as naming the index files, the normal default is [font=Courier New]index.html[/font].  Mind it's a dot (.) not an underscore (_).  In theory you could require whatever name you want by editing the [DirectoryIndex](http://httpd.apache.org/docs/2.2/mod/mod_dir.html#directoryindex) directive.

---

### Post by jamstir on 2012-02-06
jam@jam-desktop:~$ sudo addgroup webmasters
[sudo] password for jam: 
addgroup: The group `webmasters' already exists.
jam@jam-desktop:~$ 

And when i try this i get... 
jam@jam-desktop:~$ sudo gpasswd --add jamstir webmasters
[sudo] password for jam: 
gpasswd: user 'jamstir' does not exist
jam@jam-desktop:~$ 

I have bigger problems with mysql... hahah  but lets try and get first one fixed,  I turned of and on the Apache, and went to local host, it showed me the default page, was not untill i went to the /www file clicked on the file inside then it changed to my trail web page.
Hmmm,,

---

### Post by Lars Noodén on 2012-02-06
Substitute your username for "*jam*" below.  It has to be the username you have on your system to be valid.

```

sudo gpasswd --add *jam* webmasters

```

addgroup only needs to be run once.  After that, the group exists and will continue to exist until you go out of your way to delete it.  

About MySQL, two things confused me the first time I tried to run it.  

First, it operates on a [client-server model](http://en.wikipedia.org/wiki/Client%E2%80%93server_model).  Once I had the server up and running, I needed to connect to it via a client.  The client comes in the package [mysql-client](apt://mysql-client).  I didn't know that at the time and was trying the wrong way.  

Second, the server should be started and stopped via the script [font=Courier New]/etc/init.d/mysql[/font].  Nowadays, that can be done instead via [upstart](http://manpages.ubuntu.com/manpages/oneiric/en/man8/start.8.html)

---

### Post by jamstir on 2012-02-06
.. LOL  i get on one hand its says its there, then i get its not.. 

I thought by maybe downloading it again i would get what ever is wrong fixed, but..
jam@jam-desktop:~$ mysql-server libapache2-mod-auth-mysql php5-mysql
mysql-server: command not found
jam@jam-desktop:~$ 

So i tried this.. i should point out.. in the synaptic package manager tells me its already installed, i just trying this to see if it will fix a problem.
jam@jam-desktop:~$ sudo apt-get install mysql-server
[sudo] password for jam: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jam@jam-desktop:~$ 

So i cant download it,, and then i tried this..   

jam@jam-desktop:~$ mysql -h localhost -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
jam@jam-desktop:~$ 

This really has got me confused.com.
 By the way.. user name... worked.. thanks.
as for mysql, i dont know where to turn, i have read and goggled everything i can find.

Is there no one command to uninstall it and then install?

---

### Post by Lars Noodén on 2012-02-06
How much do you have installed so far?

```

dpkg --get-selections mysql-*

```

---

### Post by jamstir on 2012-02-06
jam@jam-desktop:~$ dpkg --get-selections mysql-*
mysql-client                    install
mysql-client-5.1                install
mysql-client-core-5.1                install
mysql-common                    install
mysql-server                    install
mysql-server-5.1                install
mysql-server-core-5.1                install
jam@jam-desktop:~$ I throw this in and this popped up..

sudo dpkg-reconfigure mysql-server-5.1

jam@jam-desktop:~$ sudo dpkg-reconfigure mysql-server-5.1
[sudo] password for jam: 
/usr/sbin/dpkg-reconfigure: mysql-server-5.1 is broken or not fully installed.
jam@jam-desktop:~$ 

Which i think is correct, one command i did try to use to reinstall told me 2 packs were not installed, but then it decided not to install them anyway.. i will try and find that command again and give a report.

I have other packages in synaptic not installed, but what ones are given the problem, i dont know.

---

### Post by jamstir on 2012-02-06
Its like its there, but its waiting,

jam@jam-desktop:~$ service mysql status
mysql stop/waiting
jam@jam-desktop:~$ 

jam@jam-desktop:~$ mysqladmin -u root -p status 
Enter password: 
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
jam@jam-desktop:~$

---

### Post by jamstir on 2012-02-06
6 hours of pain,, eyes watering and sleep kicking in.. but.

jam@jam-desktop:~$ mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
jam@jam-desktop:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 4
Server version: 5.1.54-1ubuntu4 (Ubuntu)

Copyright (c) 2000, 2010, Oracle and/or its affiliates. All rights reserved.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL v2 license

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>

I would say it working.

Now to find away for all these to work together.. i cant really set up mysql yet due to not having a static IP address, do you know the commands by the way for finding your internal IP address.. i belief i need this to obtain a static one.

Or there is a program somewhere that i can download that will detect if and when my IP address changes and then i can update the changes.
Tomorrow i will read all day about codes and have some fun making links from one web page to the other.

Thank you again for your help, i did a bit of reading on the security of Xammp, and went to there security set up page, near fell of my seat when i could,nt change user name from lampp and could only use a password. lol

---

### Post by Lars Noodén on 2012-02-07
> **jamstir said:**
> 
Or there is a program somewhere that i can download that will detect if and when my IP address changes and then i can update the changes.

One option could be to use a [dynamic DNS service](https://help.ubuntu.com/community/DynamicDNS).  However for "LAMP" work, you won't need an external address for MySQL unless you have Apache and MySQL on separate machines.

About the web pages if you set up [Server-Side Includes](http://httpd.apache.org/docs/2.2/howto/ssi.html) then you have standardized headers, footers and menus without having to resort to using PHP, Perl or other scripting languages.  Just be sure to use [IncludesNOEXEC](http://httpd.apache.org/docs/2.2/mod/core.html#options) to prevent other than static files from being used.

---

### Post by jamstir on 2012-02-07
I read the details on apache, seems like a good idea for once the site is up and running, thanks for the advice on DNS service.
Bit lost as to the next step, take it i should build the site then look into port forwarding? i going to be using this pc for the sole purpose of the web site and buy a laptop i hope to excess and control the site though my laptop as i will be leaving China sometime this year for home ward bound.
I get to see my wonderful pc at home again, which is getting a bit like me now.. old.. but still keeps with the best of them. lol

You seem to know  a lot on apache and all, you have a web site up and going?

---

### Post by Lars Noodén on 2012-02-08
Once you can serve up pages via the localhost, then the next step is likely to be port forwarding on your router/modem so that you can access the pages while away from home.  The settings vary from model to model and you'll have to find the instructions yourself.  As to which ports to forward, you'll need 80 (http), 443 (https) and 22 (ssh).

I've used Apache at work before and in teaching.  There are many who are more familiar with it, it's been the most common web server since 1996 or so.  It's popular for good reason.  There  is also  the [number two in popularity server, nginx](http://news.netcraft.com/archives/2012/01/03/january-2012-web-server-survey.html), which is also available in Ubuntu.

---

### Post by jamstir on 2012-02-08
I might go ahead a reg a domain name and start looking at port  forwarding, i did some work on this it seems easy enough to set up.
At the minute i found a few great programs to help build a website..

PHP FRAMEWORK.
         Codelgnitor 2.1.9

TEMPLATE ENGINE.
     Dwoo

CONTENT MANAGER SYSTEM.
Joomla, and Wordpress.

So far i have tried to install the latest Joomla, but have failed to start the install.
There,s no clear way to install it, the install in system file use,s a  different version of MYSQL, i found this not to be a problem and just  used the commands for my version, In the install file also tells me to  change the Buffer in PHP to OFF.. which i done, along with setting up  apaphe with joomla.

The instructions here are for an older version but only changed the version and the left out the number,s before that.
.[http://www.upubuntu.com/2011/11/how-to-install-joomla-17x-on-ubuntu.html](http://www.upubuntu.com/2011/11/how-to-install-joomla-17x-on-ubuntu.html)

Apache i think needs a little more set up, i open localhost in browser i still get the trail web page i built.
As you can tell i am still confused as to how all this works together.. lol
I think after i set port forwarding up and reg.. a domain name i will see a lot better whats going on with the whole thing.

---

### Post by jamstir on 2012-02-08
JSSSSS.. i have opened localhost and it shows a web page i was working on, i set a file into var/www and when i hit on it it opens another brower displays it as a file in the browser, i then tried to go back to the localhost page to try something else with it, and i cant find were it is.. hahah.

I think for now just getting to know apache and the way around would be good., i dont even know hoe i got that page saved into localhost, and now its there i cant get it out.

---

### Post by jamstir on 2012-02-09
Need help with Apache, i have tried to install php pages into  var/www/home    folder...  To make sure i was using the right default i went into the.. well you can see here what i done.

jam@jam-desktop:~$ gksudo gedit /etc/apache2/sites-available/ default
jam@jam-desktop:~$ gksudo gedit /etc/apache2/sites-available/mysite
jam@jam-desktop:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                Warning: DocumentRoot [/var/www/home/index.html] does not exist
 ... waiting Warning: DocumentRoot [/var/www/home/index.html] does not exist
                                                                         [ OK ]
jam@jam-desktop:~$ gksudo gedit /etc/apache2/sites-available/mysite
jam@jam-desktop:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                 ... waiting                                                             [ OK ]
jam@jam-desktop:~$ 

By the index.html coming back at me i know am on the right road, from my understanding by putting a php file into home folder and going to localhost/    i should be seeing the php translated. Instead i seeing the trail web page i put in and really cant work out how to get it back out again.  

I think i need to set the conf file by going back in here, gksudo gedit /etc/apache2/sites-available/ default ....... but unclear as to what i have to do.
And does anyone know a good IDE to use, i not ready for Codelgnitor 2.1.9 yet as am doing a crash course on PHP writing.

Thanks. Hope someone can help..

---

