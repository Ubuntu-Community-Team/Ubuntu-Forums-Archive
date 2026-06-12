---
title: "[SOLVED] completely remove grub2...for real"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by qwertymodo on 2008-11-24
I was recently trying out grub2, decided I didn't like it, so I uninstalled it and went back to grub legacy.  In the process a lot of stuff got messed up and I had to jump through a lot of hoops just to get grub back and happy.  Now I try to run the startupmanager gui and it tells me grub2 is still detected, but then it stops running because grub.cfg is missing :(.  Yes, I know grub.cfg is missing, i deleted it myself after "completely removing" grub2 apparently didn't work as advertised.  What other files and references have been left behind?  Why is startupmanager still recognizing grub2 as being installed?  I have even completely uninstalled and reinstalled startupmanager.  Any ideas?

---

### Post by caljohnsmith on 2008-11-24
You might want to take a look at Grub2's list of installed files:

[http://packages.ubuntu.com/intrepid/i386/grub-pc/filelist](http://packages.ubuntu.com/intrepid/i386/grub-pc/filelist)

You could go through those directories manually in your Ubuntu and make sure there is no trace of Grub2 leftover.

---

### Post by qwertymodo on 2008-11-25
Found some leftovers, just deleted them and am trying a reboot to see if it worked.

---

### Post by qwertymodo on 2008-12-01
yay, it worked.  I reinstalled the original grub just to be sure i didn't mess it up in the process and i works fine now.

---

