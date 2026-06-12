---
title: "TV-output ONLY - how to do that?"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by Thanh-BKK on 2008-05-26
Hello :)

So now i have Hardy running perfectly on one and almost perfectly on the other computer. And i just remembered that i have a THIRD computer lurking around - it hasn't been used in ages because it's primary function - recording TV programs - stopped working days after being implemented under XP.

Now i want to try if Ubuntu can get it back working :)

Needless to say that machine is a barebones machine - Compaq Deskpro EN, modified to have a 900 MHz Celeron, 512 MB RAM, 4 USB 2.0 ports instead of the floppy drive and a PCI graphics card (!) ATI with TV out. 

And herein lies the problem.

That machine is connected to the TV and ONLY to the TV. It has neither keyboard nor mouse as the video recording function could be activated via a remote control that came with the TV tuner card. 

I can plug in a mouse and keyboard via USB, however - no monitor. 

Is it possible to get Ubuntu installed so that indeed ONLY the TV-out is active, i mean - is it able (like Windoze) to detect that the only display is a TV? 

Please tell me "yes"..... it's the last non-Ubuntu machine i own and i want to change that :)

With best regards......

Thanh

---

### Post by Thanh-BKK on 2008-05-28
*bump*

Anyone with an  idea?

Thanh

---

### Post by rich86 on 2008-05-29
Yes it is possible once it is installed to change the xorg.conf file to that the output will only be on the tv. I am not sure though if you can install without having a proper monitor plugged in.
If you are just using this as a tv PVR computer then you might want to consider mythbuntu ([http://www.mythbuntu.org](http://www.mythbuntu.org)), is it speciffically designed for what you seem to be after. You can add most of the Ubuntu packages to mythubuntu if you require any other packages. You could also install Ubuntu if you prefer and add some of the MythTV features and some of the Mythubuntu packages.
Hope that gives you some help.

---

### Post by Thanh-BKK on 2008-05-29
Hello :)

I have already been looking at Mythbuntu - but i got confused with the requirements for "Backend" and "Frontend" and whatnot...... also it's requirements for the hardware (3 GHz!). Mine is only 900 MHz...... plus it asks for some sort of registration or code for Myth-TV which i don't have. 

However i am facing another problem with that machine - i can't get it to boot from CD! When i press F10 as advised to get into the BIOS, nothing happens and it just continues booting to XP. Stupid Compaq - apparently they require a special floppy to get into the BIOS, however the floppy drive has been removed to make room for the front USB sockets...... guess i'm screwed with that machine (as it has special cables to hook up a floppy drive, which i don't have, i can't just plug one in... everything is special on that model, except for the friggin' CD drive, but the cable for that one is special again with small connector). It's a Compaq Deskpro EN "small form factor". 

Best regards....

Thanh

---

### Post by rich86 on 2008-05-29
Thats a tad annoying, i have one or two ideas that might be worth a try. Have you tried any other common keys for getting to bios, such as Esc, F8 and End , its quite strange that you cannot get to it at all. Is it set up so the first boot device is the 1st hard drive? if not can you make a usb boot device? Some systems have a utility that you install from windows to edit bios settings, it could be worth looking on their website....i did just have a look and the updates seem to require a floppy disk. Do you have a spare floppy drive kicking around or in another computer you could swap in just to get it working? There is WUBI as well so you can install Ubuntu 8.04 from windows which will let you see if what you want to do will work.

As for the MythTV frontend backend thing: The mythtv wiki may provide some information, Backend: [http://www.mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Backend](http://www.mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Backend)) and Front-end: [http://www.mythtv.org/wiki/index.php/Front_End](http://www.mythtv.org/wiki/index.php/Front_End)
Basically the backend is the bit that does all the hard work (generally where the tv tuner is plugged into) it does the recording and decoding from the tuner. You can have multiple backend's having each one do a different job, such as transcoding or advert flagging (there require more CPU power).
The Frontend is the bit that you see, this shows the tv picture (by accessing the backend) it access the backend for the recordings and other features you require. You can also have multiple frontend on a network so that you can watch tv on more than one computer (with each one connecting to the backend for the content). (this does not require as much CPU power)
It is possible to have both the frontend and backend on one computer or separately on a network.
Think that makes some kind of sense. Just the challenge of getting Ubuntu on the computer first!
Hope you manage to find a way to eradicate windows from your home!

---

### Post by Thanh-BKK on 2008-05-29
Hi :)

Indeed it looks like i am kissed with that Compaq. It appears i really need to download some program from Compaq to create a floppy to boot from to get into the BIOS. 

Having a flopyy drive is no issue - i have a couple lurking somewhere. But i don't have that special Compac floppy connector cable! As the mainboard has not a single standard connector, they are all some specific "slimline" or "micro" kind of connectors. The CD drive even goes to a flat cable like the one that connects laptop keyboards... so weird, that computer. 

It would probably be able to boot from USB, but guess what - i need to get into the BIOS to enable that..... back to square one :) Right now it absolutely boots only from HDD (and maybe floppy, which i can't test). 

And yeah, it's F10 because when i start the machine, it does show "press F10 to enter setup". When i hit F10 then, it displays for a second "Compaq Setup" but then goes on to boot Windows. I tried a million times, always the same.

Time to donate that thing to a kindergarten and get a decent video recorder computer that's able to run Ubuntu :)

Best regards.....

Thanh

---

### Post by rich86 on 2008-05-29
Yeah the out look doesn't look good with that computer. If you want to keep it though an final posibility is taking the hard drive out putting in in another computer and trying to install grub on it from a liveCD. You could also put the liveCD on the hard disk then maybe boot from that. I have manged to make a LiveRAM session before so it might be possible. Depends whether you can be bothered to spend the time on it!
Good luck if you do try!,
Richard

---

### Post by Thanh-BKK on 2008-05-30
Hello :)

Thanks again for replying. I have been googling around that issue for a while (slow day at the office) and now i am wondering about something.

is it possible to initiate an Ubuntu-install from within Windows? No, NOT Wubi but a regular install that will partition the HDD and wipe out Windows. 

I found that apparently older Ubuntu versions (Edgy?) had an add-on called "install4win" or similar which did just that. However i couldn't find any info if Hardy does, too. It was/is for the precise purpose of enabling people w/o BIOS access or knowledge to install Ubuntu. While i do have BIOS knowledge, i don't have access to it :)

