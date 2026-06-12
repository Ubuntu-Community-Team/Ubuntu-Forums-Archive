---
title: "Help!  I was O.K. until I tried updating"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by Filkfive on 2009-11-24
Hi.  I'm a total n00b to Ubuntu, and we got ourselves in trouble.  Got a new Dell Mini 9 netbook on clearance a few months ago.  Worked fine, but all we had done was installed some music on the hard drive and fiddled around trying to familiarize ourselves with Ubuntu.  Not sure of the version (I'll get to that later)  But from reading another post I might have something called Gnome-panel, if that means anything to you.

Then saw there were 342 upgrades available, so my wife upgraded.  Resulting problems:

1.  Got a message that the hard drive was full before download was complete.  Somewhere in here she started the install, I assume without the full download, and ended up interrupting the install because it was taking too long.

2,  Somehow while trying to fix it, she lost most of the applications (I think that's what they are called at least.  The list you get to using the Ubuntu logo button.).  She had deleted her music to free up space, but I'm wondering if she deleted something else by accident.  Now when you click on the little Ubuntu logo the only options you have are Places, System, and Quit.  She says there used to be a lot more.

3. When I click on the Ubuntu logo, then System, then About Ubuntu, which I assume should give me the version number, nothing happens at all.

4.  When you try to complete the upgrade, it gives you an error message telling you to run "dp.kg -- configure - a" on the command line, but I can't get the command line to come up.  I found mention of a keypad shortcut to get to the command line (ctrl-alt-t maybe?), but that didn't work either.  I don't know that we even want to resume the installation without the full download anyway.

If we could just get back to the way it was before that would be fine.  But looking at other post here, almost all the answers go way over my noobie head.

---

### Post by lindsay7 on 2009-11-24
Try pressing alt plus the f2 key at the same time and enter the code you want.

You can also try entering the code    update-manager -d  after you press alt + F2.  This should upgrade and update your system.

---

### Post by llamabr on 2009-11-24
How did you install ubuntu?  or did it come installed?  If you installed it, you can just reinstall again to get back where you started.

To type the code, press ctrl-alt-f2, then type:

```
sudo dpkg --configure -a
```

to continue the update.  Then, you might do a:

```
sudo apt-get clean
```

The problem with the netbooks is that they have very small hard disks, and if you put a bunch of music on there, you might not have enough disk.  Try posting the output of:

```
df -h
```

---

### Post by ugm6hr on 2009-11-24
Unfortunately, the Dell version of Ubuntu for the Mini 9 was less than ideal.

You may be able to salvage it, but I think it may be easier to just re-install.

The problem is that the HD is often too small (if you have the 4GB version) to cope with the operating system, let alone additional files.

The only way to resolve this is to download the updates, copy them to an external HD / USB and then install from there.

You will probably be better off just installing a newer version.  I use 9.04, but I gather 9.10 works pretty well on the Mini 9 too.

PS: I have an 8GB Mini 9 with Ubuntu 9.04 installed.
PPS: There is a Dell-specific area on this forum.

---

### Post by Filkfive on 2009-11-24
Thanks for the advice everyone.  As ugm6hr surmised Ubunto came pre-intstalled and it only has a 4GB hard drive.  (Though it wasn't that may years ago the a 4 GB hard drive would have been inconceivably large even on a desktop,  but I'm showing my age)

A re-install is really what sounds like my best option.  I tried to do it earlier today, by downloading Ubuntu Netbook Remix onto a flash drive.  Was that a poor choice?  I thought that since it said it was for a netbook it might be right.  I also saw a reference saying it worked well on a Dell Mini 9.

Anyway, I tried to install it as directed here:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I was able to figure out how to change the bios so it looked at the flash drive for the operating system first on booting.  But it didn't work.  When I turned it on it thought for a while and then said  "No boot filename received"  "PXE-M0F: Exiting PXE Rom".

I assume that means the flash drive wasn't bootable.  I don't know what I did wrong there.  Any suggestions on what I'm doing wrong, or a better way to go about installing a new operating system?  The only file on the flash drive is Ubuntu-9.10-netbook-remix-i386.  It's an ISO image file of 697,156 KB in size.__

---

### Post by ugm6hr on 2009-11-25
To install Ubuntu NBR 9.10 (which is a good choice), you need to create a bootable USB drive.  Copying the iso file on to it won't work.

Do you have access to any other computers - Windows or Ubuntu?  If so, which?

You will see this: [https://help.ubuntu.com/community/Installation/FromUSBStick#Copy%20files%20to%20USB%20stick](https://help.ubuntu.com/community/Installation/FromUSBStick#Copy%20files%20to%20USB%20stick) - it explains how to use usb-creator (on Ubuntu) or Unetbootin (on Windows) to do this.

For further detail on sorting issues / wifi etc: [http://www.ubuntumini.com/2009/11/user-guides-for-ubuntu-910-karmic-koala.html](http://www.ubuntumini.com/2009/11/user-guides-for-ubuntu-910-karmic-koala.html)

Hope that helps.

When you do install, I would recommend using the "manual" setup to ensure the entire HD is used for Ubuntu, with no "swap" partition, since that will only shrink available size, and is unnecessary with 1GB RAM (and probably 512MB RAM too).

Once you have reinstalled, ask again how to update without over-filling your HD.

---

### Post by Filkfive on 2009-11-25
Thanks very much ugm6hr!  I think I made some real progress.:D  I was able to get NBR installed using Unetbootin on another computer as you suggested.  Then followed the instructions from the second link you provided to install the the [COLOR=#000099]bcmwl-kernel-source[/COLOR] package.  I gather that is supposed to repair a WiFi issue, but I am unable to test that yet as I don't have WiFi here.

I did screw up on installing NBR manually.  I didn't hit tab fast enough and it went to automatic instead.  Should I reinstall again and be sure to do it manually?

I now have only 432mb of free space on my 4 GB hard drive with only the operating system on the hard drive.  Does that sound right?  Does the new NBR installation overwrite the old operating system installation, or are they both on there taking up space at the moment?

Also, you said to ask how to update without over-filling my hard drive.

Thanks again much for you help.  You've already gotten me out of the worst of my problems.

---

### Post by Filkfive on 2009-11-25
O.K., not so good after all.  When I turned the netbook off, and then turned it back on, it loaded the original operating system that came with it, not the Ubuntu Netbook Remixthat I just installed off the flash drive.  (At least that's what I thought I did)

Also another thing I forgot to mention.  When I installed UNR I got a message about a hard drive error, something about the hard drive operating outside normal parameters.

---

### Post by ugm6hr on 2009-11-26
I suspect when you thought you'd installed NBR, that you had in fact just run it in "Live" mode.

From there you still have to install it - there should be an icon in the menu somewhere to do that (I am still using 9.04, so don't know where that icon is).

Once you have selected the Install process, from within the "Live" environment, you will get the option for Guided or Manual partitioning: choose manual.

At this stage, you need to manually remove all partitions except the very small one at the beginning of the SSD (which is some kind of Dell testing suite or something), and create a single ext4 partition as "Primary" - labelled sda2 (sda1 = small testing software at start).

sda2 : ext4 : label = "/" : format = yes
sda1 : do not use (i.e. no label)

The other defaults should be fine.

I will talk you through updating once successfully installed.

---

### Post by Filkfive on 2009-11-26
Everything seemed to work fine, though I only had time to do the installation before going out to my Thanksgiving festivities.  I didn't get to test it or do the sorting/wifi issues yet.  For anyone else using this thread as a reference, the link to clink on to install was under "Favorites", the very first heading.  (It's also under "System" the very last heading)

Thanks for your patience with me ugm6hr.  Sorry you had to dumb things down so much for me.  Happy Thanksgiving to you and all.

---

### Post by Sealbhach on 2009-11-26
> **Filkfive said:**
> Everything seemed to work fine, though I only had time to do the installation before going out to my Thanksgiving festivities.  I didn't get to test it or do the sorting/wifi issues yet.  For anyone else using this thread as a reference, the link to clink on to install was under "Favorites", the very first heading.  (It's also under "System" the very last heading)

Thanks for your patience with me ugm6hr.  Sorry you had to dumb things down so much for me.  Happy Thanksgiving to you and all.

So you got 9.10 installed OK? Here's the wireless fix for Karmic on the Mini 9: [http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

.

---

### Post by Filkfive on 2009-11-26
The [COLOR=#000099]bcmwl-kernel-source[/COLOR] package?  I did that already following ugm6hr's instructions.  Thanks for the help anyway Sealbhach.  I appreciate everyone being willing to help me out.

---

### Post by ugm6hr on 2009-11-27
Before updating, post the output from:
```
df -h
```

This will tell us how much HD sapace you have left.

---

### Post by Filkfive on 2009-11-28
Alt F2 brings up a Run Application box.  If I type "df -h"  (With a space between the F and the -), hit "Run", the box closes, nothing else happens.

So I tried with with no space between the f and the -  (I typed "df-h") and it says...


* "Could not open location 'file:///home/kathy/df-h'  Error stating file '/home/kathy/df-h': No such file or directory  *

But, if this helps I can go into the file browser and if I click on one of the Places at the bottom of the page it says there is 1.3 GB of free space.  The Update Manager says there are 131 update selected totaling 107.5mb, so it sounds like I easily have enough space to download and install them all at once, right?

---

### Post by ugm6hr on 2009-11-28
To get df -h to work, you have to run it in "Terminal" - there should be a menu entry for Terminal, else Alt+F2 has a tick-box for "run in Terminal"

In any case, 1.3GB is plenty - similar to 9.04, the NBR is much smaller than the Dell 8.04 version.

So yes, you *should* be OK to run updates.

You can update from Terminal too:
```
sudo apt-get update
sudo apt-get -d upgrade
sudo apt-get upgrade
```

Those commands in English:
1. Check what updates I need
2. Download the updates I need to /var/cache/apt/archives
3. (Download &) Install the updates I need

The rationale for separating step 2 & 3 is that you can recheck HD status after downloading, and potentially choose to install the updates 1 at a time, or move the files to an external USB, and install from there.

But with 1.3GB spare, you should be fine just to click Update when it prompts you.  Remember the download size is not the same as the installed size though.

After updating, I would recommend you keep a backup of the files in /var/cache/apt/archives/ (except the lock file), and then delete those files with:
```
sudo apt-get clean
```

Repeat this process after each significant update to ensure the HD doesn't fill with update files.

---

### Post by Filkfive on 2009-11-28
Thank you ugm6hr.  Everything seems to have gone well with your latest instructions as far as I can tell, so hopefully I won't have to bother you anymore.

BTW, if anyone is reading this at a later date for reference and wants to know where the terminal is in Ubuntu Netbook Remix, it is under Accessories.

Thank you again ugm6hr.  You been very patient with me and my ignorance.

---

### Post by ugm6hr on 2009-11-29
No problem.  Glad you got yourself sorted.

It is unfortunate that Dell shipped their 4GB Mini with an OS that filled the entire HD, and then crashed following the release of multiple updates.

I hope you find 9.10 much more productive.

---

