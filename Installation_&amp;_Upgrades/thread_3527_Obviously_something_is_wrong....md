---
title: "Obviously something is wrong..."
date: 2004-11-06
forum: Installation &amp; Upgrades
---

### Post by Grouse on 2004-11-06
I took the plunge and installed WartyWarthog on a PIII Gateway. Clean install from a downloaded ISO CD. Evrything seemed to go just fine, I put in my name, user name, and password..the thing told me it was going to start up from base install, and the screen went blank. I waited for the start up screen, and waited, and waited...got a piece of pizza, scratched my butt a few times, waited some more, and after about thirty minutes came to the obvious conclusion that something went kerblooey (thats a technical term...kerblooey). Now I'm baffled...any ideas? Any suggestions? Take it out and burn it?


HELP!!!

Grouse

---

### Post by eNiNjA on 2004-11-06
Give it another go, and when in doubt, *kick it
 
 I just put it on my neighbors Gateway...with a 300mhz cpu and 128 ram..

---

### Post by Andy Owen on 2004-11-07
I think I'm having a similar issue. I've installed on a Dell 8500 laptop. I have a few extra details which may be relevant (or different):

1) While starting up, modprobe fails for a few things. I haven't written them all down, but I know that the second one is "pciehp". For all but one of them, the message says: "Operation Not Permitted". If necessary, I can get some more detailed stuff.

2) After all these things have loaded, the screen goes blank and activity stops. However, if I type my username and password, then there is hard disk activity for a few moments. 

3) If I then press the power key (a soft power button), then the text from startup will appear on screen again, with the last line being the line telling me to log on. It them shuts down.

4) Running in recovery mode works just fine.

I have a wireless card which doesn't have particularly good Linux support (Broadcom/Dell Truemobile 1300), and have read people saying that adding "pci=noacpi" or "acpi=noirq" has solved all their problems, but I don't actually know where to add these lines :)

Sorry if this is a different issue altogether and I've thrown people off the trail.

Andy

---

### Post by Andy Owen on 2004-11-07
I did some more looking around, and I don't think that the point (1) I made before is anything to do with it. What I did do was work out what was meant by the "pci=noacpi" and adding that line (as an argument to kernel in the boot loader) means that on startup, I now get a sound.

I'm fairly sure this sound is the sound made for logging on.

I've also found that pressing Ctrl+Alt+F1 takes me to a terminal which is fully functional. If I try to start X (by running startx) then it tells me that it is already running.

---

### Post by Grouse on 2004-11-07
I solved this little problem...I installed SuSE 9.1 instead of Ubuntu. OK, I went around the problem, alright? This illustrates a point, though. Ubuntu is aiming for everybody's desktop, right? It needs to be simple enough that ordinary Windows dweebs, with no special knowledge, can install and run it on typical systems. If my mother can use it, it is simple enough. If I can install it, it is mature enough for the Joe Blow market. ***I am the target user*** (just call me Joe), and at this point I have to say that Ubuntu failed; it ain't ready yet.

   There are those who will say, "You just don't know enough about Unix/Linux systems yet, you needed to do your homework." I work for a living, I don't _want_ to do homework. SuSE 9.1 was absolutely dirt simple; answer about 3 questions, sit back and watch the pretty blinking lights, and play with the screensavers when the system says GO. 

   Ubuntu's working motto is "It Just Works", and I greatly admire the effort the guys are making...and I'm also looking forward to the time when it actually does Just Work. Until then, I'll fumble around with SuSE and Mandrake, and admire Ubuntu's effort from the sidelines.

Take care

Grouse

---

### Post by mark on 2004-11-07
[QUOTE=Grouse]I solved this little problem...I installed SuSE 9.1 instead of Ubuntu. OK, I went around the problem, alright? This illustrates a point, though. Ubuntu is aiming for everybody's desktop, right? It needs to be simple enough that ordinary Windows dweebs, with no special knowledge, can install and run it on typical systems. If my mother can use it, it is simple enough. If I can install it, it is mature enough for the Joe Blow market. ***I am the target user*** (just call me Joe), and at this point I have to say that Ubuntu failed; it ain't ready yet.

   There are those who will say, "You just don't know enough about Unix/Linux systems yet, you needed to do your homework." I work for a living, I don't _want_ to do homework. SuSE 9.1 was absolutely dirt simple; answer about 3 questions, sit back and watch the pretty blinking lights, and play with the screensavers when the system says GO. 

   Ubuntu's working motto is "It Just Works", and I greatly admire the effort the guys are making...and I'm also looking forward to the time when it actually does Just Work. Until then, I'll fumble around with SuSE and Mandrake, and admire Ubuntu's effort from the sidelines.

