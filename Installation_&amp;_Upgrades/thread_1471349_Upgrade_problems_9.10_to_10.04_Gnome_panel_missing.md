---
title: "Upgrade problems 9.10 to 10.04: Gnome panel missing, cannot shutdown, ureadahead"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by YnotStrebor on 2010-05-03
Hi all,

Fairly new user, Ubuntu is lovely, but had a few problems after the 9.10 to 10.04 upgrade that I haven't been able to solve through reading the forums. There are 3 stubborn problems: 1) no gnome-panel bars, 2) does not shutdown cleanly, 3) init: ureadahead error on startup.

Please could anyone help with some suggestions? Many thanks.

So, the upgrade went flawlessly, seemed to reboot fine. Apart from this problem:[INDENT]There are **no gnome panel bars**. The top and bottom panel bars are missing, they are no more, they have ceased to be, they have shuffled off this mortal coil, they are an ex-panel.
[/INDENT]I'd not altered the 9.10 gnome panels from their default look from the 9.10 installation. Strangely gnome-panel is often (but not always) running, and maximizing an application leaves the spaces allocated for the bars as if the bars were there.

If anyone can help me (what logs do I need to post, how do I find/create the relevant logs etc.) that would be really really appreciated.

I can eventually recover the panel menus, but I have to do recover the panel menus after every reboot.

The bigger problem is that the **system rarely shuts-down properly**; it gets stuck showing the ubuntu logo & purple background >10mins. If I press and hold the power button of the computer then the computer turns off, but the keyboard flashes the cap lock and scroll lock indicators on and off every second >10mins - a mini disco. 

On **startup** briefly this message is displayed:[INDENT]**init: ureadahead main process 242 *or* 231 *or* 241 terminated with status 5**
[/INDENT]Many thanks for any suggestions, cheers,

Tony.

What I've tried so far (some of these methods seem to have helped other people):

Alt-F2 (sometimes works if the gnome-panel is running, sometimes not) ... then if the run application box pops up typing:[INDENT]gnome-panel --replace 
[/INDENT]Also typing the following three lines into a terminal window works (until the next reboot):[INDENT]gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
[/INDENT]I've also tried adding either of these two lines to the startup-applications, but this doesn't work (although it seems to have worked for other people):[INDENT]gnome-panel --replace
*or*
gnome-panel
[/INDENT]I've manually run the update manger after the upgrade & after several reboots several times, but that hasn't helped.

Final note: To any newbie like me with a similar problem: Assign a keyboard shortcut (System  menu->Preferences->Keyboard Shortcuts->Run a terminal) to bring  up the terminal. This always gets at least a terminal window running, even if Alt+F2 doesn't work.

---

