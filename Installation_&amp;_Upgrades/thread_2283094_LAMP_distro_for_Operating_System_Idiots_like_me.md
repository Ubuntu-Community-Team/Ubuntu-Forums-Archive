---
title: "LAMP distro for Operating System Idiots like me"
date: 2015-06-19
forum: Installation &amp; Upgrades
---

### Post by madman3 on 2015-06-19
_**Preamble**_ 
I'm a web developer who is also an OSI (see title) and unfortunately have to develop and test on a Windows machine.
Up until now I have been using WAMP and XAMPP as my localhost server which has been kind of adequate.
Unfortunately these solutions are somewhat outdated and fast becoming irrelevant.
One of the biggest issues is that they use the GD image handler library which is no longer supported on more and more production servers.
But getting the alternative ImageMagick installed on the above mentioned is all but impossible especially for people like myself.
So I decided to build a LAMP server on a VirtualBox just to see if the latest Ubuntu is any easier than the last Linux install I attempted.
(RedHat 1.something many many years ago - Win95 was still "the OS to use")
Here I have to say that I found the base installation of the various Ubuntu installs available a surprisingly pleasant experience.
But then the troubles started - especially when you realize that in my world Vim is a kitchen scouring product and Vi is the short name for aunt Violet and sudo became So Do in my head and I could not get anything working in the terminal until I figured it out.
I need to be able to see my local HTTP server using the Windows file explorer and the ability to FTP into it using FileZilla and EditPlus from the Windows host.
The first 15 or so VM's were all broken by me and my keyboard.
The next bunch I tried various 3rd party solutions (which all need a collage degree to get working) and the last 2 were "more or less" successful using Samba and the default FTP server and a lot of YouTube.
Except that if you create a folder using PHP, not even PHP can get into it at all, Filezilla can do nothing with it and neither can Windows Explorer or EditPlus.
(Using "ls" the new folder is BLUE which I have been told is "executable" - ?how can you execute a folder? :confused:)

