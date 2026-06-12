---
title: "installing 64 bit computer from 32 bit Ubuntu live CD"
date: 2012-02-17
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2012-02-17
Should I be able to boot to and subsequently install a 32 bit version of Ubuntu from the live CD to a 64 bit computer ?

The reason I ask is because I placed a 32 bit live CD in my nieces' desktop computer and it would never boot up to the live CD.  I gave it what I thought was more than a sufficient time to boot from/to the CD but it never came to the TRY or INSTALL screen.

Yes computer was set to boot to CD.

Her computer is one of those new fangled jobs (by Toshiba) that has every thing built into the monitor.  Would the all-in-one feature have anything to do with it not booting to the 32 bit live CD ?

Thanks.

---

### Post by darkod on 2012-02-17
Yes, you can install and run 32bit on 64bit computer. The opposite doesn't work.

Not being able to run in live mode (Try Ubuntu), most likely has something to do with the video card. Do you know the model?

Do you get the first purple screen with the keyboard and man icon? Or nothing at all?

If you get the very first purple screen, hit Esc and it should load the older type of menu. There by pressing F6 you can open advanced options, which allows you to select boot parameters like 'nomodeset' (most often used for video issues), and only then you can select Try Ubuntu from the menu.

If that helped, note that after installing the first reboot you need to also enter by adding that parameter, and later you can make it permanent from inside ubuntu.

---

### Post by wpshooter on 2012-02-17
> **darkod said:**
> Yes, you can install and run 32bit on 64bit computer. The opposite doesn't work.

Not being able to run in live mode (Try Ubuntu), most likely has something to do with the video card. Do you know the model?

Do you get the first purple screen with the keyboard and man icon? Or nothing at all?

If you get the very first purple screen, hit Esc and it should load the older type of menu. There by pressing F6 you can open advanced options, which allows you to select boot parameters like 'nomodeset' (most often used for video issues), and only then you can select Try Ubuntu from the menu.

If that helped, note that after installing the first reboot you need to also enter by adding that parameter, and later you can make it permanent from inside ubuntu.

It has been a while since I tried it but seems to me that I got no video at all.

I will try ESC and see what happens.  Is it the nomodeset parameter that I need to choose or is it something under F4 function that relates to video resolution choices ?

Thanks.

---

### Post by darkod on 2012-02-17
The F6 will open a list of 5-6 parameters, nomodeset will be one of them. It is the first one to try, in other cases sometimes acpi=off or noacpi helps. It depends, you can try few options.

Usually if it allows to run in live mode, it will run later when installed with the same parameter.

---

