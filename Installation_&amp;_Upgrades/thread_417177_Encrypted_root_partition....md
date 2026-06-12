---
title: "Encrypted root partition..."
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by quark_77 on 2007-04-21
Hi All,

A couple of questions regarding encrypted root partitions. First though my current unencrypted setup:
[LIST]
[*]/dev/sda9 = swap
[*]/dev/sda10 = /boot (ext3)
[*] /dev/sda11 = / (XFS)
[*] /dev/sda12 = /home (XFS)
[/LIST]
Other partitions exist on my disk, sda1 = C: (win) sda5-8 = windows partitions, sda3 = recovery. Now my questions:
[LIST=1]
[*] Can I encrypt my root & home partitions in place? Or must I use the livecd as described on the Ubuntu help? Ideally I'd like not to have to reinstall Feisty...
[*] Can I integrate my TPM (1.2) into this security solution?? I have thinkfinger running fingerprint authentication already - I'm wondering if the TPM can protect against tampering as it does under windows (XP via lenovo client security solution).
[*] Which way do I go about implementing an encrypted root (no smartcard reader!)? loop-aes? LUKS? Some other method?
[*] Is there a noticeable effect on disk read-write speeds? Or battery life on laptops?
[/LIST]

Thanks for all your help - I'm mostly looking for information, I suspect the answer to Q1 is no you have to start from scratch and if this is the case I'm going to put this idea on the back burner until Gutsy Gibbon.

Quark_77

---

### Post by docomo on 2007-04-21
I can't answer all your questions but here goes:

3. I would go with LUKS which is common and relatively easy.

4. There is a noticeable effect on disk speeds, but it's not that bad. That is, I don't know how great the effect is if you actually measure it, but it doesn't feel slow.

---

### Post by quark_77 on 2007-04-22
Hi Domoco,

Thanks for the advice, LUKS seems to be the popular choice so I'm likely to go with that.

I'm still wondering if I have to reinstall? If so, is there a way to use the LiveCD and not install from the network? That is, I don't want to type:
```
sudo apt-get install ubuntu-desktop
```
and run that down my internet connection!! Other utilities are fine, such as cryptsetup.

Thanks again for all your help,

Quark_77

---

### Post by Kopfgeldjaeger on 2007-04-23
> **quark_77 said:**
> Hi Domoco,

Thanks for the advice, LUKS seems to be the popular choice so I'm likely to go with that.

I'm still wondering if I have to reinstall? If so, is there a way to use the LiveCD and not install from the network? That is, I don't want to type:
```
sudo apt-get install ubuntu-desktop
```
and run that down my internet connection!! Other utilities are fine, such as cryptsetup.

Thanks again for all your help,

Quark_77
You can encrypt your whole system (/, maybe /home, but not /boot) with a live cd. But you should have an extra partition to save the data on / and /home temporary. Or you can save the /-data on /home, and the other way around. It's really easy with Feisty. Maybe this (German) tutorial helps you:
[http://forum.ubuntuusers.de/topic/86498/](http://forum.ubuntuusers.de/topic/86498/)
You should only have to look at the commands and the text (where do we work now, which file should be edited). 

4. I do not notice anything... It even seems a bit faster than before ^^

greetings

---

### Post by quark_77 on 2007-04-25
Hi Kopfgeldjaeger,

If what you are saying is correct I can take my current setup and have an encrypted setup. From what I understand from your link and the English ones I've found, Encryption *IS* a destructive process, although I can move my 2.5GB root partition to a temporary location (not RAM obviously) and the same with home, encrypt, then restore, from the LiveCD? That would indeed solve my problem AND keep the existing setup in place, which is necessary as I'm fed up of re-installing...

Thanks for your link, I can follow the German just about... sadly I don't speak German but I do speak French.

This is going to take some time (root drive=2.5GB home 500MB) and requires a bit of re-partitioning so I will post again when I've decided what I'm doing, thanks for your help!!

Quark_77

---

### Post by quark_77 on 2007-04-26
OK everyone, having got it wrong the first time and thereby stuffing up feisty I re-installed with the partitions in the correct places. However, despite having a working root partition formatted with luks and containing an XFS file system that I can access from my unencrypted system I don't seem to be able to boot the Encrypted one.

The kernel spits out its usual stuff, then writes this:
[4.072000] Uniform CD-ROM Driver Revision: 3.2

Taking a look at /proc/kmsg and /var/log/dmesg confirms this happens as part of the normal boot sequence although what it does afterwards I don't know. I've attached that portion of the log to see if any of you can help?
```
[    7.396000] ata6: port disabled. ignoring.
[    7.400000] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GMA-4082N CX08 PQ: 0 ANSI: 5
[    7.400000] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[    7.424000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    7.424000] Uniform CD-ROM driver Revision: 3.20
[    7.424000] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    7.712000] Attempting manual resume
[    7.712000] swsusp: Resume From Partition 8:9
[    7.712000] PM: Checking swsusp image.
[    7.712000] PM: Resume from disk failed.
[    7.720000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[    7.720000] SGI XFS Quota Management subsystem
[    7.740000] XFS mounting filesystem sda11
[    7.864000] Ending clean XFS mount for filesystem: sda11
[   19.020000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.024000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.120000] Linux agpgart interface v0.102 (c) Dave Jones
[   19.200000] agpgart: Detected an Intel 945GM Chipset.
[   19.216000] agpgart: AGP aperture is 256M @ 0x0
```

I have edited /etc/initramfs-tools/modules to contain dm_crypt, dm_mod, sha256 and aes_i586. I have updated initramfs to use these modules (I think I have anyway) I'm going to try adding XFS to that list although why Ubuntu wouldn't compile it into the kernel is beyond me. Can anyone tell me what that cdrom driver is, I'll put that in the initramfs too.

Unfortunately, the log on my encrypted partition is just the one I copied there...

Any help would be appreciated, I'm half way there which is frustrating!!

Quark_77

---

### Post by quark_77 on 2007-04-27
Update on problem...

When the boot process freezes, I am able to press ctrl+c and be dropped into busybox the (initramfs) prompt. From here, I can issue cryptsetup commands and thereby mount the root partition. For whatever reason, the scripts created in /usr/share/initramfs-tools aren't doing this. Editing cryptsource=my encrypted device causes the system to freeze... I'm going to have to look into this in more detail.

Quark_77

---

### Post by Kopfgeldjaeger on 2007-04-27
Maybe this helps you:
[http://ubuntuforums.org/showthread.php?t=420182&highlight=feisty+luks](http://ubuntuforums.org/showthread.php?t=420182&highlight=feisty+luks)

:)

---

