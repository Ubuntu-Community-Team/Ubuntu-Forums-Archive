---
title: "I Cant Install Ubuntu"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by DeadThug on 2010-08-09
i had ubuntu on my old computer, but i got a different computer now and i want to switch to ubuntu as my main os. but i wanted to dual boot windows and ubuntu. so i partitioned a drive from the drive i have windows on. i then tried using wubi atleast 6 different times. 3 for live cd and 3 for right away download. i get to a screen where it is a purple background and the ubuntu logo is there with 5 dot alternating from red to white. then after about 3 minutes of waiting it just stops. on the next couple of times i left it there, thinking it just needed some time. but i left it for 6 hours straight and nothing happened. so i used my old 9.04 disc that i got from ubuntu away ago, and the same thing happened. so then i downloaded ubuntu 10.04, burned to a disc and the same thing happened.


i have a 
gateway desktop
pentium 4 cpu 2.00GHz
1 gb of ram

---

### Post by corrytonapple on 2010-08-09
Does Windows work? Could be a Hardware issue.

---

### Post by DeadThug on 2010-08-09
yes, windows works like usual.

---

### Post by corrytonapple on 2010-08-09
Do other CDs work in the drive (Of anything)? If none work, then your CD drive is dead. If they do, download the alternate install CD. The interface is easier on the graphics.

---

### Post by Otu on 2010-08-09
I'm having same kind of issue, also when i have installed 9.10 or 9.04 and upgrading to 10.04 it wont boot at all to ubuntu tried to install ubuntu 10.04 clean from several cds as well as usbstick, when installing it so, it complains some files not found every time, got it to boot to 10.04 once but then restarted and it would do same as all the other times, whats wrong with ubuntu 10.04???

---

### Post by DeadThug on 2010-08-09
yea, my cd drive works. im thinking about trying out xubuntu. anyone have advise for that os?

---

### Post by corrytonapple on 2010-08-09
> **Otu said:**
> I'm having same kind of issue, also when i have installed 9.10 or 9.04 and upgrading to 10.04 it wont boot at all to ubuntu tried to install ubuntu 10.04 clean from several cds as well as usbstick, when installing it so, it complains some files not found every time, got it to boot to 10.04 once but then restarted and it would do same as all the other times, whats wrong with ubuntu 10.04???
Does it look like this?:
[http://ubuntuforums.org/showpost.php?p=9697900&postcount=3](http://ubuntuforums.org/showpost.php?p=9697900&postcount=3)
> **DeadThug said:**
> yea, my cd drive works. im thinking about trying out xubuntu. anyone have advise for that os?
Xubuntu will run fine on your computer. It will run better than Ubuntu actually. Did you try the alternate install CD?

---

### Post by Otu on 2010-08-09
Sorry, cant remember, its been weeks since i tried.. will try soon again and post what it says exactly..

---

### Post by DeadThug on 2010-08-09
where do i get the alternate cd? im download xubuntu now, if it doesnt work, ill get the alternate cd.

---

### Post by corrytonapple on 2010-08-09
Here:
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate)
Then click the list of download locations and choose one nearest to you.

---

### Post by DeadThug on 2010-08-09
i just tried xubuntu, but the same thing happened but with the xubuntu logo

---

### Post by Otu on 2010-08-10
Ok good news, I'm now on ubuntu 10.04, first tried to install from normal cd and that didnt even start to install, but thanks to Corrytonapple I made alternate boot cd just to be sure, and it worked perfectly, i also got picture of what happened with the normal cd and i guess it might be good to show to you people but how do i get it here??

