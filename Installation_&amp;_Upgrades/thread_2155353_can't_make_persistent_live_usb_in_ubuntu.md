---
title: "can't make persistent live usb in ubuntu"
date: 2013-06-18
forum: Installation &amp; Upgrades
---

### Post by jjjjswait on 2013-06-18
hello all,

i'm trying to make an ubuntu live usb with persistence.  i've successfully made persistent live usbs from windows, but my attempts to do so in ubuntu have failed.  when using 'startup disk creator' the installation completes normally, but when i reboot with the new usb, at bootup i'm given an error message ('missing boot files', I think, but i don't want to check again as i'd lose my live installation's settings.  if necessary i can reboot to confirm that error) and am unable to proceed to the desktop.  i've also tried unetbootin, but the linux version, unlike the windows, doesn't appear to have any option for persiastence.
right now i'm using a live usb which, although persistence has failed on it, still allows me to boot into live mode.  the computer has no internal hdd and getting an old one to throw in temporarily is not possible because of my remote location.
does anyone out there know how to make a functioning persistent live usb using ubuntu?  i also have a live usb of puppy linux (unlike all other installations i've made it has retained its persistence, but its interface is too frustrating for me to use on a daily basis-- too bad, it's fast and reliable otherwise) if that can help.
thanks in advance.  losing my settings every time the power goes out isn't ideal.  my poor old computer...

---

### Post by Cheesemill on 2013-06-18
UNetBootin on Linux does have an option for persistance, it's labeled 'Space used to preserve files across reboots'.

[ATTACH=CONFIG]243934[/ATTACH]

---

### Post by jjjjswait on 2013-06-18
thanks for the quick reply.  unfortunately, the version of unetbootin that installs for me looks like this: [http://imgur.com/nyQj6jw](http://imgur.com/nyQj6jw)
i don't see any option for persistence.

---

### Post by Cheesemill on 2013-06-18
Which version of Ubuntu are you using and how did you install UNetBootin?

The exact version I am using is in the repositories for 12.10 and 13.04.

---

### Post by jjjjswait on 2013-06-18
i'm using mint 9 on this usb.  i installed unetbootin with [sudo apt-get install unetbootin]

---

