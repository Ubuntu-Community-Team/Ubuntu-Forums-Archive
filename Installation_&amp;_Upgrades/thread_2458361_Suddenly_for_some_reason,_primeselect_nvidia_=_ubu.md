---
title: "Suddenly for some reason, primeselect nvidia = ubuntu freezes at boot."
date: 2021-02-22
forum: Installation &amp; Upgrades
---

### Post by dolerbobber on 2021-02-22
Hi, i've been bashing my head against this for hours and hours on end and I want to figure out a fix. I wanted to play a game a couple days ago on ubuntu, which I've also used successfully in the past for CUDA tasks and gaming, but realized that the GPU driver wasn't working. when I did nvidia-settings, it would give me the "ERROR: Unable to find display on any available system" error

MY GPU: Geforce 960M (optimus, laptop), using drivers: nvidia-driver-460, (kernel modules provided by linux-modules-nvidia-460-generic-hwe-20.04)

I booted into windows to play the game, then when I booted back into Ubuntu, it wouldn't boot. If I let it ride, it'd freeze on the ubuntu logo loading screen. If I pressed an arrow key to see the log as it booted, it'd freeze on the cursor.

The only fix is to go into recovery and either delete the nvidia drivers, or run 'prime-select intel', which would allow me to successfully boot.

I've probably removed and reinstalled the nvidia drivers just about 100000000000 times, and read and tried every thread on the issue, to no avail. I use these scripts to remove nvidia from my system:

sudo apt-get remove --purge '*nvidia*'
sudo apt-get remove --purge '*vidia*'
sudo apt-get remove --purge '*cuda*'



Anyone know of a fix??

---

