---
title: "Can't boot from CD"
date: 2014-08-19
forum: Installation &amp; Upgrades
---

### Post by Carllacan on 2014-08-19
Hi.

All of a sudden I can't boot from CD. When I turn my computer on with a bootable CD the reader starts making noises as if it is reading it, but then it just takes me to the GRUB. 
I can enter a boot menu by pressing ESC whil the laptop turns on. When I select boot from CD I am told to insert a valid bootable media and press any key.

Things to consider:
It doesn't matter which CD I use: Debian, Ubuntu, Fedora... none works.
I could boot from CD in the past, and the CDs I then booted from don't work now.
The CD reader works; I checked with normal CDs.
The BIOS is configured to boot from CD reader, then HD, then USB. UEFI boot is disabled. I've booted from CD with this configuration.
I haven't installed any new hardware. In fact its a laptop, so I can't possibly touch anything.

More info: I use a laptop Asus K52J, and I have a dual boot with Ubuntu 14 and Windows XP. I've been able to boot from CD while having a similar configuration.

Thank you for your time.

---

### Post by Carllacan on 2014-08-20
[COLOR=#000000][FONT=verdana]I remember that the first time I tried to boot from a CD I had to configure something in the BIOS, apart from changing the boot preference order, but I can't remember what it was. Maybe it was to enable UEFI boot, but I don't remember.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]I am tempted to just enable it, but I don't want to risk bricking the laptop. Should I give it a try?[/FONT][/COLOR]

---

### Post by yancek on 2014-08-20
You need to get into the BIOS of the machine and change the boot order to boot from the CD.  Since the method varies with manufacturer, you need to watch the screen when you boot for a message "press ??? key to enter setup", there should be a specific key where I have the questions marks.  Once in the BIOS, you should see several tabs and you want the Boot one.  Should be a method to change priority there.

---

### Post by sudodus on 2014-08-20
It might be a hardware problem, anything from a bad electric connection to some hardware in the reader not working. It might also be a software problem, but it is not very likely, unless you have changed the BIOS settings (or installed a new BIOS system).

Maybe you can find how to dismount and mount the DVD drive in a manual for your computer (maybe via the internet).

If you don't want to open the computer to check the connections, you can at least 'wiggle' the DVD drive, which might fix a bad electric connection.

-o-

Is it an alternative for you to boot from USB (typically a USB pendrive or stick) instead? See this link and links from it

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Carllacan on 2014-08-21
If I press ESC i get a boot menu, but no CD is accepted as a valid boot media. Should I try disabling Secure boot?

I've also read that other Asus owners had to enable UEFI boot and Launch CSM. Should I try it?

I'm a bit scared of bricking my PC by messing with the BIOS.

---

### Post by sudodus on 2014-08-21
I can't understand why your computer suddenly stops booting from CD/DVD.

If you have and run Windows XP, you can't have UEFI and secure boot in that computer. I'm still suspecting some hardware problem with the optical drive. That is why I suggest that you try booting from USB.

Can you get (maybe borrow) a USB pendrive?

---

### Post by matt_symes on 2014-08-21
Hi

Try disabling booting from the hard drive as an option all together. Look to see if there is a boot priority option as well as a boot order. A BIOS on on of my PCs has this - fankly bizarre - setting for booting from a pen drive or hard drive after you have set the boot order.

Another option is to reset the BIOS and then set the options back. 

To achieve this, you can try loading failsafe defaults or even resetting by taking out the CMOS battery. Try this last though and see if others have more suggestions first.

Does the CDRom work when used from inside the OS installed on the drive ? 

Kind regards

---

### Post by Carllacan on 2014-08-22
[COLOR=#000000]"Does the CDRom work when used from inside the OS installed on the drive ? "
[/COLOR]
Yes, that's what bugs me the most. It would be really weird if a hardware problem affected only CD booting, wouldn't it?

---

