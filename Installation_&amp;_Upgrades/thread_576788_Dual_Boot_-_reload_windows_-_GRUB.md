---
title: "Dual Boot - reload windows - GRUB?"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by CallMeDerek on 2007-10-15
I have a dual boot system with Windows and Kubuntu installed on separate physical hard drives and am using GRUB to dual boot.  I need to reload windows with a complete reformat of that drive.
My concern is I believe GRUB is loaded on the MBR of the Windows drive – though I am not entirely sure of that fact.

If I boot off a windows install cd – launch the install and point it to reformat the windows drive I assume I will loose GRUB and the ability to boot to the second physical harddrive.

I am looking for guidance on how to proceed.

Is there a way to definitively tell what physical drive GRUB is on?
Is there an easy way to prevent loosing the GRUB dual boot setup whil reloading windows assuming it is on the MBR of the Windows drive?
Can I backup GRUB somehow or create a rescue MBR disk – Or I have found references of ways to reload GRUB from a CD boot – is that my best option?

Any advice would be appreciated – thanks in advance!

---

### Post by Herman on 2007-10-15
Hello CallMeDerek [B]
You need a [/B][Super Grub Disk]("http://supergrub.forjamari.linex.org/")those are free and only a small download.

Regards, Herman :)

---

### Post by CallMeDerek on 2007-10-15
K - that’s what i thought....

So simply boot of the windows install cd - reload it - finish the reboots etc...

Then when its done simply boot of this GRUB cd repair the GRUB/MBR and i am good to go...

Can it really be that easy?

---

### Post by Herman on 2007-10-16
> So simply boot of the windows install cd - reload it - finish the reboots etc...
Then when its done simply boot of this GRUB cd repair the GRUB/MBR and iam good to go...
Can it really be that easy?Yes, it's fairly easy with adrian15's  Super Grub DIsk, you just boot Super Grub Disk, get to the 'English Menu', and go 'Advanced'-->'GRUB'-->'Restore GRUB in Hard Disk (MBR), and then select 'Automatically Install', or you can use the manual option if the automatic one doesn't work.
The automatic option should scan you computer for a stage1 file for GRUB, and present you with a list if you have more than one Linux installation to choose from. You just select which Linux whose GRUB you want installed to MBR in your first hard disk, and Super Grub Disk will do it for you!  

There is another way to do the same thing if you have a Ubuntu Live CD, here's a link to a how-to about that, [                                                                  Re-install GRUB with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") eg; with Live CD. That's a good way to do it too, and not as difficult as you might think. 

You can also re-install GRUB in a similar fashion to the previous link from  [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") if you can get that up somehow, probably you would need to use Super Grub Disk for that too in the situation where Windows has taken over your MBR.

>  Is there a way to definitively tell what physical drive GRUB is on?Yes, when you are in Grub's Command Line Interface you can boot each hard disk by chainlaoding its MBR and see what happens, 
For example, to boot via your second hard disk's MBR, 
```
grub> root (hd1)
         
   grub> chainloader +1
         
   grub> boot
```(Your first hard disk is (hd0) to GRUB, so your second one is (hd1), and so on. You would have to try one MBR at a time.


```
Can I backup GRUB somehow or create a rescue MBR disk – Or I have found references of ways to reload GRUB from a CD boot – is that my best option?
``` Certainly you can do that, with a 'dd command, here's a link about that,  [MBR backup and restore]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd").

All those way are easy, just pick whicever one you like best. :)

Regards, Herman :)

---

