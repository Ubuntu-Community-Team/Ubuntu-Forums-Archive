---
title: "Upgrading from Breazy to Dapper - question"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by SreckoMicic on 2006-06-01
Here is the situation, I want to upgrade to Dapper, and I saw that it can be done with <gksudo "update-manger - d"> command. Update manager then report that there is upgrade available. Is this ok approach or there is any better, and will my old programs work on this upgraded version?
Thanks.

---

### Post by zAo on 2006-06-01
This should do.

---

### Post by Hanj on 2006-06-01
Yes, that should work. Remeber that you have to change your /etc/apt/sources.list file so that it says "dapper" everywhere where it now says "breezy" first. Also, you may want to back up important data, as there's sometimes problems upgrading with this method (at least I've had some troubles with it).

---

### Post by SreckoMicic on 2006-06-01
Oh and another question, is this official release or still release candidate.

---

### Post by bluenova on 2006-06-01
[QUOTE=Hanj]Remeber that you have to change your /etc/apt/sources.list file so that it says "dapper" everywhere where it now says "breezy" first.[/QUOTE]
There is no need to do this, when using the updated package manager.

---

### Post by Spleenie on 2006-06-01
[QUOTE=bluenova]There is no need to do this, when using the updated package manager.[/QUOTE]

I use this command and it doesn't seem to come up with a "new ubuntu release" button or prompt, it simply tells me I am up to date

I am currently a Breezy user who is hoping to upgrade to Dapper using this process. Is it because I am using Australian repositories?

Cheers

---

### Post by SreckoMicic on 2006-06-01
I tried with this command and when in process of downloading manager stops and shows me this message, any ideas ?


Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz) Sub-process bzip2 returned an error code (2)

---

### Post by bluenova on 2006-06-01
[quote=Spleenie]I use this command and it doesn't seem to come up with a "new ubuntu release" button or prompt, it simply tells me I am up to date

I am currently a Breezy user who is hoping to upgrade to Dapper using this process. Is it because I am using Australian repositories?

Cheers[/quote]
I think you just need to be patient, while the mirrors are all updated.

---

### Post by pellgarlic on 2006-06-01
request permission to hijack this thread slightly! 

i also have a question about ways of upgrading from breezy to dapper, but the method mentioned in post #1 is likely unsuitable for me, as the computer on which i have ubuntu installed only has dial-up internet access - i do all my large-scale downloading at work, where i have broadband access, then burn to cd or dvd, and take it home.

i know that it is possible to use the breezy install cd as a repository for installing certain extra packages (build-essential for example), so i don't suppose there's any chance i could use the dapper cd as a repository to upgrade my breezy in the same way as if i used the online repositories? i'm gonna guess the answer to this question is "DBFS" (Don't Be *Freakin'*Stupid) but i just thought i'd ask.

in lieu of this answer, what other options do i have, rather than having to do a fresh install from the dapper install cd, then reinstalling all the programs i had already installed in breezy? as my /home is on a separate partition, that stuff will be safe, and a thread i read about making a cd repository of your downloaded debs will make things slightly easier, but it would be easier still if i could go the upgrade route, rather than the fresh install/reinstall all programs route.

---

### Post by SreckoMicic on 2006-06-01
Well I don't know is there posibility to upgrade from Ubuntu CD ??
I think that might be solution, but just think didn't try :???:

By the way, I installed Daper with above solutions, have slight problems with PCMCIA services and ATI card but these are known problems so easily found solutions. VERY GOOD.

---

