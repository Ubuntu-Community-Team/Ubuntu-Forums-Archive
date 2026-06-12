---
title: "Minor Sound Issues after upgrade from 9.04 to 9.10"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by billiusmaximus on 2009-11-15
[Repost] - felt like this might be a more appropriate place to post my concern.

Hello,

I just joined the Ubuntu community today - but I would say I am an intermediate Linux user. I have been exploring Ubuntu since 8.04.

I upgraded my Dell Laptop from 9.04 to 9.10 and it works almost perfectly except for some sound issues. The sound technically works, but the volume is excessively loud and adjusting the volume control does not make much of a difference. If I max out the volume - very loud, if I minimize the volume - still very loud but sound quality is heavily degraded. This issue seems to be global, since it does not matter whether I am watching youtube or playing music in Rhythmbox.

So the questions I have are these:
1) Has anyone experienced something like this before?
2) How can I determine what sound driver is in use and whether it is working properly?
3) Are there other options I can take? Different sound drivers I can try?
4) How can I uninstall/reinstall sound drivers?

Thank you for your time.
Billius

---

### Post by alexfish on 2009-11-15
> **billiusmaximus said:**
> [Repost] - felt like this might be a more appropriate place to post my concern.

Hello,

I just joined the Ubuntu community today - but I would say I am an intermediate Linux user. I have been exploring Ubuntu since 8.04.

I upgraded my Dell Laptop from 9.04 to 9.10 and it works almost perfectly except for some sound issues. The sound technically works, but the volume is excessively loud and adjusting the volume control does not make much of a difference. If I max out the volume - very loud, if I minimize the volume - still very loud but sound quality is heavily degraded. This issue seems to be global, since it does not matter whether I am watching youtube or playing music in Rhythmbox.

So the questions I have are these:
1) Has anyone experienced something like this before?
2) How can I determine what sound driver is in use and whether it is working properly?
3) Are there other options I can take? Different sound drivers I can try?
4) How can I uninstall/reinstall sound drivers?

Thank you for your time.
Billius

check to see which sound you have alsa or pulse
Ubuntu 9.10 comes with pulse audio  some people revert back to alsa  there are links to this in the forum however from a clean install     i installed pavucontrol in synaptic pkg manager  this once installed check to see if the pavdevchooser and volumemeter has installed if not install them and check to see if there are any plugins required depending on software you have installed .goto apps sounds and video click on the pulse audio device chooser the jack should appear in the top right panel click on it and select configure local sound server click your options / also check this goto   system admin users and groups click on the keys/click to make changes /enter your password click on manage groups  /go down the list and find pulse entries click on each one in turn and anclick properties /check the boxes
root and user  that will be your log in name /once done you may have can see how the system is set up from that devchooser jack . the volume meter etc will show you how many channels are open  also you may need to set sound option in each program

---

### Post by alexfish on 2009-11-15
also search this site

