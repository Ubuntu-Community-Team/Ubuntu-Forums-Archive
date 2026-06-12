---
title: "Ubutnu20.04 stucks in boot logo screen"
date: 2020-05-04
forum: Installation &amp; Upgrades
---

### Post by jjj-9819-jjj on 2020-05-04
Ubuntu20.04 stops on the DELL LOGO Boot screen as shown in the following image.
[ATTACH=CONFIG]285739[/ATTACH]

The PC I am using is a Dell XPS 13 Laptop. Also, I'm running dual boot with Windows.
In previous versions (16.04 and 18.04), such a phenomenon did not occur.

Once I enter the recovery mode, I can log in with resume. However, when I reboot it, it stops at the Boot screen in the same way.

I reinstalled Ubuntu20.04, and when I started it with resume, I ran ```
sudo apt update && sudo apt upgrade && sudo apt full-upgrade
```, but it didn't improve. This problem has been occurring since the Beta version.

Please let me know if anyone knows how to solve this problem.

---

### Post by jjj-9819-jjj on 2020-05-04
As you can see [https://www.dell.com/support/article/en-us/sln306327/manual-nomodeset-kernel-boot-line-option-for-linux-booting?lang=en](https://www.dell.com/support/article/en-us/sln306327/manual-nomodeset-kernel-boot-line-option-for-linux-booting?lang=en) , I did the following and it started up normally.

(1) On the GNU GRUB screen, press the "E" key on Ubuntu.
(2) In the linux /boot/vmlinuz*** line, add "nomodeset" after "ro quiet splash". Then, press CTRL+X.
(3) At this point, you can see that the resolution of the Dell Logo Boot Screen has changed.
(4) In order to continue the nomodeset setting, change GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset" in sudo vi /etc/default/grub.
Then, press ESC+:wq.
(5) Execute sudo update-grub2 on the Terminal.
(6)sudo reboot

---

### Post by CelticWarrior on 2020-05-04
Just two comments:

The commands are wrong. You can run them separately but if you want one after the other then
```
sudo apt update && sudo apt full-upgrade
```
Please note there are no space in "&&". And yes, you should fully update your system like this or use the GUI tool.

If you need 'nomodeset' then you have a problem with graphics drivers. This parameter is not to be made permanent, it's just a temporary workaround. This is to say that you don't have the required drivers installed (Nvidia??) and/or have Secure Boot enabled. So, in UEFI settings, disable Secure Boot and try to boot normally. If it does boot normally then likely the drivers are installed but weren't loading due to Secure Boot.

---

### Post by jjj-9819-jjj on 2020-05-04
Thanks for the correction.....

As a graphics card, it doesn't use Nvidia graphics, it uses Intel UHD Graphics 615. Also, I disabled Secure Boot when I installed it, and it was still disabled when I checked it again.

---

### Post by dino99 on 2020-05-04
Need to report against 'linux' to ask kernel team maintainer to solve that 'nomodeset' problem (via apport: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) )

---

### Post by CelticWarrior on 2020-05-04
> **jjj-9819-jjj said:**
> Thanks for the correction.....

As a graphics card, it doesn't use Nvidia graphics, it uses Intel UHD Graphics 615. Also, I disabled Secure Boot when I installed it, and it was still disabled when I checked it again.

All [Dell XPS 15]("https://www.dell.com/en-us/shop/dell-laptops/xps-15-7590/spd/xps-15-7590-laptop#features_section") laptops have Nvidia Graphics, except the entry level model with an Intel Core i5 and Intel UHD Graphics 630, not 615.

t's actually a hybrid and switchable system with a iGPU Intel (CPU integrated) and a dGPU Nvidia (GTX1650, GTX2080 or RTX2070). So, you really need to install Nvidia drivers if not installed already (if you selected the option to install third-party drivers, firmware, software, ..., they should have been installed). Please check in Additional Drivers which Nvidia driver version you're using, if any. Select and apply the recommended version if using the open-source nouveau at the moment.

---

### Post by jjj-9819-jjj on 2020-05-04
I was very much mistaken. The laptop in question right now was a Dell XPS 13. Therefore, the Nvidia graphics card is not included. I'm sorry...

---

### Post by jjj-9819-jjj on 2020-05-04
I tried to do so, but I didn't know what procedure to follow, so I gave up.

---

### Post by CelticWarrior on 2020-05-04
> **jjj-9819-jjj said:**
> I tried to do so, but I didn't know what procedure to follow, so I gave up.

Tried to do what exactly?

Ok, so assuming you're correct this time and it has only the iGPU Intel. Now we have a problem: There's absolutely NO reason for it to hang on boot and then work with 'nomodeset' unless there's something very wrong in the installation. BTW, were there errors when running update/full-upgrade? Please post the complete error messages if applicable.

---

### Post by jjj-9819-jjj on 2020-05-04
Rather than trying, the correct answer is that I couldn't do it because the following screen didn't come up.
[ATTACH=CONFIG]285740[/ATTACH]
Also,
```
sudo apt update && sudo apt full-upgrade
``` completed successfully and didn't give up any errors.
I restarted it, but it still starts up normally. Only nomodeset can be found among the settings I've made so far.

Hmm, it's strange.
But come to think of it, the reason for doing nomodeset on an Nvidia-powered PC was to deal with the black screen by adjusting the resolution, right?
What nomodeset is doing is disabling kernel mode setting, which used to be a standard for changing the resolution and number of bits on the screen.

It's true that before I set up nomodeset, the resolution of the boot screen was rough, and it didn't start. However, by setting nomodeset, the resolution became normal and it started up. In other words, it might not have started due to a resolution problem?

Unfortunately, I'm a layman, so this may be a silly guess. However, this is the only way I can think of.

---

### Post by CelticWarrior on 2020-05-04
In layperson's terms 'nomodeset' disables graphics drivers and forces the system to fallback to a generic VESA mode.
The reason to use it with Nvidia Graphics is that some newer models have poor or no support by the default, open-source an unofficial nouveau driver for Nvidia Graphics. This results in a black screen or wrong resolution and/or freezes and all sorts of issues with input devices. So, by using it we force the system to run in that generic VESA mode, often with wrong resolution, but that at least allows the desktop to load. Then we install the Nvidia drivers the usual way and after that 'nomodeset' is not to be used anymore.

In your case you may need to update UEFI before anything else.

---

### Post by jjj-9819-jjj on 2020-05-04
Oh, I see. 

What I shold do is to update UEFI !
I've never updated my UEFI before.

I try to do tomorrow. I will report after doing this.

---

