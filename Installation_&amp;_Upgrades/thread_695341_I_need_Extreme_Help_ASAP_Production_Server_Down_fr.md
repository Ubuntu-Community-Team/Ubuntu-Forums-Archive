---
title: "I need Extreme Help ASAP Production Server Down from upgrade"
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by moos3 on 2008-02-12
Ok, I have a major problem... I needed to upgrade from 7.04 to 7.10.. did the upgrade and now I'm presented with the following on boot:

aic7xx: not mutlichannel peer found !
aacriad: Host adapter abort erquest (0,10,0)
accraid: host adapter rest request. SCSI Hang ?

check root = bootarg car /proc/cmdline
or missing doules, devices car /proc/modules ls /dev

ALERT! /dev/disk/by-uuid/823e31dd-8dc2-42bc-a451-912d27d6528e does not exit droppping to a shell!

Busybox v1.1.3 (Debian 1:!.1.3-5ubuntu7) built-in shell (ash)
enter 'help' for list of built-in commmandds

I'm completely open to ideas of why this hardware doesn't have a issue in 6.06,6.10,7.04 but in 7.10 it fails. I need to reemdy this quickly. Also all ideas and help would accepted as long as I dont have to rebuild the raid or reinstall 7.04 dude to the nature of this server handling all LDAP, SMB,DNS,WEB and VPN.

---

### Post by Whiffle on 2008-02-12
I did some googling.  DOes this server happen to be SMP or hyperthreading?  If so, that could be an issue:

[http://lists.us.dell.com/pipermail/linux-poweredge/2003-June/008261.html](http://lists.us.dell.com/pipermail/linux-poweredge/2003-June/008261.html)

I'll keep looking though.

---

### Post by moos3 on 2008-02-12
yes it has smp dual xeons 1.5ghz I think hyperthreading but I added that prameter to it and nothing.

---

### Post by Whiffle on 2008-02-12
Heres some about the aacraid driver having issues with firmware and card combinations.  Looks like you're not the only one.

[http://kerneltrap.org/node/3778?page=1](http://kerneltrap.org/node/3778?page=1)


apparently  noacpi   has helped some people as well...

---

### Post by moos3 on 2008-02-13
Update... Still not working. but got more information to possible figure out what is causing the issue. Kernel 2.6.22-14 fails to boot with the above error, kernel 2.6.20-16 boots but hangs at the kernel log deamon and gives error mdaadm: no devices listed in conf were found.  Anymore Ideas I also tried pci=noacpi and pci=noapci and noth and went into the bios and tried to disable the hyperthreading in the bios to see if that worked and nothing. like I said everything in kernel 2.6.20-16 starts up until it gets to started but kernel log daemon where it hangs, i can ping all the interfaces but I can't ssh into the server tho.

---

### Post by moos3 on 2008-02-13
bump, anyone know how to roll back to previous version?

---

### Post by moos3 on 2008-02-13
ok add the following in grub acpi=off and get this now
aic7xx: not mutlichannel peer found !
aacriad: Host adapter abort request (2,1,0,0)
SCSI3: Adaptec AIC7xxx EISA
	<AIC7899 Ultra160 >
Host adapter abort request (2,1,0,0)
SCSI 2:1:1:0: SCSI Device OffLined - not ready error recovery

Ideas?

---

### Post by moos3 on 2008-02-13
please move this thead to ubuntu Server please.

---

### Post by NullHead on 2008-02-13
It said that the uuid was off .. well I would remove the uuid and put in root=/dev/<device name> 

EDIT: although I don't know how well that will work on a raid array

---

### Post by moos3 on 2008-02-14
will try

---

