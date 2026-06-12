---
title: "dependency problem"
date: 2011-09-22
forum: Installation &amp; Upgrades
---

### Post by ak123 on 2011-09-22
hey everyone.. been a while since i posted here but i am in need of some help.. 

I have to install a program called logger svt pro or something like that.. its at [http://www.vernier.com/downloads/logger-pro-linux/](http://www.vernier.com/downloads/logger-pro-linux/)

its an urgent thing for school. Problem is, it wont install thanks to a missing dependency on something called libhall. Anyone know how to fix it?

---

### Post by Hakunka-Matata on 2011-09-22
>  **by ak123: **its an urgent thing for school. Problem is, it wont install thanks to a  missing dependency on something called libhall. Anyone know how to fix  it?

a missing dependency means the program needs that library in order to function, so install libhall (you may have trouble installing it, as libhall may conflict with other libraries already installed, try it, and find out).

Your thread 'subject line': Major problem!, Urgent!, in not very descriptive.  !!! equates to shouting, turns some people off.

---

### Post by ak123 on 2011-09-22
Well thats the issue here.. i cant seem to find the package.. its not in the default repositories and i cant seem to find a ppa for it..

---

### Post by Shazaam on 2011-09-22
Are you spelling it correctly?
I found this...
```
http://packages.ubuntu.com/lucid/libhal-dev
```

Notice only one L in libhal?

---

### Post by mörgæs on 2011-09-23
> **Hakunka-Matata said:**
> 
Your thread 'subject line': Major problem!, Urgent!, in not very descriptive.  !!! equates to shouting, turns some people off.

Fixed.

---

### Post by ak123 on 2011-09-24
thanks @mörgæs 

@shazaam you were right.. the package was actually spelt libhal1 (Last character was the number one) so it looked like two l's

---

### Post by mörgæs on 2011-09-25
If this solved the problem, please mark the thread so using 'thread tools'.

---

