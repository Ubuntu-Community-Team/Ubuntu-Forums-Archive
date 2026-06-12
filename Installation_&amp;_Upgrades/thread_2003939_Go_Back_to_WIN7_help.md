---
title: "Go Back to WIN7 help?"
date: 2012-06-14
forum: Installation &amp; Upgrades
---

### Post by Beno95 on 2012-06-14
i installed Ubuntu on my laptop along side Win 7. I want to go back to Win 7 only. I want to hard reset my computer back to factory settings so it can look like it did when I bought it. I tried pressing F8 and F10 when its starting but it only goes on GRUB and asks me to choice between Ubuntu, Memory Test, or Windows 7. I can figure out how to do it.

Can you guys and gals please help me out? I looked all over the internet cant find any situations like mine.

BTW: I don't want Ubuntu anymore just my original Windows 7, hard reset ed.

---

### Post by oboedad55 on 2012-06-14
> **Beno95 said:**
> i installed Ubuntu on my laptop along side Win 7. I want to go back to Win 7 only. I want to hard reset my computer back to factory settings so it can look like it did when I bought it. I tried pressing F8 and F10 when its starting but it only goes on GRUB and asks me to choice between Ubuntu, Memory Test, or Windows 7. I can figure out how to do it.

Can you guys and gals please help me out? I looked all over the internet cant find any situations like mine.

BTW: I don't want Ubuntu anymore just my original Windows 7, hard reset ed.

You just need to google for how to restore the Windows 7 MBR. Once that's done you can go into Windows and restore your partitions, or failing that boot into the LiveCD of Ubuntu and using Gparted do the same. I'm assuming you installed Ubuntu alongside Windows. If you installed using Wubi I believe all you need to do is uninstall Ubuntu through add/remove programs.

---

### Post by Mark Phelps on 2012-06-16
IF your PC came preloaded with Win7 and you have a (possibly hidden) partition on your drive (usually named Recovery or something like that), once you get the MBR restored, you should be able to then restore your PC to its original condition.

But ... you will have to look into the information that came with your PC to see how that is done.  This varies from one PC to another.

Some come with a "restore CD" -- which you boot into and then run a program to rewrite the Win7 install from a compressed image file contained in the Recovery partition.

Others use a special key combination that really boots you into WinPE -- and then does the same thing.

If you really want detailed help on how to restore a Win7 PC, you would do better going to a Windows 7 forum: sevenforums.com.

---

