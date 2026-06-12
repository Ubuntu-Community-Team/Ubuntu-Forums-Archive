---
title: "Dual boot?"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by dazcaz on 2009-11-29
Hello all,
I'm very much a newbie in the Ubuntu world, but I have been running it on one of my older machines for a month or so without problems...

anyhoo.
My windows machine got stung by a drive by. AVG caught it too late. Firefox let it in :(
Not happy. Two days of cleaning and it's still there!

It looks like I will need to format and reinstall Windows to sort this out.
I'd rather not have Windows, as we are are slowly moving to a Mac and  Ubuntu based house.

So how do I install Ubuntu as the main OS but still have Windows on the machine for when we need it?

Do I install Windows first and then Ubuntu using the disc partioner or can I do it the other way around?

I don't wan to run Ubuntu under wubi or whatever it's called as I beleive that require Windows to be running. I want the option of which OS to boot into on start up.

If I can get this sorted, and show my wife that Ubuntu is the way to go, I'll be able to slowly move all our Windows machines to ubuntu.

TIA

Darren

---

### Post by audiomick on 2009-11-29
hallo Darren.
Have a look at this
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

I think it is all there. Good luck converting your family. I've got half of mine converted, and a couple of friends.;)

---

### Post by howefield on 2009-11-29
> **dazcaz said:**
> Do I install Windows first and then Ubuntu using the disc partioner or can I do it the other way around?

Windows first, then Ubuntu is the easiest way. This way, Ubuntu will sort out the bootloader by itself.

> I don't wan to run Ubuntu under wubi or whatever it's called as I beleive that require Windows to be running. I want the option of which OS to boot into on start up.

Although Ubuntu would be installed to a file residing on your windows partition on a Wubi install, you will still get an option at startup as to which operating system to boot into. However, a real dual boot would be preferable.

---

### Post by mikewhatever on 2009-11-29
You'll need to do some reading on how to dual boot. Read some of the links and if you have more specific questions (less general), do not hesitate to ask.

[http://lmgtfy.com/?q=ubuntu+windows+dual+boot](http://lmgtfy.com/?q=ubuntu+windows+dual+boot)

---

### Post by presence1960 on 2009-11-29
Either way will work. You can install windows or linux first. But if you install windows after Linux to the same hard disk you will have to restore GRUB as windows bootloader will overwrite the MBR.

Since you are formatting your disk, if you intend on installing both now it would be easier to install Windows first. I would use gparted live CD or another partioning utilty to set up your partitions before installation. This will save you from having to defrag & shrink windows partition.

---

