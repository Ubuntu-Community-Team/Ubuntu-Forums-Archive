---
title: "Installing on an external USB drive"
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by AGNKim on 2010-09-05
This is probably an extraordinarily easy, yet oft asked, question. I have read some other posts, and they get close to answering, but my ignorance of all things Linux makes me skittish to forge ahead with my mind only half loaded. So I'm asking (again probably). Please forgive my overall noviceness (I just made up that word).

I currently have Ubuntu 10.04 installed on an 80G external drive via Wubi. From what I gather, Wubi isn't ideal for using Ubuntu (and I have had a few errors when booting I attribute to it). I would like to install a dual boot configuration with Win7 and Ubuntu. Can I install Ubuntu to the same external USB hard drive I have it on now (via Wubi) and have it work normally (I would of course uninstall Wubi and format the drive prior to installation). The drive is always plugged in, so there shouldn't be an issue with Grub (which I gather has lead to some issues when said USB drive is unplugged).

Please forgive if this question has been asked ad nauseum.:D

Kim

---

### Post by dave-5B on 2010-09-05
You would want to make sure grub gets installed on the external drive, not the internal one otherwise it's gonna get real confused when you try to boot ubuntu without the external connected (as you said in the question).

This would hopefully leave the windows bootloader intact on the internal drive. Then set the external drives boot priority in the BIOS to be before the internal drive. Otherwise when you install linux grub will generally overwrite the windows bootloader, the only way to get the windows one back is to reinstall windows (massive pain if your dual boot config / grub / ubuntu goes belly up). Lots of the problems I had when doing dual boots were to do with grub and the windows bootloader not playing nicely.

---

### Post by AGNKim on 2010-09-05
Thanks Dave... So it is possible, but I need to:

1. Ensure the Grub loader is also installed to the external drive.

2. Ensure BIOS is set to boot from the USB drive first.

I gather that the Grub loader will initiate when the computer boots and if I wish to use Win7, I can choose at that time to 'jump' over to the C: drive and boot Windows as normal. Correct? I know how to do #2 (heh heh), but how do I ensure the Grub loader is installed to the external drive? Is that an option during installation?

Sorry to be so green. And thanks you again.

---

### Post by Lateralis on 2010-09-05
When you install Ubuntu to your external hard drive, ensure that your BIOS is *already* set to boot from USB first, then CD second, hard drivethird.  That means going into your BIOS to change the boot order then restarting the PC with the Ubuntu LiveCD in the disk drive.  

When you install Ubuntu, grub should then be installed to the external hard disk, rather than the internal one.  

