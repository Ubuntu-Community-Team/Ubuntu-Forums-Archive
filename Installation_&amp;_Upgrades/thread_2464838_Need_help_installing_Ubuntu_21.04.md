---
title: "Need help installing Ubuntu 21.04"
date: 2021-07-13
forum: Installation &amp; Upgrades
---

### Post by mpratt on 2021-07-13
Edit: I plan on re-installing Ubuntu once I determine what needs to be done to fix the below issue.

I am trying to set up a dual boot Windows 10 Ubuntu machine. I already had windows 10 installed, I bought a new hard drive to install ubuntu onto. I have several potential issues. During setup I checked the box to install 3rd party software because I was hoping to get the official Nvidia drivers for my graphics card, as I want to install a 3D rendering program, which requires them, at which point it asked me to put in a password for secure boot, which I did. Now after install when I restarted the machine I got a message to set up or modify MOK keys, or to continue to boot to ubuntu. I didn't know what needed to be done, so I told it to continue to boot to ubuntu. When Ubuntu loaded up, it only loaded on one of my monitors, and even then when I checked the display settings it said it was an unknown monitor, and didn't give me any options to change the resolution or anything. I don't know if these 2 issues are related or how to fix them. I have an Asus ROG motherboard, in the bios, secure boot is set to windows uefi, and I am afraid to change anything because I don't want to mess up windows, which is my primary machine. should I just re-install without checking the 3rd party software check box and then try to make sure I have the correct graphics drivers after I install? Any help is appreciated

---

### Post by monkeybrain20122 on 2021-07-13
Don't check installing third party software, it is easier to install them afterwards, moreover the installer might crash when you check that.

---

### Post by grahammechanical on 2021-07-13
What specifically are you asking help for? Does Ubuntu load correctly? Do you get the Grub boot menu which allows you to select either Ubuntu or Windows 10? If, so, does Windows 10 load correctly?

There really is not much difference between installing the Nvidia drivers by ticking Install Third Party Software during installation and using Software & Updates>Additional Drivers tab to install the Nvidia drivers after installation. In both cases we get the proprietary video driver. 

The failure to correctly detect both monitors has nothing to do with secure boot stuff. That information is a distraction. It might have something to do with the video driver. We can disable the proprietary video driver through Software & Updates>Additional Drivers tab. With a reboot we will load Ubuntu using an open source video driver.

Actually there is an important difference. Ticking Install third part software also installs some non-free video and audio codecs that are very useful. We can install these afterwards also.

It might help if you told us the model of the Nvidia video card that is in that machine. Some of us here might have knowledge of issues with Nvidia drivers for that model when using Ubuntu 21.04.

Regards

P.S. According to this post what you experienced regarding secure boot; passwords & MOK management is standard procedure.

[https://gist.github.com/bitsurgeon/b0f4440984c9e60dcd8fe8bbc346c029](https://gist.github.com/bitsurgeon/b0f4440984c9e60dcd8fe8bbc346c029)

---

### Post by mpratt on 2021-07-13
> **grahammechanical said:**
> What specifically are you asking help for? Does Ubuntu load correctly? Do you get the Grub boot menu which allows you to select either Ubuntu or Windows 10? If, so, does Windows 10 load correctly?

There really is not much difference between installing the Nvidia drivers by ticking Install Third Party Software during installation and using Software & Updates>Additional Drivers tab to install the Nvidia drivers after installation. In both cases we get the proprietary video driver. 

The failure to correctly detect both monitors has nothing to do with secure boot stuff. That information is a distraction. It might have something to do with the video driver. We can disable the proprietary video driver through Software & Updates>Additional Drivers tab. With a reboot we will load Ubuntu using an open source video driver.

Actually there is an important difference. Ticking Install third part software also installs some non-free video and audio codecs that are very useful. We can install these afterwards also.

It might help if you told us the model of the Nvidia video card that is in that machine. Some of us here might have knowledge of issues with Nvidia drivers for that model when using Ubuntu 21.04.

Regards

P.S. According to this post what you experienced regarding secure boot; passwords & MOK management is standard procedure.

[https://gist.github.com/bitsurgeon/b0f4440984c9e60dcd8fe8bbc346c029](https://gist.github.com/bitsurgeon/b0f4440984c9e60dcd8fe8bbc346c029)

OK, I went ahead and re-installed Ubuntu without checking 3rd party drivers, and everything installed fine, didn't have to deal with the MOK management. Now you said I can install 3rd party software/codecs/drivers after install, do I need to use apt-get or is it available through the Ubuntu software store?

Thanks,
Mike

---

### Post by CatKiller on 2021-07-14
> **mpratt said:**
> During setup I checked the box to install 3rd party software because I was hoping to get the official Nvidia drivers for my graphics card, as I want to install a 3D rendering program, which requires them, at which point it asked me to put in a password for secure boot, which I did. Now after install when I restarted the machine I got a message to set up or modify MOK keys, or to continue to boot to ubuntu. I didn't know what needed to be done, so I told it to continue to boot to ubuntu.

This is because you're using Secure Boot. If you don't want the hassle, just turn it off in your UEFI.

The specific thing that's happening is that Secure Boot enforces that only software that's been signed by a trusted source is allowed to be run.

Because of market dominance, all motherboards trust Microsoft, and no one else (except sometimes the motherboard maker). Ubuntu and Red Hat get around it by signing their software, and then getting Microsoft to sign their signing key, so there's a chain of trust that your motherboard will use, so Ubuntu (and Red Hat) will work with Secure Boot. 

However, the Nvidia driver module shim needs to be compiled for each kernel version. This, in itself, is painless, and is handled automatically by DKMS. But it means that it isn't going to be signed by Ubuntu, and it isn't going to be signed my Microsoft. Since you're creating it, and you've told your motherboard to only allow trusted signed software to be run, you need to sign the software and tell your motherboard to trust your signature. The first part is, again, easy and automatic, but the second part needs you to actually tell your motherboard to trust your software. If you think about it for a moment you'll see why that can't be automatic without user intervention. The process is called "enrolling the Machine-Owner's Key." It just stores your signature as one that your motherboard can trust.

The password that you set during the process is only a once-off thing. You only need to remember it for the one reboot as an authorisation step. 

Once you know what it's about, it's not hard. It is easier to just disable Secure Boot, though, which is what many users recommend.

---

