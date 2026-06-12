---
title: "Boot Grub error"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jmore9 on 2010-04-15
After i finish the on line update to 10.04 from 9.10 it reboots and then cannot find grub.

It installs itself to sda1 should it be sda0 or the same as the one that is used by 9.10 ?

Little confused on this.

---

### Post by VMC on 2010-04-15
> **jmore9 said:**
> After i finish the on line update to 10.04 from 9.10 it reboots and then cannot find grub.

It installs itself to sda1 should it be sda0 or the same as the one that is used by 9.10 ?

Little confused on this.

grub should be the mbr on sda.

Do you know if it updated to grub2?

The best solution to help you would be to run the boot_info _script and ouput the RESULTS.ext file back here.

---

### Post by jmore9 on 2010-04-15
It said it was going to uodate grub.  All i know is there was no grub selection menu because it said it could not fund its spot i guess.

Tried using live cd but i gave errors of wrong versions of some file.

Just re-installed 9.10 .  I will try again and mybe try to force it to install to hda instead of hda1.

Thanks for your response.

---

### Post by jmore9 on 2010-04-15
Well i finally succeeded in upgrading to 10.04.  Turned out the major problem was thunderbird and/or its requirements.

The installer stopped completely and would not go until i removed thunderbird completely.

I also has to tell grub the install the sda instead of sda1.

---

### Post by VMC on 2010-04-15
> **jmore9 said:**
> Well i finally succeeded in upgrading to 10.04.  Turned out the major problem was thunderbird and/or its requirements.

The installer stopped completely and would not go until i removed thunderbird completely.

I also has to tell grub the install the sda instead of sda1.

Glad you figured it out yourself. If satisfied please mark this topic as [SOLVED].

---

