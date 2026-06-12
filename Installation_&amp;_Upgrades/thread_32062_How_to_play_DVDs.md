---
title: "How to play DVDs?"
date: 2005-05-05
forum: Installation &amp; Upgrades
---

### Post by Goober on 2005-05-05
Ok, I have a question about playing DVDs.  I have Totem, Realplayer, and VLC installed, and none of them can play the DVD.  I have a DVD player in my computer (obviously), what I need to do is to get a program to play DVDs.

**Totem**

For Totem, I installed [this](http://ubuntuguide.org/4.10/index.html#dvdplayback) which I thought would solve the problem.  It didn't.  Totem still cannot play DVDs.

**VLC**

For VLC, I thought it could automatically play DVDs, or just about anything.  It did when I had it on Windows.  I installed it, everything works dandy.  Except that when I try to play a DVD, i get the following:

"[00000211] skins2 interface: skin: VLC OSX Interface  author: BigBen
[00000213] main input: playlist item `dvd:///dev/dvd@0:1'
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
[00000213] dvd input error: dvdcss cannot open device
[00000213] v4l input error: cannot open device (No such file or directory)
[00000213] v4l input error: cannot open audio device (No such file or directory)[00000213] main input error: no suitable access module for `/://dvd:///dev/dvd@0:1'"

**RealPlayer**

For Reaplayer, i need to know the address of the DVD player, which I don't know. I think it is like dvd:// or something similar.  Does anybody know what it is?

Anyway, I just need to get DVDs working on one of those 3 players.  If I could do that, then I would be as happy as a clam. 

Thanks in advance!

Goober.

---

### Post by Xerampelinae on 2005-05-05
What does

ls -l /dev/dvd

say?


I'll take a stab in the dark and tell you to try:

sudo ln -s /dev/hdc /dev/dvd

---

### Post by Goober on 2005-05-06
When I type it into the Terminal, I get 

"lrwxrwxrwx    1 root     root            3 2005-05-05 08:16 /dev/dvd -> hdc"

Where the /dev/dvd is in a light blue, and the hdc yellow and highlighted in black.

For your second suggestion, I get this:

"ln: `/dev/dvd': File exists"

---

### Post by delltony on 2005-05-06
notice the error you get:
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading

DVDs use a cheesy copywrite protection scheme CSS  in any event. You need to install the decoder for the dvd to read.
#: sudo apt-get install libdvdread3 libdvdcss2

this should do the trick for you.
also make sure that you enable dma on your dvd player by default its turned off
hdparm -i /dev/hdc (or whatever you dvddrive is)  to see if dma is on
if its 0 then change it by hdparm -d1 /dev/hdc 
this command has to be done with sudo. Hope this helps you out

---

### Post by Goober on 2005-05-06
Ok, when I typed your first suggestion in, i got 

"Reading Package Lists... Done
Building Dependency Tree... Done
libdvdread3 is already the newest version.
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded."

That seems to indicate that the CSS dealie is already activated.  So that did not solve the problem.  I tried playing the DVD again with VLC, didn't work.

For your dma, I typed that in, and got the following:

"/dev/dvd:

 Model=HL-DT-ST GCE-8400B, FwRev=1.02, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:227,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 *mdma2
 AdvancedPM=no

 * signifies the current active mode"

I was unable to decifer that to see if my dma was turned on or off.

Thanks for the reply, though!

---

### Post by delltony on 2005-05-08
[QUOTE=Goober]Ok, when I typed your first suggestion in, i got 

"Reading Package Lists... Done
Building Dependency Tree... Done
libdvdread3 is already the newest version.
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded."

That seems to indicate that the CSS dealie is already activated.  So that did not solve the problem.  I tried playing the DVD again with VLC, didn't work.

For your dma, I typed that in, and got the following:

"/dev/dvd:

 Model=HL-DT-ST GCE-8400B, FwRev=1.02, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:227,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 *mdma2
 AdvancedPM=no

 * signifies the current active mode"

I was unable to decifer that to see if my dma was turned on or off.

Thanks for the reply, though![/QUOTE]
 one other thing you might wanna check not sure if it makes a difference on the dvds or not is insteall the win32codec package. 
but hdparm -d /dev/dvd should tell you if dma is enabled or not
in any event you would want to hdparm -d1 /dev/dvd

hope you get it working keep me posted. 
also try xine and see if it might somehow be a vlc issue

---

### Post by DutchLau on 2005-05-09
Hi, I've also been having problems with DMA. Here is the output of hdparm -d /dev/hdc (My DVD location):

> root@Discom:/home/discom # hdparm -d /dev/hdc

/dev/hdc:
 using_dma    =  0 (off) 

So I tried doing this:

> root@Discom:/home/discom # hdparm -d1 /dev/hdc

/dev/hdc:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off) 

What must I do to enable DMA? The output of  hdparm -i /dev/hdc is as follows:

> root@Discom:/home/discom # hdparm -i /dev/hdc

/dev/hdc:

 Model=HL-DT-ST DVDRAM GSA-4163B, FwRev=A102, SerialNo=K7351SB5729
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no
 Drive conforms to: device does not report version:

 * signifies the current active mode 

Any suggestions? Please

DutchLau

---

### Post by Goober on 2005-05-09
I have the win32codec package.

I think that I might be able to open DVDs with RealPlayer, but I need to know the address of my DVD Player.  I think it is /dev/dvd, but I am not sure, and that doesn't work for ReaPlayer.  How could I find the address of my DVD player?

And what is "Xine"?  Is it another Media Player?

Thanks for the continuing help.  I really appreciate it :)

---

### Post by Xerampelinae on 2005-05-09
Do you have two cd/dvd drives?  (two secondary ide devices)

Maybe the /dev/dvd link is screwed up.  If this is the case you could delete it and make the /dev/dvd link point to the real dvd drive.  Not sure if the link would stay though..

---

### Post by Goober on 2005-05-10
Ok, siome good news.  First, I spent the day uninstalling Warty, and then installing Hoary, sucessfully.  Then I installall those Codecs, and DVD playback ability, and the like, and then I got VLC, and some magic happened - I can now play DVDs!!!

So I want to thank everybody for their help, I am now a very happy man.

That means the only thing I cannot do in Linux is play Games, but only because I have yet to get Cedega . . .

---

### Post by DutchLau on 2005-05-10
You could always get Linux games such as described here: [http://ubuntuforums.org/showthread.php?t=5153](http://ubuntuforums.org/showthread.php?t=5153) 

I personally recommend America's Army which is a cross platform game which has apple, windoze and Linux users so you have many people playing it. You need a reasonably beefy computer though (1ghz+ 32mb vidcard+ 256ram+) to play it, and I warn you, it's very very addictive!  :razz:  :razz: 

Cheers,

DutchLau

---

### Post by garnertr on 2005-05-10
[QUOTE=Xerampelinae]What does

ls -l /dev/dvd

say?

[/QUOTE]

my says:


lrwxrwxrwx  1 root root 8 2005-05-10 14:23 /dev/dvd -> /dev/hdc

where /dev/dvd is red and /dev/hdc is normal black txt writing.

---

