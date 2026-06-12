---
title: "Upgraded from Ubuntu 14.04 to 14.10, System Boots to Black Screen"
date: 2014-12-27
forum: Installation &amp; Upgrades
---

### Post by skppy1225 on 2014-12-27
Hello.

Today I upgraded from Ubuntu 14.04 to Ubuntu 14.10. I also did a bunch of software updates on the machine while it was running 14.04, since it had been a while since I'd booted into Ubuntu. However, after I rebooted the machine upon installation, I was only taken to a black screen. I was reading some posts online and I found out that AMD graphics cards have issues running with Ubuntu 14.10. My machine has an AMD A-10 5800K APU with Radeon HD Graphics. The instructions I found online were to get to a TTY1 terminal and run a few commands to remove the drivers. The problem is that hitting CTRL + ALT + F1 does not take me to a TTY1 terminal and the black screen doesn't change. Any help would be greatly appreciated.

These are the instructions that I was attempting to follow to fix the problem: [https://mwop.net/blog/2014-11-03-utopic-and-amd.html](https://mwop.net/blog/2014-11-03-utopic-and-amd.html)

---

### Post by MAFoElffen on 2014-12-27
At boot, just as the BIOS messages pass, start pressing the <left-shift> key intermittently until the Grub menu. From there if you go to the rescue menu option > network (that will also mount the filesystem) > drop to root prompt.... then you can do your command line fix as root.

Either that or... at the root prompt (same) rename your xorg.conf to anything else, boot with "radeon.modeset=0" as a temporary kernel boot option and boot into the grahical desktop, then use the additional drivers GUI utility to re-install your drivers. Alternately, if AMD/ATI Crysalis was instaled already, you could do it from there... 

Many options.

---

### Post by skppy1225 on 2014-12-27
Hi, MAFoElffen.
Unfortunately that doesn't seem to be working. Pressing the shift key during boot just takes the system to a black screen again. The GRUB menu appears briefly and then disappears, then I'm just presented with the black screen again.

UPDATE: I'm sorry as I misread your instructions. After going in and selecting the recovery option I am still just taken to a blank screen. I am not even given the option to choose to mount drives. It just attempts to boot and goes to a black screen.

UPDATE 2: I was able to successfully get in to the recovery console. I ran the commands suggested in the article I linked to and when I ran the commands it told me the package was not even installed. I rebooted and attempted to boot again with no luck. I'm still getting the black screen upon booting. I did not attempt your second suggestion as I am relatively new to Linux and that suggestion went way over my head.

I did notice, however, when I was rebooting that there was a slight tint to the background that I would normally see when the Ubuntu logo would appear. It would appear for several seconds and go away, just like it would if it booted normally. It looks as though the machine itself is booting but it won't take me to a GUI. My HDD indicator turns off as well.

---

### Post by MAFoElffen on 2014-12-27
If you read the bottom of the first post of my sticky (link in my signature-line), I have some brief notes on installing Ubuntu's Radeon packaged drivers. If you go to the second post, there are links instructions on temporarily editing the grub boot menu to temporarily boot your system to a low graphics mode, so you could install the drivers fro your system settings/additional drivers utility. You would use: "radeon.modeset=0" as the kernel boot option, at the end of the linux boot line. There is are also a link in that second post for detailed instructions to install AMD/ATI binary drivers, if you so choose.

---

### Post by skppy1225 on 2014-12-27
I was able to log in successfully using the low graphics mode. I now have a desktop and was able to pull up Unity. It does seem like it's a little choppy and not as fluid as it was before. I'm not sure if that's because of 14.10 or the low graphics mode. Additional Drivers is telling me that I'm already using the recommended drivers for my graphics card.

---

### Post by MAFoElffen on 2014-12-27
They may installed, but not working now (for as of now unknown reasons) so... what I would do is uninstall/purge your driver and reinstall fresh. 

```

sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get update
sudo apt-get remove --purge fglrx*
sudo apt-get install fglrx
sudo apt-get upgrade
sudo reboot

```

---

### Post by skppy1225 on 2014-12-27
All of the above commands failed when I tried to execute them in Terminal. The path in the first command doesn't exist, when I try to remove the packages it tells me 0 were removed, and when I try to install the package it tells me I have unmet dependencies. Should I attempt to go and get the dependencies and then try installing it?

---

### Post by MAFoElffen on 2014-12-27
The first would remove only if there was one present, just a good-practice to check. 

If the second failed, you would have a big problem and not be able to update any software at all!!!

If the third failed, then there were no fglrx package installed, which would there were, because jockey said there were.

If the fourth failed, then the Linux kernel header file may have been with-held in your recent release upgrade, which may have been why your graphics driver failed on that same update...

Do this:
```

KVERSION=uname -r
sudo apt-get install linux-headers-$KVERSION
 
```
Then
```

Then retry to install the driver, if there are still unmet dependencies:
[code]
sudo apt-get install  --fix-broken

```
That should install whatever broken dependencies are left over with that...

---

### Post by skppy1225 on 2014-12-27
Unfortunately it still doesn't seem to be working and it still keeps informing me that I have unmet dependencies when I try to install it. I've got the output from Terminal to help make sure I'm doing everything correctly:

```
kevin@kevinspclinux:~$ uname -r
3.16.0-28-generic
kevin@kevinspclinux:~$ sudo apt-get install linux-headers-3.16.0-28-generic
[sudo] password for kevin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.16.0-28-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  liblttng-ust-ctl2 liblttng-ust0 liburcu2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kevin@kevinspclinux:~$ sudo apt-get install fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 fglrx : Depends: fglrx-core but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
kevin@kevinspclinux:~$ sudo apt-get install --fix-broken
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  liblttng-ust-ctl2 liblttng-ust0 liburcu2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kevin@kevinspclinux:~$ sudo apt-get install fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 fglrx : Depends: fglrx-core but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by MAFoElffen on 2014-12-27
and did the last command I posted resolve those dependencies?
```

sudo apt-get install  --fix-broken

```

If not, then post the output of:
```

sudo apt-get install --simulate flgrx

```
That will do a dry run of that, without actually installing anything, but will print out any broken packages or what the unmet dependencies are... That would give us an idea of what to do next.

---

### Post by skppy1225 on 2014-12-27
No, it didn't. It didn't fix any dependencies. It returns "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded." when I run the command to fix the dependencies. This is what I get when I run sudo apt-get install --simulate fglrx:

```
kevin@kevinspclinux:~$ sudo apt-get install fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 fglrx : Depends: fglrx-core but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

---

### Post by ohanzee2 on 2014-12-28
Hi skppy1225,

Would you please consider changing the title of this thread, to include AMD Radeon cards in the title so that it will help others with the same issues?  I upgraded from 14:04 to 14:10 last week I have the same issues.  Just found your post.

---

### Post by skppy1225 on 2015-01-03
> **ohanzee2 said:**
> Hi skppy1225,

Would you please consider changing the title of this thread, to include AMD Radeon cards in the title so that it will help others with the same issues?  I upgraded from 14:04 to 14:10 last week I have the same issues.  Just found your post.

Hi ohanzee2:

I'm just replying to let you know that I managed to solve this issue. I followed the instructions in this forum post found [here]("http://ubuntuforums.org/showthread.php?t=2249841&p=13151498#post13151498"). Wine apparently does has problems with 14.10 and ATI graphics chipsets, so I also used the instructions found [here]("http://sourcedigit.com/10018-completely-uninstallremove-wine-ubuntu-14-04/") to make sure that Wine was not installed. After a reboot I was able to login to the system normally, and it's working just fine.

---

### Post by MAFoElffen on 2015-01-03
Good to see this resolved. Please return to this thread, go to the upper right corner and find the link that says "thread Tools" and mark this as "Solved."

---

