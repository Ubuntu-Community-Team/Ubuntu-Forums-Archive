---
title: "First OS install... I get this error message."
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by Myfathersheart on 2010-12-29
I am just now starting to go deeper than the surface of my computer so I am very much a beginner. I have downloaded Ubuntu 10.10 and have tried to install it by mounting the image and installing "inside windows." Next, upon reboot and selecting Ubuntu from the windows loader it eventually went to a colorful screen but stayed there... the first time I let it sit there for 20 minutes or so then restarted, uninstalled/reinstalled tried again... then I let it sit there for 3 hours, nothing.  Next I tried to mount image and install "demo and full installation." This time upon reboot I choose Ubuntu from the windows loader menu and an error message came up. I will type it out below exactly as I see it because this is the same message that came up when a friend suggested I boot from a USB drive.

Busybox v1.15.3 (Ubuntu  1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) unable to find a medium containing a live file system

---

### Post by wilee-nilee on 2010-12-29
Are you just letting the wubi install happen to the C partition?

---

### Post by Myfathersheart on 2010-12-29
Yes.

---

### Post by wilee-nilee on 2010-12-29
> **Myfathersheart said:**
> Yes.

So how full is your computer?

How much space are you allotting in that first set up screen for Ubuntu?

Mounting the image, not sure what that means.

Here is the main wiki for your perusal if you have not been here already.
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20install%20Ubuntu?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20install%20Ubuntu?)

Not a lot of experienced wubi users on here but, that doesn't mean you can't get help it just may take longer.

If you wanted to just do a dual boot with partitioning I could help you there.

The times  have tried wubi it installed fine so I'm not sure of the hang up your having. 

Really one of your best insurance discs will be a Live Ubuntu cd of 10.10 burned do that and I bet wubi installs from it with no hitches. The cd will show up in computer in Windows as usual and there is a wubi installer in the ISO download.
[http://www.ubuntu.com/](http://www.ubuntu.com/)

---

### Post by Myfathersheart on 2010-12-29
I've used probably 20g of my 300g+ hardrive. 

I set up ubuntu for 17g because that is what the installer recommended.

I was mounting the disk image (at first) with virtual clone drive. 

And yes. I am ultimatley trying to dual boot with partitioning. So if you have help (an alternative to wubi) I will gladly listen.

---

### Post by wilee-nilee on 2010-12-29
> **Myfathersheart said:**
> I've used probably 20g of my 300g+ hardrive. 

I set up ubuntu for 17g because that is what the installer recommended.

I was mounting the disk image (at first) with virtual clone drive. 

And yes. I am ultimatley trying to dual boot with partitioning. So if you have help (an alternative to wubi) I will gladly listen.

Post a snippet of the disk manager so we can see how many partitions you have. You will need a burned cd or loaded thumb to do a actual dual boot.

You might try the Live cd or thumb and see if it loads wubi correctly first, your decision really.

---

### Post by Myfathersheart on 2010-12-29
I have a bootable USB version of Ubuntu 10.10 if that is what you mean by "thumb."  I have a CD as well but that is at home (I am at Starbucks, I won't have access to the CD for a couple of hours).

---

### Post by Myfathersheart on 2010-12-29
I just tried to install again from wubi and this time I installed first "inside windows" and commmitted 30g to Ubuntu. This Time during reboot I choose Ubuntu from the windows loader page. Then ran it in demo mode. This time it Ubuntu got to the install page where it runs you through a slide show of features but the installation froze the computer when it was on a stage that said something about spines.

---

### Post by Myfathersheart on 2010-12-30
Ok New update.  I installed Ubuntu from a CD with no problems on an older laptop than the one I have been trying to install on.  So now we know that it is my computer that is the problem. The laptop that is giving me difficulties is a MSI A6000 it has a dual core pentium processor and a nvidia GeForce 8200m G graphics card plus windows 7.

---

