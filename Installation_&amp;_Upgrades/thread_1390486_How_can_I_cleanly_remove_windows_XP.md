---
title: "How can I cleanly remove windows XP?"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by Leshrac on 2010-01-25
Currently I dual boot windows XP and ubuntu 9.10. However, I am quite happy about my Ubuntu installation and I am starting to think about my windows xp install as a waste of hard drive space.

I wonder what's the best way to remove the windows xp install.

I have 3 partitions, windows being the first, ubuntu being the second and the third being ubuntu's swap.

I am not familiarized with the way the grub bootloader works so I am worried about breaking it if I just remove the first (winxp) partition via gparted and expand the second (ubuntu 9.10) fill the empty space.

Can anyone advise me on the cleanest and safest course of action?

---

### Post by phillw on 2010-01-25
> **Leshrac said:**
> Currently I dual boot windows XP and ubuntu 9.10. However, I am quite happy about my Ubuntu and I starting to think about my windows xp install as a waste of hard drive space.

I wonder what's the best way to remove the windows xp install.

I have 3 partitions, windows being the first, ubuntu being the second and the third being ubuntu's swap.

I am not familiarized with the way the grub bootloader works so I am worried about breaking it if I just remove the first (winxp) partition via gparted and expand the second (ubuntu 9.10) fill the empty space.

Can anyone advise me on the cleanest and safest course of action?

Your 1st partition, the Win one, will have your Grub Boot System on it. So, when you wave bye-bye to it - Grub will disappear as well.

Re-installing Grub is no big deal.
```
sudo fdisk -l
``` should return something along the lines of
> /dev/sda1   *           1        4464    35857048+   7  HPFS/NTFS
/dev/sda2            6654        9729    24707970    5  Extended
/dev/sda3            4466        6653    17575110   83  Linux
/dev/sda5            9588        9729     1140583+  82  Linux swap / Solaris
Typically, your ubuntu are will be sda3 for a dual boot system (Whichever ends 83 Linux is the one)

