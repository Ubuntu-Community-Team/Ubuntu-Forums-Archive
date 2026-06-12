---
title: "Just can't get VMware Server to install"
date: 2006-07-19
forum: Installation &amp; Upgrades
---

### Post by underdog512 on 2006-07-19
I have tried many different sets of directions in an attempt to install VMWare server to install but I just seem to get it to work.  On my last try, the vmware-installer.pl wouldn't even run, the error message being only one word "[FAILURE]"

What is going on here? 

Is there another proven virtualization software available, perhaps through synaptic?

---

### Post by llamakc on 2006-07-19
I used qemu and successfully started up a Gentoo image I grabbed from oszoo.org.

---

### Post by Hotwhlz85 on 2006-07-19
Underdog I just successfully installed VMware tonight after struggling with it last night.  Here's an excellent how to:

[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware)

One thing I noticed last night was I kept getting errors even with pasting the codes that Peturrr supplied.  Not sure if it was my machine that was tired or me.  Tonight it installed perfectly although I am having problems installing a guest OS.

Good luck.
Ron

---

### Post by underdog512 on 2006-07-20
This is my output from the terminal when I try to install.... 


root@Ubuntu01:/home/amobley/vmware-server-distrib# ./vmware-install.pl
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/home/amobley/vmware/vmware-uninstall.pl.

Failure

Execution aborted.



could it have somthing to do with my previous attempts to install it?

---

### Post by Hotwhlz85 on 2006-07-20
That would be my guess.  I got the same error and decided it was from my earlier failed attempts as well.  Peturrr gave a code for removing that, I've copied and pasted it here:

sudo rm -R /etc/vmware

Entering that doesn't appear to do anything since the next thing you see will be your command line prompt.  When I got that I started all over and followed Peturrr's how to exactly and it worked.

Good luck.
Ron

---

### Post by underdog512 on 2006-07-21
What do I do about this?

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]     


I am so close!!!

---

### Post by underdog512 on 2006-07-24
Anybody out here?

---

### Post by bobosity on 2006-07-24
Do a search for vmware in the forum. I just went through this and found there are several threads on the subject.

---

### Post by snellgrove on 2006-07-24
> **underdog512 said:**
> What do I do about this?

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]     


I am so close!!!


What you do here, is the following:

```
sudo apt-get install linux-headers-`uname -r`
```

you may have these already, but its worth typing the above in anyways, doesn't do any harm :)

then during that vmware configure thing, and it asks about /usr/src/linux/include you want to open another terminal, and type in the following:

```
uname -r
```

this will tell you what kernel version you are running.. for example, mine is:

2.6.15-23-386

then back in the vmware terminal, **I** would type in the following:

/usr/src/linux-headers-2.6.15-23-386

but you type in what *your* kernel comes back as.

its always /usr/src/linux-headers-*and then your kernel version number*

---

### Post by underdog512 on 2006-07-25
Thanx dude!!  That helped!!  IT WORKS!!!!!!!!!!

---

