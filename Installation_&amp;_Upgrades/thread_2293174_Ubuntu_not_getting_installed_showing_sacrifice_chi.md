---
title: "Ubuntu not getting installed showing sacrifice children error"
date: 2015-09-03
forum: Installation &amp; Upgrades
---

### Post by Hitarth on 2015-09-03
[TABLE]
[TR]
[TD="class: votecell"][CENTER][COLOR=#777777]
[/COLOR]
[/CENTER]
[/TD]
[TD="class: postcell"]I was trying to clean boot my pc using bootable usb & suddenly the power was off and later when I restarted my pc it was not even entering the installation mode. It is showing errors like :
1. ACPI PCC probe failed 
2. [sdb] no caching mode page found
3. Out of memory: kill process 126 (systemd udevd) score 132 or sacrifice child
and similar errors.
I have already done memory & disks check( using the ones which came along with my pc by deafult ) and they all are showing passed still no installation proceeds & for either of the options - try or install errors as shown in this image are coming up. There should not be any memory shortage as I have 8GB ram, 1tb harddisk & i5 processor. Infact, the BIOS is also showing 8GB ram only.
It is very urgent & I will be very grateful to anyone who helps me.
[/TD]
[/TR]
[/TABLE]

---

### Post by brian-mccumber on 2015-09-03
If it is a desktop try - turn it off, unplug the power cord and hold the power button down for like 30 seconds. You can do the same if it's a laptop but you have to unplug it and remove the battery then hold the power button down. Then plug it back in and try to boot using your bootable usb. If that doesn't work your bootable media may have been corrupted when the power went out so you may have to remake it.

---

### Post by grahammechanical on 2015-09-03
Linux prints system messages to the screen. Most of them are covered by a  splash screen. Those messages are not necessarily error messages. Even  messages that say "failed" often do not stop the loading of the OS.

ACPI  PCC probe failed is a common message that first appeared on our screens  about half way through the development period of 15.04. I was running  the development version of 15.04 at the time. I am now running the  development version of 15.10 and that message does not show up. And I  have not made any changes to my machine. Do not see that message as a  problem.

Likewise, the other messages may not be things that stop  the loading of the OS. They do prove that Linux is loading for they are  Linux messages. I do not think that the "out of memory" message has  anything to do with the amount of RAM. I would guess it has more to do  with some allocation of memory assigned by the SystemD init system to  some SystemD process or other.

I do not understand what you mean  by "installation mode." Do you mean a boot menu? If Linux is the only OS  on the machine then we will not see a boot menu. The boot loader will  still be there and it will load Linux without showing a boot loader  menu.

Does Linux load to a login screen and a working desktop  environment? You do not say. If everything is working fine, then do not  worry about those messages. If Linux is not loading to a working  desktop, then that is the problem that has to be resolved.

What  version of Ubuntu are you using? Is there another OS on that machine? I  do agree with the suggestion that powering off a computer with a USB stick still plugged into the USB port will corrupt the files on the USB  stick.

Regards.

---

