---
title: "Upgrade to 12.04 has totally screwed up my PC"
date: 2012-05-09
forum: Installation &amp; Upgrades
---

### Post by Timothy Taylor on 2012-05-09
I had been running 10.04 LTS very happily.
I seem to remember seeing a pop-up some weeks back (in Update Manager I think) telling me that 10.04 LTS was now obsolete, unsupported and that 12.04 LTS was available.  I had Update Manager configured to update to LTS releases only and assumed that this would happen automatically.

I happened to browse [www.ubuntu.com](www.ubuntu.com) yesterday and saw that 12.04 LTS was now the current release, available for download.  Obviously Update Manager has some bug in it.  So I began the slow and tedious process of upgrading through 10.10, 11.04, and 11.10, to 12.04 LTS.

Everything seemed to work fine until the last step - 11.10, to 12.04. Problems appeared as soon as 12.04 started up:

The top 'menu bar' is now transparent, making date/time/icons/etc. invisible against my background. Not only that, but moving mouse over menu bar now causes menu text to appear, which clashes with the 'ubuntu desktop' title, making it unreadable / unusable. I see that this problem screws up the menu for ANY maximised application.

Similarly, the text/background on my desktop items are now black/transparent, making them all but invisible against the desktop background.

The new side/menu bar home-folder and task-switcher buttons have icons missing and now show a folder icon. They were there in 11.x - where have they gone??

I eventually discovered that system preferences and settings are now hidden in the shutdown / restart menu.  Totally obvious / sensible place to put them. :rolleyes:

The weather is now missing from clock/calendar and there is no option to add this.

The "Displays" setting window no longer offers the option to set the monitor frequency.

I can't find any trace of the Palm device sync to sync with my PDA.

Evolution has been messed up beyond belief:- 
* I now have 2 lists of folders !!!
* mail highlight is now a solid black bar which masks text completely
* contacts (titles) are black bars = absolutely useless
* calendar display is mostly black blocks: again, absolutely useless

I hoped that the grub boot menu would allow me to go back to a previous version/installation, but they have all gone now.

I haven't been able to find VBox to see if my other OSes are accessible.

I could go on, but I'm sure you get the idea.


As you might imagine, I am more than a little annoyed about this. Is there any way I can get back to a usable system or should I just lick my wounds and limp back to Microsoft?

10.04 worked perfectly well FFS!  Was there really any need to change to this new arty-farty sidebar system at all?  All that seems to have happened is that Ubuntu is now much less usable, less intuitive and more susceptible to problems.

Ubuntu developers should remember the 1st rule of engineering: If it works - don't mess with it!

:mad: :mad: and thrice :mad:

---

### Post by darkod on 2012-05-09
I don't want to insult you in any way, especially since you are in upset mode right now, but you either had some issue in 10.04 LTS too, or you misread everything.

1. 10.04 LTS is NOT unsupported. It has support 3yrs for desktop system, and 5yrs for server. That would put desktop supported until 04.2013. That's the point of being LTS, it is supported one year after the new LTS is released. For the current 12.04 Canonical decided the desktop version to have 5yrs support also, so you wouldn't need to change it until 2017.

2. A direct upgrade from LTS to LTS is NOT offered by the update manager until the first .1 is released. 12.04.1 will be released in July and only then update manager should prompt you to upgrade to the next LTS. This is if you had it set up to report upgrades to LTS only.

Doing 4 upgrades in a row is almost certain to break your system, regardless how much effort developers put into the process. There are simply too many things to go wrong.

Did the upgrade to 12.04 finish completely, or it was stopped or frozen in any way? If it was stopped, you can try finishing off the package configuration.

If it did finish completely, tough luck. Personally I can't troubleshoot this, maybe someone else will be able to.

---

### Post by iMurshaq on 2012-05-09
Have you checked installed drivers?

---

### Post by wkulecz on 2012-05-09
Open a text window (terminal) and do: sudo -i

Then try:
apt-get update
apt-get upgrade

I did a fresh install on a system that happily ran 10.04 and the graphics was messed up, until I did a bunch of updates and a reboot.

System upgrades are an attractive option in theory because its hard to remember all the stuff you've installed, but in practice they rarely go smoothly.

I'm setting up 12.04 now and I'm sure I'll be constantly rediscovering little bits and pieces that are missing as I transition from 10.04 to 12.04 these next few months :(

