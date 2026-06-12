---
title: "Ubuntu live CD won't boot!"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by dahliorse on 2006-12-22
Hello!
I have been trying to get Ubuntu liveCD to work with no success. I've tried downloading the torrents from various locations. I've burned the images at various speeds with no success. I've been using quality CD's so I'm sure that's not a problem. 
When ever I start up the computer with the live CD in, it just hangs with the Ubuntu logo and does nothing else!
I've gone through quite a number of CDs trying to get this to work and I've even tried it on my old computer with no success. 
I check the md5 check sums and that's OK. So apparently the download worked! 
So what's going on? Is this particular file download corrupt in some way? Is there something wrong with the torrent file?
grateful for any help.

---

### Post by wpshooter on 2006-12-22
First get yourself a few quality brand named CD-RWs so you can use them over and over again.

I would suggest that you download the ISO image from the Ubuntu sites via regular download method and then burn the image to the CD at 4X or less.

Then make sure you check the integrity of the CD by running the verification function found on the initial Ubuntu boot screen menu.

Run the memtest on your memory.

Try installing using safe video mode.

How much memory does your computer have ?

---

### Post by CarbonPlexus on 2006-12-22
I'm having the same issue. I downloaded the ISO file from the Ubuntu site via regular download method and verified the MD5sum. The CD won't let me start or install ubuntu or verify the integrity of CD from the menu (it still hangs at the Ubuntu logo). Safe video mode doesn't work either. The only one that works is the memtest which came out fine. I know when I had problems with an earlier ISO burning it at 1 or 2x instead of the normal rate fixed the problem but my new CD/DVD burner won't let me burn at any less than 8x. Any suggestions?

---

