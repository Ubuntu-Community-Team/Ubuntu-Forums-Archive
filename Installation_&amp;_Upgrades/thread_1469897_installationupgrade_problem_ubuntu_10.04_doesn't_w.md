---
title: "installation/upgrade problem: ubuntu 10.04 doesn't work in asus X50GL laptop"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by josemanuel on 2010-05-02
Hello,

        I am a current ubuntu user . I have installed it in multiple machines (servers, desktops, laptops). I have even installed 10.04 beta in several laptops for educational purposes without a single crash.  But 10.04 crashes in laptop ASUS X50GL with processor Intel Core 2 Duo T5800 .  In fresh installation, it hangs always, in ANY 10.04 version, beta or stable, 32 or 64 bit,  also from iso image in CD or in usb stick, ... I have tried all possibilities!. Therefore, clever enough, I though  let's do it in an indirect way: let's install the 8.04 distro (it works) and later on I will upgrade to 10.04. So I just did.  Everything was fine (also the upgrade, without a single warning) until final reboot after upgrade to 10.04....hanged at boot!. There is  incompatibility between 10.04 and this firmware, clearly. Unfortunately, 10.04 is not yet stable, I guess.  I took  a picture of the screen which I attach. It's hanged forever.

Thanks in advance for your help. 

                                     Jose Manuel

---

### Post by oldfred on 2010-05-02
I know the nomodeset worked for my nvidia but I think it also works for other systems:

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf
boot from the cd, press F6 and then select the Nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot

[http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)

---

### Post by josemanuel on 2010-05-02
Thanks a lot, Oldfred. I tried everything but it doesn't work. I could even manage to install 10.04 directly from live CD and at reboot I made the proposed action, but no effect. I guess that I will wait for solution. It's a pity, It was for my son's laptop, after convincing him (enthusiast windows user). I have no more time to spend in this issue.  Ubuntu has lost a user (my son)for the time being. Let's wait for fixes in the distribution. Cheers

                          Jose Manuel

---

### Post by zibeltbg on 2010-06-06
josemanuel,

       I had the same problem on my ASUS X50GL laptop.I managed to install Kubuntu 10.04 LTS 64 bit in the following manner-
  
    1-installed Kubuntu  9.10 64 bit
    2-upgrade and install nvidia driver from system-Hardware Drivers
    3-started upgrade to Kubuntu 10.04 LTS 64 bit, 
and stop it at the moment in which began to tow packages(you will see the message for installation problem)-Don't worry.
    4-Now, restart and go to recovery mode, and go to repair of broken packages-and Start upgrade and agree with standard answers
    5-restart and reinstall KnetworkManager which aplet   
    6-go to settings-system-settings-login-theme-select ethais-apply and go to Systray-initial screen-select default

    That it. For me it works without problem in  ASUS X50GL laptop and my daughter is very happy which Linux!

    Good luck !!!

---

### Post by josemanuel on 2010-06-07
Hello Zibeltbg, thanks a lot for your suggestions. I'll try them asap and let you know. Cheers
            Josemanuel

---

