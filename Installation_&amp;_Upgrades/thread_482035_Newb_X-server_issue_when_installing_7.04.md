---
title: "Newb: X-server issue when installing 7.04"
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by El Bajong on 2007-06-23
Hey all

I've recently gotten myself an HP NC6400 laptop with an Intel Core 2 Duo CPU and an ATI Mobility Radeon X1300 graphics card. This is a wide-screen laptop, with the highest resolution available being 1440x900. I want to run this with Windows XP and Xubuntu dual booted, and XP has already been installed.

As for Linux systems, I'm entirely fresh to their workings, so my attempts so far at finding a solution to the problem on the web has ground to a halt due to my lack of insight, so to speak.

The problem is as follows:

I boot Xubuntu 7.04 from a CD (downloaded ISO for i386 systems from Xubuntu.org) and tell it to start a normal installation (the default option). It then starts a process of running loads of very technical-looking codes past the screen in a rapid fashion, looking very much like good old MS-DOS.

Then it stops, and a messy-looking screen appears, with a simple text box in the middle saying:
> Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the Problem?

Yes/No

I choose  "Yes" and get a lot of text and numbers that are fairly incomprehensible to me. In the last lines of this, I find what I assume is the core of the problem:
> (EE) VESA(0): No matching modes
(EE) Screen(s) found, but none have a usable configuration.

Fatal Server error: no screens found

I'm not able to get anything further done from this point, other than viewing an extremely detailed error report-thingy with seemingly thousands of lines of code. After viewing that, it tells me that X server has been disabled, or something along those lines, and I'm sent back to the previously seen MS-DOS-like screen which by now has ground to a complete halt, nothing further happens. I reboot the computer after being asked to remove the Xubuntu CD, and the computer starts up in Windows XP.

So, to a person with a fair amount of computer savvy, but no Linux/Ubuntu experience whatsoever, could you please explain whats wrong, and what I need to do to sort this? I really want to learn how to use Ubuntu as I'd rather be using this in the future than having to switch to Vista once XP starts dying out...

---

### Post by El Bajong on 2007-06-24
Someone did post a reply here saying that installing from an alternate install disc would solve it, but that answer disappeared for some reason. I've just tried that, but I ended up getting the same X server message after the installation was seemingly completed. The only difference this time was that it didn't freeze up after I had gone through the messages about X server, I went back into "MS-DOS-like" mode and was asked to input login/password. I entered the login, but for some reason, when i entered the password, nothing seemed to happen, it just wouldn't let me type anything.

So, I'm basically back to where I where when making my initial post. Any other ideas to solving this?

PS: I suppose I might have to get rid of the Xubuntu installation made by using the alternate disc, since its seemingly broken. How do I proceed to do that?

---

### Post by Bothered on 2007-06-24
Hmm, sounds a little like a problem I had with 6.10 installation with my ATI X600 card. I can't find the link right now, but I overcame it by editing /etc/X11/xorg.conf. The process:

