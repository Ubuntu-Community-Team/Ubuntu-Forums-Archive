---
title: "toshiba laptop Can not install"
date: 2006-08-04
forum: Installation &amp; Upgrades
---

### Post by Lrusso on 2006-08-04
I am trying to install ubuntu on my toshiba laptop, I have the alternative disk in the cd-rom drive (COMPUTER HAS 120 MB of RAM), when I turn the computer on it just boots into Windows. Toshiba's boot menu is F2 and I get CD-Rom Drive and some other choices, but below you already have that blinking line and the computer is booting into windows.

---

### Post by mdmarmer on 2006-08-04
This may not be enough RAM -- you may need to run a lighter Linux

Look here [https://wiki.ubuntu.com/HardwareSupportMachinesLaptops](https://wiki.ubuntu.com/HardwareSupportMachinesLaptops)

and here [http://www.linux-laptop.net/](http://www.linux-laptop.net/)

Toshibas have special problems because of their unique architecture

Post back with model of laptop -- if you can add RAM it will help -- this stuff is cheep if you can find it. ;-)

Mike

---

### Post by Lrusso on 2006-08-04
Toshiba Satellite 1805-S253

---

### Post by Lrusso on 2006-08-04
shouldn't i still be able to get the install window, with that amount of ram?

I don't wanna waste the money on the ram enough though its not that much, money.

Its just whats the point if i cant even boot into the installed ;)

---

### Post by RedBoot on 2006-08-04
I would guess your problem is the CD is not bootable. I'd try basic tests:
[LIST]
[*]Can you boot another computer from this CD? If not, the CD did not get burned from the ISO properly. Re-burn.
[*]Can you boot this laptop using a different bootable CD? If not, the laptop BIOS is not set properly.
[/LIST]

If your computer has too little RAM, the Ubuntu install program will tell you so and permit a non-GUI, server install.

---

### Post by Lrusso on 2006-08-05
> **RedBoot said:**
> I would guess your problem is the CD is not bootable. I'd try basic tests:
[LIST]
[*]Can you boot another computer from this CD? If not, the CD did not get burned from the ISO properly. Re-burn.
[*]Can you boot this laptop using a different bootable CD? If not, the laptop BIOS is not set properly.
[/LIST]

If your computer has too little RAM, the Ubuntu install program will tell you so and permit a non-GUI, server install.

ok, it boot in a different computer, so its the laptop bios, I know I have to set it to boot from the CD-ROM drive, but I'm not sure how to open the BIOS on this particular computer, so I guess thats what i need help with.

---

### Post by RedBoot on 2006-08-05
I'm no expert with regards to Toshiba's BIOS. 

Its often the Del, F1, Esc or some such key. May need to check the Toshiba web site.

Anyone else know the magic key???

---

### Post by Lrusso on 2006-08-05
I just did it its the ESC key, I set it to book from the CD-ROOM drive 

Save and restart still no luck, the CD-ROM drive appears to be working properly from what I can see, the lites flash, I can here the CD spinning?

any ideas?

---

### Post by Metacarpal on 2006-08-05
When you first turn the power on, keep tapping Esc until it says to check the system setup (press F1)

At least, that's how it works on my Tecra.

---

### Post by Lrusso on 2006-08-05
excatly, but now what  ;)

---

### Post by Metacarpal on 2006-08-05
**Edit:** Wow, I'm really tired.  Sorry, didn't see your post at the same time as mine earlier.  You did change the boot sequence.

Um, sounds like a bad disc.  Do you know how to check the MD5 hash for your downloaded ISO?   Also, did you tell your burner [to burn the ISO as a disc image]("http://www.psychocats.net/ubuntu/iso.html"), or did you just burn the ISO onto the disc?

---

### Post by Lrusso on 2006-08-05
> **Metacarpal said:**
> One of your BIOS options is the boot order.  On my BIOS (Phoenix 1.6) it's near the bottom-left of the screen.  Get to that selection using arrow keys or whathaveyou, then change the order (on mine it's using the space bar - on yours, it might be different.  See the guide at the bottom of your BIOS screen).  You want CD-ROM to be the first entry.

Then save (End on mine) and it will reboot using the CD-ROM

