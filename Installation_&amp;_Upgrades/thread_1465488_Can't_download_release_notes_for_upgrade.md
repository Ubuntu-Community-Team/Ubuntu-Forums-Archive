---
title: "Can't download release notes for upgrade"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by jonathanhayward on 2010-04-29
My system says an upgrade is available, but when I click on *Upgrade*, I get:

[INDENT]**Could not download the release notes**
Please check your internet connection.[/INDENT]

My web browser can access the network fine. What's going on here?

---

### Post by Zyonin on 2010-04-29
> **jonathanhayward said:**
> My system says an upgrade is available, but when I click on *Upgrade*, I get:
[INDENT]**Could not download the release notes**
Please check your internet connection.[/INDENT]My web browser can access the network fine. What's going on here?

Same thing here.   Not sure what is going on though an overloaded server would not be out of the realm of possibility. 

I would rather avoid the download and burn ISO route and my machine's hardware/BIOS predates the "Boot from USB" option.

---

### Post by scathmandra on 2010-04-29
Same thing here, on the ASUS EEE PC 1000HE. I've tried it both through wireless and Ethernet...

---

### Post by parrot5 on 2010-04-29
Same here. Server down maybe?

---

### Post by solorize on 2010-04-29
Yup same problem here!

Rushed home this evening threw my dinner down
my head, so I could upgrade and now it wont
let me LOL gutted.

Hope they sort it out soon.

[IMG]http://i11.photobucket.com/albums/a199/solorize/updateerror.png[/IMG]

---

### Post by Peace_n_Pedals on 2010-04-29
I'm getting the same thing. Any ideas...? I did start installing it but my internet connection was really slow and it said it was going to take about 3 days to install so I stopped it and restarted my wireless, laptop etc and got a normal speed but now it either comes up with the "Can't download release notes for upgrade" message or Update Manager just freezes.

Maybe it's everyone trying to download it at once. Maybe I'll try and be patient and try again at the weekend :)

---

### Post by joeradtke on 2010-04-29
Same problem.  Tried three different computers.  Internet connection is fine - can do anything but upgrae to 10.04

---

### Post by SavageWolf on 2010-04-29
Same problem here... Stupid waiting...

How many servers does the Ubuntu update thing have anyway?

---

### Post by bapoumba on 2010-04-29
> **SavageWolf said:**
> 
How many servers does the Ubuntu update thing have anyway?

Not sure. Please be patient, it'll get better in a few days.

---

### Post by shanest on 2010-04-29
Same problem here.  If I download an iso, can I upgrade with that?

---

### Post by jonathanhayward on 2010-04-29
I just tried again, and this time it seemed to work, or at least start getting farther.

---

### Post by bapoumba on 2010-04-29
> **shanest said:**
> Same problem here.  If I download an iso, can I upgrade with that?
yes, once the CD is detected, it will offer the option to use it to upgrade. Please use torrents to dl the CD. Or wait a few days :)

---

### Post by thebigob on 2010-04-29
Ok this may be a terrible hack however I also got this error what I did was ran this

```

sudo sed -i 's/karmic/lucid/' /etc/apt/sources.list 

```

Then 

```

sudo apt-get update

```

I then cancelled the update and reran update manager.

This told me there was an error and offered me a partial upgrade which is now running happily.....

If your feeling brave you can try this if not I recommend waiting till tomorrow.

---

### Post by parrot5 on 2010-04-29
It started working... I did nothing to fix it. Guess a server was down.  The download was SLOW, at 40kB/s or so. So I cancelled it and started it again. This time it's maxing out my connection :)

---

### Post by fionasboots on 2010-04-29
I've switched the software source to [www.mirrorservice.org](www.mirrorservice.org) and then tried again and seems to be working fine :)

---

### Post by Axellink on 2010-04-29
How do you switch the software source?  I'm using a netbook so burning a iso disk is no use to moi :(

---

### Post by Niccity on 2010-04-30
> **shanest said:**
> Same problem here.  If I download an iso, can I upgrade with that?

Same problem here re release note. Eliminated obvious connection issues so must be an 'upstream' issue or possibly a bit of code in the update programme that points to a dev/null on the Net ;-)

Re ISO - apparently yes - the page below also shows how to mount the ISO as a drive to avoid having to actually burn a disc. 

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

I have not tried this but looks like a way forward if one wants that Lynx now.

Maybe the Lynx  is just not as Lucid as it could be right now! :-)

---

### Post by Kleenux on 2010-04-30
Same problem in Japan through a local mirror.

---

