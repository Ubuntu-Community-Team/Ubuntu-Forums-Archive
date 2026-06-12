---
title: "Can't run ubuntu on my pc"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by kirill578 on 2011-05-05
Yesterday, I had burn an image of ubuntu 11.04 for AMD 64, but I have problem with running it on my PC, when. Whenever I trying to try ubuntu or installing it from the live cd, there is a "_" blinking for a few seconds and then goes black. I tried the disk on other computers it worked well. 
I tried to run ubuntu 6 and it worked.

I have
AMD Athlon(tm) 64 X2 Dual Core Processor 4200+

 MSI K9N6PGM-F (MS-7309)

NVIDIA GeForce 8600 GT

---

### Post by tommcd on 2011-05-05
Your system should be just fine for Ubuntu.
Try booting with the *nomodeset* boot option. See this tutorial on how to add boot options with the F6 key from the live CD: [https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
If you are not even able to get to the initial screen from the live CD, then I would use the alternate install CD. This is a text based install only CD that should bypass any graphics related problems. 
After Ubuntu is installed you can then install the *nvidia-current* driver from the Ubuntu repos that is recommended for your nvidia card.

And welcome to the Ubuntu forums!

---

### Post by kirill578 on 2011-05-05
I have successfully installed ubuntu, however it had requested me to reboot and then it ran it with out the "acpi=off" thing so the screen went black. Somehow I managed to get to edit the boot options. There were were some commands that I did't know what were they, I just tried to add "acpi=off" but I still got the black screen.

Hope there is someone who can help me to run the system, so I'll be able to install nvida drivers.

---

### Post by tommcd on 2011-05-06
Have you tried booting with the **nomodeset** option as I suggested?
When you boot Ubuntu, hit the "e" key at the Ubuntu boot option to edit it. Scroll down to the the kernel line. Move to the end of the kernel line with the arrow keys. Then replace the words *quiet* and *splash* with **nomodeset** at the end of the kernel line.
 Then hit the CTRL + X keys (lower case x) to boot Ubuntu.
If you do not see the grub menu when Ubuntu boots, hold down the shift key as the computer boots and you will see the grub menu.

After you boot into Ubuntu, install the **nvidia-current** driver, along with **nvidia-settings** and **mesa-utils**. Then reboot (again with nomodeset) and run:
```
sudo nvidia-xconfig
``` from the terminal to configure the nvidia driver and you should be good. This is how I always install the nvidia driver.

Or you can just install the recommended driver from the *Additional Drivers* menu in Ubuntu. It should be the 
*nvidia-current* driver for your card.

---

### Post by kirill578 on 2011-05-06
Oh, Thanks that worked.

---

