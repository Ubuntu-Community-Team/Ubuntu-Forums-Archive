---
title: "at wits end: trying to pxe boot ubuntu 20.04 iso laptops connected with usb-c cable"
date: 2021-06-10
forum: Installation &amp; Upgrades
---

### Post by generalcanada on 2021-06-10
[FONT=verdana]So basically i have FOG setup to currently boot windows mdt isos.[/FONT]
[FONT=verdana]Ive been working the last few months via trial and error to get this working for Ubuntu.[/FONT]
[FONT=verdana]Ubuntu fully works properly via vmware virtual machines because built-in network adapters are no problem.[/FONT]
[FONT=verdana]When i go to take the public initrd and vmlinuz files from the public ISO and boot them to the usb-c adapters on the laptops. 2 things happen[/FONT]
[FONT=verdana]no actual interfaces are found[/FONT]
[FONT=verdana]because of this its unable to download the iso from the local server[/FONT]
[FONT=verdana]So my first thought is "oh well seems like drivers are missing"[/FONT]
[FONT=verdana]I then went ahead and tried to create my own initrd that includes the module (r8152) this didnt work[/FONT]
[FONT=verdana]I threw every module into /etc/initramfs-tools/modules and updated the initrd file. This worked The network adapter was able to get an ip address[/FONT]
[FONT=verdana]the real problem
[https://imgur.com/a/FabDD3j](https://imgur.com/a/FabDD3j)[/FONT]
"gave up waiting for root file system" "/dev/ram0 doesnt exist"[FONT=verdana]This is the part i cant get past. As you can see /dev/ram0 exists, i dont see why its not mounting the (initrd?) file system on the ramdisk?[/FONT]
[FONT=verdana]Im not the most experienced in linux, but i feel like im missing something here, i cant be the only one who is pxe booting ubuntu laptops under 20.04[/FONT]
[FONT=verdana]side note: I should add the mini.iso that previously existed under 18.04 is not being distributed for 20.04 which the laptop actually booted properly. I may end up using this and upgrading to 20.04 once fully installed, but i really want to do it this way.[/FONT]
[FONT=verdana]Another way is to just capture an image which is quite simple, i want to stay the path of "thin imaging".[/FONT]
[FONT=verdana]Any help is appreciated
[/FONT]

---

### Post by MAFoElffen on 2021-06-10
i have an initial question before I start to answer this. It comes from the Title of your post, even before reading the content of your post...

You have 2 laptops, which you are trying to connect via a USB C cable. Do they not have an Ethernet connection? PXE boot usually boots from a network device capable of PXE boot. So if they are not connected to a private network through a switch, and you want to connect them directly, then why are you not connecting them together with an ethernet crossover cable? That would be so much faster than an USB-C. You mentioned you tested this via VMware virtual machines. It worked because it had generic network adapters...Connected through the etthernet device would solve the driver situation, and is straight forward from there, right? Just saying what I am thinking on that.

Next, I applaud your ambition. I know that support for Ubuntu and the Debian branch from the FOG Project, in their Wiki stopped at 16.04 (5 years ago). I believe the information you are asking about is here: "[Ubuntu Wiki/PXE-netboot-install]("https://wiki.ubuntu.com/UEFI/PXE-netboot-install")".

The most recent Ubuntu related post I found on the FOG Project Forum was from 3 years ago [HERE]("https://forums.fogproject.org/topic/10394/trying-to-image-ubuntu-desktops?lang=en-US")

---

