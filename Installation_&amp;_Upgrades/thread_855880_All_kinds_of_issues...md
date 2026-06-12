---
title: "All kinds of issues.."
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by vistauser on 2008-07-10
This will be the fifth time im my lifetime that I have attempted a linux install.  Every time you ever mention you're running Windows you get scoffed at on the internet and told to install linux.  However, I have never been able to get anything working in linux.

On a fresh install of the latest version of ubuntu; here are my current most important issues:

1: Mouse cursor doesn't move diagonal unless you move it quickly.  If you move it slowly, you can only move horizontal or vertical.  This mouse functions fine in Vista and is a logitech g9.

2: No drivers for any device loaded, nor will it let me load any driver for any device.  Always tells me that the device isn't installed.  I have followed guides posted in several places, that are never the same which is odd, and none of them worked.

On #2; For instance, the Nvidia drivers.  If I go to hardware drivers the list is empty.  I download and use root to sh <drivers> and it attempts to install and then tells me it can't find any devices to use.  The video card in that machine is an 8800gtx.

I just don't get why everyone bashes on Vista so much.  Super easy to install, zero issues.  Download a driver and bam its working.  Everything is so smooth and I don't have to use commands to edit files in some deep directory with code that makes no sense to me.  Can find and download pretty much any kind of software and have it running without doing anything but clicking install.

Just trying to figure out what it is that people think is so great about linux and why Vista is bad is all.

---

### Post by iaculallad on 2008-07-10
-Move to recurring discussion-

EDIT: Try searching the forum. All of your problems stated have solutions stated on Forum's threads.

---

### Post by vistauser on 2008-07-11
Sorry for not saying specifically, I have searched these forums for these problems and tried the related things I have found to no avail.  I'm sure I'm missing something somewhere, but this sure is a pain in the butt for something that's suppose to be easy.

---

### Post by vistauser on 2008-07-11
I just searched some more and I never get anything relevant to my searches.  I can find nothing about the mouse issue on these forums.  If there is something I have no idea how to find it.  If you know there is such a post and know where it is, could you provide a link or something useful?

---

### Post by SilentChorus™ on 2008-07-11
Hi!

I'm only new... but I had a browse through the forum to see if I could find anything that could help you... there are similar things in the following thread... not sure if you have tried it... but it's a thought!

