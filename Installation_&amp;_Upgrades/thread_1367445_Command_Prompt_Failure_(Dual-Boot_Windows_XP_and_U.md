---
title: "Command Prompt Failure (Dual-Boot Windows XP and Ubuntu)"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by ProginoskesLives on 2009-12-29
I have an EEEPC that came with Windows XP on it, and I've been trying to install Ubuntu and set them up to dual-boot.  I'm actually a Mac person, so that may be why I'm having so much trouble.

I followed the instructions on this website ([http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows)) to install Ubuntu 8.10 on my hda2 partition.  However, after both systems are installed, it told me to boot into the command prompt and do the following:

"mkdir /mnt/share
mount -t msdos /dev/hda2 /mnt/share"

It made the directory just fine, but when I typed the line with "mount" in it, the command prompt threw up at me and said that "mount" is not internally or externally recognized.  I checked other websites, and they gave me the same code instructions.

Where did my "mount" command go?  Is there an easier way to set up Windows XP and Linux to dual-boot?

(also, I'm sorry if this is in the wrong section; I wasn't sure where to put it.)

---

### Post by ajgreeny on 2009-12-29
I'm not completely sure what you are trying to do but it looks as if you are trying to set up a mount point for the windows partition on the ubuntu filesystem.  I also have to say that I don't agree with some of the commants made in the guide you referred to.  Personally, I would always put grub on the MBR, as it makes life so much easier than messing about with the windows bootloader, and will give you the choice of which OS to boot with no further action needed on your part.

The first part, ie making the folder went OK, as you say, though it may have been better to put it in /media, rather than /mnt, but for the second part of the command, you will certainly need "sudo" in front of the command, as it can only be done as root, and depending on the filesystem of windows, you may also need to add a line to the /etc/fstab file in order to mount the partition at boot time.  Possible lines needed are as follows:-

For fat32
/dev/sda2 /mnt/share vfat defaults,user,dmask=027,fmask=137 0 0
For ntfs 
/dev/sda2 /mnt/share ntfs nls=utf8,umask=0222 0 0
or
/dev/sda2 /mnt/share ntfs-3g defaults,locale=en_US.utf8 0 0

I hope that has not confised you even more than you perhaps are feeling already, but I think you have been slightly led astray by a less than standard dual boot setup procedure.

Come back again if you need with more questions, and see if anyone else answers, as they may just disagree with me and find a way to help you more.

---

### Post by ProginoskesLives on 2009-12-30
> **ajgreeny said:**
> The first part, ie making the folder went OK, as you say, though it may have been better to put it in /media, rather than /mnt, but for the second part of the command, you will certainly need "sudo" in front of the command, as it can only be done as root, and depending on the filesystem of windows, you may also need to add a line to the /etc/fstab file in order to mount the partition at boot time.

Um, I may have forgotten to say that I can't boot into Ubuntu at all; I'm stuck with Windows and its command prompt.  I *wish*
I could boot into Ubuntu because then I'd have the terminal and I'd be fine.  That's what my main problem is.  I can't figure out how to make the system boot from hda2 (where Ubuntu is); from there I'd be able to do the commands you specified.

---

### Post by ajgreeny on 2009-12-30
Try changing the first boot device in the BIOS by hitting whichever key you need to when booting, either to just change the boot device on newer machines or entering the BIOS setup in older ones.  If you only have one drive, not partition, but actual drive, then I am completely out of my depth, I'm afraid.

---

### Post by ProginoskesLives on 2009-12-30
I went poking around in Windows and discovered the Boot.ini file, but let's back up and start from the beginning.

After much sweat and tears, I figured out how to do make a mount point and did so.  (I know you said I should disregard the webpage I was using, but I didn't know what else to do.)  I *think* I correctly made the ubuntu.bin file he mentioned, and I copied it to my C: drive.  Then I went and edited the boot.ini file so it looks like this:

> [boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(2)\ubuntu.bin="Ubuntu Linux" /noexecute=optin /fastdetect

Unfortunately, while the system displays options to start Windows or Ubuntu at startup, it won't actually boot into Ubuntu; it says I'm missing some Windows file.  So I'm not sure what I actually did to the system...

---

### Post by presence1960 on 2009-12-30
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by ajgreeny on 2009-12-30
I may have made a mistake in not realising you have used wubi to install ubuntu, but I'm not at all sure about that.

Anyway the last line of your boot.ini file quoted in your post says:-
> multi(0)disk(0)rdisk(0)partition(2)\ubuntu.bin="**Ub  untu** Linux" /noexecute=optin /fastdetectand I do not think the space should exist there in "Ub untu" as you show it, though whether that would stop it booting, I'm not sure.

If that does not help, I am out of suggestions, I'm afraid, as I have always used the MBR for grub and never had a problem so far.

---

### Post by ProginoskesLives on 2009-12-30
I finally gave up and reinstalled Ubuntu from the CD, making sure to install GRUB on hd0.  Now both of my systems are working great.  Sorry I gave up, I'm sure there could be some interesting solutions to this, but I wanted my computer to work.  :P  Thanks to everyone for the suggestions!

---

### Post by presence1960 on 2009-12-30
> **ProginoskesLives said:**
> I finally gave up and reinstalled Ubuntu from the CD, making sure to install GRUB on hd0.  Now both of my systems are working great.  Sorry I gave up, I'm sure there could be some interesting solutions to this, but I wanted my computer to work.  :P  Thanks to everyone for the suggestions!

Glad you got it working. If you want to learn about your setup & boot process download the boot info script and run the command. There will be a wealth of info about your setup & boot process in the RESULTS.txt file generated by the script.

---