### Post by grandtoubab on 2010-05-03
all about ureadahead
[http://ubuntuforums.org/showthread.php?t=1434502](http://ubuntuforums.org/showthread.php?t=1434502)

---

### Post by YnotStrebor on 2010-05-03
Many thanks grandtoubab for the info on ureadahead. I've got status 5, which turns out to be an error while tracing.

According to keybuk (the developer for ureadahead) I should add "console output" to /etc/init/ureadahead.conf and try again. I  should get a message on the console, which I'll post in the ureadahead thread and see if it is related to the panels & shutdown problems.

Thanks again.

---

### Post by YnotStrebor on 2010-05-06
Update: Shutdown now working OK, but gnome panels still broken.

After the last set of updates now the **shutdown problem seems to be fixed**.

**My gnome panels are still broken.** After every boot I've got to type gnome-panel into the terminal to get them working. Please, has anyone got any ideas to fix this?

---

### Post by johntash on 2010-05-13
> **YnotStrebor said:**
> Update: Shutdown now working OK, but gnome panels still broken.

After the last set of updates now the **shutdown problem seems to be fixed**.

**My gnome panels are still broken.** After every boot I've got to type gnome-panel into the terminal to get them working. Please, has anyone got any ideas to fix this?

I have basically the same problem.   GDM loads fine, I can log in but if I choose Gnome it just hangs and I can't click anything on the screen.   I switched to another tty and gnome-panel's taking 99-100% cpu.    

Right now, the only way I can do anything is to choose 'kde' as the session which actually doesnt start much either, but runs my apps set to start automatically so i can run gnome-terminal and metacity and get a working desktop. 

I'll update this thread if I get it working, but let me know what you find  out! :D

---

### Post by Flamarion on 2010-05-21
I have upgrade to lucid linx ubuntu and after that I get missing gnome panels also (top and bottom). It is random, and I could not figure out what triggers this problem. Is there a solution to this? I will be very gratefull for any help.

---

### Post by jflaker on 2010-05-21
Fix your screen, but you will lose customizations....you can always re-do the customizations.

go PLACES>HOME FOLDER

press CTL-H to expose the hidden files and folders.

Find the folder "gconfd" and delete or rename it.

Log out then log back in.

Your screen should now be "out of the box" like it would be when you first installed.

That is the easy way.  If you want to try to fix it, just let us know

---

### Post by salaba on 2010-05-22
I also have the same problem. No panels, neither the top nor the bottom. Alt-F2, run gnome-panel --replace, temporarily brings the panels back, but log out, log in again, the panels are missing again.

jflaker, your method did not work for me. After re-login, the panels are still missing.

Any

---

### Post by Flamarion on 2010-05-23
> **jflaker said:**
> Fix your screen, but you will lose customizations....you can always re-do the customizations.

go PLACES>HOME FOLDER

press CTL-H to expose the hidden files and folders.

Find the folder "gconfd" and delete or rename it.

Log out then log back in.

Your screen should now be "out of the box" like it would be when you first installed.

That is the easy way.  If you want to try to fix it, just let us know

Jflaker,
Thank you for your suggestion. Unfortunately, it did not work. I have noticed that the folder "gconfd"is recreated by the system just before I logoff. And I was not able to get a new screen when I log in again.
I have more information on the missing panel problem. When the panel is missing (which seems to be a random problem), I cannot work and I have to logoff with Crt-Alt-Del. Then I receive a message that there is a program running (guess which one): panel.
I have a few applets running on my panel, and one of them is used twice (meteorological information, for two different locations). I have noticed that after removing one of them, I did not get missing panel for about 10 sessions now.

What would be the other suggestion you mentioned besides deleting gconfd?

Thanks again!

---

### Post by Kharlo on 2010-06-06
the same problem here!
no panel, commands works just for the moment but after reboot, the same problem again and again, no panels

HELP please!

---

### Post by CyberCod on 2010-06-06
Same problem here.  No panels (or desktop icons) at boot.  Alt+F2 then killall gnome-panel brings them up until the next reboot.  

This is really annoying.

Nvidia drivers in use, CRT and TVout active.

---

### Post by YnotStrebor on 2010-06-09
Sorry for updating this thread with the progress of the problem sooner - I've got some workarounds that might be helpful. Nevertheless, I've not been using Ubuntu for a while due to  this problem; At least Win XP doesn't crash on shutdown (forcing a lengthy disk check), and XP also  starts correctly!

The  problems remain with missing panels and scroll-lock & num-lock lights blinking incessantly on Lucid shutdown. I just have to work around them. Some things that work  for me:

1) Turn on the login screen, and logon to KDE rather  than Gnome.
2) If you want to shutdown from Gnome without the computer crashing, first logout, then  shutdown from the login screen.
3) To start the Gnome panels from a  blank desktop ... 
it helps if you have first (before the problem  occurs, or as soon as the panels are working) assigned a keyboard shortcut to launch a terminal window,   (preferences, Keyboard Shortcuts, Desktop, Run a Terminal, example:  WindowsKey+R) ...
then, whenever you login and you have no panels, you can start the terminal with the  keyboard shortcut and type the command: gnome-panel. (or press arrow up until you  get to the previous gnome-panel that you typed.)
4) Always have a  backup operating system handy if you are using Ubuntu. Puppy-Linux is  good, as is Windows XP :-)

I have Intel 82815 graphics on the motherboard.  Does Ubuntu recognise it? No! Does Ubuntu recognise my monitor? No!  Does PuppyLinux or WinXP recognise my monitor (IIyama) & graphics card? Yes!  Do I have problems in Ubuntu with anything that uses OpenGL? Yes!

