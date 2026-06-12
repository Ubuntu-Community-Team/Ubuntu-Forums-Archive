---
title: "Linux Noob FATAL Error stuck in DOS"
date: 2005-02-28
forum: Installation &amp; Upgrades
---

### Post by sandman55 on 2005-02-28
Hi I've just installed ubuntu and during instalation I saw something about Modprobe  FATAL Error I let the instalation go on then it went to the internet and spent an hour downloading updates but all the time in a DOS screen no GUI it let me log in with username and password and said I have mail which I dont know how to access in DOS but I have since found the FATAL Error:

Modprobe: FATAL : Error inserting shpchp(/lib module/ 2.6.81-3-386/kernel/drivers/pci/hotplug/shpchp.ko):Operation not permitted

I have since run the live CD and I get a GUI.

I would appreciate it if some can help with maybe how to do a repair instal with out losing the updates I have another CD to try thanks in advance.

---

### Post by piedamaro on 2005-02-28
If you think linux is a GUI on top of DOS, you have a looong way to go. 
Those errors are unrelated to your problem. Probably the installer failed to configure your vga or monitor, search the forum for further help, I'm sure there are a lot of threads about missing raphics after instalation.

---

### Post by sandman55 on 2005-03-01
Thanks for your reply piedamaro yes I know I have a long way to go but I have to start some where

I thought as I can get a GUI with the live CD that ubuntu must have drivers for my VGA and monitor so I reinstalled ubuntu without the updates (with another CD) and I got a logon screen with GUI and I was able to go on the internet with fire fox. 
So this morning  I tried again and reinstalled with the updates and now I'm back to only being able to get a logon with a DOS screen. It said I had mail so I typed "mail" and It said

**Quote:**
To:root@local host. localdomain 
Subject: Debconf: Configuring libraw 1394-5 -- Check that /dev/raw 1394 permissionsare appropriate for you
Date: Wed, 2Mar 2005 12:00:22 +1030 (cst)
from:root@local host.localdomain (root)
The devicefile/dev/raw1394.
This library is used by applications to access Firewire devices.
The default access permissions allows only in the "disk" group.
This restrictive setting was chosen since raw1394 allows almost full access to the firewire bus and all connected devices are accessible, which may include harddisks.

If you dont intend to connect sensitive devices and e.g. only want to get video streams out of a camera, you can relax the permissions. If you dont have malicious users on your system, you can allow access for all users with this command (executed as the root user):
          chmod 666 /dev/raw1394

--
Debconf, running at localhost. localdomain
[ Debconf was not configured to display this note, so it mailed it to you. ]
**End Quote:**

I dont have firewire on this PC its an AMD Duron 800 and I wonder if it is waiting for me to give this command: 
 chmod 666 /dev/raw1394 in order to complete the setup the only thing is I dont know how to do it.

I would appreciate it if someone can give me some advice and thanks in advance

---

### Post by WillCooke on 2005-03-02
Which version are you installing?

Warty or Hoary?

---

### Post by sandman55 on 2005-03-02
warty wart hog

EDIT: Version 4.10

---

### Post by Cossins on 2005-03-02
Sorry for replying unhelpfully, but it hurts my eyes:
You must understand that DOS is an operating system (a miserably obsolete and old one). The correct term for what you mean by "DOS" is "command prompt" or "console".

- Simon

---

### Post by JmSchanck on 2005-03-02
From [www.ubuntuguide.org](www.ubuntuguide.org) (Which is very helpful and you should check it out)

> 
Q: modprobe: FATAL: Error inserting...

   1. Read General Notes
   2.
```

      $ sudo cp /etc/hotplug/blacklist /etc/hotplug/blacklist_backup
      $ sudo gedit /etc/hotplug/blacklist

```
   3. Depends on the Error shown, append the following lines at the end of file
```

      pciehp
      shpchp
      hw_random

```
   4. Save the edited file (sample)


The one you want to add is shpchp

---

### Post by sandman55 on 2005-03-03
Thanks for your help JmSchanck I have typed the first line in to the command prompt after the $ as shown:
 
$ sudo cp /etc/hotplug/blacklist /etc/hotplug/blacklist_backup
I take it that backed up the file because it was followed by a $
then I tried:

 $ sudo gedit /etc/hotplug/blacklist shpchp
