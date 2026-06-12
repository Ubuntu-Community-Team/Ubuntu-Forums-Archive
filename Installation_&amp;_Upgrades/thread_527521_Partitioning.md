---
title: "Partitioning"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by Hickler on 2007-08-16
I wanted to partition my hard drive for three OS's so I formatted my hard drive and booted from the Ubuntu live CD to reinstall Ubuntu. I ran the installer, set up the partitions and clicked install, But then at 15% it said it couldn't make the Linux-swap partition, I have tried installing Ubuntu, Fedora, and OpenSUSE all with the same result. For a while the Ubuntu live CD wouldn't boot until I formatted the hard drive with the Windows install disk. And even now it takes a really long time to boot and keeps saying things about I/O errors and all kinds of other errors until it finally boots. I have also tried using gparted but it can only delete partitions, it can't make them. Well it does make them, it just has a triangle with an exclamation point next to it and Unknown where the filesystem should be. Can anyone help or is the hard drive broken?

---

### Post by dabl on 2007-08-16
OK -- I'll give it a shot, at a fairly high level. You didn't say you already have something that you love on that hard drive, so I'm assuming you don't......

1. Download and burn yourself a GParted Live CD from [[COLOR="Magenta"]**here**[/COLOR]](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)
Boot that.  Plan to put Windows in the first partition of the first hard drive, and size that partition accordingly.  Set the "bootable" flag on that partition.

2. For ubuntu, make 3 partitions (they can be primary or extended/logical, as you wish).  The root partion "/" needs to be at least 7GB, swap can be 0.5GB, and the rest of what you want for your data is "/home".  "Apply" the partition changes, and when it is done you can exit the GParted CD.

3. If you intend to install any species of Windows, do that FIRST, and put it in the first partition on the drive.

4. Boot your Ubuntu Live or Alternate (my favorite) CD, and follow the instructions to install it.  When you get to the partitioning section, you only need to set up the mount points in accordance with #2 above, and have it format the "/" and "/home" partitions as ext3 (unless you want reiserfs like me).

5. Let Grub be installed where it naturally wants to go, which will be on the MBR of the first hard drive if Windows is already installed there.

6. If upon reboot you find yourself looking at a black screen, then it's a video card issue and you can follow this guidance to set up a VESA GUI display: [http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

HTH!  :)

---

### Post by Hickler on 2007-08-16
> **dabl said:**
> Plan to put Windows in the first partition of the first hard drive, and size that partition accordingly.

Do I have to install Windows?

---

### Post by dabl on 2007-08-16
Absolutely not!

I merely wanted to make sure not to lead you down a path that ends with "But I wanted Windows on that hard drive too!"

If you don't want Windows, then by all means plan your partitions without it.  Grub will most likely want to put the bootloader into the first partition of the hard drive, and that should be fine.  :)

---

### Post by Hickler on 2007-08-16
Okay, thanks a lot,I'm about to try that now.

---

### Post by Hickler on 2007-08-17
Sorry about being so late to reply, I didn't have any cds so I had to go buy a couple. I burned the gparted live cd but when I try to boot it on my computer it says "Loading Stage2" and sticks there. There isn't a problem with the cd because it works on another computer but I read somewhere it might be that it's having trouble with the hardware or something like that. If you know what to do it would be greatly appreciated. Thanks a lot.

---

### Post by Pumalite on 2007-08-18
Post your specs.

---

### Post by Hickler on 2007-08-18
> **Pumalite said:**
> Post your specs.
Um, where do I find them? Hehe...

---

### Post by Hickler on 2007-08-18
Wait a second, do you mean like 60GiG hard drive, 512MB RAM... stuff like that?

---

### Post by Pumalite on 2007-08-18
Mobo, graphics, RAM, drives. What system do you have installed now?

---

### Post by jacob01 on 2007-08-18
yea

---

### Post by Hickler on 2007-08-18
No system installed, I can't, I can't even partition my hard drive with gparted that comes with the Ubuntu Live CD. I don't know if you misunderstood my problem but it is not possible for me to partition/format my hard drive now, even with gparted. Would the gparted live cd be any more effective?

---

### Post by Pumalite on 2007-08-18
Definitely. Fix and partition your hard drive with Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Give '/' 10 GB minimum. 1 GB maximum for swap. The rest for /home.
We still have to sort your installation.

---

### Post by Hickler on 2007-08-18
> **Pumalite said:**
> Fix and partition your hard drive with Gparted

But Gparted can't fix or partition my hard drive... take a look at the screenshot...

---

### Post by Pumalite on 2007-08-18
Are you using Gparted, the stand alone, bootable CD? How many primary partitions do you have now in sda. I would delete all partitions and start anew if you plan a clean installation of Ubuntu only; after deleting everything, make one large primary partition; then make the extended partitions I suggested earlier.

---

### Post by Hickler on 2007-08-18
Okay, assuming that giving you the specs will help to get the live cd working, I suppose this is the graphics thing...  Mesa DRI Intel(R) 852GM/855GM 20061017 x86/MMX/SSE2, 512MB RAM, a 60GiG harddrive, And I'm not sure what MOBO means... processor?

---

### Post by Pumalite on 2007-08-18
After getting your hard drive ready, use Ubuntu Alternate CD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark the box below the green sign that says: 'Start Download'

---

### Post by Hickler on 2007-08-18
Okay, I'll get back to you in a few hours when the download finishes.

---

### Post by Hickler on 2007-08-19
The installation was going perfectly with the alternate installer when a dialog box pops up that says, "Installation step failed
An installation step failed. You can try to run the failing item again from the menu, or skip it and choose something else. The failing step is: Select and install software" Then I can continue and choose Select and install software again but as soon as I select it the error comes up again. I'm guessing "Select and install software is a fairly important step so I have no idea what to do, should I skip it? The next step is installing the GRUB bootloader...

---

### Post by Pumalite on 2007-08-19
Are you connected to the Internet? Installation requires it in your case it seems.

---

### Post by Hickler on 2007-08-19
Well, no matter what I do, I can't get it to connect, so I've got to wait till tomorrow to run out to get a cable to connect directly to the router... which is strange because there is nothing wrong with my wireless card because I was using the internet yesterday with the live CD, there's nothing wrong with the router because this computer I'm using now is connected via wireless and yet when I choose the option that allows to search for wireless networks, it says it failed. In my apartment there are at least 2 and up to 4 wireless networks active so I don't know what is wrong...

---

### Post by Pumalite on 2007-08-19
You cannot use wireless during the installation because that's something you configure AFTER you are installed. In your connection to your router make sure you set your router to give you DHCP.

---

