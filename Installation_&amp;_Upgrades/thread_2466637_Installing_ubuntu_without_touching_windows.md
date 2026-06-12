---
title: "Installing ubuntu without touching windows"
date: 2021-09-01
forum: Installation &amp; Upgrades
---

### Post by doom52 on 2021-09-01
Hello.
Is it still valid point? [https://itectec.com/ubuntu/ubuntu-installing-ubuntu-without-touching-windows/](https://itectec.com/ubuntu/ubuntu-installing-ubuntu-without-touching-windows/)
Is anything has changed since or not? I experienced such problem with bionic beaver.

---

### Post by tea for one on 2021-09-01
Are you installing Ubuntu on a separate drive?

If so, then isolate, de-activate or remove your Windows drive before starting the Ubuntu installation.
Many UEFI firmware have settings to allow the user to de-activate the drives (physical removal is then unnecessary)

Both systems in UEFI mode with GPT is the modern way.

---

### Post by ubfan1 on 2021-09-01
Launchpad bug [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379) for UEFI installs still ignores user input for the bootloader location and puts it on sda.  Until enough people add themselves to the bug's "Does this affect me" list, looks like it will not get fixed (bug's six years old, but is a superset of a 7 1/2 year old bug for a USB disk). Note when the supersetting happened, the "Does this..." count got reset back to 0 ;^(

---

### Post by doom52 on 2021-09-02
> **tea for one said:**
> Are you installing Ubuntu on a separate drive?

If so, then isolate, de-activate or remove your Windows drive before starting the Ubuntu installation.
Many UEFI firmware have settings to allow the user to de-activate the drives (physical removal is then unnecessary)

Both systems in UEFI mode with GPT is the modern way.

Yes, i need to install ubuntu on external drive. I remember sometime ago i disabled a drive in the bios but i didn't help.

---

### Post by yancek on 2021-09-02
You have not indicated which version/release of windows you are using, which is it?
Nor have you indicated how many drives you have, other than to say you want to install Ubuntu to an external drive.  Should be pretty simple.
You have not indicated whether your drives are GPT or msdos nor whether your windows is an EFI install
Is this a Desktop computer?  It will be a lot easier to disconnect drives in that case which would be best for your purpose.

Ubuntu has had the documentation site at the link below for dual booting with windows 10 available for years.  Give that a read bearing in mind that there is no mention of the bug referred to in the post above by ubfan.  This is a good reason to disconnect the windows drive.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by mIk3_08 on 2021-09-02
We have here some links that can help you to install Linux Ubuntu Operating System along side
your Microsoft Windows
Here are some Links below:
Ubuntu Community Installation Guide!
[HTML]https://help.ubuntu.com/community/Installation[/HTML]
Installation/FromUSBStickQuick
[HTML]https://help.ubuntu.com/community/Installation/FromUSBStickQuick[/HTML]
Installation/FromUSBStick
[HTML]https://help.ubuntu.com/community/Installation/FromUSBStick[/HTML]
Installation/iso2usb
[HTML]https://help.ubuntu.com/community/Installation/iso2usb[/HTML]
SmartBootManager
[HTML]https://help.ubuntu.com/community/SmartBootManager[/HTML]

---

### Post by Frogs Hair on 2021-09-02
> **doom52 said:**
> Hello.
Is it still valid point? [https://itectec.com/ubuntu/ubuntu-installing-ubuntu-without-touching-windows/](https://itectec.com/ubuntu/ubuntu-installing-ubuntu-without-touching-windows/)
Is anything has changed since or not? I experienced such problem with bionic beaver.

I have recently built a new system using different drives and disconnected the drives and installed each OS separately. Linux was installed first on 3.5 HDD and then the drive was disconnected. Windows was then installed on nvme2 drive. F11 gives the option to boot the drive that is not set as default in the bios. No boot loader mess at all.

---

### Post by oldfred on 2021-09-02
If external drive, you need to partition in advance to have an ESP on external drive. 
Only if all other drives are disconnected, so external drive is default drive will it install directly.
If drive is blank it will create gpt drive. But Ubuntu will install in UEFI mode to MBR(msdos) drive in UEFI mode. It really should not.

Multiple work arounds in the bug report.
Oldfred unmounts ESP in middle of install to have correct ESP mounted for install. Mount only appears after partitioning screen.
Tim Richardson removes esp,boot flags from all drives before install & then after install restores those flags.

---

