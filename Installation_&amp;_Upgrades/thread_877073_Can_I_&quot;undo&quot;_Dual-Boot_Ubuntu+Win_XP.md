---
title: "Can I &quot;undo&quot; Dual-Boot: Ubuntu+Win XP?"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by Babak on 2008-08-01
Hi, 
just curious whether after following this process:
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

I will be able to "undo" it and revert back to just Win XP?

that is, to remove ubuntu? I'm not planning on it but because I had an issue with GRUB before eating my boot.ini I'm a bit nervous.

Also, could someone more knowledgeable than me, tell me the consequence to the boot process if/when the dual boot is "undone"?

Finally, is there a way to dual boot but to have it default to Win XP rather than Ubuntu (after 10 sec.)?

Thanks very much!!

---

### Post by K2712 on 2008-08-01
Don't know why you'd want to, but you can certainly 'undo' the dual boot. 

Using an XP cd you would boot into the recovery console and type
```
fixboot
```
then
```
fixmbr
```
and that would overwrite grub with windows boot loader, and then you could do whatever you please with the partition Ubuntu was installed on.

And for the auto-boot to windows, 
```
gksu "any text-editor" /boot/grub/menu.lst
```
scroll to the bottom where you will see all of your existing grub entries.  Just cut the Windows section starting with the Title and ending with Chainloader +1, and then paste it right above whatever is currently at the top of the list.

---

### Post by Pumalite on 2008-08-01
You can also erase your old Ubuntu partitions and expand your XP. Use Gparted Live CD for that. Backup everything before you do it.
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

---

### Post by Babak on 2008-08-01
> **K2712 said:**
> And for the auto-boot to windows, 
```
gsku "any text-editor" /boot/grub/menu.lst
```
scroll to the bottom where you will see all of your existing grub entries.  Just cut the Windows section starting with the Title and ending with Chainloader +1, and then paste it right above whatever is currently at the top of the list.

Thanks K2712! Could you please provide a bit more detailed instructions on how to change the boot order? I understand that I have to enter the command/code that you provided but where exactly?






Thank you Pumalite. I'll tuck that link under my hat for possible later use.


> **Pumalite said:**
> You can also erase your old Ubuntu partitions and expand your XP. Use Gparted Live CD for that. Backup everything before you do it.
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

---

### Post by K2712 on 2008-08-01
> **Babak said:**
> Thanks K2712! Could you please provide a bit more detailed instructions on how to change the boot order? I understand that I have to enter the command/code that you provided but where exactly?


You're welcome.  And the wiki provides a very good in-depth explanation on how to do this:

[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by Babak on 2008-08-01
right! the wiki

doh!

---

### Post by Babak on 2008-08-01
umm... just one more thing:

which ubuntu iso should I use? I ask because I know that wubi uses or needs 'alternate' iso, right?

so if I'm doing a regualar 32bit xp dual boot install, I just use the 32bit iso?

cheers

---

### Post by K2712 on 2008-08-01
If you have the 32-bit version of windows, then the 32-bit x86 iso should be the one you need.  It will work on ~90% of the computers out there.

---

