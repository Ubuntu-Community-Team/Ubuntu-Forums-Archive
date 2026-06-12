---
title: "Installing 8.04 onto Acer Aspire 1350 - not running desktop"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by nigelm187 on 2008-07-07
Hi,

I have installed Ubuntu 8.04 Alternate CD onto an Acer Aspire 1350. The installation completes ok. On reboot, all seems to start ok until :

'running local boot scripts'

then it all stops.

I have tried modifying the grub menu - added vga=771 to the boot line

The boot then goes further until the login prompt. The screen flashes three times:

flash - one second delay - flash - one second delay - flash

then that's it. I can login at the prompt. If I try to startx, a message something like 'no screens found' displays

Any ideas how I can get this laptop to boot up properly.

Many Thanks

Nigel.

---

### Post by nigelm187 on 2008-07-07
Fixed the problem

Update the Monitor section to include the Horizontal and Vertical Refresh Rates:

Section "Monitor"
    Identifier "Monitor0"
    HorizSync 31.5 - 48.5
    VertRefresh 59.0 - 75.0
EndSection

then type startx, all works ok now....

---

### Post by Gmorales on 2008-08-31
Hi,

I'm a complete newby. I too have an Acer aspire 1350. I tryed the instal with the normal CD : failed. With the alternate, It seemed to work better but my display is full of scratches, impossible to read what is on it. So, NIGELM, could you eventually tell me how to procede in order to do this :
Section "Monitor"
Identifier "Monitor0"
HorizSync 31.5 - 48.5
VertRefresh 59.0 - 75.0
EndSection

At what point do I need to enter this - and how? 

Regards

Gerald

---

### Post by Pumalite on 2008-08-31
Backup your file:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
Edit:
gksudo gedit /etc/X11/xorg.conf

---

### Post by Gmorales on 2008-08-31
Pumalite, thank you- but as I am very new to this (I am a Mac user and not familiar with command-line at all), can you tell me at what stage I enter these lines? 
A precision: ubuntu is not installed yet - as I have this screen problem. 

Gerald

---

### Post by joshis on 2008-09-01
Hi Gmorales!

1. Insert LiveCD and boot (as you have problem with your screen, you will get only a command line - I assume you are in the console after booting the live CD)

2. type "sudo vim /etc/X11/xorg.conf", hit enter (vim editor opens)

3. find the section "monitor" in the file using the up/down keys
4. press 'I' (this will start the editor's insertion mode)
5. add these two lines inside the section (try to type patiently, vim editor is not too user friendly for newbies):

HorizSync 31.5 - 48.5
VertRefresh 59.0 - 75.0

6. press Esc (quit edit mode that you started by pressing I)
7. type ":wq!" (you will see :wq! in the bottom of the screen) and press Enter (commands Write+Quit with no prompt were executed, you are back to command line, you have edited the xorg.conf file)

8. type "startx" on the command line
-> Xserver is started

Thank you "nigelm187", this post helped me a lot (my Acer is happily running on 8.10 now;-))...

---

### Post by Gmorales on 2008-09-01
Joshis, thank you but when I start with the CD, I don't get a command-line but the graphic installer. After the choice of language, I get "Loading linux kernel" and then my screen gets unreadable - zigzags...
I tryed F4 for "instal command-line" and I get the same result. So, how can I get a command line at start?

---

### Post by joshis on 2008-09-01
Interesting - I didn't have this problem... What happens if you press Ctrl+Alt+F1 in the situation the screen is "zigzags"? Doesn't it give you a termial either?

---

### Post by Gmorales on 2008-09-01
No. Control-alt F1 does not do anything. Control-alt-F2  goes on a black screen with a line in zig-zags not readable at all... I assume this is the control line, but not usable. I'm stuck.

---

### Post by joshis on 2008-09-01
Well, maybe one more shot in the dark: press F6 before you boot the LiveCD and append " VGA=791" to the boot options. Otherwise, someone smarter than  I must come to help you...  

(Also, do you really have acer aspire 1350 laptop?)

---

### Post by Gmorales on 2008-09-01
Thank you for your help. The exact model is: Acer aspire 1355LC.
I try the F6 advice and I keep you informed.

---

### Post by Gmorales on 2008-09-01
F6: I get a command-line below the graphic interface, but whatever I enter there makes nothing special and continues the installation. There, I always get this zigzag screen...

---

### Post by joshis on 2008-09-01
And what did you choose from the menu? Did you try to start LiveCD or run installation? Do not select the install option, just run the live CD (I think the option is "Try Ubuntu without installing")...

