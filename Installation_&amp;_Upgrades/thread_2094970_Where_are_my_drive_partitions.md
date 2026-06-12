---
title: "Where are my drive partitions?"
date: 2012-12-15
forum: Installation &amp; Upgrades
---

### Post by Engineeringtech on 2012-12-15
A couple months ago I updated my desktop OS from Ubuntu 11.04 to 11.10.  The upgrade went smoothly, but I lost access to my drive partitions.  There are no icons for them on the desktop, in the launcher, or in Nautilus.   USB thumb drives, CD's and DVD's  also no longer show on the desktop when inserted.    And they don't appear in the launcher, or Nautilus either.   So I posted here, seeking help.  Basically, I was told I must've done something wrong with the upgrade.  I was told to edit FSTAB, or reinstall from scratch.  

 I tried  editing FSTAB.  I gained read only access to my windows and data partitions, but not any removable drives or optical media.     I even upgraded to 12.10, hoping that would solve the problems, but it didn't.      I've been deferring doing a full reinstall, hoping for a solution that is not so drastic, and because I doubt it will solve the problems.  The computer is not much use to me as is.

Meanwhile I have been using my  old laptop (also Ubuntu 11.04).  Everything was working fine.   I had access to all my partitions and removable media.  But I was getting annoyed by the popup messages saying that I would not get any more security updates.   So finally, after putting up with this for over a month, I decided to the update my laptop to 11.10.    As on my desktop, the installation went smoothly.     Now this is totally different hardware, yet  I got the same results.

It seems to me that this is behaviour BY DESIGN.  The 11.10 upgrade removed my access to drive partitions and removable media.  So what is necessary to restore it?

---

### Post by dino99 on 2012-12-15
is your install a real one or a virual one ? (wubi/virtualbox/...)

