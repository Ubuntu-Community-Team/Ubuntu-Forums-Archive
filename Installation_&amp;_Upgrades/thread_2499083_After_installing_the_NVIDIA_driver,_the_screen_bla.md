---
title: "After installing the NVIDIA driver, the screen blacks out and does not recover."
date: 2024-07-11
forum: Installation &amp; Upgrades
---

### Post by a03 on 2024-07-11
**Actions Taken:**
sudo apt update
sudo apt upgrade
ubuntu-drivers devices
sudo apt install nvidia-driver-535 (recommended)
sudo reboot



After&#12288;[FONT=monospace]sudo reboot,[/FONT]
The screen is completely black, with only a cursor appearing in the top left corner.


sudo apt-get purge nvidia-*
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
sudo apt-get autoclean
sudo ubuntu-drivers autoinstall
sudo reboot
nvidia-smi&#12288;&#8594;&#12288;NVIDIA-SMI has failed....





**Machine:**
ThinkPad P1 Gen 7
Processor: Intel® Core™ Ultra 7 Processor 165H with vPro® (E-cores up to 3.80 GHz, P-cores up to 5.00 GHz)
Graphics Card: NVIDIA® GeForce RTX™ 4060 Laptop GPU 8GB GDDR6

---

