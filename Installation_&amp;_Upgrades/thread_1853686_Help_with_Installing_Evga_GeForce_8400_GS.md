---
title: "Help with Installing Evga GeForce 8400 GS"
date: 2011-10-02
forum: Installation &amp; Upgrades
---

### Post by 1egoman on 2011-10-02
Hello. This is my first post, so bare with me. On my computer, I am installing a Evga GeForce 8400 GS graphic card. I installed it in the case, and then downloaded the .run file from nvidias website. Ran it, and after a while installed it. The problem is however that I have no clue how to switch from my onboard gpu to the video card. The setting in the bios reads PCIE. Anyone no how to switch from integrated to this new card?:confused:

---

### Post by MAFoElffen on 2011-10-02
> **1egoman said:**
> Hello. This is my first post, so bare with me. On my computer, I am installing a Evga GeForce 8400 GS graphic card. I installed it in the case, and then downloaded the .run file from nvidias website. Ran it, and after a while installed it. The problem is however that I have no clue how to switch from my onboard gpu to the video card. The setting in the bios reads PCIE. Anyone no how to switch from integrated to this new card?:confused:
Some BIOS autorecognize a GPU in the PCIe when you enter the BIOS Setup and sets it according.  Others still have to be set manually.  The BIOS graphics setting saying "PCIE" or "PEC" should be correct setting.  

If you knew your motherboard brand and model number, I might be able to get you the specific info for your board.

As reference to installing the .run file: Read the instructions I wrote up in this post			#[**280**]("http://ubuntuforums.org/showpost.php?p=10909540&postcount=280") of my graphics sticky.  Has all the current workarounds for installing it in Ubuntu.

---

### Post by 1egoman on 2011-10-03
> **MAFoElffen said:**
> Some BIOS autorecognize a GPU in the PCIe when you enter the BIOS Setup and sets it according.  Others still have to be set manually.  The BIOS graphics setting saying "PCIE" or "PEC" should be correct setting.  

If you knew your motherboard brand and model number, I might be able to get you the specific info for your board.

As reference to installing the .run file: Read the instructions I wrote up in this post			#[**280**]("http://ubuntuforums.org/showpost.php?p=10909540&postcount=280") of my graphics sticky.  Has all the current workarounds for installing it in Ubuntu.
The motherboard is a biostar n68s+. As far as I know, all I did to install the run file was to go into verbose mode, then press ctrl+alt+backspace. then used terminal commands to install it.

---

### Post by Frogs Hair on 2011-10-03
I have a galaxy 8400 GS and entering the bios was not required .  for my card . All I had to do is plug the card in the PCIE slot and install the driver . My on board graphics was Nvidia though .

---

### Post by 1egoman on 2011-10-04
> **Frogs Hair said:**
> I have a galaxy 8400 GS and entering the bios was not required .  for my card . All I had to do is plug the card in the PCIE slot and install the driver . My on board graphics was Nvidia though .

Did you use the Nvidia Driver from the website? And after installing the driver did you do anything to set it up? My onboard is nvidia.

---

### Post by Ms. Daisy on 2011-10-04
I had this problem.  Restart the machine and watch the text at the very beginning.  It should tell you that you press F2, F10, or Del to access setup or BIOS.  I believe each manufacturer is a bit different, so you may have to experiment.  It was F10 on my machine.  Once you get to the BIOS screen, you will look for the place to change the graphics.  I found mine through "peripheral setup".  When you're done, make sure you save your settings.  And voila! The computer ignores the on-board graphics card.

---

### Post by MAFoElffen on 2011-10-04
> **1egoman said:**
> Anyone Else? #-o
I have 2 boxes with ASUS nVidia motherboards, meaning the motherboards have GeforceX nVidia chipsets that manage the devices on the board. They are both SLI boards.  These are a little more intelgent in recognizing were the Video cards are.

I have another 3 boxes that I have nVidia on.  All three have other Integrated onboard GPU's.  2 of these I had to set the BIOS to where the graphics was located, what to use or use first.  The 3rd turns off the onboard GPU chip if another GPU is present on the bus. 

So it all depends on your motherboard.  And I can't find what your BIOS sya on that, as even Biostar doesn't have the manual in their downloads.

---

### Post by 1egoman on 2011-10-07
Never Mind. This has been too much trouble. I just returned the card and I'm going to buy an arduino. Thanks for the help!

---

### Post by MAFoElffen on 2011-10-07
> **1egoman said:**
> Never Mind. This has been too much trouble. I just returned the card and I'm going to buy an arduino. Thanks for the help!
You are going to have the same with another card on a PC...  

This "is" really a lot simpler than you are making it.  This is the short simple instructions for your nvidia card...  (for 11.04- I'll adjust these for whatever bersion you are on... You never did say)

On boot, enter Bios.  Save/Exit BiOS.

At Grub menu > press select the rescue mode > select safemode / low graphics mode.

It will boot and bring up GUI.  

Press <cntrl><t> Terminal session will popup... Run this
```
[FONT=monospace]
[/FONT]sudo apt-get update 
sudo apt-get install linux-headers-'uname -r' 
sudo apt-get remove --purge nvidia-*
sudo apt-get install nvidia-current
sudo service gdm restart

```Card and Driver Installed.

But then you said you returned it so... Good luck with your Arduino...

---

