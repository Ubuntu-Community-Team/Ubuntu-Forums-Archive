---
title: "problem with hoary cd install"
date: 2005-03-16
forum: Installation &amp; Upgrades
---

### Post by rudeboyskunk on 2005-03-16
ok, here's the problem:

i downloaded the hoary cd image and burned it onto a cd.
i put it into my laptop to upgrade from warty.
it does not read the cd at startup; it just goes straight to grub.
i thought maybe the cdrom in my laptop was messed up, but it reads other install cds just fine and can read random cds after the system is loaded perfectly.  it cannot read this cd after the system is loaded either.
the cd itself works just fine in other computers during startup and after the os is loaded(whether it be linux or windows).
i burned it onto a second cd, same exact problems.

any ideas?

---

### Post by rudeboyskunk on 2005-03-17
i just burned the live cd image, and...

...same problem.

---

### Post by afroman on 2005-03-17
I had the same problem and after numerous copies i
was told what the problem was!
First of all never copy higher than 24X as these iso images
are fragile!
Just to be safe rather copy at 8X - (this worked for me)
Second of all make sure you are copying correctly -
it shuld be copied as an image file!
If you are using nero right click on the iso and say open with 
nero it should take you to the correct writing screen
(allso worked for me) 
Hope this helps

---

### Post by n00b0id on 2005-03-17
Ok, I feel I must make sure and ask?


Did you set the boot order in BIOS to prefer CDROM instead of hard drives?


If not, tap 'del' when you boot (in the very beginning screen), you will get into BIOS. Careful in there, wrong settings may cause problems.

---

### Post by rudeboyskunk on 2005-03-17
yeah, first i tried the "temporary bootlist" thing and set it to cdrom, then after it didn't work went to the bios and saw that it was already permanently set on cdrom first (which i set it on myself, and thought i had already set it on).

i burned it as an iso image, yes, and like i said, it worked fine as an install cd on other computers.

there's some sort of problem between distinctly this computer's cdrom and hoary.

---

