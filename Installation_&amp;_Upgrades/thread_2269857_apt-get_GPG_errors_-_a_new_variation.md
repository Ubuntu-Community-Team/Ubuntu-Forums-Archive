---
title: "apt-get GPG errors - a new variation"
date: 2015-03-18
forum: Installation &amp; Upgrades
---

### Post by Kenneth_Benson on 2015-03-18
I have a Trusty 14.04.1 server installed on my system. Because I live in a place with no internet, I found and downloaded the apt-offline package. (NB: the one in your repository is 1.3.1 and broken. They have a 1.6 that works now.) When I use apt-offline the first step works, the second step - getting the update and new packages - worked with some errors that flashed by. The third step, putting the updates and upgrades back on my system gives me errors about untrusted packages which I have seen in other threads. I understand that and the fix. I can't do the fix because that machine is not on the `net and I can't download the keys directly. Can someone give me any ideas on how to get the keys installed without a direct download?

Thanks in advance for any help and ideas!

---

### Post by dino99 on 2015-03-18
i have no clue for proposing a fix, but the updating/upgrading process check the download server (usually 'main') to get trusted packages (so the gpg sign)
So i suppose that apt-offline is buggy, as it cant indeed check that server (offline)
You might want to report about that issue to get (hopefully) a fixed package.

note: vivid has the 1.6 version, which was updated recently; maybe try to install it.

[https://launchpad.net/ubuntu/+source/apt-offline](https://launchpad.net/ubuntu/+source/apt-offline)

---

### Post by Kenneth_Benson on 2015-03-19
I already have the 1.6 downloaded and running. The problem lies with the fact that apt-offline is run 1st on my disconnected machine(with GPG) which generates a file that is then put on a usb stick with apt-offline and a copy of python that runs on windows(as that is all the library has), I then take that to the library to a windows laptop and run stage 2. Stage 2 gets any update statuses and downloads any requested upgrades. This stage does NOT have access to GPG so does whatever its told to do. Stage 3, I take the usb back to my machine and the contents of the stick are synced to the machine which then discovers the GPG issues. I need to get the keys onto the disconnected machine so it knows what to tell the usb stick.

---

