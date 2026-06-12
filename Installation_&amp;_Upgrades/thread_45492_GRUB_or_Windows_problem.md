---
title: "GRUB or Windows problem?"
date: 2005-06-30
forum: Installation &amp; Upgrades
---

### Post by audaz on 2005-06-30
I have been using windows xp on my primary hd for a long time. I installed ubuntu several months ago and have enjoyed using it. Since yesterday though, I have had problems with windows. 

When I select windows xp from my grub menu, it starts to load, gets to the screen where the windows xp logo shows up with the little progress bar, and then a second later it auto-reboots. I can't get in there at all! Next time it loaded, I tried safe mode, but then after i was working in windows for about a minute or two, it automatically restarted itself again. 

I really need help if anyone knows what this could be. I don't know how it could be grub, since grub has been working fine for a while, but it's one of the things i'm thinking it could be.

Thanks for your help in advance.

---

### Post by rachii on 2005-06-30
sounds like your ubuntu install may have messed up your xp install.  i dont think it would be grub, because it sounds to me like grub is doing its job and letting you pick windows or linux then whichever one gets set on its way. its just that the windows wont boot itself. 

have you been using windows fine, then all of a sudden its not working.  or have you just been using ubuntu, and never realized that this was the case until now when you tried it?

---

### Post by mingus on 2005-06-30
Unlikely a grub problem.  Booting from grub to W$ is called "chain-loading", and literally means that grub issues a run command to the W$ C:\ntldr program and then grub quits - exactly the same as a vanilla W$ boot from the MBR.

To prove this out, get into Ubuntu and create a grub floppy boot disk.  The quick & dirty way is $sudo grub-install /dev/fd0.  There is also a good wiki HowTo on creating this floppy; I prefer this method.  Boot from that floppy to be sure it works.  Then boot from your XP install media in the Recovery console and at the prompt do:  >fixmbr.  This will overwrite grub and when you reboot you will go to W$ vanilla, grub completely out of the picture.  Use the boot floppy for Ubuntu until you fix the problem, and then reinstall grub to the MBR.

I've seen your W$ symptom from a variety of reasons:  Corrupted partition table, corruption in a system driver, system file not exactly where it is expected to be, broken filesystem chain, bad sector on a disk, failure in loading a core service, a file has been overwritten by another program, missing .dll, and infection.  Boot into Safe mode without networking, and do nothing but watch.  If it stays up, do a Run: eventvwr and look for errors.  If you can't get to diagnostics, and there is no evidence of hardware failure, you're prob looking at a repair install.

BTW, you don't have anything unusual in your configuration, like a drive overlay or LVM or RAID, etc?  There hasn't been a recent power failure or voltage surge?

---

