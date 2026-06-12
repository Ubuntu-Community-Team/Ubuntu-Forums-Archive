---
title: "Installing on a USB HDD: 2 questions"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by xtrumanx on 2007-06-19
Hello there. I'm planning to install Ubuntu 7.04 on my USB HDD and there's a few questions I hope someone could help me with before I try it.

Where would GRUB be stored if I installed Ubuntu on my USB HDD? When I formatted the drive Ubuntu was in on a previous installation, I couldn't boot into windows. My PC would encounter an error saying GRUB not found (or something of that sort). This is the place where you would get an error message when a floppy disk was left in the drive when booting. The only solution I've found for that was to either reinstall Ubuntu to get GRUB back or to reinstall windows and the message wouldn't appear again. That made me wonder if I could actually get Ubuntu to run off another computer where I didn't install it since GRUB may not run.

Also, I was wondering what would happen if I were to not connect the USB HDD with Ubuntu installed during booting. Would I still be able to get into Windows?

i understand some computers can't boot from a USB drive, but that'll be something I'll test on the computer I'll be attempting to install on. So to summarize:

1. Would I be able to boot Ubuntu from a USB HDD from a PC where the installation didn't take place?
2. Would I be able to boot into windows if Ubuntu was installed on that computer using a USB HDD that isn't currently connected?

Thanks in advance.

---

### Post by logos34 on 2007-06-19
> Where would GRUB be stored if I installed Ubuntu on my USB HDD?

IF your computer BIOS supports booting from USB devices, you want to install grub on the MBR (Master boot record) of the external usb hard drive, NOT the internal hard disk.  That way you leave the windows bootloader intact.  You would set your BIOS hard disk boot priority to boot first from 'USB-HDD1' (or however it's designated), and second from the internal drive.  That way if your usb is unconnected, the computer will skip to the internal automatically--no need to fiddle with the bios each time.  

Do a 'manual' install.  Toward the end of the Ubuntu Feisty manual installation (using Live CD) I believe you will see a screen with 'Ready to Install' and a button with '(hd0)'.  Click on it and change to '**(hd[COLOR="Red"]1[/COLOR])**' or '**/dev/sda**' (or '/dev/sdb' if internal drive is being seen as scsi/sata device sda).  If using the text-mode alternate install cd you will be prompted to specify the location (you can even put it on a floppy).

IMPORTANT: After you finish the installation, the minute you change the BIOS to boot to the usb drive, that drive becomes 'hd0'.  You will be unable to boot ubuntu until you edit the files menu.lst and device.map in the /boot/grub directory.  Boot from the live CD again, open a terminal and type these commands in succession:

> [B]sudo mkdir /mnt/ubuntu
sudo mount -t auto /dev/sda1 /mnt/ubuntu
cd /mnt/ubuntu/boot/grub
sudo gedit menu.lst[/B]

Menu.lst will open in text editor.  Change all instances of '**(hd1,0)**'--'groot' line + ubuntu kernels in the 'Automagic' section--to '[B](hd[COLOR="Blue"]0[/COLOR],0)'.  
[/B]
Change windows entry from 'root (hd0,0)' to '**(hd[COLOR="Blue"]1[/COLOR],0)**' and add mapping:
  
> title		Windows XP
[B]root		(hd1,0)
map		(hd0) (hd1)               
map		(hd1) (hd0)[/B]
savedefault
makeactive
chainloader	+1

Edit device.map:

**sudo gedit device.map**

Switch it thus:
[B](hd0) /dev/sda
(hd1) /dev/hda[/B]

Or if internal drive is being seen as scsi/sata, it should look like this:
(hd0) /dev/[COLOR="Blue"]sdb[/COLOR]
(hd1) /dev/[COLOR="Blue"]sda[/COLOR]

Now reboot and go into BIOS and set the USB as first in hard disk boot order. The usb drive becomes hd0, and when grub queries/'calls' the bios it will be directed to the correct drive.  You should get the grub menu and be able to boot into ubuntu or windows.  

> 1. Would I be able to boot Ubuntu from a USB HDD from a PC where the installation didn't take place?

Depends on the hardware and graphics.  If they're significantly different (Intel vs. AMD platform, dual-core vs. single core cpu, ATI vs. nvidia, different ethernet controllers, etc), you may have problems getting everything to work correctly assuming you're able to boot (networking, video, sound being probably the most likely problems).  You would also have to add mount points and entries for storage devices/paritions on the other computer so you could have access to them (otherwise you'll have to manually mount them each time). 

> 2. Would I be able to boot into windows if Ubuntu was installed on that computer using a USB HDD that isn't currently connected?

As long as grub is on the usb, you'll be fine. But if grub accidently gets installed to the internal hard disk MBR (as it will by default), then no.  Grub has to access the ubuntu root partition containing the config file menu.lst with the locations of linux and windows partitions, but if grub is installed on the internal drive (in which case it overwrites the windows bootloader) and the usb drive is not connected, then grub can't find root to hand off the boot process to linux or 'chainload' the windows bootloader. 

Hope that helps you along.  USB installs used to be tricky in the past, but on newer hardware and recent Ubuntu releases they're usually fairly easy. (Note: i've read of problems with bus-powered usb drives not being recognized in time to boot.  Best to use an external power adapter.)    

check out these links:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) 
[https://help.ubuntu.com/community/BootFromUSB?highlight=%28usb%29](https://help.ubuntu.com/community/BootFromUSB?highlight=%28usb%29) (a workaround you can try in case your computer does not support booting from usb devices)

---

### Post by alejandr on 2007-06-20
> **logos34 said:**
>  But if grub accidently gets installed to the internal hard disk MBR (as it will by default), then no.  Grub has to access the ubuntu root partition containing the config file menu.lst with the locations of linux and windows partitions, but if grub is installed on the internal drive (in which case it overwrites the windows bootloader) and the usb drive is not connected, then grub can't find root to hand off the boot process to linux or 'chainload' the windows bootloader. 

Hope that helps you along.  USB installs used to be tricky in the past, but on newer hardware and recent Ubuntu releases they're usually fairly easy. 

Hello,
I have done what you say.
My grub got installed to the internal drive, so.... is there any way of moving or creating a new grub on the external drive?
(I know I will have to repair my first drive MBR in order to boot without pluging in thr external drive.)
Many thanks in advance
Ale

---

### Post by logos34 on 2007-06-20
> Hello,
I have done what you say.
My grub got installed to the internal drive, so.... is there any way of moving or creating a new grub on the external drive?
(I know I will have to repair my first drive MBR in order to boot without pluging in thr external drive.)
Many thanks in advance
Ale

Here's the standard procedure:

Open a terminal in ubuntu ad type:

> **sudo grub **  (this get you into the grub shell, '>')

**find /boot/grub/stage1**
(enter output '(hdx,y)' in next command)
[B]root (hdx,y)
setup (hdx)
quit[/B]

In your case, 'find' should return '(hd1,0)'--your internal disk with grub to which you are booting is hd0 and the external is hd1, and you probably have root on first partition/sda1, hence (hd1,0).  So 'setup (hd1)' should do it.  But you are still going to change your config files as I explained above, so that root is hd0,0.  It can seem confusing because grub is basically querying the BIOS to figure out which drive is which, and when you change the boot order the designations change to.

Then, as you already know, you can restore windows bootloader to the mbr of the internal drive by booting from winxp install cd, hitting 'R' for recovery console and doing the 'fixmbr' or 'fixboot' routine, OR by making a MS-DOS boot floppy in windows and booting to that and running 'fdisk /mbr'.

---

### Post by alejandr on 2007-06-20
Logos:
Many thanks for your quick 'n clear answer.

Ale

---

### Post by floke on 2007-06-20
Or you could have just used the alternative installer and typed '/dev/sdb1' (or whatever your extHDD is seen as) when asked 'where do you want to install grub'.

;)

