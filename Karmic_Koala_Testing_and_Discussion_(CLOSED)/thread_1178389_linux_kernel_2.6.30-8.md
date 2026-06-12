---
title: "linux kernel 2.6.30-8?"
date: 2009-06-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Vanishing on 2009-06-04
Today there was a update for kernel 2.6.30-8 in karmic, I went through the update. The weird thing is its not showing up in synaptic, but it does show up in /boot/grub/menu.lst, though that boot option is broken.
anyone else experiencing that problem?

---

### Post by Vanishing on 2009-06-04
never mind...seems like linux-image for rc8 wasn't installed on my machine. Just installed it, and it works now.

---

### Post by geojorg on 2009-06-04
uname -r
2.6.30-7-generic

I just run sudo apt-get update but there was no update package for the kernel, in synaptic I do have 2.6.30-8-generic, I guess the update manager did not realice about the new kernel i would just wait for it.

---

### Post by Vanishing on 2009-06-04
weird...i got the update.. maybe its because i was on the 'gap' of when they were updating the repository..

---

### Post by Vanishing on 2009-06-04
vanishing@Vanishing:~$ uname -a
Linux Vanishing 2.6.30-8-generic #9-Ubuntu SMP Wed Jun 3 15:23:55 UTC 2009 i686 GNU/Linux

---

### Post by tad1073 on 2009-06-04
thomas@tad:~/Desktop$ uname -a
Linux tad 2.6.30-8-generic #9-Ubuntu SMP Wed Jun 3 15:38:38 UTC 2009 x86_64 GNU/Linux

---

### Post by fifth on 2009-06-04
I'm updating through Synaptic just now and 2.6.30-8 is being installed, although apt-get was showing the generic kernel packages as being held back.

---