I've cloned my 10.04 drive and may try an update from the CDROM just for grins later this afternoon.

---

### Post by Timothy Taylor on 2012-05-09
> **wkulecz said:**
> Open a text window (terminal) and do: sudo -i

Then try:
apt-get update
apt-get upgrade

...


I eventually managed to find terminal...  :)

It opens a terminal window, but this is completely blank - no prompt or cursor or anything.
:confused:

> **iMurshaq said:**
> Have you checked installed drivers?

I checked 'Hardware Drivers' which said that none are installed, which is funny - I thought I had nVidia drivers before ???  Looks like these were deleted by the upgrade??  Seems that the graphics / monitor support is trashed..?

> **darkod said:**
> I don't want to insult you in any way, especially since you are in upset mode right now, but you either had some issue in 10.04 LTS too, or you misread everything.
...

Yeah, looks like I misread re 10.04 LTS.
I should take my own advice re "if it works.."
 :facepalm:

---

### Post by enyawix on 2012-05-09
Try running **12.04 **from the live cd. If the problems go away it is a configuration issue. A clean install would clear up configuration issues. Test before you leap into a install. If all else fails I a working on a 10.04 like fork because 12.04 breaks things for me as well.

---

### Post by darkod on 2012-05-09
How about booting the recovery mode entry? Does that work?

If a menu pops up, select Drop to root shell (or similar). That should bring up a command prompt.

You can run those suggested commands in the prompt. Note that if it drops you in a root shell you already have root permissions so the sudo -i is not needed.

Just in case it needs to finish configuring some packages, I would also run:
dpkg --configure -a

Another idea is trying to run the normal mode with nomodeset parameter. It might be missing drivers and that might be distorting windows, etc. If you need help how to add the parameter for a one off boot, ask.

---

### Post by Javelin Dan on 2012-05-09
I sincerely wish you luck in trying to recover your old settings. If you can't, a fresh install is in order. Like you, I didn't care for the new desktop. You have two options: after a fresh install, you can simply log out and click on the option for the "Classic" Ubuntu desktop or do what I did and first install the Lubuntu desktop in synaptic and click on that when you log out. 12.04 really is cool once you make it bend to your will a little, and I've had no major issues so far. What makes this all worthwhile is the new 5-year Long Term Support. Once you go through this pain, you won't have to again for 5 long years as long as you keep updating. That's like 35 years in computer years! Good luck.

---

### Post by QIII on 2012-05-09
If you drop straight to root, you will not have networking and you will probably be mounted read-only, so the commands will give you a permissions error.

First enable networking in the recovery menu.  That will get you a connection and read-write mount.  Then go to root with networking.

---

### Post by Chuck Crisler on 2012-05-09
I have installed v. 12.04 on 2 systems and both had the same problem described in the initial message of the post. In both installations, I re-built the partition table and completely installed the OS. After re-starting, I logged in, the background briefly displayed and then the screen went black with only my mouse cursor showing. Sometimes I have been able to get the background to show and I have crashed compiz twice (whatever that is), once on each system. Note: nothing else is visible on the screen - NOTHING. Sometimes with clicking I have gotten some dialogs to display, but nothing that would let me make the system workable. At the moment I am trying to do yet another install, this time with 11.04. If that fails I will move on to fedora, which I have used at home for over 3 years. Frankly, I can't see how a professional organization can release something that behaves like this directly 'out of the box'.

---

### Post by darkod on 2012-05-09
> **QIII said:**
> If you drop straight to root, you will not have networking and you will probably be mounted read-only, so the commands will give you a permissions error.

First enable networking in the recovery menu.  That will get you a connection and read-write mount.  Then go to root with networking.

Thanks, didn't know that.

---

### Post by darkod on 2012-05-09
> **Chuck Crisler said:**
> I have installed v. 12.04 on 2 systems and both had the same problem described in the initial message of the post. In both installations, I re-built the partition table and completely installed the OS. After re-starting, I logged in, the background briefly displayed and then the screen went black with only my mouse cursor showing. Sometimes I have been able to get the background to show and I have crashed compiz twice (whatever that is), once on each system. Note: nothing else is visible on the screen - NOTHING. Sometimes with clicking I have gotten some dialogs to display, but nothing that would let me make the system workable. At the moment I am trying to do yet another install, this time with 11.04. If that fails I will move on to fedora, which I have used at home for over 3 years. Frankly, I can't see how a professional organization can release something that behaves like this directly 'out of the box'.

