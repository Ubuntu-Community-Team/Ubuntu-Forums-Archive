---
title: "[SOLVED] Can't boot Hardy from CD"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by klm15851 on 2008-05-31
I can't get Hardy to boot from the CD to my Dell Vostro 200.  I get as far as it asking if I want to try Ubuntu without making changes to the computer, insatll Ubuntu, etc.  I've tried both.  The Ubuntu name and logo comes up.  Then I get a prompt and error message:

(initramfs) [  121540121] ata1.00: revalidation failed (errno=-5)

After a few more lines of equally cryptic text, my PC boots to Windows (Vista).

What has gone so wrong?

This is my first-ever Linux experiece.  I was expecting a steep learning curve, but not absolute failure right out of the gate!
](*,)

---

### Post by Partyboi2 on 2008-05-31
try booting with all_generic_ide as a boot option and see what happens. To do this when you are at the main menu screen press F6 and at the end of the line add ```
all_generic_ide
``` then press enter.

---

### Post by Rocket2DMn on 2008-05-31
I had this problem on my Dell Inspiron 530, and I had to use the options "acpi=off noapic".

---

### Post by Pumalite on 2008-05-31
This might be interesting reading too:
[http://blog.youxu.info/2007/10/07/install-ubuntu-on-dell-vostro-200/](http://blog.youxu.info/2007/10/07/install-ubuntu-on-dell-vostro-200/)

---

### Post by klm15851 on 2008-06-03
Thanks so much Partyboi2, Rocket2DMn, and Pumalite!  Thanks to a combination of all of your istructions I was able to boot from the CD and do a successful installation.  I have dual boot with Vista.

I had to F6 at the main menu then type:  

                        generic.all_generic_ide=1

Thanks again for your help!!!

---

