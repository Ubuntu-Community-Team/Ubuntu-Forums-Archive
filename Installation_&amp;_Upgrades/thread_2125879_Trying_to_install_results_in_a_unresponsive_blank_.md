---
title: "Trying to install results in a unresponsive blank screen – UEFI / 64-bit version"
date: 2013-03-15
forum: Installation &amp; Upgrades
---

### Post by kiwi8mail on 2013-03-15
Hi all – I’m trying to follow the instructions on this page:  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

I’m trying to do an initial check out of an newly purchased computer with no pre-installed operating system currently installed (a “blank” system from Novatech in the UK).   I’m trying to boot from Ubuntu 12.10 on a USB stick.   It’s a Windows 8 capable computer, and uses UEFI so I am using the 64-bit version of Ubuntu (as advised on his page: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)). 

The computer boots almost immediately from the USB stick to the Ubuntu install menu.   However, selecting both “Try Ubuntu without installing” and “Install Ubuntu” both have the same result – a blank unresponsive screen that goes no further.

In BIOS:
- the boot options all have UEFI next to the, so I assume that means that they are correctly set to boot in UEFI mode (in accordance with the advice on the UEFI page)
- I can confirm that (again in accordance with the advice on the UEFI page) that secure boot is not enabled, and that quick boot is disabled.   


However, I can’t find a bios entry for “Intel SRT” – could that be under some other name?

Is there anything else I am missing?   Anything else I should be enabling or disabling?

(I haven’t tried the “Boot-Repair” step listed on this page – I don’t get as far as seeing the live session.   I could create a “boot-repair-disk” from an iso I suppose, but wouldn’t it just have the same problems booting as I am already experiencing?)

Thanks for any assistance on this…

Andrew

---

### Post by oldfred on 2013-03-15
If it did not have Windows 8 pre-installed you should not have secure boot issues. And Intel SRT is for speeding up Windows, so you probably do not have it either. It uses a small 16GB to 32GB SSD as cache for Windows.

It seems like a video issue. What video do you have? Those systems with dual video need one or the other turned off initially. 
Often nomodeset works.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

I do not think UEFI gives the same boot options or f6 to add nomodeset. I think it is more like first boot after install, that on grub menu you manually replace quiet splash with nomodeset.

---

### Post by grahammechanical on 2013-03-15
So, you cannot even get a live Ubuntu session. No? Load the DVD again and do this

1) at the first purple screen press Enter
2) at the language selection screen press Enter to select English as the language or choose another language
3) at the Try - Install screen press F6
4) scroll down the little menu and select nomodeset and press Enter
5) press Esc to get back to the Try - Install screen and try running either option.

You may need to experiment with some of the other F6 options.

Regards.

---

