---
title: "Belkin 7050 Jaunty"
date: 2009-03-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by JacobRogers on 2009-03-16
Hello,
I had the darndest time getting my wireless to work on Interepid and updating that box to the new kernel didn't much help either.

So I decided to go with the new Alpha 6 of jaunty.

I have a Belkin 7050 usb wireless card.  It says that it works and I can even connect to a network but then the internet doesn't work.  How can I trouble shoot this?

Thanks for any help.

edit: by the way I know the internet on this wireless network works because that's what I'm using on another computer right now.

---

### Post by inobe on 2009-03-16
is this wireless secured ?


what are you getting in network manager under wireless, are you connected to the correct router and not an unsecured router without net access ?

---

### Post by JacobRogers on 2009-03-16
> **inobe said:**
> is this wireless secured ?


what are you getting in network manager under wireless, are you connected to the correct router and not an unsecured router without net access ?


It's an unsecured wireless network.  I'm getting about 50% signal strength under network manager.  I'm connected to the right router and it does have net access.

---

### Post by Crafty Kisses on 2009-03-17
It could be a DNS issue, can you connect to Google by opening Firefox or whatever browser you use, and putting the following in the navigation bar?
```
74.125.45.100
```

---

### Post by JacobRogers on 2009-03-17
I got it working using ndiswrapper but I had to use a driver I got off of belkin's website instead of the one that came with the CD.

I feel so much better now, I've literally spent the past two days making this more complicated than it needed to be.

---

