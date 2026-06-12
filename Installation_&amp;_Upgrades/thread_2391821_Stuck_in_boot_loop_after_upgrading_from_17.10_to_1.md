---
title: "Stuck in boot loop after upgrading from 17.10 to 18.04"
date: 2018-05-13
forum: Installation &amp; Upgrades
---

### Post by echemdaniel on 2018-05-13
Hello all, I'm having a challenge after upgrading from 17.10 to 18.04. The package download  and installation process was successful (through update center). The laptop was required to reboot, to complete the upgrade, but it never made to the login screen after displaying the Ubuntu boot splash screen with the dots. It kept displaying "[ok] started gnome display manager at...link was shut down", as the last line on a black screen.

I'm running this as a dual boot on my Dell Inspiron 15 7537 with Intel HD Graphics Card.

I'm new to Linux. Any help would be appreciated.

---

### Post by avidhunter3 on 2018-05-13
I just upgraded my Compaq Presario from 16.04 and it hangs at the same point. I do note that further up the credits list there is one line item that does not have a green OK at the beginning but rather a red astrix.  The line states "A start job is running for hold until boot process finishes up (1min 9s / no limit)". I strongly suspect that we have the same issue.  Please help us both.

---

### Post by wildmanne39 on 2018-05-13
Hello and welcome to the forum avidhunter3, please create your own thread so the OP of this one and yourself can receive the help you both need.

Thanks

---

### Post by mörgæs on 2018-05-14
Have you considered a fresh install of 18.04?

---

### Post by moschops on 2018-05-14
Having the exact same problem on a System 76 Galago Ultrapro - only nVida graphics.  Upgrade from 17.10 using the standard upgrade UI.  

I'm able to Ctrl-Alt-F2 and login eventually (takes a few attempts to get username and password entered), then sudo init 3 to get the looping UI to stop.  From which I conclude this isn't a boot loop, it's the graphical frontend looping.  Someone claimed to fix it with reinstall of xserver but that didn't work for me.  

I would dearly like to get this fix without reverting to reinstall - this is the first time since something like Ubuntu 7.x that I've had an upgrade go bad (famous networking fail).  And I'm disappointed everyone is like "Just reinstall from a USB stick".  That sounds so Microsoft Windows.

---

### Post by mörgæs on 2018-05-15
Few people realise how complicated a process an upgrade is. I am surprised that it sometimes works. 

Since you all appear to have more or less the same problem I am even more convinced to suggest a clean install. It's the only good habit one gets from using Windows.

---

### Post by echemdaniel on 2018-05-20
@morgaes, I haven't done a clean install because I am worried I'd loose my files. i really would not mind a fresh install, but how do I get back my files? Any suggestions?

---

### Post by jdeca57 on 2018-05-20
Use your back-up? Personally I save in the cloud and whatever happens to my computer doesn't make me lose data.

---

### Post by echemdaniel on 2018-05-20
Sadly, I am unable to even log in, I'm greeted with a looped black boot screen. I say a pay where it reads "welcome to Ubuntu 18.04LTS"...then after over 20 minutes of displaying boot messages, the boot process stops with the error. Now I'm not sure how to salvage it.

---

### Post by mörgæs on 2018-05-20
From a live boot you can access your files and copy them to a safe location.

---

### Post by echemdaniel on 2018-05-20
> **mörgæs said:**
> From a live boot you can access your files and copy them to a safe location.

Thank you for this I'll give this attempt a try, and revert with results. I hope it works though.

---

### Post by echemdaniel on 2018-05-20
Thank you for this tip @morgaes, I will do this and revert with results. Hope it works through. Fingers crossed.

---

