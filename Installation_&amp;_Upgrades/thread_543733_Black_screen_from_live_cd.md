---
title: "Black screen from live cd"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by Grizzled on 2007-09-05
I am trying to run feisty fawn from the live cd. I've checked the Cd write and it is good. I've tried the light graphics and I still get a black screen with a cursor at the top. 

After hitting the F6 key at on the install or start screen I typed in a command to get the load sequence and it stops with these messages.
VFS: cannot open root device"null" or unknown block(104,1)
Please append a correct "root=" boot option Kernal panic_not syncing
VFS: Unable to mount root fs on unkown-block(104,1)

There is a cursor after this line and for input but my keyboard does not work. Help I really want to switch from windows.

---

### Post by Vic! on 2007-09-05
maybe the way you burned it was incorrect make sure that its burned the way it tells you to burn it in the ubuntu site. 'image' cd ... also what kind of computer do u have... i used my sisters mac to burn the live cd because its easier than on a windows but there are instructions for all kinds on the ubuntu site ...oh and also burn it on a regular 80 min 700mb cd i tried using a dvd r once and it wouldnt work i dont know why but it wouldnt. post back if u solve this prob

---

### Post by Grizzled on 2007-09-05
I checked the cd for integrity from the ubuntu start screen and it said it was good. I also did a md5sum check on the file and it was good.

---

### Post by merlinus on 2007-09-05
Post system specs.  May be a video problem.

-merlin

---

### Post by mindspin311 on 2007-09-05
I got the same thing in safe mode (read errors when installing in regular mode)

If you were getting these errors and using a dvd-rom.. try using another drive.. a cd rom or cd-r drive. That fixed the problem as I was getting read errors booting from the dvd-rom. Even if you don't have one in your pc, Just throw in a different drive for now to take care of the boot problem.

---

### Post by Grizzled on 2007-09-05
I have a chainteck volari v3 video card.

---

### Post by mindspin311 on 2007-09-05
[http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL](http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL)

Not listed as compatible card here. That could be the problem. You could probably get a cheaper one listed there for like $20 or less.

I found a radeon 9600 pro for $45 on newegg.com

that should be more than enough.

What are your system specs?
CPU?
RAM? (RDRAM/DDR?)
What kind of slot of motherboard for graphics card? (AGP, PCI, PCI-E?)
HDD?
Optical drives? (Cd/DVD?)

---

### Post by Grizzled on 2007-09-05
Celeron D 2.5
512 ram
Gigabyte 8s648fxp
Barracuda 7200 Seagate HDD
SamsungTS-h5522u  DVD/Cd

---

### Post by merlinus on 2007-09-05
You might try the Alternate Desktop install cd. It is text-based, but quite straightforward.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, then click the text to begin.

-merlin

---

### Post by mindspin311 on 2007-09-05
I'd suggest going through a normal installation. If it just shows a blank screen, then you need a new video card. I suggest [http://www.newegg.com/Product/Product.aspx?Item=N82E16814102410](http://www.newegg.com/Product/Product.aspx?Item=N82E16814102410)

If you are getting a ton of read errors, then I suggest trying another drive to boot from.

If all else fails.. try the alternate boot disc from the unbutu site (check the box when downloading)

---

### Post by Grizzled on 2007-09-05
Thanks, I'll try taking out my video card and see if I can get feisty running with the integrated video on the motherboard.

---

