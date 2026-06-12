---
title: "Downgrade considerations? (10.04 - 9.10 or other?)"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by eventhorizonof on 2010-06-09
I have been experiencing extensive networking problems with 10.04 and I was wondering what options there are for downgrading to a different (hopefully more stable) release. I cannot seem to get a wired connection direct from the modem. I don't know if its just me but I feel an operating system that can't do something simple like this (without extensive terminal codes and file edits etc) is not for me. Here are my system specs:

3.06 GHz E6600 Core 2 Duo
2x2GB GSKILL DDR2
MSI G41M4-F (Realtek Ethernet)
500 GB Seagate 7200

I also have a PCI NIC card  Intel PWLA8391GTBLK GIGABIT 1PC


I just want to connect to the internet in a hassle free manner. Is there a release of ubuntu that I can "downgrade" to that will make networking hassle free? I have previously used 8.04 on a different machine with no problems. Is downgrading from 10.04 trivial? I currently do not have any important files as this is a new build and file backup is not an issue. Is there anything I should keep in mind or be aware of before downgrading?

Thank you for any help.

---

### Post by _khAttAm_ on 2010-06-09
What is the type of Internet Connection that you use?

Check with Live CD to see if the version you're planning to use can get you on the internet hassle free before the downgrade if you choose to..

---

### Post by eventhorizonof on 2010-06-09
I have cable internet. Is there a certain way to go about downgrading?

---

### Post by snowpine on 2010-06-09
There is no "downgrade" option; if you want to switch to a different release, you simply install it on top of your current install (you'll lose your data of course).

The problem with switching to an older Ubuntu is that you will have less support. For example if you downgrade to 8.04 (the oldest release that's currently supported) you will only have support through April 2011. The current release, 10.04, will be supported through April 2013. Therefore I strongly recommend troubleshooting your problem with 10.04 before giving up and switching to an older release with less support. I will take a look at your other thread and see if I have any suggestions. :)

---

### Post by eventhorizonof on 2010-06-09
How do I install 9.10 over 10.04 I have the files on a usb drive but it goes right into 10.04?

---

### Post by _khAttAm_ on 2010-06-10
> **eventhorizonof said:**
> How do I install 9.10 over 10.04 I have the files on a usb drive but it goes right into 10.04?

as **snowpine** mentioned, there is no downgrade available for Ubuntu (or all other OS I know of).. however I have tried it and it worked for me. I have mentioned it in my blog here: [http://www.khattam.info/2010/03/15/howto-downgrading-from-ubuntu-10-04-lucid-lynx-to-9-10-karmic-koala/](http://www.khattam.info/2010/03/15/howto-downgrading-from-ubuntu-10-04-lucid-lynx-to-9-10-karmic-koala/)

However, you should look out for resolution in your current version and consider downgrading only if you verify there is no easy fix for the problem and there is no problem with the current version.

As for USB drive not booting, your BIOS might not have been configured to boot from USB. In most new boards, you can just press F12 and select USB boot (or HDD and then in the list of HDD, select your USB.. ).. but that depends on the type and version of BIOS....

---