---

### Post by NilsE on 2007-06-20
This is an excellent guide to installing on an external USB drive and I have done it that way a few times.  I have since just found it easier to remove the internal drive and only have the USB and CD drive active.  Takes the guesswork out of knowing where the GRUB is going and makes the drive more portable. I have accidentally forgot about the last step and doing that only once was enough for me.    

I have actually used my USB drive on other systems and have had a few burps with displays and such with very different systems which is pretty easy to fix in xorg.conf after backing it up to go back to my system later.

---

### Post by xtrumanx on 2007-06-24
> **NilsE said:**
> This is an excellent guide to installing on an external USB drive and I have done it that way a few times.  I have since just found it easier to remove the internal drive and only have the USB and CD drive active.  Takes the guesswork out of knowing where the GRUB is going and makes the drive more portable. I have accidentally forgot about the last step and doing that only once was enough for me.    

I have actually used my USB drive on other systems and have had a few burps with displays and such with very different systems which is pretty easy to fix in xorg.conf after backing it up to go back to my system later.

First of all thank you logos34 for you quick reply. I haven't had time to carry out the install as of yet, so here's to hoping all goes well. 

Quick question to NilsE though, if I were to remove the internal HDD during the install to ensure that GRUB goes to the external, what would happen if I wanted to go into windows which is located in the internal? Would I simply need to disconnect the external during boot up or would I be able to add windows into the GRUB menu (which to me would be the better option). Thanks in advance.

---

### Post by NilsE on 2007-06-24
> **xtrumanx said:**
> Quick question to NilsE though, if I were to remove the internal HDD during the install to ensure that GRUB goes to the external, what would happen if I wanted to go into windows which is located in the internal? Would I simply need to disconnect the external during boot up or would I be able to add windows into the GRUB menu (which to me would be the better option). Thanks in advance.

You have a few options.  

[COLOR="Blue"]One,[/COLOR] you can put the internal drive back in and add it to the USB grub menu but that assumes that the USB drive is the primary boot drive in the BIOS

[COLOR="Blue"]Or two[/COLOR], you can set the system to boot from the USB drive in the BIOS when it is present and when it is not it will default to the internal drive. In other words don't plug the USB drive in until after boot up from the internal drive.

[COLOR="Blue"]Or three[/COLOR], if you BIOS has an option to hit say the f12 during boot up to select a temporary boot drive like USB or CD then hit f12 when you want to boot USB and select the drive you want or let it go to boot from the internal drive without hitting f12.

[COLOR="Blue"]Or four[/COLOR], install grub on the internal drive.

---

### Post by xtrumanx on 2007-06-25
Well, everything has worked out with my installation. At first I tried installing it on my USB HDD using my PC but I've encountered and install problem I've been having since everything past 5.10 when they started issuing Live CD's only with no Install CD: the system froze. No mouse movement whatsoever.

Then I tried installing Ubuntu on my HDD using another computer and everything went fine. USB HDD has Ubuntu in it and it works on some similar computers, but alas not my own. There's apparently a graphics issue during boot up.

For reference, is there a way to see via the terminal what each drives title is: sda1,sda2,etc.

Also, is there a download available that would allow me to just install Ubuntu and not have to go through the Live CD. I can install 5.10 to this day with no problems but all the newer version just freeze up on me some point during the installation (partitioning, selecting my region. etc.) and even once as I opened firefox. Btw, I usually get Ubuntu via shipit but am ready to go the download route if install only CD's are not available that way.

---

