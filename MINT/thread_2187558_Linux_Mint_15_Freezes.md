---
title: "Linux Mint 15 Freezes"
date: 2013-11-12
forum: MINT
---

### Post by nickkrause on 2013-11-12
I have tried testing all my hardware and there fine have tried lubuntu and xubuntu and it still freezes and loops sound. Does anybody know how to fix this?

---

### Post by philinux on 2013-11-12
Moved to other distro support.

---

### Post by nickkrause on 2013-11-12
Fine is there any idea on what to do

---

### Post by nickkrause on 2013-11-12
I have tried reinstalled the amd fglrx drivers and it still freezes and loops sound can something please help if they even have a idea.

---

### Post by philinux on 2013-11-13
> **nickkrause said:**
> I have tried reinstalled the amd fglrx drivers and it still freezes and loops sound can something please help if they even have a idea.

Have you tried asking on the mint forums too?

[edit] check the xsession-errors file.

cat ~/.xsession-errors | pastebinit

---

### Post by nickkrause on 2013-11-13
[http://pastebin.com/d9ExPgdA](http://pastebin.com/d9ExPgdA) here is the link otherwise I have tried googling to no real solution

---

### Post by philinux on 2013-11-13
I see the vitual box error. Is this a vb install?

---

### Post by nickkrause on 2013-11-13
How would I fix this and no is is not installed in vb or have vb

---

### Post by buzzingrobot on 2013-11-13
What desktop are you using?  I see references to Cinnamon as well as XFCE.  

Can you provide more details? You say Mint is freezing, but then mention Lubuntu and Xubuntu.  Do they exhibit the same symptoms?  

What is freezing?  The mouse? Keyboard? When does that happen? Can you make it happen?  If so, how?

What does 'loops sound' mean?  Audio repeats?  If so, when? Is this associated with the freezing?   What is playing the audio? Does the freezing happen when audio is not playing?

Have you looked at the logs to see if any obvious errors are apparent?  I believe Mint has a log viewing app.

if you've added any software that wasn't in the stock install and runs at startup, temporarily disable it.

---

### Post by nickkrause on 2013-11-13
everything freezes and then loops at random when playing video or music normally , have looked through the logs and no issue in addition it happens in xfce and cinnamon

---

### Post by nickkrause on 2013-11-13
In addition reboots after a few seconds

---

### Post by nickkrause on 2013-11-13
It loops the sound and freezes too happens every few days tried with xubuntu and lubuntu too and to no success

---

### Post by buzzingrobot on 2013-11-13
Still unclear on what DE you are actually running and how you can continue to use that unnamed audio app after  "everything" freezes. 

References to XFCE and Cinnamon in that text snippet indicate that components of both are trying to launch. Were XFCE and Cinnamon previously installed?

Are the freezing and the looping (which you haven't explained but I gather is that unnamed app playing the a bit of audio repetitively) happening together?  If so, what happens first?

If the same behavior occurs on clean, separate, installs of Mint, Lubuntu, Xubuntu, etc. (meaning you have burned the iso's and installed each cleanly, rather than installing the respective packages on a single install) then something that is common to all must be triggering the behavior.  What they all have in common is the Ubuntu base and the hardware they run on.  You might look to see if anything is running too hot.

If you are using a proprietary video driver on a machine that supports Intel video or a FOSS driver, you might switch away from the proprietary driver to see its impact.

You don't mention the hardware in use, or the version of Mint that you are using, or what DE you are using, or which video drivers are in use.  So, we're left to make guesses.

---

### Post by nickkrause on 2013-11-13
yes there happening togethor and  th audio stops first 
I have using the amd driver.
 I addition it's a i5 2500k with an asu motherboard and intel 520 ssd with a 7770 amd graphics card.
I am using xfce

---

### Post by nickkrause on 2013-11-13
Also it's Linux mint 15 .

---

### Post by nickkrause on 2013-11-13
[http://pastebin.com/N75EMN7p](http://pastebin.com/N75EMN7p)
here is my .xsession-error file anything else or can you help me now?

---

### Post by buzzingrobot on 2013-11-13
Did you install the Cinnamon screensaver or does Mint use that on its XFCE release?

Again, I'd temporarily switch away from the proprietary AMD driver to determine if that's the source of the problem.

I remember seeing reports of Pulseaudio being blamed for lockups.  Given the potential connection with audio, that would be worth exploring.

The forums at linuxmint.com are also available. You're more likely to find someone experiencing the same problem on Mint 15 XFCE there.

---

