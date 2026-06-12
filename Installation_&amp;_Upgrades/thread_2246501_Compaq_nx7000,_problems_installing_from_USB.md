---
title: "Compaq nx7000, problems installing from USB"
date: 2014-10-01
forum: Installation &amp; Upgrades
---

### Post by jake-mailinator on 2014-10-01
Hi all

I created an installable USB with the latest Ubuntu version, by following the instructions here [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) I created it on my Windows 7 laptop.

My plan was to use the USB to install Ubuntu on an older Compaq laptop I have lying around - I wanted to give it to my Dad. However, when I boot into the USB, I get the Installer Boot menu, but the screen freezes once I choose "Try Ubuntu without installing" or "Install Ubuntu". In fact, the only options that do anything are the memory test and Help. By banging around on the keyboard, I managed to get a prompt (not sure how I managed to do that as I can't reproduce it now), and when I typed 'install' there I got the error message described here [http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux/](http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux/)

Looking around on the USB, I noticed that the **syslinux.cfg** file was in a directory called uui, so I copied it from there into the root. But no joy with that, it still hangs.

This is my first time trying to install Ubuntu, and I've heard good things about it, so I'm hoping the experience improves once I get past this hump!

thanks

---

### Post by jake-mailinator on 2014-10-01
Oh yeah, I forgot to mention that I enabled 'USB *legacy* support' in the system BIOS

---

### Post by Vladlenin5000 on 2014-10-01
Hi, welcome.

Specs of that "old Compaq"???
It probably isn't enough for a modern 3D desktop environment like Unity, the one in standard Ubuntu. You might be better served by a variant with a lightweight desktop like Xubuntu or Lubuntu.

---

### Post by codenine75a on 2014-10-01
Try a low memory install maybe without X11.   Try Ubuntu version 7.

---

### Post by jake-mailinator on 2014-10-01
Thanks for the quick responses! I'm not sure how old the Compaq is. It's a model 'nx7000' running Windows XP. It has a 40gb hard drive and 512mb of RAM. The processor is Intel Pentium M 1.4GHz.

I just tried it again and got this error: 
```
                 
[LIST=1]
[*]ERROR: PAE is disabled on this Pentium M
(PAE can potentially be enabled with kernel parameter  "forcepae" - this is unsported, may cause unkown problems, and will  taint the kernel)
This kernel requires teh following features not present on the CPU: pae
Unable to boot - please use a kernel appropriate for your CPU. 
[/LIST]

         

```

---

### Post by codenine75a on 2014-10-01
Just as I thought.  Find an older version of Ubuntu that supports 512MB of RAM.  I believe versions 7,8,9,10.10 do.
Your welcome.

---

### Post by jake-mailinator on 2014-10-01
Ok, so which should I go for: Xubuntu or Lubuntu or Ubuntu 10.10?

---

### Post by sudodus on 2014-10-01
I think you need ***Lubuntu 14.04 LTS*** (new and modern) or a ***re-spin of Ubuntu 12.04 LTS***, which might be better at recognizing the old hardware in the computer.

See these links

[This is a detailed description how to use forcepae]("https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M")

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")                 
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]

Alternative to Unity on 12.04 LTS : [Gnome Classic]("https://help.ubuntu.com/community/PreciseGnomeClassicTweaks")

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by sudodus on 2014-10-01
> **codenine75a said:**
> Just as I thought.  Find an older version of Ubuntu that supports 512MB of RAM.  I believe versions 7,8,9,10.10 do.
Your welcome.

Please remember that there are no security updates for those versions. They have all passed end of life and should not be used when the computer is connected to the internet. See this link

[Forums Staff recommendations on EOL Ubuntu releases, in particular 10.04 desktop.]("http://ubuntuforums.org/showthread.php?t=2229730")

---

### Post by sudodus on 2014-10-01
> **jake-mailinator said:**
> Ok, so which should I go for: Xubuntu or Lubuntu or Ubuntu 10.10?

These community re-spins of Ubuntu 12.04 LTS might serve you well. Try them live before starting to install anything :-)

- Bento
- Bodhi
- LXLE

You can also try with some other distros. The following are extremely small and light-weight

- Wary Puppy
- Tiny Core
- Slitaz

---

### Post by jake-mailinator on 2014-10-01
Thank you! I've got too many choices now. :)

Which would you recommend for an elderly man with zero computer knowledge, who just wants to browse the internet, and use Skype?

---

### Post by Vladlenin5000 on 2014-10-01
> **jake-mailinator said:**
> Thank you! I've got too many choices now. :)

Which would you recommend for an elderly man with zero computer knowledge, who just wants to browse the internet, and use Skype?

Anything that works smoothly and has easy access to the apps required.

---

### Post by sudodus on 2014-10-01
1. Try Lubuntu 14.04.1 LTS, PC 32-bit. Download it from

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)


If problems with for example the graphics or wifi,

2. try LXLE from [http://lxle.net/download/](http://lxle.net/download/)

LXLE 32-bit revisited (current 12.04.4) via torrent

or normal download of the isohybrid version from

[http://phillw.net/isos/linux-tools/hybrid-isos/](http://phillw.net/isos/linux-tools/hybrid-isos/)


Read the tips in my previous posts if you need help with some details

---

### Post by jake-mailinator on 2014-10-01
OK, I'm back again. I just tried the latest version of Lubuntu, but the "PAE is disabled on this Pentium M" is still coming up.

Any other suggestions?

---

### Post by Vladlenin5000 on 2014-10-01
Knowing that I would go for suggestion #2 of the post #13.
I've had many old machines brought back to life with LXLE. It's a Lubuntu spin.

---

### Post by mörgæs on 2014-10-01
Stick to the latest software, that is Lubuntu 14.04.1.
The PAE problem is easily solved using [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE) 

Old versions should only be used as a last resort and only if they are still supported. I doubt you will need it for a 7000.

---

### Post by jake-mailinator on 2014-10-02
Thanks for all the help, guys!

---

