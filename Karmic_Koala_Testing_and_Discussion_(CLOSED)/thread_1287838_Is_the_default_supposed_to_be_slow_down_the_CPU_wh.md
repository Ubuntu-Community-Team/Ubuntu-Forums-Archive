---
title: "Is the default supposed to be slow down the CPU when on batteries?"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andresmh on 2009-10-10
I think I've noticed Karmic to get slower when I'm using batteries (presumably to save power), is this the case? If so, where can it be turned off?

---

### Post by Longinus00 on 2009-10-11
I think some laptops actually have this enabled at the hardware level. Can you tell us what brand/model laptop you have?

---

### Post by zekopeko on 2009-10-11
AFAIK Ubuntu uses ondemand governor for power options. That means that even if you are on AC power you will still get CPU throttling by default. Every nice on my quad core since it saves energy (and my bill).

---

### Post by andresmh on 2009-10-11
I have a Lenovo Thinkpad x300.

---

### Post by Seventh Reign on 2009-10-11
> **zekopeko said:**
> AFAIK Ubuntu uses ondemand governor for power options. That means that even if you are on AC power you will still get CPU throttling by default. Every nice on my quad core since it saves energy (and my bill).

I dont think that is true.  I always have to manually switch my systems to Ondemand.  They are always set to Performance as default.

---

### Post by philinux on 2009-10-11
On demand seems to be the default on all the new installs I've done.

For desktops this seems wrong. Maybe someone would like to confirm or comment.
[https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/438813](https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/438813)

Easy to change by either adding the cpu scaling app to a panel or editing the file /etc/init.d/ondemand.

---

### Post by qamelian on 2009-10-11
> **Seventh Reign said:**
> I dont think that is true.  I always have to manually switch my systems to Ondemand.  They are always set to Performance as default.
Ondemand is the default on all my installs as far back as I can remember.

---

### Post by GeorgeVita on 2009-10-11
> **andresmh said:**
> I think I've noticed Karmic to get slower when I'm using batteries (presumably to save power), is this the case? **If so, where can it be turned off?**

Hi **andresmh**, for testing/understanding purposes I added 2 'CPU Frequency Scaling Monitors' to my Top Panel:
Right click on top panel, Add to panel, CPU Frequency Scalling Monitor', Add

Left click to select Frequency and/or behavior.
Right click, Preferences to select CPU# to monitor.

I add 2 icons for my 2 CPUs. It was 'on demand' by default.

Regards,
George

**EDIT:** > **philinux said:**
> Easy to change by either adding the cpu scaling app to a panel or editing the file /etc/init.d/ondemand.
I just increased my Firefox character size also as I did not saw the answer 2 posts above! Sorry ...

---

