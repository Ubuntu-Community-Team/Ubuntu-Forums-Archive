---
title: "Canceling a terminal install"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by Rurak on 2011-01-13
So I was installing wine on Ubuntu 10.10 and it came to a page looking like a user agreement page and whatnot with an <ok> at the bottom.  i could not click on anything nor press enter or any other key sequence that i could find to continue with the installation so i exited the terminal window.  Now i am unable to install anything getting an error message reading:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


I know there is a command line to cancel the previous install and allow me to install other programs and such but i cannot remember.  If anyone knows this command line i would be grateful also if anyone knows how to accept the user agreement page i encountered earlier that would be great.  Thanks in advance.

---

### Post by oldos2er on 2011-01-13
Run ```
sudo dpkg --configure -a
``` when the agreement comes up hit Tab to highlight 'Ok', then Enter.

---

### Post by Rurak on 2011-01-14
that's it.  thank you very much.  and doubly for the agreement page.

---

