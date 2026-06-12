---
title: "Help me noob!"
date: 2011-07-01
forum: Installation &amp; Upgrades
---

### Post by ChanGQ on 2011-07-01
Hi all,

I new to Ubuntu, my school require me to use Ubuntu but i do not want to install it in my lappy therefore decide to try installing it into a USB.

I follow [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) but it does not seem to work btw i use their Universal-USB-Installer-1.8.5.6

Error is no default or UI configuration directive found

---

### Post by pawhtiobo on 2011-07-01
What kind of USB Stick are trying to use (size, filesystem, etc...)?

You can also search the forum....there are some threads about this kind of issue:

[http://ubuntuforums.org/showthread.php?t=1487937&highlight=default+ui+configuration](http://ubuntuforums.org/showthread.php?t=1487937&highlight=default+ui+configuration)

[http://ubuntuforums.org/showthread.php?t=1583344](http://ubuntuforums.org/showthread.php?t=1583344)

You can also use a LiveCD.......

See ya...

---

### Post by ChanGQ on 2011-07-01
Hi pawhtiobo,

Thank for replying me, actually i did research on all the forum before posting this issues. My USB is Kingston 2GB i use both unetbootin-win-549 and Universal-USB-Installer-1.8.5.6 to try and both fail. Further more i try on both my lappy Asus U36J and Desktop Dell Inspireon 545S. The lappy give me just boot error while the desktop give me the error i posted.

I dont knw where to start trouble shooting and what to check on, i saw alot of post some say find the file syslinux.cfg but i cannot even find it that e strange part. Further more i saw some that say check e md5sum but i cannot find the software that does it.

Thank in advance

---

### Post by ChanGQ on 2011-07-01
Hi,

I reformatted the disk and attempt again FINALLY I saw the file but it seem to be in e wrong place (not very sure) did a print screen hope u can help me have a look.

Btw what a live CD?? your mean i boot up from CD??

Thank in advance

---

### Post by varunendra on 2011-07-01
> **ChanGQ said:**
> Btw what a live CD?? your mean i boot up from CD??
Yes, a Live CD is the 'desktop' version cd of ubuntu from which you can directly boot into desktop environment to try and experience it.

[Note that not every cd that is 'bootable' is a 'Live CD'. It must be able to boot into desktop environment!]

And by the way, did you try the method suggested in the first link pawhtiobo gave you? (this particular post: [http://ubuntuforums.org/showpost.php?p=10738426&postcount=33](http://ubuntuforums.org/showpost.php?p=10738426&postcount=33))

Another method with a very good success rate may be to download the latest LTS version (Ubuntu 10.04.2 LTS, preferably via torrent from [here]("http://www.ubuntu.com/download/ubuntu/alternative-download") or this [direct link]("http://releases.ubuntu.com/lucid/ubuntu-10.04.2-desktop-i386.iso.torrent")), burn it onto a CD ([see how]("https://help.ubuntu.com/community/BurningIsoHowto")), boot from that CD, and use its inbuilt 'Startup disk creator' to create a Live USB setup on your pendrive.
Since you must have already downloaded the latest version 11.04 (which is not yet as stable as 10.04.2), you can also try the same method with it first (although the success rate is higher with 10.04.2 LTS).

Apart from all this, if your laptop's CD/DVD drive is working, then you can always boot directly from the 'Live CD'. However, being able to boot from USB drive is a better option as it is faster and can also save changes you make during using it in live mode.

Last, converting your USB drive's partition type to FAT16 (or FAT in XP) may be an important change that is required.

---

### Post by ChanGQ on 2011-07-01
Hi,

icic i get wat live CD is le, but still i really want it to be in USB as my lappy assus U36J do not have a in build CD reader!! I saw the link u given me and i realized that i use FAT32 so is it wrong??? Must be FAT16 to make it work??

---

### Post by varunendra on 2011-07-02
> **ChanGQ said:**
> Hi,

icic i get wat live CD is le, but still i really want it to be in USB as my lappy assus U36J do not have a in build CD reader!! I saw the link u given me and i realized that i use FAT32 so is it wrong??? Must be FAT16 to make it work??
No, it 'should not be' wrong. But I've seen 'sometimes' computers boot from a USB stick only when it is formatted as FAT(16). I don't know the precise reason.

It may be related with 'how the BIOS handles a USB stick' or maybe related with the kind of 'emulation used in the USB stick'. For example if a USB stick emulates a 'floppy drive' for being able to be detected by the BIOS as a bootable drive, then obviously the BIOS would expect a FAT16 file system on that drive (generic floppies can't have FAT32 on them), which, if not found - would render the drive as 'unreadable' to the BIOS. Actually I've no clue why this happens, it's just a possible theory of my own to explain such behaviour to myself.

Most often, FAT32 works, but sometimes, I did need to change it to FAT16 - on a pendrive.

As for your problem, you may also wish to try unetbootin. It also has a good success rate. But try the FAT16 thing first as it won't need you to download anything else.

---

### Post by ChanGQ on 2011-07-02
Hi,

Yup i did try with unetbootin before same problem, i just try with Ubuntu 10.04.2 LTS using FAT 16 pendrive no luck also. I think i go get a dise and try out with e live dice, REALLY thank for your help hope this time confirm can work.

---

### Post by ChanGQ on 2011-07-03
Hi 

I follow what you teach me "Another method with a very good success rate may be to download the latest LTS version (Ubuntu 10.04.2 LTS, preferably via torrent from here or this direct link), burn it onto a CD (see how), boot from that CD, and use its inbuilt 'Startup disk creator' to create a Live USB setup on your pendrive."
I created it successfully but then the bio dont boot it up it just by pass it and go to my window 7! Y??

Thank in advance for any reply

---

### Post by pjd99 on 2011-07-03
Try a different brand usb stick. Other posts on the forums speak of problems with Kingston drives. 

My 1 GB Kingston stick has never worked as a USB boot device, but my 2GB LG drive and 8GB Lexar have worked (the LG one has had the most success)...

---

### Post by varunendra on 2011-07-03
> **ChanGQ said:**
> Hi 

I follow what you teach me "Another method with a very good success rate may be to download the latest LTS version (Ubuntu 10.04.2 LTS, preferably via torrent from here or this direct link), burn it onto a CD (see how), boot from that CD, and use its inbuilt 'Startup disk creator' to create a Live USB setup on your pendrive."
I created it successfully but then the bio dont boot it up it just by pass it and go to my window 7! Y??
Have you checked it on your desktop? If either of your desktop or laptop can boot from it, then the pen-drive is created correctly. No need to further fiddle with it.

If you know the Hot-Key to bring up boot menu of BIOS while the laptop is booting (most often it is on F9, F10, F12 or Esc key, but may be a different one too depending upon laptop model), see if your pendrive is listed in boot devices. Sometimes it may be listed under sub-list of hard disks or usb floppy drive. If you don't find it there, reboot while leaving the pendrive plugged in. If you find it listed, select it to boot from it. If still the boot process skips it to boot from hard disk (Win7), then it may be one of 3 reasons:

[LIST=1]
[*]It might not have been created correctly (confirm by trying with your desktop). Retry with default settings.
[*]Your laptop is unable to boot from that particular pendrive. Try a different brand as pjd99 suggested.
[*]Your laptop may simply not have the capability to boot from a USB key! Although it is highly unlikely given how modern its model is and it does not have a DVD drive by default.
[/LIST]
Anyway, if you have a USB hard drive, it can make things much easier (and certain) for you.



**_EDIT_:**
Also try enabling 'Legacy USB' support in your BIOS, or switching between different modes, if there are any, provided for USB in the BIOS.

---

### Post by Rasa1111 on 2011-07-04
> **ChanGQ said:**
> Hi 

I follow what you teach me "Another method with a very good success rate may be to download the latest LTS version (Ubuntu 10.04.2 LTS, preferably via torrent from here or this direct link), burn it onto a CD (see how), boot from that CD, and use its inbuilt 'Startup disk creator' to create a Live USB setup on your pendrive."
I created it successfully but then the bio dont boot it up it just by pass it and go to my window 7! Y??

Thank in advance for any reply

 When you boot your computer, 
You usually see something near the bottom of the screen that says "Press F12" to enter BIOS menu" (some use different F keys), So just look what yours is, and press it before the computer boots to the windows 7. 

When you're into the BIOS menu, Look for something like "Startup Devices"..
Then move "USB" to the first position, Save, and reboot. 
and it should boot into the USB drive. 

Or, on some laptops (like my thinkpad)
I can just choose "Choose temporary startup device" 
and I pick USB and it boots right into the USB drive.

 Hope this can help.
 Good luck! :KS

---

### Post by ChanGQ on 2011-07-04
OK DONE SOLVE E PROBLEM LE THANK ALL!!! i use a no brand USB (free gift) it work LOL

---

### Post by Rasa1111 on 2011-07-04
Niiice! Congrats!! :D

---

