---
title: "Upgrade to 10.04.1 LTS [Urgent]"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by rawat on 2010-08-18
Hi,

I am really in deep **** when i upgraded to 10.04.1.

ran sudo apt-get upgrade sudo apt-get upgrade-dist and rebooted.

After reboot some spawned error came...init.d unable to spawn something..no such file or directory.

After that a screen came saying

[B] ubuntu is running in low graphics mode with some options... unable to detect screen device etc etc settings.

[/B]tried running after selecting first option but no luck

Please tell me how to resolve it and get back to work

Re-installing is really not a good idea for me as i have installed lot of packages.

Can it be solved without re-installing???

---

### Post by vitothegreat on 2010-08-18
I had quite a similar situation when trying to install video drivers. 
Try exiting to terminal and apt-get install nvidia-glx nvidia-settings and reboot.

---

### Post by rawat on 2010-08-18
[B]nvidia??

But i dont have anything related to nividia in my system??

Still should i do it??[/B]

---

### Post by rawat on 2010-08-18
Hi,

i tried running the command

but got unmet dependencies

nvidia-glx:Conflicts nvidia-settings but 195.36.08-0ubuntu is to be installed.

E:Broken packages

then i installed nvidia-glx and rebooted

but still i see same screen :( :( :(

---

### Post by Rubi1200 on 2010-08-18
What video/graphics card do you have installed?

Let's first get that sorted out before making suggestions.

> **Still should i do it??**
No

---

### Post by rawat on 2010-08-18
> **Rubi1200 said:**
> What video/graphics card do you have installed?

Let's first get that sorted out before making suggestions.


No


Its INTEL integrated graphics

---

### Post by gradinaruvasile on 2010-08-18
I would still suggest reinstalling. Your system is messed up, it is likely you will be left with problems.

Ubuntu in-place upgrades seldom worked for me 100% (but they did on a few occasions 90-95%). But usually some leftover configs messed something up that enevtually i reinstalled anyway (or be, as some guys i know, left with quite annoying functionality problems).
Or just install Debian testing and enjoy the upgradeless ride...

---

### Post by Rubi1200 on 2010-08-18
> **rawat said:**
> Its INTEL integrated graphics
Can you still boot into Ubuntu and get to the desktop?

If yes, then go to Applications > Accessories > Terminal and post the output of this:

```
lspci | grep VGA
```

Once we know what card you have there may still be options to fix this.

---

### Post by gradinaruvasile on 2010-08-18
If its integrated Intel, just remove xorg.conf if you have one.

---

### Post by rawat on 2010-08-18
> **Rubi1200 said:**
> Can you still boot into Ubuntu and get to the desktop?

If yes, then go to Applications > Accessories > Terminal and post the output of this:

```
lspci | grep VGA
```Once we know what card you have there may still be options to fix this.

This is the output

00:02.0 VGA Compatible Controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)

---

### Post by rawat on 2010-08-18
> **gradinaruvasile said:**
> If its integrated Intel, just remove xorg.conf if you have one.


Its not there instead i can see only xorg.conf.failsafe file

---

### Post by Rubi1200 on 2010-08-18
Thanks rawat.

You may want to take a look here for issues with Intel cards and Ubuntu 10.04:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

You need to look if your card is mentioned (or the series) and see if there is a workaround that will help.

If nothing works for you, then backup all your data and reinstall.

For a listing of your programs and how to reinstall them, look here:

[http://ubuntuforums.org/showpost.php?p=1521615&postcount=1](http://ubuntuforums.org/showpost.php?p=1521615&postcount=1)

Hope this helps.

---

### Post by oimon on 2010-08-18
Error messages are helpful - the best thing to do is find the exact error message and google it.

As a long shot, is it this error? Check out this thread. 
[http://ubuntuforums.org/showthread.php?t=1470685&page=2](http://ubuntuforums.org/showthread.php?t=1470685&page=2)

---

### Post by rawat on 2010-08-18
Thanks oimon.  That link fixed the problem in simple steps :D. Everything came back to normal. Smooth booting with no errors. Can see my all stuff there :)

I ignored the very first error that came during booting for that you pointed me out. My mistake!!

Thanks Rubi1200. 

One more thing i need to ask. 

After following the link and doing steps as mentioned there, i rebooted the machine. Nothing came on monitor. Then i changed the monitor and display came. That's how i came to know that low graphics problem gone.

But my previous monitor is not showing anything? Could it be monitor problem? But till yesterday it was working fine!!! 

But anyways guys main issue got resolved. Thanks to all of you

Cheers
Rawat

---

