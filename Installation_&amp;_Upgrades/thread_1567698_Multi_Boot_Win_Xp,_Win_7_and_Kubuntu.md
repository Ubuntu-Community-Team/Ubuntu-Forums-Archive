---
title: "Multi Boot Win Xp, Win 7 and Kubuntu"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by vikrang on 2010-09-04
I had Windows XP installed in my machine..After that , I upgraded to Windows 7...Windows 7 installed its boot loader and added Windows Xp to its menu list..
So once I booted , I would be shown 2 entries 
 
Win 7 
Win XP
 
and I was able to boot either one of them
 
I installed Ubuntu Lucid in another partition..
 
GRUB 2 overrode the MBR and took control of it
 
Result: I was presented with the following on boot
 
1.Linux Generic
2. Failsafe
3.Memtest
4.Windows (sda1)
5. Windows(sda1)
 
The main problem is there are 2 entries for WIndows 7..I presume since there were 2 partitions one for Xp and another for 7 , it is appearing twice..
 
On selecting both however , I get into the revised NTLDR (Windows 7) which again shows a SUB MENU of Windows 7 and Windows XP...However on selection both work fine
 
I would like to eliminate the SUB MENU for Windows and would like to know as to how to make GRUB2 recognize my XP separately and 7 Separately and create 2 menu entries..
 
I know that GRUB just chainloads the WIN NTLDR..
 
Even if it chainloads, I would like to boot XP NTLDR and 7 NTLDR separately on selection of the appropriate menu entry
 
Can anyone suggest a way?

---

### Post by halj32 on 2010-09-04
the problem is that windows 7 takes over the windows bootloader so that you will have to chose Linux or windows, then in the windows bootloader win 7 or xp.
sorry but I dont know how to edit the new grub 2 bootloader but Im sure that there are plenty of posts telling you how to do it

---

### Post by oldfred on 2010-09-04
It is not a grub issue but a windows issue. Windows combines boots as you have notice, but it does it by moving the second installs boot files to the first that has the boot flag (active partition).

If both installs are in primary partitions it may be possible to move XP's boot files back to the XP partition. But if the other way around I do not think so.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by vikrang on 2010-09-05
Thanks fred..Thats a very good tutorial on Win Boot Loader...I know this issue is win related and not grub.You have given a very good pointer about installing both on Primary Partitions..I have infact installed XP and 7 on 2 Primary partitions, but the Boot flag is enabled only for one partition...Can I use Gparted and enable the flag?
Will this work? or should I repair my WIN Xp installation using Installation CD and run Fix MBR...In that case , my 7 may go for a toss..I also have a 7 DVD to repair anything if required!!! But I wanted to know if there is a simpler way?
 
 
Actually I recovered my 7 Bootloader from Easy BCD after an MBR mess up..It is very interesting to note that Easy BCD recognized both my Xp and 7 and created boot entries for it..So I am sure there is some logic whereby both the installations are recognized.

---

