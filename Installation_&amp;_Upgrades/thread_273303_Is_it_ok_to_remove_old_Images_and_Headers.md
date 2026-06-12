---
title: "Is it ok to remove old Images and Headers?"
date: 2006-10-07
forum: Installation &amp; Upgrades
---

### Post by NT4usB on 2006-10-07
In addition to the current 2.6.15-27, I have these still installed:
linux-headers-2.6.15-25-686
linux-headers-2.6.15-25
linux-image-2.6.15-26-686
linux-image-2.6.15-26-386
linux-headers-2.6.15-26-686
linux-headers-2.6.15-26
linux-restricted-modules-2.6.15-26-386
linux-restricted-modules-2.6.15-26-686

Can I remove some or all of them to free up space? I only have 8MB of 54MB left on that partition...

---

### Post by divague on 2006-10-07
yes, it's ok to remove old images and headers.

---

### Post by ciscosurfer on 2006-10-07
Unless you're pressed for space, it doesn't hurt to keep them around -- that way you can revert to an older kernel, etc. easily.

EDIT: Whoops!  I read your original post again...looks like you are pressed for space.  I would try to keep at least the last stable versions around though if you can.  If not, no worries!

---

### Post by NT4usB on 2006-10-08
Thanks for the reassurance. 
One more question..?
I have both the 2.6.15-27-386 and 2.6.15-27-686
installed. 
As far as I can tell (uname -r) I'm running on the -27-686.
Would keeping the -27-386 be sufficient as a fallback or can I nuke it and keep the -26-686 as the fallback?
Keep in mind, this is only a PVR box so If I blow it up, little would be lost...

---

### Post by ciscosurfer on 2006-10-08
Sounds good to me.  Just be sure to keep the appropriate header file(s), Config file(s), System.map files(s), and vmlinuz file(s)....all located in your /boot directory (except your header files).  Enjoy!

---

