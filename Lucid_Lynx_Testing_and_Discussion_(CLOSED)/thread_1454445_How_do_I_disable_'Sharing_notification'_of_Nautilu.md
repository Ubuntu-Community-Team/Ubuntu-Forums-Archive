---
title: "How do I disable 'Sharing notification' of Nautilus in Lucid"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by praveenthivari on 2010-04-14
As shown in the pic, I get the notification in Nautilus saying I can save files received through bluetooth in Downloads. 
Now , I dont have any Bluetooth capability for my desktop, and I dont want tht feature to be nagging me whenever I open tht folder. How do I disable tht.
May be the solution is very simple, but I am not just able to figure it out myself even after tinkering around with the preferences in Nautilus.

---

### Post by Didius Falco on 2010-04-14
This should do the trick: open **Menu/System/Preferences/Startup Applications**. Scroll through the list (it should be at/near the top) and uncheck the box by [B]Bluetooth Manager.

[/B]You should be able to log out and back in and it won't run Bluetooth automatically anymore.

---

### Post by praveenthivari on 2010-04-15
> **Didius Falco said:**
> This should do the trick: open **Menu/System/Preferences/Startup Applications**. Scroll through the list (it should be at/near the top) and uncheck the box by [B]Bluetooth Manager.

[/B]You should be able to log out and back in and it won't run Bluetooth automatically anymore.

Thanks for the reply. 
I hv already disabled the Bluetooth manager during startup:)

---

### Post by mc4man on 2010-04-15
Disable 'personal file sharing' in Startup Applications

(or see if there is something in the preferences of the nautilus dialog box

---

### Post by tekstr1der on 2010-04-15
Better yet, see the following change coming down the pipe shortly:

> gnome-user-share (2.30.0-0ubuntu2) lucid; urgency=low

  * Don't install the Nautilus bar for Lucid. It's not that useful to people
    who don't have bluetooth hardware and is not easily disabled. In the
    future, this bar will hide when the hardware is not available (LP: #532101)


---

### Post by chrisccoulson on 2010-04-15
> **tekstr1der said:**
> Better yet, see the following change coming down the pipe shortly:

Yes, I had planned to write a patch make this hide automatically for people with no bluetooth hardware, but I ran out of time for final freeze and just disabled it instead.

It will come back again in Maverick though

---

### Post by splicerr on 2010-04-15
> **chrisccoulson said:**
> Yes, I had planned to write a patch make this hide automatically for people with no bluetooth hardware, but I ran out of time for final freeze and just disabled it instead.


Ughh, I actually liked that feature.  :cry:

---

### Post by chrisccoulson on 2010-04-15
> **splicerr said:**
> Ughh, I actually liked that feature.  :cry:

So do I, but a lot of people don't have bluetooth hardware (especially desktop users), and the bar was useless for them.

Don't worry, it will be coming back :) Just not for Lucid though...

---

### Post by praveenthivari on 2010-04-16
Oh god, will we hv to wait for 10.10 to disable tht simple thing.:-(

---

### Post by chrisccoulson on 2010-04-16
> **praveenthivari said:**
> Oh god, will we hv to wait for 10.10 to disable tht simple thing.:-(

huh?

---

