---
title: "my pannels are gone"
date: 2010-03-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dinamic1 on 2010-03-19
after the last update.. 

[http://i43.tinypic.com/2l6fe1.png](http://i43.tinypic.com/2l6fe1.png)

---

### Post by kurros on 2010-03-19
Yeah I had to manually start gnome-panel as well.

I saw this in .xsession-errors, don't know if it's related:

*gnome-session[2342]: WARNING: Unable to find provider 'gnome-panel' of required component 'panel'*

I think its because we updated in between the gnome-panel, and indicator updates. Not everything is in the package archives yet, and no hard version dependencies were set to hold back upgrades. It should sort itself out in a few hours, I hope.

---

### Post by Half-Left on 2010-03-19
Press Alt, F2 and type gnome-panel. Do they come up?

---

### Post by victor.zamanian on 2010-03-19
> **dinamic1 said:**
> after the last update..

What happens if you do: Alt+F2, and then type in "gnome-panel"?

If nothing happens, are you able to open up a terminal and type "gnome-panel"? If so, what do you see?

---

### Post by Anthony M on 2010-03-19
Same problem, Alt F2 doesnt work either.

---

### Post by dinamic1 on 2010-03-19
> **victor.zamanian said:**
> What happens if you do: Alt+F2, and then type in "gnome-panel"?

If nothing happens, are you able to open up a terminal and type "gnome-panel"? If so, what do you see?

when i press ALT-F2 nothing happens but i can create a launcher on my desktop for xterm :)
[http://i39.tinypic.com/1z2ge2b.png](http://i39.tinypic.com/1z2ge2b.png)

:D thanks, worked great

---

### Post by ernstblaauw on 2010-03-19
I have the same problem. Running 'gnome-panel' solves it for me (in yakuake, which is started automatically).
I think this LP bug report is the one: [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/525240](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/525240).

edit:
I'm wrong, it's [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/542343](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/542343). Sorry!

---

### Post by kurros on 2010-03-19
> **ernstblaauw said:**
> I have the same problem. Running 'gnome-panel' solves it for me (in yakuake, which is started automatically).
I think this LP bug report is the one: [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/525240](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/525240).

That is not the same problem.

---

### Post by kurros on 2010-03-19
> **Anthony M said:**
> Same problem, Alt F2 doesnt work either.

Alt+F2 is provided by gnome-panel :D

Press Alt+T (provided by metacity) to open a terminal then run *gnome-panel &*

---

### Post by cyberkilla on 2010-03-19
I get this when I try to run it manually. It does open, but this is the message:

```
(gnome-panel:2237): EggSMClient-WARNING **: Could not load desktop file '/usr/share/applications/gnome-panel.desktop': Key file does not start with a group
```

---

### Post by Neo40 on 2010-03-19
I installed Beta-1 tonight then I had to update somes packages (68?) and I installed nvidia driver. After reboot, the panels are gone! 
Anyone else has this problem? How to solve?
Thanks!

---

### Post by rickwood on 2010-03-19
I've got the same problem.  As a temporary fix, I right clicked on the desktop and made a new launcher for gnome-panel.  I used this launcher to start the panel just fine.  Then I added gnome-panel to my startup items in System -> Preferences -> Startup Applications. Not ideal, but it works for now until this can get sorted.

---

### Post by Uncle Spellbinder on 2010-03-19
Same here. And alt-F2 does not work.

---

### Post by cecilpierce on 2010-03-19
ctrl-alt T brings up gnome-terminal then type 'gnome-panel but don't close the terminal !

---

### Post by Technoviking on 2010-03-19
nautilus is having issues also. Probably a couple of packages still needed updated.

---

### Post by tr33m4n on 2010-03-19
Same problem here... looks like some codes missing to initiate the startup

---

### Post by aviramof on 2010-03-19
thanks for the info i thought about downloading and install the dvd version but now i'm not so sure anymore weather i should do that i had the same problem as well.

---

### Post by dinamic1 on 2010-03-19
just updated (again)

now my panels and my desktop icons are gone :D at least i have my gray wallpaper
thanks "random deity" ALT + T still works

---

### Post by Uncle Spellbinder on 2010-03-19
Same here. Awaiting further updates to correct this DISASTER.

---

### Post by Uncle Spellbinder on 2010-03-19
Received 68 updates for Beta 1. Can't open any external drives or internal partitions either. Can't even open my home directory.

[img]http://content.imagesocket.com/images/Screenshot_13e1.png[/img]

Can't right-click desktop. No panels.

This latest update made the system completely unusable. Not a great way to start Beta 1.




As far as opening panel:
```
unclespellbinder@lucid:~$ gnome-panel

(gnome-panel:1676): EggSMClient-WARNING **: Could not load desktop file '/usr/share/applications/gnome-panel.desktop': Key file does not start with a group
```

---

### Post by castrojo on 2010-03-19
I've called someone, please stand by and help spread the word on not updating, and for people who it's too late for, the alt-t and gnome-panel does the trick.

---

### Post by ybytyruzu on 2010-03-19
Here too, panel gone and nautilus don't work....

---

### Post by cyberkilla on 2010-03-19
It is a bit stupid, I agree. I've been through a few Alphas now, without my computer being unusable. Then, a beta comes along and makes Plymouth a 50:50 chance of reaching GDM, no desktop icons, no panel:p

Fail.

---

### Post by thonuz on 2010-03-19
another gnome-panel update just came through. Is gnome-panel normally not in startup? I added it and then removed it after last couple of updates but panels still missing. I'm using kubuntu also which seems to have less problems right now, but the forum for kubuntu lucid has little activity unless i went to wrong place.

---

### Post by damend on 2010-03-19
Same issue here. I got around this by adding a hash to the first line of /usr/share/applications/gnome-panel.desktop

here are the steps I took:

Reboot system
At GDM login, hit ctrl-f1 to access console & login with my regular account
at the command prompt enter

    ```
sudo vi /usr/share/applications/gnome-panel.desktop
```


Make sure the file reads as follows and save it (although I do not know what the first line is supposed to be doing or where it should actually go):
[COLOR=Red]
[/COLOR]```
#X-Ubuntu-Gettext-Domain=gnome-panel-2.0
[Desktop Entry]
Type=Application


```

Once you've saved the file, go back to GDM (hit Ctrl-F7) and login. Things should be (relatively) back to normal.

---

### Post by Uncle Spellbinder on 2010-03-19
Yep. I've been involved with testing the last several Ubuntu Alphas as well as Windows Vista and 7 Alphas. Tested all through betas and final. I've never seen this type of mess in a beta release.

---

### Post by mc4man on 2010-03-19
Pretty much see the same, though I actually did a restart so there's nothing available but the background (though scroll on desktop works..

(wanted to see if the 1px fix for nautilus worked - in a way it has, certainly don't see a border anymore

Will just leave a the root shell prompt and wait/hope for an update

---

### Post by Uncle Spellbinder on 2010-03-19
No clue why my "Beta 1 Update Disaster" thread was merged here. It was about MUCH more than the panel issue which is being discussed here.

Can't open any external drives or internal partitions, can't open my home directory and can't right-click desktop. As well as no panels.

---

### Post by damend on 2010-03-19
> **damend said:**
> Same issue here. I got around this by adding a hash to the first line of /usr/share/applications/gnome-panel.desktop

here are the steps I took:

Reboot system
At GDM login, hit ctrl-f1 to access console & login with my regular account
at the command prompt enter

    sudo vi /usr/share/applications/gnome-panel.desktop


Make sure the file reads as follows and save it (although I do not know what the first line is supposed to be doing or where it should actually go):
[COLOR=Red]
[/COLOR]```
#X-Ubuntu-Gettext-Domain=gnome-panel-2.0
[Desktop Entry]
Type=Application

```
Once you've saved the file, go back to GDM (hit Ctrl-F7) and login. Things should be (relatively) back to normal.


Or just move the line to below the [Desktop Entry] line:


```
[Desktop Entry]
X-Ubuntu-Gettext-Domain=gnome-panel-2.0
Type=Application
```[COLOR=Black]




[/COLOR]

---

### Post by splicerr on 2010-03-19
Complete empty desktop here. Thank god for failsafe xterm session. Whomever is responsible for this update, thanks a lot! Maybe you should first test your updates yourself, before dumping it on other people just before the weekend starts.

---

### Post by damend on 2010-03-19
> **Uncle Spellbinder said:**
> No clue why my "Beta 1 Update Disaster" thread was merged here. It was about MUCH more than the panel issue which is being discussed here.

Can't open any external drives or internal partitions, can't open my home directory and can't right-click desktop. As well as no panels.



Same here about opening any Places. 

```
No application is registered as handling this file
```Also get when running nautilus command from terminal:

(nautilus:6108): EggSMClient-WARNING **: Could not load desktop file '/usr/share/applications/nautilus.desktop': Key file does not start with a group

Changed the file as follows:

```
[Desktop Entry]
X-Ubuntu-Gettext-Domain=nautilus
Name=File Manager

``` and can now run nautilus but still can't open any Place from the panel.

Guess I'll wait for the updates...

---

### Post by splicerr on 2010-03-19
> **damend said:**
> Same issue here. I got around this by adding a hash to the first line of /usr/share/applications/gnome-panel.desktop


Thanks! That saved the day :P

---

### Post by Technoviking on 2010-03-19
> **Uncle Spellbinder said:**
> Yep. I've been involved with testing the last several Ubuntu Alphas as well as Windows Vista and 7 Alphas. Tested all through betas and final. I've never seen this type of mess in a beta release.

Even if it has never happen before, the Ubuntu release team does warn people that Lucid is still currently beta software and issues like this could happen and not to use it on mission critical machines.

T-V

---

### Post by Uncle Spellbinder on 2010-03-19
> **Technoviking said:**
> Even if it has never happen before, the Ubuntu release team does warn people that Lucid is still currently beta software and issues like this could happen and not to use it on mission critical machines.

T-V

While I appreciate the sentiment of your post, I'm no beginner. As I stated above, having tested the last several Ubuntu Alphas as well as Windows Vista and 7 Alphas. Tested all through betas and final, I am fully aware of the perils and pitfalls of alpha/beta testing. 

Again...I've never seen this type of mess in *ANY* **beta** release.

EDIT:
And the title of this thread should be changed to reflect the true nature of this disaster of an update. It's NOT JUST PANELS.

---

### Post by kurros on 2010-03-19
Seriously? this happens all the time when there is a sprint after an ISO release. There is a big rush of updates due to the freeze and not all the updates have been built and uploaded to the archive yet. It will work out. Relax. :)

To clarify; Beta 1 is fine, you aren't running Beta 1 anymore.

---

### Post by godhika on 2010-03-19
Oh finally some nice breakage. And I feared this would turn out to be a boring testing cycle (modulo some minor plymouth glitches):lolflag:

---

### Post by mc4man on 2010-03-19
Personally going to wait for an update, looking at lucid from karmic it seems all the nautilus  .desktops ( and a few others now have 
X-Ubuntu-Gettext-Domain=<whatever>
above [Desktop Entry], when it should be at the bottom

---

### Post by drascus on 2010-03-19
Okay I am going to keep my rant to a minimum. People this is a beta 1 there are lots of bugs and bugs that result from upgrading and all sorts of things can happen. I think it's more productive to try and solve a problem rather then complain and say that this isn't beta quality. it's beta quality I am surprised it's this stable actually. 

Here is the easy fix 

1) as said before on purple screen: Ctrl + Alt + T will bring up a terminal now type gnome-panel

now your panels should be back go to System -> Preferences -> Startup Applications 


click add
what I put in
name: gnome panel
Command: gnome-panel
Comment: doesn't start correctly

click save

now when you restart your computer panels should start up no problem. When a fix is released you can delete this from start up applications.

---

### Post by skipperczt on 2010-03-19
There are a lot of .desktop files in /usr/share/applications that need a # in front of the first line. Only took a couple of minutes to fix them all.
Do what others have said about getting the gnome-panel going. Then sudo nano /usr/share/applications/nautilus.desktop  put a # in front of the first line. You can now open nautilus. I went to the /usr/share/applications folder in nautilus and just went one by one through the .desktop folders and fixed them, there are maybe 10 of them in there. Not a big deal! Gotta love running a beta!

---

### Post by mc4man on 2010-03-20
I guess you can comment them, went ahead and edited here, moved the X-Ubuntu-Gettext-Domain=nautilus to the bottom
Ex.
> [Desktop Entry]
Name=File Manager
Exec=nautilus
Icon=system-file-manager
Terminal=false
Type=Application
StartupNotify=true
NoDisplay=true
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.29.92.1
#X-GNOME-Autostart-Phase=Desktop
X-GNOME-Autostart-Notify=true
X-GNOME-AutoRestart=true
X-GNOME-Provides=filemanager
X-Ubuntu-Gettext-Domain=nautilus

(only did a few, more curious as to how an update fixes - see at least 17 here.

(the ones here that were affected
> empathy.desktop
empathy-accounts.desktop
evolution.desktop
evolution-2.2.desktop
gedit.desktop
gnome-panel.desktop
mount-archive.desktop
nautilus.desktop
nautilus-autorun-software.desktop
nautilus-browser.desktop
nautilus-computer.desktop
nautilus-file-management.desktop
nautilus-folder-handler.desktop
nautilus-home.desktop
network-scheme.desktop
palimpsest.desktop
rhythmbox.desktop
ubuntu-about.desktop


---

### Post by skipperczt on 2010-03-20
Yes, that is better. Mine was just a hack... that is a real solution.

---

### Post by alienexplorers on 2010-03-20
Updated from Alpha3 to Beta1 and ran all updates and system still functions normally.  Don't know why everybody is having problems.

---

### Post by keypox on 2010-03-20
same problems... no panels no nautlus, cannot right click.  

$ gnome-panel

(gnome-panel:1559): EggSMClient-WARNING **: Could not load desktop file '/usr/share/applications/gnome-panel.desktop': Key file does not start with a group

---

### Post by Uncle Spellbinder on 2010-03-20
> **alienexplorers said:**
> Don't know why everybody is having problems.

Well, they are real issues. As you can see by the posts and descriptions. Can't open any external drives or internal partitions, can't open my home directory and can't right-click desktop. As well as no panels. Not to mention the [Missing Menu Entries](https://bugs.launchpad.net/ubuntu/+bug/542300) issue.

---

### Post by Uncle Spellbinder on 2010-03-20
Just noticed that Gedit is not present anywhere either. This is getting worse by the minute. 

:-?

---

### Post by donniezazen on 2010-03-20
Yep No nautilus nothing just a blank screen. Is this going to be solved anytime soon.

I am planning to install Kubuntu meanwhile.

SK

---

### Post by kaa.sethu on 2010-03-20
> **kurros said:**
> Seriously? this happens all the time when there is a sprint after an ISO release. There is a big rush of updates due to the freeze and not all the updates have been built and uploaded to the archive yet. It will work out. Relax. :)

To clarify; Beta 1 is fine, you aren't running Beta 1 anymore.

1. Why release ISO before completing build uploads to the archives?

2. Does the problems brought up in this thread also occur if some one is installing freshly and not updating from Alphas ??

~Sethu

---

### Post by mc4man on 2010-03-20
> Just noticed that Gedit is not present anywhere either. This is getting worse by the minute

Well any .desktop that was affected (saw 18 here),  then it will be unavailable till the .desktop is fixed.

I'd expect there would be updates to the various packages that were built with incorrect .desktops as soon as the reason they were built incorrectly is resolved ( or possibly sooner if that's  possible..

(fixed them all here on my main install, updated a tester and the bug is certainly still active

Side note - the updated nautilus has fixed the 1px border quite well here.

---

### Post by kurros on 2010-03-20
> **kaa.sethu said:**
> 1. Why release ISO before completing build uploads to the archives?

2. Does the problems brought up in this thread also occur if some one is installing freshly and not updating from Alphas ??

~Sethu

The Beta 1 ISO is fine. The problem is with new package updates that have happened since this afternoon. If you do a fresh install and do not let update-manager do any updates just yet you will be fine.

---

### Post by NightwishFan on 2010-03-20
A fix in progress:
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/542343](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/542343)

---

### Post by donniezazen on 2010-03-20
> **kaa.sethu said:**
> 1. Why release ISO before completing build uploads to the archives?

2. Does the problems brought up in this thread also occur if some one is installing freshly and not updating from Alphas ??

~Sethu

Yes nautilus initially started but as soon as i updated it crashed and since then i have nothing but a blank screen.

---

### Post by NightwishFan on 2010-03-20
Workaround:
Press ctrl+alt+t to open a terminal. Type this to start the panels.
```
gnome-panel
```

Do not close the terminal. Then press alt+f2 and type:
```
nautilus
```

---

### Post by lidex on 2010-03-20
> **mc4man said:**
> I guess you can comment them, went ahead and edited here, moved the X-Ubuntu-Gettext-Domain=nautilus to the bottom
Ex.


(only did a few, more curious as to how an update fixes - see at least 17 here.

(the ones here that were affected

Thanks mc4man ;)

---

### Post by wgrant on 2010-03-20
See the sticky thread about this for more information.

Fixed core packages will be available from the primary mirror in around half an hour.

---

### Post by kaa.sethu on 2010-03-20
> **kurros said:**
> The Beta 1 ISO is fine. The problem is with new package updates that have happened since this afternoon. If you do a fresh install and do not let update-manager do any updates just yet you will be fine.

Ok I get the picture. Thanks for your clarifications. Excuse me for the delayed response - couldn't allocate time to pen in this response sooner.

The package updates since then have not solved the issues for my beta1 upgraded from alpha 3++ installation. So, I continue to use the solution given by "drascus" in comment #38 

~Sethu

---

