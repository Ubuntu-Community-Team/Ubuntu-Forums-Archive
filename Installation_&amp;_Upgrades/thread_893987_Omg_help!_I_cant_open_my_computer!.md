---
title: "Omg help! I cant open my computer!"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by ninjip on 2008-08-18
Well I'm really no pro in computers... I inserted the CD I ordered and some installation started after a couple trys. everything went good. atleast thats what I thought... I wanted to connect to my router but I couldnt find how to work it with the help documents. then well I clicked the installation thing on the desktop and then at 20% I got this error. It said I should try and clean my cd. Thing is, I couldn't get my CD drive to open! So well I tried shuting down the computer and reopening. Before shutting down it told me to remove the cd. So I pressed the button took out the cd closed the drive and pressed enter like it said to do. then the computer closed and when i tried reopening it said operating system not found! I tried with the CD aswell! Please help me! I just want a good working OS without spending 150$ for windows XP!

---

### Post by jualin on 2008-08-18
Can you try installing Ubuntu from the LiveCD again?

---

### Post by ninjip on 2008-08-18
By live CD you mean that ubuntu CD that was shipped to me? I tried that already. I tried putting it in the drive rebooting and I tried opening the computer without the CD. All I ever get is operating system not found...

---

### Post by swimmer618 on 2008-08-18
Try removing any debris from the disc and booting to it and installing again. If it continues to happen, the disc is probably bad. If you have a fast internet connection and a cd burner available, you should download a copy of the CD and burn it to a disc.

Find it here: [http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)
if you're unsure of which to download, go with 8.04.1-desktop-i386.

make sure that you have a program to burn an iso file-- don't simply burn the iso file to the disc with the burner built into windows. If you're burning from windows, try [www.cdburnerxp.se](www.cdburnerxp.se)

The "No operating system" message is normal if the install did not complete successfully.

---

### Post by lisati on 2008-08-18
It sounds like you have two issues here, a CD that your computer is having trouble reading, and a failed install.

See [here]("http://www.ehow.com/video_2499_clean-cds.html") for a video on cleaning CDs.

---

### Post by ninjip on 2008-08-18
=/ the CD is brand new no scratches and perfectly clean. I know the install failed but the biggest problem now is how to install anything on my computer now! These things are expensive.. I don't want it to go to waste!

---

### Post by swimmer618 on 2008-08-18
What kind of computer is it? You need to configure your computer to boot from the CD, and how to do that can vary based on who made the computer/motherboard.

---

### Post by jualin on 2008-08-18
Check the BIOS (usually Hitting "delete button" or "f2" when the computer turns on) and make sure that the CD is the first one to boot. You should be able to boot from the CD even if the install failed.

---

### Post by Loaded.len on 2008-08-18
That's my thought as well.  Check to make sure it's actually trying to boot the CD.  If there was no MBR on the HDD the first time it would automatically search other media... but if the BIOS thinks there's an OS on the HDD to hand off to (whether it's good or not) and it's set to boot the HDD first, then you're stuck.  Most newer computers have a one time boot menu (uaually F12 or something during POST) try that and make sure it's set to boot off CD.  

And if it still fails then I'd say you're CD is damaged, or your optical drive might be.

---

### Post by darrelljon on 2008-08-19
1. If your BIOS is set to boot from CD (may not be - even if you booted from the CD once to install) and
2. your CD is clean (which if you've booted from it before it probably is)
you should be able to boot a CD that has live functionality such as Ubuntu. How old is the computer and in particular the CD drive?

---

### Post by Blancmange on 2008-08-19
Oh dear! Your computer's misbehaviour does seem troubling.

I gather this is what's happend so far:
[list]
[*]You had Unbuntu running successfully on the CD (before you asked it to be installed on your hard disc).
[*]You have managed to install and run Ubuntu on your hard disc (ie without the CD).
[*]You had trouble with getting the network or the router to work, so you re-installed Ubuntu.
[*]Something horrible happended and now your PC fails to boot Windows or Ubuntu.
[*]The problem's so bad that you cannot even use the live CD on your PC anymore and you are resorting to using another PC in order to use the Ubuntu Web forum.
[/list]

Anyway, the CD might've been locked in because the eject button was disabled by software (which just happened to die horribly). If you're sure resetting your PC won't harm the data on your discs (or you don't care), you can hit the reset button or turn the power off (and after a good pause) back on to reset the CD drive. It should be able to eject the disc as usual, but beware of the tray spontaneously closing as you grab the disc. CD drives crave human flesh!

I presume your PC's BIOS must already be set up to allow your PC to boot off a CD on startup, else I can't see how you would have gotten so far as to activate the installer, or to even try out the CD before you decided you liked what you saw. It doesn't hurt to check the BIOS settings anyway.

On many PCs, you get to the BIOS by pressing the Del key when invited to by the PC when it starts up. (You might have trouble seeing the inviting message if your LCD screen is slow to turn on). From there, you can go into the Advanced Options page and fiddle with the boot options, where you set up a prioritised list of hard discs, cd-rom drives and the floppy drive to boot from. Removable media usually goes first.

I'm pretty sure whatever OS you have on your PC is munted by now. If you get the live CD going again, you'll have nothing to lose by attempting to re-install.

It's odd that you were having trouble with your router or network. If you have its DHCP (Dynamic Host Configuration Protocol) set up and enabled, any PC (even one with no capacity to remember by virtue of running off an immutable medium such as a compact disc) should be able to use the Internet without any configuration.

If your router's DHCP is disabled, your new Ubuntu system would have to be configured with the usual tedious network stuff: It's own IP address (eg: 192.168.0.75), netmask (eg: 255.255.255.0), default gateway (IP of your router. eg 192.168.0.1), and DNS server IP addresses (provided by your Internet Service Provider).

Given those examples of IP addresses, I'd set up the router's DHCP to hand out addresses 192.168.0.201 to 192.168.0.250 (on the assumption that any fixed IP address anyone choses for their machine will end in a  number between 10 and 100). BTW the gateway the router uses is one provided by your ISP.

Whatever you do with your router and your remaining PCs, be extra careful to write things down and save important stuff.

You have my condolences with regard to your unfortunate experience. You might need a friendly computer geek to help you out in person.

---

