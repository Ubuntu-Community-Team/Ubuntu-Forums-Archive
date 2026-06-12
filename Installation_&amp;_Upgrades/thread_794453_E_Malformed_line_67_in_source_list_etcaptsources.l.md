---
title: "E: Malformed line 67 in source list /etc/apt/sources.list (dist parse)"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by randywilharm on 2008-05-14
I just upgraded from 7.10 to hardy.

I can't upgrade because of this error

Please tell me what line 67 is or any advice

I can do a little code. Thanks.

---

### Post by Mr A Mouse on 2008-05-14
Randy, I'm not sure what line it's referring to, as there are only 57 lines in the file as depicted in the screenshot. If that's the entirety of the file, then try commenting out that last line.

---

### Post by Pumalite on 2008-05-14
You have to get rid of all third parties in your sources.list. Then try again.

---

### Post by randywilharm on 2008-05-14
I'll try both in that order.

Thanks guys

---

### Post by nowshining on 2008-05-14
u could of just copied the contents and pasted it in the forums code tags.

example:


```
Example
```

---

### Post by fmartinez on 2008-05-14
you can also just comment out line 67 by using the pound sign (#). 
then run sudo apt-get update
to check for errors

---

### Post by randywilharm on 2008-05-14
you are right!
i thought i could put in my own sources
without reading the lessons
Now it works cause i got rid of them
thanks a lot!

---

### Post by randywilharm on 2008-05-14
Yeah--thanks i'll do that
it's good to know otherwise i'd keep
posting images.

I SOLVED THE PROBLEM i had by removing
third-party sources!!---Thanks again....

---

### Post by randywilharm on 2008-05-14
I put in the third- party sources too soon I think.

I took them out and now I can update....

THanks a  lot.....now i'll divorce Windows for good..!

---

