---
title: "Boots only with USB Stick"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by daisyflower on 2012-05-15
I installed the .iso on the main page of the Lubuntu site.  I installed it on a netbook.  The other installs I saw linked in a different area had .deb as an extension and I was trying to install Lubuntu alongside Windows.  So, first question is, is this the right .iso for a netbook?  I have an Acer One if that helps.  I assume the answer would be the same for new netbooks.  It installed and asked to reboot.  So, I rebooted, but it wouldn't load.  I had to remove the battery and put it back in.  Then when it loaded, Windows came up.  The usual grub menu was not seen to select.I then put the USB back in and tried to reinstall.  This didn't work.  It loaded right up to Lubuntu.  This is actually not a bad thing, because if I want to use Windows I don't have to select it like usual.  However, if I want to get that grub menu to load first before launching Windows or Lubuntu, how do I do this?  I see no options to install now.

---

### Post by wilee-nilee on 2012-05-15
Sounds like grub was put on the thumbs mbr rather then the HD's.

So in the Lubuntu install open a terminal and run this command.

```
sudo fdisk -lu
```This will list the partitions, but your looking for the first three letters, no numbers, so like sda or sdb...etc

now run this command and sub your last letter for the X in sdX you see in the command.

```
sudo grub-install /dev/sdX
```Then

```
sudo update-grub
```Grub should be installed and show at boot with all the OS's now.

I am assuming here that you installed originally from the booted thumb, not from windows, if from windows discard this and let us know the install manner.

---

### Post by daisyflower on 2012-05-15
Thank you for the help.  This is what I get with the first command:


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00042119

   Device Boot      Start         End      Blocks   Id  System
[B]/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848    81922047    40857600    7  HPFS/NTFS/exFAT
/dev/sda3        81922048   266242047    92160000    7  HPFS/NTFS/exFAT
/dev/sda4       266244094   488396799   111076353    f  W95 Ext'd (LBA)[/B]
Partition 4 does not start on physical sector boundary.
[B]/dev/sda5       266244096   449376789    91566347    7  HPFS/NTFS/exFAT
/dev/sda6       449378304   484229119    17425408   83  Linux
/dev/sda7       484231168   488396799     2082816   82  Linux swap / Solaris[/B]

Disk /dev/sdb: 8010 MB, 8010194944 bytes
32 heads, 63 sectors/track, 7760 cylinders, total 15644912 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6895593a


So, it looks like it is on "sda6" and "sda7".

Is this correct?  I am not sure what to do next.

> now run this command and sub your last letter for the X in sdX you see in the command.

What do you mean by "sub my last letter"?  I see 6 and 7, so do I do this command for both?

---

### Post by wilee-nilee on 2012-05-15
Sorry it can be confusing we just want to load the master boot record also called the mbr, this is the area before the partitions, the partitions have sda5 and sda6 starting with sda1. So run these commands to load the mbr. :)

sudo grub-install /dev/sda

then 

sudo update-grub

---

### Post by daisyflower on 2012-05-15
I am sorry, I can't follow what you are saying.  So, I tried to reinstall Lubuntu two more times.  Each time it says it has finished and needs to restart, but when it shuts down, nothing happens.  I have to remove the battery from the netbook and try to boot it up again.  After a third install, it now loads the grub on the screen.  Unfortunately, it still doesn't shut down properly.  Since the USB stick was removed, it's no longer on the list in the bios settings. However, USB HDD is.  I moved that down the list, and now the netbook seems to be doing what it is supposed to do loading.  Whether or not that would have solved the problem the first time, I am not sure.  I am posting this part so if anyone else experiences the same thing, they should check the bios settings to make sure USB HDD isn't second on the list, above the regular HDD.  It seems like that is what caused the problem after installation finished.  This part involving the grub issues is resolved, but I will make a new thread about the rebooting.  It still freezes.

---

### Post by wilee-nilee on 2012-05-15
So I think we should look at the whole operating system with a script, this can be run from a ubuntu live cd or an ubuntu install. Run these commands in a ubuntu terminal then look in the ubuntu home for a results.txt, then open it and copy and paste all the text to your thread in a reply. Do this with everything plugged in.

Also confirm if you are just using a usb hard drive, and if you have a usb flash drive as well.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
``` ```
chmod a+x bootinfoscript
``````
sudo bash bootinfoscript
```So as well if we keep working together here, only do what I suggest, nothing else, and if you don't understand tell me.

Having a user doing extra stuff is really difficult to work with, or not explaining they don't understand with specificities.

---

### Post by daisyflower on 2012-05-15
Is this in regard to the grub list or the reboot issue?  The grub list now shows without the USB stick.  However, I cannot get it to restart like normal.  I need to shut down or hold the power button.  I made a new thread about this different issue.  You should be able to check my previous posts, it is right after this one.

---

### Post by jadtech on 2012-05-15
> **daisyflower said:**
> Is this in regard to the grub list or the reboot issue?  The grub list now shows without the USB stick.  However, I cannot get it to restart like normal.  I need to shut down or hold the power button.  I made a new thread about this different issue.  You should be able to check my previous posts, it is right after this one.

just so you know your new thread is not  right below this one it may have been when you made when you posted not now ...

---

### Post by daisyflower on 2012-05-16
jadtech, I was referring to my history, not the threads in this forum.  If you go to my profile, you should be able to see a thread about "restart" and "reboot" issues.  I am refraining from making other posts so someone who can help can find the thread more easily.  Again, please check my post history in my profile.

---

### Post by sanctusconsilium on 2013-01-29
Thank you! This totally worked. I know the person who posted the solution probably won't read this ever.

Also, for the solution mine had a bit of a twist.

This is EXACTLY what I had to do to make it work.

* I installed Lubuntu from a flash drive. (installation seemed to go fine)

* I took out the flash drive like normal and attempted to boot from the hard drive

* Instead of Lubuntu loading up, it just sat there on the black loading screen with a little flashing underscore (I let it sit for 10 minutes and nothing happened)

* I decided to put the flash drive back in and boot to the flash drive to perhaps reinstall or something

* Instead of booting from the flash drive the computer instead boots to the normal install of Lubuntu on the hard drive even though I selected "Boot: Flash Drive" (yes very strange....)

* I then had access to the terminal and could perform the commands

**This was the only way I could get the sudo fdisk and sudo grub install stuff to work, trying to launch the live version gave me some weird error about blocklists**

I then did the sudo fdisk -lu and sudo grub-install /dev/sdb (in my case) and poof, everything was happy

thanks again guys!

---

