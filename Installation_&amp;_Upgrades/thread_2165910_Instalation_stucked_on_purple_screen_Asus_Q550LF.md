---
title: "Instalation stucked on purple screen Asus Q550LF"
date: 2013-08-06
forum: Installation &amp; Upgrades
---

### Post by holanda-kamilla on 2013-08-06
Hey! I'm trying to install Ubuntu in my new laptop but it's not working. I'm using the USB stick to boot and I've already tried to install Ubuntu 13.04, Ubuntu 12.04, Ubuntu 10.04, Ubuntu Gnome 13.04 and Linux Mint 13. I can choose "Install XXXX"  on GRUB menu, but after select it the installation stucks on purple screen or sometimes doesn't starts. Can you help me? I'm a Linux user and I don't even know how to start with the Windows 8 that comes with my laptop.

My laptop configurations:

Asus Q550LF
[COLOR=#49494A][FONT=Arial][h=4]4th Gen Intel® Core™ i7-4500U processor.[/h][/FONT][/COLOR]
[COLOR=#49494A][FONT=Arial][h=4]8GB DDR3 memory[/h][/FONT][/COLOR]
[COLOR=#49494A][FONT=Arial]1TB hard drive (5400 rpm) SATA
NVIDIA GT 745M graphics
[/FONT][/COLOR]
[COLOR=#49494A][FONT=Arial][h=4]Thank you.[/h][/FONT][/COLOR]

---

### Post by funkbuqet on 2013-08-22
I am considering purchasing this same computer. Did you ever have any luck getting it to boot? and if so how does it run?

In my search for a new computer, I read about similar issues with other new computers that had to do with the secure boot (UEFI) feature built into them. A goolgle search will bring up all the details. Hope you get it working.

---

### Post by holanda-kamilla on 2013-09-13
Don't buy this  model! It doesn't work with Linux. I sent it back to Asus to reinstall Windows and I'm gonna sell it. It's a nightmare if u want to use Linux!

I think u should consider this models here: system76.com/laptops

---

### Post by wmcinnis83 on 2013-10-19
I have this laptop and it works just fine, Ubuntu does get stuck but thats a problem with ubuntu. I have arch and it works 100%. It does get faster if you run nomodeset but still has some issues. Have not tried with 13.10 yet.

---

### Post by bluesabre on 2013-11-03
What do you mean by "Ubuntu gets stuck"?  I'm considering purchasing this laptop and would definitely like to know more.

---

### Post by jessehanson1981 on 2013-11-23
I just bought this laptop (Asus Q550LF), and I finally figured out the correct way to install Ubuntu 13.10. There are a few steps, but, in the end, everything is working great; including the touch-screen. I tried installing elementaryOS, but it doesn't detect the wireless. Since elementaryOS uses ubuntu 12.10 as a base, I think it is too old for everything to work without more headache. 
Also, there's no need to remove the Windows 8 installation, which is great news for everyone.
Anyways, here's what I did:
0. be aware that F2 is the button you tap to get into the BIOS; right after you turn on the laptop and see the Asus logo
1. use Windows 8 to boot into the BIOS and disable Secure Boot. Here's a link with some info: [http://www.eightforums.com/tutorials/17058-secure-boot-enable-disable-uefi.html](http://www.eightforums.com/tutorials/17058-secure-boot-enable-disable-uefi.html) In my BIOS, I have the CSM mode enabled, and the PXE disabled. I also disabled FastBoot. I believe PXE is just for booting from the network card, which most of us will never do. CSM is a compatibility mode, which seems to keep the BIOS settings fairly flexible.
2. use Windows command-line to install rEFInd . Long story short, download the binary zip file, locate C:\Windows\System32\cmd.exe in the file browser, right-click on it to run it as Administrator, and follow the instructions here: [http://www.rodsbooks.com/refind/installing.html#windows](http://www.rodsbooks.com/refind/installing.html#windows) . I ran the powercfg option also, which is outlined on the right side of that page.
3. turn the computer off, and boot into the BIOS. Go into the Boot menu, and ensure rEFInd is the first option. Save Settings and Exit. If you don't see rEFInd as a boot option, then it's not installed correctly.
4. plug in the USB drive and reboot. The rEFInd boot menu should appear, and you should see the USB drive with 2 options. Select the option (first option for me) that says EFI in the description. Note: I created my USB stick with another Ubuntu machine, using the Startup Disk Creator program.
5. At this point, you should be in the Ubuntu installer, and well on your way.. I re-sized my Windows partition to about 450GB, and created a 400GB Ext4 partition, along with a 8GB Swap partition. There's no need to change the location of the boot-loader. It should install directly to the hard-drive, not a partition. It was /dev/sda for me.

.. the whole point here is that you have to boot into a Ubuntu Installer using EFI mode ..
Happy Holidays! I'm sure there's a few out there who might not have bought this sweet laptop without knowing how to install Ubuntu.

---

