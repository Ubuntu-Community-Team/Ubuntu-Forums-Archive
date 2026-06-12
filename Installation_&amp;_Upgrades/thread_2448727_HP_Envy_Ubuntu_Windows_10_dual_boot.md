---
title: "HP Envy Ubuntu Windows 10 dual boot"
date: 2020-08-12
forum: Installation &amp; Upgrades
---

### Post by rt4525 on 2020-08-12
Hello,


I am new to Ubuntu. I am trying to install Ubuntu 20.04.1 for dual boot alongside Windows 10 on an HP Envy with AMD FX-8800P Radeon R7, 12 Compute Cores 4C+8G processors. Following various online tutorials, I have tried to install Ubuntu multiple times. I have used multiple USB installers including Rufus and Universal USB Installer to make a bootable USB drive.  I have changed the settings on the computer each time. I have turned off fast startup, disabled secure boot, partitioned my hard drive so that 60GB will be free, and changed the boot order in BIOS. When I restart my computer, the USB is read and I select the option to install Ubuntu. A screen with the HP logo and the Ubuntu logo comes up and the initial disc check starts. After disc check reaches 100% it says that no errors have occurred and the Ubuntu spinner wheel starts spinning. That is where the installation stops. The logos stay up and the spinner continues spinning. I have left it in that state for hours and even overnight with no change. Ubuntu never starts installing beyond the disc check. Can someone please tell me what I can do? 
Thank you very much.

---

### Post by oldfred on 2020-08-12
Have you updated UEFI?
And if SSD, the SSD firmware?

Many new systems need drives changed from RAID or Intel RST to ACHI. But if using Windows, you must first install AHCI driver into Windows or it will not boot in AHCI mode. 

Windows AHCI instructions - some have found safeboot method better
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571)
[https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems](https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems) 
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)
AHCI enable - May have to unlock bitlocker if used
[https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243](https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243)

---

### Post by rt4525 on 2020-08-13
I have a HDD. I went to the HP website and downloaded and installed a few updates including UEFI and drivers for disk drive. After reading some of the links you provided, I checked in device manager under IDE ATA/ATAPI controllers and it says AMD SATA Controller. After the updates were completed, I restarted the computer and started the Ubuntu installation like normal, but the same thing as before happened (initial disk check 100% no errors, then spinner spins and nothing ever happens).  Also, I checked in [FONT=Arial, Helvetica Neue, Helvetica, sans-serif][COLOR=#242729]BIOS and I didn't see anything about RAID or AHCI. But, after reading some of those provided links, I am a little concerned about AHCI because I don't want to mess anything up and lose any data or functionality of Windows OS. [/COLOR][/FONT]

---

### Post by oldfred on 2020-08-13
check your computer manual. 
And you need to add the AHCI driver into Windows first, before changing it in UEFI settings. Otherwise Windows will not boot. But you can change back & then it boots, so you can add driver then.

---

### Post by rt4525 on 2020-08-15
I bought an external hard drive and backed up the entire system before making any changes to my computer. I guess I'm missing something though or it's just not making sense to me... I cannot find where to change settings to AHCI anywhere. I tried to download AHCI drivers but when I go to Device Manager and try to update drivers manually, it tells me "The best drivers for you device are already installed."  I didn't see in BIOS either where it was even listed as an option to change. I did another search online and found something that took me to RegEdit to change settings:

RegEdit
Computer
   HKEY_LOCAL_MACHINE
      SYSTEM
         CurrentControlSet
            Services
               iaStorAVC
                  StartOverride
                     0          0x000000003 (3) .... Change (3) to (0)
               storahci
                  StartOverride
                     0          0x000000003 (3) .... Change (3) to (0)

I tried that and then restarted the computer but nothing happened. I went back into RegEdit to check after restart and those changes hadn't remained in place. They went back to the way they were previously. I'm assuming that the next step is to manually rename files somewhere but I have no clue where to do any of that. There are so many different help links to choose from and it seems like all of this information is running together. I'm not exactly sure what to do now. Sorry if I'm a little slow and causing frustration, like I said before, all of this is totally new to me and, seemingly, somewhat technical for my comprehension.

---

### Post by oldfred on 2020-08-15
Exactly what model HP Envy?

HP's have not always been the easiest to work with.

---

### Post by rt4525 on 2020-08-16
The model number is m6-p113dx.

---

### Post by oldfred on 2020-08-16
This user had to use a lot of boot parameters.

pci=noearly acpi_no_static_ssdt acpi_sleep=nonvs amd_immu=force_isolation
[https://forums.linuxmint.com/viewtopic.php?t=268675](https://forums.linuxmint.com/viewtopic.php?t=268675)

Are your UEFI menu screens similar to this?
[https://ubuntuforums.org/showthread.php?t=2448563&p=13979237#post13979237](https://ubuntuforums.org/showthread.php?t=2448563&p=13979237#post13979237)

---

### Post by rt4525 on 2020-08-16
Here are some pictures of what my screen looks like.

---

### Post by oldfred on 2020-08-16
On first screen I would change hot key delay to 3 sec or so, just to have time to press key.
Then what is under the OS Boot Manager, the > means there is a sub menu.

And then what are boot options? On second screen?

---

### Post by rt4525 on 2020-08-16
When I press enter to pull up the sub menu, the only thing that comes up is a blue strip that says "Windows Boot Manager (HGST HTS541010A9E680)". There is no actual sub menu that comes up. Then I have to press esc for that to go away.

---

### Post by rt4525 on 2020-08-16
Sorry, also, the first attached picture is the Boot Options screen.

---

### Post by oldfred on 2020-08-16
On system configuration tab, what are boot options?

---

### Post by rt4525 on 2020-08-16
Here's a picture

---

### Post by oldfred on 2020-08-16
Did you try the boot parameters the other user with your model had to use?

---

### Post by rt4525 on 2020-08-18
Yes, and it finally worked. The only thing I had to do was to use the parameters:

[FONT=Lucida Grande, Trebuchet MS, Verdana, Helvetica, Arial, sans-serif][COLOR=#333333]pci=noearly acpi_no_static_ssdt acpi_sleep=nonvs amd_immu=force_isolation
[/COLOR][/FONT]
I ended up having to do the install twice though, because I took out the USB after the install was finished (so I thought), but prior to restarting the computer. A screen came up displaying many errors. I had to power down and restart the entire installation. The second time, I left the USB in until I restarted. When it was time to restart, I was prompted to remove the USB and then the installation was complete. Thank you for all of your time and help. I really appreciate it.:p

---

### Post by oldfred on 2020-08-18
Please change to solved so others can find this thread. 
Perhaps add HP Envy to title also.

---

### Post by rt4525 on 2020-08-19
Sorry for the trouble, but I can&#8217;t figure out how to change the title so I can add HP Envy. I have marked as [Solved] though. How can I change the title?

---

### Post by oldfred on 2020-08-19
When on first post, you should be able to edit title.
But I just added it.

---

