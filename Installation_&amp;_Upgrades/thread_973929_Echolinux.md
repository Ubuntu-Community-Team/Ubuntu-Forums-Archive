---
title: "Echolinux"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by vk3nay on 2008-11-07
Hi there. I am new to ubuntu, and finding a lot different to other platforms to use. If any one could assist me with the installation of a Ham radio program called _Echolinux_ First off i have downloaded and installed the Ubuntu update. The problem that i am having with Echolinux is that i have downloaded it to the desk top, But i cannot get it to install.
If there is any other amateur operator that has installed this software and any problems that they have had with it. Many thanks, Brian.

---

### Post by umechanism on 2008-11-15
Brian,

Did you get Echolinux installed?  Your post is almost a month old but I thought I would check to see anyway.  

RPM files are not at all like Windows .exe files.  Double clicking on an .rpm file will probably do nothing inside Ubuntu because Ubuntu's version of an ".exe" file is the ".deb" file.  So, what you have is an ".rpm" file but you need a ".deb" file.  There is a program called "alien" that can covert the .rpm into a .deb format for you.  I found [these links]("http://http://www.google.com/search?q=how+to+install+rpm+in+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a") using Google.

73
Mike
KE5HJO

---

### Post by n3gbz on 2008-11-24
I am able to run Echolink successfully using wine.  

After converting Echolinux with alien and installing the .deb output Echolinux will run but not connect yet.  Will update on my progress.

73 de n3gbz

---

### Post by n3gbz on 2008-11-25
Echolinux is now working properly on my Ubuntu 08.04 system- 

My servers.txt file needing be corrected was the last hurdle. Here it is:

> y@mach-01:/etc/echolinux$ cat servers.txt
nasouth.echolink.org
naeast.echolink.org
servers.echolink.org
backup.echolink.org

I had to use the ip address of the remote station to connect.  I found that by using echolink and clicking on the station info for the desired station.  Both the command line and the echogui versions of Echolinux are working. 

Going back to the initial question, I did have to convert the rpm version to a .deb and then install the .deb version.  Using the alien -i option would not work.

> sudo alien --to-deb echolinux-0.17a-1.i386.rpm

73 de n3gbz

---

### Post by pizza-is-good on 2009-06-25
Im somewhat new to Ubuntu
I installed Echolink using WINE. I can hear and connect to stations, but mic is not working, and nothing I do in the Echolink settings will work.
Any ideas?
 
73 and thanks

---

### Post by Alnico on 2009-07-17
Have you tried connecting an external microphone? Also check your firewall settings to allow UDP connections.

73

---

### Post by piju on 2009-08-26
i think u can install alien and convert the rpm file to deb file.

dont forget to apt-get -f install.

have u tried qtel on ubuntu ?




73 DE 9W2PJU K

---

### Post by piju on 2009-09-08
> **pizza-is-good said:**
> Im somewhat new to Ubuntu
I installed Echolink using WINE. I can hear and connect to stations, but mic is not working, and nothing I do in the Echolink settings will work.
Any ideas?
 
73 and thanks

You need to enable port forwarding first.
please allow all the necessary ports.

im using P1 Wimax in Malaysia, so this is my configuration for my router.

