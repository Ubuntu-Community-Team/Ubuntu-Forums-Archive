---
title: "I can't install Ubuntu 21.04 on Acer laptop"
date: 2021-09-22
forum: Installation &amp; Upgrades
---

### Post by networkz on 2021-09-22
Hello I've been trying to install ubuntu on my laptop and it always get the same error: [https://gyazo.com/476942f72c1e242aae299ba4e39aaa64](https://gyazo.com/476942f72c1e242aae299ba4e39aaa64)
I've read several posts and I've tried many things I've seen but it's been impossible to install, this error pops after I select ubuntu to install after selecting the boot usb.
I really need to use ubuntu for development otherwise I will have to sell this laptop and is not something I can afford tbh. Thanks in advance.
My model is: Acer Predator Helios 300 PH315-51-50Y7

---

### Post by Impavidus on 2021-09-22
Have you verified the download is correct? Calculate the hash and compare it to the official source. How did you create the live usb? Creating one without persistence is more reliable. Have you verified the live usb after creating it? Calculate the hash, not of the whole device, but only the part used by the live image, and compare it to the official source.

---

### Post by networkz on 2021-09-22
I've created a bootable usb with rufus and introduced the last .iso from the offical ubuntu website, so I think the usb shouldn't be a problem, from what I've read is something with Acer, I was expecting someone with the same problem with Acer to be able to help me out.

---

### Post by tea for one on 2021-09-22
Acer typically requires "trust" setting in UEFI setup for any UEFI boot entry other than Windows.

Can you check the UEFI setup pages to see if there is such a setting?

---

### Post by networkz on 2021-09-22
BIOS tbh have really little settings at least is what make me feel, I've changed secure boot and some other settings but still not working.

---

### Post by tea for one on 2021-09-22
Have a look at the images in this Acer thread.
Do you not have similar UEFI settings?

[https://community.acer.com/en/discussion/569360/how-can-i-disable-secure-boot-in-the-bios-settings](https://community.acer.com/en/discussion/569360/how-can-i-disable-secure-boot-in-the-bios-settings)

i.e. Select an UEFI file as trusted for executing.

---

### Post by networkz on 2021-09-22
Yes, this is my exact BIOS, I have it configured as in the thread you linked.

---

### Post by tea for one on 2021-09-23
> **networkz said:**
> BIOS tbh have really little settings at least is what make me feel, I've changed secure boot and some other settings but still not working.

The image in the acer.com thread shows that there is a setting for UEFI trust.
Have you explored that option?

I can't advise exactly how to adjust the setting because I do not have an Acer laptop.
The subject of Acer Trust is a common and recurring question in this forum and elsewhere.

---

### Post by slickymaster on 2021-09-23
*Thread moved to **Installation & Upgrades**.*

---

### Post by yancek on 2021-09-23
>  I've created a bootable usb with rufus and introduced the last .iso from  the offical ubuntu website, so I think the usb shouldn't be a problem

There's nothing wrong with the iso on the Ubuntu download site but you need to remember that the iso is being downloaded over many miles of wires to get to your computer unless you happen to live next door to one of their servers (highly unlikely).  Do the md5 checksum  or an sha checksum AFTER the download.  Not sure that is your problem but it is pretty simple to verify.

You haven't mentioned any other OS so is Ubuntu the only OS you have on this computer?

I also do not use Acer but from what I have read, you need to first set a Supervisor password in the BIOS firmware before you can set Trust for another OS.  And no, I don't know how you would do that.

Good luck.

---

### Post by networkz on 2021-09-23
Yes I've done pretty much every option in the BIOS haha, but still not working, only way from what I've seen is doing a custom BIOS but I'm not sure about that and is kinda dangerous

---

### Post by tea for one on 2021-09-23
> **networkz said:**
> Yes I've done pretty much every option in the BIOS haha, but still not working
Please elaborate which UEFI settings you have adjusted?
Possibly, you have missed a crucial setting?
> **networkz said:**
>  only way from what I've seen is doing a custom BIOS but I'm not sure about that and is kinda dangerous
What have you seen about a custom BIOS?

---

### Post by Sandgoose on 2021-09-24
with my acer laptop I had to goto advanced boot options in grub changing / add after "quiet splash" by "quiet splash nvme_core.default_ps_max_latency_us=5500" due to some issue with the configuration files not been setup correctly to work with the nvme drive, no idea if this is the issue but worth a shot

---

