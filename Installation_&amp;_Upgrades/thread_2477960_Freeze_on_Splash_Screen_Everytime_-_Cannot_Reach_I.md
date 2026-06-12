---
title: "Freeze on Splash Screen Everytime - Cannot Reach Install on Desktop"
date: 2022-08-12
forum: Installation &amp; Upgrades
---

### Post by legitdrew on 2022-08-12
All,


I am currently trying to install Ubuntu 22.04.1 on my PC alongside Windows. The process is as follows:


1. Download Ubuntu 22.04.1 from ubuntu releases
2. Flash download to usb with RUFUS
3. Restart PC and enter bios through F2
4. Ensure CSM is disabled, Fast boot is disabled, secure boot is disabled
5. Boot through UEFI USB device ([https://imgur.com/a/BpcXXva](https://imgur.com/a/BpcXXva))
6. Select "Try or Install Ubunutu"
7. This screen appears ([https://imgur.com/wuI0gSA](https://imgur.com/wuI0gSA))
8. I click my arrow key to move to the screen where code is executing in the background and my computer freezes at this screen and resets ([https://imgur.com/LL3hFKt](https://imgur.com/LL3hFKt))


I am new here, so if it is not clear I am not extremely savvy with computers or at least not at this level. I want to be as helpful as possible and have listed my steps above. If there is ANYTHING I can provide to assist you please let me know in a detailed comment so I can collect the necessary information and provide it to you. These are all of my steps from download to crash.


Update: I've since updated my process and also included the below image of some of the startup code that appears after I do step 6.


[https://imgur.com/BTnXjTG](https://imgur.com/BTnXjTG)


Update 2: I have since tried the following on separate occasions:


1. Replacing "quiet splash" with "nouveau.modeset=0"
2. nomodeset between "quiet spalsh" ('''quiet nomodeset splash''')
3. Deleting "quiet splash" and replacing with "nouveau.noaccel=1"
4. Deleting "quiet splash" and replacing with "noapic noacpi nosplash irqpoll"


These have all yielding failures that freeze on the splash screen code. To be clear the splash screen code is proceeded fine with "OK" at each step and just eventually freezes around the same few lines of code each time. ([https://imgur.com/K5Xjuo5](https://imgur.com/K5Xjuo5))


I am not receiving any relevant error codes from Ubuntu around the freeze.


***


Additional information:
MB is Asus Prime X570-P
I have an Nvidia GPU


Thank you I will update as comments come in.

---

