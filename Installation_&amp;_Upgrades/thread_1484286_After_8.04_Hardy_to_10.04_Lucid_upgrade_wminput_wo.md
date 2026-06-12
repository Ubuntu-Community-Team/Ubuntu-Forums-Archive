---
title: "After 8.04 Hardy to 10.04 Lucid upgrade wminput won't work without sudo"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by gfnord on 2010-05-15
After Hardy->Lucid upgrade, wminput (wiimote input device) won't work as before. It needs to be run as sudo, otherwise it says "unable to open uinput".

I followed every instruction I could find:

- I installed libcwiid1 (Hardy used libcwiid0)
- I added 'uinput' in the /etc/modules
- I added 'KERNEL=="uinput", MODE="0666"' in  /etc/udev/rules.d
- I prayed

After all this it seems to work, but still needs to be run with sudo. Since I need it to start at boot, this is a big problem for me. 

So, I even tried to run it as startup program like this: 

echo "mypassword" | sudo -S wminput ...

(I also tried changing '|' with '>'.) This resulted in a very strange behavior and generally doesn't work.

It might be that this is just a credentials-related problem and not related to wminput. Anyway, I don't know how to fix this.

I'm more-less a newbie here, so any ideas are welcome!

---

### Post by gfnord on 2010-05-20
SOLVED, kind of. 

I edited sudoers and in there enabled wminput to run with sudo without asking for password. To do that, add this at the bottom of sudoers (which must be edited with visudo):

username ALL=(ALL) NOPASSWD: /usr/bin/wminput

---

### Post by antti64 on 2011-01-24
Hi!

I'm having same problem. Have you any safer solutions for this?

Antti

---

### Post by gfnord on 2011-01-24
No. This works for me and I've stopped looking for better solutions...

---

### Post by Rebelli0us on 2011-03-14
> **gfnord said:**
> SOLVED, kind of. 

I edited sudoers and in there enabled wminput to run with sudo without asking for password. To do that, add this at the bottom of sudoers (which must be edited with visudo):

username ALL=(ALL) NOPASSWD: /usr/bin/wminput

The above works for me too, but 

KERNEL=="uinput", MODE="0666"' in /etc/udev/rules.d

...doesn't though it should. Which of the 2 is better?  Also, why doesn't battery check work?

---

