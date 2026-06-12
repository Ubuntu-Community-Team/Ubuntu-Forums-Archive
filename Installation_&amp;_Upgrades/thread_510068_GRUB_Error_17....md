---
title: "GRUB Error 17..."
date: 2007-07-26
forum: Installation &amp; Upgrades
---

### Post by Nazaiaow on 2007-07-26
Hello, I'm new to this forum and to Ubuntu (and new to Linux), I just installed Ubuntu, everything went perfectly well, rebooted the system and then I got "Grub Error 17" (It only said Error 17, no additional information)... I made a Super Grub disk, and tried to fix the problem (automatically), that didn't work.
Windows booted correctly from the Super Grub disk, but when I tried to use the option "Boot GNU/ Linux direct" I only got a bunch of errors and "SDG did NOT do it" or something.
When starting up the Live CD and looking at the Ubuntu partition it looked fine, but I couldn't change "menu.lst" because that's impossible with the live CD. (I wanted to change "boot" with the Windows partition into "bootnoverify".)

My question is: How do I get Grub/Ubuntu/Windows to boot correctly? And how can I edit "menu.lst" without being in Ubuntu?

My Hard Disk looks like this:
Windows
Documents
Ubuntu
SWAP

Thanks already for your time and help:p

---

### Post by MQMike on 2007-07-26
You have to re-install GRUB to the MBR of the Ubuntu drive.

I have a How-To on this:
How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

(BTW, You CAN do this and edit Ubuntu from the Live CD – see the How-To.)

First, you get into Ubuntu (Live CD), get a Terminal, get a GRUB prompt (sudo grub), and at that GRUB prompt, grub>, you re-install GRUB:

grub> root (hd0, 2)      #Ubuntu is in (hd0, 2), right?
grub> setup (hd0)
grub> quit
$ exit

Note:  (hd0, 2) is the first hard drive (hd0), the third partition (that’s the “2”).
(GRUB, the bootloader, starts numbering hard drives and partitions from zero.)

Re-boot to see what happens now.

Next, get into Ubuntu (Live Cd or otherwise) and edit the boot menu (/boot/grub/menu.lst) with root privileges and File-Save, File-Exit when you are done editing. Edit menu.lst to include a valid entry for Windows.

title Windows XP
rootnoverify (hd0, 0)   #Question: where is Windows exactly?
makeactive
chainloader +1

Is Windows on your hard drive, in the first partition?  If so, that is (hd0, 0).

Re-boot to test it.
(All details are in the How-To. The posts following the first post have other techniques, such as changing the default OS, etc.)

(Note:  for Ubuntu, at the command line, to get and edit menu.lst, you use
sudo gedit /boot/grub/menu.lst;
in Kubuntu, it is a bit different.
Just keep this note handy if you need it, but you may not need it.)

---

### Post by Nazaiaow on 2007-07-26
hd0,0 -> Windows (C: )
hd0,1 -> Documents (D: )
hd0,2 -> Ubuntu
hd0,3 -> SWAP