Did you try if you can run it in live mode on those machines first?

---

### Post by Timothy Taylor on 2012-05-09
I had to boot windoze to check the ID of my graphics card = ATI radeon HD5970.
I downloaded a driver from the ATI (AMD) website, but this needs to be run from terminal, so that wouldn't work.  I found "ATI binary X.Org driver" in Ubuntu Software Centre, which I installed and which has improved things slightly:
* The clashing text on the top menu-bar has gone and the bar was even solid for a few seconds!
* The "workspaces" button on the sidebar now has an icon!

I have found VirtualBox - lurking at the bottom of the "System" section of the (Ubuntu??) menu / top button pop-out.  
This is possibly the most monumentally retarded "improvement" to an interface design I have ever had the misfortune to struggle with:
[LIST=1]
[*]Click on the "Ubuntu" button to open the menu. This displays recently used Apps, Files and Downloads.
[*]Eventually discover that the little "birthday candles" icon at the bottom of this window switches to "search applications" view...
[*]Click on "System" to open the system section
[*]Click on the link to see more than just the first 4 entries in the system menu
[*]Scroll down the list until you find Oracle VM VirtualBox Manager and click it
[/LIST]

Compare with the old way:
[LIST=1]
[*]Click to open the Applications menu
[*]Click on System Tools to open the sub-menu
[*]Click on Oracle VM VirtualBox Manager
[/LIST]

Who designs this crap?  And who allows it to be unleashed on hapless users?  They should be taken out and shot.

The ATI driver has not sorted the blank Terminal issue, so trying to reach a working terminal from recovery menu is the next thing to try.

Thanks for your help folks!

I still can't believe what a ridiculous performance this "upgrade" has been.  Wasted a whole day at least.  I may yet have to reinstall 10.04 LTS on my system.  

Does anyone know if it's possible to preserve my home directory and VirtualBox VMs when doing a reinstall from CD?

---

### Post by Timothy Taylor on 2012-05-09
> **Chuck Crisler said:**
> ...
I can't see how a professional organization can release something that behaves like this directly 'out of the box'.

Yeah. 
I think Dell need to think very carefully before bundling this rubbish with their new machines.

---

### Post by QIII on 2012-05-09
@Chuck Crisler 

It is regrettable that you have had problems and we'd love to help you sort them out.

However, your experience is far from the norm.  This works for millions of people.  Although it is tempting to assume that your experience reflects that of everyone else, it is an invalid conclusion

Even the fact that perhaps 300 people come to this forum with q particular issue does not indicate that there is necessarily a systemic problem.  People come to help forums when things go wrong.  They don't come to forums to complain when things go right.  That is called referral bias, which renders conclusions drawn invalid.

Something went wrong for you and you are justified in your frustration.

Just remember that I say the same thing on Fedora forums to those having issues there.

---

### Post by darkod on 2012-05-09
1. Put the driver on a usb and you can install it in recovery mode. If you need help mounting the usb from terminal, ask. It should be like:
```
cat /proc/partitions (it will show all disks/partitions)
mount -t vfat /dev/sdb1 /mnt (mount a FAT32 usb stick from root prompt)
cp /mnt/amd* /home/username
cd /home/username
```

Then simply run it depending how it needs to be executed.

If you do all that from terminal in recovery mode (root shell) you don't need sudo in front of mount, otherwise you would.

2. As for finding software, you can click the Ubuntu logo to open the dashboard, or simply hit the Windows logo key on the keyboard. It automatically open into a search line at the top of the dashboard. Start typing the program you are after and it will show below. Fast and easy.

---

### Post by Dubslow on 2012-05-09
> **Timothy Taylor said:**
> I had to boot windoze to check the ID of my graphics card = ATI radeon HD5970.
I downloaded a driver from the ATI (AMD) website, but this needs to be run from terminal, so that wouldn't work.  I found "ATI binary X.Org driver" in Ubuntu Software Centre, which I installed and which has improved things slightly:
* The clashing text on the top menu-bar has gone and the bar was even solid for a few seconds!
* The "workspaces" button on the sidebar now has an icon!

