---
title: "My first installation of ubuntu, of course there's a problem. Hello World!"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by Starblaster1234 on 2010-01-21
Hey everyone,

Just joined the forums as I was downloading Ubuntu Desktop 9.10 (32-bit) from [COLOR=Blue][http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)[/COLOR]

Upon burning the .iso to the CD using [COLOR=Blue][ImgBurn]("http://www.imgburn.com/")[/COLOR], the verification of the CD (after burning) could not verify "initrd.lz". I checked that the file was there (it was about 5KB) and continued anyway (probably not a good idea but I figured I could always "Check disk for defects")

After putting the disk in, everything started up great, I selected English and when I clicked on "Check disk for defects" the entire process froze and a multicolored bar of random pixels showed up. I rebooted and tried the "Install Ubuntu" and even the F6 Other Options (checking all the options, then clicking "Install Ubuntu"). I even tried "Test Memory".

Otherwise the menu screen works fine. All F1 through F6 work, the entire help documentation works, but no installer.

I'm sort of stuck now and could use some input since this is uncharted territory for me. The computer does have a version of Windows XP in who-knows-what condition (it won't start up). I don't care about any of the information on the drive and would be fine with wiping it out because that's what I originally planned to do.

Thank you for your help! If you would like screen shots (taken as pictures on my phone since I have no way to get on the internet from the local computer).

---

### Post by rogue_0111 on 2010-01-21
Sounds like you need to burn another CD or copy ISO to a flash drive (my preferred way). Nothing you can do with a corrupt CD.

good luck,

may the source be with u.

---

### Post by Starblaster1234 on 2010-01-21
Unfortunately the option of booting from a USB drive is not available to me in the boot menu. After trying to burn the image to a CD again, it failed on another file.

Does anyone have any suggestions?

---

### Post by loell on 2010-01-21
verify the ISO's  md5sum,  and probably lower your CD writing speed.

---

### Post by Linuxforall on 2010-01-21
Use different media, check for firmware updates for your burner and burn at slowest speed possible.

---

### Post by Starblaster1234 on 2010-01-21
I found a neat little tool called unetbootin that decompressed all the files in the .iso and, after a few prompts, it's 98% done installing on my computer. I'm very surprised I could do this on my own (for the most part :P).

Thanks to everyone that responded. I really appreciate your time and effort!

His new name is Zombie because he was once a dead hard drive, brought back to life by Ubuntu. I look forward to playing around with my Zombie :P

---

### Post by rogue_0111 on 2010-01-23
Good luck. Enjoy.

---

### Post by k64 on 2010-01-23
I would say use [ISORecorder]('http://isorecorder.alexfeinman.com/') if you currently have Windows. That's because most other recorders extract the file rather than burn it as a filesystem.

---

