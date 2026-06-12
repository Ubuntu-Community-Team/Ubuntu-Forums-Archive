---
title: "Boot withtout changes in MBR"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by bjolen on 2007-06-21
Hi
 I installed Ubuntu 7.04 from a CD made from the  Iso-file on my 2:nd HDD. I have already Win XP on my 1:st HDD.
Got very surprised that the installation has changed MBR on 1st  HDD and installed GRUB there.
No warning of this during installation. The GRUB boot window works OK but I would like to either boot  Ubunto from a FD or from the Win boot window(boot.ini). The reason is that I want to fix the MBR(1st HDD) to get a short boot time for Windows  without the long way via GRUB
Found a  descript. on boot FDD. from Ubuntu Community Documentation   called  “GrubHowto/BootFloppy”. I made 2 FDD:s and both booted but after the Grub menu it stopped with error 15 file not found. I traced it to the Stage 2 file but have no clue of what file is missing and how to fix it.

Then I used a recipe in the GNU GRUB manual item 3.1 but the command 1+0 etc was rejected by the command line in my Ubuntu 7.04 so I failed also here.

Finally I tried to boot from Windows (boot.ini)using the description in  Community documentation Ubuntu called  Installation / From Windows.
Result the GRUB boot window (blue) showed up but when I choosed Ubuntu  the error 17 file not found appeared and I could not get further.

Does anyone know how to fix the above or another method to boot Ubuntu  without changing MBR.
Looking forward to any hints
/ Bjolen

---

### Post by Herman on 2007-06-21
You can boot either Windows or Ubuntu just as fast with Grub as any other boot method. Grub has a ten second count-down before it boots Ubuntu to give you a chance to select Windows or some other operating system. You don't have to wait for the times to finish, you can select your operating system and press 'enter', and your operating system will boot.
Windows has a thirty second count-down if I remember correctly, three times as long!
In either case, regardless of whether you use NTLDR or GRUB, you can edit the bootloader's files to set the timer to the number of seconds you require.

The easiest way would be to edit GRUB's /boot/grub/menu.lst file and customize it to suit your  needs. 
You can make Windows the default entry in Grub if you wish and adjust the timer as you like. 
It is possible to hide the GRUB menu too, so GRUB will boot Windows instantlly without you even seeing the GRUB menu. Please click on my third signature link for details.

It is not recommended to use the Windows NTLDR bootloader for dual booting. Even for dual booting more than one Windows installation it is inferior to Grub, read this, [    Understanding MultiBooting and Booting Windows from an Extended Partition]("http://www.goodells.net/multiboot/index.htm") 
GRUB is better for multi booting Windows than Windows own boot loader because it has the 'hide' command so you can 'hide' one Windows install from another. If you learn how to use GRUB, you will be much better off.

Regards, Herman :D

---

### Post by cwgpress on 2007-06-21
I agree with Herman that it's easiest to keep Grub and just tailor it to your needs. One of my reasons for this is that upgrades, re-installs, alternate kernels and other things will also want to put Grub in, and you're going to get tired of taking it back out. It works very well, it's free, and it's easy to customize, so why not just fix it up for your needs!

Aside to Herman: I don't believe that Vista uses ntldr. The Redmond folks have something new this time around I think Vista seems far more like a real operating system than the previous Windows versions. It's obvious they've been playing with Linux distros and adopting several new concepts.

The problems you're going to have with Grub are figuring out how it counts in order to specify the correct default (hint: the 'other operating systems' line counts as an operating system!) and the fact that every time you upgrade you'll have to re-edit Grub to keep Vista your default. It's no big deal, as long as you can boot into something that can edit the start.lst file...

---

### Post by Herman on 2007-06-21
> Aside to Herman: I don't believe that Vista uses ntldr. The Redmond folks have something new this time around I think Vista seems far more like a real operating system than the previous Windows versions. It's obvious they've been playing with Linux distros and adopting several new concepts.Hello cwgpress,
Thanks for your input and support. :)  Yes, I have read only a little bit about it, but no-one around where I live has Vista yet that I know of, (at least not one that I can play with and possibly destroy a few times to learn about its bootloader), can you provide any links where I can read up a little on the new Vista bootloader?  Or explain a bit more about it ?

