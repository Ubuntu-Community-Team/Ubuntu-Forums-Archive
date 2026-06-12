---
title: "CPU Frequency Scaling stopped working / shutdown problems"
date: 2010-04-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by quad65 on 2010-04-26
Hi,

Using 10.04 RC. This had happened before, I reinstalled Ubuntu. Now it's happening again. I believe something I do messes the system. I also cannot shutdown/reboot automatically. It simply waits forever. I have to press the button manually.

I need your help to find out what I did to break the system.

Thanks in advance.

What I remember I did that could be relevant:

-Compiled xserver with patch suggested below to prevent window management issues. See here:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988)

-Also using the script there to free memory.

---

### Post by LowSky on 2010-04-26
I have the same issue since way back from the Alpha , and its still occuring. probably a glitch yet to be fixed. If you hear the hard drive spin down, its ok to turn the PC off or reboot.

Newer users shouldn't be using a product that has not been officially released. And posting about this are supposed to go in the developement portion of this forum. You should also send the Bug to Launchpad so that the developers get a headcount of people effected.

---

### Post by quad65 on 2010-04-26
> **LowSky said:**
> I have the same issue since way back from the Alpha , and its still occuring. probably a glitch yet to be fixed. If you hear the hard drive spin down, its ok to turn the PC off or reboot.

Newer users shouldn't be using a product that has not been officially released. And posting about this are supposed to go in the developement portion of this forum. You should also send the Bug to Launchpad so that the developers get a headcount of people effected.

Alright, a moderator should move this topic, then.

Since you said you have the same problems and I should send the bug the launchpad, could you give me the link to bug report assuming that you reported it?

---

### Post by dino99 on 2010-04-26
> **quad65 said:**
> Alright, a moderator should move this topic, then.

Since you said you have the same problems and I should send the bug the launchpad, could you give me the link to bug report assuming that you reported it?

into console: ubuntu-bug linux   ( then "enter" to validate )

you'll be asked to create your account on launchpad to be allowed to report

---

### Post by quad65 on 2010-04-27
> **dino99 said:**
> into console: ubuntu-bug linux   ( then "enter" to validate )

you'll be asked to create your account on launchpad to be allowed to report

Thank you. But at the moment, I can't even specify which package/how to reproduce etc..  So I did not report it yet. I want it to be a useful report, not waste somebody's time.

If only someone could help me track this bug down...

---

### Post by forcecore on 2010-04-27
i can shutdown fine but when i shutdown and my power mode is powersave then after startup scaler has switched to performance mode, so basically it wont remember settings.

---

