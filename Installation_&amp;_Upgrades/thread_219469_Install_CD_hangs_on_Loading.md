---
title: "Install CD hangs on Loading"
date: 2006-07-20
forum: Installation &amp; Upgrades
---

### Post by nesl247 on 2006-07-20
Hello there. I just burned the livecd, got it to come to the graphical boot menu. You know whwere you choose to boot from harddisk, or install. Anyways, it gets to where it says loading and thats it. It doesn't do anything. Cdrom looks like it's reading, but nothing seems to be happening.

I'm going to go back and check the md5sums, but if that's not it, I don't know what is causing it.

---

### Post by swamytk on 2006-07-20
1. Boot with Install CD.
2. Select Media check option in the main menu
3. This test *must* pass through for successful installation.
4. If this test fails, problem is with your CD; else post here the exact stage at which the install fails with message on screen.

Note: what it your hardware configuration?

---

### Post by nesl247 on 2006-07-20
I wish I could do media check.It hangs on every single option there on the Loading part.

And my download just passed the md5sums test.

Also, it's a laptop. Toshiba Satellite A75 S229.

P4 Mobile 3.2Ghz
786MB RAM - Minus 128 for Graphics Card
ATI Radeon Mobility 9000

If you need more detailed specs, just ask.

---

### Post by swamytk on 2006-07-20
> **nesl247 said:**
> It hangs on every single option there on the Loading part.

where it hangs? what do you see on monitor when it hangs? do you get console?

---

### Post by nesl247 on 2006-07-20
As I said previously, it hangs when the message "Loading" appears. I'm still on the stupid main boot menu when it appears..

It seems my laptop is a piece of crap, or nero is, not really sure. Either way one of them is causing the cd to not burn properly. I'm going to try poweriso.

---

### Post by dirtylobster on 2006-07-20
I had the same problem. Burned the cd again (CDRW) and voilá!

---

### Post by swamytk on 2006-07-20
If you have more than one SIMM/DIMM modules as RAM, try removing one from slot and boot. Once I have faced such a problem, some times memory speed mismatch may cause such problem.

---

### Post by rgladwell on 2006-07-20
I'm getting exactly the same problem on my Dell Dimension 5150, ATI Radeon X600, 3G RAM. I tried re-burning the image but just got the same problem with both media check and installation options.

I'm not sure about removing memory cards from my computer: won't that invalidate my warranty? Is there some other way of discovering what is causing the error?

---

### Post by RRS on 2006-07-20
Could be a problem with the cd drive.

Do you have another machine/drive you could try it in?

---

### Post by nesl247 on 2006-07-20
I reburned it on another computer and now it's booting. Not sure if it was the drive or nero, either way, I'm just happy it's working now.

---

### Post by rgladwell on 2006-07-20
Sorry, looks like it was the ISO image: I downloaded another and it loaded fine.

---

