---
title: "remove wubi from vista (no c:ubuntu folder)"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by whetherornot on 2010-09-10
I persuaded my aunt to install wubi on her Vista machine, and now she'd like it to go away. can't blame anyone for trying...

However, none of the wubi removal methods have worked. Vista can't find any ubuntu uninstall programs, and there is no ubuntu folder either in c:, in c:\windows, or c:\programfiles, etc..

I have downloaded the uninstall program, and it just won't run. nothing happens. I have installed and ran easyBCD, and ubuntu doesn't even show up in the boot options.

However, when booting, ubuntu is the primary os option (which is the main thing that's bugging her, actually), and ubuntu is definitely still installed. I can boot into ubuntu no problem (internet access, on the other hand, is another thing. Why no wicd-curses? man.)

So Ubuntu is installed, but I can't find it anywhere when I am in Vista. And uninstalling doesn't do anything. What can I do? I've looked at numerous threads,FAQs, and the stickies, so please don't send me to the normal places if you're thinking of RTFMing me. However, relevant links would be much appreciated. Here is what I find from EasyBCD. It seems that I only have one OS in the bootloader, Windows. I am quite novice at boot stuff, so I may be missing something obvious. Grub is certainly still installed, I know that.

"There is one entry in the Windows bootloader.

Default: Windows Vista
Timeout: 10 seconds
Boot Drive: C:\

Entry #1
Name: Windows Vista
BCD ID: {current}
Drive: C:\
Bootloader Path: \Windows\system32\winload.exe"


Thanks for your time.

ps--My aunt just told me that at some point she may have deleted the ubuntu folder. Well, that makes some sense, but shouldn't ubuntu then not be able to load properly? It's definitely still in proper working order.

---

### Post by bcbc on 2010-09-10
It sounds like she has a real install (not wubi).

If the first thing she sees at boot is a grub menu (with ubuntu on the top, then memtest, then windows) then she has a real install.

To 'uninstall' you need to reinstall the windows bootloader, and then you can delete the ubuntu partitions from the vista disk manager.

You can reinstall the windows bootloader using the Vista repair console: "bootrec.exe /fixmbr"

---

### Post by whetherornot on 2010-09-11
bcbc:

thank you, you were correct. She had originally told me that she used Wubi, but in fact had done a dual boot. that makes a lot more sense. now I just have to backup her windows stuff so that I can resize the partitions, because ubuntu currently only gets around 2 gigs.

The real problem for her was simply that ubuntu booted first, so I went into /boot/grub/menu.lst and changed '0' to '4'.

I am now following wikis regarding pre-partition backups, etc., but if anyone has strategies,tweaks,time-savers re:Vista backups pre-partition, I'd love to know them or be linked.

thanks again

---

