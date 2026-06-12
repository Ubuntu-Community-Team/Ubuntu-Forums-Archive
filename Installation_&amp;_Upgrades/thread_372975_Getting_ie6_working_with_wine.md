---
title: "Getting ie6 working with wine"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by sjpritch25 on 2007-02-28
I am receiving the following error when i try and run IE6.   Here is how i went about opening iexplore.exe.   In the Terminal, I typed
> winefile
Navigated to the appropriate location
> /home/.wine/drive_c/Program Files/Internet Explorer
Then i double-clicked on iexplore.exe.

I recieved a blank white page that said Internet Explorer, but nothing else.

Here is the error in the Terminal
```
stefan@stefan-desktop:~$ winefile
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
fixme:shell:StopWatchMode () stub!
fixme:shdocvw:IEWinMain "" 1
fixme:ole:CoResumeClassObjects stub
err:ole:CoGetClassObject class {25336920-03f9-11cf-8fd0-00aa00686f13} not registered
err:ole:CoGetClassObject class {25336920-03f9-11cf-8fd0-00aa00686f13} not registered
err:ole:CoGetClassObject no class object {25336920-03f9-11cf-8fd0-00aa00686f13} could be created for context 0x3
err:shdocvw:navigate Could not create HTMLDocument: 80040154
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
fixme:shell:StopWatchMode () stub!
fixme:shdocvw:IEWinMain "" 1
fixme:ole:CoResumeClassObjects stub
err:ole:CoGetClassObject class {25336920-03f9-11cf-8fd0-00aa00686f13} not registered
err:ole:CoGetClassObject class {25336920-03f9-11cf-8fd0-00aa00686f13} not registered
err:ole:CoGetClassObject no class object {25336920-03f9-11cf-8fd0-00aa00686f13} could be created for context 0x3
err:shdocvw:navigate Could not create HTMLDocument: 80040154
Xlib:  extension "XFree86-DRI" missing on display ":0.0".

```

Thanks for any help:)

---

### Post by zvacet on 2007-03-01
Newer versions of wine have problems runing IE.If it is not some specific need install something else(firefox,opera).Download exe and put it in .wine folder and rest you know allready.

---

### Post by sjpritch25 on 2007-03-01
Know i was just messing around and wanted to see if i could get it running.    I would really like to see if Musicmatch jukebox will run because that is were i purchase all my songs.   Do you have any idea if it will run with wine????

---

### Post by bodycoach2 on 2007-03-01
You can get the IE .deb package here:

[http://ubuntuforums.org/showthread.php?t=370705&highlight=internet+explorer]("http://ubuntuforums.org/showthread.php?t=370705&highlight=internet+explorer")

Worked perfectly on my system:

[IMG]http://farm1.static.flickr.com/173/405424973_c6c095206b.jpg?v=0[/IMG]

---

### Post by mhancoc7 on 2007-03-03
> **bodycoach2 said:**
> You can get the IE .deb package here:

[http://ubuntuforums.org/showthread.php?t=370705&highlight=internet+explorer](http://ubuntuforums.org/showthread.php?t=370705&highlight=internet+explorer)

Worked perfectly on my system:

[IMG]http://farm1.static.flickr.com/173/405424973_c6c095206b.jpg?v=0[/IMG]

I have updated the program to keep it within the legal boundaries. :)
[http://www.ubuntuforums.org/showthread.php?t=370705](http://www.ubuntuforums.org/showthread.php?t=370705)

Jereme

---

### Post by aouie on 2007-03-12
You can look into [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page"). You shouldn't run into problems with Edgy. After installing just type in "ie6<ENTER>" in any terminal.
Sincerely,
Aouie

---

### Post by mhancoc7 on 2007-03-12
> **aouie said:**
> You can look into [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page"). You shouldn't run into problems with Edgy. After installing just type in "ie6<ENTER>" in any terminal.
Sincerely,
Aouie

That is exactly what this .deb package will do. It just gives you a nice GUI and helps with some common problems when errors occur with the IEs4Linux script.

[http://www.ubuntuforums.org/showthread.php?t=370705](http://www.ubuntuforums.org/showthread.php?t=370705)

Jereme

---

