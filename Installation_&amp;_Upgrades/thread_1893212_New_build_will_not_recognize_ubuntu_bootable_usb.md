---
title: "New build will not recognize ubuntu bootable usb"
date: 2011-12-09
forum: Installation &amp; Upgrades
---

### Post by Maskedrose on 2011-12-09
So this is my first build, and I'm having a difficult time getting the system to boot.

Specs: Biostar MicroATX  A880G+, AMD Phenon II x6 and 2x 4g G Skill ripjaws... 

I was hoping I could save money and use the hard drive from my old 1gb ram Acer Aspire(running vista yuck)... Vista(and a hdd with 7) will not boot. Both Windows OS go to the "Starting Windows" then quickly cut to a screen that states Windows could not boot up.. would you like to launch Startup Repair... and then it 'attempts' to repair windows and fails. 

So I was like ahhh eff it and I made a usb Ubuntu 64 bit and when I try to boot from that, I get a message like insert disc with boot files and press any key to continue (not those exact words but I am sure you know what I mean.)


What could I have possibly done wrong? I have also tried burning an ubuntu boot disc but each attempt fails(meh).


Could this be something as simple as a setting in the BIOS? Do I need to clean install with a disc(but then why can't I do it from the USB!!??)


Thanks..

---

### Post by bluexrider on 2011-12-09
Windows will not work because of hardware signatures differing from one computer to another. 

Set your BIOS to boot from USB then try it again.

---

### Post by Maskedrose on 2011-12-09
I did set my BIOS to boot from usb.

It doesn't even acknowledge anything being on the USB..

---

### Post by bluexrider on 2011-12-09
> **Maskedrose said:**
> I did set my BIOS to boot from usb.

It doesn't even acknowledge anything being on the USB..
I don't know how you created it, what files are on there or what-not. But this may shed some light on it. Help you get up and running.

 

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Maskedrose on 2011-12-09
I downloaded the ISO from ubuntu.com and used [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) to make the boot usb. I will check out that link you posted.

---

### Post by Maskedrose on 2011-12-09
So.. I accidentally turned my new build on without the hdd connected... USB boot plugged in, though.... Get this..

Ubuntu booted up and asked me if I wanted to install it. I plugged the hdd in at this point and clicked install.

seems fine now.. WTF?

---

### Post by bluexrider on 2011-12-10
> **Maskedrose said:**
> So.. I accidentally turned my new build on without the hdd connected... USB boot plugged in, though.... Get this..

Ubuntu booted up and asked me if I wanted to install it. I plugged the hdd in at this point and clicked install.

seems fine now.. WTF?

Linux assumes you know exactly what you are doing. BTW your last remark....not needed.

---

