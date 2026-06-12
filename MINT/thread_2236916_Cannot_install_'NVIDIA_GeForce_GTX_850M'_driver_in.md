---
title: "Cannot install 'NVIDIA GeForce GTX 850M' driver in Linux Mint 17 MATE"
date: 2014-07-29
forum: MINT
---

### Post by Rytron on 2014-07-29
Hi.

I can't install drivers for the 'NVIDIA GeForce GTX 850M' graphics card in Linux Mint 17 MATE.

Does my new laptop have both an Intel & NVIDIA GPU?

How can I install the Nouveau drivers only? Is the Intel GPU using the Nouveau drivers? I went to 'Driver Manager' and it's blank with the message something like 'No propriety drivers being used'.

It's my secondary PC so I won't be using it for heavy gaming. I'd rather wait for the drivers to become available in 'Driver Manager'.

---

### Post by westie457 on 2014-07-29
What does ```
lshw -C display
``` tell us?

---

### Post by Rytron on 2014-07-30
Hi westie457.

Please excuse my delay in replying.

#Output for your command:
```
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: 3D controller
       product: GM107M [GeForce GTX 850M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
  *-display
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:48 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```

I also ran this:
```
lspci | grep -E "VGA|3D"
```

```
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 850M] (rev a2)
```

---

### Post by westie457 on 2014-07-30
Well the first idea has been blown out of the water. The device is enabled in the BIOS otherwise it would not show in either of the commands.

Suggest you use Synaptic Package Manager to install the Nvidia drivers starting with 'nouveau'.
You might have to enable all Software Sources except for the 'Source Code' to get them to show.
After that 'Additional Drivers' should offer you the correct one for your card.

I am not using LinuxMint at all so the info might not be 100% correct but is a pointer in the right direction.

---

### Post by Rytron on 2014-07-31
> **westie457 said:**
> Well the first idea has been blown out of the water. The device is enabled in the BIOS otherwise it would not show in either of the commands.

Suggest you use Synaptic Package Manager to install the Nvidia drivers starting with 'nouveau'.
You might have to enable all Software Sources except for the 'Source Code' to get them to show.
After that 'Additional Drivers' should offer you the correct one for your card.

I am not using LinuxMint at all so the info might not be 100% correct but is a pointer in the right direction.

Hi westie457.

I'd settle for Nouveau for the time-being. Perhaps I'd need Bumblebee to get proper NVIDIA Optimus support? I'll try your method.

Cheers.

---

### Post by kc1di on 2014-07-31
Hi according to Nvidia you should use the 337 driver - which you can download from [here.]("http://www.nvidia.com/download/driverResults.aspx/74888/en-us")
or as mentioned above Mint has a very good driver manager and you could try what it offers you there. 

Just curious why you did not seek advice from the mint forums as they have a very good forum also :)

---

### Post by Rytron on 2014-07-31
> **kc1di said:**
> Hi according to Nvidia you should use the 337 driver - which you can download from [here.]("http://www.nvidia.com/download/driverResults.aspx/74888/en-us")
or as mentioned above Mint has a very good driver manager and you could try what it offers you there. 

Just curious why you did not seek advice from the mint forums as they have a very good forum also :)

Hi kc1di.

Thanks for the info.
I usually use the Linux Mint forums but thought I'd give this forum a try as it has far more users and I wanted to try out the 'Other OS/Distro Support' section.

Cheers.

---

### Post by kc1di on 2014-07-31
Very good hope you find a fix for the card :)

---

### Post by Rytron on 2014-08-02
Am I currently using an onboard graphics card, that is IGP (Integrated Graphics Processor)? Do all/most computers have integrated graphics?

I installed these so far: bumblebee, nouveau-firmware, nvidia-settings &#8211; and ran glxgears and the graphic runs fine. In Driver Manager, it is still blank though and it says 'no propriety drivers are in use'.

---

### Post by mrfreen on 2014-08-07
I think that's actually the heart of the problem; the IGP is being used and apparently it's not possible to switch.
Looking at your hardware, we might have exactly the same system. I really hope this can be solved, and that I haven't just blown money on a notebook with a useless nvidia card.

Does anyone know a way to switch between cards?

---

### Post by alex284 on 2014-11-03
I would like to know if anyone else is also having this problem. Apparently I downloaded and installed the graphics card from the Ubuntu Software Center. Driver 340.46 is the one the software center offered me. I want to know how I can run the graphics card as my VGA Controller.

---

### Post by coffeecat on 2014-11-06
@alex284, please start your own thread in one of the main support areas. Since you mention the Ubuntu Software Centre I very much doubt you are using Linux Mint.

---

