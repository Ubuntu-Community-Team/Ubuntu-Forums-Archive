---
title: "Can't install any distro - weird blue lines"
date: 2018-01-10
forum: Installation &amp; Upgrades
---

### Post by idea2form on 2018-01-10
I get the same green and blue lines when Linux crashes (and won't let me do anything), who can explain these weird lines?  Nvidea cards? 2x780TI

I thought I was crazy when the same USB stick that installed Ubuntu flawlessly on my laptop failed on my desktop.  

When I tried to install on Desktop the green and blue bars appeared after starting install and I could do nothing after that.  

Then I searched for solution and you Arch people said to give Arch a try.   I was super excited until I finished the install and it would hang on login.  The same green and blue bars appeared and I couldn't do anything except Control + alt + delete.  I couldn't alt + F2 or whatever and get a new terminal window or anything.

[https://photos.app.goo.gl/dhHBL1CoKPUd7ZO12](https://photos.app.goo.gl/dhHBL1CoKPUd7ZO12)


I changed all sorts of bios settings like Cpu virtualization  Nothing.  

Went step by step again though Arch install with Wiki open.  Really careful to do everything right Same thing.  

[https://photos.app.goo.gl/mSqwnaYAfhKEUHRr2](https://photos.app.goo.gl/mSqwnaYAfhKEUHRr2)

Now I was getting mad and searching like crazy for someone with the same problem.  Got a new install of Ubuntu and put the .iso on my usb drive via DD this time and it did the same thing.  

[https://photos.app.goo.gl/VUHtU5WAAFNzwraU2](https://photos.app.goo.gl/VUHtU5WAAFNzwraU2)

What is going on???  I want Linux to love me.

---

### Post by ubfan1 on 2018-01-10
You should be looking for the Nvidia nomodeset fix -- that's a video problem which goes away when the Nvidia proprietary drivers get installed.  If a legacy install, you have a function key to select the "nomodeset" kernel booting option.  A UEFI install requires you to edit the grub menu (type e at the grub menu, instructions at bottom of screen) and add the word nomodeset at the "splash quiet" words on the line starting with "linux".  That should get you into a bootable state,maybe at lower resolution, but you can then run the software updater /additional drivers tab, to get the nvidia drivers.

---

