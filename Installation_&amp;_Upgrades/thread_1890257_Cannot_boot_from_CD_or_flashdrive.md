---
title: "Cannot boot from CD or flashdrive"
date: 2011-12-03
forum: Installation &amp; Upgrades
---

### Post by chowoutside on 2011-12-03
I tried to install Ubuntu 11.10 on my new desktop, but when I tried booting from a cd, I get stuck at this message

udevd[149]: '/sbin/modprobe -bv pci:000010DEd00001081sv00003842sd00001572BC03sc00i00' [183] terminated by signal 9 (killed)

and when I boot from a flashdrive I get the same error but there are more lines after

Direct-Access
Attached scsi generic sg2 type 0
3948554 512 bye logical blocks: (2.02 GB/1.99GiB)
Write Protect is off
Mode Sense: 00 00 00 00
Asking for cache data failed
Assuming driver cache: write through
Asking for cache data failed
Assuming driver cache: write through
sdb1
Asking for cache data failed
Assuming driver cache: write through
Attached SCSI removable disk

I have tried multiple flash drives and still get this same error. I cannot boot into live CD/USB. I get the same error. 

Anyone know whats going on?

---

### Post by dandnsmith on 2011-12-03
Sounds like you have a hardware problem with that PC.
Do you already have an OS installed on it, and can that access the CD drive?
It might help with this problem to post more hardware detail.
Have you tried multiple LiveCDs, or just the one (excluding copies from the same download)?

---

### Post by coffeecat on 2011-12-03
Did you burn the CD and flash drives from the same downloaded ISO? Since you are getting the same or similar error each time, another possibility is that the ISO is corrupted. Did you check the md5 hash? If not, you may find this helpful:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by chowoutside on 2011-12-03
Thanks for the quick reply.

I already have Windows 7 installed and the CD drive is the one that burned the CD. I have it burned on a DVD not a CD. Would that make a difference?

Intel Core i7-2600K Sandy Bridge 3.4GHz
MSI P67A-G43 (B3) LGA 1155 Intel P67
G.SKILL Ripjaws Series 16GB 240-Pin DDR3 SDRAM DDR3 1600
EVGA GeForce GTX 570

I have not tried another download. Just 2 flash drives and 2 DVDs with the same iso file.

---

### Post by chowoutside on 2011-12-03
I just checked the md5 hash and they were the same. So it's not the iso file.

---

### Post by fantab on 2011-12-03
> **chowoutside said:**
> I just checked the md5 hash and they were the same. So it's not the iso file.

Try another download and if you can download it from a torrent. Then try burning the .iso at the slowest possible speed and try reinstalling. This will make us double sure that nothing is wrong with the installation media.

---

### Post by dandnsmith on 2011-12-03
As far as I know, using a DVD instead of a CD should cause no problems (if properly written) - I regularly boot from a linux mag's DVDs to try new distro releases.

---

### Post by chowoutside on 2011-12-03
I don't think its the iso file. I have tried multiple flash drives using different software to make the usb bootable.

---

### Post by oldtimer7777 on 2011-12-03
> **chowoutside said:**
> I don't think its the iso file. I have tried multiple flash drives using different software to make the usb bootable.

Just out of curiosity what kind of make and model computer is this?

---

### Post by chowoutside on 2011-12-03
> **oldtimer7777 said:**
> Just out of curiosity what kind of make and model computer is this?

Custom built.

---

### Post by oldtimer7777 on 2011-12-03
> **chowoutside said:**
> Custom built.

Specs please.

---

### Post by mo.mashi on 2011-12-04
> **chowoutside said:**
> I just checked the md5 hash and they were the same. So it's not the iso file.

I had the same problems as you. This is how you solve it:

STEPS TO BURNING A GOOD INSTALLATION MEDIA AND VERIFYING IT:

[1] MAKE SURE YOUR ISO DOWNLOADED CORRECTLY

