---
title: "32 bit ubuntu on 64 bit computer"
date: 2011-09-29
forum: Installation &amp; Upgrades
---

### Post by ciscoboy on 2011-09-29
I've got a hypothetical question that i'd like to have an answer to; what would happen if you install a 32bit ubuntu on a computer that has a 64bit  processor?

Thanks!

Ciscoboy

---

### Post by haqking on 2011-09-29
> **ciscoboy said:**
> I've got a hypothetical question that i'd like to have an answer to; what would happen if you install a 32bit ubuntu on a computer that has a 64bit  processor?

Thanks!

Ciscoboy

It will run as 32 bit.

simple answer to a simple question ;-)

---

### Post by ciscoboy on 2011-09-29
But is there any difference at all in speed, compatibility? And in between the 32bit and 64 bit ubuntu, which is more stable?

---

### Post by dino99 on 2011-09-29
you ask it, you get it :)

[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

---

### Post by ciscoboy on 2011-09-29
Thanks! The link is really helpful.

---

### Post by oldos2er on 2011-09-29
I disagree with the opinion expressed in that link. If you have 64-bit hardware there's not much reason to stick with 32-bit software.

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by haqking on 2011-09-29
> **oldos2er said:**
> I disagree with the opinion expressed in that link. If you have 64-bit hardware there's not much reason to stick with 32-bit software.

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

+1

If you have x64 then by all means install and use x64, no reason not to these days.

But if you install 32 bit will stay as 32 bit, PAE kernel will allow more ram to be seen that standard but i would go for x64 given the option.

---

### Post by ciscoboy on 2011-09-30
Okay, and what happens if you mix them up (32 bit OS on 64 processor or vice-versa)?

---

### Post by haqking on 2011-09-30
> **ciscoboy said:**
> Okay, and what happens if you mix them up (32 bit OS on 64 processor or vice-versa)?

That was answered in my first response to the OP.

32 bit OS on x64 will run as 32

x64 wont run on a 32 bit

you can run a PAE enabled 32 bit to gain access to extra memory in your system, if you wish.

Personally if you have x64 then run x64 software

---

