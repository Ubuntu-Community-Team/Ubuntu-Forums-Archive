---
title: "Installing Drivers"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by Matt_Johnson on 2010-05-17
I have a MSI N9600GT graphics card and I can't find the drivers I tried running hardware drivers and it was only showing the onboard graphics card and not the PCI-E card. Can someone help me locate drivers for this.

---

### Post by oldfred on 2010-05-17
Do you in BIOS have to turn off the on board graphics?

My install came up in about 30 sec and asked if I wanted to install the nvidia driver? I only have a 9600GT.

On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.

---

### Post by cascade9 on 2010-05-17
If yuo cant disable the onboard graphics in the BIOS, you might have to blacklist the onbaord video card.

---

### Post by Matt_Johnson on 2010-05-17
usually when you install a new graphics card driver it will set it as default and disable the onboard. I can't find any drivers for my card tho :(

---

### Post by cryptotheslow on 2010-05-17
If the card is being seen by the OS then the NVidia drivers should be available in the Hardware Drivers menu.

Very slightly newer drivers are available for download here: [www.**nvidia**.com/page/**drivers**.html ]("http://www.nvidia.com/page/drivers.html")although manually installing that way will mean you will have to reinstall them manually with every kernel update - so keep the install file somewhere handy.

Can you post up the results of the lspci command run in a Terminal?
[]("http://www.nvidia.com/page/drivers.html")

---

### Post by oldfred on 2010-05-17
You should also find the driver in synaptic.  

Installing the drivers from nvidia site adds complications, I would only do that as a last resort. And once installed may create conflicts with the downloadable one.

---

### Post by Matt_Johnson on 2010-05-17
> **cryptotheslow said:**
> 
Can you post up the results of the lspci command run in a Terminal?


How would I go about doing that?

---

### Post by Matt_Johnson on 2010-05-17
When i run the hardware drivers program says

NVIDIA accelerated graphics driver (verison 173)

NVIDIA accelerated graphics driver (verison 96)

NVIDIA accelerated graphics driver ( Verison current ) [Recommended]

I tried running each one of these and it made the computer slower or it messed it up completely

it doesn't seem like its any of these

---

### Post by oldfred on 2010-05-17
If you installed all three they are probably getting in the way of each other. You should completely remove all 3 and just reinstall the recommended one.

---

### Post by Matt_Johnson on 2010-05-19
> **oldfred said:**
> If you installed all three they are probably getting in the way of each other. You should completely remove all 3 and just reinstall the recommended one.
  nooo I used one at a time but the problem is that none of those are the gfx card i have in the pcie slot lol

---

### Post by Matt_Johnson on 2010-05-20
I fixed it by using the hardware driver tool + updating packages thanks :)

---

### Post by Matt_Johnson on 2010-05-21
I keep getting errors everytime I restart saying nvidia x server failed or something then says boot in low graphics mode!

---

