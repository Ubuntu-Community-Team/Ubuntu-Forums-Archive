---
title: "Smooth Install But Blank Screen After Reload..."
date: 2016-12-24
forum: Installation &amp; Upgrades
---

### Post by utnubu4 on 2016-12-24
Hey folks,

I have used ubuntu before on a old laptop, I had issues with that old laptop so I bought a cheap one for the time being. I installed ubuntu 16.04 with no apparent issues. I then performed the restart, entered my BIOS, and changed the boot order from USB to eMMC. I saved the changes exited and the Acer screen came up. After the Acer screen, the usual ubuntu load screen appeared with "ubuntu, ubuntu advanced options" ect. I hit the ubuntu option and all I get is a blank black screen that never changes...no matter how long I wait.

I have attempted to reinstall many times but unfortunately the outcome is the exact same result. I even attempted to reinstall alongside the ubuntu that was already installed and tried to load both options at the ubuntu screen.

My laptop is a acer aspire ES11, 1.60ghz, 32gb eMMC and 4gb RAM.

Any help and advice would be highly appreciated, thanks.

---

### Post by DuckHook on 2016-12-24
Try nomodeset as one of your boot parameters. Instructions can be found in this old (but still relevant) thread: [https://ubuntuforums.org/showthread.php?t=1613132](https://ubuntuforums.org/showthread.php?t=1613132)

Please follow the instructions towards the end of the first post.

Also try booting into the "try without installing" environment on the LiveUSB.

Also try <Ctrl>+<Alt>+<F1> to see if a proper TTY comes up.

I may not be visiting the forums much over the next few days, but the above can at least get you started.

---

### Post by utnubu4 on 2016-12-24
Thank you very much for the reply DuckHook!

I have just solved the issue and I am currently using ubuntu without the live USB.

The mistake I made was, I changed from UEFI to legacy...So I changed it back to UEFI, and in the BIOS security settings created a password which in turn allowed me to access the UEFI settings. I then had to allow ubuntu access under these settings.

Merry Christmas :)

---

### Post by DuckHook on 2016-12-24
Very happy that you found the problem. It seems that Santa may have had a present for you!

Merry Christmas to you too.

*Please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

