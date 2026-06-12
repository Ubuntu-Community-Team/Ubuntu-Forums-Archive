---
title: "Dapper-&gt;Edgy dist-upgrade woes"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by CptPicard on 2007-04-12
Ok, this is a bit strange... I just dist-upgraded my kubuntu dapper to edgy, and initially there weren't any show-stopping breakages. However, when I was doing the dist-upgrade, apt was constantly complaining about a missing locale, so it was "reverting to C".

After the upgrade, I indeed was using the C locale and my fi keymap wasn't loaded. So I went to the KDE system controls and selected the 105-key Finnish keymap. After this, something has been eating about half of my keypresses, and some keys don't function at all -- such as "a". The keyboard itself is fine, I'm writing this on the Windows side of things.

Another problem is that after the upgrade the tty framebuffer is totally messed up after X starts, so I can only use X. Next thing I'll test is booting into the "safe mode" where I did get a proper tty last time I tried and see if the keyboard issue is only X-related. If it is, I still would need some pointers where I can reconfigure my keyboard as the system is almost useless at the moment...

Now the question is... how do I reconfigure the keyboard and locales if I do manage to get myself into the box either by tty or ssh?

---

### Post by zvacet on 2007-04-12
Why didn´t you add locale?
[http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_locales_to_Ubuntu_the_command_line_way]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_locales_to_Ubuntu_the_command_line_way")

---

### Post by CptPicard on 2007-04-12
Because I didn't know how to :oops:

Thanks. Already fixed it with dpkg-reconfigure console-setup though. The keyboard issue with disappearing characters was weird, but it's ok now too.

Now to only get the tty corruption solved... I've got the ATI fglrx driver on X, for those who are interested.

---

