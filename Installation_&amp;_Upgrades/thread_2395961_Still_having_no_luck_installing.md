---
title: "Still having no luck installing"
date: 2018-07-09
forum: Installation &amp; Upgrades
---

### Post by dirigible on 2018-07-09
Over the past few days I've made several attempts to install Kubuntu 18.04 64bit and still havent succeeded.  My PC has 3 drives and there are a couple of partitions I've been using over the years to audition newer KDE versions.  Kubuntu won't install this time.  

At first I thought it was because I had been trying to install from USB.  My original DVD burner hasn't been able to burn DVDs so I gave the USB image a whirl.  No success.  

After replacing the DVD burner I tried again several times without success.  I was able to install LM KDE 18.2 on the same partition so I dont thing it's my hard drive.  

Because the DVD process is slower I was able to get a picture of an error message which I had ignored earlier.  

The main line says...
**[   0.000000] [Firmware Bug]: TSC_DEADLINE disabled due to Errata; please update microcode to version: 0x22 (or later)**

I remembered seeing a similar message in in the LM Driver Manager.  
There's a picture of a PCB labelled Unknown and it says'''
This device is not working.  
There's an option to install "intel-microcode (open-source) Processor microcode firmware for Intel CPUs.  

I have no idea what the device is that aparently not working so I have always ignored the issue.  If it aint broke, don't fix.  

Is this likely to be the same problem?  

How should I proceed?

---

### Post by dinkidonk on 2018-07-09
> **dirigible said:**
> My PC has 3 drives

If that is all the hardware in your computer, that's probably the issue! :twisted:

The bug you are experiencing must be corrected with either a BIOS update or a manual installation/update of the microcode. The microcode is the layer between the CPU and the kernel, since I do not know which CPU you have it's hard to help any further. For intel the command is usually "sudo apt install intel-microcode" or "sudo apt install intel-ucode" and for AMD it should be "sudo apt install linux-firmware".

---

### Post by dirigible on 2018-07-11
Thanks, 

Apart from the three drives, this PC also has an Intel(R) Core(TM) i7-4770 CPU @ 3.40GHz 

So I need to use

sudo apt install intel-microcode
**or**
sudo apt install intel-ucode

Do these commands yield different results? 
If so, how do I choose?

---

### Post by dinkidonk on 2018-07-11
"u" ( or "µ") is the symbol for "micro", so.. Please look at these links:

[https://wiki.debian.org/Microcode](https://wiki.debian.org/Microcode)
[https://askubuntu.com/questions/545925/how-to-update-intel-microcode-properly](https://askubuntu.com/questions/545925/how-to-update-intel-microcode-properly)

Or search for "ubuntu intel update microcode" :)

---

### Post by jeremy31 on 2018-07-11
Try installing Kubuntu without an internet connection, some people have had installs fail lately when trying to install updates while installing

---

### Post by lostmoonofsaturn on 2018-07-11
Believe those microcode updates are loaded on each boot. i.e., not burned permanently into the chip.  Try installing the update in Live Mode and then doing to the install. (sudo won't ask for a password in Live Mode.)  Perhaps that will allow a successful install. Be sure to install the microcode updates to the installed system, if you can reboot into it.

How you go about updating the BIOS depends on your hardware and its brand of BIOS.

---

### Post by jeremy31 on 2018-07-11
At some point in the 4.15 kernels they made the microcode a dependency of the kernel install so it is automatically installed

---

### Post by oldfred on 2018-07-11
All systems need UEFI/BIOS updates for Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching.     
Both Windows & Linux have updated kernels for these.
(But they keep finding new variants so further updates may also be required).

---

### Post by dirigible on 2018-07-12
Thank you all for the information and advice!

I started by issuing 
sudo apt install intel-microcode
in LM 18.2.  
That unknown device I mentioned earlier is apparently working now.  
I still have no idea what it is but now at least the Driver Manager says it's working.  

More importantly though, I tried what lostmoonofsaturn suggested and issued the same command in live mode before installing.  
This time the install worked nicely and Kubuntu booted as expected.  
After a long update I installed my favorite software and settings.  
I've got to say I'm very impressed with Kubuntu 18.04
It's very slick and polished (and my windows still wobble too :D), definitely my new daily driver.  
Next step will be to install it again on sdb which is a ssd so it can really fly.  

Thanks again!

---