I have found VirtualBox - lurking at the bottom of the "System" section of the (Ubuntu??) menu / top button pop-out.  
This is possibly the most monumentally retarded "improvement" to an interface design I have ever had the misfortune to struggle with:
[LIST=1]
[*]Click on the "Ubuntu" button to open the menu. This displays recently used Apps, Files and Downloads.
[*]Eventually discover that the little "birthday candles" icon at the bottom of this window switches to "search applications" view...
[*]Click on "System" to open the system section
[*]Click on the link to see more than just the first 4 entries in the system menu
[*]Scroll down the list until you find Oracle VM VirtualBox Manager and click it
[/LIST]

Compare with the old way:
[LIST=1]
[*]Click to open the Applications menu
[*]Click on System Tools to open the sub-menu
[*]Click on Oracle VM VirtualBox Manager
[/LIST]

Who designs this crap?  And who allows it to be unleashed on hapless users?  They should be taken out and shot.

The ATI driver has not sorted the blank Terminal issue, so trying to reach a working terminal from recovery menu is the next thing to try.

Thanks for your help folks!

I still can't believe what a ridiculous performance this "upgrade" has been.  Wasted a whole day at least.  I may yet have to reinstall 10.04 LTS on my system.  

Does anyone know if it's possible to preserve my home directory and VirtualBox VMs when doing a reinstall from CD?An alternative to booting into recovery mode is hitting Ctrl+Alt+F1 (or any F up to F6) which should bring you to an actual shell (as opposed to a terminal mimicking a shell in Gnome/Unity). There you can log in, do "sudo -i", and then
"apt-get update" and "apt-get upgrade" as noted before. Additionally, I suggest trying something like "apt-get upgrade -f" in between the first two; the extra option focuses apt-get on fixing broken packages.

As a last resort, if you have an extra flash drive or external floating around, you can boot to the live CD (before installing) and copy the folders you want onto the flash drive/external.

---

### Post by Timothy Taylor on 2012-05-09
I tried the apt-get commands from the root terminal.
No joy I'm afraid.

I will try saving my files and reinstalling 10.04 LTS from my USB stick tomorrow.  I'm falling asleep now.

I have Is there any way I can preserve my VirtualBox VMs? Reinstall wants to re-format my hard drive and I have important stuff in the VMs I need to keep.

