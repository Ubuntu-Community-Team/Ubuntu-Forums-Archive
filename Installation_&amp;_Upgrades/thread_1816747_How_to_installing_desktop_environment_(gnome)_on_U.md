---
title: "How to installing desktop environment (gnome) on Uuntu server 11.04?"
date: 2011-08-02
forum: Installation &amp; Upgrades
---

### Post by amin_eshgh on 2011-08-02
Hi I install ubuntu server 11.04 
I select ubuntu server from boot menu then enter username and password and then i see a command line  line and a black background 
How i can setup a graphical app (some thing like genome) for my server I do not know any thing :confused:
Any body can explain all step of this for me how I connect to internet how download graphical app and install it?
(I connect to web with windows 7 and adsl internet)

---

### Post by MAFoElffen on 2011-08-02
> **amin_eshgh said:**
> Hi I install ubuntu server 11.04 
I select ubuntu server from boot menu then enter username and password and then i see a command line  line and a black background 
How i can setup a graphical app (some thing like genome) for my server I do not know any thing :confused:
Any body can explain all step of this for me how I connect to internet how download graphical app and install it?
(I connect to web with windows 7 and adsl internet)
First >> Decide what the purpose of your Ubuntu *Install* is for...  

The server kernel is optimized for background scheduling of services.  The desktop kernel is optimized for realtime interactive services that occur when a user is present causing things to happen in a desktop environment (the foreground).

The Server Edition will run a desktop environment and the Desktop Edition will run Server Services... The big difference again to where the performance is optimized for, understanding that there will drawbacks leaning towards what it is optimized for.

The desktop package in order of resources used are:
lubuntu-desktop, xubuntu-desktop, ubuntu-desktop and kubuntu-desktop

 - If your choice is for Server services with a desktop:
Then you are going to want something light, which isn't going to use much resources in it's overhead.  If this is what you want, install via apt-get... using lubuntu-desktop, xubuntu-desktop, ubuntu-desktop or kubuntu-desktop (substituting the package for *package_name*) in the following format:
```

sudo apt-get install *package_name*

```Most Server Edition users, if for some reason - installing a GUI for admin, are going to lean towards Xubuntu, Lubuntu, then Ubuntu...  

There is one drawback.  At the end of the install, it's going to remap/update the kernel to the GUI. What that means to you is that you will have to create a 40_custom grub file with an entry with a text kernel boot option to be able to get back to a "classic server" text console session... otherwise, all the boot options will want to boot in an Xsession as a default.

---

### Post by calisun on 2011-08-02
> **amin_eshgh said:**
> ....
How i can setup a graphical app (some thing like genome) for my server I do not know any thing :confused: ...



At this point you need to STOP! and know what you are doing.
Installing a graphical app on the server is a big security issue, you will be hacked!

