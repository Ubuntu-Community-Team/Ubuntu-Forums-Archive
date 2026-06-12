---
title: "[SOLVED] Locked out from BIOS so cant boot CD, how to install ubuntu?"
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by al_mckin on 2008-10-07
Hi Everyone,

I'm trying to install Intrepid or Hardy on my old laptop, a Thinkpad T43.

I do not have the BIOS password, and am extremely unlikely to get it.  It can be recovered by disassembling the laptop, but for this model it requires soldering onto a chip and I really don't want to risk it!

At the minute I have XP and Fedora Core 4 on it that was installed for me by the old sysadmin who also has the BIOS password.  

I tried booting Smart Boot Manager from Grub according to the instructions here [http://ubuntuforums.org/showthread.php?t=374555]("http://ubuntuforums.org/showthread.php?t=374555") but smart boot manager kept on returning a "Disk Error 0xAA".  Apparently this might be a hardware problem or bios bug.

So, I think installing from a CD or DVD is out, unless someone has experience with this exact problem.

Otherwise, is there any other method I can use for installation?

Alastair

---

### Post by Idefix82 on 2008-10-07
You can use Wubi to install Ubuntu from Windows.
edit: [http://wubi-installer.org/]("http://wubi-installer.org/")

---

### Post by al_mckin on 2008-10-07
Can I get wubi to install it on any partition, i.e. my old FC4 partition?

If so, that is officially awesome.

---

### Post by Idefix82 on 2008-10-07
You might need this to get Ubuntu onto a dedicated partition:
[http://lubi.sourceforge.net/lvpm.html]("http://lubi.sourceforge.net/lvpm.html")

---

### Post by al_mckin on 2008-10-07
So I would have to create a wubi installation, then transfer it to a real partition using lvpm?

I'm not sure I like this solution.  I will do it if I have to though.

Is there any other way to do a fresh ubuntu install on an existing partition without a CD drive?  Is there some way to boot the installation CD from an existing partition on the drive?

Alastair

---

### Post by Idefix82 on 2008-10-07
The only other way I can think of (which is rather radical) is make the MBR of the hard drive unusable. If the BIOS is in principal allowed to boot from CD but the CD is just further down the list in the boot order then upon discovering that the hard driver is unbootable it will try to boot from the CD.
Note however that if this fails (say the BIOS is configured to not boot from anything other than the hard drive) then you have a real problem because you won't be able to boot into anything.

If this is a PC and you can remove the hard drive then you could try putting it into a computer where you have access to the BIOS and install Linux there, then put the hard drive back. But with this solution you are very likely to run into all sorts of trouble with the hardware since Linux will be expecting to use the hardware of the computer it was installed on.

Finally, you could just try your luck and create a bootable USB device. If you are lucky then the USB is set higher than the HD in the boot preference order in the BIOS. On a related note, have you checked that it doesn't boot from the CD if the CD is bootable?

All in all, I think Wubi and then transferring the installation is still the best solution I can think of.

One last thing: Not being able to boot from CD will backfire on you at some point, that's for sure. As soon as you want to substantially change psrtitions or have to recover something or need to fix the MBR you will be lost. Ergo: the sooner you get a computer with full access the better :)

---

### Post by ToasterThief on 2008-10-07
Why don't you just boot and install from an USB key?

[http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/](http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/)

It's likely that'll work on a TP.

Furthermore I seem to remember that there's a BIOS reset jumper somewhere under the keyboard.

---

### Post by ajgreeny on 2008-10-07
And I believe if you can remove the small button cmos battery from the motherboard, and surely that must be possible without a soldering iron activity, then all bios settings including password will be back to default, ie without password.  I can not imagine that you would be required to do anything drastic with solder, just to renew, or in this case remove it for a few minutes to allow a reset of the bios.

---

### Post by al_mckin on 2008-10-07
Thanks for the suggestions.

Unfortunately, it is configured to not boot from anything but the hard drive.  

I will persist in trying to make the smart boot manager work for a while.  If I can't get it, I will give up and break it open!

---

### Post by al_mckin on 2008-10-07
> Why don't you just boot and install from an USB key?

[http://www.teamteabag.com/2008/05/17...tros-from-usb/](http://www.teamteabag.com/2008/05/17...tros-from-usb/)

I dont think this will work.  The BIOS is configured to boot from hard drive only, and the password is lost.

> Furthermore I seem to remember that there's a BIOS reset jumper somewhere under the keyboard. 

> And I believe if you can remove the small button cmos battery from the motherboard, and surely that must be possible without a soldering iron activity, then all bios settings including password will be back to default, ie without password. I can not imagine that you would be required to do anything drastic with solder, just to renew, or in this case remove it for a few minutes to allow a reset of the bios.


Unfortunately, for this particular model, the password is stored on a eeprom, which means it cannot be reset with a jumper setting or removing a battery.  The only solution is this: [http://sodoityourself.com/hacking-ibm-thinkpad-bios-password/]("http://sodoityourself.com/hacking-ibm-thinkpad-bios-password/")

If smart boot manager worked, I could boot it from GRUB and then boot the CD. Unfortunately it doesnt seem to work, for an unknown reason.

---

### Post by al_mckin on 2008-10-07
Ok I think this is the solution for me.

Since I have an already working FC 4 partition I can use the methods described here: [https://help.ubuntu.com/community/Installation/FromLinux?highlight=(installation)]("https://help.ubuntu.com/community/Installation/FromLinux?highlight=(installation)")

I create a new small partition, copy the install CD contents to it, and boot it from GRUB.  Looks good!

---

### Post by louieb on 2008-10-07
> **ajgreeny said:**
> ...I can not imagine that you would be required to do anything drastic with solder...
Unfortunately he is right. IBM/Lenovo own solution is to replace the mother board. Just something to consider when purchasing a used thinkpad.

---

