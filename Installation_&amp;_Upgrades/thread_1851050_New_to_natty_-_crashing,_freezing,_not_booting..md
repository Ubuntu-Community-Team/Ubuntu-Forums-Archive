---
title: "New to natty - crashing, freezing, not booting."
date: 2011-09-27
forum: Installation &amp; Upgrades
---

### Post by Stray Wolf on 2011-09-27
I was only going to use LTS releases but I upgraded my graphics card (EVGA Nvidia GeForce 520 GT) to handle HD on my desktop (hp pavilion m8330f).  Well, the drivers were outdated in Lucid so I installed Natty.  I don't mind the new interface.  It's different so I expected to be lost half the time.  What I didn't expect was the difficulty in getting the desktop to fit my screen since the slider in Nvidia's settings menu was off screen.  Then, I wasn't getting audio and HDMI out wasn't showing up in sound preferences.  I installed pulse and alsa mixers and the HDMI out appeared in the sound preferences.  I selected it and viola!  I have sound.  Unfortunately, even with all the volume levels maxed out it's way more quiet than my other devices.  When I switch the audio from my desktop to my Xbox or my radio I almost blow my speakers when I forget to turn the volume down.  Kind of scares the buh-jeezus out of me!  Banshee worked long enough to import my music and play it a little.  Now it crashes before opening.  The Nvidia settings menu sometimes crashes the whole system when changes are attempted to be made.  Opening firefox is a roll of the dice.  Sometimes it works - sometimes it freezes the whole system - sometimes it logs me off only to log back on, select firefox, and freeze the whole system.  The whole reason for this was me trying to have my desktop stream HD from Hulu and such as good as my laptop does.  Hulu actually worked after only crashing my system once!  It even suppressed the screen saver like I always wanted.  The picture is crisp and clear in still shots but movement makes everything jerk and lag.  So, epic fail.  It works just like it did before the added graphics card and ram.  If anyone can help me watch high quality video without jerk/lag it would be much appreciated.  The other issues like banshee crashing itself, firefox crashing everything, and boosting audio output to match other devices can be on the back burner for now.

Anyway...that's my story.  I started with Karmic and upgraded to Lucid when it came out.  Those two must have spoiled me because I never had so many things go so wrong out-of-the-box like they have on Natty.  I don't see what the hubbub was about Unity.  I've never had a system stay looking like it does out-of-the-box anyway.  I'll actually have fun getting used to it.

---

### Post by MAFoElffen on 2011-09-27
> **Stray Wolf said:**
> I was only going to use LTS releases but [COLOR=Green]I upgraded my graphics card (EVGA Nvidia GeForce 520 GT) to handle HD on my desktop[/COLOR] (hp pavilion m8330f). [COLOR=Green] Well, the drivers were outdated in Lucid so I installed Natty[/COLOR].  I don't mind the new interface.  It's different so I expected to be lost half the time.  What I didn't expect was the difficulty in getting the desktop to fit my screen since the slider in Nvidia's settings menu was off screen.  Then, I wasn't getting audio and HDMI out wasn't showing up in sound preferences.  I installed pulse and alsa mixers and the HDMI out appeared in the sound preferences.  I selected it and viola!  I have sound.  Unfortunately, even with all the volume levels maxed out it's way more quiet than my other devices.  When I switch the audio from my desktop to my Xbox or my radio I almost blow my speakers when I forget to turn the volume down.  Kind of scares the buh-jeezus out of me!  Banshee worked long enough to import my music and play it a little.  Now it crashes before opening.  The Nvidia settings menu sometimes crashes the whole system when changes are attempted to be made.  Opening firefox is a roll of the dice.  Sometimes it works - sometimes it freezes the whole system - sometimes it logs me off only to log back on, select firefox, and freeze the whole system.  The whole reason for this was me trying to have my desktop stream HD from Hulu and such as good as my laptop does.  Hulu actually worked after only crashing my system once!  It even suppressed the screen saver like I always wanted.  The picture is crisp and clear in still shots but movement makes everything jerk and lag.  So, epic fail.  It works just like it did before the added graphics card and ram.  If anyone can help me watch high quality video without jerk/lag it would be much appreciated.  The other issues like banshee crashing itself, firefox crashing everything, and boosting audio output to match other devices can be on the back burner for now.

Anyway...that's my story.  I started with Karmic and upgraded to Lucid when it came out.  Those two must have spoiled me because I never had so many things go so wrong out-of-the-box like they have on Natty.  I don't see what the hubbub was about Unity.  I've never had a system stay looking like it does out-of-the-box anyway.  I'll actually have fun getting used to it.
As Hindsight--  
 - You upgraded your Video Card while under 10.04 LTS and your video card driver did not support the new card...

Why did you not install a driver for your new card while in 10.04 LTS?  Just curious...

 - Anyways. then you did a dist-upgrade to 10.10 and 11.04(?)  

Did you install the correct Video driver for your card yet?  (Because allot on the playback and compiz also deal with the GPU driver...)

*** Other's described is changes and diffrrences in the interface (Unity).  Unity Classic would be the interface you were used to in the past...

I see that you've corrected a lot of things on your own, but have gotten lost in your narration on what problems remain...What problems do you need help with at the moment.

---

### Post by Stray Wolf on 2011-09-27
> **MAFoElffen said:**
> As Hindsight--  
 A- You upgraded your Video Card while under 10.04 LTS and your video card driver did not support the new card...

Why did you not install a driver for your new card while in 10.04 LTS?  Just curious...

 B- Anyways. then you did a dist-upgrade to 10.10 and 11.04(?)  

C- Did you install the correct Video driver for your card yet?  (Because allot on the playback and compiz also deal with the GPU driver...)

D- *** Other's described is changes and diffrrences in the interface (Unity).  Unity Classic would be the interface you were used to in the past...

E- I see that you've corrected a lot of things on your own, but have gotten lost in your narration on what problems remain...What problems do you need help with at the moment.

A- It was my understanding that the latest Nvidia drivers were only available on the newest OS.  I tried under 10.04 in the terminal to install drivers and the output was that I already have the current drivers.  I should have looked into it more but from what I read I thought upgrading the OS to 11.04 would have been the quickest route.  LOL!

B- No, I didn't really upgrade.  I nuked Lucid and installed Natty over it.  Sorry for not being specific.

C- The driver installed automatically.  The nvidia-settings menu still scares me because it's crashed my system quite a bit.  I did manage to set the overscan to correct parameters.  I was going to experiment with resolutions but thats one of the things that seems to crash my system as soon as I touch it.

D- I used cairo-dock along with a lot of ccsm mods.  I only used a shrunk gnome panel on auto-hide as a notification area.  It was unrecognizable to people who just use Ubuntu out-of-the-box.

