---
title: "Flash BIOS in Ubuntu (Advent 4211 needs MSI Wind U100 Bios)"
date: 2014-04-08
forum: Installation &amp; Upgrades
---

### Post by drnebulous on 2014-04-08
Hello,
I have an Advent 4211 which I wish to overclock. However, to do this I would need the MSI Wind U100 BIOS. I am unsure how to go about doing this. I have been on the MSI website, and the tools seem to be for Windows? Even on Windows I wouldn't know how to this.
I have used Ubuntu for some years now and can do most general things in terminal, but may struggle with more complex projects. Could someone please give me simple instructions on how to achieve this? The computer is running Ubuntu 12.04 with the recent version of the LXDE desktop environment.

I have looked everywhere for information on how to do this, but with no success.

Dr Nebulous

---

### Post by Double.J on 2014-04-08
Hi there!

Welcome to the forums!

ah yes bios updates are often issued through .exe applications. Usually you don't need to 'do' anything; you download the tool, if then flashes the bios for you and viola! I've done it on 10's of machines through the years.

in short. Use windows. Do not use wine. You don't want to botch the bios!

if windows flashing is not viable, you can make a live usb of [freedos]("http://www.jessek.co.nz/2012/11/flashing-bios-with-freedos-live-usb.html?m=1") to do the job for you! 


Best of luck

Jj

---

### Post by Mark Phelps on 2014-04-08
BEFORE you attempt to flash the BIOS, make sure that BOTH of the following are true:
1) You have a way to save the current BIOS to media that can be used to restore it, should that become necessary
2) You can do a BIOS restore using the saved media without having to boot into Windows or an on-disk OS

If either is NOT true, any problem you risk turning your PC into a "brick", should anything go wrong with the BIOS update!

---

### Post by drnebulous on 2014-04-09
Hi!
How would I go about doing this in FreeDOS? And how would I save the current BIOS? If the BIOS flash did go wrong, how would I use the old BIOS to fix the problem? Would I still have to save the BIOS even if I did it in Windows?
Thanks,
Dr Nebulous

---

### Post by drnebulous on 2014-04-09
I have just looked at how to flash the BIOS via FreeDos on this site [https://wiki.archlinux.org/index.php/Flashing_BIOS_from_Linux](https://wiki.archlinux.org/index.php/Flashing_BIOS_from_Linux) but it seems really confusing! Please would someone simplify this for me! I am really worried about wrecking the computer, but I really need the extra speed of the overclock (provided by the MSI U100 BIOS) for some of my projects.

Thank you for your help,
Dr Nebulous

---

### Post by Mark Phelps on 2014-04-09
> How would I go about doing this in FreeDOS? The instructions are straightforward -- but it requires running individual commands. 
> And how would I save the current BIOS?The instructions for saving the BIOS are in the linked thread.
> If the BIOS flash did go wrong, how would I use the old BIOS to fix the problem? You would boot from the FreeDOS disketted you made from the instructions and reflash the BIOS from the copy you saved to that diskette.  Note that if the BIOS is larger than would fit on a diskette, a LOT more work is involved.
> Would I still have to save the BIOS even if I did it in Windows?Generally, motherboard manufacturers provide BIOS flashing utilities that run in Windows.  You ALWAYS need to save the current working BIOS because any number of things can go wrong.  The utility run in Windows simply makes that an easier thing to do.

Folks tend to treat BIOS flashing with the same cavalier attitude that they treat updating apps or drivers -- and that is a serious mistake!   IF you are not comfortable doing this, then forget about flashing the BIOS.

---

