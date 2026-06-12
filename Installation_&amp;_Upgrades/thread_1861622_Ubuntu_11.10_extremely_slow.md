---
title: "Ubuntu 11.10 extremely slow"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by linux_dream on 2011-10-15
Hi guys!
I upgrated Ubuntu from 11.04 to 11.10.  However the new version is immensely slow compared to the previous version.  Even by pressing the left button of mouse and drag over an empty space of the desktop I can notice that the "selection area" moves quite slowly.
I tried to move some windows, like firefox or any other, and this is really, really slow.  
Basically it moves like 3 to 5 s after I moved with my mouse.  
I thought that maybe it has to do with some compiz configuration so I played a bit there... but my interface "crashed" 2 times and I had to hard reboot (push button) since all the unity and my top bar disappeared.
What can I do to make it fluid like the previous version?  I used to run totally normally under Unity 3d of Ubuntu 11.04.

---

### Post by lsward on 2011-10-15
I'm find 11.10 to be just as fast if not faster then 11.04 and I run it on a Sony Vaio VGN-FE770G with 1 GB of RAM.  What kind of system are you running 11.10 on?

---

### Post by linux_dream on 2011-10-15
> **lsward said:**
> I'm find 11.10 to be just as fast if not faster then 11.04 and I run it on a Sony Vaio VGN-FE770G with 1 GB of RAM.  What kind of system are you running 11.10 on?
On a dual core E6300, 3 Gb of RAM.

---

### Post by lsward on 2011-10-15
Seems a lot of newer machines are running slow on 11.10.  Or at least that is the impression I get from the forum.  I wish I had some sort of suggestion, but I'm at a loss.  Hopefully someone else can take a swing at it.

---

### Post by linux_dream on 2011-10-15
> **lsward said:**
> Seems a lot of newer machines are running slow on 11.10.  Or at least that is the impression I get from the forum.  I wish I had some sort of suggestion, but I'm at a loss.  Hopefully someone else can take a swing at it.
Well thank you!  I'll be waiting for any other help then.
It's almost unusable so I'll stick with Windows XP (painfully) until the problem gets solved.

---

### Post by lsward on 2011-10-15
Sorry, it's all new to me as well.  Best of luck!

---

### Post by causeitsme on 2011-10-16
I'm experiencing a lot of lag in certain instances with 11.10. I'm running Xubuntu.

I notice it most in Mahjongg, When I click on a tile, there is about a 1/4 second delay before the tile highlights and disappears.

Also, when I click a menu; i.e., Applications, There is up to a second delay before the menu choices appear.

---

### Post by MonocleMike2 on 2011-10-16
I have just updated from 10.04 to 11.10 and it is now so slow as to be unusable.  The disk activity light is almost permanently on. It is an old Toshiba Satellite Pro.  To get 11.10 to work I had to remove .config/monitors.xml as recommended in another thread and the old fix of removing 2 files agere_.._bin from /lib/firmware has not got my wireless card working.  So now I can't connect to my WiFi and even if I could it is too slow to be usable.  It was working so well in 10.04!
Any suggestions anyone?

