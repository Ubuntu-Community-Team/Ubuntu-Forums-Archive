---
title: "Fixing my grub&gt;"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by liamhyland on 2011-04-05
For the past three weeks I have explored the forums to help solve a simple problem but not simple to me.  I am attempting to get beyond my grub> as it has hung up there after trying to update my Samsung netbook from 10.04 to 10.10.
I have found some answers but a basic question is where do I load grub from a livecd to the mount point where I have already installed my Ubuntu 
I have attached a screen shot of my partitions on my 160 gb hd and hope it can be opened?  
Thanks for helping out.  Appreciated.  Liam

---

### Post by Quackers on 2011-04-05
Why do you hve a grub prompt?
All your partitions appear to be NTFS type. Ubuntu won't be in one of those.
If you try (or have tried) to create another primary partition you will have big problems!
Did you intend to install a Linux system in sda5? If so, that partition would need to be ext3 or ext4 type - not NTFS

---

### Post by coffeecat on 2011-04-05
Do you mean that when you start your Samsung netbook you get a grub prompt and you can't boot either Windows or Ubuntu? If so, Quackers is right. There is no Ubuntu partition in sight.

Do you mean that you once had Ubuntu on that machine and that you reformatted the Ubuntu partition?

---

### Post by liamhyland on 2011-04-05
> **Quackers said:**
> Why do you hve a grub prompt?
All your partitions appear to be NTFS type. Ubuntu won't be in one of those.
If you try (or have tried) to create another primary partition you will have big problems!
Did you intend to install a Linux system in sda5? If so, that partition would need to be ext3 or ext4 type - not NTFS

My Samsung had win 7 and I put on it ubuntu 10.04 and it was duel booting.  Then I decided to update it to 10.10 but it downloaded the program and was intalling it when it just hung up and was sitting there doing nothing.  I turned it off and when I reboot it it would go into win 7 but it would just go into grub> and sit there and do nothing.  I have tried commands and get 'no kernel found'

---

### Post by liamhyland on 2011-04-05
No, I did not intentionally try to start a new partition but I did load livecd to and went as far as setting up the partitions to see what was in there but my skill level is limited when it comes to partition but I have learned lots about sda and sda1 etc.  Thanks for your help so far so do you.  Liam

---

### Post by liamhyland on 2011-04-05
> **coffeecat said:**
> Do you mean that when you start your Samsung netbook you get a grub prompt and you can't boot either Windows or Ubuntu? If so, Quackers is right. There is no Ubuntu partition in sight.

Do you mean that you once had Ubuntu on that machine and that you reformatted the Ubuntu partition?

Thanks for your response.  I have not intentionally done a reformatting anything...but in the course of two or so weeks I have started it up with a livecd and looked at the programs on it.  When I put ubuntu on it onrigionally I did use wubi. Then I went to update it....Ah I think it has come to me...maybe i put it on with wubi and then proceed to put on update it but not with wubi...am I out on left field!   Thanks liam

---

### Post by oldfred on 2011-04-05
This may be a good thread to review:

how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

if you just have wubi you need to reinstall the windows boot loader.

---

### Post by liamhyland on 2011-04-05
> **oldfred said:**
> This may be a good thread to review:

how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

if you just have wubi you need to reinstall the windows boot loader.

Oldfred, nice to lear of your addiction, and for your response. This old Liam is open to support your addiction by my question in response to your answer!   
  So I go and uninstall the wubi boot loader and reinstall it again and let it find the place authomatically or do I load it onto one of these settings as outlined in the solution given by drs305:


Areas in bold must be changed to your system's Windows partition (X,Y and sda1). To boot Wubi from the grub prompt:

Code:
insmod ntfs
set root=(hdX,Y)  # Your Windows partition. Example: set root=(hd0,1)
loopback (loop0) /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
initrd /initrd.img
boot


Can you tell me where in my disk I woul load the patrition

Thanks Oldfred from Liam in Canada

---

### Post by bcbc on 2011-04-06
```
search -s -f -n /ubuntu/disks/root.disk
echo $root

```
What does that show?

Or maybe it'd be easier just to run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/").

---

### Post by liamhyland on 2011-04-06
> **bcbc said:**
> ```
search -s -f -n /ubuntu/disks/root.disk
echo $root

```
What does that show?

