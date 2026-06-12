---
title: "Trouble installing 64 bit Ubuntu 11.04 on a Dell Inspiron 1525 laptop"
date: 2012-06-20
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2012-06-20
This Dell had Vista Home Premium on it but Vista won't boot anymore. Get a message to run a Dell Startup Repair utility to fix some errors. Seems the Master file(s) are corrupted. This Dell Inspiron 1525 model # pp29L is a dual core 2.0Ghz with 3gigs of Ram and should have no problem running 64 bit 11.04.

So Decided to just install Ubuntu 11.04. Pop a Live Ubuntu CD in and it runs fine, like Ubuntu always does. Then decide to install 11.04 and just wipe out Vista. Start the install but if keeps hanging up and stopping after the prompt with the 3 green check marks and 2 red checks to include updates and install mp3 plugins, etc! Tried doing this several times but it just freezes up at that same point and won't go on to install Ubuntu. 

Anyone know why and the solution to get the install to continue?

---

### Post by carl4926 on 2012-06-20
You were able to run the live cd ok
Did you check the media too?

Did you consider trying 12.04?

---

### Post by cybrsaylr on 2012-06-20
I've used that 11.04 Live CD on a couple installs with no problems. Awhile back when I checked that Live CD it checked out fine.
It gave me a prompt to 'upgrade the installer' which I did.

Haven't looked into 12.04 yet.
Like 11.04 because it was rock solid ..... at least for me.
Tried 11.10 when it was released but it was too buggy and I went back to 11.04.

---

### Post by carl4926 on 2012-06-20
When booting the CD, if you hit Esc, you should get the language selection then the option to install or try
Have you been here and done the install without loading the live session?

---

### Post by cybrsaylr on 2012-06-20
When booting I hit F12, then selected boot from CD which worked fine. Then I tried it out first to see how it ran. It ran fine then I hit the option to install and got the language selection. Did that then it moves to the 3 green checks and 2 red checks page, where it freezes up. Never used Esc.

Didn't try going directly to install yet.
Tried it out first, then went to install.


BTW how is 12.04?
Am downloading it right now, both the 64bit and 32bit versions.

---

### Post by cybrsaylr on 2012-06-20
Tried to directly install without running a live session and it still freezes up on the same page right after the language is selected.

I created a live CD for 64 bit 12.04 but I can't find or recall how to check it for errors or check sum. How do you check the media for 12.04?
I recall it was easy to check media with earlier Ubuntu versions.

BTW I'm running a Live CD session now with 12.04....it seems to run OK and when I tried to install 12.04 it hangs up the same way 11.04 did.

Going through the M$ site on this there are some who say a failing HDD could cause problems like this. Is that possible?

---

### Post by Sef on 2012-06-20
> Going through the M$ site on this there are some who say a failing HHD could cause problems like this. Is that possible?

Do you have your hard drive backed up? If not, then back it up first. Also I would back up Vista with [Clonezilla]("http://clonezilla.org"), so you can always restore it until Ubuntu is up and running fine, at a minimum.

---

### Post by cybrsaylr on 2012-06-20
> **Sef said:**
> Do you have your hard drive backed up?

That doesn't matter. This is a laptop a friend gave a friend to use and didn't have anything worth saving. Just discovered it has a 250GB HDD. The friend used it for several months till it stopped working and wouldn't boot up anymore. I was just trying to figure out if it is a Vista problem or a Dell hardware issue.

---

### Post by carl4926 on 2012-06-21
> **cybrsaylr said:**
> That doesn't matter. This is a laptop a friend gave a friend to use and didn't have anything worth saving. Just discovered it has a 250GB HDD. The friend used it for several months till it stopped working and wouldn't boot up anymore. I was just trying to figure out if it is a Vista problem or a Dell hardware issue.

So you are saying the Laptop is Toast?

---

### Post by cybrsaylr on 2012-06-21
> **carl4926 said:**
> So you are saying the Laptop is Toast?

