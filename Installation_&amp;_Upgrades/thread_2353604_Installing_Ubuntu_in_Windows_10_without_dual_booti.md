---
title: "Installing Ubuntu in Windows 10 without dual booting"
date: 2017-02-23
forum: Installation &amp; Upgrades
---

### Post by thedoctor818772 on 2017-02-23
Just purchased a new netbook with Windows 10 installed. I want to install Ubuntu 16.10 and really would prefer **not **to have to dual-boot. Is that even possible? If not, can I get a copy of say Windows 7 or earlier and wipe the HD and then install Ubuntu 16.10 without Windows? If so, how do I accomplish this? 

Thanks,

-MD

---

### Post by TheFu on 2017-02-23
Many systems can use virtualization to accomplish this, but most netbooks just don't have enough RAM or powerful enough CPU to do it. Most people would load up virtualbox to try it on Windows.

If you won't want Windows anymore, just install Ubuntu and let it wipe the entire hard drive. Of course, if you do this, Windows and the backup copy on the hdd will be deleted forever.

If you want Win7, then you'll need a retail copy ($$$$). I don't think MSFT sells it anymore.

For people new to Linux, running a non-LTS release like 16.10 is a bad idea. You probably want 16.04 which gets 5 yrs of support.  Non-LTS releases only have 9 months of support from the original release date - June for 16.10 is the end of support.

---

### Post by RobGoss on 2017-02-23
+1 Thefu

---

### Post by thedoctor818772 on 2017-02-23
When I tried installing ubuntu and deleting windows 10m upon rebooting I get the error: "The selected boot device failed. Press ENTER to Continue. Please help!

---

### Post by TheFu on 2017-02-23
Please clarify. I don't understand what you booted, which boot device was selected, if it ever booted, and what happened when you pressed "enter."

Did the install appear to go cleanly?  Or not?

Also, the exact model of netbook would be helpful too. Not all netbooks work well with any other OS. Virtualization really is the safest way to proceed, but without a booting OS, that option has been removed.

---

### Post by RobGoss on 2017-02-23
You do not have to delete Windows manually, once you've created a Ubuntu media ether USB or DVD, just insert that in to your machine and begin your installation 

When you get to the part of the installation how to install Ubuntu choose use the Entire disk, this will remove any other operating system on that machine presuming this is what you want

---

### Post by thedoctor818772 on 2017-02-23
Yes, the install appeared to go cleanly. Upon rebooting (and maybe I pulled the USB stick out too soon?) I got the aforementioned error message. Not sure what to do. I am running HP 15-ay041wm.

---

