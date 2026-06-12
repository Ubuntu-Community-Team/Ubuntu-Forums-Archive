---
title: "Dual Boot Problem"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by Mr|White on 2006-06-02
I had an installation of Windows XP running on my laptop when I went to install the 6.06 release on the 2nd partition. The install went fine, and I can boot into Ubuntu. 

When I boot into Windows, I get a blue screen which says UNMOUNTABLE_BOOT_VOLUME. I have searched these forums and and other places and have seen other people with the same problem. No answers yet. 

I know that GRUB was installed on the MBR and I know how to repair it with the Windows disc. 

Is there a way to fix GRUB so Windows will boot? 

Should I fix the MBR with the Windows disc and reinstall Ubuntu with the alternate disc so I can put GRUB on the partition Ubuntu is on?

Any suggetions/directions? 
Thanks

---

### Post by dpholmes on 2006-06-02
I had a similar problem.  My system still showed Windows in the Grub loader but when I attempted to boot windows it took me to Gateway's recovery setup.  I just canceled the setup and booted back into Ubuntu to make sure all of my data was still there on my windows partition (it was, thankfully... and now backed up).  I haven't tried to use the Gateway recovery yet, mainly because I'm afraid to screw up my windows partition.

Any advice would be great.
Cheers,
-doug

---

### Post by Herman on 2006-06-02
Good Day you fellows, [GAG Boot Manager]("http://gag.sourceforge.net/") will almost always boot Windows if GRUB has a few initial hiccups. Here's my own web-page with more on GAG. [http://users.bigpond.net.au/hermanzone/p12.htm]("http://users.bigpond.net.au/hermanzone/p12.htm")
If Windows doesn't boot with GAG, (highly unlikely) then you would look for some kind of damage to your Windows system and repair it. (Extremely rare- almost _never_ happens).
If Windows does boot with GAG, which I expect will be the case, you probably just have some tiney error in Grubs's /boot/grub/menu.lst file which can be simply repaired by correcting the file. Sometimes it's just one or two letters or numbers that need changing. You can get more info on how to do that here on the Ubuntu Web forums, and on my [GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm").

To allow someone to personally help you fix your exact problem, you will need to provide interested people with some information like a copy of the bottom section of your /boot/grub/menu.lst, (where the operating system boot entries are). You get that with this command:```
sudo gedit /boot/grub/menu.lst
``` 
and a copy of the results of the command```
sudo fdisk -lu
```, entered in your terminal. Those two sets of information will be vital to anyone who wants to help you.

You can skip the GAG Boot Manager part if you want, but I find it handy at times to have two ways to boot both operating systems by installing Lilo to my Ubuntu partition later on as well. That makes a very safe pair of systems, that you can always boot one way or the other.

---

### Post by Mr|White on 2006-06-02
thanks for the reply

I'm on the GAG site looking at that as an option....

**-- output from menu.lst --**

# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

**-- output from fdisk --**

Disk /dev/hda: 40.0 GB, 40007761920 bytes
16 heads, 63 sectors/track, 77520 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       26415    13313128+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2           26416       46725    10236240    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/hda3           46729       76198    14852092+  83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hda4           76198       77520      666697+   5  Extended
Partition 4 does not end on cylinder boundary.
/dev/hda5           76198       77520      666666   82  Linux swap / Solaris

Any suggestions?

---

### Post by Herman on 2006-06-02
Your menu.lst looks okay to me.
>     Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       26415    13313128+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2           26416       46725    10236240    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/hda3           46729       76198    14852092+  83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hda4           76198       77520      666697+   5  Extended
Partition 4 does not end on cylinder boundary.
/dev/hda5 76198 77520 666666 82 Linux swap / Solaris In my opinion it looks like a partitioning problem. Normally, Partitions should start and end on the cylinder boundaries. (Unless they invented something new that I don't know about yet). My feeling is that's got a lot to do with your problem. 
If it was me I'd be trying to fix that first.
I think a second opinion is called for though. Anyone second that?

---

### Post by Mr|White on 2006-06-02
I made the NTFS and FAT32 partitions in Windows before the Ubuntu install. The linux partions were made automatically by the Ubuntu install. 

In case that matters...

---

### Post by Herman on 2006-06-02
> I made the NTFS and FAT32 partitions in Windows before the Ubuntu install. The linux partions were made automatically by the Ubuntu install. In case that matters... It's interesting...

What does the output of sudo fdisk -lu give you? (notice '-l_u_', not just -'l'). :D ```
sudo fdisk -lu
``` Your first track should be empty and your first partition should begin at sector number 63.
I wonder if GRUB is looking for your Windows boot block on sector 63 but it isn't there any more, where grub expects it to be. Maybe it's even gone completely.
Can you see all your files in your Windows partition when you click on your hda1 icon on your Ubuntu desktop, or didn't you get one of those icons?
With a healthy filesysem you should have a hda1 and a hda2 icon in the top left corner of your desktop. The hda1 icon should open to browse your Windows file system. You should be able to see your Windows files there that are required for booting with such as boot.ini and NTLDR and others.

Also, did GAG Boot Manager do any good?

---

### Post by mengd2002 on 2006-06-02
[QUOTE=Mr|White]I had an installation of Windows XP running on my laptop when I went to install the 6.06 release on the 2nd partition. The install went fine, and I can boot into Ubuntu. 

When I boot into Windows, I get a blue screen which says UNMOUNTABLE_BOOT_VOLUME. I have searched these forums and and other places and have seen other people with the same problem. No answers yet. 

I know that GRUB was installed on the MBR and I know how to repair it with the Windows disc. 

Is there a way to fix GRUB so Windows will boot? 

Should I fix the MBR with the Windows disc and reinstall Ubuntu with the alternate disc so I can put GRUB on the partition Ubuntu is on?

Any suggetions/directions? 
Thanks[/QUOTE]

My suggestion is to use the Windows console to fix the master boot record.  Reinstall your Ubuntu from the alternate disk.  And use text mode install because if you use the graphics (live CD) installer GRUB is installed on the master boot record on your "C" drive.

---

### Post by Mr|White on 2006-06-02
[QUOTE=mengd2002]My suggestion is to use the Windows console to fix the master boot record.  Reinstall your Ubuntu from the alternate disk.  And use text mode install because if you use the graphics (live CD) installer GRUB is installed on the master boot record on your "C" drive.[/QUOTE]

Well I gave that a try. The windows console did nothing to fix the problem. GRUB is gone button the same blue screen comes up. 

Searching of the M$ knowledge base was no help. It said to fix to the MBR.

I am currently reinstalling windows and will attempt to install Ubuntu again on the second partition using the alternate disc to do it. 

I will continue to update.

---

