---
title: "I upgraded, and now I have this error..."
date: 2010-09-24
forum: Installation &amp; Upgrades
---

### Post by mörgæs on 2010-09-24
[B][COLOR="Red"]
The thread is closed, but a [new one]("http://ubuntuforums.org/showthread.php?p=11789959") is available.
[/COLOR][/B]


Ubuntu offers to upgrade to the next release by the push of a button. It is a convenient way of upgrading, but it is also a huge process, and many steps can fail, especially if the system was not stable from the beginning.


This guide is for you, who have tried the upgrade without luck. A lot of different problems can arise from a bad update, for example trouble with the screen card, a slow system, network problems, problems with mice and keyboard or a system which simply does not boot.

[COLOR=Red]Focus is on a classic Ubuntu install, not Ubuntu running  inside Windows (Wubi). There is some advice regarding Wubi later in the  thread, but if you have problems with Wubi, best is to read this one: [/COLOR]
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Whether or not an upgrade is generally safe compared to a clean install is not the topic. If you are reading this, you probably have trouble with an upgrade, and it is not relevant to know how often it works on other machines.

These steps are intended to be a low-tech step-by-step solution suitable for everyone. It is not guaranteed to solve all problems, but hopefully it serves as a first attempt. The process is:
 

** 1 - Does the machine like the version of Ubuntu to which you are upgrading?**

Lack of hardware support is the reason for many failed upgrades. Though the Ubuntu developers are going great lengths to ensure that a new version works on most hardware, there are examples that support is missing in new versions, often because the hardware manufacturer does not provide drivers. Screen cards are the typical problem.

Best is to try the new version in a live boot before installing. A live boot is primarily for testing, it does not change anything on the hard drive unless one decides to do so.

If the computer is newer than around 2004, it can boot from a USB memory stick, else you need to boot from CD. In both cases it might be necessary to set the boot order in BIOS. 

Buntus have a built-in USB creator, and if you want to create the USB stick using Windows, [Unetbootin]("http://unetbootin.sourceforge.net/") is recommended. Best is to download the ISO to the hard drive before running Unetbootin. 

Burning a CD should be done with the slowest speed available. Some reports indicate that write-once CD's work better than rewritable ones. Should the boot fail, test the CD itself from the boot menu or try booting another machine with the CD. 

Remember that the ISO is one big packaged file and not the installation program. Hence one needs to choose 'create CD from image' or similar while burning, not transfer the ISO file itself to the CD.


More on booting from USB, including how to get rid of the annoying U3 software found on some USB sticks:
[http://psychocats.net/ubuntu/usb](http://psychocats.net/ubuntu/usb)
In Ubuntu, U3 can be removed using u3-tool found in the repositories.


Sometimes boot options (=kernel parameters) are needed in order to get a particular version running: 
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[http://www.ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://www.ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

The complete list of boot options is here, 
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
but most often you will only need the ones mentioned above.

If that does not work:


**2 - Does the machine work with other versions of Ubuntu?**

There are always three or four supported releases of Ubuntu for the desktop and five on server side. They can be very different regarding hardware support, so don't take for granted that the newest always is best. If your first pick does not behave, try some of the other releases. Never install an unsupported release, though.
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

The fastest way of getting an ISO is through a torrent, but you can also download them from here:
[https://launchpad.net/ubuntu/+cdmirrors](https://launchpad.net/ubuntu/+cdmirrors)

Another - and often better - solution is trying one of the other Buntus:
[Xubuntu]("http://www.xubuntu.org/about") [Lubuntu]("http://en.wikipedia.org/wiki/Lubuntu") [Kubuntu]("http://www.kubuntu.org/feature-tour")


In most cases there are workarounds for the missing hardware support, first of all the boot options mentioned above, but that is outside the scope of this guide. As a first step, ask our friend Google. 

If you tried a 64 bit version without luck, give the 32 bit a try.

For old hardware, Ubuntu might be too heavy, so best is to try one of the lighter distros:
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)
Especially Lubuntu and Puppy are good candidates. 

Some people skip this point and cling to the newest release demanding it to work, no matter what, simply because it is the newest. This means asking for problems. 

Remember that the release of a new version of Ubuntu (or Windoze or Mac OS) has nothing to do with passing of a certain quality test. On the contrary, the system is released as good as it gets at a date decided upon many months before. Before wasting too long time beating the newest release to obedience, consider staying half a year more with the old one. 

If that does not work:
 

**3 - Is there a hardware problem on the machine?**

Bad memory blocks can give a lot of strange symptoms. When booting a live Ubuntu, one gets the option of testing the memory. The test runs automatically, but it might take all night.

If the test indicates errors, best is to take out the RAM sticks one by one and repeat the test to isolate the error. Beware of static electricity when doing this.


Problems with keyboard and / or mice freezing are sometimes related to the BIOS. Check that you are using the newest BIOS release.


If you have the slightest doubt of the conditions of the hard drive(s), best is to erase everything with Killdisk before installing.
[http://www.killdisk.com/](http://www.killdisk.com/)

Just burn the Killdisk ISO to a CD (like with Ubuntu) and boot from it. 

When you are adding a used disk to the system, you should always clean it first, especially if it has been used in RAID.

If Killdisk does not run, it is likely that the hard drive has physical errors and should not be used.


If that does not work:


** 4 - Ask the forum**

If the machine still does not boot a live Ubuntu, it is time for posting a question in the relevant forum. Remember to write everything you know of the hardware and describe thoroughly the attempts you have done. You could also try a live boot of Knoppix, Puppy or other Linux distros for comparison.

If you are posting for the first time, take a look at this:
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)



[SIZE=3]**Assuming that a live boot works now:**[/SIZE]
After these steps we know that the desired version of Ubuntu works on the hardware in question when booted in a live environment, but the attempted upgrade did not. This gives us two options: Trying to fix the problem(s) or installing a new Ubuntu from scratch.

It is not possible to give advice on solving specific problems in this general guide. However, if one decides to do a clean install, these are the steps:


** 5 - Back up important files.**

The /home directory contains user files. They must be copied to a safe location, for example a USB drive.

/home also contains hidden configuration files and directories, indicated by a name beginning with a . (dot). Also these should be copied to the backup drive. With control + h, Nautilus will show hidden files.

In addition to this, it is wise to back up /etc/X11/xorg.conf, if this file is present.

Note: If /home sits on its own partition, it is strictly speaking not necessary to back up any of its files since it is possible to delete only the other partitions and keep this one. Nevertheless, a backup is always a good precaution against Murphys Law.

If you can, best is to physically remove the backup drive from the system before proceeding.


**6 - Create space for the new installation.**

If you don't want to keep anything from the hard drive, just skip to the next step and let Ubuntu wipe the entire drive during installation.

If the machine has one or more operative systems next to Ubuntu (for example Windows), and if you want to keep it/them, boot the live CD again. Open the program Gparted and delete only the Ubuntu partitions.

If you have a separate /home and want to keep it as described above, take care when deleting!
 

**7 - Installation.**

Remove all unnecessary USB devices before installing, but keep the internet cable attached.

Boot with the Ubuntu version of your choice and follow the instructions on screen. If a question does not make sense to you, just follow the defaults.

If the normal CD gives trouble during installation, the first step is trying the alternate (text-based) install CD in stead. The finished system will be the same, the only difference is that the installation process itself has another look and feel.

After a boot, Ubuntu will ask for permission to download and install bugfixes. Approve everything here, but [COLOR=Red]don't install closed-source graphics drivers[/COLOR], even if Ubuntu suggests this. Only after a thorough testing and a number of reboots with open-source drivers, confirming that everything works, you can experiment with closed-source. The reason behind this is that closed-source drivers sometimes break the system, so best is to isolate this kind of error.


**8 - User files**

Now the new system is ready for use, and it is time to copy the user files back to the /home/<username> location. Keep the config files on the backup drive but don't use them unless you are absolutely sure what you are doing.


 
Now you should have a working installation. I hope you also had fun in the process and learned something.
 

Happy hacking
Mörgæs





[COLOR=Red]**Well, I get your point, but I have installed so many applications on my system that a clean install is basically out of the question**.[/COLOR]

This goes around a lot in the fora. I believe that the wording ought to be "I have installed so many applications on my system that an online upgrade is basically out of the question". Here is why:


**A)** The more modified a system is, the more you can assume that an upgrade of this particular system has not been tested by the Ubuntu developers. 

One of the blessings of free and open source software is the abundance of available applications. By all means give them a test, but remember that this moves your system further towards one-of-a-kind.

If one of these applications does not run in the new Ubuntu release or if the upgrade of this particular application has not been thoroughly tested, the whole process could fail. 

A customisation does not need to be very exotic to disturb the upgrade. Changing drivers for the graphics card or adding a personal package archive to the Software Sources might be enough.


**B)** There can be many good reasons for leaving an old application and switching to something different. For example, going from 10.10 to 11.04 Open Office is replaced by Libre Office, and in the step from 10.04 to 10.10 some Mono-based applications like Tomboy and F-spot were replaced with true open source alternatives. Let's hope we can put the old ones to rest.


**C)** Are all your applications actually needed, or are they just there because you installed them once and forgot about them? For people like me who end up with a lot of unneeded applications on the system over time ('they might come in handy some day'), it is actually good to begin from scratch and actively select the applications rather than bringing them along to another version. If you need a list to remember what was installed in your old system, it is a sure sign that you had too much.




If you in spite of this want to keep exactly the same packages in the new Ubuntu installation, there is an alternative to the online upgrade. Running the command

```
dpkg --get-selections > installed-software
```gives a text file with all installed packages on the system. If you run this command on the old system, you will have the option of running 

```
 dpkg --set-selections < installed-software 
```on the new system after a clean install and get the same selection of packages. Thanks to **bcscomp** for this suggestion.




[COLOR=Red]**So... maybe I should have done a clean install, but before I flush the machine, is there one last thing I could try to get it running?**[/COLOR]

Yes, there are some:

1) Boot the machine (into recovery mode, if necessary) and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

Read carefully the error messages, if any. The solution might be explained here.


2) Rebuild your /etc/apt/sources.list

Make a backup copy of the file mentioned above and build a new one using 
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

Select all branches, updates and third-party repositories that may have been on the system. After applying the new sources.list, run again the three apt-commands above.

Thanks to **artoonie** for this idea.

Enabling the "proposed" repository will give you access to more bug fixes, but they are in an experimental stage. It could solve the problem, but it could also create another one. Be careful here.


3) Boot into an older kernel.
In the boot proces you might see a list of available kernels. Try going through them step by step and test if one works. 

If the list does not appear by itself, pressing left-shift early in the boot will show it, provided you have the Grub 2 boot loader. If your initial install was Ubuntu 9.10 or later, you have Grub 2 - if it was older than 9.10, it is most definitely time for a reinstall.


4) If you can boot into a command prompt but not the graphical environment, you could try the command **startx**. 


5) Adding boot options as described earlier in this post is also worth trying.

---

### Post by Rubi1200 on 2010-09-25
Excellent guide mörgæs; I really hope users will refer to this when they come to upgrade/encounter problems.

Keep up the good work!

---

### Post by mörgæs on 2010-09-25
Thanks :-) Let's hope it will save some time both for asking and answering.

---

### Post by wkulecz on 2010-10-06
Before you upgrade, get an external USB drive and clone your system with
sudo rsync -ax / /media/usbdrive

You'll need one rsync command for each partition you mount.  The rsync docs are quite good.

This way you can recover if the install goes bad and try again and again if you want.  Bone up on reinstalling grub or grub2 beforehand too.

Backing up /home only will not recover all the work you did installing and configuring extra packages which is likely the reason you want an upgrade instead of a fresh install!

---

### Post by bcbc on 2010-10-06
From the release notes:
> Upgrading Wubi systems from 10.04 LTS is known to fail, and is not recommended at this time. ([653134]("https://bugs.launchpad.net/wubi/+bug/653134"))If you have already upgraded and find that the system reboots, hangs or drops you at a grub prompt when selecting Ubuntu (with or without error messages), then first try to replace the c:\wubildr file from the one in c:\ubuntu\winboot\wubildr (change 'drive' if necessary and backup c:\wubildr first as a precaution). This fix has been confirmed by many different people, as it appears that in many cases the upgrade is corrupting the wubildr file.

Otherwise another workaround is to boot a live CD, [loop mount the wubi root.disk]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?"), edit the grub.cfg (gksu gedit /*mountpoint*/boot/grub/grub.cfg) and remove all lines above the first "menuentry".

