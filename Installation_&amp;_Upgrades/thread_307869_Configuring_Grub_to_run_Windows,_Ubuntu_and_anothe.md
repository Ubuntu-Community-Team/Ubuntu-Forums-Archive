---
title: "Configuring Grub to run Windows, Ubuntu and another Linux distro"
date: 2006-11-27
forum: Installation &amp; Upgrades
---

### Post by Raven-sb on 2006-11-27
Hi All, 

Please forgive me for using windows terminology to describe what I'm trying to do, but I'm not sure of the correct linux terminology to use.

Currently I have my system set up in this way.

Hard Disk 1: Drive C: Windows XP
Hard Disk 2: Drive D: Ubuntu 6.10
                       Drive E: Unformatted

What I want to do is to use drive e to test out other versions of linux.  I was wondering if someone could please tell me how to configure Ubuntu's Grub so that I can switch between the 3 different OS's.

Any help would be warmly appreciated.  Many thanks

Steve

---

### Post by Bartender on 2006-11-27
I can give you a general outline of what I did to get 3 Linux OS'es running together on the same drive.  It's called chainloading.  You manually edit the /boot/grub/menu.lst by adding 3 lines of text above the "Debian AutoMagic" divider.  You know what I mean, right?  The Windows entries are stored below that divider.

I haven't done this enough to verify how many different ways you could type in the text, but here's what I used:

title Kubuntu
rootnoverify (hd0,2)
chainloader +1

Explanations: 
In the "title" line, I found that the process works no matter what you name the new GRUB entry.  GRUB doesn't care if you type in Kubuntu but install Xubuntu.  Kubuntu will be the name that appears when GRUB brings up the list of OS'es for you to choose before automatically booting the default one.  You could type in "Top-Secret Nuke Codes" and it would work.

The second line, on the other hand, is very specific.  
(1) GRUB needs to see a bootloader installed in the partition that you describe, and it needs to be GRUB.  Well, I've read it can be LILO but the steps to make that work are too complex for me.  
(2) The command in between those parentheses (hd*,*) has to point to the partition where you installed the Linux OS.  That number is in GRUB-speak, which means that your first drive and first partition both start at zero.  (hd0,2) points to your first HDD and your third partition.  From your original post I'm not sure if you're saying you have one drive and 3 partitions or 3 drives.  If you have 1 HDD, 3 partitions, and those partitions are Windows first, Linux second, then a blank one, then you'd enter (hd0,2).  If you have three drives, the entry will be (hd2).
(3) For this to work, you have to make absolutely sure that when installing the new Linux OS GRUB installs to that Linux partition instead of the MBR.  I've done this with PCLinuxOS and Ubuntu.  The steps were not the same.  (PCLinuxOS even gave me the option of installing LILO or GRUB so that was handy) So for whatever distro you try out, you'll have to understand the process for manually detouring GRUB because chances are it'll go to the MBR if you don't intervene.

The third line is always the same.  
chainloader +1
Easy, huh?

So, you make those changes to /boot/grub/menu.lst, save them, then maybe start up the PC and see if the new choice shows up in your GRUB startup list.  You may need to extend the amount of time GRUB waits before moving on.

Then, if that all worked out, you go ahead and install your test distro to the correct partition.  I'll say it again because this is crucial - you tell GRUB to install to that partition, not the MBR. You re-boot, and the GRUB menu.lst entry you added earlier should take you to your new distro.

You know what?  Chances are you're gonna run into a distro that only offers LILO as the boot loader.  If you can find a spare drive, I think the simplest thing to do would be to install it (unless you already have 3!) and just dedicate that one for testing.  Hook it up as secondary drive, install the entire test Linux distro to that drive, then choose which drive to boot from during the BIOS process.  Either go into BIOS and tell it you want to boot from the secondary drive, or hit the F8 button if that works with your PC.

---

### Post by Raven-sb on 2006-11-27
Thanks for the help Bartender. To clarify I have two hard drives, the first is dedicated to WIndows, the second to Linux.  I've  divided the Linux drive into two partitions , one for testing, the other for Ubuntu.

Once again thanks for your help.

---

### Post by threegremlins on 2006-12-01
I'm always mucking about with operating systems and drives, changing them frequently. In the old days you had to install root within the first umpteen cyllinders of your hard drive so I always have 82 then 83 at the begining of the primary. Because Windows XX always replaces the MBR when you install them I've begun installing them on the secondary. I open up the side panel, switch the connectors and the jumper so the system believes it is being installed on the primary, switch it back to the secondary, put panel back on. The MBR the newly installed system has rewritten is completely ignored and boots grub on the primary partition. In Xubuntu, if I have to I can change the menu list so everything boots up properly. I don't know if this helps you at all, it's just what I do.  What prompted me to reply to this was that the Windows partitions seem to need map coordinates or they don't boot. For a while I was running FreeDos and it changed the partition and now even after it's been removed and replaced with 98se, Grub still thinks it's Freedos and doesn't add the map coordinates, so it wont boot into 98se until you add them. Check it out.    

title        Ubuntu, kernel 2.6.15-27-386
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd        /boot/initrd.img-2.6.15-27-386
savedefault
boot

#Previously
#title FreeDos
#root(hd1,0)
#savedefault
#makeactive
#chainloader + 1

#changed to
title        Windows 98se 
root        (hd1,0) 
savedefault 
makeactive 
map        (hd0) (hd1) 
map        (hd1) (hd0)
chainloader    +1

title        Windows XP
root        (hd1,1)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

You noticed I moved the Windows XX sections from the bottom of the list to just below the Xubuntu section. That's because I was too lazy to hit the arrow down key so many times to boot it. It doesn't seem to matter where you put them.

---

