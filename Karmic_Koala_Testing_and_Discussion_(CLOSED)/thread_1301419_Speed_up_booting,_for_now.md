---
title: "Speed up booting, for now"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Delvien on 2009-10-26
I have noticed that on my laptop, when loading the new xsplash, it would take a long time just to load the pointless splash screen, that really didnt do anything for me, and showed a progress bar even though the only thing it was loading was.... itself.

By removing xsplash, I sped up my boot time by 20 seconds. I also turned off splash in the kernel options, and that helped too.

```
 sudo apt-get remove xsplash
```

---

### Post by graaant on 2009-10-26
This didn't speed up anything for me. All it did was display a blank screen after usplash.. for the same amount of time.

---

### Post by the.lost.one on 2009-10-26
Karmic has to be the first OS in computing history to have a 3 times slower boot time than its previous version as a FEATURE

---

### Post by MacUntu on 2009-10-26
> **the.lost.one said:**
> Karmic has to be the first OS in computing history to have a 3 times slower boot time than its previous version as a FEATURE

Are you sure you're reading your bootcharts right?

---

### Post by wilee-nilee on 2009-10-26
On my computer this also removes the ubuntu desktop, I had to install xubuntu to get back into the system. I will say though that the xubuntu desktop is very nice looking and the slash is cool, but this is at least for me not good. I think it is a anomaly, but I am fully updated.

---

### Post by the.lost.one on 2009-10-26
bootcharts? i have noticed the timings reading a clock on the sysinfo screenlet. A reboot now takes almost twice as much as it did on Jaunty. Since shutdown time is almost half of what it was on Jaunty, the boot up time roughly has to be more than twice.

On Jaunty, there was splash screen-->login-->desktop (immediately)
On Karmic it is: Black Ubuntu logo-->splash-->login-->splash-->desktop (after a few seconds, sometimes)

---

### Post by thecityofgold2006 on 2009-10-26
Have just installed Karmic and have to say I am not impressed by the boot. It looks amaturish compared to Jaunty.

What is the point of the two completely different splash screens? If they had to have two, why not make them identical?

---

### Post by knarf on 2009-10-26
ubuntu-desktop is a metapackage which exists to pull in all required packages for a functional gnome desktop but does not provide any functionality itself. Removing it does not remove any functionality but it does mean that any new 'standard' packages for the desktop are not pulled in during upgrade. It is therefore not likely that the mere removal of ubuntu-desktop caused your system to malfunction.

To see what files are provided by a package you can use the -L option to dpkg:

```
$ dpkg -L ubuntu-desktop
```

As I do not have ubuntu-desktop installed - it gets removed when I remove evolution and tomboy and such - I can not show you the output...

---

### Post by emarkay on 2009-10-26
In time from BIOS to desktop Karmic is much slower - some of it is the delay in getting GRUB2 to load, as well as the unnecessary "gee whiz" "Thobber " thing.  

The GRUB issue is being addressed, but those wanting a clean, fast, text-based boot as in all previous versions will just have to wait for the pretty picture to play...  I gave up on addressing this bad logic a bunch of weeks ago here.

---

### Post by wilee-nilee on 2009-10-26
> **knarf said:**
> ubuntu-desktop is a metapackage which exists to pull in all required packages for a functional gnome desktop but does not provide any functionality itself. Removing it does not remove any functionality but it does mean that any new 'standard' packages for the desktop are not pulled in during upgrade. It is therefore not likely that the mere removal of ubuntu-desktop caused your system to malfunction.

To see what files are provided by a package you can use the -L option to dpkg:

```
$ dpkg -L ubuntu-desktop
```As I do not have ubuntu-desktop installed - it gets removed when I remove evolution and tomboy and such - I can not show you the output...

 Thanks, I the recognize meta nature of the Ubuntu Desktop it did not remove any thing but the package with the name ubuntu-desktop in synaptic, which was hard to tell but I got a loop to log in and re-login; when I had set auto login on.

---

### Post by kansasnoob on 2009-10-26
> **the.lost.one said:**
> Karmic has to be the first OS in computing history to have a 3 times slower boot time than its previous version as a FEATURE

This has not been the case for me at all.

I was experiencing extremely slow boot times clear back in Alpha 5 I believe, and I began to play with the notion of reverting from grub 2 to legacy grub.

Now, I can't at this point actually recommend that anyone else do this, **[COLOR="Red"]if you break it, you own it[/COLOR]**, but I reverted to legacy grub following these steps:

[http://ubuntuforums.org/showpost.php?p=8071880&postcount=18](http://ubuntuforums.org/showpost.php?p=8071880&postcount=18)

One of the reasons I used the "mv" command to store the original /boot/grub was so I could easily revert what I just "reverted" but I also played with using "mkdir" to start over fresh with grub 2 (aka: grub-pc) and I was amazed at the improvement.

I don't have time to get into specifics, and **[COLOR="Red"]as I said previously I can't recommend just trying this willy-nilly, so only try it if breakage is NOT important to you![/COLOR]**

As it stands right now I have about a 23 second boot time with grub 2 and about a 20 second boot time with legacy grub. That's using "auto-login" and going to "Login Screen" and unticking the 10 second option for others to login.

---

