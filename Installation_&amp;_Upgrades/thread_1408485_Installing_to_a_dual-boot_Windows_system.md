---
title: "Installing to a dual-boot Windows system"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by sync00 on 2010-02-16
I'm currently dual-booting Vista and Win 7. Do I have to install Grub or can I continue to use the Windows boot loader?

---

### Post by darkod on 2010-02-16
You don't HAVE to, but it's better. Windows bootloader can't boot linux by default, but it can be done if you feel up to it.
Windows automatically combines the boot files if you have more than one version, so probably your vista and win7 files are combined. You can let grub install on the MBR and it will pick them up, probably as single entry. So you will first have to select that, and then you'll have option between vista and win7.
If you decide to boot with another bootloader, windows or easybcd, then and ONLY then install grub to the root partition of ubuntu, for example if the root is /dev/sda5, select grub to be installed on the partition, /dev/sda5. You need that to chainload to it, as far as I know.

---

### Post by Mark Phelps on 2010-02-16
> **sync00 said:**
> I'm currently dual-booting Vista and Win 7. Do I have to install Grub or can I continue to use the Windows boot loader?

Depends on HOW you are dual-booting today...

If you installed using Wubi (i.e., inside Windows), GRUB is not an option.  Ubuntu installed GRUB4DOS by default, in that setup, AFAIK, that's what you have to use.

If you installed to a separate partition, that begs the question of what you're using now to enable OS selection.  In this case, using GRUB, especially GRUB2, will provide you boot flexibility not available in MS Windows boot loader. But that flexibility is largely for non-MS Windows OSs.

Also, if you replace the MS Windows MBR with GRUB, and want to restore that in the future, MS has made that especially difficult to do -- requiring a Repair CD (or original install DVD) and up to three passes (because it replaces the MBR on the third pass). Leaving the MS Windows MBR alone and using something like EasyBCD avoids the MBR problem -- but it doesn't provide the customization and flexibility features of legacy GRUB or GRUB 2.

---

### Post by sync00 on 2010-02-16
I used EasyBCD and I'm happy with that for now.

I'll look into what advantages I would get from using Grub.

---

### Post by darkod on 2010-02-16
> **Mark Phelps said:**
> 
Also, if you replace the MS Windows MBR with GRUB, and want to restore that in the future, MS has made that especially difficult to do -- requiring a Repair CD (or original install DVD) and up to three passes (because it replaces the MBR on the third pass). 

Actually it seems that they haven't tried so hard to complicate things. Provided your windows boot process is OK (and grub wouldn't touch it during install), all you need is to boot the live desktop or the hdd ubuntu install and do:

sudo apt-get install lilo
sudo lilo -M /dev/sdX mbr

That installs a generic mbr on /dev/sdX disk and provided windows boot files are OK it makes windows bootable straight away. Works with XP, Vista and 7 as confirmed here.
Even for people new to linux this procedure seems easier than using windows repair cds. At least from the comments I've got here.

---

### Post by Mark Phelps on 2010-02-17
> **darkod said:**
>  ... Even for people new to linux this procedure seems easier than using windows repair cds...

Exactly ... it's easier to do this using Linux utilities than it is to mess with the MS Windows repair utilities.

---