Shame, because Ubuntu could be a good  operating system if it just could recognise some bog standard graphics  cards.

I am nigh-on completely out of patience with Lucid. I'm  logging on from time to time in the hope that an update will fix this  problem. Otherwise... Ubuntu has ceased to be my main operating system.  It has ceased to be. It has shuffled of this mortal stack. It is an ex-operating system. Windows, ah bliss (can't believe I said that)!

---

### Post by spamhog on 2010-07-16
BUMP !

I have 10.04 on 3 PCs.  To keep gnome-panel alive I need to keep a fresh clone of all my homes and restore my profiles every 2-3 days on average, and keep spare VIRGIN sudoer profiles to log into to do the cloning and restoring.

It seemed to be related to crashing w/o logging out the affected user. (CRASHING = ending up with a BLACK screen, w/o a functioning UI, be it graphic or CL.  Hadn't had a Linux crash in 2 years - nor an XP crash in maybe 3).

Today one of the virgin profiles failed, first no panels, then no panels and DIFFERENT DT BACKGROUND COLOR, and the PC hadn't even crashed with that user still logged on.

And this on a LTS release.

> 4) Always have a backup operating system handy if you are using Ubuntu.

I want to cry.

Been trying Linux since 1999, used regularly since 2001, exclusively for some 2-3 yrs (during which I didn't have to contend with the vagaries of Linux on a laptop).

If in 2010 XP is STILL more usable. STILL more reliable, STILL less prone to regression breakage, STILL less likely to waste our time, does then insisting with using and promoting Linux mean that the value we attach to an unlimited amount of our time is *nil*?

---

### Post by doublewitt on 2010-07-16
> **spamhog said:**
> If in 2010 XP is STILL more usable. STILL more reliable, STILL less prone to regression breakage, STILL less likely to waste our time, does then insisting with using and promoting Linux mean that the value we attach to an unlimited amount of our time is *nil*?

STILL less likely to waste our time...?
Well, for me, with XP, I had to re-format my entire hard disk every 4 months - a waste of time...? Even if I took all the efforts to "maintain" my system with the *best software available for complete system maintenance - I still lost lots of valuable time... endless defrags, maintenance software routines, virus scans, firewall issues, malware scans, searching + downloading these *many applications... testing them (trials) and paying for some... I'm wasting lots of my time... visiting forums and trying to solve several "bugs" for each application... a waste of time...? waiting and waiting and waiting after developers to fix all these issues... a waste of time...! wow, XP was wreaking havoc in my life! - and I am no beginner with computers... I've only mentioned a little "bit" of the endless headaches with XP and I wasted so much time already... if I would include all other *major annoyances with XP, I would also be wasting my time...

NOW that I have Ubuntu on my system... life is beautiful...! No re-formats, no hassles, no problems... for the past year, I have had such a wonderful experience on my computer enjoying the stability I didn't have with XP. In fact, I will never go back to the complicated mess with the Windows OS...

Ubuntu is the best! - **now I can manage my time wisely**... what a differance this has made in my life...

---

### Post by spamhog on 2010-07-16
> **doublewitt said:**
> STILL less likely to waste our time...?
Well, for me, with XP, I had to re-format my entire hard disk every 4 months - a waste of time...? 

Am I just unlucky?  Or too lucky on the other side?

My laptop is 4 y.o. and I'm still on my horrid original XP install.

SMART says it's been running 7000 hours.

120+ applications installed (and that's just currently).  Full of FLOSS. Nipped, uninstalled, or disabled as much MS code as I could.

Yet, meanwhile, I wore through (in Distrowatch popularity order):
4	Ubuntu
2	Mint
2	openSUSE
2	PCLinuxOS
2	Debian
2	MEPIS
1	Lubuntu
1	Kubuntu
1	Dreamlinux
2	sidux
1	Xubuntu
3	Scientific

Note that there are different releases I installed, configured to the extent that the respective communities deemed possible (or beyond in many cases), loaded with data and tried to use on the desktop.

I am not counting the multiple installs on several machines, nor things I just tried on for a few days, or ran off CD or used before 2006, or used only as fileservers / darknet nodes/ P2P or CLI-only "desktop".

That would include Zenwalk, Knoppix, Puppy, SRCD, tomsrtbt, NetBSD, OpenBSD, PC-BSD, Desktop-BSD, Libranet, Mandrake, Demolinux, Mondo/Mindi, and several more additional releases of the initial list.

I'm a quintessential faithful CLI dog. A couple of months back I was on another Super-Userfriendly Distro IRC. I saw some l33t-wannabes parroting "use the CLI" on a task adequately served by GUI. I objected, that if they wanted to sound leet, instead of loitering around a supposedly super-userfriendly distro, they might as well ssh into NetBSD - as used to do from my very 1st javaphone with a 1" screen, to cut on googling charges by connecting via a remote text browser in freakin' Texas instead of using the phone's built-in w3 doodads. Guess the response.

I K-Y'ed Linux down many an unenthusiastic throat, got several lusers to stick with it for up to 3 years, wrote install howtos for really bad machines, contributed here and there, held hands on IRC, spoke up in many public occasions.

After 10 years I feel once again stuck with nonsense such as
[LIST]
[*]a desktop environment on a STABLE, LONG TERM SUPPORT DISTRO, QUITE POSSIBLY THE BEST EVER, failing in an embarrassingly regressive way
[*]ever more members of the community polluting the search engine's caches and indexes with the kind of uninformed advice I would never dare to offer were I so palpably ignorant.
[/LIST]
Oh, but we do have compiz!

This feels like bankruptcy.

---

### Post by doublewitt on 2010-07-16
Wow - you sure went through a lot...!
About XP though, I guess you're **lucky**...
I'm sure it has run well for some... no doubt.
But then again, if a couple things went wrong with the upgrade process, 
in a sense, it's normally considered as somewhat "common" - even with various 
Windows platforms...
so no matter OS you want to talk about, they all show some problems...
there is nothing perfect out there...
we just need to find the appropriate solutions...
Ubuntu is a step in the right direction for me.

---

### Post by spamhog on 2010-07-17
OK, I have a hopefully constructive update.

[COLOR="Red"]I can **reliably reproduce**
the **disappearance of the panels**
on a **MINT NEW ACCOUNT**
and in **2 different ways**.[/COLOR]


1) [COLOR="Red"]Just USE the account.[/COLOR]
```
adduser username
...
```
Login, panels are there. Logout.  Login again.  Panels gone.

On 1st login, the user's home gets filled with the standard Gnome profile files.

Those **Gnome files** may be** originally generated with a wrong configuration**.


2)[COLOR="Red"] Don't even use the account, back up and restore the homedir.[/COLOR]
```
adduser user username
...
cp -avx /home/username /backup-path/username
rm -rf /home/username
cp -avx /backup-path/username /home/username

```
In this case, /home/username should be a straight copy of the original freshly generated /home/username **WITHOUT any Gnome-added material**.  So a login SHOULD result in a full, fresh Gnome with the panels as on a 1st login.

