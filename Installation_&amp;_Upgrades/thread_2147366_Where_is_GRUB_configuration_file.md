---
title: "Where is GRUB configuration file?"
date: 2013-05-21
forum: Installation &amp; Upgrades
---

### Post by bobcatpost on 2013-05-21
Hi All,

I have recently installed Ubuntu 12.04LTS on an old Toshiba laptop.  In order to do this, through trial and error I have found I must set acpi to off.  Now, whenever I try to boot, I must also set acpi=off in the GRUB boot options.

Is there a configuration file that I can modify with acpi set to off, so that I don't have to do it each time I boot?

Thanking you in advance,

Bob

---

### Post by darkod on 2013-05-21
/etc/default/grub

Look for the line like GRUB_CMDLINE_LINUX and put the parameter you want in between the "". Save and close the file. Run sudo update-grub to create new grub.cfg.

---

### Post by bobcatpost on 2013-05-21
> **darkod said:**
> /etc/default/grub

Look for the line like GRUB_CMDLINE_LINUX and put the parameter you want in between the "". Save and close the file. Run sudo update-grub to create new grub.cfg.




Thank you for your reply to my question.  However, when I tried to save the file after I inserted the option, it would not let me.  It said "could not create a backup file...".  I clicked "Sve Anyway" but it did not good.

Note that I did change the permissions on this file to RW for everybody (it is owned by ROOT).

Any ideas?  Thanks,

Bob

---

### Post by bobcatpost on 2013-05-21
I believe I figured it out:  I changed the permissions in the folder as well as the file, and it seemed to work.

Thanks again for your help.

Bob

---

### Post by arpanaut on 2013-05-21
You really shouldn't be changing permissions for system files.
If you need to edit a file owned by root you should use gksudo gedit /path/to/file/file.name.
Then enter your user password edit the file and save. 
Changing permissions on system files may cause unintended consequences if not now, maybe later.

See:  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bobcatpost on 2013-05-22
> **arpanaut said:**
> You really shouldn't be changing permissions for system files.
If you need to edit a file owned by root you should use gksudo gedit /path/to/file/file.name.
Then enter your user password edit the file and save. 
Changing permissions on system files may cause unintended consequences if not now, maybe later.

See:  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)


Arpanaut,

Thank you for the good advice.  Fortunately, I remembered to change them back!

Bob

---

