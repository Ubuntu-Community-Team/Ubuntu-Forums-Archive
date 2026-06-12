---
title: "How can I encrypt an 18.04 installation?"
date: 2018-04-30
forum: Installation &amp; Upgrades
---

### Post by steve169 on 2018-04-30
Using a live CD, I installed Lubuntu 18.04 on a 16-Gb flash drive. All went well, and it booted fine.

But there was never an opportunity offered to encrypt the entire flash drive, as there was when I installed 16.04.

Did I miss something?

If not, how can I encrypt the entire flash drive?

---

### Post by #&amp;thj^% on 2018-04-30
I have always used this method for Encrypting Thumb and USB Drives.
[https://www.linux.com/learn/easily-encrypt-your-flash-drives-linux](https://www.linux.com/learn/easily-encrypt-your-flash-drives-linux)
*****Fair and Important warning*****
It is crucial that you back up the data on your external drive. Do not continue on until the data has been backed up (otherwise, you run the risk of losing your data).  :)

---

### Post by sudodus on 2018-05-01
The Lubuntu **desktop** iso files use zram, which interferes with the installation of LVM with encryption.

Solution 1:  Turn off swapping to zram (or all swapping), and it will work to install LVM with encryption, if you have enough RAM in the computer.

```
sudo swapoff -a
```

Solution 2: The Lubuntu **alternate** iso files with the debian (text mode) installer need less RAM and do not use zram, and you can install according to the [testcase Encryption](http://iso.qa.ubuntu.com/qatracker/milestones/389/builds/171112/testcases/1439/results).

Please notice that encrypted home is no longer available as an option in the installers in 18.04 LTS.

---

### Post by steve169 on 2018-05-01
Dear 1fallen and Sudodus,

I will give it a try. Thanks. We newbies depend on you guys for survival.

---

### Post by sudodus on 2018-05-01
If successful, please come back and tell us the result.
Otherwise tell us what happened and ask for more help.

Good luck :-)

---

### Post by steve169 on 2018-05-04
Success, but I don't know why.

I followed the instructions in  "Testcase Encryption" but only a few of the steps, because the opportunity  to encrypt came up in the usual place. I just kept following instructions on the  screen. The installation works fine and is encrypted.

You guys must be magic. Many thanks.

---

