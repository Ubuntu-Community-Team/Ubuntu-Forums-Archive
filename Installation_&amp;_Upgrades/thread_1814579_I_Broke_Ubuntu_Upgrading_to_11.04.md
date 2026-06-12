---
title: "I Broke Ubuntu Upgrading to 11.04"
date: 2011-07-29
forum: Installation &amp; Upgrades
---

### Post by Dansid on 2011-07-29
Hi, I have no idea what to do from here.

I installed Ubuntu a few months back with a CD on my computer (on boot it gives the option of Ubuntu or Windows), and tried to update it today when it offered an upgrade to 11.04.

I said yes, yes, yes, it began installing and then asked how I wanted  to proceed with the Grub something to which I left the default option (something about leaving a local version installed where it was), it proceeded and said it needed to restart in order to finish installation. 

That was the last time I saw Ubuntu.  Now when I select Ubuntu (as well as safemode) from the start screen, I get the purple screen of flashing epilepsy. 

I have little to offer but my appreciation; can anyone help me get Ubuntu back on its feet, or wipe its presence from my computer so that I can start over?

---

### Post by Dansid on 2011-07-31
Anyone?

---

### Post by kptsuresh on 2011-07-31
it seems upgrade failed, try to remove the upgrade..

I am not sure but give a try..

go to recovery mode and try "apt-get -f install"

sudo apt-get *remove ubuntu*-desktop

then restart..

---

### Post by 2F4U on 2011-07-31
Can you get to a virtual console by pressing Ctrl-Alt-F1,2,3,.. If yes, try to look into dmesg to see if there are errors. It may also worth looking into .xsession-errors.

---

### Post by YesWeCan on 2011-07-31
> **Dansid said:**
> Hi, I have no idea what to do from here.

I installed Ubuntu a few months back with a CD on my computer (on boot it gives the option of Ubuntu or Windows), and tried to update it today when it offered an upgrade to 11.04.

I said yes, yes, yes, it began installing and then asked how I wanted  to proceed with the Grub something to which I left the default option (something about leaving a local version installed where it was), it proceeded and said it needed to restart in order to finish installation. 

That was the last time I saw Ubuntu.  Now when I select Ubuntu (as well as safemode) from the start screen, I get the purple screen of flashing epilepsy. 

I have little to offer but my appreciation; can anyone help me get Ubuntu back on its feet, or wipe its presence from my computer so that I can start over?

My guess is that you unknowingly left the original Grub boot program at the start of your disk. The Grub version changed with 11.04 and now the original Grub is incompatible with it.

The simple solution is just to install the Grub boot program again. You need an 11.04 live CD/USB of the same 32/64 version as on your HD:
boot live CD
[COLOR="Navy"]sudo fdisk -l[/COLOR] to determine the root/boot partition on your HD
[COLOR="Navy"]sudo mount /dev/sdxy /mnt[/COLOR]  where x is disk letter and y is your root partition number
[COLOR="Navy"]sudo grub-install --root-directory=/mnt /dev/sdx[/COLOR]

---