2 hrs later:wireless card working.
I am making progress.  I changed shell to Gnome Classic (No effects) from this link 
[http://blog.sudobits.com/2011/09/08/10-things-to-do-after-installing-ubuntu-11-10/](http://blog.sudobits.com/2011/09/08/10-things-to-do-after-installing-ubuntu-11-10/) 
and
[http://www.omgubuntu.co.uk/2011/10/gnome-shell-ubuntu-11-10-guide/](http://www.omgubuntu.co.uk/2011/10/gnome-shell-ubuntu-11-10-guide/)
and used the network app to get the wireless working.

Now I will find out how to make it default to that shell as it is definitely quicker.  Next I want to learn how to uninstall and remove from the hard disk all the shell stuff I don't need.

---

### Post by n0zqh1 on 2011-10-16
I notice the same problems here. I updated to v11.10.  Wondering if I should just have done a fresh install?

---

### Post by ralph_pt on 2011-10-16
> **linux_dream said:**
> Hi guys!
I've upgraded Ubuntu from 11.04 to 11.10.  However the new version is immensely slow compared to the previous version.  Even by pressing the left button of mouse and drag over an empty space of the desktop I can notice that the "selection area" moves quite slowly.
I tried to move some windows, like Firefox or any other, and this is really, really slow.  
Basically it moves like 3 to 5 s after I moved with my mouse.  
I thought that maybe it has to do with some Compiz configuration so I played a bit there... but my interface "crashed" 2 times and I had to hard reboot (push button) since all the unity and my top bar disappeared.
What can I do to make it fluid like the previous version?  I used to run totally normally under Unity 3d of Ubuntu 11.04.


  I've tested it in a pretty nice machine (4gb ram, 1 gb card drive) and its a bit slow due to all the new effects, although you can always change the graphical environment you want, in the log in screen, click in the gear image, and select the old graphical environment, you can choose normal Ubuntu there instead of the new one.

---

### Post by kaldor on 2011-10-16
For those who are having performance problems, post the following info...
[LIST]
[*]Which Graphics Card do you have? Exact name and such.

[*]Which driver? 

[*]Install GNOME Shell (*gnome-shell* package) and try this. Any difference?

[*]Try Unity 2D. Issue resolved or not?
[/LIST]

To change to GNOME Shell or Unity 2d, simple log out and select it in the gear icon by your name. Log in and you'll be using the option you selected. GNOME Shell is listed as "GNOME" and Unity 2d is listed as "Ubuntu 2d".

Using the NVIDIA proprietary driver on a GeForce 8400m is causing performance issues on Shell and Unity. No problems at all with Unity 2d.

---

### Post by MonocleMike2 on 2011-10-16
Gnome is better and Gnome Classic even more so.  Unity 2D takes for ever to load and is slow but does work.
Here is the info you want:#lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go] (rev a3)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
02:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)

lsmod
Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
binfmt_misc            17292  1 
orinoco_cs             12898  1 
orinoco                70112  1 orinoco_cs
cfg80211              172392  1 orinoco
ppdev                  12849  0 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
nouveau               663211  2 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39822  1 orinoco_cs
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73673  0 
serio_raw              12990  0 
ttm                    65224  1 nouveau
drm_kms_helper         32889  1 nouveau
irda                  185428  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
drm                   192226  4 nouveau,ttm,drm_kms_helper
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
crc_ccitt              12595  1 irda
pcmcia_core            21511  4 orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc
i2c_algo_bit           13199  1 nouveau
parport_pc             32114  1 
mxm_wmi                12859  1 nouveau
wmi                    18744  1 mxm_wmi
video                  18908  1 nouveau
toshiba_acpi           13815  0 
sparse_keymap          13658  1 toshiba_acpi
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
e100                   36289  0

---

### Post by TM720 on 2011-10-16
I'm using a NVIDIA 8400M GS with 11.10 and have had most of the problems talked about so far.

Unity is so slow it is almost unusable after 1 or 2 hours of work. It takes at least 5 minutes to even shut the system down from the UI.

GNOME classic works pretty well in comparison, but still gets laggy under a even slighly heavier workload. I like Unity but will stick with GNOME until I can find a solution.

That said, I'm still not so desperate as to devolve back to Windows. At this point it's like giving up the use of apposeable thumbs.

---

### Post by kaldor on 2011-10-16
> **TM720 said:**
> I'm using a NVIDIA 8400M GS with 11.10 and have had most of the problems talked about so far.

Unity is so slow it is almost unusable after 1 or 2 hours of work. It takes at least 5 minutes to even shut the system down from the UI.

GNOME classic works pretty well in comparison, but still gets laggy under a even slighly heavier workload. I like Unity but will stick with GNOME until I can find a solution.

That said, I'm still not so desperate as to devolve back to Windows. At this point it's like giving up the use of apposeable thumbs.

Exact same GPU as me. Check [_here_]("http://ubuntuforums.org/showpost.php?p=11352799&postcount=7").

---

### Post by Juvencio on 2011-10-16
Ubuntu will automatically detect and tell you there any additional hardware drivers are necessary or not, you just need to select the appropriate driver and click on Activate.
For any reason if your graphics card doesn’t get detected automatically then don’t be panic.

Go to dash home type
```
Additional Drivers
```

OR Go to
```
System Settings -> Additional Drivers
```

change your video drivers.

I had to reinstall my drivers after upgrade from 11.04
as it was also so slow.

---

### Post by arashiko28 on 2011-10-16
There are some cases where there is huge RAM consumption. Check at terminal "top" and system monitor and see if you can find the culprit.

---

### Post by MonocleMike2 on 2011-10-16
Oh dear, Juvencio, I updated my nvidia driver to the one it recommended and it has totally screwed my display!!  It cannot get to the login screen; it just flashes and fades and gets nowhere.  I've booted into recovery mode but how do I change back to the original driver?
If I 
sudo rmmod nvidia
will it load some sort of default driver?

---

### Post by james@finnall.net on 2011-10-16
I tried the Unity 2D and Gnome shell, both of them performed as Unity 3D on my system.  The Gnome shell would be starting all over again for me, so not really an option.  Unity 2D ignored all the Compiz settings I have configured so far.  But since no noticeable performance increase I could not see really working with either.  I laos have a KDE option available, and might try it to see what I get.  But not interested in it since they went to KDE4.  That is why I left Slackware after so many years and switched to Ubuntu.:(

In my Additional Drivers section there are 4 drivers listed and I tried 3 of them without any change in performance.  Currently running the original recommended driver.  No version number listed.  One of the others I tried listed version 173.

I tried to revert back to the 2.6 kernel but none them will boot properly.  Grub offers many but they are not functional.  So I am stuck with version 3.0 kernel.

My video is based on nVidia GeForce 8600GT card.

I suspected the graphics as well.  I upgraded another machine on Friday and did not notice any performance issues like I have here.  The other machine uses the integrated Intel video on the motherboard.

Maybe a resolution will be discovered soon.   What I have seen so far does work for me but slower performance.  Once in a while I will get a large orange rectangle overlay that covers half of my screen.  But I switch out to expo mode and wait a second it clears up and I can resume my work.

James

---

### Post by linux_dream on 2011-10-16
> **kaldor said:**
> For those who are having performance problems, post the following info...
[LIST]
[*]Which Graphics Card do you have? Exact name and such.
[*]Which driver?
[*]Install GNOME Shell (*gnome-shell* package) and try this. Any difference?
[*]Try Unity 2D. Issue resolved or not?
[/LIST]

To change to GNOME Shell or Unity 2d, simple log out and select it in the gear icon by your name. Log in and you'll be using the option you selected. GNOME Shell is listed as "GNOME" and Unity 2d is listed as "Ubuntu 2d".

Using the NVIDIA proprietary driver on a GeForce 8400m is causing performance issues on Shell and Unity. No problems at all with Unity 2d.

How do you check out your drivers in Ubuntu 11.10?  When I go into "search", the top icon in Unity and type in "driver", I get nothing.  In Ubuntu 11.04 I could see them.
Unity 3D was working just fine under Ubuntu 11.04.  I had, somehow, to switch to older NVIDIA drivers.  The new ones were totally incompatible with Unity.  I have an NVIDIA 7300 GS.  

> **Juvencio said:**
> Ubuntu will automatically detect and tell you there any additional hardware drivers are necessary or not, you just need to select the appropriate driver and click on Activate.
For any reason if your graphics card doesn’t get detected automatically then don’t be panic.

Go to dash home type
```
Additional Drivers
```OR Go to
```
System Settings -> Additional Drivers
```change your video drivers.

I had to reinstall my drivers after upgrade from 11.04
as it was also so slow.
Err... there's no "system settings" as far as I know in Ubuntu 11.10.  Or if there is such a setting, how do you reach it?
> **arashiko28 said:**
> There are some cases where there is huge RAM consumption. Check at terminal "top" and system monitor and see if you can find the culprit.
Not in my case.  3 GB of RAM, very few use of it.  Less than 1 GB for sure at any moment.

I repeat to all, with my cpu Unity and Ubuntu 11.04 was working totally normally (even Unity 3D), no lag nor anything wrong.  The update to 11.10 made it all slow.

---

### Post by MonocleMike2 on 2011-10-16
linux-dream
I've got System Settings on my application launchpad on the side of the screen.
I think I wish I hadn't.  See my reply to Juvencio above!!

---

### Post by james@finnall.net on 2011-10-16
@Linux_Dream
Click the gear in the upper right corner, like shutting down, System Settings is the top menu option.  But it has changed considerably since 11.04.  I liked the one screen and all the options it had in 11.04 better.
James

---

### Post by linux_dream on 2011-10-16
> **MonocleMike2 said:**
> linux-dream
I've got System Settings on my application launchpad on the side of the screen.
I think I wish I hadn't.  See my reply to Juvencio above!!
Hmm I see.  I think you should remove a file in xconfig or something like that.  Yeah it will load hopefully a default driver that works.

---

### Post by Juvencio on 2011-10-16
Install ATI drivers
[http://mrrichard.hubpages.com/hub/2-Ways-to-Install-FGLRX-in-Ubuntu-1110-Oneric]("http://mrrichard.hubpages.com/hub/2-Ways-to-Install-FGLRX-in-Ubuntu-1110-Oneric")

Install Nvidia drivers
[http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html]("http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html")

Also I found on my side is that my CPU is almost maxed out 
**[COLOR="DarkRed"]when I cheeked it was the (CLI) running at 98%[/COLOR]**
All I did is kill proses

see if this is the same on your system

remember we are all trying to help!

---

### Post by MonocleMike2 on 2011-10-16
I tried
sudo rmmod nvidia
and rebooted and it makes no difference!
Thank heavens it is a spare/test machine.
Can anyone help me get it back?

---

### Post by MonocleMike2 on 2011-10-16
@Juvencio
I know you are only trying to help and I am very grateful.
Thanks for the links but how do I get to them from the text terminal you get in recovery mode?
I think I need to load an existing driver for the video card but I don't know how to from the command line.

---

### Post by alexpotter on 2011-10-16
Ubuntu 11.10 was quite slow on my HP Compaq nc6220 machine, about 6-7 years old. It runs with 1.5GB of RAM and an Intel Pentium M 1.73GHz processor - and the Intel 915GM integrated graphics (128MB).

I think the problem is that Ubuntu depends more on Compiz, therefore graphics acceleration and OpenGL is more stressing, so I installed CompizConfig Settings Manager from the Software Centre and disabled a few options

I tweaked the following

1. Under 'Composite' disable 'Detect Refresh Rate'
2. Under 'OpenGL' disable Sync to VBlank and change Texture Filter to 'Fast'

It immediately took effect on my machine. It was the main thing stopping me to switch to the more responsive GNOME 3 shell.

GNOME 3 is quite fast though, and you may want to take a look. To install it, go to Terminal and type

```
sudo apt-get install gnome-shell
```

Or the GNOME Classic version:-

```
sudo apt-get install gnome-session-fallback
```

Hope I could of helped. :popcorn:

---

### Post by MonocleMike2 on 2011-10-16
@alexpotter
Any idea what "apt-get install" I could use to get a video driver?

---

### Post by Juvencio on 2011-10-16
Hey MonocleMike2

if you boot up on your pc hold the
```
ctrl + F2 keys
SORRY ITS ctrl + 2
and hold it in
```

this will allow you to select recovery mode

once their you can select the terminal (root) option 

I'm not to sure what 11.10 recovery GUI looks like

How to uninstall nvidia driver in Terminal
[http://ubuntuforums.org/showthread.php?t=1432857]("http://ubuntuforums.org/showthread.php?t=1432857")

How to Install nvidia driver in Terminal
[http://ubuntuforums.org/showthread.php?t=770190]("http://ubuntuforums.org/showthread.php?t=770190")

---

### Post by MonocleMike2 on 2011-10-16
@Juvencio
Thanks.
I'll try it now.

---

### Post by 23dornot23d on 2011-10-16
" Juvencio the second link you have  given for Nvidia is from 2008

To get back your video drivers ...... and settings ..... from a terminal if you want the
ones back from the repos ... ?

sudo apt-get update

sudo apt-get install nvidia-settings
sudo apt-get install nvidia-current

---

### Post by MonocleMike2 on 2011-10-16
The first bit worked - it removed the driver BUT...!
The attempt to re-install failed nvidia-glx-new it cannot locate.
nvidia-glx it knows a little about but says the package is missing and has no installation candidate.

I think I am getting very close to a re-install from scratch and if so I'll leave it until the morning.  T'was an early start to watch the Formula 1 and then the rugby :-)

---

### Post by Juvencio on 2011-10-16
**23dornot23d** you are right thanx

> **23dornot23d said:**
> " Juvencio the second link you have  given for Nvidia is from 2008

To get back your video drivers ...... and settings ..... from a terminal if you want the
ones back from the repos ... ?

sudo apt-get update

sudo apt-get install nvidia-settings
sudo apt-get install nvidia-current

Try this MonocleMike2

---

### Post by MonocleMike2 on 2011-10-16
@[23dornot23d]("http://ubuntuforums.org/member.php?u=953253")
Thanks.
update didn't appear to do much.
-settings said it was up to date
-current tried hard but failed with "could not resolve 'gb.archive.ubuntu.com'"

---

### Post by MonocleMike2 on 2011-10-16
Thank you every one for your help.  I shall return to this problem tomorrow morning and in the meantime wish you a pleasant evening.
Good night.

---

### Post by jimbo99 on 2011-10-16
One thing that I noticed about the replies in this thread.  Everyone seems to have forgotten that he stated his hard drive is constantly grinding.  He is also saying his system is slow, so slow as to not be usable.

First, the video card doesn't affect the HDD, in any way, has never and never will.

Second, the key is the hard drive grinding.  Not one person told him to open his system monitor.

Thirdly, has anyone bothered to ask him which desktop manager he's using?

I have a similar problem and I've traced it to the akonadi program.  The akonadi_agent_launcher has loaded itself 25+ times in my case.  If I turn it off my system performance comes back.  But akonadi is required for a bunch of services provided by KDE.

I would recommend this guy check for something similar.

---

### Post by 23dornot23d on 2011-10-16
> 
since all the unity and my top bar disappeared.



In his first post he mentions running UNITY ...... 



Your answer suggests that he is running KDE ...... 

> 
I have a similar problem and I've traced it to the akonadi program.  The  akonadi_agent_launcher has loaded itself 25+ times in my case.  If I  turn it off my system performance comes back.  But akonadi is required  for a bunch of services provided by KDE.


Unless he has added KDE too then this is not the problem ..... but others are having
slow responces in UNITY too .....

Check some of the problems in the link in my footer ...... some being related to the graphics drivers ..... but as you say the hard drive should not be hunting around for things
maybe smartmon on the hard drive too ...... to ensure the hard drive is not failing .....

---

### Post by bmwracer on 2011-10-16
Wow, looks like I'm not the only one noticing the sluggishness with 11.10.

I installed the GNOME Shell on my test PC (Dell Dimension 2400, P4, 2.40 GHz, 1GB RAM), but it's still frustratingly unusable... 

Maybe I'll go back to 11.04... Or try out the LTS 10.04.

---

### Post by Juvencio on 2011-10-17
1. Change your video drivers.

I had to reinstall my drivers after upgrade from 11.04
as it was also so slow.

2. Go to System monitor.

Also I found on my side is that my CPU is almost maxed out 
when I cheeked it was the (CLI) running at 98%
All I did is kill proses

3.To check if your computer hardware are capable of running Unity 3D, open the terminal and run this command:

```
/usr/lib/nux/unity_support_test -p
```


4. Also try what alexpotter sugested.

> **alexpotter said:**
> Ubuntu 11.10 was quite slow on my HP Compaq nc6220 machine, about 6-7 years old. It runs with 1.5GB of RAM and an Intel Pentium M 1.73GHz processor - and the Intel 915GM integrated graphics (128MB).

I think the problem is that Ubuntu depends more on Compiz, therefore graphics acceleration and OpenGL is more stressing, so I installed CompizConfig Settings Manager from the Software Centre and disabled a few options

I tweaked the following

1. Under 'Composite' disable 'Detect Refresh Rate'
2. Under 'OpenGL' disable Sync to VBlank and change Texture Filter to 'Fast'

It immediately took effect on my machine. It was the main thing stopping me to switch to the more responsive GNOME 3 shell.

GNOME 3 is quite fast though, and you may want to take a look. To install it, go to Terminal and type

```
sudo apt-get install gnome-shell
```

Or the GNOME Classic version:-

```
sudo apt-get install gnome-session-fallback
```

Hope I could of helped. :popcorn:

[COLOR="Red"][B]also have a look at
[http://www.upubuntu.com/search/label/System]("http://www.upubuntu.com/search/label/System")[/B][/COLOR]

---

### Post by MonocleMike2 on 2011-10-17
Good morning everyone.  Please keep your suggestions coming as I am not confident that a re-install will be any better though I shall have to try that later this morning if you have not been able to help me crack it.

@jimbo99
Thanks but what can I do about it when I can only get control if I boot into recovery mode which only gives me a text terminal.  From memory I had selected Gnome Classic as my shell the last time I got in but now I don't know how to get any sort of graphical interface.  The disk is not thrashing in recovery mode but it is while failing to load a GUI.

@23dornot23d
Thanks.
I have read your thread carefully and I don't think I have found anything relevant as my big problem is the lack of any sort of graphical interface so I can't try much! 

@juvencio
Thanks.  I have tried them all except system monitor which I can't get into without a GUI and anyway the disk is not thrashing in recovery mode.
The unity test fails as it cannot find a video driver and the gnome re-install says it is already there.

Is there a command which will load another video driver without trying to access the web?  Or if it must use the web how do I get a network connection (I have both hard wire and wireless to my router available)? 

One detail I have not mentioned before is that this machine is dual boot with XP and Ubuntu was loaded via wubi.  I have just checked and XP still loads and runs OK.

---

### Post by MonocleMike2 on 2011-10-17
@juvencio
Thanks.  I followed the link and then followed
[http://www.upubuntu.com/2011/10/new-nvidia-and-ati-post-release-driver.html](http://www.upubuntu.com/2011/10/new-nvidia-and-ati-post-release-driver.html)
and found this was exactly what I did to break the system!!
What I need now is a command to undo it :-)

---

### Post by MonocleMike2 on 2011-10-17
I have just tried the following
sudo apt-get install xserver-xorg-video-nouveau
and it says it is already there and is the newest version.  So I appear to have a driver but how do I get it to start using it?  There must be a config file somewhere but which and where?

---

### Post by Juvencio on 2011-10-17
> **MonocleMike2 said:**
> @juvencio
Thanks.  I followed the link and then followed
[http://www.upubuntu.com/2011/10/new-nvidia-and-ati-post-release-driver.html](http://www.upubuntu.com/2011/10/new-nvidia-and-ati-post-release-driver.html)
and found this was exactly what I did to break the system!!
What I need now is a command to undo it :-)

If you do a re-install
DO NOT USE THE POST RELEASE DRIVERS USE VERSION 173

---

### Post by MonocleMike2 on 2011-10-17
Thank you.
I have decided to do a new install so thank you and goodbye for now.  :-)  I will not use the post release drivers again!

---

### Post by MonocleMike2 on 2011-10-17
In Windows I have un-installed Ubuntu, formatted the partition and downloaded and installed 11.10.  I changed nothing.  It loaded the GUI but the disk was thrashing so, very slowly, I loaded the System Monitor and could see that Memory was running at 60% and Swap was running at over 80%.  CPU was peaking over 80%.  In processes only Gnome-System-Monitor was using the CPU.  I left it for 10 minutes until the disc light went out and now CPU is about 40%, Memory is 20.7% of 495.7 MiB and Swap is 60.2% of 256 MiB.
I have tried loading a couple of things like System and Firefox and CPU peaks then drops back and Memory and Swap stay fairly stable.
It is an old machine.  Will I be better off using Gnome Classic to reduce the load?
-------------------------------------
I'm now running Gnome Classic (without effects) and it is much better. System Monitor shows much more conservative usage and it is now only slightly slower than 10.04.  I would go back and clean install 10.04 if it had offered me that option but it didn't so I'll live with it.  That particular machine is only used for Firefox - or rather it will be when I can get the wireless working again! See
[http://ubuntuforums.org/showthread.php?p=11357826#post11357826](http://ubuntuforums.org/showthread.php?p=11357826#post11357826)

---

### Post by jimbo99 on 2011-10-17
> **23dornot23d said:**
> In his first post he mentions running UNITY ...... 



Your answer suggests that he is running KDE ...... 



Unless he has added KDE too then this is not the problem ..... but others are having
slow responces in UNITY too .....

Check some of the problems in the link in my footer ...... some being related to the graphics drivers ..... but as you say the hard drive should not be hunting around for things
maybe smartmon on the hard drive too ...... to ensure the hard drive is not failing .....

I didn't assume anything.  And his is an upgrade not a new install.  That means he's had it running for a while.  Most likely he's made changes to his configuration including possibly running KDE.  And I asked the question as to whether anyone bothered to ask him which desktop manager he was using.

VIDEO DRIVERS DO NOT CAUSE HDD THRASHING.  He's mentioned this and that IS what is causing his slowness, not the video.

I did some additional investigation.  I turned off Akonadi and I turned off the file indexer and terminated Ubuntu One.  After rebooting there was a bit better performance for my machine.  I switched to Unity for a test (what an awful program).  I noticed that though Akonadi was no longer running and no more 25+ instances of the launcher was in memory, it was still slow.

I decided to wipe my install and started over.  After doign this I noticed that the performance was fine and no more drive thrashing (on my machine).  I have a modified /etc/fstab which mounts a second drive partition as my home.  Upon reboot and logging in I had my old desktop back.  I noticed at that point that the thrashing was back, even in Unity.  If I right clicked on the desktop it took 2+ seconds to load a pop up menu.  It would take another 2+ seconds to get rid of it.

I ran the fsck against the partition and it checks OK, no problems.  I then ran the disk utility against the drive.  It also was fine.  No problems.

My conclusion on this is that there's some oddity having to do with using a separate partition as one's home. Maybe something to do with configuration files is causing some problems (I'm guessing).

Before I decided to wipe and start over, I targeted the video drivers (at the start) as the cause of the whole upgrade problem.  I ruled it out.  One note though, removing the nvidia drivers does create some other nasty issues.  I wound up having to ssh back into the box to get the drivers loaded so I could get to some semblance of a desktop.

---

### Post by bmwracer on 2011-10-17
Pulled out the existing HDD, put in a new one and did a fresh install of 11.10 from scratch... No improvement: still dog slow. :(

No improvement installing and choosing the GNOME shell, either.

---

### Post by fritzk on 2011-10-17
I've been using Ubuntu from Version 9.x on my Dell 2400 (2 GB RAM, 3 GHz CPU) and previous versions have all worked great. I presumed Ubuntu 11.10 would too, but I've been disappointed.

Recently, I'd received error messages from Update Manager on 11.04, so I decided to do a complete reinstall of 11.10.  My first surprise was that instead of using the Swap volume that was already in place, 11.10 decided to carve out another swap volume and left the existing one orphaned.  

Then I noticed 11.10 was much slower than 11.04. I booted off the 11.04 CD and went to System Monitor. With nothing else running, CPU history showed an average of 14 percent.  Then I booted off the 11.10 CD and System Monitor showed an average CPU history of about 35 percent. When I booted off my hard drive, System Monitor shows an average CPU history above 50 percent, which frequently peaks to 100 percent for minutes at at time. When I click on an icon, it might take a minute for the app to show up on the screen. I'd like to determine where all the CPU cycles are being used.  It's almost as bad as Windows XP running a dozen apps at the same time.

I've followed a number of suggestions made above with CompizConfig Settings Manager, but they only made it run slower.  If I can't find a solution to speed things up, I'll be forced to return to 11.04, or maybe even 10.x.

I'd appreciate any constructive ideas anyone has to speed this computer up.

---

### Post by DustofDust on 2011-10-17
> **MonocleMike2 said:**
> In Windows I have un-installed Ubuntu, formatted the partition and downloaded and installed 11.10.  I changed nothing.  It loaded the GUI but the disk was thrashing so, very slowly, I loaded the System Monitor and could see that Memory was running at 60% and Swap was running at over 80%.  CPU was peaking over 80%.  In processes only Gnome-System-Monitor was using the CPU.  I left it for 10 minutes until the disc light went out and now CPU is about 40%, Memory is 20.7% of 495.7 MiB and Swap is 60.2% of 256 MiB.
I have tried loading a couple of things like System and Firefox and CPU peaks then drops back and Memory and Swap stay fairly stable.
It is an old machine.  Will I be better off using Gnome Classic to reduce the load?
-------------------------------------
I'm now running Gnome Classic (without effects) and it is much better. System Monitor shows much more conservative usage and it is now only slightly slower than 10.04.  I would go back and clean install 10.04 if it had offered me that option but it didn't so I'll live with it.  That particular machine is only used for Firefox - or rather it will be when I can get the wireless working again! See
[http://ubuntuforums.org/showthread.php?p=11357826#post11357826](http://ubuntuforums.org/showthread.php?p=11357826#post11357826)

i upgraded to 11.10 and my desktop was unusable slow and couldnt play anymore videos

try lxde... just install it and reboot and at login select lxde which needs less resources and is quicker

i use it here this way and you get a speedy desktop :)

u said you deleted your ubuntu partition... maybe you do again and try out lubuntu

---

### Post by jimbo99 on 2011-10-17
I'm posting more in hopes of maybe spark an idea or two within others as to how to solve this problem.

I posted recently that I had modified my /etc/fstab to mount a hard drive partion as my home folder.  That seemed to be the cause of my slow down.  If I just used the default folder as my home folder on a clean install everything worked well.  No slow downs, no lag, no extra high cpu utilization, no 25+ copies of this or that program loaded in RAM.  Unfortunately, in order to get a more responsive system I had to go back to using the home folder the default install created.  But...

To test a bit further I decided to rename my .kde folder and to copy the .kde folder (created by the new install) into my home folder on the second drive.  I then modified the /etc/fstab file to put it back into play and rebooted.

Everything seemed fine.  No more thrashing.  Few if any warnings from mail agent or from the file indexer.  Right clicking on the desktop immediately brought up the pop up menu and left clicking with it up made it instantly disappear.  Things seemed ok until I opened up the web browser.  I had installed the version of google chrome from the software center.  The browser began to lag again.  It would take 2-3 seconds to bring up a menu or more to open a new tab.  It also would freeze chrome when I typed in a url with the drop down suggestion window frozen above all other apps.  I had to alt+ctrl+esc to kill it.

So, some progress, but some steps backwards.  Right now I'm using Firefox.

---

### Post by bmwracer on 2011-10-17
Couldn't take it anymore: I went back to 11.04.

Compared to 11.10, it's incredibly fast... And besides, the Control Center in 11.04 allows for a lot more customization... Don't know why they stripped it down in 11.10. :confused:

Cheers!

---

### Post by dlstyley on 2011-10-17
Just installed 11.10 after a break from Ubuntu.  Clean, default install of Ubuntu 11.10 from iso.  

Default desktop is obscenely slow to the point of not usable (never waited long enough for it to load left bar - not sure that it ever will....).  Mouse clicks respond in 5-10 seconds.  

If I select 2D from login screen, it works much better, but still seems slow (glitchy redraws, etc).  

Looking at System Monitor shows fairly high CPU usage by compiz and xorg if anything on the screen is moving (moving, resizing windows, etc.)

Dell Precision 370
intel P4 2.8 GHz (hyperthreaded)
nvidia quadro nvs 280

using proprietary nvidia driver 173, but have tried 96 and post-release updates for both with no effect.  

Found this interesting, but don't know enough to know whether this applies or how to try it out...

[http://www.nvnews.net/vbulletin/showthread.php?t=166698&page=4]("http://www.nvnews.net/vbulletin/showthread.php?t=166698&page=4")

```
~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: Quadro PCI-E Series/PCI/SSE2
OpenGL version string:  2.1.2 NVIDIA 173.14.30

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes


```

---

### Post by Juvencio on 2011-10-18
I have noticed that running unity uses 1Gig ram on idle.
Changing it to genome classic did change it back to 0.5Gig ram on idle.

(For those who don&#8217;t know wear to change it on login screen click the gear next to you user name)

So there is something about unity.

I am running 11.10 on a windows 7 ready PC so 1Gig ram on idle is nothing for me.


[COLOR="Red"]**Replace The Unity Interface With Cairo Dock 2.4 **[/COLOR]
[http://www.upubuntu.com/2011/10/replace-unity-interface-with-cairo-dock.html]("http://www.upubuntu.com/2011/10/replace-unity-interface-with-cairo-dock.html")

---

### Post by jimbo99 on 2011-10-18
> **dlstyley said:**
> Just installed 11.10 after a break from Ubuntu.  Clean, default install of Ubuntu 11.10 from iso.  

Default desktop is obscenely slow to the point of not usable (never waited long enough for it to load left bar - not sure that it ever will....).  Mouse clicks respond in 5-10 seconds.  

If I select 2D from login screen, it works much better, but still seems slow (glitchy redraws, etc).  

Looking at System Monitor shows fairly high CPU usage by compiz and xorg if anything on the screen is moving (moving, resizing windows, etc.)

Dell Precision 370
intel P4 2.8 GHz (hyperthreaded)
nvidia quadro nvs 280

using proprietary nvidia driver 173, but have tried 96 and post-release updates for both with no effect.  

Found this interesting, but don't know enough to know whether this applies or how to try it out...

[http://www.nvnews.net/vbulletin/showthread.php?t=166698&page=4]("http://www.nvnews.net/vbulletin/showthread.php?t=166698&page=4")

```
~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: Quadro PCI-E Series/PCI/SSE2
OpenGL version string:  2.1.2 NVIDIA 173.14.30

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes


```

Unless you have screen lag your performance issue is NOT your video card.  Is your hard drive thrashing?  (the light on all the time?) Have you looked at your system monitor to see what might be using the CPU cycles?  Is there one or more programs causing the CPU utilization to be very high?

My system is slow and I've made various posts showing how I have worked through the issues.  My conclusion is that there's more than one problem here. I'm also disappointed in Canonical.  Each subsequent release seems to be worse than the other, going back several releases.  They need to get their quality control under wraps and to take responsibility for much of what's going on here.

---

### Post by harold95 on 2011-10-18
> **kaldor said:**
> For those who are having performance problems, 
To change to GNOME Shell or Unity 2d, simple log out and select it in the gear icon by your name. Log in and you'll be using the option you selected. GNOME Shell is listed as "GNOME" and Unity 2d is listed as "Ubuntu 2d".

this works very well.

how would i go about making it "stick" as the next time i boot the computer, i go right back to unity 3d?

---

### Post by jimbo99 on 2011-10-18
> **harold95 said:**
> this works very well.

how would i go about making it "stick" as the next time i boot the computer, i go right back to unity 3d?

It should stay that way until you change it to something else.

---

### Post by dlstyley on 2011-10-18
> **jimbo99 said:**
> Unless you have screen lag your performance issue is NOT your video card.  Is your hard drive thrashing?  (the light on all the time?) Have you looked at your system monitor to see what might be using the CPU cycles?  Is there one or more programs causing the CPU utilization to be very high?

I do not have hard drive thrashing.  As stated in my original post, I am seeing screen lag coupled by high CPU utilization by compiz and xorg.  

Anyone more experienced with linux have a chance to look at the thread I posted.  In particular, this post?  

[http://www.nvnews.net/vbulletin/showpost.php?p=2487669&postcount=9](http://www.nvnews.net/vbulletin/showpost.php?p=2487669&postcount=9)

It's for debian, but I'm unclear how much is shared across X.  Does this apply to the version of X installed with 11.10 of ubuntu?

---

### Post by harold95 on 2011-10-18
> **jimbo99 said:**
> It should stay that way until you change it to something else.

yeah i thought so too. no deal.
goes right back to the default every time.

---

### Post by Viser on 2011-10-18
My 11.10 is extremely slow. I found that Xwindow is seems to slows down the system:
```
/usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -back
```
This process eats cpu on every mouse move, every window switch.
I tried different nvidia drivers(173, 280, 285) - no luck.
```
/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 8400M GS/PCI/SSE2
OpenGL version string:  2.1.2 NVIDIA 173.14.30

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

```

Any idea?:(

---

### Post by atentik on 2011-10-18
Alright, I am also having a lag issue after the upgrade to 11.10... and a lot of it. I can't use google-chrome, can't use any graphic related stuff including compiz. My ```
/usr/lib/nux/unity_support_test -p
``` produces
[PHP]X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  21
  Current serial number in output stream:  21
[/PHP]
and my ```
lspci
``` procudes
[PHP]
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:03.0 Communication controller: Intel Corporation Mobile PM965/GM965 MEI Controller (rev 0c)
00:03.2 IDE interface: Intel Corporation Mobile PM965/GM965 PT IDER Controller (rev 0c)
00:03.3 Serial controller: Intel Corporation Mobile PM965/GM965 KT Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
05:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
05:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
05:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)

[/PHP]
I believe it is using intel.. How do I get the driver for this?
Thanks.

---

### Post by MonocleMike2 on 2011-10-19
> **jimbo99 said:**
> It should stay that way until you change it to something else.
If you auto-login then it goes to Unity but if you manually login then it sticks to what you selected last time.
[http://ubuntuforums.org/showthread.php?t=1862181](http://ubuntuforums.org/showthread.php?t=1862181)
I think this is probably be a bug/feature!

---

### Post by ophysis on 2011-10-19
+1 here for the lag.

Everything was perfect before the upgrade to 11.10.

This f'n sucks!!

---

### Post by Juvencio on 2011-10-19
[COLOR="Red"]**Updates released!**[/COLOR]

Do the updates and see if they help.

My pc now running at 700 MIB not a 1 Gig ram.

---

### Post by MonocleMike2 on 2011-10-19
A screenshot of my system monitor is 1/2 way down on the right.  This is the only machine where I am running 11.10 the others are held at 11.04!

Sorry!  Screenshot pasted in but it doesn't come out.  Tried twice!

CPU1 19%  CPU2 29%
470.5 (50%) of 937 MiB  70.3 (27.4%) of 256 MiB

---

### Post by atentik on 2011-10-19
> **atentik said:**
> Alright, I am also having a lag issue after the upgrade to 11.10... and a lot of it. I can't use google-chrome, can't use any graphic related stuff including compiz. My ```
/usr/lib/nux/unity_support_test -p
``` produces
[PHP]X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  21
  Current serial number in output stream:  21
[/PHP]
and my ```
lspci
``` procudes
[PHP]
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:03.0 Communication controller: Intel Corporation Mobile PM965/GM965 MEI Controller (rev 0c)
00:03.2 IDE interface: Intel Corporation Mobile PM965/GM965 PT IDER Controller (rev 0c)
00:03.3 Serial controller: Intel Corporation Mobile PM965/GM965 KT Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
05:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
05:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
05:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)

[/PHP]
I believe it is using intel.. How do I get the driver for this?
Thanks.

Anything?

---

### Post by Juvencio on 2011-10-19
Has anybody try using xdiagnose?

This package is a friendly GUI application for diagnosing several
common X.org problems on Ubuntu.

X.org diagnosing and repair unity.

> **atentik** have you installed your gpu drivers
Go to top panel wear you can select to shut down
and select system settings then select additional drivers
this will show you all your gpu drivers 

---

### Post by atentik on 2011-10-19
> **Juvencio said:**
> Has anybody try using xdiagnose?

This package is a friendly GUI application for diagnosing several
common X.org problems on Ubuntu.

X.org diagnosing and repair unity.


I got an error when I try xdiagnose
[PHP]
Traceback (most recent call last):
  File "/usr/bin/xdiagnose", line 57, in <module>
    app = XDiagnoseApplet()
  File "/usr/lib/python2.7/dist-packages/xdiagnose/XDiagnoseApplet.py", line 39, in __init__
    'active':self.has_enable_debugging(),
  File "/usr/lib/python2.7/dist-packages/xdiagnose/XDiagnoseApplet.py", line 160, in has_enable_debugging
    self.load_config()
  File "/usr/lib/python2.7/dist-packages/xdiagnose/XDiagnoseApplet.py", line 113, in load_config
    d = config_dict('/etc/default/grub')
  File "/usr/lib/python2.7/dist-packages/xdiagnose/config_update.py", line 55, in config_dict
    for line in fileinput.input(filename):
  File "/usr/lib/python2.7/fileinput.py", line 253, in next
    line = self.readline()
  File "/usr/lib/python2.7/fileinput.py", line 345, in readline
    self._file = open(self._filename, self._mode)
IOError: [Errno 2] No such file or directory: '/etc/default/grub'

[/PHP]

And there is No additional driver. Please see the attached picture.

---

### Post by atentik on 2011-10-19
any1?

---

### Post by laurens@pz.nl on 2011-10-19
my Eee-top was kinda useless with 11.10, but after sudo dpkg --reconfigure -a gnome-classic is running like a charme again

---

### Post by Juvencio on 2011-10-20
***_atentik_***

Are you using an on-board graphic card?

System Settings will show drivers for added hardware. 

Try the following, and see if you get somewhere with the slow pc issue!
Changing to other desktop options, like unity 2D or Genome.
Also do the updates they were released.

If this helped with the slow pc issue, I suggest you start a new Thread for Intel Graphics if you don't come right with the links I supplied.

[B]
#! Ubuntu 9.04 Update Intel Graphics?[/B]
[http://ubuntuforums.org/showthread.php?t=1403796]("http://ubuntuforums.org/showthread.php?t=1403796")

**Intel Integrated Graphics & Ubuntu Unity? **
[http://ubuntuforums.org/showthread.php?t=1698612]("http://ubuntuforums.org/showthread.php?t=1698612")
[B]
HOWTO: Jaunty Intel Graphics Performance Guide[/B]
[http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582")

---

### Post by PartsMan on 2011-10-20
[LEFT]My desktop is also slow after a fresh install of 11.10.
The same set up was so quick with 10.04 that I didn't even run my second core.

I am running this video card.
**[SIZE=3]ZOTAC ZT-52FPC2N-HSL GeForce FX 5200 256MB 128-bit DDR PCI  Video Card[/SIZE]**

My cores are also working "hard". I usualy have one touching on 80% and the other at 50%. Only about 450mg of my 2g of ram though.

[/LEFT]

---

### Post by syoung27 on 2011-10-20
i find it lags hard everytime i open a new program. Banshee freezes up practically every song, only for a few seconds but what the heeeck. hopefully this gets an update or something! might be checking other distros soon :( ubuntu keeps losing it's appeal

---

### Post by Juvencio on 2011-10-20
Dose anybody read this thread or do they just post hoping for a reply.

THE SLOW PC ISSUE IS CAUSED BY UNITY

This is what I did for my pc to help speed it up. step 1, 2 & 3

1. I had to reinstall my GPU drivers after upgrade from 11.04 as it was also so slow.

2. Also I found on my side is that my CPU is almost maxed out when I cheeked it was the (CLI) running at 98%, All I did is kill proses

3. Updates released! Do the updates and see if they help.

4. Has anybody try using xdiagnose? This package is a friendly GUI application for diagnosing several common X.org problems on Ubuntu.
X.org diagnosing and repair unity.

5. Also try Changing to other desktop options, like unity 2D or Genome. Replace The Unity Interface With Cairo Dock 2.4 

[http://www.upubuntu.com/2011/10/repl...airo-dock.html](http://www.upubuntu.com/2011/10/repl...airo-dock.html)

or even try genome 3 instead of unity.

> **alexpotter said:**
> Ubuntu 11.10 was quite slow on my HP Compaq nc6220 machine, about 6-7 years old. It runs with 1.5GB of RAM and an Intel Pentium M 1.73GHz processor - and the Intel 915GM integrated graphics (128MB).

I think the problem is that Ubuntu depends more on Compiz, therefore graphics acceleration and OpenGL is more stressing, so I installed CompizConfig Settings Manager from the Software Centre and disabled a few options

I tweaked the following

1. Under 'Composite' disable 'Detect Refresh Rate'
2. Under 'OpenGL' disable Sync to VBlank and change Texture Filter to 'Fast'

It immediately took effect on my machine. It was the main thing stopping me to switch to the more responsive GNOME 3 shell.

GNOME 3 is quite fast though, and you may want to take a look. To install it, go to Terminal and type

```
sudo apt-get install gnome-shell
```

Or the GNOME Classic version:-

```
sudo apt-get install gnome-session-fallback
```

Hope I could of helped. :popcorn:

---

### Post by dlstyley on 2011-10-20
Since I had just newly installed 11.10 and had little invested in it.  I decided to start over with 10.04.  

Now all is well.  CPU's at 0% when idling and no lag in screen rendering.  Don't have the new cool Unity, but oh well...

To recap, with 11.10, my symptoms were:
- completely unusable in Unity 3D mode (wouldn't even render the icons in the left bar and menus took 5-10 seconds to render)
- laggy screen redraws in Unity 2D mode
- high CPU utilization of xorg and (sometimes) compiz in Unity 2D mode, regardless which nVidia drivers installed (tried, 173, 96, post updates of both, and even tried installing latest directly from nVidia)
- same behavior after installing and trying Gnome 
- same behavior after removing "restricted drivers" (which uses Nouveau?)

All this leads me to something about the version of X installed by 11.10 creates these symptoms with my hardware.  I didn't know how (or if it is possible) to downgrade X, so just fell back to 10.04.  


This still "feels" like the problem I was plagued with (my card doesn't appear to support Trapezoid rendering).  

[http://www.nvnews.net/vbulletin/showthread.php?p=2487669#post2487669](http://www.nvnews.net/vbulletin/showthread.php?p=2487669#post2487669)

Can anyone tell me if this would affect Ubuntu 11.10 users?  It talks about this problem being in XOrg 1.11, but isn't it likely that this same code would be in the X version of Ubuntu 11.10?  I think that version is 1.12, but not sure how to read those version numbers...

---

### Post by cclements on 2011-10-20
Hey guys, just thought I'd throw my experience in here.  

MacBook Pro 7,1 (NVidia 320M)

I was having extreme slowness in launching applications as well.  It would sometimes take firefox +4s to launch.  I was able to completely eliminate the sluggishness by:

1.  installing the latest nvidia driver from the website, 285.something
2.  in nvidia x server settings app, set "powermizer" to "prefer maximum performance"

Immediately, the sluggishness went away.  Firefox now opens in slightly over a second.  Hope this helps someone.

---

### Post by PartsMan on 2011-10-21
Mine ran better last night after an update. 
Turns out a problem with Medibuntu was keeping my updates from loading.

I am idling at 7% or less on both cores now.

---

### Post by vicshrike on 2011-10-21
When I upgraded from 11.04 it was a bit slow and clunky. But today after an upgrade to the new kernel, 3.0, it feels both faster `n` fresher.

---

### Post by linux_dream on 2011-10-21
I switched to Unity 2d and the problem disappeared.  I had however some graphical bugs in a java application.
I did updates and now... I don't even have Unity.  I can't access any web browser under linux.  In the top bar all I see is "help", "change background" and icons to enter in my folders.  So I don't know what to do to get Unity back.

---

### Post by coldbrook7 on 2011-10-21
After a little more hair pulling I found the problem.
Running Intel Core Duo with 3GB ram and nvidia Gforce graphics.
The Nvidia driver was the problem.
Opened the system settings-additional drivers window.
It was using the graphics driver (version 173).
Downloaded the (version current) (recommended) driver, after restart the install is running smooth again.

---

### Post by linux_dream on 2011-10-21
> **coldbrook7 said:**
> After a little more hair pulling I found the problem.
Running Intel Core Duo with 3GB ram and nvidia Gforce graphics.
The Nvidia driver was the problem.
Opened the system settings-additional drivers window.
It was using the graphics driver (version 173).
Downloaded the (version current) (recommended) driver, after restart the install is running smooth again.
Nice, I want to try but I don't have Unity anymore (gone by itself after downloading the upgrates and installing+reboot).  How do I reach the drivers?

---

### Post by cfar on 2011-10-22
Hi 2 all !
I'm a new here, in this ubuntu world.
I've just installed ubuntu 11.04 and used it about 2 weeks.
In fact everything was fine, but the new update has been released.
I installed it and figured out the this new ubuntu 11.10 FREEZING LIKE HELL!:mad:
The previous, 11.04, version and this one looks for me like Porsche 311 and ukrainan car Zaporozec (for this who never seen this car, you are lucky :D). 
There are lots of lags. In particular every my opening and closing program have delay about 3-10 sec.
Lots of freezing, the most of them happen just after entering the system.:(

So the question is: How can I revert this update and return to the 11.04 version.
Thank you.

---

### Post by masgeeks on 2011-10-22
I never upgrade a machine, I start from scratch.  Every time I have ever tried an upgrade (because I got *lazy*) I would have issues and would wind up wiping it clean anyway.

I did a clean install on my primary workstation of 11.10 and it is fast and stable and happy with gnome-shell...  :)

---

### Post by MonocleMike2 on 2011-10-22
> **cfar said:**
> Hi 2 all !
I'm a new here, in this ubuntu world.
I've just installed ubuntu 11.04 and used it about 2 weeks.
In fact everything was fine, but the new update has been released.
I installed it and figured out the this new ubuntu 11.10 FREEZING LIKE HELL!:mad:
The previous, 11.04, version and this one looks for me like Porsche 311 and ukrainan car Zaporozec (for this who never seen this car, you are lucky :D). 
There are lots of lags. In particular every my opening and closing program have delay about 3-10 sec.
Lots of freezing, the most of them happen just after entering the system.:(

So the question is: How can I revert this update and return to the 11.04 version.
Thank you.

See this thread:
[http://ubuntuforums.org/showthread.php?t=1863650](http://ubuntuforums.org/showthread.php?t=1863650)

---

### Post by Suncat2000 on 2011-10-22
The old graphical environments don't exist in 11.10. You can remove Unity and install Gnome Classic, but it's not the same.

11.10 is noticeably slower than 11.04. About 10-15% slower.

I guess that serves me right for updating on a week night. :-/

---

### Post by dadimix1 on 2011-10-24
> **linux_dream said:**
> Well thank you!  I'll be waiting for any other help then.
It's almost unusable so I'll stick with Windows XP (painfully) until the problem gets solved.

I had a same problem and I had other problems such as laptop getting too hot, fan was always.That was before I had installed VGA driver, mine is GEFORCE 310. 
Now I have no problem. I hope this will help you
Regards

---

### Post by jimbo99 on 2011-10-30
11.04 to 11.10 (after many years of running Ubuntu successfully).  I'm at the point where I can't use Linux any longer.  Not until this issue is resolved.

From my initial upgrade I had problems.  My first issue was some obscure error that told me that I had to do a dpkg re-configure because the upgrade had failed and was likely unusable.  I did this without rebooting and I re-ran the upgrade.  After that completed there were no errors.  Upon reboot I was stuck at the Ubuntu start-up screen.  I had some issues getting into the box and had to "ssh" into it and run the display driver install (nVidia proprietary).  Upon installation and reboot I was taken to the desktop, having Unity as the default, even though I had KDE set as default before the upgrade.

I played some with Unity, concluded it was an awful piece of ****, and logged out to switch to KDE.  Upon logging in I noticed the HDD was thrashing.  I also noticed super slow performance.  I opened system monitor and noted that 2 of the 4 CPU cores were over 50% and a third was at 100%, and the HDD continued to thrash.

I then discovered that the akonadi app had been loaded 25+ times each taking 26+ mb of ram.  I also noted that the file indexer was running.

I searched for a way to terminate akonadi and found I needed to edit some config file.  I then searched how to turn off the file indexer.  Upon reboot I no longer had the 25+ instances of akonadi and I assumed the file indexer had stoppped but the HDD was still thrashing.

I tried to get help in the forums and on IRC but no one even tried to help.

I then chose to, since I had my home folder on a second HDD, erase the install and start over clean.

I performed the install without issue.

When I rebooted I was back to a desktop with Unity.  The HDD was no longer thrashing and the multiple instances Akonadi were no longer present.  All seemed well.

I then decided to alter my /etc/fstab to put back my home folder (on a second HDD).  I edited it, saved, rebooted.  When I did I was back at my old desktop but performance was awful again.  The HDD was thrashing.  Akonadi was at 25+ instances.  CPU utilization was through the roof.

I removed the refrence in /etc/fstab and rebooted.  Came back to a stable machine.

At this point I chose to rename the .kde folder.  After doing this I edited the /etc/fstab (to put my home folder back in place) and rebooted and came back to my KDE desktop with a fresh set up.  I checked the CPU utilization and it was fine.  Akonadi was still loading 25+ instances of itself.  But there was no HDD thrashing.

I then turned off Akonadi and have been using it this way since, but there are outstanding issues.

Google Chrome is super slow to open, to open a tab, and to close tabs or bring up a pop-up menu.  Firefox has the similar problems.

More often than not if I check the system monitor (with Google Chrome closed) it still lists multiple references to it.  Even after clearing the Google Chrome instances, more often than not when I try to type in a web address in the address bar Google Chrome will lock up.  I can't close it.  I have to alt+ctl+esc and kill it that way.  It won't close any other way.

I've changed many settings in Google Chrome to turn off things that might affect the address bar. I've also disabled all extensions.

No luck.  

Since the performance issues are similar in Firefox something else is wrong besides the browsers.

I turned off IPv6.  No cure.

I spend a lot of time in the browser.  I can't have this type of persistent issue.

Any ideas/suggestions would be appreciated.

---

### Post by MonocleMike2 on 2011-10-30
I have got two machines that just won't work under 11.10 so I have cleaned them and put 11.04 back and they continue to work well.  I think I will leave there for a long while.  If it ain't broke, don't fix it!

---

### Post by jimbo99 on 2011-10-30
Yeah, though you haven't said why.  I do agree something is wrong and it is my opinion that Canonical hasn't tried to aid others nor have any fixes been forthcoming.

---

### Post by jimbo99 on 2011-10-30
> **MonocleMike2 said:**
> See this thread:
[http://ubuntuforums.org/showthread.php?t=1863650](http://ubuntuforums.org/showthread.php?t=1863650)

that thread is not related to his complaint in any way, shape, or form.

---

### Post by intelprabus on 2011-11-03
even i had the same problems with ubuntu 11.10...
gnome 3 + fedora = heaven not so fast
gnome 3 + ubuntu 11.10 =hell utterrrrrrrrrrr slowwwwww
unity 3d + ubuntu = doesn't work with old fx5500 gpu
unity 2d + ubuntu = doesn't like it at all

i think i am going to drop off ubuntu..after the fedora 16 release / opensuse 12.1 release this month..

they doesn't seem to care about the old systems..... and gnome shell integration is not perfect if u got an old gpu..

Mac OS X = Ubuntu 11.10 
in terms of OS system requirements...

Surprisingly i am running even Mac OS Leopard in my system but Ubuntu 11.10 sucks..

i hope that they change the name "Ubuntu - LINUX" to "Ubuntu OS 12"....

Ubuntu is not linux anymore...

---

### Post by manki on 2011-11-12
If your hard disk has become busier causing slowness, it's most likely because the default stack size might have changed.  You can edit /etc/security/limits.conf and reduce the size of your stack.  I have posted directions on my blog: [http://linuxtips.manki.in/2011/11/tweaking-stack-size-of-linux-processes.html](http://linuxtips.manki.in/2011/11/tweaking-stack-size-of-linux-processes.html).  Hope this helps.

---

### Post by jcola on 2011-11-12
I can tell you that when I logged out and switched to GNOME CLASSIC desktop instead of Unity 3D, my system is more responsive and much faster. When I upgraded to 11.10 from 11.04 I noticed difference too. 11.10 is way slower. It is so slow.. 

I tought it was my fglrx-driver, so I updated (I had Catalyst 11.8 ) to Catalyst 11.10. Well then even youtube videos started to lag. So I went back to 11.8 and stick with it. Why u can't just install newest drivers without problems? And yes I updated it correctly, and removed the old FGLRX-driver before new install.

Unity 3D is just so heavy, strangely it worked alright in 11.04.

And in Gnome u can add shortcuts to your desktop;)


BTW Oneiric has many bugs that will make your everydaylife harder,for example, some applications won't start (Transmission)

[http://ubuntuforums.org/showthread.php?t=1872977](http://ubuntuforums.org/showthread.php?t=1872977)

BUT YEA, BACK TO GNOME CLASSIC!!

---

### Post by Paul Chang on 2011-11-21
I also experience similar problems: start up very slow; sometimes, there is no response at all if I click my mouse to open a file or a URL or a shortcut to start a program.

My machine has the configuration: AMD Phenon II quad-core, 4G ram, XFX 1G video card using Nvidia lastest driver, etc.

---

### Post by Juvencio on 2011-11-28
XFCE is a most popular lightweight desktop environment for Unix

Why Xubuntu?

Xfce is ideal workstation desktop environment for slower end computers (P2 and up with 256 megs of RAM or so). Kubuntu and Ubuntu with KDE and Gnome can consume quite a bit of resources, so if you need something lightweight you should consider Xfce. Xubuntu is the version of Ubuntu that comes with Xfce as its default desktop environment. 

Adding Xubuntu to an existing Ubuntu/Kubuntu
Paste in this command in the terminal:

[PHP]sudo aptitude update
sudo aptitude install xubuntu-desktop[/PHP]

_***[http://www.virtualhelp.me/linux/49-installing-xfce-on-ubuntu]("http://www.virtualhelp.me/linux/49-installing-xfce-on-ubuntu")***_


you still get a bit of a lag but it 100% better than Unity.

if you don't want the lag try Xubuntu instead of Ubuntu but be prepared for a whole new set of issues.Not to hectic but first try Xfce if you are happy then don't change but be warned Ubuntu is just going to get worse for old pc's

[B][I][U]
Get Xubuntu[/U][/I][/B]
[COLOR="Red"][B][I][U]
[http://xubuntu.org/getubuntu]("http://xubuntu.org/getubuntu")[/U][/I][/B][/COLOR]

Minimum system requirements

You need 256 MB RAM to run the Live CD or 256 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM at install time.

To install Xubuntu with the standard installer (Ubiquity), you need 4.4 GB of free space on your hard disk. The Alternate Install CD only requires you to have 2 GB of free space on your hard disk.

Once installed, Xubuntu can run with starting from 256 (or even just 192) MB RAM, but it is strongly recommended to have at least 512 MB RAM.

---

### Post by JDDurrant on 2011-12-10
> **n0zqh1 said:**
> I notice the same problems here. I updated to v11.10.  Wondering if I should just have done a fresh install?

I tried doing a fresh install on my old Dell. Didn't work... I have a Dell Dimension 5150 with the following specs:
160GB HDD
1GB DDR2 RAM
2.89GHz Intel Pentium D
Motherboard integrated graphics

The computer was quite slow on Windows XP so I installed Ubuntu on it while Ubuntu 11.04 was the latest version. When I "upgraded" to 11.10 I noticed it getting slower so I decided to do a fresh install of it. It was just as slow after the fresh install, if not slower and now the thing won't boot into Windows XP. At the moment the computer is running PCLinuxOS and I haven't had much time to mess about with it.

It looks like Ubuntu has a bug or something that makes it as slow as it is at the moment because I installed it on my mate's computer with the following specs:
1TB HDD
8GB DDR3 RAM
3.4GHz Quad-Core AMD Phemon II Processor
Anyway, these are extremely high end specs which work on video games at their highest settings but when I installed Ubuntu 11.10 on it with Wubi, it was extremely slow.

---

### Post by wavesailor on 2011-12-13
Hi,

I've upgraded from 10.10 to 11.10 and find it extremely slow and unresponsive sometimes. Sometimes it kinda freezes although the hard-disk light flashes.This normally happens if I switch apps or open a new app etc. It's almost so bad I'm considering going back to 10.04. 

**Does anyone have some suggestions on how to get it to run faster?**

My Laptop (Fujitsu LifeBook S7020) has the configuration:
[LIST]
[*]Intel Pentium M Processor 725 1.6GHz
[*]1 gig memory
[*]Intel Mobile 915GM/GMS/910GML Express Graphics Controller
[/LIST]

---

### Post by jvcastle on 2012-01-03
> **wavesailor said:**
> Hi,

I've upgraded from 10.10 to 11.10 and find it extremely slow and unresponsive sometimes. Sometimes it kinda freezes although the hard-disk light flashes.This normally happens if I switch apps or open a new app etc. It's almost so bad I'm considering going back to 10.04. 

**Does anyone have some suggestions on how to get it to run faster?**

My Laptop (Fujitsu LifeBook S7020) has the configuration:
[LIST]
[*]Intel Pentium M Processor 725 1.6GHz
[*]1 gig memory
[*]Intel Mobile 915GM/GMS/910GML Express Graphics Controller
[/LIST]

I did go back to 10.04 LTS...

Same Problem:(

11.04 Ran OK on my old Dell Precision 380

Even the early 11.10 ran fine.  During one of the updates I got the unusable lags many folks experience.  I tried ALL the recommended fixes.  Updated nvidia drivers, tried using alternate desktop managers.
Finally even did a FRESH INSTALL of 11.10 - The unusable lags remained.  There is something wrong in the current (as of Jan 2012) release of 11.10 that doesn't work on some machines!

After wasting DAYS trying to get 11.10 working I gave up and did a new install of 10.04 LTS- I have used that on an old Dell latitude as my primary web server - it runs flawlessly and doesn't waste my time.

I probably won't be upgrading to 12.04 LTS when that comes out either...

---

### Post by Finolin on 2012-01-03
Hello First post here. Want to give my experience with this extremely slow issue with 11.10. I am quite new to Linux so i did an install inside windows and dual booted both windows and Ubuntu. It was sooo slow i had a bad impression of linux and decided I'm going to back to windows, so i formatted and went back to xp. Then i decided a few minutes later I'm going to try again and this time do a fresh install of Ubuntu and use the whole drive instead of dual boot so i booted from the disc this time and did a clean install. 

  The slow issue wasnt an issue it is quite fast actualy im able to download something from software center and actually use the computer now, which was impossible the first time around. Everything is much smoother now and has renewed my opinion about linux (I Love it) its way better than windows in every way. I hope that my story helps others users that are having the same problem, what i did may or may not fix the issue but its definately worth the try I'm not sure if it is an issue with the distro with upgrading from a previous version ot from windows, or if it was an isolated experience. (Excuse my spelling)

---

### Post by MuppetandChums on 2012-01-04
11.10 worked fine after install. Then 2 weeks after crapola. SO SLOW. Even after updates today which I'd hoped would fix the problem.

Thinkpad T41 1GB RAM, 1.6 processor. It worked fine with 10.04.
I wont bore you with the disastrous upgrade.

Just why am I using (attempting to use) an OS that's slower than Vista with the same amount of RAM ?

Stupid is as stupid does.

Back to 10.04

---

### Post by ritchierope on 2012-01-06
Hello Guys!

Thank you very much for the last couple of replies about this problem. Now I see that it really IS an issue and it has nothing to do with video drivers or my configuration. I have been having the same problem too, I am posting my experiences so that maybe someone can skip trying them, as they did not work for me. (installing fresh 11.10 with XFCE)

With the 10.04 or even 10.10 Ubuntu I had absolutely no problems, moreover 11.04 worked quite fine too (a little bit slower, though, but unity - understandable), but with 11.10 my horror started, lagging applications and CPU at 100% all the time. (I tried unity 2d and gnome3 too, they were a bit better, but still disturbingly laggy)

I thought it worthed installing Xubuntu 11.10 (although I have an IBM laptop, Pentium M 2.0Ghz and 1 GB ram which I wouldn't call a low-performance one) and the problem persisted. When watching a youtube video (with HTML5, which worked way better than flash in 10.10) the CPU works 50%+ all the time and if I only want to check an already opened tab in Firefox, the music video starts lagging and the music goes unenjoyable. I was using XFCE for about 2 years with my 750mhz 256mb dell and sometimes the system goes that slow as if I were using that laptop now.

I started looking for another distro, but I think I'll follow your lead and go back to 10.04 or 10.10 and never upgrade again... something went really wrong with 11.10...

---

### Post by mathdater on 2012-01-24
I AM A NEWBIE TO UBUNTU. I was on 11.04 for months. I upgraded to 11.10 and now I am suffering the wrath of open source. I am  running Oracle virtual box on top of Windows 7 with 3 gbs of ram.

---

### Post by SongOfMyself on 2012-01-26
Just to share my experience as some are saying it's due to 11.10 having issues with new/higher spec computers... My desktop is about 4 months old, it's specs:

Ubuntu 11.10 - Intel i7 3.40GHz - 16GB RAM
NVIDIA GTX 560 - 6TB total internal storage

It's flawless so far for me. For comparison, my Acer Netbook ( Intel i3 1.20GHz, 4GB RAM, 500GB hdd ) runs pretty much the same as the desktop, at least for day to day tasks. Gaming, video editing, etc. naturally it's slower.

---

### Post by linuxwalker on 2012-02-12
Hey everyone,

I independently noticed how slow 11.10 is and just made a post about ([http://ubuntuforums.org/showthread.php?t=1924189](http://ubuntuforums.org/showthread.php?t=1924189)).

It looks like the now-ubiquitous use of Python to run many parts of Unity and Software Center, Ubuntu One, etc. may be part of the noticeable slowdown and drive thrashing.

I'm wondering why they are now using Python everywhere. It's become popular, but it's so dang slow. I'm preparing to install a faster, cleaner linux distro alongside this. Just keeping Ubuntu since I'm more familiar with it as sort of a backup.

---

### Post by Sylfurd on 2012-04-01
Hello !

I got a similar problem with my new Sony Vaio VPC SE2C5E laptop.

This issue even happened with the live CD of Ubuntu 11.10. Ubuntu boots super fast, I can log in and everything works wonderfully but after 10~20 seconds everything become extremely slow and unusable.

I can't really launch an application, it takes several minutes ...

I managed to install Ubuntu with the alternate installer without any problem. But after the first boot the problem was here.

Even after a full upgrade in command line the issue is still there.

Here are the spec of my laptop:
Core i5 2450
8GB ram
128GB SSD

Does some have an idea ?

Thank you :)

---

### Post by tvkas on 2012-04-12
I followed the instructions here - [http://linuxtips.manki.in/2011/11/tweaking-stack-size-of-linux-processes.html](http://linuxtips.manki.in/2011/11/tweaking-stack-size-of-linux-processes.html) - and it seems to have made the biggest difference of all. I am using Unity 2D currently, will see how 3D responds to this as will. 

I lowered my stack size to 1024 just as a test and it really does boot faster and respond almost as fast ac my archived 11.04 on a USB drive runs when booted.

---

### Post by tvkas on 2012-04-12
Well, for fun, I booted my old OS 11.04 on my USB drive amd poked around. As a test I opened up GIMP and a fairly heavy image I have been working on. The image opened up in about 20 seconds and I was able to perform a fairly heavy FFT process on that image. It took about 5 minutes to complete. 

I tried the same thing on 11.10 running on my installed disk. Just to open that image took over 5 minutes and performing the same FFT process took in excess of 20 minutes. Actually, I never let it complete, I force quit because I was tired of waiting. I tried this with several different stack settings and it made no difference overall. So, it seems that the stack settings will change spedd for small processes like email or web browsing, But throw a memory hungry image at it (ove a gig while editing) and it is a no go. 

I am still experimenting to see what else helps. But one last thing I will mention is that my stack settings for my 11.04 USB is 8192. Not sure that stack settings alone will do the full job of speeding things up.

BTW, I am running a Gateway MA7, Dual Intel 1.73 ghz processors - 32 bit, Intel 945GM video. 1 gig of memory.

---

### Post by iamwhatiseem on 2012-04-13
> **alexpotter said:**
> Ubuntu 11.10 was quite slow on my HP Compaq nc6220 machine, about 6-7 years old. It runs with 1.5GB of RAM and an Intel Pentium M 1.73GHz processor - and the Intel 915GM integrated graphics (128MB).

I think the problem is that Ubuntu depends more on Compiz, therefore graphics acceleration and OpenGL is more stressing, so I installed CompizConfig Settings Manager from the Software Centre and disabled a few options

I tweaked the following

1. Under 'Composite' disable 'Detect Refresh Rate'
2. Under 'OpenGL' disable Sync to VBlank and change Texture Filter to 'Fast'

It immediately took effect on my machine. It was the main thing stopping me to switch to the more responsive GNOME 3 shell.

GNOME 3 is quite fast though, and you may want to take a look. To install it, go to Terminal and type

```
sudo apt-get install gnome-shell
```Or the GNOME Classic version:-

```
sudo apt-get install gnome-session-fallback
```Hope I could of helped. :popcorn:

Thanks - this helped me a ton.

---

### Post by freshminted on 2012-05-12
Like all previous writers, I too find 11.10 to be slowing down. Boot and start-up now take 5 minutes, and I can only think that the number of programmes on the drive, may influence this. Any external USB drives are a complete no-no, and even printers seem to delay things. As an experiment I shall be running 11.04 on an identical laptop to see what happens. I am a heavy graphics user, using GIMP and Inkscape together most of the time.

---

### Post by Luckiboy on 2012-05-12
Maybe you should decrease the swap usage.
[https://sites.google.com/site/easylinuxtipsproject/first#TOC-Decrease-the-swap-use](https://sites.google.com/site/easylinuxtipsproject/first#TOC-Decrease-the-swap-use)

It works for me:)

---

### Post by caradeporra on 2012-06-12
This thread has kind of gone stagnant, is there any updates on this?  Going through the whole thread really hasn't produced anything in the way of a fix.  My biggest question is, for any of you, has updating to 12.04 fixed the problem at all?  Or does it make it worse?

---

