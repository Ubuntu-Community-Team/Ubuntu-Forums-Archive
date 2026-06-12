---
title: "Live Cd Not Booting!"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by ghstwalker on 2007-11-27
I have Ubuntu on my macbook [x86 intel live-cd], and my Vaio [old live-cd] , I'm trying to get it up and running on my home PC [64-bit live-cd]. 

when i boot the x64 live-cd after the load bar the screen goes blank. checked cd for errors: NONE. 

when i use the x86 live-cd after the load bar the screen goes blank. checked cd for errors: NONE. 

when i use the old-live cd i get 
Uncrompressing Linux...Booting the Kernel
17179569.712000 ..MP-Bios Bug 825 timer not connected to IO-APIC
1719569.712000 Kernel Panick - No synching IO-APIC + Timer doesn't work BOO
with APIC =debugging and send a report then try booting with the noapic option
1719569.712000


What is going on?! 

Home PC specs
ASUS p5n32e-dulxe
intel e6600
2x geforge 7950gt sli
2GB RAM

---

### Post by Gzus666 on 2007-11-27
well, i would do what it says and load the kernel with noapic boot option. sounds like a APIC bios option is not setup right, i would go through the motherboard book and check out those options. possible that Ubuntu wants to control the options, and you have it setup so the OS cant control the APIC. im not 100% familiar with how linux runs APIC, so i hope im not leading you wrong

---

### Post by ghstwalker on 2007-11-28
thanks gzus i'll take a look at my BIOS options when i get home. Hope l can get it workin soon

---

### Post by Pumalite on 2007-11-28
Try these to start:(F6)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317

---

### Post by ghstwalker on 2007-11-28
thanks puma, i'll take a look at these while im in class tonight. Before I left I took a quick look at the BIOS. There is an APIC option under the Power setting, but it is greyed out. Hopefully there is an update for my mobo that will enable the option.

edit/ 
Took a look at the APIC architecture wiki and those sites you posted....Seems i have to disable the IOapic option By using NOAPIC and NOLAPIC... 
I'm New to Linux scripitng so this may be tough to me. Just started Linux scriptng in my class so we'll see.

Can anyone help me on how to change these settings for the boot. I can't boot so i cant use the VI in the terminal.

---

### Post by ghstwalker on 2007-11-28
With the 64bit live cd:
at boot screen i hit F6 and just typed
> noapic nolapic

everything seemed to be going ok then
> 266.521757 device no accepting adress 28, error - 71
then blank screen. 

threw in the 6.01 live cd and 
at boot screen i hit F6 and just typed
> noapic nolapic
booted perfect and fast as hell, but my screen is off center and none of my hardware is reconized...
well in the device manager its not recogonized as what it is


Now 2 new questions... how do i update to 7.10 and make that boot configuration permanent?

---

### Post by ghstwalker on 2007-11-29
OK, installed 6.06 to my drive and ubuntu boots no problem. 
Problem is the screen is offcenter and the device manager only knows the vendor and products of my hardware but the device type is unknown for all of them. the processory is completely unknown in all categories. 
how can i resolve this... i can't even get an internet connection up and running. tried IFCONFIG, but have no idea whats going on. cant post it because its on another computer

---

### Post by ghstwalker on 2007-11-29
bump...

---

### Post by Pumalite on 2007-11-29
Time to use the Alternate CD.

---