E- The pressing issue for me is that I spent money on graphics and ram to have Hulu stream at 720p.  Before my wife notices I spent all that money with no change in video quality...I'd like to fix it.  Hulu streams HD flawlessly on my laptop.  So, I know it's possible.  Sorry to throw so many things at the feet of this gracious community all at once.  But yeah, I don't want the wife to complain.  So, how can I help you help me stop Hulu from lagging and jerking in HD?  The picture quality is sharp...but when a camera pans or there's movement it gets kinda trippy.

---

### Post by MAFoElffen on 2011-09-27
> **Stray Wolf said:**
> 
E- The pressing issue for me is that I spent money on graphics and ram to have Hulu stream at 720p.  Before my wife notices I spent all that money with no change in video quality...I'd like to fix it.  Hulu streams HD flawlessly on my laptop.  So, I know it's possible.  Sorry to throw so many things at the feet of this gracious community all at once.  But yeah, I don't want the wife to complain.  So, how can I help you help me stop Hulu from lagging and jerking in HD?  The picture quality is sharp...but when a camera pans or there's movement it gets kinda trippy.
LMFAO!!!

Yes, that wife thing is really embarrassing! (Personal experience on that!)

Please post the results of these:
```
[FONT=monospace]
[/FONT]/usr/lib/nux/unity_support_test -p[FONT=monospace]
[/FONT]lspci -nn | grep VGA[FONT=monospace]
[/FONT]uname -r
hwinfo --monitor
hwinfo --framebuffer
xrandr -q

```
And please post your /var/log/Xorg.0.log and /etc/X11/xorg.conf

---

### Post by MAFoElffen on 2011-09-27
After thinking bout this and with the playback problems, if you installed and ran compiz-check, it might give us more pertinent info on what is going on on your box.  Here is some instructions on how to do that:
> 
The current version of the script is available [COLOR=Red][here]("http://blogage.de/files/70708/download").[/COLOR]
  You can use this command to download it to your home directory: 
