---
title: "Ubuntu 9.1 multi failures HELP!"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by ACampbell128 on 2010-03-29
Ok I just built a new pc it has an amd athlon ii, with gigabyte m68m-s2p with Nvidia 7025 chipset. I purchased 9.10 from a book store with a manual. stuck it and loaded it live. Booted up fine installed it to the hard drive. it went into hibernation and never would boot back up. Since then i have reformatted the hard drive and had several attempts at installing different flavors to no avail. First symptom is when it would get to the "installing the base" part then I would get Something along the lines of "failure to load /chroot. Still not able to do live runs!.....
 
Several Formats later, and now 16 cds with 8 different linux flavors, Still no linux!!!!!! Now when i try to install or run live I get a long list of squashfs errors. 
 
Along with this i have tried different cd/dvd drives(sata, p)ata... Hard drives both sata and pata, different cables. 
 
And still no avail!!!!! someone please help this is my first time with linux, and i have been in a 8 hour fight with it just to install it

---

### Post by ACampbell128 on 2010-03-31
Ok I have one more idea. I ordered another mobo this one with a ati chipset. hopefully it will work.

---

### Post by TBABill on 2010-03-31
You are obviously downloading different distros on another computer. Are you verifying those downloads via md5sum command from a terminal? To have so many varieties of distros failing to install sounds like either a hardware conflict/configuration issue or a defective component on a piece of hardware like the motherboard. 
 
Which distros have you tried and version of that distro? Do those CD's run in live mode ok on another machine? First thing you have to do is be certain you are working with a known good CD. After that, if your system will not run the live CD there is no point trying to install the OS because something is conflicting. Until you can resolve the live operation of the OS, don't try to install.
 
I have 3 laptops I test distros out on and my success has been found with Mandriva 2010, OpenSUSE 11.2, Linux Mint 8, Ubuntu 9.10 and 10.04, Lubuntu 10.04 and PCLinuxOS 2010 beta. They all did a wonderful job recognizing hardware and enabling sound, wireless, etc. Since I don't know what you are trying besides Ubuntu, if possible maybe give one of those a shot. They're all pretty much no-brainer installs (if I can do it they have to be! haha).
 
Have you tried pulling out one of your RAM chips (if you have multiple) at a time and trying to install, eliminating one then the other as good/bad? Your issue isn't real clear so I am just throwing ideas out there if you haven't tried already. Also try unplugging devices and running the LiveCD, such as your ethernet adapter, extra CD/DVD ROM, any extra HDD's, sound card (if not on the motherboard)?
 
Good luck. If you can post more specifics of what you encounter and at what step, plus what you are using to run as LiveCD besides Ubuntu, the forum users will surely jump in to assist.

---

### Post by ACampbell128 on 2010-03-31
Ok, I have tried Ubuntu 9.1, Mandriva 2009, Mandriva 2010, Ubuntu Netbook Remix, Ubuntu AMD64, i386, Gentoo, mandriva x86 amd64, ubuntu 10.4 beta. I have not been verifying with md5, not quite sure on how to do that. I have tested every piece of hardware except diff mobo. I got the live to work once and only once. And when I went to install it to the hard drive it installed, then went into hibernation mode, and didn't recover. So i rebooted and it wouldn't boot. so i tried to reinstall and it would fail at the installing the base.

---

### Post by TBABill on 2010-03-31
I'm guessing you have a hardware issue, but you already suspected that and took action to replace the MB.
 
If you're really new to Ubuntu this was what I did at first to perform the md5sum check. You have to know what the checksum is on the .iso file, normally given on the site you are downloading from. It's a very long string of numbers and letters that are compared to the output of md5sum on your machine to know you have an error-free .iso file. Sometimes there is a text file next to (above or below in the list) the file you are downloading and all it contains is that checksum. If you have it from the site, then do the following to compare:
 
Assuming the iso is in your download folder in your home directory, go to that file in your file manager. Once there, I think you click file, then open terminal. Within the terminal you can just type md5sum nameofyourfile.iso
 
You may have to use sudo md5sum nameofyourfile.iso and then enter your password when prompted. I haven't done it in a while so I don't recall exactly. But it will take a few moments to run and then it will output in the terminal the results. If the string of alphaneumerics matches what is on the site you downloaded from, then your file is ok. You also have to burn it to CD or DVD at the slowest speed your burner will allow to be as certain as possible you have an error free CD or DVD. You probably already knew that, but just in case.

---

