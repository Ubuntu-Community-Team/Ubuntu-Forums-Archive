---
title: "xorg.conf not found, unable edit monitor refresh rate,"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by Anime4000 on 2010-01-06
hai all...
i got problem when edit xorg.conf, i search on google, found the command to edit, but my terminal give me "File not found" so there have alternate way to edit?

here my terminal give reason:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=142676&stc=1&d=1262791290[/IMG]

so i need create a file? or have alternate way? because my monitor can't at 70Hz+ and got "out of range" and screen flickering, so i need 60Hz for best my monitor.

---

### Post by maybeway36 on 2010-01-06
Nowadays Linux doesn't usually have xorg.conf. 95% of the time it autodetects everything perfectly, and the other 5% it's a pain to configure.

---

### Post by sanderd17 on 2010-01-06
Why did you edit it before you copied it? any chance you saved it in an other location with nano?

this will be difficult to find if so.

---

### Post by Anime4000 on 2010-01-06
first i use at version 8, xorg.conf provided,
when i format to 9.10, xorg.conf not provided,

there can create?

---

### Post by doas777 on 2010-01-06
yes, the change from using the xorg, to not, came about in 8.10, and was refined a bit in 9.04 and 9.10.

first, what kind of video card do you have? is there any reason you can't use the gnome display manager console in system -> preferences?

the new way to set your res and refresh via the cli, is called 'randr'. here is some info on how to use it:  [http://www.linuxtutorialblog.com/post/solution-resetting-your-screen-resolution-with-xrandr](http://www.linuxtutorialblog.com/post/solution-resetting-your-screen-resolution-with-xrandr)

---

