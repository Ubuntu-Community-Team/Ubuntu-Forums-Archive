---
title: "Lucid daily-live crash at end of install"
date: 2010-04-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by VMC on 2010-04-03
For the past two days I've experience ubiquity crashing at the tail end of the install. Right around 95%. *dpkg* was finishing up.
It started on Apr2 daily-live.

Here is the [bug]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/554324") I reported.

---

### Post by ELD on 2010-04-03
There is already a bug report:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/123301](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/123301)

---

### Post by VMC on 2010-04-03
> **ELD said:**
> There is already a bug report:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/123301](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/123301)

That bug was from 3 years ago. Ubiquity has changed a lot in years. Its not the same error I'm getting.

---

### Post by ELD on 2010-04-03
Oh crap didn't even notice the date, silly me.

---

### Post by VMC on 2010-04-03
> **ELD said:**
> Oh crap didn't even notice the date, silly me.

Your not alone. I notice a few people commented without leaving logs.

Once a bug has been confirmed, triaged, and fixed , its highly unlikely any developer will respond.

---

### Post by babyhuey on 2010-04-03
My install crashed as well.

That being said the install still booted and seems complete.

---

### Post by jppr on 2010-04-03
This bug was fixed in the package ubiquity - 2.2.14

---------------
ubiquity (2.2.14) lucid; urgency=low

  [ Jonathan Riddell ]
  * Update Kubuntu icon desktop/hi*-app-ubiquity.png for new logo

  [ Mario Limonciello ]
  * Don't bail out if oem-config/remove_extras doesn't exist yet since
    oem-config isn't actually installed. (LP: #554324, LP: #554664)
 -- Mario Limonciello <email address hidden> Sat, 03 Apr 2010 15:20:32 -0500

---

