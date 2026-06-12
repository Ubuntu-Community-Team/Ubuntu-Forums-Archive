---
title: "help creating a usb stick to run Ubuntu"
date: 2020-02-10
forum: Installation &amp; Upgrades
---

### Post by azcowboy2 on 2020-02-10
I am trying to create a usb stick to run Ubuntu from the stick on windows 10

I tried several time using Rufus but it never worked.....I followed the instruction exactly at least 10 times

I have no clue what I am doing wrong....

Loaded the Ubuntu ISO file..loaded it in Rufus as directed...just cannot get it to work

Any help Greatly appreciated

---

### Post by guiverc on 2020-02-10
I'll just provide links - 
[https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-windows/14020](https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-windows/14020)

Possibly also useful : [https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0) OR [https://discourse.ubuntu.com/t/how-to-verify-your-ubuntu-download/14010](https://discourse.ubuntu.com/t/how-to-verify-your-ubuntu-download/14010) (*to verify your download was perfect*) and [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck) (*used to validate the write to media, where CD refers to cd/dvd/hdd/ssd/thumb-drive or any media where the ISO was written to*)

If I have troubles booting & validating an thumb-drive (where I wrote ISO to) on one box, I usually boot it on a different box and perform the "Check disc for defects" there. If it fails to boot on the second box I usually assume the write to media failed  (*though I may re-check md5sum anyway on ISO as that's extremely quick*)

---

### Post by dustyt on 2020-02-11
Be more specific.

What is not working???

Are you having issues creating the live usb?

Or are you having issues getting your pc to boot the live usb?

---

### Post by azcowboy2 on 2020-02-11
Thank you for your response I greatly appreciate it...

I loaded the iso file of Ubuntu 18

Loaded it into RUFUS

Followed instruction line for line

It says the usb stick is ready however when I try to boot from the usb stick - my PC does not bring up Ubuntu and boots directly to windows.

---

### Post by sudodus on 2020-02-11
Please tell us about the computer - brand name and model
and also about the graphics chip/card - brand name and model

It will be easier for us to give good advice, when we about the hardware. Otherwise we can only guess.

---

### Post by azcowboy2 on 2020-02-11
Thank you very very much..I will try it now!!

---

### Post by azcowboy2 on 2020-02-11
I just dont understand....I followed the instrctions exactly and still does not work...I even tried 3 different usb sticks....

---

### Post by dustyt on 2020-02-11
OH OK, the usb stick is fine, it is the computer's boot menu.

It is set to boot the hard drive first and may not even have usb boot enabled.

Google your computer to find out what F key brings up the boot menu. Shut it off and turn back on with the usb stick already inserted. Tap that key while it is powering up, keep tapping and the menu should come up. If your usb stick is listed, simply select it and it will boot.

If it is no listed google the same and find out which F key loads your bios. Repeat the proceedure above to get to the bios screen. Find usb boot and enable it. And I personally would go to the boot device menu and move the usb stick to the top so you don't have to mess with the boot screen key after. Some pc's revert this setting and put windows back on top next time around. But all don't and you will know what is going on if it doesn't boot the usb stick next time. You're stuck having to select it in the boot menu key press process.

Test drive well and study up on all the changes you will need to make to the bios and how to go about installing before you actually install though. This will save you a lot of hassle if you decide this is the distro for you.

---

### Post by yancek on 2020-02-11
I think your problem is likely what is described in post 8 above as you have made no mention of changing the boot order in the BIOS firmware so until you do that, it will always boot the pre-installed windows.  From a cold boot, you should see a message on screen (usually lower left of the screen) telling you which key you need to use to access boot options or BIOS firmware.  THis varies greatly with manufacturer so knowing that might help someone to help you also.

---

