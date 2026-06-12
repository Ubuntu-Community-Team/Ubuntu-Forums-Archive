---
title: "&quot;Starting up...&quot; issue on Hardy"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by dadslayer on 2008-11-18
Hi guys,

I've been registered for a while and I'm more like an active reader than a poster. I keep browsing the forums everyday to find new stuff to read and also learn from others experiences.

In the last couple of days, however, I've been facing a minor (?) issue with my Ubuntu setup. Every now and then, when my computer boots up and I select Ubuntu to load up (I'm also using Windows XP - I'm a Web developer), I get the "*Starting up ...*" message... and that's it. Ubuntu won't load. Then, I just go and reboot my PC again, start over and it eventually will pass the "Starting up ..." message.

While this is not what I consider a normal behavior, I was willing to not pay attention to it and just forget about it. Get the message. Reboot. The problem is that now I'm getting this error more often than before (it used to appear every 3-4 days, now I'm being forced to reboot my PC up to 4-5 times before Ubuntu can load properly).

I must mention that I'm really new to Linux so please explain things to me as if I was a 6 yo kid.

Thanks in advance for all your help!

---

### Post by dadslayer on 2008-11-20
Bump!

---

### Post by dadslayer on 2008-11-21
Anyone? :(

---

### Post by mgangav on 2008-11-21
Do you remember if you had to install any major upgrade for this problem started to happen. Also, did you notice any other strange things after starting up Ubuntu completely?

---

### Post by dadslayer on 2008-11-22
> **mgangav said:**
> Do you remember if you had to install any major upgrade for this problem started to happen.Well, I've been using Ubuntu 8.04 all this time. Haven't upgraded / downgraded to any other distro so far.> **mgangav said:**
> Also, did you notice any other strange things after starting up Ubuntu completely?When Ubuntu loads, before the splash screen is shown I get some DOS-like messages similar to what older versions of Windows (98, ME, etc) shows when loading. Don't know if that's normal or not since I'm new to Ubuntu.

Other than that, Ubuntu seems to be working fine.

---

### Post by Eric06 on 2008-11-22
Hi, I also have the same issue, it looks like the PC has is when starting from 'cold' (just after putting power to the machine), I had this problem monthes ago and I did put a post: no response. After a Kernel update the issue disapeared, it came back a month or 2 ago...
It looks like Grub to Kernel transition dies, I could not find any error messages in the log either. 
here is the link to my original post [http://ubuntuforums.org/showthread.php?t=801366](http://ubuntuforums.org/showthread.php?t=801366)

A mystery so far

---

### Post by mgangav on 2008-11-24
> **dadslayer said:**
> Well, I've been using Ubuntu 8.04 all this time. Haven't upgraded / downgraded to any other distro so far.When Ubuntu loads, before the splash screen is shown I get some DOS-like messages similar to what older versions of Windows (98, ME, etc) shows when loading. Don't know if that's normal or not since I'm new to Ubuntu.

Other than that, Ubuntu seems to be working fine.

Well, I am also a newbie to Ubuntu, so bear with me. It seems that like the previous poster said, their is a disconnect happening somewhere during the boot up process.

Try starting Ubuntu in Recovery mode and see what happens.
If you are dual booting, just choose the recovery mode option from the Grub menu.
If you aren't dual booting. Try pressing escape during the startup process. Then you will get the menu from which you can chose recovery mode.

---

### Post by Eric06 on 2008-11-26
Has anyone searched if there is an open problem on GRUB for this. I did but could not find anything significant (and I have no clue how to log and track a problem)

I have upgraded to 8.10 last weekend in the hop of a change but I still have the same erratic behavior at start up : as everything changed but GRUB, it is either a bug in GRUB or a hardware setup (mine is 'optimised default' on my ACER aspire) in the BIOS that is not good.

---

