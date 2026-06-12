---
title: "Ubuntu does not boot"
date: 2012-08-30
forum: Installation &amp; Upgrades
---

### Post by bikeryder22 on 2012-08-30
okay, so i installed ubuntu (formatted my HDD before installation) and it installs fine but when i boot it up it is a purple screen and then 5-10 seconds later it gets all pixelated and says monitor going to sleep, also it dose not boot..

can you guys please quick reply? 

thanks


EDIT: also right now i am on the option "try ubuntu"

---

### Post by MG&amp;TL on 2012-08-30
This sounds like a graphics problem.

What graphics card do you have?

Also, in your live session, open a terminal (purple box, press Ctrl-Alt-T) and type:

```
lspci
```

and paste output here. Thanks!

---

### Post by bikeryder22 on 2012-08-30
> **MG&TL said:**
> This sounds like a graphics problem.

What graphics card do you have?

Also, in your live session, open a terminal (purple box, press Ctrl-Alt-T) and type:

```
lspci
```and paste output here. Thanks!
i have NVIDIA GeForce 9500Gs

and this is the output

> 00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA Controller [RAID mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:05.0 FireWire (IEEE 1394): LSI Corporation FW322/323 (rev 70)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 Network controller: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe
05:00.0 VGA compatible controller: NVIDIA Corporation G96 [GeForce 9500 GS] (rev a1)



---

### Post by darkod on 2012-08-30
For Nvidia, did you try to boot with nomodeset?

At the grub boot menu (hit Shift when booting if you have only ubuntu and there is no grub menu), highlight the ubuntu entry and hit 'e' for edit. That will show the boot lines.

Using the arrows keys, move towards the end of the line starting with linux. Add nomodeset after the 'quiet splash'. Hit Ctrl + X or F10 to boot.

If that worked, open Additional Drivers and activate the driver offered. The above procedure is not permanent, so if activating the driver didn't work, you will need to use it every time you boot until you make it permanent.

Lets see if it works first, and then we can talk about making it permanent.

---

### Post by bikeryder22 on 2012-08-30
> **darkod said:**
> For Nvidia, did you try to boot with nomodeset?

At the grub boot menu (hit Shift when booting if you have only ubuntu and there is no grub menu), highlight the ubuntu entry and hit 'e' for edit. That will show the boot lines.

Using the arrows keys, move towards the end of the line starting with linux. Add nomodeset after the 'quiet splash'. Hit Ctrl + X or F10 to boot.

If that worked, open Additional Drivers and activate the driver offered. The above procedure is not permanent, so if activating the driver didn't work, you will need to use it every time you boot until you make it permanent.

Lets see if it works first, and then we can talk about making it permanent.
not sure what a nomodeset is but i did some research and i got acpi_osi=, is that correct? if it is i am still getting this same problem

---

### Post by darkod on 2012-08-30
No, nomodeset is the parameter value. If you look at the boot lines as described above, the line starting with 'linux' at the and will have something like '.... quiet splash --'

You move the cursor there, and add the word nomodeset, then you press Ctrl + X or F10 to boot with this modified parameters.

---

### Post by bikeryder22 on 2012-08-30
> **darkod said:**
> No, nomodeset is the parameter value. If you look at the boot lines as described above, the line starting with 'linux' at the and will have something like '.... quiet splash --'

You move the cursor there, and add the word nomodeset, then you press Ctrl + X or F10 to boot with this modified parameters.

okaay, ill try and keep you updated

EDIT it dosnt even come up with anything mate like i cant make any selections on what to boot ect, just a purple screen for 5-10 seconds then it gets pixelated. Also dose the noise for the login page sound like bongos? cause i hear those everytime i reboot..

---

### Post by MG&amp;TL on 2012-08-30
> **bikeryder22 said:**
> not sure what a nomodeset is but i did some research and i got acpi_osi=, is that correct? if it is i am still getting this same problem

All you've got to do is edit the kernel parameters as shown above (sounds scary, not really) and add "nomodeset" to the end of the line starting with 'linux' - see [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Hope that helps you a bit.

---

### Post by darkod on 2012-08-30
> **bikeryder22 said:**
> okaay, ill try and keep you updated

EDIT it dosnt even come up with anything mate like i cant make any selections on what to boot ect, just a purple screen for 5-10 seconds then it gets pixelated. Also dose the noise for the login page sound like bongos? cause i hear those everytime i reboot..

It seems like you are missing it. If you have only ubuntu, it doesn't stop to display the grub menu because there is no point if you have only one OS.

So you have to be quick with the Shift, start pressing it right after the BIOS POST ends. If you have a fast computer it will do that quite fast, you have to get the moment right.

Otherwise, once it starts loading ubuntu, the Shift won't bring it back to the grub menu.

---

### Post by bikeryder22 on 2012-08-30
> **darkod said:**
> It seems like you are missing it. If you have only ubuntu, it doesn't stop to display the grub menu because there is no point if you have only one OS.

So you have to be quick with the Shift, start pressing it right after the BIOS POST ends. If you have a fast computer it will do that quite fast, you have to get the moment right.

Otherwise, once it starts loading ubuntu, the Shift won't bring it back to the grub menu.
mate like i said it goes to a purple pixelated screen, it dose not show me a grub menu or anything.

btw do you have skype or something so i could show your from my phone?

---

### Post by mörgæs on 2012-08-30
Please use less drama in your thread title next time.

---

### Post by bikeryder22 on 2012-08-30
> **mörgæs said:**
> Please use less drama in your thread title next time.

i need help with this asap, thats why my title is like that sorry, but i have no other OS installed besides ubuntu but something is going wrong with it

---

### Post by MG&amp;TL on 2012-08-30
At the end of BIOS, start holding the shift key. GRUB is the bootloader, and obviously the key combo won't work if you're already past that stage (purple screen). That make it clearer?

BIOS (start holding shift here)-> GRUB (hold shift here!) -> OS

---

### Post by bikeryder22 on 2012-08-30
> **darkod said:**
> For Nvidia, did you try to boot with nomodeset?

At the grub boot menu (hit Shift when booting if you have only ubuntu and there is no grub menu), highlight the ubuntu entry and hit 'e' for edit. That will show the boot lines.

Using the arrows keys, move towards the end of the line starting with linux. Add nomodeset after the 'quiet splash'. Hit Ctrl + X or F10 to boot.

If that worked, open Additional Drivers and activate the driver offered. The above procedure is not permanent, so if activating the driver didn't work, you will need to use it every time you boot until you make it permanent.

Lets see if it works first, and then we can talk about making it permanent.

okay, it worked (now i uinderstand) but now where do i go to get my drivers so i dont have to do that everytime i boot/?

---

### Post by darkod on 2012-08-30
> **bikeryder22 said:**
> mate like i said it goes to a purple pixelated screen, it dose not show me a grub menu or anything.

btw do you have skype or something so i could show your from my phone?

You should read more carefully what we say. The purple screen is usually after the grub menu has passed and the ubuntu OS has started loading. You need to press Shift earlier.

Although the grub menu also has purple background, but you would know if the menu shows. Besides, since you have only ubuntu, the menu is not displayed.

---

### Post by MG&amp;TL on 2012-08-30
> **bikeryder22 said:**
> okay, it worked (now i uinderstand) but now where do i go to get my drivers so i dont have to do that everytime i boot/?

Head to 'additional drivers' dialog. Open the dash (windows key) and search for it there. :)

---

### Post by darkod on 2012-08-30
> **bikeryder22 said:**
> okay, it worked (now i uinderstand) but now where do i go to get my drivers so i dont have to do that everytime i boot/?

Just open the Dashboard (by hitting the first button in the left side toolbar with the logo, or pressing the windows key on the keyboard), and start typing in the search line "Additional..."

The search will find any program that exists for you. So, when it finds Additional Drivers, open that and see if it offers a video driver. If it does, activate it.

---

