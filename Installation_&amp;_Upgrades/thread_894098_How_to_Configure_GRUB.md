---
title: "How to Configure GRUB"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by ananswam on 2008-08-18
Hi,

After finishing up a project for which I needed gnu, i've decided to go back to using windows but keep ubuntu installed just in case i need it again and because it is a very nice os as well. I'd like to be able to configure grub so that you can't even tell it exists unless you press escape at the right time, and have grub boot into windows xp by default. If I set hiddenmenu in menu.lst i still get a grub message that says Press any key to enter menu, is there any way to have grub be completely invisible? Thanks

---

### Post by wilbbe01 on 2008-08-18
Can you just cut the time down to as small of a value as you can?  As in the time before it automatically boots the default?

---

### Post by SkonesMickLoud on 2008-08-19
> **ananswam said:**
> Hi,

After finishing up a project for which I needed gnu, i've decided to go back to using windows but keep ubuntu installed just in case i need it again and because it is a very nice os as well. I'd like to be able to configure grub so that you can't even tell it exists unless you press escape at the right time, and have grub boot into windows xp by default. If I set hiddenmenu in menu.lst i still get a grub message that says Press any key to enter menu, is there any way to have grub be completely invisible? Thanks

Set XP as the first entry in your list, or set it as the default, and set the timeout to 1.  You might be able to set it to 0, but then you'd never have the chance to change OS.

---

### Post by steve.knoblock on 2008-08-19
I came from SuSE where the boot loader displays a menu and boots to whatever your last choice was (it shows XP and SuSE in a menu).

How do I set grub so it loads XP by default and gives me a choice should I want to boot to Ubuntu?

Thanks

---

### Post by SkonesMickLoud on 2008-08-21
> **steve.knoblock said:**
> I came from SuSE where the boot loader displays a menu and boots to whatever your last choice was (it shows XP and SuSE in a menu).

How do I set grub so it loads XP by default and gives me a choice should I want to boot to Ubuntu?

Thanks

In your /boot/grub/menu.lst put the entry for XP first and set the timeout to something like 3.  This will automatically boot XP after 3 seconds.  If you want Ubuntu, hit Escape when prompted.

---

