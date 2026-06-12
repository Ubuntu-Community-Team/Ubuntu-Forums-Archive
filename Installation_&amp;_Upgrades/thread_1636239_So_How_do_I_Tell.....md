---
title: "So How do I Tell....??"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by Karl10 on 2010-12-02
[FONT="Comic Sans MS"][SIZE="3"]**[/SIZE][/FONT]Hi Folks

So, the inevitable just happened: Windows 7 64-bit just went belly up with a contaminated registry (came installed in the laptop).  No method of repair/recover works, and I DON'T want to do a full system restore.  My system has 2 500Gb drives, and I'd like to use "C:\" for Windows (gaming, and those few apps that have no equivalent in Ubuntu), and use "D:\" for Ubuntu.  I Installed Maverick on my mostly empty second hard drive ("D:\"), and used it to salvage good downolads, contacts, bookmarks, and such from the wreckage.  I'm at the point where I'm ready to build anew, and some questions occurred to me

1.)  How can I tell whether I have the 32 or the 64=bit version installed?  I'm pretty sure there's a terminal command, like "ver," but I can't recall.

2.) Will installing Windows onto the C:\ drive trash the boot loader for Maverick?   Can I work around this by putting something on a USB drive, installing Windows, then using the USB stik contents to repair the damage to the boot loader??

I suppose the answer to "1.)" will tell me what to do about "2.)"; if I have the 32-bit version, I'll just trash it all, fdisk/format, and re-install Win7 first, (maybe WinXP alongside it), and Ubuntu/64 on the other drive.

Thanks in advance for any help; I know just enough to get into high-powered trouble faster than any newb !!

Karl, Bristol, NH:confused:

---

### Post by marcusdufrane on 2010-12-02
You should be able to get the bit version from a usual 

uname -a

command.
on my install i get this...

Linux marcus-desktop 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:58:24 UTC 2010 x86_64 GNU/Linux

which tells me of course i have the 64 bit version installed.

---

### Post by TNT1 on 2010-12-02
Install the windows 7 first, then ubuntu, and let Grub manage your boot. Windows 7 is a grub killer, and restoring it if you install win7 after ubuntu is a pita.

---

