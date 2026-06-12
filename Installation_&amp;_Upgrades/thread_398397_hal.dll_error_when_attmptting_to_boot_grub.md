---
title: "hal.dll error when attmptting to boot grub"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by crshbndct on 2007-03-31
I am attempting to install 6.10 onto an old laptop that I have. It does not have a CDRW drive, can not boot from usb, and it is not on a network. I have downloaded the release iso for 6.10, and installed grub onto my machine. I cannot burn this onto a cd conveniently and i need to have it running tonight hopefully as i need to use it for a report i have to write for school. 

I installed grub and when i booted to it, I only got the options (besides the usual lother ones) for:
"Detect and mount CD-rom"
"Load Installation media (or whatever the option is, i cant remember now)"

when i was getting the instructions for installing grub (booting with boot.ini and addind c:\grldr to it) i was lazy and used the linux and initrd.gs files from the iso image i had downloaded.

after a bit more searching, i realized that maybe i needed to use the vmlinuz and initrd.gs files from the archive to enable the "Hard drive installation" option in my ubuntu installation menu

after donloading the files, i replaced them in my c:\boot folder and attempted to start grub.

I now get the systemroot\system32\hall.dll is missing or corrupted error when i attemtp to START GRUB!!!!! not windows. windows goes fine(well as good as it can go) but when i choose start grub from the windows boot menu i just get that stupid error.


i have placed the iso file in the same directory as initrd and vmlinuz, and i really wanted to get this sorted.

either way i need to know how to either now make grub boot without spitting up the hal.dll error or getting some kind of option to tell ubuntu installer to use my iso file on the hard drive.

the machine is a dell latitude laptop, 15gb hdd, 256 ram (i was going to use xfce for the wm to make it a bit snappier)and right now is the only machine i have access to. i am also on dialup for the next two weeks, so any massive downloads are useless. buying an external cdr drive is out the question, as i am pretty broke and need my last cash to get to school this week(well actually its a course i am on, but i call it school)

please help!!!
soon!!
ta

---

### Post by crshbndct on 2007-04-01
please someone. i know it probably a hard one, but i really wanna get ubuntu going so i can get this report done tonight.

the laptop is a p3 500 btw. if anyone can help me i will be very appreciative.

my main issue is that i get a hal.dll error when attempting to start grub

---

### Post by zvacet on 2007-04-01
[http://ubuntuforums.org/showthread.php?t=316093&highlight=iso]("http://ubuntuforums.org/showthread.php?t=316093&highlight=iso")

---

