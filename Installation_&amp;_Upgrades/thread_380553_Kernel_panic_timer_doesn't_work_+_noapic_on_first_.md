---
title: "Kernel panic: timer doesn't work + noapic on first boot"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by Mau on 2007-03-09
Hello,
I just finished building a new system and I am now trying to install Ubuntu on it.

The motherboard is a Gigabyte nForce 570: [http://www.newegg.com/Product/Product.asp?Item=N82E16813128014](http://www.newegg.com/Product/Product.asp?Item=N82E16813128014).

Everything checks out okay except when I try to boot from the live CD to install.  I get to the boot screen and select start.

I then get:

```
.
Decompressing Linux...done.
Booting the kernel.
[ 42.02938] Kernel panic - not syncing: IO-APIC + timer doesn't work!  Try using the 'noapic' kernel parameter.
[ 42.029572] 
```

I half expected this (as I think I ran into the same problem a while ago on a different system), but I can't remember how to set the noapic boot parameter. I looked up on the forum and it set to press F6 and type in 'linux noapic', but it tells me that there is no bootable image named 'inux'.

How should I get around this?  I have not verified that this is true for my board, but the board should be running LinuxBIOS.

Thanks!

---

### Post by mac.ryan on 2007-03-09
I don't know if this will work for you (and if it does is just a workaround, not an answer to your problem...). However, I get the same error sometimes when I reboot the system after a power failure.

In my case, launching ubuntu in recovery mode and then again in normal mode fixes the problem.

---

### Post by Mau on 2007-03-09
I figured out that if you press F6 during the countdown to boot and then type in 'noapic' it will work fine.

---

### Post by Beruka on 2007-03-11
yeah that works but good luck when you try to boot from the physical drive the first time.,,,,

---

### Post by Mau on 2007-03-16
> **Beruka said:**
> yeah that works but good luck when you try to boot from the physical drive the first time.,,,,

It actually worked 100%.  :)

---

### Post by erdomi on 2007-03-24
When exactly do you press F6?  I am having the same problem but my system doesn't seem to respond to F6.

Thanks, 
erdomi

---

### Post by Mau on 2007-03-25
After your BIOS has posted (AKA is done), and you see the Kubuntu menu screen from the CD, press F6 while the counter is still counting down.  A window will popup with a bunch of junk in it.  Add 'noapic' after that (make sure there is a space) and press enter.  The system should boot.

---

### Post by masteryurez on 2007-07-14
> **Mau said:**
> Hello,
I just finished building a new system and I am now trying to install Ubuntu on it.

The motherboard is a Gigabyte nForce 570: [http://www.newegg.com/Product/Product.asp?Item=N82E16813128014](http://www.newegg.com/Product/Product.asp?Item=N82E16813128014).

Everything checks out okay except when I try to boot from the live CD to install.  I get to the boot screen and select start.

I then get:

```
.
Decompressing Linux...done.
Booting the kernel.
[ 42.02938] Kernel panic - not syncing: IO-APIC + timer doesn't work!  Try using the 'noapic' kernel parameter.
[ 42.029572] 
```I half expected this (as I think I ran into the same problem a while ago on a different system), but I can't remember how to set the noapic boot parameter. I looked up on the forum and it set to press F6 and type in 'linux noapic', but it tells me that there is no bootable image named 'inux'.

How should I get around this?  I have not verified that this is true for my board, but the board should be running LinuxBIOS.

Thanks!


I have exactly the same motherboard as you and I got the same problem.
I hit F6 and wrote noapic and yes, the system started. I installed Ubuntu 7.04 and rebooted but when GRUB has loaded I got the same problem again? Do you have the same problem?

Please help..

---

### Post by masteryurez on 2007-07-14
I have a conclusion of the noapic problem. Just follow the steps and it should work just fine. 

1, Start you computer and boot from CD.
2, Press F6 to get the command-line
3, Write noapic after quiet splash like this: 
```
quite splash noapic --
```4, Your system should now boot like normally.
5, Install Ubuntu and reboot.
6, When Grub count down from 3, 2, 1, 0 press "Esc" to get into GRUB.
7, Mark the kernel you usually boot from and press "e" to edit option of your kernel.
8, Mark kernel and press "e" to edit.
9, You should now get a text that says this: ```
<b-7056-4774-aa87-d94cfb40011c ro quiet splash locale=sv_SE
```(note that I have swedish language so sv_SE is just for swedish language. If you have english language it says en_GB)
10, After the text locale=sv_SE do a space then write noapic like this: 
```
<b-7056-4774-aa87-d94cfb40011c ro quiet splash locale=sv_SE noapic
```and press enter.
11, Press "b" to boot and your system would now boot. (Note that this option is only for this time you start your computer so now I'm going to learn you how to do this for everytime you boot. 
12, After your new Ubuntu installation has started up. Start a terminal and write this:
```
sudo gedit /boot/grub/menu.lst
```13, Go down to the selection that says: ## ## End Default Options ##
14, You would now see some text like this: 
```
title        Ubuntu, kernel 2.6.20-16-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=33a74983-e4ff-41c0-9e45-caea823ce8af ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=33a74983-e4ff-41c0-9e45-caea823ce8af ro single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=33a74983-e4ff-41c0-9e45-caea823ce8af ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=33a74983-e4ff-41c0-9e45-caea823ce8af ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet
```15, After the text that says ro quite splash write noapic and do this for every kernel but don't after /boot/memtest86+.bin
16, Save the file and restart your computer. You should now start Ubuntu without any problem. 

(Just note that you must do this everytime you update your kernel.)

I hope this guide was helpful. 

Good luck Ubuntu users.

// Masteryurez

---

