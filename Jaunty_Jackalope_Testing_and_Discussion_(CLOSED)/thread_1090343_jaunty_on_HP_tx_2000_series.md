---
title: "jaunty on HP tx 2000 series"
date: 2009-03-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by janmyszkier on 2009-03-08
Hello has anyone installed sound and touchscreen on jaunty?

even if i know sound is still a problem in jaunty, i remember i needed to add a line in /etc/modprobe.d/alsa-base regerding my card being hda-intel. however it still doesn't work.

the second problem is about touchscreen. i remember it was installed in alpha 4. it wasn't calibrated back then but it worked.

recently i decided to reinstall system to pure alpha 5. and the touchscenn doesn't work at all. regression? 

I'm aware it can't be done through the xorg.conf even i read in some documentation that "jaunty will propably still use it" or something. seemd fdi is now in the game but still... no response.

Hence the question: was anyone able to run these two devices on jaunty?

---

### Post by Favux on 2009-03-08
Hi janmyszkier,

I think there are suppose to be some new configuration gui's.  From the Jaunty UDS here are the notes on both gui's; Xorg.conf Options Editor and the Graphical Configuration Tool for Wacom Tablets & TabletPCs:

[https://wiki.ubuntu.com/UDSJaunty/Report/Desktop]("https://wiki.ubuntu.com/UDSJaunty/Report/Desktop")

They're down in there a ways.  I'd be interested if they are present and work.  Also what version of linuxwacom driver is included.  I think it's suppose to be 0.8.2.

---

### Post by janmyszkier on 2009-03-10
yes , i found this page too, I'm hoping it will be available in jaunty final. however there is no trace of alpha/beta build or am i wrong?

even if there is a gui, wacomcpl isn't able to find my devices now (not even the stylus). I'm amazed it worked on alpha 4 by default but not in alpha 5. Well, nothing for me except checking the next release ;)

Keeping thumbs up for people working on the GUI though.

---

### Post by Favux on 2009-03-10
Hi janmyszkier.

No I haven't seen any betas.  Just Loic2's mockup of the wacom gui and mailing-list discussions of Alberto Milone implementing it.  And also mention of gnome's Xorg configuration gui.

---

### Post by vishalrao on 2009-03-11
My tablet doesnt work (but its the older tx1000 series not the new tx2000), see [lpbug]317127[/lpbug]

edit: some good activity going on! almost there with the tx1000 touchscreen!

---

### Post by ir0nman on 2009-03-24
I'd like to know this too. I also have the tx2000 and I'm wondering if anyone has had success with Jaunty yet. It's getting close to beta time when I usually upgrade, but I'd sure like to know how things are going before I jump.

Thanks,
-Rick

---

### Post by Favux on 2009-03-24
Hi ir0nman,

Just helped a X61t user set up the other day.  Seemed straight forward.  He said the default linuxwacom was 0.8.1-6.

---

### Post by Favux on 2009-04-07
Hi Everyone,

Rather than link you to the other posts about this I thought I'd summarize a little.

Wacom tablet and tablet pc users, serial or usb, running Jaunty.  You are invited to test New Modified LinuxWacom Drivers for Jaunty.

These drivers will hopefully offer the hotplug support through HAL/.fdi that Intrepid and Jaunty were meant to have.  If you are **interested in testing** Timo Aaltonen has pre-packaged the modified linuxwacom xserver-xorg-input-wacom 0.8.2-2 and wacom-tools 0.8.2-2 for you on his ppa (3-24-09).   Note this includes a modified 10-wacom.fdi file:

NA  [https://launchpad.net/~tjaalton/+archive/ppa](https://launchpad.net/~tjaalton/+archive/ppa)

Update(4-9-09):  Above link is now invalid.  Timo's ppa has been accepted already. It's in the repositories. Either check Synaptics in Jaunty or go to: [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and select Jaunty. Then X Window System software. It's listed as xserver-xorg-input-wacom. I don't see wacom-tools so either with the package or somewhere else. If you spot it please let me know.

NA  Then click on:  wacom-tools - 1:08.2.2-OubuntuO.2

[NA  You will see the i386 and amd64 debs.]  You use them to upgrade from the 0.8.1-6 versions that come with Jaunty.  Since the patches support hotplugging through HAL you should not need to configure your xorg.conf.  I'm assuming you can calibrate through wacomcpl.  You will have to re-enable each tool with Gimp, etc.  This should work for hotplugging usb Wacom tablets and usb tablet pc's.  And the updates should also provide HAL/.fdi support  for serial tablets and serial tablet pc's.

**If you are testing** it is important for you to give feed back to this lauchpad site **[FFe] Please allow a new version of wacom-tools** posted (4-4-09):
 
[https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/355340](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/355340)

If enough positive feedback is received there is a chance they will update the Jaunty repository to the patched 0.8.2-2.  This could get Wacom on Ubuntu close to where we want it.

The announcement comes from Timo Aaltonen by way of Loïc2.  This post by Timo Aaltonen on the ubutu-devel mailing list will fill in some background.

[https://lists.ubuntu.com/archives/ubuntu-devel/2009-March/027865.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-March/027865.html)

---

### Post by theCroc on 2009-04-09
The repo is empty. Have they moved everything?

---

### Post by Favux on 2009-04-09
Hi theCroc,

I don't know.  Hopefully he just has it down temporarily while he modifies something.

---

### Post by Favux on 2009-04-09
Hi Everyone and theCroc,

It looks like Timo's ppa has been accepted already.  It's in the repositories.  Go to:  [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and pick Jaunty.  Then X Window System software.  And it's under xserver-xorg-input-wacom.  I don't see wacom-tools so either its packaged in or somewhere else.  If you spot it let me know.

---

### Post by Favux on 2009-04-11
Hi everyone,

Looks like there may be a few glitches in the new method.  We'll have to see how it shakes out after they work on it some more.

But you can still get Wacom working by compiling the new development version of linuxwacom 0.8.3-2 and using xorg.conf.  Just be sure libhal1-dev is not installed when you compile otherwise you will get unwanted HAL features.


Compiling HOW TO:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

Please read:  [http://ubuntuforums.org/showthread.php?t=1122952](http://ubuntuforums.org/showthread.php?t=1122952)

And also:  [http://ubuntuforums.org/showthread.php?t=1038949&page=8](http://ubuntuforums.org/showthread.php?t=1038949&page=8)  starting with post #75.

---

