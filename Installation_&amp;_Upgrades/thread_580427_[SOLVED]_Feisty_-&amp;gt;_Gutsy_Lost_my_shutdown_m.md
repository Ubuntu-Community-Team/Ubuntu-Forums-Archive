---
title: "[SOLVED] Feisty -&amp;gt; Gutsy: Lost my shutdown menu??"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by phibit on 2007-10-18
After upgrading to Gutsy on my laptop, no whenever I go to the "turn off" button (in the top right), I am not presented with a menu (the one that says "Turn off" "Restart" "Hibernate" etc..)

Instead nothing appears, but my clicks become powerless and my keyboard locks up, almost like it THINKS the menu is displaying and it's waiting for me to choose :s.

I don't have this problem on my desktop, and both are AMD64. Help?! I USED those buttons lol

---

### Post by phibit on 2007-10-19
nobody else has this problem?

---

### Post by mmmiiikkkeee on 2007-10-19
In kubuntu I have a similar problem.   when i use the nvidia drivers.  If i click logout the only choice i have is logout.  I don't have a shutdown choice.  the nv drivers work correctlty

---

### Post by mmmiiikkkeee on 2007-10-19
In kubuntu I have a similar problem.   when i use the nvidia drivers.  If i click logout the only choice i have is logout.  I don't have a shutdown choice.  the nv drivers work correctlty

---

### Post by svicente on 2007-10-20
Same problem, Kubuntu, no shutdown menu on KMenu.

I also have some problems with graphics (all too sluggish)  with Intel 945 and wasn't using compiz or beryl before ( [thread for that problem]("http://ubuntuforums.org/showthread.php?t=577141") )

---

### Post by theminor on 2007-10-20
I also have this problem - only logout is available. Any ideas?

---

### Post by phibit on 2007-10-20
Well hang on, my problem is that I don't have ANY menu. No logout, no suspend, no shutdown. 

Nothing appears... but IT THINKs the menu is showing so the system mouse and keyboard lock up.

---

### Post by m1b on 2007-10-20
I had a similar problem once I upgraded to Gutsy (clicking the 'quit' button and everything is locked up). 

I read (somewhere) something about the power-management service, so I  completely disabled it in 2 places (System\Admin\Services & System\Pref\Session), restarted the system and then re-enabled it. 

Don't know why it got trashed in the first place and can't tell what in my 'voodoo' procedure corrected it, but now it is working.

---

### Post by maristw on 2007-10-20
If you' re using kdm try to use gdm. I changed kdm to gdm and now I have shutdown button :)

---

### Post by Mateusz Ho&#322;ysz on 2007-10-20
Hi,

I have the same trouble. Shutdown menu appears long time after launching it (long time after click). When it finally appear there is no hibernation icon. Second launch of shutdown menu works perfectly.

Anybody?

Mateusz Ho&#322;ysz

---

### Post by phibit on 2007-10-21
> **m1b said:**
> 

I read (somewhere) something about the power-management service, so I  completely disabled it in 2 places (System\Admin\Services & System\Pref\Session), restarted the system and then re-enabled it. 

.

This worked! COOL! thanks. Now i just need to work on the face that my gnome hangs for like 25 seconds when i boot.

---

### Post by Mateusz Ho&#322;ysz on 2007-10-21
Works fine now but it.s not possible to disable power management services without waiting about 30 sec. for ahutdown menu.

---

