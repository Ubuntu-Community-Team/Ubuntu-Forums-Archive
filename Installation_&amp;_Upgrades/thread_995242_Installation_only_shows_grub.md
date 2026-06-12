---
title: "Installation only shows grub"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by Normajm on 2008-11-27
Hello,

New user, first install Ubuntu 8.1 on Dell T450 Hardware PIII w/512 mg ram, 40 gb hd.  I ran the standard install (guided option #2). Took out the CD after install and rebooted.  All that comes up is a prompt: grub>  

What do I do next?

Thanks.

JNM

---

### Post by caljohnsmith on 2008-11-27
How about booting your Ubuntu install CD again (Live CD), open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -l
```
And we can work from there if you want. :)

---

### Post by Normajm on 2008-11-27
Hi,

Thanks for the help.

I think something happened to the CD.  I rebooted with the CD in the drive, I get the Ubuntu menu, but when I select Try..without any change... I get a prompt that states Boot Loader  Live OK.  I press OK and nothing at all happens.  

Suggestions?

JNM

---

### Post by caljohnsmith on 2008-11-27
When you installed Ubuntu, did you use the "install Ubuntu" option at the first main menu of the CD, or did you do the "try without making changes", and then run the installer from the Ubuntu desktop? I would assume the former case since you can't seem to use the latter case. How about at the first main menu, select the "try without making changes," press F6 for more options, add "acpi=off" to the end of the strange text line that it shows, and then press enter to boot. If that doesn't work, instead try adding either "noapic" or "nolapic". Let me know if that works.

---

### Post by Normajm on 2008-11-27
Hi,

Sorry to report, but the suggestions didn't work.  I selected Try..., then pressed F6, got the boot string and typed apci=off at the end, nothing happened, deleted apci=off and typed noapic, nothing, changed noapic to nalpic, still nothing. 

The first time I put the CD in, I ran check CD for integrity, which passed, then I went right to install.

---

### Post by Normajm on 2008-11-27
Hi,

What do I do next?  I'm unable to get past the Ubuntu menu with the CD in the drive or boot the PC with it out of the drive.

Thanks.

JNM

---

### Post by Normajm on 2008-11-27
Hi,

Well, I switched the boot order from CD HD to HD CD, and, of course, it only came up to the grub prompt.  I switched to back to CD HD and then I was able to get a little further with the CD.  I selected Try... the chose acpi=off and got the following message: Kernel panic - not syncing: Fatal exception in interrupt.  Right before that line, there was something about bad EPI or EPI.  I tried noapic and nolapic with the same results.  Then I typed linux ide=nodma, and then the menu stopped interacting with the CD.  

Now that I know how to get the CD back working.  What can I do about about the Kernel panic message?

Thanks 

JNM

---

### Post by Normajm on 2008-11-28
Any suggestions?

---

