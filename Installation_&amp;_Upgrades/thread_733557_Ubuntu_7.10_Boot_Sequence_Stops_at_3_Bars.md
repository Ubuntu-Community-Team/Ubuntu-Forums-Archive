---
title: "Ubuntu 7.10 Boot Sequence Stops at 3 Bars"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by Archboundmind on 2008-03-23
I'm trying to switch my desktop from windows xp to ubuntu 7.10.
computer specs:
E-machine T5010
2.93Ghz
200Gb 7200 RPM SATA Hard drive
1.58 Gb RAM
Intel Pentium 4 Processor 516 

I wiped my hard drive no problem - checked the integrity of the standard desktop version of the iso-image I burned = 100% no errors - no errors during installation, but when I try to run a live cd or boot from my hard drive the installed OS, it stops at three bars every time. I also tried the alternate cd available and it didn't work. I even tried xubuntu's latest version as well and everything stops at the same point. Is there any way I canfix this problem? thanks

---

### Post by Archboundmind on 2008-03-23
here's a photo :

[IMG]http://i120.photobucket.com/albums/o199/chaos_ghost/Picture.jpg[/IMG]

---

### Post by Archboundmind on 2008-03-24
Is there anyone that knows what I can do to fix my problem, - really need my computer for school purposes - thanks

---

### Post by forestpixie on 2008-03-24
Try booting it without the quiet option - then see where it hangs, if it can boot in recovery mode let it. Then when you get to the prompt do these - I don't think you need sudo in recovery, but if the commands don't work - try with it.

cp /boot/grub/menu.lst /boot/grub/menu.lst.2403

then edit the file with nano, to save the file after you've edited it use Ctrl+O, then enter and Ctrl+X to exit file.

nano /boot/grub/menu.lst

find the buntu you boot with and remove quiet and splash from the end

> ## ## End Default Options ##

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=3138a9d0-9916-4e95-8d8c-cad4d7576ba7 ro [COLOR="Red"]quiet splash[/COLOR]
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

You can alternatively edit the file at the grub menu screen - from [this]("http://users.bigpond.net.au/hermanzone/p15.htm#Temporarily_Edit_the_GRUB_Menu") page

Once you menu is up while the line you normally boot with is highlighted press 'e' this will allow you to edit it

use the arrow key to go to the kernel line and I think press 'e' again which should allow you to edit it - go to end of line and remove quiet and splash, then enter and then 'b'

which should boot without those two options - you should now see what is being loaded and can see what is causing the pc to hang hopefully.

---

### Post by Archboundmind on 2008-03-24
awesome, hopefully this works, I appreciate the help

---

### Post by forestpixie on 2008-03-24
So do I - not necessarily going to be able to help with the problem - but if it helps to get a bit more information here then I'll be happy.

---

### Post by Archboundmind on 2008-03-24
it looks like it hangs up in the sequence of codes following "hardware drivers" everytime, not sure what I need to do to fix that though?

---

### Post by forestpixie on 2008-03-24
you need to give a bit more information, paste some of the errors here and of course now you know what you're looking for try searching for some of the errors

---

### Post by Archboundmind on 2008-03-24
I see only one error, it shows 

[57.926583] [<c02f0000>] clip_ioctl+0x500/0x510
[57.926679] ==============

thats where it stops also

---

### Post by forestpixie on 2008-03-25
Not a great deal that I can find about that error - Have you tried reinstalling, or maybe as a last resort try hardy. Sorry can't be of more help :(

Try posting a thread in ABsolute Beginners.

