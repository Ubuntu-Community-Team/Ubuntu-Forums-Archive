---
title: "Installation Problem: Stuck on initial splash screen"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by haider254 on 2007-02-25
Hi,

Linux newb here!  Installed it a few times at uni, but very noobish!

My problem is as follows,  whenever I try to install Ubuntu, I go through the usual things, I get it to boot from CD,  select the "install ubuntu" option,  and that is as far as I get!  It just freezes on the Splash Screen [(PIC)]("http://www.haider.1g.fi/ss.jpg")

I've tried the 32bit version,  64bit version, ultimate edition, 64bit alternate install....

I installed ubuntu once,  but my computers been gutted and had some parts replaced since... Parts are as follows:
CPU:  AMD Athlon 64  3500+
RAM: Corsair TWINX1024-3200C2PRO
Mobo: ASRock  939Dual-VSTA
GFX Card: Winfast Nvidia PX 7900 GS TDH 
HD:  2 IDE drives (120gb, 60gb) (don't recall makes or models)

Connected Peripherals:  Lacie USB HD (500gigs, NTFS format), Samtron 19inch CRT, Logitech MX1000(USB), Logitech Comfort keyboard(PS2), Benq W100 Projector

That's all I thinks...

Any help would be appreciated,  I'm getting tired of running a cracked copy of windows...

---

### Post by haider254 on 2007-02-25
one thing I forgot to mention:

I managed to install Mandriva 2007.  But I can't get to the GUI,  I'm stuck at the terminal,  when I try to initiate the GUI it tells me that I have "no devices" connected.

I would much prefer to use Ubuntu though,  so help installing that would be much appreciated ;)

---

### Post by aerie on 2007-02-26
Hi I'm new to ubuntu too and I have exactly the same problem, I get the same screen when starting the live cd. I tried to install 6.10 desktop amd64 say 20 times and the live cd started twice. After that I've tried:

6.10 alternate amd64
6.10 kubuntu amd64
6.06 desktop amd64
6.06 alternate amd64
6.06 desktop i386
6.06 alternate i386
debian-31r3-i386-binary-10

none of them worked, got freezed after:

Uncompressing linux... OK, booting the kernel.

except for debian which didn't even do that.