### Post by TheTeZ on 2006-12-22
Hi, I am in what I like to call my "Quest For The Perfect Operating System"
I used 98 cuz it was pretty amaizing, what i mean by this was i could hack into my own windows, and change everything. If anyone knows who strong bad is, i had it running like good old compy 386, looked the same and ran the same... Yes on 98... Pretty cool. Well I used it up untill maybe 6 months ago because, i couldent stand the crashes, and .. the crasshes, plus the fatal BSOD.  Well xp's ok, but ive got something against it... i just loath it deep down inside. Linix is interesting, ive done a little research and ive tried a few distros. The one on my comp is freespire... Not a huge fan... 
I Cant install the thing. The live CD wont boot, it will start it will get past the ubunto black boot screen, but then these two messages scroll down a black screen:
[17179###.#######] hda:ide_intr:huh? expected NULL handler on object
[17179###.#######] Buffer I/O error on device hda, logical block 15455!
No idea what these mean, but this is how i have it set up
Drive C. - Windows XP [its own hard drive]
Drive D. - Windows 98 [on a SATA hardrive in its own partition]
Drive E. - FreeSpire [on that SATA hardrive in its own partition]
Drive F. - Where I Am TRYING to put UBUNTU 6.10  [on that SATA hardrive in its own partition]

Can Anyone please tell me what these errors mean? 
i downloaded the file from the UBUNTU site and burned it at 4x i really dont think its the CD .

---

### Post by DTR00GT on 2006-12-22
> **CarbonPlexus said:**
> I'm having the same issue. I downloaded the ISO file from the Ubuntu site via regular download method and verified the MD5sum. The CD won't let me start or install ubuntu or verify the integrity of CD from the menu (it still hangs at the Ubuntu logo). Safe video mode doesn't work either. The only one that works is the memtest which came out fine. I know when I had problems with an earlier ISO burning it at 1 or 2x instead of the normal rate fixed the problem but my new CD/DVD burner won't let me burn at any less than 8x. Any suggestions?

I have the same problem - its not your CD's ( I have tried 6 different brands including DVD & DVD-RW).

I get to the Ubuntu logo (I think cuz the box is 'stripped out and can't see a thing) against a orange screen. I hear a tune (kinda like the windows startup music) and then nothing.

Thought it was my machine alone......At least windows installs :rolleyes:

---

### Post by aolforbroadband on 2006-12-22
I'm having a similar problem. After I choose whichever option, the files start loading then it says something can't be read?

Bummer. I really want to try out Linux. :(

---

### Post by spockrock on 2006-12-22
what are all your guys system specs?

---

### Post by aolforbroadband on 2006-12-22
Core 2 Duo E6300
Intel DG965WH Mobo
2GB DDR2 800
Geforce 7900GS
160GB SATA HD

---

### Post by DTR00GT on 2006-12-22
> **spockrock said:**
> what are all your guys system specs?

AMD64 Opteron 165
DFI Lanparty Ultra D (NF4)
2Gigs of DDR (Crucial)
Geforce 7800GT
250Gig Sata x2
320Gig Sata

---

### Post by colores on 2006-12-22
AMD X2 3600+
Asus M2NPV-VM
1Gigs of DDR2
Geforce 6150 (onboard)
80Gig PATA x2
40Gig PATA

SATA options in bios OFF
Sound, USB OFF

Freezes after load kernel in boot from cd (6.10 amd64 desktop)
Dapper 32 and 64 works fine.
With no splash screen option freezes in **"probing IDE interfaces ide0"**

Options test without luck:

[i]boot: live acpi=off
debian-installer/probe/usb=false
acpi=force irqpoll
noapic nolapic[/i]

Not work with other CD ROM drive...
:neutral: 

Sorry for my bad english 8)

---

### Post by spockrock on 2006-12-24
> **DTR00GT said:**
> AMD64 Opteron 165
DFI Lanparty Ultra D (NF4)
2Gigs of DDR (Crucial)
Geforce 7800GT
250Gig Sata x2
320Gig Sata

ok I have a very similar setup, as yours, I get the same problem, try booting in safe graphics mode, that might work, the problem is the free nv drivers do not work, or play nice with our cards.  You can install via the alternate disc, and then when you get to the login screen you need to press ctrl+alt+F1, login, then install the nvidia-glx drivers, and you should have no problems.

> **aolforbroadband said:**
> Core 2 Duo E6300
Intel DG965WH Mobo
2GB DDR2 800
Geforce 7900GS
160GB SATA HD

ok, I am unsure if this is the exact problem but I recall there were issues with jmicron pata controllers on some core2duo based boards.  I believe this should of been fixed have you tried booting with the noacpi options??

> **colores said:**
> AMD X2 3600+
Asus M2NPV-VM
1Gigs of DDR2
Geforce 6150 (onboard)
80Gig PATA x2
40Gig PATA

SATA options in bios OFF
Sound, USB OFF

Freezes after load kernel in boot from cd (6.10 amd64 desktop)
Dapper 32 and 64 works fine.
With no splash screen option freezes in **"probing IDE interfaces ide0"**

Options test without luck:

[i]boot: live acpi=off
debian-installer/probe/usb=false
acpi=force irqpoll
noapic nolapic[/i]

Not work with other CD ROM drive...
:neutral: 

Sorry for my bad english 8)
your english is fine, umm.... I am not sure why you are having this problem have you tried looking at the wiki, or launchpad for bugs, because people often find these bugs post, them and often have fixes for them as well.

---

### Post by hoagie on 2006-12-24
I have the same problem!
I tried many cd's and dvd's, (quality brands) but whenever I  try to burn the image, the burner gives me an error message.

---

### Post by aolforbroadband on 2006-12-25
> **spockrock said:**
> ok, I am unsure if this is the exact problem but I recall there were issues with jmicron pata controllers on some core2duo based boards.  I believe this should of been fixed have you tried booting with the noacpi options??

How do I do that?:???:

---

### Post by Sophie on 2006-12-26
Hello, guys!

Happy holidays to all!

I've just read all of this thread, and its just what I've been fighting for the last 7 hrs or so! ;)  its really quite sad- we all want Linux so bad but its just out of our reach! :mad: 
If we all have the same problem- and we do- then maybe its something with the distro and we should just try something else? Tho I like Ubuntu, and it was the most recent... Btw, I've tried Fedora just before and encountered the same obsticle. It just hangs. Sooooo annoying :D 
Anyway, good luck to all with everything 8)

---

### Post by spockrock on 2006-12-26
> **aolforbroadband said:**
> How do I do that?:???:

when you get to the boot menu, press F6, then put in your other options.

have you guys tried to use the alternate disc??

---

### Post by Sophie on 2006-12-26
Hi, people!!!

Check this out:
I tried 'Virtual Machine' software from the net (download), and it made the live DVDs for both Ubuntu and Fedora Core 5 run and install whereas before, I was having the same problem! See if it works for you.:-D  I can't say for sure if it even helped me, cause its still going. I'm writing from my bro's PC. 

Cool, good luck, and have fun. It'll all work eventually- thats what I keep telling myself, at least. ;)

---

