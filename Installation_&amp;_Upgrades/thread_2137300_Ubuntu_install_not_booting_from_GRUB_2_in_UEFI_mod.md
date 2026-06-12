---
title: "Ubuntu install not booting from GRUB 2 in UEFI mode"
date: 2013-04-20
forum: Installation &amp; Upgrades
---

### Post by Bliepo32 on 2013-04-20
Hey everyone,

I just got a new laptop (Medion Erazer X7821) with Windows 8 on it and wanted to dualboot with Ubuntu (note, this is a must, I will not remove Windows). When I start the installation, the Grub 2 menu appears, but no matter which option I select, the screen just goes blank and nothing happens. How can I fix this?

---

### Post by oldfred on 2013-04-20
Is this the grub from UEFI boot of live flash drive installer?

Do you have nVidia card? Then you need nomodeset which also works for some other video issues. But some systems also need other boot parameters.

With the UEFI grub menu, it is more like first boot after install and you have to manually edit linux line. Most show instructions show the BIOS boot which gives a menu, f6 and select nomodeset.

From grub menu press e to edit boot stanza, scroll down to linux line and change quiet splash to nomodeset.

Skip instructions on BIOS boot and it shows similar screens as part of a first boot.
 How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Gobtron on 2013-04-20
> **oldfred said:**
> Is this the grub from UEFI boot of live flash drive installer?

Do you have nVidia card? Then you need nomodeset which also works for some other video issues. But some systems also need other boot parameters.

With the UEFI grub menu, it is more like first boot after install and you have to manually edit linux line. Most show instructions show the BIOS boot which gives a menu, f6 and select nomodeset.

From grub menu press e to edit boot stanza, scroll down to linux line and change quiet splash to nomodeset.

Skip instructions on BIOS boot and it shows similar screens as part of a first boot.
 How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)



I have the same problem too. I changed "quiet splash" to "nomodeset". 

I don't see a black screen anymore, but the screen is all glitchy, and the laptop make an unusual humming sound

---

### Post by Bliepo32 on 2013-04-20
Thanks, will try that. It was the GRUB from the USB installer by the way.
EDIT: tried nomodeset, but it didn't work unfortunately :(

---

### Post by oldfred on 2013-04-20
Have you turned secure boot off, also turned fast boot off.

Not familiar with Medion. What UEFI/BIOS vendor is it.
 AMI (Aptio, AMIBIOS), Phoenix (SecureCore, TrustedCore, AwardCore) or Insyde (InsydeH20).

But I have not asked nor followed which systems use which vendor.

---

### Post by Bliepo32 on 2013-04-20
It's an AMIBIOS. Videocard is Nvidia Geforce GTX 680M. Turning off secure boot makes no difference. I haven't seen an option for fastboot, but perhaps I missed it. I'll check and report back in about 10 minutes.

EDIT: I disabled both fast and secure boot and tried things like nomodeset, noapic, and acpi_osi="Linux", but it all didn't work. BTW, thanks for all the help till now :) I hope the issue is resolvable, but I am growing doubtful.

---

### Post by oldfred on 2013-04-20
Usually that type of nVidia is Optimus or dual video which causes issues. But I do not know know exact settings to get it to work. I think some turn one or the other off to get it to boot.

 nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Switchable Graphics is killing my Ubuntu Experience - see post #9
[http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317)
Optimus
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)
Released 319.12 Beta April 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE)

---

