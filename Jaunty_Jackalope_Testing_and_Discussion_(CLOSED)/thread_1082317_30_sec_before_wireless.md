---
title: "30 sec before wireless"
date: 2009-02-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Technoviking on 2009-02-27
In Jaunty, my computer can not see any wireless networks till about 30 secs after I login Gnome. My card is a ipw3945. Anyone seeing this?

---

### Post by nystire on 2009-02-28
I'm currently seeing the same issue.

---

### Post by caryb on 2009-02-28
This might explain why every time I come home from work & logon to my wireless session I have to manually update my resolv.conf so I can get some DNS settings!



Cary


BTW this has been going on for about 4 days.

---

### Post by nIRV on 2009-02-28
> **Technoviking said:**
> In Jaunty, my computer can not see any wireless networks till about 30 secs after I login Gnome. My card is a ipw3945. Anyone seeing this?

+1, same wireless hardware driver too

---

### Post by MacUntu on 2009-02-28
> **nirv said:**
> +1, same wireless hardware driver too
+1

---

### Post by Nullack on 2009-02-28
I wonder if it is related to those changes that came through with changing the init order of some systems components recently.

---

### Post by nystire on 2009-02-28
At what stage is the card supposed to start searching for networks? Before or after X starts?

---

### Post by Gina on 2009-02-28
Yes, it does seem to take a long time to connect to the network.  Even with a wired connection it seems slow but wireless is worse.

---

### Post by MacUntu on 2009-02-28
But that delay already was there when I started testing with 28-4 (or less?) so I don't think it's related to the init script relocation.

---

### Post by dentaku65 on 2009-02-28
Silly solution.
In my case restarting the AP WI-FI router (ages that was switched on) fix the delay of connection with my wi-fi card.

---

### Post by nystire on 2009-02-28
Restarting the router doesn't appear to help in my case. For reference, I'm using a Toshiba Satellite P105-S9337.

---

### Post by rabid9797 on 2009-02-28
+1

---