PS: I have exactly the same laptop, I bet we can make it working somehow - Ubuntu is problem-less after you install it otherwise... When you are out of patience, Ubuntu 6.10 works on 100% with the laptop - then you can go through the updates (over 7.04, 7.10, 8.04), but you will need a day (a lot of downloading)...

---

### Post by Gmorales on 2008-09-01
joshis, thank you for your answer. I wa actually using the alternate CD. This explains why I could not see the command-line. Now I will try again with LiveCD. More news in several minutes.

---

### Post by Gmorales on 2008-09-01
Oooops. I followed the instructions
HorizSync 31.5 - 48.5
VertRefresh 59.0 - 75.0
under Monitor.
startx - it seemed to go a bit futher but now I have a black cross on a grey screen and nothing happens. Maybe I should go for a 6.0 version with updates as you adviced previously.

I keep you informed.

Gérald

---

### Post by Gmorales on 2008-09-01
Silly question :
When editing in vim, should I do: TAB HorizSync TAB 31.5 - 48.5 
Should I put the signe : " before and after 31.5 - 48.5 ?

Gerald

---

### Post by Gmorales on 2008-09-01
That whas this.  I needed the tabs and the sign ".
Now, I am almost there. As I have added these two lines, when I do startx, the command line returns Fatel server error: no screens found - giving up.

Should these two lines go before of after Identifier "Configured Monitor"?

Gerald

---

### Post by Gmorales on 2008-09-01
This is obviously a syntax problem as I am not familiar at all with the command line. II tryed :
	HorizSync	"31.5"		"48.5"
	VertRefresh 	"59.0" 	"75.0"

And still have "Fatal server error: no screens found"

Sorry for this, any clue is welcome.

Gérald

---

### Post by Gmorales on 2008-09-01
Do I need to add: Identifier "Monitor0" after Section "Monitor" ?

---

### Post by joshis on 2008-09-01
Well, I used tab in the beginning, tab after monitor and spaces around '-'.... Identifier must be the same as in a "screen" section...

