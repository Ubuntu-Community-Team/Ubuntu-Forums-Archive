---
title: "Installation of Ubuntu on dell 3593"
date: 2020-08-10
forum: Installation &amp; Upgrades
---

### Post by jonadan on 2020-08-10
Hello People,

I don't know whether this is the right place to ask this question but if it isn't then please ignore it.

The case is that few months back I purchased a new laptop dell 3593(i3-1005G1/1  TB /4 GB/Win 10/ Ms-office). It comes with preloaded annoying Windows 10 Os.

My Question is that whether I can Install ubuntu on that because I searched online and found([https://www.youtube.com/watch?v=Kv82a1-TyqU](https://www.youtube.com/watch?v=Kv82a1-TyqU)) that in the Boot options it has only UEFI option and no legacy/BIOS menu. Further I also came to know that if we install any other OS even if it is older windows 7 then there are issue with the drivers and people are not able to use Wifi or USB ports etc., because of lack of driver support. So if I install Ubuntu will I face any problem in that regard or after the installation I will be able to use my Laptop with Ubuntu normally.

I am not much knowledgeable in computers so please ignore the mistakes in explanation of scenario

Thank You

---

### Post by drpjkurian on 2020-08-10
You may check the hardware compatibility by booting into a bootable USB loaded with Ubuntu. You need not install ubuntu in your machine to check the hardware compatibility. As far as I know, UEFI shall not be an impediment to install Linux

---

### Post by CelticWarrior on 2020-08-10
Welcome.

Why do you think you need Legacy/CSM/"BIOS" options?
Ubuntu standalone or in dual-boot should be installed in UEFI mode. If dual-booting it actually must be because any preinstalled Windows 8 or newer is in UEFI mode.

---

### Post by oldfred on 2020-08-10
Issues are common across many models.
Dell  Inspiron 3670 UEFI update & AHCI worked
[https://ubuntuforums.org/showthread.php?t=2412152](https://ubuntuforums.org/showthread.php?t=2412152)
Dell Inspiron 3567 Review i3 7100u (Works well)
[https://ubuntuforums.org/showthread.php?t=2364642](https://ubuntuforums.org/showthread.php?t=2364642)
Dell Precision 3520 Turn off RAID & change to AHCI
[https://askubuntu.com/questions/1096492/installing-ubuntu-18-04-alongside-windows10-the-ssd-is-not-recognized](https://askubuntu.com/questions/1096492/installing-ubuntu-18-04-alongside-windows10-the-ssd-is-not-recognized)

But did see one post of a Dell user who could not change to AHCI in UEFI settings. Not sure if user was not doing it correctly, did not have UEFI updated, or Dell has a system that does not work. Most Dell systems work if UEFI updated, SSD firmware updated, drives changed to AHCI. A few need extra drivers, but Dell typically releases newer drivers. But it can take a bit before those are all included in a kernel, driver, or distribution. So newer systems need newest Ubuntu and may need newer kernel.

---

### Post by jonadan on 2020-08-11
Thanks drpjkurian for the advice I did as per your instructions but my USb is not visible so I think there is hardware compatibility issue.

Greetings CelticWarrior
Thank you
I posted this question because  I found that many users experimented with their newly purchased dell laptop then ended with messed up system. So I just want to confirm.

Thank you oldfred
You are very right that there are multiple issues and there is no single solution but I am grateful for your help

Cheers to all of you for giving helpful advice. I guess that we have to accept whatever software junk they(Microsoft+Dell) throw at us and also there is no escaping from it 
:cry::cry:

---

### Post by oldfred on 2020-08-11
The Dell issues are all easy to fix, its just if you do not know you need to change some settings or try to use an old distribution that then it seems like a major issue.

Dell was one of the first to have many systems update UEFI with Linux. I do not plan on ever buying a laptop again, but would only purchase one that had UEFI update from Linux. Even if vendor first level help says they do not support Linux, if they are in this list, then they at least provide some support.

[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist) & 
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

---

### Post by risacher on 2021-01-20
I've been using Ubuntu 20.04 on the Dell Inspiron 3593 for months now.   It works pretty well.  I have identified two challenges:

The built-in bluetooth adapter will not work with the HSP/HFP profiles, so it can use a bluetooth headset for playing audio but not as a microphone.  I solved this by using a USB bluetooth adapter.  The bug I reported here: [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1881612](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1881612)

After updating the BIOS in late 2020, the 3.5mm headset-jack microphone no longer worked properly.  I solved this by adding the following line to /etc/modprobe.d/alsa-base.conf:

options snd-hda-intel model=dell-headset4

---

