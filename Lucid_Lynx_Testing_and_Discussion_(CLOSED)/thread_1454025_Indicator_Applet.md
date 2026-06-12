---
title: "Indicator Applet"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Olmy on 2010-04-14
OK, so the volume control and battery status are now in the indicator applet but can I get rid of the envelope icon that has no options other than to invite me to set up a load of stuff I've either already set up or have no intention of setting up?

---

### Post by dino99 on 2010-04-14
use gconf editor

---

### Post by Olmy on 2010-04-14
> **dino99 said:**
> use gconf editor

Thanks, I was hoping there was an option there but I must have missed it. Where exactly is it?

---

### Post by Olmy on 2010-04-14
I've been playing with this some more and it's getting even more frustrating....

I thought I'd try clicking on mail setup and it sent me straight to evolution (that I don't use) and added even more pointless stuff to the indicator menu that I can't get rid of.

I tried out empathy (that I use very rarely) and its nice, informative notification icon had gone. I eventually found an option 'show incoming messages in the messaging menu' - unchecking this restored the icon. I'm guessing that otherwise it's linked into this indicator thingy that shows nothing to even indicate that empathy is running.

Can someone please explain what is going on? Unless I'm missing something (which is quite possible and a really hope I am) this is a giant leap backwards......

---

### Post by august on 2010-04-14
Chiming in. Just installed 10.04 beta, and found this thread when I was googling for how I could remove those built-in evolution and empathy plugs and still keep the volume and bluetooth icon.

Is there a way to do this in 10.04?

---

### Post by Ancanus on 2010-04-14
```
 sudo aptitude remove indicator-messages 
```

---

### Post by august on 2010-04-14
> **Ancanus said:**
> ```
 sudo aptitude remove indicator-messages 
```

Great! The e-mail icon is now gone :) Would be superb if this was configurable by the time 10.04 gets released, this was quite confusing. But it's a little late for that now, I guess.

---

### Post by Olmy on 2010-04-15
> **Ancanus said:**
> ```
 sudo aptitude remove indicator-messages 
```
Thanks!

I too hope a proper configuration is sorted out for the release. This (as it stands) is terribly user-unfriendly....

---

### Post by emarkay on 2010-04-15
> **Olmy said:**
> Thanks!

I too hope a proper configuration is sorted out for the release. This (as it stands) is terribly user-unfriendly....

File a bug report

I know there are already a few on this issue, but if you have a specific need, and the function has been changed without a public consensus, and/or a function has been removed without a reason, this may very well be a new legit bug.

---

### Post by maphilli14 on 2010-04-16
I too would like to know the options available.  The launchpad link in about gives you great insight into the design methodology, but I don't think that those options made it into the manual?  Perhaps a better tutorial is a good stop gap for this release? 

Mike

---

### Post by drewsus on 2010-04-17
> **Ancanus said:**
> ```
 sudo aptitude remove indicator-messages 
```

This is what I wanted, thanks!!

---

### Post by sandgren on 2010-04-27
> **Ancanus said:**
> ```
 sudo aptitude remove indicator-messages 
```
Super, that's just what I wanted :)

---