In any case, this is my xorg.conf file (or you can download it from here: [http://joshis.iprofil.cz/resources/xorg.conf):](http://joshis.iprofil.cz/resources/xorg.conf):)

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync	31.5 - 48.5
	VertRefresh	59.0 - 75.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by joshis on 2008-09-01
This is a correct link:

[Ubuntu 8.04/8.10: xorg.conf for Acer Aspire 1350]("http://joshis.iprofil.cz/resources/xorg.conf")

---

### Post by Gmorales on 2008-09-01
joshis, thank you very much for your help - but unfortunatly, it did not work.
I did it all looking closely at your file, maybe there is another problem. Investigating at the specs of my model, it seems that I only have 192M of RAM. This is maybe the reason why the install does not go further... I'll try with a lighter version - maybe xubuntu desktop... And I'll buy memory next.

---

### Post by Gmorales on 2008-09-01
yaaaaaaaw. wiiiiiiiiiii!!!! Xubuntu works. It was a memory problem. Pffff.

---

### Post by Gmorales on 2008-09-01
Nop. Finally, I get the xubuntu interface, but everything freezes. I don't get it.

---

### Post by Pumalite on 2008-09-01
Maybe you should try a smaller distro, like DSL or Puppy

---

### Post by Gmorales on 2008-09-02
Finally, finally. I bought some memory and now it works almost... One last thing. When I start the computer, it asks me to choose between Windows and Xubuntu. I choose Xubuntu and it goes again to the command line and I have to re-do all the process: sudo vim /etc... to change the HorizSync and VertRefresh. How can I avoid this?

---

### Post by joshis on 2008-09-03
Yes, it is true - I have additional 256MB RAM in my notebook, this might be a difference...

> When I start the computer, it asks me to choose between Windows and 
> Xubuntu. I choose Xubuntu and it goes again to the command line and I 
> have to re-do all the process: sudo vim /etc... to change the HorizSync 
> and VertRefresh.

Strange, when you modify the file, it should stay modified(?)... When you boot in Xubuntu, try to start command line and type:

sudo mousepad /etc/X11/xorg.conf

Editor is opened, when you modify the file and save it, the change should be persistent, desktop should be started with no problems...

---

### Post by Gmorales on 2008-09-03
Joshis, first of all, thank you so much for your help. Now everything works 100%. Starting the computer is perfect, things work, I am starting to understand the system.
It's cool and very fast.

Gérald

---

### Post by yozgoesdigital on 2008-10-07
Try to install Kubuntu on aspire 1350 (with udal boot next to XP). I encounter similair problems and I assume the solution will be the same as installing ubuntu. I also am a newbe.

Small summary of attempts:

- tried different cd's, dvds same problem (as well ubuntu as kubuntu)
- Adding "vga=771 or 791" with f6 for live cd did not work. ends up in text modus when trying to change xorg.conf with vim get only purple signs at left and no possibility for giving commands.

-directly install from start menu gives a freeze with a few flashes on the screen after " running local boot scripts /etc/*something* [OK]" It also flashes a few times.

Specs 
Acer aspire notebook 1350
704 mb ram
AMD athlon 2400+ 469 mhz

Greetings (and thanks already) Jos, if more info is needed please let me know

Had to retype this message so when not knowing by head replaced by italic writing.

---

### Post by yozgoesdigital on 2008-10-07
Just after submitting the previous message I saw a typo. X11 i used a noncapital x. Right now the notebook is working on live disc and I start to install it.

thanks for the answers in this thread, Jos

---

### Post by jeggerleg on 2008-11-03
> **joshis said:**
> Well, maybe one more shot in the dark: press F6 before you boot the LiveCD and append " VGA=791" to the boot options. Otherwise, someone smarter than  I must come to help you...  

(Also, do you really have acer aspire 1350 laptop?)

I do, and can't install Ubuntu on it either.  Forgive me, but isn't Linux reputed to be better?  I've installed various flavours of Windows from 3.1 to Vista and have never had the problems I'm having trying to install Ubuntu.

---

### Post by joshis on 2008-11-18
> **jeggerleg said:**
> I do, and can't install Ubuntu on it either.  Forgive me, but isn't Linux reputed to be better?  I've installed various flavours of Windows from 3.1 to Vista and have never had the problems I'm having trying to install Ubuntu.

This is difficult to say - what do you mean by "better"? I believe this is up to requirements and thus I do not dare to judge this. I am using Kubuntu 8.10 on laptop (Acer Aspire 1350), Ubuntu 8.10 on desktop and WindowsXP Home at home, as need it for one specific application (I won't write which one otherwise I am finished here:-D)... simply every OS has it's pros and cons...

I would say it this way (diplomatic answer): **"Better operating system is the one you better understand, Linux is harder to understand for newbies (which is me too)."**

But back to the thread subject... **Basically said: starting from Ubuntu 7.10, I guess, you cannot easily install (K)Ubuntu on Acer Aspire 1350 due to problems with graphics.**

What I suggest you if previous steps did not help you: **Find a Ubuntu 7.04 distribution, install this one and go through the sequence of updates to 8.10.** It is not comfortable but I guess it should work. You can go through the "update cycle" using a command line (and clicking through the update manager):

[FONT="Courier New"]$ sudo apt-get update; sudo apt-get upgrade; sudo update-manager --dist-upgrade[/FONT]

I hope that helps, please do not start another useless flamewar about which operating system is worse/better.

Joshis
[http://wiki.netbeans.org/PetrDvorak](http://wiki.netbeans.org/PetrDvorak)

---

### Post by tqzxzjhu on 2008-11-18
[&#24231;&#20415;&#22120;&#30095;&#36890;](http://classad.dahangzhou.com/223685.html)[&#23567;&#20415;&#27744;&#30095;&#36890;](http://classad.dahangzhou.com/223685.html)[&#21397;&#25152;&#30095;&#36890;](http://classad.dahangzhou.com/223685.html)[&#22320;&#28431;&#30095;&#36890;](http://classad.dahangzhou.com/223685.html) [&#27700;&#27744;&#30095;&#36890;](http://classad.dahangzhou.com/223685.html)

---

### Post by jeggerleg on 2008-12-06
> **joshis said:**
> 
>snip
But back to the thread subject... **Basically said: starting from Ubuntu 7.10, I guess, you cannot easily install (K)Ubuntu on Acer Aspire 1350 due to problems with graphics.**

What I suggest you if previous steps did not help you: **Find a Ubuntu 7.04 distribution, install this one and go through the sequence of updates to 8.10.** It is not comfortable but I guess it should work. You can go through the "update cycle" using a command line (and clicking through the update manager):

[FONT="Courier New"]$ sudo apt-get update; sudo apt-get upgrade; sudo update-manager --dist-upgrade[/FONT]

I hope that helps, please do not start another useless flamewar about which operating system is worse/better.

Joshis
[http://wiki.netbeans.org/PetrDvorak](http://wiki.netbeans.org/PetrDvorak)

I had no intention of starting a flame war.  I'm quite happy with Ubuntu on my Dell laptop and after following your advice re: 7.04 have managed to install it on my Acer - thank you.

---

### Post by gehatzip on 2009-02-10
I had the same problem

Joshis' "xorg.conf" works perfectly!!!

---

### Post by martyyys on 2009-03-25
Thank you very much for the info on how to Update the Monitor section to include the Horizontal and Vertical Refresh Rates. I also have Acer aspire 1350, and this solved my problem with the ubuntu installation (ubuntu 8.04). Though, it did not work for ubuntu 8.10.

---

### Post by gio10 on 2009-04-24
I had the same problem on my acer aspire 1350.
I solved it on the 8.10 adding the HorizSynch/VertRefresh settings in the xorg.conf.

Now I updated to 9.04 and it does not work anymore.

The error messages in the Xorg.0.log are:

(EE) CHROME(0): No valid modes found
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screen found

Any suggestion?

Thanks

---

### Post by giulianisenior on 2009-04-25
I have the same problem... everything worked fine with the old Ubuntu releases up to 8.10. But now with Jaunty Jackalope (9.04) I get the same "screen not found error" when I try "startx". The exact name of my model is 1355LC (one flavor of the 1350 Acer Aspire notebook family). Could anyone help?

---

### Post by nacho@saski.com on 2009-04-26
Me too. I had ubuntu 8.10 working on my aspire 1350 with Joshi's HorizSynch/VertRefresh patch. But I've just updated to 9.04 and now it doesnt work.

Same error in the Xorg.0.log are:

(EE) CHROME(0): No valid modes found
(EE) Screen(s) found, but none have a usable configuration.

In /var/log/Xorg.0.log i've seen this:
"Primary device is: PCI 01@00:00:0
VIA Technologies does not support this driver in any way"

Please, post here any solution you may find
thanks!

---

### Post by giulianisenior on 2009-04-26
Now Jaunty works for my Acer Aspire 1350 (1355LC) notebook!!!
I followed these steps:
1) getting the latest openchrome source code 
2) decompressing the code
3) entering the newly created directory
4) compiling the source code
5) restarting the x-server
6) using Ubuntu 9.04 (Jaunty Jackalope)!

