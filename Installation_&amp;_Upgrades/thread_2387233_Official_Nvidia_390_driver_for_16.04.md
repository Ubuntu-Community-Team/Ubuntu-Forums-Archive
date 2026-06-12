---
title: "Official Nvidia 390 driver for 16.04?"
date: 2018-03-16
forum: Installation &amp; Upgrades
---

### Post by onlineguy on 2018-03-16
Hi,

I could not find a reliable answer to following question: is Nvidia's 390 driver targeted for a 16.04 release?

---

### Post by #&amp;thj^% on 2018-03-16
First "reliable" and "answer" on linux has far too many variables.
And Nvidia is not a target with Linux. (Low hanging fruit)
If you mean is there a driver version for 390 then yes there is.
But please note hardware specs here would give you a better chance at reciving good solid advice. :)
So if you would start with: (If not already installed)
```
sudo apt install inxi
```
Then show your retrun of:
```
inxi -G
```
Now others here will have a better shot at a proper solution/answer.
BTW I'm using the 390 driver now.
Thanks ;)

---

### Post by monkeybrain20122 on 2018-03-16
I have been using 390 for a few weeks on 16.04 (390.30 from Nvidia's cuda repo) You can get 390.25 in the driver ppa [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

"Official" is not really that important a point to consider iMO. In Jan the official mesa update screwed up some intel machines, one fix consists of upgrading the driver with a non official repo,

---