[http://9w2pju.blogspot.com/2009/09/echolink-using-p1-wimax-for-malaysian.html](http://9w2pju.blogspot.com/2009/09/echolink-using-p1-wimax-for-malaysian.html)

---

### Post by piju on 2009-09-08
> **n3gbz said:**
> I am able to run Echolink successfully using wine.  

After converting Echolinux with alien and installing the .deb output Echolinux will run but not connect yet.  Will update on my progress.

73 de n3gbz

yes, sure. echolink on wine works perfectly.
and im loving it

---

### Post by lz5pn on 2010-05-09
First look this [http://www.chrisronk.net/ham/linux.htm](http://www.chrisronk.net/ham/linux.htm) 

Download packages from [http://www.chrisronk.net/ham/qtel-debian.tar.gz](http://www.chrisronk.net/ham/qtel-debian.tar.gz) or [http://lz5pn.homeip.net/lz5pn/echolinux/qtel-debian.tar.gz](http://lz5pn.homeip.net/lz5pn/echolinux/qtel-debian.tar.gz). 

Unpack and install them in this order :
1 echolib_0.13.0-2_i386.deb
2 libasync_0.16.0-2_i386.deb
3 libsigc++1.2-5_1.2.7-2_i386.deb
4 qtel_0.11.0-2_i386.deb

Then start qtel. 

[IMG]http://lz5pn.blog.bg/photos/75096/pic.png[/IMG]

[IMG]http://lz5pn.blog.bg/photos/75096/pic1.png[/IMG]

This worked on Ubuntu 10.04 i386 installed on eee pc 701.

:guitar:

73 de lz5pn

---

### Post by Steve440 on 2010-05-23
Can you install sounds into Qtel ?  I am running it on a 32 bit machine with Ubuntu 9.10.  
  Thanks

---

### Post by piju on 2010-06-23
i havent successfully installed qtel or echolinux on my system.
is there anybody port it to the PPA ?

---

### Post by dwmurray57 on 2010-06-25
Good Evening,

I've installed the .deb files posted by **lz5pn** (thank you for those).  I didnt get any errors during the install but Qtel will not start up.

I am running Ubuntu 10.04 on EeePC as well.  The only thing (it might be the 'big' thing) but I did the install as myself (not SU).

Any suggestions?  

Thank you in advance

73's de VA3MDW

---

### Post by ke4obt on 2010-08-09
Hey All.

My wife and I share a dual core gateway laptop with 3Gb of ram.
We've installed QTel and it seems to be working about halfway so far.
She can see the list of users and I can see her on line from a different computer  but can't connect to her and vice versa.
  For my wife with the stock QT based GUI it will be fine but for myself and several other hams using Ubuntu 10.04 converted to [Vinux]("http://vinux.org.uk") this will not work as QT based apps and Gui's are not accessible to screen readers at this time, but is being worked on.
So lets take this one step at a time and get her conected through voice to begin with.
Any and all help will be greatfully accepted.

TNX,

---

### Post by lz5pn on 2011-05-07
> **lz5pn said:**
> First look this [http://www.chrisronk.net/ham/linux.htm](http://www.chrisronk.net/ham/linux.htm) 

Download packages from [http://www.chrisronk.net/ham/qtel-debian.tar.gz](http://www.chrisronk.net/ham/qtel-debian.tar.gz) or [http://lz5pn.homeip.net/lz5pn/echolinux/qtel-debian.tar.gz](http://lz5pn.homeip.net/lz5pn/echolinux/qtel-debian.tar.gz). 

Unpack and install them in this order :
1 echolib_0.13.0-2_i386.deb
2 libasync_0.16.0-2_i386.deb
3 libsigc++1.2-5_1.2.7-2_i386.deb
4 qtel_0.11.0-2_i386.deb

Then start qtel. 

[IMG]http://lz5pn.blog.bg/photos/75096/pic.png[/IMG]

[IMG]http://lz5pn.blog.bg/photos/75096/pic1.png[/IMG]

This worked on Ubuntu 10.04 i386 installed on eee pc 701.

:guitar:

73 de lz5pn

Here [http://charlessocci.com/2010/07/06/echolink-qtel-client-ubuntu-10-04-64-bit/](http://charlessocci.com/2010/07/06/echolink-qtel-client-ubuntu-10-04-64-bit/) I found information how to install echolinux in Ubuntu 10.04 
I collect all files in one package and write short howto for this that I do.
Package available on my server [http://lz5pn.homeip.net/lz5pn/echolinux/qtel-debian.tar.gz](http://lz5pn.homeip.net/lz5pn/echolinux/qtel-debian.tar.gz) 
I replace old package whit new but name is same.
Will be good idea if some one who know more than me in programming do something (made one complete package for installing whit one click) and upload them on another server and post here where is this uploaded.
Also will be good idea Ubuntu made something to include this software in their distribution or servers.
This will give chance radio-amateurs install and use ham software easy in Linux.
73 de lz5pn

---

