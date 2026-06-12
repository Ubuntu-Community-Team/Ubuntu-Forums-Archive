---
title: "natty minimal install, starts to load then black screen"
date: 2011-08-27
forum: Installation &amp; Upgrades
---

### Post by blackone86 on 2011-08-27
So this is my second day trying to install ubuntu on my new hd. Despite the issues with my local isp and having to install using the minimal method it has been installed, well kinda. I follwed the steps and went through the minimal installation process for 11.04. Once i finished the installation it did the reboot and u see a purple box saying ubuntu 11.04 with the loading circles for a brief second and then it goes to the notorious black screen with cursor in the top left? 

theres so many topics on this issue i dont know where to start 1st

thanks

---

### Post by blackone86 on 2011-08-27
sorry for the lack of punctuation, sleep deprived!

---

### Post by jerrrys on 2011-08-27
try

Ctrl + Alt + F2

---

### Post by blackone86 on 2011-08-27
that got me to login and password so i entered that info in and got something else. 

welcome to ubuntu 11.04.....

to run command as admin (user "root), use "sudo <command>, see "man sudo_root for details

---

### Post by jerrrys on 2011-08-27
ok, your in.  now what exactly do you want to install?  a minimum build? a gnome only build? a full ubuntu install?

let me know and we can figure out the next step.

---

### Post by blackone86 on 2011-08-27
full ubuntu, this is going to be my only os on this pc. im trying to learn as much as i can as fast as i can, lol. i refuse to use windows.

ur being a great help, thank you

---

### Post by blackone86 on 2011-08-27
full ubuntu, this is going to be my only os on this pc. im trying to learn as much as i can as fast as i can, lol. i refuse to use windows.

ur being a great help, thank you

---

### Post by jerrrys on 2011-08-27
sudo apt-get update

sudo apt-get upgrade

sudo apt-get gnome-desktop

sudo reboot

this is the same as using the live cd install.

you have some 600MB to download,  so its going to take some time

[http://packages.ubuntu.com/natty/ubuntu-desktop](http://packages.ubuntu.com/natty/ubuntu-desktop)

---

### Post by blackone86 on 2011-08-27
update worked, uprgrade didnt do much but said done at the end. gnome desktop said error invalid

---

### Post by jerrrys on 2011-08-27
i took for granite that you know to enter each sudo command one at a time, sorry

---

### Post by jerrrys on 2011-08-27
hold on a second, i goof

sudo apt-get gnome desktop  should of been

sudo apt-get ubuntu-desktop  

sorry

---

### Post by blackone86 on 2011-08-27
i did enter them all one at a time and when i got to the gnome-desktop it says E: invalid operation gnome-desktop

---

### Post by jerrrys on 2011-08-27
yes forget entering the gnome-desktop, that was wrong.

replace that command with

sudo apt-get ubuntu-desktop

---

### Post by jerrrys on 2011-08-27
just to be sure you understand

sudo apt-get update

sudo apt-get upgrade

sudo apt-get ubuntu-desktop

sudo reboot

---

### Post by blackone86 on 2011-08-27
Ya I entered them individually hit enter and let them do there thing. After all are complete reboot the system. I had to run out for a bit but will enter the ubuntu-desktop when I get back and let u know how it goes. 

Thanks a ton!

---

### Post by jerrrys on 2011-08-27
and in the meantime, im going to watch New England get there butt's kicked...

---

### Post by blackone86 on 2011-08-28
After entering ubuntu-desktop and it still showing an error I Googled it. Supposed to be 
sudo apt-get install ubuntu-desktop. And now I wait for the 600mb to finish doing its thing.

---

### Post by jerrrys on 2011-08-28
> **blackone86 said:**
> After entering ubuntu-desktop and it still showing an error I Googled it. Supposed to be 
sudo apt-get install ubuntu-desktop. And now I wait for the 600mb to finish doing its thing.

yes, you are 100% right;  guess i can't watch a game and type at the same time.  my apologies, i wont try that again.

so is it working?  there's no game on now, i should be able it give you any other intelligent  answers you need without screwing up :oops:

---

### Post by blackone86 on 2011-08-28
No worries. Yes it is up and running seems to be working fine so far. Only one problem with the internet. Im running it wired right now went through the entire troubleshooting guide and still cant figure it out. It shows my wireless connection but, when i try to enter in the password for the asc11/ hex key it wont let me click the connect button? only the cancel button. I believe I have the sky2 driver, im running a sony vaio laptop.

---

### Post by jerrrys on 2011-08-28
could be drivers out there?  whats the model?

---

### Post by jerrrys on 2011-08-28
another thought:

open a terminal and enter

lshw

and post the results

---

### Post by blackone86 on 2011-08-28
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

wandered off for a while... now that mostly everything is working, ive been playing around. Had a little scare though with the cairo dock. i reset everything and ill worry about figuring that out later, lol

---

### Post by jerrrys on 2011-08-28
looks like your graphics will work ok on generic drivers, but there are other drivers to upgrade to later for 2/3D. 

a ethernet search 

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=marvell+PCI-E+Fast+Ethernet+Controller&sa=Search&cof=FORID:9#836](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=marvell+PCI-E+Fast+Ethernet+Controller&sa=Search&cof=FORID:9#836)

found this

[http://www.ubuntu.com/certification/catalog/component/pci:4354:11AB-NETWORK](http://www.ubuntu.com/certification/catalog/component/pci:4354:11AB-NETWORK)

---

### Post by blackone86 on 2011-08-29
I think it may be something with the settings etc. I can connect via ethernet cable fine its the wireless thats being stubborn. I have networking and wireless enabled and can see my network. If i click the network it acts like its trying to connect and then after a few seconds asks for the password and gives me 4 options. 1. 128 bit passphrase, i enter password we created and doesnt work. 2.WEP 40/128bit key(Hex or ASC11) i can enter the password but hitting enter/or the connect button doesnt work. 3. Leap 4. Dynamic wep    Besides the hex or asc11 option they all start to connect and then come back asking for authentication.

---

### Post by papibe on 2011-08-29
Just FYI, I almost sure that the original reason for the first black screen is a bug ([Bug #831752]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/831752")).

Regards.

---

### Post by blackone86 on 2011-08-30
[QUOTE=jerrrys;11194317]

sudo apt-get update

sudo apt-get upgrade

sudo apt-get install ubuntu-desktop

sudo reboot

this worked for the black screen and now im good to go. I also fixed the wireless problem. It wasnt really a problem just a goof on my part, entering the wrong info.

---

### Post by jerrrys on 2011-08-30
congratulations and  enjoy :)

---

### Post by blackone86 on 2011-10-04
Ive been using forums for help and to give help for many of years. This is probably the most helpful information that i have ever received, in that you took your time and applied effort into helping someone, as opposed to sending a 1 phrase statement leaving the person searching for translation. 

Thank You, Jerrrys for your help!

---

