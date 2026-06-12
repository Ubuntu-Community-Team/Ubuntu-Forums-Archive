---
title: "The infamous grub command line problem after Ubuntu installation"
date: 2019-03-08
forum: Installation &amp; Upgrades
---

### Post by peter79494 on 2019-03-08
I want to install Kubuntu 18.10 on my laptop (Acer Aspire 5 A515-51G-529R). Unfortunately it doesn't start, although installing works without problems. Instead I end up on the grub command line where "minimal BASH-like line editing is supported", but without an obvious way out. Googling revealed this is not a rare problem, but nonetheless I was not able to find a solution. I think I already reinstalled Kubuntu 5 times, but the error was always "treatment-resistant".

I also tried boot-repair, because it was sometimes suggested. It did not change anything and returned the following:
[http://paste.ubuntu.com/p/XZM2Pgf9sS/](http://paste.ubuntu.com/p/XZM2Pgf9sS/)

I also tested Open-Suse and Manjaro and they start without problems. However in both of them the nvidia driver doesn't work for me (want to use nvidia-prime instead of bumblebee). That's why I want to try Kubuntu.

---

### Post by kc1di on 2019-03-08
Since you have an Nvidia card you need to boot with [nomodeset]("https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu") until you get the correct Nvidia driver for your card installed. This is not a grub issue per sae. So boot repair will do you no good here. It's a graphics card issue. 

My advice would be to reinstall and use "nomodeset" to boot the installed version then use the driver manager to install the correct Nvidia driver. 
once that is working you can deal with prime.

P.S. Both OpenSuse and Manjaro will work with Nvidia and do support Nvidia cards.  But each in their own way. Manjaro worked with my Nvidia card out of the box didn't have to install anything.

---

### Post by peter79494 on 2019-03-08
And how do I boot with nomodeset, or better how do I boot at all with this mimimal grub? The question on AskUbuntu doesn't help, because it requires Grub to be functional.

> Manjaro worked with my Nvidia card out of the box didn't have to install anything.

In my case Manjaro pre-installed bumblebee. When I installed the nvidia driver, Manjaro could not start anymore. OpenSuse still worked, but the driver did not run.

---

### Post by oldfred on 2019-03-08
Have you updated UEFI? Just about all systems need that.

Have you set "trust", you do show ubuntu not unknown, so it looks like you may have set trust?
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) &

---

### Post by peter79494 on 2019-03-09
> Have you updated UEFI? Just about all systems need that.

On the product website I could not find an update.

> Have you set "trust", you do show ubuntu not unknown, so it looks like you may have set trust?

If you mean the function "Select an UEFI file as trusted for executing", I already tried that both with grubx64.efi and shimx64.efi. In both cases the result is the same: It doesn't change anything.

---

### Post by oldfred on 2019-03-09
Are you installing in one mode (BIOS), but booting in the other boot mode(UEFI). And have previously installed in UEFI, or vice versa.
If you just get grub> that usually is booting the wrong version of grub which can only happen if you have two versions installed, one in MBR and one in UEFI and you boot the one you did not update with new install.

---

### Post by peter79494 on 2019-03-09
I installed it in UEFI mode and also started in UEFI mode. So this cannot be the problem.

Luckily I was finally able to fix the problem. I installed it in Legacy mode and when I boot in Legacy mode, **it works**. This surprises me, because I tried the same with Ubuntu 18.4 LTS, but failed. Fu****ck UEFI!!!

So let's hope Kubuntu fulfills it's purpose: Get nvidia-prime running.

---

### Post by grahammechanical on 2019-03-09
How to change the boot options so that the installation loads with nomodeset?

This link may help. Although I do not know if things have changed in recent years;

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


See Ubuntu CD Advanced Welcome Page Options. Then check out: Changing the CD's Default Boot Options. Then go to section 6 - F6 Other Options. At this point in the DVD loading process pressing F6 will bring up other options including nomodeset. Running the Live session in nomodeset will install Ubuntu with no modeset and so Ubuntu should load.

Then open Software & Updates and under the Additional Drivers tab you should see an option to install a proprietary video driver. Allow time for the utility to search online for the right driver.

Regards

---

### Post by ajgreeny on 2019-03-09
If you can get to the grub menu when booting an installed system that's giving you display problems at boot you can quickly press E when the menu appears.
This takes you to an edit page where you can search for the words "splash quiet" and add nomodeset there so it reads "splash quiet nomodeset" then press F10 to boot this one time with nomodeset (I think it's F10 but it says what to use in the text below the menu).

Once booted to the GUI install the recommended driver from Additional Drivers and reboot.

---