Not sure.
Can't get it to run Vista but in runs 64 bit 11.04 and 64 bit 12.04 fine as a live session, just can't get it to install either of them Ubuntu versions. 

Just ran some Dell diagnostics on that laptop and it reports a few bad sectors on the 250GB HDD, plus says the Master File is corrupt. Not sure if it's worth putting a new drive in that old laptop. The owner said the battery only lasts ~20 minutes on a charge now.

---

### Post by cybrsaylr on 2012-06-22
I suspected the HDD was bad. Took it into a local Office Depot and after running a few tests, they feel the OEM Toshiba drive is failing. They said the reason the Ubuntu Live CD ran well was because it was able to totally bypass the faulty drive. 

They said you can either buy a new replacement drive or get a 16GB SD or SDHC card for about 20 bucks, since there is a slot on the laptop for that. Then they said you can install Ubuntu on that SD card and run Ubuntu off it. They said this card will act as a SSD booting up and running faster than a conventional HDD! Never heard of this option before. 

Question is, is it doable and easy to setup? How do you get Ubuntu to boot off this SD card? There is no option for this in the bios.

---

### Post by oldfred on 2012-06-23
Few systems boot a SD card, but you can install to a USB flash drive. USB is not as fast as a hard drive and flash is not fast particularly on writes. I have a full install of Ubuntu 12.04 on a 16GB flash with 8GB for / (root) and 8GB for data. It is more for testing on my laptop as I did not have room for a second install which I do on my desktop. It is functional, but not speedy especially loading larger apps like Firefox or Libreoffice. But once in memory, I do not notice much difference. Since install is mostly writes that was a lot slower.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

Installs to 4GB flash, newer of Ubuntu versions require 4.4GB as minimum
HOW TO Avoid Wubi & Install Ubuntu 10.04 on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)
HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

---

### Post by cybrsaylr on 2012-06-23
oldfred, thanks for the info.

I've also put versions of Ubuntu on thumb drives with 'Startup Disk Creator' but never did a full install. What that techie at Office Depot told me sounded pretty interesting and just wondered if it was practical to do.

---

### Post by oldfred on 2012-06-23
Some have used this to boot flash when BIOS does not support it. They said they were adding flash drives also. I have not used it.

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

If your computer boots from the PC card then it should be just like any install.

---

### Post by cybrsaylr on 2012-06-24
Thanks for the link.

It's amazing what you can do with Linux.

---

### Post by cybrsaylr on 2012-06-30
Got a 250GB Seagate HDD. Took about 5 minutes to install. Booted it up with a Live CD of 64 bit 12.04. It ran well. 

Then did an install that ran fairly smooth till the end where it just hung up and seemed to stall and never told me to restart the laptop. Decided to do a 'force quit'. Then did a restart and 12.04 booted up fine. At the start of the install I checked off the two boxes for 12.04 to install all updates and mp3 plugins etc. The mp3s installed but not the 269 updates. Had to do them after the restart. Recall the same thing happened with 11.04 and 11.10 in the past....had to do all the updates after the restart. That said 12.04 seems to be running nice. Just have to get used to it since it's a bit different from 11.04.

The new Seagate drive seems to be running OK but will have to keep an eye on it. Got it at Best Buy where they said it had a 5 year warranty on their website. This was one of the reasons I selected Seagate! However when I opened up the box the hard drive manual said it only has a 1 yr warranty! Took it right back for a refund. Then wanted to get another Seagate with a longer warranty but they ALL  have only a 1 yr warr on laptop drives! Looked at WD drives and they are only giving a 2 yr warr on laptop drives not 3 years! Salesmen blame it on 'floods in Thailand' where they claim all drives are made now!!! Sounds a bit fishy to me but who knows. Anyway I paid $50 for that 250GB Seagate drive and after I got my refund I see them marking down that same 250GB Seagate I just returned to $35! So I decided to get it after all and save a few bucks. Will keep my fingers crossed and hope if it fails in fails in the first year....lol.

Anyway 12.04 seems to be running very well in that Dell laptop and boots up in 32 seconds!

---

