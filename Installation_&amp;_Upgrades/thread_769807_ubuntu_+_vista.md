---
title: "ubuntu + vista"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by eskay_karthik on 2008-04-26
I am running both Ubuntu and vista in my laptop. And they are working fine together.
Now there is some problem in vista ( probably due to virus ) and it has slowed down.
I would like to restore the comp to factory settings, which will reinstall vista in the C drive alone i think. So, my Ubuntu partition will not be affected.
All that i need to know is about the grub, what should i do so that i get the grub options for multiple OS even after reinstalling vista .. I don't want Ubuntu to get unusable in any way because it is working perfectly fine and i cant waste time reinstalling Ubuntu and all softwares also ( cos i spent days together setting up Ubuntu )

Please help.
eskay

---

### Post by Tatty on 2008-04-26
Is your ubuntu install on a separate hard drive?  If not then restoring to your "factory settings" is almost certainly going to wipe your ubuntu partition.

To re-install grub after a windows install... [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by eskay_karthik on 2008-04-26
No.
Ubuntu is in the same hd as vista..
Anyways, thanks.

eskay

---

### Post by Tatty on 2008-04-26
In that case i would presume that ubuntu is going to get wiped doing this, so back up everything you dont want to lose from it before going ahead.

---

### Post by VMan on 2008-04-26
Definitely backup before trying to restore your Vista.  If you're lucky (I was), the restore disk will allow you the option to restore just to your Vista partition and will leave your linux partitions alone.  I will be testing (re-confirming) this next week.  For some reason, various programs just stopped working in Vista.  I only boot into Vista a few times a month, so am not sure how I managed to do that.

I'll be restoring Vista and then doing a fresh install of 8.04 on my laptop.  I did this once before and was able to preserve my /home partition.  I have an external hard drive to back up /home prior to doing this though so in case I remember incorrectly, I don't lose anything.

---

