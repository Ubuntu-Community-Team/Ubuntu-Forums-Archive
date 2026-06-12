---
title: "Solved Grey Box Flash 10 Issue in 8.10 Alpha6"
date: 2008-09-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by surfed on 2008-09-27
After days of banging my head against anything i could find i managed to get flash to work with this simple step (after applying every other solution i found on this forum):

create /etc/adobe/mms.cfg containing this line:

WindowlessDisable = 1


thats it.

Just wanted to add that this was in 64 bit ibex

---

### Post by Sef on 2008-09-28
moved to ibex forum.

---

### Post by ThrobbingBrain66 on 2008-09-28
> **surfed said:**
> After days of banging my head against anything i could find i managed to get flash to work with this simple step (after applying every other solution i found on this forum):

create /etc/adobe/mms.cfg containing this line:

WindowlessDisable = 1


thats it.
I'm glad that fix works for you.  It's disconcerting however, that you had to do that at all.  That bug was supposedly fixed in Firefox 3.0.2

[http://blogs.adobe.com/penguin.swf/2008/09/firefox_302_get_it.html](http://blogs.adobe.com/penguin.swf/2008/09/firefox_302_get_it.html)

---

### Post by psyke83 on 2008-09-28
> **ThrobbingBrain66 said:**
> I'm glad that fix works for you.  It's disconcerting however, that you had to do that at all.  That bug was supposedly fixed in Firefox 3.0.2

[http://blogs.adobe.com/penguin.swf/2008/09/firefox_302_get_it.html](http://blogs.adobe.com/penguin.swf/2008/09/firefox_302_get_it.html)

There are numerous issues with nspluginwrapper and ia32-libs. The whole point of a development cycle is to iron out such issues. If you're looking for production quality now, go with Hardy.

---

### Post by ThrobbingBrain66 on 2008-09-28
> **psyke83 said:**
> There are numerous issues with nspluginwrapper and ia32-libs. The whole point of a development cycle is to iron out such issues. If you're looking for production quality now, go with Hardy.

When I posted, he had not yet edited his post to say that he was using 64-bit.  I was just going off the information that I had at the time.

---

### Post by surfed on 2008-09-28
Are we all in a good mood today....

---

### Post by Udibuntu on 2008-10-27
Hardy gives me grey boxes aplenty.

Flash 9, Flash 10, the OP's method, nothing works.

Open a second tab that has flash, and every flash box turns grey, sometimes flash goes grey with a single tab...

](*,)

---

