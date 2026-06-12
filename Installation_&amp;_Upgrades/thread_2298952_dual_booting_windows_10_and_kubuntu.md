---
title: "dual booting windows 10 and kubuntu?"
date: 2015-10-14
forum: Installation &amp; Upgrades
---

### Post by Wroif on 2015-10-14
hi

I'm trying to get my computer to dual boot kubuntu and windows 10. My computer is a 2012 sony vaio s. 

I already upgraded on of my other laptops to ubuntu, and when I did, I just burned a ubuntu CD, inserted it in my laptop and rebooted with the cd inside it in order to install it. But this method doesnt seems to work on this computer. I've tried with a dvd, and from a usb, neither worked. I went into the bios to change the booting order, still nothing worked. 

I really don't know what to do at this point.

Any help would be appreciated. 

Thanks a lot guys!

---

### Post by oldfred on 2015-10-14
Is system UEFI or BIOS?
Are you installing 64 bit version of Ubuntu?
Model & video chip?

CD is not large enough for Ubuntu, not sure about Kubuntu?
Flash drive is often easier & reusable.

Many newer systems require you to also turn on or allow boot from other devices. Do you have settings like that in UEFI or BIOS?

---

### Post by Wroif on 2015-10-15
the system is bios,
i downloaded the 64bit version
the model is vpcsa290s
As for the Gpu, I think that it is a [COLOR=#333333][FONT=proxima-nova]AMD Radeon HD 6470M

I'm using dvd that are 4.63gig, and the kubuntu iso is 1.22gigs. I tried downloading the ubuntu iso and see if that works.

And how can I check if those setting are turned on?[/FONT][/COLOR]

---

### Post by Bucky Ball on 2015-10-15
*Thread moved to **Installation & Upgrades**.*

---

### Post by Wroif on 2015-10-15
i'm sorry! I didn't realize that my thread was in the wrong categorie. anywho

I was able to boot kubuntu from usb, but the only option available was to wipe windows 10 and install kubuntu. I dugged around a little, and I found out that it was like that because you cant have more than 4 partitions in one hard drive, and my laptop already has four. There is two called recovery, one called "system reserve" and the C: drive. I was wondering, what would happen if I were to delete one of the recovery partitions? one is 15.78 gigs and the other is only 504 mb. If i deleted the 504mb partition in order to install mint, would I encounter any issues?

---

### Post by oldfred on 2015-10-15
Often the smaller one is vendor misc files, and the larger one an image of drive as purchased (not a Windows installer), so you can recover. If small you should just be able to backup and many vendor tools still work from a logical partition, so if needed you can restore to anew logical partition.

But my new system insisted I make the vendor recovery & Windows recovery and after that offered to delete them. If hard drive fails it is a bit difficult to use recovery partition on failed drive to image a new drive.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

