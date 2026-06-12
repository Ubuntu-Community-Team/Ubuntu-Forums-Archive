---
title: "Clonezilla &amp; GRUB problem"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by kakashi_12 on 2010-04-30
Okay, so this is my first time ever using Clonezilla to actually restore an image. Now that it's restored the whole drive (dual boot Ubuntu and XP) it won't boot. It just sits at the GRUB screen saying please wait to boot. Can I put in the Ubuntu CD and rebuild the GRUB? It won't allow me to go anywhere else or say any OS.

---

### Post by kansasnoob on 2010-04-30
Please use an Ubuntu Live CD and post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by kakashi_12 on 2010-04-30
What would the command be to list that info?

---

### Post by kakashi_12 on 2010-04-30
nvm, i understand the cmd from the link now.
 
But, I can't find a download link for a LIVE Ubuntu iso. I found Ubuntu 10 (but it's too big to fit on a cd-r. barely). i want either 8 or 9. I found 9, but it's not live.

---

### Post by kakashi_12 on 2010-04-30
Unfortunately that bash command isn't working! But I got the application downloaded. I can open it and it displays a bunch of info. Do you want me to paste that? Should I also paste my menu.lst

Edit: nvm, i got the cmd to work.

---

### Post by kakashi_12 on 2010-04-30
Here's the attachment of the txt file.

---

### Post by kansasnoob on 2010-04-30
Do you know where the Boot Info Script downloaded to?

Usually either Desktop or Downloads. If it's on the Desktop run the command:

```
cd Desktop
```

And then:

```
sudo bash boot_info_script055.sh
```

If it runs at the very end it will say where the RESULTS.txt is saved. As an example my downloads go to Downloads (and I have a weird symlinked data system):

```
lance@lance-desktop:~$ cd Downloads
lance@lance-desktop:~/Downloads$ sudo bash boot_info_script055.sh
[sudo] password for lance: 
Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sda8 for information... 
Searching sda9 for information... 
Searching sda10 for information... 
Searching sda11 for information... 
Searching sda12 for information... 
Searching sda13 for information... 
Searching sda14 for information... 
Searching sda15 for information... 
Searching sda16 for information... 
Searching sda17 for information... 
Searching sda18 for information... 
Searching sda19 for information... 
Searching sdb1 for information... 
Searching sdb2 for information... 
Searching sdb5 for information... 
Searching sdb6 for information... 
Searching sdb7 for information... 
**[COLOR="Red"]Finished. The results are in the file RESULTS3.txt located in /mnt/sda9[/COLOR]**
lance@lance-desktop:~/Downloads$ 

```

I realize my setup is complex but you can see it says the RESULTS3.txt is in /mnt/sda9 so I'd look there to find it. Then personally I like to just right click that file, choose to compress and use the "paper clip" thingy at the top of these reply boxes to attach the compressed tar.gz :)

---

### Post by kakashi_12 on 2010-04-30
Ya, see above. I editted my post saying that I figured out the command finally. and i posted in the next post my results.

---

### Post by kansasnoob on 2010-04-30
> **kakashi_12 said:**
> Here's the attachment of the txt file.

Cool! You figured it out while I was typing :)

Give me a little bit to digest that, I'll be back.

---

### Post by kansasnoob on 2010-04-30
OK what we know now, Win XP is on sda1 and it's boot files appear to be intact:

> sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

And Intrepid is on sda3:

> sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

But I've never seen any *buntu with a "/boot/grub/grub.conf", but I also only used Intrepid very briefly because 8.04 was simply better for me. I can assure you though that neither 8.04 or 9.04 had a "/boot/grub/grub.conf" so that might be kind of a problem.

Then again are you aware that Intrepid has reached end-of-life?

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