Edit - you could also try asking the question here - [https://answers.launchpad.net/ubuntu](https://answers.launchpad.net/ubuntu)

---

### Post by VIPea on 2008-03-25
I'm experiencing this exact same problem :(
Can someone please help.

I was so excited when I received my CD in the post today, only to find it doesn't work..

---

### Post by Archboundmind on 2008-03-25
yeah, I appreciate the help though - I'll post some info if I can figure this out.
- yeah I've already tried 3 different cds for ubuntu including the alt-cd - all of them 100% integrity and md5s are good - no errors - then I've also tried the dapper drake ubuntu 6.06 version as well as xubuntu's latest version where none of them work on my computer haha - its so irritating - my laptop has been able to run every cd I've burned no problem, - I have suspicion in the hardware of my computer -computers 3 years old

---

### Post by VIPea on 2008-03-25
Yeah! Exactly the same here. I tried the disc on my laptop and it worked :S

---

### Post by forestpixie on 2008-03-25
> - yeah I've already tried 3 different cds for ubuntu including the alt-cd 

maybe hardy will crack it for you, can't really think of anything else that'd help as I said near the beginning but at least you know what is causing the problem for you.


I found this - but it looks a bit drastic - you could try adding it to the kernel line by editing grub temporarily rather than editing menu.lst. Like this

> Once you menu is up while the line you normally boot with is highlighted press 'e' this will allow you to edit it

use the arrow key to go to the kernel line and I think press 'e' again which should allow you to edit it - go to end of line and remove quiet and splash, then enter and then 'b'

try adding>  ide=nodma to the end

All the searches I try end up with at the same results - and one of them is this thread. If you still get no luck try in launchpad and in abs beginners.

Good luck

---

### Post by Black_Nautilus on 2008-03-25
Im just curious because i am having the same issue only if i try and boot using my PCI video card.

Are you using an on-board video or a seperate card ?

If seperate what type of card?

Not for sure if we are having the same issue but it sounds like it.

---

### Post by Archboundmind on 2008-03-25
yeah I'm using an ATI PCI video card - so you say it runs with another video card? - my boot sequence stops at only one error - in the hardware drivers

---

### Post by forestpixie on 2008-03-25
That's made me think - you could try setting the video driver to vesa - will start with basic graphics - then you could see if you can install the driver.

Boot to recovery mode - if it lets you - you'll finish at a prompt. This is the command - from my memory you answer questions questions as best you can - but when you get to the card driver choose vesa

```
sudo dpkg-reconfigure xserver-xorg -phigh
```

then ```
startx
```
see if it boots, or reboot it.

Worth a shot at this point I guess

---

### Post by VIPea on 2008-03-25
> **Black_Nautilus said:**
> Im just curious because i am having the same issue only if i try and boot using my PCI video card.

Are you using an on-board video or a seperate card ?

If seperate what type of card?

Not for sure if we are having the same issue but it sounds like it.

I'm using an Nvidia graphics card. Is there a way I can use the internal one? Would that make a difference?

---

### Post by forestpixie on 2008-03-25
You could try the reconfigure command above or if you have the knowledge take the card out, even if you haven't it's not hard to do.

---

### Post by Black_Nautilus on 2008-03-26
If you can set the internal as default in the BIOS you would be able to do the install.

Once in ubuntu get the corret driver installed to the card and set the monitor config to something usable as it wont have one to detect the settings from. 

Next reboot because the driver install will require it once you boot up you will get a config screen for your vidoe card config the card BUT DO NOT set the nvidia as default from this utility you will get a black screen and hear the login screen music if you do. 

Load in to ubuntu once to desktop go to SYSTEM >> ADMINISTRATION >> SCREENS and GRAPHICS once there make sure to set the card to use the correct driver and then set the Nvidia card as default screen also make sure to set up the monitor setting or you will get really low resolution. 

Once that is done log out as it tells you to dont reboot. Move your video cable and log back in using the nvidia card. 

Thats as far as i have gotten i am not for sure if you set the card as default in the bios if it will still work but from what i see happening on mine it should when it loads the restricted drivers now. 


But we will see, if you need any more info just send me a shout and i will help all i can. Good Luck!

---

### Post by damispyderbyte on 2008-03-26
Try irqpoll that may fix many errors. Try noapci command also.

you must edit the kernal to do this esc to get to boot menu. Hit e then go to the one that says kernal then hit e. add irqpoll at the end and noapci alss.

Hope this helps

---

### Post by Archboundmind on 2008-03-26
> **Black_Nautilus said:**
> If you can set the internal as default in the BIOS you would be able to do the install.

Once in ubuntu get the corret driver installed to the card and set the monitor config to something usable as it wont have one to detect the settings from. 

Next reboot because the driver install will require it once you boot up you will get a config screen for your vidoe card config the card BUT DO NOT set the nvidia as default from this utility you will get a black screen and hear the login screen music if you do. 

Load in to ubuntu once to desktop go to SYSTEM >> ADMINISTRATION >> SCREENS and GRAPHICS once there make sure to set the card to use the correct driver and then set the Nvidia card as default screen also make sure to set up the monitor setting or you will get really low resolution. 

Once that is done log out as it tells you to dont reboot. Move your video cable and log back in using the nvidia card. 

Thats as far as i have gotten i am not for sure if you set the card as default in the bios if it will still work but from what i see happening on mine it should when it loads the restricted drivers now. 


But we will see, if you need any more info just send me a shout and i will help all i can. Good Luck!


I appreciate the info - but the problem I have is that I can't do anything that gives me any form of access to a command prompt. I have Ubuntu installed on my computer but I can't boot it from a live cd or the hard drive. 

damispyderbyte, thanks, 
I tried your commands - it stalled at the same spot in the boot sequence though - 


I really think it has something to do with my video card - I had problems in Windows XP where I had to download the ATI Catalyst Driver Radeon 9250 to fix the graphic transitions when opening a window or scrolling 

Thanks for the help - I'm gonna try out a new video card hopefully this weekend

---

### Post by Black_Nautilus on 2008-03-27
can you change your bois to use an onboard video card or does your board not have one ?

---

### Post by Archboundmind on 2008-03-28
not sure I'll give it a shot 

-updates - 
I've tried every form of ubuntu, - then fedora, xubuntu, opensuse - everything just freezes in the middle of boot or installation - you think my mother board has gone bad?

---