Take care

Grouse[/QUOTE]
My experience with SuSE was a little different...it just "never worked" for me (at least on my VAIO laptop).  However, on my Intel-based (D865GLC) desktop, Ubuntu's been pretty smooth.  I'm about to try it on my laptop - if you're interested, I'll post any *caveats* here.

Regards,

Mark

---

### Post by wallijonn on 2004-11-07
Since I am old-school I usually set all my IRQs manually before installing any OS. BTW, WXP could care less what IRQs you've set up - it will build it according to whatever it wants. (But that's another story).

I always disable BIOS and VIdeo cacheing and shadowing, along with ACPI. When it reboots I always go into the BIOS and change the boot priority from CD to HD0. 

I seldom have a USB device inserted when installing an OS, nor a printer connected. My keyboard and mouse are always connected to PS/2 ports (because of older Linux distros and Western Digital and Seagate HD utilities). 

So, yes, I was pleasantly surprised when Ubuntu went right in with my Logitec MX510 connected to my USB port. But there's no way I would install any OS with an USB  scanner, camera, printer, mem sticks, or PDA connected.

Most distros have recognised my parallel port HP Laser printer upon reboot.

---

### Post by Grouse on 2004-11-08
[QUOTE=wallijonn]Since I am old-school I usually set all my IRQs manually before installing any OS. BTW, WXP could care less what IRQs you've set up - it will build it according to whatever it wants. (But that's another story).

I always disable BIOS and VIdeo cacheing and shadowing, along with ACPI. When it reboots I always go into the BIOS and change the boot priority from CD to HD0. 

I seldom have a USB device inserted when installing an OS, nor a printer connected. My keyboard and mouse are always connected to PS/2 ports (because of older Linux distros and Western Digital and Seagate HD utilities). 

So, yes, I was pleasantly surprised when Ubuntu went right in with my Logitec MX510 connected to my USB port. But there's no way I would install any OS with an USB  scanner, camera, printer, mem sticks, or PDA connected.

Most distros have recognised my parallel port HP Laser printer upon reboot.[/QUOTE]


See, obviously you are *not* the typical Joe Blow....I have no idea what the heck you are talking about! I'm glad you know this stuff, and admire you for it...but you just proved my point! (thanks). I'm not a dumbass, I actually have a slightly higher than average IQ, and work as an Analytical Chemist for a Governmental Agency...(we send alot of tax dollars into outer space) but I'm not a computer GeeWhiz, and Ubuntu is not for me...yet!

I'll keep checking in on it though, cuz the philosophy sounds dead bang on target.

Grouse

ps..anyone here play Enemy Territory?

G

---

### Post by wallijonn on 2004-11-08
Okay, 

it booted into the cd.
you installed it past the point where it started to reboot.
it then hung.

You will have to go into your motherboard's BIOS (usually through hitting the delete key, f1, f2, f8, f10...) when it first powers up and look at what the format is for your hard disk drive. Is it set to AUTO? If it is you should change it to Large or LBA. escape, f10, save. 

