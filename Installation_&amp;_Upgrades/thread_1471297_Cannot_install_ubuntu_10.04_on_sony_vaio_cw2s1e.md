---
title: "Cannot install ubuntu 10.04 on sony vaio cw2s1e"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by steffenomak on 2010-05-03
Hi, cant install it or event boot it to try, becouse when i choose to install or test it the sceen goes blank. I hade the same problem when I hade the older version but solved it whit using the custom eidi or whats is calld and changing xorg.conf. But I saw that nvidia had posted the drivers for GeForce gt 330m on its site for 32 and 64 bit linux drivers so i wanted to try the newest ubuntu. The thing is that i cant event install it or anything, so i cant use the eidi method eather.

I would realy like to go whit ubuntu and not having the problems im having whit windows after a new install i had. And I also thik developing c++ code in linux i much faster.

Tanks for the help and i hope there is a fix for my problem.

---

### Post by divague on 2010-05-03
If you're using the liveCD, after selecting the language, hit F6 and check nomodeset. That worked for me.

---

### Post by steffenomak on 2010-05-10
> **divague said:**
> If you're using the liveCD, after selecting the language, hit F6 and check nomodeset. That worked for me.

I could install it but when i boot into it the screen goes black

---

### Post by Moriarty123456 on 2010-05-10
I have the same problem on my old Sony Viao (VGN-B1VP). Just a blank screen. Have had to go back to 9.10. Pity, as I'm new to Ubuntu/Linux I'd much rather use the newest version.

---

### Post by steffenomak on 2010-05-10
> **Moriarty123456 said:**
> I have the same problem on my old Sony Viao (VGN-B1VP). Just a blank screen. Have had to go back to 9.10. Pity, as I'm new to Ubuntu/Linux I'd much rather use the newest version.

He ok, but i just got the idea that using the liveCD and edit the xorg.conf of the installed ubuntu and force it to use a custom edid that makes it possible to use 3d acc, and most of all i should be able to loggin and install correct videodrivers. But i dont know why linux overal has problem whit sonys stuff

---

### Post by divague on 2010-05-10
> I could install it but when i boot into it the screen goes black

Then maybe this could help, when you see the grub screen select the Linux option you use and hit 'e'. Go to the 'linux /boot/vmlinuz....' line and after splash hit space and type *nomodeset* then press ctrl+x to boot.

---

### Post by emorkay on 2010-05-11
Hi,
@divague:
that helped my friend too...
thanks..

---

### Post by soulitude on 2010-06-01
Hi guys,

I just bought a sony vaio and its giving me a hard time installing ubuntu 10.04. Will check out your measures there..and thanks divague!:KSwill get back after the check.

---

### Post by steffenomak on 2010-06-01
> **soulitude said:**
> Hi guys,

I just bought a sony vaio and its giving me a hard time installing ubuntu 10.04. Will check out your measures there..and thanks divague!:KSwill get back after the check.

When you install, just after language where you can choose to install or try it, press f6 i think and select nomodeset. Then you have to always have that option. If you need any more help

---

### Post by soulitude on 2010-06-02
Hi Steffenomak,

Thanks for the help. Now i have installed ubuntu lynx. Had to give nomodeset like you mentioned. Now that i have installed i have to give nomodeset next to the linux image line with grub edit every time i login. This is actually a bit annoying. I tried to locate xorg.conf and write it there after logging in but couldn't locate the file xorg.conf

Is there anyway i can save this option on OS and set the kernel to boot with nomodeset without having to write it everytime?

Waiting for your reply..cheers:D

---

### Post by steffenomak on 2010-06-02
> **soulitude said:**
> Hi Steffenomak,

Thanks for the help. Now i have installed ubuntu lynx. Had to give nomodeset like you mentioned. Now that i have installed i have to give nomodeset next to the linux image line with grub edit every time i login. This is actually a bit annoying. I tried to locate xorg.conf and write it there after logging in but couldn't locate the file xorg.conf

Is there anyway i can save this option on OS and set the kernel to boot with nomodeset without having to write it everytime?

Waiting for your reply..cheers:D

in "/boot/grub/grub.cfg" you can at about line 69 for me change how it look to make it permanent. But it is not recomended normaly, but to get it to work change the boot option at "linux:" and change at the where you are changing now to nomodeset

But remember that after some updates especially the first update it changes back, but it doesnt happen often.

If you have anything else ask!

---

### Post by soulitude on 2010-06-02
Hey,

thanks for the reply! take care.

---

### Post by bcbc on 2010-06-02
> **steffenomak said:**
> in "/boot/grub/grub.cfg" you can at about line 69 for me change how it look to make it permanent. But it is not recomended normaly, but to get it to work change the boot option at "linux:" and change at the where you are changing now to nomodeset

But remember that after some updates especially the first update it changes back, but it doesnt happen often.

If you have anything else ask!

Better to change it in /etc/default/grub ```
gksudo gedit /etc/default/grub
```
There's a line ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
Add it after that and run ```
sudo update-grub
```

---