Yet, even on the 1st login, panels gone.
[LIST]
[*]The only conceivable difference is in file system metadata.
[*]This is germane to an account losing the panels after a crash / power failure, as that too may impede disk flushing and syncing of metadata.
[*]A metadata change also happens during a successful login with panels.
[*]It stands to reason that there's an issue with something that reads filesystem metadata and based on that determines that panels are not to start.
[/LIST]
The weird thing is, my so far little-used but older personal account is fine. It has survived several login-logout cycles and even one instance of power failure without proper logout.

Mine was a fresh and well behaved install, not an upgrade.  The issue may have come down through the **UPDATE** stream in the last several days, which would affect upgrades too, not from the **UPGRADE** process itself.

ASK ME QUESTIIONS!  I wouldn't know what to ask...

---

### Post by candtalan on 2010-07-17
I also have gnome panels missing from a new clean install of 10.04. 
I posted about it a while ago:
[http://ubuntuforums.org/showthread.php?p=9278906#post9278906](http://ubuntuforums.org/showthread.php?p=9278906#post9278906)
it is strange, as I found, and still find on this particular machine:
'This machine is dual boot ubuntu for tests and also runs another Ubuntu 10.04 which was version upgraded from 9.10, and this 10.04 works perfectly.'

as in the linked thread
 using a virtual terminal
ctrl and alt and F1
  to do
pkill gnome-panel
 then ctrl alt F7
to revert to gui again
works to restore th epanels, but thi sis a machine ot b ehanded on to a newcomer and it is unusable for that purpose with this malfunction.

any comments most welcomed

---

### Post by doublewitt on 2010-07-21
Add this to your collection of software...

download this nice little application that either restores your default panels (top and bottom) or restores saved panels that you personally customized. You might have to re-boot your computer to see the results.

The application is called **PanelRestore**
[http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/](http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/)
It's tiny (787 bytes). Simply follow the instructions on the webpage - it's easy to use...

---

### Post by YnotStrebor on 2010-07-22
Thanks for the link, but I get a page not found error.

My panels still do not appear on boot up, I have to launch them from a terminal window using the gnome-panel command.

If I don't log off before shutting down, then the shutdown crashes. Oh, and after a recent update I cannot logoff or shutdown if I'm running the KDE shell.

None of the 5 or 6 (maybe more - I've lost count) of the gnome updates have fixed the problem. I still want to use Ubuntu as my main operating system (so I can recommend it truthfully to my friends) - but at the moment I cannot recommend it because most computer users do not like a operating system that loses the user interface at the drop of a hat.

Ho hum. Still having to use XP, but would love to use Ubuntu for most things. Never had to reformat XP on my home computer for 6 years, or 2000, or 98, had to reformat once in 95, and never with 3.1 or 3.0. Had to reformat every couple of years with MS-DOS 3, but that was because the RLL 10MB hard drive had to be reformatted every so often. Ah, the days when 640K of RAM was "enough for any conceivable application" (to quote from the IBM manual, which I foolishly gave away along with the machine).

This dual-boot XP install barely gets slower with age, and I've never been unable to fix a problem within a week with XP.

Waiting for three things from Ubuntu:
1) The panels start automatically when I start Ubuntu
2) I can shutdown Ubuntu without it crashing
3) My 82815 Intel graphics card is recognised by Ubuntu

