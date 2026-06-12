---
title: "Install to Laptop with No CD or USB Boot Option"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by YodaJones on 2007-06-02
I have a old Dell Inspiron 4000 that I want to install Ubuntu on.  My problem is this laptop has no CD drive nor does the BIOS have a boot from USB option.

I was hoping I can remove the hard drive from the laptop and install it in my external USB drive case.  Then somehow create a bootable image on the HDD from my desktop, re-install the HDD in the laptop and boot into the installation of Ubuntu.

I have been successful in connecting the HDD to the desktop via the USB case and reformating the HDD as ext3.  But when I copy the files from the ISO the laptop does not boot into the Ubuntu setup.

I hope I have explained this well enough.

Has anyone done this, or can someone show me how I can do it?

Thanks!

---

### Post by YodaJones on 2007-06-02
P.S.

I should also mention that there is no operating system on the laptops HDD so I cannot boot the laptop at all at the moment.

---

### Post by homunq on 2007-06-02
I'm in a similar position. In my case, the laptop has just about all non-essential parts broken; the square of keys e through b don't work, the USB port I resoldered on and it's falling off again,  the CD/DVD drive is broken, luckily it's so old that it has a serial keyboard/mouse port.

1. First I thought: "install" to the drive as external to my working computer, then put it back in the machine. That got me a working grub but graphics were all hosed, I was stuck in text mode, and who knows what else was all wrong. Still, it's one way (maybe there are easier ones) to get grub into the MBR of your disk, which is necessary for anything that follows.

2. I found another article here called " HOWTO: Install Edgy 6.10 from an .iso file" ([http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093)) which looked promising, But when I followed the instructions (using the alternate files from [http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/) and skipping steps 8 through 10, as recommended on page 9 of the thread) and got installation to start but eventually it still tried to look for some packages on the nonexistent CD and gave errors.

3. Next I thought: put the ISO onto another partition of the hard drive, then get grub to mount the ISO as if it were a CD and boot from there. A little googling (key search terms: "boot from a iso" and "isoemu") showed me that that was going to be pretty complicated, involving (among other things) making sure that the entire ISO was totally unfragmented on my disk.

4. So then I tried copying all the files themselves off of the CD to a hard drive partition and getting GRUB to boot into there. Found an article on softpedia called "alternative installation methods for Feisty" which told me what to put in my menu.lst. This got my machine to start booting but it hangs in squashfs - I think because my CD drive is not just absent but actually broken.

Now I'm going to bed. If nobody gives me a brilliant solution in this thread, I think I'll try 4 again but with the alternate files from step 2 (that is, those at [http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/) ). Or just do a net install, wait a few days for my slow connection and hope the power doesn't go out (did I mention the laptop internal battery charger is dead too?).

Good luck to you Yodajones, and if anyone else has suggestions we're all ears. Or if you succeed using one of the ideas from above, let me know what you did. I'm working with a DVD iso for Ubuntu 7.04.

---

### Post by YodaJones on 2007-06-02
I am still searching for some way to do this.  I found this:

[http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)

But that article presumes you can boot from a network, or at least have a functioning operating system already on the HDD.

This article is to setup a bootable USB thumb drive:

