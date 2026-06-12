---
title: "Second time installing Ubuntu, second time FREEZE at &quot;installing the grub2 package&quot;"
date: 2020-02-13
forum: Installation &amp; Upgrades
---

### Post by mbindy1 on 2020-02-13
I am on the second attempt to install ubuntu, this time with a purchased installation dvd. The first was my own created usb.
Both times the screen froze at "installing the grub2 package." I am only a beginner, have had little experience going into BIOS, etc, but I need help, please.
I used ubuntu years ago and want my old laptop to run it. To clarify, I chose to install ubuntu NOT alongside windows10 and I chose to wipe everything.
I will be so grateful for any help! Please make it clear to this newbie. Thanks so much!

---

### Post by oldfred on 2020-02-13
What brand/model system? What video card/chip?

You say old, but Microsoft has required UEFI/gpt since Windows 8 released in 2012.
So are you installing in UEFI of BIOS boot mode.
And UEFI drives normally are gpt, but then you must have an ESP - efi system partition for UEFI install or a bios_grub partition for BIOS install or grub will not install. 

Post this:
sudo parted -l

---

### Post by mbindy1 on 2020-02-13
oldfred, thank you thank you for responding! I have to tell you that much of your reply is over my head, but I will try to figure it out and do what you recommend! I do not understand what you meant by "Post this: sudo parted -l"
My laptop is ASUS, bought in 2012
[COLOR=#4D4D4D][FONT=&amp]**[FONT=inherit]ASUS Laptop A53 Series A53Z-NS61 AMD A6-Series A6-3420M (1.5 GHz) 3 GB Memory 320 GB HDD AMD Radeon HD 6520G 15.6" Windows 7 Home Premium 64-Bit[/FONT]**
[/FONT][/COLOR]
[COLOR=#4D4D4D][FONT=&amp]
[LIST]
[*]AMD A6-Series A6-3420M (1.5 GHz)
[*]3 GB Memory 320 GB HDD
[*]AMD Radeon HD 6520G
[*]1366 x 768
[*]Windows 7 Home Premium 64-Bit
[*]DL DVD+/-RW/CD-R
[/LIST]
[/FONT][/COLOR]

---

### Post by EuclideanCoffee on 2020-02-13
Welcome to Ubuntu. Thanks for giving it a try. If you don't get it the first time, please be patient with yourself. You should learn a lot, but in no time, you'll be an expert. :)

I found this video of someone discussing how they went about booting Ubuntu on an older model ASUS computer.

[https://youtu.be/uuPEmQJfFwo?t=119](https://youtu.be/uuPEmQJfFwo?t=119)

I'm not an ASUS expert, but it appears you need to change something in the BIOS. I would start where I set the pointer in the video. Earlier, they did some updates that aren't needed.

To go to your BIOS, restart your computer and hit the F2 key or hold it down. You should see a bright blue screen. Take some time to explore this, and watch the video for some reference.

Feel free to experiment with these settings, and you'll get the hang of it.

If you want more help, ask specific questions to this thread, and I'll check up on it. Good luck.

---

### Post by oldfred on 2020-02-13
Windows 7 was normally installed in BIOS/MBR configuration.
A few vendors started using UEFI with Windows 7, probably to test their UEFI configuration.
You probably need to check Asus site to see if it has an update. My Asus motherboard allows me to download UEFI update & install directly from reading a FAT32 formatted partition. Some also have a bootable DOS image with the update file.

A few systems have ways to lock write onto hard drive in UEFI/BIOS settings.
Many need to be set to AHCI.
If you are erasing entire drive, it should not matter how you install (UEFI or BIOS), it should just work.

Post partition (parted) info using terminal in live installer.

---

### Post by EuclideanCoffee on 2020-02-13
Oh in the past I've had to set computers from "RAID" to "AHCI."

You may also want to consider turning off secure boot, especially if that doesn't mean much to you now.

---

### Post by mbindy1 on 2020-02-17
Hello again! UPDATE: I am now in a live session and at the point of installing Ubuntu 19.04. I have these choices for "installation type" and don't know which is best:
Reinstall ubuntu 18.04
Erase Ubuntu 19.04 and reinstall
Install Ubuntu 19.04 alongisde Ubuntu 19.04
Eras disk and install ubuntu
Which one should I choose?
Thanks!!!

---

### Post by oldfred on 2020-02-17
Do not use 19.04, it has reached EOL or end of life.
Ubuntu 19.04 support ends on January 23, 2020. 

Best to use 18.04.4LTS or if very new hardware 19.10.
20.04LTS will be out in April.

[https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)

Post this:
sudo parted -l

What do you want. It seems you already have an install or two?
Did you backup your data otherwise the erase options will remove all of it.

---

