---
title: "Boot Issue for dual boot Ubuntu 22.04/Windows 11 Setup"
date: 2024-03-22
forum: Installation &amp; Upgrades
---

### Post by chesshawk on 2024-03-22
I have a Dell computer running a Ubuntu 22.04/Windows 10 dual boot  setup. It was working pretty well, but recently I've no longer been able  to enter the boot menu to select which OS to boot or enter the BIOS,  even when I press the appropriate keys. When I do press F2 or F12,  the keys do something, because my computer will hang forever at a black  screen leaving me only one option to shutdown and repower. My computer  can boot normally, only into Ubuntu, if I press no keys.


 I tried changing the GRUB-TIMEOUT-STYLE to the menu, but this did not bring me to a menu either.

 I used systemctl reboot --firmware-setup to reboot my  system forcibly into the BIOS, but this only crashed and failed to boot  properly. I get an error that says "software reset failed -524 and UBSAN  array-index-out-of-bounds in a virtual box directory". I don't use a  virtual box to boot Ubuntu, it's booting from hardware, I'm using the  virtual box for something else.

I also made a post here but no one seemed to know anything: [https://askubuntu.com/questions/1506510/ubuntu-dual-boot-setup-unable-to-launch-into-bios-or-boot-menu?noredirect=1#comment2643061_1506510](https://askubuntu.com/questions/1506510/ubuntu-dual-boot-setup-unable-to-launch-into-bios-or-boot-menu?noredirect=1#comment2643061_1506510)


 
I installed boot repair and ran the boot-info,  which gave me this result: [https://paste.ubuntu.com/p/QNbPrZCbjD/](https://paste.ubuntu.com/p/QNbPrZCbjD/)

I am very happy to run the default repair to see if this will fix the issue, but I am in no rush, so I thought I would ask here first. My computer works fine, and I don't need to go back into Windows for any specific purpose. 

One thing that baffles me is how this error occurred. If anybody has an inkling of the answer, could they tell me how I got this error so I can avoid it in the future?

---

### Post by tea for one on 2024-03-23
> **chesshawk said:**
>  When I do press F2 or F12,  the keys do something, because my computer will hang forever at a black  screen leaving me only one option to shutdown and repower. My computer  can boot normally, only into Ubuntu, if I press no keys.
If your dedicated keys to access UEFI settings and PC boot menu are not behaving correctly, then it may be worth a visit to a Dell support site.
> **chesshawk said:**
> I used systemctl reboot --firmware-setup to reboot my  system forcibly into the BIOS, but this only crashed and failed to boot  properly. I get an error that says "software reset failed -524 and UBSAN  array-index-out-of-bounds in a virtual box directory". I don't use a  virtual box to boot Ubuntu, it's booting from hardware, I'm using the  virtual box for something else.
You did prefix with sudo?
```
[s]sudo systemctl reboot --firmware-setup[/s]
```
Forget that suggestion - I had no idea that it worked without sudo.
We live and learn, don't we.
> **chesshawk said:**
> My computer works fine, and I don't need to go back into Windows for any specific purpose.
If you are adventurous, remove the Ubuntu disk (sda) and see if the UEFI firmware displays the Windows Boot Manager?
If both disks are removed (i.e. no OS available), some UEFI firmware automatically jump into the UEFI setup pages?
> **chesshawk said:**
> One thing that baffles me is how this error occurred. If anybody has an inkling of the answer, could they tell me how I got this error so I can avoid it in the future?
My gut feeling is that you will have to explore solutions concerning the UEFI firmware - possibly an upgrade if available.

---

### Post by oldfred on 2024-03-23
What were results of "cold" boot as suggested by oldfred. :)
You have to fully power down, remove power cord, hold power switch to drain any remaining power & then press correct key to get into UEFI/BIOS. Still can be quick, so may have to try more than once.
Dell is usually f2 to get into UEFI/BIOS.

My newer Dell laptop with Intel 11th gen calls it BIOS. But when in "BIOS" it say its UEFI only.
Dell often has firmware updates, an older system may still have some UEFI firmware updates.

---

### Post by chesshawk on 2024-03-23
Well, oops, sorry for not listening to you the first time oldfred! I tried another cold boot and this time it worked! I can access the bootloader/BIOS. I also now see a Dell logo when I boot. previously I saw no Dell logo, only the Ubuntu logo. 

 I tried to do the cold boot previously but it seemed ineffective. I also had the same problem this time as well, but I decided to give it a couple shots because I got lucky and saw the Dell logo appear once; I got really excited. Previously I was not unplugging my computer and cycling the power by pressing the power button several times. However, when plugging in my computer again, my computer would partially turn on and then turn off again, without me pressing the power button. I think this was interfering with the process of the cold boot. To get around this, I left everything plugged in, turned off the power strip, then cycled the power button several times. Then when I turned on the power strip, the computer only booted once, and properly at that.

Thank you very much oldfred, and I clearly should have taken you more seriously the first time! Next time I guess for the next ignorant person who doesn't know what a cold boot is you should explain it for them, I did not know I had to unplug the computer for cold boot when you told me a few weeks ago. I only shut down, and waited a bit before restarting, which had no effect. Thank you for being tech support for so many random strangers on the internet. I really appreciate it. 

I will say that this problem began when I relocated my computer from one part of my house to another, which involved unplugging my computer and then plugging it back in, perhaps improperly. I am not sure why when I plug in my computer it turns on for half a second and then turns off again. It seems like power surges in when I plug it in, but not sure what it is doing or why it breaks things. If someone understands what happened I would love to know.

And yes, to tea for one, I did use sudo to reboot the system, just didn't include when I posted it. I could try removing the HDD, to force the system to try to use the windows boot loader, I didn't think of that. But since it's fixed I guess I will leave that question unanswered for now.

---

### Post by oldfred on 2024-03-23
Glad you got it working.
Cold boot does not always work or work first time. Various capacitors or other parts hold a charge for a while, so system does not see a full reset.

With laptops even more difficult as you usually have to remove battery. Some have special keys that only vendors help desk knows.

Some system only fully reset UEFI/BIOS with jumper pins on motherboard. I had to do that once and those pins are tiny, even with needle nose pliers difficult to get correct.

---

