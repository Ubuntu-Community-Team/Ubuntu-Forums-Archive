---
title: "Problems installing ubuntu"
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by foolman89 on 2008-09-12
I am having difficulties installing ubuntu. The first time i did i got all the way through to the log in screen, where no matter what i did it would log in give the login sound, and promptly go into a black screen. After a few seconds it would send me back to the login screen again. This would happen everytime. So i just gave on the idea for a bit. Now recently i had to wipe my hard drive clean, and reinstall windows so i decide to try to instally it again. This time however i decide to test it straight from the  cd again with the same result. Can anyone tell me what i am doing wrong here? I tried with both architecture types installition and it doesnt change anything.

---

### Post by Pumalite on 2008-09-12
Memory? Graphics?

---

### Post by foolman89 on 2008-09-12
It has a gig of memory and i have a ATI RADEON XPRESS 200 Series card.

---

### Post by Pumalite on 2008-09-12
Your video card could be the problem. Try the Alternate CD.

---

### Post by foolman89 on 2008-09-12
No thats not it since its linux supports that video card.

---

### Post by Pumalite on 2008-09-12
What kind of display do you have?

---

### Post by foolman89 on 2008-09-12
I have a 19 in flat lcd

---

### Post by Pumalite on 2008-09-12
Get a Knoppix Live CD and see if you can boot it:
[http://www.knopper.net/knoppix-mirrors/index-en.html](http://www.knopper.net/knoppix-mirrors/index-en.html)
If you can; post:
lshw

---

### Post by foolman89 on 2008-09-13
I downloaded Knoppix and load it up and it worked. I could surf on the browser it had, i even changed the display settings and it worked fine.

---

### Post by JumpForJoy on 2008-09-14
Is there any other ways around this problem?

---

### Post by Pumalite on 2008-09-14
Where is:
sudo lshw
(Knoppix bypasses BIOS. You have not resolved anything yet)

---

