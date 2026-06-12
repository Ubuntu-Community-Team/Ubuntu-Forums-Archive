---
title: "downverter doesn't start - can not  install downverter"
date: 2013-09-08
forum: Installation &amp; Upgrades
---

### Post by fra2rizla on 2013-09-08
[FONT=FreeSans][SIZE=3][COLOR=#222222]helloguys, I am a new happy ubuntu user after 15 years or so on windows..[/COLOR]

[COLOR=#222222]Ihave a dell inspiron 6400 laptop, 32 bit, 2gb ram, cpu intel T21301.86 GHZ x 2, and I have installed ubuntu 12.04, kernel linux3.8.0-30-generic, gnome 3.4.2.[/COLOR]

[COLOR=#222222]I[/COLOR][COLOR=#222222]tworks beautifully and so far no problem, but I have installeddownverter and I see it in dash but when I click on it nothinghappens. I tried to unistall and install back, restart laptop, getthe deb file from different source but this problem is still there.So the weird things are this:[/COLOR]

[COLOR=#222222]1)when I click on it on the dash, the software doesn’t start.[/COLOR]

[COLOR=#222222]2)I tried to uninstall it and realised that I can only do it fromterminal ( sudo apt-get remove downverter ), if I open it in softwarecenter, the software centre allows me to reinstall it but not touninstall it (and I can open it in software center just clicking onthe deb file I downloaded and not looking through the installedsoftware)[/COLOR]

[COLOR=#222222]3)even after having installed downverter from terminal ( sudo apt-getremove downverter and then, just to make sure everything is cleanedup sudo apt-get autoremove and sudo apt-get update I still see thesoftware link on the dash[/COLOR]
[/SIZE][/FONT]


[LIST=1]
[*][FONT=FreeSans][SIZE=3]I    tried to open the software from terminal just typing downverter and    the terminal tells me the file is not there  ( but as you can read    in number 2 if I click on the downloaded deb file my laptop opens    software centre from that tells reinstall, so I assume for software    centre and for the dash [number 1] the software is there, but    actually it is not installed, because the terminal tells me the file    is not there.)[/SIZE][/FONT]
    [FONT=FreeSans][SIZE=3]
[COLOR=#222222]what    shall I check? please specify step by step, I am quite new to do    things in the terminal.[/COLOR]

[COLOR=#222222]OR    can any of you suggest another graphic video dowanloader software    that lets you chose not only the output format file but also the    quality of the file you are downloading ( I mean 1080 p or 720 p, or    480 p), I tried all video downloader but this one just let me chose    the output file but not the quality of the download and it doesn’t    chose automatically the best quality. I know you can do it with the    terminal, but being new to ubuntu I prefer to have a graphic version    software. Also I know there are plug in for firefox but I use chrome    ( not chormium and apparently all the plug in for chorme have been    removed from the chorme web store and the browser doesn’t allow me    to install extension that are not in their web store) Thank you so    much.[/COLOR][/SIZE][/FONT]
[/LIST]

---

### Post by fra2rizla on 2013-09-08
I found ClipGrap and it works. Probably the .deb package for 32 bit is corrupted because there's a missing file. (/opt/downverter/downverter )

---

