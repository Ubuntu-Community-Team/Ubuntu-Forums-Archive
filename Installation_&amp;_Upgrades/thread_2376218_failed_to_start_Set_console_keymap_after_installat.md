---
title: "failed to start Set console keymap after installation problems"
date: 2017-10-31
forum: Installation &amp; Upgrades
---

### Post by ludo-calabrese on 2017-10-31
Hello,
I'm using an HP 15-bw039 and running ubuntu 16.04.3 LTS or rather trying to run. I'm currently writing from a live USB. I'm not completely sure that this is the right subforum, but I wanted to stress how the problem happened after having some trouble with the installation and in fact might be likely related. If you think it's appropriate to move the thread elsewhere, please do.

FAILED TO START SET CONSOLE KEYMAP

The problem I'm having right now is shown in the the two pictures below. This happens when I try to boot normally without the bootable usb stick I'm using now.

1) [https://pasteboard.co/GRvHPJX.jpg](https://pasteboard.co/GRvHPJX.jpg)
2) [https://pasteboard.co/GRvJcav.jpg](https://pasteboard.co/GRvJcav.jpg)

When I boot into ubuntu, I get the error message:

Failed to start Set console keymap

and a bunch of other things below till I get a Show Plymouth Screen and the the computer just hangs there. I cannot login into ubuntu.

By pressing ctrl+alt+f1, I am able to login anyway in tty. Here I execute the command suggest in the first picture, ie, 

See 'systemctl status keyboard-setup.service' for details.

and you can see the output in the second picture. I don't know how to interpret it and any help would be appreciated.

INSTALLATION TROUBLES BEFORE

Now so far the problem does not look very different from questions like --> [https://askubuntu.com/questions/848652/system-will-not-boot-after-reconfiguring-keyboard-configuration-and-installing-c](https://askubuntu.com/questions/848652/system-will-not-boot-after-reconfiguring-keyboard-configuration-and-installing-c) or --> [https://ubuntuforums.org/showthread.php?t=2306009](https://ubuntuforums.org/showthread.php?t=2306009) , but in fact this is just the latest of a string of problems I've been having, so I better ask and explain the whole story, since they might very well be related.

So the computer is brand new. It's got windows 10 preinstalled. I wanted to get rid of it and install ubuntu 16.04. I put the iso file in a usb stick and install ubuntu by selecting 'erase disk and install ubuntu'.

Though I had to use a little fsck, the installation appeared to have worked. I turn on the computer, I see the grub menu, select ubuntu and log in without problems. 

In fact, a couple of things were weird already. For one thing, every time I booted ubuntu, I got a flash as in the picture above right after selecting ubuntu in the grub menu.

[https://pasteboard.co/GRvJCQA.jpg](https://pasteboard.co/GRvJCQA.jpg)

For another one, windows seems to be still in the computer. Below a couple of screenshot from gparted. Is this normal?

[https://pasteboard.co/GRvJS1Z.png](https://pasteboard.co/GRvJS1Z.png)
[https://pasteboard.co/GRvKaCR.png](https://pasteboard.co/GRvKaCR.png)

At this point, I realized I should have already asked here or on stackexchange, but I went on and played with ubuntu a little bit.

(as a side remark, annoyingly one thing that also didn't work was wifi. Turns out that is a problem between the wifi chip I have and ubuntu [https://ubuntuforums.org](https://ubuntuforums.org), still I thought I'll buy a wifi adapter and sooner or later they will release the linux driver for the chip)

I downloaded a couple of things, chrome, latex and so on and the computer got frozen at a point during download. I didn't think anything of it, sometimes os's get stuck after all, but I did a very stupid thing right after. Ctrl + Alt + F1 didn't work, so I went ahead and did a hard reboot.

At this point I got an error saying:
error: failure reading sector 0x0 from hd2
error: no such device: f797dcf3-569c-4d86-524e4d0fcqcq

At this point, I used the live usb again and ran boot repair. Grub reappered the normal way and I booted ubuntu. Once again, the computer asked to me use fsck and I did, this time it took a long time compared to the previous time I used fsck, I must have been clicking yes to all the fixes for five or ten minutes. Below the screen with the fsck suggestion:

[https://pasteboard.co/GRvLp8mF.jpg](https://pasteboard.co/GRvLp8mF.jpg)

Anyway after that, I found the error I started the post with.

USB STICK TROUBLES

Finally, I also get this error when booting via the usb stick:

[https://pasteboard.co/GRvLVdW.jpg](https://pasteboard.co/GRvLVdW.jpg)

which looks very similar to the other picture except for the absence of fsck.

After a while, ubuntu loads anyway if I use the usb stick, but I can see that screenshot a few times before finally having ubuntu ready. This error also appeared either after installing ubuntu or after the hard reboot.

Here's the boot info as well: [http://paste.ubuntu.com/25860154/](http://paste.ubuntu.com/25860154/)

--------------------------------------------------------------------------------------------

You can see I hardly know what I am doing, I definitely should have been more careful. Thanks in advance for any help, if I missed anything describing what happened or if you need more info, please let me know.

---

