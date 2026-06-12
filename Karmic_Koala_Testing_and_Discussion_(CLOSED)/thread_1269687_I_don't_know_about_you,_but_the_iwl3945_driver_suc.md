---
title: "I don't know about you, but the iwl3945 driver sucks at to connecting weak signals."
date: 2009-09-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-09-18
The iwl3945 on Ubuntu won't reliably stay connected to anything below a 40% signal.

In Windows, I have no such problem and even a 10% signal will work fine.

What gives and why is the iwl3945+Network-Manager combo so horrible?

Maybe I need to give wicd a second look.

---

### Post by MacUntu on 2009-09-18
Does this also happen if you connect directly via wpa_supplicant? Have you tried compat-wireless drivers ([http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download))?

---

### Post by Starks on 2009-09-18
1. Why would I use compat-wireless when the Karmic kernel already has its bleeding edge wireless drivers?

2. I don't know how to use wpa_supplicant and I don't think I should considering that the network is unencrypted.

---

### Post by Squonk07 on 2009-09-19
> **Starks said:**
> The iwl3945 on Ubuntu won't reliably stay connected to anything below a 40% signal.

In Windows, I have no such problem and even a 10% signal will work fine.

What gives and why is the iwl3945+Network-Manager combo so horrible?

Maybe I need to give wicd a second look.

I've had this very same problem for as long as I can remember when running Ubuntu. In addition, I have trouble detecting weak signals at all that are usually detected immediately in Windows.

Also, somewhat related: is there a way to manually force Network-Manager to poll for available signals? In my dorm sometimes I have to wait a full ten minutes or more for either of the two available networks to show up. I usually find these in Windows by repeatedly searching for them.

---

### Post by tjeremiah on 2009-09-19
i too notice this problem but thought it was only me. While surfing, out of nowhere I would lose connection even though im "connect" and pages would stall or will not load for minutes.

---

### Post by tjeremiah on 2009-09-19
Bump!

---

### Post by VMC on 2009-09-19
I don't think its Ubuntu's fault. Who's maintaining that iwl3945 driver ?

Have you check LP for any reports?

---

### Post by slakkie on 2009-09-19
> **VMC said:**
> I don't think its Ubuntu's fault. Who's maintaining that iwl3945 driver ?

Have you check LP for any reports?

iwl drivers are stock intel afaik. So Intel provides the code for their wireless cards to the linux kernel. See also [http://intellinuxwireless.org/](http://intellinuxwireless.org/)

I also have the iwl drivers, I haven't notices this issue, since my signal doesn't go below 50% at any given time.

---

