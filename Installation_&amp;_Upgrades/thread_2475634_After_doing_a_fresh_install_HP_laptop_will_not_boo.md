---
title: "After doing a fresh install HP laptop will not boot."
date: 2022-06-02
forum: Installation &amp; Upgrades
---

### Post by irv on 2022-06-02
Just so you know I am not a newbe I have been using Ubuntu Linux for many years now. But something strange keeps happening.
I have an older HP laptop, but it has a i7 CPU and 16 gig of RAM and a 500 SSD. I use it for testing different distors. I had Ubuntu 20.04 on it which I upgraded to 21.10 to 22.04. no problem. I decided to try ARCH. I install raw Arch, they I tried Manjaro and Endeavor. Again, everything went well. Then I thought I will give MX a try. Tried three different desktop, KDE, Gnome and xFce. Because MX didin't come with Gnome and I installed over KDE I had a few issues, but I expected I would.
Okay, that the background and now with the strange things that is happening. I went back to Ubuntu 22.04 and it installed great with no problems. I wiped the Hard Drive and did a clean install. When I went to reboot the laptop would not boot. It was like the Hard Drive wasn't there. I thought I must have did something wrong, so I just installed again and the same problem, no boot.
To make sure it wasn't the hardware I install MX again, and everything worked. Install 22.04 the third time and same problem. I even tried installing Window 10 and it install okay, tried to install 22.04 again after windows, and had the same problem.
Okay, I went out and got another .iso file and made another USB and did the install again the 5th time, and with the new USB I had the same problem.
Is it possible that there is a problem with the install from the 22.04 iso file?
All my other computer were just upgrade to 22.04 and not a fresh install so I don't know what else to try except to try to install 21.10 and then upgrade. What are you thoughts on this?

---

### Post by TheFu on 2022-06-03
If you use the efi boot manager, can you boot?
Is the SSD firmware up to date?  MX Linux isn't known for having the most current of releases.
Does the BIOS see the SSD? It just isn't found from Ubuntu?

---

### Post by sudodus on 2022-06-04
I think the Ubuntu installer might need some help. Create a partition table. MSDOS partition table might be best for this old horse. Then try again, let the installer 'use the whole drive'.

If no luck, create a GUID partition table, GPT, and try again to install.

---

### Post by irv on 2022-06-05
Okay, here is what I ended up doing. I left MX installed and installed 22.04 along side it. It boots fine now. it setup a new grub so I can boot into either or. It still doesn't answer why it would not setup right if I installed it alone. I thinking it is because of how the install for Ubuntu is coded that it has something to do with the old BIOS on this laptop. I know it is hard to account for ever piece of hardware out here. All I know is 4 other Linux distros installed just fine.

---