It said:
sudo: gedit: command not found

then I tried:

 $ sudo gedit /etc/hotplug/blacklist_shpchp
It said:
sudo: gedit: command not found

In desperation I tried

 $ sudo gedit /etc/hotplug/blacklistshpchp
It said:
sudo: gedit: command not found

I have just noticed before the "$" in each line (I have two computers running here) there is a ~ for example:
My username@ubuntu:~ $

I would appreciate it for any help here

---

### Post by Buffalo Soldier on 2005-03-03
When you installed Ubuntu, which installation method did you choose? The default mode should install GUI automatically.

Gedit is a GUI-based text editor. And I'm guessing it's not installed because you still don't have a GUI.

You can try using nano, a console-based text editor. Just use the same command but just substitute **gedit** with **nano**.

---

### Post by lerrup on 2005-03-03
well, gedit won't work because you need to have a window manager running - try nano instead of gedit to see what works.

I would suggest that the problem would be with the graphical part of the system, usually known as X.  What graphics card have you got, are there any errors with an X or windows thrown up?  Did you see it being installed?  Does your graphics card work in windows?

I would suggest that a reinstallation after checking the hardware is up to speed would be a good idea and ensure that you install ***_everything_*** including "optional" or extra packages and then update.

Let us know how you get on.

---

### Post by sandman55 on 2005-03-03
[QUOTE=lerrup]well, gedit won't work because you need to have a window manager running - try nano instead of gedit to see what works.

I would suggest that the problem would be with the graphical part of the system, usually known as X.  What graphics card have you got, are there any errors with an X or windows thrown up?  Did you see it being installed?  Does your graphics card work in windows?

I would suggest that a reinstallation after checking the hardware is up to speed would be a good idea and ensure that you install ***_everything_*** including "optional" or extra packages and then update.

Let us know how you get on.[/QUOTE]

[QUOTE=Buffalo Soldier]When you installed Ubuntu, which installation method did you choose? The default mode should install GUI automatically.

Gedit is a GUI-based text editor. And I'm guessing it's not installed because you still don't have a GUI.

You can try using nano, a console-based text editor. Just use the same command but just substitute **gedit** with **nano**.[/QUOTE]


Thanks for your reply **lerrup** and **Buffalo Soldier** Yes my graphics card works in Win98 also ubuntu live cd also If I instal ubuntu and dont do the updates it works but when I instal and let the  instal automatically update Im left at the command prompt.

This is my third instal attempt using the (automatic) linux instal.
The first try I let the instal include the updates (about 1 Hour of them on ADSL) but with no GUI only command prompt .
the second instal I did not let it do the updates and I had a GUI Im not sure about sound though (I may not have had the volume up).
So I tried a third time and let it do the updates but no good stuck at the command prompt.

My graphics card is Nvidia Riva TNT2 Model 164 - model164 pro
My CPU is AMD Duron 800

I actually have two errors the rest have OK

modprobe: FATAL:Error Inserting pciehp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/pciehp.ko): Operation not permitted  

and a second one

Modprobe: Fatal: Error Inserting shpchp (/lib/modules/2.6.8.1-3-386/kernels/drivers/pci/hotplug/shpchp.ko): Operation not permitted

The command nano works and gets me in but I dont know how to save and exit there are commands at the bottom of the page save isn't one of them but I cant get them to work if I do control + s   a prompt opens at the bottom of the page that says "[ XOFF ignored, mumble mumble.]" if I move the cursor near the prompt it goes away

---

### Post by Buffalo Soldier on 2005-03-03
The command to exit in nano is **^X** meaning hitting both **Ctrl** key and **X** key.

Then it will ask you: ```
Save modified buffer (ANSWERING "No" WILL DESTROY CHANGES) ?
```basically it's just asking whether you want to save the changes you have made or not.

**Y** for yes, **N** for No and **^C** (**Ctrl** key + **C** key) to cancel.

---

### Post by sandman55 on 2005-03-03
Thanks Buffalo Soldier thats got me started when in nano I typed "pciehp" then hit enter then "shpchp" then hit enter then exit it said "save modified buffer" then it asked "file name to write: /etc/hotplug/blacklist" I left a space and typed "pciehp" I got out and back in to nano did the same thing and typed "shpchp" I then typed "exit" to logout and mometary pressed the start button to reboot (I dont know any other way to reboot in command prompt).

