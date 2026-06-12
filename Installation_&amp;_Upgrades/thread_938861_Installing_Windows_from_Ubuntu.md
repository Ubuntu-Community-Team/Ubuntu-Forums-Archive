---
title: "Installing Windows from Ubuntu?"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by RwR on 2008-10-05
Hi
I want to format my hard drive and install Windows XP again, but I have a problem: there is an option in my BIOS that was changed for no reason, making it impossible to use my USB keyboard during the computer boot. As I don't have a PS/2 keyboard avaliable, I thought that I had no way to do this because I need to press "any key" during the computer boot to run the Windows CD. So I found out that my Ubuntu 7.04 LiveCD doesn't need any key to be pressed to run, and I was able to use it (when the menu comes up, I just wait some seconds and it automatically runs the OS).

So I think the only way I have to install Windows after formatting the HD, is to install Windows from within Ubuntu, but I'm pretty sure there is no way to do that. But as a Linux noob, I think that the experts around here know better :)

Thank you.

---

### Post by donec on 2008-10-05
Can't you just enable USB keyboard in your bios and then boot from your XP disk?

---

### Post by Elfy on 2008-10-05
If you can get the livecd to boot then there is no reason why the win install disc won't.

So you have a couple of options - enable usb kbd if you can, or use the livecd to format a space for the win to install on. 

Not sure aboiut Feisty, can't remember - but if the partition editor isn't already on the disc you could install it and then create space for windows. You need to put win at the front of the disc if you can.

What do you have installed at the moment?

---

### Post by Herman on 2008-10-05
> there is an option in my BIOS that was changed for no reason, making it impossible to use my USB keyboard during the computer boot. As I don't have a PS/2 keyboard avaliable, I thought that I had no way to do this because I need to press "any key" during the computer boot to run the Windows CD. Hmmm, I remember one time when I ran some program in my laptop and clicked on an option I didn't understand properly. It caused some trouble with my keyboard, something like what you are describing.
The solution for me was to go into the BIOS, and reset the BIOS back to 'optimized defaults'.
That fixed it instantly. :)

Then I just had one or two settings to make.
Will that help?

Regards, Herman :)

EDIT: It's an intriguing question though. I know that we can copy the contents of a Ubuntu Live CD to another (spare) partition on a hard drive, (or USB), and boot it as a LiveCD and install with it.
I am not sure, but I imagine it would be technically possible to do the same with a Windows Installation Disc. However, it will still ask you to 'press any key to boot from the CD', so I don't know if you'll be any further in front after the work you'll do to arrange that. You'll still be stuck with the keyboard problem.
SO I think you'll need to fix the keyboard problem first, no matter what else you do.

---

### Post by RwR on 2008-10-05
Belive me, if I could just change the USB option in the BIOS i would, the problem is that I can't because the keyboards don't work during the boot, as I said. And I have no PS/2 keyboard avaliable.

> **forestpixie said:**
> If you can get the livecd to boot then there is no reason why the win install disc won't.The reason is that with the Windows CD i need to press a key, and with the Ubuntu CD I don't.

So what I'm thinking is: If I format the HD and start my PC with the Windows CD inserted, the computer will have no option but to run the CD, right? I'm just not sure that the keyboard will work during the installation.

Thank you for all your help. I will keep trying to solve this, maybe the only was is with a BIOS reset

---

### Post by Elfy on 2008-10-06
_If_ the bios has been changed from default and _if_ it has been changed so that usb kbd doesn't work then you should be able to return to the defaults by removing the CMOS battery.

But I'm not sure as I ahve an 'old' board and it has no such options to start with :)

Wait for other opinions but it's all I can think off.

---

### Post by Braytok on 2008-10-06
> **forestpixie said:**
> _If_ the bios has been changed from default and _if_ it has been changed so that usb kbd doesn't work then you should be able to return to the defaults by removing the CMOS battery.

But I'm not sure as I ahve an 'old' board and it has no such options to start with :)

Wait for other opinions but it's all I can think off.

Exactly what I was going to recommend. Near the CMOS battery there should be a jumper that you can use to reset your BIOS but I couldn't tell you which one with out knowing the motherboard. The safest bet would be to remove the CMOS battery and then power cycle the machine once then put the battery back in  and all *should* be right with the world.

---

### Post by RwR on 2008-10-06
> **silve said:**
> make a boot diskette with DOS that automatticaly runs setup.Sounds interesting, a may do that if it really helps. But I'm sort of a newbie, so i'll have to do some research.
Ill tell you what my motherboard is when i'm at home.

---

### Post by RwR on 2008-10-12
OK, now I just want to format the drive, but I can't find a way to do that without using the keyboard during the boot. Is it possible to format it from Ubuntu 7.04 Live CD? If it isn't, is there another live CD that I can use that DOESN'T REQUIRE A KEYBOARD to use?

Thanks for the help.

---

### Post by louieb on 2008-10-12
Here in Texas there a quite a few mom and pop computer stores. Most have a basket full of used ps2 keyboards.  Even the local big box retail stores carry an inexpensive PS2 keyboard.  Seems like it would be a lot easier to just go get one  for when you need it and be done.

There is a partition editor on the Ubuntu live cd: System>Administration>Partition Editor.

---

### Post by RwR on 2008-10-13
Thank you louieb. I also think it would be much easier, but apparently I cant find one as easly as you... I have to ask it from a friend.

Thanks again.

---