So every fortnight or so I download the latest updates with my fingers crossed.

---

### Post by doublewitt on 2010-07-22
Try this link:
[http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/](http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/)

---

### Post by YnotStrebor on 2010-07-22
Thanks Spamhog for working out a way of reproducing the problem. Hopefully someone will read what you've written and have a blinding flash of inspiration as to what is going on.

For me, to restore the panels I no longer need to start a virtual terminal using ctrl+alt+f1 (thanks Candtalan for the clear summary) , instead:

1) Get the panels working (try some of the methods mentioned previously in this thread)
2) Assign a shortcut key to launch a terminal (e.g. WindowsKey+R)
3) Check the shortcut key works
...
4) Now every time Ubuntu starts and it has forgotten to load the panels, press your shortcut key
5) In the terminal window type *gnome-panel *
6) Panels are restored for the session
...
7) On restarts: If you've not typed many commands into the terminal, then pressing the up arrow in the terminal window might be the quickest way of typing the *gnome-panel* command.

(By the way, in case there are any newcomers reading the thread, the way  to get back to the GUI from the virtual terminal is to press  ctrl+alt+f7)

---

### Post by YnotStrebor on 2010-07-22
Thank Doublewitt for reposting the link, the link now works, but the problem remains.

Downloaded the file, ran it, chose to the restore default panels, panels were removed, shutdown & rebooted machine, no panels on start-up.

Same problem as before, no panels. Something is rotten in the state of Denmark.

---

### Post by doublewitt on 2010-07-22
I wonder if the best thing to do - *in your case* - is to make a clean fresh new format & install of Ubuntu... that might help to clear up those issues...

---

### Post by YnotStrebor on 2010-07-22
In my case the last resort will be a clean reinstall - especially because people are having this problem with a clean install.

Gut feeling is that if only Ubuntu would recognise my bog standard graphics card on my bog standard IBM machine (not IBM compatible, this is a really bog standard IBM ancient Pentium III Netvista) then all would be well.

