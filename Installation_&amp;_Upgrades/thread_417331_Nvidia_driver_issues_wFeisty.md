---
title: "Nvidia driver issues w/Feisty"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by Rotaj on 2007-04-21
I updated to Feisty yesterday. After finalizing the upgrade, I was left with 2 items to update. Below, the first section is the description from the update manager. The second section is the error output from applying the update. 

Should I delete the files it is referring to, forcing a new download?


These XFree86 4.x/X.Org binary drivers provide optimized hardware acceleration of OpenGL applications via a direct-rendering X Server and support the newer GeForce, nForce and Quadro families of NVIDIA chipsets.
AGP, TV-out and flat panel displays are also supported.
If you have a TNT, TNT2, or older GeForce, you may need the nvidia-glx-legacy package instead of this one.
To enable the driver, run "sudo nvidia-glx-config enable". 


E: /var/cache/apt/archives/nvidia-glx-dev_1%3a1.0.9631+2.6.20.5-15.20_amd64.deb: subprocess pre-installation script returned error exit status 2
E: /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-15.20_amd64.deb: conflicting packages - not installing nvidia-glx
E: /var/cache/apt/archives/libgl1-mesa-dev_6.5.2-3ubuntu7_all.deb: conflicting packages - not installing libgl1-mesa-dev
E: /var/cache/apt/archives/mesa-common-dev_6.5.2-3ubuntu7_all.deb: conflicting packages - not installing mesa-common-dev

My vidio is an nvidia 6100 w/256mb integrated into the motherboard.

---

### Post by mhansen on 2007-04-21
To be honest, I've never had a problem using the nvidia drivers from nvidia....the ubuntu packages just don't seem to work for me.  You might want to try those.


Regards,
Mike

---