These are the commands I wrote:

1) wget [http://www.openchrome.org/releases/xf86-video-openchrome-0.2.903.tar.gz](http://www.openchrome.org/releases/xf86-video-openchrome-0.2.903.tar.gz)
2) tar xvzf xf86-video-openchrome-0.2.903.tar.gz
3) cd xf86-video-openchrome-0.2.903
4) sudo ./configure --prefix=/usr
... in this step I got an error concerning some missing libraries (xorg-server, xproto, xvmc, fontsproto, libdrm)... I solved these problems typing:
4-a) sudo apt-get build-dep xserver-xorg-core
4-b) sudo apt-get -f install
4-c) sudo apt-get install libxvmc-dev
5) sudo make
6) sudo make install
7) sudo /etc/init.d/gdm restart
8) then the X Desktop appeared!!!

I hope this can be of help!

---

### Post by nacho@saski.com on 2009-04-26
it works, thanks a lot, giulianisenior!
I've fixed it following your post and with some help grabbed here
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)
for the openChrome 2D driver compilation installation

---

### Post by Squirreltech on 2009-04-26
after step 4a i get this error:
could not open file /var/lib/apt/lists/us.archive.ubuntu.com_ununtu_dists_jaunty_main_source_sources - open (2 no such file or directory)

any ideas?
can i download these packages somewhere through my web browser on XP and install them manually(i have read write access to my ntfs xp partition). i'm somewhat new to this so the more detailed the better. thanks.

---

### Post by Squirreltech on 2009-04-26
I've updated and upgraded apt-get and not i ran all three of those commands 4a-4c and they seem to work, however when i run ./configure --prefix=/usr  it tells me that xserver-xorg is missing, however when i type apt-get install xorg-server it says it is installed. so i am at a loss. when i try to type make it does not work. can't rememer the error message, sure it has something to do with the fact that the compile didn't complete properly

---

### Post by modemlamer on 2009-04-26
xorg-server  still missing... 

xserver-xorg is installed... there is no package called xorg-server

---

