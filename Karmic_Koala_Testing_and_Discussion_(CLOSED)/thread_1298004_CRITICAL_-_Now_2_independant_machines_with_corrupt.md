---
title: "CRITICAL - Now 2 independant machines with corrupted Recovery Menu."
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-22
In Recovery Menu, I have now seen this on 2 machines, when trying to "Make free space". 

"Mountall cancelled.
general error mounting filesystems.
A Maintenance shell will now be started.
CONTROL-D will  teminate this shell and re-try."
Then it goes to a corrupted CLI, missing the first character, while still in the red and blue Recovery menu.  Nothing works except pushing the "Reset" button or powering down.

**Please test this NOW**,  and if confirmed I will file a bug.
[B]
ALSO[/B], I am still getting the  "Mount is busy" error when selecting "File System Check".
[http://ubuntuforums.org/showthread.php?t=1288666&highlight=file+system+check](http://ubuntuforums.org/showthread.php?t=1288666&highlight=file+system+check)

---

### Post by emarkay on 2009-10-22
Bug filed:
[https://bugs.launchpad.net/ubuntu/+bug/458352](https://bugs.launchpad.net/ubuntu/+bug/458352)

---

### Post by Azmo on 2009-10-25
I get it with i386 and amd64, both on my machine and through virtual box, and regardless if using grub1 or grub2.

Is there anyone here who does NOT have this problem?

---

### Post by matthewbpt on 2009-10-25
I also have this problem on my machine. Upgraded manually from Jaunty to Karmic.

---

### Post by inportb on 2009-10-25
Eh, works for me on a clean installation, with friendly-recovery 0.2.8.2. Make free space displays nothing and goes back to the menu. I also tried a couple of other options and they all return to the menu just fine.

---

