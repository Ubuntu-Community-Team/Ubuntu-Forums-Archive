---
title: "Can't start ubuntu after update"
date: 2021-08-18
forum: Installation &amp; Upgrades
---

### Post by danielth2 on 2021-08-18
Hi, I am having a similar issue here.

I am running Ubuntu 20.04 on an Acer Predator computer, using an Nvidia graphics card (the computer also has an Intel graphics card, but the "nvidia-settings" utility makes sure I always use the Nvidia GPU. This has been working perfectly for a couple years now.

Yesterday I installed updates prompted by Ubuntu (i.e. equivalent to apt-get update) and on reboot the computer stays stuck on the "Predator" logo, before grub appears. I don't know what to do since I can't choose boot options, since I don't reach the grub menu.

Any help greatly appreciated, of course I'm happy to give more details if needed.

---

### Post by coffeecat on 2021-08-18
Post moved to its own thread.

---

### Post by danielth2 on 2021-08-18
Update:

From some googling, I found some people experiencing a similar issue due to the new 5.11 kernel. [https://askubuntu.com/questions/1356344/after-kernel-5-11-update-computer-wont-boot-related-to-nvidia-drivers-kerne](https://askubuntu.com/questions/1356344/after-kernel-5-11-update-computer-wont-boot-related-to-nvidia-drivers-kerne)

Most answers recommended to boot using the older kernel (5.8) but I don't know how to do that when I don't have access to grub (boot freezes before it gets there). I tried pressing escape or f12, but it didn't do anything. Does somebody know how I can get out of this?

---

### Post by maketopsite on 2021-08-18
Same problem with another Acer laptop and ubuntu 20.04. (UEFI) Grub reinstall did not help. Raising boot menu is necessary to start ubuntu.

---

### Post by maketopsite on 2021-08-18
> **danielth2 said:**
> Hi, I am having a similar issue here.

I am running Ubuntu 20.04 on an Acer Predator computer, using an Nvidia graphics card (the computer also has an Intel graphics card, but the "nvidia-settings" utility makes sure I always use the Nvidia GPU. This has been working perfectly for a couple years now.

Yesterday I installed updates prompted by Ubuntu (i.e. equivalent to apt-get update) and on reboot the computer stays stuck on the "Predator" logo, before grub appears. I don't know what to do since I can't choose boot options, since I don't reach the grub menu.

Any help greatly appreciated, of course I'm happy to give more details if needed.

Did you try power off, remove battery, then press Power off / on button and hold for few seconds ?

---

### Post by danielth2 on 2021-08-18
Hi, thanks for your reply. No I've not tried removing the battery; would that produce a "more complete" reboot? Have you tried it yourself?

---

### Post by maketopsite on 2021-08-18
> **danielth2 said:**
> Hi, thanks for your reply. No I've not tried removing the battery; would that produce a "more complete" reboot? Have you tried it yourself?

Hi, you are welcome. It is proven it can solve some similar problems. I was not able to try it so far in this case.

---

### Post by danielth2 on 2021-08-19
Hi, my issue finally got resolved more easily than I thought.

In the end, I managed to bring up GRUB by repeatedly pressing "Shift" during boot (before and during splash screen). From there I simply booted Ubuntu as normal, and everything was working. Then I rebooted, and GRUB showed again normally, without needing to press Shift or anything. So I'm really not sure what happened, but it seems to have fixed itself?

And for the record, it seems I was too quick to blame the 5.11 kernel, as a check now shows that I'm running the 5.4 kernel (with Ubuntu 20.04.2).

---

### Post by danielth2 on 2021-08-19
Re-update, somehow it seems like I simply got into an unstable state.

When starting the computer, either:
- The boot happens normally with no input on my part
- The boot stays stuck on the splash screen and I have to force-shut the computer
- I need to press shift repeatedly at start to make GRUB appear, after which I can normally boot into Ubuntu (and everything works fine)

So I normally manage to get through, but it can take a couple attempts before something works. I would be grateful if anyone has ideas on how to troubleshoot this intermittent issue.

---

### Post by tea for one on 2021-08-19
If you have to press [COLOR="#0000FF"]Shift[/COLOR] to reach Grub, it implies that you have installed Ubuntu 20.04 in Legacy mode?

Can you open a terminal and post the output from:-
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"

```
How old is your device?
Are you dual-booting with Windows 10?

---

### Post by danielth2 on 2021-08-19
Thank you for your reply.

The device is recent (Acer laptop bought new in 2019), and your command returns "UEFI mode". I am indeed dual-booting with Windows 10.

In that case it could be that me pressing Shift actually had nothing to do with grub showing up (as I mentioned, sometimes it just works perfectly normally).

---

### Post by tea for one on 2021-08-19
In UEFI mode, after power on, press the ESC key at, say one second intervals.
Hopefully Grub will appear.

_Other considerations_

I would configure Grub to appear every time because it will easily allow you to enter recovery mode when necessary.
If you have also had to force shut down the PC with power off, you may have inadvertently caused file system damage (which sometimes affects the boot process).
You can generally fix this with **fsck** in a [COLOR="#0000FF"]live[/COLOR] session.

---

### Post by maketopsite on 2021-12-05
> **tea for one said:**
> If you have to press [COLOR=#0000FF]Shift[/COLOR] to reach Grub, it implies that you have installed Ubuntu 20.04 in Legacy mode?

Can you open a terminal and post the output from:-
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"

```
How old is your device?
Are you dual-booting with Windows 10?

Manually raising boot menu is still needed to boot Ubuntu 20.04 LTS

```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
UEFI mode

```

It's approximately 5 years old laptop.
No Windows installed.

---

### Post by tea for one on 2021-12-05
> **maketopsite said:**
> Manually raising boot menu is still needed to boot Ubuntu 20.04 LTS

```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
UEFI mode

```

It's approximately 5 years old laptop.
No Windows installed.

I do not understand your comment
Please start a new thread with more information:-

PC details?
Ubuntu version?
Describe your difficulty?
What happened?
What did you expect to happen?

---

### Post by maketopsite on 2021-12-06
> **tea for one said:**
> I do not understand your comment
Please start a new thread with more information:-

PC details?
Ubuntu version?
Describe your difficulty?
What happened?
What did you expect to happen?

Done here: [https://ubuntuforums.org/showthread.php?t=2469663](https://ubuntuforums.org/showthread.php?t=2469663)

---