If you get a read-only error on grub.cfg, then either use vi or nano, or before running gedit first run: 
sudo chmod +w /*mountpoint*/boot/grub/grub.cfg
Note: if you install kernel updates, new kernels, remove kernels, run update-grub etc. you'll have to reapply the workaround as grub.cfg is regenerated automatically. It's easier to do this before you reboot (or you'll have to use the live CD again).

PERMANENT MANUAL FIX:
I am working on completing testing for this but so far it works on 10.04.1 and 10.10 which all are affected by the same issue. [http://ubuntuforums.org/showpost.php?p=10180520&postcount=78](http://ubuntuforums.org/showpost.php?p=10180520&postcount=78)
You still need to boot the wubi before applying the permanent fix.

---

### Post by Rubi1200 on 2010-10-06
> **bcbc said:**
> From the release notes:


If you have already upgraded and find that the system reboots or hangs when selecting Ubuntu (with or without error messages), then a workaround is to boot a live CD, [loop mount the wubi root.disk]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?"), edit the grub.cfg (gksu gedit /boot/grub/grub.cfg) and remove all lines above the first "menuentry".
Thanks for this information bcbc; much appreciated.

Couple of questions:

1. prior to this I have observed that you were recommending that users should reinstall the Windows bootloader (in most cases) to correct the problem.

> **[COLOR=DarkRed][SIZE=3]Important Note to Wubi (Windows Ubuntu) Users: Grub Update results in "No Such Disk":[/SIZE][/COLOR] **
A late July 2010 Grub 2 update is causing a "**[COLOR=DarkRed]no such disk[/COLOR]**"  error for some users of WUBI, resulting in an unbootable system. If the  system doesn't display the original Windows menu, the most likely cause  of the failure is that Grub 2 was installed in the MBR and/or on the  Windows partition. To correct this, restore the Windows bootloader using  this link:
[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

Whether the failure is due to improper user selections or Grub 2's  failure to recognize a Wubi install, it has been reported in the  following bug and users can review it for status updates and recovery  options when they become available:
[https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

2. is the method suggested in your post above mine now the preferred way of dealing with this issue?

Thanks in advance,
Rubi

---

### Post by bcbc on 2010-10-06
> **Rubi1200 said:**
> Thanks for this information bcbc; much appreciated.

Couple of questions:

1. prior to this I have observed that you were recommending that users should reinstall the Windows bootloader (in most cases) to correct the problem.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

2. is the method suggested in your post above mine now the preferred way of dealing with this issue?

Thanks in advance,
Rubi
You're right, Rubi. I should have clarified. 
The problem that bug 610898 refers to is still an issue. The symptom of this is that your computer boots straight to a grub rescue prompt instead of the windows boot manager. This bug only affects wubi installs to a partition other than the main windows partition, and only if the user elects to install the grub-pc bootloader to their hard drive master boot record (MBR). The fix for this remains to reinstall the windows bootloader.

But there is a new problem involving grub2 changes that are breaking wubi upgrades to 10.10. The symptoms of this are that you still boot to the windows boot manager, and can boot windows, but whenever you try to boot Ubuntu it either reboots or hangs (before displaying the grub menu). It may or may not display some error messages e.g. error: command loadfont/gfxterm not found.
At present this affects any wubi install ([https://bugs.launchpad.net/bugs/653134](https://bugs.launchpad.net/bugs/653134)). From Colin Watson's recent comment on this bug it is unlikely that a wubi upgrade will be possible anytime soon for a wubi install on a different partition to windows (this is where it's related to 610898 ). And at present any wubi upgrade may fail (results are inconsistent and no fix has yet been released).

---

### Post by Rubi1200 on 2010-10-06
Excellent! 

This will definitely be very useful when it comes to helping users who face these problems.

Thanks bcbc :)

---

### Post by driversat on 2010-10-08
great work thanks!
i have upgraded from 9.10 to 10.04 online(notified by update manager)
i was during update asked to save or replace some files(i don't remember which files) and i replaced them with new suggested ones.
now my machine turns on but doesn't display the desktop menu,icons, bar...nothing but a picture of a galaxy in background.
any ideas please?
ps: 9.10 was working fine without probs and my graphics card is nvidia geforce4 mx-440

---

### Post by mörgæs on 2010-10-09
> **driversat said:**
> 
any ideas please?

Yes... Follow the 8 steps in the guide above.

---

### Post by archolman on 2010-10-09
[COLOR=Indigo]Sorted with Update Manager...[/COLOR]
Hello all.
 I have just tried to "apt-get dist-upgrade" from 8.04., hoping to end up with 10.04
However, the result is I am still running 8.04.
(Synaptic does not show any link to upgrade to 10.04)
I now only have 2 screen resolutions available, 800 x 600 & 640 x 480, I had the 1280 x 1024  resolution previously.
Some of the packages could not be downloaded, , "--fix missing" made no difference.
Rebooting from cold has not made any difference.

Help?

AMD Athlon64 2-core, 2Gb RAM, HP flat monitor

---

### Post by archolman on 2010-10-09
See above...

---

### Post by puspworld on 2010-10-10
I have upgraded my old machine to ubuntu 10.10. I followed a upgrade tutorial found on [http://tech.mobiletod.com/how-to-upgrade-the-latest-version-of-ubuntu-10-10/](http://tech.mobiletod.com/how-to-upgrade-the-latest-version-of-ubuntu-10-10/) . They provided detailed steps about everything on Ubuntu 10.10

---

### Post by Handssolow on 2010-10-10
gdm binary 1816
failed to acquire org.gnome.DisplayManager
gdm-binary 1816
could not acquire name bailing out

After the upgrade reboots wouldn't deliver a graphical interface, I couldn't gdm restart. Fortunately pressing ESC at reboot gets me to into Grub where I select a previous working kernel 2.6.32-35-generic-pae and a working graphical interface. I could then removed the third party NVIDIA driver and rebooted into 2.6.35-22-generic-pae with low resolution graphics. Finally I re-installed the recommended NVIDIA driver. Phew it's working again.

---

### Post by thered on 2010-10-11
Since upgrading from 10.04 to 10.10 I get this same message twice:

modprobe:FATAL: could not load /lib/modules/2.6.35-22-generic/modules.dep No such file or directory

It then hangs for a good 20secs or so before booting to Ubuntu.

I also have to put my password into Keyring now whereas before I didn't - this is very annoying.

Ideas?

---

### Post by mörgæs on 2010-10-11
How does the system behave if you try the tests described in the first post?

---

### Post by thered on 2010-10-11
I didn't think them pertinent.  I had a working system with 10.04. I did the recommended thing and did a network upgrade.  I received no alerts during the procedure, I have changed nothing since. <headscratching>

PS I resolved the keyring issue by stopping a bunch of startup apps.

Edit: Seems there is a bug, just checked the launchpad site: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421")

---

### Post by vchapman on 2010-10-11
I have upgraded from 10.04 to 10.10. However, on the first go around I terminated the upgrade before it was finished. I was able to go back to an old version and the upgrade restarted and terminated properly, I think.

I have two problems at this point.

First, the system always boots into tty mode rather than graphics mode. How do I change this?

Second, when I run the failsafe graphics mode, it appears that my nvidia xconfiguration file is missing or otherwise corrupt. So I can't get my monitor into the correct resolution. How do I fix this.

Thanks for your help.

---

### Post by Terrycymru on 2010-10-11
Can anyone clarify the position of WUBI upgrades from 10.04 to 10.10 **where legacy GRUB is still used in 10.04** and where WUBI is installed on the Windows partition? I have followed all the bugs including #653134 and it seems that these are essentially issues with GRUB 2.

So, unless the upgrade changes legacy GRUB to GRUB 2 there should be no problem? I have not tested an upgrade yet. Has anyone been brave enough?

---

### Post by Legend28469 on 2010-10-11
I upgraded, from 10.04 to 10.10... I installed the new grub I dual boot 7 and Ubuntu...

so.. When I goto boot into Ubuntu (which was successfully installed).. it is terribly dark.. and cranking up the brightness/contrast does nothing..

I can login.. (if u look closely enough.. but.. from then I can't do anything (possibly due to the fact that I can BARELY see anything)..

any ideas?

---

### Post by jackdale on 2010-10-12
> **Legend28469 said:**
> I upgraded, from 10.04 to 10.10... I installed the new grub I dual boot 7 and Ubuntu...

so.. When I goto boot into Ubuntu (which was successfully installed).. it is terribly dark.. and cranking up the brightness/contrast does nothing..

I can login.. (if u look closely enough.. but.. from then I can't do anything (possibly due to the fact that I can BARELY see anything)..

any ideas?

Have you tried changing the settings on your GPU driver?  I have and nvidia card and had similar problems with an old screen.  Fiddling with the GPU settings did the trick for me.


On a separate matter...


 if I follow step 8, it would obviously not re-install my old programs.  That's fair enough.  However, what if I had a paid-for program, such as Fluendo, downloaded from the software centre, what would be the deal there?  do i need to buy it again?

I wish that upgrading was as smooth as just pressing the upgrade button.  Unfortunately, I've had problems every time I upgrade to the next ubuntu version.  A fresh install always seems to be the answer.  My laptop is a Mac, and upgrading on this is very simple: I put the CD into the drive and the upgrade pretty much takes care of itself.  And everything works,  even after Leopard (32 bit) update to Snow Leopard (64 bit)!

---

### Post by mörgæs on 2010-10-12
> **jackdale said:**
> 
If I follow step 8, it would obviously not re-install my old programs.  That's fair enough.  However, what if I had a paid-for program, such as Fluendo, downloaded from the software centre, what would be the deal there?  do i need to buy it again?

I don't know since I have never bought a program, but I expect that one gets a registration key when buying, which will activate the program again after a reinstall. 

> **jackdale said:**
> 
I wish that upgrading was as smooth as just pressing the upgrade button.  Unfortunately, I've had problems every time I upgrade to the next ubuntu version.  A fresh install always seems to be the answer.
It is also my experience. If people want to explore the hidden corners of Ubuntu, it is a good (though sometimes long) exercise to troubleshoot an upgrade, but in the fora we tend to forget that not all users are keen on this challenge. If we don't help the user who just wants to get a system running without any tweaking (like the vast majority of Windows and Mac users), Ubuntu will never be big.

---

### Post by sHaDYvB on 2010-10-12
@mörgæs

I've had the issue with wubi installed in a secondary partition, after upgrading from 10.04 to 10.10 i couldn't boot the ubuntu and it just restarted..

following a reply in the forums ( can't get back to the url ) i copied wubildr* files to the D partition and that solved the problem.

Please put it as a quick fix in your main post as there are many people having the same problem and cannot fix it.

---

### Post by JackAcid on 2010-10-12
I did the stupid thing and upgraded a wubi install from 10.04 ->10.10 and after following the instructions was able to boot into my fresh new 10.10 install.

HOWEVER... this morning I dutifully ran the kernel security updates.. on my new 10.10 install .. and got the same problem. fortunatly I had the instructions printed out and was able to again boot into ubuntu.

Thinking to permanently fix the problem I went looking into the forums and wubi install guide to figure out how to make the wubi install a real partition install and it does not appear there is ANY way to do this (or any other kind of update/upgrade) with a wubi 10.04 virtual system.

Am I missing something? Or will I have to bite the bullit and do a fresh 10.10 install on a new partiton? I would rather not, but sometimes I guess there is no other way.

---

### Post by bcbc on 2010-10-12
> **JackAcid said:**
> I did the stupid thing and upgraded a wubi install from 10.04 ->10.10 and after following the instructions was able to boot into my fresh new 10.10 install.

HOWEVER... this morning I dutifully ran the kernel security updates.. on my new 10.10 install .. and got the same problem. fortunatly I had the instructions printed out and was able to again boot into ubuntu.

Thinking to permanently fix the problem I went looking into the forums and wubi install guide to figure out how to make the wubi install a real partition install and it does not appear there is ANY way to do this (or any other kind of update/upgrade) with a wubi 10.04 virtual system.

Am I missing something? Or will I have to bite the bullit and do a fresh 10.10 install on a new partiton? I would rather not, but sometimes I guess there is no other way.

Howto migrate wubi install to partition: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354) (caveat, I haven't yet tested this on Maverick - only on a very early alpha maverick version).

---

### Post by Legend28469 on 2010-10-12
> **jackdale said:**
> Have you tried changing the settings on your GPU driver?  I have and nvidia card and had similar problems with an old screen.  Fiddling with the GPU settings did the trick for me.


On a separate matter...


 if I follow step 8, it would obviously not re-install my old programs.  That's fair enough.  However, what if I had a paid-for program, such as Fluendo, downloaded from the software centre, what would be the deal there?  do i need to buy it again?

I wish that upgrading was as smooth as just pressing the upgrade button.  Unfortunately, I've had problems every time I upgrade to the next ubuntu version.  A fresh install always seems to be the answer.  My laptop is a Mac, and upgrading on this is very simple: I put the CD into the drive and the upgrade pretty much takes care of itself.  And everything works,  even after Leopard (32 bit) update to Snow Leopard (64 bit)!

Actually the problem seems to be with the new kernel, because I went back one kernel and I am able to use Ubuntu 10.10 on it, but on the new kernel the problems start occurring again.

---

### Post by crienoloog on 2010-10-13
Upgraded from wubi installed 10.04 to 10.10 and after upgrading from 10.04 to 10.10 i couldn't boot the ubuntu and it just restarted..
I tried BCBC option to boot from CD and run gksu gedit the grub.cfg but there wasn't one at all in the grub folder.
The sudo mkdir /win and replacement with mounting virtual disk did not work for me at all... Sorry if I sound confusing but am a pretty noob in this field.
I can boot Windows 7 by the way... thnk G....
The wubi ldr swap from one partition to other does not work for me either because it already is on same partition.
Hope this helps anyone, and getting it resolved a.s.a.p.
I'm sure more noobs are tearing their hair out at this moment...
Thanks for any help.


Update: I finaly was able to edit my grub.cfg... restarted but problem stays. I can start Windows 7 in first grub, when I sellect Ubuntu; it will give me very fast two errors [can't read so fast] then black screen and back to start up and again first grub screen.
I was up to date with the latest 10.04 updates.
I see the root.disk in Windows [some 29Gb] and though I have enough space on seperate ext. HD it says it can't make a copy due to space... so I can't reinstall without loosing important data.

HELP......

---

### Post by Legend28469 on 2010-10-13
Umm... well.. I don't know if this helps anyone.. but.. I tried playing around yesterday.. and I figured that plugging my monitor into my laptop (while booting).. actually brings the screen up on both my monitor and my laptop.. and then if i unplug the monitor at the login screen.. my laptop works like normal... ... ... if I try to boot without monitor plugged in and just use the laptop screen.. my problem reoccurs... ... ... ... ...

Weird eh?

---

### Post by md10 on 2010-10-13
Upgraded from 10.04, rebooted.. and now VMware Workstation 7 doesn't work. Having error: Unable to build kernel module.

TIA for help.

md10

SOLVED by installing the patch command

---

### Post by James Keating on 2010-10-13
Re: 1 - Does the machine like the version of Ubuntu to which you are upgrading?

You should amend this to say that the ability to run Ubuntu from a live CD means only that an install CAN SOMEHOW EVENTUALLY be made to run properly. It might be easy but it might take a lot of work -- back up everything first. I had fatal errors with 10.04 (booting into a blank screen) and 10.10 (booting into an X failure and a command line). The CDs ran fine after the installs failed, and made my system more accessible for fixing. 

If the CD runs but the install doesn't, then yes,
4. Ask the forum
My 10.10 problem was shared on Oct. 12 by exactly one person, who had no solution. Googling produced nothing. I figured that time would produce more people and some advice, so I waited and tinkered. The next evening, I found a solution. In the meantime, several other people had solutions of their own.

---

### Post by dre1187 on 2010-10-14
i did a fresh install from 10.10 on my ocz agility2 and it either doesnt boot or it hangs for like 5 mins then i can log in. I think my ssd drive and the kernel are the problem.

I was running kernel 2.6.32 fine on 10.04 ssd drive was extremely fast.

---

### Post by mörgæs on 2010-10-14
> **James Keating said:**
> Re: 1 - Does the machine like the version of Ubuntu to which you are upgrading?

You should amend this to say that the ability to run Ubuntu from a live CD means only that an install CAN SOMEHOW EVENTUALLY be made to run properly. It might be easy but it might take a lot of work -- back up everything first. I had fatal errors with 10.04 (booting into a blank screen) and 10.10 (booting into an X failure and a command line). The CDs ran fine after the installs failed, and made my system more accessible for fixing. 


Hi, thanks for your response. 

The guide is intended to be a one-size-fits-almost-all manual. Yes, there are a few exceptions where a CD boots fine but the install doesn't, but rather than dealing with this in the guide I would prefer that people just open a thread in the forum. 

If all exceptions are covered in the guide, it will be to long and cumbersome to use.

---

### Post by mörgæs on 2010-10-14
> **dre1187 said:**
> i did a fresh install from 10.10 on my ocz agility2 and it either doesnt boot or it hangs for like 5 mins then i can log in. I think my ssd drive and the kernel are the problem.

I was running kernel 2.6.32 fine on 10.04 ssd drive was extremely fast.

It could be related to the SSD, Ureadahead or a combination of the two. I have not tried SSD's myself, so I can not give a precise answer, but maybe the best is simply staying with 10.04 for a few more months.

---

### Post by dre1187 on 2010-10-14
yeh thats what i plan on doing :/ I was really looking forward to using the multitouch features and diskTRIM features in the 2.6.35 kernel. I really think that it is a kernel issue that 2.6.35 has. When i was on 10.04 and manually installed the 2.6.35 kernel my box wouldnt boot. Hopefully a fix is released soon or they start to offer the features in 2.6.35 in 2.6.32

---

### Post by danielsender on 2010-10-14
Hi,

I just upgraded a perfectly running 10.04 on my Dell Precision M50 laptop with NVdia Quadro4 to 10.10. I also ran into the bug described on [https://bugs.launchpad.net/bugs/626974](https://bugs.launchpad.net/bugs/626974) .

```
[    22.036] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support)
[    22.036] Current version of pixman: 0.18.4
[    22.036]    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    22.037] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.037] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 13 22:46:54 2010
[    22.037] (==) Using config file: "/etc/X11/xorg.conf"
[    22.037] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.038] (==) ServerLayout "Default Layout"
[    22.038] (**) |-->Screen "Default Screen" (0)
[    22.038] (**) |   |-->Monitor "Configured Monitor"
[    22.039] (**) |   |-->Device "Configured Video Device"
[    22.039] (**) |-->Input Device "Keyboard0"
[    22.039] (**) |-->Input Device "Mouse0"
[    22.039] (==) Automatically adding devices
[    22.039] (==) Automatically enabling devices
[    22.122] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.122]    Entry deleted from font path.
[    22.253] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    22.253] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.253] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    22.253] (WW) Disabling Keyboard0
[    22.253] (WW) Disabling Mouse0
[    22.253] (II) Loader magic: 0x81f8e00
[    22.253] (II) Module ABI versions:
[    22.253]    X.Org ANSI C Emulation: 0.4
[    22.253]    X.Org Video Driver: 8.0
[    22.253]    X.Org XInput driver : 11.0
[    22.253]    X.Org Server Extension : 4.0
[    22.255] (--) PCI:*(0:1:0:0) 10de:017c:1028:00d5 rev 163, Mem @ 0xfc000000/16777216, 0xe0000000/134217728, 0xdff80000/524288, BIOS @ 0x????????/131072
[    22.257] (II) Open ACPI successful (/var/run/acpid.socket)
[    22.258] (II) "extmod" will be loaded by default.
[    22.258] (II) "dbe" will be loaded by default.
[    22.258] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    22.258] (II) "record" will be loaded by default.[    22.258] (II) "dri2" will be loaded by default.
[    22.258] (II) LoadModule: "glx"
[    22.265] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    22.341] (II) Module glx: vendor="NVIDIA Corporation"
[    22.341]    compiled for 4.0.2, module version = 1.0.0
[    22.341]    Module class: X.Org Server Extension
[    22.341] (II) NVIDIA GLX Module  96.43.18  Tue Jul 13 13:31:40 PDT 2010
[    22.341] (II) Loading extension GLX
[    22.341] (II) LoadModule: "extmod"
[    22.365] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    22.366] (II) Module extmod: vendor="X.Org Foundation"
[    22.366]    compiled for 1.9.0, module version = 1.0.0
[    22.366]    Module class: X.Org Server Extension
[    22.366]    ABI class: X.Org Server Extension, version 4.0
[    22.366] (II) Loading extension MIT-SCREEN-SAVER
[    22.366] (II) Loading extension XFree86-VidModeExtension
[    22.366] (II) Loading extension XFree86-DGA
[    22.366] (II) Loading extension DPMS
[    22.366] (II) Loading extension XVideo
[    22.366] (II) Loading extension XVideo-MotionCompensation
[    22.366] (II) Loading extension X-Resource
[    22.366] (II) LoadModule: "dbe"
[    22.367] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    22.367] (II) Module dbe: vendor="X.Org Foundation"
[    22.367]    compiled for 1.9.0, module version = 1.0.0
[    22.367]    Module class: X.Org Server Extension
[    22.367]    ABI class: X.Org Server Extension, version 4.0
[    22.367] (II) Loading extension DOUBLE-BUFFER
[    22.367] (II) LoadModule: "record"
[    22.368] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    22.368] (II) Module record: vendor="X.Org Foundation"
[    22.368]    compiled for 1.9.0, module version = 1.13.0
[    22.368]    Module class: X.Org Server Extension
[    22.368]    ABI class: X.Org Server Extension, version 4.0
[    22.368] (II) Loading extension RECORD
[    22.368] (II) LoadModule: "dri"
[    22.369] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    22.369] (II) Module dri: vendor="X.Org Foundation"
[    22.369]    compiled for 1.9.0, module version = 1.0.0
[    22.369]    ABI class: X.Org Server Extension, version 4.0
[    22.369] (II) Loading extension XFree86-DRI
[    22.369] (II) LoadModule: "dri2"
[    22.370] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.370] (II) Module dri2: vendor="X.Org Foundation"
[    22.370]    compiled for 1.9.0, module version = 1.2.0
[    22.370]    ABI class: X.Org Server Extension, version 4.0
[    22.370] (II) Loading extension DRI2
[    22.370] (II) LoadModule: "nvidia"
[    22.370] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    22.371] dlopen: /usr/lib/xorg/extra-modules/nvidia_drv.so: undefined symbol: miEmptyData
[    22.371] (EE) Failed to load /usr/lib/xorg/extra-modules/nvidia_drv.so
[    22.372] (II) UnloadModule: "nvidia"
[    22.372] (EE) Failed to load module "nvidia" (loader failed, 7)
[    22.372] (EE) No drivers available.
[    22.372]
Fatal server error:
[    22.372] no screens found
[    22.372]
Please consult the The X.Org Foundation support
     at http://wiki.x.org
 for help.
[    22.372] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    22.372]
``` I still don't understand if there is a solution available for running the nvidia drivers, if not, how do I do to run the nv drivers?

Thanks in advance,

Daniel

---

### Post by danielsender on 2010-10-14
Hi,

I was able to switch to the "nv" driver by simply changing the entry "nvidia" to "nv" in the xorg.conf file. However I would still like to have the accelerated driver running. I have one more issue: in 10.10 when I restart all the processes that are being shutdown appear on the screen, how to I stop this from happening? Thanks,

Daniel

---

### Post by svegress on 2010-10-15
> **bcbc said:**
>  I noticed some reports that copying c:\ubuntu\winboot\wubildr over c:\wubildr fixed the problem. It's unconfirmed, but easy to try without using live CD. (If you installed on another 'drive' change as appropriate).
With gratitude everyone,  the copying of the wubibldr file to the Windows root directory worked for me.  
Booting with Windows 7, I renamed c:\wubildr as a precaution and made sure that I only copied and not moved C:\ubuntu\winboot\wubildr to  c:\   Three minutes work as opposed to a lot of messing around with files and partitioning that I barely understand. Then a simple restart and Ubuntu with all my files intact came up as normal.   I will now write a note for filing in the computer's documentation box so I will discover the answer again the next time wubi refuses at the starting gate. 

Wubi is a wonderfully reliable half way house--except when it stuffs up like this.  I can remember going through much the same pain when I first moved towards Ubuntu trying to use the beta wubi.  I learnt that time that a good, uptodate backup is essential insurance.  If I hadn't found this set of posts I would have been reconstructing from the ground up and then hoping that my incremental backup done with Simple Backup over the last few days had worked. 

You might ask why I bother to stay with Wubi instead of partitioning for a dual boot. A real gotcha from Microsoft: the new Compaq Presario CQ56 has four partitions on the internal disk taken up by Windows and that is the limit to the number of partitions allowed.  If anyone knows a way around this, I am listening.

---

### Post by crienoloog on 2010-10-15
@svegress: lucky for you...
However it didn't work for me... I already had a newer wubildr in my Windows root folder, but to test I renamed it wubildr(2) and copied the one from /ubuntu/winboot folder...
Ubuntu still gives me the double error: file not found and returns start-up.

---

### Post by bcscomp on 2010-10-15
Just a question to all who have upgraded from 10.04 to 10.10. WHY?? when it is so easy to backup your home/s directory/s followed by:
pkg --get-selections > installed-software
And if you wanted to use the list to reinstall this software on a fresh ubuntu setup:
dpkg --set-selections < installed-software
if Ubuntu 10.04 worked on your laptop/desktop PC a clean install will almost certainly work with 10.10 
The secret to Linux working on any computer, including Ubuntu is CHOOSE YOUR HARDWARE!!!
Please do yourselves a favor.

---

### Post by crienoloog on 2010-10-15
> **bcbc said:**
> From the release notes:


If you have already upgraded and find that the system reboots or hangs when selecting Ubuntu (with or without error messages), then a workaround is to boot a live CD, [loop mount the wubi root.disk]("https://wiki.ubuntu.com/WubiGuide#How can I access my Wubi install and repair my install if it won't boot?"), edit the grub.cfg (gksu gedit /*mountpoint*/boot/grub/grub.cfg) and remove all lines above the first "menuentry".

If you get a read-only error on grub.cfg, then either use vi or nano, or before running gedit first run: 
sudo chmod +w /*mountpoint*/boot/grub/grub.cfg

Note: if you install kernel updates, new kernels, remove kernels, run update-grub etc. you'll have to reapply the workaround as grub.cfg is regenerated automatically. It's easier to do this before you reboot (or you'll have to use the live CD again).

PS I noticed some reports that copying c:\ubuntu\winboot\wubildr over c:\wubildr fixed the problem. It's unconfirmed, but easy to try without using live CD. (If you installed on another 'drive' change as appropriate).

@bcbc:
Please see my earlier post as well...
Did a regular update of a wubi installed 10.04 and the update within to 10.10
I can still start Windows.
I did your option to boot from CD and run gksu gedit the grub.cfg. 
First couldn't even find the grub.cfg then copied the one from the liveCD [if I remember correctly] and edited it. Did not work.
Copied the wubildr from the ubuntu folder - which was older then the new one already in the Windows root folder... No good.
Could use the Ubuntu 10.04 and 10.10 on my HP Probook 4510s with Windows 7 Prof. without problems.... after your -o loop code, I cannot use either CD anymore. Both give errors or hang - meaning something is seriously wrong in Windows.
I stopped the automatic start of HP tools as well...
This morning I found a new update of Windows on my machine taking place and after restart an automated check of the harddisk... something going on at MS?

All the best and thanks.

---

### Post by bcbc on 2010-10-15
> **crienoloog said:**
> @bcbc:
Please see my earlier post as well...
Did a regular update of a wubi installed 10.04 and the update within to 10.10
I can still start Windows.
I did your option to boot from CD and run gksu gedit the grub.cfg. 
First couldn't even find the grub.cfg then copied the one from the liveCD [if I remember correctly] and edited it. Did not work.
Copied the wubildr from the ubuntu folder - which was older then the new one already in the Windows root folder... No good.
Could use the Ubuntu 10.04 and 10.10 on my HP Probook 4510s with Windows 7 Prof. without problems.... after your -o loop code, I cannot use either CD anymore. Both give errors or hang - meaning something is seriously wrong in Windows.
I stopped the automatic start of HP tools as well...
This morning I found a new update of Windows on my machine taking place and after restart an automated check of the harddisk... something going on at MS?

All the best and thanks.
crienoloog, I'm sorry you're having problems.

I think it's important to try to understand the instructions, and if you have any questions or the instructions don't work for you,  then stop what you are doing and come back and ask for help. I really can't tell after the fact what has happened from your description - i.e. what grub.cfg you may have copied, or how loop mounting the root.disk may have broken two read-only live CDs

Booting the live CD shouldn't be affected by anything in those instructions and isn't related to windows booting, or windows updates. The CD is booted directly from the computer's BIOS and isn't affected by any OS installed on your computer.

---

### Post by crienoloog on 2010-10-15
I'm not saying its your fault, don't misunderstand me... I just wrote in the hope you can do something with it for other people too...
So what you are saying is that maybe my BIOS is corrupted in some way? Part of the error I saw passing by trying to boot up from the LiveCD was something about a loop thing. [sorry I'm not technical enough]

---

### Post by alanraymt on 2010-10-15
> **bcbc said:**
> From the release notes:


If you have already upgraded and find that the system reboots or hangs when selecting Ubuntu (with or without error messages), then a workaround is to boot a live CD, [loop mount the wubi root.disk]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?"), edit the grub.cfg (gksu gedit /*mountpoint*/boot/grub/grub.cfg) and remove all lines above the first "menuentry".

If you get a read-only error on grub.cfg, then either use vi or nano, or before running gedit first run: 
sudo chmod +w /*mountpoint*/boot/grub/grub.cfg

Note: if you install kernel updates, new kernels, remove kernels, run update-grub etc. you'll have to reapply the workaround as grub.cfg is regenerated automatically. It's easier to do this before you reboot (or you'll have to use the live CD again).

PS I noticed some reports that copying c:\ubuntu\winboot\wubildr over c:\wubildr fixed the problem. It's unconfirmed, but easy to try without using live CD. (If you installed on another 'drive' change as appropriate).
[SIZE=5]
I tried a simple [/SIZE]copying c:\ubuntu\winboot\wubildr over c:\wubildr [SIZE=6] [SIZE=5]and I can assure it works. thanks alot BCBC[/SIZE][/SIZE]

---

### Post by bcbc on 2010-10-15
> **crienoloog said:**
> I'm not saying its your fault, don't misunderstand me... I just wrote in the hope you can do something with it for other people too...
So what you are saying is that maybe my BIOS is corrupted in some way? Part of the error I saw passing by trying to boot up from the LiveCD was something about a loop thing. [sorry I'm not technical enough]

I'm not assuming you're saying that. I just want to make the point that if something doesn't look right, it's best to stop and come back for more info; and also that it's unlikely that the live CD or windows could be affected in that way. Which points to some other cause.
I also doubt your bios is corrupted. That seems unlikely.

But if you booted up from the live CD before, and now you cannot - I can't explain that either unless you scratched the cd. Check the surface of the cd and clean it if necessary.

When the computer starts up enter BIOS and check the boot order to ensure the CDROM is before the internal hard drive. Then let it boot and report back any errors. If it boots straight from the hard drive, make sure the CD drive light is coming on and you hear the disk spinning. If it does but bypasses it, you'll have to burn a new Ubuntu CD. If not, it might be a hardware problem.

Once you get it booting post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net")and I'll see if I can figure out what's going on.

---

### Post by mörgæs on 2010-10-15
> **bcscomp said:**
> Just a question to all who have upgraded from 10.04 to 10.10. WHY?? when it is so easy to backup your home/s directory/s followed by:
pkg --get-selections > installed-software
And if you wanted to use the list to reinstall this software on a fresh ubuntu setup:
dpkg --set-selections < installed-software
if Ubuntu 10.04 worked on your laptop/desktop PC a clean install will almost certainly work with 10.10 
The secret to Linux working on any computer, including Ubuntu is CHOOSE YOUR HARDWARE!!!
Please do yourselves a favor.

Good point. I have added this to the guide.

I would say that the secret is 'choose your software' and don't expect the latest Ubuntu release to be the only option.

---

### Post by crienoloog on 2010-10-15
Her you go:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   452,743,829   452,741,782   7 HPFS/NTFS
/dev/sda2         452,749,312   484,206,591    31,457,280   7 HPFS/NTFS
/dev/sda3         484,206,592   488,390,655     4,184,064   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002   6 FAT16


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   488,392,064   488,392,002   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       0bbfe133-4361-4804-bcc1-6902066703f6   ext4                                     
/dev/sda1        01CB4CF123EAC990                       ntfs                                     
/dev/sda2        CCC880B2C8809C78                       ntfs       HP_RECOVERY                   
/dev/sda3        C474-B594                              vfat       HP_TOOLS                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        15F3-3C5B                              vfat       FREECOM HDD                   
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        15F3-3C5B                              vfat       FREECOM HDD                   
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/FREECOM HDD       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdc1        /media/FREECOM HDD_      vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


======================== sda1/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 01cb4cf123eac990
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 01cb4cf123eac990
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=nl
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 01cb4cf123eac990
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 01cb4cf123eac990
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 01cb4cf123eac990
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 01cb4cf123eac990
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 01cb4cf123eac990
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set ccc880b2c8809c78
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

============================= sda1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda1/Wubi: Location of files loaded by Grub: =================


   3.6GB: boot/grub/grub.cfg
  10.2GB: boot/initrd.img-2.6.32-25-generic
  10.7GB: boot/initrd.img-2.6.35-22-generic
   6.9GB: boot/vmlinuz-2.6.32-25-generic
   7.8GB: boot/vmlinuz-2.6.35-22-generic
  10.7GB: initrd.img
  10.2GB: initrd.img.old
   7.8GB: vmlinuz
   6.9GB: vmlinuz.old

```

---

### Post by bcbc on 2010-10-15
> **crienoloog said:**
> Her you go:
...


So that looks ok - try the workaround to edit the grub.cfg - it's still the original. From a live cd run the following:
```
sudo mkdir -p /media/win
sudo mount /dev/sda1 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
sudo cp /mnt/boot/grub/grub.cfg /mnt/boot/grub/grub.cfg.backup
sudo chmod +w /mnt/boot/grub/grub.cfg
gksu gedit /mnt/boot/grub/grub.cfg

```
Delete everything up until the lines (and leave everything after alone):
> ### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-22-generic" {


Save, exit, reboot, select Ubuntu. Enter on first entry.

PS also edit your previous post. Put a [[SIZE="1"] [/SIZE]CODE] before the bootinfoscript results and a [/CODE] after it. That makes it more readable.

---

### Post by crienoloog on 2010-10-16
Burnt a new CD 10.04.1 [32 bit and verified to be OK] to be save...
Restarted on Live CD and got this:
```

BusyBox v.1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) uilt-in shell(ash)
Enter 'help' for a list of built-in commands.

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squasfs

```

---

### Post by bcbc on 2010-10-16
> **crienoloog said:**
> Burnt a new CD 10.04.1 [32 bit and verified to be OK] to be save...
Restarted on Live CD and got this:


Use the live CD you used to run bootinfoscript. All you need to do is a minor edit to grub.cfg.

---

### Post by tomdkat on 2010-10-16
> **bcscomp said:**
> if Ubuntu 10.04 worked on your laptop/desktop PC a clean install will almost certainly work with 10.10 
I certainly hope so.  My upgrade from 10.04 (64-bit) to 10.10 (64-bit) hasn't gone smoothly at all.  Right now, I'm plagued with two main issues:
[list]
[*]Frequent and random hangs (even the mouse won't move and ctrl-alt-del does nothing).
[*]Not being able to mount the internal SATA drive ([bug #634407](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/634407))
[/list]
So, I'm going to see if I can give a clean install an attempt on a different hard drive.  If the hangs and SATA drive issue persist, I'll revert back to Ubuntu 10.04 and wait for the subsequent release.

Peace...

---

### Post by crienoloog on 2010-10-16
OKAY !!!!
Thank you bcbc... But now that I have an edited grub file... Howe is that for the future? Do I need to worry on the next update or do I need to do something myself?
Thanks again and all the best. Now I'm going to back up... ;)

---

### Post by bcbc on 2010-10-16
> **crienoloog said:**
> OKAY !!!!
Thank you bcbc... But now that I have an edited grub file... Howe is that for the future? Do I need to worry on the next update or do I need to do something myself?
Thanks again and all the best. Now I'm going to back up... ;)

Yes it's a workaround. Whenever you install a new kernel or remove and old one it automatically regenerates grub.cfg. So, either don't update or, after applying updates click on "Restart later" and then go and edit your grub.cfg.

---

### Post by MishMich on 2010-10-17
A few months ago, I installed 10.04 (Intel) 64-bit from live CD in the UK within the Windows 7 filesystem.  I set this up to add Ubuntu as a boot option after W7, and that takes me into a boot menu for Ubuntu.  I am now in a different country, and followed the instructions to run the update.  all looked to go OK, and if I select W7 that boots OK.  But, when I select Ubuntu, it just reboots the PC back to the boot menu for W7 or Ubuntu.  I don't have a live CD for 10.10, but may be able to get hold of a 10.04 or other linux (debian, PCLOS, etc.) live CD's.  How do I get the Ubuntu option in the Windows bootloader to load up the Ubuntu bootloader, and what do I need to do to get that to load up the upgraded 10.10 on the Windows filesystem?  Is this possible?

I also have an dual-boot XP & 10.04 32-bit installation on a netbook, installed on their own partitions, but am reluctant to upgrade in case the same sort thing happens.  On the netbook install, there is only a single bootloader for windows or ubuntu.

Thanks

---

### Post by bcbc on 2010-10-17
> **MishMich said:**
> A few months ago, I installed 10.04 (Intel) 64-bit from live CD in the UK within the Windows 7 filesystem.  I set this up to add Ubuntu as a boot option after W7, and that takes me into a boot menu for Ubuntu.  I am now in a different country, and followed the instructions to run the update.  all looked to go OK, and if I select W7 that boots OK.  But, when I select Ubuntu, it just reboots the PC back to the boot menu for W7 or Ubuntu.  I don't have a live CD for 10.10, but may be able to get hold of a 10.04 or other linux (debian, PCLOS, etc.) live CD's.  How do I get the Ubuntu option in the Windows bootloader to load up the Ubuntu bootloader, and what do I need to do to get that to load up the upgraded 10.10 on the Windows filesystem?  Is this possible?

I also have an dual-boot XP & 10.04 32-bit installation on a netbook, installed on their own partitions, but am reluctant to upgrade in case the same sort thing happens.  On the netbook install, there is only a single bootloader for windows or ubuntu.

Thanks
Boot windows, copy/rename c:\wubildr to c:\wubildr.backup 
Then copy c:\ubuntu\winboot\wubildr to c:\wubildr
Reboot. 
If that works you don't need a live CD.

On the netbook it sounds like you don't have wubi. So an upgrade would probably be ok. But I don't recommend upgrading without a backup or a live CD in case you need to reinstall grub or something weird happens.

---

### Post by Dubbayoo on 2010-10-21
I upgraded from 10.04 to 10.10 and now my keyboard (Logitech MK700 wireless) doesn't work completely. I can no longer do ALT + PRINTSCREEN. PRINTSCREEN works fine and the ALT key works with other combos.

---

### Post by ubontik on 2010-10-21
I upgraded from Ubuntu 10.04 to 10.10. The installation was fine. I restarted the computer and it opened in terminal-like view with command line on black screen. How to switch to GNOME?
When I ran startx I got the following message "Failed to load module "nvidia" (loader failed. 7)". 
I checked under /usr/lib/xorg/extra-modules the driver is there. 10.04 was running fine with this driver.

Thanks

---

### Post by phoenixfire76 on 2010-10-21
I've upgraded from 10.04 Netbook to 10.10 Netbook and my USB external DVD Burner is no longer automounting.

Inserting a CD/DVD results in the drive being read and the drive icon disappearing from the File Manager menu......I have confirmed that the drive works on the same hardware under different OS...

Any help would be appreciated.

---

### Post by rainbow99984 on 2010-11-01
Hi, well this is not an Error just performance - Upgraded to 10.10 from 10.04 so far no problem at all.  
My system boot time upto the login screen is very good. but after login it takes considerable 1~2 min. to show the desktop, any idea? my guess is its because of compiz that I'm running as art-manager fail to open if i click on it to open from System->Pref.->Art-Manager.
In System-Monitor i can see Compiz and gtk-window-decorator running normally. 
Thanks rahul

---

### Post by jackdale on 2010-11-01
what are you hardware specs?  It shouldn't take that long to log in even with compiz.
on similar hardware, my ubuntu 10.10 makes my os x 10.6.4 look slow and dated.

I run ubuntu desktop with compiz, emerald, cairo-dock, high pixel background and it logs in in a flash.

4GB ram, 2 x 2.6GHz intel CPU, 1GB NVidia GPU (by no means a fast system)

I have had slow log ins before and the following seemed to cause problems:

1) using the PPA version of compiz or cairo-dock (ie the testing PPA) - suggest use the official release.
2) having kubuntu-desktop installed in ubuntu usin the gdm or kdm
3) upgrade errors

you could try a fresh install (but remember to back-up first!)

---

### Post by ejog on 2010-11-01
I upgraded from 10.04 to 10.10 and now my scanner no longer works. It's connected by Firewire (IEEE 1394) and worked perfectly with 10.04 and below for the last couple of years, using Vuescan. Now Vuescan and Xsane both say 'no scanner connected'.

Is there a problem with IEEE connections on 10.10? I can't find a reference to it in the 'known issues' thread.

Any help appreciated.

---

### Post by MishMich on 2010-11-04
> **bcbc said:**
> Boot windows, copy/rename c:\wubildr to c:\wubildr.backup 
Then copy c:\ubuntu\winboot\wubildr to c:\wubildr
Reboot. 
If that works you don't need a live CD.

On the netbook it sounds like you don't have wubi. So an upgrade would probably be ok. But I don't recommend upgrading without a backup or a live CD in case you need to reinstall grub or something weird happens.

Apologies for the delay in responding. Was holding back till I had time to attend to this.  Not had time.  I'm thinking I may wait until I get access to a live CD of 10.10, and go for a fresh install onto the file/partition created for the 10.04.

Thanks.

---

### Post by gulmer on 2010-11-10
This problem deals with the mouse.Upgraded from 10.04 to 10.10,64 bit.The problem is the mouse's left button stops working,and the scroll wheel stops functioning.Right button works and the pointer works.To fix the problem,I removed the USB cable(wireless mouse and keyboard)for 3 seconds and plug it back in,and everything works again.This only happened with the 10.10 upgrade.I would like to find a permanent fix for this,for the wife would not want to deal with unplugging and replugging,I don't care for it either.
 This is the only problem I've encountered so far with this upgrade.

---

### Post by matt! on 2010-11-13
Choosing 2.6.32-25 I'm being dumped to busybox/initamfs having upgraded my wubi installation. 

Replacing the wubildr doesn't work for me
(I'm using a special wubildr that gets around another bug that is still to be fixed - see my old posts for info on that one)

Editing the grub.cfg does not work for me.

Luckily I can still boot using a kernel 2.6.32-24

What is the best way to stay abreast of this wubi mess and hear about solutions to these problems?

Thanks,
matt

---

### Post by bcbc on 2010-11-13
> **matt! said:**
> Choosing 2.6.32-25 I'm being dumped to busybox/initamfs having upgraded my wubi installation. 

Replacing the wubildr doesn't work for me
(I'm using a special wubildr that gets around another bug that is still to be fixed - see my old posts for info on that one)

Editing the grub.cfg does not work for me.

Luckily I can still boot using a kernel 2.6.32-24

What is the best way to stay abreast of this wubi mess and hear about solutions to these problems?

Thanks,
matt
Are you sure you upgraded - 2.6.32-25 is a lucid kernel - maybe you just ran lucid updates.

Regarding wubildr, I have no idea... I think the only person who knows what's going on is Colin Watson and he is a pretty busy person it seems. 

But your problem sounds more like an issue with the initramfs. Boot the -24 kernel and update the -25 as follows:
sudo update-initramfs -k 2.6.32-25-generic
See if that fixes it.

---

### Post by matt! on 2010-11-13
Ah, right. I guess that shows how limited my Ubuntu knowledge is

I had to do this, with the -u option
```
sudo update-initramfs -u -k 2.6.32-25-generic
```

But there is no change to my situation.

The exact error message I'm getting is one about the NTFS volume not being able to be mounted. A full chkdsk /r made no difference, either

---

### Post by bcbc on 2010-11-13
> **matt! said:**
> Ah, right. I guess that shows how limited my Ubuntu knowledge is

I had to do this, with the -u option
```
sudo update-initramfs -u -k 2.6.32-25-generic
```

But there is no change to my situation.

The exact error message I'm getting is one about the NTFS volume not being able to be mounted. A full chkdsk /r made no difference, either

OK too bad :( The chkdsk won't help - if that's the problem then nothing would boot. So somehow you have an issue with the latest kernel. You could try purging and reinstalling the -25 kernel. I'm not sure if this would do anything. I don't think this is related to wubi as there were a bunch of the same initramfs/busybox prompts when the -24 kernel came out and it affected both wubi and normal installs.

At the worst, just uninstall the -25 and then you won't have to manually select the -24 each time. Unless there's something you need on the -25 that's not on the -24.

---

### Post by matt! on 2010-11-14
Thanks, I've uninstalled -25 but i still have to choose -24 (I've always had that grub kernel choice menu)

---

### Post by xenus on 2010-11-21
> **rainbow99984 said:**
> Hi, well this is not an Error just performance - Upgraded to 10.10 from 10.04 so far no problem at all.  
My system boot time upto the login screen is very good. but after login it takes considerable 1~2 min. to show the desktop, any idea? my guess is its because of compiz that I'm running as art-manager fail to open if i click on it to open from System->Pref.->Art-Manager.
In System-Monitor i can see Compiz and gtk-window-decorator running normally. 
Thanks rahul
If you're using an AMD dual or better processor and you have C1E enabled in BIOS this is a known symptom.  The solution is currently to disable the option in the BIOS.
Gory details here:  [https://bugzilla.kernel.org/show_bug.cgi?id=15289](https://bugzilla.kernel.org/show_bug.cgi?id=15289)

---

### Post by identiti on 2010-11-22
I have upgraded from 10.4 to 10.10 using the update manager and when my system boots up the error 'sab1 not supported' comes up whilst its loading, what does this mean ? Also I get some problems connecting to the router now.

---

### Post by ayyork on 2010-11-23
HI i put  ubuntu 10.10 on my computer it was great i then the driver finder told  me that I could make my computer 3d so i downloaded the driver now my  computer will not read my hardrive and will not boot.
if you know how to fix this please help me.
and i have tried to put ubuntu back on with a live cd but it says error

---

### Post by mörgæs on 2010-11-24
This does not sound like a problem with an upgrade going awry. Please open a new thread in 
[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

and state everything as precise as possible: Your hardware, the driver you tried to install, the exact error message and the steps you have done already to solve the problem.

---

### Post by tomdkat on 2010-11-25
> **tomdkat said:**
> I certainly hope so.  My upgrade from 10.04 (64-bit) to 10.10 (64-bit) hasn't gone smoothly at all.  Right now, I'm plagued with two main issues:
[list]
[*]Frequent and random hangs (even the mouse won't move and ctrl-alt-del does nothing).
[*]Not being able to mount the internal SATA drive ([bug #634407](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/634407))
[/list]
So, I'm going to see if I can give a clean install an attempt on a different hard drive.  If the hangs and SATA drive issue persist, I'll revert back to Ubuntu 10.04 and wait for the subsequent release.

Peace...Well, I've tracked down the frequent hangs to a Firefox extension.  I haven't identified the problematic one but when I turned off all of the Firefox extensions, the hangs mostly went away.

As for the SATA drive issue, a recent kernel update to kernel version 2.6.35-23-generic solves the problem so I can now access my SATA drive.

Peace...

---

### Post by archolman on 2010-11-27
Thank you very much for the tute, morgaes. And to the other contributors.
 I wish I had been patient enough to read-up first, being an exemplar is interesting!

 However, I now have a working system, & it is good! Thanks be to the forums, Linux Format Magazine, & the Open University! 


  The box (a P4) that I had the update games with, has been 'retired' until I can afford to get new RAM. One of the sticks died, & a LiveCD now takes an hour to load, & forever to respond to the keyboard/mouse. Ho-hum.

---

### Post by fccluck on 2010-11-28
> **bcbc said:**
> From the release notes:


If you have already upgraded and find that the system reboots, hangs or drops you at a grub prompt when selecting Ubuntu (with or without error messages), then first try to replace the c:\wubildr file from the one in c:\ubuntu\winboot\wubildr (change 'drive' if necessary and backup c:\wubildr first as a precaution). This fix has been confirmed by many different people, as it appears that in many cases the upgrade is corrupting the wubildr file.

Otherwise another workaround is to boot a live CD, [loop mount the wubi root.disk]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?"), edit the grub.cfg (gksu gedit /*mountpoint*/boot/grub/grub.cfg) and remove all lines above the first "menuentry".

If you get a read-only error on grub.cfg, then either use vi or nano, or before running gedit first run: 
sudo chmod +w /*mountpoint*/boot/grub/grub.cfg
Note: if you install kernel updates, new kernels, remove kernels, run update-grub etc. you'll have to reapply the workaround as grub.cfg is regenerated automatically. It's easier to do this before you reboot (or you'll have to use the live CD again).

I did the editing grub.cfg thing, but what is the fix for the future?  And what is it in those first set of lines that is preventing so many people from booting?

---

### Post by bcbc on 2010-11-29
> **fccluck said:**
> I did the editing grub.cfg thing, but what is the fix for the future?  And what is it in those first set of lines that is preventing so many people from booting?

There is no permanent fix that I am aware of. I'm not expecting one anytime soon either. From what I can figure out, the developer who is making these changes to grub (Colin Watson) is also responsible for wubi - because the main wubi developer (Agostino Russo) is not available anymore. And this grub developer doesn't have much time to investigate wubi. There also doesn't seem to be much oversight by Canonical in terms of them providing wubi and making sure that it's stable. 

So, basically, your options are to backup data and reinstall Wubi and never update grub-pc or grub-common. Or to migrate the wubi to a partition as described here: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Here's a quote from the [#ubuntu-devel channel on IRC]("http://irclogs.ubuntu.com/2010/10/06/%23ubuntu-devel.txt") to explain the situation, referring to the bug that affects you (that hasn't seen any change since before the Maverick release):
> [14:42] <cjwatson> wubi upgrades have never worked right before.  it would have been nice to say that they worked this time, but I have a hard time considering it a blocker
[14:43] <cjwatson> (this is not to say I don't appreciate efforts to get them to boot ...)
[14:43] <cjwatson> er, to work
[14:43] <cjwatson> wubi really needs a maintainer who isn't me.  Agostino has been mostly lacking in time
[14:44] <cjwatson> I'm only doing it by default

PS this maverick bug has been passed on to 10.04 installs now. They are breaking too since a grub update in the last week or so.

---

### Post by lilmissdids on 2010-11-29
Hello everyone!
I've been updating since 4.04 and have never had any problems - and I am sure I jinxed myself, because right before updating from 10.04 to 10.10 I thought how lucky I was that every update has always gone so smoothly. ;)
For the past six years I've more or less been able to google myself through any difficulties, but I haven't come across anything helpful for this one. I don't know what exactly went wrong, but after the upgrade was done, it said that it had finished with errors. And many things aren't working correctly now (programs - skype, vlc etc as well as the x missing in the corners to close windows and my already sluggish laptop is even slower)  
I know this is one of the problems. Does anyone know how to fix it??
Thank you so much for your time!!! 


```
Loading new virtualbox-ose-3.2.8 DKMS files...
Building only for 2.6.35-23-generic
Building initial module for 2.6.35-23-generic

Error! Bad return status for module build on kernel: 2.6.35-23-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/virtualbox-ose/3.2.8/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/virtualbox-ose-dkms.0.crash'
dpkg: error processing virtualbox-ose-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 virtualbox-ose-dkms
N: Ignoring file 'conkyhardcore-karmic.li' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Make fie..
```
DKMS make.log for virtualbox-ose-3.2.8 for kernel 2.6.35-23-generic (i686)
Mon Nov 29 21:17:39 CET 2010
make: Entering directory `/usr/src/linux-headers-2.6.35-23-generic'
  LD      /var/lib/dkms/virtualbox-ose/3.2.8/build/built-in.o
  LD      /var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/built-in.o
  CC [M]  /var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.o
In file included from /usr/src/linux-headers-2.6.35-23-generic/arch/x86/include/asm/msr.h:17,
                 from /usr/src/linux-headers-2.6.35-23-generic/arch/x86/include/asm/processor.h:21,
                 from /usr/src/linux-headers-2.6.35-23-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:56,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from /var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/../SUPDrvInternal.h:99,
                 from /var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:33:
/usr/src/linux-headers-2.6.35-23-generic/arch/x86/include/asm/errno.h:1: error: include/asm-generic/errno.h: Input/output error
In file included from /usr/src/linux-headers-2.6.35-23-generic/arch/x86/include/asm/processor.h:21,
                 from /usr/src/linux-headers-2.6.35-23-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:56,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from /var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/../SUPDrvInternal.h:99,
                 from /var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:33:
/usr/src/linux-headers-2.6.35-23-generic/arch/x86/include/asm/msr.h: In function ‘native_read_msr_safe’:
/usr/src/linux-headers-2.6.35-23-generic/arch/x86/include/asm/msr.h:88: error: ‘EIO’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.35-23-generic/arch/x86/include/asm/msr.h:88: error: (Each undeclared identifier is reported only once
/usr/src/linux-headers-2.6.35-23-generic/arch/x86/include/asm/msr.h:88: error: for each function it appears in.)
/usr/src/linux-headers-2.6.35-23-generic/arch/x86/include/asm/msr.h: In function ‘native_write_msr_safe’:
/usr/src/linux-headers-2.6.35-23-generic/arch/x86/include/asm/msr.h:111: error: ‘EIO’ undeclared (first use in this function)
In file included from include/linux/mmzone.h:664,
                 from include/linux/gfp.h:4,
                 from include/linux/slab.h:12,
                 from /var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/../SUPDrvInternal.h:100,
                 from /var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:33:
include/linux/memory_hotplug.h: In function ‘mhp_notimplemented’:
include/linux/memory_hotplug.h:184: error: ‘ENOSYS’ undeclared (first use in this function)
In file included from include/linux/module.h:13,
                 from /var/lib/dkms/virtualbox-ose/3.2.8/build/r0drv/linux/the-linux-kernel.h:71,
                 from /var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:34:
include/linux/kmod.h: In function ‘call_usermodehelper_fns’:
include/linux/kmod.h:98: error: ‘ENOMEM’ undeclared (first use in this function)
In file included from /var/lib/dkms/virtualbox-ose/3.2.8/build/r0drv/linux/the-linux-kernel.h:77,
                 from /var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:34:
include/linux/fs.h: At top level:
include/linux/fs.h:373: error: include/linux/path.h: Input/output error
In file included from /var/lib/dkms/virtualbox-ose/3.2.8/build/r0drv/linux/the-linux-kernel.h:77,
                 from /var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:34:
include/linux/fs.h:383: error: include/linux/capability.h: Input/output error
In file included from /var/lib/dkms/virtualbox-ose/3.2.8/build/r0drv/linux/the-linux-kernel.h:77,
                 from /var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:34:
include/linux/fs.h:925: error: field ‘f_path’ has incomplete type
In file included from include/linux/mm.h:40,
                 from /var/lib/dkms/virtualbox-ose/3.2.8/build/r0drv/linux/the-linux-kernel.h:78,
                 from /var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:34:
/usr/src/linux-headers-2.6.35-23-generic/arch/x86/include/asm/pgtable.h:622: error: include/asm-generic/pgtable.h: Input/output error
In file included from /var/lib/dkms/virtualbox-ose/3.2.8/build/r0drv/linux/the-linux-kernel.h:78,
                 from /var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:34:
include/linux/mm.h: In function ‘do_mmap’:
include/linux/mm.h:1295: error: ‘EINVAL’ undeclared (first use in this function)
In file included from /usr/src/linux-headers-2.6.35-23-generic/arch/x86/include/asm/tlbflush.h:5,
                 from /usr/src/linux-headers-2.6.35-23-generic/arch/x86/include/asm/highmem.h:26,
                 from include/linux/highmem.h:43,
                 from include/linux/pagemap.h:10,
                 from /var/lib/dkms/virtualbox-ose/3.2.8/build/r0drv/linux/the-linux-kernel.h:79,
                 from /var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:34:
include/linux/sched.h: At top level:
include/linux/sched.h:93: error: include/linux/cred.h: Input/output error
In file included from /var/lib/dkms/virtualbox-ose/3.2.8/build/r0drv/linux/the-linux-kernel.h:79,
                 from /var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:34:
include/linux/pagemap.h: In function ‘mapping_set_error’:
include/linux/pagemap.h:31: error: ‘ENOSPC’ undeclared (first use in this function)
include/linux/pagemap.h: In function ‘fault_in_pages_writeable’:
include/linux/pagemap.h:398: error: ‘EFAULT’ undeclared (first use in this function)
include/linux/pagemap.h: In function ‘fault_in_pages_readable’:
include/linux/pagemap.h:421: error: ‘EFAULT’ undeclared (first use in this function)
In file included from /var/lib/dkms/virtualbox-ose/3.2.8/build/r0drv/linux/the-linux-kernel.h:96,
                 from /var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:34:
include/linux/pci.h: At top level:
include/linux/pci.h:58: error: include/linux/pci_ids.h: Input/output error
In file included from include/asm-generic/pci-dma-compat.h:7,
                 from /usr/src/linux-headers-2.6.35-23-generic/arch/x86/include/asm/pci.h:109,
                 from include/linux/pci.h:1222,
                 from /var/lib/dkms/virtualbox-ose/3.2.8/build/r0drv/linux/the-linux-kernel.h:96,
                 from /var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:34:
include/linux/dma-mapping.h: In function ‘dma_set_coherent_mask’:
include/linux/dma-mapping.h:108: error: ‘EIO’ undeclared (first use in this function)
include/linux/dma-mapping.h: In function ‘dma_set_max_seg_size’:
include/linux/dma-mapping.h:127: error: ‘EIO’ undeclared (first use in this function)
include/linux/dma-mapping.h: In function ‘dma_set_seg_boundary’:
include/linux/dma-mapping.h:142: error: ‘EIO’ undeclared (first use in this function)
/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c: In function ‘vboxdrvLinuxUid’:
/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:377: error: dereferencing pointer to incomplete type
/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c: In function ‘vboxdrvLinuxGid’:
/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:386: error: dereferencing pointer to incomplete type
/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c: In function ‘vboxdrvLinuxEuid’:
/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:395: error: dereferencing pointer to incomplete type
/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c: In function ‘VBoxDrvLinuxInit’:
/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:459: error: ‘EINVAL’ undeclared (first use in this function)
/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c: In function ‘VBoxDrvLinuxCreate’:
/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:726: error: ‘EPERM’ undeclared (first use in this function)
/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c: In function ‘VBoxDrvLinuxIOCtlSlow’:
/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:880: error: ‘EFAULT’ undeclared (first use in this function)
/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:885: error: ‘EINVAL’ undeclared (first use in this function)
/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:895: error: ‘E2BIG’ undeclared (first use in this function)
/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:906: error: ‘ENOMEM’ undeclared (first use in this function)
/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c: In function ‘VBoxDrvLinuxErr2LinuxErr’:
/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:1062: error: ‘EACCES’ undeclared (first use in this function)
/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:1063: error: ‘EINVAL’ undeclared (first use in this function)
/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:1064: error: ‘EILSEQ’ undeclared (first use in this function)
/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:1065: error: ‘ENXIO’ undeclared (first use in this function)
/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:1066: error: ‘EFAULT’ undeclared (first use in this function)
/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:1067: error: ‘ENOLCK’ undeclared (first use in this function)
/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:1068: error: ‘EEXIST’ undeclared (first use in this function)
/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:1069: error: ‘EPERM’ undeclared (first use in this function)
/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.c:1070: error: ‘ENOSYS’ undeclared (first use in this function)
make[2]: *** [/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv/linux/SUPDrv-linux.o] Error 1
make[1]: *** [/var/lib/dkms/virtualbox-ose/3.2.8/build/vboxdrv] Error 2
make: *** [_module_/var/lib/dkms/virtualbox-ose/3.2.8/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
```

---

### Post by pierreu1 on 2010-11-29
In Maverick, I ran the following commands with sudo and without and I am a bit confused because no text file could be found! Noting happened after I ran the command! Where is the test file being generated? Am I missing something? Thank you.


If you in spite of this want to keep exactly the same packages in the new Ubuntu installation, there is an alternative to the online upgrade. Running the command

```
dpkg --get-selections > installed-software
```gives a text file with all installed packages on the system. If you run this command on the old system, you will have the option of running 

```
 dpkg --set-selections < installed-software 
```on the new system after a clean install and get the same selection of packages. Thanks to **bcscomp** for this suggestion.[/QUOTE]

[COLOR="White"].[/COLOR]

---

### Post by bcbc on 2010-11-30
> **fccluck said:**
> I did the editing grub.cfg thing, but what is the fix for the future?  And what is it in those first set of lines that is preventing so many people from booting?
I found the permanent fix to the problem. For complete details see [https://bugs.launchpad.net/wubi/+bug/653134](https://bugs.launchpad.net/wubi/+bug/653134)

But here are the salient bits:> 

First back up /boot/grub
sudo cp -r /boot/grub /boot/grubbackup
 Then delete all the stuff in /boot/grub that isn't supposed to be there (everything added after fresh wubi install)
 cd /boot/grub
sudo rm *.mod
sudo rm *.img
sudo rm *.lst
sudo rm *.o
sudo rm *.pf2
sudo rm -rf locale
 This leaves 2 files:
bcbc@ubuntu:/boot/grub$ ls
grub.cfg  grubenv
 Update the grub.cfg automatically:
sudo update-grub
 FIXED!
 Not done yet - prevent grub updates from breaking it again:
Go to Synatpic, select packages grub-pc and grub-common, click on Package, Lock Version
You have to lock grub-pc and grub-common still, until the developers figure out how to prevent the problem from reoccurring on grub updates. Ironic I suppose, because when they release a fix you won't get it (or need it).

EDIT:
This fix has been tested and confirmed on a 10.04.1 install, an install upgraded from 10.04.1 to 10.10, as well as a new 10.10 install (with grub-pc reinstalled to intentionally break it).

---

### Post by Rubi1200 on 2010-11-30
Thanks yet again to bcbc for the tireless efforts to find solutions for Wubi installs :)

Quick question or two:

1. I assume this still needs to be done from the LiveCD if the install breaks?

2. If users employ the previous method of removing lines from grub.cfg (everything above the first menuentry) and then lock the version in Synaptic once back into Ubuntu will that also work or is the above method preferred?

---

### Post by bcbc on 2010-11-30
> **Rubi1200 said:**
> Thanks yet again to bcbc for the tireless efforts to find solutions for Wubi installs :)

Quick question or two:

1. I assume this still needs to be done from the LiveCD if the install breaks?

2. If users employ the previous method of removing lines from grub.cfg (everything above the first menuentry) and then lock the version in Synaptic once back into Ubuntu will that also work or is the above method preferred?

1. While you can delete the files from a live CD, you can't run 'sudo update-grub' on a wubi install without booting it (even chroot doesn't work). So they still need the workaround to boot the Wubi install and then after that make these changes.

2. No the previous method is just a quick fix that will break whenever you get a kernel update, or remove a kernel: this causes grub.cfg to be automatically regenerated and unless you take these extra measures, the grub.cfg will still cause problems.

Locking versions of grub-pc and grub-common isn't actually necessary with this new fix but it's a safeguard in case the grub developers release a new grub update without fixing the problem (I don't know how likely this is, but it's an unnecessary risk to take). 

Locking grub-* is also what I recommend to users who decided just to reinstall as this also prevents the problem from happening in the first place (as we know there already is a grub update waiting to break every fresh wubi install)

---

### Post by Rubi1200 on 2010-11-30
Thanks for the explanation.

Let me quickly summarize the main points and correct me if I am wrong (this is so I can explain it simply to users facing these issues).

1. if the Wubi install is already broken, use the fix previously advised and then boot into Ubuntu and run commands in the new method outlined in post #78.

2. if it is a fresh install or a reinstall and nothing is broken, lock the GRUB packages in Synaptic as a precaution.

By the way, since there are now a number of posts flying around with various "versions" of these fixes, I wondered if you might consider consolidating them into one "mega thread," so to speak?

I would be more than willing to help you in any way I can; editing, consolidating, etc. Let me know here on the forums or via PM.

---

### Post by bcbc on 2010-11-30
> **Rubi1200 said:**
> Thanks for the explanation.

Let me quickly summarize the main points and correct me if I am wrong (this is so I can explain it simply to users facing these issues).

1. if the Wubi install is already broken, use the fix previously advised and then boot into Ubuntu and run commands in the new method outlined in post #78.

2. if it is a fresh install or a reinstall and nothing is broken, lock the GRUB packages in Synaptic as a precaution.

By the way, since there are now a number of posts flying around with various "versions" of these fixes, I wondered if you might consider consolidating them into one "mega thread," so to speak?

I would be more than willing to help you in any way I can; editing, consolidating, etc. Let me know here on the forums or via PM.
Rubi1200 that is a great idea, to consolidate them. I'm just engaged in a '[discussion]("http://ubuntuforums.org/showthread.php?t=1629755")' with drs305, who has come up with yet another fix. I don't have time to complete the 10.04.1 to 10.10 upgrade test case until later today anyway. Or else create a solution thread that you can edit later. Thanks for all your help.

Edit: and I forgot to say, you're exactly right in your summary of the situation.

---

### Post by drs305 on 2010-11-30
I'm doing a clean install of 10.04.1 to test, then will upgrade to 10.10 and try to post my findings before I go to work tonight.

---

### Post by bcbc on 2010-11-30
> **drs305 said:**
> I'm doing a clean install of 10.04.1 to test, then will upgrade to 10.10 and try to post my findings before I go to work tonight.
OK... just remember that there is a 10.04.1 grub update that is breaking 10.04.1 installs. So I guess you should avoid the 10.04.1 grub-pc and grub-common update or it will break before you even get to upgrade.

---

### Post by Rubi1200 on 2010-11-30
I look forward to reading about the results of these tests.

@bcbc:
I will only have time towards the end of this week to get the posts and various fixes consolidated into a neat and tidy format.

However, before posting and requesting that it perhaps be made into a sticky I would like you to review whatever I put together.

I would like to know if I can PM you or if you would prefer I send it to drs305 (assuming he agrees) and that he reviews it before posting.

Either way, I will contribute in any way I can as there have been a slew of posts recently with these issues and I think that a sticky might help users.

---

### Post by four_or_six on 2010-11-30
I have just installed a few updates from the Update manager, and on rebooting I can only get as far as the point where I choose between Ubuntu and windows. I pick Ubuntu, and after a few seconds my computer reboots and I am back at the place where I choose between windows and Ubuntu again! I am totally stuck, can anyone help?!

---

### Post by drs305 on 2010-11-30
Most of this has already been posted somewhere (if not here), but I'll include my tests today.

Here are my findings & possible solutions:

**Fresh install, Ubuntu 10.04.1 Wubi**
Boots fine.
Update/upgrade and restart > **Fail:** Reboots as soon as I select Ubuntu (Wubi).

**Second test: Upgrade working 10.04.1 Wubi > 10.10 Wubi**
Initial Reboot >  Boots properly.
The good news is that the bug on upgrading from 10.04 to 10.10 appears to have been fixed. I didn't need to replace wubildr.
Numberous files are in /boot/grub, the *loadfont* section of *grub.cfg* exists, but the system boots from the Wubi menu.

Update grub with no changes immediately after install: OK

Post-Install Update >  There were no updates available, so I installed an older kernel which would trigger an update to grub. 
Result:  **Fail:** grub> prompt

**Analysis:**
The boot failure is due to the presence of additional files in Wubi's /boot/grub, as *bcbc* suggests. 

<Geek stuff that proved inconclusive>
Specifically, it appears the presence of the "loadfont" conditional in /boot/grub/grub.cfg after an update of grub may trigger the failure to boot. This conditional is built into grub.cfg during a grub update if the  /usr/share/grub/unicode.pf2 file is located. If this file is not located, G2 searches for /boot/grub/unicode.pf2 and then /usr/share/grub for ascii.pf2. If any of these 3 files are found, the 'loadfont' conditional is created and the Wubi boot fails after a grub update. However, this conditional is not responsible for *every* failure, so won't be included in the solutions.
</Geek stuff>

**Solution:**
In order to operate, Wubi G2 normally only has grub.cfg and grubenv in /boot/grub. 

**To Restore Wubi Booting:**
Restoration requires an Ubuntu installation CD (LiveCD), another Ubuntu installation, or a rescue CD which gives you access to the Wubi *root.disk* file. The solution involves mounting the Windows folder, followed by mounting the Wubi root.disk. 

Create mount points and mount Windows and Wubi. In the following example, Windows is assumed to be on **sda1**. Change as required (sda2, sdb1, etc):
```

sudo mkdir /mnt/windows /mnt/wubi
sudo mount /dev/**sda1** /mnt/windows
sudo mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/wubi

```
At this point the Wubi files are accessible via command line or file browser. **/** is located at /mnt/wubi

Remove all lines prior to the first *menuentry* of /boot/grub/grub.cfg. This is from the start of the file to the "### BEGIN /etc/grub.10/10_lupin ###" section. 
```
gksu gedit /mnt/wubi/boot/grub/grub.cfg
```
Save the file. Do not try to update grub. Reboot.

Now that you are back into the Wubi install, to prevent this from happening again:

Solution 1:
Remove all files except grub.cfg, grub,env from /boot/grub, then run update-grub.


That's all the time I have today, but *bcbc* posted the way to prevent it from happening again earlier in the thread. Later perhaps I'll reduce the number of commands needed for moving all the files.

---

### Post by bcbc on 2010-11-30
Thanks drs305... 
I also ran the upgrade to 10.10 from 10.04.1 (just completed). For me it still broke but left me at a grub prompt> so I could boot manually from there. Then I applied the fix to remove extra files from /boot/grub. After that running 'sudo update-grub' fixed the problem.

I also confirmed removal of a kernel automatically regenerates grub and still works.

The only exception I get is regarding video (but the end result is the same as a default wubi install, so I am not fussed).
> bcbc@ubuntu:~$ sudo update-grub
[sudo] password for bcbc: 
Generating grub.cfg ...
*** cat: /boot/grub/video.lst: No such file or directory***
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found Dell Utility Partition on /dev/sda1
Found Microsoft Windows XP Professional on /dev/sda2
Found Ubuntu 10.10 (10.10) on /dev/sda5
done
bcbc@ubuntu:~$ 
I still think this fix is 'fine and well', but the hassle required for the target audience (newcomers to Ubuntu) makes this a less than ideal approach. I hope that someone can persuade the developers to do something about it soon.

We still need to caution any wubi user from updating grub-pc or grub-common (or upgrading from 10.04.1 to 10.10). This is the best way to avoid the problem in the first place.

PS A fresh install of 10.10 is safe for now as there are no grub updates in 10.10 at this time.

---

### Post by mörgæs on 2010-11-30
> **pierreu1 said:**
> In Maverick, I ran the following commands with sudo and without and I am a bit confused because no text file could be found! Noting happened after I ran the command! Where is the test file being generated? 


The file will be created in the present directory. Sudo is not necessary. It is a text file, so you can see it afterwards with the command 

```
less installed-software
```

---

### Post by Bushcraft Bill on 2010-12-01
are you saying you were able to boot up ubuntu how do you do that?

I am an old dos monger is their a batch file that can be downloaded and run to do the fixes needed?

I get to the grub prompt but all I know what to type in is reboot so I can run windows7 and be online...LOL...

> **bcbc said:**
> For me it still broke but left me at a grub prompt> so I could boot manually from there.

---

### Post by drs305 on 2010-12-01
> **Bushcraft Bill said:**
> are you saying you were able to boot up ubuntu how do you do that?

I am an old dos monger is their a batch file that can be downloaded and run to do the fixes needed?

I get to the grub prompt but all I know what to type in is reboot so I can run windows7 and be online...LOL...

Check the Wubi only section of this guide:
[Grub Rescue Prompt Megathread]("http://ubuntuforums.org/showthread.php?t=1594052")

Note a "grub" prompt is actually better than a "grub rescue" prompt, so the thread applies to your situation as well.  ;-)

---

### Post by Bushcraft Bill on 2010-12-01
thanks!
this fixed things for me for now!

> Some users reported copying the wubildr from the c:\ubuntu\winboot\ directory over c:\wubildr fixed the problem

---

### Post by prmdk on 2010-12-01
This is my first post. I was not sure where to put my query so i am asking here.

Not matter which software i try to installed i get this error. I think the software package is downloaded just fine but system has trouble installing it.

Any help is appreciated..

[IMG]http://imgur.com/e9NrZ.png[/IMG]

](*,)

---

### Post by drs305 on 2010-12-01
> **prmdk said:**
> This is my first post. I was not sure where to put my query so i am asking here.

Not matter which software i try to installed i get this error. I think the software package is downloaded just fine but system has trouble installing it.


prmdk,

Welcome to the Ubuntu forums. :-)

Normally you would start your own thread. Since you are new here, Absolute Beginners would be a good place to post if you aren't familiar with linux commands or the Ubuntu GUI menus.

There is an error in the file /var/lib/dpkg/available near line 29102. You can open gedit to that line and take a look. If the error is obvious and you know how to fix it, just make the change and save the file. It looks like you just have to add a new line with ENTER.

If you aren't sure, post the lines around line 29102. You can turn on the line numbers in gedit via the Edit, Preferences, View (tab).

To open the file near the error:
```
gksu gedit +29102 /var/lib/dpkg/available

```
You will be asked for your password when you open the file since it is a system file and you have to assume 'admin/root' privileges to edit it.

---

### Post by prmdk on 2010-12-01
> **drs305 said:**
> 
To open the file near the error:
```
gksu gedit +29102 /var/lib/dpkg/available

```You will be asked for your password when you open the file since it is a system file and you have to assume 'admin/root' privileges to edit it.

Thanks drs305,

I entered the code you gave but the gedit seems unable to open it.

[IMG]http://imgur.com/0keQc.png[/IMG]

---

### Post by drs305 on 2010-12-02
It's a simple text file so it should have opened. No problem - we can just empty it and it will be rebuilt when necessary:

```
sudo dpkg --clear-avail
```

If this remedies the problem please mark the thread SOLVED via the 'Thread Tools' link near the top right of the first post.

---

### Post by pierreu1 on 2010-12-09
> **mörgæs said:**
> The file will be created in the present directory. Sudo is not necessary. It is a text file, so you can see it afterwards with the command 

```
less installed-software
```

Oh! Thanks so much! I will have to remember that command! Very useful!

Could I pick your brain one more time then? I would like to be able to save the output, but when I select select all in the terminal, I am only able to save what is being presented on the screen. Not to sure if this an error, but is there a way to copy and paste the whole content?

Thanks so much!

---

### Post by mörgæs on 2010-12-09
You don't have to capture anything from the terminal window by hand. The '>' sign does this for you. It is called 'piping', in case you want to google it further.

After running the command just go to your home folder, and with Gedit or a similar editor open the file named *installed-software*.

It works with any command, for example **ls -l > contentsOfMyDirectory ** will create a file with the results from **ls -l**.

---

### Post by pierreu1 on 2010-12-09
> **mörgæs said:**
> You don't have to capture anything from the terminal window by hand. The '>' sign does this for you. It is called 'piping', in case you want to google it further.

After running the command just go to your home folder, and with Gedit or a similar editor open the file named *installed-software*.

It works with any command, for example **ls -l > contentsOfMyDirectory ** will create a file with the results from **ls -l**.

Oh! Thanks so much! There is so much to learn and so little time, but now that I have a little bit more time, I might learn a little bit more, thanks to you!

I am trying to learn more about the commands by following a few excellent descriptions on the web! I will persevere!

Thanks a lot!

All the best!

---

### Post by mörgæs on 2010-12-10
You are welcome. This book gives a good introduction to Ubuntu:
[www.ubuntu-manual.org](www.ubuntu-manual.org)

It is written for 10.04, but most applies to 10.10 as well.

---

### Post by omarly on 2010-12-11
> **wkulecz said:**
> Before you upgrade, get an external USB drive and clone your system with
sudo rsync -ax / /media/usbdrive

You'll need one rsync command for each partition you mount.  The rsync docs are quite good.

This way you can recover if the install goes bad and try again and again if you want.  Bone up on reinstalling grub or grub2 beforehand too.

Backing up /home only will not recover all the work you did installing and configuring extra packages which is likely the reason you want an upgrade instead of a fresh install!

Just what I have been looking for :)
At least I think so. I will try it out on next upgrade.
:P

---

### Post by pierreu1 on 2010-12-11
> **mörgæs said:**
> You are welcome. This book gives a good introduction to Ubuntu:
[www.ubuntu-manual.org](www.ubuntu-manual.org)

It is written for 10.04, but most applies to 10.10 as well.

Oh! Thanks! That is extremely useful! 

Here is [a beautiful video]("http://www.wimp.com/wecould/") that feels is representative of your support and you!

All the best!

---

### Post by niharthekadi on 2010-12-22
i currently have ubuntu 9.10 + XP installed

i have downloaded the ISO of 10.10
I tried to preview using "Install inside windows" with 3 GBs on the drive where windoz is installed.
But after installing i am not able to log in.
When i write wrong passwd it doesn't let me log on obviously,
but even after writing the right passwd it redirects to the log-in page again.
I thought I forgot the passwd but 
when I uninstalled & tried 2nd time ,it happened agin.

---

### Post by Rubi1200 on 2010-12-23
Hi,
if this is a Wubi install, see here:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

In any event, so we can see what is going on with your setup, please boot the computer with a LiveCD and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here and we will try and help you fix this.

Thanks.

---

### Post by BattlePope on 2011-01-01
> **bcbc said:**
> From the release notes:
If you have already upgraded and find that the system reboots, hangs or drops you at a grub prompt when selecting Ubuntu (with or without error messages), then first try to replace the c:\wubildr file from the one in c:\ubuntu\winboot\wubildr (change 'drive' if necessary and backup c:\wubildr first as a precaution). This fix has been confirmed by many different people, as it appears that in many cases the upgrade is corrupting the wubildr file.

Otherwise another workaround is to boot a live CD, [loop mount the wubi root.disk]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?"), edit the grub.cfg (gksu gedit /*mountpoint*/boot/grub/grub.cfg) and remove all lines above the first "menuentry".

If you get a read-only error on grub.cfg, then either use vi or nano, or before running gedit first run: 
sudo chmod +w /*mountpoint*/boot/grub/grub.cfg
Note: if you install kernel updates, new kernels, remove kernels, run update-grub etc. you'll have to reapply the workaround as grub.cfg is regenerated automatically. It's easier to do this before you reboot (or you'll have to use the live CD again).

PERMANENT MANUAL FIX:
I am working on completing testing for this but so far it works on 10.04.1 and 10.10 which all are affected by the same issue. [http://ubuntuforums.org/showpost.php?p=10180520&postcount=78](http://ubuntuforums.org/showpost.php?p=10180520&postcount=78)
You still need to boot the wubi before applying the permanent fix.


So it turns out I tried the first fix, and it didn't work. And I tried the second fix, and I don't have a grub.cfg in the location specified, just a grubenv file. Any ideas?

---

### Post by drs305 on 2011-01-01
> **BattlePope said:**
> So it turns out I tried the first fix, and it didn't work. And I tried the second fix, and I don't have a grub.cfg in the location specified, just a grubenv file. Any ideas?

I'll assume you are using Wubi within Windows.

If you need to create a grub.cfg file, it's possible you are also missing other files as well (or not). In any case, you can use the 'chroot' procedure in the following link to make sure Grub2 is properly installed. Make sure you use the "Wubi" section in Step 1.
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

It's possible all you need to do is recreate the grub.cfg file. If you want to try a less intrusive solution, accomplish steps 1 & 2, then run "update-grub" and it should generate the grub.cfg file. You can then skip steps 3-4 and then complete it with 6 - 8. If this doesn't work, run all the steps, which includes purging and reinstalling Grub2.

---

### Post by anand1 on 2011-01-01
Hello everyone,
 Recently purchased Acer aspire 4738z laptop with pentium p6100 processor,3 gb RAM , Intel Graphics Media Accelerator HD (Intel GMA).
 I installed 32bit version of ubuntu 10.10 and it worked fine. I downloaded 64bit version and installed on top of the 32version by CD. It installed properly and instructed to restart. After restarting lots of commands come in and end as 
ubuntu 10.10 username-Aspire-4738z tty1 
username-Aspire-4738z login-
I log in my username and password then another sets of lines appear and end as 
usename@username-aspire 4738z:$-
At this point i dont know what to do.the familiar desktop does not come.I switch off the laptop. I searched the net and tried typing 
startx  that takes me to a black screen. 
alt+ctrol+f7  that takes me to a black screen with a cursor blinking
i typed apt-get install ubuntu (dont exactly remember ) the message comes as 'you have latest version of ubuntu'

Please suggest a solution, i have no experience of linux. I hope this was the right place to post.
Thanks.
anand

---

### Post by bcbc on 2011-01-01
> **BattlePope said:**
> So it turns out I tried the first fix, and it didn't work. And I tried the second fix, and I don't have a grub.cfg in the location specified, just a grubenv file. Any ideas?

What partition is your wubi install on?
When you try and boot do you get a grub prompt (not a rescue prompt?)

Edit: I see I am 8 hours late coming to the table. Did you get it sorted out already?

---

### Post by anand1 on 2011-01-02
no more problems, i installed linux mint julia. it works fine.
bye
anand

---

### Post by Dipinp on 2011-01-03
I have the same problem mentioned by anand1.. plz help...

---

### Post by Arrow102 on 2011-01-04
Hello. I am getting an error when I try to install Ubuntu 10.10 and even 10.4 on my system. It looks like this:

E: Sub-process/usr/bin/dpkg - error code 1

and when I continue with the install I get a bootloader error at /dev/sda

I have no idea what these mean. I am installing on a recently formatted hard drive, so I'm not sure why I'm getting these errors. Does anyone have any advice or can you at least direct me on how to manually install the bootloader so my computer will run off the hard drive when restarted? When running off the install CD, the Trial mode in both versions works just fine, but every install I try fails. Thanks

---

### Post by mörgæs on 2011-01-04
Hi, welcome to you both.

Please only post in this thread, if your problems are related to an upgrade. It seems to concern a fresh installation, so best is to search in the other threads and open a new one, if the problem is not covered already.

One advice, though, is trying the alternate installer: [http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/) 
If this does not help, please search the other threads as explained above.

---

### Post by bdalzell on 2011-01-09
I upgraded to Lucid from Karmic and ended up with a system that showed several problems. (1) Low graphics mode, (2) MySQL not working. (3) Only some choices from Grub menu working. (4) My CD ROM drive not working (try to use the commonest solution, booting off the install disk when this happens).

I messed around trying to solve things and made some things worse.

However today I was able to boot the computer from one of my choices in GRUB - and I spent some time looking at what was in / and discovered broken links both for vmlinuz and initrd.img. There was also a link for each marked vmlinuz.old and initrd.old. I used gnome-commander in "start as root mode"  and examined the preferences on the broken folders to see where they pointed. They where linked with a non-existant kernel and a non existant initrd.img. 

The .old version of these files did point to an existing kernel and initrid.img. 

So I deleted them and renamed the old links by removing the .old at the end of the names. This enabled me to boot into a working installation without having to page down in the list of files on the GRUB screen.

I do not know how my earlier attempts to fix stuff resulted in the links to the non-existant files.

at least I have full resolution on my 1680 x 1050 monitor and MySQL is NOW working.

Now if I can just get my cdrom drive working...

PS: To use Gnome-commander to see prefernces for files and directories you highlight the entry in the file window and then use the right mouse button to bring up a drop down menu. Preferences is the last item. Choose it to see various things about the file and also to change permissions.

To install gnome-commander:
   sudo apt-get install gnome-commander

Gnome Commander gets installed in the Accessories sub menu

---

### Post by sjsu on 2011-02-01
I am just new to this forum and your answer just gave me what I was looking for. I had this problem and had to reinstall wubi totally three times. Last time even my windows got corrupted. Thanks for the info

---

### Post by jonthomas83 on 2011-02-03
Hi all, I'm gutted my first post here is as a result of needing help, but here  goes.

I've updated within the last hour. 83 updates needed. I had to restart and after I did so, it hasn't been able to load Ubuntu since.

I run a dual boot machine with Windows XP and it keeps looping me back to the OS selection, if I press Ubuntu it loops, Windows is fine. 

Have I lost all my work or is there a way back from this?

Any help would be greatly appreciated, thank you.

---

### Post by bcbc on 2011-02-03
> **jonthomas83 said:**
> Hi all, I'm gutted my first post here is as a result of needing help, but here  goes.

I've updated within the last hour. 83 updates needed. I had to restart and after I did so, it hasn't been able to load Ubuntu since.

I run a dual boot machine with Windows XP and it keeps looping me back to the OS selection, if I press Ubuntu it loops, Windows is fine. 

Have I lost all my work or is there a way back from this?

Any help would be greatly appreciated, thank you.
Nah - that sounds totally fixable. Have a look at the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") and post there if you need help.

---

### Post by jonthomas83 on 2011-02-03
> **bcbc said:**
> Nah - that sounds totally fixable. Have a look at the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") and post there if you need help.

That's great news, thank you, ill take a good look and will post there. Thanks again for your time. :)

EDIT: Problem fixed, thank you so much! (for anyone else who sees this, it was "Problem 2, Solution 1" in the above WUBI thread link). Thanks again bcbc, you're a legend! :)

---

### Post by SundayForever on 2011-02-26
One of the blessings of free and open source software is the abundance  of available applications. By all means give them a test, but remember  that this moves you system further towards one-of-a-kind.

---

### Post by mörgæs on 2011-03-03
> **SundayForever said:**
> One of the blessings of free and open source software is the abundance  of available applications. By all means give them a test, but remember  that this moves you system further towards one-of-a-kind.

It is always nice that people quote me (and now I am quoting you in return), but was there a question?

---

### Post by Keith_Beef on 2011-03-06
I just upgraded from 9.10 to 10.04, and after it had at last completed I was faced with a screen resolution of 640 × 480 on a screen that is capable of 1920 × 1050.

I could get the nvidia XServer Settings to start, but could not choose any higher resolution that this.

Also, I had no panel at the top of the screen, so no menus... Ihad to create a launcher for  gnome-terminal on the desktop and work from there. 

Well, after trying for half an hour to change the resolution, I decided to delete the xorg.conf files from /etc/X11/ and restart. 

This gave me the correct 1920 × 1050 resolution, but with a band of speckly pixels along the top edge, and the whole display seems shifted down... i.e., I can move the mouse pointer beyond the physical bottom edge of the screen,

Moreover, I can now no longer run the nvidia XServer Settings; when I try to do this, I get the message "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the server"... but if I do this, the display goes back to 640 × 480...

What can I do to fix this?

K.

---

### Post by Keith_Beef on 2011-03-06
Oh, and my keyboard selector applet has disappeared from the panel, and I don't find it in the list when I try to add an applet...

K.

---

### Post by mörgæs on 2011-03-08
This is a good example of an update going haywire: Several independent, small or large problems appearing, and possibly more problems still unnoticed.

My guess is that the fast and safe solution is in post #1.

---

### Post by Keith_Beef on 2011-03-08
> **mörgæs said:**
> This is a good example of an update going haywire: Several independent, small or large problems appearing, and possibly more problems still unnoticed.

My guess is that the fast and safe solution is in post #1.

Well, I think that few problems in my system at the moment all stem from the video configuration.

The lack of panel was really due to the resolution... the panel was probably present, just "off screen"... when I tried editing the xorg.conf file that got created, I was able to pan the screen around to see the panel.

I really don't want to have to go through the whole installation again, just to fix a broken video driver and configuration.

This upgrade from 9.10 to 10.04 was really just a step in the path to 10.10... if I can't fix the video in 10.04, I might just go to 10.10 in the hope that it fixes itself in the process.

But I see from your post #1 that F-Spot is replaced by something else... I have been using F-Spot for a couple of years, and have a small collection of images in there. I wonder what will happen.

K.

---

### Post by Keith_Beef on 2011-03-09
Well, I could not find a way to get this fixed...

Every time I removed the xorg.conf file, I got my nice 1920 x 1050 display, but lost access to the nvidia configuration tool.

When I ran the nvidia-xconfig command I got an xorg.conf file, got back the nvidia configuration tool, but that tool refused to go beyond 640 x 480.

So I tried to upgrade to 10.10 from the console...
sudo do-release-upgrade -d

Well, this took hours, but finally finished around 05h30 EST today... and still left me with a broken system.

Now, I have *no* working XServer. This is starting to become really, really annoying. Using aptitude in the console is really not my idea of an ideal way to fix broken packages!

I noticed a few messages flashing by during the process, references to something like "invalid [or incorrect?] version number... Intrepid ... invalid character in version number". The system must have kept a log of the updates I did, so I should be able to locate these in the log and then use apt-get -remove on those packages, right? or will the invalid character in the version number make that impossible?

Then, I need to know *exactly* which packages are necessary to get my Sparkle 9800GTX+ card working.

I think that this would be nvidia-current plus all its dependencies... I think that I do *not* need to get nv or nouveau.

Or, I suppose the last resort would be to download a CD, burn it, and then start the installation of 10.10 as if it were a new system, but keeping /home and maybe /opt as they are.

K.

---

### Post by biroglyph on 2011-03-17
Good day.
I have been running 10.04 on my Shuttle KPC for some time now. Last night my system froze up and I resorted to powering the machine off and on. Subsequently, running certain apps would cause the os to reboot. Because of this, I selected the recovery option from the GRUB menu, and this process eventually caused all packages to be upgraded. Now when the system boots, after the GRUB menu I get:

[INDENT][FONT="Courier New"]The disk drive for / is not ready yet or not present[/FONT][/INDENT]

if I select [FONT="Courier New"]S to Skip[/FONT] i receive the same message but for /tmp.

if I select [FONT="Courier New"]M for manual[/FONT] recover the system boots into the maintenance shell where i'm not sure what do do next. I can see that my data is intact.

[EDIT]I have now created a usb stick installer and it immediately crashed out saying-
"critical temperature reached (60 Degrees) shutting down."

i now remember seeing a the same message during the initial recovery boot mentioned above. [/EDIT]
 

Any suggests on what to try would be most appreciated.

Thanks

---

### Post by ichigo6420 on 2011-03-20
How do you do a clean install? I've tried all of your suggestions but they didn't seem to work :( thank you

---

### Post by mörgæs on 2011-03-20
Please don't double-post.

---

### Post by bent12 on 2011-03-22
well done nice work an d thanks for shearing  such a nice help

---

### Post by ottosykora on 2011-03-26
symbol grub_xputs not found


after upgrade from 10.04 to 10.10

---

### Post by drs305 on 2011-03-26
> **ottosykora said:**
> symbol grub_xputs not found after upgrade from 10.04 to 10.10

Normally that message means Grub 2 was not fully installed. The most comprehensive way to fix this is to completely remove and reinstall Grub 2. If this is a normal Ubuntu installation (not Wubi) you can use a LiveCD and the procedures in the "Chroot" link in my signature line to do this.

---

### Post by lich 6222 on 2011-04-07
I have tried  to upgrade from 9.04 to 9.10  a long time ago
it have failed cause my Ram was bad 

my primary os is windows xp
but i had ubunti installed as second
after fixing the Ram issue  I installed 
Ububtu 10.10 and it was working great until yesterday
but in loging had like 4 option

1 ubuntu generic
2 recover Ubuntu
3 test ram
 4 Windows

for 6 month ( 158 days)  was using only ubuntu 10.10
but yesterday have the BAD idea to select the recover
got some meesage of a long time like 1 hour went to sleep
when i wake  uo was a message about cpu heat
I restart the computer
now I can only use Windows
my Ubuntu 10.10 was Dowgrade to 10.04 and isnt installed properly
and get stucked in login 
Question 
1.how can I recover my instalation ubuntu 10.10 
2. how i removed the  recover Ubuntu option

---

### Post by drs305 on 2011-04-07
lich 6222,

It would be best to boot the LiveCD, download and run the boot info script from the following site. Post the contents of the RESULTS.txt here so we can check the status of your boot files.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

Generally, I'd expect all you will have to do will be to boot the LiveCD, run a grub command to write to the MBR, and if your Ubuntu system is intact you will be able to boot either Windows or Ubuntu.

But to be sure, please post the RESULTS.txt.

---

### Post by lich 6222 on 2011-04-10
after 1 hour of  booting from live cd ubuntu 10.04 trial and error found the script and runing it i have the result

from the resullutext
 i got
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #11 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /wubildr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda12: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda13: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab

sda14: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   178,725,622   178,725,560   7 HPFS/NTFS
/dev/sda2         178,726,910   976,751,999   798,025,090   f W95 Ext d (LBA)
/dev/sda5         567,158,823   567,367,604       208,782   e W95 FAT16 (LBA)
/dev/sda6         567,367,668   976,751,999   409,384,332   e W95 FAT16 (LBA)
/dev/sda7         308,207,616   370,637,963    62,430,348  83 Linux
/dev/sda8         561,389,568   567,158,783     5,769,216  82 Linux swap / Solaris
/dev/sda9         178,726,912   302,833,663   124,106,752  83 Linux
/dev/sda10        302,835,712   308,205,567     5,369,856  82 Linux swap / Solaris
/dev/sda11        434,888,704   556,122,111   121,233,408  83 Linux
/dev/sda12        556,124,160   561,375,231     5,251,072  82 Linux swap / Solaris
/dev/sda13        370,638,848   432,142,335    61,503,488  83 Linux
/dev/sda14        432,144,384   434,880,511     2,736,128  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       49e04282-f382-448c-a8f7-a81dab479823   ext3                                     
/dev/sda10       8ad86258-aade-41d5-9163-47fbeccb5441   swap                                     
/dev/sda11       f1982224-4334-40b9-b309-f1a9e31fb4d6   ext4                                     
/dev/sda12       027eb6e6-99b9-4d24-9e47-7965ddedce4a   swap                                     
/dev/sda13       a2c6a9a2-08f9-41a7-9dc3-3b4b03f7b065   ext4                                     
/dev/sda14       573e38df-f898-4c0c-9eed-979dd3d54e67   swap                                     
/dev/sda1        6470395E7039385E                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda7        4cd4dd8a-304b-47ce-a472-2e5bbe7cb8f4   ext4                                     
/dev/sda8        0ac0d180-670a-4587-b1a4-017521b31249   swap                                     
/dev/sda9        9af44979-909e-4cac-9585-452d4928b955   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


==================== sda1/ubuntu/disks/boot/grub/menu.lst: ====================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=6470395E7039385E loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-19-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=6470395E7039385E loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.28-19-generic

title		Ubuntu 9.04, kernel 2.6.28-19-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=6470395E7039385E loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.28-19-generic

title		Ubuntu 9.04, kernel 2.6.28-18-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=6470395E7039385E loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=6470395E7039385E loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 9.04, kernel 2.6.28-17-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=6470395E7039385E loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=6470395E7039385E loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.04, kernel 2.6.28-16-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=6470395E7039385E loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=6470395E7039385E loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6470395E7039385E loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6470395E7039385E loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=6470395E7039385E loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=6470395E7039385E loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
chainloader	+1


======================== sda1/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

C:\wubildr.mbr = "Ubuntu"


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: ubuntu/disks/boot/grub/menu.lst
    ??GB: ubuntu/disks/boot/initrd.img-2.6.28-11-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.28-15-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.28-16-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.28-17-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.28-18-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.28-19-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.28-11-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.28-15-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.28-16-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.28-17-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.28-18-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.28-19-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.31-22-generic

============================= sda1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=4cd4dd8a-304b-47ce-a472-2e5bbe7cb8f4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=0ac0d180-670a-4587-b1a4-017521b31249 none            swap    sw              0       0

=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=9af44979-909e-4cac-9585-452d4928b955 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=8ad86258-aade-41d5-9163-47fbeccb5441 none            swap    sw              0       0

========================== sda11/boot/grub/grub.cfg: ==========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,11)'
search --no-floppy --fs-uuid --set f1982224-4334-40b9-b309-f1a9e31fb4d6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,11)'
search --no-floppy --fs-uuid --set f1982224-4334-40b9-b309-f1a9e31fb4d6
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,11)'
	search --no-floppy --fs-uuid --set f1982224-4334-40b9-b309-f1a9e31fb4d6
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=f1982224-4334-40b9-b309-f1a9e31fb4d6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,11)'
	search --no-floppy --fs-uuid --set f1982224-4334-40b9-b309-f1a9e31fb4d6
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=f1982224-4334-40b9-b309-f1a9e31fb4d6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,11)'
	search --no-floppy --fs-uuid --set f1982224-4334-40b9-b309-f1a9e31fb4d6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,11)'
	search --no-floppy --fs-uuid --set f1982224-4334-40b9-b309-f1a9e31fb4d6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 6470395e7039385e
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda11/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda11 during installation
UUID=f1982224-4334-40b9-b309-f1a9e31fb4d6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda12 during installation
UUID=027eb6e6-99b9-4d24-9e47-7965ddedce4a none            swap    sw              0       0

=================== sda11: Location of files loaded by Grub: ===================


 240.0GB: boot/grub/core.img
 245.2GB: boot/grub/grub.cfg
 241.0GB: boot/initrd.img-2.6.32-24-generic
 240.8GB: boot/vmlinuz-2.6.32-24-generic
 240.8GB: boot/vmlinuz-2.6.32-30-generic
 241.0GB: initrd.img
 240.8GB: vmlinuz

=============================== sda13/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda13 during installation
UUID=a2c6a9a2-08f9-41a7-9dc3-3b4b03f7b065 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda14 during installation
UUID=573e38df-f898-4c0c-9eed-979dd3d54e67 none            swap    sw              0       0

=================== sda13: Location of files loaded by Grub: ===================


 196.6GB: boot/vmlinuz-2.6.32-24-generic
 196.6GB: vmlinuz

```
here it end

---

### Post by drs305 on 2011-04-10
> **lich 6222 said:**
> after 1 hour of  booting from live cd ubuntu 10.04 trial and error found the script and runing it i have the result


Thanks for posting that file. I added "code" tags for formatting purposes. You can do this by highlighting the text and pressing the # icon while you are writing your post.

I don't see any files for 10.10, which should be using the 2.6.35 kernel. The only one which looks normal is your Ubuntu on sda11, which is Lucid. I think that is the one you may be having problems with, but that is probably your best chance of regaining a bootable system.

I can't tell for sure if your Grub2 is broken of if it's working but you can't login after Ubuntu takes over. If G2 is broken, you can try to get it working again from the LiveCD. You will mount your Ubuntu partition and then reinstall Grub2:
```
sudo mount /dev/sda11 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Do not put the partition number in the second command.

If it boots, run "sudo update-grub" to refresh the Grub menu.

---

### Post by Camilia on 2011-04-10
The menu bars are misaligned, thus difficult to click on. I go to monitor change it then restore it to correct it. But every time I come back on have to reset it in the monitor menu.

---

### Post by lich 6222 on 2011-04-11
> **drs305 said:**
> Thanks for posting that file. I added "code" tags for formatting purposes. You can do this by highlighting the text and pressing the # icon while you are writing your post.

I don't see any files for 10.10, which should be using the 2.6.35 kernel. The only one which looks normal is your Ubuntu on sda11, which is Lucid. I think that is the one you may be having problems with, but that is probably your best chance of regaining a bootable system.

I can't tell for sure if your Grub2 is broken of if it's working but you can't login after Ubuntu takes over. If G2 is broken, you can try to get it working again from the LiveCD. You will mount your Ubuntu partition and then reinstall Grub2:
```
sudo mount /dev/sda11 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Do not put the partition number in the second command.

If it boots, run "sudo update-grub" to refresh the Grub menu.

Thank you very much !

that what I did  
(image from   terminal)
buntu@ubuntu:~$ sudo mount/dev/sda11/mnt
sudo: mount/dev/sda11/mnt: command not found
ubuntu@ubuntu:~$ sudo mount /dev/sda11 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
cp: reading `/usr/lib/grub/i386-pc/915resolution.mod': Input/output error
ubuntu@ubuntu:~$ 
(end terminal Image)


I will try to restart computer with little hope it will do

---

### Post by drs305 on 2011-04-11
> **lich 6222 said:**
> 
I will try to restart computer with little hope it will do

Unfortunately, I believe you are correct.

When you run 'grub-install' from the LiveCD it attempts to copy the files from the */usr/lib/grub/i386-pc* folder to the /boot/grub directory (in your case the sda11 Ubuntu partition) of your real installation. For some reason this failed. The problem is most likely not with the specific file mentioned in the error message - that just happened to be the first file it tried to copy.

The problem could be with the CD, a problem writing to the partition due to a file system error, or something else. I don't know if using the wrong architecture CD (32-bit/i386 vs 64-bit/amd) would produce an error for this operation or not (both have an i386 folder). 

You might want to make sure you have a copy of the latest CD (10.04.2) since that is the version currently on your sda11 partition.

I don't see any file system errors in RESULTS.txt, but you could also run an fsck check on the sda11 partition just to be sure. Make sure the partition isn't mounted when you run the check:
```
sudo umount /dev/sda11
sudo e2fsck -f -y -v /dev/sda11
```

---

### Post by doorunrun on 2011-04-11
This maybe more of a Grub2 annoyance, but at boot time on my Grub2 Menu is showing the wrong version of Grub.

I upgraded from 9.04 to 10.10 and had a few post upgrade issues to deal with regarding Grub2. In particular I was getting the "incorrect syntax" message which turned out to be a problem with a missing video.lst file and was documented on the forum.

After getting that fixed, and booting seemed to be smooth, I decided I would rather see the Grub2 Menu since this machine is more of a server than workstation. But when the system boots and the Grub menu is displayed the top line displays, "GNU GRUB version 1.97~beta4."

But, after boot when I use the command, "grub-install -v" I get 1.98+20100804-5ubuntu3.
I'm using kernel 2.6.35-28-generic on a VMware virutal machine. I've hunted around for solutions to this without any luck. Any ideas?  Thanks!!

---

### Post by drs305 on 2011-04-11
> **doorunrun said:**
> I'm using kernel 2.6.35-28-generic on a VMware virutal machine. I've hunted around for solutions to this without any luck. Any ideas?  Thanks!!

Well, we can first see what you are really using with this command:
```
grep 'for i in' /etc/grub.d/05_debian_theme
```

Grub 1.97-beta4 will include "for i in {/boot/grub,/usr/share/images/desktop-base}/moreblue..."

Grub 1.98 will include "for i in /boot/grub/`basename ${WALLPAPER}...".

If your system is actually using 1.97 we should be able to purge and reinstall grub-common, grub-pc, since these should be the default on Maverick (2.6.35...). Since you upgraded you may still have Grub legacy remants on the system as well - the purge/reinstall would take care of them as well.

---

### Post by doorunrun on 2011-04-11
> **drs305 said:**
> Well, we can first see what you are really using with this command:
```
grep 'for i in' /etc/grub.d/05_debian_theme
```

Grub 1.98 will include "for i in /boot/grub/`basename ${WALLPAPER}...".

If your system is actually using 1.97 we should be able to purge and reinstall grub-common, grub-pc, since these should be the default on Maverick (2.6.35...). Since you upgraded you may still have Grub legacy remants on the system as well - the purge/reinstall would take care of them as well.

drs305, thanks for the quick reply! Running the command, I get the correct response for Grub 1.98, 'basename ${WALLPAPER}.......

So the purge/reinstall should do the trick, right?

---

### Post by drs305 on 2011-04-11
> **doorunrun said:**
> drs305, thanks for the quick reply! Running the command, I get the correct response for Grub 1.98, 'basename ${WALLPAPER}.......

So the purge/reinstall should do the trick, right?

I would expect it to remove the incorrect designation. I'd purge grub-common, which would remove grub-common, grub (grub legacy) and grub-pc (grub2). Then reinstall grub-pc (which will also include grub-common). 

If you need help with the screen prompts, refer to Step 4 in the 'Chroot' link in my signature line (note chroot is not required, it's just I have a more complete description of the purge/reinstall there).

---

### Post by doorunrun on 2011-04-11
Thanks again drs305 that fixed things up. Your guides are very well done and extremely helpful!!   Cheers!

---

### Post by lich 6222 on 2011-04-12
> **drs305 said:**
> Unfortunately, I believe you are correct.

When you run 'grub-install' from the LiveCD it attempts to copy the files from the */usr/lib/grub/i386-pc* folder to the /boot/grub directory (in your case the sda11 Ubuntu partition) of your real installation. For some reason this failed. The problem is most likely not with the specific file mentioned in the error message - that just happened to be the first file it tried to copy.

The problem could be with the CD, a problem writing to the partition due to a file system error, or something else. I don't know if using the wrong architecture CD (32-bit/i386 vs 64-bit/amd) would produce an error for this operation or not (both have an i386 folder). 

You might want to make sure you have a copy of the latest CD (10.04.2) since that is the version currently on your sda11 partition.

I don't see any file system errors in RESULTS.txt, but you could also run an fsck check on the sda11 partition just to be sure. Make sure the partition isn't mounted when you run the check:
```
sudo umount /dev/sda11
sudo e2fsck -f -y -v /dev/sda11
```

the problem is geting worse 
1 I can't even try to run windows 
2 I can only run with live cd atm
3 an ISO image of  Ubuntu 10.10 burned under windows will not work
4. with ubuntu 10.4 live CD I can't mount any Part of HardDisk
5.tryibg to install ubuntu in partion 15 !!
fail after copying 68% of file

for me is the question should i try to reciver windows and install 
Ubuntu after ?
or should I install Ubuntu as a new instalation  crashing all info on Harddisk

in the Mean time trying to download Ubuntu 10.10 

Anyway Thank you for the Try

---

### Post by drs305 on 2011-04-12
My usual recommendation is to get Windows working first if that is your major OS. Grub2 and Ubuntu can handle the transition. The major drawback is that when installing Ubuntu second make sure you don't overwrite the Windows partition.

You can try to restore Windows via the Windows repair disk, but the LiveCD can also do this. From the LiveCD:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
This should allow the MBR to point to your Windows boot partition and if the Windows files are still intact it should boot.

---

### Post by lich 6222 on 2011-04-12
> **drs305 said:**
> My usual recommendation is to get Windows working first if that is your major OS. Grub2 and Ubuntu can handle the transition. The major drawback is that when installing Ubuntu second make sure you don't overwrite the Windows partition.

You can try to restore Windows via the Windows repair disk, but the LiveCD can also do this. From the LiveCD:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
This should allow the MBR to point to your Windows boot partition and if the Windows files are still intact it should boot.



from terminal

 run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo apt-get install lilo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mbr
Suggested packages:
  lilo-doc
The following NEW packages will be installed:
  lilo mbr
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 415kB of archives.
After this operation, 1,331kB of additional disk space will be used.
Do you want to continue [Y/n]? y

( end from terminal)
(after operation got this screen 

ge configuration




 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring lilo &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; LILO configuration                                                        &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; It seems to be your first LILO installation. It is absolutely necessary   &#9474; 
 &#9474; to run liloconfig(8) when you complete this process and execute           &#9474; 
 &#9474; /sbin/lilo after this.                                                    &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; LILO won't work if you don't do this.                                     &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474;                                  <Ok>                                     &#9474; 
 &#9474;                                                                           &#9474; 
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
                                                                               
and hhere i t seem not to folow what you said

---

### Post by drs305 on 2011-04-12
You don't run any commands other than the first to install the lilo package and the second to point the MBR to the partition with the boot flag.

We don't really configure lilo, which is what the subsequent messages try to get you to do. A full lilo installation would include menu choices, etc. All we are trying to do is the first stage of the installation, which will transfer control to the Windows bootloader (and not lilo).

---

### Post by mörgæs on 2011-04-19
Soon a new release of Ubuntu is out, and with it comes the tidal wave of (repeated) questions. 

I have changed a lot in the original post. Could I please ask you people for a proof-reading? Thanks in advance.

---

### Post by bcbc on 2011-04-20
> **mörgæs said:**
> Soon a new release of Ubuntu is out, and with it comes the tidal wave of (repeated) questions. 

I have changed a lot in the original post. Could I please ask you people for a proof-reading? Thanks in advance.

The major Grub-related problems with Wubi have been fixed for Natty. At the moment I'm not aware of any major Wubi issues with the upgrade. I like the reference to the Wubi megathread which is the best place to get up-to-date info on current Wubi problems and fixes/workarounds. But the Wubi-specific posts in this thread related to the 10.10 upgrade are no longer relevant.

Thanks for providing this helpful thread.

---

### Post by DarkTide on 2011-04-26
Nice guide.  I hope members here will refer to this when they come to upgrade/encounter problems.

---

### Post by ghostatnit on 2011-04-28
I always get this kind of error
and the installation fails
.....
any suggestions...
installArchives() failed: perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Preconfiguring packages ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Preconfiguring packages ...
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 147677 files and directories currently installed.)
Preparing to replace tzdata 2011e-0ubuntu0.10.10 (using .../tzdata_2011g-0ubuntu0.10.10_all.deb) ...
Unpacking replacement tzdata ...
Setting up tzdata (2011g-0ubuntu0.10.10) ...

Current default time zone: 'Asia/Kolkata'
Local time is now:      Thu Apr 28 16:41:56 IST 2011.
Universal Time is now:  Thu Apr 28 11:11:56 UTC 2011.
Run 'dpkg-reconfigure tzdata' if you wish to change it.

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 147677 files and directories currently installed.)
Preparing to replace libpcsclite1 1.5.5-3ubuntu2 (using .../libpcsclite1_1.5.5-3ubuntu2.1_i386.deb) ...
Unpacking replacement libpcsclite1 ...
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
Setting up libpcsclite1 (1.5.5-3ubuntu2.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 firmware-b43-installer
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1

---

### Post by mörgæs on 2011-04-28
Please open a new thread in Absolute Beginners Talk and state everything about your hardware and the versions of Ubuntu you have tried.

---

### Post by SlyBlyahoff on 2011-04-28
Hi everyone, 

I am sorry to bother you with that reply but I would be happy if some additional information as available out there and I didn't manage to find it. 

Ubuntu 11.04 was officially released today and I am so eager updating my current Ubuntu 10.04 to it. Problem is that my Update Manager does not show me 11.04 as an available update. I asked my friends and the told me they just did it. For me it is still not accessible. Is it possible me having some system problems or some requirement that my computer configuration is not supporting? Or is it just that release is not available on all the servers yet... or too much traffic...  I don't know... 


Thank you in advance for you help, guys. 

Best Regards,
Sly

---

### Post by DuncanNZ on 2011-04-28
If you're impatient but can download the alternate iso (best to use bittorrent while the demand is so high, try here: [http://www.ubuntu.com/download/ubuntu/alternative-download#bt](http://www.ubuntu.com/download/ubuntu/alternative-download#bt)) then you can upgrade using the iso file as described here: [https://help.ubuntu.com/community/NattyUpgrades#AlternateUpgrade](https://help.ubuntu.com/community/NattyUpgrades#AlternateUpgrade)

If it's all the same to you a fresh install is however always preferable.

---

### Post by bcbc on 2011-04-28
> **SlyBlyahoff said:**
> Hi everyone, 

I am sorry to bother you with that reply but I would be happy if some additional information as available out there and I didn't manage to find it. 

Ubuntu 11.04 was officially released today and I am so eager updating my current Ubuntu 10.04 to it. Problem is that my Update Manager does not show me 11.04 as an available update. I asked my friends and the told me they just did it. For me it is still not accessible. Is it possible me having some system problems or some requirement that my computer configuration is not supporting? Or is it just that release is not available on all the servers yet... or too much traffic...  I don't know... 


Thank you in advance for you help, guys. 

Best Regards,
Sly

Open update manager, click settings, go find the settings where it says to prompt only for new LTS releases (when you install an LTS release it defaults to only prompt you for new LTS releases).
Then you'll see that Maverick is available. You have to upgrade to maverick before you can upgrade to Natty.

There are other options - like using ubiquity to install with the 'upgrade' option (that preserves /home and some custom stuff... but installs fresh stuff as well:
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
> Renewing the Installation without formating the partitons (in contrast to upgrading), will also keep the personal data and configurations under /home but will renew all system settings under /etc as well as the default set of installed packages.

PS don't forget to backup beforehand

---

### Post by ilovechi23 on 2011-04-28
ok so i upgraded today and after it install and rebooted i was stuck at this screen ( see the pic) can anyone help with this please?

---

### Post by mörgæs on 2011-04-29
Yes... follow the eight steps in the first post :-)

---

### Post by ZazzyE on 2011-04-29
Just upgraded from Lubuntu 10.10 to Lubuntu 11.04 via a fresh install.

The Loading screen has a funny error - its half on my screen, half off.  I figured graphics drivers *might* be able to fix that, but we'll see.  

But, those won't install.  The package dkms, on which nvidia-current depends, prompts me to put the install disc into my cd drive, even when I'm online. Wth? Even worse, it doesn't recognize the disc.  This happens with Apt-get and synaptic.  GmountIso has another dependency which causes this problem.

jockey-gtk can't get gain control over the folder /var/cache/archives/apt/lock/ so it doesn't do much either for my video drivers.

---

### Post by drs305 on 2011-04-29
ZazzyE,

I don't know exactly how Lubuntu works, but you most likely have to remove the installation CD from the repository (sources.list). 

In Synaptic or Software Sources, it would be under Settings, Repositories. Untick the CD reference in the lower panel. From the Ubuntu Software Center, you can access it via Edit, Software Sources.

---

### Post by ilovechi23 on 2011-04-29
> **mörgæs said:**
> Yes... follow the eight steps in the first post :-)

Was you talking about my post??

---

### Post by Automat2 on 2011-04-29
Thanks Morgaes for your guide, but I'm having a problem with the latest release of Ubuntu (11.04).

I have downloaded this OS from an alternative download (via Torrent, which has shown a lot quicker). I have created a CD from the .ISO with Brasero.

I have inserted this CD in the drive, and has started opening Synaptic. 

Rebooting the system with or without the CD on the drive has no effect -I don't think this is a live CD. Nor it has if I try to open the CD and execute "autorun" manually from the desktop > "cannot find the autorun program.

Have you got any idea to sort me out?

---

### Post by mörgæs on 2011-04-29
Thanks. 

Brasero sometimes gives trouble. I vote for Gnomebaker.

You could try the MD5 test to verify that the CD is correct:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Automat2 on 2011-04-29
Do you know what's the difference between "Desktop" and "Alternative" releases?

---

### Post by mörgæs on 2011-04-29
There is no difference regarding the system being installed. The difference is the process itself.

The alternate ISO is in coarse graphics, has no 'live' option and works on more hardware than the regular version.

---

### Post by znobrdr on 2011-04-29
Go follow the 8 steps? hmm...  Not helpful

New Ubuntu user, was pretty excited even after my crashes, and sweaty recoveries and finally getting to actually use it! Then the fatal mistake, upgrading 11.04!

Was up to date, latest ver 10.10 going to 11.04, 2.5 hours later the cute little window says about 3 minutes to go, just have to decide something related to a worm called grub.

Don't recall the choices but something along the lines of

1 keep the old one - (the one that works?)
2 try some new thing - (obscure terms that sound like it will wipe out my windows)
3 show 3 things side by side (terminal window of 4 mashed together languages)
4 Do this other thing (Actually marked "Experimental")

I chose 1 and of course it didn't work! Otherwise I'd be using the new stuff instead here instead of digging through incoherent information seeking a solution.

I realize its a different system etc. But I just don't have another 8 to 10 hours to invest in operational issues beyond a blank screen. If you're going to get to critical mass on this Ubuntu you have GOT to communicate better and more clearly. I love the idea behind it, and I am not a newbie to technology working in communications, networks, etc. Please Don't take me through 3 hours of upgrades and at then end ask me in a foreign language what to do to get the thing to boot correctly. Somebody just was not thinking here!

I did a search a few minutes ago with "11.04 upgrade" it return no entries, yet here they are. 

I am certain that my issue is simply booting but digging through a forum to find follow 8 steps of which 7 are too late is just not helpful. If Linux is so great why not run a crisis program thorough the system first to ID the top 10 "crash" issues and put up a warning to the user! Linux is fast seriously fast I love that part!

Keep up your efforts! I believe in what you are all doing and support with $ too but until mid May I can not afford to waste another 8 hours figuring out how to fix the dual boot! 
So for now, it's Windows XP continuing on.

Can I go back to 10.10 somehow?:confused:

---

### Post by drs305 on 2011-04-29
> **znobrdr said:**
> Can I go back to 10.10 somehow?:confused:

There isn't a restore function.

Are you sure that it is a GRUB problem? Are you left at a "grub" or "grub rescue" prompt, or an initramfs Busybox message? If not, it could be a video problem or something else happening after control is passed to the initrd image or the kernel.

If you want to try to fix your boot problems please boot a LiveCD, download and run the boot info script from the following site, and post the contents of RESULTS.txt. If it's a boot problem we can get it fixed.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by znobrdr on 2011-04-29
```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2can.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *      8,819,685   330,673,540   321,853,856   7 HPFS/NTFS
/dev/sda2                  63     8,819,684     8,819,622   b W95 FAT32
/dev/sda3         330,674,174   390,721,535    60,047,362   5 Extended
/dev/sda5         330,674,176   388,151,295    57,477,120  83 Linux
/dev/sda6         388,153,344   390,721,535     2,568,192  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2045 MB, 2045247488 bytes
47 heads, 46 sectors/track, 1847 cylinders, total 3994624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                 247     3,994,623     3,994,377   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        96FCDA15FCD9EF8B                       ntfs                                     
/dev/sda2        423B-2BDF                              vfat                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        0f818a6f-6714-472a-acf3-3b2840b68c3f   ext4                                     
/dev/sda6        9649e941-54ae-455b-997b-ec2f9b29632b   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        FC30-3DA9                              vfat                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/FC30-3DA9         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="6"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 0f818a6f-6714-472a-acf3-3b2840b68c3f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 0f818a6f-6714-472a-acf3-3b2840b68c3f
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0f818a6f-6714-472a-acf3-3b2840b68c3f
    linux    /boot/vmlinuz-2.6.38-8-generic root=/dev/sda5 ro   quiet splash vt.handoff=7
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0f818a6f-6714-472a-acf3-3b2840b68c3f
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=/dev/sda5 ro single 
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0f818a6f-6714-472a-acf3-3b2840b68c3f
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=0f818a6f-6714-472a-acf3-3b2840b68c3f ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0f818a6f-6714-472a-acf3-3b2840b68c3f
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=0f818a6f-6714-472a-acf3-3b2840b68c3f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0f818a6f-6714-472a-acf3-3b2840b68c3f
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0f818a6f-6714-472a-acf3-3b2840b68c3f ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0f818a6f-6714-472a-acf3-3b2840b68c3f
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0f818a6f-6714-472a-acf3-3b2840b68c3f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0f818a6f-6714-472a-acf3-3b2840b68c3f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 0f818a6f-6714-472a-acf3-3b2840b68c3f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 96FCDA15FCD9EF8B
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 423b-2bdf
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=0f818a6f-6714-472a-acf3-3b2840b68c3f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9649e941-54ae-455b-997b-ec2f9b29632b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 195.2GB: boot/grub/core.img
 171.7GB: boot/grub/grub.cfg
 170.7GB: boot/initrd.img-2.6.35-22-generic
 170.7GB: boot/initrd.img-2.6.35-28-generic
 195.5GB: boot/vmlinuz-2.6.35-22-generic
 195.5GB: boot/vmlinuz-2.6.35-28-generic
 176.0GB: boot/vmlinuz-2.6.38-8-generic
 170.7GB: initrd.img
 170.7GB: initrd.img.old
 195.5GB: vmlinuz
 195.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  f2 53 38 5d a4 52 1a d6  ec 16 01 58 d4 09 82 97  |.S8].R.....X....|
00000010  16 a1 10 50 02 e7 21 0c  15 2d be 97 11 61 08 40  |...P..!..-...a.@|
00000020  41 d1 74 2c 36 69 39 a6  f5 69 76 90 b9 17 4c 0a  |A.t,6i9..iv...L.|
00000030  bc 61 9e 3a 15 63 8d 6e  49 ad 51 e5 5c e3 db d4  |.a.:.c.nI.Q.\...|
00000040  d6 a6 cf b6 4e b4 f7 b7  d7 0f c8 ae a8 c2 3d e6  |....N.........=.|
00000050  ec f7 b4 32 3e fc a7 23  1a 77 dd 28 e8 f2 ad bf  |...2>..#.w.(....|
00000060  38 f9 63 44 07 cc fc dd  86 23 a3 3c d6 37 9b 16  |8.cD.....#.<.7..|
00000070  e4 db 57 e3 b4 91 dc 78  d6 db 69 35 62 e0 fc 7a  |..W....x..i5b..z|
00000080  cc df 00 27 23 db f8 1e  91 58 e4 f8 8d 9f 42 ce  |...'#....X....B.|
00000090  6e cb f3 37 8d 97 09 5a  7e d4 5f c3 90 34 9a a6  |n..7...Z~._..4..|
000000a0  44 dc 04 33 3b 2c 2c f1  b3 4c 26 d7 5f 31 d7 76  |D..3;,,..L&._1.v|
000000b0  18 cb ea 82 43 53 bc 95  4a 79 bf 06 25 95 57 5f  |....CS..Jy..%.W_|
000000c0  34 f5 55 56 2c b1 df a3  8d 3a 6d 1c f8 28 73 f1  |4.UV,....:m..(s.|
000000d0  6f 31 8d 3f 6a 9d 91 16  59 a9 0b 7e 45 a7 95 87  |o1.?j...Y..~E...|
000000e0  fe d8 52 cb 46 f6 f2 49  ee 57 8d c7 bf be 75 55  |..R.F..I.W....uU|
000000f0  63 72 6a 45 ae a6 fd 66  25 20 12 45 3a 74 85 45  |crjE...f% .E:t.E|
00000100  fd e9 47 d3 c9 a0 d4 fc  34 6d ea f6 8d 47 b5 63  |..G.....4m...G.c|
00000110  bf 96 fb 3b 3c 6a 5a d9  12 25 ed f9 77 e5 d6 e9  |...;<jZ..%..w...|
00000120  ae 19 d6 7e 46 09 9f 2c  31 f6 56 39 73 72 9e b5  |...~F..,1.V9sr..|
00000130  da 3e dc dc 04 55 e5 d5  ee c0 8e 73 92 e2 ee 34  |.>...U.....s...4|
00000140  83 bb b2 b4 92 81 53 b0  c4 60 aa ad 9f 8f 61 c7  |......S..`....a.|
00000150  8e 59 2f 55 e7 0f 8a d5  a9 d5 3b f6 17 51 ec e6  |.Y/U......;..Q..|
00000160  ea 20 a7 46 1a 05 55 ac  95 ce 41 92 20 44 4c 58  |. .F..U...A. DLX|
00000170  c7 2a 78 08 2a 2a 49 32  c0 ef b7 09 2a 21 b8 f4  |.*x.**I2....*!..|
00000180  43 21 a4 ea 64 e8 a7 33  62 08 d3 a2 d1 91 4a ad  |C!..d..3b.....J.|
00000190  90 5f ce 98 ca a0 42 8a  55 06 99 2e 74 c5 e4 03  |._....B.U...t...|
000001a0  22 d6 3f e4 dd d5 c3 e3  fa fc fe cd 40 48 61 0e  |".?.........@Ha.|
000001b0  26 49 72 76 66 72 ca 88  03 11 7a e8 80 57 00 fe  |&Irvfr....z..W..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 08 6d 03 00 fe  |............m...|
000001d0  ff ff 05 fe ff ff 02 08  6d 03 00 38 27 00 00 00  |........m..8'...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde

```

---

### Post by drs305 on 2011-04-29
To ensure Grub 2 is looking at the correct partition, run these commands from the LiveCD:
```

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Do not include the partition number in the second command.

We didn't get what exactly happens when you boot, but the above is the easiest thing to try. If that doesn't solve your issue, please state exactly what happens when the boot fails - error messages, prompt, etc.

If you are left at a grub prompt, please run:
```
ls (hd0,5)/boot/grub
```
and tell us if you see lots of *.mod files, among others.

---

### Post by znobrdr on 2011-04-29
Is it necessary to run from live cd? if so must live cd be 11.04?

I have access to the terminal via the version from "previous versions" running now... if I need live cd for 11.04 then will take 3 to 4 hours to download.....

---

### Post by drs305 on 2011-04-29
You are able to boot a previous kernel? The submenu contains Maverick kernels. Is it still able to boot into Maverick?

If you are still able to boot an older kernel, the chances are good that it isn't a Grub2 problem. It is more likely either a failed installation or perhaps a bad initrd image. 

For the moment, don't bother downloading the LiveCD, but please tell us what happens when you do try to select the Natty kernel.

---

### Post by znobrdr on 2011-04-29
Yes, lots of mod files.....

---

### Post by znobrdr on 2011-04-29
Sorry seems we did replies same time.....

did the modifications you suggested now have 

grub rescue>

and yes, have lots of mod files when I put in your ls command

---

### Post by ZazzyE on 2011-04-29
> **drs305 said:**
> ZazzyE,

I don't know exactly how Lubuntu works, but you most likely have to remove the installation CD from the repository (sources.list). 

In Synaptic or Software Sources, it would be under Settings, Repositories. Untick the CD reference in the lower panel. From the Ubuntu Software Center, you can access it via Edit, Software Sources.

Derp - I dunno why I checked that.  And apparently the only reason the video problem was the disc had an error or five.  Reburned, reinstalled, didn't tell the Synaptic to try to use the disc, no problems.

---

### Post by drs305 on 2011-04-29
> **znobrdr said:**
> and yes, have lots of mod files when I put in your ls command

Let's try booting from the rescue prompt:
```
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
insmod (hd0,5)/boot/grub/linux.mod
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot

```
If that fails, try these for the linux and initrd lines:
```
linux (hd0,5)/boot/vmlinuz-2.6.38-8-generic root=/dev/sda5 ro
initrd (hd0,5)/boot/initrd.img-2.6.38-8-generic
```

I'll be resuming my vacation but will check the thread tomorrow...

---

### Post by znobrdr on 2011-04-29
Let's try booting from the rescue prompt:
 	Code:
 	set prefix=(hd0,5)/boot/grub set root=(hd0,5) insmod (hd0,5)/boot/grub/linux.mod linux (hd0,5)/vmlinuz root=/dev/sda5 ro initrd (hd0,5)/initrd.img boot 
The above did not work.... error "Gave up waiting for root device"

ALERT! /dev/sda5/ does not exist. Dropping to a shell!

---

### Post by znobrdr on 2011-04-29
Could someone following this thread get me back to the original boot / Grub?

At least before I started down this path I had access to an older version of Ubuntu and my Windows, now zero!

Seems my benefactor has returned to his vacation!

---

### Post by znobrdr on 2011-04-30
Thanks for your assist 

For now, doing a full image restore back to windows on my HD. I'll be replacing this machine soon and when that happens will put Ubuntu on it again as a stand alone. Clearly for me at least dual boot system carries far too much risk of lost time and file access. 

The interactive stability is not there at this time. (should have left well enough alone) was enjoying 10.10.

Windows is not my favorite that is certain, but it's the enemy I know!

See you all again soon I'm sure. PS I didn't realize that this upgrade had just arrived. Had I known that I would have never pressed the upgrade button. To the rest of you intrepid explorers, "Onward!" Kaizen!

Thanks again for trying.:D:)

---

### Post by drs305 on 2011-04-30
> **znobrdr said:**
> Could someone following this thread get me back to the original boot / Grub?

At least before I started down this path I had access to an older version of Ubuntu and my Windows, now zero!

Seems my benefactor has returned to his vacation!

I'm still checking on the thread, just not as often as normal. Sorry I can't provide more timely inputs.

If you are still trying to resolve this let me know. It appears you have given up on this installation.

The one avenue I'd investigate is whether your BIOS can see the entire 200GB. When I asked about the *.mod files, were you checking from the grub prompt or looking at the /boot/grub folder from the LiveCD or Maverick? 

Also, at the initramfs prompt, you could run this command to see if the system can see the sda5 partition at all:
```
ls /dev/sd* /dev/disk/by-uuid
```

---

### Post by cdoebbler on 2011-04-30
I get this message when I try to update 11.04 using sudo apt-get update (I also posted the upgrade-manager error as an attached png file):
```

:~$ sudo apt-get update
[sudo] password for XX: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick InRelease                      
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) natty InRelease                     
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]  
Get:2 [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg [198 B]                   
Get:3 [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release.gpg [489 B]          
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) natty-updates InRelease                       
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [23.2 kB]    
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                               
Hit [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Get:5 [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main i386 Packages [781 B]             
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main TranslationIndex                    
Get:6 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) natty Release.gpg [198 B]                   
Get:7 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) natty-updates Release.gpg [198 B]           
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [2,808 B]         
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) natty Release                                 
Err [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) natty Release                                 
  
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) natty-updates Release                         
Err [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) natty-updates Release                         
  
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [14 B]      
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [14 B]       
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [14 B]     
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages [11.0 kB]  
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages [14 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages [4,970 B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages [14 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US               
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main Translation-en_US                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main Translation-en                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Fetched 44.1 kB in 1min 1s (712 B/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
:~$

```

---

### Post by drs305 on 2011-04-30
> **cdoebbler said:**
> I get this message when I try to update 11.04 using sudo apt-get update 
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
:~$

It appears the Natty partner repository is causing an error. Open Synaptic (System Settings (top right icon), Synaptic). Settings, Repositories, Other Software tab. Untick the Canonical Partners tab(s). Press 'Reload' or close Synaptic and run "sudo apt-get update".

If you don't get the error again, re-enable the Partners repositories if desired.

Note: I added 'code' tags to your post for formatting purposes. You generate them with the # icon in the menubar.

---

### Post by mikebravo on 2011-05-01
Would a moderator please point me toward an authoritative essay on a beginners level about how to respond to messages and choices given DURING the upgrade process. I know that at one point I was presented with a scroll box presenting four or five different options, none of which meant anything to me. I selected what I hoped was the default and plunged ahead. I would like to see a discussion of the pros and cons of all the choices one is likely to encounter during the upgrade process.

---

### Post by ken78724 on 2011-05-01
mörgæs 
Could not find an upgrade from 10.04 to 11.04 so I went to Synaptic Package Manager. Did a search for 11.04. Clicked go and apparently I created a problem, i.e., making Open Office 3.2 not open, Before I left the forum I said let me visit Mörgæs. Found some items I wished to copy on your page and paste in Open Office which the instant it opens it dies. Can I use your step below for a workaround? 
If you in spite of this want to keep exactly the same packages in the new Ubuntu installation, there is an alternative to the online upgrade. Running the command

Code:

dpkg --get-selections > installed-software

gives a text file with all installed packages on the system. If you run this command on the old system, you will have the option of running

Code:

 dpkg --set-selections < installed-software

It was a short time a clean install of 10.04 had been done on a new for me PC. I protected nothing to get the same selection of packages.

no I had not used bcscomp's precaution before upgrading, getting an external USB drive and clone my system with
    sudo rsync -ax / /media/usbdrive   
Ken

---

### Post by mörgæs on 2011-05-01
I am not sure that I understand the question.

You are mentioning Open Office. Do you really want to bring it along to 11.04, where Libre Office is installed by default?

---

### Post by jprobe on 2011-05-01
Great guide, mörgæs! :)

---

### Post by krbhnp on 2011-05-02
Hi everyone
i have been tryin to upgrade to ubuntu 11.04 from ubuntu 10.10 but sometime after i click upgrade button, it says i have no free space on /home or some folder..(I don't remember) but my drive (file system) has 26 gb of free space...please help...
i don't know much about the codes so please tell me in a layman's term..
Thanks

---

### Post by SlyBlyahoff on 2011-05-02
Hi everyone, 

I updated my Ubuntu from 10.04 via 10.10 to 11.04. Most of the features seem fine to me (not enough time to take a detailed look). Just one annoying bug occurs. When my laptop (Toshiba with nVidia video card) is idle for a long time with screensaver turned on it freezes that way. I move the mouse, try different keyboard combinations, etc. but it doesn't work. I have to restart it from the button to get back in the desktop. Does someone from you guys know how to fix that one? 

Some help on that would be greatly appreciated. Looking forward to hearing from you. 

Best Regards,
Sly

---

### Post by ronmaroria on 2011-05-02
I recently upgraded to 11.04. when i try to update from update manager, i get this error:

E:Problem executing scripts APT::Update::Pre-Invoke 'if [ -x /usr/bin/daptup ]; then /usr/bin/daptup --pre; fi', E:Sub-process returned an error code. What could be the fix??

---

### Post by Dubbayoo on 2011-05-02
i tried to enable desktop cube and now when I log in I get NO window decoration at all. I ran ccsm from terminal and disabled the cube.

---

### Post by mörgæs on 2011-05-02
The purpose of this thread was not discussing how to mend a broken upgrade. On the contrary, I hope people will choose the safe and fast solution: Reinstall, plain and simple. I have used Ubuntu from 5.10, and not once did the upgrade work.

It surprises me that people nevertheless post requests for fixing an upgrade. Did you read first post?

I get it: An Ubuntu dialog box suggested upgrading, and then it should work, right? That is a fair expectation, but reality is otherwise. Time to get experienced with reinstalling.

---

### Post by MurphysLaww on 2011-05-03
Not to be mean to Linux in general, but it seems by circular route, we are now back to what you get with windows.

A suggested upgrade should work, but 9 times out of 10, doesn't.

Obviously, the difference is that it's free, and open source, which is why I love it, but I'm a relatively computer literate person. 

I wish the masses could use this, but it's just not quite there yet. I still have to suggest win7 to friends that I don't want calling me all the time for computer advice.

My upgrade actually seems to have worked for the most part minus an issue with a broadcom wireless chipset.

---

### Post by jay-dubb on 2011-05-03
I actually did the upgrade for 10.04->10.10 and now 10.10->11.04, and it worked both times for me, however the former was with a Virtual Machine while the latter was with my desktop. Anyway, I actually did a clean re-install after finishing the upgrade, just because I was trying to pin down the potential sources of the bugs I found.

And for what it's worth, assuming you have a decent internet connection, in my experience reinstalling is *much* faster than doing the upgrade. I figure it took me about 3 hours, start to finish, to complete the upgrade to Natty, whereas it took me about 1 hour to do the reinstall (from downloading the ISO, to making the live CD, to wiping out my old install and re-installing Natty).

But I also agree that the upgrade option needs to work consistently. I wonder if it'll be more sure-fire for upgrading from 10.04->11.04 because they're both LTS (long term support) releases?

---

### Post by Riskexas on 2011-05-03
I have this problem: (i didnt want to do much stuff)
[http://ubuntuforums.org/showthread.php?p=10762669#post10762669](http://ubuntuforums.org/showthread.php?p=10762669#post10762669)

---

### Post by bcbc on 2011-05-03
> **jay-dubb said:**
> I actually did the upgrade for 10.04->10.10 and now 10.10->11.04, and it worked both times for me, however the former was with a Virtual Machine while the latter was with my desktop. Anyway, I actually did a clean re-install after finishing the upgrade, just because I was trying to pin down the potential sources of the bugs I found.

And for what it's worth, assuming you have a decent internet connection, in my experience reinstalling is *much* faster than doing the upgrade. I figure it took me about 3 hours, start to finish, to complete the upgrade to Natty, whereas it took me about 1 hour to do the reinstall (from downloading the ISO, to making the live CD, to wiping out my old install and re-installing Natty).

But I also agree that the upgrade option needs to work consistently. I wonder if it'll be more sure-fire for upgrading from 10.04->11.04 because they're both LTS (long term support) releases?

It does take longer to upgrade, but not 3 hours - that's because you're downloading all the individual packages through the update manager. If instead you download the alternate ISO and run the cdromupgrade it will take you much less time.

I've run the upgrade many times - I have a 9.10 install I updated to 10.04 and to 10.10 and soon I will upgrade it to 11.04. I've also done many Wubi upgrades for testing. In my experience it works fine most of the time - I would definitely recommend upgrading over reinstalling - just take a backup first - and check the release notes.

PS I guess you meant 12.04 in your last line.

---

### Post by Tamale on 2011-05-03
My upgrade fails with the following error:

E: Could not perform immediate configuration on 'python-pyatspi2'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)

Please help!

---

### Post by ken78724 on 2011-05-04
> **mörgæs said:**
> I am not sure that I understand the question.

You are mentioning Open Office. Do you really want to bring it along to 11.04, where Libre Office is installed by default?

Apologies. Having never used 11.04, I do not yet know about Libre Office. Just booted the PC with this problem & am looking to see if it installed via synaptic package manager. 

Wow,,, got an error message & can not log in. says "Install problem. Configuration defaults for Gnome Power Management have not been installed correctly. Contact your computer administrator. This I do not understand & this being a new PC for me, I did no backup nor did I expect synaptic package manager to get me to this new problem.

my signature is wrong for this new for me PC. Is an AUSTEK with recently added RAM and a stepped up fast Video Card which I can't give this instant. Hope that makes no difference as far as configuring the Gnome Power Manager.  

I mean, I cannot get tell you if Libre Office installed as I cannot log in. 
Your assist will be graciously appreciated.
:confused:

---

### Post by mörgæs on 2011-05-04
Thanks for the trust, but I can not help with that. My best advice is in the first post.

---

### Post by sikander3786 on 2011-05-05
> **ken78724 said:**
> Apologies. Having never used 11.04, I do not yet know about Libre Office. Just booted the PC with this problem & am looking to see if it installed via synaptic package manager. 

Wow,,, got an error message & can not log in. says "Install problem. Configuration defaults for Gnome Power Management have not been installed correctly. Contact your computer administrator. This I do not understand & this being a new PC for me, I did no backup nor did I expect synaptic package manager to get me to this new problem.

my signature is wrong for this new for me PC. Is an AUSTEK with recently added RAM and a stepped up fast Video Card which I can't give this instant. Hope that makes no difference as far as configuring the Gnome Power Manager.  

I mean, I cannot get tell you if Libre Office installed as I cannot log in. 
Your assist will be graciously appreciated.
:confused:
I think this might help.

[http://ubuntu4beginners.blogspot.com/2011/02/gnome-power-manager-error-at-login.html](http://ubuntu4beginners.blogspot.com/2011/02/gnome-power-manager-error-at-login.html)

---

### Post by tschill on 2011-05-07
Thank you for this guide, mörgaes[SIZE=1]. [/SIZE]After Ubuntu worked initially perfectly after the upgrade to 11.04, two days ago everything except the background wallpaper disappeared. Ubuntu Classic worked fine, so I followed your your link to Ubuntu for Beginners! and the hint to the command "unity -- reset" did the trick. Probably you guys here get a lot of new users like me with every upgrade, so thanks a lot for all the time and effort you spend here in the communtiy.

---

### Post by linuxftw3 on 2011-05-07
to anyone who is going to or has already upgraded to 11.04 natty, DOWNGRADE ASAP! NATTY SUCKS! the repositories are completely screwed up #-o

---

### Post by mörgæs on 2011-05-07
@tschill: Thanks. Yes, there are a lot of people getting into similar trouble every time a new release is out, because they are upgrading (as the system encourages them to do). Rather than answering each and everyone I wrote this. Sikander wrote the exact advice that helped you, though.

@linuxftw3: That was quite a statement, which you are repeating over and over. Could we ask for a little documentation and explanation?

---

### Post by PablolyonsD on 2011-05-07
[http://ubuntuforums.org/showthread.php?t=1751331](http://ubuntuforums.org/showthread.php?t=1751331)


I have a project to hand in 2moro, any help would be awesome...

---

### Post by Shalimar on 2011-05-08
I cant conect to my radio internet anymore I use a radio with login and password so it is configured as DSL. the conection is working properly cause i am using it right now at the windows i have on the same computer.
Anyone have a idea how to fix it? cause if i reinstall the older version i will have to do backup of all my data. The previos version on the grub options doest work also.

---

### Post by bcbc on 2011-05-12
> **bcbc said:**
> It does take longer to upgrade, but not 3 hours - that's because you're downloading all the individual packages through the update manager. If instead you download the alternate ISO and run the cdromupgrade it will take you much less time.

I've run the upgrade many times - I have a 9.10 install I updated to 10.04 and to 10.10 and soon I will upgrade it to 11.04. I've also done many Wubi upgrades for testing. In my experience it works fine most of the time - I would definitely recommend upgrading over reinstalling - just take a backup first - and check the release notes.

PS I guess you meant 12.04 in your last line.
So, I guess I have to eat my words a bit because my upgrade didn't go quite as smoothly as I expected...

I restored my 10.10 backup which I had moved for some other testing and ran the upgrade. I used the alternate CD but let it check online for updates as well.

Anyhow my computer froze during the upgrade (that's been happening before so not too surprising - but inconvenient). I rebooted into recovery, selected "fix package errors" and it resumed the upgrade. The next issue was it required the Natty desktop CD - which was in my sources.list for some reason - so I had to cancel, log in and edit that. Then restart my desktop with a hybrid maverick/natty mix, run an apt-get dist-upgrade. 
And finally, 3 hours later (or so) it looks like it's working fine. :)

So yeah - maybe not the simplest upgrade.

Still I would probably have restored and done it again if it failed.

---

### Post by Tuminoid on 2011-05-13
Besides having the USB gets stuck problem as described here: [http://ubuntuforums.org/showthread.php?p=10767344#post10767344](http://ubuntuforums.org/showthread.php?p=10767344#post10767344)

I now have a now problem:
update-initramfs gets stuck on every update operation, it does nothing and so update-manager/apt just sits there forever. I searched for similar problems, but all I got was an error about someone's /boot being full, but I don't have that as separate partition and my disk isn't full.

Setting up initramfs-tools (0.98.8-ubuntu3) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic

---

### Post by South Shore Pats Fan on 2011-05-13
I upgraded to Ubuntu 11.04 64 bit on an Acer Aspire laptop and when I log in, all I see is the background. Nothing else every comes on and my keyboard doesn't seem to work (although if it did I probably wouldn't be able to tell). I've seen several bug reports that Ubuntu 11.04 isn't working with my model of Aspire and I was wondering if there's any resolution.

---

### Post by Rebelli0us on 2011-05-15
It takes 15 minutes to do a clean install but many hours to upgrade, and in my experience there is always something broken after the upgrade. So why bother upgrading?

---

### Post by artoonie on 2011-05-16
So I was getting a plethora of errors which I just managed to fix. If you have similar problems to me, this might work.

I was getting the error:
> Could not calculate the upgrade
An unresolvable problem occurred while calculating the upgrade.  Please report this bug against the 'update-manager' package and include the following error message:
'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'and every time I tried to install something, I got something like:
>  upstart : Depends: mountall but it is not going to be installedAnd no suggestions on google helped.


What did work was restoring my sources.list using this site:
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

And checking all Branches, Updates, and all third-parties that I think may have been on my system.


Hope that helps someone else!

---

### Post by bcbc on 2011-05-16
> **Rebelli0us said:**
> It takes 15 minutes to do a clean install but many hours to upgrade, and in my experience there is always something broken after the upgrade. So why bother upgrading?

I would guess the average user wouldn't want to do a fresh install each time there is a new release. I know I don't.

For every seasoned user that believes the upgrade is buggy, I encourage them to test the upgrade during development - perhaps from Beta1 (or if you're brave Alpha3). It just requires a simple backup beforehand or a test computer. Then report the bugs and help make the process better for everyone.

---

### Post by mörgæs on 2011-05-17
> **bcbc said:**
> I would guess the average user wouldn't want to do a fresh install each time there is a new release. I know I don't.

Neither do I. 

I do a fresh install once a year, skipping every other release. When support is close to running out, I install the version which is about 5 months old.

---

### Post by mörgæs on 2011-05-17
@artoonie: 

That was a good idea, thanks. I shall add this to the first post.

---

### Post by tastygrue on 2011-05-18
This is my problem:
  I upgraded to 11.04, and everything went rather smoothly.  I used the computer daily, for school assignments and games and whatnot, and would suspend it after I was done.  Then one day, I decided to shut it down.  No big deal.  But when I tried to start it up again, I found that the keyboard lights (Caps Lock and Num Lock) would not turn on and no keyboard buttons would work.  And even worse, after the usual startup process, right before when my login screen would appear, what I think was a bios os select screen, (the one that lets you choose from different os's on your computer) came up, and had no timer countdown to automatically pick the os.  I hadn't configured it before since I only had Ubuntu on the computer.  And since my keyboard won't work, I can't choose anything.   So, I would really appreciate it if someone could help.  If it helps, the optical mouse light comes on.

---

### Post by sikander3786 on 2011-05-19
> **tastygrue said:**
> This is my problem:
  I upgraded to 11.04, and everything went rather smoothly.  I used the computer daily, for school assignments and games and whatnot, and would suspend it after I was done.  Then one day, I decided to shut it down.  No big deal.  But when I tried to start it up again, I found that the keyboard lights (Caps Lock and Num Lock) would not turn on and no keyboard buttons would work.  And even worse, after the usual startup process, right before when my login screen would appear, what I think was a bios os select screen, (the one that lets you choose from different os's on your computer) came up, and had no timer countdown to automatically pick the os.  I hadn't configured it before since I only had Ubuntu on the computer.  And since my keyboard won't work, I can't choose anything.   So, I would really appreciate it if someone could help.  If it helps, the optical mouse light comes on.
If possible, try with some other keyboard preferably a PS/2 one.

Or try plugging your keyboard in another USB port.

This happened to me when my printer's USB cable malfunctioned and in my case, unplugging the printer helped.

---

### Post by ACGilbert on 2011-05-19
> **tastygrue said:**
> This is my problem:
  I upgraded to 11.04, and everything went rather smoothly.  I used the computer daily, for school assignments and games and whatnot, and would suspend it after I was done.  Then one day, I decided to shut it down.  No big deal.  But when I tried to start it up again, I found that the keyboard lights (Caps Lock and Num Lock) would not turn on and no keyboard buttons would work.  And even worse, after the usual startup process, right before when my login screen would appear, what I think was a bios os select screen, (the one that lets you choose from different os's on your computer) came up, and had no timer countdown to automatically pick the os.  I hadn't configured it before since I only had Ubuntu on the computer.  And since my keyboard won't work, I can't choose anything.   So, I would really appreciate it if someone could help.  If it helps, the optical mouse light comes on.

Check boot settings and boot priority in your bios.
My 11.04 installation messed this up for some unknown reason.
Hope this helps.

AC

---

### Post by danielbu on 2011-05-30
I was happily running 9.10 in dual boot with WinXP on my Thinkpad T60. Finally found time to update to Natty. Update to 10.04 already had problems recognizing the keyboard. Somehow I got through that, then updated to 10.10 and via console to 11.04. Now I can't get Natty to recognize the whole keyboard in GUI, only in console. Weird things work: the windows key adds a number over the buttons in Unity. Some of the Fn keys work. The pointer works with both the trackpad and the red button, but neither set of mouse keys work, so I can't input my password to unlock the keyring. Recovery console works fine, and I can get into programs that work without GUI, like aptitude, from there. I have done dpkg, etc, but to no avail. ](*,)

---

### Post by hughessg on 2011-06-03
After upgrading from 10.10 to 11.04, my profile disappeared. I searched the forums and found a post with a similar issue and the fix was to make sure the UID was above 1000. My UID was 501. I am running a triple boot system on a Macbook. My bootloader  is rEFIT. I can choose OS X, Ubuntu, and Windows from that menu. When I choose either windows or Ubuntu, I get the Grub2 screen and choose the OS of my choice. Before the upgrade I could choose Ubuntu, click on my profile and load up as usual. When I originally installed Ubuntu I had switched my UID to 501 so I could read and write to my OS X partition. I had lost my profile at that time also. A workmate re-enabled my profile, but admitted he had no idea how he did it or what the original problem was. After this upgrade and changing my UID back to 1000, these are the errors I get:

1.Could not update ICEauthority file /home/USERNAME/.ICEauthority
2.There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)
3.Nautilus could not create the following required folders:/home/USERNAME/Desktop,/home/USERNAME/.nautilus.
Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them. 

So my question is: should I just format the Ubuntu partition and start new or try and salvage my profile? 

Thanks in advance!

---

### Post by dakra137 on 2011-06-03
Question: Why did update manager attempt a "partial upgrade" to my 10.04 system?

I've been running 10.04 for over a year. I have update manager set to check daily and pop up as needed. I always let it _update_ whatever is required for security or is recommended. It is also set to offer _upgrades_ to "long term support releases only"

Last night (when I got back from a trip) instead of a typical update manager display of security and recommended up_dates_, it showed as a partial distribution up_grade_, which I let it do.

Among other things, it took me to:
Linux *machinename* 2.6.32-32-generic-pae #62-Ubuntu SMP Wed Apr 20 22:10:33 UTC 2011 i686 GNU/Linux

When I run update manager now, it lists **checkbox** and **checkbox-gtk **greyed out behind a pop up that says "not all updates can be installed...."  It offers a <Partial Upgrade> button. When clicked, it churns, then says, "Your system is up to date. The upgrade will be cancelled."

Question: Is this reasonable?

Question: Is it likely to be in state the will prevent security and other updates to 10.04?

---

### Post by mörgæs on 2011-06-03
> **dakra137 said:**
> 
Question: Is this reasonable?


No, people should not be offered a partial upgrade (actually I think they should not even be offered a normal upgrade). I can hardly think of a reason for wanting a partial.
[http://ubuntuforums.org/showthread.php?t=1751299](http://ubuntuforums.org/showthread.php?t=1751299)


> **dakra137 said:**
> 
Question: Is it likely to be in state the will prevent security and other updates to 10.04?

Try the three apt-commands mentioned in the first post and watch the error messages, if any.

---

### Post by Vallard on 2011-06-03
[http://ubuntuforums.org/showthread.php?t=1744749](http://ubuntuforums.org/showthread.php?t=1744749)

Anyone can help?
More than 1k of views and only 8 answers....

---

### Post by Rebelli0us on 2011-06-04
You can fix some problems by uninstalling compiz and setting "visual effects" to None.

---

### Post by ken78724 on 2011-06-05
many thanks; found my error; the OS went on a 40 gig master with a 500 gig slave with a faulty install. But Sikander your guide will be used when I reinstall HD set aside so get 11.04 running on another PC then back to this PC which has xrun problems on the kxstduio 10.04.02 

your guide is handy, > **sikander3786 said:**
> I think this might help.

[http://ubuntu4beginners.blogspot.com/2011/02/gnome-power-manager-error-at-login.html](http://ubuntu4beginners.blogspot.com/2011/02/gnome-power-manager-error-at-login.html)

---

### Post by edfast on 2011-06-10
Not quite sure I am at the right thread, as this all came about not with a fresh install, but after updating after two-three months of happy computing using Natty installed onto a fresh SSD, but this is what just happened: I have been running natty on a macbook 2,1; no major issues. After last update (june 9) I had difficulties shutting down, so I forced the system down (maybe this was my mistake) through an 'American reboot' as it's known in Europe, ie; by pulling the plug. On restart, I get the message 'no bootable device, pls insert boot disc' and have tried since to go via various acrobatics in the terminal of the disk-booted system to try and get at what's on the hard drive, but no such luck. So what are my options now? Is there any known way by which I can restore my original system, rescue the drive or even just retrieve my data (not much)? Most of the programmes were canonical, in addition I ran Skype beta, Gmediaplayer, PlayDownloader through Java, Spotify preview, an OpenVPN utility that I never got to working properly. The last update installed updates for Chrome and possibly Skype, other than that I'm not quite certain. I have no problems booting from install-CD, but cannot seem to find my SSD, and also can't seem to get into the various startup-options via the try-Ubuntu/install-Ubuntu flash screen. Ideas? Help!

---

### Post by danielbu on 2011-06-11
I found that using aptitude in terminal to remove compiz and gnome do solved my problem.:p

---

### Post by mitae20 on 2011-06-12
hi all,


i'm a newbie to Ubuntu, was using version 9.04 and decided to upgrade to 10.04 LTS. halfway through the upgrade, my internet connection was lost and when i tried to boot my laptop i get command lines and not the graphical interface for 10.04...is there any way to manually re-install version 10.04? i'm a bit confused about what to do...

thanks!

mitae

---

### Post by mörgæs on 2011-06-12
Hi, welcome to the fora.

Yes, it is all explained in the first post.

---

### Post by AchBlewy on 2011-06-17
I recently upgraded to 11.04 using the Upgrade Manager over the network. The upgrade seemed to go fine, I think there was some hardware complaints but everything seemed fine except that all the data in my home directory is gone. I have no idea if this is important, but during the upgrade dialog I was asked if I wanted to get the encryption passprase and clicked no, but opened a terminal window and got it anyway. 

Anyway I did see that there exists a .Private folder with encrypted subfolders/files. Is it possible that my data is hiding here? I fiddled around a bit following some directions about how to manually decrypt those directories but without success. My question remains, is it possible my data is hiding encrypted in the .Private directory? If so what is the correct procedure to get it back into my home directory?

I have powered down the system to reduce the number of errors I am making. So forgive me if I am somewhat poor on details here.

Dell Precision 360

---

### Post by AchBlewy on 2011-06-18
A little bit more information: I shut down and restarted the system using a 10.4 CD. Mounted the interesting partition and peaked into my home directory. The data is all there, unencrypted. That is nice. I went ahead and tarred up the interesting parts and backed it up to a memory stick. 

There are still many possibilities about what is going on here, and I still dont know what to do to get my system running under 11.04. I will enumerate a few possible explanations: Possibility (1): My home directory is normally encrypted (the data is encrypted on a cold disk), but 11.04 does not know (and I dont know) how to unencrypt it, however, 10.4 unencrypts the thing without me having to do anything (somehow this does not seem likely). Possibility (2): The data is unencrypted on the cold disk, but 11.04 goes ahead and encrypts the thing (a) on boot up or (b) on log in and places it in the .Private directory. Possibility (3): 11.04 does not know where my real home directory is and recreates an empty new one with a standard .Private directory filled with who knows what.

I think I can easily check Possibility 2b.

---

### Post by mörgæs on 2011-06-18
I was going to suggest that you open a new thread on the topic, since there is not much advice on encryption here, but I see you have already done so. Good luck.

---

### Post by homyakchik on 2011-06-26
mörgæs:

Thanks for the excellent and informative guide. I did as was suggested and read my way through the whole thing.

I was running 10.10 until I booted into it (for the first time in a couple of months) and it asked me to upgraded to 11.04. Sucker for a Latest And Greatest that I am I let it.

Been nothing but misery so far. I was hoping there'd be a way to _uninstall_ 11.04 and take it back to 10.10 (which not only worked but which I had customized); unfortunately, reinstalling 10.10 from the CD looks to be the best all-around answer. (I can't even access the Earlier Versions that _did_ work. _Those_ lock the machine up now.) *sigh* Oh, well.

Again, thanks for all the information; I learned a lot just reading it. Keep up the good work.

Davey

---

### Post by mörgæs on 2011-06-26
Thanks! Good to hear that people can use it.

---

### Post by tommpogg on 2011-07-01
Suppose I want to do a clean installation of newer version of Ubuntu.
Suppose that my home directory is located in a ad-hoc partition.

1) How can I reinstall the OS without touching my home directory?
2) How can I set my home directory once the OS has been reinstalled
3) will any software/program installed in my home directory be available after reinstalling the OS? (supposing that there are no compatibility issues with the newer OS).

Thank you

---

### Post by trungvkvk on 2011-07-02
hello everyone.
 I just installed ubuntu should also like to participate in the topic to learn more.
 thank you for allowing me to join topic.

---

### Post by androiddurga on 2011-08-01
I am facing problem while installing android on ubuntu 10.4
ie  Could not open: /home/duproot/.android/avd/sri_avd.ini

little bit urgent plz tel me solution i want to run android apps:confused:

---

### Post by dannneman on 2011-08-02
Hello.

Im running  a 8.04 LTS ( Linux web-t 2.6.24-23-server #1 SMP Mon Jan 26 00:55:21 UTC 2009 i686 GNU/Linux)

I runned apt-get update and then apt-get upgrade.

When the process came to libc6 it stopped.. (libc6_2.7-10ubuntu8_i386.deb)
Then everyting just said.. 
error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

(couldnt even do ps or ls).


Luckily i runned under vmware and had a snapshot to revert to.

But how do I update my system?

Thanx
Daniel

---

### Post by oldunixguy on 2011-08-12
I upgraded using Update Manager from 64-bit 9.10 to 10.04lts and now get "The disk drive for /bulk is not ready yet or not present" at boot time.

On 9.10 I had /dev/md0 2-disc raid mirror that contained a Log Vol of the entire md0 for /. grub was installed on each of the raid drives.

When I now boot and it gets to the "Ubuntu" with the moving dots it displays below it "The disk drive for /bulk is not ready yet or not present" and "Continue to wait; or Press S to skip mounting or M for manual recovery". It will stay like this until I respond.

I press S and the system completes startup as it was with 9.10 without any other problems.

What is going on here and how do I cure this?

What data do you need to help diagnose this?

thanks,
oldunixguy

---

### Post by jj76541 on 2011-08-21
I have 11.04 installed on my system, with an old un useable version of windows vista. After attemtping to install bluetooth software, i get  eror messages  concerning  "S20cups" and other S20 files, and am not allowed to boot into ubuntu 11.04 at all, even after a so called clean install........ Now on my loader I have like 9 versions on ubuntu  11.04, and cant access one of them ! Theres also a note about cleaning out my "dsyslog"  im very ubuntu illiterate, and dont understand most of the terms yet, but I love how clean and simple Ubuntu is !

Any suggestions?

Thanks;

John 
[email]jj76541@ymail.com[/email]

---

### Post by mörgæs on 2011-08-22
Hi, welcome to the fora.

If both Windows and Ubuntu are unusable, I guess the best is to back up your user files and reinstall Ubuntu. If you choose 'use entire hard drive for Ubuntu' in the process, you will delete all the failed systems.

---

### Post by guy.komaclo on 2011-09-01
I have the same problem. 
I need help. In fact, during the upgrading, many times, I found on the screen windows popping up telling that "such files" is not correctly installed" other times, I had some windows where it was stated that I had some missing files.

I don't know what to do.

My screen is blank, period.

I need help


> **driversat said:**
> great work thanks!
i have upgraded from 9.10 to 10.04 online(notified by update manager)
i was during update asked to save or replace some files(i don't remember which files) and i replaced them with new suggested ones.
now my machine turns on but doesn't display the desktop menu,icons, bar...nothing but a picture of a galaxy in background.
any ideas please?
ps: 9.10 was working fine without probs and my graphics card is nvidia geforce4 mx-440

---

### Post by mue.de on 2011-09-18
Excellent Guide, thanks!
I copied it offline (Scrapbook at usb-stick) so that i have it available when i boot a live-dvd.
If i saw it before, it would have saved many hours of struggling.
I still got the system not running clean after a backport-repo-update, but's another thread

---

### Post by mörgæs on 2011-09-18
Thanks :-) Feel free to copy and distribute whenever you like.

---

### Post by rlgribble on 2011-10-14
I'm not sure if this is the right forum, but I'll give it a try.  I just upgraded to from 11.04 to 11.10.  There were two package failures - one in Nautilus (dropbox?) and the other with the flashplayer install plugin.

Reboot.  System starts to come up, then gives the message "Waiting for network configuration..." (I'm on wireless.)  Then "Waiting up to 60 more seconds for network configuration..."

The first couple of times, it proceeded to boot - but I couldn't use my login.  It accepted the password, then displayed text, then back to the main login screen (Note:  I went back to the 10.04 version of the desktop in 11.04).  I could get into a root login graphical environment.  I booted to the recovery kernel, and got into a console, where I could log in as myself (or root).  I looked and found that the ".Xauthority" file had ownership problems, which I fixed.  Note that I could connect to my wireless network while in root's graphical environment.

Now when I boot I can't even get to a graphical screen.  Period.  It still complains about the network configuration, then goes to a black screen, from which there is no recovery.

I really need my system back, and would be most grateful for any suggestions.


Thanks,

Richard.

---

### Post by mörgæs on 2011-10-15
> **rlgribble said:**
> I'm not sure if this is the right forum...

After reading the first post in full length you will know :-)

---

### Post by mrnilspeters on 2011-10-15
Just a short notice:
Upgrading to Ubuntu 11.10 not recommended for Nokia Booklet Users.

After upgrading a running version of 11.04 to 11.10 I got the "network timeout" bug. After fixing that, X "couldn't find a screen". Spent some hours trying to fix that. Then I switched tactics and tried a complete new installation of 11.10 which hangs during the installation process:
"init: lightdm main process (2854) terminated with status 1"

I've done some hours of research and now switch back to Ubuntu 11.04 which was working "almost fine".

Maybe it was a bit early to adopt to the new Ubuntu 11.10. IMHO wait for new release.

---

### Post by christosophia on 2011-10-15
> **mrnilspeters said:**
> Just a short notice:
Upgrading to Ubuntu 11.10 not recommended for Nokia Booklet Users.

After upgrading a running version of 11.04 to 11.10 I got the "network timeout" bug. After fixing that, X "couldn't find a screen". Spent some hours trying to fix that. Then I switched tactics and tried a complete new installation of 11.10 which hangs during the installation process:
"init: lightdm main process (2854) terminated with status 1"

I've done some hours of research and now switch back to Ubuntu 11.04 which was working "almost fine".

Maybe it was a bit early to adopt to the new Ubuntu 11.10. IMHO wait for new release.

Can you switch back painlessly?

---

### Post by mrnilspeters on 2011-10-15
> **christosophia said:**
> Can you switch back painlessly?

Wouldn't say that exactly. I did a complete reinstall "to save some time" ;) After all I should have researched a bit more before installing the update.

---

### Post by cidthecoatrack on 2011-10-16
So I'm not sure if this is the correct place to post - if not, please feel free to redirect me. :)

My current issue is that I upgraded to Xubuntu 11.10, but after the upgrade, I got the "boots to a black screen" issue.  At first the problem seemed to be the graphics drivers, so I installed the nvidia drivers.  Then startx wouldn't work.  I have tried what feels like everything short of a fresh install.

The error that startx throws isn't even helpful.  It just says "connection to X server lost" and stops.

Any thoughts/helpful comments?

---

### Post by agtejeo on 2011-10-17
Not sure this is the correct forum to post this but:

after upgrading from 11.04 to 11.10 (Kubuntu both), libreoffice-impress doesn't make 3d-opengl transitions as before (obviously, libreoffice-ogltrans is installed).

Suggestions?

---

### Post by mörgæs on 2011-10-17
What makes you not sure?

---

### Post by trouserless on 2011-10-17
Aventail VPN client no longer works.  This appears to be an error with the libssl and libcrypto library versions.  I've tried to re-install the client and it cannot locate the aforementioned libraries with the following error:


Installing Aventail Connect 10.0.4.035...
This version of Aventail Connect is already installed.
Would you like to reinstall it? (y/n) y
Uninstalling Aventail Connect 10.0.4.035...
Aventail Connect uninstall complete.
Looking for tun driver...  tun is present and correct.
Unpacking archive AventailConnect-Linux-10.04.035.tar.bz2...
Setting up permissions...
Using certificates in /etc/ssl/certs
Resolving dependencies for 64-bit OS ...
Resolving dependencies for 64-bit OS ...
Resolving dependencies for 64-bit OS ...
Resolving dependencies for 64-bit OS ...
Aborting install, AvConnect has unresolved dependencies
	linux-gate.so.1 =>  (0xf76f5000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf76b5000)
	libssl.so.0.9.7 => not found
	libcrypto.so.0.9.7 => not found
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf75c9000)
	libm.so.6 => /lib32/libm.so.6 (0xf759f000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7581000)
	libc.so.6 => /lib32/libc.so.6 (0xf7407000)
	/lib/ld-linux.so.2 (0xf76f6000)

I have manually checked for libssl and libcrypto versions 0.9.7 and they are links from /lib32 into the 0.9.8 versions of the same files.  I noticed also that libssl.so.1.0.0 and libcrypto.so.1.0.0 also exist on this system (both different 32bit ELF files, not symlinks).

edit:  this was after an upgrade from Natty

---

### Post by rafaelcbf on 2011-10-17
I run apt-get install -f and I get this 


rafaelcbf@rafaelcbf-AOA150:~$ sudo apt-get install -f
[sudo] password for rafaelcbf: 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
liblash3 libpanel-applet-4-0 libboost-python1.46.1 libswscale0 python-opengl
libbluray0 libswt-gnome-gtk-3.6-jni phonon python-gtkglext1 libpostproc51
python-pypdf libwsutil0 libboost-thread1.42.0 libswt-gtk-3.6-java
libavformat52 libdvbpsi6 virtualbox-ose-guest-utils
libswt-webkit-gtk-3.6-jni libswt-cairo-gtk-3.6-jni libswt-gtk-3.6-jni
python-rsvg libavfilter1 phonon-backend-gstreamer libmagick++3 libphonon4
libcheese-gtk18 libwireshark0 python-pythonmagick virtualbox-ose-guest-dkms
libquicktime1 libwiretap0 libgtkglext1 libglademm-2.4-1c2a freeglut3
libmatroska3 gir1.2-panelapplet-4.0 libboost-python1.42.0 libavdevice52
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
binutils
Suggested packages:
binutils-doc
The following packages will be upgraded:
binutils
1 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
8 not fully installed or removed.
Need to get 0 B/2,387 kB of archives.
After this operation, 1,090 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 224850 files and directories currently installed.)
Preparing to replace binutils 2.21.0.20110327-2ubuntu3 (using .../binutils_2.21.53.20110810-0ubuntu3_i386.deb) ...
Unpacking replacement binutils ...
dpkg-deb (subprocess): failed to read on buffer copy for failed to write to pipe in copy: Input/output error
dpkg-deb: error: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/binutils_2.21.53.20110810-0ubuntu3_i386.deb (--unpack):
short read on buffer copy for backend dpkg-deb during `./usr/share/man/man1/ld.bfd.1.gz'
Processing triggers for man-db ...
Errors were encountered while processing:
/var/cache/apt/archives/binutils_2.21.53.20110810-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


What can I do? I need to do it so I can use the Ubuntu Software Center.

---

### Post by c69 on 2011-10-17
The developers should all be shoved out an airlock.
 
If this is such a "major" release to involve such hardship, then it should have gotten a major revision number. 
 
Going from 11.04 to 11.10 seeemed innocuous, but now my development platform, including all tools is bricked, without network access, in some unknown state of repair.
 
Besides trying to roll back or salvage the repair, I have a good 80 hours in tools and configuration work on this install, that is likely lost, along with all the time being lost to fixing this debacle.

---

### Post by mörgæs on 2011-10-18
The numbers refer to year and month of the release. They do not indicate what is major and what is minor.

I understand your anger, but it is better to post it somewhere else. This thread is meant for advice regarding a fresh install.

---

### Post by birchb1024 on 2011-10-19
[COLOR=DarkGreen]**Ubuntu upgrade (from  Natty to Oneric) **[/COLOR][B]Not much working 

[/B] I run an  ASUS U50V laptop, nothing special. All these things don't work any more:

[LIST]
[*]The 'terminal' icon is blank.
[*]My desktop background has gone
[*]The Firefox icon is blank.
[*]Only 2D login session works
[*]System monitor icon is blank.
[*]With only Firefox and System Monitor running, 920 Mbyte RAM is being used !!! WTF? THAT IS NEARLY A GBYTE.
[*]My default application settings are gone.
[*]The System Info icon is blank.
[*]The boot time is now very long. Display a message about waiting for  network configuration. Then another about waiting another 60 seconds.  Zzzzzzz
[*]The laptop keyboard back lighting does not work, where it did on Natty.
[*]Home Folder icon is blank
[*]TortoiseHG has disappeared from Nautilus
[*]Dash icons are blank for MP3 .SH  and many other file types.
[*]There are three dash icons for VirtualBox, no hint why.
[*]My custom menu has disappeared, well all the menus are gone :sad:
[*]After running Xine, the Dash disappears altogether leaving a black  bar at the top of the screen. And the "Menu bar has disappeared, so no  way to control running application windows.
[*]OK now my session is totally wedged because both Dash and the Menu  bar have gone. Well actually it's not gone it's just invisible. [COLOR=Red]Workaround is to get lucky and hit the 'Workspaces' icon. [/COLOR]
[*][COLOR=Red][COLOR=Black]In Nautilus and on the desktop, directories have 'file' icons. 
[/COLOR][/COLOR]
[*][COLOR=Red][COLOR=Black]Banshee fails to launch. Totally.
[/COLOR][/COLOR]
[/LIST]
[LEFT][COLOR=Red][COLOR=Black]Can anyone figure out why there are so many blank icons?

[/COLOR][/COLOR][/LEFT]

---

### Post by cidthecoatrack on 2011-10-19
> **cidthecoatrack said:**
> So I'm not sure if this is the correct place to post - if not, please feel free to redirect me. :)

My current issue is that I upgraded to Xubuntu 11.10, but after the upgrade, I got the "boots to a black screen" issue.  At first the problem seemed to be the graphics drivers, so I installed the nvidia drivers.  Then startx wouldn't work.  I have tried what feels like everything short of a fresh install.

The error that startx throws isn't even helpful.  It just says "connection to X server lost" and stops.

Any thoughts/helpful comments?
Well, got it solved: Managed to save the files I needed and just did a clean install, which solved the problem.  The problem probably came from trying to do the distro upgrade from within X; know better for next time. :)

---

### Post by gringo loco on 2011-10-22
Great sig quote, may I use it? how would you like the credit to read?? thinking about it made my update problem seem awfully insignificant.

---

### Post by mörgæs on 2011-10-22
Feel free to use my signature as you want. You don't have to mention me, just spread the word.

Thanks for asking, though.

---

### Post by littlebird on 2011-10-23
Ok, so I have been going over this issue in another thread (Failed Upgrade in Installations and Upgrades), but thought someone might have some ideas over here.  I recently upgraded from 11.04 to 11.10, which was at first a major problem, but have been able to upgrade the system to 11.10 (thanks to jimbo99 and wnelson!) via the terminal with alt-ctrl-f1.  

The problem I now have is a non-existent GUI.  A normal boot gives me the normal load screen, and then a black screen with the textual description of what the computer is thinking (checking battery state, stopping bluetooth, etc.).  I have tried to install Unity via the terminal (sudo apt-get install unity, hope that's correct), but I keep getting an error message : "Errors were encountered while processing: flashplugin-downloader
                                                                                flashplugin-installer
                  E:Sub-process/user/bin/dpkg returned an error code (1)"

After this, the install aborts.  I tried installing GNOME instead with no luck, the packages failed to load completely.  ](*,) Any ideas?

---

### Post by qtat43 on 2011-10-23
with the upgrade a message of "the support is limited for your graphics hardware, may have problems after upgrade" since then my adobe keeps crashing, its up to date. I am new to everything and don't know what to do to fix it?

---

### Post by trouserless on 2011-10-24
> **trouserless said:**
> Aventail VPN client no longer works.  This appears to be an error with the libssl and libcrypto library versions.  I've tried to re-install the client and it cannot locate the aforementioned libraries with the following error:


Installing Aventail Connect 10.0.4.035...
This version of Aventail Connect is already installed.
Would you like to reinstall it? (y/n) y
Uninstalling Aventail Connect 10.0.4.035...
Aventail Connect uninstall complete.
Looking for tun driver...  tun is present and correct.
Unpacking archive AventailConnect-Linux-10.04.035.tar.bz2...
Setting up permissions...
Using certificates in /etc/ssl/certs
Resolving dependencies for 64-bit OS ...
Resolving dependencies for 64-bit OS ...
Resolving dependencies for 64-bit OS ...
Resolving dependencies for 64-bit OS ...
Aborting install, AvConnect has unresolved dependencies
	linux-gate.so.1 =>  (0xf76f5000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf76b5000)
	libssl.so.0.9.7 => not found
	libcrypto.so.0.9.7 => not found
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf75c9000)
	libm.so.6 => /lib32/libm.so.6 (0xf759f000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7581000)
	libc.so.6 => /lib32/libc.so.6 (0xf7407000)
	/lib/ld-linux.so.2 (0xf76f6000)

I have manually checked for libssl and libcrypto versions 0.9.7 and they are links from /lib32 into the 0.9.8 versions of the same files.  I noticed also that libssl.so.1.0.0 and libcrypto.so.1.0.0 also exist on this system (both different 32bit ELF files, not symlinks).

edit:  this was after an upgrade from Natty

Figured this out out, hope this helps someone:

the problem was that the Aventail (SonicWall VPN client) is 32bit software and required the 32bit libraries to work properly.

In order for this client to find the libraries it needs (libssl/crypto.so.0.9.7), create symlinks to the backward compatible libraries of the right architecture (32, not 64).  Oneric installs libssl/crypto.so.0.9.8 32 32bit in (/usr/lib32) and 64 in /usr/lib.

Simply create a symlink from the 64bit library directory for each of these libraries to their 32bit backward compatibility library and it works:

cd /usr/lib ; sudo ln -s /lib32/libcrypto.so.0.9.8 libcrypto.so.0.9.7

cd /usr/lib ; sudo ln -s /lib32/libssl.so.0.9.8 libssl.so.0.9.7

and it all works (finally).

---

### Post by TexasPedi on 2011-10-25
During the upgrade from 11.04 to 11.10, via wireless, the computer froze, so I restarted it--it does not load Ubuntu anymore, nor does it try to upgrade. I have tried restarting it in safe mode--but it comes to a point and does not proceed. Restarting it in "regular" mode brings it to a blank screen with [ok] on the top right corner.
Restarting with new Ubuntu 11.10 cd does not make it work---it comes to a point where it says--"Computer needs to restart and upgrade" or something to that effect---but does not upgrade.
please advise, thanks, TexasPedi.

---

### Post by TexasPedi on 2011-10-25
last line on rebooting in safe mode is roo@yt-Latitude-E6500:^#

---

### Post by mörgæs on 2011-10-26
Did you read first post in this thread?

By the way, enabling root is not recommended:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by TexasPedi on 2011-10-26
yes, I read  the first post, and have googled the heck out of the problem. I still am not able to have any Ubuntu back--not the old 11.04 or the new (partially upgraded 11.10).
It is very surprising that will all the problems that the upgrade seems to be causing, THAT there is no simple fix. This would not have happened in Windows--atleast it has not happened in the last 20 years. I would have "system restored" it.
Is there no "overwrite and format all the previous hard drive space and install a new version" type solution that ubuntu has? I am willing to forgo all the stuff that I had on the drive( It was a backup!!)

---

### Post by mörgæs on 2011-10-26
> **TexasPedi said:**
> 
Is there no "overwrite and format all the previous hard drive space and install a new version" type solution that ubuntu has?

Yes, that is exactly what the thread is about. How do 11.04 and/or 11.10 run in a live boot?

---

### Post by TexasPedi on 2011-10-26
I CANNOT do an install. 

The computer just says "take the disc out and press enter"--and then goes into a fit/spasm, and gets stuck. All the sudoing to get upgrades and updates and checking graphic cards have not been able to put Humpty Dumpty together again. 

At this point it has become like a challenge to "repair" this--more for "fun" than for necessity. I do not plan to do anything substantial with my Ubuntu now.

---

### Post by equusdruides on 2011-10-31
Hi all,

I am trying to go from 10.04 to 10.10 on an dell mini netbook.  I keep getting this error:

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release](http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release)  Unable to find expected entry  (Source/binary-i386/Packages in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

Any ideas?

Thanks in advance!

---

### Post by equusdruides on 2011-11-07
Did I put the above post in the right place?  I am new at this.

---

### Post by mörgæs on 2011-11-07
If you read the first post, you would know the answer: This thread is meant to help people with a fresh install, not with trying to fix a failed upgrade, which is often a waste of time. 

However, your problem does seem to be possible to solve. You could try to change mirror as a first step.

---

### Post by equusdruides on 2011-11-08
Thanks for the reply.

This machine came with Ubuntu 9.04.  I have had no problem upgrading until now.  (Trying to go from 10.04 to 10.10 for starters)  Should I try another version such as Lubuntu and if so will I lose all the info on this netbook?  I am a total newb at this and I don´t pretend to be able to solve this on my own.  I am good at following directions.  I read through the first post before posting here but I did not find a way (at least one I could see) around this error.  Where do we go from here?

Thanks.

---

### Post by James Keating on 2011-11-08
Upgrading to 11.10 left both of my laptops unable to boot into any session. I burned a CD of Lubuntu and installed that, and am happy happy happy. This is what Linux should be, fast and easy. It has all the good Ubuntu stuff that makes wireless and printing easy, and rips out all the stuff that is annoying and slow. There isn't much missing, and adding what you want is easy.

Lubuntu will give you an option to keep your personal files while upgrading. I didn't lose anything. 

But back up your home directory first. Use something that is a front end for rsync. Or run it as a command or script: 
sudo rsync -av --delete  --exclude .gvfs /home/you/ /media/disk/home/you 

Before upgrading, note what programs you use -- e-mail, browser, editors, etc. Lubuntu has its own default set, all very simple. Then reinstall them. 

After installation, I removed
abiword 
gnome-mplayer 
leafpad
xpad
gpicview
mtpaint 
pidgin
sylpheed
ttf-indic-fonts-core ttf-kacst-one
ttf-khmeros-core ttf-lao ttf-thai-tlwg
xfishtank 
xdaliclock 
xscreensaver
xscreensaver-gl 

You won't use the same set of programs as me, but put in at least
lubuntu-restricted-extras
for Java runtime environment, Microsoft fonts, Flash plugin, DVD playback, LAME (to create compressed audio files) and patent codecs for Chromium.

I had video trouble for a while (couldn't play downloaded .flv files for a while, but it seems to have sorted itself out) and also installed
gstreamer-gconf
gstreamer-plugins-base-apps
ffmpeg
gnome-codec-install 
libavcodec-extra
libavformat-extra
libavdevice-extra
libavutil-extra
libpostproc-extra
libswscale-extra

I also had to go into VLC and set video output to X11 (xcb).

My soundcard wasn't recognized, so I had to install and run alsamixer from the command line and select the sound card. (Alsamixergui doesn't have this option.)

---

### Post by mörgæs on 2011-11-08
> **equusdruides said:**
> 
Should I try another version such as Lubuntu 


Yes, you should try a live boot of any distro you can get your hands on. There is no one-size-fits-all. After that you know better which one to install.

> **equusdruides said:**
> 
... and if so will I lose all the info on this netbook?


If 'info' means your user files, then no. Just follow step 5 in the guide. 


> **equusdruides said:**
> 
I read through the first post before posting here but I did not find a way (at least one I could see) around this error.


Exactly which step/formulation didn't you understand? I am happy to change it, if something is unclear.

---

### Post by mörgæs on 2011-11-08
@James Keating:

Yes, Lubuntu and Xubuntu are really getting a following these days, and that is well deserved. There is more Lubuntu advice here:
[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)

You have done a lot of modifications to your system, but I think it is important to note that most users will have a great Lubuntu installation by just doing a next-next-next-finish.

---

### Post by enkr1pt3d on 2011-11-09
I have searched around here, found people with similar problems around, but not quite the same.

First of all, im a complete noob at linux in general.

I have made a live USB instalation with the ubuntu 11.10 into a usb pen.

Everything was working great and i was really happy with it. Until.. i decided to download the updates.

After that the system just freezes when booting up, and displays the message:


"Waiting for network configuration"

and then

"Unatended upgrade in progress during shutdown sleeping for 5 seconds"

i pressed ESC and the screen displays the same message over and over again:

"error: ext2_lookup:deleted inode referenced 261906"

and thats it.. cant do anything else about it.. I couldnt find and answer for this problem anywhere else so far... 

Any one has any idea on how to solve this? Or anyone has had similar problem with this? 

thanks in advance for any help someone can give me.

---

### Post by love2learnlinux on 2011-11-30
I have the exact same problem.  It seems file system related, I've tried playing with different commands like fsck and msdosfsck, but I'm new to this too so I have no idea what I'm doing.  Any help would be appreciated.

---

### Post by mörgæs on 2011-12-01
Hi, welcome to the fora.

If you want help then you need to provide us with much more information. 

Which Buntu release are you using?
How was it installed?
Did it work before?
Have you installed all updates?
Which hardware are you using?
What is "the exact same problem"? Do you mean the "waiting for network configuration"-message?
and so on
and so on.

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by love2learnlinux on 2011-12-13
Hi, thanks for asking

Which Buntu release are you using?
--Ubuntu 11.10, same as enkr1pt3d
How was it installed?
--On a USB drive, using persistence, same as enkr1pt3d
Did it work before?
--yes, a few times and I was very happy with it, same as enkr1pt3d
Have you installed all updates?
--yes, same as enkr1pt3d
Which hardware are you using?
--8GB PNY USB Drive, in a DELL E6400 orginally, now I tried it in a DELL D610, 
What is "the exact same problem"? Do you mean the "waiting for network configuration"-message?
--yes

Hopefully, I got the details right this time :)

I'm getting the idea that one should not update persistent USB drive installations.  Can one to a 'full install' on a USB drive?

Sorry, I really don't know what I'm doing.

---

### Post by dakra137 on 2011-12-13
to love2learnlinux re Can one to a 'full install' on a USB drive?

YES. What I do:

Use an 8GB flash drive or memory card. 

Create 2 partitions,ONE 6GB as EXT2 or EXT3 but not EXT4,since it has the extra logging. I call the partition USBLINUX. 2nd 2GB partition as SWAP.

I do not think you will need  HP USB Disk Storage Format Tool SP27213.exe HPUSBFW.exe to make it bootable. YMMV.

Install linux onto it from the installation CD/DVD. (be careful to select the USBLINUX partition as the target for both the install and GRUB)

When it is done, look for and examine the USB's /etc/grub/grub.cfg or /boot/grub/grub.cfg file. If the "**search**" and "**linux**" statements do not use uuid's, then try
**sudo update-grub**

If that doesn't update the USB's grub.cfg file, then 
**sudo grub-mkconfig -o /*pathtotheUSB*/grub.cfg**
where ***pathtotheUSB*** is wherever the install placed grub.cfg on the USB drive.

This is important to get grub.cfg to specify UUID's for both the search and linux statements. Otherwise, the stick may not boot on other machines or even this one if  partitions are changed on hard drives or other devices added or removed.

When it is all working, I manually edit the grub.cfg (a NO NO, I know know) to remove menu sections for other than the USB stick.

---

### Post by trouserless on 2011-12-13
> **trouserless said:**
> Figured this out out, hope this helps someone:

the problem was that the Aventail (SonicWall VPN client) is 32bit software and required the 32bit libraries to work properly.

In order for this client to find the libraries it needs (libssl/crypto.so.0.9.7), create symlinks to the backward compatible libraries of the right architecture (32, not 64).  Oneric installs libssl/crypto.so.0.9.8 32 32bit in (/usr/lib32) and 64 in /usr/lib.

Simply create a symlink from the 64bit library directory for each of these libraries to their 32bit backward compatibility library and it works:

cd /usr/lib ; sudo ln -s /lib32/libcrypto.so.0.9.8 libcrypto.so.0.9.7

cd /usr/lib ; sudo ln -s /lib32/libssl.so.0.9.8 libssl.so.0.9.7

and it all works (finally).


I forgot to mention one should also install the libs they are asking for and run the commands above as Ubuntu ships with the 1.0 version of the libs by default:

sudo apt-get install libssl0.9.8:i386

hope this helps too..

---

### Post by DavidS on 2011-12-25
I have been running Ubuntu 10.10 on my main computer.  Last night I upgraded to 11.04.  

After the upgrade it seemed that the boot process stops completely after reporting:

* Starting TiMidity++ ALSA midi emulation...   [ OK ]

but I now find that the problem seems to be simply that gdm won't start.

Before upgrading I copied the whole system to another partition, "just in case".  I didn't copy the /home folder, which is on a partition of its own.

As well as the new kernel, the grub menu shows the old kernels and correctly states the partition I copied them to.  I can boot the computer using the latest of these (2.6.35-31-generic).  It seems to boot correctly (including gdm), apart from the fact that some of the user settings have been changed, of course.  When I go to a console, though, it reports the system as "Ubuntu 11.04 (GNU/Linux 2.6.35-31-generic i686)".

Using the new kernel, if I log in on a console as root and then type 'gdm' I get:

** (gdm-binary:2214): WARNING **: Failed to acquire org.gnome.DisplayManager
** (gdm-binary:2214): WARNING **: Failed to acquire name; bailing out

I find that there is a process "gdm-binary" running.  If I kill it, and then type 'gdm' at a root prompt, I get 6 lines similar to:

gdm-binary[2253]: WARNING: GdmDisplay: display lasted 0.050740 seconds

Looking at the Xorg logs, I find "NVIDIA: Failed to load the NVIDIA kernel module." etc.

The nvidia module appears to exist in /lib/modules/2.6.38-13-generic-pae/kernel/drivers/video/nvidia/ (which is the new kernel)

What should I do next to find out why the old kernel loads its nvidia module OK but the new one doesn't?

David

---

### Post by love2learnlinux on 2011-12-28
Thanks [dakra137]("http://ubuntuforums.org/member.php?u=1035644"),
Now that the holidays are over I'll give this a try.

---

### Post by aaazman on 2011-12-31
Folks:

I have installed, configured, and **updated** numerous times with Ubuntu 11.10 onto both USB flash drives (i.e., 4GB and 8 GBs.) After a couple of reboots or more, it will get stuck at boot time. I clicked Ctrl-Alt-F1 and watched the different messages. USB drive problems, INODEs, Unattended Update, and Waiting for Networking, are commonly displayed. Ctrl-Alt-F7 takes you back to X, but the screen still has the boot dots. Sometimes, I get a login screen! I usually use the latest USB/Flash Drive Installation application under Windows for persistent installation. Sometimes, I managed to reach the Desktop but no networking for any browser at all! I also tried Mint 12 (i.e.,from Ubuntu,) after update, it displayed same issues!

I have resorted just installing LTS 10.04 for both USB/Flash drives. Everything works except some problems with Linux Image Kernel V3. At the very least it can be downgraded to a previous version.

---

### Post by Eidmantas on 2012-01-18
Hi guys,

Just did an update. And I've got this problem. From all the sound troubleshooting I did, Ubuntu still has all the audio drivers on the terminal atleast theyre shown. The problem is that I  get sound on the minimum level only, and the device shown on input/output UI is gone. 

Sadly, with the functon + volume up/down keys I can't control my sound (Nothing happens), with the slider also - nothing. It's always on the very minimum side. The terminal mixer's sound are all up.What could be the problem? Thanks.

[http://imageshack.us/photo/my-images/40/screenshotat20120118210.png/](http://imageshack.us/photo/my-images/40/screenshotat20120118210.png/)
[http://imageshack.us/photo/my-images/812/screenshotat20120118210.png/](http://imageshack.us/photo/my-images/812/screenshotat20120118210.png/)
[http://imageshack.us/photo/my-images/853/screenshotat20120118210.png/](http://imageshack.us/photo/my-images/853/screenshotat20120118210.png/)

---

### Post by mörgæs on 2012-01-19
For sound problems this thread is better:

[http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)

---

### Post by Eidmantas on 2012-01-24
> **mörgæs said:**
> For sound problems this thread is better:

[http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)
Function key combinations apart from the screen brightness don't work anymore aswell, I guess I need a fresh install.

---

### Post by yo_bhan on 2012-02-29
> **Eidmantas said:**
> Function key combinations apart from the screen brightness don't work anymore aswell, I guess I need a fresh install.

solved here
[http://ubuntuforums.org/showpost.php?p=11424797&postcount=6](http://ubuntuforums.org/showpost.php?p=11424797&postcount=6)

---

### Post by mortenmeldal on 2012-03-14
Hi Im MPM,
I have ubuntu studio 11.10 and upgraded and i have a very specific problem with kde-runtime-data which will not install and gives the error:

E: /var/cache/apt/archives/kde-runtime-data_4%3a4.7.4-0ubuntu0.1_all.deb: short read on buffer copy for backend dpkg-deb during ./usr/share/kde4/services/searchproviders/beolingus.desktop'

It does not matter what I do it wont install. All other KDE dependencies are OK it is just this file and the kde-runtime appear as broken?? Any advice will be appreciated.

Kind regards
MPM

---

### Post by Keith_Beef on 2012-03-15
> **mortenmeldal said:**
> Hi Im MPM,
I have ubuntu studio 11.10 and upgraded and i have a very specific problem with kde-runtime-data which will not install and gives the error:

E: /var/cache/apt/archives/kde-runtime-data_4%3a4.7.4-0ubuntu0.1_all.deb: short read on buffer copy for backend dpkg-deb during ./usr/share/kde4/services/searchproviders/beolingus.desktop'

It does not matter what I do it wont install. All other KDE dependencies are OK it is just this file and the kde-runtime appear as broken?? Any advice will be appreciated.

Kind regards
MPM

It looks like the package file might have been corrupt... 
[http://raphaelhertzog.com/2011/06/27/deciphering-one-of-dpkgs-weirdest-errors-short-read-on-buffer-copy/](http://raphaelhertzog.com/2011/06/27/deciphering-one-of-dpkgs-weirdest-errors-short-read-on-buffer-copy/)

---

### Post by MAFoElffen on 2012-03-15
> **mortenmeldal said:**
> Hi Im MPM,
I have ubuntu studio 11.10 and upgraded and i have a very specific problem with kde-runtime-data which will not install and gives the error:

E: /var/cache/apt/archives/kde-runtime-data_4%3a4.7.4-0ubuntu0.1_all.deb: short read on buffer copy for backend dpkg-deb during ./usr/share/kde4/services/searchproviders/beolingus.desktop'

It does not matter what I do it wont install. All other KDE dependencies are OK it is just this file and the kde-runtime appear as broken?? Any advice will be appreciated.

Kind regards
MPM
Not sure all you have installed or not. But, 
Here's what I have install that is related:

kde-runtime
 - kde-runtime-data
 - plasma-scriptengine-declarative
 - plasma-scriptengine-javascript

Note that the packages above after the "-" are 3 packages that are a part of kde-runtime... so when you install kde-runtime, the other 3 packages are installed.

What I notice on packages that don't want to install,  I first check what the install log says to see what the dependencies are. Sometimes, it's not a dependency  problem, but rather a conflict with a package that is already installed.

---

### Post by mörgæs on 2012-03-24
After more than 100.000 page views this thread has served its purpose. Many of the posts are (fortunately) obsolete now, since Buntu has evolved quite a bit. 

Thanks for posting, everybody.

The thread is closed, but a [new one]("http://ubuntuforums.org/showthread.php?p=11789959") is available.

---

