---
title: "nvidia &amp; xserver problem continues"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by flyingsolo on 2006-06-05
I've followed the Sticky above on xserver problems but doesn't work for me.  I'm not sure where to turn or what to try now.  Reading the forums, this is a  very common issue.  Since my nvidia card (Geforce4 MX420) was working well in Breezy whatever happened to drivers during the update process?  During configuration of xserver, I presume to select "nv" to represent nvidia but is there another appropriate choice?  How do I reload specific nvidia drivers?
Thanks for help again--I'm pretty frustrated and yet I'm hopeful it can be solved!

---

### Post by fluffington on 2006-06-06
The nVidia drivers are in the repositories, so manual installation isn't necessary.

nv is the open-source driver, which I have yet to see work. What you want is the one called "nvidia". If you don't have it, you probably need to do the following:

```
sudo apt-get install nvidia-glx
``` 
You should already have linux-restricted-modules installed, but if not, you'll have to do this too:

```
sudo apt-get install linux-restricted-modules-`uname -r`
``` 
Once everything is installed, the following should allow you to get your display working:

```
sudo dpkg-reconfigure xserver-xorg
``` 
Follow the on-screen instructions. Make sure to select the "nvidia" driver and to disable the "dri" module when prompted.

---

### Post by flyingsolo on 2006-06-06
OK!! I seem to have got beyond the nvidia driver issue but now when I boot to ubuntu, I get a 'black screen of death'--just a blank screen with nothing happening and no response to keyboard input--just frozen.  To get back here, I put disc in drive and am running from live CD.  More help please!  What to do next?

---

### Post by Jason_25 on 2006-06-07
You should examine the xorg log to see what's wrong.  It sounds like x didn't start.

---

### Post by tseliot on 2006-06-07
Boot in Recovery mode (which you can choose from the GRUB menu as soon as you turn on your computer.

You'll see ONLY the command line

Then type:
```

sudo nano -w /etc/X11/xorg.conf
```

and add the following option in your Section Device

```
Option "NvAgp" "0"
```

CTRL+X to exit (save the file)

then type:
```
reboot
```

---

### Post by flyingsolo on 2006-06-07
When I attempt reboot in recovery mode, it fails with the final few lines of reply being:
Begin: Waiting for root file system........
Done:
ALERT! /dev/mapper/Ubuntu-root does not exist.  Dropping to a shell!

and then I'm in a bash command so can't run (or don't know how to) sudo nano -w /etc/X11/xorg.conf
as suggested by tseliot above.  To me, this looks bleak!  Am I headed for a fresh install?  Could a fresh install of Dapper in a new partition likely be able to extract data files from my old Breezy partition that I haven't been able to upgrade to Dapper yet?

update--I was able to enter "recovery mode" with the third recovery in list provided by GRUB and so followed tseliot's instructions above.  However, this still just brought me to a blank screen, no input available, just as in my earlier post above.
(comment-I was content with Breezy but wanted to see the 'improvements' in Dapper but all has been frustration; most important, I don't want to lose files created over past 6 months in Breezy; if ever I solve this, I'll follow advice of others to partition data files separately from OS)

---

### Post by tseliot on 2006-06-08
[QUOTE=flyingsolo](comment-I was content with Breezy but wanted to see the 'improvements' in Dapper but all has been frustration; most important, I don't want to lose files created over past 6 months in Breezy; if ever I solve this, I'll follow advice of others to partition data files separately from OS)[/QUOTE]
If you have a livecd you can save your data to another CD or storage medium.

It is likely that Dapper's kernel doesn't support your controller, therefore your hard disk is not detected properly. If you want to see if I'm wrong (which I hope) you can try a Dapper desktop CD (it's a livecd which features also the installer) and see if it detects your partition.

---

### Post by flyingsolo on 2006-06-08
I have used the live Dapper CD and, yes, it does detect my hard drives (dual boot Dell P4, ~2.5 GHz, 512 RAM & separate XP and Ubuntu hard drives)  Live CD does get me to partitioner and both drives are visible. Can I partition free space on the Ubuntu drive, then install Dapper so now would have 'triple boot' and then copy data files from Breezy partition to Dapper?  Seems like a hard way to do an upgrade!

---

### Post by tseliot on 2006-06-08
[QUOTE=flyingsolo]I have used the live Dapper CD and, yes, it does detect my hard drives (dual boot Dell P4, ~2.5 GHz, 512 RAM & separate XP and Ubuntu hard drives)  Live CD does get me to partitioner and both drives are visible. Can I partition free space on the Ubuntu drive, then install Dapper so now would have 'triple boot' and then copy data files from Breezy partition to Dapper?  Seems like a hard way to do an upgrade![/QUOTE]
Do you want to resize your partition with Ubuntu so as to make a new partition? I have never tried that. But if it works you're safe.

BTW I use the following structure for every distro I install:
/ (root) on a separate partition
/home on another partition
and of course a SWAP partition.

---

### Post by flyingsolo on 2006-06-08
My_real_ goal was to just upgrade my existing breezy to dapper but I can't seem to get past this unresponsive black screen during boot process.  The initial nvidia driver issue is clearly not the whole problem.  Now i'm considering alternate routes to dapper but not sure if any will work given the problems i've seen already. Any other thoughts on why the black, unresponsive screen?
(thanks by the way for ongoing assistance)

---

### Post by tseliot on 2006-06-08
[QUOTE=flyingsolo]My_real_ goal was to just upgrade my existing breezy to dapper but I can't seem to get past this unresponsive black screen during boot process.  The initial nvidia driver issue is clearly not the whole problem.  Now i'm considering alternate routes to dapper but not sure if any will work given the problems i've seen already. Any other thoughts on why the black, unresponsive screen?
(thanks by the way for ongoing assistance)[/QUOTE]
Sometimes during upgrades things just go wrong and you need a fresh installation.

Perhaps I'm not competent enough to help you but many things have changed since Breezy's release: a new version of the Xserver, a new kernel and mounting system, etc.

---

