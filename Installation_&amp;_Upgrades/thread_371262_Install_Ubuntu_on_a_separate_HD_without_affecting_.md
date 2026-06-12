---
title: "Install Ubuntu on a separate HD without affecting ntdlr on primary HD?"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by janz84 on 2007-02-26
I was wondering if it is possible to install and run Ubuntu on a separate HD without modifying the ntdlr for windows on the primary HD. I'm would like to install the AMD64 version for my Opteron cpu.

I have already tried an AMD64 alternate install disk on my secondary harddrive and have ran the grub installer part on /dev/sdb (my second harddrive). However, grub fails to load Linux when I select that HD in my BIOS's BBS.

Any solutions to this matter would be greatly appreciated.

---

### Post by mikewhatever on 2007-02-26
Are there any error messages when 'grub fails to load Linux'?

---

### Post by janz84 on 2007-02-26
Yes, I get a "Error 17: Cannot mount selected partition" when I select "2.6.17-10-generic," "2.6.17-10-generic (recovery mode)," and "memtest86+."

When I select the windows xp pro option I get a "Error 13: Invalid or unsupported executable format,"  however,  I do not need the ubuntu designated HD to boot my windows HD.

---

### Post by janz84 on 2007-02-26
going to try a reinstall with the regular 6.10 amd64 desktop disk after it finishes downloading

edit... scrap that... download is way too slow.

---

### Post by confused57 on 2007-02-26
You might want to read over this guide:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by janz84 on 2007-02-28
Using that guide as a reference this is what I did:

Opened my case and disconnected my windows HD.

Connected my SATA1 cable to my ubuntu HD.

Reinstalled ubuntu on ubuntu HD using the alternate install cd I already had.

Let grub occupy the mbr of the ubuntu HD.

Opened back up case and connected windows HD to SATA2.

Powered on system and made the windows HD boot before the ubuntu HD.

Using this setup, windows will load unless I press F8 (the BBS popup menu button for my BIOS) and select my ubuntu HD... which was the desired result for this thread.

P.S.
Why would I want ubuntu installed and transparent?

To hide it from another user of my computer who uses windows xp exclusively, and not have to reset the default os in the menu.lst file when kernel upgrades are made.

P.P.S
Thanks for the guides confused57!

---

