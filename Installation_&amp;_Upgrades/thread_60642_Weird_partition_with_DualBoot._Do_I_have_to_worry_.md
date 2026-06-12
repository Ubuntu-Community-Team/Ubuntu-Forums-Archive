---
title: "Weird partition with DualBoot. Do I have to worry or not?"
date: 2005-08-28
forum: Installation &amp; Upgrades
---

### Post by ankerman on 2005-08-28
We are planning to work on schools with Ubuntu. We bought three Thinkpad R50 laptops and decided for two of them to make them Dual-Boot.

The laptops (40gb) were pre-installed with Windows XP. I followed (exactly) the instructions of the WIKI:
[https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo)

I thought we did succeed: Windows XP and Ubuntu are both working fine (as far i can see). So i did exactly the same with the second laptop. Trying to figure out how to get rid of Windows XP for the third one, I found out that there is something wrong with the partitions:

sudo fdisk -l:

Disk /dev/hda: 40.0 GB, 40007761920 bytes
16 heads, 63 sectors/track, 77520 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       34065    17168728+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2           68611       77520     4490640   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/hda3           34075       67177    16683502+  83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hda4           67177       68595      714892+   5  Extended
Partition 4 does not end on cylinder boundary.
/dev/hda5           67177       68595      714861   82  Linux swap / Solaris

Partition table entries are not in disk order

Since everything seems to work fine, i need to know if i have a serious problem or not. Will i get problems later and is it better to do something about it? And if i have to do something about it: what to do differently? I still have a third pre-installed Windows XP so i have one more chance to do it in another way.

---

### Post by weekend warrior on 2005-08-29
I'd say if the first one was fine then try the third the same way as in the wiki. The second Thinkpad could be an anomaly. If the third turns out well and if you have the time, it doesn't hurt to try installing the second one again to see if you have the same problem with it or not.

---

### Post by ankerman on 2005-08-29
Thanks for the response, but:

Not one, but both of the laptops i worked on have the weird partition tables. They are exactly the same. To me it seems that the WIKI is not giving the full-proof solution. So definitely i'm not going to use the same method for the third one.

The first question is still: does it hurt continuing to work like this? Is it a problem that the partitions are not in disk order?

---

### Post by weekend warrior on 2005-08-29
I did manage to misread that, sorry.  [This may be of interest](https://www.redhat.com/archives/redhat-install-list/2002-August/msg00182.html). Have a look and see if it answers your question.

From what I can see, it doesn't look as if it will cause problems. Unfortunately no method is foolproof, especially with XP, so you may wish to look for other dual boot primers to compare methods. Caution is always wise but if you're not detecting any trouble it seems ok to continue with the third but keep searching for more information just in case something comes up later on.

---

### Post by weekend warrior on 2005-08-29
On a side note, is there a specific reason for these to be dual boot systems? Would it fit your needs for example to have one with XP and the other two with just ubuntu? It makes things simpler in the long run to have each dedicated to just one type of OS.

---

### Post by ankerman on 2005-08-29
[QUOTE=weekend warrior]On a side note, is there a specific reason for these to be dual boot systems? Would it fit your needs for example to have one with XP and the other two with just ubuntu? It makes things simpler in the long run to have each dedicated to just one type of OS.[/QUOTE]

We will work in places where there are problems with electricity and internet connections are not easily available. We will make websites together with the children and we will have to know if the websites are rendering ok on Windows, since that is the only thing people are using in the Internet-cafes.

We already managed to set-up a wireless ad-hoc connection both with Windows and Ubuntu, but we managed to do it with Ubuntu because we learned from Windows.

If it is not necessary we will not work with Windows. The third laptop can have only Ubuntu on it and be the main local server.

---

### Post by ankerman on 2005-08-29
[QUOTE=weekend warrior]I did manage to misread that, sorry.  [This may be of interest](https://www.redhat.com/archives/redhat-install-list/2002-August/msg00182.html). Have a look and see if it answers your question.

From what I can see, it doesn't look as if it will cause problems. Unfortunately no method is foolproof, especially with XP, so you may wish to look for other dual boot primers to compare methods. Caution is always wise but if you're not detecting any trouble it seems ok to continue with the third but keep searching for more information just in case something comes up later on.[/QUOTE]

Is it an idea to forget about resizing the Windows-disk with the:
System Rescue CD ISO image ([https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo))
and directly installing Ubuntu on the Windows-laptop? There should be an option:
don't overwrite Windows?

---

### Post by recce101 on 2005-08-29
On your original question, I get the "partition table entries are not in disk order" reply to fdisk -l on two machines. It appears to mean simply that, for example, partition 5 is closer to the beginning of the disk than partition 4 since the numbers are not all reshuffled every time you repartition. It's probably there in an attempt to save you confusion if you're comparing the fdisk table with a graphical display like Partition Magic or a Linux equivalent. You could have a similar situation with DOS/Windows drive letters if you've repartitioned more than once or added a second drive, though I haven't seen that reported by fdisk.

Regarding the "does not end on cylinder boundary" issue, I googled that quote and found 3900 entries. Not necessarily a serious problem -- it just "depends." Sometimes my Drive Image program (Windows) offers to fix a boundary discrepancy after I've resized a Linux partition, and whether I allow it to or not doesn't seem to make any difference. Do your own google and you'll get a better feel for the situation.

---

### Post by weekend warrior on 2005-08-29
On your last questions ankerman,

The options you have are "erase entire disk" or "manually edit partition table", as shown [here](http://www.mrbass.org/linux/ubuntu/install/).  Once you're in manual edit there's a "use largest continuous free space" option. But of course that free space has to exist.

*If* there's free space, meaning Windows isn't taking up the whole drive, then yes you could just let ubuntu install without resizing. But I'm assuming XP *does* take up all the drive, right? In that case you need to resize to have somewhere to create the linux partition and swap. Now if you want something else to resize and create that space, there are other Live CDs for example [here](http://www.pclinuxonline.com/wiki/PartiTioning). 

Here are a couple of other places you can look for information on resizing and installing.

This one is with the tools in ubuntu you may already be familiar with.
[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

This one is from Gentoo but it's a different approach that might interest you.
[http://gentoo-wiki.com/HOWTO_Install_Linux_after_Windows](http://gentoo-wiki.com/HOWTO_Install_Linux_after_Windows)

---

### Post by ankerman on 2005-08-29
Thanks a lot for your responses. My conclusion (for now) is that i will just continue with my DualBoot laptops, including my weird partition tabels. If i will have any problems later, i  will let you know. If i decide to try again another way, i also let you know.

And another thing:
In my situation the laptops are starting with the Grub-bootloader including an extra option for WindowsNT/2000/XP. This refers to some kind of hidden partition to recover your Windows in case of problems. Since that is not working in this way, i did comment that out:

sudo pico boot/grub/menu.lst

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
#title          Windows NT/2000/XP
#root           (hd0,1)
#savedefault
#makeactive
#chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

