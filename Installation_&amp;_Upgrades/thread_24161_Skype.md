---
title: "Skype"
date: 2005-04-05
forum: Installation &amp; Upgrades
---

### Post by thechitowncubs on 2005-04-05
I seem to be having trouble installing skype on my new Ubuntu Hoary Laptop.

I tried both the .deb package and the binary from skype.com

when I try to launch the binary, it spits out an error saying: ```
Error while loading shared libraries: libxft.so.1: cannot open shared object file: No such file or directory
```

I did successfully INSTALL the .deb package, BUT I can't launch it. It just sits there when i launch it from applications>internet>skype

Does anyone have any tips or guides that I can read? I tried the [www.ubuntuguide.org/temp](www.ubuntuguide.org/temp) and that didn't work.

Thanks for the help.

---

### Post by sfw5000 on 2005-04-05
you need to install the libxft font library.. basically just open synaptic and search for libxft and install it... should work then.

---

### Post by thechitowncubs on 2005-04-05
thanks, that helped with the binary troubles

---

### Post by thechitowncubs on 2005-04-05
is there anyway to get the .deb package working?

because the binary doesn't look good at all visually

---

### Post by sfw5000 on 2005-04-05
It doesn't look good, I believe, because it uses kde libraries for its visual appearance... I think if you install certain kdelibs it will look better, but i'm not sure which ones... 

anyone know those?

---

### Post by thechitowncubs on 2005-04-05
[QUOTE=sfw5000]It doesn't look good, I believe, because it uses kde libraries for its visual appearance... I think if you install certain kdelibs it will look better, but i'm not sure which ones... 

anyone know those?[/QUOTE]
 that'd be great if someone could find out

---

### Post by jiyuu0 on 2005-04-06
updated and corrected... should work on a fresh install :)
[http://ubuntuguide.org/temp/#skype](http://ubuntuguide.org/temp/#skype)

---

### Post by thechitowncubs on 2005-04-06
[QUOTE=jiyuu0]updated and corrected... should work on a fresh install :)
[http://ubuntuguide.org/temp/#skype](http://ubuntuguide.org/temp/#skype)[/QUOTE]
 Wow, thank you so much.

This is a skype problem but maybe you guys have experienced it. My skype gets stuck on the connecting phase and never connects. Have you guys ever had that problem with ubuntu?

---

### Post by tomchuk on 2005-04-06
[QUOTE=sfw5000]It doesn't look good, I believe, because it uses kde libraries for its visual appearance... I think if you install certain kdelibs it will look better, but i'm not sure which ones... 

anyone know those?[/QUOTE]
 apt-get install kcontrol and you will be able to edit font settings for kde apps.

---

### Post by laurens on 2005-04-08
[QUOTE=thechitowncubs]
This is a skype problem but maybe you guys have experienced it. My skype gets stuck on the connecting phase and never connects. Have you guys ever had that problem with ubuntu?[/QUOTE]

I have exactly the same thing, no idea as to why. It's not my internet connection, as on windows there's no problem.

Just to be sure we're talking about the same thing: I start skype, it fetches all my contacts and all, but when I try to call any of them, or try to send them a textmessage, it doesn't connect and doesn't send the messages.

I tried calling echo123, but it fails to connect there, too. Anybody got any clues?

---

### Post by Nano on 2005-04-08
All these problems with Skype sound so familiar to me.
Personally I never managed to make it work with esd so I have to kill esd before starting it.
Before to lauch Skype type "killall esd".
Then start it and try echo123 again to see if it worked or not.

---

### Post by tomchuk on 2005-04-08
[QUOTE=tomchuk]apt-get install kcontrol and you will be able to edit font settings for kde apps.[/QUOTE]

My bad, skype is a straight qt3 app. Install qt3-qtconfig and use qtconfig to edit your qt theme.

---

### Post by thechitowncubs on 2005-04-10
Has anyone got skype to work with Gnome/ESD?

I really want this to work, this is the only thing turning me off from linux  :-?  and the one thing that i can't figure out.

---

### Post by sfw5000 on 2005-04-10
[QUOTE=thechitowncubs]Has anyone got skype to work with Gnome/ESD?

I really want this to work, this is the only thing turning me off from linux  :-?  and the one thing that i can't figure out.[/QUOTE]

OK, I just did a new install on a new computer and here is how I got it to work step by step.

1) Install skype using the instructions posted by Ubuntu Geek:

```
wget http://www.skype.com/go/getskype-linux-fc2

sudo alien -d skype-0.92.0.2-fc2.i386.rpm

sudo dpkg -i skype_0.92.0.2-1_i386.deb

note: I had to install some qt stuff to get it to work

sudo apt-get install libqt3-mt-dev
```

NOTE, you might need some other stuff like libxrender1 -- all additional needed packages can be found in synaptic. If Skype fails to start, then you should start it from the command line (just type "skype" into a console). Note any errors that appear -- install any packages it complains are missing.

