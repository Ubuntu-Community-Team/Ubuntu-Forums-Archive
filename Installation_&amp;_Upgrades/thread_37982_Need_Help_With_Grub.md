---
title: "Need Help With Grub"
date: 2005-05-29
forum: Installation &amp; Upgrades
---

### Post by mtweldon on 2005-05-29
I have 3 hard drives.. 1 has xp, 2nd has all kindsa music and junk files, other has linux.  Im trying to make it to where I can unplug the linux HD and plug in my junk files so I can boot up windows with all my music and all that.  When I try this I get Error 17 I think it is, guessing because it no longer sees the linux partition.  Any easy way to fix this?  Should I just get rid of grub with the windows fixmbr command and then when I want to use the linux partition just F8 and select that HD?  Or is it possible through grub?

---

### Post by Jenda on 2005-05-29
Did you try editing GRUB's menu options? I'm not sure, but it might help.

---

### Post by mingus on 2005-05-31
[QUOTE=mtweldon]I have 3 hard drives.. 1 has xp, 2nd has all kindsa music and junk files, other has linux.  Im trying to make it to where I can unplug the linux HD and plug in my junk files so I can boot up windows with all my music and all that.  When I try this I get Error 17 I think it is, guessing because it no longer sees the linux partition.  Any easy way to fix this?  Should I just get rid of grub with the windows fixmbr command and then when I want to use the linux partition just F8 and select that HD?  Or is it possible through grub?[/QUOTE]
 The info in your post is a bit unclear . . .

Are all 3 drives connected in your system, and you are trying to swap #2 and #3 in/out of a second drive bay, or ???

If you have 3 drives installed, just define them correctly in /etc/fstab and they will be mounted at boot for Ubuntu to see.  Of course, Windows will not see the 3rd linux drive.

For booting, try installing grub on a floppy (grub-install /dev/fd0) and booting from it to make sure that your system can boot from the 3rd drive.  If it works, you can run grub again to put the loader into the MBR.

---

