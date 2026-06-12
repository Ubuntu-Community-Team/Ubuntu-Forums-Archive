---
title: "Greek font problem"
date: 2009-03-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by aethralis on 2009-03-10
I'm suddenly experiencing a weird font problem. This could be of course due to wikipedia itself (and can be that this is a wrong forum to post the question). But anyhow, I have two attachments here and in one the Greek font is really strange - in the other it is normal. The strangeness results from wikipedia tag {lang|el}. Has anyone else experienced this? I have not noticed it before, seems that this appeared only today (or so). My WinXp in Virtualbox displays the Greek text OK. Any ideas?

---

### Post by Reiger on 2009-03-10
It's caused by lack of a good system font for Greek texts. If you have WinXP and you feel comfortable doing this you can just install all your Windows Fonts (TTF altough a couple other types will also work) and consider it fixed (you'll now have the same system fonts available in Ubunutu as well).

---

### Post by aethralis on 2009-03-10
Hmm.. thats not the cause, I'm afraid. As the other characters (second screenshot) are displayed correctly the lack of good system font is probably not the cause. As I said, I have not experienced this before (and I have used Jaunty for some weeks now).

---

### Post by Nullack on 2009-03-10
edit - wrong thread

---

### Post by Reiger on 2009-03-10
> **aethralis said:**
> Hmm.. thats not the cause, I'm afraid. As the other characters (second screenshot) are displayed correctly the lack of good system font is probably not the cause. As I said, I have not experienced this before (and I have used Jaunty for some weeks now).

First those are two distinctly different font classes: one is Serif the other is Sans-serif (Arial style by the looks of it). I suggest installing Palineo Lineotype and see if that makes a difference (its a Win XP font). 

Put it another way: I experience (consistently) the same issues because I frequent certain fora where Greek excerpts are thrown around from time to time. Installing a swathe of Windows fonts consistently fixes it (heck, it may just be a narrow-minded CSS rule insisting on a Windows font be present when its not).

---

### Post by aethralis on 2009-03-10
Problem solved after reboot (did not install any new fonts). No idea what was wrong.

---

