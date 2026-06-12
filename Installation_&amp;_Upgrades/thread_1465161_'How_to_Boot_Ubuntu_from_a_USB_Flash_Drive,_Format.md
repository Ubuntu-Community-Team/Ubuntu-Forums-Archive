---
title: "'How to Boot Ubuntu from a USB Flash Drive, Formatted Ext4'"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by jmbiscarra on 2010-04-29
[FONT=Arial][SIZE=2]Does anyone  know how to boot Ubuntu from USB flash drive that is formatted ext4?

That is, making a portable ubuntu. But not merely a LiveUSB created using the 'Universal USB Installer' or 'UNetbootin' because the LiveUSBs created using these applications are formatted in FAT32 and uses a persistent partition just to save the changes and files.

If I have your attention,[/SIZE][/FONT][FONT=Arial][SIZE=2] what we  want to achieve is a portable and bootable Ubuntu in a flash drive that is  formatted in ext4.[/SIZE][/FONT]
[FONT=Arial][SIZE=2]
For your reference, you may want to read this article in  Phoronix.com: [/SIZE][/FONT][[SIZE=2]*[FONT=Arial]Testing Out Linux  File-Systems On A USB Flash Drive[/FONT]*[/SIZE]]("http://www.phoronix.com/vr.php?view=14362")[FONT=Arial][SIZE=2], published [/SIZE][/FONT][FONT=Arial][SIZE=2]on 11  November 2009.[/SIZE]

[/FONT]

---

### Post by Herman on 2010-04-29
It is simple, just install Ubuntu in the USB drive in the same way as you would in a hard drive, but install GRUB to the USB drive's MBR instead of to MBR in the first hard disk.

---

### Post by SUDOwoodo on 2010-04-29
> **Herman said:**
> It is simple, just install Ubuntu in the USB drive in the same way as you would in a hard drive, but install GRUB to the USB drive's MBR instead of to MBR in the first hard disk.
How would you go about installing grub to the USB MBR isntead of the first hard drive?

---

### Post by Herman on 2010-04-29
You just hit the 'Advanced' button when you get to step 7 of 7 in the installation process and pick the drive or partition you want from the drop-down list. 

See the illustrations in this link if you're not sure,  [COLOR=#000000][Ubuntu /  Windows Dual Boot]("http://members.iinet.net.au/%7Eherman546/p24.html").

[/COLOR]

---

### Post by jmbiscarra on 2010-04-30
Thanks to both Herman and SUDOwoodo. Now I do have a portable Ubuntu 10.04 64bit. By the way, I used VirtualBox for Windows to do so, since the computer I used has no optical drive.

---

### Post by Herman on 2010-04-30
Congratulations! I'm happy to read that you were successful. 
If you want any help to make Ubuntu run a little faster in your flash memory just ask me, there are a few adjustments we can make to improve the performance.

---

### Post by jmbiscarra on 2010-05-02
[FONT=Arial][SIZE=2]Yes, please?[/SIZE]
[/FONT]

---

### Post by Herman on 2010-05-02
:) Okay, well one thing I always do after installing Ubuntu in flash memory is to set GRUB to tell the Linux kernel at boot time to use either the noop or the deadline IO sheduler.

By default, Ubuntu uses the CFQ IO scheduler, which is ideal for hard disks because it can queue up disk reads and writes until the hard disk's read and write heads, on the end of the pivoting controller arms, will be passing through the right area of the hard disk for a quick read or write to particular places on the disc platters.

In flash memory, there's no spinning platter, no controller arms and no read and write heads to wait for, we can just request or send data to and form the disk without any queueing.

[CFQ IO scheduler]("http://en.wikipedia.org/wiki/CFQ") - wikipedia

[Noop OI Scheduler]("http://en.wikipedia.org/wiki/Noop_scheduler") - wikipedia

[Deadline OI Scheduler]("http://en.wikipedia.org/wiki/Deadline_scheduler") - wikipedia

The way to do it is to edit your /etc/default/grub file and then run update-grub.

Open your /etc/default/grub file with gedit text editor with this command, 
```
gksudo gedit /etc/default/grub
```Insert the words 'elevator=deadline' or 'elevator=noop' between the "" marks after the words 'GRUB_CMDLINE_LINUX=',
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
# GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="**[COLOR=DarkOrchid]elevator=deadline[/COLOR]**"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

