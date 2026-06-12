---
title: "use external hard drive as usb flash drive?"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by waterbottle on 2010-05-15
Please forgive my horrendous lack of knowledge. 
I am trying to install Ubuntu netbook remix on my netbook with a usb external hard drive instead of a flash drive. So far I've used unetbootin to (mount?) Ubuntu onto the hard drive. I've changed the boot order but it just loads into Windows instead.
My questions are...
Is this even possible to do, or did I just waste a lot of time?
If what I am doing could work, what should I do about my computer not booting from the external hard drive?
Thanks!:)
---waterbottle

---

### Post by darkod on 2010-05-15
Are you sure unetbootin finished the process correctly? Can you boot that usb hdd on another computer?

As for the BIOS settings, usually the device is called USB-HDD even when you are using a usb stick. So you will need to make sure USB-HDD is before HDD and you save the settings. As an alternative, if you have a Quick Boot menu you can use that to boot from USB-HDD without changing BIOS settings.

If you need further help with the unetbootin process, just ask.

PS. unetbootin shouldn't not mount ubuntu onto the hdd. I don't know whether you used the term wrongly, because the only thing unetbootin is supposed to do si:
- unpack the ISO to the usb hdd (stick)
- write a bootloader which will start up the files from the ISO (and this is the crucial part)

---

### Post by efflandt on 2010-05-15
Some systems may have trouble recognizing that there is a hard drive attached externally if they boot too fast before the drive spins up.

I have especially had that problem with Dell laptops, even if USB has been set before hard drive in the boot order.  It seems like the only way I can get them to boot from an external hard drive is either to reboot with the drive already connected, or from cold boot, have to go into CMOS setup and change something that does not matter, so it reboots from scratch instead of resuming from there.  And then I still have to hit the key to select a boot device, but at least USB shows up then.

---

### Post by oldfred on 2010-05-15
why not just a full install to the hard drive?

Install karmic Screens shown with advanced button
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

ASUS EeePC netbook PC 10.04 install
[http://members.iinet.net/~herman546/p28.html](http://members.iinet.net/~herman546/p28.html)

---

### Post by pete_m on 2010-05-15
I read this thread with interest . .

I'm an EEE PC user planning an imminent move to Ubuntu Lucid in the hope of performance improvements and the benefit of tying in to a fresh LTS release.

i've put some work into my existing Ubuntu install based on 9.10 karmic nbr2 and am very happy with the results - full credit and thanks to all

First screenshots - more soon - of my work in progress at

[http://www.youtube.com/watch?v=YoI4wRVVjBs](http://www.youtube.com/watch?v=YoI4wRVVjBs)

i'm therefore hoping to be able to upgrade my machine rather than do a fresh install, tho i have by now got .iso's of my present install and backups( dumps ) of gconf.

i'm still comparitively new to Linux so any observations and guidance will be much appreciated ..

i have an external USB 320Gb HDD so i've been thinking of making this a 'live' system, or perhaps of making a full install of Lucid to that drive.

I'm experimenting with usb-creator to be sure of having a reliable boot of my present system before proceeding. 
no luck so far with providing persistent storage on the stick - any ideas ?
  .
if i were to let usb-creator to format  the stick what partitioning if any does it do ?

if i understand correctly unetbootin lets one boot directly from an .iso image on the stick . .
is it possible to use this prog to boot from a number of iso's living on the same stick ?
(  without having to get too far into the  arcana of chain-loading .. )


Best to all . .

---

### Post by waterbottle on 2010-05-15
Hello again!
I took longer to get back than I expected.
@Darkod: Nope, it didn't work on any other computers here. I figured I'd screw something up one way or another.
@Darkod & Efflant: I've tried the the Quick Boot menu and the external hard drive spins fast enough from the start.
@Oldfred: I want to take my netbook places without carrying the external hard drive everywhere to boot Ubuntu. I also don't want to pay money or void my warranty by moving hardware around in my netbook. :P (I'm still reading the last article though)
@Pete_m: ???

Also, the reason I'm using an external hard drive is because my external disk drive doesn't work, I live too far away from a store that sells computer devices for me to bother to go there, and I am much too impatient to order something online. :)

Thanks for the replies.
---waterbottle

---

### Post by darkod on 2010-05-15
OK. So, if i understood correctly, you are using unetbootin from windows right?

Start the applications again, click on Disk Image option and select the ubuntu ISO. At the bottom you should select where to put the bootloader. By default I think USB Stick is selected but not sure if the hdd is detected as such. You can notice whether the hdd drive letter, like D:, E:, F:, etc, is shown or not. If not, try changing the option from USB stick to Hard Disk.
BUT MAKE SURE you DO NOT select C:!!! Select the letter of your usb hdd.

After it's done, you don't have to reboot immediately, just close unetbootin.
See if you can boot from the usb hdd and there should be some basic boot menu that unetbootin created, usually the entry you need to select is called just 'default'.

---

### Post by waterbottle on 2010-05-15
That's exactly what I did before. :)
However, you gave me an idea on what I might have messed up on!
Going to test that idea out...
---waterbottle

---

### Post by waterbottle on 2010-05-15
All right, my idea failed and I'm falling apart.
I downloaded the iso file, formatted the external hard drive, used unetbootin on the file with that hard drive. The external drive was renamed to "Install Ubuntu Netbook" with files included in it, then I restarted my computer and tried booting from the usb external hard drive. It booted windows instead.
I followed all of these steps and I can't figure out where I went wrong. :(

---

### Post by darkod on 2010-05-16
Are you sure your computer can boot from usb? After the second attempt, can the usb hdd boot on another computer?

Another alternative is (but you have to 'waste' a CD): Burn the ISO on a cd. Boot with the cd another on another computer if it has a cd-rom. Plug the usb hdd in that computer too. Go into live mode (Try Ubuntu) and in System use Startup Disc creator to create the bootable usb hdd from the ISO.

I'm not sure if unetbootin is not creating the bot properly. The above procedure should definitely work. Hopefully... :)

---

### Post by waterbottle on 2010-05-16
I'll try the alternative method a little later today. :D

---

### Post by waterbottle on 2010-05-16
[SIZE=7][B]Success!
[/B][SIZE=3]Thanks for all of the help!
I'm posting this reply with Firefox on Ubuntu Netbook Remix.
:guitar:
[/SIZE][/SIZE]

---

### Post by pete_m on 2010-05-17
Excellent - that's good news . .

I've started a   [thread about USB stuff]("http://ubuntuforums.org/showthread.php?p=9313733") and oldfred has put some very useful links. 

[Herman's site ]("http://members.iinet.net/%7Eherman546/")has loads of relevant material - 

[]("http://members.iinet.net/%7Eherman546/")

---

