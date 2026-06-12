---
title: "WiFi not immediately connecting"
date: 2009-12-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Rallg on 2009-12-14
My Asus EEPC-1005HA has no trouble connecting its WiFi on Karmic. But on Lucid testing, there is an oddity: When the system boots, WiFi looks for (but does not connect to) a transmitter. Even if the transmitter was previously in use with the system, and whether or not it is password protected, automatic WiFi simply does not connect on first try at boot time.

However, if I go over to the WiFi icon, the pop-up menu of available sites will usually claim that I am indeed connected to the strongest, previously used site. If I click on its name, two things will happen: First, I will get a notification that WiFi could not connect. Then, a few moments later, the notification will tell me that it is connected, and I can use the WiFi.

I do not know what this means. In the end, I get WiFi, so it is an oddity rather than a problem.

Perhaps at boot, there is a race condition between the WiFi software and something else?

Has anyone else seen this behavior?

---

### Post by ranch hand on 2009-12-14
> **Rallg said:**
> My Asus EEPC-1005HA has no trouble connecting its WiFi on Karmic. But on Lucid testing, there is an oddity: When the system boots, WiFi looks for (but does not connect to) a transmitter. Even if the transmitter was previously in use with the system, and whether or not it is password protected, automatic WiFi simply does not connect on first try at boot time.

However, if I go over to the WiFi icon, the pop-up menu of available sites will usually claim that I am indeed connected to the strongest, previously used site. If I click on its name, two things will happen: First, I will get a notification that WiFi could not connect. Then, a few moments later, the notification will tell me that it is connected, and I can use the WiFi.

I do not know what this means. In the end, I get WiFi, so it is an oddity rather than a problem.

Perhaps at boot, there is a race condition between the WiFi software and something else?

Has anyone else seen this behavior?
I know nothing about WiFi but I do know you better be filing a bug on this one.
```

ubuntu-bug <the package that runs your connection>

```
Follow the directions once you are on launchpad.  Pretty simple and it will not be fixed if they don't know its broken.

---

### Post by Rallg on 2009-12-14
I'll file a bug report if it hasn't been fixed when beta stage approaches.

---

### Post by ranch hand on 2009-12-14
That is why you need to file now.  So it will be fixed.

Is everyone waiting for someone else to file?

If only one bug is filed on this it will not be worked on because it will not be confirmed.  It will get a higher urgency rating with more bugs filed.

---

### Post by Rallg on 2009-12-15
I marked it "solved" today, because the behaviour has changed. It was never a big problem, just a nuisance; perhaps I hadn't updated some file during the numerous partial updates.

---

