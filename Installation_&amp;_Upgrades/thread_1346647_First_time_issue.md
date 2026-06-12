---
title: "First time issue"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by ivicks on 2009-12-05
Hello all,

So I have been running ubuntu 8.10 for about a year now and when ubuntu 9.10 came out I figured I would go ahead and install the new version. I also figured it would be a good time to buy a bigger hard drive to, so I installed in the new drive and checked the disk with the ubuntu 9.10 everything was fine but now here is the issue when I tell it to install.

I tell the install for english then to install from CD to the new hard drive
then the disk does its system check and updates the time. Once it has finished the time update it takes me directly to a login screen. It does not ask me to do any formatting or install setup. Just takes me directly to a login screen and I have no idea what the username and password is, since I didnt set anything up.

Any help would be great. Thanks

---

### Post by darkod on 2009-12-05
I remember something like this on the forum, I think.
Go into BIOS and disable any raid settings. Then boot with the ubuntu cd select Try Ubuntu option and once it has loaded from the cd in terminal do:
sudo apt-get remove dmraid

Sometimes a hdd comes with traces of raid settings on it and ubuntu 9.10 seem tobe unable to see the drive at all. Check this out and see if it helps.

---

### Post by ivicks on 2009-12-05
thanks for the reply darkod

I figured out the issue.

I forgot to disconnect the backup drive that had installed its was running on an ext3 file system and I am gonna say that caused the problem. Once it was disconnected the install went just fine.

Leason Learned: make sure you have your coffee :)

---

