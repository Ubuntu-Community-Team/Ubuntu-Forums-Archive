---
title: "Can't Boot into Unbuntu, help please :)"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by mmacintyre on 2007-02-10
Hi,

I am trying to complete a dual boot Ubuntu and WinXp machine.  I was able to get all the way through setting up and installing Ubuntu.  The only issue I had was GRUB was installed on the MBR, and I still wanted to keep using the Windows boot loader (The instructions I was following said I would be able to choose where I wanted to install Grub but the option never came up it just installed it directly to the MBR).  So, I ran 'fixmbr' from the winxp boot disk and obviously that fixed the the issue, however the only problem is I have no way to get back into Ubuntu.

Does anyone know what I can do to help fix the situation? Ubuntu appears to be installed but there is no way to get to it, do I just have to add a line to boot.ini or do I need to install Grub somewhere again? or Do I need to reinstall Ubuntu again?  

I have checked numerous other posts but can't seem to find anything that has this issue.

I am almost there... any help would be great

thanks for the support,

Mike

---

### Post by max.diems on 2007-02-10
You'll probably have to add a line to pass control to GRUB (after reinstalling GRUB). Why do you want to use boot.ini anyway?

---

### Post by umuntu_ngabantu on 2007-02-10
[QUOTE=mmacintyre;2133830]Hi,

I am trying to complete a dual boot Ubuntu and WinXp machine.  I was able to get all the way through setting up and installing Ubuntu.  The only issue I had was GRUB was installed on the MBR, and I still wanted to keep using the Windows boot loader (The instructions I was following said I would be able to choose where I wanted to install Grub but the option never came up it just installed it directly to the MBR).  So, I ran 'fixmbr' from the winxp boot disk and obviously that fixed the the issue, however the only problem is I have no way to get back into Ubuntu.


Mike, 

Are you by any chance able to get into Winxp? If not, are you getting a "grub 17"?

---

### Post by mmacintyre on 2007-02-10
Hi, I can still get into WinXP no problem it is like Ubuntu is not even there.

The reason I still want to use the Windows boot loader is my family uses the computer and I thought it would be better if I made a few changes to the current setup, when I installed Grub it made ubuntu the default choice, so I thought it would be easier to use the windows boot loader.

thanks for the quick replies.

Mike

---

### Post by andrian.ivanov on 2007-02-10
:)

---

### Post by mikewhatever on 2007-02-10
I do not know how to boot Ubuntu without a boot loader of some kind, since Windows can't see Ubuntu partition at all. Can you post the link to the instructions. 
It looks like the easiest way to achieve what you want, (dual boot Ubuntu & XP) it to install GRUB to the MBR. After both OSs are bootable, you can customize GRUB menu, so that Windows boots by default, and you can still boot Ubuntu if needed. You can also hide GRUB menu, so that no one actually knows there is another OS installed.
Here is a [GRUB GUIDE](http://users.bigpond.net.au/hermanzone/p15.htm) to consult, just in case, and you're welcome to post back if any more help is needed.

---

### Post by Rab22 on 2007-02-10
> **mmacintyre said:**
> Hi, I can still get into WinXP no problem it is like Ubuntu is not even there.

The reason I still want to use the Windows boot loader is my family uses the computer and I thought it would be better if I made a few changes to the current setup, when I installed Grub it made ubuntu the default choice, so I thought it would be easier to use the windows boot loader.

thanks for the quick replies.

Mike

I would just change GRUB to default to Windows.  Then inform them that when they see the selection screen, not to change anything.

You can do that by editing your /boot/grub/menu.lst and changing the default.

---

### Post by Snowbat on 2007-02-10
You can add Ubuntu to your Windows bootloader.
[http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why](http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why)

To do this from your current situation, you'll need to:

[LIST=1]
[*]Install GRUB in the first sector of your Ubuntu /boot partition (boot from a Live CD, mount your boot partition,  chroot to your boot partition, run GRUB to install the GRUB bootloader to the first sector of your Ubuntu /boot partition)
[*]Image the first sector of this partition to a file and copy the file to Windows C:\
[*]Modify Windows' boot.ini to add an entry for Ubuntu and a pointer to this file
[/LIST]

Sorry I don't have specifics how to do this in Ubuntu - I'm a Mandriva user who is not yet familiar with Ubuntu.

---

### Post by clickwir on 2007-02-10
Do like RAB22 said, use GRUB just have the Windows partition as the first(default) one and then your family doesn't have to do anything to get into windows.

GRUB is much better than using the windows boot loader.

---

### Post by max.diems on 2007-02-10
It may also be possible to hide the GRUB prompt to those who aren't looking.

---

### Post by mmacintyre on 2008-02-21
thanks for all the help

---

