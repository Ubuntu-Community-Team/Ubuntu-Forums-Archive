---
title: "Ubuntu 20.04 UEFI installation - duty for creating secure boot password?"
date: 2020-08-30
forum: Installation &amp; Upgrades
---

### Post by x3nion on 2020-08-30
Dear community,

I'm new to Linux and Ubuntu and would like to install Ubuntu 20.04 as a dual boot configuration with  Windows 10 with UEFI standard. Therefore, I've been asked to create a secure boot password when  selecting the point with the third-party software. There it says, that  installing third-party drivers would require a secure boot password. However, I can deselect "Configure Secure Boot" without the point  "Install third-party software" being deselected.

Now I've got two questions:


 1) So is it possible to select the point with the third-party software  without having to configure secure boot? Or will this lead to problems,  i.e. that third-party apps won't be able to be installed afterwards and I get an error? Or would I be asked after the installation to create a password for  installing third-party apps?

2) In case I choose an UEFI secure boot password in Ubuntu, is there a possibility to deactivate it afterwards?

I attached a picture so that you can see which step during the installation process I mean.
Link: [https://www.magentacloud.de/lnk/lYBpOJcj#file](https://www.magentacloud.de/lnk/lYBpOJcj#file)

I'd be grateful for every reply!


 Kind regards, X3nion

[IMG]https://imgur.com/a/N5lOwNW[/IMG]

---

### Post by oldfred on 2020-08-30
Canonical cannot create a secure key for third party drivers which you may want for video or WiFi. But if a user believes driver software is secure, he can create his own key.
With UEFI Secure Boot then entire boot chain must be secure using keys. This is only for drivers or software that must be integrated into the kernel.  

If you remove a key, then you cannot Secure boot.
If not Secure booting, you can remove the UEFI Secure boot password. Some systems require you to set a UEFI password to gain access to some UEFI settings. But then you cannot ever lose that password or you have a brick. Some reset password back to blank after changing settings. 

I currently do not use Secure Boot, but may in future. 

Older:
Torvalds clarifies Linux's Windows 8 Secure Boot position
[http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

The only major wide spread boot virus was years ago released by Sony to prevent you from playing music, unless you had license from Sony.

---

### Post by x3nion on 2020-08-30
Hey oldfred and Thanks for your reply!

Well indepentent from having enabled or disabled secure boot in my bios, Ubuntu asks me to create an UEFI secure boot password.
But what happens if I installed Ubuntu having selected the point with the third-party apps, but deselected the password field and so haven‘t provided a password?
The third-party point remained selected and the drivers (e.g. graphic driver) seemed to have been installed anyway.

What could happen in this case, having not provided any password?

Kind regards,
X3nion

---

### Post by oldfred on 2020-08-30
I do not know, but expect you then could not easily change to UEFI Secure Boot.
If dual booting with Windows and a Windows update also updates UEFI, it may turn Secure Boot on and cause issues.
But you can either turn Secure Boot off, or reinstall drivers with a key, if desired.

---

### Post by x3nion on 2020-08-30
Mhm so disabling Secure Boot in BIOS should work in doubt in case I haven‘t provided a secure boot password in Ubuntu, right?
But what do you mean with reinstalling the drivers wirh a key? Is there a possibility to set up a secure boot password in Ubuntu after the installation?

Kind regards,
X3nion

---

### Post by oldfred on 2020-08-30
You would have to reinstall the secure boot versions of grub & kernel if not already installed. And then can add the proprietary driver using your key.

Secure Boot
[https://wiki.ubuntu.com/SecurityTeam/SecureBoot](https://wiki.ubuntu.com/SecurityTeam/SecureBoot)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

---

### Post by x3nion on 2020-08-30
Mhm okay, but you don‘t mean a complete new inatallation of Ubuntu?
And disabling secure boot in the bios wouldn‘t work out as well in order to install drivers?

Kind regards,
X3nion

---

### Post by oldfred on 2020-08-30
If you have UEFI on, but Secure boot off, drivers just install. You then do not need to provide key.

I always do a new install with every LTS release and often each in between version, just to see differences. But have yet to experiment with Secure boot on.

---

### Post by x3nion on 2020-08-31
So did I get it right that in my case where I haven't provided an UEFI secure boot password during the installation process, everything should be fine when I deactivate secure boot in bios and drivers will then install without problems?

---

### Post by oldfred on 2020-08-31
Its not whether you have provided an UEFI password which may or may not be required to change all the settings you need to change, but whether you have UEFI setting as UEFI Secure Boot on, UEFI on or CSM on. And each motherboard mfg seems to do it a bit differently.

My motherboard from 2014 has "Windows" and "Other". But manual says if installing Windows 7 use "Other". Windows 7 did not support Secure Boot, so that is the Secure boot on/off setting.

---

### Post by x3nion on 2020-08-31
Well I got told to create an UEFI secure boot password when changing the proprietary display driver. Then I created a password, and landed in the MOK menue after the restart and had to choose between "Continue boot, Enroll MOK, enroll key from disk, enroll hash from disk".
Unsure what to choose, I chose "Continue boot", but this led to Ubuntu not booting anymore.
What did I do wrong in this case? 

Kind regards,
X3nion

---

### Post by oldfred on 2020-08-31
You must still have Secure Boot on.

You must enroll your key, if you added a proprietary driver and have Secure Boot on.
But I do not have Secure Boot on, nor need any proprietary drivers, so cannot help more than link I posted in #6 which has the details you should follow.

---

