---
title: "Dual boot problem with windows 8"
date: 2013-04-10
forum: Installation &amp; Upgrades
---

### Post by bearbear008 on 2013-04-10
I succeeded in installing ubuntu along with windows 8. Now , I want to add ubuntu boot entry into windows 8 boot menu. I installed easy bcd and made windows 8 default option and added ubuntu entry . When I restarted , first I'm getting ubuntu boot menu, then windows 8 boot menu. I can enter ubuntu , but when I enter windows 8 , pc just restart. What to do ????

---

### Post by oldfred on 2013-04-11
If you are getting grub first that is because it still is first in UEFI. UEFI controls boot from the folders in the efi partition just like devices. Some UEFI have it as one menu, some have you go into UEFI maintenance to change settings. And UEFI remembers previous.

Someone posted this with their UEFI, but every system is different.
      >  Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 
And to remove entries as UEFI remembers them.
UEFI system only shows ubuntu. Delete ubuntu entry & reboot a couple of times & it resets to defaults including drives & USB ports.



Do not know anything about EasyBCD. With UEFI you really should not need it as all systems are equal boot loaders in the efi partition.
       [http://neosmart.net/blog/](http://neosmart.net/blog/)

---

