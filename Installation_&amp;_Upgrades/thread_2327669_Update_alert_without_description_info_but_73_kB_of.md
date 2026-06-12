---
title: "Update alert without description info but 73 kB of ghost data"
date: 2016-06-13
forum: Installation &amp; Upgrades
---

### Post by Leeteq on 2016-06-13
After a normal Ubuntu "Software Updater" update, I am presented with a strange message:

(here is all the info/text in the Software updater window, where the fields that normally contain update details are completely empty)

*********************
"Updated software is available for this computer.
Do you want to install it now?"

"This computer also needs to restart to finish installing previous updates."

Details of updates: <empty>

Technical description: <empty>

73 kB will be downloaded

Cancel / Install Now

***************

This looks suspicious.
Restarting the computer does not help, still want to install those 73 kB of "ghost data".
Tried to search (google plus here in the forums) if anyone else have reported this, but no luck.

---

### Post by howefield on 2016-06-13
What does the command line give you ?

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

You'll get notice of the packages to be upgraded and a chance to confirm or abort.

---

### Post by grahammechanical on 2016-06-13
It is not unknown for the panels under the heading "Technical details" to be blank. I have seen it in the past. True, I am not seeing it now. We may not be using the same version of Ubuntu. I am using the development version (Yakkety Yak). And I do not check the technical details of every package. But when this happened in the past if affected all the packages being offered for an update, and with the development version there are always lots of updates, and it went on for a few days.

Then there are those times when it seems the same packages are being installed more than once. Actually, they have been downloaded but not installed because they depend on other packages that are not yet ready to be put in the update channel. But the Update Manager lists them as available for update because the task has not been completed.

Regards

---

### Post by Leeteq on 2016-06-28
Thanks for the replies. 

Apt-get update did not show anything strange, went through without fixing it (only ran once). Did not run Apt-get upGRade at all.

But some days later, a normal Software Updater run - went through as normal, but this time that 73kb thingy was not there after it finished anymore.  I am very sure I did NOT/never actually update/accept/install it, so something on the server or in the index was causing it, I think. Now it is gone, I am not any wiser, but at least I did not accept it just to get rid of the strange issue.  

I will report back here later if it happens again.

---