[http://www.extremetech.com/article2/0,1697,2132615,00.asp](http://www.extremetech.com/article2/0,1697,2132615,00.asp)

I was wondering if somewhere here is the answer, but most cases I have found want a working USB or CD drive.

I was hoping I could setup something like when you buy a new Dell.  The first time you turn it on it starts setting up the operating system (typically Windows).  I was hoping to be able to do something like that by pre-configuring Ubunti on the HDD attached to my desktop in a external USB case.

I found a couple "Ghost" - like tools.  But I am not sure this will work since the hardware is very different.

Still looking for a solution in case anyone can help!

---

### Post by homunq on 2007-06-02
I've decided to do the work to get isoemu working, will post my results in this thread.

---

### Post by YodaJones on 2007-06-02
I am not having any success with the thread you mentioned:

[http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093)

I am afrain that some steps whic may be clear to more experienced Ubuntu/Linux folks is over my head.  For example:  The directions mention installing grub on the new HDD, but not how that is accomplished.

I also could use better instructions on the partitioning and necessary directory creation on the target HDD.

I am not new to computers, but Have been using Windows for many years so the commands and terminology are foreign to me.

If anyone has written more clear (read easier) directions I would sure like to be pointed towards them.

Thanks!

---

### Post by ToniCipriani on 2007-06-02
Try using loadlin. Boot the machine using DOS boot disk, swap the Ubuntu disc in, and load Linux from there using loadlin.com. I tried this on an Thinkpad 240Z (The machine only supported floppy or RPL booting) and works fine.

---

### Post by YodaJones on 2007-06-03
Hi Toni,

I think you didn't read the start of this thread.  This computer cannot boot.
There is no CDROM drive.
The floppy drive does not work.
This laptops BIOS does not have a "boot from USB device" option.

I need to find a way to load the OS on the HDD with the HDD removed, re-install the HDD in the laptop and then complete the install.

---

### Post by ToniCipriani on 2007-06-03
Then that works. Use a boot floppy, copy the contents of the CD onto the hard drive, make it DOS bootable, then run loadlin.

---

### Post by Slackersrule on 2007-06-03
I'm in the same situation, although I actually have a CD Drive on a dock, but it's giving me issues.

---

### Post by YodaJones on 2007-06-03
Hi Toni,

Sorry, but I am not understanding the procedure you mean.  How can I make a boot floppy, and why would I make a boot floppy if I do not have a floppy drive?

I hope I am not frustrating you with this, I just don't understand the concept.

Thanks

---

### Post by homunq on 2007-06-05
I'm writing this from my "dead" laptop.

I realized that isoemu was not a good option - if you install from within an emulator, your installer will not see your real hardware. And if isoemu is only an emulator temporarily during the boot stage, the installer would still be looking in the wrong place later on.

So I just put the hard drive on another computer (using an external housing, but you could do it internally too). I boot the other computer using the install DVD (CD would work) and use the graphical installer to install to the disk (making sure to click "expert install" at the step 7 of 7 and put GRUB on the external disk, don't TOUCH the disk of your host system). I mount the disk (if it doesn't show up in your browser, you may have to launch system->admin->gnu partition editor and do "refresh volumes") so I can edit the /media/thediskname/boot/grub/menu.lst , deleting any OS's from the host system and changing the "root" entries of the external os's from something like /dev/sda2 to something like (hd0,1) ... that is, counting from 0, the first hard disk and second partition.

Then you put your hard disk back in your computer and boot. Chances are the video card is different and so it gives you a blue screen with an error and leaves you in text mode. Figure out what graphics card you have on the machine - either by cracking it open or by googling the make and model and "video driver" or "graphics card" or something - and then run the command

sudo dpkg-reconfigure -phigh xserver-xorg

(as explained in /etc/X11/xorg.conf ) and set the driver and resolution from the menus. Now reboot and you should be cooking with gas.

I am not sure that there's not some other hardware misconfigured by the original install, but my experience is that the usual suspects (PCMCIA, networking, sound) all function. As far as I can tell, everything but your screen is detected on boot, not configured on install. If there are some old heads here who could comment on that, it would be great.

---

### Post by homunq on 2007-06-05
If you have a fast net connection, another option would be [http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html).

---

### Post by ToniCipriani on 2007-06-15
> **YodaJones said:**
> Hi Toni,

Sorry, but I am not understanding the procedure you mean.  How can I make a boot floppy, and why would I make a boot floppy if I do not have a floppy drive?

I hope I am not frustrating you with this, I just don't understand the concept.

Thanks

I misread your post, and thought you had a CD-ROM drive, but just can't boot from it. My machine didn't have a drive, but I have an external PCMCIA drive.

Here's what I did:

1. Make a DOS floppy, with CD drivers and loadlin.exe

2. After booting up, insert the Ubuntu CD

3. Use loadlin to load the Linux image on the CD and proceed from there.

Here's what I would try with your situation

1. Create a small partition with just the CD installation files

2. Use the boot floppy I just mentioned, then loadlin from that partition, and carry on the install from there

Alternatively, I think you can use a Debian boot floppy. I heard that works, but I haven't tried.

Also, try this: [http://www.linuxquestions.org/questions/showthread.php?t=341981](http://www.linuxquestions.org/questions/showthread.php?t=341981)

---

