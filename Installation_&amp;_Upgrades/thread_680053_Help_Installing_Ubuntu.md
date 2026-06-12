---
title: "Help Installing Ubuntu"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by ToySoldiers on 2008-01-27
Hey there. I've just been given a crappy old computer that I was going to try and install Windows XP on. It seemed that the disc wasn't being read by the PC. When booting it, all I get is "Missing OS". I then decided to scrap that, and install Linux Ubuntu on it, as i've never used Linux. I have downloaded the ISO, and burned the image to CD 2 times (first time being burnt incorrectly, second time seems the same). The first time it just burned the ISO to a disc. The second time, it burned correctly. I explored the CD and I can see all the individual files and folders, like it says in the install guide.

I inserted the disc into the PC, and i've tried playing with many different BIOS settings. I've changed the boot sequence to boot from CD. I have had the PC recognise the 2 CD-Roms, and then I get the messages

"Booting from Apati CD-ROM.......: Failiure
Missing OS"

I have just tried to run Ubuntu using the Live version on the CD on my PC, which everything works. I restarted my PC and I got the menu screen. I selected Start Ubuntu or install, or something. I then get a box saying "Error reading boot disc". I then tried to verify the disc, and get the same error. I've just been reading the guide on some problems. One thing I decided to check is the md5sum. I downloaded the software, and checked the md5sum. It seems though my md5sum doesen't match the one it's supposed to. Everything downloaded perfect, but my md5sum isn't the same. Does this mean I need to redownload Ubuntu?

Thanks for your help.

---

### Post by Partyboi2 on 2008-01-27
try downloading it again, and  choose another mirror to download from, when you burn the iso to disk burn at a low speed like x4 or lower as this does a better burn and less chance of corruption.

---

### Post by ToySoldiers on 2008-01-28
So the way I burned the CD was correct and shouldn't have any problems? I used Ahead Nero, went to File>Burn Image. I didn't think I burned the image correctly. I did burn it at 48x though. Should I use the same program, but change it to 4x?

Thanks

---

### Post by Partyboi2 on 2008-01-28
always best to burn at a slower speed. If the md5 matches and you have already burn't to cd at 48x try the disk, If  the md5 matches and you have not yet burn't it then I suggest burning at x4 or lower.
when you boot the live cd you will come to a main menu screen with options select  "Check Cd for Defects" (or something like that) this will check that the burn of the cd went ok.

---

### Post by ToySoldiers on 2008-01-28
I downloaded the Ubuntu 7.10 ISO file a few days ago, the one I have been trying to burn and use. I noticed that the Ubuntu ISO file should be around 695MB. My copy is only 580MB. Not sure what happened there. I checked the MD5Sum and they are not the same. I downloaded the alternate version, and checked MD5Sums, and they match. I will try burning this to CD later tonight at 4x.

---

### Post by TJCIB on 2008-01-28
I had the same error on an older computer.

Out of curiosity I installed a newer CD Drive (took it from another computer) and it finally read it.  You said it is an older computer, maybe ts just the drive...?

To be honest, it was actually my 3rd CD Drive that I tried....

---

### Post by ToySoldiers on 2008-01-28
Well I just finally got it to read the disc and boot from CD. It came up with the Ubuntu install, and I was away installing it. It got to the base install, and stuck at 6%. I'm not sure if it just stopped or taking a while, but a box did come up saying a file was corrupted. something beginning with lfibdipl0 or something.

I turned the computer off, and I eventually got to the screen again. I did the "Check disc for defects" and then it was stuck on some nvidia thing, so I turned it off again. I just tried to install Windows XP, but I got a message saying "missing NTLRS" or something. I can't get it to boot from CD now.

What shall I do. Could I ignore that corrupted message, and it would have carried on, or does that mean yet another disc doesen't work? It was all downloaded succesfully, md5sums matched, and burned at 4x.

---

### Post by dreamer.redeemer on 2008-01-28
Sounds like hardware problems to me, especially if you can't install windows or ubuntu. Of course, that means it could be anything: ram, hard drive, motherboard chipset, cd-rom drive...

---

