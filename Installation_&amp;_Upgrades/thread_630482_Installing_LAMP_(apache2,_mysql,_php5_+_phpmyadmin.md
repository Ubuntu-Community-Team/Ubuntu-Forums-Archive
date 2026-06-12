---
title: "Installing LAMP (apache2, mysql, php5 + phpmyadmin) on Gusty 7.10"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by aubreyisland on 2007-12-03
I just followed the simple steps [here,]("http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100") I will re-post for convenience:

Lately I&#8217;ve been using ubuntu 7.10 for all my projects/daily work.
As a web developer i should have LAMP on my machine and now i would guide you through installing it on yours.

This guide is divided into 3 steps: installing/tesing Apache, PHP and finally MySQL.

Lets start with Apache:
1. Open the terminal (we will be using it through most of my guide) from Applications > Accessories > Terminal
2. Install apache2 using apt-get by typing the following
```
sudo apt-get install apache2
```

Note that you should know the root password.
Now everything should be downloaded and installed automatically.
To start/stop apache2 write:
```
sudo /etc/init.d/apache2 start
sudo /etc/init.d/apache2 stop
```

Your www folder should be in: /var/www/

If everything is OK you should see an ordinary HTML page when you type: [http://localhost](http://localhost) in your firefox browser

Finished with Apache ? lets conquer PHP:
1. Also in terminal write:
```
sudo apt-get install php5 libapache2-mod-php5
```

or any php version you like
2. restart apache
```
sudo /etc/init.d/apache2 restart
```

This is it for PHP :D
Wanna test it ? Just create an ordinary PHP page in /var/www/ and run it.
Example:
```
sudo gedit /var/www/test.php
```

and write in it: ```
< ?php echo "Hello World"; ?>
```

Now run it by typing [http://localhost/test.php](http://localhost/test.php) in firefox&#8230; You should see your &#8221; Hello World &#8221;

66 % is over, lets continue to installing MySQL:
1. Again and again in terminal execute:
```
sudo apt-get install mysql-server
```

2. (optional) If you are running a server you should probably bind your address by editing bind-address in /etc/mysql/my.cnf and replacing its value (127.0.0.1) by your IP address
3. set your root password [COLOR="Red"](although mysql should ask you about that when installing)[/COLOR]
```
mysql> SET PASSWORD FOR &#8216;root&#8217;@'localhost&#8217; = PASSWORD(&#8217;xxxxxx&#8217;);
```

4. Try running it
```
mysql -uroot -pxxx
```

where xxx is your password.
Note: You can install PHPMyAdmin for a graphical user interface of MySQL by executing
sudo apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin

5. restart apache for the last time
```
sudo /etc/init.d/apache2 restart
```

Congratulions your LAMP system is installed and running :D
Happy Coding

Note: I edited my Applications Menu (right-click) and added a launcher in my Internet Item that Launches: 

```
sudo /etc/init.d/apache2 start
```

And subsequently for restart and stop.

Also I had to chown the www folder so that I could easily edit files in it:

```
cd /var/
sudo chown -R USERNAME www
```

...then created a symlink in my home directory:

```

ln -s -v /var/www /home/USERNAME/www

```

---

### Post by smartbei on 2007-12-03
Alternatively,
```

sudo tasksel lamp-server

```

And then if you want set the mysql server password as shown above.

---

### Post by aubreyisland on 2007-12-03
Saw that in another post, but I know it doesn't update with apt-get or anything...

---

### Post by smartbei on 2007-12-03
What do you mean? tasksel is simply a script that installs packages through aptitude in groups by common usage.

As far as I know there is no difference between packages installed by tasksel and packages installed by you.

---

### Post by aubreyisland on 2007-12-03
That's just what I had read on another post...

---

### Post by adster101 on 2007-12-10
Cool post and it all worked well except that I can't see how to start or get to phpmyadmin.

where's it to?

---

### Post by aubreyisland on 2007-12-10
Im pretty sure you do localhost/phpmyadmin or something like that. I'm back in Windowz so, pheh!

---

### Post by nexes on 2007-12-16
This is a handy guide, but there's one thing that should be done differently.

Instead of chown'ing /var/www or anything inside of it, you should place a symlink in place of that directory that points to a folder in your home directory.

So, create a folder called public_html or something similar in your home directory, then do (if you're not root):

sudo rm /var/www -r
sudo ln -vs /home/you/public_html/ /var/www

It's probably not a big deal for use on your own PC, but that's still the proper way to do it. :)

On a server, particularly a multiuser one, you'd want to do it yet another way.

---

### Post by jimmccool on 2008-03-13
WHOAH THERE HORSE!

I've just tried to do a taskel lamp... and encountered problems... If it looks too easy, it prolly is, unfortunately... I killed the process when it [probably luckily] stalled. There are some horror stories here that might make you think twice: [http://ubuntuforums.org/showthread.php?t=598462](http://ubuntuforums.org/showthread.php?t=598462) 

Actually, the command to actually install LAMP  is not "sudo tasksel lamp-server" but instead
'sudo tasksel install lamp-server' - but I really wouldn't advise it. I'm now going to do the sensible thing and install the packages individually, as described above.

There's a pretty comprehensive guide to TASKSEL here [https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

---

### Post by pk_rulz on 2008-03-21
Can someone tell me which repo should be activated for this Apache Install ... I am having issues ... My Apache install is fine but after I install PHP and test it it does not work

---

### Post by fruni on 2008-03-22
It is saying this when i try to install apache:

fruni@fruni-laptop:~$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package apache2

---

### Post by zvacet on 2008-03-23
If you use server 


```
sudo nano -Bw /etc/apt/sources.list
```

add line

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe multiverse

Isupose that you use Gutsy.If that is not a case replace **gutsy **in the line with version you use.

If you run desktop

**system<admin>software sources**>check all boxes under Ubuntu software and updates tab.Reload.In **synaptic>edit tab<mark packages by task>select LAMP**

---

