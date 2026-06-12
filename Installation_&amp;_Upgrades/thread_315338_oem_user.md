---
title: "oem user"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by jeoharris on 2006-12-09
Hi everybody,

I am very new to Ubuntu and I have a question: after installation I got the message to use "sudo-oem-config-prepare". Can someone detail this for me? Should I create another user? The oem will be erased?

Thanks,

Jeo

---

### Post by riven0 on 2006-12-09
Alright, that's pretty strange. Never came across that before. Did Ubuntu install fine? Do you boot up without problems?

---

### Post by jeoharris on 2006-12-09
Yes, everything is just fine. I didn't run yet that command, but what will be the difference between "oem" and another user that I created. Is "oem" with root privileges like in fedora? I played with fedora a little bit but I like much more Ubuntu.

Thanks,

Jeo

---

### Post by towsonu2003 on 2006-12-09
I think this answers your question: [http://ubuntu.wordpress.com/2005/10/11/ubuntu-oem-mode/](http://ubuntu.wordpress.com/2005/10/11/ubuntu-oem-mode/)

---

### Post by taurus on 2006-12-09
You used the alternate CD so you first need to log in as oem and the password that you've created during the installing process.  Then at the prompt, run this command to create the actual user on your machine and remove oem...

```
sudo oem-config-prepare
```

---

