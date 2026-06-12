---
title: "Dual Boot with WinXP on IBM T41 Laptop"
date: 2005-08-11
forum: Installation &amp; Upgrades
---

### Post by fujie on 2005-08-11
Hello,

I recently installed Ubuntu on my desktop dual booting with WinXP and it works great, so I went to install it on my laptop as well.  My laptop recently had a dual boot system going with Suse 9.1 and WinXP and it worked just fine.  When I installed Ubuntu on my laptop, linux seems to boot fine (from grub) and work well, however, WinXP blue screens on bootup (from grub) and gives the error "UNMOUNTABLE_BOOT_VOLUME".

I've looked this error up and tried everything from the MS site and still nothing works.  I have also tried searching google/forums and haven't been able to find anyone with this specific dual boot problem.

My best guess is that the Ubuntu installer changed the partition table in a way that WinXP doesn't like.

If anyone has any advice, please let me know.  Thanks,

-Fuji

---

### Post by timtimtimtim on 2005-08-11
fuji-
i had a similar problem once i uninstalled mepis from a winxp dual boot machine.  it ended up being a problem with the mbr (look up info on how to use "fixmbr" and "fixboot" using your winxp disc on the microsoft site).
oh, here: [http://support.microsoft.com/default.aspx?scid=kb;en-us;314503](http://support.microsoft.com/default.aspx?scid=kb;en-us;314503)

even after using fixmbr, i had to edit my boot.ini file on my winxp installation to remove the text calling for the old mepis installation.
you should be able to edit the boot.ini file to accurately list the two installations on your machine (both the xp and ubuntu).
even if you just get windows to boot again, you could then re-install ubuntu after that.

for more detail, just search for "fixmbr" and "boot.ini"
hope this helps,
-tim

---

### Post by fujie on 2005-08-11
thanks for the help tim!

a few quick follow up questions:

so basically, i should be using the windows boot loader instead of grub?

were you able to edit your boot.ini file from linux because you had WinXP on FAT?

-fuji

---

