---
title: "Installed Lubuntu on an old Pentium M, using forcepae."
date: 2014-11-11
forum: Installation &amp; Upgrades
---

### Post by irv on 2014-11-11
I had an old laptop with a Pentium M processor that I used on a sound system for many years. It had an older copy of Ubuntu Studio on it. I was trying to install Lubuntu 14.10 on it and ran into one problem. I couldn't install it because I forgot it didn't have a Hard Drive. I had to laugh at myself for that one. I had a old SATA 500 Gig HD but the laptop had an IDE. I quickly went on Amazon and order a [Micro SATA Cables - 2.5 inch SATA SSD or HDD Drive to IDE 44 Pin IDE Adapter]("http://www.amazon.com/dp/B0049D7PCU/ref=pe_385040_30332200_TE_item") for #3.64 that should allow me to use the drive. I thought I would go ahead and hook it up via USB and install the OS. It went well and I got it installed but seeing I didn't have an internal HD it would not set up the grub so it still refused to boot from the USB. I might have other issues with the laptop because I could only get it to boot from the CD/DVD. That's Okay, I will just wait until I get the adapter.

When I went to install I had to follow this work-around because of the new kernel and the pae. 
> With the Install choice high-lighted press F6. (This option needs less RAM than installing from 'Try Lubuntu')

A menu with a number of options appears. The option 'forcepae' is not there, so press Escape to close the list.

Now a string of options is visible, often with 'quiet' or 'quiet splash --' at the end. Add 'forcepae' to the string after the two dashes.

... quiet splash -- forcepae 
This is nice that I didn't need to find a different copy with a fake-pae.

Now when I tried to install without going into the live OS, I had trouble getting on my network. It wouldn't allow me to enter my WEP password. I final just booted into the live OS and logged on to my network and did the install. I think if it wouldn't have been for the grub problem I would have been good to go. 

I will come back and post again after I get the adapter and do the install again. Or maybe it will just boot up after I put the drive in the laptop?
Here is a couple of photos of the old laptop.
[ATTACH=CONFIG]257895[/ATTACH]  [ATTACH=CONFIG]257896[/ATTACH]

---

### Post by ubfan1 on 2014-11-11
If you get the grub menu when trying to boot the usb disk, take a look at the grub commands (type e to edit, instructions on page) and see what devices are used.  An old bug has grub using the wrong devices because after the usb live media is removed, the devices get renumbered.  Where UUIDs are used, they are OK, but anywhere you see an hd1 or sdb, change it to hd0 or sda.  Then try the boot (ctrl x or F10) and if successful, immediately run sudo update-grub to fix the problem with the grub.cfg file.

---

### Post by irv on 2014-11-12
What I get when boot, (because there is no hard drive) is:
> error: Attempt to read or write outside of disk 'hd0'
Entering rescue mode
Then I get the prompt:
grub rescue>

---

### Post by ubfan1 on 2014-11-12
OK, at the grub prompt, use the tab completion to list the available disks (start a command like set root=(hd  then tab to get the choices).  See which number your target is using.  Then from the live media, look at the USB disk's grub.cfg file in /boot/grub/grub.cfg, and fix the devices in that file.  Then try reboot from the USB disk.  Disk enumeration is pretty machine specific -- I usually get hd0 as the internal hard disk when booting from USB, but other knowledgeable people have stated they get hd0 as the USB boot device.  The old bug was 384633.  Things seems to have changed these days, with the target being given hd0 instead of the last number one.  I'm doing less with USB because of the bad things it does with my UEFI nvram entries (why, why, why!!!).

---

### Post by irv on 2014-11-12
The tab key does nothing, but I am not worried about it. I should have the adapter in a couple of days and I will just install the HD in the laptop and get it going that way. Thanks for the help anyway. It appears to be trying to boot for the USB but I believe I have some other issues with the USB on this laptop.

---

### Post by irv on 2014-11-19
It just so happens that my son has the same Old Pentium M computer like I have. My other son was selling these laptops many years ago and we both got one about the same time. He called me the other day and said he was having problems with his laptop which was running XP. He had his wife drop it off and I installed Lubuntu on it and everything went like a fine tune clock. All I had to do was install with forcepae. When the install screen came up I hit the F6 key then the ESC key and added the forcepae to the end of the command line that was on the screen. Before it installed it gave me the warning that it was forcing the pae in the CPU and than when on with the install. I did the install from the live OS because I had to get it on my network and get an Internet connection. 

After installing the OS I installed all the updates along with LiberaOffice. I also backed up his data from the XP and put it all back in Lubuntu. I changed his wallpaper to what he had and it is good to go. I think he will like it better than when he had XP because it runs much faster. From power on to the desktop it takes about 45 seconds. WinXP took about a minute 45 seconds to boot. Lubuntu is about a minute less.

---

