---
title: "Could I install Ubuntu on a 8gb SD card and install the apps on an external hard driv"
date: 2021-07-18
forum: Installation &amp; Upgrades
---

### Post by juntjoo2 on 2021-07-18
I would have my laptop in between but 8 was thinking this "modular" setup would allow me to easily swap machines like when my current dinosaur laptop takes a final nose dive.

---

### Post by GhX6GZMB on 2021-07-18
Nice idea, but I doubt that it will work. There are so many configurations, drivers and hardware dependencies that you'd need a 100% clone of your "dinosaur laptop", and then I fail to see the gain.

---

### Post by juntjoo2 on 2021-07-18
What about how the live CD works? How could I use that but put on an SD card? Is usually used for temporary uses?

---

### Post by guiverc on 2021-07-19
You haven't said what release or system you want to install.

Ubuntu Desktop has recommended the minimum of 25GB since Ubuntu 17.10 (ie. all GNOME3 releases).  See [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements). Ubuntu Server has lower listed requirements, but in both setups it will depend on what you plan to do with it.  (*many blogs & users say you can live with less, but it depends on what you'll use it for & what software, upgrade procedures you'll follow etc*)

**Yes** you can have each directory on different drives; eg. put the directory /snap on a external drive so all installed snaps go to the external drive; likewise for other directories, so yes it's possible.

I've had a motherboard die and tried to just swap disk out of one box, and into another of the same brand/model box, and the system failed to boot. I briefly worked on it then decided it was far quicker to re-install rather than make it work and thus re-installed. I didn't expect to need to reinstall, given the same brand/model box was used even though some components may have changed given they were nearly a year apart in production.

I've swapped drives between  different boxes & had the resultant drive boot & be perfectly usable. In fact I've volunteered at a [recycler]("https://www.computerbank.org.au/") where we cloned drives (*an installed Ubuntu/Ubuntu-MATE system*) that were put in *builds* before *testing* and most booted *pretty near* perfectly, before our final tweaking (*for the hardware of the build*). At the recycler if a box failed to boot with a cloned drive it was usually discarded (ie. *box was really recycled*) as it may have meant hardware issues, or it required a real install *which took too long to configure and test*. 

Yes swapping installs between boxes is possible (*and works more than it fails*), but in my own experience I'd suggest it's not guaranteed, and I tend to *clean* install on boxes I rely on because of issues.  Especially given installs don't take long (*a QA-test install of Lubuntu on a `dell [optiplex] 990 (i7-2600, 16gb, nvidia geforce gt 6600 gt)` would take less than 2 minutes not including boot time though it had a good ssd*)

For a *live* system with persistence - yep that's definitely possible, and I'd create it with `mkusb` - I'll suggest reading [https://help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

---

### Post by juntjoo2 on 2021-07-19
Thanks for all that input. My laptop is archaic. I can't do much with it. 1ghz 4gigs ram. My Ubuntu disk is a few years old too. 16.0.4 I believe off the top of my head. I'll probably get new hardware within a year. All I wanted was something to play movies and do some excel with. I used to use some emulator for excel I forget what it was called but it worked. I just went back to windows 7 because of the familiarity but I wasn't able to reinstall it after my last mobo died(only cost $30 to replace)

---

