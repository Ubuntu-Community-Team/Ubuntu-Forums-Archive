---
title: "Add vga to boot?"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by samtuk on 2011-05-16
Hi,

I have searched high and low for an answer to this, so any help would be hugely appreciated.

I just installed gOS ubuntu (dual with 7), during the install i could boot into it by adding VGA=0x31B to the end.

I have now installed and only get a black screen, i have tried to add it to the grub boot by following the on screen instructions (o = add line e = edit) but it will not save it and just boots as normal.

It makes a beep noise when i get to the black screen, so i know the x is there, just can't see it. I can CTRL+ALT+F1-F6 but have no ide on how to change resolution once there.

Any help would be hugely appreciated,
Many thanks,
SamT

---

### Post by aphatak on 2011-05-16
Does your BIOS support that mode?  The way to confirm it is to hit 'c' when the Grub menu appears.  This should show a screen with a grub prompt.  Once at the Grub prompt, enter the command 'vbeinfo'.  This should show a list of all the modes the BIOS supports.  If 0x31B is not in it, select the mode with the resolution closest to the one you want, and use the corresponding code instead.
Will you please post the results?  Maybe I can learn something from it, too.

---

### Post by samtuk on 2011-05-16
Thanks for the reply.

I pressed C and went to the grub line, vbeinfo returned a command not found.

I did vbeprobe (Not sire if its the same, found it under the help command) which returned:

0x100      640x400x8
0x101>151  640x400x8
0x152      640x400x8

I have definitely used 0x31B on the install screen, it gave me a larger resolution than id like, but it worked for my screen.

---

### Post by samtuk on 2011-05-16
Found the solution here [http://ubuntuforums.org/archive/index.php/t-133764.html](http://ubuntuforums.org/archive/index.php/t-133764.html)
(bottom post)

I was trying to add vga as a new line, turns out that you need to add to the end of boot/vmlinuz line.

---

