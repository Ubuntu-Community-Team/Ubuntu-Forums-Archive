---
title: "My Ubuntu experience so far"
date: 2006-09-06
forum: Installation &amp; Upgrades
---

### Post by gollyg on 2006-09-06
I read an article in the sydney morning herald about the new usability of linux, and it mentioned ubuntu in particular. This was enough to rekindle my interest in Linux. I have dabbled in the past, but never really got into it. Perhaps now was the time.

I navigated to the ubuntu site and was immediately impressed by the clean site and relative simplicity of the navigation. There were brief descriptions of various installs, and an nice online documentation area which I read reasonably throroughly. 

Seeing as I was looking for a webserver and file server I chose the server install and downloaded and burnt the cd. I installed it without a hitch. Except that the server version didn't install with a graphic interface. No problem, it was easy to find instructions on installing the desktop, which I followed. 

Restart the system and first problem - the "no screens found" error. Googled it, found a post on this forum explaining what had happened and how to fix it. Followed the instructions but still no graphic interface.

Perhaps this is all to do with the server install (the screens issue was said to be). Downloaded the desktop version with plans of installing the extra packages I needed. Insert the cd - yay - graphics. Choose to install ubuntu. Now we are really going places. Well, not really. Install hung on the second line - mounting root folders or something like that.

Back to google - found that this is a documented issue. Followed the various fixes. No good. No luck. No progress. Well at least there is always the alternate cd - a text based install. 

Download the alternate cd, burn it, start the install. Yay. Past the first hurdle - it asks me a few details about my location and keyboard. Things are happening this time. They're really happening. Or are they - hasnt that screen been blue for a really long time? With no writing on it. and no cd access.

I fear that my 2 days spent trying to load ubuntu are coming to an end, and without spying that lovely graphic interface. 

I will probably give up for now, and try later. But the promises of the interviewee on the sydney morning herald site of a relatively painless install process rang a little hollow.

This is not a complaint about a product that has been provided. It's free for god sake. How could I complain about that. Furthermore, I have not given up on ubuntu - I will try to install it when I get some more free time. The forums seem helpful, the community supportive.

I guess I really wrote this because its a new users experience of this software, and hopefully it will help to improve it. 

Thanks for your attention.

---

### Post by wieman01 on 2006-09-06
I understand that this has been a frustrating experience, but perhaps there is still a chance that it turns out to be a pleasant one... 

If I were you, I'd format your entire harddisk (or at least the Linux partitions) and re-install the Desktop version. This is not a promise but it's very likely that this will work for you. 

Just a thought... Would you be happy to welcome you to our little (though growing) community.

---

### Post by Inhumane on 2006-09-06
I've had the same problem, if you're using a 3D card other than the built in one, that's what happens. What I first did was try connecting my monitor to the built in card (first enabling it from the BIOS), it worked, then I reconnected, I said Yes to diagnose the problem and it showed me all those errors, within those you should try looking for PCI: x : x : x or AGP " " and replace them with the values showing, then do sudo dpkg-reconfigure xserver-xorg and follow the instructions, select the card, but this time also type in the PCI/AGP: x : x : x. It should then work:)

---

### Post by gollyg on 2006-09-06
Thanks for the responses. I did try completely erasing my hard disk, then partitioning it and reformatting it. Same problem - hangs at the same place.

I am not using what I would consider exotic hardware - an intel 845 GBV board, intel 2.4 processor, one seagate drive, one ricoh cd drive, all hooked onto the primary ide. Using onboard graphics chip (perhaps the problem?). During this time i have progressively disabled everything I could including Secondary IDE, floppy controller, AGP graphics, onboard sound, serial and parallel ports and USB.

still zip.

I have also run the knoppix live system on this computer without issues.

Arghhh. wouldn't be so bad if I didnt really want to use ubuntu!

---

### Post by wieman01 on 2006-09-06
Really surprising that Ubuntu is such a hassle. But yes, Knoppix is the best distribution when it comes to recognizing even "exotic" hardware. However, it's disturbing that your hardware is so much of a headache since my onboard graphic card (Intel 855) is not problem at all.

Oh well, Ubuntu is not perfect. Hope it will continue to make progress in that respect.

---

### Post by gollyg on 2006-09-06
uhoh. reading another post about the same hanging issue led me to remove some pci devices as recommended. This did not resolve the problem, but whilst in the bios I disabled some options - one of which was the fast boot option. This meant that it was actually checking things before booting. At this point I got the dreaded hardware beeps and a RAM error message. 

Funny, because the system had been successfully running Windows 2000 the day that I decided to upgrade. Not only that, I was able to install the commandline version of ubuntu server. But this is definitely a potential issue!

Will replace the ram and post back.

hopefully I will be ubuntuing soon.

---

### Post by gollyg on 2006-09-07
Memory issue was to do with bios settings that i had changed. However, i noticed that when doing a text install it was hanging when detecting the cd rom drive. Wierd, considering it was actually running off that drive! but changing the drive got me past that point. I now seem to be stuck at a different point with a few errors being generated, but at least something different is happening.

perhaps, perhaps, perhaps.

---