[http://en.wikipedia.org/wiki/PulseAudio](http://en.wikipedia.org/wiki/PulseAudio)

it has useful info and links / how to etc

---

### Post by billiusmaximus on 2009-11-15
> **alexfish said:**
> check to see which sound you have alsa or pulse
Ubuntu 9.10 comes with pulse audio  some people revert back to alsa  there are links to this in the forum however from a clean install     i installed pavucontrol in synaptic pkg manager  this once installed check to see if the pavdevchooser and volumemeter has installed if not install them and check to see if there are any plugins required depending on software you have installed .goto apps sounds and video click on the pulse audio device chooser the jack should appear in the top right panel click on it and select configure local sound server click your options / also check this goto   system admin users and groups click on the keys/click to make changes /enter your password click on manage groups  /go down the list and find pulse entries click on each one in turn and anclick properties /check the boxes
root and user  that will be your log in name /once done you may have can see how the system is set up from that devchooser jack . the volume meter etc will show you how many channels are open  also you may need to set sound option in each program

I believe that I am using ALSA - but how do I confirm this? I figured this because I was messing with the Alsamixer and noticed that when I increase the master volume from the applet on the desktop bar, the PCM and LFE channels increased VERY rapidly (they maxed out almost immediately) and the 'Master' channel increased much more slowly.

Is it possible to correct this behavior and make the volume increase more steadily?

How can I "convert" to Pulse from ALSA?

Also, I do not know what you mean by 'pavdevchooser' and 'volumemeter'. A search in Synaptic yielded no results.

Thank you for your time.
Billius

---

### Post by alexfish on 2009-11-16
Hi been to Bed

if you go to system admin users and groups click the box click to make changes
enter your password  and click on manage groups click do you see any entries for pulse
if there click each one in turn and then click on properties the boxes user and root need to be checked 
if pulse is not there then pulse  may not be installed

can you try this from the terminal and post the results
$ aplay -l
$  gedit /etc/pulse/daemon.conf




if you go to synaptic type in the seach area type in " pulse"

in the listings you should pulse bits
are any of the pulse boxes green

look down the list 

can you see
 padevchooser
pavumeter
pavucontrol

or anything with pulse

if nothing in pulse  you can try this

right click the loudspeaker / top right panel
to open then control
if its alsa then the alsa switches with be visible
are they single or double
if there double there should be a chain showing at the bottom
you can click on the chain to break it this gives you seperate control over the channels
also hovering over the switches with the mouse a description should show what channel is which

if the switches are single then you may have to play around with the sound prefs and swiches to get the desired result

also found this thread worth looking into

[http://ubuntuforums.org/showthread.php?t=1306443](http://ubuntuforums.org/showthread.php?t=1306443)

---

### Post by billiusmaximus on 2009-11-16
I attached a script of the output of the commands:
aplay -l
cat /etc/pulse/daemon.conf

And I was able to find the 'padevchooser' and 'pavumeter' and 'pavucontrol' packages and installed them.

Thanks for your time.
Billius

---

### Post by billiusmaximus on 2009-11-16
Also, I forgot to mention that I did see pulse entries in the users and groups properties and I made sure I checked the boxes for both my username and root.

---

### Post by alexfish on 2009-11-16
ok 
do you now see the pulse audio device chooser in the apps sounds & video
also go to system preferences do you see pulse audio preferences

if so click the audio device chooser in the apps
the jack should show up in the top right panel

click on it and you will see a dropdown menu list

let me know if this there

---

### Post by billiusmaximus on 2009-11-16
Yes, the PulseAudio applet appeared in the top right panel. I click it and there is a dropdown menu.

Billius

---

### Post by feddozz on 2009-11-16
Hi
same proiblem here.
I just checked the boxes for both my username and root  for the pulse entries in the users and groups properties. It was not checked.
I rebooted but pulse is not appearing yet in Application-> Sound & Video.
Also here is what i get when I issue 

```
aplay -l
```

```

feddozz@feddozz-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
feddozz@feddozz-laptop:~$ ^C
feddozz@feddozz-laptop:~$

```

Can you help me?
Thanks

---

### Post by alexfish on 2009-11-16
the menu list should be something like this

default server
default sink
default sauce
-----------------
manager
volume control
volume meter play back
volume meter recording
configure local sound server
preferences
-----------------
quit


Click on the manager

look at the pages
server info
devices  
clients
modules
sample cachet

under the server info
 what is the default sink
what is the default sources

under devices do the sinks and sources match server info and does the description match your device from the aplay-l command that you did in console

in the clients you prob see

cosolekit
gnome volume control media keys
esound client(unix socket client)
gnome volume control applet
esound client 
esound client
esound cliend  
libcanbera
pulse audio manager

in the sample cachet what does the playback on show

Next rightclick the loudspeaker and open up the sound preferences
in the output you will see the sliders that relate to the output you pick
when done let me know /

check that the sound is not muted
click on the hardware
you should see your card and a drop down box with a list of options
for testing mine i picked a playback with 5.1 sound
  you may still have no sound at this stage

---

### Post by billiusmaximus on 2009-11-16
> **alexfish said:**
> 

if you go to synaptic type in the seach area type in " pulse"

in the listings you should pulse bits
are any of the pulse boxes green

look down the list 

can you see
 padevchooser
pavumeter
pavucontrol

or anything with pulse



Did you try doing this yet? This should install the required packages and allow you to see the PulseAudio applications under 'sound and video.'

---

### Post by billiusmaximus on 2009-11-16
@Alexfish: I must run a few errands but I will get back to you in an hour or two.

Thanks,
Billius

---

### Post by feddozz on 2009-11-16
> **billiusmaximus said:**
> Did you try doing this yet? This should install the required packages and allow you to see the PulseAudio applications under 'sound and video.'

Ok I installed pavu packages and now I have got pulse in Application->Sound&Vid
I opened volume control while playing a youtube video, on the tab playback I can see the volume bar moving. On the tab Output devices says i don't have any hardware output devices available

---

### Post by feddozz on 2009-11-16
ok now post #11 is clear
in server info 
default sink=auto_null
default Source= auto_null.monitor

In devices sink and source match those in server info but no match with aplay-l list

Sample cache playback=auto_null

in sound preference output I see only one device called Dummy output

Hope I collected all the info
thanks!

---

### Post by alexfish on 2009-11-16
> **feddozz said:**
> ok now post #11 is clear
in server info 
default sink=auto_null
default Source= auto_null.monitor

In devices sink and source match those in server info but no match with aplay-l list

Sample cache playback=auto_null

in sound preference output I see only one device called Dummy output

Hope I collected all the info
thanks!
I am seeing from your list something which seems odd ie modem device
check your hard ware with a device manager

you need to right click the loudspeaker icon to get the sound prefs

ps what mother board is it
do you have add on cards if your using on board sound make sure its available from the bios
and that the sound system is connected to the correct jacks
was it a clean install of ubuntu or an upgrade

added  / 18 November
your software modem is found with the aplay -l in the console

try this link for cure

[http://ubuntuforums.org/showpost.php?p=8317477&postcount=1639](http://ubuntuforums.org/showpost.php?p=8317477&postcount=1639)

---

### Post by feddozz on 2009-11-16
I upgraded from 9.04
Sound pref hardware list empty
I am using onboard sound
It's a laptop toshiba portege'
What info do you need about the modem?

---

### Post by alexfish on 2009-11-16
> **feddozz said:**
> I upgraded from 9.04
Sound pref hardware list empty
I am using onboard sound
It's a laptop toshiba portege'
What info do you need about the modem?
some people are experiencing problems after upgrade
if ubuntu is the only os on your toshiba it may be worthwhile doing a clean install using whole hard drive if you got os or home directory you want to keep then follow another thread / there are threads in the forum. back soon

try looking here

[http://ubuntuforums.org/showthread.php?t=246906](http://ubuntuforums.org/showthread.php?t=246906)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[http://ubuntuforums.org/showthread.php?p=8328294#post8328294](http://ubuntuforums.org/showthread.php?p=8328294#post8328294)

---

### Post by billiusmaximus on 2009-11-16
> **alexfish said:**
> some people are experiencing problems after upgrade
if ubuntu is the only os on your toshiba it may be worthwhile doing a clean install using whole hard drive if you got os or home directory you want to keep then follow another thread / there are threads in the forum. back soon

Isn't easier to just copy the home directory onto another media such as an external HDD, thumb drive, or CD/DVD?

---

### Post by alexfish on 2009-11-16
hi maximus 

how is pulse going

yes some times easier for the home directory

---

### Post by billiusmaximus on 2009-11-16
@alexfish:

Default Sink: alsa_output.pci-0000_00_1b.0.analog-stereo
Default Source: alsa_input.pci-0000_00_1b.0.analog-stereo

And yes, the devices match the server info. However, under devices, there is a second source:
alsa_output.pci0000_00_1b.0.analog-stereo.monitor

Not sure what that means.

Under clients, I see everything in your list except 'libcanbera' and 'consolekit.' So I searched for consolekit in Synaptic and it is already installed.

Thanks,
Billius

---

### Post by alexfish on 2009-11-16
they seem fine 
play some music with your player  select  volume meter  playback from the jack
any results showing
next step is to try 

select system prefs pulse audio prefs

these are the boxes i checked
network access  / make discoverable pulse audio sound devs available locally
network server / enably network acess to local sound devices
simultaneous output / add virtual output device for for simultaneous output on all local sound cards

maybe try a reboot and test again

---

### Post by alexfish on 2009-11-16
this is a screen shot of what i have
/home/alex/Desktop/Screenshot.png

---

### Post by alexfish on 2009-11-16
this is another screen shot with the volume control sliders unlocked
they should move independant of each other

---

### Post by billiusmaximus on 2009-11-16
Unfortunately, there has been no change to the behavior of my volume control. I am thinking perhaps I might uninstall all the pulse stuff and try reinstalling.

I am also considering doing a fresh installation of 9.10 to see if that resolves the issue. However, I am dual booting XP/Ubuntu and I am not sure if I know how to repave Ubuntu and leave XP untouched. I am sure it's possible though.

I provided 4 screenshots of alsamixer. The first shows everything muted, and from there I incremented the master volume slightly, as you can see on the right side of my screen. Then notice how the alsamixer behaves on the left.

Thanks,
Billius

---

### Post by alexfish on 2009-11-16
your top slider seem to be set to 0
but showing 100%
try moving the slider to full ( move it to the right )

---

### Post by alexfish on 2009-11-16
try selecting pulse audio volume control from apps
here is a screen shot 
the window on the left is it

click on the play back 
goto apps 
select totem movie player
goto edit preferences  click on the audio 
and select which matches your speaker set up
play a tune does it look like this attached screenshot


added 
is your system amd64 or 32bit / looking at other threads 64 bit seem to have bigger headaches

added
 links for pulse worth looking at
for first steps look at first link

pulse ubuntu sound

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

[https://help.ubuntu.com/community/So...otingProcedure](https://help.ubuntu.com/community/So...otingProcedure) ' link not working from here ? taken from another thread

should be "https://help.ubuntu.com/community/SoundTroubleshootingProcedure"
........................................................................
[http://en.wikipedia.org/wiki/PulseAudio](http://en.wikipedia.org/wiki/PulseAudio)

[http://en.wikipedia.org/wiki/PulseAudio](http://en.wikipedia.org/wiki/PulseAudio)

[http://en.wikipedia.org/wiki/Adobe_Flash#Video_in_web_pages](http://en.wikipedia.org/wiki/Adobe_Flash#Video_in_web_pages)
[http://ubuntuforums.org/showthread.php?t=1305924&highlight=install+home+directory](http://ubuntuforums.org/showthread.php?t=1305924&highlight=install+home+directory)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
...........................................................................
 tutorial quotes

[http://www.unix-tutorials.com/search.php?act=search&term=Enable+Surround+Sound+in+Ubuntu+Linux+%28PulseAudio%29]("http://www.unix-tutorials.com/search.php?act=search&term=Enable+Surround+Sound+in+Ubuntu+Linux+%28PulseAudio%29")
..........................................................
added link for enabling speaker channels

[http://www.unix-tutorials.com/go.php?id=4126](http://www.unix-tutorials.com/go.php?id=4126)
[http://mybroadband.co.za/vb/blog.php?b=303](http://mybroadband.co.za/vb/blog.php?b=303)

---

### Post by Mosdarkrai on 2009-11-18
to test, use this code:
$ speaker-test -twav -c2

---

### Post by alexfish on 2009-11-28
added link for alsa / sound cards / etc  worth looking at

[http://www.topology.org/linux/alsa.html](http://www.topology.org/linux/alsa.html)

---

