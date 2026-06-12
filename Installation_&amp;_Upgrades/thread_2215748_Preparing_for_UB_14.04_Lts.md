---
title: "Preparing for UB 14.04 Lts"
date: 2014-04-08
forum: Installation &amp; Upgrades
---

### Post by jaygee2 on 2014-04-08
I have aquired a Dell Optiplex GX620 Intel Pent D Cpu 3.40Ghz  3.39Ghz with 4Gig ram and 80gig HD.
My intention is to switch the HD with a blank spare and install Ub 14.04. keep the Win7 for use in case of disaster
The Win7 install looks very robust and the Dell needs the correct drivers etc.

I will use Parted Magic to format the HD and a live CD to install UB 13.10 (64 bit) as a start point

My main worry is will I damage the Bios or cause some other disaster. I believe that Dell is a difficult OS to alter.

Any hints or tips to achieve my objective would be much appreciated.

Jaygee

---

### Post by Double.J on 2014-04-08
Hi there!

Just to clarify, you plan to remove the existing hard drive and put in a blank which will only be used for ubuntu?

If that is the case, you do not need to use parted magic at all. When you boot the live ubuntu CD, you can just run install and select 'use whole disk'. If you do want to use separate partitions, this can be done from the ubuntu installer under advanced, or you can use the gparted  program on the ubuntu cd by clicking 'try'.

You can dual boot ubuntu and windows on the same machine. Although with an 80gb hdd it's not ideal - if you were to, give ubuntu 20gb and windows 60.

do you still have your windows install disks and licence? (The licencs on this machine is likely for xp) Personally I would put in a larger hdd, install windows 7 then run ubuntu and install alongside windows 7. The ubuntu installer will set up the bootloader grub so that you can choose between them at boot.

in this instance, windows should be installed first, and MUST be first on the hard drive.

as for your bios, there is no need to worry. No change you make to the hard drive will make any difference to you bios - it actually lives on your motherboard not your hdd. The only change you'll have to make to the bios is likely to be the boot order - setting the cd drive or usb device above the hard drive to the installer boots.

As for dell being difficult, I've not had this issue, they actually have very accurate manuals online and it's always easy to get the windows drivers after install.  People have had some trouble installing linux on new dells and particularly hp machines but this is because they have a new type of bios called uefi. Your machine will not have this issue.

Happy ubuntuing!

Jj

---

### Post by jaygee2 on 2014-04-08
Thank you for your reply, I was being overcautious but you set my mind at rest.
I went ahead as planned and have now got 13.10 installed. I suppose it is just a case of nerves.
I am looking forward to 14.04.The next step is DL a copy of 14.04 beta and see how that goes.

I have no reason to miss win7 but the machine came preinstalled and the HD has one of those strange folders 
for reinstall if necessary. I had a preused HD and did not know what was on it, nowt as it turned out. The install
went well and everything is up and running.

Thank you for your reply

---

### Post by Double.J on 2014-04-08
Hey there!

really glad to hear it went without a hitch!

will you be adding 14.04 beta to the disk as a dual boot? If so, i'd recommend telling it to install it's boot loader to a partition, not to /dev/sda. That way when you restart just your 13.10 will boot. You then open a terminal and run
```
sudo update-grub
```
and your 14.04 entry will be added to the ubuntu bootloader. It does create a chain boot, but as 14.04 is Still in beta, best not to have it in charge of the bootloader.

14.04 is pretty stable right now, I've only had two errors since the alpha, but still remember it's beta and things are moving real fast. I don't usually replace my existing main ubuntu install for the first month after launch!

Jj

---

### Post by jaygee2 on 2014-04-08
Hi, yes to all of the above, thank you for the info.

jaugee

---

### Post by jaygee2 on 2014-04-09
I have been unable to find the solved button. Perhaps someone could set it for me

---

### Post by westie457 on 2014-04-09
> **jaygee2 said:**
> I have been unable to find the solved button. Perhaps someone could set it for me

Click on Thread Tools at the top of the page, you should then be able to 'Mark as Solved'.

---

### Post by jaygee2 on 2014-04-09
Thanks Westie457, a job done.

---

