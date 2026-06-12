---
title: "Issues installing via USB bootable drive on MacBook PRO 5,3"
date: 2015-02-12
forum: Installation &amp; Upgrades
---

### Post by bill76 on 2015-02-12
Hello all. I apologize upfront if this has been covered before. However I have combed through forum after forum and countless how to's on installing Ubuntu via USB thumb drive.

10.6.8
system: MacBook Pro 5,3
2.66 ghz Intel C2D
4GB DDR3 1067 Mhz

I install rEFit (I didn't realize that I could get rEFInd at the time) and I can reboot and I get the rEFit boot menu.

I started out with downloading the ISO of Ubuntu 14.04.1-desktop-amd64 and converting for boot using the methods described for USB Ubuntu bootable drive. It is a success and I unmount and restart.

I get to the rEFIt menu and I have 4 choices to boot to.
1. Mac OS
2. EFI\boot\bootx64.efi
3. EFI\boot\grubx64.efi
4. Boot Legacy OS from HD (I believe this to the be the partion I have already set for Ubuntu installation.
5. Boot Ubuntu 14.04 (my USB.) 

On options 2 & 3 I am presented with: 
1. Try Ubuntu
2. Install Ubuntu
3. OEM Install
4. Check Disk Status

I have tried both options 1 and 2 on options 2 & 3 each time it freezes at a distorted graphic I cant even make out (I assume its the Ubuntu logo I can see blotches of a red animation representing the loading process...) if I let it sit there it will eventually freeze. I have pressed F6 and it takes me to a spitout of systemcheck and it usually freezes at the bottom around sound check OK.

When I choose option 5 USB (boot Ubuntu) it goes to a black screen flickers a couple of times (looks like its about to switch to a loading screen) then displays Non-system disk Press any key to reboot. I have to end up power cycling as its unresponsive.

I have even tried using rufus 1.4.12 (ISO USB boot/loader, Windows application) to create the bootable USB and I receive the same error.

Is it possible that I need to delete rEFit and attempt to let USB auto boot? 

I have even tried pressing Option while restarting to get Apple boot chooser and I am presented with the same bootx64 and grubx64 options and the same options within.

I am however able to choose Terminal, Command line and change boot parameters on the bootx64 and grubx64 however its presented in a form that I am not familiar with.

Surely I can install 14.04? I have had no issues installing XP via bootcamp in the past it always worked. I have also had no issues running Ubuntu 12 via VMware. 

Would a bad video driver cause the Try Ubuntu OS loading to freeze? It's just not . I have tried Koroa 20 (Cinnamon) and I run into the same issues. I have read forums and posts where others with the same build as I had no issues installing or were able to get Ubuntu to install eventually.

Anyone point me in the right direction? I really want to run Ubuntu as a dedicated OS and not via a virtual machine. And as much as I love my MAC...I am not happy with where Apple is going with its OS. 



I have tried DVD as well and get the same errors and often times DVD wont even read at all (I think my superdrive is failing). As far as superdrive other aspects of machione run great.

---

### Post by Bucky Ball on 2015-02-12
When you get to the 'Try Ubuntu' options screen, hit F6. You should get a pop-up list. Choose 'nomodeset' and proceed. Any different?

---

### Post by bill76 on 2015-02-12
I know what screen you are taking about. But unfortunately when it gets to the screen the logo is stretched beyond recognition and can only be recognized by blotches of red animation. Pressing F6 just goes to a black screen showing hardware check passing OK or fail. I don't even get the usual menu where nomodeset resides or F2 - F5 options.

---

