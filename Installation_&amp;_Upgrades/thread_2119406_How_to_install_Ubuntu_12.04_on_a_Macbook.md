---
title: "How to install Ubuntu 12.04 on a Macbook"
date: 2013-02-23
forum: Installation &amp; Upgrades
---

### Post by geovino on 2013-02-23
Is there a iso version of Ubuntu 12.04 or 12.10 that will install on a Mac?

---

### Post by Sef on 2013-02-24
Is this an Intel based Mac?

---

### Post by geovino on 2013-02-24
> **Sef said:**
> Is this an Intel based Mac?

Yes.

---

### Post by buzzingrobot on 2013-02-24
Yes.  Look for a filename with "+mac+ in it. There's one [here]("http://cdimage.ubuntu.com/releases/12.04/release/").

Bear in mind that it won't do an EFI install, using BIOS compatibility mode instead. If you have a MacBook with two video cards, one an onboard Intel and the other a discrete Nvidia or AMD card, your install will only see one of them.  You need to install in EFI mode to see both cards.

I spent most of this weekend trying to setup 12.04.02 on a MacBook Pro 8,2.  I installed in EFI mode and BIOS compatibility mode, with no problems.  In EFI mode, the system saw both video cards, but I was unable to switch from the AMD to the Intel. In either mode the machine ran too hot and the fans were always maxed out.  In the end, I went back to OS X.

Hardware varies across the MacBook range, so your experience might easily be different.

(Fedora 18 does install in EFI mode on its own.)

---

### Post by geovino on 2013-02-24
So if this is a 3 yr old mac book which has an Intel chip I can use the regular Ubuntu live CD whether 12.10 or 12.04? 

Maybe I was thinking of when there was PPC chips that had their own Ubuntu version a few years ago. You don't see those too much anymore.

---

### Post by buzzingrobot on 2013-02-24
> **geovino said:**
> So if this is a 3 yr old mac book which has an Intel chip I can use the regular Ubuntu live CD whether 12.10 or 12.04? 



Yep.

---