Or can i use Wubi to install Ubuntu within Windows, then boot into Ubuntu and simply delete all the Windows files? Does Wubi require a WORKING Windows? 

I guess i would already be happy if i could start the live CD within Windows and then take it from there....... 

(That poor little computer was looking at me asking "when will i get Ubuntu, too?" and i want to end this pain for him)

By the way on the second one i managed to get that kernel upgrade in without issues, and tweaked the KDE part of the system to really kick ***. I wish XFCE would work (some sort of already-known bug), then i had them all three on one machine. On the main computer i disabled all updates now - machine runs without the slightest flaw, i rather keep it that way :)

Best regards.....

Thanh

---

### Post by rich86 on 2008-05-30
Turns out it is possible, i have not done it myself but seems pretty simple: [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

It looks like you change the windows boot loader to load a dos-grub that loads the linux kernal, you then have the choice of either running the installer from an image, cd, or network install. You might need to change a few things to Hardy from Gustsy and it looks like only the alternate CD will work.
It might be work using Xbuntu on that machine anyway thinking about it, you can still run things like MythTV it just uses much less resources so will run faster on that computer. I have it running on a crazy old laptop it still takes 1min to do a full boot, but windows takes literally 5-10 mins...

In regards to updates, it might be a good idea to check to see what updates are available from time to time as if it is an internet connected machine important security updates may become available (hate to bring it up again but for example the pretty major SSH security error found a few weeks ago). You can always duplicate the install you have on another partition to use as a test bed before updating your main build.

Good luck with that method,
Richard

---

### Post by Thanh-BKK on 2008-05-30
Hi :)

Thank you very much for the reply, i appreciate it. I will see if i can get the alternate CD downloaded next Monday (i do that at the office - faster line!) and if i can start from there...... if i only get the Live CD or the installer started, the rest will run by itself :)

About the security updates, i am afraid to say that i am not the least bit scared of getting hacked - i have zero important things on the computer that a potential hacker would be interested in, i don't do online banking or purchasing and i smell phish when i receive a phishing e-mail...... in 11 years Windows i had a single virus (!!!) and zero adware, malware, spyware or similar...... so, honestly, i am not too concerned about "security holes". 

And i DO run manual updates from time to time, so if i see something that doesn't directly affect the system (such as a new kernel or key application that i use daily) i do install it. Just no more daily nagging "there's 59 updates, 3 of which may make your next reboot an adventure". I have seen (and read about) that plenty..... and i am too much of a n00b to be confronted with a white, blinking, cursor on otherwise empty black background when i need to get work done. 

And i want to keep that Vista DVD inside it's beautiful package :)

With best regards.....

your Thanh

---

