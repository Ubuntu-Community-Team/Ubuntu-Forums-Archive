---
title: "Newbie: Please help with boot repair"
date: 2017-01-30
forum: Installation &amp; Upgrades
---

### Post by carlschultz2020 on 2017-01-30
Hello, 

I tried installing Ubuntu alongside Windows 7. 
My machine has three hard drives (and I was trying to get a separate hard drive to linux). 
The installation completed, but, now I am unable to boot neither OS. 

Here is my pastebin link:

[http://paste.ubuntu.com/23895337/](http://paste.ubuntu.com/23895337/)

I will appreciate any guidance to a solution or resource. 

Best regards,

Carl

---

### Post by ubfan1 on 2017-01-30
Your sdb and sdc appear to be in a RAID setup.  You might get better help by putting "RAID installation problem" in the title.  Unfortunately, I know nothing of RAID. Did you even get a grub menu?  Just an uninformed guess, but maybe you need a separate boot partition to hold the /boot/grub/grub.cfg file and kernels.

---

### Post by carlschultz2020 on 2017-01-30
The machine has three disks.  BIOS shows all as being non-raid.  For some reason, boot-repair shows those drives as being in a RAID configuration. Yes, I get a grub menu.

---

### Post by oldfred on 2017-01-30
Its not a BIOS or FakeRAID but hardware type RAID. 
Normally then sdb & sdc would be seen as one drive.

> promise_fasttrack_raid_member 

Do not know RAID either, but have seen other threads where some tools get confused with RAID, LVM and gpt.
Thinking gpt is misconfigured somehow. But it may be ok.

But Desktop installer does not fully support RAID. Issue seems to usually be the install of grub  as grub needs different settings on where to install depending on type of RAID. Often Boot-Repair adds correct drivers and will correctly install grub, but it may depend on type of RAID.

---

### Post by carlschultz2020 on 2017-01-30
Thanks, I reinstalled (this time sharing the Windows7 hdd, instead of using a separate hdd). 
I was able to boot linux, and grub gives me the option to select OS at power up.

---

