---
title: "Ubuntu Cinnamon 24.04 Clone to PC with same Motherboard."
date: 2024-11-20
forum: Installation &amp; Upgrades
---

### Post by tedman2 on 2024-11-20
I have Ubuntu Cinnamon 24.04 installed on a Z97 Motherboard.
Just Cloned it with a duplicator dock.
Installed it on another Z97 machine made by same manufacturer (ASUS)
The source machine has no GPU.
The destination machine has a GTX 960 GPU.
Having problems with no access to the repository. 

Can access the rest of the internet OK.

Below is the error message that I am getting.

The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software.
Transaction failed: Previous installation hasn't been completed
 E:Method http has died unexpectedly!, E:Sub-process http returned an error code (100), E:Method /usr/lib/apt/methods/http did not start correctly

Seriously stumped !

---

### Post by grahammechanical on 2024-11-20
The cloned operating system will not have a proprietary video driver for that GTX 960 GPU. Can you not use Software & Updates>Additional Drivers tab to activate a proprietary video driver? You need to be connected to the internet to do this.

Regards

---

### Post by tedman2 on 2024-11-20
I understand the issue with the GPU driver.
The problem is that I am unable to gain access to the repository.
Internet access elsewhere is just fine.

Just added this extra info to my original posting.

Below is the error message that I am getting.

The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software.
Transaction failed: Previous installation hasn't been completed
 E:Method http has died unexpectedly!, E:Sub-process http returned an error code (100), E:Method /usr/lib/apt/methods/http did not start correctly

---

### Post by grahammechanical on 2024-11-20
What command are you using to get that error message. I am not familiar with the Cinnamon desktop. But I wonder if you need to activate the Universe repository. I do not know what repository Ubuntu keeps proprietary video drivers in. I have found this:

[https://documentation.ubuntu.com/server/how-to/graphics/install-nvidia-drivers/?_ga=2.235411273.919200181.1732120470-1880007736.1729076438](https://documentation.ubuntu.com/server/how-to/graphics/install-nvidia-drivers/?_ga=2.235411273.919200181.1732120470-1880007736.1729076438)

But it makes no mention of activating a repository. Try using the instructions for the Ubuntu-Drivers tool.

Regards

P.S. http is an executable file ( a program) it is located in /usr/lib/apt/methods/
See if it has permission to execute. Are you spelling the file name correctly?

---

