---
title: "Dialup port?"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by Vekemi on 2006-09-27
When I do

```

sudo pppconfig

```

it asks me for which network modem I should use (/dev/ttyS1, etc.) but I don't know which one to put for it. Help?

---

### Post by kidders on 2006-09-27
Hi there,

A brute force way of finding out which /dev entry to choose would be to open a terminal window, type **cat /dev/ttyS0**, open a second, type **echo -e "AT\n">/dev/ttyS0**, and see what happens. If your modem doesn't say hello, try again with /dev/ttyS1 and so on.

You won't have to try very many ... If it's not one of the first three, it ain't there, I'd say.

Is your dmesg any help, by the way?

---

### Post by Vekemi on 2006-09-28
If it isn't there, how am I supposed to fix it? :|

---

### Post by Bachstelze on 2006-09-28
Given that your modem is working properly (drivers installed) wvdial will tell you :

```
sudo wvdialconf /etc/wvdial.conf
```

The correct port will appear in /etc/wvdial.conf

(I strongly sugget using wvdial to dial your ISP by the way)

---

### Post by Vekemi on 2006-09-28
It doesn't show anything, which is weird. I can access my dialup just fine via Windows.

I'm using a laptop, if that changes anything.

---

### Post by kidders on 2006-09-29
Hmmm...

Well it's tremendously unlikely your modem won't work in Linux, but if you have a thing called a "winmodem" (half a modem!), you might have trouble, if memory serves me.

Ordinarily, your dmesg should contain some reference to having detected the hardware ... start there and see what you find. With luck, it will not only tell you Linux found it, but also what it did with it in /dev terms.

Do you know what kind of modem you have?

---

