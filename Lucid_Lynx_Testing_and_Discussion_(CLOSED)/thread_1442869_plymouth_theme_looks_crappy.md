---
title: "plymouth theme looks crappy"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ffi on 2010-03-30
On my desktop the plymouth theme looks really crappy (lo res, few colours) on my laptop it looks much better (correct res en colourful)

How do I fix this?

---

### Post by Funnnny on 2010-03-30
Oh please provide at least some information, any information

---

### Post by ffi on 2010-03-30
What more do you need, I can take a pic

---

### Post by kklimonda on 2010-03-30
You are probably using a closed video driver on your desktop. If not please write what gpu do you use, what xorg driver is loaded etc.

---

### Post by keybuk on 2010-03-30
For a detailed explanation, see: [http://www.netsplit.com/2010/03/30/all-about-kernel-mode-setting/](http://www.netsplit.com/2010/03/30/all-about-kernel-mode-setting/)

---

### Post by ffi on 2010-03-30
> **keybuk said:**
> For a detailed explanation, see: [http://www.netsplit.com/2010/03/30/all-about-kernel-mode-setting/](http://www.netsplit.com/2010/03/30/all-about-kernel-mode-setting/)
Thanks for the explanation, I do have an nvidia card and use the proprietary driver
btw I think on mandriva it does work

---

### Post by cyberkilla on 2010-03-30
> **ffi said:**
> Thanks for the explanation, I do have an nvidia card and use the proprietary driver
btw I think on mandriva it does work

I think a blank screen with "Loading Ubuntu..." in the corner would look a lot less awful.. Perhaps they should fall back to that.

---

### Post by ffi on 2010-03-30
Dunno, maybe just enabling KMS for KMS aware drivers is a better solution

---

### Post by cyberkilla on 2010-03-30
> **ffi said:**
> Dunno, maybe just enabling KMS for KMS aware drivers is a better solution

That doesn't really mean anything. The proprietary drivers give Plymouth something like 16 colour VGA at boot time. The non-proprietary drivers are more forthcoming, so the boot screen looks nicer.

They have already stated that you can set it to use VESA, but you might have trouble with suspending/hibernating, etc.

---

### Post by cheapsaket on 2010-03-30
I have the same issue with my ati card. I can't use the open source drivers as my system crashes randomly with them so had to go with fglrx.

I would like to know how to set the plymouth resolution to VESA.

As for suspend/hibernate: suspend does not work for me and hibernate is very  slow hibernating and EXTREMELY slow coming back from hibernation.

---