### Post by ToySoldiers on 2008-01-28
Well would reburning the ISO to disc using my computer (i've been using Nero on the other computer, windows me) with the software shown in the Ubuntu guide make a difference? If it doesen't work that time, then give up? I don't want to waste all these discs, so if it's worth a try and would maybe make a difference, then i'll try it.

---

### Post by ToySoldiers on 2008-01-28
What about trying a different Linux distrubution, such as Damn Small Linux? Would this be a better chance of working on the computer i'm trying with. It's quite old, when I got the boot screen, it said something about the BIOS being aged, it's 1999 and Ubuntu wants atleast 2000. It's a Pentium II/III. No idea how much ram, etc...

Also, is Ubuntu and/or Damn Small Linux quite user friendly? It's not all about codes and such? I don't mind some coding, but alot to do most things i'd rather give up now. I'd love to get Linux running on this piece of junk I have sitting here, as it would be some great experience as I would like to work with computers when I start college.

---

### Post by stevescripts on 2008-01-28
duh ... you *ARE* burning the iso on a CD-R, rather than a CD-RW, yes?

If the md5sum is not correct, you dont have the proverbial snowballs chance of an
install.

Re:  Damn Small Linux - it may be worth a try from the livecd - but be advised
that if you install it, you're gonna have a bunch of stuff to d/load and install ...
(if I am reading between the lines correctly ;) )

Try to find the specs on your computer - it would help the friendly folks here
help you.

Steve

---

### Post by ToySoldiers on 2008-01-28
Yes I am burning the ISO to a CD-R.

The md5sum is correct for the alternate version I downloaded. I just tried to install again, and all I get is

file:///cdrom/pool/main/f/findutils/fundutils-4.2.31-1ubuntu2_i386.deb was corrupt

Then a screen which asks if I wish to contiue. After selecting continue, this is what I get for every single thing it tries to retrieve. It is just stuck on 6%.

There is no OS on the computer. Only thing I can get into is the BIOS. How can I find the specs of this computer?

Would a different cd drive be a good try? These cd-drives look quite old and crap. I have a newer one which I can try. I did try plugging it in but the computer don't turn on. I can try again, if it may be a possibility of it working. It may be the cd drive not working properly, so the disc isn't being read.

---

### Post by stevescripts on 2008-01-28
Quickie gut reaction.

With the md5sum correct, and a corrupt deb - sure looks like a hardware
issue.

Re - computer specs - Google on the make/model# ?

I wont be back til much later tonight - but lots of folks here stand ready
to help.

Steve

---

### Post by ToySoldiers on 2008-01-28
The computer has a sticker on the back which says

> SKU4130599  MODEL: 24503D/7
CT641/3CYW6C/BG2L
CT641/PIII450/64MB SDRAM/10GB HARD DISK
DVD4X/WIN98/S/SUITE/FAX
MODEM/           LEE

Also says Daewoo on the computer in places.

---

### Post by stevescripts on 2008-01-28
hmm - that looks bad - I cant think of *any* modern OS that is gonna run
in 64MB of RAM. 

Anybody else got a clue?

Steve

---

### Post by Partyboi2 on 2008-01-28
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://damnsmalllinux.org/](http://damnsmalllinux.org/)
[http://www.puppylinux.org/user/viewpage.php?page_id=1](http://www.puppylinux.org/user/viewpage.php?page_id=1)

or maybe consider getting some more ram. :)

---

### Post by stevescripts on 2008-01-28
Thank you Partyboi2. 

Having just recently tinkered with both DSL and Puppy, guess I didn't take a good
look at the requirements.

Hope this helps ToySoldiers, sure looks like it should.

Steve

---

### Post by ToySoldiers on 2008-01-29
I've read about DSL and Puppy Linux, and they seem like they're for really low end systems. But as you said stevescripts, if I were to use DSL, I need to do alot of downloading and installing, which is what I don't really want to be doing. I'm not sure about Puppy Linux, do you still have to download alot?

I'm just gonna have 1 more shot at trying to get linux onto this computer, so i'd like to try the most likely one there is. This computer is basically the crappest computer there is, so whichever Linux needs the lowest requirements, I think i'm going to try.

Thanks for your help.

---

### Post by ToySoldiers on 2008-01-29
bump.

---

### Post by apaciq on 2008-01-29
Try this since it looks like you an "old" pc...when it boots up...try pressing "DEL" key or F1, F2, and down the line...if you get to the BIOS....check the boot up sequence...after making it the necessary changes...to make it boot to cd rom drive..choose what ever that denotes the cd rom drive as the first boot...press F10 save changes...it could be that it is booting to the hard drive first...
hope this helps...

---

### Post by ToySoldiers on 2008-01-30
I have already done all of that, which is why I have had it booting from CD. Thanks for your help though.

Anyone else be able to help me?

---

