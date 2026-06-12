---
title: "Linux insatlled on dell mini 1012 without bootloader"
date: 2011-08-30
forum: Installation &amp; Upgrades
---

### Post by fifa20007 on 2011-08-30
Hi, I tried to install ubuntu and opensuse on my dell mini 1012,
but each time , it failed to install bootloader ( & initrd or sth like this i guess) , I installed "boot repair" and  "boot manager" and "startup manager" too but they didn't repair my trouble.
My hard drive is empty and no other os is installed on it.
Used gparted to format my hard too.
Used two methods to write image on two different flash memory.
first method : using mac terminal, didn't work (flash was unbootable)
> Mac

We would encourage Mac users to download Ubuntu Desktop Edition by burning a CD for the time being. But if you would prefer to use a USB, please follow the instructions below.
 
Note: this procedure requires an .img file that you will be required to create from the .iso file you download.
 
TIP: Drag and Drop a file from Finder to Terminal to 'paste' the full path without typing and risking type errors.
 
Download the desired file
Open the Terminal (in /Applications/Utilities/ or query Terminal in Spotlight)
Convert the .iso file to .img using the convert option of hdiutil (e.g., hdiutil convert -format UDRW -o ~/path/to/target.img ~/path/to/ubuntu.iso)
Note: OS X tends to put the .dmg ending on the output file automatically.
Run diskutil list to get the current list of devices
Insert your flash media
Run diskutil list again and determine the device node assigned to your flash media (e.g. /dev/disk2)
Run diskutil unmountDisk /dev/diskN (replace N with the disk number from the last command; in the previous example, N would be 2)
Execute sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m (replace /path/to/downloaded.img with the path where the image file is located; for example, ./ubuntu.img or ./ubuntu.dmg).
Using /dev/rdisk instead of /dev/disk may be faster.
If you see the error dd: Invalid number '1m', you are using GNU dd. Use the same command but replace bs=1m with bs=1M.
If you see the error dd: /dev/diskN: Resource busy, make sure the disk is not in use. Start the 'Disk Utility.app' and unmount (don't eject) the drive.
Run diskutil eject /dev/diskN and remove your flash media when the command completes
Restart your Mac and press alt while the Mac is restarting to choose the USB-Stick
The second method in windows and using "universal USB installer" app (worked but didn't install bootloader)
> Windows

Insert a USB stick with at least 2GB of free space
Download the Universal USB Installer
Click 'Run' when prompted

If the security dialog appears, confirm by clicking 'Run'

Read the licence agreement and choose 'I Agree' to continue

Select Ubuntu Desktop Edition from the dropdown list

Click 'Browse' and open the downloaded ISO file
 
Choose the USB drive and click 'Create'

 
none of them insatlled a bootloader (like grub or lilo ) on my dell mini , I tried to change boot orders => didn't work .
tried to disable booting from other things => didn't work.
tried to install grub from terminal => didn't work.
in each boot my dell mini gets into network booting.
It is going to craze me.
pls help.
kthanks.

---

### Post by snowpine on 2011-08-30
Welcome to the forums!

I think you are missing a step. :) If all you've done is prepare an Ubuntu Live USB, then you haven't yet "installed" Ubuntu, and it's normal not to have a bootloader.

Try following these easy 1-2-3-4 instructions. It sounds like you are still at Step 2 and haven't done Step 3 yet, is that correct?

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by fifa20007 on 2011-08-31
> **snowpine said:**
> Welcome to the forums!

I think you are missing a step. :) If all you've done is prepare an Ubuntu Live USB, then you haven't yet "installed" Ubuntu, and it's normal not to have a bootloader.

Try following these easy 1-2-3-4 instructions. It sounds like you are still at Step 2 and haven't done Step 3 yet, is that correct?

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
installed ubuntu (4 times ) and opensuse (1 time).
but no bootloader insatlled.
Thanks for your reply.

---

### Post by fifa20007 on 2011-09-01
Any reply would be helpfiul.

---

### Post by Hakunka-Matata on 2011-09-01
can you boot into the liveCD and chose "try ubuntu without installing"?  Can you boot the machine to any OS, to examine what the status/situation is?

---

### Post by sidzen on 2011-09-01
IME, netbooks are tricky.  I'd start with a zero-wiped hdd and go with lubuntu or (at most) [URL="http://linux.softpedia.com/dyn-postdownload.php?p=53015&t=0&i=6"]xubuntu 10.04
[/URL]

---

### Post by fifa20007 on 2011-09-01
> **sidzen said:**
> IME, netbooks are tricky.  I'd start with a zero-wiped hdd and go with lubuntu or (at most) [URL="http://linux.softpedia.com/dyn-postdownload.php?p=53015&t=0&i=6"]xubuntu 10.04
[/URL]

> **Hakunka-Matata said:**
> can you boot into the liveCD and chose "try ubuntu without installing"?  Can you boot the machine to any OS, to examine what the status/situation is?

@sidzen thanks a lot for your answer, but I don't want to install other distributions (but if didn't fixed this problem i should do!)
 
