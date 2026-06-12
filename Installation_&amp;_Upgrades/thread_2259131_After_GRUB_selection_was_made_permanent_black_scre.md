---
title: "After GRUB selection was made permanent black screen appears"
date: 2015-01-02
forum: Installation &amp; Upgrades
---

### Post by iums1 on 2015-01-02
Hi,

I'm currently trying to install Lubuntu via a bootable USB device next to a windows installation but after it booted from USB and I made a selection "Try Lubuntu before installing" it goes into a permanent black screen and I have to restart the system by pressing the reset button. What could cause this and how do i fix it?
I exchanged the USB device, i used different ISO utilities like rufus, unetbootin and others, I tried different Ubuntu distros but it's the same outcome every time.

My System:
[IMG]http://i58.tinypic.com/jigd42.png[/IMG]

---

### Post by Bucky Ball on 2015-01-02
When you get to the 'Try Lubuntu' or 'Install Lubuntu' option screen hit F6 and try using the 'nomodeset' option. Might work.

The black screen smells a bit like a graphics issue, and this could by pass that problem.

You can also choose 'Something Else' and create the partitions manually instead of letting Lubuntu do the default 'alongside' install. That can sometimes be problematic. You need to have the space to install Ubuntu to, naturally, but if you are running Win7 or up you should use the disk management app in there to shrink the Windows partition if you need to, not the Gparted tool in Ubuntu.

Hope that gives a few clues.

---

### Post by iums1 on 2015-01-02
> **Bucky Ball said:**
> When you get to the 'Try Lubuntu' or 'Install Lubuntu' option screen hit F6 and try using the 'nomodeset' option. Might work.

That worked. I read in another post that you have to press E and exchange the term "quiet" with "nomodeset".
I installed Lubuntu successfully and rebooted but now none of the installed operating systems boots at all. Neither windows nor Lubuntu boots after the mainboard vendor logo. It just goes into a black screen. I think it has something to do with my GPU. I guess it's too modern for Linux.

---

### Post by yancek on 2015-01-02
You did not indicate which version of windows you are using or whether you are using UEFI/GPT or the standard BIOS.  That is significant information and not installing both systems with the same method will cause this sort of problem.

---

### Post by grahammechanical on 2015-01-02
You have what is called hybrid graphics. And that makes the situation much more complicated. You can choose to set the BIOS/UEFI to use one graphic adapter or the other but to use both with any kind of usefulness you will need Ubuntu/Lubuntu 14.04.1 and either Bumblebee or the latest Nvidia proprietary video driver and maybe Indicator Prime.

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

[http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html](http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html)

[http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html)

This is after you have made sure that both Windows and Lubuntu are installed in the same mode - either EFI mode or Legacy mode.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

