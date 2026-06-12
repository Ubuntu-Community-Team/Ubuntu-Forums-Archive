---
title: "ATI Graphics Card Proprietary driver problem after upgrading to 12.10"
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by shresthanator on 2012-11-13
so i just upgraded from 12.04- and I seem to be having issues with my ATI HD 4870 card. After googling for the solution- seems like this is a pretty wide spread problem. 

My main issue is if I install the proprietary drivers and reboot- my system craps out. The resolution is low and unity is gone. 

So to be honest, I don't know much about this. I have looked through the fourms and I have tried what other ubuntu users have suggested... I have tried to manually install fglrx, fglrx-updates, tried to install old drivers, and the version from the AMD website....nothing seems to be working. 

I know very little about this- but I have read that this might be a problem with Xserver. "Some say that the new Xserver version is not supported by ATI". 

What does this mean for an average user like me? I really cannot afford a new graphics card right now, should I just go back to using 12.04? 

Is it likely that this problem will be fixed in the near future? 

Has anybody found a workaround to this issue?

---

### Post by SysBoot on 2012-11-13
Have you tired installing one of these?
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)
if so does it work? What happens when or if it doesn't?
Also, have you tired installing the additional proprietary dirver in "additional drivers"?

---

### Post by QIII on 2012-11-14
Your card has been moved to a legacy driver support branch and will not work with any driver that will work with X Server 1.13, which is used by Ubuntu 12.10.  Installing a driver from ATI's website will be of no use, as the driver that would otherwise work with your card will not work with X Server 1.13.  The 12.10 driver will not work with your card.

This is not an "X Server problem".  It is the result of AMD/ATI's decision to terminate ongoing Linux driver development for the card.

There is no solution that includes an ATI driver unless you are also willing to go back to an older version of X Server, which is not a satisfactory answer.

Short of buying a new card, you have pretty much one option if you stay with Ubuntu 12.10:  use the default open source Radeon driver, which has gotten very good and should serve the vast majority of users very well.

Since 12.04 is an LTS, using it might be your best course of action for now.

---

### Post by SysBoot on 2012-11-14
> **QIII said:**
> Your card has been moved to a legacy driver support branch and will not work with any driver that will work with X Server 1.13, which is used by Ubuntu 12.10.  Installing a driver from ATI's website will be of no use, as the driver that would otherwise work with your card will not work with X Server 1.13.  The 12.10 driver will not work with your card.

This is not an "X Server problem".  It is the result of AMD/ATI's decision to terminate ongoing Linux driver development for the card.

There is no solution that includes an ATI driver unless you are also willing to go back to an older version of X Server, which is not a satisfactory answer.

Short of buying a new card, you have pretty much one option if you stay with Ubuntu 12.10:  use the default open source Radeon driver, which has gotten very good and should serve the vast majority of users very well.

Since 12.04 is an LTS, using it might be your best course of action for now.
This is probably a stupid  question, but is the open source driver the default one before you install additional drivers, or is it the one in additional drivers?

---

### Post by Mark Phelps on 2012-11-14
> **SysBoot said:**
> This is probably a stupid  question, but is the open source driver the default one before you install additional drivers, or is it the one in additional drivers?

Not a stupid question ... but, the open source driver IS the one installed by default as part of Ubuntu installation or upgrade.

---

### Post by lonewohlf42 on 2012-11-16
Hi  I have an ATI HD 4830 graphics card and my system works perfectly with the live Ubuntu 12.10 DVD. My card uses the same drivers as yours. I had the same problem as you
after I upgraded from 12.04 to 12.10.
I used Ctrl+Alt+T to open a terminal and typed in "unity" then enter. This reset unity and from then on everything worked properly. I also sometimes get a "compiz has shutdown unexpectedly" error message, but typing "unity" into a terminal resets everything and all works from then on. This is only a temporary solution. I'm still having problems when I first boot up my system. I'm working on a fix. The fact that the live dvd of 12.10 64 bit works perfectly tells me that the problem is not the graphics card driver. Try using the live dvd yourself if it works then you know it's not the driver. I get the Linux Format magazine 
and they have had the same problem trying to upgrade to 12.10. They had no solution either. In their article they say they hope Canonical  fixes the problem before publication
but no such luck.

---

### Post by QIII on 2012-11-16
The fact that it works from a Live CD indicates that the default open source Radeon driver is being used and has no bearing on the performance of the proprietary driver..  If it is working in an installed environment, it is because the default open source Radeon driver is being used, or you have used a scripted solution with a PPA to downgrade X Server and install an older proprietary driver.  Otherwise, you cannot be using the proprietary driver that would otherwise work with that hardware.

This situation *will not* and *cannot* be fixed by Canonical or the purveyor of any Linux distribution.

Unless AMD/ATI reconsiders its position on continued development and Linux driver support for the legacy products, there is no "solution" to be had.

---

### Post by lonewohlf42 on 2012-11-16
I have done nothing to the drivers or downgraded anything it works as is. I'm using it right now, and it works fine after typing unity in the terminal and pressing enter. I'm not the only one that this worked for. I got this from another person who posted on the forum.

---

### Post by lonewohlf42 on 2012-11-16
I didn't mean to get you upset.

---

### Post by QIII on 2012-11-16
Who is upset?

The OP asked about the proprietary driver.  You are not using the proprietary driver with Quantal unless you have downgraded to X Server 1.12 and are using an older driver.  You are using the default open source Radeon driver as I suggested the OP should do.

Of this I am quite sure.

---

### Post by lonewohlf42 on 2012-11-16
I understand what you mean about the driver, but there is still the problem with the upgrade to 12.10 not working properly. I still have the problem of unity not working
when I start up my computer and why I have to enter unity in a terminal to get it to work.
You also should check out the article in Linux Format Magazine, the article doesn't paint a pretty picture about ubuntu 12.10 performance rating of 4 out of 10 and overall score of 6 out of 10.

---