```

[COLOR=#121212]wget [http://blogage.de/files/70708/download](http://blogage.de/files/70708/download) -O compiz-check[/COLOR]
 
```
Afterwards, you have to make it executable:  
```

[COLOR=#121212]chmod +x compiz-check[/COLOR]
 
```
And finally run it like this:  [COLOR=#121212]
```

./compiz-check

```[/COLOR] 
Keep in mind that you have to be in the directory the script is located at to make it work.
In case you want to use it anywhere (and by any user), you have to store it in your $PATH environment variable (e.g. /usr/local/bin).

 Afterwards you will be able to run Compiz-Check by running [COLOR=#121212]compiz-check[/COLOR] no matter where you are.


---

### Post by Stray Wolf on 2011-09-27
Hope this doesn't wear out your mouse wheel...

XXXX@XXXX:~$ usr/lib/nux/unity_support_test -p
bash: usr/lib/nux/unity_support_test: No such file or directory
and:
XXXX@XXXX:~$ user/lib/nux/unity_support_test -p
bash: user/lib/nux/unity_support_test: No such file or directory
then:
XXXX@XXXX:~$ lspci -nn | grep VGA
02:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:1040] (rev a1)
then:
XXXX@XXXX:~$ uname -r
2.6.38-11-generic

then:
XXX@XXX:~$ hwinfo --monitor
                                              > hal.1: read hal dataprocess 2136: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                -I'd like to note that the terminal create a huge blank space between the output and the new prompt (XXX@XXX:~$).  So much so that I had to scroll up a page to even see it.
then:
XXXX@XXXX:~$ hwinfo --framebuffer
                                              > hal.1: read hal dataprocess 2160: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files

-same large blank page
then:
XXXX@XXXX:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1280 x 720, maximum 1280 x 720
default connected 1280x720+0+0 0mm x 0mm
   1280x720       50.0*    51.0  
   960x720        52.0     53.0  
   960x600        54.0  
   960x540        55.0  
   928x696        56.0     57.0  
   896x672        58.0     59.0  
   840x525        60.0     61.0     62.0     63.0     64.0  
   832x624        65.0  
   800x600        66.0     67.0     68.0     69.0     70.0     71.0     72.0     73.0     74.0     75.0  
   800x512        76.0  
   720x480        77.0     78.0  
   720x450        79.0  
   720x400        80.0  
   700x525        81.0     82.0     83.0     84.0  
   680x384        85.0     86.0  
   640x512        87.0     88.0     89.0  
   640x480        90.0     91.0     92.0     93.0     94.0     95.0     96.0  
   640x400        97.0  
   640x350        98.0  
   576x432        99.0    100.0    101.0    102.0    103.0    104.0    105.0  
   512x384       106.0    107.0    108.0    109.0    110.0  
   416x312       111.0  
   400x300       112.0    113.0    114.0    115.0    116.0  
   360x200       117.0  
   320x240       118.0    119.0    120.0    121.0  
   320x200       122.0  
   320x175       123.0  
Then following your next post I ran compiz check.  I'm going to paraphase the output since the system froze at a certain point.  Output: Gathering info about system...
Distribution:  Ubuntu 11.04
Desktop Environment:  Gnome
Graphics Chip: nVidia Corporation Device 1040 (rev a1)
Driver in use: nVidia
Rendeing Method: nVidia
Checking if its possible to run compiz...
Checking for texture_from_pixmap...

BOOSH!  That's where it locked up.  Waited ten minutes then hard shut-down.

---

### Post by MAFoElffen on 2011-09-27
> **Stray Wolf said:**
> Hope this doesn't wear out your mouse wheel...
```

XXXX@XXXX:~$ lspci -nn | grep VGA
02:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:1040] (rev a1)

``````
XXXX@XXXX:~$ uname -r
2.6.38-11-generic

``````

davis@Zero-GX612AA-ABA-m8330f:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1280 x 720, maximum 1280 x 720
default connected 1280x720+0+0 0mm x 0mm
   1280x720       50.0*    51.0  
   960x720        52.0     53.0  
   960x600        54.0  
   960x540        55.0  
   928x696        56.0     57.0  
   896x672        58.0     59.0  
   840x525        60.0     61.0     62.0     63.0     64.0  
   832x624        65.0  
   800x600        66.0     67.0     68.0     69.0     70.0     71.0     72.0     73.0     74.0     75.0  
   800x512        76.0  
   720x480        77.0     78.0  
   720x450        79.0  
   720x400        80.0  
   700x525        81.0     82.0     83.0     84.0  
   680x384        85.0     86.0  
   640x512        87.0     88.0     89.0  
   640x480        90.0     91.0     92.0     93.0     94.0     95.0     96.0  
   640x400        97.0  
   640x350        98.0  
   576x432        99.0    100.0    101.0    102.0    103.0    104.0    105.0  
   512x384       106.0    107.0    108.0    109.0    110.0  
   416x312       111.0  
   400x300       112.0    113.0    114.0    115.0    116.0  
   360x200       117.0  
   320x240       118.0    119.0    120.0    121.0  
   320x200       122.0  
   320x175       123.0  

```BOOSH!  That's where it locked up.  Waited ten minutes then hard shut-down.
So essentially, the above was the only output from all those commands? hwinfo not returning info from your montior or GPU would be a concern, but lspci saw the GPU and xrandr saw the monitor...

Admin note- When posting output, code or logs- please use the "#" button in the posting tool bar to insert CODE tags and paste the text within the tags.

So really went "Boosh" when accessing the compiz files and config?  Does it help if you do this:
```

sudo compiz --replace
sudo metacity --replace

```And still haven't seen your /var/log/Xorg.0.log and /etc/X11/xorg.conf files...

---

### Post by Stray Wolf on 2011-09-28
Ooops!  The logs are attached.  Is it easier to have .txt files attached or to have the actual text just copied and pasted in the post?
Since those commands were ran on a system that doesn't seem to like multitasking right now...should I run them with firefox closed?  I at least have to run gedit to save the output.  I guess you'll let me know.  Thanks a million!

---

### Post by MAFoElffen on 2011-09-28
> **Stray Wolf said:**
> Ooops!  The logs are attached.  Is it easier to have .txt files attached or to have the actual text just copied and pasted in the post?
Since those commands were ran on a system that doesn't seem to like multitasking right now...should I run them with firefox closed?  I at least have to run gedit to save the output.  I guess you'll let me know.  Thanks a million!
Doesn't matter to me.  Either way.

I see a few things...

First in this section of your xorg.conf:
```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 520"
EndSection

```You should add a few lines pointing to where your card is in the PCI BusID
```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 520"
[COLOR=Teal]    BusID          "PCI:2:0:0"
    Screen         0
[/COLOR]EndSection
 
``````

[    20.858] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    20.858] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    20.858] (--) NVIDIA(0): Connected display device(s) on GeForce GT 520 at PCI:2:0:0
[    20.858] (--) NVIDIA(0):     Panasonic-TV (DFP-1)
[    20.858] (--) NVIDIA(0): Panasonic-TV (DFP-1): 165.0 MHz maximum pixel clock
[    20.858] (--) NVIDIA(0): Panasonic-TV (DFP-1): Internal Single Link TMDS
[    20.879] (II) NVIDIA(0): Assigned Display Device: DFP-1
[    20.879] (II) NVIDIA(0): Validated modes:
[    20.879] (II) NVIDIA(0):     "1280x720+0+0"
[    20.879] (II) NVIDIA(0): Virtual screen size determined to be 1280 x 720
[    20.908] (WW) NVIDIA(0): Panasonic-TV (DFP-1)'s EDID does not contain a maximum image
[    20.908] (WW) NVIDIA(0):     size; cannot compute DPI from Panasonic-TV (DFP-1)'s
[    20.908] (WW) NVIDIA(0):     EDID.
[    20.908] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    20.908] (--) Depth 24 pixmap format is 32 bpp

```Hmmm.  The xorg log shows a problem seeing EDID and calculating modes.  All it sees as a mode is "1280 by 720... which is fine and not causing your distortion problem.

It sure seems like the nvidia kernel (nvidia_drv.so) is getting loaded late.  On your box it's almost the last module loaded...but even that doesn't seem to be throwing any errors and is fine...

*** If you start up in Ubuntu Classic (no effects, no compiz loaded), do you have the same video problems?

You're using nvidia-current right?

---

### Post by Stray Wolf on 2011-09-28
> **MAFoElffen said:**
> Doesn't matter to me.  Either way.

A-It sure seems like the nvidia kernel (nvidia_drv.so) is getting loaded late.  On your box it's almost the last module loaded...but even that doesn't seem to be throwing any errors and is fine...

B-*** If you start up in Ubuntu Classic (no effects, no compiz loaded), do you have the same video problems?

C-You're using nvidia-current right?
 
A- My system boots up maybe 1 out of 3 tries.  I noticed that the times it actually boots up is when I see the screen go from purple to the nVidia splash screen for a half a second then black for a few seconds, then the pointer then the desktop.  When I don't see the nVidia splash screen the system goes from purple to black and I have to hard shut down and try again.

B-I haven't started in Ubuntu Classic.  My PC is set to log in without a password so it just loads the desktop.

C-I'll double check.  I guess I just assumed it would have installed the latest available drivers.  What was the command? sudo apt-get install nvidia_current?

I've trolled the forums a bit while at work today and stumbled across a few things I may try when I get home this evening.  First:
apt-cache policy xserver-xgl
then if running XGL I need to:
sudo apt-get remove --purge xserver-xgl

My system is pretty choppy too and I saw this:
1)Install and run ccsm
2)On the Composite tab uncheck "Detect Refresh Rate"
3)On the OpenGL tab uncheck "Sync to Vblank"

I'll be amazed if those steps solve the problem but my hope is that it helps.  I'll also be modifying that xorg.conf file.

---

### Post by MAFoElffen on 2011-09-28
> **Stray Wolf said:**
> A- My system boots up maybe 1 out of 3 tries.  I noticed that the times it actually boots up is when I see the screen go from purple to the nVidia splash screen for a half a second then black for a few seconds, then the pointer then the desktop.  When I don't see the nVidia splash screen the system goes from purple to black and I have to hard shut down and try again.

B-I haven't started in Ubuntu Classic.  My PC is set to log in without a password so it just loads the desktop.

C-I'll double check.  I guess I just assumed it would have installed the latest available drivers.  What was the command? sudo apt-get install nvidia_current?

I've trolled the forums a bit while at work today and stumbled across a few things I may try when I get home this evening.  First:
apt-cache policy xserver-xgl
then if running XGL I need to:
sudo apt-get remove --purge xserver-xgl

My system is pretty choppy too and I saw this:
1)Install and run ccsm
2)On the Composite tab uncheck "Detect Refresh Rate"
3)On the OpenGL tab uncheck "Sync to Vblank"

I'll be amazed if those steps solve the problem but my hope is that it helps.  I'll also be modifying that xorg.conf file.
Before doing:
```

sudo apt-get install nvidia-current

```
Check to see what is installed via System > Administration > Additional Driver or from the commandline:
```

gtksudo jockey-gtk

```
Check in that applet to see what "is" installed.

