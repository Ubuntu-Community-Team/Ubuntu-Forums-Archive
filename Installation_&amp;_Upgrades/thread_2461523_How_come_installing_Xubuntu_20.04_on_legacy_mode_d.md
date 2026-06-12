---
title: "How come installing Xubuntu 20.04 on legacy mode doesn't work?"
date: 2021-05-02
forum: Installation &amp; Upgrades
---

### Post by salamilimos on 2021-05-02
When I first got my HP ProBook 450 G2, second hand, it was set to Legacy Mode by default and I was able to install Lubuntu 18.04, it booted just fine, but when I tried to upgrade via clean install to Xubuntu 20.04, it wouldn't boot, I get this message:

[IMG]https://www.reviversoft.com/blog/wp-content/uploads/2012/08/DSC00057.jpg[/IMG]

So, the solution I found was to set my boot mode in my BIOS to UEFI. Although, I choose UEFI Native (Without CSM) because I didn't know the difference between that and UEFI Hybrid (With CSM).

[IMG]https://www.top-password.com/blog/wp-content/uploads/2014/09/hp-probook-uefi.jpg[/IMG]

So, after setting my boot mode to UEFI Native (Without CSM) and reinstalling Xubuntu 20.04 afterwards, and it worked, I was able to boot.

What I'm trying to understand is, why isn't installing Xubuntu 20.04 on Legacy Mode working anymore like it did in Lubuntu 18.04?

---

### Post by ajgreeny on 2021-05-02
What did you use to create the USB install media that you used?

Some USB writing applications don't give you a choice of mode of writing, eg rufus, I believe.
Did you check the downloaded iso file you used against its published checksum?

---

### Post by salamilimos on 2021-05-02
> **ajgreeny said:**
> What did you use to create the USB install media that you used?

I used Startup Disk Creator.

> Some USB writing applications don't give you a choice of mode of writing, eg rufus, I believe.
Did you check the downloaded iso file you used against its published checksum?

Yes I did, it matches.

---

### Post by grahammechanical on 2021-05-02
The motherboard is set to Legacy mode but what about the Ubuntu live.install session. If that is loading to UEFI then this might happen. Just guessing. I have a BIOS motherboard. So, I have no experience of my own from which to give advice.

Regards

---

### Post by oldfred on 2021-05-02
The boot of the USB is separate from the default boot set in UEFI settings for installed systems.

Most UEFI offer two boot options for a bootable Ubuntu live installer, one clearly UEFI like UEFI:XXX or XXX where XXX is name or label of flash drive.
How you boot install media is then how it installs.

Some tools like Rufus only create an installer in one boot mode or the other. Then the only option in UEFI will be to boot in that mode.

---

### Post by salamilimos on 2021-05-02
I'm still confused on what's happening though.

How come installing Lubuntu 18.04 on this laptop worked when it was set in Legacy Boot Mode? But doesn't work when I try to install Xubuntu 20.04 on the same boot mode, prompting me to set my boot mode to UEFI?

---

### Post by oldfred on 2021-05-02
Again, how you boot install media controls whether you install in BIOS/Legacy or UEFI.
The default setting in UEFI is only for your installed system, once installed.

---

### Post by salamilimos on 2021-05-02
> **oldfred said:**
> Again, how you boot install media controls whether you install in BIOS/Legacy or UEFI. The default setting in UEFI is only for your installed system, once installed.  I booted my liveUSB like this: [https://www.youtube.com/watch?v=k0ohDvl-GsY](https://www.youtube.com/watch?v=k0ohDvl-GsY)

---

### Post by oldfred on 2021-05-02
Then how did you make USB flash drive?

And which screen do you get?
Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen 20.10 uses grub for both
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by salamilimos on 2021-05-02
> **oldfred said:**
> Then how did you make USB flash drive?

And which screen do you get?
Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen 20.10 uses grub for both
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I used Startup Disk Creator.

My system boots in UEFI mode, but not in Legacy Mode.

---

### Post by ajgreeny on 2021-05-03
When you choose the USB as the device to which to boot to, there may be two instances of the USB available, one being the UEFI version, the other lagacy/BIOS.

Did you see them both in the list? Did you use the correct one?

---

### Post by coffeecat on 2021-05-03
Not chat. Moved to a support forum.

---

### Post by salamilimos on 2021-05-03
> **ajgreeny said:**
> When you choose the USB as the device to which to boot to, there may be two instances of the USB available, one being the UEFI version, the other lagacy/BIOS.

Did you see them both in the list? Did you use the correct one?

Based off what I recall, my boot options were like this:
[IMG]https://i.ytimg.com/vi/0IzLTVSmUKo/maxresdefault.jpg[/IMG]

I saw only one instance of "USB Hard Drive". It was the same both for Legacy Mode and UEFI Native.

---

### Post by oldfred on 2021-05-03
Please attach screen shots.
If you use the Forum's advanced editor, you can use the paperclip icon to attach screenshots. Post #4 1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

Have you upgraded UEFI to see if newer version is any better? 
This may be a case where using Rufus and selected just the boot mode you want.
Either UEFI/gpt or BIOS/Legacy/CSM boot with MBR.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

---

### Post by cmcanulty on 2021-05-03
I suggest you get into the BIOS menu not the boot menu usually is f2 f10 or some other key. The boot order options are not the same as the BIOS setting which have many other setup options

---

### Post by ubfan1 on 2021-05-03
Just the other day I noticed a 20.10 SD card in a USB adapter booted in UEFI, even when I selected "legacy first".  Selecting just legacy, and it didn't boot.  SD card created with dd from the ISO.  An older 18.04 USB (dd on the ISO) worked fine, booting the selected mode first.  I haven't booted legacy for ages, but something definitely changed in 20.10, so maybe 20.04 too.

---

