---
title: "Problem with Ubuntu 8.10 and DVI"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by kbloem on 2008-11-08
Hello,

i've got a problem with Ubuntu 8.10. When i install it my screen gets messed up. I'm seeing a lot of scrambled images. It happens when i'm connected to DVI and NOT on VGA. It's a Nvidia graphics card 7600GT. 

When i install it connected to vga i get a normal image but when i'm switching back to DVI i get a scrambled image again. It allready happens during booting with the splash screen. Al the vesions give me the same problem. The version i tried are Ubuntu x64 and x86 and also Kubuntu x64 and x86. 

Does anyone know how to fix this? I dont want to buy a new videocard. In windows everything is working ok so it isn't defective....

Thanks

---

### Post by kbloem on 2008-11-09
Anybody? :sad:

---

### Post by kbloem on 2008-11-10
Come on, there must be someone who knows what to do.....

---

### Post by starcannon on 2008-11-13
Looking into it, I have 8400m gs, twin 7950 gt's in sli mode, and a 6600gt, none of them require anything special to run from the dvi port; you have something outside of my norm. I know I've seen a modeline o something for dvi in the nvidia readme's, just a matter of locating it.

I'll keep looking, excuse the time lag, if your patient someone here, maybe even me, will help you solve your hardware issue.

Hang in there, once its working correcty you'll be very pleased, OS installs are difficult on some hardwares.

---

### Post by kbloem on 2009-01-29
Ok here is what i did....

I installed using the onboard VGA. After that i went to [www.nvidia.com](www.nvidia.com) and downloaded the 180.22 driver.

Then i went to the shell and killed X with sudo killall gdm

Then i installed the driver i downloaded with sh NVidia.......

After that i went back to my BIOS and changed my adapter to PCI-E.

While booting my Ubuntu logo was still looking messed up so i thought it didnt solve anything. But when i got to the logon window everything was ok.

I am relatively new to Ubuntu so i don't know a lot but is it possible my shell still uses the 173 or 177 driver from Nvidia for booting before it gets into gnome?

How can i update my shell with the new driver?

---

