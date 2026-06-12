---
title: "Ubuntu and Fedora 38"
date: 2023-07-12
forum: Installation &amp; Upgrades
---

### Post by vasya99 on 2023-07-12
HI,

I have latest Ubuntu installed. 
After installing Fedora I reboot and first time I see grub menu and can  choose Fedora and boot but if I reboot second time Fedora disappear from  the boot menu and I can boot only Ubuntu again.

Please help me

---

### Post by guiverc on 2023-07-12
It's helpful if you're very specific. By *latest Ubuntu* I take it you mean Ubuntu 23.04 or the 2023-April release of Ubuntu, but you've not said if Desktop or Server. I'll assume desktop as that's what I'm most familiar with.

**1. Boot method**

You didn't specify if they share the same disk, are on different disks, and if they were installed in the same mode (ie. both *legacy*, or both* uEFI* as that really matters, where you expect only one OS to boot if they were installed in different modes).  If you installed one OS in uEFI & the other in BIOS, you'll find you need to change a *firmware/BIOS *setting to boot the other OS in my experience.

**2. Grub changes**

Grub which is used (*by default*) on both Fedora & Ubuntu systems should automatically detect the other OS in my experience. however [a change was made with grub 2.06]("https://lists.ubuntu.com/archives/ubuntu-devel/2021-December/041769.html") where that is *not* the default.. My own Fedora happily detects my other OSes (openSuSE & Ubuntu) without issue, but I can't recall if I changed the Fedora default or not.. as whilst Ubuntu reverted the behavior back to the prior standard, other OSes did not, and thus this maybe your issue (*my Debian install on upgrades often drops my Ubuntu from its lists*).  This grub change maybe something to look at.
[B]
3. File system choices[/B]

Another problem I've experienced relates to the *file-systems* used for install. By default OpenSuSE defaults to *btrfs* which non-OpenSuSE system do not usually default to, and it can make detecting other OSes problematic.. so I'd check what *file-systems* you opted to use for your systems, as that can make a difference. You can work around issues like *btrfs* (*as I did for many years, before I stopped using it a default*).

Those are what I'd check for, or my thoughts on what you wrote.  Sorry it won't be very helpful, but I offer it in hopes it'll provide some search detail.

---

### Post by Rubi1200 on 2023-07-12
Hi and welcome to the forums :-)

Probably the easiest way for us to help you sort this out would be to post the results of the boot info script. See link in my signature, choose the option to create a summary report. Please do not try and repair yet.

Thanks.

---

### Post by vasya99 on 2023-07-12
[QUOTE=guiverc;14150229]It's helpful if you're very specific. By *latest Ubuntu* I take it you mean Ubuntu 23.04 or the 2023-April release of Ubuntu, but you've not said if Desktop or Server. I'll assume desktop as that's what I'm most familiar with.\

I have Ubuntu desktop and Ubuntu desktop LTS

**1. Boot method**

You didn't specify if they share the same disk, are on different disks, and if they were installed in the same mode (ie. both *legacy*, or both* uEFI* as that really matters, where you expect only one OS to boot if they were installed in different modes).  If you installed one OS in uEFI & the other in BIOS, you'll find you need to change a *firmware/BIOS *setting to boot the other OS in my experience.

They are on the same disk, both uEFI

**2. Grub changes**

Grub which is used (*by default*) on both Fedora & Ubuntu systems should automatically detect the other OS in my experience. however [a change was made with grub 2.06]("https://lists.ubuntu.com/archives/ubuntu-devel/2021-December/041769.html") where that is *not* the default.. My own Fedora happily detects my other OSes (openSuSE & Ubuntu) without issue, but I can't recall if I changed the Fedora default or not.. as whilst Ubuntu reverted the behavior back to the prior standard, other OSes did not, and thus this maybe your issue (*my Debian install on upgrades often drops my Ubuntu from its lists*).  This grub change maybe something to look at.

Fedora detects Ubuntu, Ubuntu does not detect Fedora
[B]
3. File system choices[/B]

Another problem I've experienced relates to the *file-systems* used for install. By default OpenSuSE defaults to *btrfs* which non-OpenSuSE system do not usually default to, and it can make detecting other OSes problematic.. so I'd check what *file-systems* you opted to use for your systems, as that can make a difference. You can work around issues like *btrfs* (*as I did for many years, before I stopped using it a default*).

All systems are ext4

---

### Post by vasya99 on 2023-07-12
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

Probably the easiest way for us to help you sort this out would be to post the results of the boot info script. See link in my signature, choose the option to create a summary report. Please do not try and repair yet.

Thanks.

Thank you. I will run script tonight.

---

### Post by tea for one on 2023-07-12
> **vasya99 said:**
> Fedora detects Ubuntu, Ubuntu does not detect Fedora
Your Ubuntu grub configuration may need to be edited.
```
sudo nano /etc/default/grub
```

```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false - [COLOR="#0000FF"]Do you have this parameter?[/COLOR]
```
The default for Ubuntu 22.04 is GRUB_DISABLE_OS_PROBER=true

Don't forget to run [COLOR="#0000FF"]sudo update-grub[/COLOR] to save the new configuration.

---

### Post by vasya99 on 2023-07-12
> **tea for one said:**
> Your Ubuntu grub configuration may need to be edited.
```
sudo nano /etc/default/grub
```

```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false - [COLOR=#0000FF]Do you have this parameter?[/COLOR]
```
The default for Ubuntu 22.04 is GRUB_DISABLE_OS_PROBER=true

Don't forget to run [COLOR=#0000FF]sudo update-grub[/COLOR] to save the new configuration.

Thank you very much. The problem is solved. I do not understand why os probe is disabled by default

---

### Post by oldfred on 2023-07-12
Security reasons:

[https://www.phoronix.com/news/Ubuntu-22.04-Multi-Boot-Changes](https://www.phoronix.com/news/Ubuntu-22.04-Multi-Boot-Changes)
> The issue at hand is GRUB 2.06 has disabled os-prober by default as the  feature for GRUB to detect other installed operating systems. OS-Prober  is disabled by default upstream now due to security issues over it going  through and mounting all partitions on the system when checking them  for other operating systems and that could be taken advantage of if  making use of file-system vulnerabilities. 


I have always preferred to turn off os-prober & add boot stanza to 40_custom. I have a lot of partitions and update where os-prober runs are very slow. With it off updates are much quicker. 
Ubuntu has a link to latest kernel so you can add a boot stanza using that and never have to update it. Not sure about other distributions.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

