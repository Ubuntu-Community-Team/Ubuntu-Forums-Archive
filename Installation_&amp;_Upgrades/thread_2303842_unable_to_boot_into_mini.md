---
title: "unable to boot into mini"
date: 2015-11-22
forum: Installation &amp; Upgrades
---

### Post by stevenhmaple on 2015-11-22
Hey guys, I installed Ubuntu mini into one of my partitions (main system is Win10) and now I'm unable to boot into it. I tried using EasyBCD but adding that partition to the windows bootloader is a no go because, according to EasyBCD, I'm booting in EFI mode. Do note that I did install Kubuntu onto the same partitions before and was able to boot into it via win10's advanced startup. This time, and the previous time with Kubuntu, I've split my 30gb partition into the main partition and a 4gb swap partition.

I'm stuck here. I also turned off UEFI and set it to legacy mode in my BIOS. Any help/suggestions? Thanks! :p

---

### Post by Bucky Ball on 2015-11-22
Welcome. If Windows is installed in UEFI you should be installing Ubuntu in UEFI. Perhaps you could try again and make sure this is the case.

When you say the Ubuntu Mini, do you mean you did a [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD")? This is not the simplest route for a newcomer. Did you have a clear plan of what you wanted to achieve with it? There are no defaults with the mini, unless you choose a machine profile during the tasksel section. Whatever is installed apart from the kernel is entirely up to you and done through the CLI.

---

### Post by stevenhmaple on 2015-11-22
> **Bucky Ball said:**
> If Windows is installed in UEFI you should be installing Ubuntu in UEFI. Perhaps you could try again and make sure this is the case.

When you say the Ubuntu Mini, do you mean you did a [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD")?
Yes, I did do a minimal install. I put the iso into a usb and boot from it in legacy mode because it did not work normally. Dx

---

### Post by Bucky Ball on 2015-11-22
Start again if Windows is in UEFI and install in UEFI. 

Please re-read my last post as I've edited it. Basically, when you installed the mini, did you choose a machine profile during install? If not, it would be expected that on reboot you will be at a CLI (big black terminal) with a blinking cursor asking you to login.

---

### Post by stevenhmaple on 2015-11-22
> **Bucky Ball said:**
> Start again if Windows is in UEFI and install in UEFI. 

Please re-read my last post as I've edited it. Basically, when you installed the mini, did you choose a machine profile during install? If not, it would be expected that on reboot you will be at a CLI (big black terminal) with a blinking cursor asking you to login.
according to memory (I installed this a few hrs ago), I installed in legacy mode because the usb drive (or the installation files) were not detected upon boot. after reading the [minimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD") page, I understood that it wasn't compatible with UEFI, and I switched into legacy mode. During the installation, I went through the process as normal, as if the same with a graphical installer, and there weren't any particular errors either. I didn't install any software packages though, since I wanted to play around and learn with this, from the ground up. But I don't know what is a machine profile? The installation process seemed normal and I didn't see anything regarding a machine profile?

---

### Post by sudodus on 2015-11-22
I think you are right, the Ubuntu mini.iso works only in BIOS mode, not in UEFI mode.

But you can do something very similar with the Ubuntu Server iso file, and it is made to work also in UEFI mode, at least ***recent versions of Ubuntu Server amd64*** (64-bit version). For example, **ubuntu-14.04.1-server-amd64.iso** works in UEFI mode.

Don't install any server package (if you don't want it).

Reboot, login to the text screen system and install whatever you want to create, for example

```
sudo apt-get install lubuntu-core
```

or even something lighter. I think ***Bucky Ball*** has more experience than I of what packages to select for a good minimal graphical desktop :-)

---

### Post by stevenhmaple on 2015-11-22
> **sudodus said:**
> I think you are right, the Ubuntu mini.iso works only in BIOS mode, not in UEFI mode.

But you can do something very similar with the Ubuntu Server iso file, and it is made to work also in UEFI mode, at least ***recent versions of Ubuntu Server amd64*** (64-bit version). For example, **ubuntu-14.04.1-server-amd64.iso** works in UEFI mode.

Don't install any server package (if you don't want it).

Reboot, login to the text screen system and install whatever you want to create, for example

```
sudo apt-get install lubuntu-core
```

or even something lighter. I think ***Bucky Ball*** has more experience than I of what packages to select for a good minimal graphical desktop :-)
Oh, so there was an alternative! May I ask if there is a difference between the server and minimal? I'm not planning to install any packages until I get to the CLI screen, so everything should be the same?

---

### Post by sudodus on 2015-11-22
It will not be exactly the same but very similar, so I could not tell which version would be better (when installing in BIOS mode). Obviously, the server iso is better in UEFI mode, because it works ;-) Remember to use the 64-bit version.

---

### Post by stevenhmaple on 2015-11-22
> **sudodus said:**
> It will not be exactly the same but very similar, so I could not tell which version would be better (when installing in BIOS mode). Obviously, the server iso is better is UEFI mode, because it works ;-) Remember to use the 64-bit version.
Thanks! I'll give it a try. Since it is very similar, hopefully the server ver. won't impact the desktop experience a whole lot! :D

---

### Post by Bucky Ball on 2015-11-22
Before you go much further, what are you intending to install at the CLI once you have the kernel install with the server ISO? If you are intending to install something like 'xubuntu-desktop', just install Xubuntu because that is what you'll be doing and defeats the purpose of bothering with a mini. If you're intending *ubuntu-desktop anything, install the full version. Virtually the same and less bother. 

And my mistake, thanks sudodus. Mini doesn't work with UEFI. There are workarounds you can use to get it to boot with UEFI Windows, but you may not need to go there, depending on your plan of action with your install.

(PS: I thought people were misquoting me and getting my handle wrong until I noticed Buster Ball's user name! LOL.)

---

