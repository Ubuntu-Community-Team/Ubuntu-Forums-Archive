---
title: "Intrepid Alpha6 fails to boot"
date: 2008-09-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by aethralis on 2008-09-19
This is about the a6 386 live cd, intrepid a5 live cd and hardy have no problems booting. Tested the cd and its ok. It hangs during the boot (complete freeze ctr+alt+del does not work) and the last message displayed is
[109:836839] usbcore : registred new interface driver btusb

Maybe this is somehow related to the bug [#263059]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263059"). I have also the iwl3945 driver (Lenovo 3000n100). Anyone else experiencing this?

---

### Post by alienexplorers on 2008-09-19
No, Mine ran perfectly with no errors on my home built desktop.

---

### Post by aethralis on 2008-09-19
> **alienexplorers said:**
> No, Mine ran perfectly with no errors on my home built desktop.

I'm very happy about that fact, my home built desktop also boots without problems. Question is more about the connection between the wireless driver and bootability.

---

### Post by Perpetual on 2008-09-19
I can not get any of the Intrepid Alphas to boot on my HP DV6910 laptop.  Hardy works fine.  Same failure as the OP.  Mandriva boots fine as does Vista :)

---

### Post by rbmorse on 2008-09-19
Perpetual, do you know which video chip you have in your HP?  I can't boot Intrepid on my desktop with ATI video without a work-around.

---

### Post by Perpetual on 2008-09-19
> **rbmorse said:**
> Perpetual, do you know which video chip you have in your HP?  I can't boot Intrepid on my desktop with ATI video without a work-around.

NVIDIA GeForce Go 7150M.  Thanks for asking though.

---

### Post by edwarda on 2008-09-19
Perpetual: I have the ibex running on my HP dv9000 but ran into some similar problems.  On the first boot nothing was displayed after a few minutes made the most horrific system beep sound you ever heard.

The solution was to run recovery mode from grub selecting the X configure option from the list afterwards resumed a normal boot.  Finally when gnome has booted up enable the NVIDIA restricted driver.

Subsequent normal boots go (relatively) without a hitch. 

I have a 8600M GS graphics card so this may or may not work for you I think the problem lies with the newer NVIDIA cards not supporting some of the lower resolutions that the open driver falls back on.

hope that is some help to you:)

---

### Post by Perpetual on 2008-09-19
> **edwarda said:**
> Perpetual: I have the ibex running on my HP dv9000 but ran into some similar problems.  On the first boot nothing was displayed after a few minutes made the most horrific system beep sound you ever heard.

The solution was to run recovery mode from grub selecting the X configure option from the list afterwards resumed a normal boot.  Finally when gnome has booted up enable the NVIDIA restricted driver.

Subsequent normal boots go (relatively) without a hitch. 

I have a 8600M GS graphics card so this may or may not work for you I think the problem lies with the newer NVIDIA cards not supporting some of the lower resolutions that the open driver falls back on.

hope that is some help to you:)

Thanks.  Will give it a go tonight.  Out of curiosity, does your DV9000 (same lappy my wife has) have an Atheros wifi card?

---

### Post by edwarda on 2008-09-19
Nope It's an Intel wifi card.

---

### Post by Perpetual on 2008-09-19
> **edwarda said:**
> Nope It's an Intel wifi card.

Problem is, I can not boot the live cd.  I do not see recovery mode in grub when booting the live cd.  Hardy boots and installs fine on this laptop.  Haven't searched launchpad yet.  Will do that a little later.

---

### Post by edwarda on 2008-09-20
Ah didn't realise you were using the live CD.  I used the updater, bit of a mistake to be honest Hardy was running great.  Now preparing for a few weeks of bugs and gremlins :( Someones got to do it I guess.

---

### Post by noworry on 2008-09-22
hey, i am also having a hard time with intrepid alpha 6. Mine is a hp/compaq nc6400 and it is not booting. It is struct after "loading hardware drivers".