Sure... Follow those leads and tell me how it goes for you.

---

### Post by Stray Wolf on 2011-09-28
Seems I'm running the current version of nVidia as per jockey and the terminal.  I modified the Xorg.conf file.  Rebooted and did the ccsm thing too.  I'm not running XGL.  So, I guess I'll test Hulu now... the desktop seems to be running more smoothly.  I'll get back with you after some experimenting.

---

### Post by MAFoElffen on 2011-09-28
> **Stray Wolf said:**
> Seems I'm running the current version of nVidia as per jockey and the terminal.  I modified the Xorg.conf file.  Rebooted and did the [COLOR=Red]ccsm thing too[/COLOR].  I'm not running XGL.  So, I guess I'll test Hulu now... the desktop seems to be running more smoothly.  I'll get back with you after some experimenting.
I'll be here...

Hey you may have missed a few steps in the cssm fix, especially since your are running nvidia:
_Step 1_
- sudo apt-get install compizconfig-settings-manager
- Open up the CompizConfig Settings manager via the *System > Preferences* menu
- On the Composite tab uncheck "Detect Refresh Rate"
 - Click the &#8216;*General Options*&#8216; button and go to the &#8216;*Display Settings*&#8216; tab
- Change the &#8216;refresh rate&#8217; to &#8217;60&#8242; using the slider (though higher if you&#8217;re a gamer, etc.  What it really should be set to is the refresh rate of the "Resolution Mode" that the card and monitor is set to)
- On the OpenGL tab uncheck "Sync to Vblank" to disable it.
_Step 2_
- Open Nvidia X Server Settings Via the *System > Preferences* Menu
- Choose &#8216;OpenGL Settings&#8217; on the left-hand side
- Check the box next to &#8220;Sync To VBlank&#8221; to enable it
- Exit from the nvidia-setting app.
- Reboot

What that does for Compiz and Nvidia is to disable the sync to vsync in compiz and turns it over to your nvidia card.  That way the hardware is taking care of it itself.

---

### Post by Stray Wolf on 2011-09-29
> **MAFoElffen said:**
> I'll be here...

Hey you may have missed a few steps in the cssm fix, especially since your are running nvidia:
_Step 1_
- sudo apt-get install compizconfig-settings-manager
- Open up the CompizConfig Settings manager via the *System > Preferences* menu
- On the Composite tab uncheck "Detect Refresh Rate"
 - Click the &#8216;*General Options*&#8216; button and go to the &#8216;*Display Settings*&#8216; tab
- Change the &#8216;refresh rate&#8217; to &#8217;60&#8242; using the slider (though higher if you&#8217;re a gamer, etc.  What it really should be set to is the refresh rate of the "Resolution Mode" that the card and monitor is set to)
- On the OpenGL tab uncheck "Sync to Vblank" to disable it.
_Step 2_
- Open Nvidia X Server Settings Via the *System > Preferences* Menu
- Choose &#8216;OpenGL Settings&#8217; on the left-hand side
- Check the box next to &#8220;Sync To VBlank&#8221; to enable it
- Exit from the nvidia-setting app.
- Reboot

What that does for Compiz and Nvidia is to disable the sync to vsync in compiz and turns it over to your nvidia card.  That way the hardware is taking care of it itself.

I'm using ccsm.  It must be a it different from the version you have but I think I got it.  I installed hardinfo and it crashes the system when it show "Scanning display..." but when it does work it generates a pretty thorough system report.  I've also had more consecutive successful boot-ups.

Oh yeah!  Hulu was still jerky before you had the notion to make Compiz and Nvidia know their place.  I'm off to double check these settings and try Hulu again...Colbert Report this time!  

-Yeah, still jerky.  I don't mind if you give up on me but I'm going to keep bumping this thread.  I'm glad I did the new install for the experience.  There's got to be a way since Hulu and the like are flawless on my laptop.  But that was out-of-the-box so it's not like I made it run like that.  I just figure that it's possible to reproduce and I'm sure I've got the right hardware.  If you want me to run or re-run any more commands let me know.  I could generate a hardinfo report...

---

### Post by MAFoElffen on 2011-09-29
Not reasy to give up on you yet.  You have me curious now...

Have you tried this? >>  [Firefox Flash-Aid plugin]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")

---

### Post by Stray Wolf on 2011-09-29
> **MAFoElffen said:**
> Not reasy to give up on you yet.  You have me curious now...

Have you tried this? >>  [Firefox Flash-Aid plugin]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")

Will do!  I don't get home to the desktop until 6:30PM CST.  I was also thinking along the lines of seeing if MythTV works with Hulu and streams better but your solution may be to the core of the issue.

---

### Post by Stray Wolf on 2011-09-30
I tried flash-aid.  It moves or renames libflashplayer.so. and the Hulu desktop can't find it.  I can fix that though.  But flash-aid installs a beta version of flash that does drop less frames, but it also has deinterlace issues (horizontal lines occasionally dance across the screen).  I didn't post anything last night because the system was crashing a lot.  I reinstalled the stable version of flash and tried right clicking on a video and adjusting some settings.  The only one I saw was for "hardware acceleration".  I had to adjust some settings in BetterPrivacy so flash settings LSO's would be stored then tried it in FF and in the Hulu desktop.  Really didn't notice a difference between enabled acceleration and disabled.

Maybe there's a way to adjust the frame rate and deinterlace in flash.  I'm going to go troll for more answers.

---

### Post by MAFoElffen on 2011-10-01
> **Stray Wolf said:**
> I tried flash-aid.  It moves or renames libflashplayer.so. and the Hulu desktop can't find it.  I can fix that though.  But flash-aid installs a beta version of flash that does drop less frames, but it also has deinterlace issues (horizontal lines occasionally dance across the screen).  I didn't post anything last night because the system was crashing a lot.  I reinstalled the stable version of flash and tried right clicking on a video and adjusting some settings.  The only one I saw was for "hardware acceleration".  I had to adjust some settings in BetterPrivacy so flash settings LSO's would be stored then tried it in FF and in the Hulu desktop.  Really didn't notice a difference between enabled acceleration and disabled.

Maybe there's a way to adjust the frame rate and deinterlace in flash.  I'm going to go troll for more answers.
I'm looking into this more today... I have 5 boxes running here NVidia and I can't reproduce this problem (they are all working fine).  Seems this has been an issue since Ubuntu 8.10...

