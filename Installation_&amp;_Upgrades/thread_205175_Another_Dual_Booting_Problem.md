---
title: "Another Dual Booting Problem"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by mps69 on 2006-06-28
Hi
I’m sure this is not a new problem, but I can’t seem how to fix it.
I’ve been running with the Live CD for a few weeks on a Windows XP Pro PC. Thought the OS was pretty cool and took the plunge last night to install it using a dual booting process.
I’ve backed up all my important data on another drive and installed Acronis OS boot program. I choose this because my wife uses the PC and just wants something nice and simple so she can load up the correct OS, in her case XP. This part installed ok.
I’ve used this tutorial [http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html), which was very simple. I selected to resize my 90gb boot drive down by 30gb for the new OS. All cool so far. This last step is where I think it’s all gone belly up. I choose to reboot the PC but not before trying to eject the Live CD. I couldn’t get it out, so I had to open “home/my computer” and eject from there. The OS just locked up at this point. Nothing would work, so I had to force a switch off. When the PC came back up Acronis failed and I got a message MBR error, press enter to try and find OS. I was then asked to input my floppy disc. I don’t have this, infact I don’t have a floppy drive.
Now I can’t boot the PC to either OS. What I can do is insert the Live CD and I do get back up with that.
What I have done before all this started was backed up my XP OS using DriveImage XML, but I didn’t backup the MBR, mainly cause one I couldn’t get it to work. Yeah I know in hindsight that’s really really dumb!!
Can anyone offer some advice where I can go with this?
Thanks in advance

---

### Post by aysiu on 2006-06-28
You can try [using the live CD to restore Grub to the MBR](http://ubuntuforums.org/showpost.php?p=117829&postcount=2).

---

### Post by mps69 on 2006-06-28
thanks for the quick reply, I'll give this a try, but before I do how can I find the HD and boot numbers?

---

### Post by aysiu on 2006-06-28
```
sudo fdisk -l
``` is a quick and easy way to see your partition table and partition locations and filesystems.

---

### Post by mps69 on 2006-06-28
Ok this is how things are set just now
> Disk /dev/hdb: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1913    15366141    7  HPFS/NTFS
/dev/hdb2            1914        3738    14659312+   5  Extended
/dev/hdb3            3739        3739           0    e  W95 FAT16 (LBA)
/dev/hdb5            1914        3738    14659281    7  HPFS/NTFS

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         967     7310488+   b  W95 FAT32
/dev/sda2             968        5205    32039280    7  HPFS/NTFS
/dev/sda3           13537       20673    53955720    5  Extended
/dev/sda4   *        5206       13536    62982360   83  Linux
/dev/sda5           13737       20673    52443688+   7  HPFS/NTFS
/dev/sda6           13537       13736     1511937   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$

I don't want to completely knacker my system so I'm going chicken out and ask what I should really type to restore the grub. :confused: 
Thanks

---

### Post by aysiu on 2006-06-28
Since the only Linux partition I'm seeing in there is /dev/sda4, I'm guessing it'd be this: > 4. Type ```
root (hd0,3)
```, or whatever your harddisk + boot partition numbers are
5. Type ```
setup (hd0)
```, ot whatever your harddisk nr is.

---

### Post by mps69 on 2006-06-28
When I try the first code I get
 > Error 21: Selected disk does not exist
Didn't think I should go with the next code.
I forgot the mention the fdisk shows up a 30gb and 160gb. The 160gb is my normal 
boot drive, if that makes any differnce?
Thanks for your time and understanding =D>

---

### Post by aysiu on 2006-06-28
But the 30 GB one doesn't appear to have any Linux partition on it.

---

### Post by user1397 on 2006-06-28
[FONT=monospace]what does "your harddisk nr" mean?
[/FONT]

---

### Post by mps69 on 2006-06-28
That will be the bit that says sda4 on the 160 drive, see I'm learning already ;-) 
Your right the other drive doesn't have a linux partition.
What can you suggest?

---

### Post by aysiu on 2006-06-28
I think that's supposed to be short for *hard disk number*.

---

### Post by aysiu on 2006-06-28
[QUOTE=mps69]That will be the bit that says sda4 on the 160 drive, see I'm learning already ;-) 
Your right the other drive doesn't have a linux partition.
What can you suggest?[/QUOTE]
Hm. I've never done it with /dev/sda before. It should work, though, since the example given was with /dev/sda.

All my drives are /dev/hda. 

If you have the Alternate CD, you could try the HowTo the post I linked to was responding to.

Maybe someone else can jump in with a helpful suggestion...

---

### Post by user1397 on 2006-06-28
[quote=aysiu]I think that's supposed to be short for *hard disk number*.[/quote]ah, that makes sense.  so many abbreviations nowadays, how can we all keep up? :)

---

### Post by mps69 on 2006-06-28
Thanks your help anyway mate.
Can  anyone suggest anything else?
It's a 160GB Serial ATA hard drive on a Compaq Presario, if that's any help.
I have tried "root (sd0,3) "but that has came back with "23: Error while parsing number"
> f you have the Alternate CD, you could try the HowTo the post I linked to was responding to.
Sorry I don't have that CD "yet"

---

### Post by pboguszewski on 2006-07-20
Make sure you are sudoing when you run grub or other commands.  You will get the "selected disk does not exist" error if you do not have root access.  Good luck.

---

### Post by Herman on 2006-07-20
I'll bet the post above here bypboguszewski will solve the problem.

Here are a couple of additional tips that might be handy in the grub shell.
1) You can use your 'Tab' key to find out what partition numbers you might want to type after the 'root' command by typing; root ( and then pressing your Tab key twice. ```
grub> root ( <Tab> <Tab>
``` That should give you a nice feedback advising you of possible partition numbers to complete the command with.

2) Another useful grub command is the 'find' command, when you want to check on partition numbers. You can type; find /vmlinuz, or; find  /boot/grub/stage1  to  have grub find you Ubuntu partition numbers for you. ```
grub> find /boot/grub/stage1 
``` The output from that command will give you the right partition number to type after the 'root; command too.

Probabaly those will just confirm that the info aysiu supplied was correct though, and typing 'sudo grub' instead of just 'grub' to enter the grub shell will solve the problem.

All the best, Regards, Herman :D

---

