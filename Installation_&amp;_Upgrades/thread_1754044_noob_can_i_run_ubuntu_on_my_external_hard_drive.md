---
title: "noob* can i run ubuntu on my external hard drive?"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by blitzkriegg9x on 2011-05-09
This is my first post so give me a brake please.
Is it possible to run Ubuntu off of my external hard drive? And completely leave my internal hard drive (with win7) alone. my external hard drive is connected via e-sata. I have used Ubuntu in the past but never really grew on me, i have always wanted to be an Ubuntu user but i want to go about doing so gradualy and safely.



edit* tell me if im in the wrong section, im new to this forum.


please help :confused:

---

### Post by garvinrick4 on 2011-05-09
Yes you can it will be drive sdb and your internal is drive sda if you add another drive in that order will be sdc and so on and so on.
Here is link to help you install choose sdb to put grub into (your boot manager) then you can
choose through BIOS to boot off of sda (windows) or sdb (ubuntu) sdb will be capable of booting
both windows and Ubuntu and sda boots only Windows. Link below: And always have back ups
of any personals when installing New Operating System or adding, resizing or deleting partitions.
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
If you are using whole drive you can just choose that at install and put grub in sdb
file system go's in / and format is ext4.

---

### Post by garvinrick4 on 2011-05-09
Linux calls partitions sda1, sda2, sda3 and so on Windows calls them 
C, D, H, F and so on. Same thing different OS. Linux is also case sensitive where 
Windows is not. Second drive would be sdb1, sdb2 sdb3 and so on. always put
grub in sda if using first drive, sdb if second drive, sdc if third drive and so on.
Never put in a sda1, sdb1, sdb5 and so on always just sda, sdb or sdc whichever
drive putting linux onto. There is a post installation guide in my signature and also
a .pdf book to download that is informative. Enjoy.

---

### Post by blitzkriegg9x on 2011-05-09
i'm a little more newbie then that.. i sorta get what your saying, but i'm learning the basics still. i dont know the right terminology but grub is what yo use to boot up right? basically

so what do i need to do in order to prepare to instal Ubuntu on my external?

---

### Post by becausegoogledidntknow on 2011-05-09
I'm actually on my laptop with an external HD Ubuntu(Meerkat) right now!

Do you plan on installing by using a LiveCD? That's the easiest way.

---

### Post by garvinrick4 on 2011-05-09
This will give you a tutorial with graphics from Ubuntu: Step by step: Remember you are sdb:
[Download | Ubuntu]("http://www.ubuntu.com/download/ubuntu/download")
another link:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by blitzkriegg9x on 2011-05-09
well i ahve ubuntu 9.10 cd i got in the mail a long time ago.. can i use that then upgrade?

---

### Post by garvinrick4 on 2011-05-09
> **blitzkriegg9x said:**
> i'm a little more newbie then that.. i sorta get what your saying, but i'm learning the basics still. i dont know the right terminology but grub is what yo use to boot up right? basically

so what do i need to do in order to prepare to instal Ubuntu on my external?
Nothing will do it for you while you install.

---

### Post by blitzkriegg9x on 2011-05-09
so i can just use ubuntu 9.10 cd i got in mail? how do i  know im not puting ubuntu on my internal?

---

### Post by garvinrick4 on 2011-05-09
> **blitzkriegg9x said:**
> well i ahve ubuntu 9.10 cd i got in the mail a long time ago.. can i use that then upgrade?
If you have a blank CD you can download 10.04 the Long term support version and burn a
CD. I gave you link and instructions in "Download Ubuntu" link.
9.10 karmic you can install then upgrade to 10.04 is better to have fresh install you do what
you feel comfortable with. But anywhich say 10.04 would be best for you to start your journey with into Ubuntu.

---

### Post by blitzkriegg9x on 2011-05-09
why 10.4 long term support? what is that and why is it different from 11.4?

i mean i know there different but why would i use that one instead

---

### Post by garvinrick4 on 2011-05-09
> **blitzkriegg9x said:**
> why 10.4 long term support? what is that and why is it different from 11.4?

i mean i know there different but why would i use that one instead
11.04 just came out and 10.04 LTS has been out for over a year (supported for 3 years) and is real stable
and works with most hardware. You use what you want.

---

### Post by blitzkriegg9x on 2011-05-09
oh ok thank you, but is it possible and would it be the same if i used my 9.10 disk and just upgraded from there because i dont feel like waiting 4 hours to download it.:(

---

### Post by garvinrick4 on 2011-05-09
Do you have a slow download rate usually takes about 20 minutes or so maybe a bit
more. Do not know your download rate though. If you want go ahead and install
9.10 if you choose. Get back if any confusion installing you sound anxious to get started.

---

### Post by blitzkriegg9x on 2011-05-09
i am very! ok ill try that, so it wont be any different if i just upgrade with 9.10? 

ill come back with any questions i have thanks

---

### Post by blitzkriegg9x on 2011-05-09
i used 9.10 but no luck, i was given 4 options and one was to instal ubuntu so i clicked that and i took  me to a black screen with a blinking "_" i though took ill just let it go and come back, but i went away for 5 min and it was still there. tried pushing buttons nothing happened. so what do you think now. i went ahead and started the dl for 11.04. my internet speed is suposed to be 1.5 but its not and my dad wont get anything better sigh.

---

### Post by garvinrick4 on 2011-05-09
You did put the CD in and then reboot so it boots off of the CD correct. Then you
hit install and it starts the process.
*Your Dad has given you permission to install another operating system on
this machine?

---

### Post by blitzkriegg9x on 2011-05-09
im 16 its my laptop :P  asus g71gx

oh and yes i did. changed it to boot from cd

---

### Post by garvinrick4 on 2011-05-09
> im 16 its my laptop :razz:  asus g71gx
Just checking.

---

### Post by blitzkriegg9x on 2011-05-09
so what do you think i should do? just wait for 11.04? do you want my specs?

---

### Post by blitzkriegg9x on 2011-05-09
are you coming back?  : [

---

### Post by garvinrick4 on 2011-05-09
Did you download and burn a disk?

---

### Post by blitzkriegg9x on 2011-05-09
opps i posted a better thread because i thought this one died

[http://ubuntuforums.org/showthread.php?p=10793713#post10793713](http://ubuntuforums.org/showthread.php?p=10793713#post10793713)

and its downloading now. 55%

edit 64%

---

