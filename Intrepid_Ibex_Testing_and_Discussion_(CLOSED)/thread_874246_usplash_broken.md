---
title: "usplash broken"
date: 2008-07-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jnw222 on 2008-07-29
even on hd i have had usplash problems 

it used to have a very glitchy screen
but now it does not work at all just a red and white srceen 

everyting else seems to work

(alpha 3)

---

### Post by jfernyhough on 2008-07-29
I seem to think there are unresolved issues with the new usplash backend. Just wait, it'll sort itself out. But if you want to know what's going on with your system during boot just disable splash in the GRUB options (/boot/grub/menu.lst; splash -> nosplash, or on boot, e to edit options).

---

### Post by autocrosser on 2008-07-29
That has been going on for quite a while --I posted a bug about it in May--see: [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662)

If you look thru Launchpad for Usplash bugs--you will find several, all along this general theme. The Devs are working on it--I am sure a fix will be found soon.

---

### Post by coffeecat on 2008-07-31
> **jnw222 said:**
> just a red and white srceen 

Well, on this thread of yours:

[http://ubuntuforums.org/showthread.php?t=862327](http://ubuntuforums.org/showthread.php?t=862327)

... a couple of people posted a fix for your original scrolling text problem, but **after** you gave up posting. Did you see their posts?

So what have you done in the interim to get a 'red and white screen'? :-s Can you explain what you mean?

---

### Post by Gina on 2008-08-01
I get red and white vertical stripes on my P4 with ATI graphics on startup and shutdown.  Some of the time continuous stripes from top to bottom and some broken up into long thin blocks.  Graphics is alright otherwise.

---

### Post by plun on 2008-08-02
After some trouble installing latest kernel 2.6.26-5 usplash works again for me.

But I have 3 indicators running on screen during start...:)

(nvidia-177 as graphic driver)

---

### Post by KIAaze on 2008-08-02
I'm having the same bug with the multiple loading bars and sometimes I get the red&white screen too.

But does anybody having this bug also experience this one?:
[https://bugs.launchpad.net/ubuntu/+bug/253243](https://bugs.launchpad.net/ubuntu/+bug/253243)

---

