---
title: "Can Vista be installed on an Ubuntu based system?"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by xp_newbie on 2008-08-18
Of course Vista can be installed on a system that has Ubuntu installed on it. What I meant in my question is: Can Vista be installed on such system without effecting the MBR, **[SIZE="4"]such that Ubuntu's GRUB continues to be the one that boots the system?[/SIZE]** (and such that I can later modify menu.lst to include Vista in the boot options).

I know that Ubuntu can be installed on a system that has Vista installed, such that GRUB becomes the one that boots the system. What I am asking is about the reverse order: **First install Ubuntu, then install Vista**.

Can this be done?

If so, how?

Thanks,
Alex

---

### Post by mellowd on 2008-08-18
This is possible, you'll just need to reinstall grub once Vista is installed

---

### Post by tuxxy on 2008-08-18
Yes, I would prefer to isntall windows first but it can be done.

---

### Post by xp_newbie on 2008-08-19
> **mellowd said:**
> This is possible, you'll just need to reinstall grub once Vista is installed
Thanks. Can you point me to a HOWTO that shows how to re-install grub?

---

### Post by dstew on 2008-08-19
[Here]("http://ubuntuforums.org/showthread.php?t=224351") is a good thread on restoring grub after installing Windows. It is not hard to do.

---

### Post by FrizzleFry on 2008-08-19
And here's a step by step guide with screenshots.

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

---

### Post by xp_newbie on 2008-08-19
Thank you, dstew and FrizzleFry. This is exactly what I was looking for. The two versions complement each other, and give the best of both worlds. Now I can proceed to install Ubuntu 8.04 on my new PC without having to wait for the funds needed to buy Vista.

And here is another nice link:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