What a day...
:(

---

### Post by darkod on 2012-05-10
I haven't used VB much, but I believe copying whole of the VB folder(s) will work. Try googling for backing up the VMs and attaching them to the new VB install later.

---

### Post by Chuck Crisler on 2012-05-10
Very interesting update. No, I didn't run the live CD version because I need a system that I can begin working on. It would be difficult for me to configure a live CD version to do what I need, though I know it can be done. What I need will require at least one and probably multiple re-boots to configure. I am putting together a bridge for impairment testing (brctl, netem, token bucket, etc). Now, for the interesting new development. First, it looks like the 12.04 *MAY* be working properly (and it does look nice). I put a CD with 11.04 in the drive, wondering how I could gracefully re-boot the system when I can't see any menus. It displayed a screen that allowed me to logout, but there was another option (sorry, I don't remember it) but ultimately a dialog was displayed that allowed me to select between 2 options: a) ubuntu, b) ubuntu-2D (????????) I don't have a clue what that is, but selected it. Now, the toolbar, left side slide-out menu, etc. all display properly. My guess is (someone please correct me) that my old hardware doesn't support some new display mode which caused my problem. If that is the case, then SHAME on the ubuntu developers for not properly detecting that during installation and falling back to a workable mode. It is ridiculous that a system fails immediately after a smooth installation in a way that you absolutely cannot recover from.

---

### Post by darkod on 2012-05-10
> **Chuck Crisler said:**
> Very interesting update. No, I didn't run the live CD version because I need a system that I can begin working on. It would be difficult for me to configure a live CD version to do what I need, though I know it can be done. What I need will require at least one and probably multiple re-boots to configure. I am putting together a bridge for impairment testing (brctl, netem, token bucket, etc). Now, for the interesting new development. First, it looks like the 12.04 *MAY* be working properly (and it does look nice). I put a CD with 11.04 in the drive, wondering how I could gracefully re-boot the system when I can't see any menus. It displayed a screen that allowed me to logout, but there was another option (sorry, I don't remember it) but ultimately a dialog was displayed that allowed me to select between 2 options: a) ubuntu, b) ubuntu-2D (????????) I don't have a clue what that is, but selected it. Now, the toolbar, left side slide-out menu, etc. all display properly. My guess is (someone please correct me) that my old hardware doesn't support some new display mode which caused my problem. If that is the case, then SHAME on the ubuntu developers for not properly detecting that during installation and falling back to a workable mode. It is ridiculous that a system fails immediately after a smooth installation in a way that you absolutely cannot recover from.

The question was about trying it, not using live mode as your main system. That would be ridiculous of course.

The point is that with ubuntu you can at least load live mode and see if there are any issues with that version on your machine. If there is, don't upgrade until you resolve them and decide if you want to use the new version at all.
You hit the upgrade button first and then complain about issues you could have easily seen in live mode. Most probably it would have shown that unity is not working on your machine either because of old hardware or driver that needs to be updated.

Bottom line, test first, upgrade later.

Now, if you think unity is the only thing holding you back, or if you simply don't want to use it, you can install gnome classic on 12.04 too:
[http://www.ubuntugeek.com/how-to-install-classic-gnome-desktop-in-ubuntu-12-04-precise.html](http://www.ubuntugeek.com/how-to-install-classic-gnome-desktop-in-ubuntu-12-04-precise.html)

Once you install it, on the login page you will have the gnome classic option when you click the ubuntu logo to select what type of session you want to load.

---

### Post by Chuck Crisler on 2012-05-10
No, you miss the point. Yes, perhaps I could have tested *PART* of Ubuntu, but it would have been time consuming and challenging to test a 12.04 Live CD *for the application that I need it for*, which is the only real test, which I have still not yet completed. I *ASSUME* that netem et.al. will work, but I *ASSUMED* that a fresh install would work and I was 'misguided' (not quite wrong) about that. And you are wrong about using a Live CD - it is not as ridiculous as you might think. It actually works fairly well, especially for something like a dedicated bridge. I used it several years ago for just that purpose. It just isn't as nice as a real install. With a real install I can more easily setup scripts to configure the network impairment configurations that I want. This system will then be used by QA for advanced testing, not by me, so it has to be easy to use and reliable.

---

### Post by Jack the R on 2012-05-10
> **darkod said:**
> 
The point is that with ubuntu you can at least load live mode and see if there are any issues with that version on your machine. 

I wouldn't bother with live mode either, it's next to worthless.  I'm not saying it's totally worthless, but it doesn't 100% tell you if a new release is good or not.  It didn't tell me 11.10 would develop the compiz bug after a couple weeks of use.  It didn't tell me Mandriva would fail to install in the last stage of the install process (there's a bug in the installer, I forget what it is having moved on).  

The only way to do this - new install, new hard drive.  When the new install has totally proven itself out over months of use, then you can stick the old hard drive into an external case and use it for storage.  Till then, keep it as a backup, because you may need it. 

I've got a stack of install cds an inch and a half high which failed to work properly across any of three different machines.  Anyone who thinks Linux doesn't have a problem, either has mad skillz beyond what the average user should be expected to have (we can't all be the Stig of computer use), or they're kidding themselves.  I've tried Ubuntu, Kubuntu, and Mint, and all three have resource usage bugs - be it in compiz, akonadi, nepomuk, strigi, etc.  I've come to take it for granted that any distro is going to be crap on install and take days to get sorted out, if I'm lucky enough to connect to someone who knows how to fix the problem.  No wonder Linux never succeeded on the desktop.  You can't dump not-ready code on the average computer user and expect them to fix it or uninstall it.  They'll go running back to Windows and be lost to Open Source forever.

---

### Post by QIII on 2012-05-10
> **Jack the R said:**
> You can't dump not-ready code on the average computer user and expect them to fix it or uninstall it.

... which is why, of course, there is not a single Windows support forum to be found anywhere ...

No OS or software package is entirely free of bugs or frustrations.  If we who create software tried to produce things like that, we'd never release anything.  And I'd be selling pencils on the street corner to feed myself.

The fact is that people are *used to *the quirks of Windows and don't see them as "problems".  They have grown up with windows for almost 30 years now.

For those of us who were using Unix long before Windows, and Linux for 15 years or so, Linux quirks seems quite familiar.

The difference is the simple historical accident that Windows and Apple bumped heads long ago and Windows gained market share more quickly than Apple.  People expect a PC to be "Windows".  In their minds, "PC" and "Windows" are indistinguishable in interchangeable.

---

### Post by Timothy Taylor on 2012-05-10
Just to say that I've had to do a clean reinstall of 10.04 LTS, which is progressing nicely.

I have browser & bookmarks, Skype, UPS monitor and a few other bits n bobs set up now.

Does anyone know how Evolution settings are stored?  Is this in my home directory (which I've backed up) and is it simply a matter of copying the files back to restore my folders, email accounts, etc.?

Similarly, my VirtualBox VM files are backed up.  Presumably I can import these back into VirtualBox without too much grief?

Should have a fully recovered system by the weekend...
:)

---

### Post by Dubslow on 2012-05-11
> **Timothy Taylor said:**
> Just to say that I've had to do a clean reinstall of 10.04 LTS, which is progressing nicely.

I have browser & bookmarks, Skype, UPS monitor and a few other bits n bobs set up now.

Does anyone know how Evolution settings are stored?  Is this in my home directory (which I've backed up) and is it simply a matter of copying the files back to restore my folders, email accounts, etc.?

Similarly, my VirtualBox VM files are backed up.  Presumably I can import these back into VirtualBox without too much grief?

Should have a fully recovered system by the weekend...
:)
I've never used Evolution, but it's a decent bet the data's stored in a home folder named .evolution. Select "hidden files" in Nautilus, or do "ls -a" in your home folder. I don't know about VM, but try just copying your old folder over the new equivalent.

---

### Post by That 70s Show on 2012-05-13
Same thing. I upgraded through all of the versions by using the suggested routes in the Ubuntu Software center. The side bar access doesn't do it for me either. MANY "crash reports" sent in while running 12.04. Access to certain files and the general "feel" of 12.04 just didn't make me comfortable. I backed up Evolution (email) and burned everything to CD-R's before using G-Parted to wipe the hard drive and start all over again. I re-installed Ubuntu 10.04 but the "evolution backup.tar.gz" file that was extracted from the email program that came with 12.04 doesn't seem to be compatible with the 10.04 restore. Good thing I had all emails backed up elsewhere! Once the bugs are worked out, I'm sure 12.04 LTS will be fine even though it will take some getting use to until then, long live 10.04 LTS! (Correct me if I'm wrong but, I believe LTS stands for "Life Time Service"... Support for the LTS versions will continue so you shouldn't have to upgrade if you don't want to.)

---

### Post by darkod on 2012-05-13
> **That 70s Show said:**
> Same thing. I upgraded through all of the versions by using the suggested routes in the Ubuntu Software center. The side bar access doesn't do it for me either. MANY "crash reports" sent in while running 12.04. Access to certain files and the general "feel" of 12.04 just didn't make me comfortable. I backed up Evolution (email) and burned everything to CD-R's before using G-Parted to wipe the hard drive and start all over again. I re-installed Ubuntu 10.04 but the "evolution backup.tar.gz" file that was extracted from the email program that came with 12.04 doesn't seem to be compatible with the 10.04 restore. Good thing I had all emails backed up elsewhere! Once the bugs are worked out, I'm sure 12.04 LTS will be fine even though it will take some getting use to until then, long live 10.04 LTS! (Correct me if I'm wrong but, I believe LTS stands for "Life Time Service"... Support for the LTS versions will continue so you shouldn't have to upgrade if you don't want to.)

Since you were doing a clean install you could have tried 12.04. Many times the issues happening after a number of upgrades (depending how many in a row) are because of so many upgrades. A clean install might have not had those issues.

If the "access, look, feel" complain is about the Unity interface, you can install gnome classic which gives you the same interface as the previous versions.

---

### Post by That 70s Show on 2012-05-13
As a side-note: Evolution can be backed up simply by clicking "File" and then, "Backup settings" from the Evolution task bar. It has worked for me on many occasions, with the exception of this latest adventure... Backing up Evolution from 12.04 and Restoring it to 10.04. I've been Windows-Free for close to 6 years and will not look back! I can rest assured that the Ubuntu developers are doing everything they can to work the bugs out of the Ubuntu OSs. Hats off to the Ubuntu Linux developers, volunteers, geeks, nerds, and gurus! UBUNTU is the best! (Even after things don't go exactly as planned...) :)

