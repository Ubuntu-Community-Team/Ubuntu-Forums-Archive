---
title: "Install Ubuntu on HP 755G5 R7-2700U Elitebook errors"
date: 2019-03-25
forum: Installation &amp; Upgrades
---

### Post by dalep0 on 2019-03-25
Hello.

I tried to install the following versions:

- Ubuntu 18.04 / 18.10: I get a black screen when trying to boot with legacy boot (secure boot disabled)
- Ubuntu beta 19.04: Was able to install but when I try to boot for the first time it hangs (black screen). I noticed the installation was really slow, and now after installing I am not able to install it again :/

Has anyone installed successfully ubuntu in this model?

Sadly, there is no support on HP side, I apologize for the lack of information, but if anyone faced this before I appreciate the help.

Cheers.

---

### Post by Rubi1200 on 2019-04-04
Hi and welcome to the forums :-)

From my search your laptop has the specifications to easily handle Ubuntu.

Are you installing over Windows or in a dual-boot configuration?

I recommend booting from a LiveCD/USB and choosing to Try Ubuntu and then follow the instructions from the link in my signature to create a boot summary report which you can then post here.

Thanks.

---

### Post by dalep0 on 2019-04-04
Hello, thank you for responding Rubi.
I am booting with Secure boot disabled, I only want one OS on my laptop (linux <3).
I tried booting with my USB but when I try to install or start the OS without installing it gets stuck with a black screen.
I was able to install 19.04 beta version but after the installation I get the same error (stuck in black screen) after I select ubuntu from Grub
I installed Debian stretch though, but I have to install all drivers manually and I haven't been successful with the graphics.

---

### Post by Rubi1200 on 2019-04-05
I would give some of the options here a try:
[https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

### Post by dalep0 on 2019-04-09
Ok thank you so much for your help.

I couldn't make it work with 18.04 & 18.10 but I managed to get it working with 19.04 (beta).

For anyone struggling with this, if you get the black screen with UEFI grub, try press E on the grub options and replace "quiet splash" with "nomodset" and ctrl x when selecting Try ubuntu. Then install from within and you should get the drivers.

More info on the link Rubi provided above.

Cheers.

---