I do know about Computer Guru's [EasyBCD]("http://neosmart.net/dl.php?id=1") for helping Windows Vists users dual boot with Ubuntu and other Linux. 
Actually, that reminds, me, it's another option bjolen might want to look into, I'm pretty sure EasyBCD works for Windows XP as well as Vista now.

I also have a link here for a Vista-specific dual boot how-to by molly_001,DUAL BOOT VISTA and LINUX (Ubuntu 6.06) [B][http://tinyurl.com/hrbhy](http://tinyurl.com/hrbhy)
[/B]Is this link still up to date?

Regards, Herman :D

---

### Post by Herman on 2007-06-21
> The problems you're going to have with Grub are figuring out how it counts in order to specify the correct default (hint: the 'other operating systems' line counts as an operating system!) and the fact that every time you upgrade you'll have to re-edit Grub to keep Vista your default. It's no big deal, as long as you can boot into something that can edit the start.lst file.....or you could just cut the entire Windows boot entry from the bottom of the menu.lst file and paste it halfway up, just above the line that says '### BEGIN AUTOMAGIC KERNELS LIST'. That's the easiest and the best way. ;)
See this link,  [Changing the default operating system]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc") (booted by the timer).

Regards, Herman :D

---

### Post by logos34 on 2007-06-21
> Found a descript. on boot FDD. from Ubuntu Community Documentation called &#8220;GrubHowto/BootFloppy&#8221;. I made 2 FDD:s and both booted but after the Grub menu it stopped with error 15 file not found. I traced it to the Stage 2 file but have no clue of what file is missing and how to fix it.

I also had a problem with that howto--got the grub menu but it wouldn't boot the main kernel.  It took some trial and error troubleshooting to get it right.  In my case, copying stage1 and stage2 wasn't enough--it seems I needed something else in there, maybe the 'default' file (still not sure).  I also have to mount floppies to 'floppy0', my fstab default mount point.

Here is what works for me:

sudo mount /dev/fd0 /media/floppy0
sudo mkdir /media/floppy0/boot
sudo mkdir /media/floppy0/boot/grub

-Copy ALL files in /boot/grub:

**sudo cp /boot/grub/* /media/floppy0/boot/grub**   (the '/*' means any subdirectories are not copied)

Perhaps that will work for you.  Or make a [SmartBootManager]("http://linux.simple.be/tools/sbm") floppy.

---

### Post by alienexplorers on 2007-06-22
Just stick with grub.  It's easier than playing with floppies.  Never had a problem with grub a little research could not fix.

---

### Post by cwgpress on 2007-06-22
> **Herman said:**
> ..or you could just cut the entire Windows boot entry from the bottom of the menu.lst file and paste it halfway up, just above the line that says '### BEGIN AUTOMAGIC KERNELS LIST'. That's the easiest and the best way. ;)
See this link,  [Changing the default operating system]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc") (booted by the timer).

Regards, Herman :D
Thank you, Herman. I went to a Vista launch event, and that's how I knew about the differences in booting. I'll find a reference for you when I get time.

I didn't know I could add an external program into the automagic section. I should have realized that programs in the linux mostly are logical, not using special cases when a general one will do. I appreciate the tip.

---

### Post by bjolen on 2007-07-04
Hi fellows
Thanks for your valuable advices.
Regarding boot FD:s they are important in situation e.g. when MBR has been changed by some other installation etc or any other emergency sits. I will try your kind advice logos 34 .
Q: Is there any other way, to init Grub at start up keeping the orig Win MBR, than using FD or CD or USB stick.
E.g. can I change/add  something in the Win installation so the first I get at start up is the Grub menu.
Regarding changing Grub menu.lst  file I found a handy menu driven tool that makes it easy.

I will also look more into EASY BCD to se what it can give.

/ Bjolen

---

