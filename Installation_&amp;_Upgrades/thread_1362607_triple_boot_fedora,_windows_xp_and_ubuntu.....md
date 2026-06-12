---
title: "triple boot fedora, windows xp and ubuntu....?"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by an3urysm on 2009-12-23
Hi, i m already dual booting Fedora 12 and Windows XP. I m planning to install Ubuntu 9.10 next. But i read somewhere if i m to triple boot, i should be installing the Server version instead of the Desktop. 
Is it so...? is there anything else i want to watch out....?

---

### Post by phillw on 2009-12-23
> **an3urysm said:**
> Hi, i m already dual booting Fedora 12 and Windows XP. I m planning to install Ubuntu 9.10 next. But i read somewhere if i m to triple boot, i should be installing the Server version instead of the Desktop. 
Is it so...? is there anything else i want to watch out....?

No, the desktop version will be fine - unless you only want the server (LAMP) with no GUI (Windows, icons etc - just a command line).

Make a partition for 9.10 (10 GB min, is recommended). You don't need to make a new /swap - it will see & use the one from Fedora.

As you're putting 9.10 on last - it'll want to put on Grub2 as the Booting system. Grub2 is fine & it will 'see' your xp & fedora areas for you & add them to the list of boot-options.

Phill.

---

### Post by an3urysm on 2009-12-23
do i have to install grub 2 separately or does it come with the ubuntu installation cd.? i guess it ll replace the grub installed by fedora.

P.s. i m a linux newbie, please bear with my questions:KS

---

### Post by SuperEngineer on 2009-12-28
Ubuntu 9.10 comes wit Grub 1.97 (aka '2').  It will replace your previous grub but if you download the application 'Startup Manager' in 9.10 you will be able to safely and easily choose your preferred default boot distro.

Hope this helps.

---

### Post by restrict on 2010-01-16
I have been trying to triple boot win7 ubuntu 9.10 and fedora 12. but failing. i have first installed win 7 then ubuntu and finally fedora. but failing to boot into ubuntu now. plz help me

---

### Post by kansasnoob on 2010-01-16
> **restrict said:**
> I have been trying to triple boot win7 ubuntu 9.10 and fedora 12. but failing. i have first installed win 7 then ubuntu and finally fedora. but failing to boot into ubuntu now. plz help me

If you'll boot your Ubuntu Live CD and then post the results of the Boot Info Script as described below I'll be glad to try and get it sorted out for you.

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

I have to run a few errands so it may be a couple of hours.

---

### Post by restrict on 2010-01-16
Thanks. I'll surely get back to u. Thanks for the help :)

---

### Post by kansasnoob on 2010-01-16
> **restrict said:**
> Thanks. I'll surely get back to u. Thanks for the help :)

Feel free to send me a brief PM just pointing me back to this forum thread.

It shouldn't be all that difficult. One option would be to add Ubuntu to Fedora's grub but I'd prefer restoring Ubuntu's grub2 to the mbr and I'm about 90% sure we can get it to recognize Fedora with a few simple commands.

That Boot Info Script should give me all the info I need to do either, although I'm less than proficient dealing with Fedora's grub. That's why I'd prefer using Ubuntu's grub2.

Grub2 is actually quite nice once you figure out a few very basic things.

---

