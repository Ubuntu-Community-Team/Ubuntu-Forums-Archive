---
title: "Unity problem and Updates not installing"
date: 2012-09-04
forum: Installation &amp; Upgrades
---

### Post by satyamM on 2012-09-04
Recently, I upgraded to 12.04 from 10.04 through update manager. 
Initially, I had problems with graphics as my GUI was not coming at the time of boot.
I solved it by gdm, but then made lightdm my default display manager.

Now I have two problems::

1. **Every time I boot the computer, I have to go to ctrl+alt+f1 ( command prompt) to type  'unity --reset' so that main application bar(top bar) and launcher show up on Desktop,  if I reboot the computer the main app bar(i.e top bar which shows time and battery life etc.)  and launcher disappear **....... I think 'unity' is not set 'ON' defaultly,  please someone suggest what to do in this ??


2. I have another problem of installing updates, whenever I open 'Update Manager', there are some updates which it shows to install, **but when I press 'Install Updates', the manager just hangs for 3-4 seconds and then do nothing...... **it should ask for password and then start installing updates but it does nothing................

Any solution to this problem??

:-k     :-k      :-k     :-k     :-s....

---

### Post by satyamM on 2012-09-04
Somebody reply please.......

 :frown:     :frown:    :frown:      :confused:     :confused:     :confused:

---

### Post by satyamM on 2012-09-05
No-one got no answer to this ??????

---

### Post by satyamM on 2012-09-05
Is anyone listening to me??  
:-(     :-(    :-(

---

### Post by satyamM on 2012-09-06
:confused:           :idea:          :icon_frown:       :frown:       ](*,)            ](*,)            :cry:


Reply Moderators....

---

### Post by arpanaut on 2012-09-06
Open a terminal use this code and report any errors shown
```
sudo apt-get update && sudo apt-get upgrade
```Hopefully the updates will solve the unity problems.

---

### Post by mörgæs on 2012-09-06
> **satyamM said:**
> :confused:           :idea:          :icon_frown:       :frown:       ](*,)            ](*,)            :cry:


Reply Moderators....

Yes: Please stop bumping your thread. It does not help you getting an answer, but this might do:
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by satyamM on 2012-09-06
> **arpanaut said:**
> Open a terminal use this code and report any errors shown
```
sudo apt-get update && sudo apt-get upgrade
```Hopefully the updates will solve the unity problems.

Hey arpanut,

Thanks for replying.... Finally I get a reply.....

I have done > sudo apt-get update && sudo apt-get  upgrade  and then rebooted...
but no help........after rebooting, still the top bar and launcher doesn't show up...
Ask if you want some more info.....

---

### Post by satyamM on 2012-09-06
> **mörgæs said:**
> Yes: Please stop bumping your thread. It does not help you getting an answer, but this might do:
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

