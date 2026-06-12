---
title: "[SOLVED] install php, apache, rpm packages using apt-get is not working"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by oalexandrino on 2007-11-10
Hello all,

first of all, sorry by asking any stupid question.

I'm PHP Developer who always uses Windows OS to develop my web sites. 
I use linux, at my company FreeBSD, just for deploying and testing scripts and websites.

So I don't have much experience when the topic is "set up" a Development Environment in Linux.

let me continue...

I used to use Red Hat Linux some years ago, and now when I met Ubuntu I loved it.
So, I have to set up this packages in my system.

- PHP 5
- Apache 2
- Perl

As Ubuntu doesn't have rpm as package management I have to use apt-get. Am I sure?

Have a look at these commands that I put at the terminal.

commands:

 sudo apt-get install apache2
 sudo apt-get install php5
 sudo apt-get install libapache2-mod-php5
 sudo /etc/init.d/apache2 restart

results:

# sudo apt-get install apache2
# Reading package lists... Done
# Building dependency tree       
# Reading state information... Done
# E: Couldn't find package apache2
# sudo apt-get install php5
# Reading package lists... Done
# Building dependency tree       
# Reading state information... Done
# E: Couldn't find package php5
# sudo apt-get install libapache2-mod-php5
# Reading package lists... Done
# Building dependency tree       
# Reading state information... Done
# E: Couldn't find package libapache2-mod-php5
# sudo /etc/init.d/apache2 restart
# sudo: /etc/init.d/apache2: command not found
 

What have I done wrongly?

Other question would be:

How to install rpm packages if dont have rpm.
by using alien? so, how can I install it?

thanks for any reply!

---

### Post by Hagbard on 2007-11-10
It sounds like there is a problem with your repositories configuration, because these packages are available. The file /etc/apt/sources.list contains the URLs to download packages from. Probably the easiest way for you to work with it is via the Synaptic Package Manager, which also works well for installing software in general. Launch Synaptic, then open the Settings menu and select Repositories. You probably want to have most of the "downloadable from the internet" options checked and active, and cd-rom sources turned off. After making these selections, you will need to choose "Reload" from the synaptic main window. Unless there is some additional problem, this should give you access to all the software you need for your development work.

There are also many good command line tools for searching the repositories. Try "man aptitude" to learn more about the options.

---

### Post by louieb on 2007-11-10
How about ```
sudo tasksel install lamp-server
```Debian got it right.  More here: [ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")
and theres XAMPP too . [HOWTO: (XAMPP) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=223410")

That is after you get  your repository problems cleared up.

---

### Post by oalexandrino on 2007-11-11
thanks for the reply...

now I got how it works...


I think at the instaltion time ubuntu tried to connect to those servers in order to verify some update.

I found this comment in the sources.list

# Line commented out by installer because it failed to verify:
I uncommented all lines for the repositories

it has solved my problem!

thanks!

---