I ll try booting from the recovery mode and submit the bug along with the logs. any idea, what are the logs that i have to attach for this kind of problem ?

---

### Post by waspbr on 2008-09-22
unfortunately intrepid has not been a smooth ride for me. Although my laptop has been working fine with intrepid (with a few minor hitches), my desktop is not doing so well. I decided to upgrade from hardy, since it worked so well in my laptop...

what happened was that the computer loads up to the 2.6.27-3 kernel, but just as the spash loader goes off, when the GDM is supposed to pop up, the monitor goes off. I manage to bring it to the shell console with the good old "SHIFT+ALT+F1". but that's where things get scary. 

it keeps on printing an error on the screen every few minutes that says

```
[###.######] ata#: EH pending after 5 tries, giving up
```

where # represents a given digit that changer everytime the error message is printed. 

I thought it might have been something from the update, since I have a separate /home partition, I formated the root partition and tried a fresh install. Same error. 

tried updating, tried installing the fglrx  graphics drivers (radeon HD 3850 AGP), but no cake.

luckly I still have another partition with LinuxMint Elyssa, another with PCLOS and another with win XP. So my PC is still very much usable, however it seems that I will have to wait a bit more for intrepid. 

yes I have already filed a bug report, there seem to be a few others with the same problem

---

### Post by Perpetual on 2008-09-25
I am getting frustrated here.  I am finding that I can not boot any distributions that are using 2.6.27 kernels.  This includes Ubuntu, Fedora and Mandriva.  I have searched through the respective forums and on Google and I am starting to think I am the only person having this problem as I can not find any discussion about this beyond this thread.  I can boot all of the distributions prior to the 2.6.27 kernel.

What do I have to do at boot to get to where I can install a distribution built with 2.6.27?  :confused:

---

### Post by Sandsound on 2008-09-27
> **waspbr said:**
> 

it keeps on printing an error on the screen every few minutes that says

```
[###.######] ata#: EH pending after 5 tries, giving up
```

where # represents a given digit that changer everytime the error message is printed. 


Same here :( it's very annoying

Is it some kind a disk error or... ?

---

### Post by jerrylamos on 2008-09-28
> **Perpetual said:**
> I am getting frustrated here.  I am finding that I can not boot any distributions that are using 2.6.27 kernels.  This includes Ubuntu, Fedora and Mandriva.  I have searched through the respective forums and on Google and I am starting to think I am the only person having this problem as I can not find any discussion about this beyond this thread.  I can boot all of the distributions prior to the 2.6.27 kernel.

What do I have to do at boot to get to where I can install a distribution built with 2.6.27?  :confused:
What you do to get 2.26.27?  I"ve got it on this Thinkpad R31 two ways:
1. Alpha 5, just update the kernel with synaptic if need be.  Alpha's 4 and 6 don't boot on the Thinkpad (Launchpad bug 259385)  DO NOT DO ANY UPDATES!  THEY'LL KILL THE INSTALL!
2. Alpha 6 Xubuntu and Kubuntu kernel 2.6.27 run O.K. (with typical Alpha bugs) on the Thinkpad.  It's the mix of Gnome 2 and kernel 2.6.27 on Ubuntu that doesn't work.

You can get various alpha levels by going to link [http://www.ubuntu.com/testing/hardy/alpha3](http://www.ubuntu.com/testing/hardy/alpha3) replacing the 3 with 4 or 5 or 6.

Beta is due Oct 2 which might be a whole new can of worms.  I'll be giving it a try....

Jerry

---

### Post by fedrox on 2008-10-12
intrepid beta, 2.6.27-7, toshiba a100-170, intel iwl3945. sometimes not booting. stopping at loading hardware drivers.
SOLVED. change the name of your HDD device in /boot/grub/menu.lst and /etc/fstab: not the UUID! the real name: for ex. /dev/sda1.
This works.

---

### Post by fedrox on 2008-10-13
ERRATA CORRIGE: This DOESN'T work

---

