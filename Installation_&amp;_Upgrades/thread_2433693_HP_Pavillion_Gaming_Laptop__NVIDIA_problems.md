---
title: "HP Pavillion Gaming Laptop / NVIDIA problems"
date: 2019-12-23
forum: Installation &amp; Upgrades
---

### Post by Ordes on 2019-12-23
Hi, i am trying to get my ubuntu running in my HP Pavilion 15-cx0075ng, geForce GTX1050Ti

The Main install runs fine. I have to add "nomodeset" to grub in order to not get a boot freeze.

Problems:
# my FN keys for brightness and monitor switch are not working. I tried adding "acpi_osi=" to grub. But without success 

Main Problem:
I cannot switch to my external monitor. Tried several  options. But all without success 

Tried Solutions:
1. Purge Nvidia, install ubuntu-devices autoinstall
Using: Nvidia 440 properitary
Result: None. 
> Ubunt Display settings does not recognize a second display
> Nvidia Settings Window is complete empty when opening

2. Using Community drivers > same result 

3. Install source 440 and installing
Result: horrible
After installing the source 440 drivers my internal display will not work any more. And the output will only be sent to my external monitor. I made the install while the external monitor was not connected. After my reboot. Ubuntu was loading on internal monitor. When the login screen was about to be displayed, the monitor changed to log View. When I then plug in my external monitor mylogin screen is displayed. 
First I thought this mismatched happened because I installed the drivers with the external monitor connected. But it didn't matter. I made a complete new ubuntu install, than added the source drivers without ever attaching my external monitor. But the outcome is the same.

Conclusion: 
When using 440 source. The output signal only goes to HDMI and internal is gone. 
I can revert this by purge nvidia + ubuntu-drivers autoinstall

Questions:
1. I don't know if I cannot switch to external because of a not working driver or because of a not functioning FN key.
# FN key volume is working
# FN key brightness is not

# on my previous laptops FN key and drivers were always working out of the box. Also monitor switch

2. NVIDIA drivers. 
What would be the right way to install the appropriate drivers and get them working?
Some advice 440 source, some 440 ppa. 
But for me:
440 ppa >> no nvidia settings 
440 source >> nvidia settings are displayed correctly, with GPU, temperature etc; but I have no more internal display i can use ....

---

### Post by Autodave on 2019-12-23
What 'buntu version are you running?

---

### Post by Ordes on 2019-12-23
1804-03

---

### Post by Autodave on 2019-12-23
OK...did some research.  That model has 2 GPUs in it: the nVidia and also an Intel.  The nVidia is only supposed to run when needed, otherwise the Intel runs ti save battery power.  These can sometimes be fun to get working properly and you are probably going to need the help from someone way higher on the pay scale than myself. :-)  One thing that I do know is this: can you disable the Intel GPU in the BIOS?  If you can, this will be your easiest fix.

---

### Post by CatKiller on 2019-12-23
> **Ordes said:**
> The Main install runs fine. I have to add "nomodeset" to grub in order to not get a boot freeze.

Don't do this.

Pretty much all your other difficulties stem from this. By setting that option you are specifically saying that you don't want any resolutions set - not the main display, not any additional displays. Which is exactly what you're seeing.

There *is* a reason to **temporarily** use that option. The nouveau open source driver is not very good at automatically detecting resolutions. During the install process and first boot that's the driver that will be in use, and the symptom of it not being able to find the correct resolution is that you get a black screen or a black screen with a flashing cursor. Using nomodeset for those two boots *only* lets you boot at whatever resolution the BIOS sets to get the job done. After the first boot you can install the proprietary driver and you won't need that option any more.

Using it wrecks the ability of any driver - nvidia, intel, or amd - to detect and set the resolution of the displays.

---

### Post by Ordes on 2019-12-23
Txs for the advise. 

The explanation about the "nomodeset" makes sense. I will try tomorrow and let you know how it worked out. 
So basically, 
#1 set it temporarily for the first boot. Otherwise I am not able load into ubuntu
#2 install the proprietary drivers 
# hopefully ubuntu will then load correctly without nomodeset

> I will also check for for the GPU settings in bios

---

### Post by CatKiller on 2019-12-23
> **Ordes said:**
> So basically, 
#1 set it temporarily for the first boot. Otherwise I am not able load into ubuntu
#2 install the proprietary drivers 
# hopefully ubuntu will then load correctly without nomodeset

That's it. 

Optimus setups - which is what you've got - are a pain. When they first started pairing Nvidia with Intel Nvidia's attitude was that it simply wasn't intended to work in Linux at all. The community came up with Bumblebee, which was kind of rough. Recently Nvidia have started the groundwork for making it work properly with Prime, which is still kind of rough. Either way you'll need the proprietary driver installed to use the Nvidia part. Don't be tempted to use the .run file from Nvidia's website.

---

### Post by Ordes on 2019-12-23
@CatKiller,

TXS for your adivse. Everything now worked out of the box like a charm.
"nomodeset" was the cause of all the problems. It was a pitty that my first tutorials about dealing with the boot up freeze, all advised to also add "nomodeset" to the grub permanently. I should have thought more about this, instead of just doing. But your post made it clear to me.

Anyhow.....
for those experience the same problems: 
Here is the comprehension:
1. add "nomodeset" temporarily on boot
2. $ add-apt-repository ppa:graphics-drivers
3. get recommended driver by system: $ ubuntu-drivers autoinstall
4. check for right driver in "software&update"
4. run update & upgrade
5. reboot

---

