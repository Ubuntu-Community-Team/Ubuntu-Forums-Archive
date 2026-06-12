---
title: "I upgraded, and now I have this error..."
date: 2012-03-24
forum: Installation &amp; Upgrades
---

### Post by mörgæs on 2012-03-24
(The old thread is visible [here]("http://ubuntuforums.org/showthread.php?t=1580857")).


[SIZE=3]**[COLOR="Red"]First: If you are thinking of posting in the thread, please read this post thoroughly.[/COLOR]**[/SIZE]


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

