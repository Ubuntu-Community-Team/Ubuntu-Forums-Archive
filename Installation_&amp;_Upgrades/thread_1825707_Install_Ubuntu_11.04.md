---
title: "Install Ubuntu 11.04"
date: 2011-08-15
forum: Installation &amp; Upgrades
---

### Post by Montezuma45 on 2011-08-15
I'm trying to do a simple install.  Wipe out existing system and replace with 11.04 but I can't get past initial screen.  Is there a different CD version I need to use?

Last year I used 10.04 LTS and it worked fine, this year I wanted to start with the newest and go from there.  I use Remastersys to make my own install version for 600+ laptops and I need to be able to wipe out the existing systems without effort.

---

### Post by infamous-online on 2011-08-15
> **Montezuma45 said:**
> I'm trying to do a simple install.  Wipe out existing system and replace with 11.04 but I can't get past initial screen.  Is there a different CD version I need to use?

Last year I used 10.04 LTS and it worked fine, this year I wanted to start with the newest and go from there.  I use Remastersys to make my own install version for 600+ laptops and I need to be able to wipe out the existing systems without effort.

Hmm try this out, run it as a live demo if you have it on that custom build that you made, and from there click on the install option and see if that helps.

---

### Post by Montezuma45 on 2011-08-15
I got past that but not good for mass production.  Apparently it needed so much free disk space to run.  Booting from the CD, I just deleted some folders and it allowed me to continue.  I now have it installed on one laptop.

I need to know, is this unique to me or SOP?  Doesn't the installation program ask if you want to delete the whole disk or have a dual operating system, like 10.04 LTS did?  I'm not looking forward to have to initialize disk before installing on 600+ laptops this year.

---

### Post by yuzhongfeixia on 2011-08-15
> **Montezuma45 said:**
> I'm trying to do a simple install.  Wipe out existing system and replace with 11.04 but I can't get past initial screen.  Is there a different CD version I need to use?

Last year I used 10.04 LTS and it worked fine, this year I wanted to start with the newest and go from there.  I use Remastersys to make my own install version for 600+ laptops and I need to be able to wipe out the existing systems without effort.
i installed unbuntu,but i find that it has no make and gcc command

---

### Post by bigcreturns on 2011-08-16
I posted this in another thread in regards to installing VMware tools.

Ensure for 11.04 server edition you have: make, gcc and the linux C header files installed.

sudo apt-get update

sudo apt-get install make

sudo apt-get install gcc

Then enter: 
uname -r

My kernel was: 2.6.38-10-generic

sudo apt-get install build-essential linux-headers-**2.6.38-10-generic**

Now run the vmware-install.pl script.

---

### Post by Montezuma45 on 2011-08-23
:confused:   I guess the question still stands.  Did 11.04 eliminate the ability to remove an old operating system and install the 11.04 without prepping the hard drive?

---