Going to try few more things, dug these up on another forum:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-mga/+bug/572550](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-mga/+bug/572550)
and it s also referenced here:
[http://ubuntuforums.org/showthread.php?t=1467466&highlight=gnome+panel](http://ubuntuforums.org/showthread.php?t=1467466&highlight=gnome+panel)

---

### Post by doublewitt on 2010-07-22
Even though you made a fresh install in the beginning, sometimes, things go wrong during the OS setup process. And so, if that's the case, then a new "install" can be done to correct it. This sort of thing happened to me several times with Windows as well. Anyways, good luck on your research... hope everything works out...

---

### Post by YnotStrebor on 2010-07-22
This command seems to have helped people experiencing the same panel problems if they have a certain Matrox graphics cards:[I]

sudo aptitude remove compiz compiz-core[/I]

Unfortunately, it didn't work for me. But it doesn't seem to have caused any problems either.

And if all else fails I'll do a clean reinstall, but first I'll exhaust a few more months of trial and error and updates.

Thanks Doublewitt for your support and the "hope everything works out." Yes, you're right, Windows upgrades also can suffer from problems too - and I've had to use the repair option on the Win XP installation CD a few times on friends' & work's computers. Given the vast numbers of hardware & software & history permutations its unsurprising that these problems arise for all operating systems.

---

### Post by YnotStrebor on 2010-07-27
[B]Now I can shutdown!

[/B]The latest load of updates have solved my shutdown problem. Ubuntu now shuts down correctly for me.

Many thanks to the person who wrote whichever update did the trick!

Keeping my fingers crossed that a solution to the panel problem comes along soon.

---

### Post by doublewitt on 2010-07-28
> **YnotStrebor said:**
> **Now I can shutdown!**

good news...!

---

### Post by kroneaux on 2010-08-08
Fixed up an old hp machine for my fiancee's parents.
Panels went missing. Clean install.

Made a launcher that sits on the desktop with the gnome-panel command. This can be double clicked after login. Easy for the parents.

Then the volume disappeared from the panel and I had to make keyboard shortcuts. Not so easy for the parents to remember the keys. 

Also noticed that sometimes auto login works, sometimes it goes to the login prompt, and sometimes can't start X at all. I wondered if it was the i810 intel onboard video. I have tried finding a pattern, restarting vs shutting down, the results seem random. Gnome sometimes would not start with the install disk either.

Updated 8-6-10 and froze on shutdown. Had to hold power button.

Unpredictable results in starting a desktop has put me off upgrading my own machine. 

Other than this, I like what I have seen of 10.04.

---

### Post by joe_joe_20 on 2010-08-09
I had a similar problem of missing panels after upgrading from 9.10 to 10.04.

I tried many of the suggestions I found on many forums without success.

Then, I remembered receiving an error message during the update process about my graphics card driver, so I went in System/Administration/Hardware drivers and I disabled my nvidia driver.

After a reboot, my panels were back.

Maybe you have a similar problem with your graphics card driver, even though it's not the same card (mine is a 3d prophet II MX).

---

### Post by alulim on 2010-08-09
god, i've had it, i've been using Linux for years, since I was a teen, and all thought that time you keep telling yourself its a progressive and collaborative process. but people. I give the F up. I have more problems now than when I installed Ubuntu the first time years ago and I cant even remember how many "upgrades" have passed since then. (and its not just Ubuntu) the term if it ain't broke dont fix it never seems to have crossed anyones mind. this is absurd. im sorry. I have to go do grownup things with a computer that works now. 10.04 you are the straw that broke the camels back.

good luck guys, see ya in excel someday.

---

### Post by mayliffe on 2010-08-26
I too am experiencing this. About 80% of startups for me there is no panel. The desktop applet which does killall gnome-panel works fine for me. I've not been able to identify a specific bug for this on launchpad, has it been reported?

Dell Inspiron 1720, nvidia graphics, 64 bit Ubuntu Lucid

---

### Post by alexjt on 2010-10-07
Hi everyone, Im fairly new posting on this forum, but my personal experience in Ubuntu Linux is great (well not all days are great days, but you can learn a lot about it).

I have been trough the same situation with the Gnome-Panel :confused: application and everithing started when I tried to customize the look and feel of my Gnome-Panel, after a couple of mods trough GCONF-EDITOR. I noticed that the panel (both top and bottom) where missing, or when I opened Pidgin or any other application the panel just desappeared, after some days I tried any possible solution checking other forums, but no luck. 

What I tried so far, is to download Compiz from the Ubuntu Software Center.

1) System > Ubuntu Software Center
2) In the search box type: Compiz and install it
3) Then restart the computer
4) Then go to System > Appearence (where you change the themes and background image) > select the Visual Effects tab and select EXTRA or NORMAL (depending on your computer hardware)

