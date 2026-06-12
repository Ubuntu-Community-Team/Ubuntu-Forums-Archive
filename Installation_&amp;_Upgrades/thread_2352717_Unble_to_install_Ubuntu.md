---
title: "Unble to install Ubuntu"
date: 2017-02-15
forum: Installation &amp; Upgrades
---

### Post by sumanto2 on 2017-02-15
Unble to [COLOR=#ff0000]install[/COLOR] Ubuntu on Motherboard-Gigabyte GA-Z270M-D3H, Processor-intel core i5 6500, RAM-Corsair DDR4 2400MHz (1x8GB and 1x16GB total-24GB), HDD-Samsung SSD 750 EVO (250GB).
Tried both version of Ubuntu 14.04 LTS and Ubuntu 16.04 LTS but [COLOR=#ff0000]failed[/COLOR].
Please help me.:confused:

---

### Post by howefield on 2017-02-15
Perhaps you could describe how the installations failed ?

Give others something to work with.

---

### Post by sumanto2 on 2017-02-15
Tried to install from both usb pen drive and dvd. After booting from pen drive/dvd it showed the menu but after choosing Ubuntu screen becomes black and nothing no response. I've installed Ubuntu from those pen drive/dvd on other machines with different configurations where they worked but in this one it in not working, please help me and thanks for quick response.

---

### Post by howefield on 2017-02-15
I'd first try using the nomodeset option.

During boot up of the Live media, pressing F6 should give you a menu from which nomodeset can be selected.

What graphics card are you using ?

---

### Post by sumanto2 on 2017-02-15
[COLOR=#000000]No extra graphics card in installed.[/COLOR][SIZE=2]

I'm using [COLOR=#000000] Motherboard-Gigabyte GA-Z270M-D3H and using single monitor connected to the inbuilt graphics port in the motherboard. I don't have much knowledge about hardware. The link to the motherboard is [/COLOR][/SIZE]http://www.gigabyte.us/Motherboard/GA-Z270M-D3H-rev-10#kf [SIZE=2][COLOR=#000000]

I'm sending some images what is happening.
Please check them[/COLOR][/SIZE]

---

### Post by termibuntu on 2017-02-15
It seems it is a acpi pcc problem, which is a hardware defect. i dont know how to fix it but replacing that specific hardware might work . You may also be able to install it disregarding that error, such as i got an error saying 'memory corrupt at (some numbers)' which i think is about the ram, but then, i could install it. if it is something mandatory needed for ubuntu to run, then you could replace the hardware. If any other OS would run, then ubuntu would too. hope this helps.

---

### Post by sumanto2 on 2017-02-15
One other OS is running perfectly, but Ubuntu 14.04 or 16.04 is not installing at all.
The installation process of Ubuntu is stopping abruptly, giving me no scope to install it.

---

### Post by termibuntu on 2017-02-15
what is the os that it runs perfectly? if its windows then the error shouldnt be there. because of how much power windows wants.

---

### Post by sumanto2 on 2017-02-15
Windows 10 is running perfectly.

---

### Post by termibuntu on 2017-02-15
If windows runs perfectly, then it could be that ubuntu is incompatible with your acpi pcc or its defective. Does ubuntu even need one?

---

### Post by oldfred on 2017-02-15
Do not use 14.04, and you may do better with 16.10 or even the not yet released 17.04 (daily). 
You have very new hardware. And most vendors do not directly support Linux. 
So drivers have to be developed, kernels & support software updated & tested and then included into distributions.
Older versions will not support very new hardware. And even newest may require updating some bits & pieces directly from source.

A year ago I built a Skylake system and installed 16.04 even before it was released. I was not worried as it did not have to always work as long as I could boot something.
But I normally have to change a lot of UEFI settings to configure system correctly.

Do you have UEFI fast boot off? 
UEFI set for AHCI for hard drive, not RAID nor IDE?

Even with Intel, the nomodeset may help. Intel has some new drivers that after install, you probably need.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by termibuntu on 2017-02-15
Hi. The error is apparently a harmless message regarding the pcc driver. You could try reinstalling ubuntu so that way, the driver can be reinstalled. I hope this finally helps! :)

---

### Post by termibuntu on 2017-02-15
> **oldfred said:**
> Do not use 14.04, and you may do better with 16.10 or even the not yet released 17.04 
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

No. Though op said he cannot enter the grub menu. In the pictures, it show exactly that! EDIT: he could get into grub, but cannot boot ubuntu. Hmm.... I wonder if the op has tried this. But i dont know if you could actually boot ubuntu if its a harmless message.

---

### Post by QIII on 2017-02-15
termibuntu -- Please observe that in the images provided by the OP, "GNU GRUB" appears in the upper right.

sumanto2 -- forgive me if I missed it, but have you attempted "Try Ubuntu without installing"?

---

### Post by termibuntu on 2017-02-16
Yes it does appear, i should have worded it by saying that he got to the grub menu but got the message 'acpi pcc probe failed', of which i meant he couldnt boot into ubuntu. And yes. What i said about reinstalling ubuntu, i forgot to mention the try ubuntu option. Sorry if i worded things a bit wrongly.

---

### Post by sumanto2 on 2017-02-17
Thank you all for your valuable responses.


Sorry for my late response for your queries.


I installed Nvidia GeForce GT 710 graphics card in a PCI slot and bingo! Ubuntu 14.0 LTS is up and [COLOR=#006400]running[/COLOR].....


The inbuilt graphics of Gigabyte GA-Z270M-D3H is not working as it is new.


And I'm sure you all Genius will develop the driver soon.


Thanks again all of you for the prompt suggestions.=d>

---

### Post by oldfred on 2017-02-17
I installed this for my Skylake. And now it says I may be missing a Kabylake driver (which is not a correct warning).

 Intel Driver updates
[https://ubuntuforums.org/showthread.php?t=2342137&p=13565767#post13565767](https://ubuntuforums.org/showthread.php?t=2342137&p=13565767#post13565767)
Updates often needed for Skylake or Kabylake
[https://01.org/linuxgraphics/intel-linux-graphics-firmwares](https://01.org/linuxgraphics/intel-linux-graphics-firmwares)

---

