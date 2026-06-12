---
title: "Base system installation error : official CD"
date: 2005-07-04
forum: Installation &amp; Upgrades
---

### Post by gez on 2005-07-04
I am trying to install Hoary, and at about 10% through installing the base system I get the following scary red error message:

>   Base system installation error

>   The debootstrap program exited with an error (return value 1).

>   Check /var/log/messages or see virtual console 3 for details

Virtual console 3, or the messages file, ends with: 

>   cp: read error: Input/output error

I have seen several postings that quote this error but they all seem to have been using burned CDs. I sent off for TWO official CDs and both of them do exactly the same thing. The Live CD works perfectly though, thats what I'm using now!

---

### Post by speedwolf on 2005-07-10
That's the exact same message that I get.
I can't use the live cd though. It starts to boot then the kernal dies. I can't exactly remember the final error but I thought it wasn't really important as I want the install on my HD not to run from CD.

---

### Post by RJARRRPCGP on 2005-07-11
Probably a bad CD burn. (corrupted CD burn)

---

### Post by yoshic on 2005-07-11
yeah, i've got the same problem. this is because the cdrom cannot read the disk , probabbly a bad burning, in my case  my disk had an scratch  ;-)

---

### Post by trash on 2005-07-11
I just ran into the same error installing onto an older machine, however I have used this cd many times before without any problems. The machine that this problem happened is a P1, with 98mb of ram (a 64mb stick and 2 32mb= strange in itself).
I have used the same cd since to reinstall on a PII so i know for sure the cd is ok.

The other oddity on the P1 is that it can't quite get working with two hd drives, so i am thinking its a bios issue... but i am only guessing.

---

### Post by boxerboy on 2005-07-13
im haveing same errors as u are only im booting from burnt cd. i ordered the cds but they havent showed yet been a few weeks i wish i know what to tell u to help u but if i find out i will let u know.

---

### Post by speedwolf on 2005-07-14
I've actaully been thinking for a few days that my dvd/cd-rw is borked.
I'll replace it with a slower dvd-r that I've got lying about and see if that makes a difference.

---

### Post by trash on 2005-07-16
Ubuntu now running on a P1 166mmx... ram was my install problem, I removed all the ram except a good 32mb stick and the install was flawless... after hoary was up and running I stuck the rest of the ram back in and i'm still good to go with 98mb lol. OOo ONLY takes a minute and a half to open!! haha.

as mentioned in my earlier post, it's the 64mb stick that is only being read as a 32... go figure... anyhow good luck guys.

---

### Post by h0bbe on 2005-07-30
I have exactly the same problem with my Shipit CD's: debootstrap error=couldn't retrieve bsdutils. I've tried with five different CD's and still have the same problem. The LiveCD works fine though.

Is it really possible that all of the CD's are bad or is there a solution to the problem?? There is a description of it on [https://bugzilla.ubuntu.com/show_bug.cgi?id=12790](https://bugzilla.ubuntu.com/show_bug.cgi?id=12790) but I don't understand what do do.

I really want to get Ubuntu working!

---

### Post by OneSeventeen on 2005-08-01
When I looked through my "screen 3" it looked as though the problem was it's inability to write to the floppy disk.  In my case, I don't have a floppy drive on my laptop.

Any ideas if this might be the same problem?  (I went ahead and told it to go on to the next step: copying all extra packages to the hard drive) and after it copied them, it ran the grub installer, and after rebooting without the CD it is installing the packages.

Perhaps this is a problem that can be ignored?

---

### Post by h0bbe on 2005-08-04
Your way of doing it OneSeventeen solved my problem too! Now I'm also a happy Ubuntu user :-)

I didn't check what went wrong though and are still wondering how many others who give up on Ubuntu because of this!? There are a whole lot of forum threads out there on this problem and the most common reply is "sounds like a bad CD!". I'm not sure that's the explanation and hope the Ubuntu team correct it for the next release.

---

### Post by bturner45 on 2005-08-15
Hi folks,

I have the Warty pressed cd's. The 'Live' cd boots just fine on my system, i have a emachines W3052 with xp-sp2, 512mb ram, 120gb hdd, dvd+/-rw, amd sempron 3000+. no way should this be happening. i have not had the machine a month yet. the xp side of things works fine. i hate xp... just really want to run linux and can't seem for the life of me to find one that works...

