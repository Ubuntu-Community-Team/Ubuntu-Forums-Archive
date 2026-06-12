---
title: "gpsim &amp; deprecated GTK+extra"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by Graemej on 2010-04-28
There is a package called gpsim which is a simulator for PIC microprocessors. It is used by a fairly small community but is under active development and has been for many years. A decision was made by someone to deprecate GTK+extra claiming it was not being actively developed which is not the case and is now at GTK+extra-2.1.2 release and as far as I can tell bug free.

The gpsim developers don't seem to have had any contact from Ubuntu over this issue which leaves me very surprised that a culture of "We don't want this package - too bad about those who are beavering away at an open source program which is a bit obscure anyway"

Gentoo also deprecated the package but had contact with the gpsim developers and re-instated it. Fedora still has it.

Here is the tricky bit! I was using gpsim under windows but finally decided to cross over from the dark side and after checking on support for my critical apps (gpsim was top of the list) I went for Ubuntu only to find after hours of reading and setting up (I am really inexperienced with Linux) gpsim was crippled to only a command line app. I have 100's of hours of gui time invested in this programme.

I hope I am posting in the right place as I have never posted in an Ubuntu forum before.

Graeme Jury

---

### Post by petereiso on 2011-02-26
G'day Graham

I wholeheartedly agree.

I tried to get the gpsim giu by compiling gtk+extra, but it depended  on other things that I could not find via apt or even by google.

Fedora has it, debian 5 has it, debian 6 does not. Very frustrating.

Being a refugee from M$ windoze I ave been settling in to my new  environment nicely over the past few years.  But to have to go on wild  treasure hunts to make something that used to work operative is  disappointing.  I look at a computer as a tool to, among other things,  dabble in electronics, and not as the hobby itself.

*bitching finished*, and thanks to the maintainers for every thing else.

Can any-one say whether the maintainers are likely to re-enable the gui?

cheers 
pete

---

### Post by stephenhobbs on 2011-02-27
Have just been through the same pain: Swapped from MS Vista to Ubuntu 10.10, almost entirely a happy and positive experience! The one big headache I have is in getting Microchip PIC development going.
On older Ubuntu versions I manage to get gpsim to build from source, but on 10.10 it seems impossible with my level of high-level programming experience.

I tried to build gpsim 0.25 from source, but it wanted gtkextra-2.0.
Went to the gtkextra sourceforge site, grabbed the sources, but they won't build due to various compile errors, which I'm guessing are due to incompatibility with gtk headers ont he system already, or perhaps the gcc version, hard to tell.
I tried gtkextra versions 2.1.1 2.1.2 and 3.0, all fail to build.

I really need the gpsim GUI to work, as I need to use the LCD module to develop LCD display code without the nuisance of debugging on physical hardware.
Really I need to be able to get gpsim to build from source, as I also hope to develop my own gpsim module.

Ubuntu maintainers, please can we get support for gpsim and gtkextra?

Thanks.

---

### Post by Graemej on 2011-02-28
Thanks for your support guys. There is still no movement on this issue which should never have happened in the first place. I still have to keep my machine as dual boot just because of no gui support for gpsim. I am also needing the gui for LCD development and if I don't get any response I think I will move to archlinux where gpsim runs fine.

Graeme

---

### Post by Ricardo_RSP on 2011-05-31
Well, i got the same problems of you all, now im downloading the gpsim for Windows and ill try to emulate on Wine, hope it works. :)

---

### Post by fusebox on 2011-08-28
Ye who seeks a working simulator shall get it [here]("https://launchpad.net/~michael-gruz/+archive/elektronik/+packages")

---

### Post by nsaddington on 2011-09-09
Hi Fusebox.
Thanks for your post. 
I tried to install the GPSIM .deb package from the site you linked to, on Natty but still could not satisfy GTK+extras dependencies.
I couldn't install the libgtkextra-x11-3.0-glade_3.0-0ubuntu3_i386.deb package that I found there either.

Any clues what I should do to get a gui version of GPSIM going.

Thanks for your help.

---

### Post by fusebox on 2011-09-10
The trick is to Download ONLY THE MAVERICK .debs for your architecture [here]("https://launchpad.net/~michael-gruz/+archive/elektronik/+packages?field.name_filter=&field.status_filter=published&field.series_filter=maverick").
Herd them all into one folder, open a terminal there and 
```
sudo dpkg -i *.deb
```

I managed to install gpsim with the GUI but sadly it always crashes when I launch it.
Lets be optimistic and hope it works on your side.

I've also contacted the package maintainer on the issue. 
In the mean time I've been using MPLABX beta for linux. Grab it [here]("http://ww1.microchip.com/downloads/mplab/X_Beta/installer.html")
Chose your platform and architecture at the top right, select all the development tools in the center column
and click "download now".
Each package is an individual download.
Total size is > 200mb

but still, try installing GPSIM. I would like to know whether you got it to run.

---

### Post by sioux1977 on 2011-09-20
Hi Guys... i have opened a thread on gpsim forum on sourceforge because i have patched gtk+extra to succesfull compile under ubuntu 11.04.

