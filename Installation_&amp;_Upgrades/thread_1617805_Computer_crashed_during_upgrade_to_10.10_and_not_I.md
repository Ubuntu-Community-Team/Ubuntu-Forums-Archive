---
title: "Computer crashed during upgrade to 10.10 and not I cannot get login or the terminal p"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by defmer on 2010-11-09
I was upgrading from 10.04 to 10.10 when my laptop crashed due to a HW issue not related to upgrade. But now when I start 

1) The laptop, it boots up till the point GDM log in screen is displayed without any log-in option. The system does not respond to any keyboard or mouse actions.

2) when I try to recover (recovery mode), the boot process comes til a point where it says "Console: switching to color frame buffer device 180x56"

and the prompt just stays there. it does not not drop to terminal.

when I choose an older option in the grub, I do get dropped to initramfs prompt.

So please help me restore my machine. re-instillation is not an option as I have some data I need in the home directory. Thank you.

---

### Post by holiday on 2010-11-09
> **defmer said:**
> I was upgrading from 10.04 to 10.10 when my laptop crashed due to a HW issue not related to upgrade. But now when I start 

1) The laptop, it boots up till the point GDM log in screen is displayed without any log-in option. The system does not respond to any keyboard or mouse actions.

2) when I try to recover (recovery mode), the boot process comes til a point where it says "Console: switching to color frame buffer device 180x56"

and the prompt just stays there. it does not not drop to terminal.

when I choose an older option in the grub, I do get dropped to initramfs prompt.

So please help me restore my machine. re-instillation is not an option as I have some data I need in the home directory. Thank you.

This happened to me. Not with 10.10 but with another release. 

Using a LiveCD, I could still access my data directories and pull them onto a USB drive. Then I formatted the drive, re-installed, loaded my data back in and all was well.

The problem is probably in your boot partition. The rest of your disc is ok.

---

### Post by defmer on 2010-11-09
I tried to do that, but my home folder was/is encrypted and so I cannot copy it either. I tried to use encrypt-mount-private. but I just got an error saying that the folder is not setup properly.

so is there any way to mount/access the encrypted home folder?

---

### Post by konakid on 2010-11-09
I was doing a software install and mine crashed and it did similarly. I'm not quite sure how I did it but there is a way to access terminal before you even boot up. I typed 'sudo apt-get install' and it said I had a previous install of something which hadn't finished and it finished the install and it worked fine. Sorry I can't remember how I got to terminal. I think there was an option in the boot menu.

---

### Post by sikander3786 on 2010-11-10
Here is a workaround to manually mount encrypted home directories.

[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually)

Also this one,

[http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/](http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/)

---

