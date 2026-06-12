---
title: "No boot with &quot;splash quiet&quot; options after upgrade"
date: 2014-05-10
forum: Installation &amp; Upgrades
---

### Post by foxy123 on 2014-05-10
I have upgraded my daughter's HP DV6 laptop to 14.04 and could not boot into it. After removing options splash and quiet it started to boot but it looks a bit ugly and I wonder if I can turn them back using probably some other options? The grub config file looks now like:
```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=5
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="acpi_osi=Linux quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="acpi_osi=Linux"
GRUB_CMDLINE_LINUX=""
```

---

### Post by sudodus on 2014-05-11
Did you change something else to make the computer boot? If that is the case, you can try with the boot options **quiet splash** again. I suggest that you try it temporarily (editing the grub menu). See this link

[https://help.ubuntu.com/community/Grub2/Troubleshooting#Editing_the_GRUB_2_Menu_During_Boot](https://help.ubuntu.com/community/Grub2/Troubleshooting#Editing_the_GRUB_2_Menu_During_Boot)

---

### Post by foxy123 on 2014-05-11
> **sudodus said:**
> Did you change something else to make the computer boot? If that is the case, you can try with the boot options **quiet splash** again. I suggest that you try it temporarily (editing the grub menu). See this link

[https://help.ubuntu.com/community/Grub2/Troubleshooting#Editing_the_GRUB_2_Menu_During_Boot](https://help.ubuntu.com/community/Grub2/Troubleshooting#Editing_the_GRUB_2_Menu_During_Boot)
No, I left all other things as they were. I have already tried to add the quiet and splash back and the laptop did not boot.

---

### Post by sudodus on 2014-05-11
The easy solution is to accept that it is ugly during boot.

Other options include trying with various boot options, for example those suggested at F6 in the installer:

acpi=off
noapic
nolapic
edd=on
nodmraid
nomodeset

(I'm not sure, maybe nomodeset is the most likely to help you)

---

### Post by foxy123 on 2014-05-11
> **sudodus said:**
> The easy solution is to accept that it is ugly during boot.

Other options include trying with various boot options, for example those suggested at F6 in the installer:

Thanks a lot. Tried out all of them with the following results:

acpi=off [COLOR="#FF0000"]failed: booted but no wifi[/COLOR]
noapic [COLOR="#0000FF"]OK[/COLOR]
nolapic [COLOR="#0000FF"]OK[/COLOR]
edd=on [COLOR="#FF0000"]failed[/COLOR]
nodmraid [COLOR="#0000FF"]OK [/COLOR]
nomodeset [COLOR="#FF0000"]failed[/COLOR]

Currently I set it to noapic but I am not sure which is better if any.

---

### Post by sudodus on 2014-05-11
I think it is OK with noapic.

---

