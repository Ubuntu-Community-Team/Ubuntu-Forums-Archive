---
title: "Upgrade to Ubuntu 12.04 (Precise Pangolin) from 11.10 (Oneiric Ocelot)"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by ihustler on 2012-04-27
To get started, press **Ctrl – Alt – T** on your keyboard to open Terminal. When it opens, run the commands below to update your current system before upgrading.


sudo apt-get update && sudo apt-get upgrade



 
[[IMG]http://3-ps.googleusercontent.com/h/www.liberiangeek.net/wp-content/uploads/2012/01/Upgrade-to-Ubuntu-12.04_F4D0/504x70xupgrade_ubuntu_precise_thumb_3.png.pagespeed.ic.16lgG1P4FV.jpg[/IMG]]("http://www.liberiangeek.net/wp-content/uploads/2012/01/Upgrade-to-Ubuntu-12.04_F4D0/upgrade_ubuntu_precise_4.png")
 
After updating your system, press **Alt – F2** on your keyboard, then type the commands below into the command box.
update-manager -d 
[[IMG]http://3-ps.googleusercontent.com/h/www.liberiangeek.net/wp-content/uploads/2012/01/Upgrade-to-Ubuntu-12.04_F4D0/503x242xupgrade_ubuntu_precise_1_thumb.png.pagespeed.ic.fa0g8QEnoM.jpg[/IMG]]("http://www.liberiangeek.net/wp-content/uploads/2012/01/Upgrade-to-Ubuntu-12.04_F4D0/upgrade_ubuntu_precise_1.png")
 
Next, click ***‘Upgrade’*** to begin upgrading your system.




 
[[IMG]http://4-ps.googleusercontent.com/h/www.liberiangeek.net/wp-content/uploads/2012/01/Upgrade-to-Ubuntu-12.04_F4D0/503x275xupgrade_ubuntu_precise_2_thumb.png.pagespeed.ic.JPO-6lz0OV.png[/IMG]]("http://www.liberiangeek.net/wp-content/uploads/2012/01/Upgrade-to-Ubuntu-12.04_F4D0/upgrade_ubuntu_precise_2.png")
 
Wait for Ubuntu to finish downloading and installing all 12.04 packages.
 
[[IMG]http://1-ps.googleusercontent.com/h/www.liberiangeek.net/wp-content/uploads/2012/01/Upgrade-to-Ubuntu-12.04_F4D0/498x330xupgrade_ubuntu_precise_3_thumb.png.pagespeed.ic.3auNVYF1sv.jpg[/IMG]]("http://www.liberiangeek.net/wp-content/uploads/2012/01/Upgrade-to-Ubuntu-12.04_F4D0/upgrade_ubuntu_precise_3.png")
 
Restart your computer and you’re done.












[SIZE=3][I][B]Command Line Upgrade :
[/B][/I][/SIZE]


1. ***apt-get update***
2. [I][B]do-release-upgrade




Enjoy Upgrading :)...
[/B][/I]

---

### Post by lads on 2012-05-02
After doing the update + upgrade, I do not have the Upgrade button in the update manager. How else can I start the upgrade?

---

### Post by grahammechanical on 2012-05-02
Are you saying that after running the command in the first image that your system did not go through the other images leading to the last image? Distribution Upgrade with its check list of six things to do?

Have you tried opening Update Manager from System Settings and seeing if it has an Upgrade button.

I updated an 11:10 early this moring. Update manager did have an upgrade button but I have chosen to wait a few days before upgrading. Also, when I boot into 11.10 I get a message telling me that there is an upgrade available to 12.04.

Do you not get any of this?

Regards.

---

### Post by jadtech on 2012-05-02
ok key to getting the release upgrade to come up #1 your version of Ubuntu has to be 100% up to date, if ubuntu is used little its easy to miss up dates and kernel updates. you might want to change your server in update manager first, if its been a while the one you are using or had set could be  not working, not up to date or changed what ever  then go to  yout terminal window  and type or paste each of these line one  at a time ..

```

sudo apt-get update

sudo apt-get dist-upgrade

sudo do-release-upgrade


```

---

### Post by jerrrys on 2012-05-02
You can also do a release upgrade in terminal

sudo do-release-upgrade

jadtech beat me :)

---

### Post by lads on 2012-05-03
> **grahammechanical said:**
> Are you saying that after running the command in the first image that your system did not go through the other images leading to the last image? Distribution Upgrade with its check list of six things to do?

Have you tried opening Update Manager from System Settings and seeing if it has an Upgrade button.

I updated an 11:10 early this moring. Update manager did have an upgrade button but I have chosen to wait a few days before upgrading. Also, when I boot into 11.10 I get a message telling me that there is an upgrade available to 12.04.

Do you not get any of this?


The answer is always yes. This was already the case with the upgrade to 11.04 and 11.10, in different machines.

In the end I had to start it from the command line.

Thank you all for the answers.

---

### Post by Ymurti on 2012-05-04
I did everything that was instructed and I got this:

yajnamurti@yajnamurti-laptop:~$ sudo do-release-upgrade
Checking for a new ubuntu release
No new release found
yajnamurti@yajnamurti-laptop:~$ 


But the System info tells me that I am still using Ubuntu 11.10


Any help? :)

---

### Post by Ymurti on 2012-05-07
I got it and I have upgraded to Ubuntu 12.04 and I am very happy. Thank You to you all the Ubuntu :guitar:

---

