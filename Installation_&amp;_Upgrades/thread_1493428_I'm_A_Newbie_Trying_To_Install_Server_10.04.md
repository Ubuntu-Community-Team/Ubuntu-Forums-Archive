---
title: "I'm A Newbie Trying To Install Server 10.04"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by Orange Worker on 2010-05-25
Hi,
 
I'm trying to install Ubuntu Server 10.04 (32 Bit), but my computer is not booting from the disc for some reason. I've burned a data CD and configured my bios to boot from CD.
 
I've also tried selecting all boot devices to CD, but then I get a screen that asks me to insert a disc (I don't have that exactly right, but it's something along the lines of that)
 
Thanks,
Henry
 
:guitar:

---

### Post by oldos2er on 2010-05-25
You need to burn the *iso file as an image, not data. See [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Orange Worker on 2010-05-26
Thank you, that worked.

---

### Post by Orange Worker on 2010-05-26
I would rather use a GUI interface, does this mean that I have to install the destop version as well? If so, which version should I install first? I realize that I'm probably going to have to install this a bunch of times before I get it right. Thanks for all the help.
 
Henry

---

### Post by wkulecz on 2010-05-26
IMHO the server install download should warn its not for "newbies".

Install the destop OS and then use synaptic package manager to install the server components you need nfs, postfix, apache, etc.

You'll have a good GUI environment to install from and work with.  Having the Live CD option will come in handy if you need to fix boot (Grub2) issues.

You turn the desktop version into a server by installing the server packages you need.  If its a heavy use server you may want to install the server kernel, but there is no benefit I'm aware of to installing both on the same machine.

---

### Post by Orange Worker on 2010-05-26
Thank you for your reply. Is the "synaptic package manager " something that is included in the OS, or is it a seperate download?
 
I'm looking to run an application created with PHP.

---

### Post by Orange Worker on 2010-05-26
I've installed Ubuntu Desktop 10.04 and it couldn't have been any easier. I've also checked out the "synaptic package manager" and I believe that Apache and the software I need is already installed to use it as a server. So my question is, where do I need to store my PHP files?

When I had Windows Server 2003 and WAMP installed, my PHP files were in a folder called "www" which I believe was located at C:\wamp\www

Thanks for the help; it's greatly appreciated.

Henry

---

### Post by SlidingHorn on 2010-05-26
basically if you simply do the following, everything should install on its own:

```
sudo apt-get install apache2 [color="Red"]I believe you already did this[/color]
sudo apt-get install php5-mysql
sudo apt-get install libapache2-mod-php5
sudo apt-get install mysql-server
```

or, if you're running Ubuntu 7.04 or later, you can do this with tasksel by the following:

```
sudo tasksel install lamp-server
```

Hope this helps!

---

### Post by Orange Worker on 2010-05-26
Sliding Horn,

Thanks for sending the code to upgrade to LAMP, it worked. Could you tell me which folder I need to put my PHP files into and will this folder be located somewhere in "File System" ?

Thanks,
Henry

---

