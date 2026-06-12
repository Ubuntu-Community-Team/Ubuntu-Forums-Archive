---
title: "Black screen afther install ubuntu 16.04 lts"
date: 2017-08-04
forum: Installation &amp; Upgrades
---

### Post by erikebz on 2017-08-04
Hi I am trying to install[COLOR=#0000ff]Ubuntu 16.04 LTS alongside with WINDOWS 10[/COLOR] in a notebook HP PAVILION ab010la with the next HW AND SW:

[B]17.7.2
Crimson ReLive
[COLOR=#ff0000]AMD Radeon R6 Graphics  (512 MB)
AMD Radeon R7 M360 as secondary gpu with 2 GB [/COLOR]
DDR3
Windows 10 (64 bit)
12 GB
AMD A10-8700P Radeon R6, 10 Compute Cores 4C+6G
[http://i.imgur.com/DFnYIpw.png](http://i.imgur.com/DFnYIpw.png) those are the especifications but they are in spanish :s[/B]

As you can see my Notebook has dual graphics i dont know if this become into a problem for ubuntu.

I install UBUNTU using RUFUS and a USB with 8 Gb.When i try to install as the default config the installer never pass of the loading bar.
I search in google and finded the "nomodeset" line, with this config im able to install and run UBUNTU at the first time wirh normally.

The problem appear when i turn off my computer and turn on it again.

The GRUB seems as the same but whe i push enter for run UBUNTU, my screen keeps in a black color and never send image to my screen.
Then i have to shut down the PC with the power button.

I turn on the pc in place of grub It shows me the next:
**minimal BASH like line editing is supported” Grub error in Ubuntu based Linux...**


and i cant start my pc until i shut down the pc with PB and run Windows with the BIOS (f9 FOR BOOT OPTIONS) then i can not run UBUNTU until i clear the partition where it is installed but the boot option of ubntu never dissapear of the boot options.

Then i have to reinstall Windows 10 and i reinstalled w10 more than 5 times just for this problem.

Does anyone knows how can i fix the black screen problem? (i am thinkin that this problem has to be with the 2 gpus but idk)
well i still suing W10 until someone help me to install it correctly :p

Hope you can help me beacuse i want to leave windows and starts using Linux because i need for my courrier...

---

### Post by BenginM on 2017-08-05
Hiya , welcome to the forums ..
disable one of the two GPUs , and  maybe you wouldn't need to boot with nomodeset for the installation ..

---

### Post by erikebz on 2017-08-05
ok thank you, i will try and if this works post the result here...

---