[http://ubuntuforums.org/showthread.php?t=768837&highlight=Mouse+cursor+doesn%27t+move]("http://ubuntuforums.org/showthread.php?t=768837&highlight=Mouse+cursor+doesn%27t+move")

I hope it helps in some way...

~Dani~

---

### Post by vistauser on 2008-07-11
> **SilentChorus™ said:**
> Hi!

I'm only new... but I had a browse through the forum to see if I could find anything that could help you... there are similar things in the following thread... not sure if you have tried it... but it's a thought!

[http://ubuntuforums.org/showthread.php?t=768837&highlight=Mouse+cursor+doesn%27t+move]("http://ubuntuforums.org/showthread.php?t=768837&highlight=Mouse+cursor+doesn%27t+move")

I hope it helps in some way...

~Dani~

Thanks for trying man I appreciate it.  That however isn't the problem I'm having and doesn't fix my issue.

---

### Post by CraigWatson on 2008-07-11
What motherboard are you using? It could be that Ubuntu doesn't like that particular chipset. Also, try using the CD as a LiveCD (not an installer) - you can test stuff like hardware compatability this way without physically installing it on your hardware.

It may be worth having a look at other distros, [Fedora](http://www.fedoraproject.org) is the main one I use. Fedora 9 is the latest version and has been proven to work with the nVidia drivers. Fedora also provides both GNOME (the Ubuntu default desktop environment) and KDE LiveCDs and also an install DVD that incorporates most of the software you could need.

Linux is all about doing things your way. It's proven to be a lot less bloated and a lot more stable than Windows (there have been next to no viruses for Linux in the world, ever). Once you have it set up (and I do agree, the setting up is an area of Linux which does have to be improved) and got your mind around the differences between the Linux world and the Windows world, your machine will literally "just work" - it's that stable. There's also no third-party bloatware like antiviruses, adware scanners, firewalls because you simply don't need them in Linux.

I'm not going to start on my anti-Vista rant but I'll sum it up with this: I'm typing this on a Samsung X20 laptop with 1.2GB RAM and a Pentium M 1.6GHz CPU. I have GNOME skinned to look as close as possible to Apple OS X (including the 3D Leopard dock and transition and transparency effects and animations). Vista would baulk at this hardware, but Linux runs completely happily on it.

That installation of Fedora runs out of 5.2GB. That includes the base operating system, OpenOffice, Amarok (media player), VLC, Firefox, Thunderbird and all of my other programs, plus an Apache webservice and MySQL database service. I could regale you for hours with Linux tales but I think I'm showing my geek-ness :p.

---

### Post by zxscooby on 2008-07-11
did you try cleaning your mouse balls?

---

### Post by CraigWatson on 2008-07-11
> **zxscooby said:**
> did you try cleaning your mouse balls?

The Logitech G9 is a Laser mouse :)

---

### Post by vistauser on 2008-07-11
> **CraigWatson said:**
> What motherboard are you using? It could be that Ubuntu doesn't like that particular chipset. Also, try using the CD as a LiveCD (not an installer) - you can test stuff like hardware compatability this way without physically installing it on your hardware.

It may be worth having a look at other distros, [Fedora](http://www.fedoraproject.org) is the main one I use. Fedora 9 is the latest version and has been proven to work with the nVidia drivers. Fedora also provides both GNOME (the Ubuntu default desktop environment) and KDE LiveCDs and also an install DVD that incorporates most of the software you could need.

Linux is all about doing things your way. It's proven to be a lot less bloated and a lot more stable than Windows (there have been next to no viruses for Linux in the world, ever). Once you have it set up (and I do agree, the setting up is an area of Linux which does have to be improved) and got your mind around the differences between the Linux world and the Windows world, your machine will literally "just work" - it's that stable. There's also no third-party bloatware like antiviruses, adware scanners, firewalls because you simply don't need them in Linux.

I'm not going to start on my anti-Vista rant but I'll sum it up with this: I'm typing this on a Samsung X20 laptop with 1.2GB RAM and a Pentium M 1.6GHz CPU. I have GNOME skinned to look as close as possible to Apple OS X (including the 3D Leopard dock and transition and transparency effects and animations). Vista would baulk at this hardware, but Linux runs completely happily on it.

That installation of Fedora runs out of 5.2GB. That includes the base operating system, OpenOffice, Amarok (media player), VLC, Firefox, Thunderbird and all of my other programs, plus an Apache webservice and MySQL database service. I could regale you for hours with Linux tales but I think I'm showing my geek-ness :p.

Hey, thanks for the reply.

My motherboard is an EVGA 680i MB.  Cpu is intel core duo extreme x6800.  I have it setup as a dual boot with vista.  I mentioned earlier the video card being 8800gtx, but there is two of them which are sli'ed in vista.  Not sure if that messes things up.  

Not trying to start any arguments about anything, just wanted to point out a couple things that I don't quite understand.  When people use the virus argument for example, I haven't had a virus since windows 95.  Nowadays, you have to pretty much open and run them yourself to get one.  Same for spyware, etc.  I haven't had any malware/virus/etc since I've had Vista.  (I had a couple spyware infections with XP because I was using some grey area software (read: cracks)).  Viruses are written for Windows because that's what the vast majority of people use.  A virus can't spread without hosts.

I have 0 anti-virus, anti-spyware, etc, etc.  I know how to look and see if anything suspicious is going on, even rootkit activity.  I do have some tools on a thumb drive I use to check clients computers and on occasion I give mine a good once over.  Never have issues because I simply don't install viruses, spyware, etc.

Now, as far as hardware requirements, I will agree you need higher specs to run Vista well on.  But that's like saying you can run counterstrike well so crysis must suck.  

This is just the way I have seen it.  But like you see, I'm giving Linux a try so I can figure it out for myself.  I'll give Fedora a try.   While I don't agree with a couple of things in this list, I thought this was interesting reasons to give it a go: [http://dmartin.org/weblog/things-i-can-do-in-linux-that-i-cant-do-on-windows](http://dmartin.org/weblog/things-i-can-do-in-linux-that-i-cant-do-on-windows) (I do like beryl)

I hope I'm not coming off as a tool, just expressing how I see the whole debate.  At least I've giving it a try and who knows, I may figure out for myself while some people love linux so much.

---

### Post by Vorian Grey on 2008-07-11
> **vistauser said:**
>  
I just don't get why everyone bashes on Vista so much.  Super easy to install, zero issues.  Download a driver and bam its working.  


Not everyone has an easy time getting Vista to work. It took me forever to get sound working. The same holds true for Linux as well. What I normally do is run the LiveCD to test for hardware problems. I keep trying out distros until I find one that works with my hardware. Ubuntu works a lot of the time but not always. 

It helps to make sure you have Linux friendly hardware before you get started, though.

---

### Post by rockface on 2008-07-12
> **vistauser said:**
> Hey, thanks for the reply.

My motherboard is an EVGA 680i MB.  Cpu is intel core duo extreme x6800.  I have it setup as a dual boot with vista.  I mentioned earlier the video card being 8800gtx, but there is two of them which are sli'ed in vista.  Not sure if that messes things up.  

Not trying to start any arguments about anything, just wanted to point out a couple things that I don't quite understand.  When people use the virus argument for example, I haven't had a virus since windows 95.  Nowadays, you have to pretty much open and run them yourself to get one.  Same for spyware, etc.  I haven't had any malware/virus/etc since I've had Vista.  (I had a couple spyware infections with XP because I was using some grey area software (read: cracks)).  Viruses are written for Windows because that's what the vast majority of people use.  A virus can't spread without hosts.

I have 0 anti-virus, anti-spyware, etc, etc.  I know how to look and see if anything suspicious is going on, even rootkit activity.  I do have some tools on a thumb drive I use to check clients computers and on occasion I give mine a good once over.  Never have issues because I simply don't install viruses, spyware, etc.

Now, as far as hardware requirements, I will agree you need higher specs to run Vista well on.  But that's like saying you can run counterstrike well so crysis must suck.  

This is just the way I have seen it.  But like you see, I'm giving Linux a try so I can figure it out for myself.  I'll give Fedora a try.   While I don't agree with a couple of things in this list, I thought this was interesting reasons to give it a go: [http://dmartin.org/weblog/things-i-can-do-in-linux-that-i-cant-do-on-windows](http://dmartin.org/weblog/things-i-can-do-in-linux-that-i-cant-do-on-windows) (I do like beryl)

I hope I'm not coming off as a tool, just expressing how I see the whole debate.  At least I've giving it a try and who knows, I may figure out for myself while some people love linux so much.

I've read many such comments from 'Windows' users. They come to Linux forums and ask questions that seem legitimate on the surface but beneath carry a quite different meaning.

They ask their question then at the end of their statement say something along the lines of 'it works in Windows'. These are shills trying to disguise their agenda.

And yes, I have Vista. I've tweaked and fiddled with it more than most and the damn thing fights me at every turn.

If you are not one of these individuals, my apologies and I hope you sort out you problems.

---

### Post by dantakeoff on 2008-11-06
he sounds legit. its difficult to switch once you know an os, its like learning everything that took so long to learn in the first place, again... but i read somewhere that there are more than 300 linux distros out there, and a bunch of them have live cds. ive tried everything i could find, and when something doesnt work on the live cd, i dont install the bugger. i run ubuntu on an acer aspire 5315 that shipped with vista, and get this... it came preinstalled with 17 gigabytes of heavy vista programs, took 2minutes to boot properly, and gave me endless advice on how to obtain expensive proprietry software. i soon found out that installing xp on this machine was a nightmare, but i did it anyway. and then got virus after virus. ubuntu sorted me out, it worked out of the box, apart from the wireless driver which i fixed with ndsiwrapper. my point is that if i could have such a nightmare with a brand new machine that came with a preinstalled os that probably added alot to the cost of the new pc, dont be surprised if you have to fiddle around getting an os that isnt prefitted for your machine to work. think of it as an initiation into the world of free software. everybody here has had a similar experience i think. but everyone finds a solution, through the forums or wherever. dont give up, itll pay dividends once your machine is up and running.
peace to the knowers...

---

### Post by jimv on 2008-11-06
> 1: Mouse cursor doesn't move diagonal unless you move it quickly. If you move it slowly, you can only move horizontal or vertical. This mouse functions fine in Vista and is a logitech g9.

Wow, I don't think I've even ever heard of that happening.  I did a quick Google search and everyone else seems to just be having issues getting all the buttons to work with that mouse...no mention of problems moving the cursor though.  Hmm.

> 2: No drivers for any device loaded, nor will it let me load any driver for any device. Always tells me that the device isn't installed. I have followed guides posted in several places, that are never the same which is odd, and none of them worked.

Are you talking about the Hardware Drivers control panel?  Because that only shows something if there is a proprietary driver available for a piece of your hardware.  Odd that it's not recognizing the 8800 though.

> On #2; For instance, the Nvidia drivers. If I go to hardware drivers the list is empty. I download and use root to sh <drivers> and it attempts to install and then tells me it can't find any devices to use. The video card in that machine is an 8800gtx.

I've never had much luck with Nvidia's driver installer in Ubuntu.  The prepackaged version in the repos usually seems to work though.  To install it, run this command:  sudo apt-get install nvidia-glx-177

> I just don't get why everyone bashes on Vista so much. Super easy to install, zero issues. Download a driver and bam its working. Everything is so smooth and I don't have to use commands to edit files in some deep directory with code that makes no sense to me. Can find and download pretty much any kind of software and have it running without doing anything but clicking install.

Vista's ok.  I used it for a year and was fine with it, until I discovered that it was somehow corrupting my photos that were sitting on my storage drive.  And it wasn't just me, there's a whole long thread on MS Technet of people with the same issue.  Since I couldn't allow my stuff to be destroyed, I had to go back to XP on that box.

As far as Ubuntu goes, it's a great OS for my low-end laptop.

---

