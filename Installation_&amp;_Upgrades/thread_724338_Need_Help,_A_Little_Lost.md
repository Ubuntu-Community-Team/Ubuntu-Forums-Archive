---
title: "Need Help, A Little Lost"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by aglc2005 on 2008-03-14
This may be a little confusing as to what I am trying to accomplish. I am currently running Windows XP Pro 64-bit on my desktop, I abandoned Ubuntu on there when I couldn't get my surround sound working properly (I'm still using that and only that on my laptop though). I have found some newer information that pertained to my specific sound card and would like to get this up and going. The problem that I have is my one hard drive is a little older and requires that I use the Western Digital Data Lifeguard software in order to recognize the entire drive. I have tried a lot of things to change this, but I cannot get it to work without this. One of the problems that I have come across is that if I install an OS, the software that is required to run this drive (which is written on the MBR) is lost and I have to use the Data Lifeguard to restore the MBR on that drive and get it work properly. I really want to get back to Linux, but I have found that after running the Data Lifeguard, Grub is no longer available, and it boots straight into XP. So how can I go about getting this drive to work with both XP and Ubuntu? I have a LOT of data on this drive, so it cannot be erased. It is formatted in FAT32 so the main purpose of being accessible in both XP and Ubuntu seeing how I cannot find 64-bit drivers for XP that will allow me to access the ext3 partitions.

Thanks in advance.

---

### Post by Pumalite on 2008-03-14
Boot ubuntu with Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
You might have to reinstall Grub to its own partition first:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by aglc2005 on 2008-03-14
> **Pumalite said:**
> Boot ubuntu with Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
You might have to reinstall Grub to its own partition first:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Your first link doesn't work.

And I couldn't think of the software the drive needs at the time of my first post, it's that stupid Dynamic Drive Overlay stuff.

---

### Post by Pumalite on 2008-03-14
The link is fine. I'm sorry it doesn't work for you. If you could give more details of your particular problem, maybe we could help in some other ways.

---

### Post by aglc2005 on 2008-03-20
Pretty much the Dynamic Disk Overlay has to be installed in order for the whole 250gb to show up, which loads when the computer boots. If I install the Dynamic Drive Overlay before I install Ubunut, Grub over writes this and the Dynamic Disk Overlay no longer loads. If I install the Dynamic Disk Overlay after Ubunutu, then Grub is no longer there. 

Now I know that I could use the Windows Boot Loader to launch Grub, BUT the 250gb drive has almost 200gb on it already and I am really wanting to switch back to Ubuntu without wiping out this drive.

---

### Post by Pumalite on 2008-03-21
Backup everything and try this:

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

### Post by aglc2005 on 2008-03-25
> **Pumalite said:**
> Backup everything and try this:

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

Thanks, I'll give this a try.

---