If you do not know what you are doing, try using a version that is designed for ease of use. Following version does not have a graphical interface, but it does have web based interface which is much more secure, done for you by experts, and is based on ubuntu:
[http://www.zentyal.org/]("http://www.zentyal.org/")

Another option is to install web based interface yourself on ubuntu server you already have installed:
[http://www.webmin.com/]("http://www.webmin.com/")
But I would not recommend this for you since you are new to linux, you will have a hard time with installation and security issues. So for you I would recommend getting already pre-configured server with web interface, which will make your life easier.   

Besides zentyal which I mentioned earlier, which is based on Ubuntu, here are other linux server distributions that include web interface. They are not ubuntu based, they are all based on Centos (aka: Redhat Enterprise Linux):
[http://www.clearfoundation.com/]("http://www.clearfoundation.com/")
[http://www.blueonyx.it/]("http://www.blueonyx.it/")
[http://wiki.contribs.org/Main_Page]("http://wiki.contribs.org/Main_Page")

---

### Post by MAFoElffen on 2011-08-03
> **calisun said:**
> At this point you need to STOP! and know what you are doing.
Installing a graphical app on the server is a big security issue, you will be hacked!

Since I've been involved with X-Windows since my early days working for govt projects under DEC systems in 1988...I'm trying to understand how installing a graphical desktop manager (XDM, GDM. LXDM, XDM. KDE) to an existing graphics layer involves a security risk and creates a security issue(?)  

I really would like to hear that one.  You know that the text console of thee Server edition is still a aubergine "text" console session (vga)? Explain how you think the text console session (tty1 thru tty6) or graphical console session (tty7 thru tty10) of Xorg... is a security risk(?).  I really am open minded, learn somethiing new every day and have a very twisted sense of humor.

Ubuntu (debian based), whether the Server or Desktop Edition, is on the same base, subject to the same security layers, access, rights and privileges.  As this "new" user is installing a Server Edition box in, most likely, a home network environment, where this server would probably have no access from outside that network... Does that make sense that creating an outside port to that didn't exist before, may not be as safe as where no-outside ports existed?

There are ports he could lock down, that are not being used... but those same posts would be there, listening, whether he had a graphical desktop... or if he had the Desktop Edition installed, with server services installed. 

How would connecting and creating an outside connection to a web-based admin tool be more secure than him keeping local access while he learns to administer his own local server?  I explained the performance issues and drawbacks.... But for someone starting out and learning-by-doing... the load he's going to have / he's not going to even notice.

I'm thinking what he is doing - is not mission critical, but rather a home-based, "give me these abilities" kind of thing.

The question was "is it possible" and "how"... In our "own opinion."  We both gave him that,  For allot of people, this is a hands-on learning process.  That's how I learned and continue to learn.

---

### Post by calisun on 2011-08-03
Security?
More open ports to worry about, yes, for an experienced linux user that is no issue. All they have to do is This..and..this..and..this  and system is secure, but for unexperienced user that could be a daunting task and many times it is not done simply from not understanding the system.
Also, see this:
[http://theinvisiblethings.blogspot.com/2011/04/linux-security-circus-on-gui-isolation.html]("http://theinvisiblethings.blogspot.com/2011/04/linux-security-circus-on-gui-isolation.html")

You mentioned that MAFoElffen will learn by doing it. A simple web search reveals many..many tutorials on how to install it, so it looks like he is looking for a "simple" solution. That is why I suggested other distros that are geared to what he is looking for.
Not every linux distribution is best for everything, just like there are many cars (Trucks, sports cars, buses) so each linux has its own purpose, and Ubuntu server is not for everyone.
Also, like you mentioned that MAFoElffen is only looking for a home server, there is a linux version for that also. All the versions I have mentioned earlier, I have used them all as my home server, and they worked great. There is also a distro especially designed as a home server, which I have not tried yet, but I have heard great things about it.  It is:
[http://www.amahi.org/]("http://www.amahi.org/")

Don't get me wrong, I believe knowledge is power, but some people treat computers as a passion, and others treat it a only a tool to accomplish other things, and they don't care how it gets done.

---

### Post by MAFoElffen on 2011-08-03
> **calisun said:**
> You mentioned that MAFoElffen will learn by doing it. A simple web search reveals many..many tutorials on how to install it, so it looks like he is looking for a "simple" solution. That is why I suggested other distros that are geared to what he is looking for.
Not every linux distribution is best for everything, just like there are many cars (Trucks, sports cars, buses) so each linux has its own purpose, and Ubuntu server is not for everyone.
Also, like you mentioned that MAFoElffen is only looking for a home server, there is a linux version for that also. All the versions I have mentioned earlier, I have used them all as my home server, and they worked great. There is also a distro especially designed as a home server, which I have not tried yet, but I have heard great things about it.  It is:
[http://www.amahi.org/](http://www.amahi.org/)

Don't get me wrong, I believe knowledge is power, but some people treat computers as a passion, and others treat it a only a tool to accomplish other things, and they don't care how it gets done.
@calisun-- Switch my monicker "MAFoElffen" for "amin_eshgh" and you have the particular new user who is trying to use Server Edition for what he hasn't mentioned yet.  (I assumed as a home server or his experience level would be a little higher.)

MAFoElffen is "me." Computers are one of my passions. Another is helping users, trying to fix things and making things work that others say shouldn't..  That's why I have this sticky here:
**[B]Sticky:**[/B]                         [COLOR=#008C00]**[all variants]**[/COLOR] [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535") 
and maintain some Android ROMs for PDA Phones...  With those, I'm having fun... With the "manuals' Ubuntu staff want me to write for them, that almost sounds like work...  Not sure what to tell them on that yet.  Maybe this Winter when things slow down some.

---

### Post by calisun on 2011-08-04
> **MAFoElffen said:**
> @calisun-- 
MAFoElffen is "me." 

OOOPS, sorry, for mixing up the names, I just copy/paste without double checking that I copied the correct name :lolflag:

And thanks for having a passion for helping people out on this forum, people like you is what makes this forum work =D> 

And I like what you said:

> **MAFoElffen said:**
> making things work that others say shouldn't.. 

I also believe in that, if we listened to all the nay-sayers [-X we would still be in the stone age. :frown:

thanks and Good luck.

---