Seems that all the fixes they came up (that I've found so far) are centered around what we thought in posts 10 and 13.

What are you using for playback (browser, video player)?  I know I used to have some info here on tuning flash and video playback for gaming in Firefox... I'll try to find that today.

---

### Post by MAFoElffen on 2011-10-01
Curious-- What is the results of:
```
[FONT=monospace]
[/FONT]dmesg | grep drm
LIBGL_DEBUG=verbose glxinfo

```

---

### Post by MAFoElffen on 2011-10-01
Here's the Links I had om that...

How to Optimize Flash in Firefox (Ubuntu):
[http://ubuntuforums.org/showthread.php?t=1533664](http://ubuntuforums.org/showthread.php?t=1533664)

The Gentle Art of Firefox Tuning (And Taming):
[http://linuxmafia.com/~rick/firefox.html]("http://linuxmafia.com/%7Erick/firefox.html")

A lot of this article is still pertinent to version 7:
[http://sunseven.hubpages.com/hub/Optimizing-Firefox-3-Hacks-And-Tweaks](http://sunseven.hubpages.com/hub/Optimizing-Firefox-3-Hacks-And-Tweaks)

And this is more than anyone would ever want to know about Firefox:
[http://www.tweakguides.com/Firefox_1.html](http://www.tweakguides.com/Firefox_1.html)

---

### Post by Stray Wolf on 2011-10-01
> **MAFoElffen said:**
> Curious-- What is the results of:
```
[FONT=monospace]
[/FONT]dmesg | grep drm
LIBGL_DEBUG=verbose glxinfo

```

[FONT=monospace] [/FONT]dmesg | grep drm:  doesn't output anything...just goes to a new prompt.
LIBGL_DEBUG=verbose glxinfo:  Froze the system the first time.  I'm about to try it again though...

I've only watched flash vids with Hulu desktop and FF.  I've only ran Ubuntu on two boxes.  The desktop (hp's m9330f) has had the same flash issues since Karmic.  On it I've ran Karmic, Lucid and  now Natty.  The laptop has only had Lucid on it (Dell's Inspiron 1564) and it's ran flash videos through FF and Hulu perfectly from day one.  Seriously, my laptop streams HD better than my old cable provide.

I can't remember - did I already post my lscpi output?  Would that help?  I could also attach hardinfo's report.  It's very thorough.  But just like everything else when it gets to scanning my display it locks up the system frequently.

Off to do that second command (LIBGL_DEBUG) again.  Hopefully it doesn't lock me up.

---

### Post by Stray Wolf on 2011-10-01
Awesome!  Didn't have to hard-shut-down this time.  Lot's of output.  You're too awesome and I sooo appreciate this!  Here goes:
```
LIBGL_DEBUG=verbose glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_EXT_swap_control, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_framebuffer_sRGB, 
    GLX_NV_present_video, GLX_NV_copy_image, GLX_NV_multisample_coverage, 
    GLX_NV_video_capture, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness
GLX version: 1.4
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GT 520/PCI/SSE2
OpenGL version string: 4.1.0 NVIDIA 270.41.06
OpenGL shading language version string: 4.10 NVIDIA via Cg compiler
OpenGL extensions:
    GL_ARB_blend_func_extended, GL_ARB_color_buffer_float, 
    GL_ARB_compatibility, GL_ARB_copy_buffer, GL_ARB_depth_buffer_float, 
    GL_ARB_depth_clamp, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_draw_buffers_blend, GL_ARB_draw_indirect, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_draw_instanced, 
    GL_ARB_ES2_compatibility, GL_ARB_explicit_attrib_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_framebuffer_object, GL_ARB_framebuffer_sRGB, 
    GL_ARB_geometry_shader4, GL_ARB_get_program_binary, GL_ARB_gpu_shader5, 
    GL_ARB_gpu_shader_fp64, GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_imaging, GL_ARB_instanced_arrays, GL_ARB_map_buffer_range, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_occlusion_query2, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_provoking_vertex, 
    GL_ARB_robustness, GL_ARB_sample_shading, GL_ARB_sampler_objects, 
    GL_ARB_seamless_cube_map, GL_ARB_separate_shader_objects, 
    GL_ARB_shader_bit_encoding, GL_ARB_shader_objects, 
    GL_ARB_shader_precision, GL_ARB_shader_subroutine, 
    GL_ARB_shading_language_100, GL_ARB_shading_language_include, 
    GL_ARB_shadow, GL_ARB_sync, GL_ARB_tessellation_shader, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_buffer_object, 
    GL_ARB_texture_buffer_object_rgb32, GL_ARB_texture_compression, 
    GL_ARB_texture_compression_bptc, GL_ARB_texture_compression_rgtc, 
    GL_ARB_texture_cube_map, GL_ARB_texture_cube_map_array, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_gather, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_multisample, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_query_lod, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, 
    GL_ARB_texture_swizzle, GL_ARB_timer_query, GL_ARB_transform_feedback2, 
    GL_ARB_transform_feedback3, GL_ARB_transpose_matrix, 
    GL_ARB_uniform_buffer_object, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_attrib_64bit, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_ARB_viewport_array, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_bindable_uniform, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXTX_framebuffer_mixed_formats, GL_EXT_framebuffer_object, 
    GL_EXT_framebuffer_sRGB, GL_EXT_geometry_shader4, 
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_provoking_vertex, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_shader_objects, 
    GL_EXT_separate_specular_color, GL_EXT_shader_image_load_store, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_texture3D, GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_format_BGRA8888, 
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_shared_exponent, GL_EXT_texture_sRGB, 
    GL_EXT_texture_swizzle, GL_EXT_texture_type_2_10_10_10_REV, 
    GL_EXT_timer_query, GL_EXT_transform_feedback2, GL_EXT_vertex_array, 
    GL_EXT_vertex_array_bgra, GL_EXT_vertex_attrib_64bit, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_KTX_buffer_region, GL_NV_alpha_test, GL_NV_blend_minmax, 
    GL_NV_blend_square, GL_NV_complex_primitives, GL_NV_conditional_render, 
    GL_NV_copy_depth_to_color, GL_NV_copy_image, GL_NV_depth_buffer_float, 
    GL_NV_depth_clamp, GL_NV_explicit_multisample, 
    GL_NV_fbo_color_attachments, GL_NV_fence, GL_NV_float_buffer, 
    GL_NV_fog_distance, GL_NV_fragdepth, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, 
    GL_NV_framebuffer_multisample_coverage, GL_NV_geometry_shader4, 
    GL_NV_gpu_program4, GL_NV_gpu_program4_1, GL_NV_gpu_program5, 
    GL_NV_gpu_program_fp64, GL_NV_gpu_shader5, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_coverage, 
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query, 
    GL_NV_packed_depth_stencil, GL_NV_parameter_buffer_object, 
    GL_NV_parameter_buffer_object2, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_shader_buffer_load, 
    GL_NV_texgen_reflection, GL_NV_texture_barrier, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_lod_clamp, 
    GL_NV_texture_multisample, GL_NV_texture_rectangle, GL_NV_texture_shader, 
    GL_NV_texture_shader2, GL_NV_texture_shader3, GL_NV_transform_feedback, 
    GL_NV_transform_feedback2, GL_NV_vdpau_interop, GL_NV_vertex_array_range, 
    GL_NV_vertex_array_range2, GL_NV_vertex_attrib_integer_64bit, 
    GL_NV_vertex_buffer_unified_memory, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, GL_OES_depth24, 
    GL_OES_depth32, GL_OES_depth_texture, GL_OES_element_index_uint, 
    GL_OES_fbo_render_mipmap, GL_OES_get_program_binary, GL_OES_mapbuffer, 
    GL_OES_packed_depth_stencil, GL_OES_rgb8_rgba8, 
    GL_OES_standard_derivatives, GL_OES_texture_3D, GL_OES_texture_float, 
    GL_OES_texture_float_linear, GL_OES_texture_half_float, 
    GL_OES_texture_half_float_linear, GL_OES_texture_npot, 
    GL_OES_vertex_array_object, GL_OES_vertex_half_float, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SUN_slice_accum

84 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x024 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x025 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x026 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x027 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x028 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x029 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x02a 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x02b 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x02c 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x02d 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x02e 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x02f 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x030 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x031 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x032 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x033 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x034 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x035 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x036 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x037 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x038 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x039 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x03a 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x03b 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x03c 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x03d 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x03e 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x03f 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x040 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x041 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x042 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x043 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x044 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x045 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x046 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x047 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x048 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x049 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x04a 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x04b 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x04c 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x04d 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x04e 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x04f 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x050 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x051 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x052 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x053 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x054 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x055 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x056 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x057 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x058 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x059 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x023 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x05a 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x05b 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x05c 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x05d 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x05e 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x05f 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x060 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x061 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x062 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x063 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x064 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x065 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x066 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x067 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x068 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x069 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x06a 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x06b 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x06c 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x06d 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x06e 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x06f 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x070 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x071 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x072 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x073 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x074 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon

167 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x075 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x076 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x077 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x078 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x079 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x07a 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x07b 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x07c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x07d 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x07e 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x07f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x080 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x081 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x082 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x083 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x084 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x085 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x086 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x087 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x088 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x089 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x08a 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x08b 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x08c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x08d 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x08e 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x08f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x090 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x091 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x092 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x093 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x094 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x095 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x096 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x097 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x098 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x099 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x09a 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x09b 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x09c 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x09d 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x09e 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x09f 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a0 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a1 24 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0a2 24 dc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0a3 24 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0a4 24 dc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0a5 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a6 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a7 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a8 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0a9 24 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0aa 24 dc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0ab 24 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0ac 24 dc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0ad 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x0ae 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x0af 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  0 0 None
0x0b0 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  0 0 None
0x0b1 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x0b2 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x0b3 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  0 0 None
0x0b4 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  0 0 None
0x0b5 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x0b6 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x0b7 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4  0  0 16 16 16 16  0 0 None
0x0b8 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4  0  0 16 16 16 16  0 0 None
0x0b9 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0ba 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0bb 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0bc 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0bd 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0be 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  2 1 Ncon
0x0bf 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0c0 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  0 16 16 16 16  4 1 Ncon
0x0c1 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0c2 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0c3 32 tc  0  32  0 r  y .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0c4 32 tc  0  32  0 r  y .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0c5 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0c6 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  2 1 Ncon
0x0c7 32 tc  0  32  0 r  . .   8  8  8  0 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0c8 32 tc  0  32  0 r  . .   8  8  8  8 .  s  4 24  8 16 16 16 16  4 1 Ncon
0x0c9  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 16  0 16 16 16 16  0 0 None
0x0ca  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 16  0 16 16 16 16  0 0 None
0x0cb  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0cc  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0cd  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0ce  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0cf  0 sg  0  16  0 r  y .   5  6  5  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0d0  0 sg  0  16  0 r  . .   5  6  5  0 .  .  4  0  0 16 16 16 16  0 0 None
0x0d1  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 16  0 16 16 16 16  0 0 None
0x0d2  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 24  0 16 16 16 16  0 0 None
0x0d3  0 sg  0   0  0 r  . .   0  0  0  0 .  .  4 24  8 16 16 16 16  0 0 None
0x0d4  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d5  0 sg  0  32  0    . .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d6  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d7  0 sg  0  32  0    y .  16 16  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d8  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0d9  0 sg  0  32  0    . .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0da  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0db  0 sg  0  32  0    y .  32  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x0dc  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x0dd  0 sg  0  64  0    . .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x0de  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x0df  0 sg  0  64  0    y .  16 16 16 16 f  .  4  0  0 16 16 16 16  0 0 None
0x0e0  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x0e1  0 sg  0 128  0    . .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x0e2  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x0e3  0 sg  0 128  0    y .  32 32 32 32 f  .  4  0  0 16 16 16 16  0 0 None
0x0e4  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0e5  0 sg  0  32  0    . .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0e6  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0e7  0 sg  0  32  0    y .  16 16  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0e8  0 sg  0  32  0 r  . .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0e9  0 sg  0  32  0    . .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0ea  0 sg  0  32  0 r  y .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0eb  0 sg  0  32  0    y .  16 16  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0ec  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0ed  0 sg  0  32  0    . .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0ee  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0ef  0 sg  0  32  0    y .  32  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x0f0  0 sg  0  32  0 r  . .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0f1  0 sg  0  32  0    . .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0f2  0 sg  0  32  0 r  y .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0f3  0 sg  0  32  0    y .  32  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x0f4  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x0f5  0 sg  0  64  0    . .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x0f6  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x0f7  0 sg  0  64  0    y .  16 16 16 16 f  .  4 24  0 16 16 16 16  0 0 None
0x0f8  0 sg  0  64  0 r  . .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x0f9  0 sg  0  64  0    . .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x0fa  0 sg  0  64  0 r  y .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x0fb  0 sg  0  64  0    y .  16 16 16 16 f  .  4 24  8 16 16 16 16  0 0 None
0x0fc  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x0fd  0 sg  0 128  0    . .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x0fe  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x0ff  0 sg  0 128  0    y .  32 32 32 32 f  .  4 24  0 16 16 16 16  0 0 None
0x100  0 sg  0 128  0 r  . .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x101  0 sg  0 128  0    . .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x102  0 sg  0 128  0 r  y .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x103  0 sg  0 128  0    y .  32 32 32 32 f  .  4 24  8 16 16 16 16  0 0 None
0x104  0 sg  0  16  0 r  . .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x105  0 sg  0  16  0    . .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x106  0 sg  0  16  0 r  y .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x107  0 sg  0  16  0    y .  16  0  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x108  0 sg  0  64  0 r  . .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x109  0 sg  0  64  0    . .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x10a  0 sg  0  64  0 r  y .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x10b  0 sg  0  64  0    y .  32 32  0  0 f  .  4  0  0 16 16 16 16  0 0 None
0x10c  0 sg  0  16  0 r  . .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x10d  0 sg  0  16  0    . .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x10e  0 sg  0  16  0 r  y .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x10f  0 sg  0  16  0    y .  16  0  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x110  0 sg  0  16  0 r  . .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x111  0 sg  0  16  0    . .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x112  0 sg  0  16  0 r  y .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x113  0 sg  0  16  0    y .  16  0  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x114  0 sg  0  64  0 r  . .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x115  0 sg  0  64  0    . .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x116  0 sg  0  64  0 r  y .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x117  0 sg  0  64  0    y .  32 32  0  0 f  .  4 24  0 16 16 16 16  0 0 None
0x118  0 sg  0  64  0 r  . .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x119  0 sg  0  64  0    . .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x11a  0 sg  0  64  0 r  y .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None
0x11b  0 sg  0  64  0    y .  32 32  0  0 f  .  4 24  8 16 16 16 16  0 0 None

```

---

### Post by MAFoElffen on 2011-10-01
> **Stray Wolf said:**
> dmesg | grep drm:  doesn't output anything...just goes to a new prompt.

The put put from your "LIBGL_DEBUG=verbose glxinfo" looked great... No out put from the "dmesg | grep drm"... 
> If you get DRM version output but not your card-specific DRM version  output, you may not have a supported card, [COLOR=Red]or it may not be getting  probed due to the PCI ID being missing from the driver[/COLOR].So... sounds like Direct Rendering, DRI and DRM are configured, loaded and working, BUT not finding your card on the PCI bus(?)  

Remember post             #[**9**]("http://ubuntuforums.org/showpost.php?p=11293465&postcount=9")? (<--Link to) Where I asked you to add the PCI address of your video card to your xorg.conf file?  Can you confirm that that change is there?

---

### Post by Stray Wolf on 2011-10-02
Sorry it always takes so long for me to respond.  The system didn't boot up two-thirds (literally) of the time until yesterday.  Then it just didn't boot.  Needless to say I reinstalled and paid close attention this time.  I didn't check to do updates during the install this time, nor did I check to install third-party software during the natty install.  I watched the "details" of the natty install and noticed my "Bios mask(?)" was wrong but that it was corrected successfully.  Also said mod nvidia-current couldn't be found, then added automatically.  Anyway, here's xorg.conf. now:
Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection

I found this: [http://www.webgapps.org/add-ons/flashvideoreplacer](http://www.webgapps.org/add-ons/flashvideoreplacer) and so far only tested it on youtube this morning with stellar results.  I'm about to test it on Hulu.com.  I wonder if I can configure it to be used by the Hulu desktop?

After my reinstall natty started with the classic desktop and prompted me that I need additional drivers.  The options were for an experimental driver or the recommended current.  This time I installed the drivers and restarted the system before I did a software update.  I also made sure to set up audio properly before attempting to use any apps that would require sound.

Off to do more testing.  So far I'm impressed with the progress this time around.

So, I haven't got flashvideoreplace to work with hulu yet...desktop or web.  Though the sites that work with flashvideoreplace are as good a quality as one could get.  I'm using totem as the plugin/mimetype.  It's beautiful, smooth and no deinterlace issue either!  I'm off to the flashvideoreplace homepage to see what they can tell me.

---

### Post by Stray Wolf on 2011-10-02
```
[display]
fullscreen = FALSE
width = 1280
height = 720
pos_x = 212
pos_y = 179

[remote]
lirc_device = /dev/lircd
lirc_remote_identifier = mceusb
lirc_release_suffix = _UP
lirc_repeat_threshold = 10
button_name_up = Up
button_name_down = Down
button_name_left = Left
button_name_right = Right
button_name_select = OK
button_name_menu = Home

[flash]
flash_location = /var/lib/flashplugin-installer/npwrapper.libflashplayer.so

[screensaver]
suspend_script = (null)
resume_script = (null)

[version]
latest = (null)
eula_version = 1
```

I posted this to see if it would be possible to make changes here and get it to do a flashvideoreplace or something.  The cool thing I noticed about using totem through flashvideoreplace is how consistently it suppresses the screen saver during playback.

---

### Post by MAFoElffen on 2011-10-02
Good on that.  I now see 'something' glaring out at me... You are now using 'Default Device" instead of any NVidia drivers???
> **Stray Wolf said:**
> 
```
Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection
```
How is that working out for you?

---

### Post by Stray Wolf on 2011-10-03
> **MAFoElffen said:**
> Good on that.  I now see 'something' glaring out at me... You are now using 'Default Device" instead of any NVidia drivers???

How is that working out for you?

I really didn't notice a difference.  I still set overscan in Nvidia-settings and the adjustments took.  But right after I posted that xorg.file I made the changes as suggested in post #9 just out of curiosity.  I have noticed successfully booting more than once in a row.  Actually...after the change to the xorg.file the system only froze once on boot up.  It would always freeze after the log-in screen.

So, was the Nvidia driver the default device?  Maybe on default it was trying to use the drivers before they were loaded?  Anyhow, I saved the "default" xorg.conf file in "My Documents" as xorg.conf.old so if you want I can go back and forth and really try to pay attention to the differences.

---

### Post by MAFoElffen on 2011-10-03
> **Stray Wolf said:**
> I really didn't notice a difference.  I still set overscan in Nvidia-settings and the adjustments took.  But right after I posted that xorg.file I made the changes as suggested in post #9 just out of curiosity.  I have noticed successfully booting more than once in a row.  Actually...after the change to the xorg.file the system only froze once on boot up.  It would always freeze after the log-in screen.

So, was the Nvidia driver the default device?  Maybe on default it was trying to use the drivers before they were loaded?  Anyhow, I saved the "default" xorg.conf file in "My Documents" as xorg.conf.old so if you want I can go back and forth and really try to pay attention to the differences.
LOL... You got me on that.  

Here's yours:
```
[FONT=monospace]
[/FONT]Section "Device"
   Identifier    "Default Device"
   Option    "NoLogo"    "True" 
EndSection

```
"Identifier" in this section assigns this particular device section to a variable named "Default Device"... which is a little didffrent, as NVidia usually uses names like "Device0" or "Device1"... The idientifier (name) "can be" anything, as long as that name is referenced consistently through the other sections (so things match up).

Notice that your Device section (compared to mine below) has no "Driver" line to tell xorg which driver to use.  

Here is one of mine:
```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 Ultra"
    BusID          "PCI:3:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 Ultra"
    BusID          "PCI:3:0:1"
    Screen          1
EndSection

```
I posted the section from this box so you could see mulitple (SLI) cards and basically see what is consistent and what changes in that section.  The device sections say- use this driver for this card (at this BusID)... Other sections call this section to match in up with screen, monitor and the overall server layout.

That a good general explanation of that, that you can understand?

---

### Post by Stray Wolf on 2011-10-03
> **MAFoElffen said:**
> LOL... You got me on that.  

Here is one of mine:
```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 Ultra"
    BusID          "PCI:3:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 Ultra"
    BusID          "PCI:3:0:1"
    Screen          1
EndSection

```I posted the section from this box so you could see mulitple (SLI) cards and basically see what is consistent and what changes in that section.  The device sections say- use this driver for this card (at this BusID)... Other sections call this section to match in up with screen, monitor and the overall server layout.

That a good general explanation of that, that you can understand?

I'd say you did good.  Just curious - when the xorg file says "default device-default drivers"  where is that pointing to?  Somewhere has to say something like "default device = XXXX or default drivers = XXXX right?   Like I said, if you're really curious I can bounce back and forth between the xorg.conf and xorg.conf.old.

Just curious - what does: Option    "NoLogo"  "True" mean?

---

### Post by MAFoElffen on 2011-10-03
> **Stray Wolf said:**
> I'd say you did good.  Just curious - when the xorg file says "default device-default drivers"  where is that pointing to?  Somewhere has to say something like "default device = XXXX or default drivers = XXXX right?   Like I said, if you're really curious I can bounce back and forth between the xorg.conf and xorg.conf.old.

Just curious - what does: Option    "NoLogo"  "True" mean?
Beep!  You misunderstood... You have no driver line in your device section...

Just from memory, yours is like this:
```
[FONT=monospace]
[/FONT]Section "Device"    
  Identifier    "Default Device"     # <-- "Default Device" is now the name that call this Device section
  # notice there is no line here saying:  Device "nvida". That would point to the nvidia driver...
  # Notice there is no BusID line to point the card to a specifics card in tthe PCI bus...
  Option    "NoLogo"    "True"    # <-- This line would not be needed if your not using an NVidia card...
EndSection

```[FONT=monospace]
That would have your's evolve into:
[/FONT]```
Section "Default"     
  Identifier     "Default Device"     
  Driver         "nvidia"     
  BusID          "PCI:2:0:0"     
EndSection 

```If you wanted to change the name "Default Device" to something else, you would have to do a search and replace to change all refrences of it at once, so there would not be any conflicts or dead ends.  It's really fine leaving it as that, even if it is a little odd.

---

### Post by Stray Wolf on 2011-10-03
Well, currently I have the "Nvidia" xorg.conf loaded but when I was using the "default" xorg.con I was still able to adjust the overscan in the NVidia-settings gui.  Does that make sense?  Xorg said I wasn't using nVidia drivers, but changing nVidia settings worked and still work just the same with xorg.conf set like you suggested in post #9.  Even if it doesn't make sense that's exactly whats going on.  Weird huh?

---

### Post by MAFoElffen on 2011-10-03
> **Stray Wolf said:**
> Well, currently I have the "Nvidia" xorg.conf loaded but when I was using the "default" xorg.con I was still able to adjust the overscan in the NVidia-settings gui.  Does that make sense?  Xorg said I wasn't using nVidia drivers, but changing nVidia settings worked and still work just the same with xorg.conf set like you suggested in post #9.  Even if it doesn't make sense that's exactly whats going on. [COLOR=DarkRed] Weird huh?[/COLOR]
Logic defying kind of weird!

---

### Post by Stray Wolf on 2011-10-04
Remember in post six (before configuring xorg.conf) you had me run compiz check and it's output was:
Distribution:  Ubuntu 11.04
Desktop Environment:  Gnome
Graphics Chip: nVidia Corporation Device 1040 (rev a1)
Driver in use: nVidia
Rendeing Method: nVidia
Checking if its possible to run compiz...
Checking for texture_from_pixmap...

Then the system froze up.  Now that I have the xorg file scripted for the nVidia drivers, maybe I should run it again to see if it still freezes up.

Do you think I could change that Hulu desktop file (post [http://ubuntuforums.org/showpost.php?p=11304933&postcount=25](http://ubuntuforums.org/showpost.php?p=11304933&postcount=25)) to use totem like the flashvideoreplacer does in FF?

---

### Post by MAFoElffen on 2011-10-04
> **Stray Wolf said:**
> Remember in post six (before configuring xorg.conf) you had me run compiz check and it's output was:
Distribution:  Ubuntu 11.04
Desktop Environment:  Gnome
Graphics Chip: nVidia Corporation Device 1040 (rev a1)
Driver in use: nVidia
Rendeing Method: nVidia
Checking if its possible to run compiz...
Checking for texture_from_pixmap...

Then the system froze up.  Now that I have the xorg file scripted for the nVidia drivers, maybe I should run it again to see if it still freezes up.

Do you think I could change that Hulu desktop file (post [http://ubuntuforums.org/showpost.php?p=11304933&postcount=25](http://ubuntuforums.org/showpost.php?p=11304933&postcount=25)) to use totem like the flashvideoreplacer does in FF?
Yes on running again...

On tuning the Hula config file... Can not find any documentation on that file at all... nor much on the hula desktop (beside on the install.) Nothing on changing the video player inside it.

I did find some breadcrumbs in their support section:
> Q : I've upgraded to Flash Player 10.0.32 and I'm having problems viewing video in fullscreen mode. How can I fix this?
     There is a known issue with Adobe's latest Flash Player's hardware  acceleration feature and certain graphics cards.  You can turn off the  hardware acceleration feature by the following steps:     
[LIST]
[*]Go to Hulu.com and watch a video.
[*]Right-click on the player and select "Settings".
[*]Click to the first tab in the settings window and uncheck the "Enable hardware acceleration" box.
[*]Click "Close" and try watching any Hulu video in full screen mode again.
[/LIST]
On FlashVideoReplacer... Says install from Firefox Extensions and the version installs easier from there.  Then you can get tuning and tweaking tips from their site"
[http://www.webgapps.org/tutorials/firefox/optimization/preferences-tweaks](http://www.webgapps.org/tutorials/firefox/optimization/preferences-tweaks)

Although it doesn't mention anything about hula or hula desktop...

---

