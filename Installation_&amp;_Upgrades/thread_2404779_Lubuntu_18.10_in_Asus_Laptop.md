---
title: "Lubuntu 18.10 in Asus Laptop"
date: 2018-10-28
forum: Installation &amp; Upgrades
---

### Post by vjoxyodo on 2018-10-28
Hello guys,

I have a Asus F3Jc with Centrino Core 2 Duo 1.66GHz with 1Gb Ram (I'll upgrade to 3 GB) with a fresh 120 GB Sandisk. I was able to install Lubuntu 18.10 32Bit i386 version with no problems, after connectin network cable it activated Wireless smoothly, the thing is that this laptop has a control for CPU frequency and fan control. I Windows XP there was a small driver that would control this with a button in the keyboard, but I'm having problems with after the install the system heats a lot and after using a bit of the system like firefox etc the heats a lot and stucks and for sure this is a frequency/fan problem since the fan doesn't work after heating.

Can anyone help me please with this?

Best regards,
Pedro Lopes

---

### Post by DuckHook on 2018-10-28
Welcome to the forums, vjoxyodo.

Power management, especially in older HW, is a bit of a black art with Ubuntu, and especially with the newest versions ever since they went to systemd. Here are a few older pages that may help. No guarantees though. Although my knowledge of power management is feeble due to older HW that just works, I know that it's touch and go with many older laptops.

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)
[https://help.ubuntu.com/community/PowerManagement/ReducedPower](https://help.ubuntu.com/community/PowerManagement/ReducedPower)

There is also the following, although I'm unable to help you with the content because I don't use the apps.

[https://itsfoss.com/reduce-overheating-laptops-linux/](https://itsfoss.com/reduce-overheating-laptops-linux/)

Good luck!

---

### Post by vjoxyodo on 2018-10-29
Hello,

I'll give it a try this week. I already installed lm-sensors and runned pwmconfig, and system said there isn't any pwm fans. Actually before installing Lubuntu, I changed thermal paste, cleaned all dust from system. Yesterday I started the computer and the fans start and stop, start and stop for 3/4 seconds with low-speed - dont know if this is from Lubuntu start problem since I putted lm-sensors in daemon start or a problem with temp sensor in the motherboard. This is really strange.

---

### Post by vjoxyodo on 2018-11-02
> **DuckHook said:**
> Welcome to the forums, vjoxyodo.

Power management, especially in older HW, is a bit of a black art with Ubuntu, and especially with the newest versions ever since they went to systemd. Here are a few older pages that may help. No guarantees though. Although my knowledge of power management is feeble due to older HW that just works, I know that it's touch and go with many older laptops.

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)
[https://help.ubuntu.com/community/PowerManagement/ReducedPower](https://help.ubuntu.com/community/PowerManagement/ReducedPower)

There is also the following, although I'm unable to help you with the content because I don't use the apps.

[https://itsfoss.com/reduce-overheating-laptops-linux/](https://itsfoss.com/reduce-overheating-laptops-linux/)

Good luck!

Actually I think I found the problem. The CPU fan is not working at all, I had two thoughts CPU PWM pins are not working and fan engine is dead. 

So I have a fan with just 5v and Ground, I started the computer and connected fan wires to 5V and Ground of the 4 pin and it powered, so power is coming from motherboard (dunno if it is enough Amps for supposedly dead fan).

Then I powered my RPI added a breadboard and connected the 5v and ground directly to fan 4 pin - in some occasions it started to spin just 3 or 4 clicks other occasion no spin at all. So my mind goes to fan engine dead, I searched and bought from aliexpress a replace fan I think in two weeks I'll get in my mail box. I'll post news when the fan arrives and is installed, hoping to solve this problem :)

---

### Post by vjoxyodo on 2018-11-26
Like I thought, grip fan motor dead. Installed the new 3.5 bucks fan and worked like a charm. Actually now system is pretty stable, with a upgrade from 1GB to 3GB of RAM. Unfortunately fan speed control is done with power management, but fan speeds up when I'm pushing the CPU. Now I'll try to install to Ubuntu Mate, which is a more similar flavour to Ubuntu LTS, hope system can stand a heavier OS.

Thanks for your help and hope this tips help somebody :)

---

