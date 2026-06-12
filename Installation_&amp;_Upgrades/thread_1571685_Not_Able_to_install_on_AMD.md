---
title: "Not Able to install on AMD"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by rohansakhale on 2010-09-10
Hello,
I have installed Windows 7 Ultimate on my AMD Phenom II x4 945 having AM3 Socket system, with motherboard ASUS M2N68-AM SE2.
But now i wanted to install Ubuntu 10.04 AMD64 on it, but after installation when i try to Load Ubuntu from the boot menu, i just see the blank screen whereas my system keep running.
I am also been using Nvidia 9500GT 1Gb as an external graphics card.

In the hardware component support, i didnt find AM3 Socket support for AMD.
[https://wiki.ubuntu.com/HardwareSupportComponentsMotherboardsAmd](https://wiki.ubuntu.com/HardwareSupportComponentsMotherboardsAmd)

Please help me install ubuntu on my system.

Thank you

regards,
rohansakhale

---

### Post by Dayofswords on 2010-09-10
i have a AM3 CPU (amd phenom ii x6 1055t) so that cant be it as it works fine here

---

### Post by MacinViLLe on 2010-09-10
> **Dayofswords said:**
> i have a AM3 CPU (amd phenom ii x6 1055t) so that cant be it as it works fine here

Same here, I was able to install it with AM3 computer without that hassle. Try to remove the graphics card and use the onboard one, that may help us deduct.

---

### Post by rohansakhale on 2010-09-10
Which version did you download?
I tried Windows Installation & later i tried Installation using USB stick as instructed on the site during download.
It gets blacked out, any graphical reason??

Solution to the problem will be great :)

---

### Post by slooksterpsv on 2010-09-10
You could also try to install the NVIDIA drivers from terminal by going to a TTY.

Press CTRL+ALT+F1 when you just have the black screen, and it should give you a login prompt. Login, your password won't show when you type it in, so make sure you type it in correct. Now type in:
```

sudo apt-get update

```

Umm... I don't have or have ever used nvidia so you'd have to apt-get install [nvidia_driver] - which I don't know what one it is as there's tons of packages. ATI it's easy, fglrx.

---

### Post by rohansakhale on 2010-09-10
^ installing driver will be a later part i guess, i am not able to start even the Live Ubuntu using the USB stick, after certain step of loading some files for Boot-up installation, it just freezes or don't know i don't see anything going further, but the CPU is still running.

@MacinVille: Removing the graphics card wont be a proper solution to this i suppose, coz for running Windows & other Softwares & Games i need the graphics card.

Can anyone please help me more broadly regarding where i am going wrong in installation.

Thank you
[ ]("http://ubuntuforums.org/member.php?u=1062618")

---

### Post by PRC09 on 2010-09-10
I am running the same motherboard with a different AM3 processor and it installed fine using the onboard graphics .Try installing without the card and install it after you get up and running....

---

### Post by MacinViLLe on 2010-09-10
> **rohansakhale said:**
>  Removing the graphics card wont be a proper solution to this i suppose, coz for running Windows & other Softwares & Games i need the graphics card.

Remove the graphics card temporarily while we're troubleshooting you're Ubuntu problem. If Ubuntu runs using the onboard card, then we know where to focus. You can always put back the card anytime you want to use Windows ;)

Have you considered running the Ubuntu in a virtual box with Windows 7 as the host OS instead? Well of course it will depend on your needs.

---

### Post by rohansakhale on 2010-09-10
Installed Ubuntu successfully by removing the graphics card, but it affected my Windows 7 & i am not able to run it :(
Also how do i run Ubuntu along with the graphics card ?

---

