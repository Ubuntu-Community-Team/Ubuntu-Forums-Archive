---
title: "Boot repair disk report"
date: 2016-01-28
forum: MINT
---

### Post by zigaboo on 2016-01-28
[http://paste.ubuntu.com/14690727/](http://paste.ubuntu.com/14690727/)

I have a feeling this might be the wrong forum for this, but I couldn't find anything else on google.

Tell me if I need to post more!

---

### Post by kansasnoob on 2016-01-28
What exactly is the problem? From the boot info I can see that Mint is the only OS installed and grub appears to be installed properly.

---

### Post by howefield on 2016-01-28
Thread moved to the "*MINT*" sub forum.

---

### Post by zigaboo on 2016-01-28
Sorry, I thought the log would show everything, I have no idea how this works.

when I try to boot, I get these:

error: disk 'hd0' not found.
Entering rescue mode...
grub rescue> _

---

### Post by kansasnoob on 2016-01-28
Well according to the boot info you only ran Boot Repair to collect info rather than choosing to run the default repair:

> =================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sda1 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s


=================== User settings
**The settings chosen by the user will not act on the boot**.

So maybe if this was a reinstall grub didn't get installed properly?

I'd first try running Boot Repair and let it run the "recommended repair":

[https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu)

If that doesn't fix it maybe [Mint]("http://forums.linuxmint.com/index.php?sid=79020d15952a57145726f0628b48830a") has some specific grub voodoo that I'm not aware of.

---

