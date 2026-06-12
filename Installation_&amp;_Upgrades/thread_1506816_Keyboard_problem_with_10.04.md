---
title: "Keyboard problem with 10.04"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by ahagele on 2010-06-10
Hi,
I got problems with the numeric keypad on a HP probook 4510s under Ubuntu 10.04
The keypress events don't show for the numeric pad. 

Running xev to show the events I do get key press and key release events for all keys but not for some of the numeric keypad. These keys produce only a key release event.

Booting live Ubuntu 9.10 and all works fine.
And even the console (Ctrl-Alt-F1) works fine. Just X doesn't.
Also fine under Win7.

When pluging in a USB keyboard it woks too.

So I'm confused. Why would X not see the key press event?

Cheers

Andreas

---

### Post by okusi on 2010-06-12
i'm having the same problem since upgrading from 9.10. 

i have a stock standard generic keyboard, but the numeric keypad is not working properly.

i've played around with the keyboard settings in system/preferences, but this has made no difference.

anyone, any thoughts?

---

### Post by lesuisse on 2010-06-16
hi

I'm experiencing the same problem on my HP Elitebook 8540w.
I suddenly stopped working on 10.04. I think after some Linux Header updates....

---

### Post by ahagele on 2010-06-16
Hello lesuisse,
that might be right. I thought about booting the 10.04 from the live CD again and see if it works then. If it does it would be caused by one of the updates.
A

---

### Post by Costas100 on 2010-06-17
This thing (my keyboard was totally dead) happened to me and ended up abandoning 10.04. See my thread [http://ubuntuforums.org/showthread.php?t=1509847](http://ubuntuforums.org/showthread.php?t=1509847) maybe something there will trigger a thought. 

PS: I also had some updates (including headers) prior to the collapse
Costas

---

### Post by afbeta on 2010-06-30
I have the same problem with a HP elitebook 8540w.  My keypad is simply not working anymore with 10.04.  Anyone found a solution to that problem.  It also occurs when using an external keyboard.

---

### Post by Dakmor00 on 2010-07-03
I've been having a similar problem too. Turns out mine was just a silly one which was solved here: [http://geekozoid.blogspot.com/2008/06/number-pad-numeric-keypad-not-working.html](http://geekozoid.blogspot.com/2008/06/number-pad-numeric-keypad-not-working.html)

Just in case the link dies the solution for me was to:
Go System->Preferences->Keyboard then go to the 'Mouse Keys' tab and untick 'Allow to control the pointer using the keyboard'. Hope that solves it for at least some of you.

---

### Post by jvin248 on 2010-07-03
I just unselected the 'keyboard for mouse control' as Dakmor00 suggested and that fixed the problem. Big Thanks!

(note: press 'numlock' key after making the change to ensure the fix can be correctly observed, for a second I thought the update didn't work on mine but ensuring numlock was on and all was good).

---

### Post by kdxensen on 2010-07-03
Dakmor00 solved my problem, too!!! Apparently the update comes down the shoot with this "feature" enabled. Very baffling!!! Maybe I'm just getting old...

Thank you very much!!

---

### Post by iradi8 on 2010-07-28
That fixed it for me as well on my Toshiba 17" with numeric keypad. That is a BLOODY STUPID option to have on by default! Shame on you Canonical, that should NEVER have been on by default for any reason! Why would you enable something so blinking obscure that breaks something so critical to people? That's like shipping the OS with Sticky Keys turned on by default! :mad:

---

### Post by ahagele on 2010-08-08
fantastic. That's done it for me too. Just strange, this problem did not show up on the external USB keyboard. Must be different default values depending on keyboard type.
And yes it only got introduced with some software update. My original 10.04 ISO download did work just fine.
Anyway, problem solved
Andreas

---

### Post by simosx on 2010-08-08
> **Dakmor00 said:**
> I've been having a similar problem too. Turns out mine was just a silly one which was solved here: [http://geekozoid.blogspot.com/2008/06/number-pad-numeric-keypad-not-working.html](http://geekozoid.blogspot.com/2008/06/number-pad-numeric-keypad-not-working.html)

Just in case the link dies the solution for me was to:
Go System->Preferences->Keyboard then go to the 'Mouse Keys' tab and untick 'Allow to control the pointer using the keyboard'. Hope that solves it for at least some of you.

That option is not enabled by default.
It would help if you (all) can figure out what got it enabled by default for your computers. Did you enable accessibility, for example?

Unless we come to a conclusion why this got changed for you, there will be more people getting frustrated for no reason.

---

### Post by rune_kg on 2010-08-20
After an upgrade it suddenly _was_ enabled for me and my keys stopped working too. The solution described in this thread solved it! Thx.

---

### Post by mondomunchies on 2010-08-30
Go System->Preferences->Keyboard then go to the 'Mouse Keys' tab and untick 'Allow to control the pointer using the keyboard'. Hope that solves it for at least some of you.

^^^ Brilliant.  Good as new.

---

### Post by amicable on 2010-10-14
The very stupid thing about this issue is that NumLock on my keyboard was not working despite the mouse pointer option being unchecked.

Eventually, I ticked this box so that it was on, just to see if the keys were actually working. I could move the mouse pointer, so it proved they were live and connected.

Then I switched the tick box off.

Tada - the numeric keypad now works. :smile:

One odd thing remains - the NumLock LED doesn't come on anymore :icon_frown:

---

