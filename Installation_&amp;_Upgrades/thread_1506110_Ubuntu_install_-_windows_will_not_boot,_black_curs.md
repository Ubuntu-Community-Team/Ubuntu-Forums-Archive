---
title: "Ubuntu install - windows will not boot, black cursor?"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by MatthewVC on 2010-06-10
Greetings, 

I recently decided to install Ubuntu on my home computer to run a program for work that is designed for Linux.  I have two hard drives, so decided to install Ubuntu on one, and keep windows 7 on the other.

I put the Ubuntu iso onto my USB drive and installed Ubuntu.  After the install I was prompted to restart.  Upon restarting, after the boot screen flashed, the screen went blank aside from a flashing _ in the upper left.  I had no option to boot to windows or Ubuntu.  

I then tried to fix windows using the installation CD, but windows could not find anything wrong.  I reinstalled Ubuntu, and for the first time or two rebooting, Ubuntu would start, but I had no option to run windows.  I then held shift after the bootscreen, but the only options I got were to boot into linux or to do a memtest.  

Since then, when I restart my computer, I go back to the blank screen with a cursor, and if I hold shift, I can get the word GRUB to show up, instead of the program starting.  Currently I'm on the computer using the USB as a "live CD" to try to get an idea of what to do here.

I also thought to try reinstalling Ubuntu onto the hard drive with windows on it, but there is no option to use that HD in the ubuntu installation.

I'd really like to get my computer up and running, preferably without needing to reinstall windows.  Any help would be much appreciated.

Thanks,
Matt

---

### Post by resolv_25 on 2010-06-10
Here is some tutorial:
[https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)
But, if you don't have important data or plenty settings, I would prefer a fresh install.

---

### Post by MatthewVC on 2010-06-10
Thanks, but I'm not sure that downgrading Ubuntu is going to help, especially since I can't get Ubuntu to load.  Are there any suggestions on how to get windows and Ubuntu to boot, instead of just going to the black screen with a cursor?

---

### Post by Mark Phelps on 2010-06-10
> **MatthewVC said:**
> I recently decided to install Ubuntu on my home computer to run a program for work that is designed for Linux.  I have two hard drives, so decided to install Ubuntu on one, and keep windows 7 on the other.
Best way to do this, in my experience, is to disconnect the MS Windows drive during the install, thereby ensuring that nothing happens to it.  Once done, it's an easy matter to reconnect the MS Windows drive, boot from the Ubuntu drive, open a terminal and enter "sudo update-grub" -- and autogenerate a GRUB menu that includes an option to boot into MS Windows.

Since you apparently can't boot into either OS, you have to decide which one you want to fix first.

Try disconnecting the Ubuntu drive and seeing if you can boot into Win7.  IF you can, then you will need to solve the Ubuntu problem.

IF you can't, and you want to use Win7 while you're figuring out how to fix the Ubuntu problem, then run Startup Repair from your Win7 disk three times.

Since you most probably did NOT use the Win7 Backup option to create and burn a Win7 Repair CD, go the the link below, download and burn the appropriate Win7 CD, and use that to do the repair:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

---

### Post by MatthewVC on 2010-06-10
Thanks Mark, that sounds like a logical way to go.  

I've fixed windows and got that working again using the installation CD and the bootrec.exe command.  Tonight, I'm going to try to install Ubuntu with my primary HD unplugged and see how that goes.  

Is creating the grub menu as easy as typing in that command?  Or is there more I need to know to do that?

Thanks again,

Matt

---

### Post by oldfred on 2010-06-10
I am not as big of a fan as Mark Phelps of plugging & unplugging drives. If you do unplug be sure to keep windows as the first drive and let Ubuntu become the second. It may still have issues of changing from drive 0 to drive 1 but handles it better than windows. Windows once installed to drive 0 will not be happy becoming drive 1.

I prefer to keep both drives installed but you have to be careful to use the advanced button on the last partition screen of the install to be sure to install grub to the second/Ubuntu drive. Then windows is only on one drive and Ubuntu is only on the other just as unplugging but Ubuntu will find windows during the install.

Note advanced button:
[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by koppes on 2010-06-10
Hey, my computer does the same thing, and I installed using the WUBI by creating a partition.  I've uninstalled and reinstalled a couple of times, and I get the same thing over and over.

---

### Post by MatthewVC on 2010-06-14
Thanks all for the replies.  I now have Ubuntu working (mostly) on my second hard drive.  I just have two problems that I'd like some thoughts on.  


[LIST=1]
[*]When I boot, if I select my second hard drive (w/ Ubuntu) to boot first, Grub pops up but doesn't have any option to boot into windows.  If I designate the first hard drive (windows) as the first to boot, Windows starts, without the option to boot into Ubuntu.....  How can I get grub to allow me to select between windows and Ubuntu?
[*]Ubuntu formatted the second hard drive during installation, which is fine.  However, windows will no longer let me name or access the second drive, even if I go under the drive management window.  Is there any way to make windows assign a drive letter to the drive with Ubuntu on it?
[/LIST]

Thanks again!

Matt

---

### Post by oldfred on 2010-06-14
From Ubuntu run sudo update-grub and it should find windows.

Windows will not read linux file systems. I do not like writing into a system directory so while with Ubuntu I could write into the windows system directory I try to only read from it. To share files I created another NTFS partition and put any data like firefox & thunderbird profiles, photos etc in the shared partition. Now I most in Ubuntu but have spare partitions for other distros so I have another data partition to share linux data.

---

### Post by MatthewVC on 2010-06-16
Ran the grub update, and here is what I got....  any ideas?

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
ERROR: pdc: wrong # of devices in RAID set "pdc_babfihhjci" [1/2] on /dev/sda
ERROR: pdc: wrong # of devices in RAID set "pdc_babfihhjci" [1/2] on /dev/sda
done

---

### Post by oldfred on 2010-06-16
Are you or did you ever run raid?

---

### Post by MatthewVC on 2010-06-16
I'm not on a raid now, I have two SATA drives installed.  When I first installed windows, I tried to set up a raid, but there were issues with Windows 7 and my bios raid drivers, so I wasn't able to set up a raid.  Currently, I have the raid option in my BIOS disabled.  I'm puzzled as to why it thinks I have a raid set up as well...

---

### Post by oldfred on 2010-06-16
Drives save metadata for RAID. I think the updates to grub now recognize that to prevent corruption of raid disks.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

sudo apt-get remove dmraid
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/461470](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/461470)

---

### Post by MatthewVC on 2010-06-17
That did the trick!  

Thanks for all your help,

Matt

---

