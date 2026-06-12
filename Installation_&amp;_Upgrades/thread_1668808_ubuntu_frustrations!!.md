---
title: "ubuntu frustrations!!"
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by Rydahey01 on 2011-01-16
I am trying to install 10.10, but having no luck.  First time Ubuntu user, and not very computer smart, so bear with me, and use small words :) .  I downloaded 10.10 from the Ubuntu site, and checked it with 5sum;  it matched.  Burned it to CD using slowest speed (10x).  I ran "fdisk" on my HD, then formatted it so I could do a clean install.  In "post" screen, set CD-ROM as 1st boot device, and restarted.  Got to "keyboard=man in circle" symbols, pressed ESC and got to language page.  Chose English, and got to menu page.  Chose "Install Ubuntu" but it takes me to a black screen with a flashing cursor in the upper, left corner, and it just sits there and won't go any further.  Any help would be appreciated.

---

### Post by ronnielsen1 on 2011-01-16
Will it boot from the live cd (not the install option)?

---

### Post by Quackers on 2011-01-16
After choosing the language, press F6 and you should get some options. You may have a graphics problem. Some of those option will enable you to get past that problem. Nomodeset seems to be the most commonly used one, but it would depend on your graphics card. You could also check the cd for errors, as a precaution.

---

### Post by Rydahey01 on 2011-01-16
> **ronnielsen1 said:**
> Will it boot from the live cd (not the install option)?

No.  Just get a screen with a bunch of numbers, and flashing cursor at bottom.

---

### Post by Rydahey01 on 2011-01-16
> **Quackers said:**
> After choosing the language, press F6 and you should get some options. You may have a graphics problem. Some of those option will enable you to get past that problem. Nomodeset seems to be the most commonly used one, but it would depend on your graphics card. You could also check the cd for errors, as a precaution.

Will try the F6, Nomodeset.  Then try install, or run from CD?

---

### Post by Quackers on 2011-01-16
select "try ubuntu" first and see that everything loads. If nomodeset doesn't work try the other options. Do you know what your graphics card is?

---

### Post by Rydahey01 on 2011-01-17
> **Quackers said:**
> select "try ubuntu" first and see that everything loads. If nomodeset doesn't work try the other options. Do you know what your graphics card is?

Both Nomodeset and 'check disk for errors' take me to black screen with bunch of numbers, and flashing cursor.  Video card is ATI Radeon X550, 256MB PCIe.

What are system requirements for 10.10?

---

### Post by Quackers on 2011-01-17
Is that as old a card as it sounds? Not sure.
It may be worth trying 10.04, as I believe some older graphics hardware is not supported in 10.10 (due to ATI dropping support).
You could try other boot options as well.

---

### Post by vidtek on 2011-01-17
> **Rydahey01 said:**
> I am trying to install 10.10, but having no luck.  First time Ubuntu user, and not very computer smart, so bear with me, and use small words :) .  I downloaded 10.10 from the Ubuntu site, and checked it with 5sum;  it matched.  Burned it to CD using slowest speed (10x).  I ran "fdisk" on my HD, then formatted it so I could do a clean install.  In "post" screen, set CD-ROM as 1st boot device, and restarted.  Got to "keyboard=man in circle" symbols, pressed ESC and got to language page.  Chose English, and got to menu page.  Chose "Install Ubuntu" but it takes me to a black screen with a flashing cursor in the upper, left corner, and it just sits there and won't go any further.  Any help would be appreciated.

Rydahey-

Try other distros, such as Mandriva or mephis, they are a bit more user-friendly for first time users.  I found Ubuntu very frustrating as a newbie.
Quackers- if it's a PCIe video card it can't be that old!

Best regards, Tony.

---

### Post by Quackers on 2011-01-17
My x1300 is a PCIe, but it's pretty old :-)

---

