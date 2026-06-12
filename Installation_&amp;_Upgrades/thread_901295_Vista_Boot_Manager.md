---
title: "Vista Boot Manager?"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by A4orce84 on 2008-08-26
Hey Guys,

So I got Ubuntu setup on my laptop finally last night, but had a quick question.

When I was initially installing it on my computer, I used the "help my computer boot to LiveCD" option from windows....which basically creates an Ubuntu section on Vista's boot manager to allow you to boot from the CD.


Now that I have it fully installed, I have Grub boot manager that pops up first, and if I select Vista, I then I have Vista's boot manager that lists "Windows Vista" and "ubuntu."

I want to kill the Vista Boot Manager so that it just loads Vista normally from Grub, any ideas?

Thanks guys!

---

### Post by Punkoff on 2008-08-26
This looks like BootMGR is required to boot Vista. :)
You can use VistaBootPro to remove all boot variants except Vista from BootMGR. You won't see LiveCD boot option anymore ))

---

### Post by caljohnsmith on 2008-08-26
Probably the easiest way to modify your Vista boot menu is with "EasyBCD". Check out the following links:
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)
Let me know how it goes. :)

---

