---
title: "Making Buntu &gt;= 12.10 work on a Pentium M-CPU without PAE."
date: 2013-02-08
forum: Installation &amp; Upgrades
---

### Post by 7bit on 2013-02-08
For example a ThinkPad t40 or other models from that era with this Pentium-M CPU?

**ONLY** if you can afford to make it unbootable (and know how to restore it back to a working Precise) please tell me if this works:

0) (X|L|U)buntu precise is installed and running
1) download this [http://paste.ubuntu.com/1622104/](http://paste.ubuntu.com/1622104/)
   [COLOR="Red"]Edit: improved version: [http://paste.ubuntu.com/1629628/](http://paste.ubuntu.com/1629628/)[/COLOR]
   [COLOR="Red"]Edit2: I have made a deb package, see post #12: [http://ubuntuforums.org/showpost.php?p=12504589&postcount=12](http://ubuntuforums.org/showpost.php?p=12504589&postcount=12)
[/COLOR]2) make it executable and execute it as root (sudo)
3) cat /proc/cpuinfo and verify that it now contains the pae flag.

4) sudo update-manager
5) upgrade the entire system to 12.10

6.) Did it install the 3.5 kernel without errors, does it still boot (with that kernel), are there any broken/unconfigured packages regarding the kernel?

---

### Post by tgalati4 on 2013-02-08
I have a T43p (2006) vintage that I plan on upgrading from Jaunty, but I have to copy data off of it before I upgrade, so it will be a few days.

What is the purpose of this test?  I thought most Pentium-M's supported PAE, but there might be a few early-production chips that don't.

I plan on either doing a clean install or adding a partition and making it dual boot.  I have a 320GB drive, so I have some room to add another partition.

---

### Post by 7bit on 2013-02-08
> **tgalati4 said:**
> I have a T43p (2006) vintage that I plan on upgrading from Jaunty, but I have to copy data off of it before I upgrade, so it will be a few days.

What is the purpose of this test?  I thought most Pentium-M's supported PAE, but there might be a few early-production chips that don't.

I plan on either doing a clean install or adding a partition and making it dual boot.  I have a 320GB drive, so I have some room to add another partition.

if there is no pae flag in your /proc/cpuinfo then the deb package for the new kernel images  (Quantal and later) will simply refuse to install (and leave the entire package system in en inconsistent state) although at least *some* of these Pentium-M would perfectly run these new kernels if it *would* be possible to install them. The purpose of this script is to patch /proc/cpuinfo to trick the kernel .deb install script into thinking it will be installed on a compatible CPU.

If you do a cat /proc/cpuinfo and don't find any mention of "pae" in the flags then it will probably refuse to boot from the 12.10 install CD and also for 12.04 there are only a few (Xubuntu, Lubuntu) CD images that allow to boot. Again this is not the fault of the kernel, in this case it is the bootloader of the CD that will check the CPU capabilities and simply refuse to even try to boot the kernel anyways!

This means the problem is twofold:
* apt-get will work until 12.04 and from then on refuse any later kernel
* install cd bootloader also has this check and refuses to even try to start the boot process