_**The actual guts of the submission **_
Would it not be possible to have the more intelligent members of the Ubuntu community put together a distribution as follows:
[LIST=1]
[*]A stripped down "base" installation (no GUI) specifically for use in VirtualBox. 
[*]Latest versions of Apache, PHP (plus MODERN add on's), MySQL as standard. 
[*]Samba. 
[*]FTP server. 
[*]phpMyAdmin 
[*]Whatever is the easiest to use server maintenance utility for use by a browser on the host. 
[/LIST]

The installation process should do the following:
[LIST]
[*]Ask for the IP to use. 
[*]The "domain name". 
[*]The gateway IP. 
[*]One password to be used everywhere. (Yes, I know, Security - but this a dev environment, NOT production or in house) 
[*]Install everything else that is needed to get the system fully capable of doing what it needs to do. 
[*]Set everything up correctly so that it works properly "out of the box". 
[*]All permissions, user groups, users and all the other good stuff done. 
[*]Samba and FTP to go directly to the HTML storage area. 
[*]Set up Apache, MySQL, Samba and everything else to deny requests from IP addresses not in the "192.168" range. 
[*]A "help.html" script in the server root (not able to be edited or deleted would be nice!) with links to phpMyAdmin, the PHP/HTML based  server management utility and whatever else can be used for admin purposes from a browser on the host system. (I can contribute the page). 
[/LIST]

As the installation target is a VirtualBox, all the extra "in case" stuff can be left out of the distro which should make it super light.
Another plus point is that non Ubuntu users will use it and possibly become "converts".

I'm new to this forum, don't know if this is the right place for this suggestion, maybe the Ubuntu management would approve something like this, maybe it should be done off domain, maybe it will be still-born but its definitely worth a try from my perspective.

---

### Post by dino99 on 2015-06-19
a quick search point me to : [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) , hopes it can help a bit :p

---

### Post by Lars Noodén on 2015-06-19
Welcome. 

The link dino99 gave will get you started with Linux-Apache2-MySQL-PHP/Perl/Python.  Perl and Python are already included in the base installation.  By default you get set up with a single virtual host (web site) in Apache2.  By default place for this is in /var/www/ and your web pages go in /var/www/html/ but the permissions are left unset because they depend on your use case?  Will you be the only developer on the system?  If so then you can just take ownership of the directory and anything under it.  

```

sudo chown -R madman3:madman3 /var/www/html

```

If you are sharing access with other developers then some other steps are needed.  But they are easy.

> **madman3 said:**
> 
I need ... the ability to FTP into it using FileZilla ...


You probably [don't want FTP in 2015](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) and I would recommend avoiding it.  If you are using FileZilla, you can use SFTP instead.  You get SFTP as part of the package openssh-server and it will run out of the box.  You can do fancier tricks like locking specific users to particular directories and disallowing shell access, but [authenticating with keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) is considered best practice for any publicly facing system.

Ask along the way as needed.

---

### Post by madman3 on 2015-06-19
That is the process I followed early in this saga - somehow I did something that prevented it from booting on a restart !!!
What I proposed is a dedicated distro that does all the setup stuff automatically.
Some people can cook, some people can sing, put me in a terminal and it is a disaster.
Thanks for the comment though

---

### Post by madman3 on 2015-06-19
Hi Lars
I have a funny feeling that the "chown" command has caused at least one, probably more of my many fails.
As far as FTP is concerned, I bow to your knowledge.
However this is making my point that all the "right" packages should be installed and set up by the install.
Idiots like me should not have to get our sticky fingers in there because that is (in my case anyway) a disaster every time.
As an example I have just crashed installation 26 trying to set the server domain name.
(it now says "Waiting for up to 60 seconds...." ---- done it again !!!)
Fortunately I made a copy of the VirtualBox image and used that for this session.
Now I can just delete the crashed one and make another copy to carry on with.
But this sort of experience at the beginning of someone's Ubuntu journey will probably scare them off.
The aim here is to get the new users hooked by giving them something that they need desperately without all the "terminal" pain.
That can come later.

---

### Post by Lars Noodén on 2015-06-19
Yes a VM is definitely the way to go, taking snapshots along the way.  I'm not sure I can overcome in a few words the years and millions of dollars MS has spent disparaging the shell.  They've fought it because it is so flexible and powerful and even today they don't have anything close.  It's basically a fully functional programming language / environment.  But for me, one of the big selling points is that you can work remotely or locally using the same methods, one one server or thousands.  Another point, it's very consistent across distros and versions and lends itself very well to written instructions and recipes.  About the programming, anything you do via the shell is scriptable, since you are writing a script one line at a time, and thus can be automated.  I guess it is this latter you would like.  But the devil is in the details so it is hard to make a generic solution since needs are different and there is a bit of a chicken-and-egg problem with regards to knowing what is possible/needed and knowing how to do it.  I guess you're at that hard junction right now.  

At what step are you right now?  Is the web server showing you web pages when you look at it with the browser?  Can you edit web pages via the console?  If so, then the next step is using FileZilla with SFTP to do so.

---

### Post by madman3 on 2015-06-20
Hi Lars
I'm now on the 36th VirtualBox VM in my journey to get a home LAMP server up, running and usable.
If I was doing all of this on a "real world" PC I would have given up long ago but an VirtualBox you simply set up a new box, start the installation, go get some tea and then carry on.
> A BIG TIP: Once you have gone through the initial setup and the updating of the base installation, _**MAKE A CLONE**_ and carry on with the clone. That way if you break it you can delete it and make a clone of the original and start again.
The good news is that #36 is usable for the most part.
Had an almighty battle getting Filezilla and EditPlus able to save scripts to the server folder.
The bad news is that I forgot to note what I did to get the permissions sorted out so that it worked.
More bad news is that I have not yet been able to get ImageMagick installed and working on PHP.
I have a suspicion that I have not put the necessary script into some folder that PHP uses to store references or other stuff.
But I will get there eventually.
> UPDATE: sudo apt-get install php5-imagick and sudo service apache2 restart is all it took !!!

---

### Post by madman3 on 2015-06-20
Hi Lars
I'm now on the 36th VirtualBox VM in my journey to get a home LAMP server up, running and usable.
If I was doing all of this on a "real world" PC I would have given up long ago but an VirtualBox you simply set up a new box, start the installation, go get some tea and then carry on.
> A BIG TIP: Once you have gone through the initial setup and the updating of the base installation, _**MAKE A CLONE**_ and carry on with the clone. That way if you break it you can delet it and make a clone of the original and start again.
The good news is that #36 is usable for the most part.
Had an almighty battle getting Filezilla and EditPlus able to save scripts to the server folder.
The bad news is that I forgot to note what I did to get the permissions sorted out so that it worked.
More bad news is that I have not yet been able to get ImageMagick installed and working on PHP.
I have a suspicion that I have not put the necessary script into some folder that PHP uses to store references or other stuff.
But I will get there eventually.

---

### Post by Lars Noodén on 2015-06-20
VM snapshots / clones are definitely a time saver and make experimentation convenient.  

When working with web services there is a useful utility called [tail](http://manpages.ubuntu.com/manpages/trusty/en/man1/tail.1.html) which allows you to monitor the tail end of the error logs live.  If you open a new terminal window, and maybe make it a little taller, then you can run the following to watch your Apache2 logs.

```

tail -f /var/log/apache2/error.log

```

Then you can try running your scripts and watching what shows up over in the terminal.

---

