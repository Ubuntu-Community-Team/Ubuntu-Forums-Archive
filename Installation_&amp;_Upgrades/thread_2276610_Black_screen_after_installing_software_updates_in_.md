---
title: "Black screen after installing software updates in Ubuntu 14.04"
date: 2015-05-03
forum: Installation &amp; Upgrades
---

### Post by Howard-BJ on 2015-05-03
I have a Toshiba Satellite L 50-A-1FD laptop, with Nvidia Gforce 740M graphics. I have a dual boot installation with Windows 8.1 and Ubuntu 14.04 and was running on the advised 346.57 series Nvidia driver. After installing regular software updates on 1st May 2015, the computer boots to a dull purple screen, with about two cycles of the dots under the Ubuntu logo, and then goes to a black screen. I have tried to boot up with nomodeset, following advice from various sources. After booting with nomodeset, I get to my desktop login screen (though with a series of small white dots over the login screen - normally login is set to automatic without password), and my password is asked for, but not accepted. I have entered the password many times, and know that it is correct. I cannot get beyond this stage. What is the way of getting logged in and resolving the black screen issue. I have checked that the Keyboard setting is as before (UK English).

---

### Post by Christopher_angelo on 2015-05-18
> **Howard-BJ said:**
> I have a Toshiba Satellite L 50-A-1FD laptop, with Nvidia Gforce 740M graphics. I have a dual boot installation with Windows 8.1 and Ubuntu 14.04 and was running on the advised 346.57 series Nvidia driver. After installing regular software updates on 1st May 2015, the computer boots to a dull purple screen, with about two cycles of the dots under the Ubuntu logo, and then goes to a black screen. I have tried to boot up with nomodeset, following advice from various sources. After booting with nomodeset, I get to my desktop login screen (though with a series of small white dots over the login screen - normally login is set to automatic without password), and my password is asked for, but not accepted. I have entered the password many times, and know that it is correct. I cannot get beyond this stage. What is the way of getting logged in and resolving the black screen issue. I have checked that the Keyboard setting is as before (UK English).The only way to solve the password is by re-installing Ubuntu. I don't know about the black screen. But i think if you just re-install Ubuntu it will fixes it too.

---

### Post by QIII on 2015-05-18
No.  A reinstall may not be required and should generally not be the first thing that comes to mind.

Please refer to [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword).

However, this is likely due to a problem with .Xauthority and nothing at all to do with the password.

Can you get to recovery mode and follow the instructions in the link to the point that you have mounted the filesystem read/write?  (Don't move on to the password resetting part.)

---

### Post by Bucky Ball on 2015-05-18
> **QIII said:**
> No.  A reinstall may not be required and should generally not be the first thing that comes to mind.



+1. Reinstall always a last resort 'round these parts (and likely the problem would return after upgrading the new install to this point anyhow). ;)

---

