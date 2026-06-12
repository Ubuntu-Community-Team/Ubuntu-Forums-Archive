---
title: "Created 22.04 USB won't boot"
date: 2022-05-16
forum: Installation &amp; Upgrades
---

### Post by msh8er on 2022-05-16
HP laptop formerly Win10 now has Ubuntu 20.04 installed.  Ubuntu 22.04 iso which had a correct checksum is in the downloads directory.  After selecting this iso as source and usb as destination, the creator announces it is finished in 5+ minutes.  Quit
Newly created usb won't boot on either HP laptop or an older Acer that can boot either Win7 or the Ubuntu 20.04 which I created maybe 5-10 years ago.
Did the new 64GB usb need some preparation before I attempted to create the bootable usb from it?  
Other ideas?
Despite very light usage of Ubuntu for 10+ years, I consider myself a novice as I stuck with Msoft for family and friends.  Patience please.
Thank you for ideas.

---

### Post by GhX6GZMB on 2022-05-16
If you have a working 20.04 installation, why change it?
But to answer your question: you need to look at the BIOS setup. If USB isn't the first option for booting, it'll never work.

---

### Post by msh8er on 2022-05-16
The 20.04 was setup when my network was wired.  I'm wireless now and the conversion wasn't obvious.
Now the Bios is apparently showing some signature associated with 20.04 and i haven't been able to change the selection to the USB.
Thank you. 
EDIT:  When I set up 20.04, the Boot popped up with USB selected when the USB was present, but gave you a choice for hard drive with Win7.
The boot choices displayed won't let me choose the USB.

---

### Post by GhX6GZMB on 2022-05-16
Wired, not wired, what's the difference.
On an HP laptop, you press F10 when booting and you'll land in the BIOS. Set USB to first priority in the boot menu.
Ubuntu is not even in play here.

---

### Post by msh8er on 2022-05-16
That is not working as I expected.  I get there and the first entry is somehow tied to some sort of Ubuntu signature and I can't move the usb to the top of the list.  I tried to unsecure some settings, still couldn't change the boot order.  
As far as I can tell, this is my whole problem.

---

### Post by yancek on 2022-05-17
Generally, when a supposed bootable usb does not work, the first suggestions are to verify the iso with a checksum and try booting the usb on another computer.  Since you have done that already, you could try using some other software to create the bootable usb.  You might try formatting the usb as FAT32 before writing the iso to it.

Is the HP with windows 10 a UEFI install?  Is the Acer UEFI or Legacy, windows 7 is generally Legacy.

When you access the BIOS firmware on the HP, do you see option to boot the usb in UEFI or Legacy mode or both?  On the HP laptops I use, I need to first hit the Esc key then F9 for one time boot change.  Are you using F9 to make the change?  Do you have an option to use the F5/F6 keys to move an entry up or down?

---

### Post by msh8er on 2022-05-17
> **yancek said:**
> Generally, when a supposed bootable usb does not work, the first suggestions are to verify the iso with a checksum and try booting the usb on another computer.  Since you have done that already, you could try using some other software to create the bootable usb.  You might try formatting the usb as FAT32 before writing the iso to it.   **Did this**

Is the HP with windows 10 a UEFI install?  Is the Acer UEFI or Legacy, windows 7 is generally Legacy.  ** Bought HP with Win10 installed and apparently wiped it out by selecting _Install instead of Try Ubuntu_ 20.02 when I booted the USB thumbdrive on the HP.   ****The HP BIOS setup utility says UEFI and insists that I'll boot Ubuntu from the hard drive**
When you access the BIOS firmware on the HP, do you see option to boot the usb in UEFI or Legacy mode or both?** No**  On the HP laptops I use, I need to first hit the Esc key then F9 for one time boot change.**News to me,I'll try.** Are you using F9 to make the change? **No**  Do you have an option to use the F5/F6 keys to move an entry up or down? **Not on the boot entry, which I can't change**

Do I need to do the esc-f9 sequence before i get to the f10 bios prompt?

---

### Post by msh8er on 2022-05-17
I muddled my way through your advice, relying on the hope that I couldn't do much more damage to the HP.  I just successfully booted Ubuntu 22.04 frm USB and it is now installing on the HP hard drive.  I'm hoping I'll once again have a thumb drive boot option.  I definitely have Ubuntu wireless support, so now I can get down to the endless task of rebuilding lost file and info.
Thank you hugely for getting me down the right path.

---

### Post by yancek on 2022-05-17
> Do I need to do the esc-f9 sequence before i get to the f10 bios prompt? 				 

As I stated in my last post, these are options on the HP laptops I use.  They are not the same on all computers and not even the same on all HP computers.
First, turn on the computer and begin tapping the Esc key until you see a menu which will give you several options.  On my computer, there are 5 options, 2 of which are Boot Menu and BIOS setup.   Selecting Boot Menu should give you the option to select (as a ONE TIME BOOT ONLY) any OS installed UEFI.  If the computer is capable of booting both UEFI and Legacy/CSM, you should see options for the USB under either or both often by the name of the disk manufacturer.  Use the arrow up/down keys to highlight the option you want to boot and hit the enter key.

---

