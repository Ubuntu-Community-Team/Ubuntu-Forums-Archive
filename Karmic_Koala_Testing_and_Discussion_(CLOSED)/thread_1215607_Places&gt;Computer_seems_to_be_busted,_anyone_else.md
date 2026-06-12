---
title: "Places&gt;Computer seems to be busted, anyone else got this."
date: 2009-07-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-07-17
Clean install of alpha3 yesterday.

App starts but then crashes. No apport.

---

### Post by wayne_cat on 2009-07-17
no problems here ... alpha 1 + latest updates

---

### Post by durand on 2009-07-17
Works here :S

---

### Post by philinux on 2009-07-17
Just looked in messages log.

```
Jul 17 16:28:42 philinux kernel: [ 2252.573172] <6>nautilus[3359]: segfault at 0 ip 00007f1a818e9c30 sp 00007fff02bd9a08 error 4 in libglib-2.0.so.0.2103.0[7f1a8188c000+c5000]
Jul 17 16:30:13 philinux kernel: [ 2343.641257] <6>nautilus[3383]: segfault at 0 ip 00007f8dfc2b8c30 sp 00007fff2a2fd8b8 error 4 in libglib-2.0.so.0.2103.0[7f8dfc25b000+c5000]
Jul 17 16:30:26 philinux kernel: [ 2356.770432] <6>nautilus[3394]: segfault at 0 ip 00007f5a11125c30 sp 00007fff9125b738 error 4 in libglib-2.0.so.0.2103.0[7f5a110c8000+c5000]
Jul 17 16:30:31 philinux kernel: [ 2361.063403] <6>nautilus[3410]: segfault at 0 ip 00007f9276531c30 sp 00007fff8be5f8b8 error 4 in libglib-2.0.so.0.2103.0[7f92764d4000+c5000]

```

Error in libglib-2.0.so

---

### Post by tekstr1der on 2009-07-17
I had a similar situation after ubuntuone installed a couple of days ago. If smb shares were mounted nautilus would start then crash immediately. Removing ubuntuone resolved this for me.

---

### Post by philinux on 2009-07-17
> **tekstr1der said:**
> I had a similar situation after ubuntuone installed a couple of days ago. If smb shares were mounted nautilus would start then crash immediately. Removing ubuntuone resolved this for me.

All other Places>*** work fine just not Computer.
[edit] and place>network is busted too.

---

### Post by rudenko_ruslan on 2009-07-17
Confirmed, "Computer" & "Network" are broken for me too.

---

### Post by philinux on 2009-07-17
> **rudenko_ruslan said:**
> Confirmed, "Computer" & "Network" are broken for me too.

Bugged.
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/400747](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/400747)

---

### Post by terry_gardener on 2009-07-17
i get this also places-computer and network dont work app flashes up then disappears.

---

### Post by xebian on 2009-07-17
> **philinux said:**
> Clean install of alpha3 yesterday.

App starts but then crashes. No apport.

ALPHA 3???

```
July 2009
July 2nd - Rebuild Test
July 23th - Alpha 3

```

---

### Post by yoasif on 2009-07-17
Also seeing this, I will try to contribute to your bug report.

---

### Post by terry_gardener on 2009-07-17
mine now working, 

completely uninstalled and closed synaptic down and then reinstalled the following packages.

ubuntuone-client
ubuntuone-client-gnome

now seems to be working

---

### Post by chrismine on 2009-07-17
Same behavior - subscribed to bug but nothing I can add.

---

### Post by philinux on 2009-07-21
After todays updates this is fixed for me.

---

### Post by chrismine on 2009-07-21
Fixed here. Ubuntu One also working.

---