### Post by elfgoh on 2006-06-01
According to Dapper Upgrade notes:
[https://wiki.ubuntu.com/DapperUpgrades?action=show&redirect=DapperUpgradeNotes](https://wiki.ubuntu.com/DapperUpgrades?action=show&redirect=DapperUpgradeNotes)

[Quote]
There are a few ways you can get Dapper: 

1. Upgrading with the Update Manager 

2. Upgrading by changing sources and the command line 

3. Downloading an ISO and making an installation CD.
[Unquote]

So using a Dapper CD shld be possible. But it's nt clear how to get it done. Perhaps add the cdrom in synaptic? But I haven't tried this, so do it at your own risk!

---

### Post by pellgarlic on 2006-06-01
hi sreckomicic  - although i suggested the possibility of using the cd to perform an upgrade, i don't think it would actually work, because of the way the data is stored on the cd - the .deb files required to install the programs are unlikely to be included on the disk, as they will "already be installed". i just thought there was a slim possibility that they would also be included in .deb form.

but yeah, guess the best thing to do is try and see... i finish work in about 45 mins, so i'll test it out when i get home. suppose the worst that can happen is i end up with a few updated programs for my breezy installation, and i have to install dapper from scratch anyway!

can i ask, sreckomicic, do you have broadband access, or dial-up? if you have dial-up, can you describe here how long it takes to perform the upgrade? (once you have got access the repositories of course). actually, it would be interesting information even if you have broadband - i can work out roughly how long it would take for me by your experience.

---

### Post by Nicksha on 2006-06-01
You CAN upgrade using Ubuntu CD, but you have to download "Alternate install CD", not the "Desktop CD".

---

### Post by Uta on 2006-06-01
I have been following this thread and I have a question concerning the source.list
One person said you don't have to change the list, another said you did?
Can someone point me to the new Dapper source.list or paste one in this thread.
Also a misspelling in the first post, gksudo "update-manger - d"
should be. gksudo "update-manager - d"

Thanks!

---

### Post by pellgarlic on 2006-06-01
[QUOTE=Nicksha]You CAN upgrade using Ubuntu CD, but you have to download "Alternate install CD", not the "Desktop CD".[/QUOTE]

woah, stop the press! that's what i'm looking for! can i ask where you got this info from? have you tried it yourself, or have you read it somewhere reputable? this would be the perfect solution for me, and no doubt a lot of others in a similar predicament...

also, how would one go about doing the upgrade this way? is it like i suggested earlier - adding the cd as a repository, then using apt-get or synaptic to upgrade everything... or would it work kind of like the windows way of upgrading - an "over-installation" which replaces relevant system files but keeps settings and preferences intact?

---

### Post by Nicksha on 2006-06-01
It's actually right where everyone can see it: on the download page. It seems, though, that no one reads the descriptions of the CD's, which says:

> Alternate install CD

The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * creating pre-configured OEM systems;
    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installs on systems with less than about 192MB of RAM. 


(notice bullet No.3)

Unfortunately, I find myself included in that "skip-to-the-links" group. I downloaded Desktop CD, because they said that it's the preffered method of installation. So, now, I'm downloading the other ISO...

About the upgrade, I think that you were right, and that you only need to insert the disc, and you'll be asked if you wish to start the package manager. That will add the CD to the other repositories, and then the new packages will be detected, and you can do the upgrade.

---

### Post by Nicksha on 2006-06-01
Sorry, double post... Everything is just so slow...

---

### Post by Uta on 2006-06-01
I answered my own question about the source.list .
[http://www.psychocats.net/ubuntu/dapper.php](http://www.psychocats.net/ubuntu/dapper.php)

Is it possible to do this with my established wireless connect or should I connect with an ethernet cable? Thanks.

---

### Post by Nicksha on 2006-06-01
You shouldn't have to change the list. The new update-manager changes it for you when it detects that the new release is available, and when you confirm that you want to upgrade. It changes the official repos, and disables the third-party ones, then it downloads the package lists, and after calculating which packages should be upgraded, removed on installed, asks you if you still want to upgrade. That's the last confirmation, after that it does the upgrade.

---

### Post by pellgarlic on 2006-06-01
i assume that upgrading to dapper this way (i.e. using the "alternate" cd) would only upgrade the programs installed, and i would have to compile and apply the new 2.6.15 kernel myself? i can't see how synaptic could possibly do this, so is there maybe another way to use the alternate cd to upgrade? or will i just have to do the kernel compile manually?

[edit]: ok, it appears my impression was wrong - you *can* upgrade your kernel through synaptic (or apt-get), although i still don't know if updating from the dapper cd will do this or not. i guess it probably should. only one way to find out... see y'all when i emerge from the dark side of the moon...

---

### Post by GQed76 on 2006-06-01
im getting the same fetch errors. 7pm June 1st, EST

---

### Post by pellgarlic on 2006-06-01
ok, i'm thru the other side, and relatively unscathed, but not entirely...

it seems to have worked ok in general - i now have a 2.6.15 kernel to boot from, the "help" menu describes ubuntu 6.06, there are some obvious changes to the menus and extra themes etc. 

the most obvious change was the slightly scary-looking screen that appeared after rebooting, as apparently dapper doesn't like the drivers i had installed for my nvidia graphics card. will try reinstalling them. luckily i already knew to change the "nvidia" value in my /etc/X11/xorg.conf file to "nv" to allow X to function.

i had to reiinstall my "winmodem" before i could get online - it couldn't detect my modem at all. 

i have no sound at all, although it worked "out of the box" with breezy. this is quite disappointing, as one of my most important uses of my computer is for audio recording and mixing. :( 

in the "system > preferences" menu, there are 2 entries for "screensaver", the first of which complains "the XScreenSaver daemon doesn't seem to be running on display "0:0". Launch it now?" when i click on it. (this is presumably the breezy version inadvertently left over).

to be honest, i think i'd rather go through the "reinstall ubuntu and all programs" process than try to figure out all these issues, and whatever other issues crop up beyond these (which became apparent within 15 minutes of use). 

i don't know if these issues are a result of the way i performed the upgrade - perhaps i missed some important step, or perhaps they are issues a more experienced linux user would have expected and been prepared for, but i was hoping for a more fluid transition into dapper-land!

the most important thing is: i am still totally hooked on ubuntu, and as i have experienced magnitudes less of problems with ubuntu than i ever suffered with windows, and also because i know my /home is safe, and it will be a relatively easy process to reinstall my programs from my home-made cd repository, i have no real complaint to make, other than "it would have been cool if it had worked better".

oh well, at least i've already downloaded the desktop installation cd...

---

### Post by heffo_j on 2006-06-01
You can use a cd to upgrade through Synatpic. I can't recall the menu (I'm at work on windows) but there is a drop down menu that allows a cd to be recognised as the source of the upgrade. I still think you may need to change your repositories to Dapper though.

Regards
John

---

### Post by confused57 on 2006-06-01
[QUOTE=heffo_j]You can use a cd to upgrade through Synatpic. I can't recall the menu (I'm at work on windows) but there is a drop down menu that allows a cd to be recognised as the source of the upgrade. I still think you may need to change your repositories to Dapper though.

Regards
John[/QUOTE]

Read aysiu's instructions near the bottom of the first page:

[http://www.ubuntuforums.org/showthread.php?t=179477](http://www.ubuntuforums.org/showthread.php?t=179477)

---

### Post by pellgarlic on 2006-06-02
[QUOTE=confused57]Read aysiu's instructions near the bottom of the first page:

[http://www.ubuntuforums.org/showthread.php?t=179477](http://www.ubuntuforums.org/showthread.php?t=179477)[/QUOTE]

as far as i understand the instructions from aysiu on that thread, i think i did it that way - i booted into breezy, then inserted the dapper "alternate" cd (which i understand to be the "text-based" installer cd). 

breezy recognised the disc, and told me i could now start the package manager, and even provided a button to do so on that very dialog. 

so i clicked the "start package manager" button, synaptic started, and i did a "mark all upgrades" (searching for a "dist-upgrade" or "ubuntu-desktop" upgrade provided no results, so i assumed this was most likely the correct thing to do), then clicked on "apply". after accepting the listed uninstalls, upgrades and new installs, it took about 45 minutes to perform the upgrade.

as i stated in my previous post, the end result was not quite perfect, but i suspect the problem is not with the upgrade procedure itself, but rather with the particular idiosyncracies of my computer - e.g. i had manually installed the newest (v.87.56) drivers for my nvidia graphics card, my winmodem drivers also had to be installed manually. 

i have ended up doing a clean reinstall from the "desktop" cd, (i'm just a pernickety kind of guy - i like having a clean base to build upon) altho i have yet to reinstall the aforementioned drivers. 

when trying to reinstall the programs i had included in my "home-made" cd repository, i found a lot of the packages would not install because of "unresolved dependencies", (particularly with the gstreamer plugins, meaning my sound doesn't work properly yet) which i assume is due to the fact that different versions of other programs have been installed with dapper than were installed with breezy. perhaps this accounts for some of the probelms i encountered with the "upgrade" method.

---

### Post by MoT on 2006-06-02
Hello all, 
this is my first post on this forum, so don't be to harsh on me ;-)

As the "update manager"-way to upgrade Breezy to Dapper isn't working yet, I'm editing my sources.list. 
I am changing everything from Breezy to Dapper, but should i also change the first line (deb cdrom...) or only the other (online) repositories? 

Also, is it possible that the .be (for Belgium) repositories aren't updated yet, as I get several errors about repo's not being found when i open synaptic after changing my sources.list?

Then yet another question: 
I connect to my ubuntu machine via vnc, will the settings for vncserver be kept when I upgrade, or will have to connect to the machine physically after upgrading? 
Settings for Nvidia driver should be kept I think?

---

### Post by pellgarlic on 2006-06-02
hi mot - welcome to the forum!

when changing your sources.list, you don't need to change the line that refers to the cdrom, only the online repos, as you correctly guessed. (point-of-interest: the "cdrom" line refers to the ubuntu install cd, which can be used as a source of some packages, for example: build-essential, which is necessary to be able to compile nvidia drivers, some win-modem drivers, and so on)

as for the belgium repositories, i read something here: [http://www.ubuntuforums.org/showthread.php?t=133803&page=3](http://www.ubuntuforums.org/showthread.php?t=133803&page=3) (post #24) which makes me think it shouldn't make a difference - it seems that the "localized" repos (e.g. [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) or [http://be.archives.ubuntu.com/ubuntu](http://be.archives.ubuntu.com/ubuntu)) all point to the straight-forward "archive" ones (i.e. [http://archive.ubuntu.com/ubuntu)](http://archive.ubuntu.com/ubuntu)), although some people reportedly have better speeds when using just "archive" rather than "xx.archive".                

you should also double-check that there are no "typos" in your sources.list (even if you "copied and pasted" from somewhere, it's always worth double-checking). you could also try copying the part of the line that is like "[http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu)" into the address bar of your browser (or just click on that link!) for each repo that you get an error for, and see if you can look into the directories that way. if not, perhaps you are just experiencing the reults of increased usage of the repos as lots of people try to upgrade to dapper!

it is also worth considering the method referred to above, using the "alternate" ubunutu install cd as an upgrade source - it should technically provide the same packages as can be found in the repos, although i am no expert when it comes to this, and my own exerience of this method was a little short of perfect. but this is likely connected to problems other than the upgrade procedure itself.

as for your question regarding vnc, i don't know. perhaps someone who is familiar with it can answer that question for you.

your nvidia driver is another matter - if you are using the default "nv" driver that ubuntu uses when you first install, you'll be okay. if you manually installed the "nvidia" drivers, (which you may have done in order to get 3d support - i had to manually install them to get opengl apps to work) you will have to reinstall them after you have finished upgrading.

---

### Post by MoT on 2006-06-04
Pellgarlic, thanks for the help. 
I did the upgrade yesterday, and everything went fine. 
This is what I did: 
- re-added the repositories using synaptic
- update manager told me there was an upgrade available
- upgrade was completed without any errors

After this, my (self-installed) nvidia driver was still working, as was my vnc server. 
All in all, a successful upgrade without any issues. Seems ubuntu's got it worked out pretty well!

---

### Post by pellgarlic on 2006-06-05
cool, i'm glad it worked well for you :)

it's strange - when i tried upgrading using the "aternate" cd, i never got the "an upgrade is available" message, so i just used the "select all upgrades" option in synaptic... wonder if that's why my attempt didn't work perfectly... 

oh well, i'm doing a clean install of dapper tonight anyway - gives me an excuse to make changes to my partitions (specifically to abandon my "dead" windows partition, and transfer all my files from the ntfs "my documents" partition to a linux partition)

[edit]: just found out a section has been added to wiki for using "alternate" cd for upgrading: [https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)

---

### Post by elfgoh on 2006-06-08
[QUOTE=pellgarlic]

[edit]: just found out a section has been added to wiki for using "alternate" cd for upgrading: [https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)[/QUOTE]

Hey the last time checked the wiki last week, the how to had no detauls documenting the use of an alternate cd for upgrading. 

Tks to those who have put in the effort to update the wiki! Let's keep the community effort gg....

Gotta find some time to upgrade soon =)

---

