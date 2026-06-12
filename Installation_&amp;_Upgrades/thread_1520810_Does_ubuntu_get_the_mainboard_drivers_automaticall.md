---
title: "Does ubuntu get the mainboard drivers automatically?"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by greenpanner on 2010-06-30
Hi. I'm trying to get my motherboard to boot without EDID checksum "error" messages every time I boot up.

I think it is simply the ASUS K8N-E board I'm using is not completely configured with the ATI video card.(?)

I am having no real issues with my new install of LUCID LYNX but I am not familiar with all of the Ubuntu settings and stuff. 

I got my Radeon 9600XT working well with the right drivers the other day. I am not sure if I can better the performance from there or not(I think its possible but I don't know where to look). I noticed after I tried to enable KMS and was instructed to input a line in a file that I can't remember exactly. The thing is, my monitor is allowing the resolution I want but I can't access the monitor's On screen menu because of some new setting I changed. I don't know which one did it but it was after I tried to enable KMS. I really wish I could recall what I changed but all I can do is ask somebody else where to begin looking. I did the grub update thing and cheched to see if the KMS was loading and it is the EDID errors...not loading is my guess.(I just found the KMS instructions and found the right place to look but I don't know what to do...I will try to disable KMS then see what that does in a couple minutes.)

To check if KMS is loaded I used:

 dmesg | grep drm

The Small issue that is not important but still seems odd: The monitor usually has an led lit above the Brightness control and I'm able to use the OSD but now it is lighting up the four middle leds above the screen positioning controls...I don't expect you to fully get the picture but its just a 17inch crt monitor with basic menu controls and buttons. Anyway it seems the KMS is telling the monitor what to do so I can't adjust the actual screen menu on the monitor. I am not anywhere near sure if the KMS is what is actually causing this but that's why I'm asking here.

SO, my questions in a nutshell are...

Can I disable KMS without losing the Resolution I have?

How do I get the EDID checksum on boot up to stop giving an ERROR message? 

And also when I do:
dmesg | grep drmDo I need to update my BIOS? If so, What are the usual steps to do it? Through BIOS update file or through ubuntu somewhere?

Does UBUNTU auto configure my motherboard drivers at all when I install it?
Should I enable Plug n Play OS to let the OS configure the hardware?

Is this a good place to ask?

I'm not in a hurry but anything related to my thread is welcomed. TIA...

---

### Post by dino99 on 2010-06-30
some thinking:

- if things works, why doing changes ?
- about bios config: see asustek faq
- in the linux world, kernels deals with drivers directly (see: system admin hardware driver for activation)
- all the packages you need can be found into synaptic

[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

---

### Post by greenpanner on 2010-06-30
Thanks for th reply. I don't show anything in Hardware drivers. What is the difference between Plug n Play OS and Bios hardware configuration. Is Ubuntu a PnP OS? 

I know the its fine the way it is but I'm always trying to figure out what does what...especially if I think its more efficient.

Should KMS on ATI hardware be enabled? If so what is it doing?

Any related comments welcomed...thanks.

---

