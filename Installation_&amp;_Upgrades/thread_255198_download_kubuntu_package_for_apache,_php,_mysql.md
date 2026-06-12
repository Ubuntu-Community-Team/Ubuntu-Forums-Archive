---
title: "download kubuntu package for apache, php, mysql"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by tjules on 2006-09-11
where can i download kubuntu packages for apache, php, mysql?

I downloaded those packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) but when I executd the command " sudo dpkg -i [package].deb" i obtained errors messages saying that the package connot be installed because of some dependencies problems... sam thing for the other packages...

---

### Post by BoneKracker on 2006-09-11
Read the stickies in the beginner forum.  There is one about installing software.

Also, fully explore the top 3 items under the System menu where it says "Help".


This isn't windows -- you don't need to download and install software manually unless it's something that's not in our repositories (and those packages are all in our repositories).

What you do is go to System > Administration > Synaptic Package Manager and search for the software you want, then just check the box next to it and click "apply".  It gets installed automatically, and much more importantly, it will get updated automatically.  Also important, it's easy to safely and cleanly remove packages.  If you install things manually, you'll probably get your system all mucked up like your Windows box used to be.

If you're comfortable with the command line and you know the name of the package you want, you just type, for example:

sudo apt-get install blahblah

---

### Post by tjules on 2006-09-12
I assume that for both synaptic and the command suo apt-get install I need to have an internet connection.  However, i cant connect to the internet under kubuntu.. That's why i am looking for kubuntu predefined packages... any idea where i could get those pakages?

---

### Post by BoneKracker on 2006-09-13
Okay, so I guess you have an internet connection on another computer, but not this one.

Here's what I would do.  Two options.

A) You should get it connected to the internet, at least for the install.  This way you can get the updated software and get what you want on there without trouble.

B) If you can't get it connected, then you COULD try the following (no guarantees this will even work):

1.  Download the iso files and burn cdroms for BOTH ubuntu server and kubuntu.

2.  Boot the server cd, and select the option to install a LAMP server (that sets up Linux, Apache, MySQL, PHP, Perl, Python).  But I don't think that cd contains X11, and it surely doesn't contain KDE.

3.  Get your new server system booted up.

4.  Insert the Kubuntu disk.

5.  Edit the file /etc/apt/sources.lst.  You'll find there's a line in there pointing to the cd you used to install server.  You'll have to figure out what that line should look like to make it point at the Kubuntu disk.

6.  Do an apt-get install kubuntu-desktop.  It should use the cd as it's first source and only try to go the internet for updates or stuff it can't get from the cd.

7.  If that works, and you really wanted all that stuff but NOT a kernel optimized for server, you could also replace the kernel.

---