### Post by aolforbroadband on 2006-12-26
I tried F6 and this is what I'm getting:

/bin/sh: can't access tty; job control turned off (initramfs)

---

### Post by Toufik on 2006-12-28
> **aolforbroadband said:**
> I tried F6 and this is what I'm getting:

/bin/sh: can't access tty; job control turned off (initramfs)

It won't help you but I've got exactly the same error!

I'm waiting for the alternate CD to download... Surely I will burn it at low speed!  I'll let you know if it works

---

### Post by xtknight on 2006-12-28
You all have NVIDIA graphics cards and you're using Edgy.  Safe video mode does not do anything in Edgy by the way, due to [bug #59618]("https://launchpad.net/distros/ubuntu/+source/xorg/+bug/59618").  So, you're still using the nv driver and that hangs on recent NVIDIA cards.  Your only option is to use the alternate install disk, and then go into recovery mode and change the driver to vesa and reboot.  You could try this as well: [http://www.ubuntuforums.org/showthread.php?p=1680357#post1680357](http://www.ubuntuforums.org/showthread.php?p=1680357#post1680357)

The JMicron PATA driver should not affect the post-gdm boot-up as long as you're booting off another device.  It will however stop before GNOME starts if it is not compatible.

When you say it stops at the Ubuntu logo, do you mean the text-mode one that comes right after the BIOS boots off the CD, or do you mean the Ubuntu logo after GNOME starts?

---

### Post by denisesballs on 2006-12-29
I wanna add I have the Intel DG965WH motherboard as well. I think is going to be a pretty big problem coming up because Intel has an employee purchase for a lot of vendors including this motherboard, the E6300 CPU and Vista Ultimate for a very cheap price. I've tried using my existing Edgy install which is on a PATA drive along with my PATA DVDRW with no luck, it just hangs on boot. I even went as far as to buy a new SATA HDD, but I still cannot boot either the Edgy LiveCD or the Fiesty daily build (which supposedly has the newer kernel with the PATA controller fix). I don't know how else to get around this aside from maybe buying a SATA DVDRW as well and I just bought this PATA one!

---

### Post by rramalho on 2006-12-30
The problem you refer on the DG965WH is related to a Marvell P-ATA chip, that has drivers in the 2.6.18 kernel at least. OpenSuse 10.2 installed just fine on my system, wich has a DG965WH.

I would like to install Edgy somehow no my new system... I don't really like OpenSuse... It doesn't have "apt-get"...

---

### Post by denisesballs on 2006-12-30
> **rramalho said:**
> The problem you refer on the DG965WH is related to a Marvell P-ATA chip, that has drivers in the 2.6.18 kernel at least. OpenSuse 10.2 installed just fine on my system, wich has a DG965WH.

I would like to install Edgy somehow no my new system... I don't really like OpenSuse... It doesn't have "apt-get"...

Fiesty has the 2.6.20 kernel and that doesn't boot with this motherboard either.

---

### Post by PilotJLR on 2006-12-30
I have a DG965WH as well... as you know, it won't install from anything connected to the IDE port.

I successfully installed Edgy using a USB DVD drive. If you have one, or can borrow one, it makes things pretty easy... once installed, you just have to add the marvell patch, and you're all set.

---

### Post by denisesballs on 2006-12-31
> **PilotJLR said:**
> I have a DG965WH as well... as you know, it won't install from anything connected to the IDE port.

I successfully installed Edgy using a USB DVD drive. If you have one, or can borrow one, it makes things pretty easy... once installed, you just have to add the marvell patch, and you're all set.

Do you have a link for this patch or a howto? All the info. I have about this situation is on the wiki here: [https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

---

### Post by PilotJLR on 2006-12-31
Sure - at least for me, actually installing Edgy requires nothing special OTHER than a USB DVD drive.

Once installed using a boot USB DVD/CD drive, everything is normal... except your internal CD/DVD drives or IDE hard drives will not work. FOr that, follow the directions here:
[https://launchpad.net/distros/ubuntu/+bug/67012](https://launchpad.net/distros/ubuntu/+bug/67012)

If you are trying to install to an IDE hard drive instead of a SATA one, then I'm not sure how to get around that... other than buying a SATA hard disk  :-)

---

### Post by denisesballs on 2006-12-31
> **PilotJLR said:**
> Sure - at least for me, actually installing Edgy requires nothing special OTHER than a USB DVD drive.

Once installed using a boot USB DVD/CD drive, everything is normal... except your internal CD/DVD drives or IDE hard drives will not work. FOr that, follow the directions here:
[https://launchpad.net/distros/ubuntu/+bug/67012](https://launchpad.net/distros/ubuntu/+bug/67012)

If you are trying to install to an IDE hard drive instead of a SATA one, then I'm not sure how to get around that... other than buying a SATA hard disk  :-)

Yeah, I actually went out and bought a SATA drive anyways, I just didn't want to have to buy a SATA optical drive as well since I just bought my PATA dvdrw. Bearing what5 you said in mind, I think I'm just going to dump my Edgy install from my PATA HDD to my SATA HDD and apply the patch then. That is actually a lot better of a solution than I had in mind. Thanks a bunch man! Are the instruction for applying the patch in the tarball?

---

### Post by PilotJLR on 2007-01-01
Yeah, that is best overall... a slow old IDE drive would just be wrong with such a nice new motherboard  :-)

Install instructions (for after you install via a USB CD drive) are on the launchpad link... basically you untar the file, do make and then insmod pata_marvell.ko and the IDE attached drives will then work.

---

### Post by naparhi on 2007-01-01
Hello,

ubuntu 5.10 is runnning on my old IBM APTIVA Intel Pentium III 256MB RAM, 10 GB Disk, Floppy, CDROM. Now i'm trying to use xfce instead of Gnome. I found ny way of using xfce with 5.10.

Download of xubuntu-6.06.1-alternate-I386.iso was succesful, burning the imag to CD worked as well. However the CD does not boot. Copying the sbm.bin file to floppy was "hard work". 5.10 does not konw the floppy drive. Root user is unreacheable, doing it via "sudo" is clumsy.

What am I doing wrong?

1) wrong image for booting?
2) special parameters to be used for burning the image?
3) No way of using xfce with 5.10 (hidden switch somewhere)?
4) Slackware Image (10.2) is booting from CD