To write the changes to your GRUB configuration file so the settings will be read by GRUB at boot time, run sudo update-grub or sudo grub-mkconfig -o /boot/grub/grub.cfg, (both of those two commands do the same thing),
```
sudo update-grub
```

---

### Post by Herman on 2010-05-02
Another easy thing to do is go into 'System'- Preferences - 'Appearance', and set visual effects to 'none'.
(Unless you really enjoy visual effects, which can be a lot of fun to play with if you're interested in that).

---

### Post by Herman on 2010-05-02
We can also adjust the priority Ubuntu gives to temporary storing memory items our computer's very fast RAM memory compared with the much slower Linux swap area.

```
gksudo gedit /etc/sysctl.conf
```Add the line 'vm.swappiness=10' to the end of the file,
```
vm.swappiness=10
```A swappiness value of 10 seems to work best for me, and with this setting my system has the swap area available in case it really needs it, but prefers to use the memory modules as much as possible.
Depending on your hardware and what you use your computer for, you may  find some other setting better for you. You might want feel like experimenting with different settings to see what seems best. Some web page authors recommend setting swappiness to 0, but I think that's a bit radical and it resulted in slowing down my system when I tried that. 
The default value is 60 and the maximum is 100.

[Swap FAQ]("https://help.ubuntu.com/community/SwapFaq") - Ubuntu Community Docs]

[Linux Performance tuning - vm.swappiness]("http://unixfoo.blogspot.com/2007/11/linux-performance-tuning.html") - unixfoo.blogspot.com

[What Is the Linux Kernel Parameter vm.swappiness?]("http://www.linuxvox.com/2009/10/what-is-the-linux-kernel-parameter-vm-swappiness/") - Linux Open Source Blog

---

### Post by Herman on 2010-05-02
I was just doing some further reading, and I think I have found out something I didn't know before.

It's not as difficult as I thought to create a new partition in a USB flash memory stick and have it aligned to the erase block size.
I thought we needed to resort to using fdisk commands to achieve that, which I'm a little reluctant to recommend to most people.  After re-reading the blog where I first read about that, [Aligning filesystems to an SSD’s erase block size]("http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/") , and only after trawling through tbe 100 replies at the bottom, I now think that an easier way to do the same thing might work just as well.

If we pre-partition our thumb drives with GParted before we start the Ubuntu installer, we can create a partition beginning in sector 2048 by removing the check mark from the 'Round to cylinders' checkbox, and then set the spinbox for 'Space preceding' to 1 MiB.

I'm not sure how much that will actually help, but it should help performance a little and extend the life of a flash memory drive at the same time. 
I'm sorry I didn't know there is an easy way to do that before you partitioned your drive. 
I don't think I'll bother re-installing in my own flash memory sticks, but in future installations I'll be using that method for getting the partitions aligned with flash erase block size.

---

### Post by jmbiscarra on 2010-05-03
That is too kind of you. Thank you for the effort. Just one question before I proceed: You use Jaunty 32bit, right? I found in the Ubuntu Forums' Main Support Category Section that there is a separate main category for 64bit users. That makes me wonder if it will work with Lucid 64bit, or will it only damage it. Maybe after you confirm something, I still want to get verification from that 64bit Users Section of the Forum.

---

### Post by Herman on 2010-05-03
It's exactly the same process to install 32 bit, (i386) Ubuntu as it is to install 64 bit (amd64) Ubuntu.
 
Both versions seem the same to use. 

There might still be some software, like googleearth that might not yet run in the amd64 architecture Ubuntu, or at least googearth didn't work in amd64 Ubuntu the last time I tried, in the world of software things are always advancing. 

The other thing to remember is that while the i386 Ubuntu will boot and run as well in either a 32 bit or in a 64 bit dual core computer, the amd64 Ubuntu is restricted to only dual core processors. 
For a portable USB installation, the i386 will work in more computers.

I have read that the i386 Ubuntu can utilize up to about 4 GB of RAM, and we need to use the AMD64 Ubuntu if we need to access more then 4 GB of RAM.

For me the i386 version is enough. :)

---

### Post by jmbiscarra on 2010-05-03
Alright, I'll try the codes.

