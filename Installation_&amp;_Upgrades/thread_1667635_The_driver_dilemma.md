---
title: "The driver dilemma"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by Hmmster on 2011-01-15
Okay, so here's the thing.
For half a year, i've downloaded the newest driver from the ATI website, and the one from "Additional drivers" in system -> administration.
This, however, has resulted in me not seeing characters in games, such as my units/buildings in SC2, my character in WoW and my character in Perfect World.

This was solved when i started running WoW in OpenGL. For the others, however. The problem still persists.

Later i've discovered that this is purely the fault of the driver i got from System -> administration. So i obviously tried just running the one from the ATI website.

I installed it, and everything acted very laggy, when i tried opening the ATI cataclyst control center it told me 
" There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following. 
 No ATI graphics driver is installed, or the ATI driver is not functioning properly.
 Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig."


Now, after checking around on the internet a bit, i've seen that you're not supposed to run the .run file directly (As in with a simple terminal command)
If so, how am i supposed to run it?


TL;DR:
I appearently don't know how to install ATI drivers
The one from system -> preferences makes things dissapear from games




Specs:
Asus P7P55D
Powercolour ATI radeon HD 5770
Intel i5 750
Corsair dominator 2x2 1600MHz

---

### Post by Hmmster on 2011-01-15
Help! I tried installing the real ATI drivers via a guide on some wiki-website!
I did everything it said, making a package, running it etc. etc.
When i came to a step called "making a new etc/x11/xorg.conf file", it didn't work. It just said that there were no such directory.

When this happened, i decided to restart my computer. What followed was that i could see the Ubuntu 10.10 loading screen, then it went black, and my screen said "No signal detected"

I'll try to find the guide website and give a more accurate post, but not i'm on a other computer so i don't have my website history.

---

### Post by Hmmster on 2011-01-15
Help! I tried installing the real ATI drivers via a guide on some wiki-website!
I did everything it said, making a package, running it etc. etc.
When i came to a step called "making a new etc/x11/xorg.conf file", it didn't work. It just said that there were no such directory.

When this happened, i decided to restart my computer. What followed was that i could see the Ubuntu 10.10 loading screen, then it went black, and my screen said "No signal detected"

I'll try to find the guide website and give a more accurate post, but not i'm on a other computer so i don't have my website history.

---

### Post by Hmmster on 2011-01-15
See, this is what i don\t get.
I have a urgent problem, and nobody can help me, why_

---

### Post by Hmmster on 2011-01-15
See, this i what i don\t get.
I have an urgent problem, and nobody can help me, why_

---

### Post by Hmmster on 2011-01-15
See, this i what i don\t get.
I have an urgent problem, and nobody can help me, why_

EDIT> Why the **** does it keep double&triple posting_

---

### Post by dino99 on 2011-01-15
you are running 10.10 right ? so the kernel directly deal with X, no need of xorg.conf. But you might know that you need to follow EXACTLY the ubuntu howto according to the release used (not blah blah on exotic and untrusted wiki). Note that ubuntu devs spend some time to tweak our driver (and its not for nothing) so mixing ubuntu settings with external (ATI) ones is the right way to break everything, then no need whining.

into a terminal: (everything into linux world is case sensitive)

sudo rm /etc/X11/xorg.conf

open synaptic repo tab (system admin synaptic third party) and add this ppa:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

then update, upgrade and reboot

---

