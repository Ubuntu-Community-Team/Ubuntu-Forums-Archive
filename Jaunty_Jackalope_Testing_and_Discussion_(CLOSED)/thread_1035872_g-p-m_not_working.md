---
title: "g-p-m not working"
date: 2009-01-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2009-01-10
Hi all, 
 I just filed a bug [lpbug]315837[/lpbug] . If somebody has any suggestions to try or something, I'm game.

---

### Post by LordVeovis on 2009-01-11
> **ShirishAg75 said:**
> Hi all, 
 I just filed a bug [lpbug]315837[/lpbug] . If somebody has any suggestions to try or something, I'm game.

I am confused.  I can't follow what your saying.  Forgive me but it looks like you used google translator to translate from a different language >.< please can you explain again.

---

### Post by ShirishAg75 on 2009-01-11
ok lemme be more clear. 

I follow 2 ways/strategies for powering of monitor or not. 

When I'm sleeping or not using the computer the monitor is supposed to sleep in 1 minute. 

When I'm working obviously I want that it should not power off so quickly hence set the delay to 20 minutes. 

What this means now it should not switch off the monitor for 20 minutes. 

This strategy worked in Intrepid and in jaunty no matter what values I set it goes to sleep in 1 minute.

---

### Post by LordVeovis on 2009-01-11
> **ShirishAg75 said:**
> ok lemme be more clear. 

I follow 2 ways/strategies for powering of monitor or not. 

When I'm sleeping or not using the computer the monitor is supposed to sleep in 1 minute. 

When I'm working obviously I want that it should not power off so quickly hence set the delay to 20 minutes. 

What this means now it should not switch off the monitor for 20 minutes. 

This strategy worked in Intrepid and in jaunty no matter what values I set it goes to sleep in 1 minute.

Ahh, thanks.  Let me try to reproduce.

---

### Post by LordVeovis on 2009-01-11
How do you reproduce? I never changed my power settings from defaults.  gnome-power-manager when launched from terminal does nothing.  gnome-power-preferences is what is in System>Preferences>Power Management and I can set it only down to 11 min.

---

### Post by ShirishAg75 on 2009-01-11
That is because of gnome-screensaver-preferences. What you need to do is first set gnome-power-preferences delay to say something say like 20 minutes or any delay. **Only** within the delay set in gnome-screensaver-preferences you can set the gnome-power-preferences.

---

### Post by LordVeovis on 2009-01-11
> **ShirishAg75 said:**
> That is because of gnome-screensaver-preferences. What you need to do is first set gnome-power-preferences delay to say something say like 20 minutes or any delay. **Only** within the delay set in gnome-screensaver-preferences you can set the gnome-power-preferences.

So correct me if I am wrong.  Set the 'Reguard the computer as idle...' to 1 min and set 'Put display to sleep...' to 2 min

is this right?

---

### Post by ShirishAg75 on 2009-01-11
> **LordVeovis said:**
> So correct me if I am wrong.  Set the 'Reguard the computer as idle...' to 1 min and set 'Put display to sleep...' to 2 min

is this right?

It could be "put display to sleep" to 2 minutes to never. You should actually get the whole range. 

If you are getting a barrier of 11 minutes or something in gnome-power-preferences after setting gnome-screensaver-preferences to 1 minutes that's a bug (that shouldn't happen) and you should consider filing a bug-report. 

Also make sure you haven't clicked the "Activate Screensaver when computer is idle"

---

### Post by LordVeovis on 2009-01-11
> **ShirishAg75 said:**
> It could be "put display to sleep" to 2 minutes to never. You should actually get the whole range. 

If you are getting a barrier of 11 minutes or something in gnome-power-preferences after setting gnome-screensaver-preferences to 1 minutes that's a bug (that shouldn't happen) and you should consider filing a bug-report. 

Also make sure you haven't clicked the "Activate Screensaver when computer is idle"

Ok, it let me set them lower once I made that change.  I have Idle set to 1 min and I had screensaver set to start and I had the monitor set to turn off after 2 min.  It worked fine like this.  I just unchecked the SS box and will test again now.

---

### Post by LordVeovis on 2009-01-11
OK.  Just tested with 1 min for Idle and 2 min for monitor turn off and after 1 min of idle, nothing happened.  After 2 min the monitor turned off, will try some other values.  You said your monitor is turning off after just 1 min though?  Are you sure it isn't just the 'Blank Screen' screensaver?

---

### Post by ShirishAg75 on 2009-01-11
its not because I've disabled screensavers :)

---

### Post by LordVeovis on 2009-01-11
I have let it site idle for more than 1 min and had nothing happen.  Monitor set to turn off in 10 min.

Ok I set it to 1 min idle and 20 min monitor off and I will be going to buy drinks and will be back within 15 min.  If my monitor is off then i would have your problem to some extent.

---

