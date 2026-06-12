---
title: "Anybody manage to get this working on an eee pc?"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by josephellengar on 2010-04-23
I tried Lucid out on my netbook (eee 1005ha-p) after the beta 2 was released but found that it was impossible to get the wifi to work, and that nobody had yet come up with a solution to this problem.  Does anybody here know if it would be safe for me to try to install again yet?

---

### Post by Captain Smiley Pants on 2010-04-23
Here's my thread for my [1005HA Eee netbook](http://ubuntuforums.org/showthread.php?t=1459633). I've had moderate success, wifi works, dual monitors work, but I'm not exactly sure what the difference in our machines are.

---

### Post by julianb on 2010-04-23
Ubuntu lucid is working almost flawlessly on the 3 eeepc machines I have, but I can't vouch for your particular hardware. I'm not sure of the exact models I have, except that they are all different (7 inch screen, 9 inch screen, & 10 inch)

---

### Post by josephellengar on 2010-04-23
> **julianb said:**
> Ubuntu lucid is working almost flawlessly on the 3 eeepc machines I have, but I can't vouch for your particular hardware. I'm not sure of the exact models I have, except that they are all different (7 inch screen, 9 inch screen, & 10 inch)

Did you do a clean install or upgrade from karmic on the ten inch one?  And thanks for that thread to the poster above.

---

### Post by PhilGil on 2010-04-23
I don't know if you have the same chipset as I do (Ralink rt2860), but wireless is non-functional on my 1000h after a Lucid install.  Works fine in Karmic.  This is a known issue, here is the launchpad bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093) .

It doesn't look like it's going to be fixed by release day, although a Ubuntu dev said it will be included in an update.  If you can't wait, another developer was kind enough to compile a custom kernel and host the debs (see post #53).  My wireless works fine using the custom kernel.

---

### Post by josephellengar on 2010-04-23
> **PhilGil said:**
> I don't know if you have the same chipset as I do (Ralink rt2860), but wireless is non-functional on my 1000h after a Lucid install.  Works fine in Karmic.  This is a known issue, here is the launchpad bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093) .

It doesn't look like it's going to be fixed by release day, although a Ubuntu dev said it will be included in an update.  If you can't wait, another developer was kind enough to compile a custom kernel and host the debs (see post #53).

How do I check what chipset I have?

---

### Post by PhilGil on 2010-04-23
> **rossholley said:**
> How do I check what chipset I have?

Open a terminal and enter

```
lspci
```Look for "Network Controller" in the output.

---

### Post by josephellengar on 2010-04-23
> **PhilGil said:**
> Open a terminal and enter

```
lspci
```Look for "Network Controller" in the output.

Thanks.
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection

So I guess I shouldn't have the same problems as you?

---

### Post by PhilGil on 2010-04-23
> **rossholley said:**
> Thanks.
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection

So I guess I shouldn't have the same problems as you?

Doesn't sound like it.  Sorry I couldn't be more helpful.

---