### Post by Hmmster on 2011-01-15
Yes, i'm running 10.10. And i'm obviously on a liveCD now since i can't boot the main OS.
When i type that into the livecd terminal i get
"ubuntu@ubuntu:~$ sudo rm /etc/X11/xorg.conf
rm: cannot remove `/etc/X11/xorg.conf': No such file or directory
"

EDIT: And i was folowwing [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

---

### Post by dino99 on 2011-01-15
from a livecd, the commands are aplied on that cd indeed if you dont give the path to your /dev/sdxx by chrooting. But maybe its faster for you to make a fresh install again:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Hmmster on 2011-01-15
Fresh install and loose everything? Oh god no
And how would i chroot to my dev/sdxx

---

### Post by Hmmster on 2011-01-16
Oh hey, thanks for all the help, oh wait.....
Bump, why can\t anyone help me_

---

### Post by Atamisk on 2011-01-16
Sarcasm gets you nowhere. 


BTW, have you tried to boot into recovery mode? just do that, drop into a root with networking, and un-f**k the driver using the methods above. 

I made the mistake of using an nvidia-supplied driver, and now i have to re-install it every time X updates.

DX

---

### Post by Hmmster on 2011-01-17
Some times my computer just boots into the ubuntu loading screen to black screen, and some times i can choose OS from a menu, it\s pretty wierd.
So no, i can\t boot into recovery mode.

---

### Post by Hmmster on 2011-01-17
Bump

---

### Post by theDaveTheRave on 2011-01-17
if you are booting into a live CD you can still access your main HDD.

Open up nautilus (or the live CD's file browser) and you should see all the HDDs that are currently not mounted.

Mount them and navigate through them to find your main root drive, then navigate to the location of the xorg.conf file that you created, and delete it.

Then you should be able to re-boot into your system in 'recovery' mode at the very least.

David.

quick word of advice...
don't get too sarky ...  people won't help you so readily.
don't get too whiney ... people won't help you so readily.
try to stick to advice from trusted sites ... or people won't help you so readily (if you aren't sure about something, drop a link to it to ask for advice about the info).

if all else fails, use the live CD find your /home directory on the HDD and save it to an external. Then re-install.

and the multi posting is caused by a problem with the forum server (apparently) being overloaded - the price of popularity.

D

---

### Post by Hmmster on 2011-01-18
I never actually created a xorg.conf file, i got an error when i typed into terminal what the guide said, and then i rebooted, and then the black screen stuff started =p
In the place where it should be, /etc/x11, i have some files called "X", "Xorg.conf.failsafe", "xorg.conf.fglrx-0"m "xorg.conf.original-o", "Xorg.conf.original-1", "xreset", "xsession", "Xsession.options", "xwrapped.config"

Those were the ones that start with "x"

Just wondering, if i were to copy my /home/, would there be any consequences with wine?
As in, would i loose everything i have installed in wine? Would i still even have wine installed? Would everything be the same as it was before?

And try to think of it from my perspective, i'm desperate here, being on a LiveCD basically not being able to do anything sucks D:

Thanks for the help so far though.

---

### Post by Hmmster on 2011-01-18
I never actually created a xorg.conf file, i got an error when i typed into terminal what the guide said, and then i rebooted, and then the black screen stuff started =p
In the place where it should be, /etc/x11, i have some files called "X", "Xorg.conf.failsafe", "xorg.conf.fglrx-0"m "xorg.conf.original-o", "Xorg.conf.original-1", "xreset", "xsession", "Xsession.options", "xwrapped.config"

Those were the ones that start with "x"

Just wondering, if i were to copy my /home/, would there be any consequences with wine?
As in, would i loose everything i have installed in wine? Would i still even have wine installed? Would everything be the same as it was before?

And try to think of it from my perspective, i'm desperate here, being on a LiveCD basically not being able to do anything sucks D:

Thanks for the help so far though.

---

### Post by Hmmster on 2011-01-18
bump

---

### Post by Hmmster on 2011-01-18
iiiiibumpiiii

---

### Post by Hmmster on 2011-01-19
Yet another bump

---

### Post by Hmmster on 2011-01-19
Yet another bump

---

### Post by Hmmster on 2011-01-19
Yet another bump

---

### Post by Hmmster on 2011-01-19
Bump :(

---

### Post by theDaveTheRave on 2011-01-19
So you weren't able to create the /etc/x11.xorg.conf file that the guide said due to a 'directory not found error'.

Now the question is when you are logged in on the live CD are you sure you are navigating on the HDD and not the live CD version of the /etc/x11/ directory? - I just want to be sure what you are seeing. 

Unless you are navigating the CD's /etc/x11 directory, which may explain what you are seeing.?

Otherwise you have 3 files that you found in the X11 directory...


Xorg.conf.failsafe

xorg.conf.original-o

Xorg.conf.original-1

you could try to re-create the xorg.conf file from one of these use the following...

open up nautilus (or the live cd's file browser) and simply copy one of the files then rename the copy to xorg.conf reboot and see if you can get into your system...

Tell us how it goes, I'll try to be back on line in about 5 hours, right now I've got a pair of unhappy 2 year old children crying at me!

If only I could log in and turn off their sound output .... :twisted:

D

---

### Post by Hmmster on 2011-01-19
Completely sure that it's the hard drive, and not the CD i'm looking at.
When i press "home" instead of "etc", i get to my HDD home folder with all my stuff. ;)
Here's a video of me booting a couple of times, btw: [http://www.youtube.com/watch?v=ECmHiCsiB8U](http://www.youtube.com/watch?v=ECmHiCsiB8U)
And i'll try that now, i'll edit this post later!'

EDIT: Nope, did not work, tried both normally and in failsafe, both still got "No signal detected" and then black screen,

And again:
> 
Just wondering, if i were to copy my /home/, would there be any consequences with wine?
As in, would i loose everything i have installed in wine? Would i still  even have wine installed? Would everything be the same as it was before?


---

### Post by Hmmster on 2011-01-19
Sorry, bump =/

---

### Post by theDaveTheRave on 2011-01-19
Easy does it, I said 4 or 5 hours!

Glad that you are on the HDD and not the CD.

I'm surprised however that when you click the  'home' button on the live CD you are taken to your /home on the HDD ? but anyway....

If you copy the home directory you will retain all of your personal files and settings for your installed software. Just make sure you get all the 'hidden' directories and files, these will all begin with a . (period), and will most likely reflect the software package you have installed. Then after re-install just copy all of your personal files back

I can't say about wine (never used it!) and the packages that run through it. You'll need to investigate that elsewhere, it may simply be a case of creating a copy of a 'wine' directory somewhere - probably under one of.... /usr  /bin  /etc/wine run the following command to tell you where all the wine files are being held
```
locate wine
```

The other thing to try is to move the /etc/X11 directory on the HDD, whilst logged into the live CD
```
 mv /Media_HDD/etc/X11 Media_HDD/etc/X11_bad
