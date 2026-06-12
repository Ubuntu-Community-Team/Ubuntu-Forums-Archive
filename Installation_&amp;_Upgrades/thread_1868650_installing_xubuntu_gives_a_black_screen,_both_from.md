---
title: "installing xubuntu gives a black screen, both from cd and usb, 64 and 32"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by sowdust on 2011-10-24
Hello everyone.
After the upgrade to 11.10 of my ubuntu i decided to switch to xfce, since i really do not like gnome3 and it messed up my desktop appearance and other things completely. Plus, having a few unimportant but unsolved system problems I decided to backup my /home and install xubuntu 11.10 from zero.

Having an intel celeron dual core processor, I first tried downloading the amd64 version. Copied it onto a usb drive, made it bootable using unetbootin, rebooted.

First strange thing i notice:
the first time I reboot, the booting process interrupts after saying "Linuxsys" and some other introductory things on just one line of text. I have to power off manually.

Trying to reboot again, now it finally gets to the boot menu: "install,help,try w/o installing...." each option I try, seems to work for the first seconds and then just becomes a black screen.
Only option is to shut down manually.

So I tried to repeat the process: same strange behaviour (first time no boot menu, second time boot menu and nothing else).

I tried booting from a cd: same strange behaviour.

Tried from usb with the i86 version: same strange behaviour.

What could this be caused by? I never had problems installing ubuntu on this laptop, which is an acer travelmate.

Thanks in advance for any suggestion,
mattia

---

### Post by MAFoElffen on 2011-10-24
> **sowdust said:**
> Hello everyone.
After the upgrade to 11.10 of my ubuntu i decided to switch to xfce, since i really do not like gnome3 and it messed up my desktop appearance and other things completely. Plus, having a few unimportant but unsolved system problems I decided to backup my /home and install xubuntu 11.10 from zero.

Having an intel celeron dual core processor, I first tried downloading the amd64 version. Copied it onto a usb drive, made it bootable using unetbootin, rebooted.

First strange thing i notice:
the first time I reboot, the booting process interrupts after saying "Linuxsys" and some other introductory things on just one line of text. I have to power off manually.

Trying to reboot again, now it finally gets to the boot menu: "install,help,try w/o installing...." each option I try, seems to work for the first seconds and then just becomes a black screen.
Only option is to shut down manually.

So I tried to repeat the process: same strange behaviour (first time no boot menu, second time boot menu and nothing else).

I tried booting from a cd: same strange behaviour.

Tried from usb with the i86 version: same strange behaviour.

What could this be caused by? I never had problems installing ubuntu on this laptop, which is an acer travelmate.

Thanks in advance for any suggestion,
mattia
What is the model number of your Acer Travelmate?  
- From what I've found, the Travelmate goes from at least the 2xxx series through 8xxxx series, and the 2480 itself has about 20 variants.
- I think most of them have Intel video, with the older one's using the i915 chipset...

You say it "borks" mostly at the text banners before the menu... then on anything after the menu.  I've use this Xubuntu/XFCE ISO on intel chipsets - and yesy it sometimes acts up on older Intel chipsets.  Funny thing is that once I get it installed it works fine on a default driver!  Here's how I get around it with older Intel.

- First I would check the md5sum on your downloaded ISO, just to make sure it is okay.

- Boot the ISO to the menu. Sounds like this make take a few attempts on yours. 

- _If_ the first Screen is the black screen with the person/keyboard screen > Press Escape.

- This will get you to a low-res language selection screen > Press Escape.

- This will get you to the Advanced Installation Menu 

- Press F6... it will bring up a dropdown boot option menu.  Press escape.

- That will close the dropdown, but now an editable boot line will be displayed at the bttom of that screen. It you Arrow left a few times, the cursor will diplay.  Move it to before the "--".

- Add the text "i915.modeset=0 "

- Chose the try button.

*** If that still doesn't work, then I reboot and get back to the Advanced menu...

- Press Escape

-  This will prompt a Message Box saying "Exiting- You are leaving the graphical boot menu. You are starting the text mode interface."

- It should start a hardware probe to your video hardware to try to ID it.  On some older Intel chips, it will display a text message error saying it couldn't "ID the mode: XXX", blink, then displays a text menu asking for a display mode type... I think I usually use 640x480x16, which I think I remembr as "7"...

- That starts the installer in a text mode.  I go through the install... After the reboot, it seems to work just fine.

*** Note- Sometimes the above, at the video probe, will dump you down to a  text prompt saying "boot:"  Press enter and it will bring you back to the Avanced Install Menu... At this point I chang tactics.  Then I use the Ubuntu "Minimum" Installer ISO. Which is a text based installer. When it gets to the Taskel Software Install screen, I select Xubuntu desktop. 

/*
I don't know what it is about those older Intel's, but since I've found several ways around it, I don't spend much time spinning my wheels on it...
*/

Hope this helps for you.

---

### Post by sowdust on 2011-10-25
Thank you very much for your swift and detailed reply.
The only thing I had to do was to press <tab> at the boot menu and add the i915.modeset=0 and Xubuntu started fine (maybe at a lower resolution, but it could also be because drivers werent installed yet.

I went through the install process and everything seemed to work just fine; the only thing that could have gone wrong is that I manually partitioned the hard disk, setting 2gb for swap at the beginning and two primary  ext4 partitions of 10 gb and 300 gb, respectively mounted to / and /home

Now booting I get a black screen at first, that after a few seconds shuts down, while the hard disk led keeps working for a while and then becomes blinking at a semi-fixed frequency.
Probably it is just my imagination, but when I shut down the laptop the last time holding down the power button I thought I had an instantaneous glance of the desktop. But again, I might be hallucinating.

EDIT: now after two fresh installs - last one with default partition table - i managed to make grub showing, and adding the i915modeset line xubuntu finally booted well. The overall graphic just seems a little worse that what it should be and even if i added that line and nosplash --verbose to the default grub entry the first thing that appears after grub leaves is the xubuntu splash screen.
My travelmate is a 5335

---