[http://www.cyberwalker.net/faqs/reinstall-reformat-winxp/enter-BIOS.html](http://www.cyberwalker.net/faqs/reinstall-reformat-winxp/enter-BIOS.html)

How big is the disk drive?

I was assuming in your previous posit that it booted into GRUB (the boot loader), spit out a few lines on the screen and went blank (as if the video portion died). I am assuming now that after the BIOS tests the memory and it starts to boot that there is nothing on the screen. Is this correct?

---

### Post by Grouse on 2004-11-08
[QUOTE=wallijonn]Okay, 

snip

How big is the disk drive?

I was assuming in your previous post that it booted into GRUB (the boot loader), spit out a few lines on the screen and went blank (as if the video portion died). I am assuming now that after the BIOS tests the memory and it starts to boot that there is nothing on the screen. Is this correct?[/QUOTE]

yeah, that was pretty much what was happening...now, though, when I boot up, it goes to KDE, with lots of pretty pictures, etc. Everything is cool now, cuz SuSE is working fine. I'm not giving up on Ubuntu, I'm just waiting for it to get a bit more mature, a bit more ID10T proof, ya know?

Thx

Grouse


btw, its a 20GB drive, nothing else on it, no errors in the media.

---

### Post by ashley_v on 2004-11-09
You guys should really take a look around the forum before posting such topics.  All problems in regard to that are solved with my solution here ---> [http://www.ubuntuforums.org/showthread.php?t=3472](http://www.ubuntuforums.org/showthread.php?t=3472)

It has something to do with the iso image, for I know it could be corrupted packages on it even though md5 sums are correct?

Either way the solution is simple.  Reinstall and don't let Ubuntu install your desktop from the cd you downloaded.  instead edit /etc/apt/sources.list and comment out the cdrom entry.  Instead use apt-get update ; apt-get dist-upgrade ; apt-get install kde or gnome whatever desktop you want.  Then log in and it won't hang.


Ubuntu works just fine.............feels like Debian! :)

---

### Post by wilhelm on 2004-11-09
good suggestion, u know what size that download was , just want to be prepaed a might...

---

### Post by ashley_v on 2004-11-09
[QUOTE=][/QUOTE]
 Oh boy your talkin a big HUGE download but I get and got around 160k off Ubuntu servers.  I'd say tops 20 min.  Beats the junk off the cd we spent our bandwitdth on and serves Ubuntu right.

---

### Post by Grouse on 2004-11-09
[QUOTE=ashley_v]You guys should really take a look around the forum before posting such topics.  All problems in regard to that are solved with my solution here ---> [http://www.ubuntuforums.org/showthread.php?t=3472](http://www.ubuntuforums.org/showthread.php?t=3472)

It has something to do with the iso image, for I know it could be corrupted packages on it even though md5 sums are correct?

Either way the solution is simple.  Reinstall and don't let Ubuntu install your desktop from the cd you downloaded.  instead edit /etc/apt/sources.list and comment out the cdrom entry.  Instead use apt-get update ; apt-get dist-upgrade ; apt-get install kde or gnome whatever desktop you want.  Then log in and it won't hang.


Ubuntu works just fine.............feels like Debian! :)[/QUOTE]

it IS debian.

I'm wondering if you actually read the thread, or just skimmed it, cuz I don't know how to do all of that, and I don't want to learn it. **I want it to be so smooth and idiot proof that even an idiot like me can install and run with no problems.**

But thanks anyway.

Grouse

---

### Post by ohbahsan on 2004-11-09
i too am having a problem similar to that of Grouse's.  i download the cd and it installs everything fine, it even goes online to download updates.  then after it reboots i see all the linux startup messages, and then black screen.  i hard-reset, linux starts up again, and then black screen again.  i come to the website, search for similar problems, find no solutions.

i will follow Grouse's lead and install suse also.  too bad, i was really looking forward to my first linux desktop install in over 5 years.

---

### Post by ispmike on 2004-11-10
If you want to use Linux you will have to get your hands dirty eventually. SuSe is a great distro but, I have NEVER installed a linux distro that didn't require some tinkering, including Ubuntu, that should just be a given! Sorry to sound negative but even though SuSe installed fine you should expect to run into some problems (codecs, drivers, software, etc..) somewhere, good luck though.

---

### Post by ashley_v on 2004-11-10
Well maybe I'm in the wrong arena here.  I am no new user to Linux and I really hate the kind of people I'm seeing here.

First of all.  Debian itself is not for the average user if you don't know what your doing.   The fact that Ubuntu is based on debian makes it no different.  It's all Linux........dong!  Seems like what some of you need are Lindows or Linspire.  Or better yet keep your windows and use vmware to emulate Linux.

@Grouse  -- Nothing is idiot proof and if you haven't learn that by now then you should probably reconsider your options in life cause it just means your a burden if you can't do some things for yourself.

@ohbahsan  -- You followed Grouse and not my recommendations, that's why your in the same boat.

I'm no Guru but I can take any Linux and make it work...........even Ubuntu and you can too!

---

### Post by ohbahsan on 2004-11-10
the last time i used a linux desktop was about 4 or 5 years ago, back in the days when you had to manually create/guess your own X config files.  i thought things have gotten more user-friendly, but alas i didn't realize it still takes so much tinkering to get a linux desktop to work.

anyway SUSE didn't work for me either, i put in the install CD, and it hung on the welcome screen.  so i went back to the forums searching for more hints, and decided to look through my X config file.  turns out i forgot i had a second video card in my machine, and the installer got confused about which video card to use.  so i took the extra card out and re-installed ubuntu.  and presto!  i now have a login screen.

i'm happy to get this far, and it looks really nice so far.  gaim/firefox/azureus all work great.  but man there are still lots of tweaks left to do, it's very discouraging.  i now have a new found respect for windows.

---

