---
title: "partial disaster, update to lucid and its dead"
date: 2010-03-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2010-03-18
I get an error that says
File system could not be mounted: /proc/bus/usb

Cant go to recovery mode either. 
any ideas what that means?

ok i found a launchpad bug
[https://bugs.launchpad.net/ubuntu/+bug/507881](https://bugs.launchpad.net/ubuntu/+bug/507881)

---

### Post by sdowney717 on 2010-03-18
Ok, to fix you have to boot from a linux mint live CD
mount your ubuntu partition with some esoteric pie in sky commands, searched out using google.
edit your etc/fstab file and put a pound # sign in front of the line that says

none /proc/usb etc, etc....
reboot and it is up and going again

Likely anyone updating to lucid is going to run into this. I wonder if the official beta will fix it.

Now, I need to install that nvidia driver.

---

### Post by teh603 on 2010-03-18
This is why I don't do partial upgrades.

---

### Post by sdowney717 on 2010-03-18
you mean you do fresh installs?

I have been upgrading from feisty, but going to karmic something happened and had to start fresh.

---

### Post by teh603 on 2010-03-18
Yeah, I do fresh installs. Probably too many of them. Just ask my little Acer Aspire One how many times I wiped its poor little SSD. Or my Inspiron. I've only had it a few weeks and I've already wiped it five or six times.

I upgraded thru the package manager once from Jaunty to karmic, on my AAO, but it didn't improve anything and actually borked my cell modem's driver.

---

