---
title: "Usb booting of linux on win 8.1 tablet"
date: 2015-07-22
forum: MINT
---

### Post by user987 on 2015-07-22
I have a Dell venue pro 8 tablet with win 8.1 OS, 32 bit version.

How can i usb boot up like i do with my regular dell netbook into linux mint via my USB flash drive ?

This UEFI boot is different from my regular BIOS access on the netbook.

---

### Post by howefield on 2015-07-22
Thread moved to the "*MINT*" forum.

---

### Post by QDR06VV9 on 2015-07-22
Dose this work
[COLOR=#000000][FONT=arial]Hold the volume down until the bios screen appears.. in my boot menu I see my USB drive as a boot option, but it's the lowest priority item, if you move it to the top, it should pick that one to boot from.[/FONT][/COLOR]

---

### Post by user987 on 2015-07-24
The power and vol button work, but when i go into the boot tab, i  do not see the regular bios options like 

    1)hd
     2) usb
    3)cd/dvd

in which i would move usb to the top and reboot like my netbook and my usb linux os would come on in the netbook.

i see a boot piority and only window boot manager in the box for the venue 8 bios.

Any ideas on what is going on?

---

### Post by QDR06VV9 on 2015-07-24
> **user987 said:**
> The power and vol button work, but when i go into the boot tab, i  do not see the regular bios options like 

    1)hd
     2) usb
    3)cd/dvd

in which i would move usb to the top and reboot like my netbook and my usb linux os would come on in the netbook.

i see a boot piority and only window boot manager in the box for the venue 8 bios.

Any ideas on what is going on?

[COLOR=#595959][FONT=Trebuchet MS]Because the Dell Venue 8 and 11 tablets like the 7130 and 7130 have no keyboards you need to use a button combination to gain access to the BIOS.  That order is:[/FONT][/COLOR]

[LIST=1]
[*]Power up the tablet from being powered off &#8211; reboot does not seem to work
[*]Press and HOLD the volume down button (second silver button from the top on the left side) until the DELL logo screen shows ENTERING BIOS in tiny letters in the top right corner.
[LIST=1]
[*]If you see the Windows &#8216;rolling dots&#8217;, you have missed it so power down and start again.
[/LIST]
[/LIST]
[COLOR=#595959][FONT=Trebuchet MS]You will then be able to get into your Venue 11 or 8&#8217;s uEFI BIOS.[/FONT][/COLOR]
[COLOR=#595959][FONT=Trebuchet MS]Note that if you have an Atom Based Dell Venue 11 you CAN connect a keyboard to the USB port on the device or dock and press F12 to access the BIOS.
Some other helpful sites
[http://forum.tabletpcreview.com/threads/dell-venue-8-pro-how-to-boot-to-usb.59345/](http://forum.tabletpcreview.com/threads/dell-venue-8-pro-how-to-boot-to-usb.59345/)
This one is for creating a nice backup
[http://forum.tabletpcreview.com/threads/step-by-step-guide-to-creating-a-multi-boot-backup-recovery-and-install-usb-drive-for-the-dell-venue-8-pro.60245/](http://forum.tabletpcreview.com/threads/step-by-step-guide-to-creating-a-multi-boot-backup-recovery-and-install-usb-drive-for-the-dell-venue-8-pro.60245/)

And a nice video with comments (should read them)
[/FONT][/COLOR]https://www.youtube.com/watch?v=1WrRngZ4giE[COLOR=#595959][FONT=Trebuchet MS]

Good Luck
Regards[/FONT][/COLOR]

---

### Post by user987 on 2015-07-27
Hi Runrickus,

                    I was able to get into bios sucessfully from your first post.
The problem is once in bios when i go to the boot tab, i see the following:
    1) file browser add boot option
    2) file browser del boot option
    3) fast boot        (disable)
    4) secure boot    (disable)
      
 Boot Option Priorites
 Boot option #1    (window boot manager)

No where do i see usb in the boot option priorites.

Also my usb flash drive which i use to boot my net boot is attached to the tablet and it does not see it.

Is there something i need to to enable?

I know for my netbook i had to under the advanced tab enable bios legacy for usb to show up as a boot option.

Under the tablet's bios i went to the advanced tab and see that:

usb configuration

1) enable usb boot   (enabled)
2) external usb ports   (enabled)

