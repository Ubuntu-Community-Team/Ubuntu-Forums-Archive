---
title: "Dual Boot XP/Ubuntu"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by nbitting on 2008-01-29
Okay, so I am a college student who needs to keep XP on my laptop.  I want to install Ubuntu on the same laptop keeping XP.  I don't want to have to format my drive and re-install XP.  It will take to long to backup all of my files and I've heard there's a way to create new partitions to install Ubuntu without having to format.  I think it's possible using SystemRescueCD.  I found a good tutorial to help with this on LinuxDevCenter.com.[URL="http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html"]

http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html[/URL]

Is this method failsafe?  I cannot afford to lose all of my progz in XP.  It's mainly due to the fact that my college program is pro-Microsoft and we are using Visual Studio .NET and so far it doesn't work using wine.

Please check out the link above and let me know if it's a good way of doing it without chancing a crashed drive.

Thanks!

---

### Post by Pumalite on 2008-01-29
Baching up all your files before the installation of a new OS is a matter of good practice. I don't know about your link, but I can tell what I'd do. Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Resize your XP partition (right click on partition; choose resize from menu). Create new partitions in this space just created:
10 GB for '/'
/swap equal to RAM
The rest for /home.
Install Ubuntu, go Manual and use the partitions already prepared.

---

### Post by nbitting on 2008-01-30
> 
Burn to disk and boot from it. Resize your XP partition (right click on partition; choose resize from menu). Create new partitions in this space just created:
10 GB for '/'
/swap equal to RAM
The rest for /home.


so I need to create three new partitions?  '/', '/swap', and '/home'???

---

### Post by Pumalite on 2008-01-30
Those are three logical partitions within the extended partition you created initially.

---

### Post by nbitting on 2008-01-30
sorry for being such a newb here, but I'm still a little confused.

Right now I have the NFTS partition correct?

I have roughly 23GB of my 80GB HD free.  I do plan on deleting more progz and files soon.

I've defraged my C: drive a few times after deleting old files and progz.

When I run GParted, what do I do? Can you provide a step by step process on how to create the partitions needed to dual boot XP/Ubuntu without losing XP.

What partitions do I need to make, in total?

---

### Post by wjp.reg on 2008-01-30
Thought I might weigh in as the scenario sounds familiar ;-)

I setup a /boot partition as a primary partition so that I would not have to write grub to the MBR, which otherwise "could" prevent me from booting to the rescue partition of my lenovo laptop in the even of a catastrophe.  I then created extended partitions for: a fat32 shared data area, a / (root), /home and swap.

In all I have the following partitions: 

[primary]
NTFS 
rescue
boot
[extended]
fat32
/
/home
/swap

Seven partitions in total.

Cheers

---

### Post by Pumalite on 2008-01-30
You can also read this:
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by nbitting on 2008-01-30
Okay got the partition part...now, during the Ubuntu installation do I install ubuntu tu / (root) ???

---

### Post by wjp.reg on 2008-01-30
yes but;-)

you will need to specify which partition is to contain which subsystem.  Ubuntu will offer to do a default install, with the option of a custom install. You need to do a custom install so that you can label and format the linux partitions accordingly (/boot, / , /home, /swap).

Once the partitions are identified ubuntu will proceed with the actual formatting and installation.

---

### Post by Pumalite on 2008-01-30
You don't need a /boot partition. Just install Grub to MBR (by default) and you will have dual boot.

---

### Post by wjp.reg on 2008-01-30
> **Pumalite said:**
> You don't need a /boot partition. Just install Grub to MBR (by default) and you will have dual boot.

Sorry, don't agree; if you still want to be able to activate windows rescue partition you don't want MBR overwritten.

Otherwise, I do agree :-)

---

### Post by Pumalite on 2008-01-30
You can also install Grub to it's own partition and then modify boot.ini following this instructions:
You can add ubuntu to the windows boot loader:

Boot from the LiveD.

Step 1) Install Ubuntu. On the last screen click on the "advanced" button and replace (hd0) by /dev/sda3. (Here you need to replace sda3 by whatever partition Ubuntu is on)

Don't reboot immediately. Instead stay on the LiveCD.

Step 2) Mount your Windows partition:

Code:

sudo mount  -t ntfs-3g  /dev/sda2 /windows

(Here replace sda2 by whatever partition Windows is on)

Step 3) Copy the first sector of the Ubuntu partition to a file on the Windows partition:

Code:

sudo dd if=/dev/sda3 of=/windows/ubuntu.bin bs=512 count=1

(Be very careful when using "dd". Info on dd)

Step 4) Add ubuntu to the windows boot loader:

Open "boot.ini" from the Windows partition via
Code:

sudo gedit /windows/boot.ini

Add this line to the end of the file:
c:\ubuntu.bin="Ubuntu"

Save the file.

Reboot and you get should get a menu with a Windows and Ubuntu choice.
__________________

---