[http://www.google.fr/#hl=fr&gs_nf=3&gs_rn=1&gs_ri=serp&pq=ubuntu%20don't%20show%20desktop%20icons&cp=7&gs_id=x&xhr=t&q=ubuntu+desktop+icons&pf=p&safe=off&tbo=d&sclient=psy-ab&oq=ubuntu+desktop+icons&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&fp=ac9d2c5f7cf2a4ff&bpcl=39967673&biw=1485&bih=909&bs=1](http://www.google.fr/#hl=fr&gs_nf=3&gs_rn=1&gs_ri=serp&pq=ubuntu%20don't%20show%20desktop%20icons&cp=7&gs_id=x&xhr=t&q=ubuntu+desktop+icons&pf=p&safe=off&tbo=d&sclient=psy-ab&oq=ubuntu+desktop+icons&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&fp=ac9d2c5f7cf2a4ff&bpcl=39967673&biw=1485&bih=909&bs=1)

---

### Post by oldfred on 2012-12-15
I do not know what you mean by lost partitions. 

Or is it the new Unity which does not show icons on desktop. But you should see them in the left panel of Nautilus or in Unity's left panel.

I do not really know Unity as I use fallback.

       Unity info
[http://unity.ubuntu.com/about/](http://unity.ubuntu.com/about/)
[http://www.omgubuntu.co.uk/2011/04/how-to-add-folder-quicklists-to-the-home-launcher-in-ubuntu-unity/](http://www.omgubuntu.co.uk/2011/04/how-to-add-folder-quicklists-to-the-home-launcher-in-ubuntu-unity/)
[http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)
[http://www.omgubuntu.co.uk/2012/04/10-things-to-do-after-installing-ubuntu-12-04/](http://www.omgubuntu.co.uk/2012/04/10-things-to-do-after-installing-ubuntu-12-04/)
    
examples for 11.10 & 12.04
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)

       # for gnome2 prior to 12.04
sudo apt-get install gnome-session-fallback
# this is same as fallback but based on gnome3 for 12.04 or later
sudo apt-get install gnome-panel

---

### Post by darkod on 2012-12-15
I wouldn't say it's by design because on my computer both in 11.10 and 12.04 the usb drives show as icon in Unity.

I do clean installs, not upgrades, but if it's by design it wouldn't auto mount usb drives even in a clean install.

I don't know how exactly to help you with troubleshooting but it's not by design. Maybe something went wrong during both upgrades.

---

### Post by Engineeringtech on 2012-12-15
I never said anything in my post about a virtual installation.   My machines have been triple boot (DOS, Windows and Ubuntu) since I first set them up.   Grub (or is it Grub2 now?) handles booting the Os's.    DOS, Windows, and Ubuntu all boot fine on both machines.  Windows didn't have any problem identifying and mounting my data partitions, thumbdrives and inserted optical media.  

As I also already said in my post, the drive partitions no longer appear on the desktop, in the launcher, OR in Nautilus.  Nor do thumb drives or optical media mount in any of those locations when they are inserted.   That is what I mean by " lost".  I don't have access to them!    What else would I mean by "lost"?  

Now I also don't know why anyone would say I should not expect them to be available/ mounted.      If the partitions were available in 11.04, and all previous versions I have used, going back to 9.04,  wouldn't they still be available under 11.10?   All  I had to do was go up to the "Places" menu to find them.   As I selected them, they appeared (mounted?) on the desktop.   

I find it hard to believe my upgrades of two completely  pieces of hardware could have both gone wrong in the same exact way.  It's too easy to just say, "start over", or "to a fresh install".

---

### Post by darkod on 2012-12-15
Just in case, can you post the output of:
```
sudo parted -l
```

Also, to make sure any usb drive is recognized at all, you can run the parted command before and after you plug it in. That would be one test to see if the usb ports are working correctly under ubuntu.

Even if the usb ports are not working, that would not explain why partitions on the internal diks don't appear in Nautilus under Devices. Can you post a screenshot of Nautilus?

---

### Post by Engineeringtech on 2012-12-15
[QUOTE=darkod;12406410]Just in case, can you post the output of:
```
sudo parted -l
```Also, to make sure any usb drive is recognized at all, you can run the parted command before and after you plug it in. That would be one test to see if the usb ports are working correctly under ubuntu.

Even if the usb ports are not working, that would not explain why partitions on the internal diks don't appear in Nautilus under Devices. Can you post a screenshot of Nautilus?[/QUOTE

Took what seemed like FOREVER to get a response from "sudo parted -l"

I couldn't figure out how to insert screenshot here.  So I attached the files:

---

### Post by darkod on 2012-12-15
Does that partition list look correct to you? You have one fat16 and few fat32 partitions. You said you have dos, windows and ubuntu.

It's very rare not to have any ntfs partition. Even the now ancient XP was running on ntfs instead of fat32.

Do you really have your disk layout as it showed it, or it suffered some corruption maybe?

Waiting a long time to display the parted results usually means either a corruption or a failing hdd. Unfortunately I can't offer any evidence for that, just a huntch. I have a couple of failed hdds that initially show as normal, but as soon as you try anything, like printing the partitions list with parted, it never finishes. It just gets blocked.

As you can notice comparing the screenshots, after connecting a usb drive it didn't show at all. It doesn't even recognize it.

---

### Post by oldfred on 2012-12-15
Does gparted show partitions and do any have little yellow or red icons. If you click on icon it may tell what issue is. But it probably means you need to run chkdsk from Windows on those partitions.

---

### Post by Engineeringtech on 2012-12-15
> **darkod said:**
> Does that partition list look correct to you? You have one fat16 and few fat32 partitions. You said you have dos, windows and ubuntu.

It's very rare not to have any ntfs partition. Even the now ancient XP was running on ntfs instead of fat32.

Do you really have your disk layout as it showed it, or it suffered some corruption maybe?

Waiting a long time to display the parted results usually means either a corruption or a failing hdd. Unfortunately I can't offer any evidence for that, just a huntch. I have a couple of failed hdds that initially show as normal, but as soon as you try anything, like printing the partitions list with parted, it never finishes. It just gets blocked.

As you can notice comparing the screenshots, after connecting a usb drive it didn't show at all. It doesn't even recognize it.

This is my laptop's partition map.   My desktop partition map is near identical excepting it is a 500 MB drive instead of 80 MB.     There is nothing unusual about using FAT32 for  Windows.  NTFS may be the default file system selected by the Windows installer, and supposedly more secure than FAT32, but FAT32 is a valid option, and generally acknowledged to be much faster than NTFS.  That is why I have used it on numerous systems.  However I am using NTFS on my desktop for both the Windows boot drive, and the Data partition, and the desktop suffers from the same exact problem (can't access the partitions, thumb drives, and optical media from Ubuntu).  

Incidentally, this partition map is the same partition map I've used on both laptop, and deskstop, for 6 years and 3 years respectively.   I do some engineering work in DOS and have a CAD program which only runs under Windows.       I didn't have any problem doing a GPARTED scan of my drives before the Ubuntu upgrade.   And I haven't had any indications of pending hard drive failure  on either machine.   This is the 3rd hard drive I have had in my laptop.    I've had two hard drives in the desktop.   If I even see the slightest indication of file corruption I go looking for a replacement.

Anyway, I am doubting this has anything to do with the problem, because my optical media and USB drives don't show up in the launcher, desktop, or Nautilus either.  Optical media and USB drives always appeared on the desktops BEFORE  I upgraded both machines to 11.10.    I know they are functioning properly, because I can  pop a DVD movie in one of the opticals on the desktop, open VLC player, and tell it to run the movie on /dev/dvd1.   That works just fine.  So the drives and partitions are there, it's just that Ubuntu is hiding them from me.

---

### Post by oldfred on 2012-12-15
Several years ago I had XP working from sda1. Then when working on my new sdc drive, gparted would stall, and only after about 10 minutes show only sdb & sdc. I ended up running chkdsk on sda1. XP booted faster and gparted worked again. It seems now the NTFS drivers do show the partitions but may show errors now in gparted. I think it is the same for FAT32.

Part of the reason FAT32 is faster is that it has no journal, so recovery takes longer and is less likely in case of partition issues, particularly power failure or abnormal shutdowns. FAT32 also has a maximum file size of 4GB.

---

### Post by Engineeringtech on 2012-12-17
> **oldfred said:**
> Several years ago I had XP working from sda1. Then when working on my new sdc drive, gparted would stall, and only after about 10 minutes show only sdb & sdc. I ended up running chkdsk on sda1. XP booted faster and gparted worked again. It seems now the NTFS drivers do show the partitions but may show errors now in gparted. I think it is the same for FAT32.

Part of the reason FAT32 is faster is that it has no journal, so recovery takes longer and is less likely in case of partition issues, particularly power failure or abnormal shutdowns. FAT32 also has a maximum file size of 4GB.

Thanks Oldfred.  I will try running chkdsk on SDA1.  Do you think that once I do this, I will again see partitions in the Launcher or Nautilus?

JC

---

### Post by oldfred on 2012-12-17
Do not know. 

But chkdsk flags or hibernation flags are some of the more common reasons for Linux not mounting a Windows formatted partition. That is to prevent damage that then could not be fixed by chkdsk.

---

### Post by Engineeringtech on 2012-12-27
> **oldfred said:**
> Do not know. 

But chkdsk flags or hibernation flags are some of the more common reasons for Linux not mounting a Windows formatted partition. That is to prevent damage that then could not be fixed by chkdsk.

Oldfred,

What's a chkdsk or  hibernation flag?  Is there a way to remove them?  And after you remove the flag, how do you direct Linux to examine the partitions and mount the ones which can be mounted?

---

### Post by oldfred on 2012-12-27
If a partition needs chkdsk, then a flag is set. Linux will not open it to prevent additional damage. When the flag is set, Windows should run chkdsk automatically but may not. Then you have to run it manually.

The same with hibernation. If Linux sees the hibernation flag it should not write to it, but we have seen several posts where users write into a hibernated file system and corrupt it. Again chkdsk is required. 

But Windows chkdsk may not alway resolve all issues, so good backups are always the best solution. And the same applies to Linux formatted partitions also.

---

### Post by BertN45 on 2012-12-27
> **Engineeringtech said:**
> Oldfred,

What's a chkdsk or  hibernation flag?  Is there a way to remove them?  And after you remove the flag, how do you direct Linux to examine the partitions and mount the ones which can be mounted?
Chkdsk flag you can remove by running chkdsk in Windows or Dos. The hibernate flag you could remove by shutting Windows down instead of hybernating it. If you always hybernate windows, try shutting it down.

If you were using hibernate for Windows (default behavior since Vista), the newer versions of Ubuntu/Linux kernel refuse to mount the involved windows partition(s). See [http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

In that case you are right, you don't see the FAT partitions by design to avoid potential corruption

---

### Post by Elmer Fudd on 2012-12-28
For what it's worth..
Found my partions and external devices by opening Nautilus and selecting the "GO" menu item and then "Computer".  Everthing then showed up in the right panel. I miss the Places menu as well.

Now Running:
Sony F-series Laptop
Release 12.04 32-bit
Kernel 3.2.0-35 gen-pae
GNOME 3.4.2

---

### Post by Engineeringtech on 2012-12-29
> **Elmer Fudd said:**
> For what it's worth..
Found my partions and external devices by opening Nautilus and selecting the "GO" menu item and then "Computer".  Everthing then showed up in the right panel. I miss the Places menu as well.

Now Running:
Sony F-series Laptop
Release 12.04 32-bit
Kernel 3.2.0-35 gen-pae
GNOME 3.4.2


THANK YOU!   Your post finally told me how to locate my drive partitions.   I don't know why the people who created Ubuntu chose to hide them from users, or why other people in this forum couldn't help me find them.    I've been following instructions about editing FSTAB, and running CHKDSK from Windows, and nothing has worked.

Unfortunately, this great advice has not resolved the issues with my external drives (USB and Firewire) or optical drives.  (Inaccessible)  So I will mark this thread solved, and follow through with my intent to leave Ubuntu.  (I had just announced this in another thread.)  

I thank everyone who helped me, or tried to help me.

---

### Post by BertN45 on 2012-12-29
Well probably you also could find them by selecting View -> Sidebar -> Places and there should also your CD/DVD and USB sticks/disks appear, if they are used.

By the way there is a program ubuntu-tweak that allows you to have those things displayed at the desktop again.

---