1. Boot using the LiveCD until you hit the problem.
2. Change to a console using Cntrl+Alt+F6
3. Enter "sudo pico /etc/X11/xorg.conf"
4. Find the "Device" section and change the driver to "ati" (or "radeon" - I don't remember which worked - try one, then if it fails at step 7, try the other).
5. Save (Cntl+O) and quit pico (Cntl+X).
6. Enter "sudo /etc/init.d/gdm stop" and then "sudo /etc/init.d/gdm start".
7. Press Cntl+Alt+F7 - if you see a desktop then it's worked. If you don't see a desktop (after trying both ati and radeon drivers) then I'm way off the mark and don't proceed any further.
8. Run the installer for xubuntu if you want to install it, remembering to take precautions such as backing up etc first.
9. Once xubuntu has installed and the system restarted, the problem will probably recur (this time from the freshly installed system, rather than from the LiveCD). Change to a console again using Cntl+Alt+F6. Log in with the your username and password set up in the install.
10. Type "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak", and repeat steps 3, 4, 5, 6, and 7.

Hope this helps!

---

### Post by El Bajong on 2007-06-24
Thanks for the suggestion Bothered, but it fails at #7 for my part. After changing device driver to either "ati" or "radeon", stopping and starting GDM, I get the same "Failed to start the X server" message as earlier. The difference now is that when I check the "X server output", instead of the two errors listed in my first post, I find this:

> (EE) No devices detected

Fatal server error:
No screens found

Two things I should mention:
1. Ahead of giving me the "Failed to start the X server" message, the screen flickers a few times back and forth.
2. When looking through the "Device" and adjoining sections in xorg.conf, I notice that pretty much all information there says something like "Generic Monitor" or otherwise non-specified stuff. No actual hardware names listed for display related hardware.

---

### Post by Bothered on 2007-06-24
Looks like this bug has been come across before. I managed to find this, although this was a problem with wubi: [http://ubuntuforums.org/showthread.php?t=446210](http://ubuntuforums.org/showthread.php?t=446210)

---

### Post by El Bajong on 2007-06-25
The solution there is a tutorial for a Dell Inspiron 6400 specifically, including running scripts which are made for that computer in particular. Is it really safe to perform such an operation on my computer, which is an HP NC6400?

---

### Post by El Bajong on 2007-06-25
Could I possibly use this driver to fix the problem? [http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)

If so, how do I move it into the computer, and get it properly set up where it belongs? The computer is connected to a wireless network, at least when in Windows XP.

---

### Post by eapache on 2007-06-25
Try following bothered's explanation, but with a few tweaks:

- step two and seven are unnecessary. when x crashes, it should give you a prompt. try omitting them
- in step 6, use the command "startx" instead

If that doesn't work, please post the device sections of your xorg.conf file (the one you edit) for you monitor, your graphics card, and your screen.

---

### Post by El Bajong on 2007-06-25
The prompt I get after X crashes seems to be faulty, it generates a lot of weird codes whenever I use the left/right buttons, try to backspace, and so on. In other words, I had to press ctrl+alt+ F7

When I try entering "sudo startx" (I assumed this is what you asked me to do, but also tried writing sudo sudo /etc/init.d/gdm startx to be on the safe side) after having entered sudo /etc/init.d/gdm stop, the screen flickers a bit and gives me the "(EE) No devices detected" message in regular text format.

the xorg.conf readout:

> Section "Device"
   Identifier           "Generic Video Card"
   Driver                "ati"* [originaly said "vesa", have also tried entering "radeon"]*
   BusID                 "PCI:1:0:0
EndSection

Section "Monitor"
   Identifier           "Generic Monitor"
   Option               "DPMS"
EndSection

Section "Screen"
   Identifier           "Default Screen"
   Device               "Generic Video Card"
   Monitor              "Generic Monitor"
   DefaultDepth     24
   SubSection "Display"
       Depth                       1
       Modes                       "1024x768"  "800x600"  "640x480"
   EndSubSection
   SubSection "Display"
       Depth                       4
       Modes                       "1024x768"  "800x600"  "640x480"
    EndSubSection
   SubSection "Display"
       Depth                       8
       Modes                       "1024x768"  "800x600"  "640x480"
    EndSubSection
   SubSection "Display"
       Depth                       15
       Modes                       "1024x768"  "800x600"  "640x480"
    EndSubSection
   SubSection "Display"
       Depth                       16
       Modes                       "1024x768"  "800x600"  "640x480"
    EndSubSection
   SubSection "Display"
       Depth                       24
       Modes                       "1024x768"  "800x600"  "640x480"
    EndSubSection
EndSection

---

### Post by Pumalite on 2007-06-25
Time to try:

sudo dpkg-reconfigure xserver-xorg
startx

---

### Post by haden9 on 2007-06-25
Try using the xubuntu alternate cd, you can download it from here:

[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

Also I had the same issue with Ubuntu 7.04 so I followed this guide, but since you are using Xubuntu some comands in terminal may vary but this may be of use:

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

Good luck and plz post your outcome!!!!

:popcorn:

---

### Post by El Bajong on 2007-06-25
> **Pumalite said:**
> Time to try:

sudo dpkg-reconfigure xserver-xorg
startx

This is what happened when I tried that:

"sudo dpkg-reconfigure xserver-xorg" starts a blue/white screen thing, where it asks me if I would like it to autodetect. I answer "Yes", and it immediatly returns with a message under the heading "No X server known for your video hardware"

"There is either no video hardware installed on this machine (e.g. serial console only), or the "discover" program was unable to determine which X server is appropriate for the video hardware. This could be due to incomplete information in discover's hardware database, or because your video hardware is not supported by the available X servers."

I then get a list of video card drivers, where "vesa" is chosen by default. I look for "radeon" and "ati", with the latter being the only one present, which I then select. It asks me to enter a identifier for my video card, with "Generic Video Card" being given by default. Since "ATI RADEON X800" is given as an example, I try entering my card in the same format, "ATI RADEON X1300"

The next screen wants me to configure the BusID of my video card, if i am using a PowerPC machine or have got multible video devices. Since the answer to these questions to my knowledge are no, I leave it at that and proceed.

The next steps want me to enter an amount of dedicated RAM, but since I am unsure of the answer, I leave it blank.

I answer "yes" on the "Use kernel framebuffer device interface?" question.

I enter "no" for keybord layout, since it has a Norwegian layout.

I leave "xorg" entered in the field when asked for an XKB rule.

I enter "pc105" as keyboard model, since that seems to be the closest to my keyboard.

On the question of keyboard variant, I leave it blank, since I don't have the faintest idea of what would be the correct answer for my computer.

On the question of keyboard options, I leave this too blank, for the same reason.

I select "gpmdata" on the first mouse question.

I answer "Yes" on the question of whether or not to emulate 3 button mouse.

I leave the advanced checlist thing as it is.

On the question of whether or not to write default files section to configuration file, I answer "Yes".

I answer "Yes" on attempting monitor autodetection.

This seems to fail, as the following text field says something like "Generic Monitor". Per the suggestions in the text given, I try entering the computer brand and make here, "HP NC6400"

I select the following resolutions from the next screen, which are the ones I can use when in Win XP mode:
1440x900
1280x768
1152x864
1024x768
800x600

I select the "simple" method from the next screen, and then choose "Up to 14 inches", since the screen is 14.1".

I answer "Yes" to the question of writing monitor sync ranges to the configuration file.

I select 24 bits color depth, which ends the configuration tool.

I now enter "sudo startx" in the prompt, resulting in the by no familiar set of codes ending with

> (EE) No devices detected

Fatal server error:
No screens found

---

### Post by Pumalite on 2007-06-25
You are supposed to choose 'vesa'. Once in; then configure your video. Myself I use propietary drivers; in my case, NVIDIA. If you choose to go that route, contact me and I'll give you the recipe.

---

### Post by El Bajong on 2007-06-25
> **haden9 said:**
> Try using the xubuntu alternate cd, you can download it from here:

[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

Also I had the same issue with Ubuntu 7.04 so I followed this guide, but since you are using Xubuntu some comands in terminal may vary but this may be of use:

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

Good luck and plz post your outcome!!!!

:popcorn:

I tried this, but I am unable to get anything done at point 4/5, at #5, it tells me the following: "E: Couldn't find package xorg-driver-fglrx"

Might this possibly be caused by the computer not being properly connected to the web when in this mode? I know for sure that it's online when I log into Windows XP, but I haven't the faintest idea of the situation when in Linux/Xubuntu mode. How can I find out whether or not it is connected, and if the latter is the case, how do I actually get the Linux/Xubuntu part of the computer connected to the web while I'm unable to get into the "proper" OS?

---

### Post by haden9 on 2007-06-25
> **El Bajong said:**
> I tried this, but I am unable to get anything done at point 4/5, at #5, it tells me the following: "E: Couldn't find package xorg-driver-fglrx"

Might this possibly be caused by the computer not being properly connected to the web when in this mode? I know for sure that it's online when I log into Windows XP, but I haven't the faintest idea of the situation when in Linux/Xubuntu mode. How can I find out whether or not it is connected, and if the latter is the case, how do I actually get the Linux/Xubuntu part of the computer connected to the web while I'm unable to get into the "proper" OS?

If you get past the other points which do require you to be connected to the network (Xubuntu is getting update to the latest version prior to installing the fglrx driver) then you should have network up to that point as well. Perhaps you could try pinging a website to make sure you are still connected, or releasing/renewing the ip address with:

sudo ifdown eth0 (to release)

sudo ifup eth0 (to renew)

Thats a command that worked for me when I had this connectivity issue, you will see if it obtains or not an ip address that way too. I hope this helps!!!

---

### Post by El Bajong on 2007-06-25
I realize that this is something I really ought to know, but how exactly do I ping a website? (Did that question make me feel even more like a newbie or what :p)

I tried entering for example "ping www.google.com" and a load of other variations and websites, but I get the response "ping: unknown host www.google.com".

As for "sudo ifdown eth0", I get the following response (after entering my password): "ifdown: interface eth0 not configured".

"sudo ifup eth0" gives me this response: "Ignoring unknown interface eth0=eth0".

---

### Post by Ub1476 on 2007-06-25
Try this guide:

[Linky]("http://ubuntuforums.org/showthread.php?t=448809&highlight=HOWTO%3A+Installing+start")

Hope it works

---

### Post by haden9 on 2007-06-25
> **El Bajong said:**
> I realize that this is something I really ought to know, but how exactly do I ping a website? (Did that question make me feel even more like a newbie or what :p)

I tried entering for example "ping www.google.com" and a load of other variations and websites, but I get the response "ping: unknown host www.google.com".

As for "sudo ifdown eth0", I get the following response (after entering my password): "ifdown: interface eth0 not configured".

"sudo ifup eth0" gives me this response: "Ignoring unknown interface eth0=eth0".

I was wondering if by any chance when you installed Xubuntu, you had it connected to a network so that it could configure the DHCP settings on its own. In any case you did ping the website properly, what I would suggest perhaps is to try pinging 127.0.0.1 (local host) just to make sure that the network card is working in that environment.

Good luck!!!!

---

### Post by El Bajong on 2007-06-26
When pinging local host, it returns something like this:
> 64 bytes from 127.0.0.1: icmp_seq=5 ttl=64 time=0.011 ms

I tried the DHCP configuration thingy in earlier installation attempts, but wheren't realy able to get it working, so when I installed Xubuntu (seemingly succesfully, though without the X server issue being resolved) using the alternate disc, I just skipped that and said I'd do it later. What will I have to do to configure it now?

Isn't there anyway I can get hold of the required update(s) without direct web acces? Could I for example download the required stuff to this computer (a functional Win XP desktop), put it on a USB drive, stick this into the laptop and use Win XP which is installed and working there to unload it into a place on the laptop's harddrive where I am able to access it from in Xubuntu?

---

### Post by haden9 on 2007-06-26
Perhaps there are, I just wouldnt know since I use Ubuntu and I heard that they differ a bit somehow, but why not do this, just use the alternate install cd again, do everything from scratch and let the installation pick up the dhcp settings automatically, there you will know right away if it is being configured automatically or not. Anyways that is if you have network access, otherwise I would be able to tell you how to load updates onto a thumbdrive :( sorry there...

---

### Post by El Bajong on 2007-06-27
I tried the automatic configuration thing at first, but it didn't work, as far as I recal, it told me that it wheren't able to do it automaticaly. I thought "fine, I'll do it later" and left it at that.

Is it possible to get that part of the config tool up and running again without having to do another alternate disc install? I've already got three halfway botched alternate xubuntu installs, and I'd love to not have to make yet another one which would clog up the drive. I am planning on formating the disc once I've found the solution to this problem and set everything up properly from scratch, but I'd prefer not having to format it until I have solved this.

---

### Post by El Bajong on 2007-06-28
Good people, I finaly got through!

I did another install with the alternate disc to get the DHCP thing working. As usual, it wouldn't autoconfigure. What I did then, was quite simply inserting a network cable to the computer, and re-did the autoconfigure, which worked flawlessly. It appears that my problem was that the wirless connection wasn't really working in Xubuntu like it where in XP.

Thereafter, I followed the steps listed in link #2 underneath, and after rebooting, _it worked perfectly_!

> **haden9 said:**
> Try using the xubuntu alternate cd, you can download it from here:

[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

Also I had the same issue with Ubuntu 7.04 so I followed this guide, but since you are using Xubuntu some comands in terminal may vary but this may be of use:

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

Good luck and plz post your outcome!!!!

:popcorn:

The first thing I did when I got in was changing the look of the desktop (very intuitive and easy) to the darkest, cleanest, most beautifulest desktop layout I have ever seen. Not in my wildest dreams could I have dreamt of such a clean desktop look :)

Did try going online and tried out a few sites, where some worked and others didn't work that well, but I guess it'll need a lot more tweaking until it's running smoothly in all areas. I did read somewhere that firefox in Ubuntu didn't work with YouTube due to some Flash incompatabilities, but it worked flawlessly for me.

Anyways, since I've now got four seperate Xubuntu installations in addition to the XP one on the computer, the next thing I'll do is format it all, re-install XP and then get a single, clean Xubuntu install, and then start learning to use this beautiful thing.

Big, massive thanks to the patient and helpful people who helped me out with this :)

---

### Post by haden9 on 2007-06-29
Good to hear that you were able to come through!!!! Gotta love the glass effect and the OSX icon themes ;)

haden9

---

