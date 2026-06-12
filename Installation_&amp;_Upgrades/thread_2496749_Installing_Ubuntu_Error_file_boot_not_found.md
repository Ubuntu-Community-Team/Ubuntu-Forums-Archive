---
title: "Installing Ubuntu: Error: file /boot/ not found"
date: 2024-04-10
forum: Installation &amp; Upgrades
---

### Post by 4R%@&amp;huj on 2024-04-10
Hello,

I am currently a Cybersecurity student who is attempting to install Ubuntu to get more acclimated with Linux and using the terminal. I'm super new using the OS so I'm not quite sure how to resolve the error that I get in the title. It appears for a millisecond when first booting to Ubuntu. I can try Ubuntu and use the software, however I cannot install it on to my hard drive as I get an error. I've tried a few simple troubleshooting steps that I could find on forums and Youtube, but can't seem to come to a solution.

I am currently running on a Macbook Pro 2017 and am attempting to install the latest version available of 20.04.4 from a USB stick that I created using Balena Etcher. I am looking to completely remove the Mac OS from my system and solely use Ubuntu for training and studying. 

I also ran a report using Boot-Repair [https://paste.ubuntu.com/p/YR7b2dktw9/](https://paste.ubuntu.com/p/YR7b2dktw9/). I've tried re-configuring the USB multiple times as well as using various USB sticks. I've also tried different versions of Ubuntu but still run into issues with the installation.

Can someone point me in the right direction as to what I need to do to get the OS fully installed?

---

### Post by MAFoElffen on 2024-04-10
I think maybe its a problem with what MAC hardware requires, and the way Etcher is prepping the USB Flash Drive.

MAC hardware will not boot unless the Partition table is GPT. It does not recognise MS_DOS partition tables...

What OS are you using on the machine you are creating the Installer LiveUSB?

---

### Post by 14nd on 2024-04-11
found this ...seems like a lot of hassle with a mac :eek:

[https://gist.github.com/cjonesy/2e2d8ca5e50ee1811f70](https://gist.github.com/cjonesy/2e2d8ca5e50ee1811f70)

---

