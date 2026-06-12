---
title: "wary of grub and MBR issues"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by technik on 2008-04-24
Hi folks, first post.

Last time I had experience of Ubuntu was I believe version 4...think it was warty from memory but I might be wrong there. Last time I installed it GRUB got involved and buggered my MBR and in the end I had to format and returned to XP

Now I want to try again. I have a 3 hard disk setup. 2 disks are for files so I wont lose anything important if it farks up again but i'm cautious due to my previous experience.

My primary hard disk has XP Pro on one partition at the moment but when I reformatted most recently (a month or so ago) I made a 2nd partition of 20GB on the disk which is currently unformatted and unused. I'd like to use this one for ubuntu.

Are there any precautions or steps I should take to make sure nothing dodgy happens so I can have a functioning dual boot system? 

I'm sure it's been asked before but i've been doing a few searches and only seem to find stuff for people installing on 2 totally separate disks or those upgrading a current install of ubuntu.

Thanks for any tips! My other option is to install ubuntu with VMware and run it that way but i'd like a "proper" install if possible but don't really want to risk wasting an evening doing reformats like the last time I tried! :D

(My linux experience is minimal but i have a networking degree and work in a data centre so i'm not too bad with some technical instructions)

---

### Post by BbUiDgZ on 2008-04-28
> **technik said:**
> Hi folks, first post.

Last time I had experience of Ubuntu was I believe version 4...think it was warty from memory but I might be wrong there. Last time I installed it GRUB got involved and buggered my MBR and in the end I had to format and returned to XP

Now I want to try again. I have a 3 hard disk setup. 2 disks are for files so I wont lose anything important if it farks up again but i'm cautious due to my previous experience.

My primary hard disk has XP Pro on one partition at the moment but when I reformatted most recently (a month or so ago) I made a 2nd partition of 20GB on the disk which is currently unformatted and unused. I'd like to use this one for ubuntu.

Are there any precautions or steps I should take to make sure nothing dodgy happens so I can have a functioning dual boot system? 

I'm sure it's been asked before but i've been doing a few searches and only seem to find stuff for people installing on 2 totally separate disks or those upgrading a current install of ubuntu.

Thanks for any tips! My other option is to install ubuntu with VMware and run it that way but i'd like a "proper" install if possible but don't really want to risk wasting an evening doing reformats like the last time I tried! :D

(My linux experience is minimal but i have a networking degree and work in a data centre so i'm not too bad with some technical instructions)

I just done a fresh install of 8.04, i have three H/Ds one with XP/Ubuntu (was debian) and the other two one sata and one ata as storage drives. on first attempt of 8.04 install i got grub error 21, to fix this i removed (unplugged the drive power) my 2 storage drives and reinstalled 8.04 with just my system drive. after checking both windows and ubuntu booted i plugged back in my two storage drives and all is fine.
Probally not the best solution but worked for me.

---

