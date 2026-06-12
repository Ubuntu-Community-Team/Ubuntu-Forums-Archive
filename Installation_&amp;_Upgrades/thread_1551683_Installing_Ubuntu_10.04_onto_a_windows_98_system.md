---
title: "Installing Ubuntu 10.04 onto a windows 98 system"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by nootkan on 2010-08-12
I have tried searching for windows+98 and windows 98 and "windows 98" but cannot find any info on how to install Ubuntu 10.04 over my windows 98 system. Is this possible? I have downloaded and burned the iso 32 bit version onto a cd and when I try to run it in the old system it does nothing not even an error message. I know the cd is valid as I can run it on my laptop with no issues. 
 
The system info is as follows:
> Windows 98 4.10.2222A
Pentium 3
256 mb ram
32 bit

---

### Post by cj.surrusco on 2010-08-12
Maybe you should try the alternate CD. It has a text-based installer that is a little more friendly to older systems.

---

### Post by nootkan on 2010-08-12
That's the only way huh?  Unfortunatley I have to go back to work for four months and won't have the time to wait for the alternate cd.  Was kind of hoping to try it on my old computer asap before making the switch.  I've played around on the laptop a bit but don't want to install it there just yet.

---

### Post by dcollier on 2010-08-12
Since this is a windows 98 box, try using a different slice of ubuntu, like xubuntu or kubuntu.  One of these should work on that old box.

---

### Post by nootkan on 2010-08-12
Thanks for your reply, what is meant by a different slice?  Is that a different os than ubuntu?  Is it as user friendly as the destop verion 10.04?

---

### Post by JBAlaska on 2010-08-12
Most likely, your older computer will not boot from the CD directly. I remember installing win 95 &98 on systems and having to create a boot floppy to enable the CD drivers and continue to boot from the CD.

You need to find out the make and model of your CD drive and build a boot-able floppy disk with a autoexec.bat and config.sys files containing your cd driver lines.

---

### Post by nootkan on 2010-08-12
Unfortunatly, I'm not much of a tech guy so I'll try the download of Kubuntu and see if that works otherwise I'll reformat (I have instructions on how to do this) using windows 2000 and try again.  If that fails then I'll just scrap the idea altogether.

---

### Post by mörgæs on 2010-08-12
Kubuntu is by no means lighter than Ubuntu. Xubuntu might give a small advantage, but not enough for 256 MB.

Your options are:


The text-based installer, if you are lucky.

A minimal Ubuntu installation:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

Another Linux distro, for example Puppy or Slitaz.

---

### Post by JBAlaska on 2010-08-12
You mentioned win2000, do you have a win2000 disk that will boot in that computer? If so you should be able to boot a LiveCD of Ubuntu. 

If not try this [Link](http://www.onecomputerguy.com/install/floppies.htm) for instructions on making a boot floppy with generic CD-ROM support.

**If you scroll down the page a bit, you can download a win98 boot floppy image that is pre-setup to boot most all IDE CD-Roms of that era.**

If this is indeed your problem another distro will NOT help nor will formating the HD.

Good luck!

---

### Post by nootkan on 2010-08-13
Okay I got the mini ubuntu 10.04 to install on a full disk. I type sudo tasksel and a window shows up for software selection however when I hit enter for the software chosen in red I get sent back to the username@ubuntu:~$ prompt. Am I supposed to put in the cd or be online for this step? Right now I'm just on the computer by itself trying to learn how to get to the desktop. I've started reading throught the [https://help.ubuntu.com/10.04/serverguide](https://help.ubuntu.com/10.04/serverguide) manual but it's not easy to understand.
 
I also tried using the steps in the link [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal) but got a lot of failure errors after typing in the three commands
> sudo apt-get update
sudo apt-get install xorg xterm gdm icewm menu firefox gksu synaptic --no-install-recommends
sudo service gdm start
The last Error of quite a few after the sudo apt-get update command:
> W: Failed to fetch [http://security.ubuntu.com/dists/lucid-security/multiverse/i18n/Translation-en_CA.bz2](http://security.ubuntu.com/dists/lucid-security/multiverse/i18n/Translation-en_CA.bz2) 
Tempory failure resolving 'security.ubuntu.com'
 
I'm assuming the other errors from the other two commands are in large part because of the first command errors so I won't post them here unless you want me to.
 
Not sure where to go from here.

---

### Post by mörgæs on 2010-08-13
You need to have wired internet access during the entire process. The mini.iso contains only the bare minimum, hence the name, and everything else must be downloaded.

If you want a real minimal system, don't install the suggested configurations offered by the CD. They will give you a whole lot of useless packages. 

Best is to hand-pick the packages with apt-get, after the basic installation is done. 

This might be an inspiration: 
[http://ubuntuforums.org/showpost.php?p=9287016&postcount=223](http://ubuntuforums.org/showpost.php?p=9287016&postcount=223)

---

### Post by nootkan on 2010-08-13
Well this time I left the internet hooked up and rebooted with the cd to start over.  I removed the cd and rebooted again and after I got to the username@ubuntu:~$ and typed in all three commands in sequence and everything seemed to install okay other than it loaded so fast I couldn't keep up with the messages. At the end I got the Ubuntu 10.04 screen and then I got an error message that reads:
> The disk drive for dev/mapper/cryptswap1 is not present. Continue to wait or press S to skip or press M for manual recovery. After skipping I got a black screen and had to reboot and this time I pressed M and got this message: Filesytem check or mount failed and something else that I couldn't read before it went black.
 
Should I try an older version of Ubuntu? Say 8.10 for example?

---

### Post by marl30 on 2010-08-13
I'm somewhat new to Ubuntu. I'm running 10.04 on my newer computer, but have been toying around with some lite distros for my older computer, which has just 320MB. I've tried out Puppy Linux and Tinyme.

I would recommend you try Puppy Linux. Tinyme would have been great too, if it didn't have a bug that disables restart and shutdown after an update (there is a work around though). But both these distros can run fast using 64MB ram and smaller.

---

### Post by nootkan on 2010-08-14
Yeah I looked at puppy linux and for the life of me I cannot figure out how to install it on my computer even after reading through the instructions and forum.  Therefore I will look for something easier (hopefully).  Thanks for the reply.

---

### Post by confused57 on 2010-08-14
Did you happen to see this tutorial, with screenshots?:
[http://puppylinux.org/wikka/InstallationFullHDD](http://puppylinux.org/wikka/InstallationFullHDD)

Puppy Documentation:
[http://puppylinux.org/wikka/CategoryDocumentation](http://puppylinux.org/wikka/CategoryDocumentation)

---

### Post by mörgæs on 2010-08-14
> **nootkan said:**
> Well this time I left the internet hooked up and rebooted with the cd to start over.  I removed the cd and rebooted again and after I got to the username@ubuntu:~$ and typed in all three commands in sequence and everything seemed to install okay other than it loaded so fast I couldn't keep up with the messages. At the end I got the Ubuntu 10.04 screen and then I got an error message that reads:

 
Should I try an older version of Ubuntu? Say 8.10 for example?

I have just sat up a minimal 10.04, and I am getting a similar error at boot time. The system is working well, so I guess it is a false alarm. There has been many problems with 10.04 reacting to false alarms regarding the hard drive before.

In general it is good to try various versions, but 8.10 is obsolete.
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

---

### Post by nootkan on 2010-09-02
Well I've given up on Ubuntu/Linux, it's back to windows for me.

---

