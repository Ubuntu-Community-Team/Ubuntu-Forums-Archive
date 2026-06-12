---
title: "nvidia quadro k600 driver dies"
date: 2021-11-10
forum: Installation &amp; Upgrades
---

### Post by vector on 2021-11-10
Hi all,
New ubuntu studio install on a HP Z220 pc running I7 and 1tb SSD
on 2nd reboot displays drops to 640

After much reading i got around this by purging nvidia drivers
lspci -v now indicates its using the nouveau
so far reboots are ok to highres but how do I get nvidia to work?

Tried settings/software/additional drivers. 
selected nvidia metapackage 470 but on reboot same low res problem 
xrandr: Failed to get size of gamma for output default

Purged nvidia drivers again and Im back to nouveau and higher res
but what do i need to kickin in the nvidia (I want to run darktable which uses opencl)

---

### Post by ActionParsnip on 2021-11-10
Does the nouveau driver do what you need? Any issues at all?

---

### Post by vector on 2021-11-10
"Does the nouveau driver do what you need? Any issues at all?"
A good question. 
Resolution wise its fine. I can only go by what I've read in that its slow compared to nivida driver when using opencl which is what darktable uses and my sole purpose for the machine.
I was actually hoping to prove this at some point for myself by comparing some darktable process with and without the nvidia drivers. Its just annoying that I can't get the driver to work to allow me to prove this one way or the other.

---

### Post by vector on 2021-11-15
Gave this another attempt. This time:
sudo apt-get remove --purge '^nvidia-.*'
ubuntu-drivers devices ....to confirm which driver was recommended

sudo apt install nvidia-driver-470
sudo reboot
nvidia-smi   to prove it held
so far so good and Darktable picked up on the openCL. Looks like  a winner.
Not sure why the previous attempts failed.

---