On booting up I still have the two faults so I went back into nano and after viewing help I typed Control+o and put it in that way, still no good so instead of a space between the file and "pciehp" I used "_" but still have the faults.

I'm sorry to be such a pain but can you see where I'm going wrong, when I save I see the file with the appendment at the top of the screen and when I go back into nano I expect to see pciehp and shpchp at the end pf the list but its not there.
any help would be much appreciated.

---

### Post by Buffalo Soldier on 2005-03-03
You did everything correctly except for the last step. When it asked "file name to write: /etc/hotplug/blacklist" just hit **Enter** key.

---

### Post by sandman55 on 2005-03-04
Thanks for that Buffalo Soldier. I did what you said and I dont have any errors on bootup and the two appendments are on the nano list.

The only problem is I'm still at the command prompt also at the command prompt
Myusername@ubuntu:~$ I typed startx and it says "-bash:starx: command not found" I'm begining to wonder if I should reinstal without the updates because its the updates that are messing things up.

What do you think or do you have any other suggestions? I'm sorry to keep bothering you

---

### Post by sandman55 on 2005-03-04
Below is a quote from my earlier post about mail that I got from the console when I first installed I have tried chmod 666 /dev/raw1394 at the command prompt and sudo chmod 666 /dev/raw1394 and it said /dev/raw1394 : No such file or directory I dont know if I should persue this angle incase it is the reason I cant get a GUI as it (mail) says it has something to do with permissions and I dont have firewire on my Computer.

[QUOTE=sandman55]
To:root@local host. localdomain 
Subject: Debconf: Configuring libraw 1394-5 -- Check that /dev/raw 1394 permissionsare appropriate for you
Date: Wed, 2Mar 2005 12:00:22 +1030 (cst)
from:root@local host.localdomain (root)
The devicefile/dev/raw1394.
This library is used by applications to access Firewire devices.
The default access permissions allows only in the "disk" group.
This restrictive setting was chosen since raw1394 allows almost full access to the firewire bus and all connected devices are accessible, which may include harddisks.

If you dont intend to connect sensitive devices and e.g. only want to get video streams out of a camera, you can relax the permissions. If you dont have malicious users on your system, you can allow access for all users with this command (executed as the root user):
          chmod 666 /dev/raw1394

--
Debconf, running at localhost. localdomain
[ Debconf was not configured to display this note, so it mailed it to you. ]
[/QUOTE]

---

### Post by lerrup on 2005-03-04
The quick and dirty way to try this is to reinstall without updates.  Then start synaptic.  You can either start it in a terminal by typing  $ sudo synaptic  or click on it from the menu.

When you have done that press refresh which will scan to see what updates are needed.  Then mark the updates and press apply.  At this point it will tell you what it is going to do.  If it is deleting a whole shed load of stuff including X and gnome don't proceed but copy and paste it to your next posting and we will see what you can do.

Make sure you've configured it so you can go online in Ubuntu first though :wink:

---

### Post by sandman55 on 2005-03-04
[QUOTE=lerrup]The quick and dirty way to try this is to reinstall without updates.  Then start synaptic.  You can either start it in a terminal by typing  $ sudo synaptic  or click on it from the menu.

When you have done that press refresh which will scan to see what updates are needed.  Then mark the updates and press apply.  At this point it will tell you what it is going to do.  If it is deleting a whole shed load of stuff including X and gnome don't proceed but copy and paste it to your next posting and we will see what you can do.

Make sure you've configured it so you can go online in Ubuntu first though :wink:[/QUOTE]

Thanks lerrup I'll have a bit more of a play with this first (try a few commands I found in a search "startx" nothing to lose if I'm going to reinstall, I might learn something :lol: ) then I'll do as you suggest.

---

