---
title: "Install BasicLinux"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by argos3016 on 2009-11-19
I know that is not the better question on this forum, but:
Anyone installed BasicLinux on a IBM ThinkPad 755C 486DX4?!?
Because i already did all steps to install it.
I think that is the floppy driver...
[http://lists.ibiblio.org/pipermail/baslinux/2007-February/013030.html]("http://lists.ibiblio.org/pipermail/baslinux/2007-February/013030.html")
I don't understand this help. Can anyone tell me what is this,please? :confused:confused:

---

### Post by phillw on 2009-11-19
> Most Thinkpads have an "inverted floppy drive change line"
(why IBM did it this way, I don't know).  To fix it, add:
---------------
floppy=thinkpad
---------------
to the loadlin line in boot.bat  (in your DOS directory)


Hi

What it is saying that on thinkpads you need to add the line floppy=thinkpad in the place it says.

After that, it should work.

Not having a thinkpad, i cannot say that this works, but the source of the solution seems reliable. Give it try, it won't completely break your system, just may knock out the floppy drive (or, as it says - make it work)

Regards,

Phill.

---

