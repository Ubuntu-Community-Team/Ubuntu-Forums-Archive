---
title: "Tux when booting vga=791"
date: 2005-05-27
forum: Installation &amp; Upgrades
---

### Post by fjleal on 2005-05-27
Greetings!
Just a simple question: when one boots with the "vga=791" option, shouldn't there be a penguin in the top left corner of the screen?

Thank you. This is a major problem, any help is appreciated... ;)

---

### Post by Xian on 2005-05-27
[QUOTE=fjleal]
Just a simple question: when one boots with the "vga=791" option, shouldn't there be a penguin in the top left corner of the screen?[/QUOTE]
That is not what determines whether an image appears during boot. The vga parameter only sets the appearance of the text that you see scrolling by. The image is determined by what options are compiled into the kernel.

---

### Post by fjleal on 2005-05-27
[QUOTE=Xian]That is not what determines whether an image appears during boot. The vga parameter only sets the appearance of the text that you see scrolling by. The image is determined by what options are compiled into the kernel.[/QUOTE]
Thank you. I assumed that having a graphical mode choosen during boot would automaticaly enable it, but of course it may depend on other options. By other words: no matter what you do, you _will_ recompile your kernel! ;)

I just asked because all other distros I've tried (Red Hat, Slackware...) show up the sympathetic penguin if booting in vga mode. Why not Ubuntu?

---

### Post by Xian on 2005-05-27
[QUOTE=fjleal]I just asked because all other distros I've tried (Red Hat, Slackware...) show up the sympathetic penguin if booting in vga mode. Why not Ubuntu?[/QUOTE]Probably because Ubuntu is Debian based and that is not included as a default config in the kernel. I know how to add it in Debian as there was a nice How-To over at LQ Forums and it worked great, but it included patching and then compiling the kernel. There is a specific Debian patch that is intended for just this purpose.

In Ubuntu, I just use [Splashy](http://wiki.nanofreesoft.org/index.php/Splashy). But that is very developmental package.

---

