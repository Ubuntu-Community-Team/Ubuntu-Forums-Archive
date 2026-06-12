---
title: "Grub doesn't let me boot from PATA Disk"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by RandomStyuff on 2007-10-26
I am a long time SUSE and now openSUSE user. For a while I've been telling myself to try Ubuntu, just to see how it is and what the big deal is all about. I saw 7.10 as a good opportunity to do so. The problem is I ran out of hard drive space on my 320 GB SATA drive, so I decided to use an old, unused 80GB PATA disk I had sitting around.

I downloaded the Gusty Gibbon DVD through Bit-torrent, and installed it onto the HDD. I had disconnected my main disk(SATA) completely, to avoid any accidents that sometimes happen. Installation went smoothly, and everything was fine... and then I restarted and ... Grub Error 21. Thats what it says, error 21... so I go online from the Ubuntu live CD (to lazy to switch HDDs) and find out that error 21 means that the disk is not there, or not found. So I decided to try something. I switched  HDDs (more like add my main HDD and not remove the new one) and went to my openSUSE install and then from inside the YaST control center I added the Ubuntu entry into my openSUSE GRUB menu.

Now I get to the GRUB menu just fine, but if I choose Ubuntu, I get 21 again.

What I believe the problem to be: My motherboard, the Asus P5B- WiFi/AP, uses the Intel P965 chipset, or one that doesn't have built in PATA support anymore. The PATA chip is a J-Micron.
I believe that because the BIOS/CMOS doesn't detect the disk, GRUB doesn't know where to link to, and because of that I can't boot onto it. Can anyone think of a work around? Will a different boot loader work? Any suggestions on what to do (other than go buy a SATA, because I have no money whatsoever to spare right now...)?

Thanks in advance

---

### Post by thelocust on 2007-10-26
when you boot up and it gives you the option of OS's to boot from i.e. ubuntu, memtest. hit Esc to stop it from trying to boot highlight the top Ubuntu hit "e" twice and see what the (hd0,0) is play around with the number untill it works 
 
(hd0,1)
(hd1,0)
(hd1,1)
ect...
 
(my bad didn't read the whole post if you can see the HDD in the bios the above wont work. Sometime bios can be stuburn try messing around with them or taking out the battery to clear them.)

---

### Post by RandomStyuff on 2007-10-26
No, I don't see it in the BIOS... 

I think the problem is that the PATA on my motherboard is done through a J-Micron controller which makes GRUB not detect the disk. I CAN mount the disk with openSUSE, so I know that it is connected and ok. 
When I did the editing GRUB you mentioned in your post [(hd0,1) and so on] I noticed that when (hdX,Y) where Y is any value and X is any value other than 0, it tells me that the hard drive doesn't exist. On hd0 it doesn't give me this error, but on all the rest I get error 21, (which, I believe means that it can't find the disk)

I will try messing with BIOS

---

### Post by thelocust on 2007-10-26
PATA to SATA converter.

---

### Post by RandomStyuff on 2007-10-26
Nice idea... but I've given up...

I will move all my music, vids and pictures onto the PATA disk (because once in Linux, and by that I mean both openSUSE and Ubuntu LiveDVD, I can mount it just fine), and then use the free space to resize my openSUSE partition and install Ubuntu on :D

Thanks anyways! After going through the BIOS I think that what I wanted to do is impossible (short of buying a converter or new HDD) so I guess this is the best option.

---