just hoping this will now keep working as good as now :) didnt like fedora 13, too little programs in packet manager and im too noob to compile anything :(

---

### Post by corrytonapple on 2010-08-10
Try the alternate CD like Otu did.

---

### Post by DeadThug on 2010-08-10
alright, ill try it now.

---

### Post by DeadThug on 2010-08-25
it didnt work.

i tried doing it and it messed up my xp. took a week just to get xp installed again. i ordered a disc from ubuntu and that didnt work either.

---

### Post by GenBattle on 2010-08-25
Try editing the grub entry (F6 on boot) and removing "splash" and "quiet". If this doesn't work by itself, try adding "xforcevesa", "acpi=off" or "nomodeset".

This got the standard live CD working for me (after weeks of frustration). There's also a "i915.modeset=0" or "i915.modeset=1" option that works for problems with some intel graphics chipsets.

---

### Post by dFlyer on 2010-08-25
Check your sectors on the hd with some other program other than from MS. I had a computer that kept failing and hanging on install. Windows said the HD was good. After I downloaded the HD system utilities and tested it. It showed multi sectors screwed. Replaced HD and ubuntu installed without a problem.

---

### Post by roy913 on 2010-08-26
i intuitively suspect this is a kernel compatibility issue. Have you tried downloading LiveCDs with different kernels to try. To be eco-friendly and cost saving, instead of burning LiveCDs, you may want to build LiveUSB by UNetbootin. Sometimes older kernels mythically work better than the newer ones during installation.

---

### Post by roy913 on 2010-08-26
if "Alt + F1" is still responsive to give you system messages while booting, please post them here.

---

### Post by DavidOfLondon on 2010-08-26
You've got lots of options. Have you checked your capability to boot from a USB mem stick? (See Ubuntu page install instructions)

A very common problem is the failure of certain files to be written to the ISO image CD because the record speed is too high. 

Make a new CD and this time be sure to turn the burn speed right down as low as it can go. Everyone is in a rush to create speedy burns that are actually missing files.

If you put the CD in and nothing happens but other discs DO work then clearly the problem is the disk.

Follow Ubuntu's install instructions to the letter, being certain not to save a Windows 7 install image when you're using Windows XP, for example.

If you CAN install from an image burnt to the USB then do it. 

All the options saying "Show Me How" here - [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Should be closely examined.

Good luck,

David.

---

### Post by corrytonapple on 2010-08-26
> **DeadThug said:**
> it didnt work.

i tried doing it and it messed up my xp. took a week just to get xp installed again. i ordered a disc from ubuntu and that didnt work either.
Why it would mess up XP I don't know. Sounds like you got GRUB to work. You did not have to reinstall XP. You could just have posted here and we could reverse it.Try another Linux distro. I am just out of ideas.

---

### Post by DeadThug on 2010-08-26
i tried 5 different versions of linux and none worked. im giving up on linux and sticking to winxp. at least it works.

---

### Post by corrytonapple on 2010-08-26
What were they? Try Mint:
[linuxmint.com]("http://ubuntuforums.org/linuxmint.org")
Try Debian:
[debian.org]("http://ubuntuforums.org/debian.org")
Or try Lubuntu:
[lubuntu.org]("http://ubuntuforums.org/lubuntu.org")
Try looking here for your perfect distro:
[distrowatch.com]("http://ubuntuforums.org/distrowatch.com")
Remember to use a USB stick for the earth's sake.
I would hate to see you go. I might have already said it, but maybe your CD burner is bad or you CD was bad. Could you Hard Drive be failing? It will make unnatural sounds.
Please do not leave if there is an alternative.

---

### Post by DeadThug on 2010-08-26
i tried the first two you listed including fedora, xubuntu, and kubuntu.

i tried 3 different cd/dvd drives

i also tried 4 different hard drives.

---

### Post by corrytonapple on 2010-08-26
I must say it is a kernel issue. You can make your own, but you need experience doing it. I am dearly sorry to see that Linux does not work for you. Try distrowatch and see if there are any that aren't Ubuntu based.

---

### Post by DeadThug on 2010-08-27
whats kernal?

---

### Post by corrytonapple on 2010-08-27
It is what your system runs on. See Wikipedia:
[http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)
Is the CD 32 or 64-Bit? I would use 32-Bit. Please do use a thumb drive so you don't waste CDs.

---

### Post by DeadThug on 2010-08-27
if i could find the usb drive i would.

i ran out of cds a while ago, but ive just been erasing some of them to try again.

---

### Post by corrytonapple on 2010-08-28
So they are CD-RW. They are not as good as you could have left over files after they are wiped. Anyway, 64 or 32 bit? This I think is the problem.

---

### Post by DeadThug on 2010-08-28
32

---

### Post by corrytonapple on 2010-08-28
I would think that would work. If 32-bit does not work, then it is a kernal issue with 32-Bit. Try reburning the 32-Bit CD again. Could be a bad CD. I still would not try 64-Bit. You might have some more hoops to jump through using it than I think you want to put up with. I use it though and it works fine.

---

### Post by DeadThug on 2010-08-28
ive tried using 32 bit and it doesnt work. i think im just going to try out lunar linux? you know anything about that?

---

### Post by corrytonapple on 2010-08-28
I understand, but your cd could have bad blocks. Never heard of Lunar Linux. Link please and I might see if it works on your system.

---

### Post by DeadThug on 2010-08-29
i used 4 different disks to burn the iso and have gotten 2 disks from ubuntu. i doubt the reason that it isnt working is because solely on the cd.

---

### Post by DeadThug on 2010-08-29
oh and link for lunar linux

[http://www.lunar-linux.org/](http://www.lunar-linux.org/)

---

### Post by corrytonapple on 2010-08-29
> **DeadThug said:**
> i used 4 different disks to burn the iso and have gotten 2 disks from ubuntu. i doubt the reason that it isnt working is because solely on the cd.
You can doubt correctly. I do agree with you.
> **DeadThug said:**
> oh and link for lunar linux

[http://www.lunar-linux.org/](http://www.lunar-linux.org/)
Thank you. I am checking to see if it works now.

---

### Post by DeadThug on 2010-08-29
thanks

---

### Post by corrytonapple on 2010-08-29
Looks a bit technical. Try looking here? What do you use the computer for? That will help me help you find a Linux distro that is not based on Ubuntu. Ubuntu is based on Debian so I am unsure if it will work. Very stable, lots of software, good for old computers. Great all around.

---

### Post by DeadThug on 2010-08-29
im looking for something for day to day use. im just getting sick of windows. but its the only thing working for me.

---

### Post by DeadThug on 2010-09-09
just to give everyone an update, ubuntu is installed and working perfectly. i dont know what happened or what i did, but its working.

thanks corrytonapple for all your help


now i just need helping customizing it and switching from windows.

---

### Post by corrytonapple on 2010-09-09
My specialty. See my complete Ubuntu customization applications and ways to customize here:
[http://ubuntuforums.org/showthread.php?t=1545480](http://ubuntuforums.org/showthread.php?t=1545480)
Glad to see that it works. Now if you are going for a Windows look you should go for KDE by installing it via sudo. If you need help with that, just start a new thread and tell me so here. I would stay with Ubuntu for a while and see how it feels when you are done customizing.

---

### Post by DeadThug on 2010-09-10
ok thanks.


i have encountered one problem though. it has shut down 3 times and froze up. on all 3 times i can remember installing lots of stuff at a time. should this not be done or what? im used to windows freezing if i do too much stuff but it never shut down.

---

### Post by corrytonapple on 2010-09-10
Did it go in a cycle of shutting down? Did it restart? Did you turn it off? What was it freezing on? What are you trying to install and from where? What if I............. no, just messing with you. :)

---

### Post by DeadThug on 2010-09-11
lol. its hasn't happened recently and i think thats because i haven't been doing like 15 things at a time with it.

---

### Post by corrytonapple on 2010-09-11
Interesting how that works, huh? :)

---

### Post by DeadThug on 2010-09-11
yep. lol.

---

