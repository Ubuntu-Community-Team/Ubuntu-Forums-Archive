---
title: "Editing Grub2 Menu"
date: 2011-10-29
forum: Installation &amp; Upgrades
---

### Post by vanattab on 2011-10-29
I am setting up a dual booting computer for my friend.He wants his vista and ubuntu to dual boot. I did a dell system restore to reset vista and then installed ubuntu. Everything is working fine except there are some extra entries in the grub menu I would like to get rid of. Here are all the options:
Ubuntu
Ubuntu (recovery)
Memtest+
Vista
Windows XP Embedded

I want to get rid of the Memtest+ and the XP Embedded option so as not to confuse my friend. I know I can get rid of the Memtest+ option by chmod -x /etc/grub.d/(memtest+ file) but I am not sure how to get rid of the XP Embedded. (In fact I am not sure what the XP Embedded option even is) I have read that the /etc/grub.d/30_os_prober file is what scans for other non-linux os but how do I edit it to remove the XP without removing vista?
Thanks Alex

---

### Post by critin on 2011-10-29
My un-expert opinion is to leave them if your friend is a new ubuntu user.  He will quickly learn which line to choose and these are there on purpose.  If he ever has problems he may still be able to get into the os to fix them and if you're the fixer, you will be glad they're there too.
I don't know what the xp embedded is either, but what if it's a windows recovery/restore/repair and he needs it someday?

There are ways to hide them and someone will explain.

---

### Post by drs305 on 2011-10-29
The safest thing to do would probably install and use Grub Customizer. It's a great tool for tweaking the Grub menu. The 'Customizer' link in my signature line will take you to a thread about it.

Another 'safe' way of accomplishing what you want would be to create a custom menu (/etc/grub.d/40_custom) by copying the Windows entry you want into that file. Save it, update grub, and when you reboot make sure the entry is included in the menu and try it out.

If it boots correctly, you can use the "chmod -x" command you mentioned in your post on /etc/grub.d/30_os-prober. Once you update-grub and reboot you should only see your Ubuntu options and whatever you placed in 40_custom (assuming you have already taken care of Memtest).

---

