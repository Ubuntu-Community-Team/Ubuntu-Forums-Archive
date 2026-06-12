---
title: "GRUB installation failed"
date: 2017-02-05
forum: Installation &amp; Upgrades
---

### Post by jet-bundle on 2017-02-05
I have an 4-year-old HP Pavilion dm1 laptop which shipped with Windows 7, and a few months ago I replaced that with Ubuntu 14.04. I'm now trying to install Lubuntu 16.10 and failing, each time with an error message "The 'grub-pc' package failed to install into /target/. Without the GRUB boot loader, the installed system will not boot." Clicking OK then gives a choice of options "How would you like to proceed", but whichever option I choose clicking OK has no effect.

I've tried this several times. First I tried to replace the Ubuntu installation with Lubuntu (there were no files that I needed to keep); the next time few times I selected "something else" and specified partitions manually; then I installed Ubuntu 16.04.01 LTS successfully and tried to install Lubuntu alongside. For this last attempt I successfully resized the Ubuntu partition but still couldn't finish the Lubuntu installation. So right now I have a working Ubuntu installation, in a small partition, but no Lubuntu, which is what I really want.

I'm installing from ISO images on DVDs. I've tried both 64-bit and 32-bit versions of Lubuntu, and have checked the DVDs for errors. I've tried installing directly, and also from a try-out instance of Lubuntu running from the DVD. Any advice would be gratefully received.

---

### Post by oldfred on 2017-02-05
A 4 year old system was just when UEFI came popular with Windows 8, but some chose Windows 7 and that could have been UEFI.
And Windows with UEFI uses gpt partitioning.

So post this, if gpt then you need either the ESP - efi system partition or for BIOS a bios_grub partition:
sudo parted -l

Probably better to use the 64 bit version if only 4 year old system.

If you just need to reinstall grub.
       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System

[/URL]
 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]
[/URL]

---

### Post by jet-bundle on 2017-02-05
Thank you. The Boot-Info link is 
[http://paste2.org/kgdybeZH](http://paste2.org/kgdybeZH)

---

### Post by oldfred on 2017-02-05
You have BIOS/MBR with 16.04 in sda1 and 16.10 in sda6.

Boot-Repairs default fix is to just reinstall your 16.04 grub.
But in its advanced options should be the choice to choose operating system and drive to install boot loader into.
You can then try to install 16.10's grub into MBR. Not sure why during install it would have given errors.

You should also be able to boot 16.04, and run this to add a boot fo 16.10.
sudo update-grub

And if booted in 16.10 you can easily reinstall its grub to MBR directly.
       sudo grub-install /dev/sda

    But every update of kernel in 16.10 will require you to also boot 16.04 and rerun the update.
Or you can add a manual entry in 40_custom to always boot newest kernel.

If thinking of keeping multiple Ubuntu installs, often better to have smaller system partition of 20 or 25GB and large data partition for all your data that you can use in all installs.

---

### Post by yancek on 2017-02-05
What option did you us to install the bootloader when you installed Lubuntu?  Your boot repair output shows Ubuntu 16.04 on sda1 and Lubuntu 16.10 on sda6.  If you look at the grub.cfg file for Ubuntu on sda1, there is no entry for Lubuntu on sda6.  Have you tried booting Ubuntu and simply doing:  sudo update-grub.  You should not need Grub on the Lubuntu partition as Grub will find the kernel and initrd files and create a menuentry for Lubuntu.  The message you are seeing is generic as the installer doesn't know you already have an instance of Grub on another partition.

---

### Post by jet-bundle on 2017-02-05
Thank you, After sudo update-grub (in 16.04) I can now select 16.10 from the boot menu. But in 16.10 I get sudo: grub-install: command not found, so something isn't quite right. If you have any further advice then that would be gratefully received, but at least I can now make some progress.

---

### Post by oldfred on 2017-02-05
Are you copying & pasting this exactly?

```
sudo grub-install /dev/sda
```

Even spaces become important in terminal commands.

---

### Post by yancek on 2017-02-05
Best to copy and paste commands you are given such as the one above.  Entering an upper case letter where it should be lower case and the reverse will not work.  If you try a command and it fails, copy and paste the command you used here or wherever you post looking for help.

---

### Post by jet-bundle on 2017-02-06
I get the "command not found" message when pasting the command into the terminal window (copied from the code window in oldfred's post above).

---

### Post by yancek on 2017-02-06
In Lubuntu, I expect the sudo grub-install /dev/sda is failing because the Grub files needed were not installed during the installation of the system for whatever reason?  When you boot your Lubuntu and go to the /boot/grub directory, do you see all the various Grub files there?  I'm not sure why the Grub installation failed on Lubuntu and can't think of any simple way to fix that.

---

### Post by jet-bundle on 2017-02-06
There are four files in /boot/grub (gfxblacklist.txt, grub.cfg, grubenv and unicode.pf2) and three folders (fonts, containing unicode.pf2; i386-pc, containing 271 files, mostly *.mod; and locale, containing four files *.mo).

---

### Post by oldfred on 2017-02-06
Looks like you have at least most of grub.
Not sure why you would get command not found.

If grub not fully installed, you can reinstall it.
If booted into your system, just reinstall grub-pc (that is BIOS version).
If using Boot-Repair from other install, or live installer, you can in advanced options run the full uninstall/reinstall of grub from there.

       # purge old and reinstall new to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
sudo grub-install --recheck /dev/sda
sudo update-grub

---

### Post by jet-bundle on 2017-02-06
Thank you. I guess I can make my own way from here.

---

