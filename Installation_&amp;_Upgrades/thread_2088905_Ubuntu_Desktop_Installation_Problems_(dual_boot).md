---
title: "Ubuntu Desktop Installation Problems (dual boot)"
date: 2012-11-27
forum: Installation &amp; Upgrades
---

### Post by Guaraldi on 2012-11-27
Hi everyone,

I am new to open source platforms thought Ubuntu would be a nice start. Sadly, I'm having tons of installation problems even if I'm googling for solutions.

First, I tried installing Ubuntu via a CD of Ubuntu, When I tried running Ubuntu, all went well but I did not had any network. I tried to install it via CD and here is what happened. 

[IMG]http://s11.postimage.org/g4tzv1c6b/PIC000105.jpg[/IMG]

As you can see, Ubuntu does not detect my hard drive or my internet connection (I'm not using wireless - there is an Ethernet cable connected to my build-in network card).

I also tried installing without emulating via cd first. Here is the picture 
[IMG]http://s12.postimage.org/jpd0c2sjh/PIC000103.jpg[/IMG]

I then tried to install ubuntu via wubu. Here is the setup I selected : 

[IMG]http://s9.postimage.org/iivqeww27/wubi.png[/IMG]

And here is what happened when I rebooted

[IMG]http://s7.postimage.org/tea97wdbf/PIC000102.jpg[/IMG] 
I followed some instructions on the forum about downloading wubi, extracting the iso on a folder on my destop, using virtual drive to open my iso... None of them worked out for me. 

When I tried to boot via CD post-bios while I had a wubi installation on my logical drive, I was able to emulate Ubuntu again but not to install it (same problem as with first installation (doesnt detect the drive/network). When I tried to close Ubuntu, I ended up with this screen 
[IMG]http://s13.postimage.org/3tljz4mon/PIC000107.jpg[/IMG]

This led me to wonder if my overclocked setup was the cause of my problems, but even with stock settings on my motherboard nothing changes. 

Finally this is my hardware. Hope this can help you guys out.

Manufacturer:                  Gigabyte Technology Co., Ltd.
                        Processor:                  Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz (8 CPUs), ~4.0GHz
                        Memory:                  6144MB RAM
                        Hard Drive:                  1 TB
                        Video Card:                  NVIDIA GeForce GTX 560 Ti  
                        Monitor:                  LG FLATRON W2253V
                        Sound Card:                  Speakers (High Definition Audio Device)
                        Speakers/Headphones:                  Astro A50
                        Keyboard:                  daskeyboard
                        Mouse:                  Razer Naga
                        Mouse Surface:                  Steelseries
                        Operating System:                  Windows 7 Home Premium 64-bit (6.1, Build 7601) Service Pack 1 (7601.win7sp1_gdr.120503-2030)
                        Motherboard:                  X58 GUERILLA
                        Computer Case:                  HAF 922

Thanks in advance, sorry for spelling errors I'm not English native :(

---

### Post by oldfred on 2012-11-27
Welcome to the forums.

I really do not know wubi. But wubi does not work on gpt partitioned drives. Is your system booting from legacy/BIOS or the new UEFI. Most motherboard with i7 processors can use either. And if UEFI you will have gpt partitions.

I prefer to use flash drives now for installs, a bit faster than CD. And some of the newer versions need larger than standard CDs. What version are you installing?

Almost all Ethernet hard wired connections work. And an install works better if you have that working so it can update drivers and all the software. May be best to resolve that first, but I do not know a lot of the details as all my systems just work.

But your nVidia will have issues. I have nVidia and have to add nomodeset on liveCD or USB boots and first boot after install. With 12.10 I had to install kernel headers before installing the nVidia drivers. I only use the nVidia drives that Ubuntu offers, but some very new video may need the very newest nVidia drivers. Ubuntu now offers several versions so usually one or the other works with most.

       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

    procedure is different for flash drive, CD/DVD, and first boot.

IF booting in UEFI mode some things also are different. 

For Ethernet post these command from terminal if you can boot liveCD.
lspci -v
dmesg | grep eth
# Plug in and see if errors:
dmesg | tail -n10
# Check by chipset:ie e1000e
sudo lsmod | grep e1000e

---

