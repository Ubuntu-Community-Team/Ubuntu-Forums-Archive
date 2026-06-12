---
title: "Video Resolution problem 9.10-&gt;10.10"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by OriTheEep on 2011-04-07
Having clicked the Update button from the Update Manager, I returned to my PC some time later and, after viewing messages about problems with something called fglrx, clicked the reboot button. Instead of my normal desk top, there were lots of lines on the screen and a large square also of lines, which turned out to be the mouse cursor.

I reset the machine and booted into Recovery mode. Lots of faffing about with "Repairing broken packages" and associated reboots and I had a visible desktop - but at a very low resolution.

The PC uses a Sapphire Radeon HD 3450 card (ATI) with an old ADI Microscan 5GT via VGA. With 9.10, I had this set to 1600*1200 which setting appears to be still in place as I see a message "Could not apply the stored configuration for monitors X Server does not support size" while the desk top is loading.

Having had problems before with the ATI driver with 8.10, I tried to remove it. Ah, that's what the fglrx business was all about! No dice:"installArchives() failed" and back to lots of pretty lines.

So I had two error conditions to research and found plenty but nothing seemed applicable. It is possible that the solution does lie with something I have already read but since all the solutions I've seen are specifically tailored to the individual problem described, I'd rather not mess about with something that might do real damage if incorrectly used.

Enough waffle from me. I'll (naturally!) post the contents of any relevant files should they be needed but shan’t clutter this request with possibly unnecessary ones now.

Thanks for reading.

Tom.

---

### Post by mörgæs on 2011-04-07
ATI made closed-source (fglrx) drivers for 9.10, but not for later releases. For these, the open source drivers is the way to go, and they have actually improved a lot. 

If you had fglrx enabled while upgrading, this could explain the trouble. 

I would go for a clean install of 10.10. My guess is that this will be faster and safer than messing with obsolete configuration files.

---

### Post by OriTheEep on 2011-04-08
> **mörgæs said:**
> ATI made closed-source (fglrx) drivers for 9.10, but not for later releases. For these, the open source drivers is the way to go, and they have actually improved a lot. 

If you had fglrx enabled while upgrading, this could explain the trouble. 

I would go for a clean install of 10.10. My guess is that this will be faster and safer than messing with obsolete configuration files.

Thanks for the reply, mörgæs.

Can I ask a couple of questions?

Will the latest open-source driver support 1600*1200? I suppose it should but I haven't been able to find out for myself.

Re-installing from scratch is always a major pain. If I have to write off this installation anyway, it won't hurt to try and rejig it. If it is too much to try and guide me through fixing the configuration files that need to be looked at (and I quite understand that the people capable of helping others on here must be keeping very busy), could I just have the names and locations of possibly relevant files so I can try and research them myself?

Thanks again.

---

### Post by mörgæs on 2011-04-08
It's not that I don't want to take the time for helping. I just don't know the answers (have Nvidia screen card).

---

### Post by OriTheEep on 2011-04-08
> **mörgæs said:**
> It's not that I don't want to take the time for helping. I just don't know the answers (have Nvidia screen card).

:oops: Sorry, didn't mean to upset.

---

### Post by mörgæs on 2011-04-08
You didn't! I just tried to say that I could not help more in this thread. 

English is not my mother tongue, so maybe it sounded strange.

---

### Post by OriTheEep on 2011-04-08
> **mörgæs said:**
> You didn't! I just tried to say that I could not help more in this thread. 

English is not my mother tongue, so maybe it sounded strange.

Ah!

No, it's not your English (much better than many who use it as a native language btw) at fault. Simply the difficulty caused by words on a screen lacking the tone of voice which conveys so much in conversation. Smilies help - a bit.

Looks like I'll have to take a deep breathe and dive in then. I'll be very dischuffed if I do all that and then find I still can't get the right screen resolution. :(

---