Tip: Once you finish the install, change the boot order so your HDD is first.  Saves about 10 seconds every time you turn it on.

no i did that

"I just did it its the ESC key, I set it to book from the CD-ROOM drive

Save and restart still no luck, the CD-ROM drive appears to be working properly from what I can see, the lites flash, I can here the CD spinning?

any ideas?
Edit/Delete Message"

---

### Post by Metacarpal on 2006-08-05
Sorry 'bout that.  See my edited post above.

---

### Post by Lrusso on 2006-08-05
> **Metacarpal said:**
> Sorry 'bout that.  See my edited post above.

It booted from the CD on this Windows PC though so I don't think thats a problem, could it still be?

---

### Post by Metacarpal on 2006-08-05
Pardon if this is a silly question, but I just want to be sure.
When you look at the CD in Windows, is it one large file or lots of files on the CD?

It's also entirely possible that the download itself was corrupted, so that while the disc appears by and large fine, the bootable files may be fragged.  Do you still have the ISO you downloaded?  If so, can you check the MD5?

---

### Post by Lrusso on 2006-08-05
> **Metacarpal said:**
> Pardon if this is a silly question, but I just want to be sure.
When you look at the CD in Windows, is it one large file or lots of files on the CD?

It's also entirely possible that the download itself was corrupted, so that while the disc appears by and large fine, the bootable files may be fragged.  Do you still have the ISO you downloaded?  If so, can you check the MD5?

ill look but it booted on this computer, ill look after i try burning another 1 on a slower burn speed

---

### Post by RedBoot on 2006-08-05
I've had that problem before where you just can't seem to make it boot for a CD. It's a pain. 

Can it boot from another bootable CD? WinXP setup disk?

Here are some links for dealing with systems that can't boot from CD. Wish they were more straight forward.
[https://help.ubuntu.com/community/Installation/FromWindows]("https://help.ubuntu.com/community/Installation/FromWindows")

[https://wiki.ubuntu.com/InstallingOrBootingUsingIsoFile?highlight=%28boot%29%7C%28install%29]("https://wiki.ubuntu.com/InstallingOrBootingUsingIsoFile?highlight=%28boot%29%7C%28install%29")

---

### Post by Lrusso on 2006-08-05
Not sure, ill try some more things in the morning

---

### Post by Lrusso on 2006-08-05
changed my mind, I did not boot from a Windows 98 Disk, do you think the drive is bad?

---

### Post by Lrusso on 2006-08-05
You guys are gonna think this is wild, I decided I might as well try my look with some tricks LOL, I powered on the computer and pop the tray out, then turned it off, i started the computer witht he tray open and when it POSTed, I poped the tray in and it booted from the CD, installing now, thanks for the attempted help though

---

### Post by A2A on 2006-08-05
For my Toshiba 1800 Satellite, I have to hit F12, then hit "C" which corresponds to CD-ROM.  And the xubuntu CD started booting.  The change in Boot Sequence is temporary, it's set to boot from the Primary HDD everytime, and if you need to change that, then you will have to hit F12, everytime and tell it where to boot from.

Hope this helps,

A2A

---

### Post by Metacarpal on 2006-08-05
> **Lrusso said:**
> You guys are gonna think this is wild, I decided I might as well try my look with some tricks LOL, I powered on the computer and pop the tray out, then turned it off, i started the computer witht he tray open and when it POSTed, I poped the tray in and it booted from the CD, installing now, thanks for the attempted help though

That's some mad ingenuity you've got going there! :D  Great thinking - glad you were able to get the install going.

---

### Post by RedBoot on 2006-08-05
Reminds me of Humphrey Bogart smacking the African Queen (that's a boat, not a lady!) with a wrench to get it to work.

:grin:

Hope it goes well for you now.

---

### Post by mulder_edu on 2006-08-07
I've worked with alot of Toshiba's, I'm using a Satellite right now.  They can be a real pain about trying to boot to a cd-rom.  You can try it a hundred times and get nothing and then it will just start working out of the blue.  I had the same problem for awhile.
My problems had alot to do with the BIOS menu.  I think my problem was it wanted me to hit END to save and exit, and I kept hitting ESC.  The system is sort of stupid.](*,) 

David.

---

