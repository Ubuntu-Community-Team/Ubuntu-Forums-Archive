---
title: "Want to Dual Boot With Mandrake - How Is It Done"
date: 2005-11-25
forum: Installation &amp; Upgrades
---

### Post by rickon on 2005-11-25
Hi all,

I am still quite a newbie at Linux although I have been using Ubuntu for about a month and am very pleased.  However I would like to dual boot with Mandrake.  Would you be able to show me how to do it please.  I know it uses things called lilo and grub but thats about all I know.

I have a computer with two hard drives and wish to put one distro on hda and one on hdb.

Thanks

Rickon

---

### Post by dsjas297 on 2005-11-26
I think you shouls just install both OSes on your computer. I'm pretty sure that Mandrake also allows you to install GRUB on the master boot record. GRUB should automatically detect both OSes.

---

### Post by rickon on 2005-11-26
[QUOTE=dsjas297]I think you shouls just install both OSes on your computer. I'm pretty sure that Mandrake also allows you to install GRUB on the master boot record. GRUB should automatically detect both OSes.[/QUOTE]

Hi Thanks for the reply.  Yes I have  installed both distros, but Ubuntu will not recognise mandrake.

Rickon

---

### Post by john dobborough on 2005-11-26
I once had a similar problem. I had mandrake and windows xp on my computer, dualbooting via lilo-programme which comes with mandrake. Then I wanted to triple boot with suse. But lilo only recognizes mandrake as the choice for booting up linux, no suse.
Solution: leave lilo and mandrake the way it is booting by way of the hard disk (lilo) and install suse using a floppy disk specially for the boot of suse.

Now i can boot windows or mandrake with lilo on the hard disk. If i want to use suse, then I insert the floppy disk and suse boots up.

This is a workaround, but it works for me.
useful tip?

---

### Post by akiro.yamamoto on 2005-11-26
Hi,
I googled around and found this site.

[http://www.linuxquestions.org/questions/showthread.php?threadid=384994](http://www.linuxquestions.org/questions/showthread.php?threadid=384994)

The information can be adapted to allow you to triple boot M$ , Ubuntu and Mandriva 10
Just don't overwrite the boot loader when your installing Mandriva.
Then boot into Ubuntu and add a section to your /boot/grub/menu.1st file for mandriva as outline in the above web site.

I hope this helps....
Regards
:smile:

---

