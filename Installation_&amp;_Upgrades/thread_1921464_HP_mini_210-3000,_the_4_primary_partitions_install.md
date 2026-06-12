---
title: "HP mini 210-3000, the 4 primary partitions installation problem with a twist"
date: 2012-02-06
forum: Installation &amp; Upgrades
---

### Post by psifunk on 2012-02-06
Hi all. I have the same problem with hp mini that others pointed out in these forums but I can't use any of the solutions proposed. 

(btw very good solutions here : [My Successful Install of ubuntu netbook 10.04 on a HP Mini 210-1084NR - Page 3 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1556573&page=3")  ).  

Quick overview of the problem and the proposed solutions: hp mini comes with four primary partitions for windows and hp stuff and so no room for another one. So either no ubuntu,let one partition go (delete it or back it up on an external disk) or only ubuntu (erase everything)

In fact I find myself in a situation were I can't backup on an a drive other than the one of the notebook (i don't have any others  :P )  and I want to keep all the hp and windows stuff. So I need some tips.

From reading other posts I think something along these lines should work but I would like your advice and opinion since I am not sure if I understood correctly. So here it goes:

- Use windows facility to resize the windows partition (c:) and free up 120Gb (that i did)
- Make an image of the partition HP TOOLS and save it on the remaining c: which is about 130 Gb, to have it as backup _(using what?)_
-Use GParted to delete HP TOOLS partition in order to have the possibility of a new primary partition (a simple delete operation would be enough?)
-Forget temporarily about the 12Gb that HP TOOLS were occupying
-Make the unallocated space freed up in step one into a new primary partition using GParted
-Insert live USB and one should have the option to install ubuntu automatically in dual boot

(slightly irrelevant note: Myself I would have never booted windows the  first place and use the hole disk of this new petite machine  for ubuntu. That's what I did on my asus notebook. BUT the owner of this  has never tried anything except windows and is taking no risks and I  think telling her to go buy a disk drive to do the back up kind of beats the purpose of convincing her to try ubuntu.)

---

### Post by Mark Phelps on 2012-02-07
> **psifunk said:**
> In fact I find myself in a situation were I can't backup on an a drive other than the one of the notebook (i don't have any others  :P )  and I want to keep all the hp and windows stuff. So I need some tips.

Several major problems right off ...

First, not being able to back up anything to an external drive makes ANY installation of Ubuntu (other than Wubi) risky as there is likely to be no easy way, and maybe even no hard way, to recovery your working system if the dual-boot install has problems.

Second, I normally advise folks to use the FREE version of Macrium Reflect to backup their Win7 install before they start a dual-boot setup, and to make the Linux Boot CD (used for Restore), but your first problem and the (supposed) inability to boot your mini from CD makes this another major problem.

Third, I normally advise folks to use the Win7 Backup Feature to created and burn a Win7 Repair CD BEFORE starting the dual-boot setup -- as this allows you to repair any Win7 boot loader problems resulting from the dual-boot config.  But again, if your mini can't boot from CD, this will do you no good.

> - Use windows facility to resize the windows partition (c:) and free up 120Gb (that i did) Good start
> - Make an image of the partition HP TOOLS and save it on the remaining c: which is about 130 Gb, to have it as backup _(using what?)_
You don't need an image of HP Tools, you just need the contents -- which you can copy to your Win7 OS partition.  But then, boot/restore functions dependent on these is likely NOT to work because you will have removed the partition where they WERE and moved them to a different location.
> -Use GParted to delete HP TOOLS partition in order to have the possibility of a new primary partition (a simple delete operation would be enough?) For removal, yes.  But, it's a small partition and doesn't free up much space.  Also, its removal may result in complications (see above).
> -Forget temporarily about the 12Gb that HP TOOLS were occupying??
> -Make the unallocated space freed up in step one into a new primary partition using GParted
-Insert live USB and one should have the option to install ubuntu automatically in dual boot
Would not do it this way -- more below.

>  ... BUT the owner of this  ... is taking no risks and I  think telling her to go buy a disk drive to do the back up kind of beats the purpose of convincing her to try ubuntu.)
That's true -- but dual-boot installs always come with some risk -- which is made a LOT bigger by the inability to do backups first.

Partition Wizard makes a great FREE partitioning tool -- which runs in MS Windows and comes in bootable ISO form.  But, I don't know if it can be installed to USB stick.  IF it can, I would boot from that and use it to move your Windows partitions to the "left" to put all the free space on the "right".

Once you have that done, you can boot from the Ubuntu installer USB stick and use "something else" to install Ubuntu to the new free space.

---