### Post by Bliepo32 on 2013-04-20
The laptop does indeed have two video-adapters: intel HD graphics 4000 en the NVIDIA card. But there is no option to choose between the two, or to disable one. I was wondering, would it be possible to install 12.10 in Legacy mode, then repair GRUB and get it to work in UEFI mode? It seems it worked in this thread: [http://ubuntuforums.org/showthread.php?t=2100372](http://ubuntuforums.org/showthread.php?t=2100372)

---

### Post by oldfred on 2013-04-20
Another thread with similar issues.
[http://ubuntuforums.org/showthread.php?t=2137344](http://ubuntuforums.org/showthread.php?t=2137344)
But no resolution.

Some have installed in BIOS mode and used Boot-Repair to convert to UEFI. It uninstalls grub-pc and installs grub-efi.
       How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)

      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Bliepo32 on 2013-04-23
> **oldfred said:**
> Another thread with similar issues.
[http://ubuntuforums.org/showthread.php?t=2137344](http://ubuntuforums.org/showthread.php?t=2137344)
But no resolution.

Some have installed in BIOS mode and used Boot-Repair to convert to UEFI. It uninstalls grub-pc and installs grub-efi.
       How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)

      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Alright, I finally managed to find some time to try this. I set the BIOS to legacy mode and the Xubuntu 12.10 desktop ISO booted fine. Installation went without any problems. After that, I could boot into the new installation without any problems. I downloaded boot-repair as in the instructions, went to the advanced options and enabled the secure boot option and let it do it's job. After rebooting, I got a red screen saying there was a signature mismatch for secure boot, so I disabled it. After that, Grub came up, but I could not boot Xubuntu (although Windows booted fine from the Grub menu). I tried recovery mode, but it hangs as soon as it tries to load the initial ram disk. Could it be a driver problem or something?

---

### Post by oldfred on 2013-04-23
That can be video and/or other boot parameter that is needed. If it worked in live mode then it probably is video.

What video chip/card do you have. Often nomodeset works which you can add to linux line in grub menu. At grub menu use e and replace quiet splash with nomodeset. Recovery mode also uses nomodeset.

       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[URL="https://help.ubuntu.com/community/BootOptions"]https://help.ubuntu.com/community/BootOptions
[/URL] [http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

[URL="https://help.ubuntu.com/community/BootOptions"]
[/URL]

---

### Post by Bliepo32 on 2013-04-25
I tried using nomodeset, but it hangs at "Starting crash report submission daemon                  [OK]".

---

### Post by oldfred on 2013-04-25
Crash reports are not good. Does it say what is causing it? What version are you installing?

Some have reported that the very new released today version 13.04 also works well with new computers.

---

### Post by Bliepo32 on 2013-04-25
It hangs at boot and it is Xubuntu 12.10 64bit, which I installed in BIOS Legacy mode, then boot repaired and booting using UEFI mode. Because it hangs at boot, no error is displayed.

[img]https://dl.dropboxusercontent.com/u/16291507/2013-04-25%2014.25.53.jpg[/img]

---

### Post by oldfred on 2013-04-25
I do not know enough, but it may be additional kernel parameters or video issues.

Have you tried recovery mode?

---

### Post by LaCrem on 2013-04-26
Hey, here with a Medion Erazer x6823 and same problem. This laptop has nVidia Optimus with an Intel 4000 and a nVidia 670m. I have tried everything, deactivating secure boot, Intel Virtualization, nomodeset, noacpi, nolacpi, etc...
Live usb is booting when Legacy and nomodeset, UEFI mode is not booting either, I think it shouldn't be a video card compatibility problem cos is working in legacy, in fact you can install Ubuntu only in your laptop in Legacy mode, but I want to keep Windows 8 for gaming. I tried 12.10x64 and 13.04x64 and nothing, both freezing at the same point. Blank screen, it read the pendrive for 4 or 5 seconds and that's all.
Bios is American Megatrends too.
I have tried with other distros and exactly the same behaviour.
I think maybe could be any UEFI/digital sign incompatibility.

ED: In theory is the same system than the MSi GT/GX series.

---

### Post by CSNate on 2013-04-28
This sounds like an optimus issue.  I fixed the problem by adding nomodeset but also i915.modeset=1.

In /etc/default/grub set the GRUB_CMDLINE_LINUX_DEFAULT varliable to: quiet splash i915.modeset=1 nomodeset

It should look something like this:  ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1 nomodeset"
```

It worked on my Asus N56VJ and Ubuntu 13.04.

Basically, the way I understand it, you need to tell the Nvidia graphics to disable kernel mode setting, but you need to enable mode setting for i915 (Intel) graphics.

---

### Post by LaCrem on 2013-05-06
> **CSNate said:**
> This sounds like an optimus issue.  I fixed the problem by adding nomodeset but also i915.modeset=1.

In /etc/default/grub set the GRUB_CMDLINE_LINUX_DEFAULT varliable to: quiet splash i915.modeset=1 nomodeset

It should look something like this:  ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1 nomodeset"
```

It worked on my Asus N56VJ and Ubuntu 13.04.

Basically, the way I understand it, you need to tell the Nvidia graphics to disable kernel mode setting, but you need to enable mode setting for i915 (Intel) graphics.

Nah, still not working. If I use legacy mode is working, but not when UEFI. I think it should be a problem with digital signature and my UEFI Bios.

---

### Post by Bliepo32 on 2013-05-27
I finally managed to get it working. First, I installed Xubuntu in legacy mode. Next, I installed all updates & rebooted. After that, I installed bumblebee and rebooted again. Then I installed boot-repair to enable UEFI booting (it won't work if you enable SecureBootm so don't). Next, I rebooted, went into BIOS, changed settings to UEFI and disabled secure boot and it worked :)

Must have been some update or something that made things work. Anyway, I am happy that it works now.

---