Don't verify the download with MD5! It's too weak: if a downloaded  DVD/CD image is only slightly corrupted, it may still give you a passing  MD5 (this happened to  me). Ubuntu also gives out the SHA256 signatures of their media. Much  less risk of a collision (that's when two different files come out with  the same hash signature). I found the SHA256 signatures here:

[http://sles-smt.uni-konstanz.de/linrz/linrz.hiwi.rz.uni-konstanz.de/images/ubuntu/checksums](http://sles-smt.uni-konstanz.de/linrz/linrz.hiwi.rz.uni-konstanz.de/images/ubuntu/checksums)


open the prompt, go to the  directory of your iso and type:

sha256sum <put the name of your ISO here>.iso

Eg:
sha256sum ubuntu-11.10-dvd-amd64.iso 

if sha256sum doesn't work, download and install the jacksum package and execute the following command:

jacksum -a SHA256 <name of your iso>.iso

)

Compare to results of the web.

[2] WHEN YOU BURN YOUR CD/DVD, use slowest speed your burner hardware can  handle and check the verify CD/DVD option in your burning software.

[3] WHEN YOU BOOT YOUR CD/DVD: use the check CD/DVD option. 

It may be a bit more work then your used to  but trust me, the last  thing you want to be doing is running a corrupted installation. At the  best, the installer will quit on you, at the worst, you'll be running a  corrupted OS without realizing it....

---

### Post by Topsiho on 2011-12-04
Just to be sure, as I don't see it in any of the replies: did you burn the .iso file AS AN IMAGE?

It doesn't matter whether you burn it on a CD or a DVD (if the .iso file is not too large for a CD, of course).

Topsiho

---

### Post by dandnsmith on 2011-12-04
While we're on that track, you can easily check that you got the method correct. If you load the CD/DVD with an OS already running, you'll see a whole filestructure (not just a single file) if you got it right.
However I'm reasonably sure, from the general detail that that comment wasn't needed.

---

### Post by chowoutside on 2011-12-30
hey guys. Just had a chance to try this again and I ran into the same problems. I don't believe that there is anything wrong with the iso file.

Here are my full specs:

MSI P67A-G43 (B3) LGA 1155 Intel P67
Intel Core i7-2600K Sandy Bridge 3.4GHz LGA 1155 95W
G.SKILL Ripjaws Series 16GB (4 x 4GB) 240-Pin DDR3 SDRAM DDR3 1600
EVGA SuperClocked 012-P3-1572-TR GeForce GTX 570
Rosewill BRONZE Series RBR1000-M 1000W 
LIAN LI Lancool PC-K62
LITE-ON DVD Burner SATA Model iHAS124-04
Rosewill RCR-IC002 74-in-1 USB 2.0 3.5" Internal Card Reader
ZALMAN CNPS9700 LED 110mm 2 Ball CPU Cooler

Would trying to install 64bit version of ubuntu be causing this problem?

---

### Post by dandnsmith on 2011-12-30
In your predicament I would:
1) check BIOS displays, to see all hardware is recognised
2) try removing all but 1 RAM stick, and boot with that
3) try a different CD drive

---

### Post by drthrd on 2011-12-30
You have a GeForce GTX 570. I have had problems with the cd also. I would try this [http://ubuntuforums.org/showpost.php?p=11572583&postcount=7](http://ubuntuforums.org/showpost.php?p=11572583&postcount=7) and see what happens.

---

### Post by chowoutside on 2011-12-30
> **drthrd said:**
> You have a GeForce GTX 570. I have had problems with the cd also. I would try this [http://ubuntuforums.org/showpost.php?p=11572583&postcount=7](http://ubuntuforums.org/showpost.php?p=11572583&postcount=7) and see what happens.

Thanks that did the trick. But I just booted into ubuntu off the cd. If I install it to my harddrive, would I have to keep changing the nomodeset? Also would my resolution be fixed somehow if I do a complete install?

Thank you so much for your help.

---

### Post by drthrd on 2011-12-30
> **chowoutside said:**
> Thanks that did the trick. But I just booted into Ubuntu off the cd. If I install it to my harddrive, would I have to keep changing the nomodeset? Also would my resolution be fixed somehow if I do a complete install?

Thank you so much for your help.

What I did was install Ubuntu and when it restarted I had to use the safe mode I think its called. Once in Ubuntu I installed the proprietary drivers using "Additional Driver". Then everything was fine.

Went back and seen what I did. When the boot loader came up I choose Recovery Mode. Then on the next set of options I choose to start normal boot. Then installed the proprietary drivers. As far as I know if you do not choose to use a different driver you would have to add the nomodeset line to your boot. Have to edit grub config file. I am kinda of busy right now but shortly I am going to do more testing.

In my opinion someone should make a sticky explaining how to use nomodset for Nvidia cards. For some reason on certain Nvidia cards there is a problem with the Nouveau driver. However from me testing Kubuntu does not do this though. Other ditros I have tried does not do this either (Fedora, Mandriva,  openSUSE). But Ubuntu and Parted Magic does. Very strange. If anyone is trying Ubuntu and having problems with the Live CD hanging and stalling or problems like that and have a Nvidia card they should try the nomodeset, it is something with the Nouveau driver.

---

### Post by chowoutside on 2011-12-30
Finally got it installed. Thanks everyone for the responses.

---

### Post by emerson1234567890 on 2011-12-31
I got the same problem but it shows a flashing line instead

---

