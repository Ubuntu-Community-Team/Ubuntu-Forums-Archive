---
title: "fun with grub2"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by rahilm on 2009-12-02
hello all..
i've been playing around with grub2 recently and decided upon a simple experiment.

I recently installed Windows 7 on my hard disk which obviously wiped out the mbr.

Fine. what i am trying to do is... I have a 1 Gig MicroSd card which is of no use, I want my grub2 on it so that the linux part only shows up when i plug in the car..

The card is bootable...i have booted puppy linux and DSL several times through it..

what i have achieved so far as follows:

memory card is sdc1
```
sudo mount /dev/sdc1 /mnt
```This mounts my drive on /mnt (for practical purposes)

```
sudo grub-install --root-directory=/mnt /dev/sdc
```this installs grub2 on the card.

When I did reboot into my card, I was disappointed to find no menu, just the Command line. After searching I found that the grub-install command did not create a grub.cfg file on the card..

So , I did
```
configfile (hd1,6)/boot/grub/grub.cfg
```this makes use of the grub.cfg file i have it on sda6.
Everything was normal after that..point to note is that when i run grub2 from the card my hard disk becomes (hd1) which is normal(i.e was same in grub legacy)

My question is ..Is there a way to create a grub.cfg file in the card. I tried copying the one in sda6 but then grub2 hung up at startup.

Also , how do you update such a grub.cfg ..since editing it directly is forbidden (i use update-grub2 in ubuntu)


Note: sda6 contains Ubuntu 9.10
Grub version is 1.97 beta4

---

### Post by darkod on 2009-12-02
This article has instructions how to reinstall grub2 and also includes instructions what to do if missing grub.cfg:
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

Look at number 2) Using Ubuntu 9.10 liveCD

You update grub2 with sudo update-grub
but it all depends what exactly you want to update/change. Grub2 basics:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by rahilm on 2009-12-02
I think you didn't get my question? I don't want to restore grub2
I know how to restore grub2, I did it once

just want to know how to install grub2 to a usb disk

ps. This is not a help request just an experiment

---

### Post by phillw on 2009-12-02
> **rahilm said:**
> I think you didn't get my question? I don't want to restore grub2
I know how to restore grub2, I did it once

just want to know how to install grub2 to a usb disk

ps. This is not a help request just an experiment

Creating bootable removable devices, with all sorts of contortions and mixes is well covered at [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)  You could do a lot worse than have a pop over there and see how they a) put 9.10 onto a removable device - and possibly the section on putting multi-boot options onto a removable device.

Regards,

Phill.

---

### Post by wojox on 2009-12-02
What if you ran:

```
sudo grub-mkconfig
```

to make a new grub.cfg file? May work or not.

---

### Post by rahilm on 2009-12-02
My intention is not running ubuntu 9.10 on a pen drive !!
My intention is making grub2 run satisfactorily in it

I can try things but I don't want to mess up the windows MBR accidently so I am asking if any of you had any success with such an experiment

regards

---

### Post by phillw on 2009-12-02
> **rahilm said:**
> My intention is not running ubuntu 9.10 on a pen drive !!
My intention is making grub2 run satisfactorily in it

I can try things but I don't want to mess up the windows MBR accidently so I am asking if any of you had any success with such an experiment

regards

My intention of you using the pendrivelinux tutorial was to actually put grub2 onto a pen-drive. However, as you aren't going to have any operating system to run Grub2 on your pendrive - how are you expecting it to work ?

The MBR is very small and hands control over to a boot-loader in either win, or grub2 very quickly. I'm not too sure if you could possibly install ubuntu onto your pen-drive, create your Grub2 boot-loader and then remove ubuntu from the pen-drive. Have a play ;-)

Regards,

Phill.

---

### Post by darkod on 2009-12-02
> **rahilm said:**
> I think you didn't get my question? I don't want to restore grub2
I know how to restore grub2, I did it once

just want to know how to install grub2 to a usb disk

ps. This is not a help request just an experiment

My point was that the process to restore and install grub2 is more or less the same. It depends which location you are installing to and what do you use as root device.

In case you want to boot your ubuntu which is on the internal hdd but with grub2 which is on usb stick, use the hdd partition where you need to enter the device name for root, and use the stick as destination to install grub2.

As for your question whether I have tried it, NO. I am running things the simple way, with grub2 on my MBR and it works perfectly from day 1. IMHO you have more chance to mess things up by trying non-standard procedures (if you don't have any experience with them), than letting grub2 take over the MBR of the hdd.

---

### Post by oldfred on 2009-12-02
I have not tried it but Herman seems to have some info. The link takes you one or two paragraphs above where it should be.

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-install](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-install)

---

### Post by rahilm on 2009-12-03
I managed to get it correct:
just did:
```
sudo grub-mkconfig -o /mnt/boot/grub.cfg
```

and everything is working the way I want it..

Thank You guys...for helping me out in the experiment. i now know more about grub2 now. I can now put grub2 on my MBR.

---

