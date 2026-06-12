---
title: "Dell Optiplex Ubuntu 20.04 Post Install Issues"
date: 2020-06-20
forum: Installation &amp; Upgrades
---

### Post by JWB47 on 2020-06-20
I am extremely frustrated right now with the installation of first 18.04.04 LTS and then 20.04 LTS on this Dell PC.

Here is the configuration:

OptiPlex 3070 Micro BTX          
     338-BRSV  Intel® Core™ i5-9500T (6 Cores/9MB/6T/2.2GHz to 3.7GHz/35W); supports Windows 10/Linux          
     619-AHKN  Windows 10 Pro 64bit English, French, Spanish          
     370-ADZL  8GB 1X8GB 2666MHz DDR4 Memory          
     400-BEUQ  M.2 128GB PCIe NVMe Class 35 Solid State Drive                  
     555-BDZT  Qualcomm® QCA9377 Dual-band 1x1 802.11ac Wireless with MU-MIMO + Bluetooth 4.1 with Internal Antenna                     
     555-BEYL  Qualcomm Wireless QCA9377 1x1 driver          

Here is what transpired since I received the Optiplex this past Monday.


[LIST=1]
[*]My intent is not to dual boot with Windows 10 (I know I should have ordered it with Ubuntu 18.04 installed, but I could not find that option on the Dell Canada site.) 
[*]I first tried installing 18.04.04 using a USB 2.0 stick. It did not work as it seems USB 2.0 is not supported for booting. 
[*]I then tried with a USB 3.0 stick using 18.04.4 and was able to get the filesystem onto the nvme replacing Windows 10, but I could not figure out how to get the EFI folder in the right place with the required file in place. I tried all the examples provided re-installing many times. So, I decided to go with the latest version 20.04 LTS. 
[*]After several attempts, I was able to get the OS installed properly with a single EFI partition and a single root (/) partition. 
[*]When I rebooted after the install, I was able to go into the Bios settings and locate the appropriate file for ubuntu. Saved the settings and rebooted. 
[*]The system rebooted into Ubuntu and asked for my login information. I entered the desktop and after checking the various applications installed, I was very happy and was about to get ready to do the configurations I do on a new PC. I noticed an icon for software updates, so I had them installed and then had the system reboot. 
[*]This is where it went wrong again. Instead of the login prompt that I was expecting, I got a screen with the Dell Logo at the top, a continuously spinning circle in the middle and Ubuntu at the bottom. This continued for hours before I pulled the plug, as I could find no key presses to stop the spinning. 
[/LIST]

I am stuck now, I really do not know what to do besides using the Dell restore tool to get windows back on the PC and then figure out how to start again (which I do not want to do.

Any thoughts on how I can get this installation working would be greatly appreciated.

Many thanks

John

---

### Post by paul.k.dmitriev on 2020-06-21
Hello! I have the same problem on dell optiplex 7060 (micro). But on both dell laptops all work fine

Update: if i connect to this optiplex via ssh and restart gdm3 service all work correct. Untill next reboot.

---

### Post by CelticWarrior on 2020-06-21
Please update UEFI ("BIOS") before anything else. Even new computers often need it.
Then also update the NVME drive firmware as it often correct minor issues.

---

### Post by paul.k.dmitriev on 2020-06-21
At 7060 latest fw are installed.
I changed /lib/systemd/system/gdm.service for delayed start of gdm3:

ExecStart=bash -c 'sleep "20" && /usr/sbin/gdm3'

and it seems, that problem solved.

---

### Post by JWB47 on 2020-06-21
> **paul.k.dmitriev said:**
> Hello! I have the same problem on dell optiplex 7060 (micro). But on both dell laptops all work fine

Update: if i connect to this optiplex via ssh and restart gdm3 service all work correct. Untill next reboot.

Unfortunately, I cannot ssh into the pc, as I have not had the chance to open port 22 and setup ssh correctly.

Thanks for the tip, I will keep it in mind.

John

---

### Post by JWB47 on 2020-06-21
> **CelticWarrior said:**
> Please update UEFI ("BIOS") before anything else. Even new computers often need it.
Then also update the NVME drive firmware as it often correct minor issues.

The BIOS is at the current version 1.3.1 it was updated 20200616T081644.

I haven't found where to update the NVME drive firmware, but there does not seem to be any relevant update on the Dell site.

Thanks for the suggestion.

John

---

### Post by JWB47 on 2020-06-21
> **paul.k.dmitriev said:**
> At 7060 latest fw are installed.
I changed /lib/systemd/system/gdm.service for delayed start of gdm3:

ExecStart=bash -c 'sleep "20" && /usr/sbin/gdm3'

and it seems, that problem solved.

Thanks, I will keep this in mind for when I get access again.

John

---

### Post by JWB47 on 2020-06-21
> **paul.k.dmitriev said:**
> Hello! I have the same problem on dell optiplex 7060 (micro). But on both dell laptops all work fine

Update: if i connect to this optiplex via ssh and restart gdm3 service all work correct. Untill next reboot.

Paul:

Are you implying you had configured ssh access before you rebooted for the first time? 

If not, how did you manage to get to the desktop or a shell prompt?

Thanks for the help.

John

---

### Post by paul.k.dmitriev on 2020-06-22
> **JWB47 said:**
> Paul:

Are you implying you had configured ssh access before you rebooted for the first time? 

If not, how did you manage to get to the desktop or a shell prompt?

Thanks for the help.

John

Hello!
I tried two variants. The first one - enable ssh after install. In some cases it boot Ok and i can login.
The second way - after installing ubuntu, when installer prompts to reboot you may switch console (ex. Ctrl+Alt+F3) and edit this file in /target/lib/systemd/......

Also you can boot from live-cd and edit this or install ssh via chroot

---

### Post by JWB47 on 2020-06-22
> **paul.k.dmitriev said:**
> Hello!
I tried two variants. The first one - enable ssh after install. In some cases it boot Ok and i can login.
The second way - after installing ubuntu, when installer prompts to reboot you may switch console (ex. Ctrl+Alt+F3) and edit this file in /target/lib/systemd/......

Also you can boot from live-cd and edit this or install ssh via chroot

Ok, many thanks. 

I was able to finally get to the login prompt by trying the reboot, power-off, boot again and repeat method. I installed ssh and updated the firewall rules, so I am now logged in directly and over ssh from another pc. I will make the change to the systemd file you suggested and test.

Many thanks for your help.

John

---

