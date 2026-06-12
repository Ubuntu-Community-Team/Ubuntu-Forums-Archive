---
title: "Shows keyboard/human icon, then stops with cursor in uper left corner."
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by horseatingweeds on 2011-01-12
What does it mean if you boot from a live CD, the CD spins, a screen appears with the keyboard and human icons at the bottom, then a blank screen appears with a blinking cursor in the upper left corner - and that's it? It just stays that way.

I've tried two different discs, one 10.04 and one 10.10; and two different disc drives.

---

### Post by horseatingweeds on 2011-01-13
I've tried Kubuntu also. It's first screen is the menu. I choose 'Start Kubuntu' and then I'm back with the blank screen and blinking cursor. 

Should I give up?

---

### Post by horseatingweeds on 2011-01-13
I've tried Kubuntu also. It's first screen is the menu. I choose 'Start Kubuntu' and then I'm back with the blank screen and blinking cursor. 

Should I give up?

---

### Post by Quackers on 2011-01-13
What graphics card do you have?

---

### Post by horseatingweeds on 2011-01-13
Radeon 7000, ATI

---

### Post by Quackers on 2011-01-13
First, have you checked the MD5SUM of the downloaded iso file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that checks out you should check the cd for errors. When booting from the cd press the Esc key, choose language, then you should get a screen with some options. Choose the one for checking the cd.
If that checks out ok, from the same screen press F6 key and some boot options should appear. I'm not sure which will be best for your graphics card, but the nomodeset option seems to work for a lot.

---

### Post by horseatingweeds on 2011-01-14
The hash matches. I burned a fresh CD. Hitting escape while it tries to boot from the CD brings up a menu. But when I try any of the options it gets stuck in the blank screen with blinking cursor, including when I try the disc error checker. The escape key gets me into the textual installer - or what I assume is. A prompt appears awaiting a command. 

I tried a Debian CD. That seems to work. I got into the graphical installer easily and right away.

---

### Post by Quackers on 2011-01-14
Did you try the boot options? nomodeset/i915.nomodeset=1 etc, etc. All of them, one at a time?

---

### Post by horseatingweeds on 2011-01-14
I tried each of the 'Other Options' one at a time: 
apci=off
noapci
nolapic
edd=on
nodmraid
nomodeset

Are those the options you're talking about? The only other options categories I've seeing are Help - Keymap - Language - Modes - Accessibility - Other Options

---