The main idea here is to switch from the metacity window manager to Compiz, beacuse so far my GNOME-PANELS are working normally in around 25 sessions and they are still there. Im still testing this, but I hope this helps to you, beacuse I know that is not easy interact with the OS without our beloved panels.

---

### Post by cato58 on 2010-10-18
I too have been having this problem.  Sometimes I log in the gnome panels are there, at other times they are not.

I found a way to jury rig the screen to get the gnome panel every time.

First, change the background theme to high contrast.  This brings the gnome panels back for me.

Next, add a new panel to the top and add the applications you want to the new panel.

Change the background theme to the desired theme.

Now whenever I log in I will either have one or both panels at the top of the screen.

---

### Post by chris1379 on 2010-11-06
OK, this is the exact problem I'm having.
Sony PCG-FX150
Intel 815 chipset
PIII 750
The panels are almost always missing at login. The computer freezes at shutdown with numlock and scrolllock lights flashing. My internal display is not recognized as 1024x768. killall gnome-panel brings up the panels. Oh, and I usually don't hear the login sound. Has anyone found a solution yet?

Chris

---

### Post by chris1379 on 2010-11-07
I found a solution to the missing panels. Just change the theme to Clearlooks or one of the others. I'm using Ambiance Orthodox from [http://gnome-look.org/content/show.php/Ambiance+Orthodox?content=122914](http://gnome-look.org/content/show.php/Ambiance+Orthodox?content=122914) . It looks like the Lucid default theme but has the min, max and close buttons on the right. The panels come up every time.

Chris

---

### Post by Jerommel on 2010-11-17
No problems with missing panels here.
But sometimes my panels, which I have on left and right, suddenly appear in the middle of the screen !
After a few seconds it's back to normal again.

Also, the window list (I have it on the right) sometimes gets really confused and look like it's having a fit when I open a window, or a window opens itself.
This also sometimes occured with 9.04 (I skipped 9.10), but it recoveres by itself more easily whereas with 9.04 I had to kill Gnome Panel...
I don't understand why with vertical panels the window list is not just rotated, so you can still read the texts.
I can only see icons.

I recently added a narrow auto-hiding panel on top for my applications.
This has been behaving really strange at times, ending up in the middle of the screen or yoyo-ing like crazy.

And I hate the new "all in one" notification area. You can no longer dwell over the icons there to have info or click for the window to appear instantly.

Sometimes I wish I had stuck with 9.04 with the cosy brown / orange looks.

---

### Post by obi_wan_kenobi on 2011-02-16
Hi all, 

New ubuntu user here. 

Panel woes.  

I've tried twice to orient a horizontal panel on the bottom of the desktop and to set it as unexpanded, but on restart it appears at the top, and if I open panel properties and select "Bottom" in the orientation dropdown, it just doesn't comply and sticks with "Top".  I have to hold Alt and select the panel with the mouse, then drag it to the bottom. 

Notably, if I set the panel to be expanded, I *can* modify the Right-Click-on-panel>properties>general>orientation to "Bottom".  Also, if I leave it on this setting, the panel appears properly at the bottom when I restart.  

But... I don't want to leave it expanded.

---

### Post by Judebert on 2011-07-30
Removing compiz and compiz-core (and their dependent packages) worked for me.  Thanks!

---

### Post by pyutaros on 2012-01-18
I filed this bug report with gnome-panel in Bugzilla: [https://bugzilla.gnome.org/show_bug.cgi?id=668202](https://bugzilla.gnome.org/show_bug.cgi?id=668202)

---

### Post by oldos2er on 2012-01-18
I'm closing this thread; not only is it old, but unfortunately as the developer says there will be no bug fixes for older gnome-panel bugs.

---

