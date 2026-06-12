---
title: "need help switching completely to Linux"
date: 2011-11-21
forum: Installation &amp; Upgrades
---

### Post by justtoplay on 2011-11-21
Right now i have both operating systems (windows xp and lunix) as a option right now when i boot up. But i have decided to switch fully to lunix and have made a bootable flash drive following these instructions [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download).
Will this work if i reformat my hard drive and boot from the flash drive. If it will how would i go about reformatting my hard drive, because  when i boot form my flash drive now i still get the option to either boot into xp or lunix instead of being able to reformat and do a fresh install. I want lunix as my main and only os.

---

### Post by hhh on 2011-11-21
It's Linux, not lunix. If your USB drive has the ISO installed on it properly, then you will be able to boot into a working desktop session (called a LIVE session) to test things out, and then can start the installer from there which will walk you through the hard drive format and the installation. Usually a computer doesn't automatically boot from USB though, you have to tell it to do so at boot via a menu. At boot, try hitting F1 or Esc. Other possible key triggers are F8, F11, etc... (maybe there is a quick message displayed like "Press F10 to enter Setup).

Personally, unless hard drive space is a serious issue for you, I would not delete the Windows partition. I keep mine even though I rarely use it, because once in a while I need to do something that Linux won't do. It has also come in handy to recover my Linux setup when I have made an error.

---

### Post by justtoplay on 2011-11-21
Yes yes i am well aware of how to get o the boot menu and i do boot form the usb but like i said it still just go to giving me the options to boot into my current os(s) xp and the linux i have now.

---

### Post by hhh on 2011-11-21
Then the ISO didn't properly transfer to the USB as it's sending you back to Grub.

BTW, if you have Linux already installed as dual boot and you insist on removing Windows, you can use gParted to delete the Windows partition and then expand the Linux partition into the free space (back up important files first though).

---

### Post by justtoplay on 2011-11-22
ty ill check it out

---

### Post by justtoplay on 2011-11-22
I would really like a fresh install. >.<
Its on my flash drive right i know that for sure. I followed this [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

So i don't know why it wont work.

---

### Post by satanselbow on 2011-11-22
> **justtoplay said:**
> I would really like a fresh install. >.<
Its on my flash drive right i know that for sure. I followed this [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

So i don't know why it wont work.

Unfortunately following the instructions does not guarantee that it will work first time - you never built an IKEA wardrobe? :D

Did you create the stick in Windows or your existing Lunix? ;)

For whatever reason it looks like your USB stick is not being booted at startup.

There are a few possibilities:

1) USB not in bios device startup list - enter you bios (F1/F2/F9/F10 keys are regular access keys though there are others and it is very system dependent) Add "USB Device" at the top of the boot order list of move it to the top if it is already there.

2) Transfering the ISO to your stick failed for whatever reason - try the procedure again being mega careful that you are using the correct device. 

3) The ISO you are creating your USB from may be corrupt - if you grabbed it from a torrent this is unlikely (as there is built in error checking) but any file download can get corrupted in transit. Try downloading the ISO again - bittorrent is best ;)

Good Luck!

---

### Post by mastablasta on 2011-11-22
have a look here: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
 
you need to boot form USB and then select install in the menu. During install you will be asked if you wish to use the whole disk and when you say yes it will be reformated.
 
if you are having issues with booting from USB or if it is giving out a strange menu, then you can try again by putting the image on iso using unetbootin: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) or linuxliveUSB: [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)  programme (both are free and work well in windows).
 
if you still can't figure out what is wrong then boot the liveUSB and select try it then go to this site:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
 
download the script and follow the instructions found on the site. Then post the results.txt here. That way we can see what is going wrong with your boot sequence.

---

### Post by darkod on 2011-11-22
It sounds like you are not booting from the USB. Don't forget, it's not enough to just plug it in. You need to "tell" your computer to boot from it before booting from your HDD. I guess that's why you receive the "normal" grub menu, you are booting from the HDD.

You can either use a key like F10 or F12 to enter a Boot Menu if that's supported, or you need to enter BIOS and set USB before HDD in boot devices.

Once you boot from the USB, yes, you can delete all of the HDD and install just ubuntu there. I think I don't need to mention that this will DESTROY all your windows and ubuntu data that you currently have!!! Some people somehow have the idea that it will move the data into the new install when it clearly says it will be erased.
If you want only ubuntu on the hdd the best beginner option would be "erase and use whole disk" or similar...

---

### Post by hhh on 2011-11-22
I love people who repeat the same thing I just said.

For what it's worth, with recent versions of Ubuntu I have been unable to create a Live USB from another Linux partition. As a matter of fact, the latest Canonical instructions for creating a Live USB are for either Windows or Ubuntu only. Try booting into your Windows partition and create the Live USB from there using these instructions (Step 2, check the buttons for USB and Windows)...
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by justtoplay on 2011-11-22
No i can guarantee you i going to the boot menu on start up and going  too removable devises and picking usb. I will try re downloading the iso  and using the llinuxliveusb again and reformat the usb which i all ready did but it might be possible that the iso was corrupted in the first place.

---

### Post by justtoplay on 2011-11-22
ok i just did a fresh install of xp just so i could have a clean slate to work with and because there is nothing on the hd any way. (Main goal) i want lunix as my pirmary os
and mabye xp as a back up. How should i move on from here should i do a dual boot and mess with the partitions or what, if so can some one explain to me how i would set up the partitions. Im gessing give just give enough space for the xp os and 1 gig for vurtual memery. (most likly wrong)

---

### Post by darkod on 2011-11-22
I hope you didn't let XP use the whole HDD. If you planned to dual boot you should have planned the partitions sizes before installing XP. That way you allocate to XP only what you plan. No need to resize a freshly installed XP because the resize can break it.

As for space, only you know what you use ubuntu and XP for, and how much space you need for each. If XP is a backup do you still install particular programs? How much space do they take? etc

---

### Post by justtoplay on 2011-11-22
well i used all the hd but 10 gig....
Ok say i just wanted ubuntu as a os.I have tried booting from flash drive.I  uploaded a picture of its contents([http://tinypic.com/r/2bck06/5](http://tinypic.com/r/2bck06/5)).I have reformatted the thing 2 times with  fresh .iso(s).I dont know why it wont boot up. On the boot menu it said  removable devises you go into that and it said usb i use that and it just boots  up normally and goes to xp. I need a alternative to install from usb or a way to make it work.[IMG]http://tinypic.com/r/2bck06/5[/IMG]

---

### Post by darkod on 2011-11-22
Do you have another comp to try booting it with the usb to see if it will work?
The picture doesn't say much because you can't see if it's bootable or not, just the files.
Did you create it with universal usb installer?

---

### Post by satanselbow on 2011-11-22
> **justtoplay said:**
> On the boot menu it said  removable devises you go into that and it said usb i use that and it just boots  up normally and goes to xp. I need a alternative to install from usb or a way to make it work.

Some bios have separate entries for USB-HDD, USB-CDROM etc etc - your bios may not be "Bootable USB stick" capable...

The alternative is to burn the ISO onto CD/DVD :(

---

### Post by justtoplay on 2011-11-22
I was afraid of the alternative being a cd or dvd i don't have any. :(

Yes i did use the universal installer but it might be that the bios is not compatible like mentioned above :(.

Is there any other way.

---

### Post by justtoplay on 2011-11-22
never mine i found some blank cds thank god

---

