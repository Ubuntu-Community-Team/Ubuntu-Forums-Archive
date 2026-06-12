---
title: "windows and ubuntu linux grub bootup configuration"
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by ARBE on 2008-10-08
hi,

i am encountering some issues i am not exactly expert in:

- multi boot system disaster recovery
- windows and ubuntu linux bootup configuration
- grub bootup configuration


my situation is:
boot up problems on a multiboot windows xp and ubuntu linux harddrive.

what i did:
---------------
creating data images for recovery
-------------------------------------
i wanted to do data images ewith acronis true image 8 under windows xp.
it seemed that to back up only the windows xp system partition would not be enough, since grub bootmanager modified the bootup sequence in a way that you also need the linux partition with the boot/grub directory and the bootup files.

attempt to fix corrupt linux file system
-------------------------------------
so i tried to image the two linux partitions via windows xp, which would have been possible, but there was the message that the linux partition file system was corrupt and i needed to run a fsck on linux first.
that is what i did, but i probably somehow got a conflict doing fsck while linux was running.
i probably should have used the ubuntu linux live cd to startup with and then apply the fsck command from there to the non-operating ubuntu linux partition.
instead i applied fsck on the running linux from itself ... which resulted in a non-bootable state for both systems. 

bootup error message
-------------------------------
GRUB Loading stage 1.5

GRUB loading, please wait ...
Error 17
--------------------------------------------------------
and after that, the system halts, no bootup !
--------------------------------------------------------

searching the internet for advice
----------------------------------------------------------
now! dont panic, now we have the us keyboard layout which is different than ours ... ubuntu live dvd startup, surfing on the web with ubuntu running from dvd, looking for the suitable procedures to save the grub bootup procedure ...

i get tons of manuals, particular linux commands to mount the linux boot directory and to configure the grub startup choice menu file. quite a lot of help requests in newsgroups and forums, but not what i am looking for ...

my questions are:
-----------------------------------------------------------
1. what changes does grub do when installed with ubuntu linux to the windows xp partition and data (same drive, different partitions) ?

2. how can i undo these changes for a normal standard windows xp bootup procedure, without grub and linux ?

3. once installed, how can i repair grub and a maybe dammaged ubuntu linux, operating at both the windows xp and the linux partition ?

4. imean, i could fix everything by wiping my harddrive, reinstalling windows xp and then ubuntu to fix the problem.
that would take me about 15-20 minutes for the windows basic installation and about 30 minutes for the ubuntu basic installation.

5. but then, i still would not know how to fix the bootmanager section !
these installations were improved and added with updates and applications during 6 months, which lets you wanting to know the repair methods, rather than the restart and re-install method, which of course may make more sense in non-repairable cases.

6. thats the news for now, i am reading the grub manual, takes some time ....

7. i will have to deal with bootmanagers in the future, also on other system platforms, since now, the mac is fast and it can run windows and linux too ...... by the way, what is the recommended universal bootmanager software for mac and pc now ?

8. please send useful comments to [email]aarberger@gmail.com[/email]
thankyou !

---

### Post by caljohnsmith on 2008-10-08
> **ARBE said:**
> 
so i tried to image the two linux partitions via windows xp, which would have been possible, but there was the message that the linux partition file system was corrupt and i needed to run a fsck on linux first.
that is what i did, but i probably somehow got a conflict doing fsck while linux was running.
i probably should have used the ubuntu linux live cd to startup with and then apply the fsck command from there to the non-operating ubuntu linux partition.
instead i applied fsck on the running linux from itself ... which resulted in a non-bootable state for both systems. 

Yes, unfortunately you are exactly right; you should never run fsck on a file system that is mounted, so you can't run fsck on a file system that you are currently using. Doing the fsck from the Live CD would have been the way to go. 

> **ARBE said:**
> 
my questions are:
-----------------------------------------------------------
1. what changes does grub do when installed with ubuntu linux to the windows xp partition and data (same drive, different partitions) ?

Grub won't do anything to the Windows partition itself unless you accidentally install Grub to the boot sector of the Windows partition instead of the MBR (Master Boot Record) of the HDD. 
> **ARBE said:**
> 
2. how can i undo these changes for a normal standard windows xp bootup procedure, without grub and linux ?

You can run "fixmbr" from the Windows Install CD to put a Windows boot loader in the MBR, and that should be sufficient. If you accidentally installed Grub to the boot sector of your Windows partition like I mentioned above, you can run the "fixboot" command to fix that. 
> **ARBE said:**
> 
3. once installed, how can i repair grub and a maybe dammaged ubuntu linux, operating at both the windows xp and the linux partition ?

Since you ran that fsck on you Linux partition while it was mounted, I think your best bet is to reinstall Linux at this point. If you have valuable data you want to recover, you can use programs like "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")".

Let me know if you have more questions, but personally I think reinstalling Ubuntu is the best option at this point.

---

### Post by ARBE on 2008-10-08
thanx for your hints, was screenreading and trying the stuff.

1. i think the edubuntu linux partition is definitely not working anymore.
during automated installation, i probably installed the grub filesystem into the windows mbr (stage 1). 
i mean all these steps are not that easy to handle w/o a detailed description.

2. i tried your hints, what worked is the mbr creation with the original windows install cd, with "fixmbr".

3. i am currently in a system upgrade situation, since as usual there is no more or limited support for older versions.
then, if you have some hints on which multiboot manager to use on a mac pro (mac osx 10.5, windows xp, linux, ...).
there is also the possibility to use full disk encryption and a windows native installation w/o bootcamp ...?!

anyway, that would be useful to have an easy-fixable and reliable multiboot starter software plus full disk encryption.

thx again and best regards
ARBE

---

