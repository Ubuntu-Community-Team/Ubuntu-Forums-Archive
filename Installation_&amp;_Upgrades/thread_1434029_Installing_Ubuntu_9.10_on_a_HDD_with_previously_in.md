---
title: "Installing Ubuntu 9.10 on a HDD with previously installed WinXP and Ubuntu 7.04"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by siemprepeligroso on 2010-03-19
Dear friends,

I have a HDD of 160 GB, it is divided 80 GB to XP and 80 GB to Ubuntu 7.04, now I want to change from Ubuntu 7.04 to Ubuntu 9.10, since Ubuntu 7.04 is not supported anymore I can't have a direct upgrade, so I need to install a fresh Ubuntu OS.

I want to replace 7.04 with 9.10 without affecting my WinXP OS and of course I want to have the same size on both OS like before.
What do I have to do.

Is there going to be such a option to chose while installing setup or I have to do smth else.

Thanks in advance :)
BB

---

### Post by anagor on 2010-03-19
During the install at some point you will be presented with an option to choose where to install Ubuntu, look [here]("https://help.ubuntu.com/community/GraphicalInstall") at step 8.
Here you will need to choose manual, after which you will need to choose which partition will hold the new Ubuntu, point to your old ubuntu partition here and select "change" or "edit", I don't remember the exact name, its type (ext3,ext4 - preferably), mount point (just choose "/") and either to format or not. choose to format so that no old files from previous install will interfere with the new install.
And that's it I believe, all the rest is straightforward.

Also in my opinion I think you should wait for the Lucid release in April, or if you can't wait, install Lucid [beta]("http://www.ubuntu.com/testing/lucid/beta1"), which will upgrade itself to the release gradually. Even at beta stage it proves to be very solid and trouble free, at least for me.

---

### Post by siemprepeligroso on 2010-03-20
Thank you very much, for your help, I will try it tomorrow. I have to install Edubuntu so I guess I won't be able to find Edubuntu beta of the Lycid Lynx since they are released later than the official version.
Thanks anyway.

---

### Post by anagor on 2010-03-20
Edubuntu actually released lucid beta also, here [http://cdimage.ubuntu.com/edubuntu/releases/10.04/beta-1/]("http://cdimage.ubuntu.com/edubuntu/releases/10.04/beta-1/").

My reasoning for installing beta was that lucid is going to be an LTS release, it is seems to be very stable and quite good even if its not final right now.

Cheers;

BTW: I'm going to update my primary desktop tomorrow to lucid beta, so happy installing for both of us I guess.

---

### Post by siemprepeligroso on 2010-03-21
yeah you are right, I'll be starting the installation process in 30 minutes if nothing goes wrong.

---

