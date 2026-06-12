---
title: "Failed Upgrade, Lost Data"
date: 2012-05-20
forum: Installation &amp; Upgrades
---

### Post by nphawat on 2012-05-20
While i was upgrading from 11.10 to 12.04 ubuntu using the one click upgrade, first the connection was lost so i had to restart and carry on with a partial upgrade like suggested, at some point i had to restart and thats when neither versions of ubuntu launched properly.

I am backing up my data every 2 weeks but i didn't before trying the upgrade (Mistake i should have done so)

i know installed the 11.04 along side the partially upgraded 12.04 (like suggested by the installation menu to keep my old data files)

I was running only 64bit ubuntu and too bad i didn't read the **I upgraded, and now I have this error... **thread prior to upgrading

how can i retrieve my old data ?

---

### Post by darkod on 2012-05-20
It seems the main problem is that your connection got broken, not the upgrade process.

Also, you didn't need to install 11.04 just to get your data, it should be readable from live mode. Installing 11.04 along side would make it shrink your 11.10/12.04 installation which sometimes can actually corrupt data.

So, what exactly is the problem you are having? From either your 11.04 or from live mode you should be able to open the partitions on your disk and read the data you want.

Did you try that?

---

### Post by nphawat on 2012-05-20
Thank you for the suggestion i am extracting my data now from the newly installed 11.04 as i had no other way to access the live mode primely because i don't know how to access it. Can you please suggest a tutorial or a reference for beginners that can be helpful in my learning phase (starting by how to access the live mode) ?

Have a pleasant day

---

### Post by darkod on 2012-05-20
Every time you boot your machine with ubuntu cd or ubuntu usb stick, it will show a menu with Try Ubuntu and Install Ubuntu.

The Try Ubuntu is what we usually call live mode. It loads ubuntu running from that cd/usb, not making any changes to your hdd.

That's why this is best for any rescue operation because it doesn't touch your hdd much. It only touches it when you open the hdd partitions to copy data from them.

There is not a specific tutorial for live mode, just select Try Ubuntu and it will load it, unless there are any hardware compatibility issues. Then it will be working from the cd/usb.

After you copy your data, you can try couple of things to save the partially upgraded 12.04 if you want. Or maybe you prefer to do a clean install of 12.04 after you get the data out, it's up to you. If you don't want to lose software and settings already there, you can try saving it. If it fails, you can always do a clean install. :)

---

### Post by s9032g@comcast.net on 2012-05-20
Are you doing this wired or wireless? In any upgrade it is basic to do it wired. Did you install ALL available updates to your 10.04 before you started. Also basic.

---

### Post by nphawat on 2012-05-21
> **darkod said:**
> Every time you boot your machine with ubuntu cd or ubuntu usb stick, it will show a menu with Try Ubuntu and Install Ubuntu.

The Try Ubuntu is what we usually call live mode. It loads ubuntu running from that cd/usb, not making any changes to your hdd.

That's why this is best for any rescue operation because it doesn't touch your hdd much. It only touches it when you open the hdd partitions to copy data from them.

There is not a specific tutorial for live mode, just select Try Ubuntu and it will load it, unless there are any hardware compatibility issues. Then it will be working from the cd/usb.

After you copy your data, you can try couple of things to save the partially upgraded 12.04 if you want. Or maybe you prefer to do a clean install of 12.04 after you get the data out, it's up to you. If you don't want to lose software and settings already there, you can try saving it. If it fails, you can always do a clean install. :)


Thank you darkod for the clarification i extracted the data gave the live mode a try did a clean installation of the 12.04.

---

### Post by nphawat on 2012-05-21
> **s9032g@comcast.net said:**
> Are you doing this wired or wireless? In any upgrade it is basic to do it wired. Did you install ALL available updates to your 10.04 before you started. Also basic.


I was doing it wireless, unfortunately the wired option is not that easy, but its ok i managed to download the 12.04 separately than i installed it from a usb stick using pendrive to make it bootable.

---