If you want to be absolutely certain that Grub cannot be installed to your internal drive, then disconnect your internal drive during installation.  It will mean that Grub will not automagically add an entry in the boot menu for Windows, meaning you will have to add it yourself.  (I'm sure we lovely folks can help you out with that!)

---

### Post by garvinrick4 on 2010-09-05
If you are using whole drive for ubuntu and it is in USB port it will be drive sdb and internal will be drive sda in linux in Windows they are lettered like C drive D drive and so on.
Boot off of you Cd and choose to install go through process of answering keyboard, language and so on. When you get to installation make sure you choose your external drive not your internal and choose to use whole drive when you get to page 8 their is a advanced tab in lower right, click it and choose sdb not sdb1 or sdb2 but sdb. That will put
your grub (bootloader) in correct place. Remember your external drive is sdb and internal sda if you had another external would be sdc and so on and so on. If you just focus and choose correct drive and put grub in sdb you will be in business. 
 Then you can boot if BIOS is set to USB first or second behind CD just ahead of HDD or you can open BIOS and will be a F key to hit to open a screen where you can choose what  drive you want to boot from.
 It will overwrite whatever is on your external drive when you install The format for Ubuntu is ext4 Windows is NTFS and in Linux / means the same as C: drive in Windows. Enjoy.

---

### Post by thegutterpoet on 2010-09-05
i am trying to do the same thing...install ubuntu an on old internal laptop hard drive in a usb connected bay. I followed the installation until i got to the manually partition screen and did not go past the screen which showed me the following:.

_________________________________________
sda1 (ntfs)        sda2 (ntfs)
104.9mb           320gb

device type  size  used
/dev/sda1 ntfs 104.9mb  35mb
/dev/sda2 ntfs 319965mb   unknown

/dev/sdb
/dev/sdb1 ntfs 320070  3221mb

So in my case, the sdb1 ntfs 320070mb is my USb connected extrernal hard drive??? In its perfectly safe for me to choose that area, and leave my main internal drive completely alone???

---

### Post by garvinrick4 on 2010-09-05
> **thegutterpoet said:**
> i am trying to do the same thing...install ubuntu an on old internal laptop hard drive in a usb connected bay. I followed the installation until i got to the manually partition screen and did not go past the screen which showed me the following:.

_________________________________________
sda1 (ntfs)        sda2 (ntfs)
104.9mb           320gb

device type  size  used
/dev/sda1 ntfs 104.9mb  35mb
/dev/sda2 ntfs 319965mb   unknown

/dev/sdb
/dev/sdb1 ntfs 320070  3221mb

So in my case, the sdb1 ntfs 320070mb is my USb connected extrernal hard drive??? In its perfectly safe for me to choose that area, and leave my main internal drive completely alone???If it is the usb drive it would be to use sdb1 for install and
format it to ext4 and make it / in tab. Then in page 8 click advanced tab in lower right corner and choose sdb to put grub ( boot manager in). I take it sda drive in internal works fine? And yes leave internal drive completely alone it has nothing to do with sdb (external) install. Is Windows in sda drive? Not anything to do with Ubuntu install but sda2 saying unknown is a question for me.

---

### Post by AGNKim on 2010-09-05
Thank you, garvinrick4 (well, thanks to all of you). I am printing those instructions out now and will be installing today. I'll let you know what happens.

Kim

---

### Post by oldfred on 2010-09-05
Some computers promote the external to sda, you just need to be sure which drive is which. 

The to make sure grub installs to the correct drive, use the advanced button on the last partition screen and choose which drive to install grub to: Do not choose partititons.

Advanced button
[http://members.iinet.net.au/~herman546/p24/022f.png](http://members.iinet.net.au/~herman546/p24/022f.png)

External is just like install to two drives, so this shows and example with screenshots.
Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by thegutterpoet on 2010-09-06
> **garvinrick4 said:**
> If it is the usb drive it would be to use sdb1 for install and
format it to ext4 and make it / in tab. Then in page 8 click advanced tab in lower right corner and choose sdb to put grub ( boot manager in). I take it sda drive in internal works fine? And yes leave internal drive completely alone it has nothing to do with sdb (external) install. Is Windows in sda drive? Not anything to do with Ubuntu install but sda2 saying unknown is a question for me.

Thankyou for responding, mate...i just really needed my mind put at ease regarding this install, as in the past I have only ever installed linux onto my internal drives...and even then, the windows i was using on those internal drives could be reinstalled...my sda drive has windows 7 64 bit installed. And yes, it works perfectly well.

I was assuming that as I have a 64 bit intel duo core processor that I should get the 64 bit ubuntu 10,04????

---

### Post by nikRbokR on 2010-09-08
> 
I was assuming that as I have a 64 bit intel duo core processor that I should get the 64 bit ubuntu 10,04?

You don't necessarily have to get the 64-bit version of Ubuntu just because your processor is capable of it. I personally haven't used it, but from what I've heard it has had it's share of unique problems in the past. I usually just stick with the 32-bit because there tend to be a greater array of programs that work with it, and I don't quite think the pros of 64-bit outweight the cons.

Ultimately it's up to you though... good luck

---

### Post by oldfred on 2010-09-08
Four years ago I ran the 32bit version. With Karmic a year ago I converted to the 64bit version and have not had any issues that I can say are because of it being 64bit.

If you want more  info on converting from a subi install.

HOWTO: migrate wubi install to partition by bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by AGNKim on 2010-09-12
Finished the new, clean install. Everything is working great (well, for some reason I have to choose the external USB drive _every time_ I want to boot the GRUB for Ubuntu... I attribute that to Dell and not Ubuntu... or me :) )

Thanks again everyone. I had read that the forums here were very helpful, and I must admit this is true.

Kim

---

