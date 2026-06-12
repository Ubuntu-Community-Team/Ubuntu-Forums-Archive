---
title: "Installing to a USB external drive?"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by crjackson on 2010-03-22
Okay, so my testing laptop LCD died in me.  I want to take one of my external 2.5" usb drives and install from my solid, perfectly stable Karmic laptop.

Will I have any pitfalls as a result?  Will it screw up my primary systems GRUB or file system?

Thanks

---

### Post by ronparent on 2010-03-22
I've installed on a usb memory stick to keep the beta 1 install, isolated for now, and permit me to move it between four computers for testing. This works to leave the individual set-ups unchanged. The proviso is that the grub boot sector and grub be installed on the removable drive. This permits booting to the lucid beta only when the external drive is plugged in and selected as the boot drive (if your bios permits). When the drive is not connected you boot normally as you do now. Hope this is of some help.

---

### Post by crjackson on 2010-03-22
Okay, so now I need real help.  The install went fine but the drive wouldn´t boot.

Now it also wont boot the the internal drive.  I simply get something like

Gurb Error

Grub Rescue>

Now what do I do to repair the internal drive (sda).  Im guessing I need to reinstall grub2 but I havent a clue how to do that.

---

### Post by crjackson on 2010-03-23
Pheww....  Managed to fix it...  I won't make that mistake again.

I'm not able to boot from my 80GB USB drive, but I managed to fix my Grub2 and get back to normal.

---

### Post by ronparent on 2010-03-23
To successfully restrore your grub2, you would have had to run the grub-update. I'm surprised it didn't pickup the install on the 80gb drive, Unless it wasn't plugged in at the time??? I had the opposite results (which I hadn't intended) when I ran grub-update from the install on my external usb drive. It picked up the multiple menu entries for each kernel of my lenghtly 9.04 install on the internal drive along with my win7 install. So now the entire computer (only one of four)can be booted from the external drive when the external drive is selected as boot. I would have to run grub-update from each of the other three computers in the house for the usb installed grub to function simularly on them. 

I'm glad to hear your main computer is back in business. I think that if your external drive is not in your repaired grub menu that you will either have to install the grub boot sector on your externrnal drive booting from the live cd, or run a grub-update from the fixed drive 9.10 installation with the external usb plugged in. The former choice will make the external drive truly portable in that it can be booted from any computer that can bios select the external drive as the boot drive.

---

### Post by crjackson on 2010-03-23
> **ronparent said:**
> To successfully restrore your grub2, you would have had to run the grub-update. I'm surprised it didn't pickup the install on the 80gb drive, Unless it wasn't plugged in at the time??? I had the opposite results (which I hadn't intended) when I ran grub-update from the install on my external usb drive. It picked up the multiple menu entries for each kernel of my lenghtly 9.04 install on the internal drive along with my win7 install. So now the entire computer (only one of four)can be booted from the external drive when the external drive is selected as boot. I would have to run grub-update from each of the other three computers in the house for the usb installed grub to function simularly on them. 

I'm glad to hear your main computer is back in business. I think that if your external drive is not in your repaired grub menu that you will either have to install the grub boot sector on your externrnal drive booting from the live cd, or run a grub-update from the fixed drive 9.10 installation with the external usb plugged in. The former choice will make the external drive truly portable in that it can be booted from any computer that can bios select the external drive as the boot drive.

Are you saying that from the Grub Rescue> prompt, I could have simply typed grub-update and that would have fixed it?

What I did was boot from a LiveUSB stick and reinstall the Grub, then booted and ran grub-update.

---

### Post by ronparent on 2010-03-23
> Are you saying that from the Grub Rescue> prompt, I could have simply typed grub-update and that would have fixed it?

I am not yet familiar enough with grub2 to be able to answer that question. What I am saying is that if your external 80gb had been inserted your 10.04 install on that drive would have been included in your menu when you updated (and that can be done any time). Of course it would create a grub error if the drive was not connected (really minor). Alternatively you can install a grub boot in the mbr of the external drive that would work only if that drive was selected as the boot drive in bios (or by hitting a key to select it at boot time - depends on the computer - ie my hp portable offers an option on the boot screen hitting escape to select a usb drive as boot). I personally prefer the last option because the boot up to the external drive is offered only when you want to use it - it is also portable and can be used on any computer supporting a usb bootto get to the system on that external drive. In any case I'm sure that you can use you rescue disk to place the grub mbr wherever you want.

---

### Post by crjackson on 2010-03-23
> **ronparent said:**
> I am not yet familiar enough with grub2 to be able to answer that question. What I am saying is that if your external 80gb had been inserted your 10.04 install on that drive would have been included in your menu when you updated (and that can be done any time). Of course it would create a grub error if the drive was not connected (really minor). Alternatively you can install a grub boot in the mbr of the external drive that would work only if that drive was selected as the boot drive in bios (or by hitting a key to select it at boot time - depends on the computer - ie my hp portable offers an option on the boot screen hitting escape to select a usb drive as boot). I personally prefer the last option because the boot up to the external drive is offered only when you want to use it - it is also portable and can be used on any computer supporting a usb bootto get to the system on that external drive. In any case I'm sure that you can use you rescue disk to place the grub mbr wherever you want.

Well, the problem was that after the install, nothing worked regardless if the USB drive was plugged in or not.  I couldn't boot to any drive so updating grub was not an option as far as I can tell.

With the USB drive plugged in I got the rescue prompt.
With the USB drive unplugged, i got the rescue prompt.

I finally booted to a LiveUSB thumb drive and, re-installed grub2 to my main drive, and reformatted my external 80GB USB drive.

I would love to be able to boot the external drive, but I've trashed my main drive twice now (lost lots of data first time), so I'm not planning to experiment any more.

---

### Post by ronparent on 2010-03-23
Understandable, since prior disaster have made me more cautious. To the extent that this time I actually disconnected all internal drives prior to installing to the USB stick. I would not have any of the internal drive OS's on my stick's boot menu except that I inadvertently ran grub-update from the 10.04 installed on the drive to correct the booting defaults so that it would boot on it's own.

I am confused by your situation however. You obviously had written the grub 2 mbr to your internal drive but it wasn't finding lucid on the usb???

---

