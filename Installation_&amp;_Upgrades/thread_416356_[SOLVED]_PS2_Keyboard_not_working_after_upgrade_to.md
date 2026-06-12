---
title: "[SOLVED] PS/2 Keyboard not working after upgrade to 7.04"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by Greg Knight on 2007-04-21
Hi all,

I have just completed my upgrade from 6.10 to 7.04.

Everything seems to have gone perfectly, except that my keyboard no longer works in Ubuntu.

The keyboard works fine; as I can get through GRUB into Vista (which is where I am typing this - on the same box and keyboard).  I can get into the system as I have it set to automagically log into my wifes desktop user account, but I can't type when I get there.

Once I get to the GDM login screen the keyboard is no longer working.  

I am very confused.  I have been using this keyboard with no dramas on this rig sine 5.10 with no dramas.

Help me Ubu-tu Kenobi you're my only hope.

Cheer!
Greg

---

### Post by Greg Knight on 2007-04-22
Decided to re-install 6.10 and worry about 7.04 later.

---

### Post by Big Ed on 2007-04-22
I had the same problem.  AMD64 box, upgraded from Edgy to Feisty, USB mouse worked but PS2 keyboard didn't.  (Numlock light was on and it still worked in bios screen.)  I tried a few of the suggested solutions from other posts in these forums, but none of them worked.  I found that if I disabled USB in the bios, then my keyboard would work.  But then my mouse wouldn't.  So I enabled USB again and disabled just the mouse in bios.  (USB keyboard was already disabled in the bios.)  Now the PS2 keyboard works and so does the USB mouse.

I don't know if this will help anyone else, but there are a lot of posts about non-functional keyboards with Feisty.

Ed

---

### Post by Greg Knight on 2007-04-24
Ed,

Thanks!

I will try that on the weekend!

 I too am on an AMD Box using a USB mouse witha PS/2 KB.

Cheers!
Greg

---

### Post by Greg Knight on 2007-04-24
Sweet Hurrah!

Thanks Big Ed.  Worked a treat

---

### Post by Big Ed on 2007-04-24
I'm glad it worked for you.  And I notice that you just couldn't wait until the weekend.  :-)

Ed

---

