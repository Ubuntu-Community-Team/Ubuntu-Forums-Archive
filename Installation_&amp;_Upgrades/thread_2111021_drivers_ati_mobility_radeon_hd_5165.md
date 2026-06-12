---
title: "drivers ati mobility radeon hd 5165"
date: 2013-01-31
forum: Installation &amp; Upgrades
---

### Post by thunder_god on 2013-01-31
Hello
 
I have a toshiba satellite l505-13e and ubuntu 12.04.1 lts 64 bit

Ubuntu can not recognise my graphic ( ATI mobility radeon hd 5165).

Search in some blogs how to install manualy the drivers but there was always a step were i got stucked because of an error or something.

Is there anyone who can give me the commands to install my graphic. 

Thanks for the help in advance.

Regards

---

### Post by darkod on 2013-01-31
How exactly it can't recognize the card?

By default, ATI cards should work with a driver/module called radeon. But that has limited options.

The better driver to use is fglrx. If you open Additional Drivers does it offer to activate fglrx?

---

### Post by thunder_god on 2013-01-31
when i try to activate the driver there come an error. It says that cannot do it

---

### Post by thunder_god on 2013-02-01
anyone can help me?

---

### Post by darkod on 2013-02-01
I don't know if that card is supported by the fglrx driver. Does it work with the default radeon driver, or it doesn't work at all?

---

### Post by Mark Phelps on 2013-02-01
> **thunder_god said:**
> when i try to activate the driver there come an error. It says that cannot do it

OK ... first of all, if Ubuntu did NOT recognize your graphics chipset you would have a black, blank screen -- which is clearly NOT the case as you would have said that.  Ubuntu installed the default Radeon driver for you -- which is why you see a desktop.

Second, WHAT does is say (specifically) when you try to activate? We need to know the error message to provide specifics.

Third, there are often two additional driver options, the first of these typically works, the second (often called post-update) usually does NOT work.  Which of these are you trying to use?

---

### Post by thunder_god on 2013-02-03
It seems like is instaled now. Tryed again without any error.

Just one last question.

I just have one grafic drivers option where you said that should be 3. As is it is working now, it shall not be a problem, correct?

Thanks for the help and sorry is i wasted some of you time

---

### Post by Mark Phelps on 2013-02-03
> **thunder_god said:**
> ...I just have one grafic drivers option where you said that should be 3. As is it is working now, it shall not be a problem, correct?

Actually, there are typically two Additional Driver options, not three, and the second of these nearly always fails.

IF your video is working OK, then you don't have a problem.

And, you didn't waste our time -- we're here to help.

---

