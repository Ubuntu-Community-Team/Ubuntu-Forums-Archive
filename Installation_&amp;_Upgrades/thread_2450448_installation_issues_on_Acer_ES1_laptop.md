---
title: "installation issues on Acer ES1 laptop"
date: 2020-09-13
forum: Installation &amp; Upgrades
---

### Post by stomatopod on 2020-09-13
Hey there,

So i know there's no shortage of threads on issues with installing linux on Acer laptops... but here's another one. 

I've installed Lubuntu 20.04 onto the laptop, but when it comes time to boot it without the bootable USB device, I get the "Checking media... [Failed]" loop issue.

I just ran boot-repair which didn't seem to change the outcome. I've changed the boot order in the BIOS settings as recommended in Boot-repair and tried adding the EFI as a trusted source (I've run out of options to add now, but when i tried selecting the Shim file as the latest trusted EFI file, it said that it already existed). The boot repair paper file can be found here: [https://paste.ubuntu.com/p/WmGJNYjPWG/](https://paste.ubuntu.com/p/WmGJNYjPWG/).


Any help or suggestions would be greatly appreciated!

Cheers,

-Scott

---

### Post by oldfred on 2020-09-16
Line 34: 
> Boot0000* Unknown Device: 


To see that without Boot-Repair
sudo efibootmgr -v

Make sure your UEFI is the most current version available from Acer. 

That means you have not set trust and named it to whatever you want, but usually just "ubuntu".

Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[https://community.acer.com/en/categories/predator](https://community.acer.com/en/categories/predator)
Acer Travelmate B117 (success - after some UEFI boot troubles) Trust related
[https://forum.siduction.org/index.php?topic=6272.0](https://forum.siduction.org/index.php?topic=6272.0)

---

### Post by stomatopod on 2020-09-20
Hey,
Thanks for taking the time to help out. I followed some of those links to get some ideas. What ended up helping me (and i don't know if all the steps necessarily helped, but at least ONE of them did!) was setting a password for the supervisor in the BIOS settings, and then deleting all the secure boot options, then adding shim.x64 as a new trusted EFI file and pushing it to the top of the boot priority list. 

Bam, done. I now have a working laptop!

Thanks again for your help. 

Cheers,

-Scott

---

### Post by oldfred on 2020-09-20
Glad you got it working.
You can change to solved.

---