@Hakunka-Mateta I don't have portable cd-driver but i believe it could boot up from a cd and do it however I can choose the "try ubuntu without installing" option with usb too. (I'm posting using live ubuntu from the usb on my netbook right now).
Yes , I had hackintosh and windows on it but wiped them.(and don't want to install any of them again because I have another pc that has them).
and i didn't understand your mean of "status/situation". Would you explain it?
Thanks a lot.
Regards
pls reply .

---

### Post by Hakunka-Matata on 2011-09-01
> **fifa20007 said:**
> @sidzen thanks a lot for your answer, but I don't want to install other distributions (but if didn't fixed this problem i should do!)
 
@Hakunka-Mateta I don't have portable cd-driver but i believe it could boot up from a cd and do it however I can choose the "try ubuntu without installing" option with usb too. [COLOR=Red](I'm posting using live ubuntu from the usb on my netbook right now).[/COLOR]
Yes , I had hackintosh and windows on it but wiped them.(and don't want to install any of them again because I have another pc that has them).
and i didn't understand your mean of "status/situation". Would you explain it?
Thanks a lot.
Regards
pls reply .

 [COLOR=Red](I'm posting using live ubuntu from the usb on my netbook right now).[/COLOR] 
[COLOR=Black]Since you are already using Ubuntu by way of having booted into the liveCD/USB (it's the same thing, CD or USB) then it would seem you're in good shape to continue on by installing ubuntu to your hard disk. 
[/COLOR]
[LIST]
[*][COLOR=Black] You should have an Icon on your desktop labeled 'install', no?[/COLOR]
[*][COLOR=Black]by 'situation/status', I mean  the state of your install, is it installed to hard disk? 
[/COLOR]
[*][COLOR=Black]Open a Terminal window and run [/COLOR]```
sudo fdisk -lu"
```  post the output into a new reply between [ code] [ / code] tags.
[*] Click the # icon to insert your code tags around the reply text.
[*]What version of ubuntu are you using?, 10.04, 10.10, 11.04?
[*] Knowing which version you are using makes it easier to explain how to start certain programs, because the default desktop layout is different for each version/release.
[*]Also run the program 'gparted', which will show graphically how your hard drive is formatted.  post a 'screenshot' of that graphic so we can further suggest how to proceed.
[/LIST]
 I've got to leave now for all day trip, will get back to this upon return.  Good Luck

---

### Post by fifa20007 on 2011-09-02
> **Hakunka-Matata said:**
> [COLOR=Red](I'm posting using live ubuntu from the usb on my netbook right now).[/COLOR] 
[COLOR=Black]Since you are already using Ubuntu by way of having booted into the liveCD/USB (it's the same thing, CD or USB) then it would seem you're in good shape to continue on by installing ubuntu to your hard disk. 
[/COLOR]
[LIST]
[*][COLOR=Black] You should have an Icon on your desktop labeled 'install', no?[/COLOR]
[*][COLOR=Black]by 'situation/status', I mean  the state of your install, is it installed to hard disk? 
[/COLOR]
[*][COLOR=Black]Open a Terminal window and run [/COLOR]```
sudo fdisk -lu"
```  post the output into a new reply between [ code] [ / code] tags.
[*] Click the # icon to insert your code tags around the reply text.
[*]What version of ubuntu are you using?, 10.04, 10.10, 11.04?
[*] Knowing which version you are using makes it easier to explain how to start certain programs, because the default desktop layout is different for each version/release.
[*]Also run the program 'gparted', which will show graphically how your hard drive is formatted.  post a 'screenshot' of that graphic so we can further suggest how to proceed.
[/LIST]
 I've got to leave now for all day trip, will get back to this upon return.  Good Luck

1- yes I have. I know what are live Ubuntu's characteristics ;) .
2- no, It is not installed but It was.(i'm going to install it again).
3- here you are:
```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e50d3

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 8075 MB, 8075140608 bytes
249 heads, 62 sectors/track, 1021 cylinders, total 15771759 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?  3224498923  3657370039   216435558+   7  HPFS/NTFS
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(187, 180, 14) logical=(208867, 164, 10)
Partition 1 has different physical/logical endings:
     phys=(784, 0, 13) logical=(236906, 245, 22)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?  3272020941   930513678   976730017   16  Hidden FAT16
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(906, 235, 61) logical=(211945, 226, 20)
Partition 2 has different physical/logical endings:
     phys=(262, 116, 59) logical=(60274, 59, 9)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?           0           0           0   6f  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(370, 101, 50) logical=(0, 0, 1)
Partition 3 has different physical/logical endings:
     phys=(10, 114, 13) logical=(278207, 123, 4)
Partition 3 does not end on cylinder boundary.
/dev/sdb4        50200576   974536369   462167897    0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(3251, 187, 45)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(63125, 203, 34)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```
4- I'm using 11.04 natty narwhal.
5- here is the screenshot.
[IMG]http://ubuntuone.com/2nOUV9VAbSWDq25HWKYwsw[/IMG]
and thanks alot for your helps.

---

### Post by fifa20007 on 2011-09-02
Oh no. got a new error:
[IMG]http://ubuntuone.com/0SIhyQH42Y19PJq0YUjkJX[/IMG]

---

### Post by fifa20007 on 2011-09-02
any solution for the error?

---

### Post by Hakunka-Matata on 2011-09-02
do you have a RAID array?  GParted's picture is indicating that as a possibility, and read the following thread.
look at this thread, it's similar to your situation; [http://ubuntuforums.org/showthread.php?t=1535704](http://ubuntuforums.org/showthread.php?t=1535704)

---

### Post by fifa20007 on 2011-09-02
no, they're solution was updating ubiquity but mine is latest version
any help?
kthanks

---

### Post by Hakunka-Matata on 2011-09-02
[LIST]
[*]Everything we've seen so far is saying sda is empty, no partition table, no nothing.
[*]GParted:  have you tried creating a new partition table using gparted?
[*] There's nothing important on the drive, right?
[LIST]
[*]New Partition table will wipe out what ever's there if anything.
[*]It could be recovered right away, (before the disk is written too a lot), by another program.
[/LIST]
[*]Try to create a New msdos partition table, your space should appear as unallocated if that suceeds.
[/LIST]

---

### Post by fifa20007 on 2011-09-03
1- no I didn't try.
2- right.
3- succeeded.
what's the next step?

---

### Post by fifa20007 on 2011-09-03
tried to install it again. ubiquity error 10 : fixed. but the "The ext4 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed." error is still in the installation routine.

---

### Post by Hakunka-Matata on 2011-09-03
Alright, good.

[LIST=1]
[*] create four partitions.  Manually, using gparted again
[*]1st, Logical, WRONG should have said PRIMARY, type Extended, size Big, use at least 50% of drive, or 100GB min.
[LIST=1]
[*]All the following partitions get created in the unallocated space within the Extended partiton
[/LIST]
 
[*]2nd.Logical,  / (root) Type Linux (83) 10-20GB
[*]3rd. Logical  /home Type Linux (83) big, where all your data goes 100GB?
[*]4rd. Logical swap 2GB
[/LIST]
**EDIT:  When you're done post the output of ```
sudo fdisk -lu
```**

---

### Post by fifa20007 on 2011-09-03
> **Hakunka-Matata said:**
> Alright, good.

[LIST=1]
[*] create four partitions.  Manually, using gparted again
[*]1st, Logical, type Extended, size Big, use at least 50% of drive, or 100GB min.
[LIST=1]
[*]All the following partitions get created in the unallocated space within the Extended partiton
[/LIST]
 
[*]2nd.Logical,  / (root) Type Linux (83) 10-20GB
[*]3rd. Logical  /home Type Linux (83) big, where all your data goes 100GB?
[*]4rd. Logical swap 2GB
[/LIST]
**EDIT:  When you're done post the output of ```
sudo fdisk -lu
```**
creating logical partition is disabled dude.

---

### Post by Hakunka-Matata on 2011-09-03
You first have to create the Extended partition.  Logical partition only exist inside extended

MY MISTAKE< EXTENDED will be a PRIMARY, sorry

---

### Post by fifa20007 on 2011-09-03
> **Hakunka-Matata said:**
> You first have to create the Extended partition.  Logical partition only exist inside extended
alright.

---

### Post by fifa20007 on 2011-09-03
what type of ext should it be? 2 or3 or 4?

---

### Post by Hakunka-Matata on 2011-09-03
Ext 4 for / and /home

---

### Post by Hakunka-Matata on 2011-09-03
This is a little 80GB on this machine I'm typing in.
as an example

---

### Post by fifa20007 on 2011-09-03
unable to create primary :
[IMG]http://i.imgur.com/fnZEW.png[/IMG]

---

### Post by Hakunka-Matata on 2011-09-03
good, 
execute, apply, hit green check mark:  to apply the new settings you've asked it to make.  have to apply those changes first, then make next partition.

I have a hard time remembering to hit the green check too!

---

### Post by fifa20007 on 2011-09-03
I've already done it . and that picture was captured while I applied the changes.
also tried to create a logical one .
got this error:
[HTML]<!DOCTYPE html PUBLIC '-//W3C//DTD XHTML 1.0 Transitional//EN' 'http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd'>
<html xmlns='http://www.w3.org/1999/xhtml' xml:lang='en-US' lang='en-US'>
<head>
<meta http-equiv='Content-Type' content='text/html;charset=utf-8' />
<title>GParted Details</title>
</head>
<body>
<p>GParted 0.7.0 --enable-libparted-dmraid</p>
<p>Libparted 2.3</p>
<table border='0'>
<tr>
<td colspan='2'>
<b>Create Logical Partition #1 (ext4, 116.67 GiB) on /dev/sda</b>&nbsp;&nbsp;00:00:02&nbsp;&nbsp;&nbsp;&nbsp;( ERROR )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
create empty partition&nbsp;&nbsp;00:00:01&nbsp;&nbsp;&nbsp;&nbsp;( SUCCESS )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<i>path: /dev/sda5<br />start: 4096<br />end: 244684799<br />size: 244680704 (116.67 GiB)</i>
</td>
</tr>
</table>
</td>
</tr>
</table>
<table border='0'>
<tr>
<td colspan='2'>
set partition type on /dev/sda5&nbsp;&nbsp;00:00:01&nbsp;&nbsp;&nbsp;&nbsp;( SUCCESS )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<i>new partition type: ext4</i>
</td>
</tr>
</table>
</td>
</tr>
</table>
<table border='0'>
<tr>
<td colspan='2'>
create new ext4 file system&nbsp;&nbsp;00:00:00&nbsp;&nbsp;&nbsp;&nbsp;( ERROR )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<b><i>mkfs.ext4 -j -O extent -L &quot;&quot; /dev/sda5</i></b>
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<i>sh: getcwd() failed: No such file or directory<br />mke2fs 1.41.14 (22-Dec-2010)<br />/dev/sda5 is apparently in use by the system; will not make a filesystem here!<br /></i>
</td>
</tr>
</table>
</td>
</tr>
</table>
</td>
</tr>
</table>
</td>
</tr>
</table>
<p>========================================</p>
</body>
</html>[/HTML]

---

### Post by fifa20007 on 2011-09-03
forgot to say that mt partition scheme is mbr , should it be guid?

---

### Post by Hakunka-Matata on 2011-09-03
> **fifa20007 said:**
> I've already done it . and that picture was captured while I applied the changes.
also tried to create a logical one .
got this error:
[HTML]<!DOCTYPE html PUBLIC '-//W3C//DTD XHTML 1.0 Transitional//EN' 'http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd'>
<html xmlns='http://www.w3.org/1999/xhtml' xml:lang='en-US' lang='en-US'>
<head>
<meta http-equiv='Content-Type' content='text/html;charset=utf-8' />
<title>GParted Details</title>
</head>
<body>
<p>GParted 0.7.0 --enable-libparted-dmraid</p>
<p>Libparted 2.3</p>
<table border='0'>
<tr>
<td colspan='2'>
<b>Create Logical Partition #1 (ext4, 116.67 GiB) on /dev/sda</b>&nbsp;&nbsp;00:00:02&nbsp;&nbsp;&nbsp;&nbsp;( ERROR )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
create empty partition&nbsp;&nbsp;00:00:01&nbsp;&nbsp;&nbsp;&nbsp;( SUCCESS )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<i>path: /dev/sda5<br />start: 4096<br />end: 244684799<br />size: 244680704 (116.67 GiB)</i>
</td>
</tr>
</table>
</td>
</tr>
</table>
<table border='0'>
<tr>
<td colspan='2'>
set partition type on /dev/sda5&nbsp;&nbsp;00:00:01&nbsp;&nbsp;&nbsp;&nbsp;( SUCCESS )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<i>new partition type: ext4</i>
</td>
</tr>
</table>
</td>
</tr>
</table>
<table border='0'>
<tr>
<td colspan='2'>
create new ext4 file system&nbsp;&nbsp;00:00:00&nbsp;&nbsp;&nbsp;&nbsp;( ERROR )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<b><i>mkfs.ext4 -j -O extent -L &quot;&quot; /dev/sda5</i></b>
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<i>sh: getcwd() failed: No such file or directory<br />mke2fs 1.41.14 (22-Dec-2010)<br />/dev/sda5 is apparently in use by the system; will not make a filesystem here!<br /></i>
</td>
</tr>
</table>
</td>
</tr>
</table>
</td>
</tr>
</table>
</td>
</tr>
</table>
<p>========================================</p>
</body>
</html>[/HTML]

Yes, some other program has the disk mounted and locked, it's probably got the "key" picture icon showing in the partition colomn.
close other programs that might be open, update manager, synaptic package manager, disk tools of any sort, ubuntu software center?

---

### Post by fifa20007 on 2011-09-03
> **Hakunka-Matata said:**
> Yes, some other program has the disk mounted and locked, it's probably got the "key" picture icon showing in the partition colomn.
close other programs that might be open, update manager, synaptic package manager, disk tools of any sort, ubuntu software center?
i closed everything(also my internet browser)
got this.
[HTML]<!DOCTYPE html PUBLIC '-//W3C//DTD XHTML 1.0 Transitional//EN' 'http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd'>
<html xmlns='http://www.w3.org/1999/xhtml' xml:lang='en-US' lang='en-US'>
<head>
<meta http-equiv='Content-Type' content='text/html;charset=utf-8' />
<title>GParted Details</title>
</head>
<body>
<p>GParted 0.7.0 --enable-libparted-dmraid</p>
<p>Libparted 2.3</p>
<table border='0'>
<tr>
<td colspan='2'>
<b>Delete Logical Partition (unknown, 116.67 GiB) from /dev/sda</b>&nbsp;&nbsp;00:00:00&nbsp;&nbsp;&nbsp;&nbsp;( SUCCESS )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
calibrate /dev/sda5&nbsp;&nbsp;00:00:00&nbsp;&nbsp;&nbsp;&nbsp;( SUCCESS )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<i>path: /dev/sda5<br />start: 4096<br />end: 244684799<br />size: 244680704 (116.67 GiB)</i>
</td>
</tr>
</table>
</td>
</tr>
</table>
<table border='0'>
<tr>
<td colspan='2'>
delete partition&nbsp;&nbsp;00:00:00&nbsp;&nbsp;&nbsp;&nbsp;( SUCCESS )
</td>
</tr>
</table>
</td>
</tr>
</table>
<p>========================================</p>
<table border='0'>
<tr>
<td colspan='2'>
<b>Create Logical Partition #1 (ext4, 116.67 GiB) on /dev/sda</b>&nbsp;&nbsp;00:00:02&nbsp;&nbsp;&nbsp;&nbsp;( ERROR )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
calibrate New Partition #1&nbsp;&nbsp;00:00:00&nbsp;&nbsp;&nbsp;&nbsp;( SUCCESS )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<i>path: /dev/sda-1<br />start: 2111<br />end: 488396799<br />size: 488394689 (232.88 GiB)</i>
</td>
</tr>
</table>
</td>
</tr>
</table>
<table border='0'>
<tr>
<td colspan='2'>
create empty partition&nbsp;&nbsp;00:00:01&nbsp;&nbsp;&nbsp;&nbsp;( SUCCESS )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<i>path: /dev/sda5<br />start: 16065<br />end: 244686014<br />size: 244669950 (116.67 GiB)</i>
</td>
</tr>
</table>
</td>
</tr>
</table>
<table border='0'>
<tr>
<td colspan='2'>
set partition type on /dev/sda5&nbsp;&nbsp;00:00:01&nbsp;&nbsp;&nbsp;&nbsp;( SUCCESS )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<i>new partition type: ext4</i>
</td>
</tr>
</table>
</td>
</tr>
</table>
<table border='0'>
<tr>
<td colspan='2'>
create new ext4 file system&nbsp;&nbsp;00:00:00&nbsp;&nbsp;&nbsp;&nbsp;( ERROR )
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<b><i>mkfs.ext4 -j -O extent -L &quot;&quot; /dev/sda5</i></b>
</td>
</tr>
<tr>
<td>&nbsp;&nbsp;&nbsp;&nbsp;</td>
<td>
<table border='0'>
<tr>
<td colspan='2'>
<i>sh: getcwd() failed: No such file or directory<br />mke2fs 1.41.14 (22-Dec-2010)<br />/dev/sda5 is apparently in use by the system; will not make a filesystem here!<br /></i>
</td>
</tr>
</table>
</td>
</tr>
</table>
</td>
</tr>
</table>
</td>
</tr>
</table>
<p>========================================</p>
</body>
</html>[/HTML]

---

### Post by Hakunka-Matata on 2011-09-03
> **Hakunka-Matata said:**
> This is a little 80GB on this machine I'm typing in.
as an example

Are you running your machine right now using that disk?, no, you're on liveCD right?

look at my thumbnail again, post# 23.  Does your drive have the 'keys icon" showing in partition column?

---

### Post by fifa20007 on 2011-09-03
> **Hakunka-Matata said:**
> Are you running your machine right now using that disk?, no, you're on liveCD right?

look at my thumbnail again, post# 23.  Does your drive have the 'keys icon" showing in partition column?
yes i'm on live Usb right now . (you saw my partitions , i don't have any os on them).
no i don't have that key icons.
Thanks for your help.

---

### Post by fifa20007 on 2011-09-03
i opened update manager, there are a lot of updates ti install, include a new kernel update , should i update it?

---

### Post by Hakunka-Matata on 2011-09-03
Yes,  If you're on LiveCD they cannot be written to disk, are you running off CD or USB now, the liveCD?

---

### Post by Hakunka-Matata on 2011-09-03
> **fifa20007 said:**
> yes i'm on live Usb right now . ([COLOR=Red]you saw my partitions[/COLOR] , i don't have any os on them).
no i don't have that key icons.
Thanks for your help.

I saw your sda partitions, I don't know if you have other hard drives connected to the machine.
Oh yeah, and I can see from the desktop Icon's you're running off LiveCD, do you have maybe two instances of gparted running?, maybe in a second or third workspace? 
If you are sort of stuck at this point, why not just reboot?  Rebooting doesn't take long on that hardware, or does it?

---

### Post by fifa20007 on 2011-09-03
Usb, and that has a little space to save things. (specified that space using unetbootin )

---

### Post by fifa20007 on 2011-09-03
> **Hakunka-Matata said:**
> I saw your sda partitions, I don't know if you have other hard drives connected to the machine.
i have another , that is my usb .

---

### Post by Hakunka-Matata on 2011-09-03
Your USB LiveCD is running in persistence?, how much space does the partition have?

---

### Post by fifa20007 on 2011-09-03
what do you mean by "persistence" ?
[IMG]http://ubuntuone.com/3BUeBSXtJOgDTCcKI7vAk2[/IMG]

---

### Post by fifa20007 on 2011-09-03
as far as I remember I allocated about 100 (or 500) mb to save things.

---

### Post by Hakunka-Matata on 2011-09-03
> **fifa20007 said:**
> Usb, and that has a little space to save things. (specified that space using [COLOR=Red]unetbootin[/COLOR] )

Persistence, writing the usb disc with persistence allows you to install a complete OS installation on it just as if it were a internal hard drive.  The mode is called persistent, you can make updates to it, everything, just like on your hard drive.  So it's no longer simply an install CD, liveCD.

The latest release of unetbootin-linux-549 has the persistence available, but you have to select it while running the program.

---

### Post by fifa20007 on 2011-09-03
yes , it's running on persistence.
KThanks

---

### Post by fifa20007 on 2011-09-03
and sorry, as i said in the 1st post , i used universal USB installer app, but it had sth like persistence mode too.

---

### Post by fifa20007 on 2011-09-03
so, what to do now?

---

### Post by Hakunka-Matata on 2011-09-03
Get the hard drive formatted and ready to receive that easy install.

---

### Post by Hakunka-Matata on 2011-09-03
```
 sudo fdisk -lu
```

and a graphic of the gparted grahic, like earlier.

---

### Post by fifa20007 on 2011-09-03
what 2 do with the error?

---

### Post by Hakunka-Matata on 2011-09-03
show me the error (no, I'm not from Missouri)

We're troubleshooting, right?  Need to see what is going on,

---

### Post by fifa20007 on 2011-09-03
> **Hakunka-Matata said:**
> show me the error (no, I'm not from Missouri)

We're troubleshooting, right?  Need to see what is going on,
right.
but we didn't fix the last error.
post 28
[http://ubuntuforums.org/showpost.php?p=11214376&postcount=28](http://ubuntuforums.org/showpost.php?p=11214376&postcount=28)

---

### Post by fifa20007 on 2011-09-03
> **Hakunka-Matata said:**
> show me the error (no, I'm not from Missouri)

We're troubleshooting, right?  Need to see what is going on,
i didn't say that you are from Missouri.
???!!!!
(i know what does it mean)

---

### Post by fifa20007 on 2011-09-03
i think i should burn the file on a new usb Or remove the hard disk of my netbook and then assemble it to a notebook and install it. i'm sure that the second method works.

---

### Post by Hakunka-Matata on 2011-09-03
Exactly what is the error you get, where? 
 GParted won't let you Apply settings?

Your liveCD is working fine it sounds like, you can open and run GParted no problem, right?
But when you try to Add or change a partition you get the errors that "/dev/sda5 is apparently is use by the system" CORRECT?


/dev/sda5 is apparently in use by the system

---

### Post by fifa20007 on 2011-09-03
I get this error after applying extended format to entire of the disk when i want to apply primary partition ( as i said it is disabled and i selected logical partition ) type ext4 .
i can't write the error more obvious , that was the output from program.
- yes it works completely.
- CORRECT
Thanks a lot

---

### Post by Hakunka-Matata on 2011-09-03
> **fifa20007 said:**
> I get this error after applying extended format to entire of the disk when i want to[COLOR=Red] apply primary partition[/COLOR] ( as i said it is disabled and i selected logical partition ) type ext4 .
i can't write the error more obvious , that was the output from program.
- yes it works completely.
- CORRECT
Thanks a lot

It's not possible to create a primary partition inside of an Extended partition.  
If you have the Extended partition created, applied, then you create LOGICAL partitions.  
Extended partitions house only logical and swap partitions. **EDIT: let me say it a better way, Extended partitions may not contain a primary partition**

---

### Post by Hakunka-Matata on 2011-09-03
run ```
sudo fdisk -lu
``` and it will show us what has been created, I still don't know because you haven't said if you have any partitions created now?

---

### Post by fifa20007 on 2011-09-03
i did  and got that error

---

### Post by fifa20007 on 2011-09-03
this is the routine :
creating new partition table (msdos) - 
add an extended partition -
create a new ext4 logical partition in extended -
the explained error -
created unknown type partition
the output:
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ee5ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   488396799   244197376    5  Extended
/dev/sda5            4096   244684799   122340352   83  Linux

Disk /dev/sdb: 8075 MB, 8075140608 bytes
249 heads, 62 sectors/track, 1021 cylinders, total 15771759 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?  3224498923  3657370039   216435558+   7  HPFS/NTFS
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(187, 180, 14) logical=(208867, 164, 10)
Partition 1 has different physical/logical endings:
     phys=(784, 0, 13) logical=(236906, 245, 22)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?  3272020941   930513678   976730017   16  Hidden FAT16
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(906, 235, 61) logical=(211945, 226, 20)
Partition 2 has different physical/logical endings:
     phys=(262, 116, 59) logical=(60274, 59, 9)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?           0           0           0   6f  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(370, 101, 50) logical=(0, 0, 1)
Partition 3 has different physical/logical endings:
     phys=(10, 114, 13) logical=(278207, 123, 4)
Partition 3 does not end on cylinder boundary.
/dev/sdb4        50200576   974536369   462167897    0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(3251, 187, 45)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(63125, 203, 34)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

---

### Post by fifa20007 on 2011-09-03
and as i expected . the second method worked .
but it doesn't mean i want to leave this trouble.
I don't leave here till i shout this problem out.
With your helps

---

### Post by Hakunka-Matata on 2011-09-03
> **fifa20007 said:**
> this is the routine : creating new partition table (msdos) -  add an extended partition - create a new ext4 logical partition in extended - the explained error - created unknown type partition the output: ```
Disk /dev/sda: 250.1 GB, 250059350016 bytes 255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x000ee5ca     Device Boot      Start         End      Blocks   Id  System /dev/sda1            2048   488396799   244197376    5  Extended [COLOR="Red"]/dev/sda5            4096   244684799   122340352   83  Linux[/COLOR]  Disk /dev/sdb: 8075 MB, 8075140608 bytes 249 heads, 62 sectors/track, 1021 cylinders, total 15771759 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x20ac7dda  This doesn't look like a partition table Probably you selected the wrong device.     Device Boot      Start         End      Blocks   Id  System /dev/sdb1   ?  3224498923  3657370039   216435558+   7  HPFS/NTFS Partition 1 has different physical/logical beginnings (non-Linux?):      phys=(187, 180, 14) logical=(208867, 164, 10) Partition 1 has different physical/logical endings:      phys=(784, 0, 13) logical=(236906, 245, 22) Partition 1 does not end on cylinder boundary. /dev/sdb2   ?  3272020941   930513678   976730017   16  Hidden FAT16 Partition 2 has different physical/logical beginnings (non-Linux?):      phys=(906, 235, 61) logical=(211945, 226, 20) Partition 2 has different physical/logical endings:      phys=(262, 116, 59) logical=(60274, 59, 9) Partition 2 does not end on cylinder boundary. /dev/sdb3   ?           0           0           0   6f  Unknown Partition 3 has different physical/logical beginnings (non-Linux?):      phys=(370, 101, 50) logical=(0, 0, 1) Partition 3 has different physical/logical endings:      phys=(10, 114, 13) logical=(278207, 123, 4) Partition 3 does not end on cylinder boundary. /dev/sdb4        50200576   974536369   462167897    0  Empty Partition 4 has different physical/logical beginnings (non-Linux?):      phys=(0, 0, 0) logical=(3251, 187, 45) Partition 4 has different physical/logical endings:      phys=(0, 0, 0) logical=(63125, 203, 34) Partition 4 does not end on cylinder boundary.  Partition table entries are not in disk order 
```  
OK, that's great, now we have something to work with.
sda5 is overlapping sda1, see the start and end position of sda5, it's completely contained within sda1, and extended partition.  NO CAN DO, that is the reason for your error.
first, delete sda5
then within the unallocated area beneath sda1, create your logical partitions.

---

### Post by fifa20007 on 2011-09-03
will try it

---

### Post by fifa20007 on 2011-09-03
dude if i delete sda5 we jump back to step 2 of the routine .
also tried without deleting sda5 , while it wanted to create sda6 returned same error

---

### Post by Hakunka-Matata on 2011-09-03
Know what, I'm wrong, it should be ok, sda5 is a logical partition.  If you've already deleted it no problem.  I'd suggest you just create a new **partition table** on the drive, wipe it out completely.  
Then create a big Extended, but leave maybe 50GB unused space in front of it.  
then logical's inside of Extended
logical partitions are always numbered 5 or higher.  sda1 - sda4 numbers are always, primary partitions.  

You can't hurt anything at this point, play with it for a minute or two and create this and that, whatever, then just start over with a new partition table, it takes very little time to actually do it once you're familiar with how it works.  OK?,  If you have the time, take your time now, you'll get it right away and never look back.

---

### Post by fifa20007 on 2011-09-03
OK thanks , so goodbye till tomorrow .
Thanks a lot for your helps.

---

### Post by Hakunka-Matata on 2011-09-03
Good Luck, Salama

---

### Post by fifa20007 on 2011-09-04
OK, the problem was my usb, i created another ubuntu persistence mode usb and did the instruction , got the error :
**Unable to install GRUB in /dev/sda**
Executing 'grub-install /dev/sda' failed

This is fatal error.
please help.
Thanks a lot.

---

### Post by fifa20007 on 2011-09-04
the app that i made the usb with it may be the problem, I'm going to try unetbootin app.

---

### Post by fifa20007 on 2011-09-04
note: i got that fatal error with both of my usb flashes.

---

### Post by Hakunka-Matata on 2011-09-04
> **fifa20007 said:**
> note: i got [COLOR=Red]that fatal error[/COLOR] with both of my usb flashes.

And what is  [COLOR=Red]that fatal error???[/COLOR]

---

### Post by fifa20007 on 2011-09-04
the mentioned error in post #64
any solution?

---

### Post by Hakunka-Matata on 2011-09-04
post output ```
sudo fdisk -lu
```
please

---

### Post by fifa20007 on 2011-09-04
> **Hakunka-Matata said:**
> post output ```
sudo fdisk -lu
```
please
sdd is the mentioned drive , not sda and sdb
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006fed7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   158368769    79184353+  83  Linux
/dev/sda2       158368770   312576704    77103967+   5  Extended
/dev/sda5       158368833   306568394    74099781   83  Linux
/dev/sda6       306568458   312576704     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 16.0 GB, 16001036288 bytes
64 heads, 32 sectors/track, 15259 cylinders, total 31252024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00032657

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    31250431    15625200    c  W95 FAT32 (LBA)

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c130d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048   486322175   243160064   83  Linux
/dev/sdd2       486324222   488396799     1036289    5  Extended
/dev/sdd5       486324224   488396799     1036288   82  Linux swap / Solaris

```

---

### Post by Hakunka-Matata on 2011-09-04
how are you running right now, in liveCD, or booted from a hard drive?
sudo df -h

---

### Post by fifa20007 on 2011-09-04
in livecd (persistence mode)
```
Filesystem            Size  Used Avail Use% Mounted on
aufs                  3.9G  399M  3.3G  11% /
none                  489M  652K  489M   1% /dev
/dev/sda1              15G  5.4G  9.6G  37% /cdrom
/dev/loop0            658M  658M     0 100% /rofs
none                  496M  308K  496M   1% /dev/shm
tmpfs                 496M  8.0K  496M   1% /tmp
none                  496M   96K  496M   1% /var/run
none                  496M     0  496M   0% /var/lock

```
livecd on usb

---

### Post by Hakunka-Matata on 2011-09-04
Let's try reinstalling grub, yeah, one more time.......................

Open Terminal:

```
sudo mount /dev/sda1 /mnt

sudo grub-install --boot-directory=/mnt/boot /dev/sda

Reboot
```

after reboot # Refresh the GRUB 2 menu with sudo update-grub

OK?

---

### Post by fifa20007 on 2011-09-04
I think sda should be changed to sdd , no?

---

### Post by fifa20007 on 2011-09-04
after reboot should i boot in hard drive?

---

### Post by Hakunka-Matata on 2011-09-04
> **fifa20007 said:**
> I think sda should be changed to sdd , no?

Well, sure I guess so, if that is where you installed ubuntu to.

on sda, which partition has ubuntu installed to, sda1 & sda5?, or just sda1?, or just sda5?

on reboot try to start from hard drive.

---

### Post by Hakunka-Matata on 2011-09-04
if you have ubuntu installed on both sda & sdd, and you install Grub to the MBR of both drives, you can then boot from either drive (first drive BIOS) and you can select (via the grub menu) which OS you want to load.

---

### Post by fifa20007 on 2011-09-04
> **Hakunka-Matata said:**
> if you have ubuntu installed on both sda & sdd, and you install Grub to the MBR of both drives, you can then boot from either drive (first drive BIOS) and you can select (via the grub menu) which OS you want to load.
I installed the ubuntu (which we are talking about it) on sdd and sda is another hard drive that has no problem (it is the hard drive of my another pc) , i wrote it in post #70.
i forgot to say that the installation routine didn't finish when i got the fatal error ( it gave me 3 options , 1- retry installing grub / 2- install grub on another place / 3- continue without installing grub / but none of them worked , i mean i clocked on each option several times but nothing happened and the system crashed)

---

### Post by fifa20007 on 2011-09-04
do you know how can i use unetbootin in ubuntu?

---

### Post by Hakunka-Matata on 2011-09-04
ok, let's do the routine again, but with a little bigger hammer this time.

```
*********************ChRoot**********************

sudo fdisk -l

sudo mount /dev/sdXX /mnt

for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done

sudo chroot /mnt

update-grub

grub-install /dev/sdX

grub-install --recheck /dev/sdX

for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done

sudo umount /mnt

sudo reboot
```

[B]tell me if you have any doubts about what drive letters & #s to insert in the sdXY, sdX fields.
and it may be helpful to see a transcript of the Terminal action.  Screenshot is fine if you make it ledgeable.  cheers
[/B]

---

### Post by fifa20007 on 2011-09-04
i don't know to put which sdd partition in sdxx and do this now or after a new install?

---

### Post by Hakunka-Matata on 2011-09-04
you have to do it as you are typing the code into the terminal.

```
sudo mount /dev/sdXX /mnt
```# you type ```
sudo mount /dev/sdd1 /mnt
```is that correct, your Linux system is partition sdd1, correct?  If not, correct it.
# sdd1 has your ubuntu system files loaded in it, correct?  It's your linux OS.
# to see if it worked, look at the directory listing for the /mnt folder, like this:
```
sudo ls /mnt
```

---

### Post by fifa20007 on 2011-09-04
ok thanks,
will be back in 30 mins.

---

### Post by fifa20007 on 2011-09-04
busy day, i think i should do that tomorrow .
sorry

---

### Post by fifa20007 on 2011-09-05
a new problem :(
when i put my hard drive in netbook , it boots into ash (busy box / built in command line )  .
what to do?

---

### Post by fifa20007 on 2011-09-08
Found out sth new :
This  problem is only on my Hitachi hard drive.

---

