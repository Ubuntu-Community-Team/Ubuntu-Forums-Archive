---
title: "Upgrade 10.04 ---&gt; 12.04"
date: 2012-05-02
forum: Installation &amp; Upgrades
---

### Post by deserthowler on 2012-05-02
I noticed my update manager for 10.04 doesn't show "upgrade to 12.04."  I have the manager set to "show LTS."  Does this mean the upgrade path isn't ready yet?  Not a problem, just curious.

Earl

---

### Post by jadtech on 2012-05-02
> **deserthowler said:**
> I noticed my update manager for 10.04 doesn't show "upgrade to 12.04."  I have the manager set to "show LTS."  Does this mean the upgrade path isn't ready yet?  Not a problem, just curious.

Earl

most using 10.04 have the same issue , the upgrade docs say you must be completely up to date before the release upgrade will be avalable to you 10.04.4 then the upgrade will appear.

---

### Post by deserthowler on 2012-05-02
> you must be completely up to date before the release upgrade will be available to you 10.04.4 then the upgrade will appear.

I just did the updates from update manager with no problems. :confused:  Is there a problem with PPA?

Earl

---

### Post by jadtech on 2012-05-02
try changing servers in update manager some time this works

---

### Post by QIII on 2012-05-02
First things first:  Back up everything you can't afford to lose.

Disable any PPAs and non-standard sources you may have in your sources list.  Uninstall any proprietary drivers.

Use the terminal to do

```
sudo apt-get update
```and 

```
sudo apt-get dist-upgrade
```dist-upgrade does ***not*** do the upgrade to the new version.  It does what upgrade would do but it also attempts to resolve dependency issues.

Then see if you have the option to upgrade to 12.04.

---

### Post by Clancy_s on 2012-05-02
I'm not seeing it on my 10.04 machine either; the release notes for 12.04 say the upgrade for 10.04 will come in June or July (my confusion) and give instructions for how to get it if you don't want to wait - I decided to wait until it's offered so didn't pay much attention to the instructions.

---

### Post by deserthowler on 2012-05-02
> **Clancy_s said:**
> I'm not seeing it on my 10.04 machine either; the release notes for 12.04 say the upgrade for 10.04 will come in June or July (my confusion) and give instructions for how to get it if you don't want to wait - I decided to wait until it's offered so didn't pay much attention to the instructions.

Thank you for the information.  I've been using 10.04 since early Beta.  I can wait a couple of  more months.

Earl

---

### Post by kingcharles1666 on 2012-05-05
This was the same for the 8.04 to 10.04 upgrade.
It will become available after the first point release of 12.04.
So when  12.04.1 becomes available you will start to see the message that a new release is available.

---

### Post by Tanker Bob on 2012-05-05
I upgraded my Dell laptop from 10.04 LTS to 12.04 LTS by going through all the intermediate upgrades. It took a little over 3 hours, but ran mostly on its own. That worked perfectly for me. 

If your laptop has nVidia video in it, you need to search the forum for the issues with the 12.04 nVidia drivers.

---

