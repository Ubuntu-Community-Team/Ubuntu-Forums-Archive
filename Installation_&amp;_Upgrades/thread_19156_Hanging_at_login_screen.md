---
title: "Hanging at login screen"
date: 2005-03-10
forum: Installation &amp; Upgrades
---

### Post by triviaseeker on 2005-03-10
Initially I had trouble installing when I got to choosing the location.  The mouse and keyboard would not work. Eventually I found on the forum linux acpi=off noapic which completed the install. 

Now I am stuck at the login screen and unable to enter any details.

I am using Warty.

Any ideas anyone?

---

### Post by alastair on 2005-03-10
Is this after rebooting into the new installed system?

If those options worked for you before, perhaps all you need to do is add them to the kernel line in GRUB for the installed system. For instance :

At GRUB, press ESC - go to the kernel line and "e" to edit .... "b" to boot.

You can add kernel args at the end of the kernel line.

Then, look to make the change permanent by editing your /boot/grub/menu.lst file.

Read some docs though - and be CAREFUL.

---

### Post by triviaseeker on 2005-03-10
>>Is this after rebooting into the new installed system?<<

Yes.

I will give your suggestion a go. Thanks

---