the cd's i am using are 'pressed' cds. i ordered them a while back. was a really happy camper when it came in. didn't have a computer then. now i have a computer but the linux doesn't seem to want to work.

it boots up, goes to the first screen about selecting your keyboard. it has english which is fine as i am in the u.s. i hit enter. nothing. the keyboard is not being recognized. the system is frozen tight. i have to power off to get things going again.

i d/l'd the newest version, burned it down, same story.  i d/l'd debian, same story.

i have in fact d/l'd several 'debian-based' distros and all have the same problem at the same spot, which leads me to believe it is a problem in the debian installer itself, rather than the particular distro.

would really appreciate a bit of help here. if i can't get this to work soon i am just gonna blow linux off. i've just about reached the end of my patience. ms might be 'evil' but at least it works flawlessly with my setup. i don't like ms. i hate them to be brutally honest. it was on the new pc when i bought it.

save me... please...


[QUOTE=h0bbe]Your way of doing it OneSeventeen solved my problem too! Now I'm also a happy Ubuntu user :)

I didn't check what went wrong though and are still wondering how many others who give up on Ubuntu because of this!? There are a whole lot of forum threads out there on this problem and the most common reply is "sounds like a bad CD!". I'm not sure that's the explanation and hope the Ubuntu team correct it for the next release.[/QUOTE]

---

### Post by Thunderguy on 2005-11-16
bturner45,

                 I'm on an Emachines W3050, I think the only difference between our systems is you have a larger hard disk, anyway, I had the same problems you did and figured out exactly what is causing them.  Our systems have a thing called USB Mouse support, what this really seems to do, is detect USB peripherals and set them up for PS/2.  When you turn on the system that numlock state is lit, and something messes up when configuring the keyboard,  I believe this is just a simple mis-understanding between the kernel keyboard drivers and the Bios, there is a way you can fix this ( I'm in Ubuntu Breezy right now. ) Go into your Bios, it may be under advanced options.. I'm not quite sure, Disable your USB Mouse support.
              
        Afterwards you should find the kernel detects the keyboard just fine.. There is another problem I should point out when installing Ubuntu on these types of systems.. type expert at the boot prompt, I don't know why but the system freezes on setting up 'apt-get' You would want to skip that step by using the expert mode (it would later ask you to write your own sources.list, but this is fairly easy as the stuff is already in there). Then the system should install fine, just be careful to read all the directions in the expert mode install ( as the default is usually to wipe your drive, if you want to keep existing files.. I highly suggest editing the partition table yourself), and you may not have sudo capibilities it would install a 'root' account for expert-mode, but these are the work-arounds I found for installing Ubuntu. On another note I would pay attention to the hosts file, I had problems with Gnome loading slowly on the default install.. I'd be glad to help further if you send me anything private on the forum.

 -- hope all goes well with your system as it did for me!  but incase it doesn't, don't forget to write your emachines restore cd's as incase things go terribly wrong (usually via pebkac issues if you don't read everything)... Then you can always have atleast something to recover back to, Cheers!

---

### Post by jfreak on 2005-12-03
i have an old hp brio and the cd stalls during "installing the ubuntu base system"
but it sometimes stalls before during "Loading additional components"
the live cd only works half of the time, never stalling in the same place

i've tried:
     restarting the instalaion saying no to the PCMCIA stuff
     continueing with copying extra packages
and neither worked :confused: 

i've tried two burnt instalation cd's (one copied from a shiped cd and one from an iso immage) and the shiped instalation cd.  They all are exactally the same.

---

### Post by bunty on 2005-12-07
Have any of you guys actually checked the md5sum on the image you're burning?

I have just downloaded the dvd iso image for the second time (10h worth) only to find that the checksum fails.

I dont know what is going on on these servers but last time the file that started as being 2G endded up as 2.9G , today it was back to 2G , one continuous download but the md5 fails.

I dont know someone is playing with modifying the iso without changing the files name , the md5 are out of date or what , but for me I've had enough of this farce.

Pathetic.:confused:

---

