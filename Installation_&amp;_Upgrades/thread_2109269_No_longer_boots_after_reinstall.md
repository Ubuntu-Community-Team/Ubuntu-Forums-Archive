---
title: "No longer boots after reinstall"
date: 2013-01-27
forum: Installation &amp; Upgrades
---

### Post by stephon8 on 2013-01-27
A while ago I had Windows 7 and Ubuntu 12.04 installed on my Lenovo Ideapad Z570 with no problems. After I switched to Windows 7/Debian I started having problems. Both operating systems were extremely slow. So I did a clean install of 7 and still had the same problems. Now I couldn't get the drivers for my wireless card to work either.

So I reinstalled Ubuntu over the whole system. It worked. Then for some reason I decided to reinstall again. This time things were back to being slow and now the system won't boot. On top of that, grub now loads extremely slow and when it does, half the time pressing e or c does nothing.

I have tried reinstalling again and booting with nomodeset. Any ideas of where I can look from here? I find it strange that it used to work with no problems in the past. The Live CD also works fine

---

### Post by stephon8 on 2013-01-27
Update:

I got grub acting normally by changing SATA controller working mode from AHCI to compatibility in the BIOS, but I still have no progress on getting the system to boot.

The only thing that I can thing of that would have changed anything other than the hard drive (which was wiped for the install) is that I updated the BIOS when I reinstalled windows. Could something have messed up with that? Is there anything that having reformatted my hard drive could have changed from when I bought the computer with Windows 7 preinstalled and then dual booted Ubuntu?site:ubuntuforums.org

---

### Post by darkod on 2013-01-27
Upgrading the bios not always helps, in fact sometimes it can start creating issues for you.

Go through the bios and make all necessary adjustments because after upgrading it it loads the defauls. But the defauls should work in most cases too.

As for the sata mode, AHCI is actually better than IDE (Compatibility). And even if you change it after ubuntu has been installed, it should still work. Windows doesn't work if you make changes in the sata mode after installation, but ubuntu does.

If you can try the hdd in another sata port, do that too.

You can try leaving the sata mode to AHCI and trying a new install.

I really don't see much logic in what is happening. Either the bios upgrade actually created issues for you instead of solving them, or the hdd is beginning to die on you slowly.

---

### Post by stephon8 on 2013-01-28
I finally used Smart to test my hard drive and that ended up being the problem. Bought a new hard drive set my BIOS back to default and everything worked. I guess my first sign of hard drive issues should have been the 3+ hour install. Thanks for the help!

---

