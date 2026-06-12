---
title: "Every install attempt results in restart"
date: 2012-06-05
forum: Installation &amp; Upgrades
---

### Post by Applejackson on 2012-06-05
I am COMPLETELY new to Ubuntu and linux (except for tiny bits with an android phone).  I have a fresh machine with completely clean hard drives both Seagate, both detected by bios, one 1TB, the other 750GB.  I want to switch or at least be able to dual boot from Windows 7 Ultimate.  I first attempted the install after installing Windows several times, with several discs (both dvd and cd, 64 and 32 bit versions).  I tried making a usb install stick but apparently my bios does not allow usb as a boot option.  I have now decided to go with a clean install of Ubuntu and using a Virtual Machine for any Windows needs I still might have.  I have formatted both drives so there is no operating system left on them.  I have now just tried the "alternative" 32 bit installer disk but get the same loop every time.  Every time I hit enter on Install Ubuntu or even Try Ubuntu without installing (on the regular, non-alternative discs), the computer just reboots and I end up in an endless loop with seemingly no way to install Ubuntu.  I'm almost to the point of giving up and just going back to Windows, but I'd really like to make the switch so I would be extremely grateful if anyone can help.  Here is a photobucket album showing the loop in order.  MOST of it is legible.  I hope they can help someone who knows a thing or two to tell me what's going wrong.

[http://photobucket.com/ubuntuproblems](http://photobucket.com/ubuntuproblems)


Thank you in advance

---

### Post by spcwingo on 2012-06-05
Have you tried the option labeled "Check disk for defects"?  This will ensure that there is nothing wrong with the install medium.  IE: bad download, bad burn, etc.

---

### Post by Applejackson on 2012-06-05
I remember trying that on one of the many discs I burned, and if I remember correctly it brought up a bunch of gibberish (to me) then froze, or it restarted.  I can't remember exactly since I've been through this so many times.  I will try that again and report back.  [COLOR=Blue]EDIT: Yeah just tried the check disc for defects and got a reboot same as in the pictures above.[/COLOR]

As an aside, while burning image (I'm using Nero 7), should I burn at the lowest speed, or let it burn at it's own rate?

---

### Post by spcwingo on 2012-06-05
> **Applejackson said:**
> I remember trying that on one of the many discs I burned, and if I remember correctly it brought up a bunch of gibberish (to me) then froze, or it restarted.  I can't remember exactly since I've been through this so many times.  I will try that again and report back.  [COLOR=Blue]EDIT: Yeah just tried the check disc for defects and got a reboot same as in the pictures above.[/COLOR]

As an aside, while burning image (I'm using Nero 7), should I burn at the lowest speed, or let it burn at it's own rate?

When burning images it's always best to burn at the slowest possible speed but, only after checking the hash of the downloaded image.  If you're using Win you can use this utility to do so:

[http://www.winmd5.com/]("http://www.winmd5.com/")

By the way, what release are you trying to install?

---

### Post by Applejackson on 2012-06-05
Trying to install 12.04.  I have a 64 bit system but wasn't sure which to go with since it says 32 bit is recommended.  I tried both with the same results.  On DVDs and CDs.   I will try checking the hash with the link you provided and get back to you on that.  [COLOR=Blue]EDIT: just to be sure, where do I find the CORRECT hash for either of these install images?[/COLOR]

---

### Post by Applejackson on 2012-06-05
I can't seem to bring up the Ubuntu home site now.  Regardless, when I tried to install AFTER windows 7, it said it could not open/extract wubi every time.  Not sure if that helps.  [COLOR=Blue]EDIT: Doesn't matter.  Found the ubuntu hash page here [/COLOR]https://help.ubuntu.com/community/UbuntuHashes [COLOR=Blue]and used the corresponding hashes in the software you recommended.  NONE of them are matching.  How does this happen?[/COLOR]

---

### Post by Applejackson on 2012-06-05
So how does one go about getting the correct MD5 in order to install correctly?  I can't seem to do it judging by my files all being unmatched.

---

### Post by oldfred on 2012-06-05
They only recommend 32bit as about 25% of users have old systems. They assume those with newer systems that have 64bit hardware will know to download 64bit version.

Your system should boot from USB, but you have nVidia. I have nVidia 9600GT and have to use the nomodeset on CD, USB and first boot. Each has slightly different ways to get nomodeset parameter added to boot.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Applejackson on 2012-06-06
I do understand the difference between the copy and burn image so there's no problem there.  Will try the nomodset option when I have a change a bit later with the discs I have. Unfortunately, as started the MD5s for the files I've downloaded match the ones on Ubuntu hash page, so I'm not very confident...

Thank you for the alternative possible solution though.

---

### Post by Applejackson on 2012-06-06
Ok, I tried installing with the nomodeset option ticked and ended up with this freeze screen:  [http://i1067.photobucket.com/albums/u438/applejackson75/Ubuntu%20installation%20loop/ubnomode.jpg](http://i1067.photobucket.com/albums/u438/applejackson75/Ubuntu%20installation%20loop/ubnomode.jpg)

I still don't seem to be able to get matching MD5 checks  though and I even redownloaded the 64bit iso and burned a new cd at the slowest speed (10x) on nero 7, with data verification.

---

### Post by oldfred on 2012-06-06
If md5sums do not match thing it may not be a good ISO. 

Are you downloading directly from Ubuntu or one of the official mirrors?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
hashes are here also
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by Applejackson on 2012-06-06
Is there a hardware component I could possibly remove in order to install, then add that hardware back later?  

I really don't want to go back to windows as my main OS.

---

### Post by Applejackson on 2012-06-06
> **oldfred said:**
> If md5sums do not match thing it may not be a good ISO. 

Are you downloading directly from Ubuntu or one of the official mirrors?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
hashes are here also
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

I downloaded all of my isos directly from the ubuntu site, checked the hashes on the ubuntu hash page and none of them are ever even close.  Once the MD5sum determines the hash on  the isos I've downloaded, I can plainly see they don't match, but try verifying anyway, just in case.  Always says UNMATCHED!

---

### Post by ajgreeny on 2012-06-08
Try downloading with a torrent client; no idea what is used by windows for this, nor what is available, but there are many.  Torrent downloads check as the separate packets of the whole file are downloaded, and if any are not correct, the client tries again.  Torrent downloads will therefore always be good, in my experience.
[http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)
Scroll down a little for the torrent files.

You still need to burn the image at as slow a speed as possible to ensure a good CD.

---

### Post by Applejackson on 2012-07-04
> **ajgreeny said:**
> Try downloading with a torrent client; no idea what is used by windows for this, nor what is available, but there are many.  Torrent downloads check as the separate packets of the whole file are downloaded, and if any are not correct, the client tries again.  Torrent downloads will therefore always be good, in my experience.
[http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)
Scroll down a little for the torrent files.

You still need to burn the image at as slow a speed as possible to ensure a good CD.


Been a while since I'd been able to get back to messing with all this.  Almost gave up and just installed Windows again, but this advice of using the torrent download worked a charm to get the hash to match.  Thanks a ton for the advice all around, as I'm now able to install without a problem (so far, it's installing now).

---

