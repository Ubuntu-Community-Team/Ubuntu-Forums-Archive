---
title: "Unable to Install Ubuntu"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by mdietz on 2007-08-28
I've tried installing Ubuntu on my new laptop without any success.  I know the CD is fine since I used it on my desktop without any problems.  The laptop is a HP tx1215nr with 1GB of RAM, AMD TL-56 1.8ghz and a GeForce Go 6150 running on Vista.

Every time I start the install, the disc works fine and says its loading the necessary components.  However, the screen then goes and makes odd colors.  From there, I am only able to force the computer to shutdown and try again.  I've also tried installing in text mode.

I did notice an error which reads: "firmware_helper[6292]: main: error loading 'lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:03:00.0' with driver '[unknown]'.

Any help is welcomed, as my knowledge has been exhausted.

---

### Post by merlinus on 2007-08-28
How did you partition your drive?  Also, your video card will cause problems, but it seems you used the Alternate Install cd with no luck either.

-merlin

---

### Post by mdietz on 2007-08-28
I hadn't partitioned the drive.  When I installed Ubuntu on the desktop, I used the partition function during the install.  This time around, I wasn't even able to get to that point.

---

### Post by merlinus on 2007-08-28
Before attempting ubuntu install, delete temp and other unneeded files, backup data, set virtual paging to zero (set it back after install), and defrag several times.

With vista, use its disk manager to resize its partition.

-merlin

---

### Post by mdietz on 2007-08-29
Same result after setting the virtual memory to 0 and freeing up 20GB.  There's some other errors that go by too quickly for me to read, though I saw something about "No such file found" for manufacturer, BIOS and product.

---

### Post by merlinus on 2007-08-29
Another option after shrinking the vista partition is to use gparted live cd to set up the ones for ubuntu.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Then you can select them in the partitioning menu from the install cd.

-merlin

---

### Post by likemindead on 2007-09-01
I'm having a similar but more crippling problem that seems to revolve around bcm43xx_microcode5.fw not loading.

I've tried to boot from my Feisty Live CD and I've also tried a Linux Mint 3.0 Live CD. Both hang trying to load bcm43xx_microcode5.fw.

My computer freezes up if I try to update via the manager or terminal, it freezes when I try to run ndiswrapper, and it freezes up randomly or doesn't boot at all when it feels like it.

Please help?! Thanks in advance.... ... .. .

---

### Post by likemindead on 2007-09-01
[SOLVED] (Thanks to bmartin.)

> **bmartin said:**
> If you were using the offline installer, the program wouldn't be looking for build-essential. You need an internet connection to retrieve the build-essentail package when using the online installer.

You can remove the firmware, for one thing. This will disable your wireless connection.
```
sudo modprobe -r bcm43xx
for fw in `find -P /lib/firmware/ -name 'bcm43xx_*.fw'`; do sudo rm $fw; done
```
Then I'd use the offline installer ([here]("http://blakecmartin.googlepages.com/bcm43xx-gtk-installer-0.2.2.tar.gz"), from the first post). You need to have a compatible kernel. If it says your kernel is incompatible, post the output of **uname -r** and I'll make a tarball so that you can install ndiswrapper without downloading build-essential.

---

### Post by unclesamslair on 2007-09-01
I have a similar problem with my desktop. It's a Dell Dimension 2300 with 38gb hard drive 256mb ram 1.8ghz processor and Windows XP. I've already backed up all my files. I downloaded the iso files multiple times from different sources (even torrents) specifically concentrating on getting the ubuntu-6.06.1-desktop-i368.iso version. I check the Md5sum with winMd5sum and burn the iso with infrarecorder onto a Verbatim CD-RW (4x). I then reboot and hit F12 and choose to boot from the "ide cd-rom device" it I then check for CD integrity and although it takes a while it comes out fine. I reboot and then choose to start ubuntu or install it and 15 minutes later the virtual cd os is up. I then click to install and 10-12 minutes later a blank screen pops up. A minute later that blank screen asks me what language I speak. I say, why English of course. 5-7 minutes later the map of the world shows up and ask me where I live, I try to use the drop down menu but it doesn't respond. 20 minutes later nothing responds, 10 minutes later my mouse doesn't even move, 30 seconds later I give up and reboot. I then try the same thing with the alternate version with more luck I choose text installation, wipe my unpartitioned hard drive and install ubuntu. After installing base system stuff it's start the "select and install" software thing. right at sixty percent when it's installing something called "xserver.x" or something like that it all disappears and all I'm left with two little white blocks on the screen and no OS. After booting up Windows I try downloading the Live CD and burning it onto a CD-R (52x) hoping it's increased speed would solve any freezing problems. No such luck. I am not going to give up on this, so please help, I'm desperate!

---

### Post by merlinus on 2007-09-01
You do not have enough RAM to install from the live cd.  Did you checksum your Alternate .iso download?

[http://www.psychocats.net/ubuntu/iso#checksum](http://www.psychocats.net/ubuntu/iso#checksum)

Also, burn at no more than 4x, and be sure to check the cd for errors at the startup menu.

Also, it is possible that your cd drive has defects.  You might check the Alternate on another machine or drive.

-merlin

---

### Post by unclesamslair on 2007-09-01
> **merlinus said:**
> You do not have enough RAM to install from the live cd.  Did you checksum your Alternate .iso download?

[http://www.psychocats.net/ubuntu/iso#checksum](http://www.psychocats.net/ubuntu/iso#checksum)

Also, burn at no more than 4x, and be sure to check the cd for errors at the startup menu.

Also, it is possible that your cd drive has defects.  You might check the Alternate on another machine or drive.

-merlin

I thought 256mb ram was the minimum requirement, plus, even if I don't have enough ram for the live cd, what about the alternate. Not trying to be rude, just a little frustrated.

PS: I checksummed everything and checked CD integrity (I have two cd drives and I tried them both one player another burner)

---

### Post by merlinus on 2007-09-01
256M RAM  is sufficient for the Alternate.

You can run the live cd with 256M, but since the entire os is running in RAM you cannot then also install it.

The Alternate cd is text-based, but quite straightforward.  It goes directly into the installation from the menu, and there is no option to try out the os first.

-merlin

---

### Post by paschar on 2007-09-01
i just started using Ubuntu today, the trick to it is your pop up blocker 
in your tool bar click tools then pop up blocker settings, then you can either allow temporay pop ups or  always allow pop up, if this wont do the trick then your system has issues. best of luck Paschar

---

