---
title: "Need to back up current GRUB2 before re-install..."
date: 2011-06-23
forum: Installation &amp; Upgrades
---

### Post by Moozillaaa on 2011-06-23
Anyone know how to do this?

Really, all I need is to **retain an entry in GRUB2** for a second disk, which has it's own GRUB2, which I want to keep intact, and not have removed when re-installing the GRUB2 on the 1st disk...

---

### Post by oldfred on 2011-06-24
You can just copy /boot/grub/grub.cfg.

If you do not run update-grub it will not remove any entires. Or if you do not have entry run this to make sure it has all the systems in the grub.cfg.

sudo update-grub

If you have two drives & two grubs, you do have to keep track of which drive you are booting in BIOS and keep that version updated even after changes to the other system.

If you want to fully document your system:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