I am sorry Mr. [[COLOR=#DD4814]**mörgæs**[/COLOR]]("http://ubuntuforums.org/member.php?u=939075") if I bumped the thread, but I was not getting replies which was very uncommon here at UF. I followed the above link which you referenced, and I think I have said almost everything clearly in my question, if you see.   

Anyways, Please tell me the solution if one is not getting replies on her/his thread. Should she/he make another thread with different problem statement? or do something else so that she/he is able to solve the problem.


Thanks and Regards.
Satyam M.
Friends call me insane because I have un-installed windows and chose Ubuntu.

---

### Post by arpanaut on 2012-09-06
So all packages updated? No errors?  Anything held back?

Did you have ccsm (compiz-config-setting-manager) installed?
Did you have things all tricked out there?

Did you have any ppa's enabled before the upgrade? This may have some impact on your settings.
Have you checked your video drivers?

---

### Post by mörgæs on 2012-09-06
You should wait, plain and simple. People who might help you live all around the world.

When you bump, the thread disappears from the 'unanswered' list, creating (not solving) the problem.

---

### Post by arpanaut on 2012-09-06
I seem to recall back in early testing when Unity was first released  that the Ubuntu Unity Plugin was sometimes disabled on upgrades.  

If you do not have ccsm installed do so now.

```
sudo apt-get install compizconfig-settings-manager
```Then open it and click on Unity Plugin and make sure it is enabled on the left side in that part of the manager.

A long shot but might help.

PS: Be careful with ccsm, Unity can be sensitive about changes there!

---

### Post by satyamM on 2012-09-06
@arpanaut :: Okay let me tell you what happened some days back when I just upgraded to 12.04 from 10.04...

That evening I started upgrading to 12.04 from Update Manager only.....It took around 2-3 hours to upgrade.......That night, after upgrading , one of my friends adviced me to install the "Cairo Dock" software from Ubuntu Software Centre for a good look of desktop. After installing it, that night it worked all fine, Desktop was looking awesome. I was very happy to upgrade to Ubuntu 12.04 and then I shut it down and slept.

But the very next morning I wake up, I boot the computer and see a heck, I was not able to see my GUI (means Desktop icons and Cairo Dock and anything). What I could see was only command prompt which came just after the booting process when Ubuntu logo comes and those five dots get red and white........... The problem was due to Cairo Dock (I'm sure of this).......there was a warning pop-up window which came the last night when I installed Cairo Dock which said something like " compiz has crashed and blah blah.." (don't remember exactly)....I didn't care for it...

I asked here and also searched on internet about the problem and finally I solved the problem somehow till evening, it ate my whole day....... in the solving process I un-installed Cairo Dock and may be did something to compiz ( may be un-installed it).......
I solved the problem by starting service gdm...

So this is the story,....now tell me what to do...??

Also, I haven't checked my video drivers, tell me how to do it..
By ppa's enabling, do you mean those ppa's which come in Synaptic Package Manager--> Repositories --> Other Software --> links beginning with [http://ppa](http://ppa). laucnchpad.....(and further)....... are these links ppa's ??


Thanks and Regards
Satyam M.
Tell me if you don't like stories.

---

### Post by satyamM on 2012-09-06
I am afraid if I install compiz, then if I would be able to see GUI again or not......because that whole day was wasted in just configuring what's the problem which happened because of compiz....and I don't want to be in similar situation again..........

To tell you my system info :: I am working on Dell Inspirion 15R 1st Generation laptop, which has 3Gb RAM and  [HTML]lscpi[/HTML] produces following output ::

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
12:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
13:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
```

---

### Post by arpanaut on 2012-09-06
No worries about vid. drivers, Intel's are part of the kernel.

You cannot run unity without compiz as unity is a plugin of compiz, 
so if the commands you say you used in 1st post work to produce a usable desktop with the sidepanel on left then you have compiz working.
The ccsm is the manager for the plugins for compiz so to be sure the unity plugin is set to run by default that setting needs to be checked. Make sense?  

At log in are you using unity session?  Or something else? It has been so long since I used gdm login that I can't remember exactly how it works. but shouldn't effect logging in to different sessions.
I don't use cairo dock so I don't know how installing and uninstalling might effect Unity Desktop.

---

### Post by satyamM on 2012-09-06
> **arpanaut said:**
> No worries about vid. drivers, Intel's are part of the kernel.

You cannot run unity without compiz as unity is a plugin of compiz, 
so if the commands you say you used in 1st post work to produce a usable desktop with the sidepanel on left then you have compiz working.
The ccsm is the manager for the plugins for compiz so to be sure the unity plugin is set to run by default that setting needs to be checked. Make since?  

At log in are you using unity session?  Or something else? .


Yes, I am able to produce a usable Desktop by typing command [HTML]unity --reset[/HTML] in command prompt (i.e I go to ctrl+f1+alt).........what happens at first is my Desktop comes with all icons but the top bar (which shows time and battery life) and left side launcher doesn't show up.... so I go to prompt (i.e ctrl + f1 + alt) and type unity --reset to make it correct....

Yes and that's what I need right now..... how to turn on unity for default... ? Do you know how to on it for default...?

Thanks and Regards
Satyam M.
I am going to a class, will be able to reply after an hour.

---

### Post by arpanaut on 2012-09-06
See my post #12 in this thread.

---

### Post by satyamM on 2012-09-06
How to open compiz-manager then.....I am not able to find command to open it, so that I can change my Unity settings.....

---

### Post by arpanaut on 2012-09-06
Hit the top button on the launcher then type ccsm, hit the icon presented and it should launch.
Then check out if the Unity Plugin is enabled.

---

### Post by satyamM on 2012-09-06
Here's screenshot of mine.....see if its okay.....

ok. i'm gonna sleep, its 2 am here...... have a class at 9 am.....will solve problm tomorrow morning after the class.......

---

### Post by arpanaut on 2012-09-06
that's the correct setting.
Did that not correct the login to Unity desktop?
If not I'll have to do some more digging, 
there might be some config files in the /home folder to mess with.

---

### Post by satyamM on 2012-09-06
I just booted my laptop, and yes I didn't get Unity desktop..
I again had to go command prompt and type 'unity --reset' to get proper settings.....



Regards.
Satyam M.
(I'm feeling Insomniac now, cant sleep)

---

### Post by arpanaut on 2012-09-06
That is the correct setting.
If that didn't do the trick for a proper login to Unity Desktop , 
I'll have to do some more digging.

---

### Post by satyamM on 2012-09-07
So what is the problem?
Did you dig it out arpanut ?
I showed you the screenshot that even I have done correct setting, but problem is still occurring on boot that  my top bar and left side launcher are not coming after booting....and I have to go to prompt and perform 'unity --reset' to get usable Desktop.


Satyam M.

---

### Post by arpanaut on 2012-09-07
Sorry about spacing this out, but the 12.10 Beta 1 came out last night and I have been ISO testing and doing installs, my bad.

I found a couple of cases that were similar, the first one seems very close to the symptoms here. The suggested cure there was to reinstall the ubuntu-desktop package See here: [http://ubuntuforums.org/showpost.php?p=12214520&postcount=4](http://ubuntuforums.org/showpost.php?p=12214520&postcount=4) Log out and log in. Hopefully that will take care of it.
That would be my first choice, That may clear up any lingering Cairo Dock issues too.

Also you might want to check for sure that when you are logging in that you are choosing the Ubuntu Session at the sign on prompt, Not the Ubuntu 2d Session.

The second option would be to to remove all the configuration  setting files  for compiz so they will get reset to defaults on a reboot. To start I would reboot ,then when you log in and do the **ctrl+alt+f1 **to get to a console and log in then enter these commands one at a time: 
```
rm -rf ~/.compiz/ 
rm -rf ~/.compiz-1/
dconf reset -f /org/compiz/
sudo reboot
```This looks a little radical but it just removes the compiz configuration files in your home folder which will as I said be re-spawned at defaults when you reboot. The third command just resets a dconf setting.

Anyway that&#8217;s the best solutions I could find.
Good Luck, hope that solves the issue.

---

### Post by satyamM on 2012-09-07
Thanks for replying and I have no problems  if you reply late.

Anyways, is re-installing the Desktop dangerous or safe for GUI because I am a bit feared after what happened with GUI when I installed Cairo Dock...I don't want to loose it again.

---

### Post by arpanaut on 2012-09-07
I would not think so, but in trouble shooting 'puter issues it is not always "fail-safe" unfortunately.
I know nothing about Cairo Dock and the changes it brings to the GUI, and cannot guarantee that it will not bork the GUI, but it should not as it is just reinstalling the standard/default desktop package.

Whatever, back-up your important data to external media so if worse comes to worst the solution is simply to reinstall and migrate your data back.

I believe neither or both solutions should  do anything non-recoverable to your system.
Your call, If you can live with the present work-around, stay the course, if not make back-ups and go for it . I have always thought of computer/OS problems as learning opportunities. Of course, not without long diatribes of cursing and pleas to any available deity... LOL

All I'm saying is back-up, be prepared, and you may learn something. Honestly nothing destructive should happen.

---

### Post by satyamM on 2012-09-08
> **arpanaut said:**
> I would not think so, but in trouble shooting 'puter issues it is not always "fail-safe" unfortunately.
I know nothing about Cairo Dock and the changes it brings to the GUI, and cannot guarantee that it will not bork the GUI, but it should not as it is just reinstalling the standard/default desktop package.

Whatever, back-up your important data to external media so if worse comes to worst the solution is simply to reinstall and migrate your data back.

I believe neither or both solutions should  do anything non-recoverable to your system.
Your call, If you can live with the present work-around, stay the course, if not make back-ups and go for it . I have always thought of computer/OS problems as learning opportunities. Of course, not without long diatribes of cursing and pleas to any available deity... LOL

All I'm saying is back-up, be prepared, and you may learn something. Honestly nothing destructive should happen.



Okay, finally I did take the backup and re-installed the Desktop ::
```

satyam@ubuntu:~$ sudo apt-get install --reinstall ubuntu-desktop
[sudo] password for satyam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libswscale0 libwildmidi0 chromium-bsu libavutil50 vorbis-tools
  openoffice.org-java-common wine1.2 libpostproc51 liblualib50 libavformat52
  fonts-uralic kdesudo libalut0 libx264-98 ttf-uralic chromium-bsu-data
  libvpx0 libglc0 openbsd-inetd libavcodec52 zsh update-manager-kde liblua50
  libmatroska3
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  ubuntu-desktop
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,932 B of archives.
After this operation, 58.4 kB of additional disk space will be used.
Get:1 http://in.archive.ubuntu.com/ubuntu/ precise/main ubuntu-desktop i386 1.267 [3,932 B]
Fetched 3,932 B in 1s (3,566 B/s)           
Selecting previously unselected package ubuntu-desktop.
(Reading database ... 243953 files and directories currently installed.)
Unpacking ubuntu-desktop (from .../ubuntu-desktop_1.267_i386.deb) ...
Setting up ubuntu-desktop (1.267) ...
satyam@ubuntu:~$ 

```

Now I am going to log off and log in....lets see what happens...

---

### Post by satyamM on 2012-09-08
Problem still exists......
Desktop didn't come as it should have come and again I went to do reset unity to produce usable Desktop....

Now I am gonna try second option...lets see what happens in that case.....

---

### Post by satyamM on 2012-09-08
I tried second option..and this time I was only able to get fast boot, Desktop appeared more quick than previously.....for once I thought problem is solved, but it WASN'T unfortunately....

I must tell you some errors which I get when I do 'unity --reset' on prompt (ctrl+alt+f1)..

One line is something like::
```

(compiz:2471) : GConf-CRITICAL **: gconf_client_add_dir assertion 'gconf_valid_key (dirname, NULL)' failed

```

Another line is like::
```

ERROR: 2012-09-08 12:42:10 unity.launcher.trashlaunchericon  TrashLauncherIcon.cpp:62 Could not create file monitor for trash uri:  Operation Not supported

```

Yes, the trash icon in the side-launcher is not working....I click on it, it doesn't open, nothing happens actually, rather I open another folder and then I click on Trash from left side menu items, then it opens up....

Another one is like::
```
(compiz:23601): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```


So any comments on above arpanut...

I know I am giving you so much pain..... but I am ready to fix the error in whatever time it takes, you can take your time and then come back and reply......Thanks.


Regards.
Satyam M.

---

### Post by arpanaut on 2012-09-08
Sorry to hear that, I'm at a loss as to where to go from here.

One thing to try is to purge cairo-dock if you just un-installed purging will remove any unused config files.```
sudo apt-get purge cairo-dock
```that may help. 

something to try,  While at your desktop session, instead of going to  a virtual terminal try the regular terminal and doing a unity -- reset. 
Then you can copy and paste the terminal output here to look at.

I don't know???  How attached to your present install are you?
A fresh install might bring considerable relief, No?
I know it's a PIA but may prove to be less painful and time consuming in the long run.
Sometimes upgrades don't go as well as expected.

I have no clue at this point as to what about cairo-dock brought on these problems so my ability to help is limited.

---

### Post by satyamM on 2012-09-08
Hey arpanut,

I just don't know how that stroke my mind, but I followed your advice of running 'unity --reset' in terminal at Desktop. I did that, and it produced somewhat similar results as it was producing when ran in ctrl+alt+f1.  Everything resumed normal but in terminal the process was not over as it just hangs after some lines, but usable Desktop came and I started to use it.....

But suddenly I did ctrl+c on terminal as I had to run a C program(although I could have done it in a new window but I did it in a hurry)  and the desktop was gone again, I was left with only icons and nothing else........

Then suddenly an idea strikes my mind to look  for ccsm settings which seemed very fine two days ago when we shared screenshots.

I type 'ccsm' in terminal, and look for 'Ubuntu Unity Plugin' checkbox,  and see if it is cheked or not and I find it is NOT checked..... I checked it and as soon as I checked it, then  appears a pop-up window which says something like "compiz-Library tool box is disabled. Do you want to enable it ?"
I enabled it, as I enable it, again a pop-up window comes and asks again to enable something, I enable it too.......then I see my desktop resumes normal.....then I thought of rebooting...I closed ccsm, and in same terminal I type 'sudo reboot'.....

And this time when I see my Desktop::: "OMG...it is working".  I again opened ccsm and looked for the  checkbox for 'Ubuntu unity plugin'.......and yes it was marked obviously.......

I again rebooted just to make sure the problem was completely gone and YES the problem is gone.....it is normal now.......woah !!.


Any comments from you on this.. :D

---

### Post by arpanaut on 2012-09-08
> Any comments from you on this.. :grin:YAY! That's just amazing, I don't know what it was that got us over the hump but glad it has worked out.  Funny how things work sometimes. LOL No reinstall, that's a relief!

Probably had to do with the purging and recreation of the compiz configuration files... I remember back in early development of Unity that there were issues with the plugin getting disabled and seeing those questions popping up to enable things, that's why there is no checkbox on the initial ccsm screen. people were accidentally disabling it and then losing the desktop.  Betcha it was some incompatible setting of compiz being carried over from 10.04.

But Hey, Glad your system is back to normal!
Lets hope it sticks...  I'm happy that I could be of assistance.

P.S. If after a few days the fix does stick, come back and mark this thread as "Solved" from the "Thread Tools" at the top of the page.

OT.  Glad you got your 50 posts now and got an avatar!

---

### Post by satyamM on 2012-09-08
>  Betcha it was some incompatible setting of compiz being carried over from 10.04.Yes. May be something that worked in 10.04 but didn't work in 12.04.

> 
Lets hope it sticks...  I'm happy that I could be of assistance.
Yes, of course. Couldn't have solve it if you didn't propose different methods/tricks and that last one, running unity from Desktop terminal only.
Anyways, at least I know something more of Ubuntu now, because this problem occurred and we solved it. So thank you very much.=D>=D>=D>


> Glad you got your 50 posts now and got an avatar!Thanks a Lot.    :guitar:      \\:D/


Regards.  ):P

Satyam M.

---

