---
title: "Updated Ubuntu / Constant Reboot"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by asmegin_slayer on 2008-12-01
Hello,

I gave away a custom built computer, with ubuntu 8.04, of mine as a christmass present last year. It has run well for him until recently... A few weeks ago I had asked him if he had ever installed the required updates on his computer, which I found out that he hasn't been. So I told my brother to install the automatic updates that ubuntu puts out....

Well while he was installing the updates, he did get a few error messages (he couldn't remember what were they)... Then he went ahead and restarted the computer... When he logged in, the computer suddenly restarted by its own. When it got to the splash screen, it restarted again at random times.... It also restarts during the GRUB loading part.

At first I thought it was a Power supply issue, but alas it was not. He restarted and then the machine asked to go to BIos to fix the CPU time i think? So we went inside the cmos and found that the time was incorrect. so we changed it to the correct time and rebooted it again. And the computer still reboots when getting into the Grub screen...

I'm stuck, I'm assuming that the update must of messed something with GRUB.. is there a way to fix this issue?

---

### Post by lemming465 on 2008-12-02
If the power supply is OK, run memtest86+ for at least 30 minutes to see if you have any RAM issues.  Your symptoms sound like more a hardware problem.

---

