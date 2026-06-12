---
title: "My installation cannot continue"
date: 2011-02-23
forum: Installation &amp; Upgrades
---

### Post by BBAzar on 2011-02-23
I have been trying to install on my toshiba satellite c655 laptop the ubuntu operating system. Anytime it gets to where i can use it as a live DVD and I would want to install, it gets to stage 3 of 7 and gets stuck. No error messages are given, the install dialog can be minimized and other task done but the installation will never continue. Anyone with idea about how to go round it.

---

### Post by tommcd on 2011-02-23
Are you using a Ubuntu DVD iso? If so, then why not just try the regular Ubuntu CD iso that you can get from ubuntu.com?
Next, be sure to check the md5sum of the iso that you downloaded to be sure it is valid:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
If this iso checks out ok then it is good to use.
Next, if you are burning the Ubuntu CD from Windows, try using Iso Recorder or Infra Recorder, and be sure to burn the CD at the slowest possible speed:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Then when you boot the Ubuntu CD be sure to run the option to check the CD for defects:
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
Note: You may need to hit the space bar when you boot the Ubuntu CD to get the option to check the CD for defects.
These checks will ensure that you have a valid CD to use to install Ubuntu.

And welcome to the Ubuntu forums!

---

### Post by Rubi1200 on 2011-02-24
In addition to what tommcd already advised, please do the following:

1. full specifications especially RAM and graphics card

2. output of the following command from the terminal:
```
sudo parted -l
```
(lowercase L not 1)

Thanks.

---

### Post by Quackers on 2011-02-24
Is that the stage at which you enter your username? If so, did your username start with a capital letter? Try again without a capital letter.

---