### Post by sudodus on 2021-07-19
I suggest that you try a **light-weight flavour of 20.04.x LTS: Lubuntu, Ubuntu MATE and/or Xubuntu persistent live** created with [mkusb](https://help.ubuntu.com/community/mkusb). You may consider a fast USB 3 pendrive with at least 16 GB in order to get a better experience even if the computer has only USB 2 ports. See [this link](https://help.ubuntu.com/community/Installation/FromUSBStick/pre#Notes_about_speed).

Edit: After testing some time you may want to full installation of your favourite flavour of Ubuntu. Then it is best to make a **fresh installation**.

---

### Post by juntjoo2 on 2021-07-19
What about an SD card? I don't have a pen drive. But I've got a couple sd cards and am adapter to go in the slot in my laptop

---

### Post by sudodus on 2021-07-19
SD cards behave pretty much like USB pendrives, and there are fast and slow cards too. You can try with your 8GB card. Maybe it will be big and fast enough for you.

I would say that with a small and slow card makes it more suitable for a live or persistent live system. An installed system demands more space and faster access (and will also cause more wear of the memory cells).

---

### Post by C.S.Cameron on 2021-07-19
I am not understanding why you are not just installing Ubuntu on your external drive? It does not need to o on a flash drive or SD card. I find external mechanical drives faster than SD cards for running Ubuntu. A external SSD would be great. If you plan on moving it from computer to computer do not install any proprietary drivers at this time and everything should work okay

---

### Post by MAFoElffen on 2021-07-20
Just a note. 

You didn't say whether your system and card reader was USB, PATA or  SATA... Or if USB, whether it was USB2 or USB3. I know form experience that some internal card readers will not  let you boot from, because they don't usually show the cards as "storage" drives. Some USB SD card readers will not boot as a USB storage device. Make sure it comes up as USB Storage.

SD cards are slow to read and write. The fastest SD cards are about 4-5 times slower than USB2.0. USB3.0 is 10 times faster than USB2.0. A good 16GB USB drive is less than the price of the same size reasonably fast (as SD Cards go) SD Card...

So yes, people are recommending getting an USB thumb drive.

---

### Post by juntjoo2 on 2021-07-20
I don't have an external drive. Well, I could if I wanted to but my hdd isn't SSD so it would be slowly externally and as I'm learning anything "external" on this laptop is SLOW. So now I just want the startup/live install "disc" to be on my SD card to then install Ubuntu on my laptop, with hdd inside

---

### Post by juntjoo2 on 2021-07-20
> **MAFoElffen said:**
> Just a note. 

You didn't say whether your system and card reader was USB, PATA or  SATA... Or if USB, whether it was USB2 or USB3. I know form experience that some internal card readers will not  let you boot from, because they don't usually show the cards as "storage" drives. Some USB SD card readers will not boot as a USB storage device. Make sure it comes up as USB Storage.

SD cards are slow to read and write. The fastest SD cards are about 4-5 times slower than USB2.0. USB3.0 is 10 times faster than USB2.0. A good 16GB USB drive is less than the price of the same size reasonably fast (as SD Cards go) SD Card...

So yes, people are recommending getting an USB thumb drive.

Ah, okay... So my bottleneck is my SD card itself then! I get you now. I thought the USB transfer was slow! Even for 2.0. Must be the card. So "pen/thumb drive " for a live OS. I'm just gonna use the SD card for now to get it installed on my laptop. The CD drive can't finish the install. So on to the next step... 

With Ubuntu 16.0.4 live CD can I get the latest Ubuntu onto my SD card? I presume so. I'll be looking into that next...

---

### Post by sudodus on 2021-07-20
> **juntjoo2 said:**
> Ah, okay... So my bottleneck is my SD card itself then! I get you now. I thought the USB transfer was slow! Even for 2.0. Must be the card. So "pen/thumb drive " for a live OS. I'm just gonna use the SD card for now to get it installed on my laptop. The CD drive can't finish the install. So on to the next step... 

With Ubuntu 16.0.4 live CD can I get the latest Ubuntu onto my SD card? I presume so. I'll be looking into that next...

Yes, if the Ubuntu 16.04 live CD (I suppose it is actually a live DVD) works, you can get the latest Ubuntu onto your SD card. And then install Ubuntu into the internal HDD. I would recommend the lastest LTS release, 20.04.x LTS where x will be 2 or higher (depending on when you download the iso file).

Good luck :-)

---

### Post by juntjoo2 on 2021-07-20
Thanks!

---

### Post by ActionParsnip on 2021-07-20
8Gb is plenty for Ubuntu. You could have /home on a separate storage but you cannot change where packages are installed.

---

### Post by MAFoElffen on 2021-07-20
Is there a reason why you are using version 16.04 LTS? Because that old version is end-of-life already and is not getting any security updates...For example. is your system 32bit? 

Which then if a 32bit system, yes, 16.04 and do a release upgrade to get to 18.04, which will dead-end it there, but still be supported and get updates for a few more years.

If it is 64bit, and you install/run on 20.04 LTS, then you can put a snap directory onto whatever drive you want, and if you install apps through snap, then snap will install that app to that drive...

---

### Post by juntjoo2 on 2021-07-20
16.0.4 is what currently I have ready to work. As soon as I can I will upgrade. My dinosaur hardware is just slowing me down.

Its 64 bit

Whats snap?

---

### Post by MAFoElffen on 2021-07-20
Basically: "Snap" is a new type of package manager with it's own "SnapCraft Store" for applications. One perc, as it compares to Apt and the usual Ubuntu Store, Apt will lock a version of an application to the version of Ubuntu. The SnapCraft Store allows you to get newer versions of applications.

Here's a link to find out more: [https://snapcraft.io/store?_ga=2.5513649.308337836.1626740652-1473109897.1624679787](https://snapcraft.io/store?_ga=2.5513649.308337836.1626740652-1473109897.1624679787)

---

### Post by juntjoo2 on 2021-07-21
Thanks

---

### Post by him610 on 2021-07-21
You may want check out Xubuntu Core - [https://xubuntu.org/news/introducing-xubuntu-core/]("https://xubuntu.org/news/introducing-xubuntu-core/")

---

