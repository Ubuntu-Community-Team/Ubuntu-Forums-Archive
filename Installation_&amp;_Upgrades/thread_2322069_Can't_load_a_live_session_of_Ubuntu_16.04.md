---
title: "Can't load a live session of Ubuntu 16.04"
date: 2016-04-26
forum: Installation &amp; Upgrades
---

### Post by JoTwo on 2016-04-26
Hi everyone,

I am new to this forum but I have used Ubuntu for over 5 years now even though I stopped for a while when I had a Mac. I have now a brand new Asus N551V on which I want to install Ubuntu 16.04 alongside Windows 10. Before the release of 16.04, I managed to start a live session and install 15.10. I wanted a clean install of 16.04 so I completely deleted 15.10 without any problem.

After downloading 16.04 and creating a bootable live USB drive with it I restarted my computer to try the live session. The different options appeared as expected (Try, install, ...) but when I chose to try the live session, the loading screen remained frozen forever and I had to restart in Windows... I downloaded it again in case the first ISO was corrupted but it happened again. I tried a live USB of 15.10 and this time it worked. Any idea of what is the problem?

Thank you very much for your help.

---

### Post by Bucky Ball on 2016-04-26
*Thread moved to **Installation & Upgrades**.*

Just a thought: there might still be something missing that you're needing in 16.04. 

Boot from the install media, when you get to the purple screen with the icon at the bottom (if that still exists in 16.04, don't remember) hit any key and you should end up at the 'Try Ubunu' 'Install' etc. screen with some selections along the bottom of the screen.

Hit F6 and choose 'nomodeset'. Continue. Any different?

---

### Post by moteprime on 2016-04-26
I find these fails happens for two reasons, either the way I create the USB boot stick or uefi (bios) settings are to blame.
You'll have the best chance if you use "USB startupdisk Creater".
In your computers EFI (BIOS), make sure secure boot are off. As long as your'e experimenting with this turn on both 'Legacy* and UEFI, turn on CSM and to be sure also move the USB stick before your disk in the startup boot order.
The Ubuntu bootloader Grub, should be able to sort these things out, so you can turn of CSM and Legacy boot after installing Ubuntu.

---

### Post by JoTwo on 2016-04-26
Thank you Bucky Ball, I am going to try that as soon as I come back home.

moteprime, why using Unetbootin on Windows wouldn't work? Also Secure Boot is already off from when I installed 15.10. I really don't see why it would have to also turn on Legacy Mode and CSM since I could install 15.10 without doing that... Do you?

---

### Post by grahammechanical on 2016-04-26
See the section Changing the CD's Boot Options - section 6 - F6. See some pictures of what you are looking for. Sometimes we might need a combination of these F6 boot options

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards

---

### Post by moteprime on 2016-04-26
@JoTwo  I'm not out to argue with you, it should work fine in the setup you describe, but as it does not, something most be wrong.
I try new linux distributions every month on USB stick and in my experience it makes a difference to different distros if i use DD, unetbootin, usb creator. I don't know why, but i know that odds for Ubuntu to work for me are higher when using Startup disk creator. Unetbootin are notoriously buggy. 
And just this weekend i had to enable Legacy and CSM to boot a Debian live USB session.
Getting a live session to boot not always as easy as it should be.

---

### Post by JoTwo on 2016-05-02
Hi everyone,

I was really busy with work these past days so I couldn't test your solutions. I just tested the nomodeset option. I couldn't hit F6 since when I boot on my key Grub appears directly and it is not an option but after looking on the Internet I found that is is possible to change the boot command by hitting the key 'e'. I replaced an option by nomodeset and this time it seemed that it went a little bit further in the booting process because an empty desktop appeared with a big pointer but nothing else... Any idea why?

I haven't tested enabling Legacy yet but I'll dot it soon.

---

### Post by moteprime on 2016-05-03
If you can start Ubuntu your'e past any problem related to boot options in the BIOS.

---

### Post by sudodus on 2016-05-03
I think you have problems with the driver for your graphics and/or wifi chips. Please specify your computer

- Brand name and model (already known: Asus N551V)
- CPU
- RAM (size)
- **graphics** chip/card
- **wifi** chip/card

and we might be able to give you more specific help.

-o-

If still problems with 16.04 LTS, maybe you should try the still current version 14.04.1 LTS with long time support.

---

