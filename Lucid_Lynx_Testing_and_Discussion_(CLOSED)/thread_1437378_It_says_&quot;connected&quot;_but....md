---
title: "It says &quot;connected&quot; but..."
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ubunterooster on 2010-03-23
With wireless it seems to set up properly until the point were I try to actually go online. "Page not found" on every site, while it says it is connected...

?

---

### Post by ubunterooster on 2010-03-23
Sorry, going back to Karmic for now.

---

### Post by doas777 on 2010-03-23
the first thing i would check is  name resolution. 
if you haven't rebuilt yet, what do you get from 
```
nslookup www.google.com
```

---

### Post by ubunterooster on 2010-03-23
I'll remember this in case it happens later

---

### Post by jaoc223 on 2010-03-23
Can you get online while tethered to the modem or router? which kernel are you using? for me the 2.6.32-20 kernel released with beta1 did not allow me to get to any websites. my solution was to use the kernel 2.6.32-14 from alpha3. have you tried to jump start it, i.e connect tethered then select your wireless AP see if it connects and then untether the moodem or router. have you tried disabling ipv6 in ff?

---

### Post by ubunterooster on 2010-03-23
Sorry I'm back on Karmic, it was my fathers PC. It worked fine hardwired. We were using the beta and yes I tried the tether trick. Sorry but  my father is not an adventurer enough for us to take the time.

---

