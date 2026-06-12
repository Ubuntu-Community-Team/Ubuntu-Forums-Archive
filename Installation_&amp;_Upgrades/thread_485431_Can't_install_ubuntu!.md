---
title: "Can't install ubuntu!"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by arnab on 2007-06-26
I've the following configuration

Intel Pentium D 3 GHz
Intel Original G965RY Motherboard
1GB RAM
160GB HDD
SONY DVD Writer

When I try to install Ubuntu 7.04 it's shows boot screen. After selecting install ubuntu it shows 'uncompressing linux... booting......". But after that nothing happens. :( Please help.

---

### Post by merlinus on 2007-06-26
Try Safe Video Mode, or the text-based Alternate Desktop install cd.

-merlin

---

### Post by scuba_suit on 2007-06-26
arnab i'm having the same problem, gotta dell p4 2.4ghz 256RAM, i just put in a 40gb hard disk that i used on my other pc, it wasn't the master, anyway i put in the cd and choose "start or install ubuntu" and it's starts loading in the linux kernel but then nothing, the screen goes black, merlinus i'll try your advice and see of that'll work and get back to this thread...

---

### Post by scuba_suit on 2007-06-27
arnab, have you tried rebooting like merlinus said? i'm not near my pc to do it, gave up last night, do i have to put in a special command in the line on the bottom below the boot options? i'm using a hard disk that i had before on another pc and understand that all the information could be wiped out (don't care, i want ubuntu), should i just buy a new hd and put ubuntu on that? ugh, i want ubuntu NOW!!!:o

---

### Post by merlinus on 2007-06-27
I used the Alternate Desktop text-based install cd for a 5-year-old Compaq with 256MB RAM and a 1.09GHz processor.  Worked great!

-merlin

---

### Post by brunovalentino on 2007-06-27
Had the same problem, with a Presario F500

Try this,

When starting up, where you have to choose if install Ubuntu or load from hard disk, press F6 and add "noapic irqpoll noirqdebug" (without the "), and then press enter.

Worked for me, hope it works for you. Good luck and dont give up!

---

### Post by scuba_suit on 2007-06-27
well here's the shlameel and the shlamazel so far: 

when it's at the install (first) menu, at the bottom after i press F6 i get this:

Boot Options :file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --

now, my question is when i put in the boot parameters, do i erase all that ('Boot Options' doesn't erase) then type in "noapic irqpoll noirqdebug" then hit enter? do i put in "boot:" after Boot Options?  it starts loading everything in until i get these lines at the bottom of my screen and the pc locks up:

[  187.350590] Kernel panic - not syncing: VFS: Unable to mount root fs unknown - block(104,1)
[  187.350646]

OR


[  156.053701] Kernel panic - not syncing: VFS: Unable to mount root fs unknown - block(104,1)
[  156.053757]

huh? robot no understand, what does it mean? does it have to do with the hd? i have a dell dimension 2400 and the hd i put in is an ATA hd 40gig, merlinus how do you get the Alternate Desktop text-based install cd? is it on the live cd? or do you have to request it from the site? oh and as for my hd, the jumpers are set so that it's on "master w/ slave present" but it's the only hd (but will add another hd down the line) can that also have an effect on how this is affecting the install? should i set the jumpers on "master only"? uuuggghhhh calgon take me away....

---

### Post by merlinus on 2007-06-27
Add those to the end of the boot parameters.  And it may still not work.

Once again, I suggest trying the Alternate Desktop install cd.

And.... are you the shlemiel or the shlemozzel?

;)

-merlin

---

### Post by scuba_suit on 2007-06-27
at this point i'm hassenfeffer incorporated, but i guess i'll keep trying, i'll request the Alternate Desktop cd though... if there are any other suggestions please drop some science on this conundrum of a pickle... actually i just went onto the main page for ubuntu to request another cd, but there is no Alternate Desktop text-based cd, is it on the cd i already have?

---

### Post by merlinus on 2007-06-27
You can download the Alternate Desktop install cd at:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, and then click the text to start the process.

After downloading, it needs to be burned as a disk image, not a data disk, and at a slow speed (~ 4x).

It is text-based, and so you will not have what seem to be the video problems you are experiencing.

Please continue to post with problems or questions -- that's what this forum is all about!

-merlin

---

### Post by Gutts1979 on 2007-06-27
Hi everyone im new to ubuntu and am trying to install it on my new computer.
I have a core2Duo 6400, nvida 8600Gt, 1Gb Ram, a 320 Gb sata hard drive 

ive tried countless time to install ubuntu but come up with this everytime




ata 7.01: failed to set xfermode (err-mask=0x4)
buffer I/O error on device fd0 logical block 0


                                                                                                            (this runs down the page the ends on)



BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built in shell (ash)
Enter 'help' for a list of built-in comands.

/bin/sh: can't access tty; job control turned off
(initramfs)






Can anyone help at all?

          Thanks.

---

### Post by merlinus on 2007-06-27
Have you tried Safe Video Mode?  Or you can download the Alternate Desktop install cd, which is text-based.

Once installed, you can get the drivers for your NVidia card in this fashion:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Good luck!

-merlin

---

### Post by scuba_suit on 2007-06-28
merlin, you gotta walk me through the Alternate Desktop download and installation, you said to dl it and then burn it on a cd as an image not as a data disc? i think i have roxio (i gotta laptop that i can do this on) that when it asks what kind of cd i will be making it either asks me if i'm makin an audio or data disc, so i would assume choose data right? and then how do i save it as an image? lemme know so i can go lenny and squiggy on it....(yes, i'm sticking with ending my replies with laverne and shirley references)

---

### Post by merlinus on 2007-06-28
If you select data disk, there should be an option (look in the File menu) to burn a disk image.

I do not have roxio anymore since i hissed remond bye-bye.

You can, however, d-l infrarecorder, freeware burning software with that option.  I have used it to burn disk images.

[http://infrarecorder.sourceforge.net/](http://infrarecorder.sourceforge.net/)

Keep those cards and letters coming....

-merlin

---

### Post by scuba_suit on 2007-06-28
well i dl'ed the Alternate Desktop cd, and burned it, now how i do i run it? remember, the pc i'm installing to does not have an os, i'm trying to install just ubuntu on it, when i put the AD in and start the pc, i get a message saying that it doesn't recognize it and just gives me the F1 option to reboot it or F2 to enter setup, but i've been trying to install with the live cd, but i keep getting these "Kernel panic" messages about the "fs root" and that there is an unknown block, could it be the connection to the hd? now i'm feelin like laverne's dad, mr. defazio...

---

### Post by merlinus on 2007-06-28
Did you burn the cd as a disk image and NOT as a data disk?  Sorry for asking again, but often folks make this mistake inadvertently.

If you look at the contents in windows, it should show folders and files, and not just one file.

Did you burn it at a slow (4x) speed?

Can you try to boot it on another computer?

-merlin

---

### Post by scuba_suit on 2007-06-28
yep burned it as an .iso image at x4 writing speed, the pc i'm trying to boot it to doesn't have any os,i'm going to try on another pc...

---

### Post by lisati on 2007-06-29
I can appreciate your frustration.  For my laptop with a CDRW/DVDROM drive I spent a lot of time mucking about with the live CD and the alternate CD without success. I ended up burning a copy of alternate CD ISO image onto a DVD and installed from that, no hassles. Weird, but it worked.

---

### Post by scuba_suit on 2007-06-29
this is what i'ce done so far: made the Alternate Desktop cd, burned the image (.iso) onto a cd, but when i pop in the cd into another computer, it starts to read it as an audio file (windows media player opens up, WTF!?), i did it on roxio and from the file menu there is an option to burn it into an .iso image but i'll dl infrarecorder and do it again i guess, i'm hittin those "Kernel panic" messages when i do put in the boot parameters, the AD disk, is that only good on pc's with os's like windows? cuz i'm starting from scratch, pc with NO os.... oh yeah, uh, laverne and shirley ref, okay i got it: i'm feelin like the big ragu, like carmine cuz ubuntu is makin me dance in circles...

---

### Post by merlinus on 2007-06-29
Look at the contents of the cd in windows explorer.  If for some &*^%$# reason it opens media player, shut that down.

If you do not see a bunch of folders and files, then it did not burn as a disk image but as a data disk.

The install disk will run on just about any machine.

Keep on dancin'....

-merlin

---

### Post by scuba_suit on 2007-06-29
yep, i tried installing it on my wife's pc, no dice, i guess her pc is too old (333mhz p3),i guess i gotta check the pc first, just to make sure the IDE cables are not messed up, check the jumpers on the hd (i'm just settin to 'master' and when i get another hd, i'll deal...) then burn another AD disc and this time use infrarecorder, when i told people that this'll be my summer project, i didn't think it was going to turn into a PROJECT....

---

### Post by scuba_suit on 2007-07-05
well here we go with the ongoing saga of installation: okat i checked out all the IDE cables, fine, took the jumper off my hd so that now it's only a master, i start loading in ubuntu with the "boot: live noapic nolapic" parameter (as it's the only one that i feel like i get close to installing) but i keep getting the "unknown block (104,1)" message that's stopping the installation and freezing up my pc, what IS "block (104,1)"??? and why is it stopping me from installing? WWHHHYYY? oh yeah, should my hd be clean with nothing on it, reformatted in order for the install to go through?

---

