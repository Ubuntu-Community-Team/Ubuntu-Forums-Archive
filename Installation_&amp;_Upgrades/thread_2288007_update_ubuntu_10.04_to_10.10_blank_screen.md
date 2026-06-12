---
title: "update ubuntu 10.04 to 10.10 blank screen"
date: 2015-07-23
forum: Installation &amp; Upgrades
---

### Post by IslingtonN5 on 2015-07-23
I really hope someone can help, i'm seriously stuck and pulling my hair out.
My hardware:- Lenovo ThinkPad X220
- Spec can be found here: [http://www.cnet.com/uk/products/lenovo-thinkpad-x220/specs/](http://www.cnet.com/uk/products/lenovo-thinkpad-x220/specs/)

I took the decision to update my Ubuntu system from ubuntu 10.04 to 10.10. Once the process completed, i constantly see a blank screen.

I've searched multiple forums some saying "Hold shift" and press E on the GRUB menu to solve the issue, but i cannot get this to work.

CTRL+ATL F1 gets me to a login screen, but my login details are not recognised..

Any advise???

I'm new to Ununtu and this is putting me off already

---

### Post by v3.xx on 2015-07-23
You should of upgraded direct to 12.04.

Like 10.04; 10.10 is also end of life.

How bout a fresh install?

---

### Post by Bashing-om on 2015-07-23
IslingtonN5; Hello; Welcome to the forum.

> 
I'm new to Ununtu and this is putting me off already

Don't beat on dead horses.

10.04. 10.10. 11.04. 11.10, 12.10, 13.04. 13.10, and 14.10 are all End_of_life releases and have no support.
If you want ubuntu, a fresh install of a current release is strongly advised ( 12.04, 14.04 or 15.04 ).
12.04 is a (L)ong (T)erm (S)upport release and is supported until April of 2017;
14.04 is also a LTS release with support 'til 2019
15.04 is the current interim release, support for 9 months, 'til Jan 2016.

Attempting to upgrade from 10.04 to a current release is a long hard road -> 10.04 -> 12.04 -> 14.04 and is likely not to make the jump; not to discount the bandwidth and the time factor. There was a huge change in the operating system at 12.04 with the introduction of unity as the Desktop Environment; may not adapt from the environment of 10.04 .

[INDENT][INDENT]clean ;
[INDENT][INDENT][INDENT]fresh install
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by IslingtonN5 on 2015-07-25
I followed the fresh install advise and tried loading 15.04 on my laptop, now i'm getting:

GNU GRUB version 2.02~beta2-15ubuntu0.1

Minimal BASH-Like line editing is supported. For the first word, TAB lists possible command completion. Anywhere else TAB lists possible device or file completions.

---

### Post by Bashing-om on 2015-07-25
IslingtonN5; Well ... not;

That means grub can not find it's config files on the hard drive.
As a 1st approximation, we need to "know" that the install medium is viable.
Boot the install medium, as soon as the bios screen clears depress and hold a shift key -> language screen, escape key to accept the default -> boot options menu .
In this menu is " check disk for defects " .
Run the test, does it return with no rerrors ?

Then if no errors, we look at the hard drive's partitioning, and (RE-)install grub ( bootloader ) to the hard drive.

[INDENT][INDENT]small steps
[INDENT][INDENT][INDENT]will get there
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

