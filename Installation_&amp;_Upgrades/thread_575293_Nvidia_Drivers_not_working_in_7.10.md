---
title: "Nvidia Drivers not working in 7.10"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by mmilitia9 on 2007-10-13
I have the nvidia drivers installed because when I could actually see the Nvidia listing in dpkg-reconfigure xserver-xorg.  Plus, when I could actually see the Ubuntu screen with the integrated card that I had to enable to install.. I installed the Nvidia driver from the actual pop up that pops up on the fresh install to make your hardware work and stuff like that...

Soo, with that said.. I think the problem lies within somewhere in the xorg.conf file then? Or did the download of the nvidia driver fall through?

Any suggestions would be appreciated... thank you


Dominick

---

### Post by PmDematagoda on 2007-10-13
Did you try:-

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

or

```
sudo dpkg-reconfigure xserver-xorg
```

?

---

### Post by Pumalite on 2007-10-13
What Nvidia card do you have?

---

### Post by mmilitia9 on 2007-10-13
Nvidia Geforce FX 5500... Sorry bout that.



How do I go about finding out what slot my PCI card sits in?

---

### Post by PmDematagoda on 2007-10-13
Is it a PCI-E? If so then 1:0:0 should be correct.

---

### Post by mmilitia9 on 2007-10-13
By default it said it was 0.2.0

But I don't know what the heck I have to do in order to make 7.10 work from a Fresh Install.  I mean.. what else is there to edit out?  Why isn't X Starting?

---

### Post by PmDematagoda on 2007-10-13
Wait a minute, 0:2:0 must apply to the address of the integrated VGA, change it to the one I gave you and see if that makes a difference.

---

### Post by mmilitia9 on 2007-10-13
I tried.  It didn't work.

When I enter Ubuntu in recovery mode it gets me to the command prompt.  When i get there, I type 'startx'
I get this when I type that:

No matching device section for instance(BusID Pci:1:1:0)
No device Found



Fatal server error
No screens found
Fatal IO error 104 on xserver


Now.. I edited my xorg.conf file and made sure that Nvidia was placed under driver and stuff like that.. I then typed...
Sudo dpkg-reconfigure xserver.xorg

Re-writed something... now when I hit 'startx' my monitor goes BLANK.. and stays blank

Also.. When I rebooted.. Instead of seeing the actual Ubuntu pic and the loading bar.. I saw text based stuff and alot of OK's

... :(

---

### Post by PmDematagoda on 2007-10-13
Ok, now did you change the address to 1:0:0 or pci1:1:0?

---

### Post by mmilitia9 on 2007-10-13
No.  I didn't.  Xorg.conf is still 0:2:0

I did change it though after u mentioned to give it a shot.. but since it didnt improve anything anyway.. I just put it back to 0:2:0

---

### Post by PmDematagoda on 2007-10-13
Hmm, did you try installing the latest Nvidia driver from the Nvidia website?

---

### Post by mmilitia9 on 2007-10-13
Well, I can't log into the actual Ubuntu.. I'm doing everything from command prompt... is there a code I could use to get it going?(Like apt-get)

The drivers I got from Nvidia were the ones that popped up in the bubble when I got inside of Ubuntu and it loaded up.. (While I was using the onboard graphics)..I installed the drivers... But once I rebooted It wouldn't let me return back to Ubuntu at all..


Overall.. all of my researching has me leaning towards why I'm having so much problems with my Nvidia Geforce FX5500PCI... 

I have a Intel 845 onboard integrated video chipset.  It keeps wanting to load with Ubuntu and not my Nvidia  Geforce FX 5500 card... This is what I think.. I believe I have to do some editing with the xorg.conf file... but I have not the slightest clue where to get started.

Lets start from here...

Fresh install of Ubuntu 7.10.  You have a Integrated video card and a PCI Video card.  The PCI video card is what is enabled in the BIOS.  Still.. Everytime you try to load up into Ubuntu.. It goes blank for you.  

What would you do from here? Exact steps...

---

### Post by PmDematagoda on 2007-10-13
Hmm, lets try one more address shall we? Try 2:0:0 and see.

---

### Post by mmilitia9 on 2007-10-14
Hahaha, Sweeeeet.  That didn't work at all.  But what did work was... 1:1:0.  I happened to plug that into the xorg.conf file and it booted right into the desktop without any more crap.  Awesome! 

So, anyone that is struggling on the same exact crap as me... The problem is def in your xorg.file.  Make sure you know where your BusID is located and etc..

---

### Post by PmDematagoda on 2007-10-14
> **mmilitia9 said:**
> Hahaha, Sweeeeet.  That didn't work at all.  But what did work was... 1:1:0.  I happened to plug that into the xorg.conf file and it booted right into the desktop without any more crap.  Awesome! 

So, anyone that is struggling on the same exact crap as me... The problem is def in your xorg.file.  Make sure you know where your BusID is located and etc..

Brilliant:), you must have used the "trial and error" method haven't you? And how is Alien Arena?

---

### Post by mmilitia9 on 2007-10-14
Never played it.  Looks cool though :)  I'm just sittin around here configuring my Ubuntu.  Just got Compiz working and stuff.. it locked me out again, but I was able to edit some xorg.conf things to get it back running (I don't know why the computer insists on putting bus 0:2:0 but its really simple changing it to 1:1:0) haha.. Anyway.  thanks for all the help.  stay in touch.. your pretty helpful :D

-Dominick
Skype: mmilitia9

---