```

and replace it with the contents of the live cd's /etc/X11
```
 cp /LiveCDROM/etc/X11 Media_HDD/etc/X11
```

obviously replace the < Media_HDD > and < liveCDROM > paths with the correct ones for your system (or use the file manager).

Again you'll want to check you caught any hidden files / directories.

David.

---

### Post by theDaveTheRave on 2011-01-19
Easy does it, I said 4 or 5 hours!

Glad that you are on the HDD and not the CD.

I'm surprised however that when you click the  'home' button on the live CD you are taken to your /home on the HDD ? but anyway....

If you copy the home directory you will retain all of your personal files and settings for your installed software. Just make sure you get all the 'hidden' directories and files, these will all begin with a . (period), and will most likely reflect the software package you have installed. Then after re-install just copy all of your personal files back

I can't say about wine (never used it!) and the packages that run through it. You'll need to investigate that elsewhere, it may simply be a case of creating a copy of a 'wine' directory somewhere - probably under one of.... /usr  /bin  /etc/wine run the following command to tell you where all the wine files are being held
```
locate wine
```

The other thing to try is to move the /etc/X11 directory on the HDD, whilst logged into the live CD
```
 mv /Media_HDD/etc/X11 Media_HDD/etc/X11_bad
```

and replace it with the contents of the live cd's /etc/X11
```
 cp /LiveCDROM/etc/X11 Media_HDD/etc/X11
```

obviously replace the < Media_HDD > and < liveCDROM > paths with the correct ones for your system (or use the file manager).

Again you'll want to check you caught any hidden files / directories.

David.

---

### Post by Hmmster on 2011-01-19
Appearently, my hard drive is called ea13cece-6349-4d88-a5a7-0dfb7ee2bb94



> 
ubuntu@ubuntu:~$ mv /ea13cece-6349-4d88-a5a7-0dfb7ee2bb94/etc/x11 ea13cece-6349-4d88-a5a7-0dfb7ee2bb94/etc/x11_bad
mv: cannot stat `/ea13cece-6349-4d88-a5a7-0dfb7ee2bb94/etc/x11': No such file or directory
ubuntu@ubuntu:~$ 
So i decided to do Sudo Nautilus since i'm not allowed in that folder to do anything by default.
I renamed the old /etc/x11 to /etc/x11_bad, and i copied the one from the LiveCD to the HDD /etc/x11 :)
I'll try to reboot now.


