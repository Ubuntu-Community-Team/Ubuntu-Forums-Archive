---
title: "Grub issues - Installed 12.04 alongside windows"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by Dave.YNA on 2012-04-27
Hello Everybody,

I am having a strange grub issue and would like to see if anyone can offer some wisdom. 

In a nutshell after installing 12.04 alongside Windows I do not get an option to boot into Ubuntu at start up. Now I know this is not new to the forums but where my issue slightly differs is that it appears that grub has installed to my Pen Drive which I used to install the OS. 

- If I boot normally, I go straight to windows
- If I change the boot order and put my USB stick in, it boots to GRUB and I can select the OS. 
- Another strange thing is I am not able to boot into the "liveCD" on the stick. 

- To make sure I had not installed the OS on the pen drive by mistake I checked my partions on my hard drive and also check the free space available on the stick before and after installing some new programs / language packs etc and the pen drive has the same amount of space so I can only assume it Ubuntu installed correctly and there is an issue with grub. 

Any advice to install grub to the correct place?

I saw the boot-repair app listed on another post but was not sure if it would be applicable to me given the USB drive curve ball. 

Cheers

---

### Post by zdeuyo on 2012-04-27
> **Dave.YNA said:**
> Hello Everybody,

I am having a strange grub issue and would like to see if anyone can offer some wisdom. 

In a nutshell after installing 12.04 alongside Windows I do not get an option to boot into Ubuntu at start up. Now I know this is not new to the forums but where my issue slightly differs is that it appears that grub has installed to my Pen Drive which I used to install the OS. 

- If I boot normally, I go straight to windows
- If I change the boot order and put my USB stick in, it boots to GRUB and I can select the OS. 
- Another strange thing is I am not able to boot into the "liveCD" on the stick. 

- To make sure I had not installed the OS on the pen drive by mistake I checked my partions on my hard drive and also check the free space available on the stick before and after installing some new programs / language packs etc and the pen drive has the same amount of space so I can only assume it Ubuntu installed correctly and there is an issue with grub. 

Any advice to install grub to the correct place?

I saw the boot-repair app listed on another post but was not sure if it would be applicable to me given the USB drive curve ball. 

Cheers

Hello,

I had a similar problem and Boot-Repair fixed it about 1 hour ago on this computer I am writing this from. Here is the link

Link: [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

Follow the instructions exactly on that page.

Let me know if it works.

---

### Post by Dave.YNA on 2012-04-27
Hey, thanks for the advice... I will give it a try and let you know. I am not in a place where I can tinker now :)

Appreciated

---

### Post by zdeuyo on 2012-04-28
Hello,

Did this solve your issue?

---

### Post by Dave.YNA on 2012-05-03
Hi Sorry for the delay! I literally have only just had chance to try it.

Yes it worked, thanks! Will mark this thread as solved.

---