So it seems i can usb boot but i don't see usb  anywhwere to be use, whereas you and the articles show that the usb option is shown.

Any ideas on what is going on?

---

### Post by QDR06VV9 on 2015-07-27
> Any ideas on what is going on?
How Strange!:confused:
This should work for you though. Fingers Crossed.
[http://www.daossoft.com/blog/how-to-boot-from-usb-on-dell-venue-windows-8-tablet/](http://www.daossoft.com/blog/how-to-boot-from-usb-on-dell-venue-windows-8-tablet/)

Also if you can boot from USB after reading that page you **might** have to edit Grub /etc/grub.d/custom
And set it "timeout=3"
[B]Only if you can get to where you can boot from USB.

[/B]Android actually runs pretty nice installed. I know that is not what you want but worth Mentioning.
[https://www.youtube.com/watch?v=h2OaO8J6OQ8](https://www.youtube.com/watch?v=h2OaO8J6OQ8)
> [COLOR=#333333][FONT=Roboto]Published on May 23, 2015[/FONT][/COLOR][COLOR=#333333][FONT=Roboto]This is how to install/run Android on a Dell Venue 8 Pro tablet. It's a pretty involved process, but isn't too difficult. To do this, you'll need a Micro USB to USB adapter, 2 USB flash drives (one needs to be at least 4 GB, the other at least 1 GB), a USB hub, and a USB keyboard and mouse. To make the Linux USB drive, you'll need a Mac or Linux machine, however it may work using Win32DiskImager on Windows. Android seems to run perfectly fine on this device, the only issues are that sleep mode doesn't work, and the cameras don't work.

Links:

Bootable Linux USB commands: [http://dosdude1.mooo.com/fedletusb.html](http://dosdude1.mooo.com/fedletusb.html)

Android files for second USB drive: [http://dosdude1.mooo.com/files/Venue8...]("http://dosdude1.mooo.com/files/Venue8ProAndroid.zip")

Fedlet Linux: [https://adamwill.fedorapeople.org/201...]("https://adamwill.fedorapeople.org/20141209-fedlet-i686.iso")
[/FONT][/COLOR]
[COLOR=#333333][FONT=Roboto]
[LIST]
[*]**Category**
[LIST=|INDENT=2]
[*][Science & Technology]("https://www.youtube.com/channel/UCiDF_uaU1V00dAc8ddKvNxA")
[/LIST]

[*]**License**
[LIST=|INDENT=2]
[*]Standard YouTube License
[/LIST]
[/LIST]
[/FONT][/COLOR]


---

### Post by user987 on 2015-07-27
Hi,
      i will give the article a try later, but the more research i do, i am finding out that i somehow need to get the legacy mode and enable it.
The UEFI  of win 8/8.1 and higher do not support it.

Will let you know what happen later.

---

### Post by user987 on 2015-07-29
Hi Runrickus,
                    I have read the links you recommeded and others that i found, in all the cases they show a usb option.
For some reason my win 8.1 OS firmware does not give that option and it does not give the ability to use the legacy bios which is crucial to get the usb to show on my tablet.

I guess i have to live with the tablet as a win 8.1 OS only machine.  Typical progress 1 step forward and 2 step back.

My old 6 year single core netbook running three different flash drives of Zorin 9.0 LTS, Ubuntu 14.04 LTS, and Mint 17.0 LTS
runs just as fast as the quad core tablet with win 8.1 for internet usage, so i guess the tablet will gather dust as my netbook is still my go to machine.  

The tablet is faster compare to the win 7 installed on the netbook internal SSD drive, but with linux as i say above it runs great.

Thank you for all your help in this endeavor.

---

