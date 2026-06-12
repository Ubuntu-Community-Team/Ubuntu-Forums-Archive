---
title: "USB keyboard not recognized on boot"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by tomwtomw on 2006-12-07
Hello

I have installed Ubuntu 6.10 on a sistem which already had Win XP pro. I now have dual boot, but my Logitech Ultra-X USB keyboard is not recognized on boot. Works fine when Ubuntu loads. The SP2 keyb works OK on boot. What can I do to fix the problem?

Thanks

---

### Post by bscbrit on 2006-12-07
If the keyboard works when Ubuntu loads, when does it stop working? Or have I misunderstood what you have written....?

---

### Post by bscbrit on 2006-12-07
I think I'm am working out what you mean.  Check your BIOS to ensure that the USB kbd is recognised there at boot time.

---

### Post by Bourlotieris on 2006-12-07
See at your motherboard's BIOS if you have an option for "USB Legacy Support" or something similar and if you do enable it. Had the same problem and worked for me.

---

### Post by tomwtomw on 2006-12-07
Thanks for your replies. Where would I check for that option, **Bourlotieris**? I'm afraid I'm kind of a newbie in that department. 

Just to clarify things a bit, the USB keyb works OK everywhere, except on the boot screen (where I choose between Win XP and Ubuntu). When I need to make that choice, I need to do it with the older PS2 keyb.

---

### Post by Bourlotieris on 2006-12-07
Yes, I understand the problem you have, same with what I used to have. To enter you BIOS menu you have to press a certain key at boot time (usually the DEL key, your Motherboard should have a message at the bottom of the screen about that, like: "Press Del to enter BIOS setup". From there on I am afraid you are on your own as motherboards tend to have all kind of different setup menus and there is no standard. You'll have to do a little search in the setup menu but it shouldn't take you long. Look for peripherals or something like that in the description in the main menu. Don't forget to save your changes before you exit the BIOS setup menu. I believe you should be able to solve this matter in the next 10-15 minutes. I'll wait for a reply from you.

---

### Post by tomwtomw on 2006-12-07
That's great, works like a charm. Thank you, you've been most kind. Just one more question--could enabling this option "interfere" with anything else on my computer?

---

### Post by Bourlotieris on 2006-12-07
> **tomwtomw said:**
> That's great, works like a charm. Thank you, you've been most kind. Just one more question--could enabling this option "interfere" with anything else on my computer?

Not to my knowledge. I did this trick about 9 months ago and didn't have any side effects at all. It was the same thing suggested to me when I had the same problem by some very experienced computer users.

By the way welcome to the Ubuntu community, it's a superb place to be :D

---

### Post by tomwtomw on 2006-12-07
Thanks. :)

Judging by my first discussion here, it really does seem like a great place. :)

---

