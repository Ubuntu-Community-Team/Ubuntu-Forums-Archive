---
title: "Boots to black screen after update to 2.6.28-7"
date: 2009-02-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nixie Pixel on 2009-02-10
Hi, I have been running Jaunty, on the 2.6.28-6 kernel, with a few problems, but nothing major.  (Firefox, npviewer.bin crashes)

I updated yesterday to 2.6.28-7, and now whenever I boot to that kernel, after the Ubuntu splash screen I get a black screen.  I can't do anything other than push the power button...though if I enter my username and password blindly I believe it actually logs me in since the hard drive spins in a manner indicating login and startup.

If I boot back to 2.6.28-6 I am able to log in, but all my desktop applets crash for some reason.

Any ideas about what this is, and how I should fix it?  Or should I just wait for the next kernel update?

Thanks!

---

### Post by PRGUY85 on 2009-02-10
I get same black screen on 2.6.28-7.  Everything works perfectly on 2.6.28-6.

I can hear the computer logging in but only a black screen is shown.

---

### Post by dr_kabuto on 2009-02-10
Hi,
seems to be a problem with usplash, various bug reports have been reported to launchpad. Seems that users with an Intel graphic chipset are affected. If you edit menu.lst remove the 'quiet splash' options, and you should get a login screen again.

---

### Post by tawmas on 2009-02-10
Do you have intel graphics? If so, search is your best friend and [this thread]("http://ubuntuforums.org/showthread.php?t=1065044") is for you too! :-)

---

### Post by Nixie Pixel on 2009-02-10
> **tawmas said:**
> Do you have intel graphics? If so, search is your best friend and [this thread]("http://ubuntuforums.org/showthread.php?t=1065044") is for you too! :-)

Thank you - I did search, I did find that thread, and assumed it did not apply to me as I do not have the Intel 915 chipset nor do I see the graphical problems that users are reporting in that thread.  I do have a different chipset and I don't have any graphics at all - I do see the splash screen just fine, which they do not.

I will try the menu.lst workaround as noted above.

---

### Post by tawmas on 2009-02-10
> **Nixie Pixel said:**
> Thank you - I did search, I did find that thread, and assumed it did not apply to me as I do not have the Intel 915 chipset nor do I see the graphical problems that users are reporting in that thread.  I do have a different chipset and I don't have any graphics at all - I do see the splash screen just fine, which they do not.

I will try the menu.lst workaround as noted above.

Understood. Actually, after the kernel update to -20 I no longer see the usplash artifacts, but I still have the black screen and locked system. What kinf of chipset do you have? Others reported the same problem with i945...

---

### Post by Nixie Pixel on 2009-02-10
Ok, removing "splash" allowed me to boot.  Thank you!

My graphics card:  Intel Mobile GM965/GL960

(How do I mark the question as resolved?  Sorry for the noob question...)

---

### Post by dr_kabuto on 2009-02-10
Hi,
Just edit the thread name and put a '[Solved]' in front of it.

---

### Post by Nixie Pixel on 2009-02-10
Ok, done, thanks.

One last question - is there a way I can help with solving the bug?  I'm new to the whole launchpad thing, and don't know how to begin helping.

---

### Post by dr_kabuto on 2009-02-10
Hi,
if you want to partecipate in bug reporting, first you should make an account in launchpad. After that you could report new bugs and/or make comments in report made by others. For your bug there's alread a confirmed bug report, [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/327230](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/327230) and an ubuntu developer already at work on it.

---