Hope You had a good start in the new year
Norbert

---

### Post by Sef on 2007-01-01
1) Did you md5sum the download? (not necessary if a torrent used)

2) Did you burn it as an iso?

3) Did you burn it at 4x or less?  Faster can corrupt the burn.

---

### Post by naparhi on 2007-01-02
Hello,

1) the download was done using bittorrent
2) the downloaded image was burned "as is" to cd. Is there anything special to do for burning?
3) the cd is readable with the filesystem browser
4) I don't know the speed, burning was done by my son on his windows machine

Kind regards
Norbert

---

### Post by rramalho on 2007-01-04
> **rramalho said:**
> The problem you refer on the DG965WH is related to a Marvell P-ATA chip, that has drivers in the 2.6.18 kernel at least. OpenSuse 10.2 installed just fine on my system, wich has a DG965WH.

I would like to install Edgy somehow no my new system... I don't really like OpenSuse... It doesn't have "apt-get"...

Hi again!!

I managed to install Edgy on the Intel DG965WHwith an external USB Hard Disk box. I dismantled it, connected a PATA DVD-RW drive to it, and configured the mainboard to boot from USB.

And it installed normally. It's already working. I'll tell you guys later IF the Marvell patch works... People are saying that it can read/write from a harddrive but can't write DVD discs. I'll tell you guys later. :)

The damn thing is FAST. :)

C ya,

---

### Post by denisesballs on 2007-01-11
Wanted to update you guys that I've had incredible success with the Intel DG965WH. All I needed was a USB CDROM to install Edgy to my SATA drive. After the install was complete I applied all the updates, booted into Edgy and my PATA dvdrw and PATA HDD were picked up fine! I didn't have to apply that Marvell or any other patches, and I've been reading/writing to both the PATA hard drive and burning dvds with my PATA dvdrw. I guess it's just that the installer CDs and really any linux CD cannot boot this board in a live environment. Everything is working very well, i can see both CPU cores in /proc/cpuinfo and gkrellm, onboard video was a little sketchy, but the board did have a PCIe x16 slot, so I put in an MSI NVIDIA GeForce 6600GT and with the latest NVIDIA drivers, I am flying with this box. Everything I've thrown at it with Beryl it's handled without a problem; full screen transparent video etc. Some memory advice with this board for those who have it, make sure you get RAM with 5-5-5 timing. I'm using dual channel PC2-6400 Corsair you can find here - [http://www.newegg.com/product/product.asp?item=N82E16820145566](http://www.newegg.com/product/product.asp?item=N82E16820145566) .

---

