---
title: "[help] Installing ubuntu 9.10 to external hard drive."
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by Rickmasta on 2009-12-06
Hello guys. I'm trying to install the latest ubuntu (9.10) onto an external usb hard drive. I've done it before, but with version like 6.X. I followed a tutorial, so I don't really know what I did. 

I can't seem to find a specific tutorial on installing 9.10 to an external hard drive. So I was wondering, should this tutorial work the same? [http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/](http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/)

Also, another side question, do I HAVE to burn the ubuntu to a CD, or can I burn it to a DVD instead?

---

### Post by darkod on 2009-12-06
There is really no difference. At the step 4 when is asks where to install select the external hdd, remember how it's named (for example /dev/sdb if you have only one internal hdd called /dev/sda) and on the last screen before clicking Install click on Advanced and double check if grub2 will be installed on /dev/sdb too. In other words, on the same external drive.
In BIOS setup the USb HDD before HDD as boot device, and when your external drive is plugged in the BIOS will boot grub2 from there. When it's not, it will keep booting from the internal one.

If during the installation you prefer to create your own partitions manually, the rest still remains the same.

---

### Post by Rickmasta on 2009-12-06
> **darkod said:**
> There is really no difference. At the step 4 when is asks where to install select the external hdd, remember how it's named (for example /dev/sdb if you have only one internal hdd called /dev/sda) and on the last screen before clicking Install click on Advanced and double check if grub2 will be installed on /dev/sdb too. In other words, on the same external drive.
In BIOS setup the USb HDD before HDD as boot device, and when your external drive is plugged in the BIOS will boot grub2 from there. When it's not, it will keep booting from the internal one.

If during the installation you prefer to create your own partitions manually, the rest still remains the same.
Thanks. But I still want my internal Vista to be my defualt Operating system, and the linux just on the side. So would I skip the last part where you mentioned. 

> .
In BIOS setup the USb HDD before HDD as boot device, and when your external drive is plugged in the BIOS will boot grub2 from there. When it's not, it will keep booting from the internal one.

---

### Post by darkod on 2009-12-06
That's exactly why I said that. Make sure grub2 will not install itself on your internal drive. It should be on your external one and when that drive is not plugged in you are using vista as usual. But with the usb hdd plugged in, you need grub2 to boot ubuntu. How do you plan to boot it without grub2?
You plan to have vista on internal and ubuntu on external right?

---

### Post by Rickmasta on 2009-12-06
Yes.

So with what you're saying. I have to unplugg the external hhd if I want to automatically boot vista, and if it's plugged int, it'll automatically boot ubuntu.


And if I unplugg my internal hard drive while installing the OS onto the usb one. I won't have remember the name cause only the external would be connected, right?

Sorry if I'm asking too many question. I just want to make sure I understand and install everything correctly, so that I wouldn't have to come back, again.

---

### Post by darkod on 2009-12-06
It's better to ask in advance. :)
There are few options to do this so there is no "correct answer".
Currently you have your int hdd with vista. No need to unplug it for installing ubuntu, in fact that can even complicate things.
Plug in the ext hdd, boot with the ubuntu cd, select Install and on step 4 select the ext hdd as destination which will probably be called /dev/sdb. But compare the size of the drive, it will be shown too, to be sure that's the correct one, I don't know your system to guess the name like this. If it really is /dev/sdb at the last step make sure grub2 bootloader is also installed at /dev/sdb as explained previously. The installer will finish and that's it.

Now... you have few options when booting. If in your BIOS you set up a sequence like HDD, then USB HDD, your int hdd will boot first and that will immediately boot vista as if ubuntu doesn't exist. That's because windows bootloader can't see linux by default (and that's why you need grub2). With that kind of setup you can only boot vista.
If you set up in BIOS the sequence USB HDD, then HDD, it will boot the ext hdd which has grub2. It will not immediately boot ubuntu instead it will show choice for ubuntu and vista. Which means if you have this setup in BIOS, you want to boot vista but you forget the ext hdd plugged in you can still boot vista from the grub menu.
Also, if you have this setting and you want to boot vista, a simple solution would be to unplug the ext hdd and since it can't be found by BIOS it will continue with the next choice, in other word the int hdd and vista. That's what I meant. It's easier to take the cable out then entering BIOS.
And anyway, even if the grub menu boots up you can still select vista.

Does that help?

---

### Post by Rickmasta on 2009-12-06
There. Thanks man! Everything's set. I apprieciate the help

---

### Post by n4pgw on 2009-12-06
I am a total newbie and installed Ubuntu many times on an external USB HDD.  The process is rather simple. As a precaution, I first told the bios of my computer that my internal drive was not installed and to boot from the USB device or CD-ROM.  Then I plugged in my USB drive and inserted the Ubuntu 9.10 Desktop CD-ROM in the drive and turned on the computer (this worked with a laptop and a desktop.)  I followed the install instructions and everything went well. Then I set the computer up to recognize the HDD again.  When I wanted to boot to Linux, I told the bios to boot to the USB device, or for windows, I booted normally.  (F-12 during warmup on the computer gives me boot options.)

Later, I reinstalled the external HDD from my laptop, but this time I chose to let GRUB be installed on my Vista drive inside the Laptop.  The result was a perfect install.  (I had to plug the laptop into a wired network for the first upgrade to get the wireless adapter drivers.) It is still working flawlessly after a whole week.  ;)

I also installed a separate internal hdd in my desktop running XP Pro.  When I finished, the boot sector was broken.  I only get "GRUB _" when I try booting from the internal hdd.  (I will start a support thread for that in a moment.)  I can still tell the computer to boot from the USB device and boot it up. I just don't have access to windows.

Since the ISO is a CD-ROM ISO, I imagine it would not burn successfully to a DVD, but a DVD drive wil boot a CD if that is your worry.  CDs are cheep so you might be able to find a friend to give you a blank if you need it. I burned mine from a DVD burner onto a blank CD-ROM.  -- FWIW

Good luck
Buck

---

