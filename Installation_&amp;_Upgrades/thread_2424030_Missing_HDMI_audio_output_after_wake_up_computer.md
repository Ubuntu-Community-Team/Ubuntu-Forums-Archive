---
title: "Missing HDMI audio output after wake up computer"
date: 2019-08-02
forum: Installation &amp; Upgrades
---

### Post by milan-matejcek on 2019-08-02
Hello,
i use Ubuntu 18.04.2 and kernel 4.15.0-55-generic i observe behavior, when i power on the notebook HDMI audio output works fine and it is vissible in settings. When I suspend computer and wake up, HDMI output missing in settings and does not work. I must restart notebook. Few weeks before works fine after wake up everithing works fine.


I asked on [nvidia forum]("https://devtalk.nvidia.com/default/topic/1058536/linux/missing-hdmi-audio-output-after-wake-up-computer/") and they recommend me let contact ubuntu kernel dev.

Here is the answer from nvidia forum
> The ACPI of notebooks turn the sound function of an nvidia gpu off on boot and resume, so the kernel has to turn it on again. Thus, this doesn't depend on any nvidia driver version but the kernel version which obviously fails to do so on resume. Please report to the Ubuntu kernel devs. A workaround would be using the nvhda module which was needed previously to do the task when the kernel wasn't turning the sound on by itself.



Thank you for response.

---

### Post by ubfan1 on 2019-08-02
Bugs should be reported at [Bugs]("https://bugs.launchpad.net/ubuntu").  You can try selecting a previous kernel when the grub screen is displayed by selcting the Advanced Options..., probably line 2, and select a previous kernel.

---

### Post by milan-matejcek on 2019-08-02
This is not possible.
I selected previsou kernel in grub menu and i cannot login, "login loop problem". I found i must run 
> sudo update-initramfs -u -k 4.15.0-54-generic and reboot
alright i login to my profile, but external monitor does not run. I remember [this]("https://devtalk.nvidia.com/default/topic/1044770/linux/hdmi-output-missing-in-xrandr-command-and-external-monitor-not-work/") set mode set 1 and 0 i try both and nothing help. External monitor does not work because hdmi is not visible.

Sorry i don't know how continue.

---

### Post by ubfan1 on 2019-08-02
Maybe I don't understand, but since you can login with the ...55 kernel and HDMI works until a suspend, create the initrd for the ...54 kernel, and reboot, selecting the ...54 kernel. Why do you need to recreate the ...54 initrd?  Did you delete it?  Wasn't it successfully running before?

---

### Post by milan-matejcek on 2019-08-05
If i boot by previous kernel ..54, then external monitor and HDMI audio does not work, black screen, no signal... I can't test it.

---

### Post by milan-matejcek on 2019-08-20
I upgrade kernel version "5.0.0-25" and now it is fixed. Nvidia driver is still same.

---

### Post by markackerman8@gmail.com on 2019-08-21
Awesome you got it fixed so fast and easily!

For others with a similar (HDMI not waking issue) ...

One 'sneaky' workaround is to tell Ubuntu to "Pause", and then Ubuntu will give you an option to pause (and NOW it will wake up with your HDMI working!

---

