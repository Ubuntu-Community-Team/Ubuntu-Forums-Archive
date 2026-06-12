---
title: "Lubuntu install freezes on boot up."
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by loren45 on 2010-08-23
Hello all, 

Linux newb here. I was looking for a lightweight distro that I really like and Lubuntu was it. I installed in on all three of my comps with out issues and my old Dell desktop(512mb ram) is flying now. Way faster than XP even right after a fresh install of both on the same desktop. 

On my fourth install, my girlfriends old toshiba laptop, it installed fine. After the restart and reboot it gets to the Lubuntu logo with the 5 dots under it. It gets through 4 of the dots then freezes. I left it for 20 minutes and it was stuck. 

I tried booting from cd again and check disc for defects. It said it found 2 files with errors, press any key to reboot. Which I did and it just booted right back into the freeze. Maybe since I have to manually make it boot from cd every time it was wanting to boot back into the CD after the disc check, I'm not sure. 

I tried burning a new iso on a slower speed, same thing for a total of 3 reinstalls with the same effect. 

The only thing different about this install compared to my others is: 
 

A) I had to flash the bios from windows before I started to even get the damn thing to be able to boot from CD

B) I decided to just wipe XP and install Lubuntu on the whole drive. 

Does anyone have any ideas on how to get Lubuntu to boot up properly? Its pretty much the last hope for this computer. 

Thanks in advance.

---

### Post by lechien73 on 2010-08-23
Are you able to boot to a desktop from the Lubuntu Live CD, or does it cause the same problem?

---

### Post by loren45 on 2010-08-23
Yes I can access the desktop via the live CD. When I click install Lubuntu it takes me there where I have to click on the hard drive icon to begin installation.

---

### Post by loren45 on 2010-08-23
Just one more piece of info that may be relevant. Upon the restart after the install,

when it ejects the disc I got the page filled up with this:

[ 1380.04530] end_request: I/O error, dev sr0, sector 631044

This filled the page but each line with different numbers. It happened on my new desktop, I hit enter and all was good after that so I didn't think much of it. It didn't do it on my laptop, or my old desktop. 

It did display this message on the problem laptop, not sure what it means.

---

### Post by NeoGraven on 2010-08-23
If I may ask, what are your laptop specs?

---

### Post by loren45 on 2010-08-23
Toshiba A100. 

It appears that there are several different versions when I looked up the specs but basically its a pentium processor, 512mb ram, 80g hard drive. 

I think the disc drive is failing, I wonder if pulling the hard drive and installing it with another drive would work. Because every time I check disc for defects it get errors. I used the same disc on 3 other machines with zero problems.

---

### Post by loren45 on 2010-08-23
Well, I put the toshiba hard drive in my Dell Inspiron laptop expecting to have to reinstall but it booted up just fine.

So the OS installed fine but just won't boot on the toshiba laptop. 

Any thoughts?

---

### Post by spcwingo on 2010-08-23
What I would do is try the mini installer disc.  If you would like to go that route it can be downloaded here:

[http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/netboot/mini.iso]("http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/netboot/mini.iso")

Burn and boot as normal.  After booting install just a command line system.  Next boot into your system and login on the terminal.  After that, run this command:

```
sudo nano /etc/apt/sources.list
```

When that opens find the lines that are commented out [(they will have a # in front of them)BTW, just the ones formatted like this:

```
deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
```

or this:

```
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted
``` ]

and remove the comment annotation (the #) on all of them except the ones that have "backports" somewhere in the line.

After that save (CTRL+O) then exit (CTRL+X).

Finally run these commands:

```
sudo apt-get update
```

followed by:

```
sudo apt-get install lubuntu-desktop
```

then:

```
sudo apt-get clean
```

finally:

```
sudo reboot
```

If all goes well you should boot into your new Lubuntu desktop.  :)

EDIT:  I have just seen the part about the error in one of your previous posts...if the above doesn't work it may just be a hardware problem.  I would suspect the RAM first, the CD-ROM second, and the motherboard last.  Just my $0.02.

---

### Post by loren45 on 2010-08-25
> **spcwingo said:**
> What I would do is try the mini installer disc.  If you would like to go that route it can be downloaded here:

[http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/netboot/mini.iso]("http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/netboot/mini.iso")

Burn and boot as normal.  After booting install just a command line system.  Next boot into your system and login on the terminal.  After that, run this command:

```
sudo nano /etc/apt/sources.list
```

When that opens find the lines that are commented out [(they will have a # in front of them)BTW, just the ones formatted like this:

```
deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
```

or this:

```
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted
``` ]

and remove the comment annotation (the #) on all of them except the ones that have "backports" somewhere in the line.

After that save (CTRL+O) then exit (CTRL+X).

Finally run these commands:

```
sudo apt-get update
```

followed by:

```
sudo apt-get install lubuntu-desktop
```

then:

```
sudo apt-get clean
```

finally:

```
sudo reboot
```

If all goes well you should boot into your new Lubuntu desktop.  :)

EDIT:  I have just seen the part about the error in one of your previous posts...if the above doesn't work it may just be a hardware problem.  I would suspect the RAM first, the CD-ROM second, and the motherboard last.  Just my $0.02.

spcwingo, 

IT WORKED!!! HOLY ****! I spend a solid two days messing with this and was pulling my hair out. All I wanted to do was make my girlfriends computer usable again and I wiped XP off her drive and was getting ready to reinstall it in defeat but I saw your post and thought I'd give it one last try. 

I can't thank you enough! 

That was a LENGTHY PROCESS too, all in all just under 3 hours. I had no idea what was gonna happen and frankly I was skeptical but when it actually booted into the OS, and I rebooted just to be sure I was quite pleased. 

Would you mind explaining the difference between that install process and booting from CD? I'd like to have a basic understanding of why it worked and why it didn't at first.  

Thanks again your help is very much appreciated!

---

### Post by spcwingo on 2010-08-25
Installing from the standard live disc will only install the image that was made from the packages at release time.  The way that you just did it was all the packages were brought in one-by-one and installed.  So, if one of those packages from the live disc had a bug that wouldn't let you install you bypassed the older version and installed the updated version at install time as opposed to upgrading later.  Anyways, I'm glad you got it going and as always happy Ubuntuing!  :)

---

### Post by loren45 on 2010-08-25
Ok that makes sense. I noticed there were a couple things different about her desktop features than mine, mostly for the better. Still no proper hibernate function and disable tap to click still can't be saved however. Oh well, her computer is functional and lightning fast now and she's happy :) Thanks again.

---

