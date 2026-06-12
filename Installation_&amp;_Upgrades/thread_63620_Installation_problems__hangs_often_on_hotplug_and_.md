---
title: "Installation problems : hangs often on hotplug and gives black screen"
date: 2005-09-08
forum: Installation &amp; Upgrades
---

### Post by Zillion on 2005-09-08
I am trying to install Ubuntu Hoary.

I am installing it together with WinXp.

The installation seems to go well, but after it all install things and it boots it hangs 3 out of 4 times on "Starting Hotplug subsystem". Sometimes it boots further but then just gives black screen. 

I reinstalled both XP and Hoary now 4 times, I even low level formatted my hdd but I cant get it to work.

Specs :

Ubuntu Hoary x86 (cd of early official release)

mobo : MSI K8N Neo4 platinum (amd 64)
audigy2 soundblaster
nvidia 6800 GTO
160 gb maxtor hdd

some n00b help would be appreciated. Is my grafix card not compatible or so? or do I need another Ubuntu release? tx

---

### Post by Strider on 2005-09-08
Probably need to disable the apic.  From the Grub boot menu, edit the config and add the following to the kernel line:

nolapic

Then boot up.  If that works, add "nolapic" to the kernel boot line in the grub config file.

You can find the grub.conf file under /boot/grub.

---

### Post by Zillion on 2005-09-08
tx but, nope same thing 
it boots.. then at the time the Ubuntu login screen should comes (if it doesnt hang at Starting hotplug subsystem) the monitor gets black - and gets no signal from puter anymore

I really like Ubuntu, I have it running on my 2nd pc, but this is driving me nuts... what the hell can I do.. I need OS quick.. maybe install Mepis then..

---

