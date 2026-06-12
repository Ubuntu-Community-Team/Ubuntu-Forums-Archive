---
title: "booting from cd"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by bluemonaboo on 2007-09-03
hi.new to linux today. liked the idea of running laptops from cd-rom but not up to that yet.will try feather later. just downloaded and burned ubuntu to cd. have correctly burned it to my understanding. browsing the cd shows the files as they should be. set 2 laptops to boot from cd but it wont boot. can browse the cd from windows but not boot from cd.

---

### Post by Sef on 2007-09-03
1) Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the download?

2) Did you burn the cd at 4x or less?  (Faster can corrupt the burn.)

3) Did you check if the disk is good?

---

### Post by bluemonaboo on 2007-09-03
thanks for replying. no i didnt fd5sum the download.and i burnt at 24x. il burn at 4x and try again. i have a feeling the download will have to be done again. i saved it to a usb stick then transfered it to hard drive. iv read the fd5sum but could you anyone explain how to do it ?

---

### Post by merlinus on 2007-09-03
[http://www.psychocats.net/ubuntu/iso#checksum](http://www.psychocats.net/ubuntu/iso#checksum)

-merlin

---

### Post by Pumalite on 2007-09-03
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by bluemonaboo on 2007-09-03
yes just did the fd5sum for windows and the download is ok.will try the 4x cd shortly.

---

### Post by bluemonaboo on 2007-09-03
still doesnt boot. could it be the capacity of the cd? its a 697mb cd and it shows as totally filled with no space left after the install. do i need a larger cd?

---

### Post by Pumalite on 2007-09-03
Are you burning as an 'Image' and not Data?

---

### Post by bluemonaboo on 2007-09-03
i burnt as a data cd.. so il burn as an image.. see how that goes. ty

---

### Post by bluemonaboo on 2007-09-03
i burnt as an image. same problem. will not boot from the cd. can anyone please help.

---

### Post by Pumalite on 2007-09-03
Go to BIOS and make sure your CD is first in boot order.

---

### Post by bluemonaboo on 2007-09-03
the laptop is set to boot from cd-rom 1st. im familiar with installing windows.this is a cd burning problem. the download has checked out ok. so it must be the burning process thats the problem

---

### Post by merlinus on 2007-09-03
It also may be that your cd drive has developed some defects, or the lens is dirty.

Try the cd on another machine.

-merlin

---

### Post by bluemonaboo on 2007-09-03
thanks but iv tried different machines already. i give up. im going to try solaris 10

---

### Post by Pumalite on 2007-09-03
It's Windows the problem; not Ubuntu. It left your hard drive littered.

---

### Post by msft_fuqt_me on 2007-09-04
For what it's worth, I am having exactly the same problem (can't boot from CD).

I am actually more familar with Linux than with Windows, I run various flavors of Linux on several servers. I've been hearing about Ubuntu and was thinking about putting it on an old Dell Dimension 2350, but just like the starter of this thread, the machine will not boot from the CD. I did the checksum as well as burning at 4x. The files appear to be there when viewing the disc from within XP.

If I open the CD from within Windows, I get the Ubuntu splashscreen.

But when I boot from the CD, it seems like the video never kicks in (I hear an audio sound like maybe the Ubuntu logo is up, but the screen is black).

One thing is that this machine came with a (weak) onboard Intel video chipset, but I installed a more powerful Nvidia graphics card. But Nvidia is a major vendor, so I would expect that Nvidia cards would work with Ubuntu...

Removing the graphics card is not an option, unfortunately. Is there an Ubuntu Hardware Compatibility list anywhere?

Thanks.

---

### Post by bluemonaboo on 2007-09-05
back from solaris. after spending $30 on 3gig of download found it even more dfficult. did find the solution though to problem here with the non booting cd. the problem was the programme i used to burn the cd. used nero 5 1st. that didnt work. so then used a free programme called infrarecorder and presto.. the feather os i downloaded onto a usb stick now boots off a cd that didnt b4.expect wen ubuntu is burnt with infrarecorder it will work too

---

### Post by msft_fuqt_me on 2007-09-05
> **bluemonaboo said:**
> back from solaris. after spending $30 on 3gig of download found it even more dfficult. did find the solution though to problem here with the non booting cd. the problem was the programme i used to burn the cd. used nero 5 1st. that didnt work. so then used a free programme called infrarecorder and presto.. the feather os i downloaded onto a usb stick now boots off a cd that didnt b4.expect wen ubuntu is burnt with infrarecorder it will work too

I tried with Infrarecorder and still have the same problem.

I think it has to do with the video support on the Ubuntu CD. machine boots from the CD, and I get an audio welcome prompt, but the monitor is black and there is no video.

Can anyone assist? From searching the forum archives, it seems as though quite a few people are having a similar problem as this...

---

### Post by merlinus on 2007-09-05
You might try the Alternate Desktop install cd. It is text-based, but quite straightforward.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, then click the text to begin.

-merlin

---

### Post by msft_fuqt_me on 2007-09-05
> **merlinus said:**
> You might try the Alternate Desktop install cd. It is text-based, but quite straightforward.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, then click the text to begin.

-merlin

Thanks for that suggestion!

But as I understand it, the Alternate Desktop install is for installs only and won't let me run Ubuntu from the CD. I want to run Ubuntu from the CD first to check it out, as well as make sure it's compatible with my hardware before I go in and re-partition this machine's drives and do a full install.

Do you know if there is a way to break out of the GUI livecd boot sequence, and load something like a character-mode boot loader or a Windows-style safe mode?

---

### Post by merlinus on 2007-09-05
Safe Video Mode from the startup menu.

-merlin

---

### Post by gubemton on 2007-10-27
> **msft_fuqt_me said:**
> For what it's worth, I am having exactly the same problem (can't boot from CD).
[snip]
I wanted to put Ubuntu on a very old PC (previously running Mandrake); I found that while I   could boot from the CD, installation failed repeatedly. I managed to solve the problem by changing the old CD drive (made in 1997, so probably an 8-speed or 12-speed) for a newer one. 

You could try booting from a different device -- eg copy the CD to a USB device or external HD -- or try a different CD drive.

---