When you remove sda1 (simply format it to ext4, I'll explain in a while) - You'll need to boot from LiveCD and head over to Section 13 of this thread --> [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

On a one disk, old dual boot system - you're destination would be sda3, as per the example above - the thread does repeat how to check it.

That will get you back booting ... Now you have a spare partition. I'd suggest making it into a seperate /home partition - This is real handy when you want to upgrade, as it means all your profiles, Desktop etc is saved. To do that, head over to --> [Create a separate home partition in Ubuntu]("http://www.psychocats.net/ubuntu/separatehome")  And remember you're going to be using sda1 for your new /home area, so you don't need to repartition. (You'll be swapping the sda1 and sda3 bits round, as your **exisisting** home is on sda3 and the **new** home will be on sda1 - Assuming you have a layout like my dual boot system.

Regards,

Phill.

---

### Post by Leshrac on 2010-01-25
Thank you very much for your help.

I do have a little problem, the machine I am using is a pretty old laptop and the cd drive does not work properly, I can't use it to boot. It does not have the option of booting from a USB drive either.

I installed ubuntu using UNetbootin from windows xp.

I am worried about losing my grub install because I wouldn't know how to boot the machine if it were to break.

---

### Post by phillw on 2010-01-25
> **Leshrac said:**
> Thank you very much for your help.

I do have a little problem, the machine I am using is a pretty old laptop and the cd drive does not work properly, I can't use it to boot. It does not have the option of booting from a USB drive either.

I installed ubuntu using UNetbootin from windows xp.

I am worried about losing my grub install because I wouldn't know how to boot the machine if it were to break.

In that case ... don't do it !!

Head over to [http://ubuntuforums.org/showthread.php?t=1195275&page=28](http://ubuntuforums.org/showthread.php?t=1195275&page=28)  and post the problem to drs305 - I can only think of him suggesting a way to move grub - but, as there is a danger of completely borking your machine - I'm not too sure what to suggest.

He'd deffinately be the one to ask - and, yes you can tell him I sent you, he'll curse at me later - lol

Ask him to have a look at this thread - it will save you retyping everything.

/edit ... don't need to - I will ask him !!!

Regards,

Phill.

---

### Post by presence1960 on 2010-01-25
> **Leshrac said:**
> Currently I dual boot windows XP and ubuntu 9.10. However, I am quite happy about my Ubuntu installation and I am starting to think about my windows xp install as a waste of hard drive space.

I wonder what's the best way to remove the windows xp install.

I have 3 partitions, windows being the first, ubuntu being the second and the third being ubuntu's swap.

I am not familiarized with the way the grub bootloader works so I am worried about breaking it if I just remove the first (winxp) partition via gparted and expand the second (ubuntu 9.10) fill the empty space.

Can anyone advise me on the cleanest and safest course of action?

GRUB is on the MBR usually which is a space before the first partition on a hard disk. So if you remove sda1 you will not touch GRUB for two reasons: sda1 is windows and does not have GRUB installed to it and it is not a linux partition with GRUB installed to the first sector of that partition.

Instead of expanding the ubuntu partition why don't you format the windows partition to ext3 or ext4 and use it (sda1) as a data/storage partition? That is another option.

If you expand sda2 to take the space from sda1 your GRUB should still be fine.

---

### Post by drs305 on 2010-01-25
I agree with presence that Grub 2 shouldn't be on the Windows partition and removing it should cause no boot problems if you are currently using Grub 2 to boot your machine. If you have concerns please download and run the boot info script which will tell us everything we need to know about your current setup:
[http://ubuntuforums.org/showthread.php?t=1291280]("http://ubuntuforums.org/showthread.php?t=1291280")

@ phil - there are lots of users a lot smarter than me when it comes to this stuff.  ;-)

---

### Post by presence1960 on 2010-01-25
> **drs305 said:**
> 

@ phil - there are lots of users a lot smarter than me when it comes to this stuff.  ;-)
Humility- that is an endearing trait & indicates strong character.

Don't sell yourself short though. Your how to on GRUB2 really helped me out tremendously. So I will say a big THANK YOU for sharing your knowledge.

---

### Post by drs305 on 2010-01-25
> **presence1960 said:**
> Humility- that is an endearing trait & indicates strong character.

Ah, you could have just praised me for speaking the truth. 

The fact is we've all learned a lot from the forum community.

---

### Post by jflaker on 2010-01-25
If the system is that bad, you could pull the drive and install it into a USB drive enclosure then access your data as sudo user...

You will likely need to chown and chmod, but your data will be accessible and don't forget to browse your hidden folders.

---

### Post by Leppie on 2010-01-25
> **presence1960 said:**
> GRUB is on the MBR usually which is a space before the first partition on a hard disk. So if you remove sda1 you will not touch GRUB for two reasons: sda1 is windows and does not have GRUB installed to it and it is not a linux partition with GRUB installed to the first sector of that partition.
i am not familiar with unetbootin, but hopefully it doesn't leave the same kind of mess as wubi does...
in any case i suppose that completely reinstalling grub2 wouldn't be a bad idea.

> **presence1960 said:**
> Instead of expanding the ubuntu partition why don't you format the windows partition to ext3 or ext4 and use it (sda1) as a data/storage partition? That is another option.

If you expand sda2 to take the space from sda1 your GRUB should still be fine.
i would go for the data/storage partition option. i am not 100% sure, but i think that grub actually saves a physical address as link in the mbr. if i am not mistaken, i think i've seen posts of people resizing their ubuntu partition and after modifying fstab and running update-grub ended up with a grub error upon reboot.

---

### Post by phillw on 2010-01-26
> **presence1960 said:**
> GRUB is on the MBR usually which is a space before the first partition on a hard disk. So if you remove sda1 you will not touch GRUB for two reasons: sda1 is windows and does not have GRUB installed to it and it is not a linux partition with GRUB installed to the first sector of that partition.

Instead of expanding the ubuntu partition why don't you format the windows partition to ext3 or ext4 and use it (sda1) as a data/storage partition? That is another option.

If you expand sda2 to take the space from sda1 your GRUB should still be fine.

Thanks presence, 
the general consensus is that he's okay to just reformat sda1 - You'll see on my earlier thread that I suggested using that partition to pop his /home directory onto. Assuming that his ubuntu is on sda3 (I'll make sure he checks) and the old win is on sda1 - the [Create a separate home partition in Ubuntu]("http://www.psychocats.net/ubuntu/separatehome")  would be easy for the OP to follow, as the OP just needs to swap round the references of sda3 and sda1 in that excellent tutorial, and skip the making a partition part of it. A useful thing to have, a seperate /home.

@jflaker - yes, I think in the situation he finds himself, getting a 2.5" usb disk caddy would be a good move. The older IDE ones (that he would need) are only about $10 these days.

Regards,

Phill.

---

### Post by Leshrac on 2010-01-26
Thanks everyone for your input.

From what I understand about what you guys said, grub is not actually stored inside the windows partition *and* grub should continue loading ubuntu undisturbed as long as ubuntu is still installed in the second partition.

So I could just format the fat32 partition as ext4 and follow the instructions on how to map it to /home and I would not need to touch grub's configuration at all?

I'll make sure to run the boot info script on the machine and post the info back to you as soon as I can get my parents unhooked from aisleriot solitaire.

---

