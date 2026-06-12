---
title: "Installing 7.10 Server on VMPlayer"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by prodonjs on 2007-11-15
I am trying to set up an FTP server using Ubuntu Server 7.10 hosted on a VMWare virtual machine as part of a class project. I've worked with Ubuntu desktop before and figured that the installation process would be fairly straight forward. My only goal for tonight was to just get the OS installed and then worry about the configurations for specific services later. However, I went through the installation process from the CD and found a number of difficulties.

When I restarted the OS after the installation, I got the message "Panic: CPU is too old for this kernel". I did some digging and found something about PAE support, but I could not find anything about VMWare Player 2.0 specifically dealing with.

I was hoping to find out if anyone else has successfully gotten Ubuntu Server 7.10 to run on VMWare Player and if so, how they did so. I saw some articles about uninstalling the linux-server kernel and installing a generic kernel, but when I followed those I got package dependency errors even though I follow the correct ordering of steps to install the new kernel images and then remove the old server images.

Basically, is there a way to get this working outside of some nasty, work-around solution?

---

### Post by RikardSvenningsen on 2007-11-27
I got same problem under VMWare Workstation 6.0.1 and 6.0.2
Se attached file

Best regards.
Rikard Svenningsen
Danmark

---

### Post by prodonjs on 2007-11-27
Well, I'm not sure how your problem will be resolved but I can tell you what fixed mine. I am using a relatively old laptop (3 years) with an Intel Pentium M Centrino processor. The particular core of my processor does not support PAE (physical address extension) which is what the linux-server kernel is complaining about.

Now there is an option in the VMX configuration that lets VMWare try to virtualize this, but I believe it's not possible to do this if your phsyical processor does not support PAE. I did some digging on Google and found similar posts talking about the fact that the Centrino Dothan cores, which is what I have, do not support it.

So I found that I couldn't use the server kernel. I did found a very useful resource though that helped me to recover my Ubuntu Server installation by removing the server kernel and installing a generic kernel.

I think you'll find it helpful.

[http://paul.annesley.cc/articles/2007/05/01/ubuntu-704-feisty-server-parallels-cdromkernel-workaround](http://paul.annesley.cc/articles/2007/05/01/ubuntu-704-feisty-server-parallels-cdromkernel-workaround)

---

### Post by RikardSvenningsen on 2007-11-28
I have now tried it. It didn't help me.
The only difference I got when I tried was that it couldn't find the linux-image-2.6.20-15-server

So still not working.

Best regards
Rikard Svenningsen

---

### Post by prodonjs on 2007-11-29
Oops, I apologize for not specifying that the fix was for Ubuntu Server 6.10 Feisty Fawn, not Gutsy Gibbon.

The kernel version will not 2.6.20.15.

You can find the version of your kernel by looking into the looking into the /boot directory I believe, or better yet you can do something like this.

sudo apt-get remove linux-server-kernel-$(uname -r)

And the $(uname -r) command subsitution will replace that string with the version of your kernel. I believe that solution will work.

---

### Post by RikardSvenningsen on 2007-11-30
I found that some body else got the same problem: CPU too old...
For me the solution was do as in this link:

[http://tombuntu.com/index.php/2007/09/05/making-ubuntu-server-work-in-virtualbox/](http://tombuntu.com/index.php/2007/09/05/making-ubuntu-server-work-in-virtualbox/)

---

### Post by Tichondrius on 2007-12-24
wa....wa....wa

Why bother with virtualbox when vmplayer is free. 
It's beyond simple to set up a ubuntu server running in vmplayer.

Step 1 - Install vmplayer (latest version) - it's free from vmware.
Step 2 - Go to vmware's virtual appliance page, and download Ubuntu 7.10 JEOS image 
  (it's optimized for running in a virtual environment)
Step 3 - unzip the Ubuntu image, and double click on the VMX file to fire it up in vmplayer.
Step 4 - done, your Ubuntu server is now running. You can log in with username "user",
  password "user"

Note this image of Ubuntu does not have X-windows and many of the server packages. You can install them using apt-get as usual. Alternatively you can use a different virtual appliance - the Ubuntu 7.10 desktop image.

For development purposes, I think the JEOS image is the best to start with, and then I installed SSH, MySQL, Apache and anything else I want. I only SSH to login to the Ubuntu server running in vmware, I don't use or need the terminal screen or an X-desktop.

Got it ?

---

