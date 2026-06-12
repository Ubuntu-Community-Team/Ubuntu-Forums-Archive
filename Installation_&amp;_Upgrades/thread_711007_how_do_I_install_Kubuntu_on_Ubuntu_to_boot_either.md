---
title: "how do I install Kubuntu on Ubuntu to boot either?"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by himagain on 2008-02-29
Hi folks,
About to give up .... again.
Persisted with SUSE103 for weeks, came back to Ubuntu to try again and after a week, it still won't work properly even though the install worked out of the box!

Having problems with Gnome Synaptic especially and what may be DVD read problems with it.

I want to now try the dual desktop option and can't find out how.
I have a full install disk for it, but am not game to simply let it go.  How do you install the second one alongside Gnome?

Cheers!

---

### Post by TeslaTony on 2008-02-29
There are two ways to do that:

1) Install Kubuntu as a dual-boot system. I doubt that is what you are asking, but the install CD should let you do it pretty easily.

2) Go to Synaptic and search for kubuntu-desktop. This will download a bunch of files and take a while to install and configure, but not you'll have the option at the login window to choose either KDE or Gnome for your session. Just click session=>KDE before you log in. The only downside I've found is that when you start up or shut down your computer, you'll get the Kubuntu splash screens instead of the Ubuntu splash screens.

---

### Post by himagain on 2008-02-29
Thanks TeslaTony, (2) is just what I was looking for!

Now all I have to do is get Virtual Box into the system somehow.
(Synaptic doesn't want to know about outside sources on my system....)

Cheers!

---

### Post by banewman on 2008-02-29
Have you got all repositories enabled?
Open the synaptic package manager and click "settings" from the top menu - then "repositories" then make sure all are selected except "source.
:)

---

### Post by Jammy4041 on 2008-02-29
After you install the kubuntu desktop, can you switch between using kde (aka Kubuntu desktop) and gnome (aka Ubuntu desktop) each time?

---

### Post by himagain on 2008-02-29
> **TeslaTony said:**
> There are two ways to do that:

 you'll have the option at the login window to choose either KDE or Gnome for your session. Just click session=>KDE before you log in. The only downside I've found is that when you start up or shut down your computer, you'll get the Kubuntu splash screens instead of the Ubuntu splash screens.

Hi again,
Tried that and did get the blue KDE screen  it (flew past)but  no options and back into Gnome.

Cheers,

---

### Post by kenny1948 on 2008-05-16
> **himagain said:**
> Hi again,
Tried that and did get the blue KDE screen  it (flew past)but  no options and back into Gnome.

Cheers,

Do you get a login screen?  If so in Kubuntu there is a little drop down menu below the enter symbol. If you click it, you will get the option to choose what type of session you want Kde or Gnome. I kept missing this and going into Gnome desktop.

Likewise if you're not getting a login. Upon boot hit Esc and you will get a menu. Click on the version you want then you should get your login page. 

Hang in there. Kubuntu works great for me, once I figured out how to login.:)

---

### Post by diogenes2 on 2008-06-27
> **kenny1948 said:**
> Do you get a login screen?  If so in Kubuntu there is a little drop down menu below the enter symbol. If you click it, you will get the option to choose what type of session you want Kde or Gnome. I kept missing this and going into Gnome desktop.

Likewise if you're not getting a login. Upon boot hit Esc and you will get a menu. Click on the version you want then you should get your login page. 

Hang in there. Kubuntu works great for me, once I figured out how to login.:)

Hi Kenny,
I just got back and left a thank you as Diogenes2 - also me :-)
Now all I need is:
1. Sound to work
2. Access other Drives
3. Get the Vbox update safely installed. 
4. Find out how to add Linux Drivers for (1)

---

### Post by archat68 on 2008-06-30
I have Kubuntu both alternate disk and desktop disk. I've heard that KDe can be installed over Gnome with the help of these without downloading anything with the following command:
> sudo mv /etc/apt/sources.list /etc/apt/sources.list.nocd

sudo apt-cdrom add

sudo aptitude update

sudo aptitude install kubuntu-desktop

sudo mv /etc/apt/sources.list /etc/apt/sources.list.cd

sudo cp /etc/apt/sources.list.nocd /etc/apt/sources.list

But when I issue the commands i get:

> arup@arup-desktop:~$ sudo mv /etc/apt/sources.list /etc/apt/sources.list.nocd
[sudo] password for arup: 
arup@arup-desktop:~$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
E: Failed to mount the cdrom.

Why does mounting fails?
But I'm getting the nautilus window when i insert the CD and can browse all the files on it.

So, what to do?
Pls help.

---