### Post by p!=f on 2005-03-04
Those error messages can be safely ignored. They just mean you do not have that hardware available.
[http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#booterrors](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions#booterrors)

```

echo shpchp | sudo tee -a /etc/hotplug/blacklist
echo pciehp | sudo tee -a /etc/hotplug/blacklist

```

---

### Post by sandman55 on 2005-03-05
[QUOTE=lerrup]The quick and dirty way to try this is to reinstall without updates.  Then start synaptic.  You can either start it in a terminal by typing  $ sudo synaptic  or click on it from the menu.

When you have done that press refresh which will scan to see what updates are needed.  Then mark the updates and press apply.  At this point it will tell you what it is going to do.  If it is deleting a whole shed load of stuff including X and gnome don't proceed but copy and paste it to your next posting and we will see what you can do.

Make sure you've configured it so you can go online in Ubuntu first though :wink:[/QUOTE]

Well I tried that when I got to the "Mark all upgrades" I tried "smart upgrade" then later "default upgrade" all the way through the process the lower right pane said "No package is selected" I have also tried at the start clicking on "All" (also The apply button is greyed out)
This seems strange when it spent an hour upgrading when I upgraded with the install
My install disk is warty version 4.10 its one of the free disks I'm also sending this from my ubuntu install

---

### Post by lerrup on 2005-03-06
Have you made sure you've refreshed the packages?  When you've done that are there any error messages?  

Otherwise, how long does it take to refresh?  Does it connect and download the packages from the internet?

If not tell check etc/apt/sources and we'll see if there's a problem with that.

---

### Post by sandman55 on 2005-03-07
[QUOTE=lerrup]Have you made sure you've refreshed the packages?  When you've done that are there any error messages?  

Otherwise, how long does it take to refresh?  Does it connect and download the packages from the internet?

If not tell check etc/apt/sources and we'll see if there's a problem with that.[/QUOTE]

Hi lerrup Thanks for your help

Im typing on one computer (WinXP) and doing as you suggest on an other (Ubuntu)

What I've done is open Synaptic Packet Manager click the icon reload, a window opens for about 1 or 2  seconds its title is "Downloading Index files" under total progress it says Downloading file 4 of 4 there is nothing in the pane "single files" 

I then click the icon "Mark all upgrades" a prompt then opens "mark all up grades in a smart way?" I have previously chosen both ways but this time I choose smart up grade.

The icon "Apply" is greyed out and not available.

Ive now checked $ sudo gedit etc/apt/sources
the pane "sources" in the window that opens  is empty, when I close a prompt askes if I want to save and I select "dont save"

Ive been able to do things on the ubuntu computer like mount my Win98 Disk use  firefox and it seems like a good usable operating system it just seems strange you would think it would have something to up grade when with previous installs    it spent an hour up grading  ](*,)

---

### Post by Buffalo Soldier on 2005-03-07
[QUOTE=sandman55]Hi lerrup Thanks for your help

Im typing on one computer (WinXP) and doing as you suggest on an other (Ubuntu)

What I've done is open Synaptic Packet Manager click the icon reload, a window opens for about 1 or 2  seconds its title is "Downloading Index files" under total progress it says Downloading file 4 of 4 there is nothing in the pane "single files" 

I then click the icon "Mark all upgrades" a prompt then opens "mark all up grades in a smart way?" I have previously chosen both ways but this time I choose smart up grade.

The icon "Apply" is greyed out and not available.

Ive now checked $ sudo gedit etc/apt/sources
the pane "sources" in the window that opens  is empty, when I close a prompt askes if I want to save and I select "dont save"

Ive been able to do things on the ubuntu computer like mount my Win98 Disk use  firefox and it seems like a good usable operating system it just seems strange you would think it would have something to up grade when with previous installs    it spent an hour up grading  ](*,)[/QUOTE]
 In Synaptic go to Settings -> Repositories. See which repositories are checked. Make sure
```
URI: http://security.ubuntu.com/ubuntu/
Distribution: warty-security
Section(s): main restricted
```are checked.

---

### Post by sandman55 on 2005-03-07
[QUOTE=Buffalo Soldier]In Synaptic go to Settings -> Repositories. See which repositories are checked. Make sure
```
URI: http://security.ubuntu.com/ubuntu/
Distribution: warty-security
Section(s): main restricted
```are checked.[/QUOTE]

Im stuck in mail at the moment at the console.

I did Ctrl+Alt+F3 and it said I had 3 mail I think the first two are the same because it took me to no.2 It gives me instructions to add entries /CID and /TrueType  (Fonts) to /etc/X11/XF86Config-4
When I navigate my way out of mail Ill try what it says because it reminded me just after my install I tried to improve my fonts I clicked on a download in a thread and nothing happened I forgot about it and its probably the cause of my problem in my last post I said:

[QUOTE=sandman55]a window opens for about 1 or 2  seconds its title is "Downloading Index files" under total progress it says Downloading file 4 of 4 there is nothing in the pane "single files"[/QUOTE]

that "Downloading file 4 of 4" is probably what I clicked on it reminds me of the saying that "A little bit of knowledge can be dangerous"  in other words a noob at the console of the mothership :lol: 

If that doesnt work I'll try what you say  Buffalo Soldier, thanks for your patience with me

---

### Post by SleepWalkerX on 2005-03-07
[QUOTE=sandman55]Hi I've just installed ubuntu and during instalation I saw something about Modprobe  FATAL Error I let the instalation go on then it went to the internet and spent an hour downloading updates but all the time in a DOS screen no GUI it let me log in with username and password and said I have mail which I dont know how to access in DOS but I have since found the FATAL Error:

Modprobe: FATAL : Error inserting shpchp(/lib module/ 2.6.81-3-386/kernel/drivers/pci/hotplug/shpchp.ko):Operation not permitted

I have since run the live CD and I get a GUI.

I would appreciate it if some can help with maybe how to do a repair instal with out losing the updates I have another CD to try thanks in advance.[/QUOTE]

i had this happen to me before, and the modprobe error made no difference for me with the problem.  my problem had to do with my configuration of xfree86 (which was really annoying, they really have to work on that..)   at the prompt type [PHP]sudo dpkg-reconfigure xserver-xfree86[/PHP] 
 (i think that's what it should be)
and go through the configuration.  make sure you put 8bit for the color type and like 800x600 for the screen resolution for now.  you can probably work on increasing the resolution later.  see if this works.

---

### Post by sandman55 on 2005-03-08
[QUOTE=Buffalo Soldier]In Synaptic go to Settings -> Repositories. See which repositories are checked. Make sure
```
URI: http://security.ubuntu.com/ubuntu/
Distribution: warty-security
Section(s): main restricted
```are checked.[/QUOTE]

Thanks Buffalo Soldier I looked and only 
"deb cdrom:[Ubuntu 4.10_Warty Warthog_-Previewi386 Binary (20041020])/ unstable main restricted"
was checked so I checked [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
Distribution: warty-security
Section(s): main restricted 
and reloaded and it looked like I had some action and showed downloading some security files 8 of 8 I then clicked "Mark all upgrades" clicked smart upgrade and nothing and Apply was not available.

I think I will reinstall and start with a fresh slate especially as I may have messed things up at the start But before I do I will try what  SleepWalkerX suggests then I will reinstall to start with a clean slate

EDIT: I didnt read SleepWalkerX's post properly its for my earlier problem of being stuck at the command prompt which I might try later if the downloads messup my vidio card

---

### Post by sandman55 on 2005-03-08
Well Ive reinstalled Ubuntu tried the refresh in synaptic packet manager but no good so I did as you suggested Buffalo Soldier and checked 
URI: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
Distribution: warty-security
Section(s): main restricted

and we have action I refreshed and it downloaded then I clicked smart upgrade and it marked about 100 for up grade and two for instal but I cant copy and paste the selections to firefox so you guys can give your opinions. Does anyone know how? Screen dumps wouldnt be any good they would be huge, otherwise I'll review them as best I can and then try Applying them

---

### Post by sandman55 on 2005-03-09
Well I checked
URI: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
Distribution: warty-security
Section(s): main restricted
as Buffalo Soldier suggested downloaded and installed the updates with Synaptic packet manager (about 1.5 hours a little over 100 files) then ran Synaptic packet manager again it found 4 more so I downloaded and installed them **and I still have a GUI** amazing success **Thanks to all who gave advice**

---

### Post by Buffalo Soldier on 2005-03-10
We only give some hints, it is you who did all the hard work, persevere and being patience. Congratulations :)

---

### Post by sandman55 on 2005-03-10
[QUOTE=Buffalo Soldier]We only give some hints, it is you who did all the hard work, persevere and being patience. Congratulations :)[/QUOTE]

Thanks Buffalo Soldier

---