### Post by modemlamer on 2009-04-26
the missing package is:


 xserver-xorg-dev


always the dev files ;)

type:

 sudo apt-get build-dep xserver-xorg-video-openchrome

and then:


sudo ./configure --prefix=/usr

again

and you're fine!

---

### Post by Squirreltech on 2009-04-26
no screens found still acer aspire 1355 LCI. should i put the vertrefresh rates and all that stuff into the xorg,conf file? what does your aspire 1355lc  xorg.conf file look like

---

### Post by Squirreltech on 2009-04-26
it worked it worked it worked

i added the refresh rates found on the first page and started x and it worked.

thanks all i am extremely happy

---

### Post by vintageveloce on 2009-04-28
This thread also allowed me to get the GUI up and running on my Averatec 3200 (AV3225HS) laptop for Jaunty 9.04. 
The key point being the Averatec uses the same VIA video chipset, I think.
I should note that I also had to edit my sources.list so that the required software could be found.
Thanks to all.
Carl

---

### Post by bonnyfused on 2009-05-18
So, here I am too with an Acer 1355XC...
I'm now up with Ubuntu 9.04 thanks to the steps indicated here (MANY THANKS!).

Now the question is: how do I get fluid video/graphics? The fact is that when I drag windows, I see them not fluid moving...

Thanks for any help!

B.

---

### Post by BluntedBoyWonder on 2009-06-23
:KS Thanks so much people,:KS these tips enabled me to install Jaunty on my Acer Aspire 1350 too! Little bit of extra work, but at least I have the latest Ubuntu again, after 8.1 which did not work either.

I have a little additional problem now that I've installed it. Maybe someone else has this too? Maybe it's just my hardware?

Whenever I try to use my two external harddrives, especially when scanning my mp3 collection with Amarok, Exaile, Nicotine+... anything I tried really, my entire usb support crashes after a minute and I have to reboot. My usb mouse, keyboard, anything I had connected won't work anymore. Sounds familiar to any of you fellow Aspire 1350 users? It's like something overloads and goed into a coma.

---

### Post by SKaRCHa on 2009-06-29
My solution was backport Karmic package to Jaunty:

[https://launchpad.net/ubuntu/karmic/+source/xserver-xorg-video-openchrome/1:0.2.903+svn741-1](https://launchpad.net/ubuntu/karmic/+source/xserver-xorg-video-openchrome/1:0.2.903+svn741-1)

This is the howto I followed to do it:

[http://www.tolaris.com/2009/03/31/backporting-debian-packages-with-pbuilder/](http://www.tolaris.com/2009/03/31/backporting-debian-packages-with-pbuilder/)

Hope this helps! ;)

---

### Post by NewBeeMichael on 2009-08-05
Hi!

"after step 4a i get this error:
could not open file /var/lib/apt/lists/nl.archive.ubuntu.com_ubuntu_dists_jaunty_main_source_Sources - open (2 no such file or directory)"

"type:
sudo apt-get build-dep xserver-xorg-video-openchrome
and then:
sudo ./configure --prefix=/usr
again"

Running this when LiveCD is inserted works perfect and I can even get the UI running, so that's where I installed the OS from. Now 9.04 is installed on the hard drive and having the same trouble again. Fighting it with the same solution as when the LiveCD was inserted doesn't help me at all, again I have the message: "could not open file /var/lib/apt/lists/nl.archive.ubuntu.com_ubuntu_dists_jaunty_main_source_Sources - open (2 no such file or directory)" after running: sudo apt-get build-dep xserver-xorg-video-openchrome...

I have really no clue anymore... Also changed the refresh rates in the xorg.conf file already, that doesn't help either.

Any idea's are welcome! Thanks in advance!

Cheers, Michael

---

### Post by NewBeeMichael on 2009-08-09
Hi all!

Finally found (after couple of days, grrrrr :mad:) what the problem caused. It appeared to be the time-zone setting during installation! If you choose Europe-Amsterdam, the links to the files that you need to perform "sudo apt-get build-dep xserver-xorg-core" and "sudo apt-get build-dep xserver-xorg-video-openchrome" are wrongly set. The files where it refers to really don't exist!

When I found that out, solution was pretty easy, just "fool" the system and select during install time zone North America-New York. Than run the story mentioned on previous page and set the HorizSync and VertRefresh rates in xorg.conf file. After that ubuntu 9.04 runs perfect on my Acer Aspire 1355LC!

Thanks everyone who posted the solutions!

Michael

---

