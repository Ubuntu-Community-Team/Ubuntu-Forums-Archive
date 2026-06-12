---
title: "Installing Ubuntu 10.10 x64"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by DsHs on 2011-02-11
Hi,

I'm new to Ubuntu and I'm having problems installing it.
I have an i7 processor and running windows 7 x64.
I just downloaded the .iso file (I chose Ubuntu 10.10 x64) and burned it into a cd like explained in the instructions.
I changed the boot order to boot from cd and restarted.
It boots from the cd and I see a purple screen with "ubuntu" and 5 dots that change colors like some kind of loading thing.
That's all the experience I could get from Ubuntu so far. Half an hour later the "loading thing" didn't move anymore.
I tried again and it just keeps loading...

Any suggestions?
Thank you.

---

### Post by tejendra on 2011-02-11
its not a problem i think,may be you should try once again it takes time but it always get installed. Try once again and just left it to do the working.

---

### Post by sikander3786 on 2011-02-11
Welcome to the forums :-)

Please post your hardware specs including RAM, Processor and Graphics card.

Secondly, as soon as the computer starts booting from the Live CD, hit any key and you'll see a menu. Press F6 and enable nomodeset. Continue boot, does it take you to the desktop this time?

If it still doesn't, there are 6 of boot parameters in F6 menu and you might need to try all of them, one-by-one.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by DsHs on 2011-02-11
Ok, I'll give it a try.

---

### Post by Valentin630 on 2011-02-11
> **sikander3786 said:**
> Welcome to the forums :-)

Please post your hardware specs including RAM, Processor and Graphics card.

 
I have the same problem with 10.10.x64 on 2 computers and it seems me it does not depend on hardware.

The installation stops with: 
mounting /dev/loop0 on //filesystem.sqashfs failed: Input/output error.

I think the message does not point to the live CD (I have checked it)?

But if it is important: both computers with AMD X2_x64 and Nvidia and Ati Radeon cards 
(I see the graphics works)

---

### Post by anoopm101 on 2011-02-11
try usb booting, its better and faster

---

### Post by Valentin630 on 2011-02-11
> **anoopm101 said:**
> try usb booting, its better and faster
I did, the result is:
PANIC: early exception ....

I googled and found that people have the same problem and did not see the
solution. Don't you think that it is very strange?
And I do not have the md5sum to check the downloaded image!
Is here an Expert?

---

### Post by Valentin630 on 2011-02-11
> **DsHs said:**
> Hi,
Any suggestions?
Thank you.

Take a DVD version 

[http://nginyang.uvt.nl/maverick/](http://nginyang.uvt.nl/maverick/)

at list you can be sure what have you downloaded:P

P.S. One year ago I have downloaded Ubuntu-x64 version and couldn't to install it
because of some errors. I begin to think that it is not random phenomena...:(

---

### Post by DsHs on 2011-02-12
That was the same error I got.
I've an i7, NVidia 360M and 8gb of ram (ddr3 1333MHz) -> Asus G60Jx.
I can't boot from usb. I mean, I've skrewed with the device priority in the BIOS and now I can only either boot from cd or hdd. 
I'm too lazy to keep looking for a solution for that...
I've burned another cd and I'm planning on trying it. I'll report the results.
I'm picking the right x64 version, right?

edit:
I tried with dvd. I got past that screen but it crashes after a while.
Tried again with cd. Error is something related to user id missing.

---

### Post by Valentin630 on 2011-02-12
> **DsHs said:**
> 
I tried with dvd. 

my attempt with dvd (see the link above) was sucsesseful: I have 10.10.x64 on
my computer.
Conclusion: the CD from ubuntu size is a rubbish, buy DD if you unable to download it free:D

---

### Post by oldfred on 2011-02-12
Are you burning at the slowest speed you can, it often makes a better CD. You often need a good liveCD or USB version to make repairs.

Some have success with the alternative installer. It is not the graphical version but the old school text based. It is not a liveCD.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by DsHs on 2011-02-12
I burned the dvd at the slowest speed.
Dvd = crash after choosing language.
Cd = won't do a thing
Usb = can't be done

People come up to me saying how awesome Linux is. In 2 days, Linux made me force the pc to shut down more times than Windows ever did since I got this computer.
I really was hoping to use it, but I can't even start to install it.
Is there someone who can tell me how to fix this? I'll provide any information that you think is necessary.

---

### Post by oldfred on 2011-02-12
Back to first post. If you have Ubuntu and dots working it may be video issue. 

What video card/chip are you using?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
boot from the cd, press F6 and then select the nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

Have you checked this:
Note Known Issues section
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes)

[http://www.phoronix.com/scan.php?page=article&item=intel_sandy_speed&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_sandy_speed&num=1)

---

### Post by DsHs on 2011-02-12
I have a GTS 360M.
With the cd I won't get past the loading dots.
With dvd I chose the language, then I see dots, then it crashes and everything's messed up. In my first try I saw pieces of my windows desktop in random order. In my second try I got to see black and white squares.
Are you sure that "nomodeset" will do the trick? Is that enough to keep the installation from crashing?

---

### Post by oldfred on 2011-02-12
I cannot be sure without trying it. On my computer I installed from USB flash drive and it totally turned monitor off. Only because I was on USB I could see it still flashing - install was still working, but I could not see anything. The nomodeset worked for me.

---

