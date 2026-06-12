---
title: "Install ABC's??"
date: 2005-10-17
forum: Installation &amp; Upgrades
---

### Post by JimH on 2005-10-17
I'm a newbie trying to install Ubuntu for the first time on my PC.  I must be missing something basic because when I try to boot from the install CD, my computer does nothing; that is doesn't reognise that there is anything on the CD. I have read the install manual and it does not provide any specific information on how to begin the install. Can anyone help?  Where can I find specific information on the steps to install Ubuntu?

---

### Post by Griffin3 on 2005-10-17
Mmm, this is probably tricky grounds to walk on, but, have you made sure that you have the BIOS on your computer set up to boot first from the CD? If your computer will boot from, say, a windows CD just fine, then the BIOS is set correctly and the Ubuntu CD image you have burned is probably corrupted.  

If your computer will not boot from a windows CD, you probably need to go into your BIOS at the very first black screen on booting (pressing Del key or F10 sometimes, computers vary), look through advanced BIOS settings, and probably there is one named "Boot Order" or something similar.  try to find a selection where the computer attempts to boot from the CD before the hard drive.

---

### Post by dbott67 on 2005-10-17
If your BIOS is set to boot from CD first, it could be a couple of other issues:

1. Flaky CD-ROM drive --- try taking the CD to another computer with a known-working CD-ROM.  This will help eliminate possibilities and pinpoint the problem.  If the CD works in another computer, then it's likely that the problem is with your PC.  If it doesn't work, then it could just be related to errors during the burn.

2. Burn speed was too high when you burned ISO image (this has happened to me a couple of times).  Re-burn the ISO image at a much lower speed (around 8x or so).

PS - I'm assuming that you checked the MD5 hash to make sure you got the entire ISO image intact.

---

### Post by dbott67 on 2005-10-17
With regards to verifying MD5 hash for file integrity, here is a page that provides further details on how to check the hash from Windows, as well as various other methods.

[http://userpages.umbc.edu/~mabzug1/cs/md5/md5.html]("http://userpages.umbc.edu/%7Emabzug1/cs/md5/md5.html")

I'll make the assumption that you downloaded the ISO image to a Windows computer.  If so, this is the file you need.

[http://www.pc-tools.net/win32/md5sums/]("http://www.pc-tools.net/win32/md5sums/")

I've never had to do this myself, so it is quite possible that there are easier/better methods available to check the MD5 hash, but a quick google returned the links I've noted.

-Dave

---

### Post by Herman on 2005-10-17
Hello, JimH,
               As far as some ABC information on how to install Ubuntu goes, try my signature link.
      It's titled 'ubuntu dual boot' but it doesn't matter if you're not dual booting, the main steps are the same. For a straight install, you skip the partitioning part in the middle by choosing 'erase entire disk'. Or you might decide to dual boot when you see how, but that's up to you, depending on your own circumstances.
 Anyway, I wish you luck and I hope you have a good, smooth install.
 Bye from Herman.

---