One more question though: There are single, dual, triple, quad, ... , 128, ... core CPUs available. Suppose they are all capable of 64bit computing (capable of storing 64bit integers in their registers and transferring 64bit words to the memory). Considering your statement **" ... the amd64 Ubuntu is restricted to only dual core processors."**, does this mean that amd64 Ubuntu does not comply with computers that has single, triple, quad, ... , 128, ... core CPUs, even though these CPUs can do 64bit computing?

This might not be proper to ask since we are in an Installation and Upgrades Section of the Forum, but please excuse me for asking. You may ignore this question if you like. Sorry if I appear as a bother.

64bit CPUs and ALUs have been around somewhen in the 1970s, yet 64bit  computing is still not well grown. Still I want use Ubuntu amd64 because I want to contribute to the promising future of 64bit computing. It is only a bit of a sacrifice, anyway.

---

### Post by Herman on 2010-05-03
> **... the amd64 Ubuntu is restricted to only dual core processors."**,  does this mean that amd64 Ubuntu does not comply with computers that  has single, triple, quad, ... , 128, ... core CPUs, even though these  CPUs can do 64bit computing? You are very alert! 
I phrased that statement rather poorly, I didn't really mean that amd64 Ubuntu would only work in PCs with dual core processors.
What I should have said was the amd64 bit version of Ubuntu doesn't boot  if we try to boot it in a computer with a single core processor, but  the i386 versions of Ubuntu will boot in computers with either kind of  CPU.
I have one computer with a quad core processor and I had amd64 Ubuntu in it and it was working very well. I imagine amd64 Ubuntu will probably work in a computer with six core processor too.

The only reason I re-installed with i386 was because the i386 i had in it before had been booting up in 4.19 seconds, and the best I was able to get out of the amd64 Lucid Lynx was around a 6 second boot up. Now with the i386 I'm back down to a 3.03 second boot time. The boot time isn't really all that important, it was just a challenge I was having fun with, and I learned a little more about computers and operating systems trying to see how fast I could get the new Lucid Lynx to boot up.

Where I live, there are still quite a lot of i386 computers around, I'm not sure about in the rest of Australia or the rest of the world, but for me it seems as if a USB installed Ubuntu is more portable if it's the i386 version, at least at the time of writing this post. I think more new computers have dual or quad core CPUs, and those will slowly replace a lot of the older single core computers most likely. 
> 64bit CPUs and ALUs have been around somewhen in the 1970s, yet 64bit   computing is still not well grown. Still I want use Ubuntu amd64 because  I want to contribute to the promising future of 64bit computing. It is  only a bit of a sacrifice, anyway.     Oh, I see, that's a good idea and admirable ambition. You are making me think things over myself. Maybe I should give amd64 another try.

---

### Post by jmbiscarra on 2010-05-05
> **Herman said:**
> :) Okay, well one thing I always do after installing Ubuntu in flash memory is to set GRUB to tell the Linux kernel at boot time to use either the noop or the deadline IO sheduler.

By default, Ubuntu uses the CFQ IO scheduler, which is ideal for hard disks because it can queue up disk reads and writes until the hard disk's read and write heads, on the end of the pivoting controller arms, will be passing through the right area of the hard disk for a quick read or write to particular places on the disc platters.

In flash memory, there's no spinning platter, no controller arms and no read and write heads to wait for, we can just request or send data to and form the disk without any queueing.

[CFQ IO scheduler]("http://en.wikipedia.org/wiki/CFQ") - wikipedia

[Noop OI Scheduler]("http://en.wikipedia.org/wiki/Noop_scheduler") - wikipedia

[Deadline OI Scheduler]("http://en.wikipedia.org/wiki/Deadline_scheduler") - wikipedia

The way to do it is to edit your /etc/default/grub file and then run update-grub.

Open your /etc/default/grub file with gedit text editor with this command, 
```
gksudo gedit /etc/default/grub
```Insert the words 'elevator=deadline' or 'elevator=noop' between the "" marks after the words 'GRUB_CMDLINE_LINUX=',
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
# GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="**[COLOR=DarkOrchid]elevator=deadline[/COLOR]**"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```To write the changes to your GRUB configuration file so the settings will be read by GRUB at boot time, run sudo update-grub or sudo grub-mkconfig -o /boot/grub/grub.cfg, (both of those two commands do the same thing),
```
sudo update-grub
```

Hello. I put the noop scheduler instead. I felt the change. Thank you.

---