md5 sum is correct for all and I burned the cd's as slow as my drives (cd burner and dvd burner) let me.
I disabled ACPI options of the BIOS, tried with only one memory bank ( by the way, the memtest didn't show anything wrong), disconnected the SATA HD and put an old ATA samsung 4GB..... and nothing.
I downloadad an iso image based on slax with wifi tools for linux,didn't take too much care about burning it slow, and this live cd it worked perfectly from the begining.

I've seen a couple of threads with problems starting the live cd with AsRock motherboards
with ULi chipsets.....

Anyway I'll never give up

AMD Athlon 64X2 4200+ 
Dual Channel 2x1024Mb Kingston PC2-5300
AsRock AM2XLi-eSATA 2 (ULi 1697 Chipset)
ATI RADEON X550 PCI Express 
MAXTOR sATA 250 GB

---

### Post by haider254 on 2007-02-26
thought I would bump this up,  there seems to be a couple people with this problem...

---

### Post by aerie on 2007-02-26
I forgot to say that I have a SMC WiFi adapter and a TV tuner. I'm going to disconnect them from the board and try again. In the begining I was suspecting of the ATI card but since you have nvidia..

---

### Post by aerie on 2007-02-26
definitely the pci cards are not the problem, I keep getting the same screen.

---

### Post by aerie on 2007-02-27
well, I managed to start 6.06.1 i386 live cd. My card reader was to blame, I unplugged from the motherboard and the cd worked.

When the live cd starts up press F6 and delete the "quiet-splash" ending (only this), then type in "break=bottom" and boot with it. This way you will see where it fails and may be it will give you a clue for further searching in the forum.

---

### Post by aberry5555 on 2007-02-27
I think this problem is the display drivers, after the "break=bottom" part you will get a command line, try the following: 

```
chroot /root nano /etc/X11/xorg.conf
```

scroll down till you find a heading called "device" under which should be a sub-heading saying "driver". to the right of it will be the name of the driver in inverted commas, change whatever this is to "vesa". now do ctrl+O then ctrl+X to exit the text editor and, when the command line comes back up type in

```
exit
```

Hopefully that might have helped, post back to say how much further you got.

---

### Post by aerie on 2007-02-27
I don't actually  want to steal haider254's post but when trying to start the 6.06.1 i386 live cd it froze showing this line:

[17179588.880000] ohci_hcd 0000.0013.0:OHCI Host Controller

so I suspected of USB devices. since I disconnected my card reader and the live cd started. Then I tried  ubuntu 6.10 desktop amd64 and now is installed in my samsung ATA HD and I'm typing this post from it. ubuntu recognized all the devices even the wifi adapter and connected to internet directly. Now I'm going to change the screen's refresh rate, if I figure out how, because 60Hz is killing me!!

So Haider254 don't lose hope!

---

### Post by haider254 on 2007-02-27
> **aerie said:**
> I don't actually  want to steal haider254's post but when trying to start the 6.06.1 i386 live cd it froze showing this line:

[17179588.880000] ohci_hcd 0000.0013.0:OHCI Host Controller

so I suspected of USB devices. since I disconnected my card reader and the live cd started. Then I tried  ubuntu 6.10 desktop amd64 and now is installed in my samsung ATA HD and I'm typing this post from it. ubuntu recognized all the devices even the wifi adapter and connected to internet directly. Now I'm going to change the screen's refresh rate, if I figure out how, because 60Hz is killing me!!

So Haider254 don't lose hope!

Gonna try out some of the suggestions here... check out the screen I have open as I read this:

[http://www.overclockers.co.uk/showproduct.php?prodid=SW-037-MS&groupid=33&catid=20&subcat=](http://www.overclockers.co.uk/showproduct.php?prodid=SW-037-MS&groupid=33&catid=20&subcat=)

---

### Post by haider254 on 2007-02-27
> **aberry5555 said:**
> I think this problem is the display drivers, after the "break=bottom" part you will get a command line, try the following: 

```
chroot /root nano /etc/X11/xorg.conf
```

scroll down till you find a heading called "device" under which should be a sub-heading saying "driver". to the right of it will be the name of the driver in inverted commas, change whatever this is to "vesa". now do ctrl+O then ctrl+X to exit the text editor and, when the command line comes back up type in

```
exit
```

Hopefully that might have helped, post back to say how much further you got.


Now,  I followed Aerie's lead and disconnected my USB HD,  that managed to get my Alt Disks OEM installer rolling.   Managed to install it (takes longer than I remembered) and now I have it to the point where I can run the revovery mode,  but not the GUI mode,  when I try I get the following on the screen:

[img]http://www.haider.1g.fi/pic/ubprob.jpg[/img]

Now, I assume it's an issue with them there display drivers as ubuntu seems to be running in the background, when I hit the power button, it seemed to go through some kind of shutdown procedure. Now, I assume if I type all of that into the command line it will have the same effect as doing it on the boot screen thingy,  so I'll try that in a bit...

But please do advice further ;)  :popcorn:

P.S.  Ignore the flowery patterned wallpaper...

---

### Post by aerie on 2007-02-27
If you can enter in the recovery mode that's because you have installed the OS, right?

Start the computer and press ESC in order to get the recovery mode again. After ubuntu does its tasks you will get the command line, something like this:

root@alvaro-desktop:~#          (this is in my case ..)

then type:

nano /etc/X11/xorg.conf    (be careful it's X11 not x11 and leave an space between nano and /)

it opens an editor. Then search for something like this ( in your case instead of ATI you will get nVidia....) :

Section "Device"
                Identifier         "ATI Technologies, Inc. Radeon X600 (RV370)"
                Driver               "ati"
                Bus ID              "PCI:1:0:0"
End Section

in the "Driver" line replace what you get with "vesa" (in my case "ati"). Then save the file (Control+O) and exit (Control+X) you get the command line again, type startx end press enter
that will start X (I hope so).

(By editing this file I fixed my screen refresh rate issue,from 60Hz to 85Hz but instead of "Device" section I edited the "Monitor" section VertRefresh).

Sorry if my posts are not very clear but english is not my native language.

---

### Post by haider254 on 2007-02-28
> **aerie said:**
> If you can enter in the recovery mode that's because you have installed the OS, right?

Start the computer and press ESC in order to get the recovery mode again. After ubuntu does its tasks you will get the command line, something like this:

root@alvaro-desktop:~#          (this is in my case ..)

then type:

nano /etc/X11/xorg.conf    (be careful it's X11 not x11 and leave an space between nano and /)

it opens an editor. Then search for something like this ( in your case instead of ATI you will get nVidia....) :

Section "Device"
                Identifier         "ATI Technologies, Inc. Radeon X600 (RV370)"
                Driver               "ati"
                Bus ID              "PCI:1:0:0"
End Section

in the "Driver" line replace what you get with "vesa" (in my case "ati"). Then save the file (Control+O) and exit (Control+X) you get the command line again, type startx end press enter
that will start X (I hope so).

(By editing this file I fixed my screen refresh rate issue,from 60Hz to 85Hz but instead of "Device" section I edited the "Monitor" section VertRefresh).

Sorry if my posts are not very clear but english is not my native language.

Your english is fine ;)

Appreciate the help,  I have to go Uni now, but when I get home I'll get ubuntuing and see if I can sort this out ;)

Any idea about the Bus ID,  mine is running from PCI-E,  do I need to edit that? or just hope it works :D

---

### Post by haider254 on 2007-02-28
Well that done it!

Danke indeed...

Now to personalise this whole thing ;)

---

### Post by haider254 on 2007-02-28
After a few hours messing around with this I've realised there is a lot to configure and install!
-NTFS Hard drives are all Read-Only
-Sound doesn't work
-videos don't work
-Can't get a resolution higher than 800x600
-The display is sooo twitchy,  man, this is confusing!!

This is gonna take some time...

---

### Post by aerie on 2007-02-28
Mine is PCI-Express too and works perfectly.Only change one thing each time you edit xorg. If this way you start the GUI then you should look for some nvidia drivers and install them.

---

### Post by aerie on 2007-02-28
I think you need some codecs for video just like windows, I can't see videos too. I don't know anything about sound problems. The display is that bad because you are running vesa drivers and are quite old. Use "Search"  option of the forum, type nvidia video drivers or something similar and see what you get, that's what I did.

---

### Post by haider254 on 2007-02-28
> **aerie said:**
> I think you need some codecs for video just like windows, I can't see videos too. I don't know anything about sound problems. The display is that bad because you are running vesa drivers and are quite old. Use "Search"  option of the forum, type nvidia video drivers or something similar and see what you get, that's what I did.
yeah,  I'm trying to find a guide,  but the ones I've tried so far have run into problems :(

---

### Post by haider254 on 2007-02-28
I managed to get it almost done! I used the guide below!   All I have to do is sort out this refresh rate and then my graphics will be sorted ;-)  55hz gives you a headache quicker than I would have thought :D

[http://doc.gwos.org/index.php/Install_Nvidia_other_drivers](http://doc.gwos.org/index.php/Install_Nvidia_other_drivers)

---

### Post by aerie on 2007-02-28
That's why the first thing I did was change refresh rate :) 
I'm happy to see that you have fixed some problems.
I told you, don't lose hope. I think this is going to be my ubuntu motto:) 
Good luck from now on. I'm going to "explore" my new OS a little bit to get used to it.

---

### Post by SaddisticTwist on 2007-02-28
[http://www.ubuntuforums.org/showthread.php?t=370895](http://www.ubuntuforums.org/showthread.php?t=370895)

I had that problem too. But I got the Live CD to work (The link above).

But I havent figured out how to get passed it after I've installed it.

---

### Post by aerie on 2007-02-28
I have a link for you, the name of the page is very promising ;)



[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by aerie on 2007-02-28
I'm sorry, the link was for haider254 I didn't want to mislead you. This is the first time I participate in a forum and I'm a bit clumsy.

---

### Post by SaddisticTwist on 2007-02-28
That link did not help. That link is for installing "things" in Ubuntu. Were stuck installing Ubuntu , either that or stuck after installing ubuntu.

---

### Post by aerie on 2007-02-28
well I'm sorry, as I said, the post was for haider254.
your problem comes when installing ubuntu or you have installed it and does not load the GUI?

---

### Post by haider254 on 2007-02-28
> **SaddisticTwist said:**
> That link did not help. That link is for installing "things" in Ubuntu. Were stuck installing Ubuntu , either that or stuck after installing ubuntu.

I can't be sure but I think once you have the Live CD running you can install it on-the-fly...   I think I done this once during some lab work at Uni...  Have a look around,  see if you find like an installer...


Thanks for the link aerie ;)


My problems now are as follows:
- Sound doesn't work  (Sound card isn't listed in alsa, but reading around the ubuntuforums looks like people have solved it) C-Media CM6501 is my intergrated sound card
- It wont boot with any USB media connected (Flash stick or external hard drive) this isn't a huge problem.
- All of my NTFS drives appear read only!  I've managed to mount them, and I went through some procedure which was supposed to make the writeable, but it just tells me root is the owner, when I login as root and try to change to writable it tells me it's a read only drive and I can't change it.

Any help with the above subjects and I might take this OS on full time ;)

BTW,  Ubuntu isn't like windows where you have to format every year to keep your system clean?  doing this on a yearly basis might get a bit tiresome,  although once you get the hang of it it isn't that bad, I had to reinstall graphics drivers again and after 6 hours of figuring out how to do it the first time I got it done in like 15 minutes :D

EDIT:  I have an old Sound Blaster laying around which I'll consider throwing in (if I have any PCI slots left :P),  gonna try that tomorrow,  will take care of one issue... I do prefer my Onboard sound to the Creative one though :(

---

### Post by aerie on 2007-02-28
About the USB HD, connect them,  then start the computer,when grub loads, try to keep pressed num-lock button till  the kernel is loaded and ubuntu splash screen appears and see what it happens.

I don't know if you have fixed the codecs, if not try :

[http://www.getautomatix.com/]("http://www.getautomatix.com/")  

.This program install a series of utilities, codecs and even nvidia video drivers. Yaou only have to check the options you want to install.

---