So that might be somewhat of a moot point :(

Since you cloned a whole drive it's possible that something changed in Windows, like it's picky about it's "start point" on the drive. Also look here:

[http://www.nilbus.com/linux/disk-copy.php](http://www.nilbus.com/linux/disk-copy.php)

Lots to try and consume but lets do some more troubleshooting. let's create a Windows readable mbr. From the Live Desktop (I guess that's how you ran the Info Script):

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

Then see if Windows will boot. If not you have a Windows problem.

In the mean while I'll start comparing UUID's.

Edit: What version of Ubuntu did you download?

---

### Post by kakashi_12 on 2010-04-30
If I create an MBR, will that effect the one that's on there? Am I creating it then putting it on the hard drive? Will that override the GRUB loader? Very confused.

---

### Post by kansasnoob on 2010-04-30
> **kakashi_12 said:**
> If I create an MBR, will that effect the one that's on there? Am I creating it then putting it on the hard drive? Will that override the GRUB loader? Very confused.

From what you've said you can boot nothing now, eh?

You've downloaded some version of Ubuntu Live CD, eh?

If so we can change the mbr as often as we like (especially if you can copy-n-paste commands). To give the drive a Windows mbr do as I said in my last post. To give it a GRUB mbr I really need to know what version of Ubuntu Live CD you're using. It's very easy. Don't worry.

---

### Post by kakashi_12 on 2010-04-30
I almost went "oh sh*t", I was getting a bunch of error messages when rebooting. But I think that's cause I took the live cd out too early when rebooting. Then I was like, "Sweeeet, it boots to Windows!"
 
So now what?!:popcorn:

---

### Post by kakashi_12 on 2010-04-30
The version of the live cd is ubuntu 8.4.4

---

### Post by kansasnoob on 2010-04-30
Well this is good! You can at least boot Windows!

Hey let's face it Windows ain't free :lolflag:

So now we have to figure out Intrepid. Let me think a bit. I won't abandon you.

---

### Post by kansasnoob on 2010-04-30
Just FYI I'm looking :)

And thinking :confused:

I also have someone hitting me with PM's waaaaaaaaay too often :frown:

Please be patient.

---

### Post by kansasnoob on 2010-04-30
**[COLOR="Red"]oops, I left out "update grub"! added it now![/COLOR]**

So, I can't find anything indicating Intrepid should have a "/boot/grub/grub.conf"! Nothing!

So we'll try fixing things in a chroot. You'll need to use your new 8.04.4 CD, boot to a Live Desktop and copy-n-paste these commands (some are quite long so you must copy-n-paste):

```
sudo mount /dev/sda3 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
mv /boot/grub /boot/grub_backup
```

```
mkdir /boot/grub
```

```
apt-get install --reinstall grub
```

```
update-grub
```

```
grub-install /dev/sda
```

Then you need to open a grub shell:

```
grub
```

You'll see the "prompt" change then:

```
root (hd0,2)
```

```
setup (hd0)
```

```
quit
```

Then we'll exit the chroot:

```
exit
```

And unmount:

```
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```

Then reboot and see if you can boot Ubuntu. If not repeat the previous steps to create a Windows mbr.

---

### Post by kakashi_12 on 2010-05-01
ok. i did all that code. and it still didn't work. grub still just sits there.
 
i'm not sure i understand all that code. did i recreate grub or something?
 
anyways, what now? if i redo the lilo command, that will just put me back at square one, right? what now?

---

### Post by kansasnoob on 2010-05-01
> **kakashi_12 said:**
> ok. i did all that code. and it still didn't work. grub still just sits there.
 
i'm not sure i understand all that code. did i recreate grub or something?
 
anyways, what now? if i redo the lilo command, that will just put me back at square one, right? what now?

Sorry to just disappear as I did. We had a heck of a storm blow through and my power's been out.

I still have a lot of clean up to do around here, but as far as your problem goes "square one" was being able to boot nothing.

You at least found that you can boot Windows so I wouldn't call that "square one" :)

As I said Intrepid has reached end-of-life so we might encounter problems dealing with installing or reinstalling packages, etc.

The thing is my goats need a roof over their heads so that takes priority at the moment. I know this is a pain for you but you do now have one of two OS's booting :)

Dealing with an end-of-life OS can be very difficult and I still don't understand that grub.conf being in there.

---

### Post by kakashi_12 on 2010-05-01
Do you just not know how to fix it?
 
...
 
Can anyone else help me?

---

### Post by kansasnoob on 2010-05-02
It may help to see a new RESULTS.txt from the Boot Info Script since we totally reinstalled grub.

Another thought I had was trying Super Grub Disc just to see if it can boot Intrepid. Just a note from SGD:

> If you are a newbie please check for Cdrom, Usb or floppy download instead of SG2D Cdrom, SG2D Usb and SG2D floppy on mirror #0. This is the old Super Grub Disk which actually works better than the new Super Grub Disk based on Grub2. Sorry for any troubles that you run into.

So personally I'd stick with version 0.9799 at the bottom of this page:

[http://developer.berlios.de/project/showfiles.php?group_id=10921](http://developer.berlios.de/project/showfiles.php?group_id=10921)

But I'm thinking that if you were able to follow my instructions properly and grub reinstalled properly that the cloning may have damaged something in Ubuntu beyond just grub :(

And IMHO it might be rather pointless to invest a great deal of time into recovering Intrepid since it's no longer supported. Even upgrading an EOL release can get messy:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Specific for Intrepid to Jaunty:

[https://help.ubuntu.com/community/EOLUpgrades/Intrepid](https://help.ubuntu.com/community/EOLUpgrades/Intrepid)

Depending on your disc size and used vs free space I've found it's generally easy to install a new Ubuntu next to the old one, transfer my files, and then delete the old Ubuntu once all is restored, then finally resize the new Ubuntu to use that space. Or if you have a spare drive you could also just back up your data and then transfer it back to the new Ubuntu.

But, as I said yesterday, I still have a great deal of cleanup around here that must be done.

---

### Post by kakashi_12 on 2010-05-04
I think I finally solved this. I just re-cloned all over. And instead of cloning the whole drive, I just did separate partitions. Therefore not affecting the mbr.

---

### Post by SBillion on 2012-05-24
There is a simple solution.
When you clone an entirer disk, you don't need to reinstall grub or other amorcing system, because I can suppose you have already it :P!
Just restore the MBR and not install grub. So when you are in restore mode, choose expert mode and simply uncheck -g !!
Sorry for my bad english :(

Have fun!

---

