---
title: "looking for suggestions: 486-75 with 16 MByte"
date: 2004-11-05
forum: Installation &amp; Upgrades
---

### Post by Poldi on 2004-11-05
hi all.

I am looking for a nice graphical environment to use with Ubuntu on a 486DX4-75 with 16 MByte RAM.

I know I can install Ubuntu without the default desktop and use apt-get to get me anything on earth, but what (apart from X) do I select?

is XFCE already an option with 16MByte or do I have to use one of the more nostalgic Window Managers (tvwm, IceWM etc)?

I could probably upgrade my memory to 24MByte, although this could get more costly than I would like.

on a related issue: are there nice-looking GtK-themes for 256 colours out there? has anybody seen the Ubuntu themes on 640*480/8Bit?

thanks and regards,
Carsten

---

### Post by az on 2004-11-05
You need at least 32 megs of ram to install ubuntu.  The installer runs from a ramdisk, you see....


Try Debian.  Use Woody and then upgrade whatever packages you need from Sarge, Sid or Ubuntu...

---

### Post by jwenting on 2004-11-05
I once got Redhat 5.3 working on a 486DX100 with 16MB RAM but I wouldn't recommend it.
The installation alone took 48 hours, launching X took about 20 minutes and starting even XTerm took 5+ minutes :)
I dared attempt a kernel compile, that took over 72 hours (and of course failed at the last stage, just my luck).

You're better off with Windows 95, it outperforms everything else on such hardware.

---

### Post by Poldi on 2004-11-05
[QUOTE=azz]You need at least 32 megs of ram to install ubuntu.  The installer runs from a ramdisk, you see....


Try Debian.  Use Woody and then upgrade whatever packages you need from Sarge, Sid or Ubuntu...[/QUOTE]

as I have no CD-ROM at that machine right now I was planning to take the harddrive to a stronger computer, install the base there and bring it back to this one, get network working and continue. granted, I am a bit optimistic concerning the hotplug/detection system, but it could work.

kind regards,
Carsten

---

### Post by Poldi on 2004-11-05
[QUOTE=jwenting]I once got Redhat 5.3 working on a 486DX100 with 16MB RAM but I wouldn't recommend it.
The installation alone took 48 hours, launching X took about 20 minutes and starting even XTerm took 5+ minutes :)
I dared attempt a kernel compile, that took over 72 hours (and of course failed at the last stage, just my luck).

You're better off with Windows 95, it outperforms everything else on such hardware.[/QUOTE]

brr, what a suggestion... ;-)

this machine is running OS/2 Warp 4.52 today just fine.

actually I am coming back to Linux with Ubuntu. the first Linux I installed was Linux 0.997xyz (I don't think it was a distribution at all at that time, just 17 disks from out university's FTP-server) on a 486-33. I had X11 back then, why shouldn't I today?

you should note that I am not trying to run Gnome on it...

kind regards,
Carsten

---

### Post by az on 2004-11-05
"You're better off with Windows 95, it outperforms everything else on such hardware"

Bullcrap!  My linux system runs circles around the Win95 that was there when I got the laptop.  And I can use usb and a whole lot of other stuff.

Insofar as the hotplug, It should work just fine!  The only thing is the X configuration which will be detected as it installs.  If you just want to install a custon system(you dont have the drive space, anyway...) then install X yourself when you got the harddrive back in it's home.

---

