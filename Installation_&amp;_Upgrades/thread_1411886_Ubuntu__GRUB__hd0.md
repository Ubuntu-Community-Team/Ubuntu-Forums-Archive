---
title: "Ubuntu / GRUB / hd0"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by cat2005 on 2010-02-20
I have a question.  If this is the wrong forum, then please move it.

I have a dual boot setup:  2x internal SATA hdd

- 1 hdd is ubuntu 9.04
- 1 hdd is win7

I originally had winXP and my grub menu let me select either "ubuntu 9.04" or "windows XP".

However, this menu is no longer valid because I installed windows 7 over windows XP.

Thus, my menu should show "ubuntu 9.04" and "windows 7" but it still shows the old menu.

To change my menu, I know I need to re-install grub.  The problem is, I don't remember exactly where I put it.  I know I put it on the ubuntu hdd.  Also, I remember I let ubuntu put grub in the default - I did not make it place grub in any strange places.  I think it said: hd0 or maybe it was hda; I can not remember the exact wording.  However, I do remember it was not something like hda1, hda2, etc.
[I]
I want to re-install grub in the exact same place, but I can't remember exactly where I allowed ubuntu to install grub.[/I]

I would appreciate any advice.  

I do have a copy of GRUB (Legacy, which is what 9.04 uses) on CD (SuperGRUB disc) and can use that if needed.  

Thank you!

---

### Post by darkod on 2010-02-20
As long as you are getting a grub boot menu, that means grub is there and it didn't get deleted. With 9.04 you are using the old grub1 or grub legacy which doesn't automatically detect that you have 7 now.
Did you try to boot windows from the menu? I guess it should boot 7 fine.

If it does, then just boot ubuntu and open /boot/grub/menu.lst with:

sudo gedit /boot/grub/menu.lst

Towards the bottom you will see the windows entry. Just change Windows XP into Windows 7, save and close the file, and that's it.

---

### Post by cat2005 on 2010-02-21
> **darkod said:**
> As long as you are getting a grub boot menu, that means grub is there and it didn't get deleted. With 9.04 you are using the old grub1 or grub legacy which doesn't automatically detect that you have 7 now.
Did you try to boot windows from the menu? I guess it should boot 7 fine.

If it does, then just boot ubuntu and open /boot/grub/menu.lst with:

sudo gedit /boot/grub/menu.lst

Towards the bottom you will see the windows entry. Just change Windows XP into Windows 7, save and close the file, and that's it.



Oh yes, I can select either OS, but I must do so by entering BIOS and changing the hdd boot order.

So, to clarify what you said:
a)  boot into ubuntu
b)  sudo gedit /boot/grub/menu.lst
c)  replace XP with windows 7  --  but how picky is it about spelling?  Is it cap sensitive, etc?

Thanks, I appreciate your help!

---

### Post by darkod on 2010-02-21
> **cat2005 said:**
> Oh yes, I can select either OS, but I must do so by entering BIOS and changing the hdd boot order.

So, to clarify what you said:
a)  boot into ubuntu
b)  sudo gedit /boot/grub/menu.lst
c)  replace XP with windows 7  --  but how picky is it about spelling?  Is it cap sensitive, etc?

Thanks, I appreciate your help!

In menu.lst that like will be like

title Windows XP

The commnd 'title' has to remain spelled correctly but the rest is what shows up in the boot menu. If you misspell it, it will still work but it will be misspelled. :)

---

### Post by cat2005 on 2010-02-21
I will give it a whirl.  Thanks!

---

### Post by darkod on 2010-02-21
Just to clarify things little better, ubuntu (and linux) is VERY sensitive to spelling. For example /boot/grub/menu.lst will work but /boot/grub/Menu.lst is considered another file and it won't.
So when writing commands you need to do it EXACTLY.
But in this particular case, we are talking about the name of your windows entry and ubuntu couldn't care less how you call it. If you want to put:

title windows VISTA

it doesn't care. As long as you know that it will boot 7 when you select that. :)

---

