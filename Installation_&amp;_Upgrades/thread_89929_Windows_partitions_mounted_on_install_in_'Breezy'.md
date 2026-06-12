---
title: "Windows partitions mounted on install in 'Breezy?'"
date: 2005-11-13
forum: Installation &amp; Upgrades
---

### Post by Herman on 2005-11-13
I am noticing that sometimes, after a fresh 'Breezy' install, there are icons in the top left corner of the monitor for other partitions, which seem to be automatically mounting on boot. If this is so, then it is a great improvement in 'Breezy'. The developers rock! :D  
 I have not found this to be the case every time though, and I suspect it might be only for FAT32 partitions, or only for Windows partitions.
Can anyone inform me as to the conditions that determine whether this happens or doesn't happen? I'll need to update my example install website forthwith! I am doing some test installs right now anyway, and will soon establish a pattern to this excellent feature. But it would be nice to know from someone who is informed better than me, what exactly are the factors that influence this pleasant occurence?:smile: 
(Herman)

---

### Post by Herman on 2005-11-13
Well, it seems like it doesn't happen on my little PcChips 'BookPC' Bki810 test computer. (400Mhz celeron CPU, 125Mb ram). 
But either I'm 'loosing my marbles', or it happens on some computers and not others. I'm sure this happened twice last night on two Acer Aspires, one with 3.0Ghz Intel Pentium, and the other with 2800+ AMD Sempron.  :confused:
I'll keep experimenting, but it would be nice if someone can let me know the right information, I can only find these things out by trial and error. Apparently sometimes this method (trial and error), could be leading me to make conclusions that might not be correct for everyone.:rolleyes: 
Anyway, if some computers can do it, then it's a good thing! :smile:

---

### Post by yesplease on 2005-11-17
Ntsf is also automounted in Breezy (i cant help you with the icons because I removed them and use the Places menu instead).

Mounting is regulated in etc/fstab, you need to add different values for ntsf and fat partitions. (search the forum for them). Edit: this looks good; [https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28mount%29](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28mount%29)

For reading linux files on ext3 from windows I use explore2fs (1.07), works very well :)

---

### Post by Biased turkey on 2005-11-17
It's strange, none of my windows partitions ( NTFS and FAT32 ) show up as you mentioned.
My windows partitions are on another disk, could it be the reason why I can,t see them ?

---

### Post by yesplease on 2005-11-17
@biased turkey: That cant be the reason, my winodws partitions are completely separated from Ubuntu on a second disk and they are automounted.

Did you follow the instructions in the link I provided (note that there are other howtos on this forum).

When that fails, post your fstab file and relevant hardware and perhaps somebody can help you.

---

### Post by Herman on 2005-11-17
Thanks for the replies you fellows, so it does happen to other people too, and I am not going crazy! :) 
 I will update the website when I get some time, (I'm extremely busy with work for a while). I did some more installing and it seems as if the installer probably detects what kind of computer it is going into and installs Ubuntu a little bit differently in different types of computers. I don't know yet whether it depends on the CPU or amount of RAM or just exactly what it is that makes it decide to give us the partitions auto-mounted in some computers, but I like it!:D 
You are correct, yesplease, about needing to edit /etc/fstab. I saw where aysiu advised someone to change their 'mount options' for those partitions in /etc/fstab from 'defaults' to 'iocharset=utf8,umask=000', to enable full read and write capabilities. These partitions are automounted on start-up in my machine, and so are all my new 'ssh' links I am experimenting with on my home LAN. This is really handy and fast for people like myself who love to move files fast from one partition to another and around the LAN! It's great, I love it! Thanks developers!:D 
I have also found that I can access partitions in my other computers on my LAN, like if I am networking between Ubuntu systems for example, I can access the other computer's Windows and FAT32 partitions if I want. This is very handy, and I believe (for me), it is alright, because I use SSH networking, and have good secure passwords. However, there might be security implications for some people when these partitions are mounted all the time. If an attacker did manage to get in somehow then they would be able to access information on the other partitions easily. If someone had sensitive info on there other partitions it would be compromised. As far as I know, Ubuntu is 100% stealth at firewall testing sites until people start making changes to things they don't understand.  It would be best if people with secrets umount theirs each time, or create a special partition for their secrets that they only mount when they need to. That's my idea anyway, but I'm no security expert, I'm just beginning with networking with Ubuntu, and would welcome any advice from others who would be more advanced than I am on this topic. :D 
Any?

---

### Post by yesplease on 2005-11-17
Herman wrote "'iocharset=utf8,umask=000', to enable full read and write capabilities".

I think that is for Fat only, but I did not search for official info. I think it is more secure to not to give write (and read) capabilities to anybody.
Give them only to superusers for instance, because it will make you stop and think before you overwrite files and make it hard for intruders to abuse shared partitions over LAN.

---

### Post by Biased turkey on 2005-11-17
[QUOTE=yesplease]@biased turkey: That cant be the reason, my winodws partitions are completely separated from Ubuntu on a second disk and they are automounted.

Did you follow the instructions in the link I provided (note that there are other howtos on this forum).

When that fails, post your fstab file and relevant hardware and perhaps somebody can help you.[/QUOTE]

The link you give on the Ubuntu wiki says that for Ubuntu 5.10 it's automatic so there is nothing to do right ?

---

### Post by yesplease on 2005-11-17
[QUOTE=Biased turkey]The link you give on the Ubuntu wiki says that for Ubuntu 5.10 it's automatic so there is nothing to do right ?[/QUOTE]

It was automatic in my breezy 5.10 setup, and it should work by default. However, the poster says it did not work automatically on all computers.

Did you check if there are icons for ntfs partitions in the "places" menu?

---

### Post by Herman on 2005-11-29
Well now, I have an interesting phenomenon to report on this subject:
After many experiments and failed attempts to force my other partitions to automount on boot up in this old test computer, they have suddenly began automounting themselves without me doing anything! 
This is very odd!:rolleyes: 
Thinking back, I was doing some other experiments and doing a lot of re-booting to test some other trick I was learning and on one re-boot I saw it say something like '/ has rebooted more than 30 times without having a file system check - forcing a file system check' (or something like that),(this was part of the white typing on the black screen while waiting for the computer to boot Ubuntu). It did a kind of 'progress bar' across the screen (with a row of = signs), while I waited. It was after that boot that I have not been getting these partitions automounted in this old computer now!:D

---