Here the link to the thread:
 [http://sourceforge.net/projects/gpsim/forums/forum/6830/topic/4715417](http://sourceforge.net/projects/gpsim/forums/forum/6830/topic/4715417)

Actually i have gpsim working on ubuntu 11.04 with gui... lcd modules and so on...

I really hope this can help...

BR Simone.

---

### Post by stephenhobbs on 2011-10-04
> **sioux1977 said:**
> Hi Guys... i have opened a thread on gpsim forum on sourceforge because i have patched gtk+extra to succesfull compile under ubuntu 11.04.

I really hope this can help...

BR Simone.

Brilliant! :KS

I applied the same gtk+extra patch and was able to build gpsim-0.26.1 on Ubuntu 10.10.
Getting a few glitches when it runs, but nothing that wasn't there since years ago anyway.

Thank you very much for fixing and posting that patch.

Steve.

---

### Post by fouadatmeh on 2011-10-08
Thanks sioux1977 :)
Just a little addition to the noobs like me out there to save them some time..
to get things working, do the following commands:

> sudo apt-get install libgtk2.0-dev libpopt-dev libpopt0 libreadline6-dev


Install gtk+extra-2.0.0 (with modified "gtkextra/gtkitementry.c" file as per the above link) by going inside the "gtk+extra-2.0.0" dir and doing:
> ./configure
make
sudo make install

then install the gpsim by going into its folder and doing the same as for the gtk+

After the install, do "sudo /sbin/ldconfig" to solve the following error " gpsim: error while loading shared libraries: libgpsim.so.0: cannot open shared object file: No such file or directory"

**This was done on Ubuntu 11.10 beta

---

### Post by fusebox on 2011-10-08
Super!\\:D/\\:D/\\:D/
Now for the next problem.....
SIMULATION OF 16bit PICs :D

---

### Post by mostofmonty on 2011-10-11
fouadatmeh - thanks heaps for summarising all the steps clearly, but I am still having trouble with the patching.

when I highlight and copy the patch from 

[http://sourceforge.net/projects/gpsim/forums/forum/6830/topic/4715417](http://sourceforge.net/projects/gpsim/forums/forum/6830/topic/4715417)

it ends up all jumbled without any of its 'tab's of 'carriage return'/'new line's, and I believe this is why I run into the error:

```
patching file gtkitementry.c
Hunk #1 FAILED at 134.
Hunk #2 FAILED at 696.
Hunk #3 FAILED at 698.
Hunk #4 FAILED at 700.
Hunk #5 FAILED at 704.
Hunk #6 FAILED at 709.
Hunk #7 FAILED at 712.
Hunk #8 FAILED at 721.
Hunk #9 FAILED at 726.
Hunk #10 FAILED at 729.
Hunk #11 FAILED at 733.
Hunk #12 FAILED at 766.
Hunk #13 FAILED at 768.
Hunk #14 FAILED at 1031.
14 out of 14 hunks FAILED -- saving rejects to file gtkitementry.patched.rej
patching file gtkitementry.c
Hunk #1 FAILED at 1241.
Hunk #2 FAILED at 1275.
Hunk #3 succeeded at 633 (offset -1064 lines).
2 out of 3 hunks FAILED -- saving rejects to file gtkitementry.patched.rej
```

etc

i can't wait to get a graphical IDE like MPLAB running on Ubuntu! :D

---

### Post by fusebox on 2011-10-11
First Lemme save you some time with the patching
Please find attatched "gtkitementry.zip"

Second, your wish came true a while back
There is an IDE like MPLAB for Ubuntu..
[Its the new cross platform MPLABX from microchip!]("http://www.microchip.com/en_US/family/mplabx/index.html")

[Check it out]("http://www.microchip.com/en_US/family/mplabx/index.html")

---

### Post by mostofmonty on 2011-10-12
Thanks heaps fusebox :)

---

### Post by jacobite on 2012-04-19
Thanks for the great info, I've just installed gpsim with gui on Lubuntu 11.10. One thing though, gkt+extra wouldn't install using the latest version (2.1.2) which is linked to on the gpsim site, so I reverted to version 2.0.0 with the patched file provided by fusebox. Maybe 2.1.2 will install using the patched file, but I didn't try it.

---

### Post by mcinsand on 2013-01-31
Hi.  Like some others, I have been trying to install gpsim, but no luck so far.  Configuring goes okay.  However, with or without the patched file, though, I get the following at the end of my output when trying to make, and that is with or without the patched gtkimentry.c file.


[COLOR="Blue"]In file included from gtkcharsel.c:21:0:
/usr/include/glib-2.0/glib/gunicode.h:23:2: error: #error "Only <glib.h> can be included directly."
gtkcharsel.c: In function 'gtk_char_selection_realize':
gtkcharsel.c:182:21: warning: variable 'charsel' set but not used [-Wunused-but-set-variable]
make[2]: *** [gtkcharsel.lo] Error 1
make[2]: Leaving directory `/home/stan/Downloads/gtk+extra-2.0.0/gtkextra'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/stan/Downloads/gtk+extra-2.0.0'
make: *** [all] Error 2[/COLOR]

Googling to hunt what contains charsel or gtkcharsel hasn't helped, so far.  Any pointers as to what I'm overlooking?

Regards.

---