No, same "Signal not detected" crap :(

Also, i tried to install another OS via this LiveCD like two days ago, when the installation was complete, nothing more appeared in my "Choose OS"-screen :S

---

### Post by theDaveTheRave on 2011-01-19
do you get a CLI ?? or nothing at all??

D

---

### Post by Hmmster on 2011-01-19
I press what OS i want to use ->
The screen goes black, but background lighted with LEDs and a little underline flashing in the top ->
The screen goes entirely black, as if it was turned off ->
The little flashing underline comes back, and the LEDs ->
A ubuntu loading screen comes up, and in the middle of it, the screen goes black and the screen says "No signal detected", and it goes black as if it's off again, this time for good =p


I CAN choose safe mode or whatever it's called and choose to get a command line in the menu, though?

---

### Post by theDaveTheRave on 2011-01-19
Just thinking 'aloud' as it were....

What is the complete error message that you get? I guess you have searched for it in google, what what the advice?

I guess you don't even get to a cli login? if you do have you tried starting X from here?
[code]startx[code]

if you can post any output that would be great.

Otherwise check the contents of the following folder

/usr/lib/X11/xinit

and compare with the same on the liveCD.

David

---

### Post by Hmmster on 2011-01-19
I press what OS i want to use ->
The screen goes black, but background lighted with LEDs and a little underline flashing in the top ->
The screen goes entirely black, as if it was turned off ->
The little flashing underline comes back, and the LEDs ->
A ubuntu loading screen comes up, and in the middle of it, the screen goes black and the screen says "No signal detected", and it goes black as if it's off again, this time for good =p


I CAN choose safe mode or whatever it's called and choose to get a command line in the menu, though?

---

### Post by Hmmster on 2011-01-19
I press what OS i want to use ->
The screen goes black, but background lighted with LEDs and a little underline flashing in the top ->
The screen goes entirely black, as if it was turned off ->
The little flashing underline comes back, and the LEDs ->
A ubuntu loading screen comes up, and in the middle of it, the screen goes black and the screen says "No signal detected", and it goes black as if it's off again, this time for good =p


I CAN choose safe mode or whatever it's called and choose to get a command line in the menu, though?

---

### Post by Hmmster on 2011-01-19
I press what OS i want to use ->
The screen goes black, but background lighted with LEDs and a little underline flashing in the top ->
The screen goes entirely black, as if it was turned off ->
The little flashing underline comes back, and the LEDs ->
A ubuntu loading screen comes up, and in the middle of it, the screen goes black and the screen says "No signal detected", and it goes black as if it's off again, this time for good =p


I CAN choose safe mode or whatever it's called and choose to get a command line in the menu, though?

---

### Post by Hmmster on 2011-01-19
I press what OS i want to use ->
The screen goes black, but background lighted with LEDs and a little underline flashing in the top ->
The screen goes entirely black, as if it was turned off ->
The little flashing underline comes back, and the LEDs ->
A ubuntu loading screen comes up, and in the middle of it, the screen goes black and the screen says "No signal detected", and it goes black as if it's off again, this time for good =p


I CAN choose safe mode or whatever it's called and choose to get a command line in the menu, though?

---

### Post by Hmmster on 2011-01-19
EDIT: Now this is just ridicilous, if the server makes this many double posts, something is terribly wrong.

---

### Post by Hmmster on 2011-01-19
> **theDaveTheRave said:**
> Just thinking 'aloud' as it were....

What is the complete error message that you get? I guess you have searched for it in google, what what the advice?

I guess you don't even get to a cli login? if you do have you tried starting X from here?
[code]startx[code]

if you can post any output that would be great.

Otherwise check the contents of the following folder

/usr/lib/X11/xinit

and compare with the same on the liveCD.

David
Nothing comes up on the screen OS-wise, my SCREEN just says "No signal detected", which it would say if i were to example put it on without anything plugged in except power cable.

And the content of the folder seems to be identical.
And no, i do not get a cli login.

---

### Post by theDaveTheRave on 2011-01-19
Ok so you can get a CLI if you log in via safe mode, that is at least something.

Try what I suggested about starting x from the cli in safe mode.

see what errors you get.

Then after making a note of them, try to fix any broken packages...

```
sudo apt-get -update
``` to re-synch any problem source files
```
sudo apt-get -check
``` to see what is broken, hopefully something about X
```
sudo apt-get --fix-broken
```  to repair it..

followed by 

```
sudo apt-get -upgrade
``` to install the lastest version of any of the installed files

Also looking back to your original post, you could try uninstaling the ATI drivers that you had downloaded - this will require for you to find where they are installed, and then find the 'uninstall' script for them.


and finaly, maybe you should do a dist upgrade, if it is available (I'm assuming you aren't running 10.10)?

Last option, that I  can think of...

If you have space on your HDD, create a dual boot with a 'clean install' to a separate partition. Then it should just be a matter of linking in the correct directories / installed packages from /etc and /bin for example.

Do you also have an 'on board' video output from your motherboard (I assume the ATI card is an added plugin. If so have you tried using this output port rather than the ATI card, remember you may need to change your BIOS on re-boot to tell the pc not to use the ATI card (or something).

David

---

### Post by theDaveTheRave on 2011-01-19
I hate to say it but I'm running low on ideas, and I can't really tell exactly what the problem is.

I'm no longer sure if you can get a CLI via safe mode or not?

I think you may have to give it up as a bad experience and re-install, again if you have space on your HDD do a dual boot with the new install, that will at least give you 'breathing space', and you should be able to simply copy across the wine folders.

I'll keep checking back on your progress, but I need to rest the brain cells for a while.

David

ps, I agree about the multi post thing, I keep getting 'server not responding' messages, when I suddenly realised that in actual fact the posts where being made, I was just getting an error message because the acknowledgement was taking so long!

---

### Post by Hmmster on 2011-01-19
Okay, i'm not sure what exactly a CLI is, but through safe mode i can get a terminal window, granted i don't log in or anything in it, but it's still a terminal-like window. =p

So, typing in "startx" made tons of text get in there really fast, and after about one and a half second the screen went black and said "No signal detected" as usual.

Fixing broken packages went fine
Typing in "sudo apt-get check" got me
> 
Reading package lists...Done
Building dependency tree
Reading state information...Done

And typing in "Sudo apt-get --fix-broken" just got me the apt-get help screen

Yes, i'm running 10.10'

And as said, i followed this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

You can probably find there where it became installed.

And as i've said before, when i tried installing ubuntu 10.04 through this LiveCD nothing new turned up in my grub choose OS thingy, so i guess the install failed somehow? :S
I guess i'll have to try again.

---

### Post by Hmmster on 2011-01-19
Okay, i'm not sure what exactly a CLI is, but through safe mode i can get a terminal window, granted i don't log in or anything in it, but it's still a terminal-like window. =p

So, typing in "startx" made tons of text get in there really fast, and after about one and a half second the screen went black and said "No signal detected" as usual.

Fixing broken packages went fine
Typing in "sudo apt-get check" got me
> 
Reading package lists...Done
Building dependency tree
Reading state information...Done

And typing in "Sudo apt-get --fix-broken" just got me the apt-get help screen

Yes, i'm running 10.10'

And as said, i followed this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

You can probably find there where it became installed.

And as i've said before, when i tried installing ubuntu 10.04 through this LiveCD nothing new turned up in my grub choose OS thingy, so i guess the install failed somehow? :S
I guess i'll have to try again.

---

### Post by theDaveTheRave on 2011-01-19
OK,

so follow the guide for 'testing' the instalation and then use the info for removing it if you have had a problem.

for info CLI and 'terminal window' are the same thing. I doubt that you have a 'terminal window' as the term window would imply you have a working GUI desktop. You do have a screen that shows just the prompt however, and no decorations around the outside - you effectively have a terminal prompt.

Whilst you are there, I suspect that you have upset GRUB somehow, and that is why you aren't getting a list of available systems to boot into. Have a hunt on the forums for how to turn this off and on. I have it turned off on my system, with a 5 second interval where I can press escape and get the menu should I need too, yours may have been set to 'zero' seconds, so try pressing escape when you boot up to see if you get a grub menu. [Here is the grub info stuff courtesy of Ubuntu Geek]("http://www.ubuntugeek.com/show-and-hide-the-grub-menu-on-ubuntu.html")

David

---