---

### Post by That 70s Show on 2012-05-13
Thanks for the info about Gnome classic... I'll have to give it a shot! LONG LIVE UBUNTU!

---

### Post by Bobi86 on 2012-05-13
I have recently upgraded to ubuntu 12.04 from 10.04. I face the below issues  after upgrade.

1) I was unable to connect to the wifi i.e: there is no wireless network detector showing up.
i have reinstalled the Broadcom STA wireless driver available in the systems tools -> additional drivers. But even then it doesn't work.

2) I have difficulty in viewing the installed applications. can i change the menu navigation as it was in the previous 10.04? or pls let me know how can i add the places, application, system administration etc in the desktop menu.

Thanks in advance.
Regards,
Balaji

---

### Post by darkod on 2012-05-13
> **Bobi86 said:**
> I have recently upgraded to ubuntu 12.04 from 10.04. I face the below issues  after upgrade.

1) I was unable to connect to the wifi i.e: there is no wireless network detector showing up.
i have reinstalled the Broadcom STA wireless driver available in the systems tools -> additional drivers. But even then it doesn't work.

2) I have difficulty in viewing the installed applications. can i change the menu navigation as it was in the previous 10.04? or pls let me know how can i add the places, application, system administration etc in the desktop menu.

Thanks in advance.
Regards,
Balaji

