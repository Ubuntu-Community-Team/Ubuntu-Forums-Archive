---
title: "Installing Ubuntu on a server"
date: 2014-11-25
forum: Installation &amp; Upgrades
---

### Post by ddemers on 2014-11-25
Last time I installed Ubuntu, was about 10 years ago when I was in college, since then I have strictly managed Windows clients and servers.   The exception to this is a few Ubuntu servers that I helped support, but it left a sour taste... if the server didn't do a check desk every x days it would forcefully do one upon the next reboot... and there was a chance it would just freeze.  I would like to make sure this server is setup correctly.

The OS will be installed on a HP proliant server.

Questions: 

1  Where do I download Ubuntu 12.04 LTS, is there an official download location?
2.  do I just download the desktop version?  Seems like the server version doesn't have a GUI and I want a GUI
3.  Is there a document detailing best practices for setting up Linux/Ubuntu in an enterprise/business environment (i.e. so it doesn't do things like chkdsk every 3 months).

---

### Post by mörgæs on 2014-11-25
1) Why do you want 12.04 and not 14.04? 

2) **sudo apt-get install ubuntu-desktop** adds the GUI and default applications to a server install - or you could add server components to a desktop install.

3) Don't know. I mostly use the desktop.

---

### Post by ddemers on 2014-11-25
the vendor wants that  version.

thanks for the info

---

### Post by mastablasta on 2014-11-26
> **ddemers said:**
> 
Questions: 

1  Where do I download Ubuntu 12.04 LTS, is there an official download location?
Ubuntu.com ->downloads-> server-> alternative downloads
> 
2.  do I just download the desktop version?  Seems like the server version doesn't have a GUI and I want a GUI

Server doesn't have GUI as there is usually no monitor attached to it. however you can install a GUI using apt get (depends what you want and if you want full desktop or just a simple windows manager). be advised that default Ubutnu UGI needs good 3D hardware acceleration and will use resources on server. resources that could be used better elsewhere. simple example. default GUI needs 1 GB ram to run efficiently. it will use about half of that on idle. Server needs 256 MB ram and uses very little on idle (a couple of MB).

second option is to use a webgui - to administer server via browser. have a look at zentyal, webmin or ajenti. Zentyal is a drop in replacement for windows SBS based on ubutnu and officially supported.

> 
3.  Is there a document detailing best practices for setting up Linux/Ubuntu in an enterprise/business environment (i.e. so it doesn't do things like chkdsk every 3 months).

first of all chkdsk can not be run on Linux. it's a windows program. Linux runs fsck and it runs it after certain number of reboots on desktop. I am sure that function can be turned off. there is no specific guide for business server as each business has different needs for their server. Zentyal makes it easy to setup and administer, add programs or services.

servers are usually on all the time. so you would likely want to setup some automatic updates. there is no need to reboot server constantly.

---

### Post by coldraven on 2014-11-26
1. [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/) scroll down the page to see different download options, I prefer the Torrent because it is usually faster.
2. Using a GUI on a server is considered to be a security weakness
3. Don't know

Edit: Alternatives to cpanel here [http://alternativeto.net/software/cpanel/](http://alternativeto.net/software/cpanel/)

---

### Post by ddemers on 2014-11-26
thanks for the information.

I knew chkdsk was a windows thing, but I had no idea what the Linux part was, if this is a default setting on server also I will need to figure out how to turn it off, will deal with that later.

I  understand each business needs different and the GUI adds additional resources and security holes.   Unfortunately this is the only Linux server I will be supporting with little chances of supporting/maintaining others so the gui is a requirement, otherwise I will spend a lot of time looking up commands/trying stuff I don't fully understand, which is likely to be a larger security concern :)


I will install it on the server today, I am pretty sure HP support Ubuntu as part of its deployment software so drivers shouldn't be an issue.  Is there a 'device manager' program where I could verify device drivers are functioning correctly

---

### Post by mastablasta on 2014-11-26
> **ddemers said:**
> 
I  understand each business needs different and the GUI adds additional resources and security holes.   Unfortunately this is the only Linux server I will be supporting with little chances of supporting/maintaining others so the gui is a requirement, otherwise I will spend a lot of time looking up commands/trying stuff I don't fully understand, which is likely to be a larger security concern :)

the just use some WebUI. you type in IP of the server, enter the password and can maintain it from your home over a GUI.

By the way by default Zentyal installs both XFCE desktop GUI and Web GUI. you can givei it a try in virtualbox if you are not in a hurry.

Unless you use server gui you will be running desktop and doing administration in command line anyway. server tools (open ssh, mail server etc) are command line based. however web user interfaces i mentioned here show the data and commands in a GUI way. they make it easy to setup things in just a few clicks usualyl with some sane defaults. desktop doesn't have these kind of things. so another reason why it is useless. if server is opened to internet you will need to secure it. i am not aware of desktop tools but this is usually done via either server webGUI or CLI.

any i will also add here that settign up the server is not so much about commands as it is about editing config files. now some programs have nice comments in their config files and configuration is easy. e.g. mail=1 to enable email, mail= 0 to disable etc.

> 
I will install it on the server today, I am pretty sure HP support Ubuntu as part of its deployment software so drivers shouldn't be an issue.  Is there a 'device manager' program where I could verify device drivers are functioning correctly

it does, although i think they are promoting Red Hat = CentOS more. Now CentOS has very long support term and 2 very good web GUI. One is ClearOS, the other one is Nethserver. However both are still on CentOS 6, while new one is 7. I expect them to slowly move to 7 within the next 6 months. in my opinion Ubuntu is a lot friendlier.

HP also pushes SUSE Enteprise Linux, but many of their servers and desktops also have Ubuntu certification. : [http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/) 

and once again what is the server used for ? there might be easy to setup GUI options and we could help you and give maybe better advice to make it easier. i am also a GUI person. though i conceeeded i need to do some things in terminal and is someitmes  asier to do them in CLI (which is where SSH and putty - in windows - come in handy).

---

