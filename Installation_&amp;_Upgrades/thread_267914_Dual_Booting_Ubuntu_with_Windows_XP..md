---
title: "Dual Booting Ubuntu with Windows XP."
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by Compucore on 2006-09-29
I had given another techie a cd od Dapper drake for himself to use. I was speaking with him recently about how it went. It went kind of okay. When he was in the live CD and did a repartition of the hard drive to leave both windows and Ubuntu on the same drive which was a 160 gig hard drive. He partition the drive as 30 gigs for windows XP and the rest for Ubuntu. After installing Ubuntu completely. Grub didn`t see the windows partition at all. I was wondering if Grub if it is cause that the Windows partition was NTFS and does not recognized by grub to go in and boot windows XP itself. I never really had a problem like this even on earlier version of Linux since I was using two different drives completely and the primary drive was fat32. (This is going back as far as 2000.) 

I don`t have the specs off hand of his computer with me right now. I will ask him what they are later on this afternoon. I think someone had mentioned that Windows XP and Linux in general don`t like each other all too well. I don`t know if it was here or on another message board completely. I don`t want to accuse anyone here. 

Would it be better off he had gotten a second hard drive and just installed ubuntu on that one and leave his other drive as just a windows drive. 

Compucore

---

### Post by Kateikyoushi on 2006-09-29
I have a win partition on my notebook and could boot it anytime.
This Lin and win do not like each other is not true, you can even read the other OS's partitions as long you use ext3 or rfs.

---

### Post by pseudonym on 2006-09-29
> **Compucore said:**
> Grub didn`t see the windows partition at all. I was wondering if Grub if it is cause that the Windows partition was NTFS and does not recognized by grub to go in and boot windows XP itself.

Did your friend install grub into the master boot record? This is usually the recommended approach. It could just be that grub didn't pick up the winxp partition when it installed. It happens sometimes. But it is easily fixed.

When you reply, post a copy of the file /boot/grub/menu.lst .

And to second what the last poster said, win and lin 'like each other' more than you think :) Certainly, dual booting on the same disk is no problem at all.

---

### Post by Compucore on 2006-09-29
Well I know they like each other in the earlier version for sure. I never had a problem with win98 SE and redhat and that was in 2000 over 6 years ago. I will double check him to make sure. I am sure that he did somthing wrong when it came to the installation. He`s french on top of that and doesn`t understand English too well when it comes to the written or orally speaking. Maybe he could of edited grub when he was in the ubuntu environment to make it bootable. I rememeber making a modification one time for the newer kernels that came out with the 386 extension on it. I had to add irqpoll to it. Since I was using a AMD K6-2 and it was having problems booting in. But on his I thought for sure that it would have detected it first shot arounf when installing. And I have a feeling that he didn`t do a full defragmentation on his windows XP partition. Maybe that might have something to do with it too. I`ll pdate everyone here about it once I find out. 

Compucore

---

