---
title: "ubuntu mate 20.04, black screen after install no boot menu"
date: 2021-10-27
forum: Installation &amp; Upgrades
---

### Post by sebigbos on 2021-10-27
Hello,

I´m a newbie here in the forum and not very experienced in Linux. I have a AMD graphic card HD5670 and a quite new display, Asus VP28. I run it with displayport connection. I installed Ubuntu Mate 20.04 from DVD and this didn´t show any flaws. The live system booted in normal mode and the display showed 2560x1440 with 60 Hz. When I boot from hard disk after install, I get a black screen, while the system obviously is booting.

I already saw that there are some hints to solve this in this forum in a sticky post opened by [MAFoElffen]("https://ubuntuforums.org/member.php?u=1044547"). My problem is that I don´t see nothing, not even a boot menu to start from. The screen is black as soon as I start the hard disk. Perhaps somebody can help.

---

### Post by MAFoElffen on 2021-10-27
Being "I am" MAFoElffen...

My Disclaimer of this response is that the creator and maintainer of the "Ubuntu Mate" Distribution tells me and my son that all support issues for "Ubuntu Mate" should be posted to the "[Ubuntu Mate Forum]("https://ubuntu-mate.community/")"... And he wishes that issues related to Ubuntu Mate be asked there. Not just as being specifically relatable, but that so he knows about them and he can make sure they are addressed and resolved in and for "his" own flavored distribution. He cares about what is his and he feels very  responsible for that. I can understand that. I have the highest regard and respect for that kind of dedication and resolve. If I resolve this here, then I will try to forward him the results of that to let him know... So he is "aware" and he can make nay needed changes to that in his distribution. I support the Linux Graphics Layer as a whole. Not just in the Debian Branch. I have my own Ubuntu derivative distribution project. I can relate to his pride and ownership of Mate.

If while it is a "black screen"... Wait a few minutes to make sure it is done with anything it might be trying to do, then... if you press the <Cntrl><Alt><F4> keys (at once/at the same time) do you get a Virt-TTY session (TTY 4)?

---

### Post by sebigbos on 2021-10-28
Thank you for your answer! I didn´t get exactly what you try to tell me in your disclaimer, sorry, english is not my mother tongue. The [https://ubuntu-mate.community/](https://ubuntu-mate.community/) doesn´t look like people there waiting for me to solve my little just-a-user-problems. But if you think it´s better to ask there, I will do it. But I have the same problem with a Linuxmint Cinnamon installation, so the problem is maybe not desktop-related.

I think the system does a normal boot job, just without showing anything on the display. If I press Ctrl+alt+del and then enter, the system will shut down, like Ubuntu Mate should do. If I press ctrl+alt+F4 nothing happens. But if I press then afterwards ctrl+alt+del the system shuts down immediatly without waiting for the enter key.

---

### Post by sebigbos on 2021-10-29
it was all there, just invisible....;). Uncommmenting  GRUB_GFXMODE=640x480  in /etc/default/grub and update-grub solves the  problem. Thank you for the information.

---

