---
title: "cant install ubuntu 10.04"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by prsreek on 2010-10-25
hi..
i am new to linux world.
i tried to install ubuntu 10.04 on on my old pc.but it shows some error like this..
[IMG]http://i56.tinypic.com/2z6b6rl.jpg[/IMG]
i think its because of my video card.
i installed a new pci vga card because my onboard vga is not working.
my pc configuration is..

intel pentium 4
512mb ddr
320gb hdd
new vga card - Rage Xl ATI
onboard -Intel® 865GV chipset

i also tried to install linuxmint 9 it also shows this error..!

is there any way to solve this problem...

---

### Post by mörgæs on 2010-10-25
Hi, exactly which error did you get?

---

### Post by prsreek on 2010-10-25
the screenshot of the error is given ...
error_code+0x72/0x80
i cant use the live cd of ,ubuntu 10.04,linuxmint 9,kubuntu etc..
is there any way to solve this

---

### Post by mörgæs on 2010-10-25
Yes, now I can see. My first post was written from work, where the pictures were blocked.

You have a kernel panic, which is the Linux equivalent of Windows' blue screen. Have you tried a live boot with 10.10?

---

### Post by prsreek on 2010-10-27
i cant able to select the "live cd" option.
booted from cd,then it shows a small logo on the bottom of the monitor [white logo]
then after that it doesnt show the loading screen like this:
[IMG]http://linuxhub.net/wp-content/uploads/2010/06/Selection_021.png[/IMG]

after the small white logo appears.it then goes to the error that i was posted on my first post.
i got this cd from [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/) and i tried it on my virtual bx and it worked[laptop]
and i got this error on my pc..
plzz help...

---

### Post by prsreek on 2010-10-27
i didnt tried 10.10 
tried only 10.04..........
going to try it..!

---

### Post by TNT1 on 2010-10-27
Add a nomodeset switch before you boot off livecd, or get the alternate install cd.

---

### Post by prsreek on 2010-10-27
> **TNT1 said:**
> Add a nomodeset switch before you boot off livecd, or get the alternate install cd.
i tried but not working.............
same error ... :(

---

### Post by cogier on 2010-10-27
There are several things you could try. I would download a copy of the "Alternative CD" from here [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download") and try installing with it. It seems to check more things and does not require as much memory.

You have set "nomodeset" but you may need to experiment with the other available options "noapic", "nolapic", "acpi=off". You could select them all and if the computer boots try removing one and see what happens. 

It took 5 or 6 attempts to get an HP desktop to run Ubuntu by setting these switches. 

When you find the correct setup you may need to put the options in the Grub file and update it. For more details on this Google something like "add nomodeset to grub2".

---

### Post by prsreek on 2010-10-27
finally i got the ubuntu loding screen..
i selected option "install"
it also produce the same error 
[IMG]http://i56.tinypic.com/2cdwvus.jpg[/IMG]

---

### Post by mörgæs on 2010-10-27
By using 10.04 or 10.10? Alternate or regular? Which boot parameters did you try? 

We need some more information here...

---

### Post by KaiO on 2010-10-27
On an old machine I would definitely recommend using the *alternative* cd.
It has a text-based installer that in my experience runs better on old hardware.
You can find downloads via torrents (really fast...) here:
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt)

or as ordinary download from here:
[http://ubuntu.uib.no/releases//maverick/](http://ubuntu.uib.no/releases//maverick/)

Download this and burn ISO image to CD:
[http://ubuntu.uib.no/releases//maverick/ubuntu-10.10-alternate-i386.iso](http://ubuntu.uib.no/releases//maverick/ubuntu-10.10-alternate-i386.iso)

---

### Post by prsreek on 2010-10-27
am using 10.04 regular i tried a lot of parameters...
but no use...
am downloading the alternate version....

---

### Post by ophie99 on 2010-10-27
what kind of pc are you using? I've never seen anything like that. Maybe Puppy linux or Damn small would be a better choice. I assure you that running the latest and greatest on a old pc is a headache at best.

---

### Post by prsreek on 2010-10-27
i tried linuxmint,xubuntu,ubuntu but same problem..
when i tried freebsd and pcbsd it works...

---

### Post by mörgæs on 2010-10-27
It is amazing how die-hard Damn Small Linux is in this forum. The development ground to a halt years ago, so forget about this one.

Have you tried 10.10 alternate?

---

### Post by prsreek on 2010-10-28
i tried 10.10 alternate it stops at "detecting network hardware"
then it shows the error tht i posted on first post.

:(

---

### Post by prsreek on 2010-10-28
need some help here

---

### Post by prsreek on 2010-10-28
open suse woked in my pc.........

---

### Post by ezsit on 2010-10-28
Try other distros. Try Mandriva, OpenSUSE, Fedora. Try older versions of distros, try distros made for older hardware like Puppy. Try Zenlinux or Salix - two known for working well with older hardware. PCLinuxOS and MEPIS are also good candidates to try since they are geared towards the new user and relatively simple beasts. If Ubuntu does not work there are hundreds of other distros to try.

---

