---
title: "Macbook Pro 2'nd Gen Ati Freeze when starting X"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by wilbur.harvey on 2009-03-28
I updated my laptop last night, after no updates for 2 weeks. Now when I try to boot, it puts some garbage at the top of the screen and the entire freezes when it trys to start X. I can boot to a safe mode command prompt OK. My only option is to power off at this point. I have 3 other machines with NVidia graphics and none of them have this problem. All were upgraded on the same schedule. Any ideas?

---

### Post by minimec on 2009-03-28
Hi

The description of your problem is not very clear to me. 

Some Questions:

- I don't understand what you mean by save mode... Do you get that "low- graphics-mode" screen after a while, or do you have a complete system freeze?

- When it 'freezes', can you switch to a console with <ctrl><alt><F1> ?

- I guess that what you called "safe mode command prompt" is the "recovery mode" of grub, at the beginning of the boot process. Is that correct?

- What happens if you use an older kernel to boot the machine? You probably have the original hardy kernel 2.6.22-14-generic installed as a 2nd boot option in grub.

- Do you use the amd/ati fglrx restricted driver or the open source driver?



Cheers Minimec

---

### Post by Nullack on 2009-03-28
Bug report?

Have a look at the debugging X section of the Ubuntu wiki it contains allot of useful info - and really about most systems problems topics.

---

### Post by ktp on 2009-03-28
> **wilbur.harvey said:**
> I updated my laptop last night, after no updates for 2 weeks. Now when I try to boot, it puts some garbage at the top of the screen and the entire freezes when it trys to start X. I can boot to a safe mode command prompt OK. My only option is to power off at this point. I have 3 other machines with NVidia graphics and none of them have this problem. All were upgraded on the same schedule. Any ideas?

What chip is your ATI?  Where you using fglrx drivers?  If you were and you have R300-R500 then you will have to purge the fglrx drivers and make sure your xorg config does not use it.  You will have to use the open source ati drivers since fglrx dropped support for them.

---

### Post by wilbur.harvey on 2009-03-29
lspci lists the graphics as:
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]

By freeze, I mean the only thing I can do is to power off the machine. Nothing else responds.

I did not explicitly use the fglrx driver, but it was installed.

I uninstalled the fglrx driver from synaptic and the machine now works.

I tried booting from the previous kernel, but it still hung the same.

---

