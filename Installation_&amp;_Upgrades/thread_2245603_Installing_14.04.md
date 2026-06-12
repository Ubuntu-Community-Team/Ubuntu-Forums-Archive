---
title: "Installing 14.04"
date: 2014-09-24
forum: Installation &amp; Upgrades
---

### Post by christopher18 on 2014-09-24
Hello Everyone,

I'm very new to Ubuntu and decided I'd like to try it out, alongside with my Windows 7 installation. I created a Live CD to give it a go, which has since then created some issues. I'm not able to boot into the Live CD or Install Ubuntu unless I revert back to default CPU clock settings within my BIOS.

So, there's the issue. I also cannot install Ubuntu with my current clock settings.

Anyone else have this issue and know how to fix it? I can provide any information you need to assist me, if possible.

Thank you in advance.

---

### Post by christopher18 on 2014-09-24
I did some poking around and it might be due to unstable clock settings. I've had these clock settings for over a year now and haven't had any issues with Windows 7 at all. They're stable and I idle around 40C.

For some closer look, I have an Asus P6X58D Premium Motherboard and a Intel Core i7 920 Bloomfield, overclocked at 4.0GHz. Trying to install the 64-bit version of Ubuntu 14.04.1. I'm only able to install or load into the Live CD if I put my clock settings back to "auto" or just default back to original settings.

When trying to install, I get a Kernel Panic and it does nothing. If I try to load into the Live CD, I get a Kernel Panic and it continuously reboots.

---

### Post by mastablasta on 2014-09-25
are you saying now that even on auto clock settings you can't get into live CD? if so did you check that downloaded image is good and that the burn is good?

---

### Post by christopher18 on 2014-09-26
mastablasta, thanks for the reply. Not sure why I didn't get some sort of alert or notification but, anyhow, no. I can get into the Live CD or can even install Ubuntu when I'm on auto clock. As soon as I set my clock back to my manual clock, it Kernel Panics.

---

### Post by christopher18 on 2014-09-27
So, I actually solved this and thought I'd share my resolution.

It doesn't seem that Ubuntu liked my original clock I was using. I noticed that if I change my CPU Ratio aka Multiplier from 21 to 20, it would boot just fine and everything was good to go. However, changing it from 21 to 20, would obviously make me lose some CPU speed. I decided to back it down to 20 and change my BCLK to 200 and just change my voltage .1, in order to keep a stable clock. This still achieved my goal of 4.0GHz from the processor and allow me to boot in. If anything, this helped me, because the temps are virtually exactly the same and now I'm utilizing my memory a lot better with a 20 CPU Ratio. I ran Prime95 and IntelBurnTest v2 on my Windows partition and everything was stable.

This allowed me to install Ubuntu, which is what I'm posting from as I'm typing this.

Even though no one was able to help me here, I thought I'd still share my resolution and hope it helps someone else in the future.

Thank you, I look forward to some adventures into Ubuntu.

---

