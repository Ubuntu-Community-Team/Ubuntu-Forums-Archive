---
title: "asrock 890 deluxe 4 wont boot"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by rexxxlo on 2010-11-18
i cant get ubuntu to install on this board

live usb ,desktop, alternate  or cd alternate nothing i can get to the screen where you choose options i can pick the things i want and hit enter then get a non blinking cursor 

the board is pretty new so i can t seem to find anything about it Google gives me a few people running Linux on it 

if i use the alternate i get to the detecting hardware section and it locks up.

i installed the wubi but that wont work either there is a short 5 second splash screen the te1lls you to push esc for options ive tried all the options and it wont boot either 
i have even tried the newest fedora it locks up just about the same place.

i wonder if its a bios setting or some acpi stuff but i dont know this board even offers usb3 and sata 3 so is linux just lagging behind a bit?

i tried emailing asrock and got a bad English response saying they offer no linux support

> Dear Bill,
ASRock support Windows OS does not support any Linux version.
If you have experiences some issues with windows please described .
 
ASRock America Support 

what to do what to do ?  i am currently running xp64bit it runs boots and loaded fine with no tweaking but i cant use winblows 

pleaaaaaase help






oh specs as it sits:

asrock 890fx deluxe 4
amd 6 core proc
ati video
ocz ddr3 ram
wd sata 320 hdd
ide dvd burner and dvd rom

---

### Post by rexxxlo on 2010-11-19
anything ?


is there a checklist somewhere to find out what makes a computer not boot from a live usb,cd or hard drive?

its not hardware failures because its running xp64bit as i speak

---

### Post by raym575 on 2011-04-22
been trying to install ubuntu ue 2.9 same issue as you

[http://www.phoronix.com/scan.php?page=article&item=asrock_880_mobos&num=4\](http://www.phoronix.com/scan.php?page=article&item=asrock_880_mobos&num=4\)

go to bios section read article has some help (not much explanation) will research if i find anything i will let you know

somebody on youtube has linux installed on this mb contacted this person they said had no problem installing ( what the heck!!!! ) said to install to hd or usb thumb. i will try the thumb

have tried most distros ( amd64 ) i normally get blank screen with flashing cursor and then nothing or i get a menu and the program hangs.

---

### Post by rexxxlo on 2011-04-22
i got it working later that day..... that mobo is quirky:confused:

sometimes it totally forgets the bios settings and wont boot.

 i have to take all the cards, hard drives and memory out to even get into the bios otherwise i get a blinking cursor

first thing make my changes before anything but a processor and one stick of ram is connected

 reconnect the ssd im using for the os re boot, set the boot drive for the one hdd i have connected and reboot

then click the ram all back in  and reboot

then connect the rest of my hdd's and reboot 

and then sometimes that works sometimes it wont and i have to repeat the process

dont dare try using the over clocking program or you are doing it all over again

i sent asrock an email they responded with there is no linux support for that board 

i wont ever buy an asrock again ill stick with something more linux friendly

---

