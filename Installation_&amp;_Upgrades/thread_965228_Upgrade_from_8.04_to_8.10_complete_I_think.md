---
title: "Upgrade from 8.04 to 8.10 complete I think????"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by glenngds2007 on 2008-10-31
The problem is that the desktop background picture did not change and when I start Firefox it still says 8.04.  As far as I can tell no upgrade has happened.  How can I be sure?  I have just downloaded an iso of Ubuntu 8.10 just in case I need to install from an iso.  Really need an answer quick, so I can decide what to do.:confused:

---

### Post by glenngds2007 on 2008-10-31
I got a little tired of waiting for an answer to my problem.  So I popped the Ubuntu 8.10 CD into my drive and rebooted. All went well for a little while.  When I chose to test the CD for errors--I could tell that the kernel loaded--the kernel started scanning for the CD and never found it and so a whole screen full of errors popped up.  All the errors were about ata0:1. The only problem is that there is nothing at ata0:1 since I have only one ata dvd-rw in the machines.  The problem is that I have three nearly identical computers.  All three have a Gigabyte GA-MA74GM-S2H MOBO--one has an AMD Athlon X2 4800+; one has an AMD Athlon X2 5000+; and one has an AMD Athlon X2 5800+--all three have Seagate SATA hard-drives and all three have an AOPEN DVD-RW drive.  All three had no problem installing Ubuntu 8.04 from a CD.  So basically I am stuck with three computers doing the same thing--no way to upgrade to Ubuntu 8.10.  Any ideas would be helpful at this point.:mad:

---

### Post by glenngds2007 on 2008-10-31
If CD draw is empty it ejects no problem.  If there is any kind of CD in the draw--it does eject but immediately pulls it back in on all three of my computers.  In fact I had the Ubuntu 8.10 CD in one computer and went to eject the CD and I did not grab it securely and it fell on the drive half way out and now the CD has a major scratch on it. I am very angry at this turn of events, what am I supposed take a chance of messing up any CD I need to put into a drive on any of my computers.  It has just started to do this since the failed upgrade.

---

### Post by cubeist on 2008-10-31
I have the same MOBO with different proc and disk drive and installed last night without a hitch.

If I am understanding you, you cannot boot the live cd to a desktop without errors?

First, did you md5sum the download?
Second, did you burn at the slowest speed possible?

Third, are you selecting to just install, or the "try ubuntu" option?

---

### Post by roger_1960 on 2008-10-31
Hi

The CD drawer problem is a known bug published in the 8.10 installation notes.  It sounds like you are runing 8.10

If you type 

uname -a 

in terminal it will return the kernel version (and cpu) so you should be able to tell for sure.

---

### Post by maybeway36 on 2008-10-31
> **glenngds2007 said:**
> The problem is that the desktop background picture did not change and when I start Firefox it still says 8.04.  As far as I can tell no upgrade has happened.  How can I be sure?  I have just downloaded an iso of Ubuntu 8.10 just in case I need to install from an iso.  Really need an answer quick, so I can decide what to do.:confused:

Try
```
cat /etc/issue
```
It should say Ubuntu 8.10. If it does, just change your desktop background, then change your home page to [http://start.ubuntu.com/8.10/](http://start.ubuntu.com/8.10/).

---

### Post by glenngds2007 on 2008-10-31
Thanks guys for all the help.  As far as the cat command it says 8.10.  As far as changing the homepage of Firefox I have yet to find the real home page of Ubuntu 8.10 and it is not [http://start.ubuntu.com/8.10/](http://start.ubuntu.com/8.10/).  As far as the CD not being recognized is a little of a shock when I tried to boot the Ubuntu 8.10 CD.  It is a well known fact that with the Fedora since 7.0 it has had a problem recognizing certain hard drive CD combinations usually SATA HD with an IDE DVD-RW and there solution was to tell people to try a different CD/DVD drive in there computer. My solution was to borrow a friends external DVD drive and then Fedora 7 installed no problem.  What happened was I returned my friends external DVD drive before I realized that even after it was installed Fedora 7 still did not recognize that AOpen DVD-RW drive.  So nix Fedora and I came over to Ubuntu around I believe 7.04.  Did someone borrow some code for the kernel from Fedora?:lolflag: Yes the AOpen DVD-RW drives are about 2 years old--all three of them and all three are the same model number.

---

