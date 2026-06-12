---
title: "Is upgrading from Ubuntu 20.10 to 21.04 safe yet?"
date: 2021-05-24
forum: Installation &amp; Upgrades
---

### Post by josefranw on 2021-05-24
Hello, well, yes... that. Do you happen to know if this is a safe process now, or shall I continue to wait?

---

### Post by grahammechanical on 2021-05-24
The answer is here:

[https://www.omgubuntu.co.uk/2021/05/upgrade-to-ubuntu-21-04-from-20-10](https://www.omgubuntu.co.uk/2021/05/upgrade-to-ubuntu-21-04-from-20-10)

Regards

---

### Post by josefranw on 2021-05-24
I do that but, still no upgrade is shown.

But, when I do this:

update-manager -d

I do get a notification of a new version but then, it says it's "under development"... I don't know if it is safe to upgrade yet... that's why I'm asking if anyone has upgraded successfully.

---

### Post by anneranch on 2021-05-24
Everybody is in title to opinions. 
...especially when no money is involved...
Would you bet $ on YOUR opinion ??

It theory - no video etc etc is needed , this SHOULD work 
sudo apt update && sudo apt dist-upgrade

---

### Post by philhughes on 2021-05-24
Upgrades are blocked again:

[https://askubuntu.com/questions/1338429/ubuntu-21-04-update-available-then-disappears](https://askubuntu.com/questions/1338429/ubuntu-21-04-update-available-then-disappears)

---

### Post by Impavidus on 2021-05-24
Apparently the upgrade was enabled, then disabled again. I haven't seen it offered on my Xubuntu 20.10 laptop. I'm in no hurry, so I'll wait a few more weeks. If still no upgrade in July, I'll fresh install.

---

### Post by Dennis N on 2021-05-24
> I don't know if it is safe to upgrade yet... that's why I'm asking if anyone has upgraded successfully. 

I did two upgrades of Ubuntu 20.10 to 21.04. One was on May 1 from a BIOS install of 20.10, which at the time I assumed was safe, based on the facts as I understood them. It worked with no problems. The second was an upgrade from a UEFI install of Ubuntu 20.10 on May 14, in which I accepted the risk and went ahead. I also worked fine. That computer is relatively new - built in late 2018. Both are desktop machines.

The BIOS was done by terminal:
**sudo do-release-upgrade -d**
Without the -d no upgrade was offered at that time. Can't say how it will work now. 

The UEFI system was done via the "Software Updater" GUI which offered the upgrade after updating the system.

That's just two cases, No guarantees of your success.

---

### Post by josefranw on 2021-05-24
I upgraded. By doing sudo **do-release-upgrade -d** because s**udo do-release-upgrade -c** did not prompt any update. It all works fine... so far.

---

### Post by mIk3_08 on 2021-05-24
> **josefranw said:**
> I upgraded. By doing **sudo** **do-release-upgrade -d** because **sudo do-release-upgrade -c** did not prompt any update. It all works fine... so far.
Well congratulations.  Great job! Enjoy to the new feature of Ubuntu 21.04 Hirsute Hippo. I think this has a cooler features now and it has 9 months support. Good Luck.

---

### Post by anneranch on 2021-05-25
I wonder at what point there will be a "real" statistics  of  successful upgrade and how long should one run the "new and improved (cola) " before it is statistically 
proven it actually  works?
definition of statistic:  accurate processing of bogus  data

---

