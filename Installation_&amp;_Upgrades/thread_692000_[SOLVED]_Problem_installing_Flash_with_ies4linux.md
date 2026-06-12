---
title: "[SOLVED] Problem installing Flash with ies4linux"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by cotsweb on 2008-02-09
Hi, I hope this is the right place for this query, I am a newby with Ubuntu and this is my first post.

I am trying to install ies4linux on gutsy. I develop websites and I like the idea of being able to test in lots of versions of IE while using linux.  I use Firefox myself but any website I create must work in all browsers, not just in well behaved ones.

I have followed the instructions at;
[http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu]("http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu")

It all works fine as long as I don't tick the box that says "install Flash 9".  Sadly I do need Flash for my testing to be valid.  When I include Flash I get the following output;

[I]IEs4Linux will:
  - Install Internet Explorers: 6.0, 5.5, 5.01, 7.0
  - Using IE locale: EN-US
  - Install Adobe Flash 9.0
  - Install everything at: /home/mark/.ies4linux
[ OK ]

Downloading everything we need
  Downloading from microsoft.com:
   DCOM98.EXE
   mfc42.cab
   249973USA8.exe
   ADVAUTH.CAB
   CRLUPD.CAB
   HHUPD.CAB
   IEDOM.CAB
   IE_EXTRA.CAB
   IE_S1.CAB
   IE_S2.CAB
   IE_S5.CAB
   IE_S4.CAB
   IE_S3.CAB
   IE_S6.CAB
   SETUPW95.CAB
   FONTCORE.CAB
   FONTSUP.CAB
   VGX.CAB
   SCR56EN.CAB
   IE7-WindowsXP-x86-enu.exe

  Downloading from Evolt Browser Archive:
   ie55sp2_9x.zip
   ie501sp2_9x.zip

  Downloading from macromedia.com:
   swflash.cab
[ OK ]

Installing IE 6
  Initializing
  Creating Wine Prefix
  Extracting CAB files
  Installing IE 6
  Installing DCOM98
  Installing TTF Fonts
  Installing ActiveX MFC42
  Installing RICHED20
  Installing registry
  Finalizing
[ OK ]

Installing Flash Player 9
  Extracting files
/home/mark/.ies4linux/downloads/swflash.cab: WARNING; file possibly truncated by 1199303 bytes.
/home/mark/.ies4linux/downloads/swflash.cab: no valid cabinets found
 An error occured when trying to cabextract some files.
[/I]

I am sure I am making some simple mistake but I have tried several times and can't seem to get past it.  Can anyone spot my error?:confused:

Thanks
mark

---

### Post by cotsweb on 2008-02-12
Well after some searching I found the solution to this problem.

ies4linux stores its working files in home/mark/.ies4linux (note the "." in the directory name this means that it won't show up unless you display hidden files),

My initial download of swflash.cab was corrupted but when I reinstalled ies4linux it looked in its working directory and saw that it already had a copy of this file, so it didn't download it again, it just reused the existing (corrupt) file.

Once I had found the offending directory I just deleted it then reinstalled.  ies4linux downloaded new copies of everything and installed cleanly.  Yay!

---

