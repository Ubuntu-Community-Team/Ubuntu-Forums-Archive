---
title: "MSI Wind wireless RTL8187SE not detected with kernel 2.6.28"
date: 2009-02-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jepong on 2009-02-23
I'm using Kubuntu Jaunty Alpha 4 on a MSI Wind u100x. There's no wireless support for RTL8187SE. 

I thought this is already supported? I'm sure this is also the same issue with Ubuntu.

---

### Post by yey365 on 2009-02-24
Download: rtl8187se_linux-04.tar.bz2 and execute the commands "makedrv" and "install" consecutively from the command line.

Restart the system and you will have working wifi.

You can find the file here:

[http://code.google.com/p/msi-wind-linux/downloads/detail?name=rtl8187se_linux-04.tar.bz2&can=2&q=](http://code.google.com/p/msi-wind-linux/downloads/detail?name=rtl8187se_linux-04.tar.bz2&can=2&q=)

Hope this helps,

Jim

---

### Post by jepong on 2009-02-24
Thanks yey365!

Can you spoon-fed me a little? Can you write the step by step instruction. Thanks again.

---

### Post by daxumaming on 2009-02-24
```

sudo aptitude install rtl8187se-source
sudo m-a auto-install rtl8187se

```

Got my wireless working after reboot.
I do believe I have to do this everytime I do upgrade my kernel though

---

### Post by jepong on 2009-02-24
Thanks mate!

---

### Post by yey365 on 2009-02-25
yep, after every kernel update sucks but it works on Jaunty alpha and it's a quick enough fix.

jim

---

### Post by daxumaming on 2009-03-21
Just an update

> **daxumaming said:**
> I do believe I have to do this everytime I do upgrade my kernel though

Nope, I/We don't have to do this everytime there's a kernel upgrade.

---

