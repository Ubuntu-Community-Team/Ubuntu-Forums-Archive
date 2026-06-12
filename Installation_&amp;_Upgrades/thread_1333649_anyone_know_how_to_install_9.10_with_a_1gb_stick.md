---
title: "anyone know how to install 9.10 with a 1gb stick?"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by JungleBeast on 2009-11-21
My pc has no cd drive.
I'm running 32 bit 9.04 on one hdd and would like to install 64 bit on the other hdd. 

I tried using 'USB startup disk creator' to create a startup usb disk from the ubuntu-9.10-desktop-amd64.iso file  - but when i tried to boot from this it failed.   I'm thinking that was a bit school boy and I should have used a .img .   Any ideas where I could find (or convert my .iso) to a ubuntu-9.10-desktop-amd64.img ?

I also tried this method, 
[https://help.ubuntu.com/community/Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux")
which worked as far as changing my grub, but just gave me a prompt asking for a kernel name (i think..)

Finally I tried this method, 
[https://help.ubuntu.com/9.10/installation-guide/amd64/ch05s01.html#boot-initrd]("https://help.ubuntu.com/9.10/installation-guide/amd64/ch05s01.html#boot-initrd")
which also failed, leaving me with a blinking cursor once i have run the grub option on boot. A possible weak point of my method here was that I could only find a initrd.lz file in the .iso and not a initrd.gz as specified.   I wasn't sure if this was just a new thing for karmic koala or not.

Any help/pointers/opinions will be greatly appreciated.

Chris

---

### Post by Digikid on 2009-11-21
The BEST way would be to use Unetbootin.  Simply reformat your stick and plug it in.  Start up Unetbootin and click on ISO and then direct it to your ISO.

a few minutes later you will have a bootable LiveUSB of Ubuntu.

---

### Post by darkod on 2009-11-21
In fact unetbootin is best if working on windows to create your startup stick, because out of whatever reason the usb creator doesn't work on windows.
On ubuntu I have always found the method you used best. USB startup disc creator and using ISO file, you made no mistakes. Have no clue why it didn't work though.
I have done it few times, with the stick formatted as FAT32, if that helps. You can give it another go.
I don't like unetbootin because it "skips" the ubuntu main menu and it goes straight either to Try Ubuntu or Install Ubuntu (don't remember exactly). While with the ubuntu menu you could use either option. There are ways to modify this in unetbootin but that is additional procedure.

---

### Post by JungleBeast on 2009-11-21
Thank you both !! 

That's brilliant - i formatted the stick as fat32 , then usb creator prompted me to reformat later. 
Takes me straight to the install screen absolutely no problem!


One more question, I tried check files and it said I have 15 failed files. 
I ran md5sum on the original .iso and it's fine. So reburnt the usb  image, and tried again and found 15 failed files again. Is this an issue?

Also when just trying 'install' i got the white little ubuntu symbol in the middle of a black screen, i left it for 20 minutes and nothing had happened. Is this normal? Or is it broken? 

Thanks again for solving problem 1 !! :p

---

### Post by Digikid on 2009-11-21
> **darkod said:**
> In fact unetbootin is best if working on windows to create your startup stick, because out of whatever reason the usb creator doesn't work on windows.
On ubuntu I have always found the method you used best. USB startup disc creator and using ISO file, you made no mistakes. Have no clue why it didn't work though.
I have done it few times, with the stick formatted as FAT32, if that helps. You can give it another go.
I don't like unetbootin because it "skips" the ubuntu main menu and it goes straight either to Try Ubuntu or Install Ubuntu (don't remember exactly). While with the ubuntu menu you could use either option. There are ways to modify this in unetbootin but that is additional procedure.


Strange...it NEVER does that to me.  It installed a simple bootloader and gave me 8 seconds to make a choice.  If you make no choice then it takes you to the default....which in Ubuntus case is the LiveCD portion.  I never had to modify anything.  Were you using an older version perhaps?

Does not matter if you use the Windows Version or the Linux version.  They both work the same and perfectly well in my experience.

---

### Post by llazarte on 2009-11-23
Anybody has a link to an explanation as to why there is no ".img" version for 9.10?

It was so clean to just "dd if=file.img of=/dev/sdx"  :confused:

I tried to "dd" the ".iso" file with no luck. Tried "usb-creator-gtk" (have no plain usb-creator), no luck.

After fiddling a while with "unetbootin", I got a bootable UNR 9.10 stick, but, as pointed above, I lost the original UNR initial screen.

So, anybody knows why there is no longer an ".img" file available?

---

### Post by earthpigg on 2009-11-23
> anybody has a link to an explanation as to why there is no ".img" version for 9.10?

It was so clean to just "dd if=file.img of=/dev/sdx" 

+5,000,000

also, it would be nice if a graphical front-end existed to do that for those that don't like the command line.

give it a file, point it to a USB device, done.

---