Or maybe it'd be easier just to run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/").

Thanks BCBC, and it shows hd0,msdos2

Hope that will help and if not then I will follow up with your bootinfo script suggestion.
Liam from sunny Alberta.

---

### Post by bcbc on 2011-04-06
Reboot so it resets (root needs to = (loop0)). Then enter these lines (if you have any boot workarounds put them where you see 'quiet splash')

```
linux /vmlinuz root=/dev/sda2 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```

Once booted, apply the Permanent Fix in the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198").

---

### Post by liamhyland on 2011-04-06
> **liamhyland said:**
> Thanks BCBC, and it shows hd0,msdos2

Hope that will help and if not then I will follow up with your bootinfo script suggestion.
Liam from sunny Alberta.

Here are the results of my bootinfoscript:

---

### Post by bcbc on 2011-04-06
So if that didn't work, then likely your problem has more to do with the stalled upgrade than the normal wubi booting issue after the upgrade.

This is what you should do:
1. backup the root.disk (c:\ubuntu\disks\root.disk)
2. run chkdsk on windows (My computer, right click on C:, Properties, tools, check disk for errors, fix automatically... reboot to complete).
3. boot the live CD and run fsck on the disk:
```
sudo mkdir /media/win
sudo mount /dev/sda2 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk

```

If that works, you can try booting Wubi, however depending on where the upgrade failed you may still have problems. If you get any errors or weird messages doing the above, report back.

---

### Post by liamhyland on 2011-04-09
> **bcbc said:**
> So if that didn't work, then likely your problem has more to do with the stalled upgrade than the normal wubi booting issue after the upgrade.

This is what you should do:
1. backup the root.disk (c:\ubuntu\disks\root.disk)
2. run chkdsk on windows (My computer, right click on C:, Properties, tools, check disk for errors, fix automatically... reboot to complete).
3. boot the live CD and run fsck on the disk:
```
sudo mkdir /media/win
sudo mount /dev/sda2 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk

```

If that works, you can try booting Wubi, however depending on where the upgrade failed you may still have problems. If you get any errors or weird messages doing the above, report back.

 BCBC, First, let me say thank you for your support, and the many others too, including Oldfred.  I must say my saga went from bad to worse and that is partially my drama and my impatience. I went to the library and got the latest Ubuntu book (Ubuntu Unleashed 2011 Edition) and decided to re install the grub with it and the consequences was that I got the boot loader to work but when I booted it up it came to the menu and once I went into it it wanted a password (I had not given it a password), and I tried out the win 7 and it worked and it had a vista (which was the recovery version on the Samsung net-book).  I clicked on that and it came up with three options including backup.  I closed that and then when I went to reboot the Samsung came on but only the splash screen with Samsung logo flashed  and then it would go off and it would keep going on an endless cycle. 
Now I had nothing and I kept pressing every key.  I think there is a suggestion in the Samsung website for reinstalling a start up program via the usb stick.  Anyway, I knew a friend and gave it to him and he said he will fix the windows boot loader and go from there.  So hopefully he can restore it or re-install the win 7 boot loader fix.  How about that for a response.  I sure am learning... and the moral of the story..be patient.  From Liam with thanks to all who responded.

---

### Post by bcbc on 2011-04-09
I am sorry to hear your troubles. Unfortunately installing grub on a Wubi system is always a bad idea and often will break windows depending on which partition you elect to install to.

Generally you'll need to replace the grub2 bootloader with windows (bootrec /fixmbr) and repair the bootsector on the partition you installed Grub2 on (bootrec /fixboot). Also, sometimes you can end up with a mix of /boot and /Boot folders which windows won't accept.

The one positive is that likely none of your data is affected, so whatever you do - don't reinstall unless you've backed up everything. And if you need more help from us, then boot from an Ubuntu CD (select Try it, or Try without installing), and then download and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results back here.

---

### Post by liamhyland on 2011-04-17
Thank you BCBC and I will follow your directive and submitt the bootinfoscript as soon as I get the netbook back from my friend who is going through some health challenges and not able to fix it at this time.  I hope to have it back by today and post it then but if not I am off next week on retreat.... time off to heal myself spiritually and psychologically.  Thank you in anticipation, and may your days be filled with peace and joy...Liam

---

