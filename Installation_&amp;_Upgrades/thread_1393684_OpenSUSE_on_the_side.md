---
title: "OpenSUSE on the side"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by sdlynx on 2010-01-29
I just installed openSUSE on a separate partition, and chose not to install it's boot manager.  So I came back to Ubuntu so that I could do an update-grub2, but it doesn't find the SUSE installation.  Turns out, even gParted shows the SUSE partition as Unrecognized.  What went wrong?  Also, how can I add SUSE to my grub list (assuming the filesystem is/was set up correctly)?

Thanks,
SDLynx

---

### Post by zvacet on 2010-01-29
If you used ext3 or ext4 for Suse it should be recognized.Read [this]("https://help.ubuntu.com/community/Grub2") to find out how to add new entry to grub.

---

### Post by sdlynx on 2010-01-29
> **zvacet said:**
> If you used ext3 or ext4 for Suse it should be recognized.Read [this]("https://help.ubuntu.com/community/Grub2") to find out how to add new entry to grub.

Thanks, I got it up.  Apparently the installation had gone bad, a reinstall fixed it on the SUSE side.  I even got grub2 back (I just installed openSUSE's bootloader in case that was the problem last time).  However, now when I try to load Ubuntu it lets me log in but I cannot get any panels or anything for either GNOME or XCFE.  OpenSUSE runs fine.  Thus, I can't use Ubuntu aside from through the terminal.  Help?

Edit: Note, and this is probably important, I have a separate home partition that I mount (same user) for both linuxes  (grammar?).

---

### Post by sdlynx on 2010-01-30
*bump*

---

