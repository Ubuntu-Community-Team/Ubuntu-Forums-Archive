---
title: "System freezes during boot, unless I hold a key down"
date: 2008-09-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by SoCalChris on 2008-09-19
I upgraded from Hardy last night, and on rebooting am getting a weird behavior. 

Once the Ubuntu splash screen loads with the progress bar that moves back and forth, it freezes. Holding down any key unfreezes the system, and it continues loading normally, until I release the key, at which point it freezes again. Holding a key down again unfreezes the system again.

Pressing Alt+F1 to show the output also freezes, so I know it isn't just the splash screen freezing, but the entire system.

Once X loads, it works perfectly fine though, and I don't have to keep holding a key down.

I tried Ibex before (I think it was around the Alpha 3/4 timeframe) and saw the same exact behavior. I had hoped it would be fixed by now, but apparently this isn't common enough that it's getting a lot of attention.

I wasn't able to find a bug like this on launchpad, so I'll be submitting it there. In the meantime, does anyone have a workaround for this? It makes rebooting the system remotely kind of difficult... ](*,)

---

### Post by pro003 on 2008-09-19
what do you mean by "you've upgraded from hardy"?

---

### Post by SoCalChris on 2008-09-19
The system was running 8.04 previously, and was updated by using "upgrade-manager -d".

I am getting this behavior though regardless of doing a clean install, or upgrading from the previous version.

---

### Post by 67GTA on 2008-09-19
I had the same problem testing the alpha 5 live CD on my HP dv6815. The progress bar would stop, and the CD would stop loading/spinning. It doesn't matter what key, as long as I held one down, it would finish booting. I thought it might have just been a bad burn. I guess one of us need to file a bug report.

---

### Post by SoCalChris on 2008-09-19
This is on an HP DV6661SE. AMD dual core, running 64bit. I don't get this problem running the live cd, only once it has been installed.

---

### Post by 67GTA on 2008-09-19
AMD/Nvidia Dual Core 64bit here also. Hmmm....

---

### Post by pro003 on 2008-09-19
What kernel version are you running?

---

### Post by SoCalChris on 2008-09-19
It's now been submitted as a bug.
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/272247](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/272247)

Kernel version is 2.6.27-3-generic x86_64

---

### Post by pro003 on 2008-09-19
when you boot up and grub shows up, do you have options to chose other kernels, if yes, select 2.6.24.19 - generic

this is the latest one updated on ubuntu 8.04 I run...

anyway try other kernel except for that one your mentioned above...

---