### Post by Luke on 2004-11-05
ever consider damn small linux?
[http://damnsmalllinux.org/index.html](http://damnsmalllinux.org/index.html)
[http://damnsmalllinux.org/486.html](http://damnsmalllinux.org/486.html)

---

### Post by Poldi on 2004-11-05
[QUOTE=azz]"You're better off with Windows 95, it outperforms everything else on such hardware"

Bullcrap!  My linux system runs circles around the Win95 that was there when I got the laptop.  And I can use usb and a whole lot of other stuff.

Insofar as the hotplug, It should work just fine!  The only thing is the X configuration which will be detected as it installs.  If you just want to install a custon system(you dont have the drive space, anyway...) then install X yourself when you got the harddrive back in it's home.[/QUOTE]

I don't know how you know my drive space... but you might be right (720 MByte).
with 'base install' I meant exactly that: doing a Ubuntu custom and then use apt-get at the commandline to install whatever graphical system might be best.

btw, I still have no advice as to what windowmanager I should use (which was the original question). by the way; I had the OS/2 version of XFree86 3.6 running including an old Enlightment version (but I would prefere something faster).

thanks for your encouragement.

---

### Post by Poldi on 2004-11-05
[QUOTE=Luke]ever consider damn small linux?
[http://damnsmalllinux.org/index.html](http://damnsmalllinux.org/index.html)
[http://damnsmalllinux.org/486.html](http://damnsmalllinux.org/486.html)[/QUOTE]

well, I am on this Ubuntu trip right now, you see?

AFAIU Damn small is only special about it's default package selection anyway. using some kind of Debian gets me the power to apt-get everything I wish (so I could do the same selection Damn Small makes, right?). building everything myself like Gentoo does wouldn't help me much because for a 486 you cannot optimize that much compared to a default i386 package.

I really like Ubuntu on my stronger machines and what better Linux could I be looking for even on my 486 that a Debian package mechanism with polish and better hardware detection?

PS: googeling for help I cannot help but wonder what people nowadays are calling 'retro hardware'. a multi-MByte 486 is not retro in my book. my full-functioning ZX81 with 1kByte is retro. my Apple 2e with CP/M 2.2 and UCSD Pascal is retro, but why do people think it is a great achievment when they can say '... I was actually able to browse the internet and send eMail on my 486...'. when the 486 was new we were all sending mail and surfing. what are these kids thinking we did with our PCs at that time? just looking at it???

kind regards,
Carsten

---

### Post by Luke on 2004-11-05
[http://www.damnsmalllinux.org/dsl-hd-install.html#apt-get](http://www.damnsmalllinux.org/dsl-hd-install.html#apt-get)
i know that you want ubuntu anyway but just so you know...

---

### Post by Poldi on 2004-11-05
[QUOTE=Luke][http://www.damnsmalllinux.org/dsl-hd-install.html#apt-get](http://www.damnsmalllinux.org/dsl-hd-install.html#apt-get)
i know that you want ubuntu anyway but just so you know...[/QUOTE]

thanks, I see. 
and they have done a little bit more than just packaging as well as it turns out... I should really check the facts sometimes before I write stuff.

anyway - how are my chances of getting Ubuntu/XFCE/Gtk-browsers like Atlantis and Dillo to work when I upgrade to 24 MByte?

you might say 'why - just do it and tell us', but while I am optimistic all right I still know this will take days to install and configure.

that's why I am interested in any suggestion or experiences others might share.

tanks and regards,
Carsten

---

### Post by jwenting on 2004-11-05
[QUOTE=Poldi]
PS: googeling for help I cannot help but wonder what people nowadays are calling 'retro hardware'. a multi-MByte 486 is not retro in my book. my full-functioning ZX81 with 1kByte is retro. my Apple 2e with CP/M 2.2 and UCSD Pascal is retro, but why do people think it is a great achievment when they can say '... I was actually able to browse the internet and send eMail on my 486...'. when the 486 was new we were all sending mail and surfing. what are these kids thinking we did with our PCs at that time? just looking at it???
[/QUOTE]

I hear ye.
My first computer was an original IBM PC Portable (well, my father's company owned it but I was the only one who ever used it) with a whopping 640KB RAM, a 4" amber CRT and a massive 10MB harddisk. Main feature were 2 360KB floppie drives (at a time when a single 160KB drive was the norm).
Of course everything was integrated into the pressed steel case, including the keyboard and carrying handle.
OS was IBM PC-DOS 3.1 (equivalent to MS-DOS 3.2).
I learned programming BASIC and a bit of Pascal on that machine.

Main reason my father never used it was because his hernia prevented him from lifting the 10+ kilos the machine weighed.

I remember looking up the original price of that thing years later and finding it must have cost over €5000.

That's about as retro as they come in PC terms.

---

### Post by Poldi on 2004-11-05
[QUOTE=jwenting]I hear ye.
My first computer was an original IBM PC Portable (well, my father's company owned it but I was the only one who ever used it) with a whopping 640KB RAM, a 4" amber CRT and a massive 10MB harddisk. Main feature were 2 360KB floppie drives (at a time when a single 160KB drive was the norm).
Of course everything was integrated into the pressed steel case, including the keyboard and carrying handle.
OS was IBM PC-DOS 3.1 (equivalent to MS-DOS 3.2).
I learned programming BASIC and a bit of Pascal on that machine.

Main reason my father never used it was because his hernia prevented him from lifting the 10+ kilos the machine weighed.

I remember looking up the original price of that thing years later and finding it must have cost over €5000.

That's about as retro as they come in PC terms.[/QUOTE]


well, the IBM PC (desktop) started with 64kByte, so you still had a factor 10 in this regard.

beeing totally honest, I own a 16kByte memory extension for my 1kByte ZX81. but the expansion gets hot after ca. 5-10min. and has to be removed. when I got this great Sinclair computer first, I had no persistant datastore at all (at that time meaning I had no tape-recorder) meaning whenever I wanted to play a game, I had to type it in first. tell that to the Nintendo-generation...

before this gets too offtopic: the machine in question here is an IBM Thinkpad 701C. this is the one with the 'butterfly' folding keyboard and a 10,4" TFT display. while certainly not up-to-date, nothing will part me from this little one and it is still definetly among the cooler machines to have a Linux running on.

kind regards,
Carsten

---

### Post by timmytim on 2004-11-05
[QUOTE=Poldi]hi all.

I am looking for a nice graphical environment to use with Ubuntu on a 486DX4-75 with 16 MByte RAM.

I know I can install Ubuntu without the default desktop and use apt-get to get me anything on earth, but what (apart from X) do I select?

is XFCE already an option with 16MByte or do I have to use one of the more nostalgic Window Managers (tvwm, IceWM etc)?

I could probably upgrade my memory to 24MByte, although this could get more costly than I would like.

on a related issue: are there nice-looking GtK-themes for 256 colours out there? has anybody seen the Ubuntu themes on 640*480/8Bit?

thanks and regards,
Carsten[/QUOTE]
 Why, if you dont mind me asking, are you using such old hardware? You can get a Pent. 2 with atleast 64Megs RAM from a yard sale for $20.00. Hell, if you're anywhere near AZ or would pay shiping, I'll give you a pentium 2 machine, with 64MB free! Its time to part with your 486 dude. Sorry :(

---

### Post by Poldi on 2004-11-05
[QUOTE=timmytim]Why, if you dont mind me asking, are you using such old hardware? You can get a Pent. 2 with atleast 64Megs RAM from a yard sale for $20.00. Hell, if you're anywhere near AZ or would pay shiping, I'll give you a pentium 2 machine, with 64MB free! Its time to part with your 486 dude. Sorry :([/QUOTE]

IBM. Thinkpad. 701C.

see here: [http://www-5.ibm.com/se/news/2002/11/TP701c.jpg](http://www-5.ibm.com/se/news/2002/11/TP701c.jpg)
[for the non-geeks: 'as seen in James Bond and Mission Impossible']

I _do_ have other PCs as well, mind you. (Thinkpad 390, Thinkpad T20, Thinkpad T22, Thinkpad R40, Thinkpad R51p - do we see a pattern? [actually I do not keep all old stuff around - I had a Thinkpad 720, 2 Thinkpad 560, a Thinkpad 380 and 2 Thinkpad 600E - all of which I have sold - the pattern should now be obvious])

kind regards,
Carsten

---

### Post by az on 2004-11-05
Old hardware _is_ cool.  Especially when used with linux.  You just have so many possibilities.

Icewm is really easy on memory.  Wmaker is just as snappy, but it uses a little more memory and it just bugs me!

I have tried most other window managers and I always end up with icewm...  I miss the load average and network traffic graphs otherwise...

XFCE4 is not much faster than gnome, to be honest.

Firefox should run fine.  You may also install galeon from debian stable (Woody).  It is a gtk1.2 app and so is quite fast (but spartan)

---

### Post by im_ka on 2004-11-05
if you can't get ubuntu running, check out vector linux. it's made for older hardware.

btw, wmaker is my favourite wm.

---

### Post by timmytim on 2004-11-05
[QUOTE=Poldi]IBM. Thinkpad. 701C.

see here: [http://www-5.ibm.com/se/news/2002/11/TP701c.jpg](http://www-5.ibm.com/se/news/2002/11/TP701c.jpg)
[for the non-geeks: 'as seen in James Bond and Mission Impossible']

I _do_ have other PCs as well, mind you. (Thinkpad 390, Thinkpad T20, Thinkpad T22, Thinkpad R40, Thinkpad R51p - do we see a pattern? [actually I do not keep all old stuff around - I had a Thinkpad 720, 2 Thinkpad 560, a Thinkpad 380 and 2 Thinkpad 600E - all of which I have sold - the pattern should now be obvious])

kind regards,
Carsten[/QUOTE]
 Wasn't trying to be mean, was just curious. I guess i dont have the time to spare on such projects as seeing how Ubuntu runs on a 486 with limited hardware, im sorry for not understanding your logic. 

BTW: azz... Old hardware is cool! I do have some 486 - PII stuff laying around, its not in use though.

Later............

---

### Post by HungSquirrel on 2004-11-05
> building everything myself like Gentoo does wouldn't help me much because for a 486 you cannot optimize that much compared to a default i386 package.
And building your system would take years rather than mere days.

---

### Post by sageb1 on 2008-01-29
i need to know the success of this project with you 486 is going Poldi as I need to impress my brother in law.

around thanksgiving (canada) oct 07 i gave him a copy of Ubuntu Dapper 6.06 LTS LiveCD to put on his 486.

no word on his success.

---

### Post by matchstich on 2008-04-04
before this gets too offtopic: the machine in question here is an IBM Thinkpad 701C. this is the one with the 'butterfly' folding keyboard and a 10,4" TFT display. while certainly not up-to-date, nothing will part me from this little one and it is still definetly among the cooler machines to have a Linux running on.

kind regards,
Carsten[/QUOTE]

i just got of these of these yesterday, and am looking for some kinda linux to load it up with.

cept mine does not have usb, it has serial port external floppy drive.

wonder if a serial to usb connector adapter ( if there is such a monster made) would let me use a cd drive to load with?

---

