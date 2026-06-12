---
title: "making  &quot;synclient&quot; settings persistent"
date: 2012-10-07
forum: Installation &amp; Upgrades
---

### Post by ulugeyik on 2012-10-07
I use:
synclient TapButton1=1 TapButton2=3 TapButton3=2

in order to allow me to use three finger press as a middle-button click on my ASUS UX31A ultrabook. I got this tip from various posts.

I tried to make this persistent and automatic by including it in the "Startup applications" but it is not working. Furthermore, if I run it from a terminal, it stops working if I close the terminal window.

I do not understand why  I have this problem and how I can make it automatic?

Thanks,

Turgut

---

### Post by mikewhatever on 2012-10-07
What exactly did you use as command in the startups?

---

### Post by ulugeyik on 2012-10-07
> **mikewhatever said:**
> What exactly did you use as command in the startups?

Just this:
synclient TapButton1=1 TapButton2=3 TapButton3=2

Do I need to give full path?

---

### Post by mikewhatever on 2012-10-07
No, that should work ok. Can you try something like this
```
bash -c 'sleep 10; synclient TapButton1=1 TapButton2=3 TapButton3=2'
```

That should insert a delay of 10 seconds before the command.

---

### Post by ulugeyik on 2012-10-08
Thanks. That works.  I guess something was clashing somewhere but I can't tell what.

---

