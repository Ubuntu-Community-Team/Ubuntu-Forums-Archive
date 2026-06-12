---
title: "2 Grub boot options"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by justvano on 2011-02-24
I am very new to linux and Ubuntu. I recently upgraded from Ubuntu 10.04 to 10.10. I have the same black screen problem that many people have had. I have tried a few different solutions that people have offered on this forum and other forums. I won't include all the things I have done because there are too many so I will take any suggestions that people offer.
When I boot into the grub menu there are two different boot options (besides memory test) the first is "ubuntu, with linux 2.6.35-25-generic" and the other is "ubuntu, with linux 2.6.32.28." 
My computer specs: Asus F50Sf, Intel Core Two Duo P8700 Processor 2.53GHz, 4GB DDR2 800 RAM, 2 slots, 4GB Max, 320GB SATA Hard Drive (7200RPM), DVD SuperMulti Drive, 16 Inch HD LCD Display, NVidia GT 220M 1GB DDR2 Video RAM.

Forgive me for being ignorant to your replies like I said I am very new to all of this, please give me step by step instructions. Thank you for all of your help.

---

### Post by zvacet on 2011-02-25
There is nothing wrong with that.You simply have Lucid and Maverick kernel as boot option.It is good to have two kernels in case that latest doesn´t work as it should.If you are sure that you don´t need Lucid kernel go to the synaptic and in search box type linux-image and then remove 2.6.32.28.But you can also live with both kernels.Not really a problem.

---

### Post by oldfred on 2011-02-25
If you are getting the black screen on first boot after install, you need to edit grub to add a nomodeset.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
To install Ubuntu,  boot from the cd, press F6 and then select the nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

---

### Post by justvano on 2011-02-27
> **zvacet said:**
> There is nothing wrong with that.You simply have Lucid and Maverick kernel as boot option.It is good to have two kernels in case that latest doesn´t work as it should.If you are sure that you don´t need Lucid kernel go to the synaptic and in search box type linux-image and then remove 2.6.32.28.But you can also live with both kernels.Not really a problem.

The one that I am booting from is the 2.6.32.28 version and it works. It is the other version that gives me the black screen with the flashing cursor. So should I remove the other one instead of your suggestion or is there another option.

---

### Post by justvano on 2011-02-27
> **oldfred said:**
> If you are getting the black screen on first boot after install, you need to edit grub to add a nomodeset.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
To install Ubuntu,  boot from the cd, press F6 and then select the nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

I have tried a variation of your suggestion. I have already installed 10.10 (or upgraded rather from 10.04). So I have tried to edit that same line in both of the versions that I have mentioned in the original post with no success for either. Maybe there is something I am doing wrong. The reason I went with the upgrade was because I also had trouble with the install. I also gave me a black screen with the flashing cursor. I did not try to figure out why I just went straight to the upgrade instead. It would not even go into the live disk version either. Do you have any other suggestions?

---

### Post by oldfred on 2011-02-28
Have you tried the recovery mode or removing quiet splash to see if some error messages occur?

---

### Post by justvano on 2011-02-28
> **oldfred said:**
> Have you tried the recovery mode or removing quiet splash to see if some error messages occur?

I have tried to remove the splash and replace it with nomodeset or whatever it is. I managed to get to another screen that was blue with other options like "resume normal boot" or something along those lines. I'm not sure what this is called. I could not get it to load into the desktop environment though.

---

### Post by justvano on 2011-03-09
> **zvacet said:**
> There is nothing wrong with that.You simply have Lucid and Maverick kernel as boot option.It is good to have two kernels in case that latest doesn´t work as it should.If you are sure that you don´t need Lucid kernel go to the synaptic and in search box type linux-image and then remove 2.6.32.28.But you can also live with both kernels.Not really a problem.

Thank you for your help and the walk through. If you feel like it you could add that to this forum for others who have had the same problem. Thank you for the other suggestions as well.

---

