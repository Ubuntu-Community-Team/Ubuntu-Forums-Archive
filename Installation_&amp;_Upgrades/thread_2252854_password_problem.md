---
title: "password problem"
date: 2014-11-15
forum: Installation &amp; Upgrades
---

### Post by telegiovi on 2014-11-15
dears, 
I did upgrade to Ubuntu 14.04. When it starts now I should put my password, but it does not recognize it (the password I always used) and I can access only as a guest. I then tried in the recovery mode but it says to me something like "manipulation error authentication token" (in italian). Now I do not know what to do in order to have full access. 
Any suggestion? Thank you!

---

### Post by steeldriver on 2014-11-15
The "authentication token manipulation error" when following password reset instructions in the recovery mode shell usually indicates you missed the step where the root filesystem is remounted in read-write mode:

```

mount -o remount,rw /

```

---

### Post by telegiovi on 2014-11-15
thank you. I will do it

---

### Post by telegiovi on 2014-11-15
And it works!
1000 thanks to you

---

### Post by steeldriver on 2014-11-15
No problem - thanks for marking the thread SOLVED

---