It was already mentioned you get the older style menus with gnome classic.
[http://www.ubuntugeek.com/how-to-install-classic-gnome-desktop-in-ubuntu-12-04-precise.html](http://www.ubuntugeek.com/how-to-install-classic-gnome-desktop-in-ubuntu-12-04-precise.html)

As for the wireless, maybe another module is conflicting with the card. You may receive better help in the Networking section. Also, try googling your card model and ubuntu 12.04.

---

### Post by Bobi86 on 2012-05-13
Thank you very much for you post.
The below fixed my wifi issue.
sudo apt-get install linux-firmware-nonfree sudo modprobe -r b43 sudo modprobe b43

---

### Post by Bobi86 on 2012-05-20
hi all,
      i need to run this command "sudo modprobe b43" every time i login  to the computer for the computer to show the presence of wireless  adapter in the network manager. 
some kindly help me fix this. i do not want to run this command again and again when i login to my system.
Thanks in advance.

Regards,
Balaji R.

---

### Post by venom104 on 2012-05-20
> **Bobi86 said:**
> hi all,
      i need to run this command "sudo modprobe b43" every time i login  to the computer for the computer to show the presence of wireless  adapter in the network manager. 
some kindly help me fix this. i do not want to run this command again and again when i login to my system.
Thanks in advance.

Regards,
Balaji R.


I can't be sure about ubuntu 12.04, but the other ubuntu's (and almost all debian derivatives) have a file you can edit which loads modules at boot time. Type sudo gedit /etc/modules and add the line b43, and save the file. See if that works.

---

### Post by darkod on 2012-05-20
> **Bobi86 said:**
> hi all,
      i need to run this command "sudo modprobe b43" every time i login  to the computer for the computer to show the presence of wireless  adapter in the network manager. 
some kindly help me fix this. i do not want to run this command again and again when i login to my system.
Thanks in advance.

Regards,
Balaji R.

If I am not mistaken, open /etc/rc.local with the text editor and add modprobe b43 at the end. That file is executed on every boot and it will load the module. You need to open it with sudo right for editing because it's system file:

gksu gedit /etc/rc.local

You don't need the sudo word inside the file, only the modprobe b43 part.

---

### Post by darkod on 2012-05-20
> **venom104 said:**
> I can't be sure about ubuntu 12.04, but the other ubuntu's (and almost all debian derivatives) have a file you can edit which loads modules at boot time. Type sudo gedit /etc/modules and add the line b43, and save the file. See if that works.

Actually this is a better approach. The modules you want to load should be put here.

---

### Post by kd5mkv on 2012-07-25
I recently made a bad decision and upgraded from 10.04 to 12.04.
I lost everything! It bricked my computer, what is the secret to Ubuntu
forums? I have googled a half dozen questions and cannot find any solutions to Precise fails on install, I went back to clean install of 10.04.
  Hope the bugs are worked out by 2013.

---

