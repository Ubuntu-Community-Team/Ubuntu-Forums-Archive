---
title: "Problems after upgrading from 15.10 to 16.04"
date: 2017-07-14
forum: Installation &amp; Upgrades
---

### Post by ahmedn1 on 2017-07-14
I upgraded from 15.10 to 16.04 through the distribution upgrade utility. At the end it said upgrade successful with some errors. I rebooted and I couldn't login at all. It was a login loop problem but I could solve it using this ([https://askubuntu.com/a/761581/666490](https://askubuntu.com/a/761581/666490)).

Now after I logged in, I was struck by the terrible resolution (1024x768). So I guessed maybe I need to install fglrx (I have AMD Radeon R5 not NVIDIA). That's when I knew it is not supported on 16.04 anymore. And the Radeon open-source driver is already pre-installed with 16.04 but it doesn't seem to be.

The resolution is terrible and I cannot increase it from System Settings.

I tried installing the AMD GoPro driver and it solved the problem of resolution but i came back to the login loop problem. 

What should I do?

---

### Post by Autodave on 2017-07-14
Hopefully some one else will have a better answer for you, but I have never had any luck upgrading. 13 machines, one worked, 12 didn't.

Boot with a live USB or disc, copy everything you need, do a clean install. 10+ years running Ubuntu on up to 13 machines has taught me to only use the long term releases and do a clean install each time.

Having said this, you will no doubt get a few telling you that they have never had any probs with doing upgrade. I wish I was one of them. :-)

---

### Post by ahmedn1 on 2017-07-14
I thought of a clean install but i just wanted to avoid the pain of preparing my development environment again on a fresh installation.

---

### Post by ahmedn1 on 2017-07-14
The problem is solved. So, I installed the AMD GPU Pro driver which solved the problem but got me back to the login loop problem. I used the recovery console to remove the driver using ```
sudo amdgpu-pro-uninstall
``` and when I rebooted, I could login and have the old driver working with all the resolutions I should have.

---

