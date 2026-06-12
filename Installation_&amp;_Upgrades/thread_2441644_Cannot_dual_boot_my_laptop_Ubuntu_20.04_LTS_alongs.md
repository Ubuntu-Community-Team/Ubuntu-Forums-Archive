---
title: "Cannot dual boot my laptop Ubuntu 20.04 LTS alongside W10 - Class 3 BIOS"
date: 2020-04-25
forum: Installation &amp; Upgrades
---

### Post by pedrotodorovski on 2020-04-25
[COLOR=#000000][FONT=Roboto]I have been trying to dual boot my laptop (Dell G3 15 3590) which came with Windows 10 with the brand new Ubuntu 20.04 LTS without any success. I followed several tutorials and I realized that my BIOS (Version 1.9.2) is not similar of 99.99% of the respective tutorials, because Legacy boot option was not available and my Bootable USB drive was not recognized at all (Rufus made the job - GPT partition type and Fat32). After some frustrated attempts and a surprisingly Windows crash (fixed using Dell SupportAssist software), I decided to do a deep research to discover what could be going wrong. I found [/FONT][/COLOR][this article]("https://www.dell.com/community/Windows-10/missing-option-quot-Enable-Legacy-Option-ROMs-quot-in-BIOS-setup/td-p/7381209")[COLOR=#000000][FONT=Roboto] where it is shown that UP TO 2020 Intel and Microsoft would build only UEFI based systems, "[/FONT][/COLOR][COLOR=#000000][FONT=Roboto]Intel intends to remove legacy BIOS CSM support from UEFI by Jan 2020[/FONT][/COLOR][COLOR=#000000][FONT=Roboto]", I bought my laptop this month (April, 2020) so... After several attempts I finally achieved Ubuntu installation process (via UEFI: USB), there was the following options on grub screen:

- *Ubuntu
- Ubuntu (safe graphics)
- OEM install (for manufactures)

There was no "Install Ubuntu or Try Ubuntu without installing" options as I think it should be!

By choosing the first option the installation processes started normally... But when it finishes it is requested to restart the laptop, and when I restart it on the boot screen appears this 3 warning messages:

```
[      0.000000] [Firmware Bug]: Failed to parse event in TPM Final Events Log
[      1.212471] nouveau 0000:01:00.0: DRM: failed to create kernel channel, -22
[2507.986735] sof-audio-pci 0000:00:1f.3: error: no reply expected, received 0x0
```
[/FONT][/COLOR][IMG]https://uploaddeimagens.com.br/imagens/XQuXAl4[/IMG][COLOR=#000000][FONT=Roboto]

And the boot screen freezed [/FONT][/COLOR][FONT=Roboto][COLOR=#000000]completely. (I had to turn of manually the laptop) and change Boot Sequence to start with Windows Boot Manager again.

The same happened by choosing the "Ubuntu (safe graphics) option, but instead of showing only 3 messages it showed much more...

My laptop specs:

GTX 1650
Intel I5-9300H
8Gb RAM
128Gb SSD and 1Tb HD
Dell G3-3590

I have no idea what to do to achieve this dual boot! Anyone could help me :/ Thanks for the attention![/COLOR][/FONT]

---

### Post by ubfan1 on 2020-04-25
At the grub menu, type e to edit, and on the linux kernel line, add the word "nomodeset" next to the quiet splash".  Then boot, and add the proprietary Nvidia drivers Software and Updates/Additional drivers tab, select the tested/recommended one. reboot, without the nomodeset, and it should work.

---

### Post by pedrotodorovski on 2020-04-25
I have to edit the linux kernel after installing Ubuntu, right? On the restart process...

---

### Post by ubfan1 on 2020-04-25
If you immediately install the Nvidia drivers on your first boot of the installed system with the nomodeset edited into the grub menu, you won't need any permanent nomodeset anywhere.

---

### Post by dirtscout on 2020-04-25
Try:
[I]sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install grub-customizer
sudo grub-customizer --help[/I]

You  can now review all setting in a graphical environment. From their I  would look at what **partition** Grub is installed. There are also other setting you can customize and troubleshoot from the interface. You can also search Duck  Duck Go for the settings you might need for Grub and edit them there. I  know we all prefer CLI... but sometimes visualizing the issue and  solution is more effective.

Try it out! Let me know if it helps

-dirtscout

---

### Post by dirtscout on 2020-04-25
You have to choose to use Nvidia Drivers in the the Nvidia Settings manager. Just search "Nvidia" and go from there. You should have no problems. I think I have a good solution for your dual boot issues below.

You can always try F11 on startup as well and just choose either Ubuntu or Windows. I actually prefer that method as it kind of obfuscates the installs.

---

### Post by pedrotodorovski on 2020-04-25
When you say F11 is on the boot process? Now I can only start Ubuntu by adding nomodeset in the Grub editor... But nomodeset make the OS 
ignore my graphic card, sound devices and drives in general

---

### Post by CelticWarrior on 2020-04-25
So please open Additional Drivers and install the Nvidia drivers.

---

### Post by pedrotodorovski on 2020-04-25
They are already installed! I went to Upgrades & Software, but the problem remains when booting system

---

### Post by CelticWarrior on 2020-04-25
Disable Secure Boot in UEFI and try again.

---

### Post by pedrotodorovski on 2020-04-25
Ok so let me sum up all that happened after trying all the steps that were listed...

First of all it's important to tell that NVIDIA proprietary and tested driver was selected by default on Ubuntu 20.04, so there was no need to change that preference.

I installed Ubuntu 4 times changing and testing some configs trying to fix the issue. One time I installed the "*Ubuntu" option, but this is not recommended for those who have dedicated GPUs like NVIDIA ones... and as you know on system required restart popped up those three warnings I said before that freezed the screen. On the other 3 times I selected the "Ubuntu (safe graphics)" option, that has 'nomodeset' write in linux kernel. The result was that I could open and run the OS, but functionalities that requires drives to work were not available such as sound was not working, the brightness of screen, and in some case even WiFi not working. I already installed this way with 'Secure Boot: Disable' in BIOS but the result was the same. I checked all the updates available but nothing was found. I either tried with 'nouveau.nomodeset=0' but nothing... I got stuck and nothing seems to work. I am even thinking to use Linux via WSL :roll::roll:

---