After the first part of what you told me nothing happens, I get the same Error 17, but could you explain the second part in a bit more detail please, I tried to put the things you said in Ubuntu Terminal, but it didn't work, also I don't know how to get into the "boot/grub/menu.lst" of my Ubuntu partition via the Live CD... I tried this:
sudo mkdir /media/sda3 (which made a directory on the Live CD, I think that shouldn't happen...)
sudo mount /dev/sda3 (I got an error message over there that it couldn't be found)
(The rest what I'm going to type here I didn't do due to the error messages)
cd /media/sda3
gedit /boot/grub/menu.lst
sudo unmount /media/sda3
exit

So, could you please explain in detail how it should be done, as I am a total newbie at this...
But thanks for your help anyway:P

---

### Post by confused57 on 2007-07-26
> **Nazaiaow said:**
> hd0,0 -> Windows (C: )
hd0,1 -> Documents (D: )
hd0,2 -> Ubuntu
hd0,3 -> SWAP

After the first part of what you told me nothing happens, I get the same Error 17, but could you explain the second part in a bit more detail please, I tried to put the things you said in Ubuntu Terminal, but it didn't work, also I don't know how to get into the "boot/grub/menu.lst" of my Ubuntu partition via the Live CD... I tried this:
sudo mkdir /media/sda3 (which made a directory on the Live CD, I think that shouldn't happen...)
sudo mount /dev/sda3 (I got an error message over there that it couldn't be found)
(The rest what I'm going to type here I didn't do due to the error messages)
cd /media/sda3
gedit /boot/grub/menu.lst
sudo unmount /media/sda3
exit

So, could you please explain in detail how it should be done, as I am a total newbie at this...
But thanks for your help anyway:P

You need to specify the fs type to mount your root partition:
```
sudo mkdir /media/sda3
sudo mount -t ext3 /dev/sda3 /media/sda3
gksudo gedit /media/sda3/boot/grub/menu.lst
```

You might want to post the output of your menu.lst and the output of this:
```
sudo fdisk -l
```
-l is a lowercase "L"

Here are some possible solutions for grub error 17:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)

---

### Post by MQMike on 2007-07-26
Yes, what confised57 said.

And the GRUB How-To I mentioned gives the step-by-step, although most of that is in my post.
Sorry, short of time here and just checking in.  Yours looks like a straightforward setup, so I'm sure the basic GRUB methods will work (I do it all the time).  Just be patient and try the How-To, noting what has been said so far.

---

### Post by MQMike on 2007-07-26
If you reinstall GRUB, root - setup - quit, you won't need the live CD to edit menu.lst.

---

### Post by Nazaiaow on 2007-07-26
> **confused57 said:**
> 
You might want to post the output of your menu.lst and the output of this:
```
sudo fdisk -l
```
-l is a lowercase "L"


sudo fdisk -l returns this:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device       | Boot | Start    | End    | Blocks           | Id  | System
/dev/sda1 | *       | 1         | 2611   | 20971408+  | 7   | HPFS / NTFS
Partition 1 does not end on cylinder limit
/dev/sda2 |          |  2611  | 16716 | 113294160   | 7   | HPFS / NTFS
Partition 2 does not end on cylinder limit
/dev/sda3 |          | 16717 | 19330 | 20996955     | 83 | Linux
/dev/sda4 |          | 19331 | 19457 | 1020127+    | 82  | Linux swap / Solaris
```

I put the pipes | in between to make it a bit clearer, I had to type it over because I don't have internet access on my Ubuntu Live CD

---

### Post by confused57 on 2007-07-26
Since you're not getting a grub boot menu, it's possible you might need to check your hard drive settings in bios:
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

According to your fdisk -l, your root partitions is (hd0,2), you might want to check your /boot/grub/menu.lst to see if that's what your root is, e.g. "root (hd0,2)".

You can also use SGD to restore your Window's IPL to the mbr, I think the option is something like "Fix boot of Windows"...you could at least boot into Windows without using SGD and you could still troubleshoot your Ubuntu install.  If a bios setting or root designation in grub is the problem, then SGD "should" be able to boot your Ubuntu.

---

### Post by Nazaiaow on 2007-07-26
Well, that is problem number two... SGD isn't able to boot Ubuntu, via "Boot GNU/ Linux"... Then I get Error number 18, I think that is the main problem (I just found out), do you know a solution for that? (My BIOS dates back to 2000, and the support site of Compaq (Now HP) isn't able to find my computer...) When I try to use "Boot GNU/Linux Directly" I get a 15 Error...

Still, just to let you know my gratitude, thanks for you very quick responses and superb help :)

P.S. confused57, my BIOS doesn't look at all like the one in that topic, it does not feature CMOS buttons and it's all Drop Down menu based

---

### Post by confused57 on 2007-07-26
> **Nazaiaow said:**
> Well, that is problem number two... SGD isn't able to boot Ubuntu, via "Boot GNU/ Linux"... Then I get Error number 18, I think that is the main problem (I just found out), do you know a solution for that? (My BIOS dates back to 2000, and the support site of Compaq (Now HP) isn't able to find my computer...) When I try to use "Boot GNU/Linux Directly" I get a 15 Error...

Still, just to let you know my gratitude, thanks for you very quick responses and superb help :)

P.S. confused57, my BIOS doesn't look at all like the one in that topic, it does not feature CMOS buttons and it's all Drop Down menu based

I would tend to believe the grub error 18 reported by SGD is the actual problem, here's some possible solutions for error 18:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)
I have seen this before, grub reported error 17, SGD showed error 18, which was the problem.  First of all, I would recommend that your restore Window's IPL to the mbr, using SGD.

The solution most recommended is setting up a separate /boot partition at the beginning of the hard drive, but you might want to read through some of the other solutions offered in the link. A bios update might work, but it can render your pc unusable if done incorrectly.  I don't know what your 2nd NTFS partition is, but Ubuntu might boot if it's located immediately after Windows on your 1st partition....I really don't feel qualified to give you specific partitioning advice, but there are numerous people on the forum who probably can give you instructions based on their experiences.   
If you don't get anymore replies here, you might want to start a new, descriptive thread title for  grub error 18.  
Good luck with it, I'll post back if I can think of something else for you to try.

Added:  A second hard disk to install Ubuntu on would a viable alternative...that way you wouldn't risk rendering your Window's install unbootable.

---

### Post by Nazaiaow on 2007-07-26
I still have 2 20 GB Hard Disks lying around here, I'll go test drive with those,

Thank you very much for your help:)

---

### Post by MQMike on 2007-07-26
to respond now to your request (I just returned),

First, you get into Ubuntu (Live CD), 
open a Terminal (find that under System or Admnistration?), 
at the prompt, type
sudo grub,  wait awhile,
and at that GRUB prompt, grub>, you re-install GRUB by typing the following commands, pressing Enter after each one:

root (hd0, 2)      #Ubuntu is in (hd0, 2), right?
setup (hd0)
quit
$ exit

Note: (hd0, 2) is the first hard drive (hd0), the third partition (that’s the “2”).
(GRUB, the bootloader, starts numbering hard drives and partitions from zero.)

Re-boot to see what happens now.  That should give you a boot menu from which you can choose Ubuntu.

Once there in Ubuntu, open your file manager (Commander? – sorry, I’m a Kubuntu-guy)
Type in the top location window/field
/boot/grub
Then locate menu.lst in the files that appear.
Right click on menu.lst,
Edit as Root,
Give your password.
Now edit the Windows boot entry to be as I typed in my post above.
Then
File – Save
File – Close
Close out all windows,
Re-boot to test it.

Unless something is broken (corrupted Ubuntu CD?), this will work.

---

### Post by Nazaiaow on 2007-07-26
I'd like to thank you for your help, but the problem is solved (just a moment ago) I'm now dual booting from two hard drives and it works perfectly :) , but, again, thank you very much for your help

---

### Post by bobjo on 2007-07-26
I realize that this may not be your problem, 
Recently the error 17 came up when I restarted from Windows to Linux and after searching this group I found that one user got rid of the error by unplugging his USB mounted printer.
On checking my machine I found that I had left a USB flash drive in, which I was using in Windows, I removed the Flash Drive and the error no longer appeared and all was well   
Check your USB's!!!!!

Regards
BobJ

---

