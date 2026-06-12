---
title: "Software &amp; Updates won't offer upgrade to 16.04"
date: 2016-04-22
forum: Installation &amp; Upgrades
---

### Post by cathect2 on 2016-04-22
I have the Software & Updates tool set to automatically check for updates and to notify me of any long-term support versions. But, no matter what I do, it won't offer me the upgrade to 16.04. 

Anyone else having this issue?

---

### Post by slickymaster on 2016-04-22
If you're running 14.04 it will only tell you there is a new Ubuntu update after the first point release goes live which will just happen in July.

---

### Post by cathect2 on 2016-04-22
I'm using 15.10.

---

### Post by deadflowr on 2016-04-22
For 15.10 switch the Notification from Long term release to the any new release option (or whatever that option is called in Software and Updates)

---

### Post by cathect2 on 2016-04-22
Already tried that. No joy. I know I can force this through terminal for a dist-upgrade, but I'm trying to figure out why it isn't offering this to me automatically...

---

### Post by deadflowr on 2016-04-22
Run:
```
 sudo apt-get update
```
to make sure no repo problems.
If none.
then run
```
sudo apt-get dist-upgrade
```
to ensure a completely up-to-date 15.10.

To get the ability to upgrade, the update-manager needs an update.
Which should have come recently for 15.10.

This would have been installed through normal updates, but if there is a problem with the repos for you,
then those updates might not have been installed.

If either outputs from the above commands give odd errors or something, post those errors or oddities, please.

---