12.04 still has the non-pae kernels in the repositories (only some of the install CD-Images don't have it), so it is still possible to intall 12.04 without any nasty hacks but then upgrading to 12.10 will lead to problems with the kernel upgrades and apt-get getting stuck.

There is a recommendation to download 3rd party non-pae-builds of these new kernels and install them *manually* but it seems some of the Pentium-M are indeed capable of running the original Ubuntu pae kernel and only don't show this stupid flag in the cpuinfo. ThinkPad T40 definitely *can* run the pae kernels (and probably similar thinkpads too), its just the apt-get that will not allow these kernels to be installed.

---

### Post by sudodus on 2013-02-08
I have a T42 without pae. I'm running Lubuntu 12.04 now. Have you found any problem? I guess it would be a problem to run with more than 2 GB RAM (I have 1.25 GB).

Maybe I will get time to test your method during this week-end. (I can clone the internal drive to a USB drive to get a backup while I'm tampering with it).

---

### Post by 7bit on 2013-02-08
> **sudodus said:**
> I have a T42 without pae. I'm running Lubuntu 12.04 now. Have you found any problem? I guess it would be a problem to run with more than 2 GB RAM (I have 1.25 GB).

Maybe I will get time to test your method during this week-end. (I can clone the internal drive to a USB drive to get a backup while I'm tampering with it).

You can try to install 

sudo apt-get install linux-generic-lts-quantal

this will pull in a bunch of other linux-* meta packages and linux-* packages from the 3.5 kernel (better save the list of packages it wants to install so you can remove them all again later) and then somewhere in the middle of this installation **it will fail** with error about missing pae and incompatible CPU and report broken/unconfigured packages (if it fails then remove everything it tried to install to make apt-get happy again)

if you run that script **before** you do this then apt-get will succeed and then you can reboot and it should boot with the new pae kernel although the CPU is not officially pae capable.

The script is only there to make apt-get believe it is ok to install these kernels, it does not affect the kernel itself, you need to run it only before you do a kernel update to suppress the pae related apt-get errors.

---

### Post by 7bit on 2013-02-08
cat /proc/cpuinfo | grep sizes
address sizes	: 36 bits physical, 32 bits virtual

It seems these Pentium-M do indeed have PAE built in and just do not announce it in their flags, otherwise there would be no way this CPU could have 36 bits physical address space (64GB) instead of 32 bit (non-pae, 4GB)

This means my method would work for all those Laptops that don't have pae in the flags but still have 36 bits physical address space.

The CD-Bootloader should be fixed to check for physical address space instead of that flag (which was accidentally forgotten in these particular Pentium-Ms) and the .deb install scripts should also be fixed to not grep for "pae" but for "36 bits physical" instead.

---

### Post by steeldriver on 2013-02-08
Hmm interesting - I recently put wheezy (from the mini iso iirc) on my old X30 and it insisted there was no suitable kernel - I ended up having to drop to the installer shell from which I was able to install 3.2.0.-4-686-pae manually - I thought it was something wrong with the iso

It's a PIII-M and also shows 36 bits physical in /proc/cpuinfo

I will have a play with your test if I get a chance

---

### Post by 7bit on 2013-02-09
I have improved the script a little bit, now it will put the pae flag into the flags line to the other flags, check that it isn't run a second time or on CPUs that already have the pae flag and output some diagnostic information to the console and also contains some explanations about the script in the comment block at the top.

[http://paste.ubuntu.com/1629628/]("http://paste.ubuntu.com/1629628/")

---

### Post by sudodus on 2013-02-10
> **7bit said:**
> You can try to install 

sudo apt-get install linux-generic-lts-quantal

this will pull in a bunch of other linux-* meta packages and linux-* packages from the 3.5 kernel (better save the list of packages it wants to install so you can remove them all again later) and then somewhere in the middle of this installation **it will fail** with error about missing pae and incompatible CPU and report broken/unconfigured packages (if it fails then remove everything it tried to install to make apt-get happy again)

if you run that script **before** you do this then apt-get will succeed and then you can reboot and it should boot with the new pae kernel although the CPU is not officially pae capable.

The script is only there to make apt-get believe it is ok to install these kernels, it does not affect the kernel itself, you need to run it only before you do a kernel update to suppress the pae related apt-get errors.
After cloning the drive I started:

- Your script warned that there are only 32 bits physical and virtual memory.

- I continued with 
```
sudo apt-get install linux-generic-lts-quantal
```
and it worked without complaints.

- I rebooted and the system is now running '3.5.0-23-generic'
```

sudodus@usb-lub:~$ uname -a
Linux usb-lub 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:15:33 UTC 2013 i686 i686 i386 GNU/Linux
sudodus@usb-lub:~$ grep 32 /proc/cpuinfo 
address sizes	: 36 bits physical, 32 bits virtual
sudodus@usb-lub:~$ grep pae /proc/cpuinfo 
sudodus@usb-lub:~$ ls -l /boot
...
-rw-r--r-- 1 root root 20115951 feb  1 20:59 initrd.img-3.2.0-37-generic
-rw-r--r-- 1 root root 21716879 feb 10 18:33 initrd.img-3.5.0-23-generic
...

```
Can you confirm that this is a pae kernel, that is now running in my T42 with Pentium M processor without pae?

```

model name      : Intel(R) Pentium(R) M processor 1.70GHz

```
And now it recognizes 36 bits physical memory.

Done :-)

---

### Post by 7bit on 2013-02-10
> **sudodus said:**
> 
Can you confirm that this is a pae kernel, that is now running in my T42 with Pentium M processor without pae?


Yes, it seems I was wrong assuming they would show 36 bits even *before* the pae kernel is installed. It seems it will always show 32 bit if it is a non-pae kernel. I should remove this 32 bit warning, its probably meaningless anyways.

If the the kernel boots without panic then everything should be ok. Probably this can be only found out by actually trying. Fortunately installing a new kernel will always leave your old kernels untouched, so in case it won't boot you can always go back to the older kernel.

I'm currently trying to make this script into an upstart job, installable with a simple .deb package. I'm then going to upload it to launchpad and post it here.

BTW today I finally tried it myself too, upgrading my ThinkPad T40 from Xubuntu Precise to Xubuntu Quantal with this method and everything went smoothly :-)

This is what I did:
* execute the script
* sudo update-manager (and upgrade to 12.10 without problems)
* reboot (and everything works)

---

### Post by sudodus on 2013-02-11
Congratulations to a nice tweak :KS

I think we are many users that will be able to continue using our Pentium M CPUs with modern linux versions thanks to your tweak :-)

---

### Post by 7bit on 2013-02-11
I have built a .deb package that will install an upstart job to enable this at boot time so the user does not need to start the script every time before a new kernel upgrade is to be installed. Instead it will just work[TM].

Here is the deb (for direct download): [http://ppa.launchpad.net/prof7bit/fake-pae/ubuntu/pool/main/f/fake-pae/](http://ppa.launchpad.net/prof7bit/fake-pae/ubuntu/pool/main/f/fake-pae/) (use the deb with the highest version number or better just add the ppa (see below) and use apt-get)

or alternatively just add the [[COLOR="Blue"]_ppa repository_[/COLOR]]("https://launchpad.net/~prof7bit/+archive/fake-pae") and use apt-get:
```

sudo apt-add-repository ppa:prof7bit/fake-pae
sudo apt-get update
sudo apt-get install fake-pae

```

From then on you won't have to care about it ever again. All subsequent kernel upgrades will just work. 

***

Details: When this package is installed it will automatically install and start the job and subsequently it is started also after every reboot. You can verify that when you cat /proc/cpuinfo there will be the pae flag in the "flags :" line.

If it is installed on a PC that already has the pae flag it won't do anything at all.

The above mentioned [[COLOR="Blue"]_ppa_[/COLOR]]("https://launchpad.net/~prof7bit/+archive/fake-pae/+packages") also contains the source tar.gz for download if you want to look at how it is built and how it works. Its essential parts are these files 

fake-pae.conf
debian/postinst
debian/prerm

The .conf file is the upstart job (containing essentially the script from post #1) that will be put into the /etc/init/ folder to be started on all runlevels except 0. The postinst and prerm are executed only during package installation/removal and will install and start or stop and remove the job, the rest of the files is only mandatory debian packaging stuff.

To temporarily disable it (for whatever reason) until next boot
```

sudo stop fake-pae

```

To enable it again
```

sudo start fake-pae

```

To uninstall it (which will also immediately disable it)
```

sudo apt-get remove fake-pae

```

---

### Post by megrimm on 2013-03-06
Hello,

I 'mistakenly' upgraded to 12.10 in my t42 without realizing the pae/non-pae kernel conflict. now my system is kind of broken. i can not install you .dep package because the package manager breaks when loading. anything i do with apt-get update etc give me "this kernel does not support non-pae" errors.

Can I install this a different way? I see you had an executable script at one point? might there be another way to fix my system with your script even though i have already upgraded to 12.10?

thanks!
m

---

### Post by sudodus on 2013-03-06
> **megrimm said:**
> Hello,

I 'mistakenly' upgraded to 12.10 in my t42 without realizing the pae/non-pae kernel conflict. now my system is kind of broken. i can not install you .dep package because the package manager breaks when loading. anything i do with apt-get update etc give me "this kernel does not support non-pae" errors.

Can I install this a different way? I see you had an executable script at one point? might there be another way to fix my system with your script even though i have already upgraded to 12.10?

thanks!
m

Are your old kernels from 12.04 still there, or are they wiped? If they are there, and you find them in the grub menu, try to boot from one of them!

---

### Post by megrimm on 2013-03-07
yes, I can boot to another kernel but then no matter what, when i try to install fake-pae, I still get:

megrimm@megrimm-lubuntu-t42:~$ sudo apt-get install fake-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-3.5.0-25-generic : Depends: linux-image-3.5.0-25-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.5.0-25-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

... and  'apt-get -f install' meets me with:

This kernel does not support a non-PAE CPU.
dpkg: error processing /var/cache/apt/archives/linux-image-3.5.0-25-generic_3.5.0-25.39_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-25-generic /boot/vmlinuz-3.5.0-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-25-generic /boot/vmlinuz-3.5.0-25-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.5.0-25-generic_3.5.0-25.39_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


so i feel stuck.

m

---

### Post by sudodus on 2013-03-07
I would try to remove the 'too new kernel packages'

```
sudo apt-get remove linux-image-3.5.0-25-generic
```
```
sudo apt-get remove linux-image-extra-3.5.0-25-generic
```

and then re-write the grub boot information with
```
sudo update-grub
```

---

### Post by megrimm on 2013-03-07
all i get from the first two commands is:

megrimm@megrimm-lubuntu-t42:~$ sudo apt-get remove linux-image-3.5.0-25-generic
[sudo] password for megrimm: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'linux-image-3.5.0-25-generic' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-3.5.0-25-generic : Depends: linux-image-3.5.0-25-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.5.0-25-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
megrimm@megrimm-lubuntu-t42:~$ sudo apt-get remove linux-image-extra-3.5.0-25-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-generic : Depends: linux-image-3.5.0-25-generic but it is not going to be installed
                       Depends: linux-image-extra-3.5.0-25-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by sudodus on 2013-03-07
Try the commands on this list, originally posted by *oldfred*. You need [COLOR=#ff0000][FONT=courier new]**sudo**[/FONT][/COLOR] to run them. But at this moment, avoid
dist-upgrade. Maybe the very last command will do the trick, but you might go through most of the list.

```

# This will reinstall if not current. (from my chroot procedure which does not have sudo on every line,
# so use the sudo -i first).
 
#if not chroot use: sudo -i

#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean

#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
# apt-get dist-upgrade # avoid this command until you have removed the too new kernels !!!

# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a

```

---

### Post by megrimm on 2013-03-08
So I "think" this is going to work (I have not rebooted yet).. but so far so good:


```
sudo dpkg --remove linux-image-extra-3.5.0-25-generic
sudo dpkg --remove linux-image-generic
sudo dpkg --remove linux-generic
sudo apt-add-repository ppa:prof7bit/fake-pae
sudo apt-get install fake-pae
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-image-extra-3.5.0-25-generic
sudo apt-get install linux-image-generic
sudo apt-get install linux-generic

```
...and i should be back to normal operating condition. 

thanks for all the help!
m

---

### Post by sudodus on 2013-03-09
megrimm,

Please let us know your results (after reboot) :-)

---

### Post by mfincken on 2013-03-10
> **megrimm said:**
> So I "think" this is going to work (I have not rebooted yet).. but so far so good:


```
sudo dpkg --remove linux-image-extra-3.5.0-25-generic
sudo dpkg --remove linux-image-generic
sudo dpkg --remove linux-generic
sudo apt-add-repository ppa:prof7bit/fake-pae
sudo apt-get install fake-pae
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-image-extra-3.5.0-25-generic
sudo apt-get install linux-image-generic
sudo apt-get install linux-generic

```
...and i should be back to normal operating condition. 

thanks for all the help!
m


This worked perfectly for me on an old Toshiba with a Pentium M processor. I had also mistakenly upgraded to 12.10 before installing the fake-pae package. The only thing I had to change was the update command had to happen before the fake-pae install, like this:

```
sudo dpkg --remove linux-image-generic
sudo dpkg --remove linux-generic
sudo apt-add-repository ppa:prof7bit/fake-pae
sudo apt-get update
sudo apt-get install fake-pae
sudo apt-get upgrade
sudo apt-get install linux-image-extra-3.5.0-25-generic
sudo apt-get install linux-image-generic
sudo apt-get install linux-generic

```

Thanks for the help! I am now happily running 12.10 with a Pentium M processor.

---

### Post by SirWeazel on 2013-03-12
I just wanted to say thanks to the people in this thread. I was having a similar issue and using the info provided i was able to fix my problem. I had my own thread going before i found this one.  Sometimes you search and search, find nothing. Wait a night, get some sleep, and try again.. this time with better success.  The below link is to the thread i had going asking for help.
[http://ubuntuforums.org/showthread.php?t=2122715](http://ubuntuforums.org/showthread.php?t=2122715)

---

### Post by megrimm on 2013-03-14
It has been a few days but I just wanted to say the steps I took worked fine after a reboot. I'm glad this thread has helped others!
m

---

### Post by JLeon85 on 2013-03-14
I have a T41 getting delivered next week that I'll be setting up for someone else. Can anyone advise me on what I should try installing first to have the least number of problems? I was planning on Lubuntu 12.10, but now I'm rethinking that. Thanks.

---

### Post by sudodus on 2013-03-15
> **JLeon85 said:**
> I have a T41 getting delivered next week that I'll be setting up for someone else. Can anyone advise me on what I should try installing first to have the least number of problems? I was planning on Lubuntu 12.10, but now I'm rethinking that. Thanks.

How much RAM will it have? With less than 768 MB, use the ***alternate iso to install the system***, and Lubuntu would be the best choice, because it is lighter. But let's hope there will be at least 1 GB of RAM.

I suggest that you choose between Lubuntu and Xubuntu. To do that, you can download both iso files and try them live (without installing). Let the end user decide which desktop environment to run.

- ***Lubuntu***: Install 12.04, install fake-pae with to 7bit's method in this thread, and upgrade to 12.10.

- ***Xubuntu***: Install 12.04 LTS and keep it, because it will get long time support until April 1215.

---

### Post by JLeon85 on 2013-03-15
Thanks for the advice. I believe its getting delivered with only 128MB of RAM, but I'm upgrading that right away to 2GB. I figure Lubuntu will fly on that unless the processor gets overwhelmed. I'll probably also throw in a persistent USB of Lubuntu as a backup OS if the hard drive starts to fail.  

The fake-pae sounds like it will save me a huge headache.  Also, I didn't know it was possible to upgrade one and not the other, but I will give that a try. Thanks again.

---

### Post by sudodus on 2013-03-15
Both are possible to upgrade, but due to the LTS, you need not upgrade Xubuntu until April 2015 :-)

---

### Post by mörgæs on 2013-04-20
So, summing it up: Status is that a considerable number (but maybe not all) Pentium M CPU's are in fact able to run a new Buntu with PAE kernel. 

Searching for the PAE flag, as is done when installing a standard 12.10 / 13.04, is overly conservative, as it leaves out a number of capable CPU's. Setting a fake PAE flag in the output of cpuinfo solves the problem, as can be seen in fake-pae.conf.

As of now the solution works as part of an upgrade of 12.04 or when rescuing a failed 12.10 / 13.04 installation.

How are the chances of making a respin of Lubuntu 13.04 which can be installed right away without upgrading, using scripts or adding PPA's?

---

### Post by sudodus on 2013-04-20
> **mörgæs said:**
> So, summing it up: Status is that a considerable number (but maybe not all) Pentium M CPU's are in fact able to run a new Buntu with PAE kernel. 

Searching for the PAE flag, as is done when installing a standard 12.10 / 13.04, is overly conservative, as it leaves out a number of capable CPU's. Setting a fake PAE flag in the output of cpuinfo solves the problem, as can be seen in fake-pae.conf.

As of now the solution works as part of an upgrade of 12.04 or when rescuing a failed 12.10 / 13.04 installation.

How are the chances of making a respin of Lubuntu 13.04 which can be installed right away without upgrading, using scripts or adding PPA's?
+1

Yes, please, who can do it :-)

---

### Post by SirWeazel on 2013-04-23
My questions is similar to the one above me. How would i go about adding fakepae to the install media or could i install the newer pae kernels without first starting with an older copy. The new ubuntu 12.04.2 ships with the newer pae kernel, but when i first installed 12.04 i used the alternate installer to install the non-pae kernel. Or what if i want to try 13.04? If my question is confusing, then let me know and i will try to clarify. I'm just trying to avoid the install, update, upgrade, then upgrade some more path.

---

### Post by Redalien0304 on 2013-04-23
Agreed who can do a respin for any Buntu or Lubuntu?? 

[IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **mörgæs**                     [[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=12610887#post12610887")                 
                 So, summing it up: Status is that a  considerable number (but maybe not all) Pentium M CPU's are in fact able  to run a new Buntu with PAE kernel. 

Searching for the PAE flag, as is done when installing a standard 12.10 /  13.04, is overly conservative, as it leaves out a number of capable  CPU's. Setting a fake PAE flag in the output of cpuinfo solves the  problem, as can be seen in fake-pae.conf.

As of now the solution works as part of an upgrade of 12.04 or when rescuing a failed 12.10 / 13.04 installation.

How are the chances of making a respin of Lubuntu 13.04 which can be  installed right away without upgrading, using scripts or adding PPA's?

---

### Post by sudodus on 2013-05-08
[SIZE=6]Lubuntu-fake-PAE[/SIZE]

Hello all Pentium M users,

Please visit the preliminary wiki page  [https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)   and tell me what you think.  [s]I have deliberately avoided to copy  the full instructions to the page, because I want to show that it is  preliminary (like a beta release).[/s]

*Edit*: Now the current detailed instructions also reside at the  Ubuntu wiki and are easily available from the page above. There is a new  GUI method to install directly from Windows.

---

### Post by bugbear6502 on 2013-05-21
> **mörgæs said:**
> So, summing it up: Status is that a considerable number (but maybe not all) Pentium M CPU's are in fact able to run a new Buntu with PAE kernel. 


I have a old fujitsu Siemens Amilo Pro 2000, with a Celeron M 340 1.5Ghz (according to the data sheet) (*)

I'm currently running Lubuntu 12.04 successfully. It runs fine and fast in 768 Mb of RAM
(OK, editing 60 minute MP3's in Audacity can get a bit slow...)

Is there any way shy of trying a full kernel install to confirm wether or not my CPU
will in fact run under fake-PAE?

 BugBear
(*) To make Joy complete it also has an Intel 855 graphics card, you know, the one that doesn't work right.

---

### Post by mörgæs on 2013-05-21
Please run ```
sudo lshw > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by sudodus on 2013-05-21
> **bugbear6502 said:**
> I have a old fujitsu Siemens Amilo Pro 2000, with a Celeron M 340 (according to the data sheet)

I'm currently running Lubuntu 12.04 successfully. It runs fine and fast in 768 Mb of RAM
(OK, editing 60 minute MP3's in Audacity can get a bit slow...)

Is there any way shy of trying a full kernel install to confirm wether or not my CPU
will in fact run under fake-PAE?

 BugBear
[URL="http://server/cgi-bin/wiki.pl?FujitsuSiemensAmiloProV2000"]
[/URL]

1. You need to run a pae kernel to test it. One way is to install it (and remove it afterwards) in your present Lubuntu 12.04. I have done that in my IBM Thinkpad T42 with a Pentium M 1.7 GHz.

It might be easiest to do that with ***Synaptic***. I think you are running the kernel that is managed by the package ***linux-generic***. If you install also the package ***linux-generic-pae*** and run

```
sudo update-grub
```

you will get the opportunity to test it. After testing you can select 'Previous Linux versions' in the grub menu and boot ***linux generic*** which is non-pae, and you can remove ***linux-generic-pae ***if you don't like it or don't need it.

2. Or if you do not want to touch your Lubuntu 12.04, you can use the 'grub-n-iso' method described at

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

and boot from the USB boot drive and test it live without installing anything. It will take longer time, but may feel safer.

*Edit*: A preliminary alternative is to run this command in your present Lubuntu 12.04

```
cat /proc/cpuinfo
```

and post the output of the command
[URL="https://help.ubuntu.com/community/Lubuntu-fake-PAE"]
[/URL]

---

### Post by bugbear6502 on 2013-05-24
> **sudodus said:**
> *Edit*: A preliminary alternative is to run this command in your present Lubuntu 12.04

```
cat /proc/cpuinfo
```

and post the output of the command
[URL="https://help.ubuntu.com/community/Lubuntu-fake-PAE"]
[/URL]

Sorry for the delay - I though this thread had stopped!

```

cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 9
model name    : Intel(R) Celeron(R) M processor         1500MHz
stepping    : 5
microcode    : 0x45
cpu MHz        : 1499.779
cache size    : 512 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts
bogomips    : 2999.55
clflush size    : 64
cache_alignment    : 64
address sizes    : 32 bits physical, 32 bits virtual
power management:



```

That doesn't look ideal.
 
    BugBear

---

### Post by plucky on 2013-05-24
Fujitsu-Siemens Amilo M7400 after I installed Fake-Pae

```
cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 13
model name	: Intel(R) Pentium(R) M processor 1.50GHz
stepping	: 6
microcode	: 0x17
cpu MHz		: 1500.000
cache size	: 2048 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: pae fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe bts est tm2
bogomips	: 2999.60
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 32 bits virtual
power management:

```

```
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring

```

Was then able to upgrade to 12.10 and then 13.04.

Try installing fake-pae and then run the "cat /proc/cpuinfo" and see if the pae flag is now set.

Good Luck

---

### Post by sudodus on 2013-05-24
> **bugbear6502 said:**
> Sorry for the delay - I though this thread had stopped!

```

cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 9
model name    : Intel(R) Celeron(R) M processor         1500MHz
stepping    : 5
microcode    : 0x45
cpu MHz        : 1499.779
cache size    : 512 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts
bogomips    : 2999.55
clflush size    : 64
cache_alignment    : 64
address sizes    : 32 bits physical, 32 bits virtual
power management:



```

That doesn't look ideal.
 
    BugBear

I think this CPU is a good candidate for fake-pae to run pae kernels :-) The result is typical with a non-pae kernel for Celeron M and Pentium M with pae capability but no flag. You should get 36 bits physical address size with a pae kernel, and in that case I think it works as it should.

---

### Post by sudodus on 2013-05-24
> **plucky said:**
> Fujitsu-Siemens Amilo M7400 after I installed Fake-Pae

```
cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 13
model name    : Intel(R) Pentium(R) M processor 1.50GHz
stepping    : 6
microcode    : 0x17
cpu MHz        : 1500.000
cache size    : 2048 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : pae fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe bts est tm2
bogomips    : 2999.60
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 32 bits virtual
power management:

```

```
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

```

Was then able to upgrade to 12.10 and then 13.04.

Try installing fake-pae and then run the "cat /proc/cpuinfo" and see if the pae flag is now set.

Good Luck

Great, it works for you too :KS

*@plucky*, Can I add your result to the list in the wiki page?

*@bugbear*, I agree: Try to do the same as *plucky* :-)

---

### Post by plucky on 2013-05-24
> @plucky, Can I add your result to the list in the wiki page?


Yup

---

### Post by sudodus on 2013-05-24
> **plucky said:**
> Yup
To identify the CPU, please post the output of the following command (you may need to install cpuid from the repositories).

```
cpuid|grep ^00000001
```

---

### Post by bugbear6502 on 2013-05-25
> **sudodus said:**
> To identify the CPU, please post the output of the following command (you may need to install cpuid from the repositories).

```
cpuid|grep ^00000001
```

Not sure if that request was for me or plucky, but since it's easy to do:

```

 cpuid|grep ^00000001
00000001 00000695 00000812 00000000 a7e9f9bf

```

    BugBear

---

### Post by sudodus on 2013-05-25
Thanks BugBear,

                The request was for *plucky*, who posted results from running 13.04 (with a pae kernel).

Your previous post shows that you can probably do the same, and there are several paths to follow.


A. If you want to keep your present installed system untouched, it is probably easiest to install 'grub-n-iso' from

[https://help.ubuntu.com/community/grub-n-iso](https://help.ubuntu.com/community/grub-n-iso)

to a USB pendrive and boot a live session.


B. but if you want to upgrade your system, you can do it according the instructions by mörgæs at

[http://https://help.ubuntu.com/community/PAE](http://https://help.ubuntu.com/community/PAE)

Actually in this case it is enough to install

1. fake-PAE and

2. a pae kernel, 

3. boot with the pae kernel and

4. run

```
cat /proc/cpuinfo
```

to find out if the computer now has 36 bits physical address size.

And with your cpuid spec. it is enough to be able to report the test result with your Celeron CPU.

---

### Post by plucky on 2013-05-25
```
cpuid|grep ^00000001
00000001 000006d6 00000816 00000180 afe9f9bf
```

I have reverted back to Xubuntu 12.04.2 as this is my test machine.

Do you need it to be running 13.04?

---

### Post by sudodus on 2013-05-25
> **plucky said:**
> ```
cpuid|grep ^00000001
00000001 000006d6 00000816 00000180 afe9f9bf
```

I have reverted back to Xubuntu 12.04.2 as this is my test machine.

Do you need it to be running 13.04?

No, according to my tests, cpuid gives the same information independent of the OS and/or kernel version. By the way, it is the same data as from my Pentium M, with 1.7 GHz (so it should basically be the same CPU, maybe only the clocking is different).

Thank you for testing and sharing this information about your CPU :-)

---

### Post by tginfos on 2013-07-13
Hello
I ran with kubuntu 13.04 and a non-pae kernel from linux-image -3.2.0-32-generic of previous version.
I then used fake-pae to install the latest PAE linux-image-3.8.0-26-generic successfully.

But the problem is that this kernel checks PAE presence during boot sequence, so I cannot use this kind of kernel.
So I don't really see the usefullness of fake-pae to force installation if the PAE test cannot be skipped at boot ?

my machine is thinkpad x40

> 
root@portable:~# cpuid|grep ^00000001
00000001 00000695 00000816 00000180 a7e9fbbf

root@portable:~# cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 9
model name      : Intel(R) Pentium(R) M processor 1200MHz
stepping        : 5
microcode       : 0x7
cpu MHz         : 1200.000
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : pae fpu vme de pse tsc msr mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2
bogomips        : 2392.23
clflush size    : 64
cache_alignment : 64
address sizes   : 32 bits physical, 32 bits virtual
power management:

---

### Post by sudodus on 2013-07-14
> **tginfos said:**
> Hello
I ran with kubuntu 13.04 and a non-pae kernel from linux-image -3.2.0-32-generic of previous version.
I then used fake-pae to install the latest PAE linux-image-3.8.0-26-generic successfully.

But the problem is that this kernel checks PAE presence during boot sequence, so I cannot use this kind of kernel.
So I don't really see the usefullness of fake-pae to force installation if the PAE test cannot be skipped at boot ?

my machine is thinkpad x40
```
flags           : **[COLOR=#ff0000]pae[/COLOR]** fpu vme de pse tsc msr mce cx8 apic mtrr pge mca  cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2
```
```
address sizes   : [COLOR=#ff0000]**32**[/COLOR] bits physical, 32 bits virtual
```


Welcome to the Ubuntu Forums :-)

This is a new problem or a new way to run with fake-PAE. Are you running an installed system with fake-PAE installed from the PPA? If so, either you have a version of Pentium M, that has not really all it takes to run PAE, or some developer has made the PAE checking tougher, to make it impossible to use fake-PAE to run Pentium M with new kernels.
[I]
Edit: Or maybe the problem is somewhere else in the computer (probably on the motherboard). I am running the same kernel 3.8.0-26 (Lubuntu 13.04) right now in an IBM Thinkpad T42 with Pentium M and fake-PAE successfully. I'm checking the version right now.[/I]

1. The cpuid code is slightly different, from what I have seen before.

2. I see that you have the PAE flag, I understand from fake-PAE.

3. You show 32 bits physical address size, where we have seen 36 bits with fake-PAE.

It would be very interesting share the result, if you download and try the 'grub-n-iso' original version of Lubuntu 13.04. Will it boot?

[URL="https://help.ubuntu.com/community/grub-n-iso"]https://help.ubuntu.com/community/grub-n-iso
[/URL]

---

### Post by naildeca on 2013-07-16
Thank you 7bit, sudodus and others working on this. I started following Launchpad bug 930447 soon after I upgraded to 12.04.

Today I followed the advice in post #43:
Installed fake-PAE (using post #12)
Installed a pae kernel, the one with the same version number as the non-pae I was running (using Synaptic Pakage Manager)
Rebooted using the new kernel (Kernel Linux 3.2.0-49-generic-pae)

Then I ran:
```
cpuid|grep ^00000001
00000001 00000695 00000812 00000000 a7e9f9bf

```
and 
```
cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 9
model name    : Intel(R) Celeron(R) M processor         1300MHz
stepping    : 5
microcode    : 0x45
cpu MHz        : 1298.853
cache size    : 512 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : pae fpu vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts
bogomips    : 2597.70
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 32 bits virtual
power management:
```

Everything seems to be working OK. I now feel confident that I will be able to upgrade to later versions of Ubuntu and not have to retire this computer when support for 12.04 LTS runs out in 2015.

Thanks again for all you have done.

naildeca

---

### Post by sudodus on 2013-07-17
I'm glad that our fake-PAE works for you, *naildeca* :-)

---

### Post by apec on 2013-09-09
I am pleased to report that this worked on my Thinkpad R51-2888.  12.04 wouldn't boot either so I started with 11.10.  I've brought it up to 12.10 and am happy with it under XUbuntu.  Had to disable the intel hardware video acceleration to get some GLX things to quit complaining but everything works great!  I'm debating on taking it up to 13.04.  The installer says it will disable any custom PPAs, so will that kill me?  I'm a reformed BSD guy, so a lot of the Ubuntu stuff is unknown to me.

---

### Post by sudodus on 2013-09-09
Welcome to the Ubuntu Forums  *apec* :-)

I'm glad fake-PAE works for you.

Have you got any custom PPAs? You can check that with ***Synaptic*** (check for program sources via Settings -- Repositories and the tab Other Software). For example fake-PAE will need to be restored if wiped by the upgrade. But that one should stay (and used to stay earlier at upgrades to new versions).

So before pushing the upgrading further, I suggest that you make a good ***backup***. Something could go wrong.

An alternative is to install directly into 13.04 (or even 13.10 alpha or beta) with Lubuntu fake-PAE according to one of these links.

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)
[One Button Installer, 'OBI']("http://ubuntuforums.org/showthread.php?t=2172971")

It is a good choice unless you have a lot of tweaks and private files in your current installed system, or if you prefer Xubuntu. On the other hand, I run Lubuntu plus Xubuntu Desktop to get the best from both Lubuntu and Xubuntu.

```
sudo apt-get install xubuntu-desktop
```

---

### Post by apec on 2013-09-10
Hmm.  The only PPA that shows up is for f.lux, which I deleted as I switched to redshift anyway.  I thought fake-PAE had added one, but maybe it was already removed by the previous update?  So as far as fake-PAE is concerned I should be safe to upgrade to 13.04?

---

### Post by apec on 2013-09-11
Nevermind. Upgrade went fine.  :)

```
apc@udinker:/$ uname -a
Linux udinker 3.8.0-30-generic #44-Ubuntu SMP Thu Aug 22 20:54:42 UTC 2013 i686 i686 i686 GNU/Linux
apc@udinker:/$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring


```

and yes, my cmos battery is dead.  I just got this laptop at a flea market. :D

---

### Post by sudodus on 2013-09-11
> **apec said:**
> Nevermind. Upgrade went fine.  :)

```
apc@udinker:/$ uname -a
Linux udinker 3.8.0-30-generic #44-Ubuntu SMP Thu Aug 22 20:54:42 UTC 2013 i686 i686 i686 GNU/Linux
apc@udinker:/$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring


```

and yes, my cmos battery is dead.  I just got this laptop at a flea market. :D

Congratulations :KS

Thanks to 7bit's fake-PAE, many computers like yours will have an extended life running new Lubuntu and Xubuntu versions :-)

[COLOR=#696969]When you install fake-PAE according to post #12 in this thread, the corresponding ppa will be installed and used

```
sudo apt-add-repository ppa:prof7bit/fake-pae
sudo apt-get update
sudo apt-get install fake-pae
```

If  fake-PAE is removed, grub will boot and *buntu will run (without  fake-PAE), but you cannot upgrade the kernel until you have installed  fake-PAE again, which is easy.[/COLOR]

---

### Post by apec on 2013-09-11
Well I spoke too soon on everything working fine.  Having some problems with flash now (graphics are hosed, reinstalling adobeflash had no effect).  And attempting to go into suspend crashes the system.  Not PAE related but I'll figure it out later.

---

### Post by sudodus on 2013-09-11
You may have problems because the support for your graphics chip in 13.04 is not as good as it used to be. If Xubuntu 12.04 is still good, I recommend that you stay with it until the end of life in April 2015.

It the XFCE graphics has too big foot-print, try LXLE or Bodhi (both are based on Ubuntu 12.04 and use desktop environments with small foot-prints).

-o-

If you have old Intel graphics, you could also try ***UXA*** according to the following tip from Lubuntu community mail thread.

> John Hupp wrote:

There was this helpful bug report on file at [http://bugs.launchpad.net/ubuntu/+source/linux/+bug/1178982](http://bugs.launchpad.net/ubuntu/+source/linux/+bug/1178982).

It described behavior on Dell PC's with integrated Intel graphics, in which Adobe Flash Player would display only with shades of purple and green in a horizontally compressed window (or at least that's how I would describe what I see on a Dell Dimension 2400).

The work-around (Comment #1) was to change the Xorg acceleration method to UXA. 

User reported a work-around:

-o-

Edit (or create) **[FONT=courier new]/etc/X11/xorg.conf[/FONT]** as follows: (ugh, can't format, should be a tab before each line except the first and the last).

```

Section "Device"
      Identifier "Intel Graphics"
      Driver "intel"
      Option "AccelMethod" "uxa"
EndSection

```
Restart X (reboot, restart your display manager, whatever). Colors are back to the way they used to be and flash works.

-o-

I forgot to include, however, that the bug workaround messes up the login screen (LightDM).  You can make out an entry box that one assumes is for the password entry, but everything else is largely unidentifiable.

So as a workaround it leaves a lot to be desired, unless we can also figure out how to fix the login screen.

-o-

Nio Wiklund wrote:

This method works for me to restore good graphics in an old IBM Thinkcentre with Lubuntu Saucy alpha-2 and the following Intel graphics.

VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

There is no issue with the login screen.


---

### Post by apec on 2013-09-11
Ah thanks, I figured as much.  Yes it's an Intel 82852.  I had disabled video acceleration before in order to get Stellarium working, and switching to UXA does make flash work again, but now Stellarium doesn't work - it kicks back a bunch of opengl errors.  Oh well.  More problematic is the inability to suspend.  A quick glance at the pm log suggests it's also a video problem.  I'll try to figure it out but yeah I'm starting to lean towards going back to 12.04.

---

