---
title: "Trouble Installing Nicotine and XMMS"
date: 2005-07-22
forum: Installation &amp; Upgrades
---

### Post by OscarGortez on 2005-07-22
I'm a stupid noob when it comes to Linux so try and keep things... well not overly complex.  It seems the only install i got to work is my winmodem driver :-p anyway onto my issues...

XMMS: 
I downloaded a .deb file for this which I tried to install using the dpkg command (how i did my modem drivers) and it seems to work half way untill the install gets caught up at 
"dpkg: dependency problems prevent configuration of xmms:
 xmms depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 xmms depends on libgtk1.2 (>= 1.2.10-4); however:
  Package libgtk1.2 is not installed.
dpkg: error processing xmms (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xmms"
does this mean i need to install libgtk1.2? if so what is it and how do i install it?

Nicotine:
I downloaded this unzipped some folder read the directions to install and the directions didn't work. The Instructions say "To install Nicotine, from the source tree run:

python setup.py install --prefix=<dir>"

so i go to the folder that's in, in the root terminal and type "python setup.py install --prefix=/opt" since i hear installing to the opt folder is a good idea that doesn't work... and this spits out 
"running install
error: invalid Python installation: unable to open /usr/lib/python2.4/config/Makefile (No such file or directory)"
I tried putting the <>'s in but then i get a line error.... anyone able to help me here?

---

### Post by damonw5 on 2005-07-22
[QUOTE=OscarGortez]I'm a stupid noob when it comes to Linux so try and keep things... well not overly complex.  It seems the only install i got to work is my winmodem driver :-p anyway onto my issues...
.... anyone able to help me here?[/QUOTE]
 Instead of installing from a downloaded file, open up Synaptic in System->Admin->Synaptic (or Kynaptic if you're using Kubuntu.) If you haven't enabled all the repositories yet, follow these directions: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) and reload your package lists in synaptic. Then search for xmms in synaptic -- it should be there, though I don't know about Nicotine. Then choose install and click apply. This is generally how things are installed in Ubuntu rather than downloading files separately.

BTW, try using beep-media-player instead of xmms. It uses xmms skins and is much nicer :)

As always, if you have any problems, need clarification, or have a success story, post back here!

---

### Post by OscarGortez on 2005-07-23
[QUOTE=damonw5]Instead of installing from a downloaded file, open up Synaptic in System->Admin->Synaptic (or Kynaptic if you're using Kubuntu.) If you haven't enabled all the repositories yet, follow these directions: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) and reload your package lists in synaptic. Then search for xmms in synaptic -- it should be there, though I don't know about Nicotine. Then choose install and click apply. This is generally how things are installed in Ubuntu rather than downloading files separately.

BTW, try using beep-media-player instead of xmms. It uses xmms skins and is much nicer :)

As always, if you have any problems, need clarification, or have a success story, post back here![/QUOTE]
 I'd seen some other mentions of using Synaptic, but i didn't get it since when I tried i didn't see the programs i downloaded and didn't know how to install them... but going to that link and doing what it said to update Synaptic worked like a charm... thanks

---

### Post by davy cielen on 2008-05-16
Hi, 

when you search for soulseek in synaptic,nicotine is in the list.
When installed it realy works fine (ubuntu 8.04 64bit)

---

