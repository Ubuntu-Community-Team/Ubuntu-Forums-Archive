---
title: "Install Ubuntu Core on Raspberry Zero 2 W"
date: 2021-12-08
forum: Installation &amp; Upgrades
---

### Post by domlan01 on 2021-12-08
First of all I would like to apologize. It's my first thread in this forum and I honestly don't know if I'm in the right section.
As the title suggests, I have been trying to install the IoT version of Ubuntu on an RPI Zero 2 W device for about 2 weeks, but always without success.
I started with these instructions [https://ubuntu.com/blog/raspberry-pi-zero-2-w-with-ubuntu-server-support-is-here](https://ubuntu.com/blog/raspberry-pi-zero-2-w-with-ubuntu-server-support-is-here)

I tried both the 64 and 32 bit versions and in both cases the result is the same: when I transfer the SD card from the Raspberry 4, on which I complete the registration and activation of the RSA key associated with my account, to Zero 2, this just doesn't start.
After the rainbow screen, no messages. Only the service led has this behavior: 7 flashes in sequence. Repeated indefinitely. Waited hours before deciding that nothing would change.

Studying the composition of the image used (in particular the 32-bit one, declared as working out-of-box) I imagine that it has a signature that the UEFI is not able to interpret, therefore to start.
I ask you if you have had similar experiences with this SO.


I specify that all versions of Ubuntu Core work perfectly on Raspberry 4. Also, always on the Zero 2 W, I have successfully tested these distributions:
Ubuntu Server: 21.10 (32 and 64bit)
Raspbian: standard (32 and 64 bit) and lite (32bit)

Regards

---

### Post by ActionParsnip on 2021-12-08
Do you have the latest firmware? It may help

---

