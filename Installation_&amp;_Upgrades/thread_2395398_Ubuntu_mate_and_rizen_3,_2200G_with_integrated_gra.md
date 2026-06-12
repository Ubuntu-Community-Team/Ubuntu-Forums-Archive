---
title: "Ubuntu mate and rizen 3, 2200G with integrated graphic black screen and locked, and f"
date: 2018-07-01
forum: Installation &amp; Upgrades
---

### Post by rdsparla on 2018-07-01
Hello,

                   The  installation of Ubuntu mate has been easy, then the updates too, but  then many complications arise, I have micro rizen 3 2200G with  integrated graphics, I put the following commands in the grub:  "radeon.si_support = 0 amdgpu.si_support = 1", I updated the graphic with the padoka page. And  I put the following order for errors every start is complicated,  sometimes you have to restart with the 2nd option, and again 2nd. recovery option, then hit enter. Complicated  for a person who does not handle the computer to whom I mounted this  system, rather than at the user level, in others it starts alone, after  an update I have a black screen and it is blocked. I can not enter the operating system. I want to update the kernel to 4.17, which they say: it brings improvements to the graph, but I can not enter.
I would be very grateful if someone can help me.

---

### Post by dinkidonk on 2018-07-02
Support for Raven Ridge (2200G and 2400G) is not quite there yet, try to use "nomodeset" as kernel parameter (google it) to boot the system. You will need at least Kernel 4.17.3 and MESA 18.2 for decent Raven Ridge support.

[https://askubuntu.com/questions/1007350/what-is-needed-to-use-raven-ridge-ryzen-5-2400g](https://askubuntu.com/questions/1007350/what-is-needed-to-use-raven-ridge-ryzen-5-2400g)
[https://www.phoronix.com/scan.php?page=article&item=ryzen-2400g-may&num=1](https://www.phoronix.com/scan.php?page=article&item=ryzen-2400g-may&num=1)

You can also try with the AMDGPU patched kernels from here: [https://github.com/M-Bab/linux-kernel-amdgpu-binaries](https://github.com/M-Bab/linux-kernel-amdgpu-binaries)

---

### Post by rdsparla on 2018-07-02
thinks a lot

---

### Post by kurt18947 on 2018-07-13
I just completed assembling a AsRock AB350M MoBo with Ryzen 2200G APU. I was aware of the video issues so installed an AMD HD8490 video card and pushed "Go". It started right up and everything worked including video booting an Ubuntu 18.04 live USB. I then shut down and moved the DVI monitor cable from the discrete video card to the video port on the motherboard and uninstalled the discrete video card. This time I got the POST screen then - black screen. Not even a flashing cursor. The monitor's light was the correct color to indicate a video signal but nothing. I shut down, reinstalled the discrete video card and everything worked again. I didn't try the "no modeset" switch, I may try that at some point. 

I then plugged the hard drive in which is formatted MSDOS, not GPT. I also have installed BootIt NG (a boot manager) which I didn't think there would be one chance in Hades of its working, it relies on traditional BIOS. Much to my surprise and delight, it booted right up. The CSM module in indeed compatible. I tried booting Xubuntu 16.04 and nope, black screen.  Restarted and tried booting Xubuntu 18.04 and it came right up. This was with my $8 off Ebay video card. Based on my initial impressions, Ryzen works very well with Ubuntu IF I use a not-bleeding-edge discrete video card and and Ubuntu 18.04/Kernel 4.15.xx or higher. I expect video support for Vega graphics will come but it's not there yet.

---

### Post by pitchizig2 on 2018-09-09
As of now, Raven Ridge is well supported in Ubuntu 18.04.1 on Asrock AB350M pro4 with the latest BIOS (4.90). I had to:

- Flash the MB with 4.90 BIOS.

- Update the OS kernel to Linux 4.18.0 using UKUU.

- Update MESA using Oibaff PPA.

Being uncomfortable with Gnome, I tried Mate, which was OK, but I  finally reversed to Unity which is more convenient for me. I still have a  small problem to start, it needs sometimes a couple of tries, there is  still the black screen telling it is unable to do something with IOMMU  which I don't give damn for, VBox working as a charm once virtualization  is activated in the BIOS. Once started UBUNTU is rock solid on a  machine working 24/7.

Sorry for my english.

---

### Post by salomonster on 2018-09-11
[COLOR=#000000]Hi,[/COLOR]

[COLOR=#000000]I was having the same problem, but disabling iommu on bios, updating to 4.19rc3 kernel with Ukuu and latest BIOS update for AGESA it works great. It shows some ACPI warning on boot, but no freeze at all. It boot everytime[/COLOR]

[COLOR=#000000]I hope this help you with your machine.[/COLOR]

---

### Post by rdsparla on 2019-01-14
822/5000

Hello,


The installation of Ubuntu mate has been easy, until the first update, from there many complications arise, black screen, impossible to start the operating system. I have micro rizen 3 2200G with integrated graphics, mother card assus 
 X370M Pro4. I put the following commands in the grub: "radeon.si_support = 0 amdgpu.si_support = 1", updated the graph with the padoka page. Then I changed the orders in the grub, as they indicated to me in Ubuntu Forum (I did not have answers in Ubuntu mate wiki) to: modeset amdgpu.dc = 1 acpi_osi = "Linux", each start is complicated I continue with black screen after the ubuntu icon mate, and I can not enter the operating system It stays locked. I want to update the kernel to 4.17, which they say: it brings improvements to the graph, but I can not enter.

 
I would be very grateful if someone can help me. Thank a lot.

Logs: 
 deskstop Kernel: (drm:amdgpu_init (amdgpu)) ERROR VGACON disables amdgpu kernel modesetting.
 
 
 Deskstop Kernel: ACPI: Error: (PTOS) Namespace lookup Failure . AE_NOT_FOUND (20170831/PSPARSE_364)
 
 
 Deskstop Kernel: ACPI: Error: (PTOS) Namespace lookup Failure \. AE_NOT_FOUND (20170831/PSPARSE_550)

---

### Post by dondymenelo on 2019-01-16
> **salomonster said:**
> [COLOR=#000000]Hi,[/COLOR]

[COLOR=#000000]I was having the same problem, but disabling iommu on bios, updating to 4.19rc3 kernel with Ukuu and latest BIOS update for AGESA it works great. It shows some ACPI warning on boot, but no freeze at all. It boot everytime[/COLOR]

[COLOR=#000000]I hope this help you with your machine.[/COLOR]

It works on my classmate machine we found out that iommu is not disabled then updating the rest is the trick. Thanks man!

---

