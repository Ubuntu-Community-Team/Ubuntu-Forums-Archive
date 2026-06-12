---
title: "Choppy flash video using full screen. Any xorg fix. Am using nvidia"
date: 2009-05-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-05-12
This comes and goes with each version. It gets fixed then breaks. etc etc.

---

### Post by davideotape on 2009-05-12
I think I saw a bugreport somewhere in the karmic targeted bugs that sounds similar to this. I'd post a link, but I'm on my iPod and apple haven't got round to copy and paste functionality yet :roll:. Sorry :(

---

### Post by Nullack on 2009-05-12
If your on the 64bit version dont use ia-32libs and the 32 but flash - use the native 64bit flash.

Also, dont use compiz, there is no acceleration with compiz on.

And ofcourse, you need the NVIDIA closed source driver.

---

### Post by lithorus on 2009-05-13
> **Nullack said:**
> If your on the 64bit version dont use ia-32libs and the 32 but flash - use the native 64bit flash.

Also, dont use compiz, there is no acceleration with compiz on.

And ofcourse, you need the NVIDIA closed source driver.
AFAIK, the 64bit version of flash have no openGL acceleration at all.

---

### Post by philinux on 2009-05-13
Ok I've found the problem is You Tube bandwidth related and some other sites too.

And the quality of the original vid. 

Now got compiz off. Already had the 64 bit .so file in my /.mozilla/plugins folder.

---

### Post by SKLP on 2009-05-13
> **lithorus said:**
> AFAIK, the 64bit version of flash have no openGL acceleration at all.Exactly, so one has to use the 32 bit version AFAIK

---

### Post by Nullack on 2009-05-13
> **lithorus said:**
> AFAIK, the 64bit version of flash have no openGL acceleration at all.

incorrect, it does support it, take a look at adobe labs

---

### Post by lithorus on 2009-05-14
> **Nullack said:**
> incorrect, it does support it, take a look at adobe labs
Seems things have changed then. Remember you saying the same thing earlier :)
[http://ubuntuforums.org/showpost.php?p=6896569&postcount=4](http://ubuntuforums.org/showpost.php?p=6896569&postcount=4)

Anyway to the original poster :
You can try and play with
OverrideGPUValidation=true
in /etc/adobe/mms.cfg

---

### Post by Nullack on 2009-05-14
Yes mate it changed, its good to see change in this case :)

---