2) In synaptic install polypaudio, polypaudio-alsa, polypaudio-x11, polypaudio-clients, libpolyp0, libpolyp0-glib (NOTE: not sure if you need ALL of these, but I don't see any harm in installing them all). This will remove ESD from your system and replace it with the polypaudio sound daemon/server.

3) Start up skype and call the testing service (echo123). If you don't hear anything try:
a) Open Volume Manager and click through every available tab to make sure that all the volume levels are up and nothing is muted. For me the microphone was muted in here by default, unmuting it fixed my problem.
b) Open System--Prefs--Sound and make sure you can hear testing sounds in there
c) In skype open the Options dialgoue and click on "Hand/Headsets" then try picking a different DSP device (I had to change mine to dsp1 instead of dsp)

Hope this works as well for others as it did for me.

Sam

---

### Post by Nekrataal on 2005-04-10
i did what you said, but now i have no other sound but skype, i can only hear skype, and all the other things are muted...

---

### Post by laurens on 2005-04-11
[QUOTE=sfw5000]OK, I just did a new install on a new computer and here is how I got it to work step by step.

1) Install skype using the instructions posted by Ubuntu Geek:

```
wget http://www.skype.com/go/getskype-linux-fc2

sudo alien -d skype-0.92.0.2-fc2.i386.rpm
```

[/QUOTE]

Please note that this is a really old version. Now, there's a .deb available on their site, too. So you can do 

```
wget http://www.skype.com/go/getskype-linux-deb
sudo dpkg -i skype_1.0.0.20-1_i386.deb

```

instead of

```
wget [http://www.skype.com/go/getskype-linux-fc2](http://www.skype.com/go/getskype-linux-fc2)

sudo alien -d skype-0.92.0.2-fc2.i386.rpm
sudo dpkg -i skype_0.90.0.2-1.i386.deb

```

I'll try the poly thing later, as with the solution to killall esd leaves me with a system unable to play music at the same time as using skype, which is annoying.

---

### Post by sfw5000 on 2005-04-11
Thanks laurens -- yeah when you do the wget I posted it seems to point you to the new version.. thanks for pointing out they have a .deb.

Nekrataal -- not sure what's going on there... I don't have that problem -- is polypaudio running?

```

sam@ernie:~$ ps ax | grep poly
 8045 ?        S      0:43 /usr/bin/polypaudio

```

---

### Post by Nekrataal on 2005-04-11
```
nekrataal@seidel:~$ ps ax | grep poly
 7022 ?        Ss     8:14 /usr/bin/polypaudio -Lmodule-esound-compat-spawnfd fd=18
23369 pts/0    S+     0:00 grep poly

```

Yes its running, but when on a conversation i cannot play any other sound, and the sounds from gnome are gone..is there any special setting to set up??...

---

### Post by sfw5000 on 2005-04-11
OK... so you can play music, and then do skype, but not both at the same time? I've never tried to do more than one audio thing at once, and I always turn off system sounds, so perhaps their could be some kind of conflict with having more than one program accessing the sound daemon at once. I'm pretty sure this is a common problem in Linux.. Not sure what to do about it... anyone else??

---

### Post by Nekrataal on 2005-04-11
yes, thats right, if im playing music and open skype it hangs badly...its the same as if i kill the sound daemon and run skype after that..running skype with esddsp i supoused to solve the problem, but it doesnt work, i can hear the ringing, but not the voice..

---

### Post by Marc Higgins on 2005-04-13
this is a big problem for those of us who drink coffee, listen to music & will only allow the sanctity of our cubicles to be interrupted by our mobiles or skype. we need both skype & music

---

### Post by Nekrataal on 2005-04-14
Yes, anyone knows how to work this trought??, i'll apreciate any cooperations. please help!

---

### Post by amerigo5 on 2005-04-14
I use the 'killall esd' command before opening Skype and call to echo123 works. 

To listen to music while Skype is on-standby, use XMMS (as Rhythmbox doesn't work).

Still waiting to get this resolved......

---

### Post by thechitowncubs on 2005-04-14
[QUOTE=amerigo5]I use the 'killall esd' command before opening Skype and call to echo123 works. 

To listen to music while Skype is on-standby, use XMMS (as Rhythmbox doesn't work).

Still waiting to get this resolved......[/QUOTE]
 The killall esd command works nicely, how do you start esd after you are done with skype?

And I am having big problems with echo ( the other person is complaining about a perfect duplicate of their voice). I am assuming that this is a simple fix but I can't seem to figure it out in the mixer options. If anyone has their sound configured correctly can you please post a screenshot of your settings or something of the like.

Thanks

---

### Post by Nekrataal on 2005-04-15
To start esd after killing it, use the comand:
```
esd
```
;)

---

### Post by thechitowncubs on 2005-04-15
[QUOTE=Nekrataal]To start esd after killing it, use the comand:
```
esd
```
;)[/QUOTE]
 I tried that, and it doesn't really seem to work

it just plays a sound and then when i try to play music or something it doesn nothing.

---

### Post by thechitowncubs on 2005-04-15
I got it all working good...

i just wish that this would work under ESD, how hard is it to develop something like this?

do you think the skype people while pull it off?

---