### Post by solorize on 2010-04-30
hmm got home tonight and still can not do the upgrade =(

It keeps coming up with "Could not download the release notes"
Please check your internet connection.


Just tried to upgrade on my laptop to, but get the same
error message.

Does anyone know what the actual problem is and when it may
be resolved?

---

### Post by Niccity on 2010-04-30
Finally worked for me after a lot more tries at about 3pm BST. Download speed was erratic and at times grindingly slow. Leads me to think it is just traffic levels. If so the up-side is that a lot of people are persisting and also willing to try what is still a Beta.

All I can suggest to those still having problems is just to retry from time to time. After the tedious download LL installed OK and though I have a couple of little bugs (I will report those on relevant forum/topic as soon as I have found it is not user stupidity ;-) ) it all seems to be working fine.

---

### Post by Yathi on 2010-05-01
Been trying for 2 days now. Still no luck! :(. Is it possible to upgrade from the CD and still have all the extra apps i have installed for example Eclipse, Wine, Amarok etc. I dont want to install everything all over again.

---

### Post by Girya on 2010-05-01
I was having the same problem, the default server that update manager uses must be getting hammered with upgrade requests. 

I changed server settings in update manager: update manager > settings > software sources > ubuntu software. 

I tried three or four servers before I found one that was downloading at reasonable speeds.

I'm a upgrading fool right now:P

---

### Post by chuckNbanna on 2010-05-05
Hi, I am having this same problem.

I looked into finding a server but could not find one that fixed the problem.

The funny thing is that I have a workstation sitting right next to my laptop, connected through the same router and outgoing server here.  The workstation will initiate the upgrade no problem.  The laptop will not...

I get the same error message everyone has been reporting.

Any clues?

Thanks,
Chuck

---

### Post by grzesag on 2011-04-28
Hi


System -> Update Manager -> Settings and search for best server for your location or select server (I have selected [www.mirrorservice.org](www.mirrorservice.org)) and works fine

I am in the middle of upgrading 

I hope it helps

And there is link to website if you with to read more:

[http://www.howtoforge.com/how-to-upgrade-ubuntu-10.10-maverick-meerkat-to-11.04-natty-narwhal-desktop-and-server](http://www.howtoforge.com/how-to-upgrade-ubuntu-10.10-maverick-meerkat-to-11.04-natty-narwhal-desktop-and-server)

Regards
G

---

### Post by minerbog on 2011-04-29
> **grzesag said:**
> Hi


System -> Update Manager -> Settings and search for best server for your location or select server (I have selected [www.mirrorservice.org](www.mirrorservice.org)) and works fine

I am in the middle of upgrading 

I hope it helps

And there is link to website if you with to read more:

[http://www.howtoforge.com/how-to-upgrade-ubuntu-10.10-maverick-meerkat-to-11.04-natty-narwhal-desktop-and-server](http://www.howtoforge.com/how-to-upgrade-ubuntu-10.10-maverick-meerkat-to-11.04-natty-narwhal-desktop-and-server)

Regards
G

I tried this at 21.00 BST and it works.

Gavin.
[http://www.gavinsharp.co.uk]("http://www.gavinsharp.co.uk")

---

### Post by Popaul on 2011-04-29
Servers are overloaded. You can change the server to download the update.
To pick up the best available at the moment you want to start to update, go to  System/Administration/Update Manager
On the dialog box, click 'Settings' (you may be asked your password)
In the settings dialog box, open the tab 'Ubuntu Software'. There is a list box in the middle for 'Download from:'. Unroll it by clicking on the arrow, then select 'Others...'
In the new dialog box that appears you can click on the button 'Select Best Server'. The system will go through all the reachable servers and pick-up the one that gives best signal/speed. It may take some time. When finish click on the selected server, ok, and ok/close on all the dialog boxes. Then re-do the upgrade stuff. It should be better.

---

### Post by johnshore on 2011-04-30
Thanks for the advice.  That worked perfectly for me.  Don't like the new desktop but that's another matter.

John

---

### Post by machadoug on 2011-06-21
> **Popaul said:**
> Servers are overloaded. You can change the server to download the update.
To pick up the best available at the moment you want to start to update, go to  System/Administration/Update Manager
On the dialog box, click 'Settings' (you may be asked your password)
In the settings dialog box, open the tab 'Ubuntu Software'. There is a list box in the middle for 'Download from:'. Unroll it by clicking on the arrow, then select 'Others...'
In the new dialog box that appears you can click on the button 'Select Best Server'. The system will go through all the reachable servers and pick-up the one that gives best signal/speed. It may take some time. When finish click on the selected server, ok, and ok/close on all the dialog boxes. Then re-do the upgrade stuff. It should be better.

When I do that it tests 325 servers I get the message:
> No suitable download server was found
Please check your Internet connection.

Running 9.10 trying to upgrade to 10.04.

Regards,

---

### Post by machadoug on 2011-06-22
Just for the record, I've use the suggestion below and it worked. I've upgraded all the way to 11.04.
> **thebigob said:**
> Ok this may be a terrible hack however I also got this error what I did was ran this
```

sudo sed -i 's/karmic/lucid/' /etc/apt/sources.list 

```Then 
```

sudo apt-get update

```I then cancelled the update and reran update manager.


All the best,

---

