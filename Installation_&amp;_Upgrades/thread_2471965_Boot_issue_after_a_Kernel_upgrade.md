---
title: "Boot issue after a Kernel upgrade"
date: 2022-02-14
forum: Installation &amp; Upgrades
---

### Post by Wardner_Maia on 2022-02-14
Hello, I'm using Ubuntu 20.04 and after a Boot upgrade to the last release, I updated grub and it crashed. When I try to boot it shows an alert UUID=xxxxx does not exist. Dropping to a shell (initramfs) 

I used the USB boot repair and the result is: [https://paste.ubuntu.com/p/jNgXpdYWTV/](https://paste.ubuntu.com/p/jNgXpdYWTV/)

Many thanks for any help. 

Maia

---

### Post by oldfred on 2022-02-14
Report only shows your flash drive, no internal drives at all?

Did you update UEFI & it reset UEFI settings? That may turn AHCI off or other settings you had to change to use Ubuntu.

You do show nVidia, how did you install the nVidia driver? From Ubuntu repository which is preferred or directly from a download from nVidia, which requires updates with every kernel update, so not recommended.

What kind of drive?
Is it seen in anything? UEFI/BIOS must see it or else you have a hardware issue like loose cable or broken drive.

---

### Post by MAFoElffen on 2022-02-15
Please use the 'boot-info' script instead of the 'boot-repair' script... 

I would suggest using from the PPA shown below, from a LiveCD. Boot the LiveCD. Use "Try". Once it starts the Desktop in the Live environment, open a Graphical Terminal Session by clicking once on the Desktop, then pressing <Cntrl><T>
```

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt update
sudo apt install boot-info
boot-info

```
Then use Advanced > Upload to Pastebin...

Because yes, as oldfred noted, those results ares not showing anything from your "installed system" at all...

Afterwards, I would really like to get some system information from you and your system, so we can recreate those results, to improve 'boot-info' and 'boot-repair'. I'm sure oldfred will agree with me, as we both are involved with helping with that process with the maintainer/author.

---

### Post by Wardner_Maia on 2022-02-15
Hi oldfred and [COLOR=#000000]MAFoElffen, 

Thank you for the reply. At this moment I cannot follow your suggestion because my laptop now is booting from nothing even when I am at BIOS setup. I think it's an unfortunate coincidence and I'll fix this hardware problem to go back to the tests. 

Best Regards, [/COLOR]

---

### Post by oldfred on 2022-02-16
If you have fast start up on in UEFI settings, it often boots too fast to give you time to press keys to get into UEFI settings or UEFI boot menu.

You can often force a full startup and have just a second or two to press correct key to get into UEFI, by doing a full cold boot. That is all power down, remove mains, and hold power switch to remove any remaining power. If laptop also remove battery before draining system. Then connect system & reboot.

If UEFI Secure Boot on, you may not be allowed to boot from USB as that also is not secure. Then UEFI will have another setting to allow USB boot and/or allow full USB support.

---

