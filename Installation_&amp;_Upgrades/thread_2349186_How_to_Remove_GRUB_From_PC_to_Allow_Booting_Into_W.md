---
title: "How to Remove GRUB From PC to Allow Booting Into Windows"
date: 2017-01-11
forum: Installation &amp; Upgrades
---

### Post by lastt on 2017-01-11
I recently tried to reinstall Ubuntu 16.04LTS on my usb drive because  the installation got corrupted somehow. When I did however it did  something to the HDD on my PC even though I never told it to. In  fact, in the past when I tried to install to the PC HDD it would fail  because it finds 0GB of free space on it so installing anything to that  HDD should be impossible. 
  Now however I am unable to boot into Windows at all unless the usb is  plugged in. Even worse is that the Ubuntu grub pops up even when I tell  the PC to boot to the PC HDD. When I try to boot into windows without the usb  in I get this error:
  
```
error: no such device: fb71e4ae-6251-495b-8e3c-f3f7e302348e 
Entering rescue mode:
grub rescue >_
```
  
I never intended for any Linux software to be installed to the PC  HDD, only to the usb but somehow it got on the PC HDD anyway. I attempted to restore the Vista bootloader with a system recovery DVD as recommended here: [https://ubuntuforums.org/showthread.php?t=1014708]("https://ubuntuforums.org/showthread.php?t=1014708")
Unfortunately when I boot it I get a prompt that says "Windows is checking files" and then I just get a black screen with no prompts or anything. Does  anyone know how I can remove the Linux software from the PC HDD so I can  boot into windows normally? I'd really like to fix this because the PC isn't even mine. I was just using it to get Ubuntu on my usb so I wouldn't get in the way. But now the PC is even worse off... :(

---

### Post by gdesilva on 2017-01-12
Since you have written the Windows boot loader into MBR and now you can boot into Windows, it appears the Windows installation may have got corrupted. I would try to boot the system with Windows install disk, go into repair mode and run chkdsk command on the Windows partition and reboot. To remove Linux software on the disk is easy - just work out the partition and delete it. You should be able to do this using Windows fdisk command from the repair mode but first see whether you can get Windows working again. Good luck.

---

### Post by Bucky Ball on 2017-01-12
Welcome. Please run the Bootinfoscript and post a link to the output here. We will be able to see exactly what has happened to your hard drive boot. 

You can find this in Boot Repair (see last link, first line of my signature at the bottom of this post). You can also see here for[ just the bootinfoscript]("http://bootinfoscript.sourceforge.net/"). Launch Boot Repair and don't do any repairs, just run the infoscript.

As above, your Win boot is obviously screwed and that would need to be fixed before doing much else.

---

### Post by lastt on 2017-01-13
> **gdesilva said:**
> Since you have written the Windows boot loader into MBR and now you can boot into Windows, it appears the Windows installation may have got corrupted. I would try to boot the system with Windows install disk, go into repair mode and run chkdsk command on the Windows partition and reboot. To remove Linux software on the disk is easy - just work out the partition and delete it. You should be able to do this using Windows fdisk command from the repair mode but first see whether you can get Windows working again. Good luck.

I wasn't actually able to do this. When I booted the disc I just ended up on a black screen and nothing happened. 

> **Bucky Ball said:**
> Welcome. Please run the Bootinfoscript and post a link to the output here. We will be able to see exactly what has happened to your hard drive boot. 

You can find this in Boot Repair (see last link, first line of my signature at the bottom of this post). You can also see here for[ just the bootinfoscript]("http://bootinfoscript.sourceforge.net/"). Launch Boot Repair and don't do any repairs, just run the infoscript.

As above, your Win boot is obviously screwed and that would need to be fixed before doing much else.

I tried to attach the .txt to the thread but I keep getting an error. It's the right size and everything so I'm not sure what's wrong.

---

### Post by Bucky Ball on 2017-01-14
You don't need to attach the text. When you run the bootinfo from Boot Repair it will give you a html link to the output. Just post that link. :)

---

### Post by lastt on 2017-01-14
> **Bucky Ball said:**
> You don't need to attach the text. When you run the bootinfo from Boot Repair it will give you a html link to the output. Just post that link. :)

Oh ok. I just downloaded the script and tried to run it... :oops: 

[http://paste2.org/esygdcnJ](http://paste2.org/esygdcnJ)

---

### Post by Bucky Ball on 2017-01-14
All good. 

Ok. Two things. What is on sda and what actually is it? Things seem to be a bit skew whiff as the drive you have your installs on is the second one, sdb. The system is looking for grub on sda and there's not one installed there. In fact, looks like nothing is installed there and it's possibly not formatted. 
 
I have a couple of suggestions. One is to take sda out of the box completely or disconnect it, whatever it is. It appears to be playing no part in this and then your sdb may become sda and things *might* work. The other option is to swap the cables over. Plug the one that's in sda into sdb and vice versa then reboot and see what happens. 

Third suggestion, and I don't rate this highly as I don't know what sda is, is to install grub on sda as it is not there now, and then things should work.

Firstly, try this. Take all USB sticks out of the machine and boot. What happens? Secondly, please clarify what exactly that blank disk sda is and remove it if it is not required.

See how you go.

---

### Post by lastt on 2017-01-14
> **Bucky Ball said:**
> All good. 

Ok. Two things. What is on sda and what actually is it? Things seem to be a bit skew whiff as the drive you have your installs on is the second one, sdb. The system is looking for grub on sda and there's not one installed there. In fact, looks like nothing is installed there and it's possibly not formatted. 
 
I have a couple of suggestions. One is to take sda out of the box completely or disconnect it, whatever it is. It appears to be playing no part in this and then your sdb may become sda and things *might* work. The other option is to swap the cables over. Plug the one that's in sda into sdb and vice versa then reboot and see what happens. 

Third suggestion, and I don't rate this highly as I don't know what sda is, is to install grub on sda as it is not there now, and then things should work.

Firstly, try this. Take all USB sticks out of the machine and boot. What happens? Secondly, please clarify what exactly that blank disk sda is and remove it if it is not required.

See how you go.

I'm not really sure. I think sda is actually the Windows partition. The ubuntu installer sees that it has 0GB of space because something is probably wrong with the HDD but there is an OS on there. I can't always get into it though because it only mounts randomly. I'm actually using a laptop and I'd like to avoid opening it up...  

When I boot without the USB in I either get an "Operating System Not Found" error because I think something is just wrong with the HDD. When it does boot I get the error message I posted in the OP.

---

### Post by linux1pacman on 2017-01-14
Maybe with the drive that You think has windows partition on it unplug any usb device or hdd then try fixing MBR 
[https://neosmart.net/wiki/fix-mbr/](https://neosmart.net/wiki/fix-mbr/)

---

### Post by Bucky Ball on 2017-01-14
That is your issue, then. Your system is looking on sda, the broken Windows install, for boot. Either get rid of it or fix Windows boot. That needs to be fixed before doing anything else if you're intending to use Windows on that disk.

If you're not, take that disk out of the box, plug sdb where it was, boot and see what happens. Now you have sdb as sda it just may work as expected.

PS: When you're doing this best not to 'think' something is somewhere. Better to know for sure what you have where and in what condition. If you have a broken Windows on sda this was never going to work. Or is Windows simply hibernating and won't give Ubuntu access to the disk? ;)

---

### Post by yancek on 2017-01-15
What kink of 'system recovery DVD' were you referring to in your initial post?  What you would need is the vista installation DVD to repair it if you have vista on the laptop internal hard drive.  The link you have in that post doesn't discuss anything like that and in fact is specifically for re-installing Grub to a drive which previously had Ubuntu on it and the Grub code has been overwritten by a windows install.  That was not what you needed to do.

Your 11GB drive (shown as sdb) has a windows partition on it (sdb1) which takes up most of the drive.  You have Grub in the MBR of sdb (111GB drive) and it points to the correct location so you should be able to boot Ubuntu with that drive set to first boot priority.  There is not entry for windows in the grub.cfg file so I'm not sure how you can boot any windows.

If you want to repair the boot on sda, the drive on the laptop, you need an installation DVD for whichever system it was using and you can select the Repair option on boot.  If you don't have that available, you might be able to download some type of windows repair disk to do this.

---

### Post by lastt on 2017-01-15
The disc I'm using is labeled "System Recovery DVD." Is this the wrong  type of disc? Also when I boot it I end up with a black screen so I'm  not really sure where to go from here.

---

### Post by yancek on 2017-01-16
If the DVD you are using is a windows vista System Recovery DVD, you might be able to repair the MBR with it if you have a repair option when it boots.  The instructions at the link you posted above to try to repair won't work for what you intend to do as it is specifically for repairing the Linux Grub to boot windows.  That doesn't  seem to be what you want to do.  There are instructions at the site below on reinstalling boot code for vista if you scroll down the page.  Don't use the instructions for xp as it uses a different bootloader.  If you don't have a Repair your computer option on the DVD, you will need the installation DVD or you will need to download a recovery iso file to use.  

[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

You might be better off trying to find a windows site for repairing the MBR.

---

### Post by yancek on 2017-01-16
Forgot the link in the above post.

[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

---

### Post by efflandt on 2017-01-16
Did you create recovery media for Vista on DVDs or many CDs when you first got the laptop (usually manufacturers provide a utility to do that since they no long provide hard copies on DVD)? Or newer systems can alternately set up a recovery system on 32 GB USB memory. It looks like nothing on that drive is readable at all at this point. You might see if **testdisk** can find anything on it: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) which think it is on a live/install system, or you can install it on a working system:```
sudo apt update
sudo apt install testdisk
```Once I was trying to recover what I could from an old work laptop that my boss gave to his grandsons that only contained WinXP. I booted Ubuntu into a live session from DVD and only got part of the user's home directory copied to a USB drive before the drive totally choked. It was an old PATA drive that I put in an external USB enclosure, and at that point neither Windows nor Linux could find any data on the drive. I let it sit for a few weeks and on a whim connected the USB enclosure to my Linux PC, the drive auto mounted, and I was able to copy most of user's Windows home dir except for a corrupted game dir. I must have made recovery discs at an earlier time, because I was able to reinstall WinXP to a new drive.

I had the laptop drive USB enclosure from an earlier time when a friend's drive began failing. I had copied most of her data to an external drive, but at the time I did not know where Outlook kept is old e-mail. When I took the laptop drive to the store to find a USB enclosure, I dropped the drive just a few feet onto the hard floor at the store and that totally finished it off. Nothing was readable after that. But at that point I had already set up a new Win7 laptop for her, so I copied her data to the new laptop and the only thing missing was her old emails. That was in 2009.

---

