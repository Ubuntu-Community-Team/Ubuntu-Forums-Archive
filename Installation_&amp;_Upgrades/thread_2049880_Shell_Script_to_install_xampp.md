---
title: "Shell Script to install xampp"
date: 2012-08-29
forum: Installation &amp; Upgrades
---

### Post by saugatad on 2012-08-29
I have created a shell script that helps you to download and install xampp and configure the file permission in htdocs. The script will handle all the process after initialization of the script. It can be downloaded here [https://dl.dropbox.com/u/17475393/xampp.sh](https://dl.dropbox.com/u/17475393/xampp.sh)

For more Information [http://freshtutorial.com/xampp-linux/](http://freshtutorial.com/xampp-linux/)

I would love to hear the suggestion and Feedback. Thanks
:D

---

### Post by josephmills on 2012-08-29
you should not be setting permissions like that. 

Line 20
```

chmod 777 -R /opt/lampp/htdocs

```

```

function changaroo(){
cd /opt/lampp
sudo find . -type f -exec chmod 644 {} \;
sudo find . -type d -exec chmod 755 {} \;
}

```

I also would change the shebang to bash and not sh that is just me though
all togeather

```

#!/usr/bin/env bash
#Script to install Xampp in your Linux System
## this is where I will add copyleft

#Download XAMPP
wget -O xampp-linux-1.8.0.tar.gz http://sourceforge.net/projects/xampp/files/BETAS/xampp-linux-1.8.0.tar.gz/download
#Extract XAMPP in /opt
tar xzf xampp-linux-1.8.0.tar.gz -C /opt
#Change the perission of htdocs
##chmod 777 -R /opt/lampp/htdocs
function changaroo(){
	cd /opt/lampp
	sudo find . -type f -exec chmod 644 {} \;
	sudo find . -type d -exec chmod 755 {} \;
}
if changaroo; then
	notify-send "Xampp Permissions are now set"
else
	notify-send "Something went wrong"
fi

```

---

### Post by Lars Noodén on 2012-08-29
Good initiative, but there are much easier ways for Linux.   XAMPP is fine for the Windows world where package installation is difficult and monoliths are a help.  Have you considered installing LAMP as a faster, safer, easier, more secure alternative to XAMPP?

LAMP needs no script.  

```

sudo apt-get update
sudo tasksel install lamp-server

```

And you're done.  Plus all dependencies are managed automatically and updating (including security updates) are available automatically, too.

Or it can be done using just [apt-get](http://manpages.ubuntu.com/manpages/precise/en/man8/apt-get.8.html)

```

sudo apt-get update
sudo apt-get install lamp-server^

```

Alternately, you could install the components one at a time:

```

sudo apt-get update
sudo apt-get install apache2 php5 mysql-server mysql-client

```

Linux is already there (Ubuntu) and Python and Perl are built-in to your Ubuntu system so there is no need to install either.  That leaves just the database and the web server.

For the web server, there are alternatives like nginx and lighttpd.  For the database, there is also postgresql.  

XAMPP installs programs in non-standard, must be maintained manually and included redundant programs. 

I'm curious as to how XAMPP is being promulgated over the traditional LAMP resources.  Where is it coming from?

---

### Post by josephmills on 2012-08-29
> **Lars Noodén said:**
> 
```

sudo apt-get update
sudo apt-get install lamp-server^

```



+1 I was going to also say that same thing. 
but I seen that 777 in there. and that is no good. Or at least I do not think that it is good that anyone can read write and is executable on the files. 

> If you use htaccess for password protection, then the location containing all of your password information is plainly available through the htaccess file. If you have set incorrect permissions or if your server is not as secure as it could be, a browser has the potential to view an htaccess file through a standard web interface and thus compromise your site/server 

Not sure about it or xampp thou but L.A.M.P def works

---

### Post by Lars Noodén on 2012-08-29
> **josephmills said:**
> +1 I was going to also say that same thing. 
but I seen that 777 in there. and that is no good. Or at least I do not think that it is good that anyone can read write and is executable on the files. ...

It's even worse when combined with the scripting capabilities of PHP. ;)

---

### Post by saugatad on 2012-08-29
Thanks everyone for the valuable feedback. Though lampp is awesome tool for Linux. Most people who migrate from windows still prefer xampp. Therefore I have created it. Thanks a lot everyone for your reply anyway

---

