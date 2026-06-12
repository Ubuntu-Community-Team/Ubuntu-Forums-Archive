---
title: "Windows 7 / Ubuntu dual boot / Doesnt &quot;see&quot; windows"
date: 2012-06-14
forum: Installation &amp; Upgrades
---

### Post by xLinear on 2012-06-14
hi, i have installed ubuntu onto a new partition on my hard drive (1 x 500gb) the partition is 100gb, after installing ubuntu from the LiveCD ubuntu works great BUT, whenever i re-boot my computer my screen says "Out of range" and sits there for a few 20 seconds, then it boots into ubuntu.

What i am trying to do is get back to windows, due to me needing to finish a film project.

Please help me! i have run Boot-Repair and here are the results

[http://paste.ubuntu.com/1040527/](http://paste.ubuntu.com/1040527/)

i don't know what to do,

Thanks in advance~
xLinear.

---

### Post by coffeecat on 2012-06-14
Hi and welcome to the forum.

The problem is that your monitor doesn't like the output from your graphics card for some reason when the grub boot menu would be showing. I don't have an immediate answer for this at the moment, but I will do do a bit of searching, or perhaps someone else may have a suggestion.

In the meantime, here is a way of booting into Windows, unsatisfactory but at least it should do as a temporary expedient. As soon as you see the "out of range" message, press the down arrow key four times and then press ENTER. Your machine should then boot into Windows

---

### Post by xLinear on 2012-06-14
> **coffeecat said:**
> Hi and welcome to the forum.

The problem is that your monitor doesn't like the output from your graphics card for some reason when the grub boot menu would be showing. I don't have an immediate answer for this at the moment, but I will do do a bit of searching, or perhaps someone else may have a suggestion.

In the meantime, here is a way of booting into Windows, unsatisfactory but at least it should do as a temporary expedient. As soon as you see the "out of range" message, press the down arrow key four times and then press ENTER. Your machine should then boot into Windows

thanks, ill try that now, i'm running integrated graphics at the moment (face palm) and ubuntu says it has an update for the driver, i have tried installing it before but upon ubuntu loading, and me logging in it just shows the background. i do have a 6770 in my wardrobe but i dont have enough sufficient power. thanks again

---

### Post by coffeecat on 2012-06-14
The problem may be more with the monitor that the graphics card, but what is the integrated graphics chip?

---

### Post by xLinear on 2012-06-14
the graphics chip is a:
NVIDIA GeForce 6150SE nForce 430

and the monitor is a:
LG Flatron E2240 22"

---

### Post by coffeecat on 2012-06-14
There is a known problem with the nvidia 6000 and 7000 series and the current proprietary driver, and you would need an older version of the driver. It's possible that the newer version got installed somehow, but first we need to see whether you are running with the default nouveau open source driver or whether you have installed one of the proprietary nvidia drivers. Open the application Additional Drivers and tell us what it tells you. Better still take a screenshot of the open window (Alt+Print) and attach it to your post. You can use the [img]http://ubuntuforums.org/images/editor/attach.gif[/img] button in the message toolbar, or the "manage attachments" button below the message field to upload the screenshot.

---

### Post by xLinear on 2012-06-14
[IMG]http://i.imgur.com/N0jZl.png[/IMG]

---

### Post by coffeecat on 2012-06-14
Since there is no proprietary driver installed, you must be running on the open source nouveau driver. Whether or not this is causing the problem that you see with the grub menu, I don't know. You mentioned installing an "update" for the driver before. Do you mean that you installed the current version of the proprietary nvidia driver with Additional Drivers? The current version is the 295.40, and here is a thread about the problems you might see with a 6000 series GPU and this driver:

[http://ubuntuforums.org/showthread.php?t=1969754](http://ubuntuforums.org/showthread.php?t=1969754)

I suggest you try installing the older nvidia-173 driver and see if this helps with the grub menu. Open a terminal, and:

```
sudo apt-get install nvidia-173 nvidia-settings
```

Let that install and reboot. Does that help?

---

### Post by xLinear on 2012-06-14
i installed the "update" driver on Windows 7 through the nVidia website:

When i use that command in terminal i get:
```
The following packages have unmet dependencies.
 nvidia-173 : Depends: xorg-video-abi-10 but it is not installable
E: Unable to correct problems, you have held broken packages.

```

---

### Post by YannBuntu on 2012-06-14
Hello

> **xLinear said:**
> my screen says "Out of range" and sits there for a few 20 seconds, then it boots into ubuntu.

Here is something that you can try:
run Boot-Repair, click "Advanced options", go to the "GRUB options" tab, tick the "out-of-range" option, apply.
After reboot it should display the GRUB menu.

---

### Post by xLinear on 2012-06-14
> **YannBuntu said:**
> Hello



Here is something that you can try:
run Boot-Repair, click "Advanced options", go to the "GRUB options" tab, tick the "out-of-range" option, apply.
After reboot it should display the GRUB menu.

Hi, i have tried this and i still get "out of range" ill have another look over Boot-Repair, Thanks.

---

### Post by disco_kiza on 2012-07-05
Did U manage to work this one out?

I was told to first install win and then ubuntu witch i did and i there is no windows to boot?

---

### Post by YannBuntu on 2012-07-05
**@xLinear:** do you still have the out-of-range problem?

**@disco_kiza:** welcome among us :) please create [here]("http://ubuntuforums.org/newthread.php?do=newthread&f=333") your own new thread explaining your problem and indicating your [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1").

---

