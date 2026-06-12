---
title: "Please post your tips and/or fixes here"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by ubuntu_demon on 2006-06-02
**Please post your tips and/or fixes here in this thread**

If you have problems and you need help IMHO it's best to start a **new** thread. In your own new thread : be elaborate about your problems. **Post the errors you get.** Post your /var/log/Xorg.0.log and ~/xsession-errors log files. Post the result of $lspci and post your /etc/apt/sources.list.

Also please post this :

1) System Specifications:
Monitor: CRT/LCD
Ram Amount:
HD: IDE/SATA/Scsi
Onboard or Discreet Graphics Card: NV/ATI/Intel/SiS/ect
CPU: 
MainBoard: Intel/Via/NV
Modem / Eth / Wifi brand:
Adapter cards you have installed:
2) Version of Ubuntu your using: (K)(X)(ED)Ubuntu or server.
3) Any error or output codes you receive durring the install or after:

---

### Post by barbarian on 2006-06-02
Thanks for your guide, I had trouble with dependencies yesterday until I have added koffice repos.

---

### Post by meenfreem on 2006-06-02
Hi, I'm having trouble with the upgrading. It gets stuck when it tries to install Samba. There are only 7 files left to install ](*,)

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=meenfreem]Hi, I'm having trouble with the upgrading. It gets stuck when it tries to install Samba. There are only 7 files left to install ](*,)[/QUOTE]
If you have problems regarding upgrading and you need help IMHO it's best to start a new thread and post the url of your new thread in this "discussion and questions" thread. After your problem is solved please edit your post here and say so.

In your own new thread : be elaborate about your problems. **Post the errors you get.** If the package management problem is solved but you are still having problems then post your /var/log/Xorg.0.log and ~/xsession-errors log files and post the result of $lspci

---

### Post by ubuntu_demon on 2006-06-03
this thread belongs to this sticky :

Having problems with installing or upgrading to Dapper? Here are some fixes
[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)

**Please post your tips and/or fixes here** so we can include in the sticky.

If you are having problems please start a new thread in "Installation and Upgrade Help" right here :
[http://www.ubuntuforums.org/forumdisplay.php?f=140](http://www.ubuntuforums.org/forumdisplay.php?f=140)

---

### Post by frodon on 2006-06-03
With the desktop CD, at the partition step when you edit manually the partitions and create your root and swap partition you may not be able to select the partition you created for the swap in the next step.

I waste 30min to understand why and to find a workaround.
To avoid this problem open gparted before the install (System > Administration > Gnome Partition Editor) and create your partitions then once done run the installer and the problem is gone.

This problem may happen performing a fresh install with the Desktop CD and it seems that i'm not alone in this case : [http://ubuntuforums.org/showthread.php?t=186309](http://ubuntuforums.org/showthread.php?t=186309)

---

### Post by ubuntu_demon on 2006-06-03
[QUOTE=frodon]With the desktop CD, at the partition step when you edit manually the partitions and create your root and swap partition you may not be able to select the partition you created for the swap in the next step.

I waste 30min to understand why and to find a workaround.
To avoid this problem open gparted before the install (System > Administration > Gnome Partition Editor) and create your partitions then once done run the installer and the problem is gone.

This problem may happen performing a fresh install with the Desktop CD and it seems that i'm not alone in this case : [http://ubuntuforums.org/showthread.php?t=186309](http://ubuntuforums.org/showthread.php?t=186309)[/QUOTE]
thnx!

I've added it here :
warning / take a look here prior to upgrading and installing
[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)

---

### Post by Patrick-Ruff on 2006-06-03
please take note of these 2 threads.

[http://ubuntuforums.org/showthread.php?t=186115](http://ubuntuforums.org/showthread.php?t=186115)

[http://ubuntuforums.org/showthread.php?t=187318](http://ubuntuforums.org/showthread.php?t=187318)

its becomming a major problem.

---

### Post by ubuntu_demon on 2006-06-03
[QUOTE=Patrick-Ruff]please take note of these 2 threads.

[http://ubuntuforums.org/showthread.php?t=186115](http://ubuntuforums.org/showthread.php?t=186115)

[http://ubuntuforums.org/showthread.php?t=187318](http://ubuntuforums.org/showthread.php?t=187318)

its becomming a major problem.[/QUOTE]
I have replied to this thread :
[http://ubuntuforums.org/showthread.php?t=186115](http://ubuntuforums.org/showthread.php?t=186115)

---

### Post by rotten777 on 2006-06-03
why did you close the other thread?

the advice you were giving as far as editing the menu list doesn't really work considering i can't get into the install. the cd boots, you choose standard install or safe graphics mode and it freezes on mounting the root filesystem.

---

### Post by ubuntu_demon on 2006-06-03
[QUOTE=rotten777]why did you close the other thread?
[/QUOTE]

Oops. That was an accidental mistake. I'm sorry. I opened it again. :p

I wanted to subscribe to it , but I accidentally clicked "close thread" instead, then I clicked on the firefox "stop button" and I didn't get any confirmation for closing it so I assumed it was still open. A tiny bit later I decided to reply in the thread.

[QUOTE=rotten777]
the advice you were giving as far as editing the menu list doesn't really work considering i can't get into the install. the cd boots, you choose standard install or safe graphics mode and it freezes on mounting the root filesystem.[/QUOTE]

It wasn't advice it was a request to **test**.

Please elaborate on your answer in the thread ([http://ubuntuforums.org/showthread.php?t=186115](http://ubuntuforums.org/showthread.php?t=186115)) as I don't fully understand your answer.

I don't have any more time right now.

good luck!

---

### Post by adament on 2006-06-03
A number of people installing Dapper Drake using the desktop live install cd have been experiencing the following problem: The installer boots to the point where it says Mounting root filesystem and then it stalls. Some have also reported that this issue occurs when trying to boot the newly installed system. A large thread with several different solutions to probably several different problems causing the same symptom have been discussed in this thread: [http://www.ubuntuforums.org/showthread.php?t=186115]("http://www.ubuntuforums.org/showthread.php?t=186115")

[therunnyman]("http://ubuntuforums.org/showpost.php?p=1093243&postcount=100") explains that when trying to boot a newly installed system and this occurs it is because of the disks being added to the system in the wrong order.

I have tried to summarise the different solutions/problems mentioned throughout the thread.

The common thing concerning this thread is that installer hangs at "Mounting root filesystem" when trying to boot the livecd. After having been stuck like this for some time a number of different errors have been reported.
The most common seems to be the following:
> hdb:ide_intr: huh? expected NULL handler on exit
hdb:ide_intr: huh? expected NULL handler on exit
Buffer I/O error on device hdb, logical block 357298
However some people(myself included) does not have the huh? errors but only this:
> Buffer I/O error on device hdb, logical block 357298
A third error was reported by Xombox. After having been stopped for about 3 minutes the following the output was given:
> Uncompressig Linux... Ok, booting the Kernel.
[4294007.545000] hda: drive not ready for command
Xombox later reported that the error was fixed when trying a different CD-drive. The first CD-rom drive was an ASUS DVD/CDROM E616.

The following fixs have been reported to work, however some fixs seem to work for some people and others for others. Which makes me believe that this might actually be a symptom caused by several different problems.

Beware that the different workarounds are in no particular order and as such it might not be better to try the first first. Rather read the entire list and try those which make sense on your setup(No point in trying to remove USB devices if non are attached).
[LIST]
[*]Use evms_activate -- I couldn't get this to work but it only seems that this worked for shoeshinecs give his instructions a look here: [http://www.ubuntuforums.org/showpost.php?p=1078025&postcount=3]("http://www.ubuntuforums.org/showpost.php?p=1078025&postcount=3")
[*]Remove all USB devices -- Didn't work for me, but worked for several people. A number of people have responded that this is not an option since they need their USB devices. Please beware that according to PirahnaBreaks after the installer had booted he could plug in all his USB devices again. He also reported that he had no problems when he tried to boot the installed system with USB devices plugged in. [http://ubuntuforums.org/showpost.php?p=1083336&postcount=45]("http://ubuntuforums.org/showpost.php?p=1083336&postcount=45")
[*]Disable USB2 in the BIOS -- I didn't try this, but it should be related to the solution mentioned above
[*]Just wait -- This seemed to work for a number of people, after waiting for 10 or more minutes with errors, the installer suddenly contined. However this didn't work for me
[*]Give irqpoll as a boot option -- This worked for some including me, others have reported that it helped to use noapic and nolapic too. I still had to wait a few minutes like in the solution above. Other boot options of use might be acpi=off pci=noacpi noacpi
[*][bobt]("http://ubuntuforums.org/showpost.php?p=1089433&postcount=91") reported that for him none of the above boot options worked, but instead adding ide=nodma as a boot option worked.
[*]Patrick mentioned adding root= as a boot option had worked for him -- I haven't tried this but apparently it gave him problems when trying to boot the installed system. However these problems were solved by following ubuntu_demon's guide in the following post [http://www.ubuntuforums.org/showpost.php?p=1087417&postcount=76](http://www.ubuntuforums.org/showpost.php?p=1087417&postcount=76)
[*]Using a different CD drive -- I haven't tried this but it would sound logical since it arises from those Buffer I/O errors on the CD-rom drive. It also worked for Xombox's set of errors. I don't know if the drive will be usable after install though.
[*]If all else fails the alternate install disc should work.
[*]Mjziegle mentioned something about a raid problem of his which had simmilar symptoms, [http://www.ubuntuforums.org/showpost.php?p=1085511&postcount=65](http://www.ubuntuforums.org/showpost.php?p=1085511&postcount=65)
[/LIST]

If anybody has any additional fixes or tips please either post them at this thread: [http://www.ubuntuforums.org/showthread.php?t=186115](http://www.ubuntuforums.org/showthread.php?t=186115) or PM me then I will try to keep this post up to date.

I hope this will be of help to some of you.

---

### Post by RavenOfOdin on 2006-06-04
**Q1.** Help! My packages are returning these errors!

```

<package name here> : unable to make backup link of </path/to/file here> : Operation not permitted.
dpkg-deb: Subprocess <package name here> killed by broken pipe: -1.
dpkg-deb: Error : Operation not permitted.

```

**A1.** Use the directory which is referenced by the */path/to* line and type, as root via sudo:

```

chattr -i *directory path here*/*

```

chattr -i (immutable) removes any special permissions on the file in question, like write-protect, so you can then create the backup link. If the error is instead:

```

<package name here> : unable to replace  </path/to/file here> 

```

do as above.

**Q2.** My packages won't configure via dpkg!

**A2.** At the command line type:

```

dselect

```

then at the menu, options of which should be 1 through 6, choose 4: [C]onfig. Follow the instructions it gives you after that and watch as dselect configures your packages.

**Q3.** My installer bails with something like "<file name> is trying to overwrite file in </path/to/file here> which belongs to package <package here>."

**A3.** To correct this error, go to console and type:

```

sudo dpkg -r <name of package>

```

and once it asks for your account password, type that password in and package removal will commence. You'll then be able to install your new package file over where the old one was.

**Q4.** Package A depends on Package B to install, but Package B depends on Package A to install! HELP!

**A4.** Was your install broken at some point along the line?
Did you need to remove packages which never got removed?
Go into the console, or your GNOME panel. Type:

```

sudo synaptic

```

or go to System > Accessories > Synaptic Package Manager.
In the "Filters" menu under "View", unmark everything except broken repositories, so only those display.  Then, mark the broken packages (symbolized by little red boxes) for reinstallation. If Synaptic wants to remove a bunch of packages while doing so, fine. Let it.

The package installation system is in my experience more intelligent via this than Adept, which whines on dependency problem creation.  It'll detect dependency problems and readjust accordingly.

Once again though, this is only my experience. Your mileage may vary, and before you remove *any* packages you should - just as a matter of common sense - know what you are removing.  

After this is done, your circular dependencies should resolve themselves.

That's it. I hope I helped a few of y'all out there with this, let me know if I made any mistakes or screwed anything up badly ... I hope not.

---

### Post by ubuntu_demon on 2006-06-04
Thank you very much RavenOfOdin and adament !!!!

RavenOfOdin : I'm linking to your post here :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)
[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)

adament : I'm linking to your post here :
[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)

---

### Post by KevLee on 2006-06-04
Hi all, I'm a long time windows user, but thought that I would have a look at moving to Linux, after looking around at some reviews I came to the conclusion that Ubuntu would be a good starting point.

I downloaded the ISO image, and burnt the CD from a Windows XP box (as documented).

Tried booting with this CD and got the following error:

ISOLINUX 3.11 Debian-2006-03-16 Copyright blah blah...
isolinux: disk error 20, ax=4280, drive 9f
Boot failed: press any key blah blah

I think that this was caused by burning the ISO to a 650Mb CD rather than 700Mb. 

I hope this helps.


Kev

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=KevLee]Hi all, I'm a long time windows user, but thought that I would have a look at moving to Linux, after looking around at some reviews I came to the conclusion that Ubuntu would be a good starting point.

I downloaded the ISO image, and burnt the CD from a Windows XP box (as documented).

Tried booting with this CD and got the following error:

ISOLINUX 3.11 Debian-2006-03-16 Copyright blah blah...
isolinux: disk error 20, ax=4280, drive 9f
Boot failed: press any key blah blah

I think that this was caused by burning the ISO to a 650Mb CD rather than 700Mb. 

I hope this helps.


Kev[/QUOTE]
You are right the cd's should be burned on 700 mb cd's because both the desktop and the alternate install cd are both bigger than 650 mb.

Thanks for your tip. I've add it to :
WARNING / take a look here prior to upgrading and installing!
[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)

---

### Post by rcarring on 2006-06-04
*Warning: the procedure below requires you to edit certain files in your Breezy system. *

From GUI (the desktop)


Run terminal

```

sudo apt-get update
sudo apt-get install xserver-xorg 
cd /
cd /etc/apt/ 
ls
sudo cp sources.list sources.list.bak
sudo nano sources.list


```

Add the following lines

```

#
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

```

This will add the alternate cd to list of repositories.


Run synaptic

Open Repositories menu

(Make sure you have backed up sources.list)

Remove ALL Breezy repositories leaving just the cdrom.

Save changes

Hit reload on the toolbar

Hit Mark All Upgrades

Hit Apply 

(NB this will update your system to the latest version of Ubuntu)

Reboot

(NB the stage of installing xserver-xorg is because the apt-get update may kill the xserver-xorg installed package, if you do this, you should not get X crashing due to missing files)

FROM COMMAND LINE


Run your system in recovery mode -- when you boot, hit esc when you see the grub loader, and choose recovery mode. This should take you to prompt.

The next steps set the alternate cd as the repo for the upgrade.

Open sources.list and add code below

```

#
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


```

Comment out the remaining lines referring to Breezy repos.

You should back up your sources.list before performing edit.


To edit the sources.list you need to do

```

cd /
cd /etc/apt/
sudo cp sources.list sources.list.bak
sudo nano sources.list

```

Ctrl-O to save the edit
Ctrl-X to quit nano

If nano not installed, try use pico instead.

Next you need to start the process of upgrading

```

sudo apt-get dist-upgrade

```

When the system tells you a conf file needs to be replaced, allow it to do so. My experience has been that not doing this has led to problems. The problems are that the old conf files expect certain things to be present and installed which are removed as part of the upgrade.

*[COLOR="Red"]Important -- make sure you back up your personal data first. This process is for emergency use only. Normally the upgrade should be performed from the GUI using update-manager.[/COLOR]*

---

### Post by ubuntu_demon on 2006-06-04
@ rcarring :

thnx for the guide! 

It needs a bit of cleaning/clearing up before it's usable for most users.

IMHO this guide of yours could be useful for people without a working internet connection. IMHO If your internet connection works it makes no sense to first download the cd in order to upgrade to Dapper (unless you want to do a clean install for some reason).

[quote=rcarring]
(NB the stage of installing xserver-xorg is because the apt-get update may kill the xserver-xorg installed package, if you do this, you should not get X crashing due to missing files)
[/quote]

"$sudo apt-get update" won't crash xserver-xorg 

Running $sudo apt-get dist-upgrade or the update-manager **might** cause the xserver-xorg to crash for a really small percentage of people with problems with broken dependencies.

Most people with broken dependencies have forgotten to comment non-official repos before doing the upgrade. If you upgrade using the upgrade-manager you won't have to comment non-official repos as it does this automatically.

Taking precautions as described here will prevent issues regarding unresponsiveness or not being able to log in :
[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)

---

### Post by rcarring on 2006-06-04
> 
thnx for the guide!

It needs a bit of cleaning up before I can post it though.

IMHO this guide of yours could be useful for people without a working internet connection. IMHO If your internet connection works it makes no sense to first download the cd in order to upgrade to Dapper (unless you want to do a clean install for some reason).


Would it be possible for people to ask a specific request for an alternate cd  to be sent to them?

I guess people could ask a friend who has broadband and a cd burner to download and burn the alternate cd.

I think many new users are having problems because they either haven't got any free space or their partition scheme is really complex, and that would make them a candidate for using the alternate cd.

This was a  first draft, I'll do some more work on it. Thx

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=rcarring]Would it be possible for people to ask a specific request for an alternate cd  to be sent to them?

I guess people could ask a friend who has broadband and a cd burner to download and burn the alternate cd.
[/QUOTE]

If you ordered 1 cd from shipit.ubuntu.com before Dapper you always got sent an install cd + a live cd in a single paper case. I don't know whether install cd's are still sent.

[QUOTE=rcarring]
I think many new users are having problems because they either haven't got any free space or their partition scheme is really complex, and that would make them a candidate for using the alternate cd.
[/QUOTE]

I haven't used the desktop installer. Isn't it possible to partition easily with the desktop installer ?

Having enough free space is important. Good one. I'll add something about how to create free space later.

[QUOTE=rcarring]
This was a  first draft, I'll do some more work on it. Thx[/QUOTE]

thnx for the effort!

---

### Post by rcarring on 2006-06-04
The way the cds are shipped has changed. 

From memory, I read on the old Dapper Dev forum that this time Canonical are sending a 2 cd pack with Live CDs for Gnome and KDE versions, the alternate cd is not being made available this way.

Sadly, many people really need that alternate install cd, and the fact that they have multiple partitions suggests that they have a degree of technical expertise beyond the normal user, so the alternate cd should work well for them.

As regards free disk space, my default install into a 10GB virtual hard disk, clean using the alternate cd required 4GB minimum, I wouldn't even think of trying it with a hard disk smaller than 4GB unless the server install method is used.

---

### Post by Pauliehaha on 2006-06-04
I'm trying to upgrade from Breezy to Dapper using the Update Manager and am getting the following message:

> **Not enough free disk space**
The upgrade aborts now. Please free at least 148M of disk space on /usr. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'. 

I've followed the messages advice and cleared the trash and the apt cache and when I check in Nautilus it says I have 1.1GB of free disk space, but the error keeps reappearing.

My feeling is that this isn't really a problem with the upgrade but possibly some quirk in the way my system is set up.

Any suggestions/advice would be much appreciated.

Thanks,

Paulie

---

### Post by rcarring on 2006-06-04
Do
```

df

```

in terminal to find out how much space is left.

Consider uninstalling applications such as Open Office to free additional disk space.

Is /usr in a separate root partition with /home on a separate partition?

---

### Post by Pauliehaha on 2006-06-04
Hi rcarring,

I get the following from the command you suggest:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1              4957188   3632112   1073260  78% /
tmpfs                   160932         0    160932   0% /dev/shm
tmpfs                   160932     12588    148344   8% /lib/modules/2.6.12-9-386/volatile

/usr and /home are both on /dev/hda1 and this looks like I still have over 1GB of free space?

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=Pauliehaha]Hi rcarring,

I get the following from the command you suggest:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1              4957188   3632112   1073260  78% /
tmpfs                   160932         0    160932   0% /dev/shm
tmpfs                   160932     12588    148344   8% /lib/modules/2.6.12-9-386/volatile

/usr and /home are both on /dev/hda1 and this looks like I still have over 1GB of free space?[/QUOTE]
try the -h switch to make it readable for humans :)

$df -h

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=rcarring]The way the cds are shipped has changed. 

From memory, I read on the old Dapper Dev forum that this time Canonical are sending a 2 cd pack with Live CDs for Gnome and KDE versions, the alternate cd is not being made available this way.
[/QUOTE]

I've read something about that but that was just a discussion. No decision was made. You won't get kde cd's by ordering from shipit.ubuntu.org

kubuntu cd's are available on : shipit.kubuntu.org

[QUOTE=rcarring]
Sadly, many people really need that alternate install cd, and the fact that they have multiple partitions suggests that they have a degree of technical expertise beyond the normal user, so the alternate cd should work well for them.
[/QUOTE]

There is a good possibility that they are still shipped. Otherwise they can download them ofcourse.

[QUOTE=rcarring]
As regards free disk space, my default install into a 10GB virtual hard disk, clean using the alternate cd required 4GB minimum, I wouldn't even think of trying it with a hard disk smaller than 4GB unless the server install method is used.[/QUOTE]

to free some space :
$sudo apt-get clean 

xdiskusage makes it easy to see where all your space has gone. To find the big folders in an easy way :
$sudo apt-get install xdiskusage
$sudo xdiskusage

A fully functional xubuntu costs me about 2.8  gb diskspace.

I have two installations of Dapper with ubuntu-desktop (on different partitions of a different machine). One was a fresh installation during dapper development and the other is an upgraded installation from breezy or breezy development (can't remember). Used space :
3.5 gb and 3.8 gb.

You should always have at least around 1 gb free when upgrading. 

So when installing a fresh xubuntu IMHO you should have at least 4 GB of diskspace free and when installing a fresh ubuntu you should have at least 5 GB of free diskspace. And then you will need some more diskspace for /home. I'm **not** suggesting that anyone should do a fresh install instead of an upgrade.

---

### Post by Pauliehaha on 2006-06-04
Ok that does make things clearer!

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             4.8G  3.5G  1.1G  78% /
tmpfs                 158M     0  158M   0% /dev/shm
tmpfs                 158M   13M  145M   8% /lib/modules/2.6.12-9-386/volatile

so I do have over 1GB free which makes me still wonder why I am getting a disk space error. 

I went through installed programs to check whether there was anything I could remove but am reluctant to remove anything if I can resolve the issue without doing so.

---

### Post by rcarring on 2006-06-04
@ubuntu_demon

Does it say anywhere on the Ubuntu web site that users will need 4GB for an upgrade and 5GB for a fresh install?

If not, suggest that System Requirements are edited to reflect this finding.

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=Pauliehaha]Ok that does make things clearer!

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             4.8G  3.5G  1.1G  78% /
tmpfs                 158M     0  158M   0% /dev/shm
tmpfs                 158M   13M  145M   8% /lib/modules/2.6.12-9-386/volatile

so I do have over 1GB free which makes me still wonder why I am getting a disk space error. 

I went through installed programs to check whether there was anything I could remove but am reluctant to remove anything if I can resolve the issue without doing so.[/QUOTE]
I have encountered such a situation before. For some reason the estimation is not very precise.

You probably have to remove less than 100 mb to get it working.

Don't worry if you remove some big packages you can add them later again after you have upgraded.

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=rcarring]@ubuntu_demon

Does it say anywhere on the Ubuntu web site that users will need 4GB for an upgrade and 5GB for a fresh install?

If not, suggest that System Requirements are edited to reflect this finding.[/QUOTE]
I have no idea. I suggest you start searching :p.

But it's somewhat of a personal thing some people may "need" to install 2 gb of packages after the installation to get a reasonable environment others may need only 100 mb of extra packages. I'm just reporting my personal disk space needs right now.

Later on I'll extract a summary of the useful information and add it to the sticky regarding disk space.

---

### Post by rcarring on 2006-06-04
I'll do a search later on.

I am going to recommend for the moment that for a working environment and the facility to install software packages with impunity on a new installation to chose 10GB free disk space.

However if a user is happy with an out-of-the-box install then 5GB or so should be enough.

That way you can keep your repo cached debs.

---

### Post by Pauliehaha on 2006-06-04
Thanks,

I removed a couple of packages and it's now upgrading.

Paulie

---

### Post by John.Michael.Kane on 2006-06-04
Also those posting for install help or any other issues with ubuntu please include the following in your post. 

1) **System Specifications: **
**Monitor: **CRT/LCD
**Ram Amount:**
**HD:** IDE/SATA/Scsi
**Onboard or Discreet Graphics Card:** NV/ATI/Intel/SiS/ect
**CPU:** Intel/AMD/PPC x86/x64 
**MainBoard: **Intel/Via/NV
**Modem Eth Wifi brand:**
**Adapter cards you have installed:** 
2)** Version of Ubuntu your using:** (K)(X)(ED)Ubuntu or server.
3) **Any error or output codes you receive durring the install or after:**

ubuntu_demon If you feel this should be in this thread please place it where you feel it needs to be. 
Thanks

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=SD-Plissken]Also those posting for install help or any other issues with ubuntu please include the following in your post. 

1) **System Specifications: **
**Monitor: **CRT/LCD
**Ram Amount:**
**HD:** IDE/SATA/Scsi
**Onboard or Discreet Graphics Card:** NV/ATI/Intel/SiS/ect
**CPU:** Intel/AMD
**MainBoard: **Intel/Via/NV
**Modem Eth Wifi brand:**
**Adapter cards you have installed:** 
2)** Version of Ubuntu your using:** (K)(X)(ED)Ubuntu or server.


ubuntu_demon If you feel this should be in this thread please place it where you feel it needs to be. 
Thanks
3) **Any error or output codes you receive durring the install or after:**[/QUOTE]
thnx for the suggestion. I'll add it later.

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=rcarring]I'll do a search later on.
[/QUOTE]

thnx. 

I really appreciate your help in the Installation and Upgrade Help forum!!!! 

[QUOTE=rcarring]
I am going to recommend for the moment that for a working environment and the facility to install software packages with impunity on a new installation to chose 10GB free disk space.

However if a user is happy with an out-of-the-box install then 5GB or so should be enough.

That way you can keep your repo cached debs.[/QUOTE]

Please don't suggest that. 

IMHO the typical user has enough with 5 GB for root. 

Some users tend to install a real lot of big extra software such as big (commercial) games. Advice people to use more diskspace for root if they they think they fit in that last category. 10 GB may be a nice amount for those type of users.

IMHO you should advice that they keep around 1 GB of diskspace free for it is needed for big upgrades (such as dist-upgrades to the next release).

The amount of disk space needed for personal files in /home is different for everybody and everybody should be able to make an estimate of how many diskspace they need for personal files.

---

### Post by Maksim on 2006-06-04
[QUOTE=SD-Plissken]Also those posting for install help or any other issues with ubuntu please include the following in your post. 

1) **System Specifications: **
**Monitor: **CRT/LCD
**Ram Amount:**
**HD:** IDE/SATA/Scsi
**Onboard or Discreet Graphics Card:** NV/ATI/Intel/SiS/ect
**CPU:** Intel/AMD
**MainBoard: **Intel/Via/NV
**Modem Eth Wifi brand:**
**Adapter cards you have installed:** 
2)** Version of Ubuntu your using:** (K)(X)(ED)Ubuntu or server.
3) **Any error or output codes you receive durring the install or after:**

ubuntu_demon If you feel this should be in this thread please place it where you feel it needs to be. 
Thanks[/QUOTE]

I would suggest to have Processor Architecture also like x86, x64, ppc etc.

Good Luck!

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=Maksim]I would suggest to have Processor Architecture also like x86, x64, ppc etc.

Good Luck![/QUOTE]
thnx for the suggestion!

---

### Post by Quirky on 2006-06-04
I upgraded from Breezy and the upgrade tool crashed and burned near the end of the upgrade process, after installing most packages. It said something like "Your system may be completely broken", which I didn't find too comforting!

Luckily my system was 99% usable and I was able to track down the problem: **docbook-utils** and its dependencies do not upgrade cleanly. Before upgrading, remove them to avoid this problem.

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=Quirky]I upgraded from Breezy and the upgrade tool crashed and burned near the end of the upgrade process, after installing most packages. It said something like "Your system may be completely broken", which I didn't find too comforting!

Luckily my system was 99% usable and I was able to track down the problem: **docbook-utils** and its dependencies do not upgrade cleanly. Before upgrading, remove them to avoid this problem.[/QUOTE]
thnx!

---

### Post by ubuntu_demon on 2006-06-04
I'm going to sleep now. I will update the stickies sometime tomorrow again. 

I really appreciate all the fixes and tips of everybody! Keep them coming!

---

### Post by jg123 on 2006-06-04
My list of problems and fixes:
1. First problem was upon boot I got this error:
error 13: Invalid of unsupported executable format
and the new 2.6.15-386 kernel wouldn't load. I fixed it by booting into the old 2.16.12-686 kernel and installing the 2.6.15-686 kernel. That one worked. (I know; it's more of a workaround)

2. Second problem was my eth0 network card stopped working. I also noticed on bootup it was looking for /usr/sbin/ifrename. Fortunately I found that udev replaced the ifrename and I had to make sure my /etc/iftab file was correct. It had the wrong mac address (maybe from the last ethernet I had in the PC months ago?). I put in the correct mac address, rebooted and eth0 reappeared.

3. Third problem was the following message on X startup:
Xsession: unsupported number of arguments (2); falling back to default session.
I diffed the new version of /etc/gdm/Xsession to the last version of the same file and saw that it was now sourcing my /etc/profile. I had mistakenly put "set bell-style none" in there instead of in /etc/inputrc, and now Xsession was sending this as parameters to everything in /etc/X11/Xsession.d. I took it out and the message stopped popping up.

---

### Post by therunnyman on 2006-06-05
The devs don't appear to want to fix this, so I'll do my best here to help.

A lot of servers, RAIDs and whatnot have two SATA hard disk ports on the mainboard, then a card (PCI, PCI-X, or PCI-express) for additional SATA drives. For instance, I have three disks on the machine I'm writing this from, two plugged into the mainboard, and one plugged into a PCI card. Many prefab machines come this way: Dell's servers do, I believe, and I think, well, hell, a lot of servers have that setup. Four SATA drives, two plugged into the mainboard and two plugged into a card.

You'll notice when you install Dapper to, say, SATA 0 (first mainboard port), everything will appear to be operating as normal, but it ain't. What will likely happen on reboot is a spiteful message and a drop to a shell. True bummer.

What's happened is your PCI devices are loaded first, so sda will be whatever drive you've got plugged in to your card (and sdb will be whatever drive you've got hooked to port 2 of the card).

The main problem is in udev, and I'm working on that solution. Meantime, all we RAID/more-than-two-SATA-drives people can do is physically rewire the hard disks according to this schema:

Card Port 1 = sda
Card Port 2 (if present) = sdb
Mainboard 0 =sdb (if there's only one drive rigged to the card) or sdc.
Mainboard 1= sdc (if there's only one drive hooked into the card) or sdd.

Striping gets really hairy here. Pre-install, the mainboard ports will be sda and sdb, even during the partition phase. Here, you should proceed as if sda, sdb, sdc and so on will be properly identified. Once finished, physically rewire your drives as described above.

As soon as I have this udev file figured out, I'll post it.

runny

PS If you don't feel like popping your case open, you can rewrite /boot/grub/menu.lst as well.

---

### Post by confused57 on 2006-06-06
I'm not sure if this is appropriate here, but I'll post it anyway.
I already had a computer I built dual boot Breezy/Windows set up like this:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=Dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=Dualboot)

Thought I'd try the same with my Dell Dimension 4550 with installing Dapper on a 2nd HD, ubuntu master, windows slave.  Went to reboot, set up as mentioned in the thread above, but booting Windows I got an "Error 21:Selected disk does not exist"...Booted back into Dapper, saw that the partition table for hdb was partition #1 = 35 Mb was a Dell Utility, partition #2 was Windows.  I proceeded to change the root from (hd1,0) to (hd1,1), thinking that would select the 2nd partition to boot up windows...same error 21 message.   I was frustrated to say the least, so I checked the bios and found that the primary ide controller for the slave drive was "off", changed it to "auto", rebooted immediately into windows...FYI

---

### Post by terarast on 2006-06-06
Please help! I reboot computer, begin install and after the progress bar is 100% the next step with nothing in monitor is freezes.

 Athlon2500
 1024 Ram
 ubuntu-6.06-desktop-i386

---

### Post by MrShmoe on 2006-06-07
I'm not sure if this is the right place to post this but here it goes...

I've managed to install Ubuntu 6.06 on my computer. When I start my computer GRUB starts and gives me the option too boot windows or ubuntu. When I choose to boot ubuntu it hangss on "Mounting root file system" And after about 2 min I get this message:
```
ALERT! /dev/hda1 does not exist. Dropping to a shell!


Busy Box v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of commands.

/bin/sh: can't access tty; job control turned off
```

I don't know why it says that it can't find the HDD since it could find it when I partitioned it and installed the OS on it.

My system is configured like this:

120GB S-ATA - Windows
120GB IDE - Ubuntu

the IDE-drive is partitioned like this
/dev/hda1 - used as /
/dev/hda2 - swap
/dev/hda3 - used as /home

I have no idea what to do since I've never used Linux before, please help!

---

### Post by ubuntu_demon on 2006-06-07
[QUOTE=terarast]Please help! I reboot computer, begin install and after the progress bar is 100% the next step with nothing in monitor is freezes.

 Athlon2500
 1024 Ram
 ubuntu-6.06-desktop-i386[/QUOTE]
check the first post of this thread :
[http://www.ubuntuforums.org/showpost.php?p=1080770&postcount=1](http://www.ubuntuforums.org/showpost.php?p=1080770&postcount=1)

> 
**Please post your tips and/or fixes here so we can include them in the stickies.**

If you have problems and you need help IMHO it's best to start a new thread. In your own new thread : be elaborate about your problems. **Post the errors you get**. Post your /var/log/Xorg.0.log and ~/xsession-errors log files. Post the result of $lspci and post your /etc/apt/sources.list.

Also please post this :

1) System Specifications:
Monitor: CRT/LCD
Ram Amount:
HD: IDE/SATA/Scsi
Onboard or Discreet Graphics Card: NV/ATI/Intel/SiS/ect
CPU:
MainBoard: Intel/Via/NV
Modem / Eth / Wifi brand:
Adapter cards you have installed:
2) Version of Ubuntu your using: (K)(X)(ED)Ubuntu or server.
3) Any error or output codes you receive durring the install or after:


good luck!

---

### Post by ubuntu_demon on 2006-06-07
> **MrShmoe]I'm not sure if this is the right place to post this but here it goes...

I've managed to install Ubuntu 6.06 on my computer. When I start my computer GRUB starts and gives me the option too boot windows or ubuntu. When I choose to boot ubuntu it hangss on "Mounting root file system" And after about 2 min I get this message:
```
ALERT! /dev/hda1 does not exist. Dropping to a shell!


Busy Box v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of commands.

/bin/sh: can't access tty said:**
> 
from [http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656) :
[QUOTE]
**booting stalls during "mounting root filesystem"?**
[http://www.ubuntuforums.org/showpost...6&postcount=11](http://www.ubuntuforums.org/showpost...6&postcount=11)
[http://www.ubuntuforums.org/showpost...1&postcount=41](http://www.ubuntuforums.org/showpost...1&postcount=41)
[http://www.ubuntuforums.org/showthread.php?t=186115](http://www.ubuntuforums.org/showthread.php?t=186115)


check the first post of this thread :
[http://www.ubuntuforums.org/showpost...70&postcount=1](http://www.ubuntuforums.org/showpost...70&postcount=1)

Start a new thread or join this discussion :
[http://www.ubuntuforums.org/showthread.php?t=186115](http://www.ubuntuforums.org/showthread.php?t=186115)

good luck!

---

### Post by ashridah on 2006-06-07
Along similar lines as many people's "Waiting for root filesystem" hangups, I've found that the Silicon Image 3132 SATA (sata_sil24) controller on my Asus A8N32-SLI-Deluxe motherboard doesn't seem to initialize properly when the system's booting after installation, when i was using an AMD64 version of ubuntu. (might be amd64 specific, don't know yet)

I ended up having to move my main disk drive to the Nforce4 controller (sata_nv), because even running modprobe sata_sil24 once the system had dropped to the recovery shell didn't do the trick.

Not sure why this happened, the liveCD desktop install cd was able to detect the drive fine, AND the driver seems to load okay once ubuntu has finished booting, although i can't tell that it's working okay, since I've only got the one SATA disk drive.

Just thought i'd add my piece to the puzzle :)

ashridah

---

### Post by ubuntu_demon on 2006-06-07
I've just improved the "HOWTO fix problems regarding broken dependencies" guide by adding a post about debfoster :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

I will be away for a couple of days so I won't be able to edit the stickies.

---

### Post by puk on 2006-06-07
Hi

[QUOTE=adament]A number of people installing Dapper Drake using the desktop live install cd have been experiencing the following problem: The installer boots to the point where it says Mounting root filesystem and then it stalls.[/QUOTE]

I solved this by hitting F6 on the grub-prompt and typeing in "ide=nodma" then hit enter and suprisingly enough it worked even though I know my hardware supports dma.

---

### Post by puk on 2006-06-08
Hi,

I solved a Blank-Screen Prob with my LCD which might be interesting for some Laptop installs, too...

[http://ubuntuforums.org/showthread.php?p=1111038#post1111038](http://ubuntuforums.org/showthread.php?p=1111038#post1111038)

---

### Post by The Mad Scientist on 2006-06-19
If you have problems with Dell Precision workstations locking/losing keyboard and mouse on install/first boot-up, try updating the BIOS.  My original install of 5.10 had this problem, which I worked around at the time.  When I upgraded to 6.06, the problem resurfaced.  I upgraded from BIOS A02 to A07 on my Precision 380 and the problem went away.

---

### Post by PeteJ on 2006-06-26
Hi all,

Good news here, finally.

I'm installing Dapper 6.06 LTS dual boot along with Windows 2000 (Win2K) on an old IBM ThinkPad 21 (with a new 80GB HD).   For days and days, I couldn't get the Dapper installation to work (for the search engines:  the dapper installation would hang/hanging/hanged, lock up/locking up/locked up, stall/stalling/stalled).  

I finally got it to work by throwing the kitchen sink at it.  I'm not sure which part really did the trick, but I think it was selecting Safe Graphics Mode, disabling the screen saver, and disabling power management BEFORE launching the Install desktop icon.  

This are the steps I took just before getting a successful install.  I downloaded the desktop iso and burned it to cd.  I booted from the CD, and selected the Safe Graphics Mode option.  I tapped F6.  Before the "--", I stuffed in
acpi=off noapic nolapic pci=noacpi
and I also removed the quiet and splash options,
and after the "--", I put a space then:
BOOT_DEBUG=3

Then, it eventually booted to the gnome desktop with the Install icon on the desktop.   Now here's the important part, I think.  BEFORE launching the Install icon, click on 

System > Preferences > Screensaver

and then uncheck the 

Activate screensaver when session is idle

box, and then click Close.

Then, click

System > Preferences > Power Management

and under 

Running on AC

drag the top slider all the way to the right, so that it says Never, then click Close.

Now you can double click the Install icon without the screensaver or power management getting in the way of your dapper installation.

I hope this saves some folks a few hours.

If there are any Ubuntu developers out there, first, thanks of everything(!), but also, please modify the default settings to prevent the screensaver and power management from getting in the way of the installation.

Thanks,
Pete

---

### Post by seeklinux on 2006-06-26
So this may be covered somewhere else, but in case it isn't....

If you use wireless to connect to the internet you should search on the Internet (and in these forums) to see how to get your wireless card/adapter working.  If you don't find it is natively supported (without ndiswrapper) or if  you don't know ahead of time, then you probably should do the following.  

[LIST=1]
[*]Buy or borrow a USB flash card
[*]Download the ndiswrapper deb file and copy it to the flash drive. I got it [here]("http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils_1.8-0ubuntu2_i386.deb").
[*]Get the diskette that came with your adapter/card and copy the contents of the directory for Windows XP or Windows 2000 to the flash drive. This will include a .SYS file and a .INF file at least
[/LIST]

When you use the live CD hopefully your wireless card will just work and you won't need the instructions below. But if it doesn't, then here is how to try to get it working with ndiswrapper.

*Disclaimer: I am not advocating the use of ndiswrapper instead of native linux drivers. I only use it because it was the only way to get my card working. If native Linux drivers are available and sufficient, please use those. Or if you are purchasing a new card, you can try to find one that is supported by native Linux drivers.*

Copy the files listed above from flash to your home directory. Look under **Places** to  open a window to your home directory (folder).  Your flash drive should show up on the desktop and double clicking on it should open a window to that. Then copy and paste.

Open a terminal window via **Applications->Accessories->Terminal**

Now install ndiswrapper:

sudo dpkg -i ndiswrapper-utils_1.8-0ubuntu2_i386.deb

Next in the same terminal window try to install the driver for your wireless card/adapter:

sudo ndiswrapper -i *path_to_inf_file*
sudo ndiswrapper -m
sudo modprobe ndiswrapper
sudo ndiswrapper -l

That last step should just display that the previous steps worked correctly. Hopefully when you did the "sudo modprobe ndiswrapper" your device light(s) started blinking.

Now assuming you use wireless security, you probably need to enter those properties to actually get connected. So go to **System->Administration->Networking** and hopefully you will see wlan0 listed there. Click on "Properties" and enter your SSID and your WEP key.  Once you hit Apply and OK hopefully you will get connected.

Now one other thing. When you have it configured and hit the Install button on the desktop, it will not install ndiswrapper (at least it didn't for me). So after installing, you will probably have to do the "sudo dpkg ..." step again, so keep the ndiswrapper deb file on your flash drive a little longer.  The good news is the results of your other steps probably did make it into your install, so once you get the ndiswrapper package installed again you should be ready to network.

---

### Post by brenbart on 2006-06-28
I had this problem when I first loaded Dapper on a laptop with a small hard drive.  I'm not sure exactly where it should go but I never found a forum entry to match this problem.

My laptop would boot and get to the login screen with no problems.

Then the following would occur:
1. I entered username and password
2. The progress of the various scripts being run on startup would display with a black background.
3. It would display a dark amber screen with a busy mouse cursor.
4. It would dump me back to the login screen.

No errors showed up in Xorg or dmesg

I eventually discovered the problem was caused by the partition containing my filesystem being completely full.  

I rebooted and via the grub menu recovery mode and ran 'apt-get clean' and 'apt-get autoclean' which cleared enough space to allow me to login when rebooted.

---

### Post by ELMIT on 2006-06-28
1) System Specifications:
Monitor: LCD
Ram Amount:  2G
HD: SATA
Onboard or Discreet Graphics Card: NV/ATI/Intel/SiS/ect
CPU:Intel P-4 D920
MainBoard: ASUS
Modem / Eth / Wifi brand: e1000
Adapter cards you have installed:
2) Version of Ubuntu your using: Ubuntu 6.06 AMD64.
3) Any error or output codes you receive durring the install or after:

I have installed the system without any troubles. I have partitioned my 250 G hard disk into:
/    4 G
swap   3 G
and the rest temporary as data space.

I want to remove the data space and create LVM.
I tried to use System/Administration/Disks
At the bottom I see
"Starting Administrative Application" and "Starting Disks"
and in reverse order it disappears. 
NO Window opens with these Applications!
/var/log/messages does not say anything about that either!


I can also see that 10 updates are waiting.
Clicking on the star lets the time spinning and nothing happens (except that on the bottom "Starting Administrative Applications" for a while appears.)

It is my first Ubuntu installation! What have I done wrong? How can I fix it?

bye

Ronald

---

### Post by ubuntu_demon on 2006-06-29
[QUOTE=ELMIT]1) System Specifications:
Monitor: LCD
Ram Amount:  2G
HD: SATA
Onboard or Discreet Graphics Card: NV/ATI/Intel/SiS/ect
CPU:Intel P-4 D920
MainBoard: ASUS
Modem / Eth / Wifi brand: e1000
Adapter cards you have installed:
2) Version of Ubuntu your using: Ubuntu 6.06 AMD64.
3) Any error or output codes you receive durring the install or after:

I have installed the system without any troubles. I have partitioned my 250 G hard disk into:
/    4 G
swap   3 G
and the rest temporary as data space.

I want to remove the data space and create LVM.
I tried to use System/Administration/Disks
At the bottom I see
"Starting Administrative Application" and "Starting Disks"
and in reverse order it disappears. 
NO Window opens with these Applications!
/var/log/messages does not say anything about that either!


I can also see that 10 updates are waiting.
Clicking on the star lets the time spinning and nothing happens (except that on the bottom "Starting Administrative Applications" for a while appears.)

It is my first Ubuntu installation! What have I done wrong? How can I fix it?

bye

Ronald[/QUOTE]
Please start a new thread. This thread is for tips and fixes.

---

### Post by ubuntu_demon on 2006-06-29
I've met Micheal Vogt at the summit. He's a great guy. He's a core developer working mainly on package management tools. I'm currently communicating with him about common problems regarding upgrading to Dapper.

[quote=ubuntu_demon]
Can I promise our forum users an update to the dist-upgrader which
includes common fixes as found on the forums ? If so ... how much and
which fixes will it include ?
[/quote] 

[quote=Micheal Vogt]
Yes, you can do this. I'm very happy about the suggestions in the
forums. Its the perfect place to discuss those issues it seems. 
 
I'm working on this right now, sorry that it took so long, but I had
to do some post-conference stuff first. I will definitely include the
screensaver fix (killing the screensaver before the upgrade). It will
also contain some i18n updates. I'm looking into the docbook-utils
problem right now.
 
I'll go over the launchpad bugreports as well to see what problems are
reported there and fix as much as possible.
[/quote]

[quote=ubuntu_demon]
[..]
Maybe we can figure something out to try to catch more common
problems/fixes before the actual release of Edgy.
[..]
[/quote]

[quote=Micheal Vogt]
That would be really good. I plan to get more automatic testing done
for dapper->edgy, but nothng beats user-testing  :) 

Thanks,
 Michael
[/quote]

---

### Post by pgk3734 on 2006-07-03
After upgrading to Ubuntu 6.06 there was a kernel panic.
I figured that lilo was not set up.
I first did $sudo mount -o dev /mnt/hda7  (or whatever your partition is)
or if its already mounted: sudo mount -o remount,dev /mnt/devhda7.
Lilo needs to think that /mnt/hda7 is /., so:
$sudo chroot /mnt/hda7 lilo
When you reboot lilo should now work.
I hope this works for you, it did for me.;)

---

### Post by ubuntu_demon on 2006-07-03
I've posted about this bug "booting stalls during mounting root filesystem"on my blog :
[http://ubuntudemon.wordpress.com](http://ubuntudemon.wordpress.com)

This thread contains links to possible fixes :
[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)

Currently it links to these possible fixes :
[http://www.ubuntuforums.org/showthread.php?t=197956](http://www.ubuntuforums.org/showthread.php?t=197956)
[http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11](http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11)
[http://www.ubuntuforums.org/showpost.php?p=1098541&postcount=41](http://www.ubuntuforums.org/showpost.php?p=1098541&postcount=41)

This is the big discussion thread where people post their problems :
[http://www.ubuntuforums.org/showthread.php?t=186115](http://www.ubuntuforums.org/showthread.php?t=186115)

Please post your tips and/or fixes here in this thread.

What happened in my case :
For me my /dev/hda became /dev/hde after upgrading. On a fresh install I could produce exactly the same results. To solve it I had to edit my /etc/fstab and /boot/grub/menu.1st accordingly. Each time a new kernel gets installed I have to edit my /boot/grub/menu.1st again and change /dev/hda for /dev/hde.

See for example a part of my /boot/grub/menu.1st :
```

title           Ubuntu, kernel 2.6.15-25-686
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.15-25-686 root=/dev/hde6 ro vga=0×31a
quiet splash
initrd          /boot/initrd.img-2.6.15-25-686
savedefault
boot

```

**edit :**

udev enumeration should use /sys/bus not /sys/devices
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367)

**The devs know about this bug and we might see a dapper-update someday.** No need for searching launchpad anymore. See this thread :
[http://www.ubuntuforums.org/showthread.php?t=208207](http://www.ubuntuforums.org/showthread.php?t=208207)

---

### Post by tobirius on 2006-07-03
I have two issues with Dapper. First, the integrated driver for my wireless-card adm8211 is not working. Therefor I have to use ndiswrapper to get connected. Second, the ndiswrapper version coming from ubuntu-archives is not stable at all. It freezes my system all the time. Installing the newest version (1.18) helped a lot.

---

### Post by ubuntu_demon on 2006-07-03
[QUOTE=tobirius]I have two issues with Dapper. First, the integrated driver for my wireless-card adm8211 is not working. Therefor I have to use ndiswrapper to get connected. Second, the ndiswrapper version coming from ubuntu-archives is not stable at all. It freezes my system all the time. Installing the newest version (1.18) helped a lot.[/QUOTE]
thnx for the tip!

I've disabled smileys in your post so it shows 1.18 instead of (1.18)

---

### Post by davescafe on 2006-07-09
Using the help from several threads in this forum, and by much of my own research, I have been able to work-around my problems relating to, "Mounting root file system..." and, “Waiting for root file system...”. 

[SIZE="3"]Overview[/SIZE]

> This bug is probably (most of the time?) related to people who have both SATA and PATA controllers on their motherboard.
~ Ubuntu_demon ([http://ubuntudemon.wordpress.com/2006/07/03/worst-bug-in-dapper/)](http://ubuntudemon.wordpress.com/2006/07/03/worst-bug-in-dapper/))

I have an Asus P4P800-E Deluxe motherboard (specifications below), which provides two drive controllers and will allow me to plug-in up to 4 S-ATA drives into my motherboard.  The primary controller is made by Intel, and the secondary is made by Promise.  I am only using S-ATA drives in my system, but the way the Promise drive controller works with the Asus BIOS, I think the second set of S-ATA plugs are interpreted as regular, paralell ATA drives.  I don’t understand all the technical details, but the bottom line is that I have 3 S-ATA drives, one of which is interpreted by my system as a regular, PATA drive.
  
Ubuntu works well as long as I am only using my SATA-only controller (Intel, which allows no more than two drives).  As soon as I have drives plugged-in to both the SATA (Intel) *and* PATA (Promise) controllers, I start having problems with Ubuntu booting.

[SIZE="3"]Problem 01[/SIZE]
I have 2 HDDs installed (on one, Intel drive controller).  Ubuntu works well.  Then I add a third drive, and so I have to plug it in to the Promise drive controller, which interprets this as a paralell ATA drive, and, for whatever reason, re-numbers the drives in my system.
With only 2 drives, my drives were:
> sda = Ubuntu root & Windows XP
sdb = Ubuntu home
With 3 drives, Ubuntu (or Grub?) has re-ordered the drives as follows:
> sda = New drive
sdb = Ubuntu root & Windows XP
sdc =  Ubuntu home
So when I boot the system with 3 drives, only 3 lines appear on the screen:
> Loading essential drivers...
Mounting root file system...
Waiting for root file system...
It hangs at this point for a few minutes, before dropping me into a shell.  I am not able to successfully start Ubuntu.

[SIZE="3"]How I worked-around Problem 01[/SIZE]
*****WARNING*** **this work-around requires that you edit some system files and that affeect how Ubuntu will boot.  These steps worked for me, but they may not work for you.  Use them as a guide if you like, but please don’t make these changes if you don’t feel comfortable with the risk.
[LIST=1]
[*]You will need to change the drive designations.  If you want to know for sure which to change to, you can use the Ubuntu live CD.  For me, it was less time-consuming to just guess.  If I got it wrong, it was quick to just try another drive letter until I got it right. However, if you would like to have Ubuntu tell you exactly, you can boot up the Ubuntu live CD, and once you are in GNOME, go to the System menu ==> Administration ==> Disks, or you can open a terminal and use gparted (type “sudo gparted”).  Your objective is to determine which hard drive and partition your Ubuntu root directory is located on.  This will be very different depending on your system, but for me, I have my root partition in an 15 GB EXT3 partition.
[*]Once you have figured out where your Ubuntu root partition is located (or if you would like to just guess), reboot your computer *without* the the Ubuntu CD or any other startup CDs in your drive.
[*]When Ubuntu is just beginning the boot process, and the GNU Grub boot menu selection screen appears, select the entry that I use to boot into Linux, and press the “e” key to edit.
[*]In the edit screen, you should see a series of lines that look something like:
> title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

[*]Select the the line which begins with “kernel” and press the “e” key again (to edit).
[*]Change the drive designation from the one that isn’t working to one that you think will work. For example, I changed this:
> kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda3 ro quiet splash
to this:
 > kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sdb3 ro quiet splash
(notice that “sda3” changed to “sdb3”)
[*]Press the <Esc> key when you are done editing
[*]Use the arrow keys to scroll up to the top line (root) and press the “b” key to boot.
[*]While Ubuntu is booting up, I received an error message which read:
> The superblock could not be read or does not describe a correct ext2 filesystem.  If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock: e2fsck -b 8193 <device>

exit from this shell and continue system startup
[*]Type “exit” to leave the shell and the error message behind.  We will take care of this in the next steps.
[*]At the graphical Ubuntu / Gnome log-in screen, don’t try to log-in normally (it may not work because your drives are mounted differently than expected), instead, go to a terminal window by pressing <Ctrl> <Alt> <F1>
[*]Log-in at the terminal window with your username and password
[*]Back-up your fstab file before making any changes by typing the following:
sudo cp /etc/fstab /etc/fstab.original
You can use the Ubuntu live CD and restore your original settings, if desired.
[*]Edit your fstab file:
> sudo nano /etc/fstab
or if you prefer to use vi, type:
> sudo vi /etc/fstab
[*]In the text editor, change the drive labels (names).  For my configuration, this meant changing:
> /dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda4       /home           ext3    defaults        0       2
/dev/sda2       none            swap    sw              0       0

to
> /dev/sdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb4       /home           ext3    defaults        0       2
/dev/sdb2       none            swap    sw              0       0

[*]Save your changes and exit the editor
[*]Back-up your menu.lst file by typing the following:
> sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.original
[*]Edit your menu.lst file by typing:
> sudo nano /boot/grub/menu.lst
or if you prefer to use vi, type:
> sudo vi /boot/grub/menu.lst
[*]Find the line that contains the name of the kernel you want to boot.  This should be located just *after* the line which says, “## End Default Options ##” In my system, this is approx. line 111:
> ## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot
[*]Go down the the kernel line and change the hard drive assignment, in the same way you changed it in step 3.  In my system, I changed this:
> kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda3 ro quiet splash
to this:
> kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sdb3 ro quiet splash
[*]While you’re in here, you should probably make the same change to other kernels in the list, such as the “recovery mode” kernel
[*]Save your changes and exit the editor
[*]Reboot your system by typing:
sudo reboot
[*]Ubuntu should boot up normally from now on
[*]Please note that you will need to re-apply any changes to menu.lst every time you install a new kerenel (for example, when the update service puts a new kernel down for you).
[/LIST]
[SIZE="3"]Problem 02[/SIZE]
If I install Ubuntu on my system and I have at least 2 drive controllers in use, one of them S-ATA and the other P-ATA, then I am not able to get into Windows by selecting the Windows option in GRUB.

For example:
I have 3 hard drives and I have Windows XP already installed and working fine.  I install Ubuntu on this system.  Now, when I try to select Windows XP from the GRUB selection screen, I receive an error.  I am unable to proceed and cannot start Windows XP.

This is the error text I receive:
> “Booting ‘Microsoft Windows XP Professional’

root    (hd5,0)
  Filesystem type unknown, partition type 0x7
  savedefault
  makeactive
  map    (hd0)  (hd5)
  map    (hd5)  (hd0)
  chainloader +1


NTLDR is missing
Press Ctrl+Alt+Del to restart

[SIZE="3"]How I worked-around Problem 02[/SIZE]
Many of the same steps from the previous work-around apply to this work around, so I won’t list them again.  Suffice it to say that I needed to edit my /boot/grub/menu.lst file as follows:
Broken menu.lst file as it appeared after installing Ubuntu:
> title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

Fixed menu.lst file that works for my system configuration:
> title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

[SIZE="3"]Problem 03[/SIZE]
If I install Ubuntu on my system and I have at least 2 drive controllers in use, one of them S-ATA and the other P-ATA, then I am not able to boot Ubuntu after install is complete.  This is similar to Problem 01, but different in the changes that need to be made to work-around the problem.

[SIZE="3"]How I worked-around Problem 03[/SIZE]
Once again, many of the steps from the Problem 01 work-around apply, so please refer to those steps.  To fix problem 03, I needed to edit my /boot/grub/menu.lst file as follows:
Broken menu.lst file as it appeared after installing Ubuntu:
> title		Ubuntu, kernel 2.6.15-23-386
root		(hd5,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sdf3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

Fixed menu.lst file that works for my system configuration:
> title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sdf3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot
The only change I made was, “(hd5,2)” to “(hd0,2)”.  I did not change anything in the “kernel” line.



[SIZE="3"]Other Details[/SIZE]

[SIZE="2"]My System Specifications[/SIZE]
Monitor:		CRT
Ram Amount:		1GB
HD:			SATA
Discreet Graphics Card: NV
CPU: 			P4 3.2 Ghz
MainBoard: Asus P4P800-E Deluxe
Gigabit Eathernet connected via Cat5e to wireless modem.
Adapter cards you have installed: none

Linux Version: Ubuntu 6.06 (Dapper Drake)

[SIZE="2"]References[/SIZE]
[http://www.ubuntuforums.org/showthread.php?t=208207]("http://www.ubuntuforums.org/showthread.php?t=208207")

---

### Post by ubuntu_demon on 2006-07-09
Thank you very much davescafe.

I added a link to your post in the "Having problems with installing or upgrading to Dapper? Here are some fixes " thread.

---

### Post by ubuntu_demon on 2006-07-14
This is regarding the "mounting root files system" bug

**Everyone please test this general workaround :**

[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/69](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/69)

[quote=Paul Sladen]
For those still wondering; The workaround for this issue involves specifying the partition to boot from by ID, rather than the transient location:

  1. Boot a desktop/LiveCD.
  2. Run sudo /sbin/dumpe2fs /dev/sdX | grep UUID
  3. tell 'grub' or 'lilo' to boot with that ID:

     linux ... root=UUID=d4c51a2a-d93f-4dc1-8717-9c3cdb4d41ce

and also adjust this in:

  /boot/grub/menu.lst
[/quote]

Replace sdX for sda, sdb, sdc, sdd, hda,hdb,hdc,hdd or whatever gparted on the livecd tells you it is.

You can post results either on launchpad here :
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/)
Or in this thread :
[http://ubuntuforums.org/showthread.php?p=1257154](http://ubuntuforums.org/showthread.php?p=1257154)

---

### Post by HonorSystem on 2006-07-15
I guess this is where I should post these tips, huh?  If not, I hope it wouldn't be too much trouble to remove/move this post for me.  

I had two issues with my installation of 6.06 using the standard live CD.  I am new to linux and I wasn't able to illicit any responses here, but enough googling and intuition got things fixed in the end.

1) For anyone who is having display problems with the live CD once the X Window system loads.

If your display is garbled, go to terminal via ctrl+alt+F1 and from there do the following:
```
sudo pico /etc/X11/xorg.conf
```
Scroll down to Section "Device" and change the entry for driver to "vesa".    Ctrl+X to exit the editor and press y and then enter to save the file.  Return to X using ctrl+alt+F7 and proceed to kill it with ctrl+alt+backspace.  Within a few seconds, X should restart automatically (if not, simply enter startx) and your video problems should be solved.  Being your installation and maybe play some gnometris while you wait :)

2) For anyone who is receiving the error ```
sudo: unable to lookup via setHostbyName()
```
I'm no expert by any means, but here is a tip, and a tip only.  Make sure you don't name your computer anything that starts with the "-" character (or perhaps "--", as was in my case... silly me).  It was an odd thing for me to do in retrospect, but as I stand as living proof, people do try and name their computers in such a manner.  Anyway, I reinstalled abiding by the aforementioned and all my problems were solved.

---

### Post by big_gie on 2006-07-27
I managed to workaround the “booting stalls during mounting root filesystem” bug with my Intel P4 EMT64 with a Asus P5LD2-VM DH motherboard ([http://www.asus.com/products4.aspx?l1=3&l2=11&l3=0&model=1146&modelmenu=1)](http://www.asus.com/products4.aspx?l1=3&l2=11&l3=0&model=1146&modelmenu=1)).

The problem was that the motherboard contains many disk controllers:
Intel ICH7 DH South Bridge:
1 x UltraDMA 100/66/33
4 x Serial ATA 3Gb/s, RAID0, RAID1, RAID5, RAID10
ITE IDE controler:
1x UltraDMA 133/100

I only have 1 HD and 1 DVD. Nothing on the SATA.

The HD was on the “ITE IDE controler UltraDMA 133/100&#8243; and the DVD on the “Intel ICH7 DH South Bridge UltraDMA 100/66/33&#8243;.

Saddly, only the “Intel ICH7 DH South Bridge&#8243; seem to be linux bootable (Windows XP x64 boots corectly from a HD connected to it). So the LiveCD boots (from “Intel ICH7 DH South Bridge”, install, but when I reboot, the machine “try” to boot from “ITE IDE controler” but can’t (this is still obscur...), thus the "Waiting for root filesystem" problem, followed by the busybox shell.

_**The workaround I used was :**_
[B]
1. Install from the LiveCD x86 32 bits[/B]
Be sure the drives are connected as the begining:
> 
HD -> Intel ICH7 DH South Bridge
DVD -> ITE IDE controler


**2. Shutdown**
Not to hard... :)

**3. Switch Cables**
Switch cables between the HD and DVD, so they end up like this :
HD -> ITE IDE controler
DVD -> Intel ICH7 DH South Bridge

**4. Boot**
Nothing needed to be edited.

NB. I must add also that since I don't use SATA drives, in the BIOS I  change the SATA controller to act as RAID, to be sure it didn't get in the way.

NB2. I tryed this with the 64bit edition and got the same error... I'm to tired to try another time with the 32 bit...

---

### Post by cracker on 2006-08-02
I have found a solution to the issue where the LiveCD stalls at "Mounting root filesystem" and/or "Adding liveCD user". I have tried two different drives. On the older drive, it would hang at mounting root filesystem. I bought two brand new BenQ DVD burners, and found that it hangs at Adding LiveCD user. The solution is to **switch to TTY1 as soon as "Mounting Root Filesystem" shows up**. The system just hangs if you let it be, but if you switch to TTY1 by pressing Alt+F1 as soon as the text shows up in the semi-graphical mode, the system boots successfully in a normal fasion. I hope this will help someone else.

---

### Post by SnuggieWuggie on 2006-08-05
This seems to be the approriate place for this so let me get started.

First of all, this is from personal experiance with a client's PC. I figured I'd share it since the 5.04 Guide to do this was a bit out of date.
This is kind of ripped from my experiance trying to use [http://www.ubuntuforums.org/showthread.php?t=33142]("http://www.ubuntuforums.org/showthread.php?t=33142")
So here goes,

1: Boot into your BIOS setup (usually when you're booting, you will have to press [maybe even hold] F1, F2, Escape, or similiar to enter the BIOS setup, once you're in, find the settings for "Default Graphics Card."
If it's set to Onboard, leave it. If it's set to PCI, change it to onboard, save and exit, and boot with the monitor plugged into the onboard card with Dapper drake ready to install, or.. boot into dapper.
2: Once in, update your kernel if it needs it - and reboot into the new kernel. Once that's over with, install the nvidia drivers (sudo apt-get install nvidia-glx nvidia-kernel-common) and.. sudo nvidia-glx-config enable then! Add nvidia to /etc/modules - you'll have to be root to edit it, so sudo nano or gedit or whatever you like.
3: Edit /etc/X11/xorg.conf and change whatever the device for your video card to..
```
Section "Device"
        Identifier "NVIDIA Corporation NV34 [GeForce FX 5500]"
        Driver "nvidia"
        BusID "PCI:1:9:0"
        Option "NvAGP" "1"
        Option  "RenderAccel" "true"
	Option "NoLogo" #This is optional - it will hide the NVIDIA splash screen
        #0 : Disable AGP
        #1 : use NVIDIA's internal AGP support, if possible
        #2 : use AGPGART if possible
        #3 : use any agp support (try AGPGART, then NVIDIA's AGP)
EndSection
```
Change the BUSID as approriate from your output of lspci -X (you want it to be the one for your nvidia card)
Make sure you update the md5sum of /etc/X11/xorg.conf [will add this as soon as I remember how..]
4: Reboot into the BIOS and set it back to PCI rather then onboard, try to boot with the plug on the PCI card, and see where it gets you.
If it freezes on "Loading hardware drivers" or similiar, don't worry, it did it to me too. Just reboot, setting it **back** to onboard again and plugging it into the onboard card. It should boot fine that way.
Now to blacklist the drivers for the Intel Card..
5: add these two lines:
```
blacklist intel_agp
blacklist agpgart
```
to /etc/modprobe.d/blacklist - save, and reboot and switch to PCI.. you know the drill. :---)
6: Should work fine now. Enjoy. :)
7: If it fails, boot into save mode and undo the blacklist and do dpkg-reconfigure xserver-xorg - make sure you ctrl+alt+backspace before you do, which kills the currently running X Server.

Cheers.
I will edit/fix this as needed.. I know it needs some work.

---

### Post by Kodiak3000 on 2006-08-07
I will start by saying that I am a complete and utter newbie, but I had a problem this morning that I found on at least two different threads, and neither one of them addressed the "solution" I eventually got to work for me.

I've had 6.06 installed on a brand new machine for a week now.  It's been working great, then all of a sudden this morning it froze at "Mounting Root File System".  I rebooted, cold rebooted, booted from the CD, you name it - I always got the same thing.

I went into BIOS, and found that the "Quick Boot" option was enabled.  This allows the OS to bypass certain tests while booting, which saves time.  I decided to disable this, which I guess allowed the system to check itself.  I also rebooted from the CD using "Start or Install" option.

That got me past the freeze and Ubuntu started up, but it started  with the "generic" desktop, logged itself in as "Ubuntu" and offered me the option to install.  I was hoping not to have to do that, so I rebooted (from the menu this time, yay!) and removed the CD.  

It started fine, and all my data is still there.

I'd love to know if this helps anyone, so please let me know!

Cheers

---

### Post by billdbrk on 2006-08-10
This post describes how I worked around several problems that I ran into installing Ubuntu server on a Dell PowerEdge 2900 with a PERC5/i RAID controller and 3 160 GB SATA drives comprising a single RAID 5 array.  

To begin with, the installer showed the individual drives (sda, sdb, sdc) *and* the RAID device (sdd).  I partitioned /dev/sdd and tried to continue the install, but it quit when formatting the partitions I set up and  complained that there was insufficient space on one of the partitions. I went back to the partitioning screen and deleted an existing partition that was being shown on /dev/sda.  This allowed the install to complete, but when I rebooted the newly installed system Grub hung with an error 21 when trying lo load stage 1.5.

I worked around this problem by starting the install again, but this time I hit Ctrl-Alt-F2 when I got to the http proxy screen.  At this point I issued the following two commands:

> modprobe -r megaraid_sas
modprobe megaraid_sas

Ctrl-Alt-F1 got me back to the install procedure and when I continued the the only disk that showed up was the RAID 5 array (/dev/sda).  I partitioned it again and the install went smoothly.  

When I rebooted, Grub loaded all stages successfully and started to boot.      It then hung while looking for the root filesystem and eventually dropped me into a busybox shell.  The keyboard did not work so I had to reboot with the power button.  I booted the machine with the server CD and chose Repair a Broken System from the menu.  I went through everything up until the hard drive detection completed which showed 4 hard drives and the partitions on each.  

I escaped to a shell using Ctrl-Alt-F2 again and was able to determine that the megaraid_sas was not part of the initial ramdisk (initrd.img-2.6.15-23-amd64-server).  I corrected this by the following set of commands:

> modprobe -r megaraid_sas
modprobe megaraid_sas
mount /dev/sda1 /mnt       (or maybe it was /dev/sdd1)
mount /dev/sda3 /mnt/usr   (or /dev/sdd3)
chroot /mnt
echo "megaraid_sas" >> /etc/mkinitramfs/modules
update-initramfs -u -k 2.4.15-23-amd64-server
exit
shutdown -r now

I had to use the power button again as the shutdown process hung.  When it rebooted, it still would not boot and it dropped into a busybox shell again. To get around this I again rebooted with the CD and chose the Repair a Broken System option, escaped to a shell after the disk detection with Ctrl-Alt-F2, and did the following:

> vi /boot/grub/device.map
I changed the line > (hd0)   /dev/sda to
> (hd0)   /dev/sdd

Then I did the following:

> vi /boot/grub/menu.lst
and changed 
> 
/boot/vmlinuz-2.6.15-23-amd64-server root=/dev/sda1 ro quiet splash


to this

> 
/boot/vmlinuz-2.6.15-23-amd64-server root=/dev/sdd1 ro quiet splash


Then I edited the file /etc/fstab:
> vi /etc/fstab
and I changed all occurances of [COLOR="Plum"]sda[/COLOR] to [COLOR="Plum"]sdd[/COLOR].

When I rebooted this time, the system booted properly.  However, the network interface was not working, so I executed the following commands:

> 
<login as non-root user>
sudo sh
<enter non-root user password>
modprobe -r bnx2
modprobe tg3

and configured eth0 by hand - resulting in a functioning network.  The first thing I did was the following:

> apt-get update
apt-get install -f gcc g++ make kernel-package fakeroot
mkdir /usr/local/src/new-kernel
chown *user.group*  /usr/local/src/new-kernel


where *user* and *group* are the username and group for a non-root user.  Then I downloaded the source for the latest stable kernel from a mirror of [www.kernel.org]("http://www.kernel.org") which was 2.6.17.8.  I then compiled and installed the new kernel by first
logging in as non-root user and then using he following commands:
> 
cd /usr/local/src/new-kernel
wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.17.8.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.17.8.tar.bz2)
bunzip2linux-2.6.17.8.tar.bz2
tar xvflinux-2.6.17.8.tar 
cd linux-2.6.17.8
make mrproper
cp /boot/config-2.6.15-23-amd64-server config
make oldconfig

I was prompted to choosed several new options and just kept the defaults.
When the configuration was done I used the follwing commands:
> 
make-kpkg clean
fakeroot make-kpkg --revision=custom.1.0 kernel_image
dpkg -i ../kernel-image-2.6.17.8_custom.1.0_amd64.deb
update-initramfs -c -k 2.6.17.8

The last steps were to reverse the above changes to /boot/grub/device.map, /boot/grub/menu.lst, and /etc/fstab.  Then it was necessary to insert the following line
> 
initrd          /boot/initrd.img-2.6.17.8

below the following line
> 
kernel          /boot/vmlinuz-2.6.17.8 root=/dev/sda1 ro quiet splash

and again after
> 
kernel          /boot/vmlinuz-2.6.17.8 root=/dev/sda1 ro single


Now I rebooted with the new kernel and was ready to go.

---

### Post by greenhat on 2006-08-11
I gotta say I'm a little dissapointed.  I just downloaded 6.06.1 and reinstalled hoping this problem would be fixed with the update and no dice. ](*,) 

I expected that since this problem has been known for such a long time and is apparently well understood by the developers that they would have included the fix in the 6.06.1 update.

Oh well, maybe next time. :roll:

---

### Post by ubuntu_demon on 2006-08-11
> **greenhat said:**
> I gotta say I'm a little dissapointed.  I just downloaded 6.06.1 and reinstalled hoping this problem would be fixed with the update and no dice. ](*,) 

I expected that since this problem has been known for such a long time and is apparently well understood by the developers that they would have included the fix in the 6.06.1 update.

Oh well, maybe next time. :roll:
What problem are you talking about ?

If you are talking about the UDEV / mounting root file system bug then take a look here :
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/)

If they would backport the fix from Edgy at this point other stuf f will probably break.

---

### Post by greenhat on 2006-08-11
> **ubuntu_demon said:**
> What problem are you talking about ?

If you are talking about the UDEV / mounting root file system bug then take a look here :
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/)

If they would backport the fix from Edgy at this point other stuf f will probably break.

Sorry - guess that wasn't very clear was it :oops: 

I was referring to the "bug mounting root filesystems" problem.

Thanks for the link.  Guess I can start waiting for Edgy :-#

---

### Post by ubuntu_demon on 2006-08-11
> **greenhat said:**
> Sorry - guess that wasn't very clear was it :oops: 

I was referring to the "bug mounting root filesystems" problem.

Thanks for the link.  Guess I can start waiting for Edgy :-#
Yeah you should wait for Edgy. Shouldn't be a long wait : [https://wiki.ubuntu.com/EdgyReleaseSchedule](https://wiki.ubuntu.com/EdgyReleaseSchedule)

---

### Post by ubuntu_demon on 2006-08-17
From [https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/) :

[quote=Scott James Remnant]
Officially marking as Rejected for dapper.

Here is the reasoning:

- We applied the &#8220;fix&#8221;, as planned, to the udev in Edgy Eft.

- While the fix corrected the problem described here, it caused new problems. Because it was a fundamental change to device ordering, it changed the order of other devices where more than one existed in the system &#8212; including other disks

- For Edgy this was not a problem, as the upgrade makes other changes that make device order non-important anyway

- These changes are too invasive for backporting to dapper

- This bug has a known workaround, which can be applied by the minority of users affected by it

- That workaround is preferable to causing far more working systems to cease functioning.
[/quote]

---

### Post by PaulP on 2006-09-28
The development of the foo2oak driver has been discontinued by the author
(see [http://http://foo2oak.rkkda.com/]("http://http://foo2oak.rkkda.com/")) mainly because of lack of support from HP.

As a result the foo2oak driver was withdrawn from the foo2zjs package
although the foo2oak-wrapper and support files are still present.

If you are unable to print on your Laserjet 1500 or other OAKT printer
you can either search for an older package or drop me a line,
since I kept a copy of the driver from an older download.

Also feel free to tell HP what you think of their support for Linux users. :evil:

---

### Post by dbrunoNJ on 2006-10-12
I recently decided to return to the gnu/linux world after a good 4 year hiatus or so - and I'm damn glad I did!

Anyways, here was my experience attempting to install flavors of Ubuntu on an old P3 550mhz, 256mb RAM system.  Symptoms seemed to cross "flavors" and be universal.  For tracking purposes, I made attempts using Xubuntu Live, Xubuntu Alternate, and Edubuntu Alternate.

_Initial Attempts_
[LIST]
[*]Live - after Xubuntu splash screen "loading restricted drivers..." it drops back to "Uncompressing kernel...." and freezes.  Documented issue on these forums.
[*]Alternate - install initiates and proceeds to point where it verifies CD then says the CD is not valid.  Documented on these forums as a CD-ROM detection issue.
[/LIST]

_2nd Attempts: using boot flag "ide=nodma"_
[LIST]
[*]Live - no difference from initial attempt except one occasion where it gave error (forget exact wording, sorry!) that it could not connect to TTY and then dropped to BusyBox
[*]Alternate - files seemed to load faster but otherwise the same as initial attempt
[/LIST]

_3rd Attempts: using boot flag "hdparm -d0 /dev/cdroms/cdrom0,"_
[LIST]
[*]Live - no difference from initial install
[*]Alternate - on initial occasion using the flag, install proceeded forward to point of partitioning tables, then errored out, not able to locate "proc" files; after that no change from initial attempts
[/LIST]

_4th Attempt: Install using a different cdrom drive and Edubuntu Alternate: Workstation Setting_
FLAWLESS AND DONE IN AN HOUR AND A HALF!!

Not the most elegant solution, as I'm lucky in that my house is a computer junkyard, but it works and that's really what I care about.  I was hoping to propose Edubuntu as a solution for a planned community computer school/computer center my non-profit is hoping to set up, and, I'm happy to say, it's looking pretty good!

---

### Post by jabberwoki on 2006-11-27
<package name here> : unable to make backup link of </path/to/file here> : Operation not permitted.


chattr -i directory path here/*

Hi I have this problem and i tried using this solution, I sudoed as root and issued following command  sudo chattr -i /usr/share/apt/.../hacks.mo

I also tried sudo chattr -i /usr/share/apt/.../* but annother file in the directory producews this error, flag not recognized

I didnt get a error as though it had worked but when checking the permissions thay had not changed and I did aptitude dist-upgrade but it produced the same error(as above)

The permissions on the file are owner > forbidden, Group > read, other > forbidden.  The group is a number as is the user and I cannot edit the permissions as root nor find the user or group in kuser either!

I,ve tried dkpg -i --force-overwrite <file> but this fails also, operation not permitted

I have also looked at the free space and it is not a problem

[http://wnywebdesigner.com](http://wnywebdesigner.com) standards based web development at a very resonable price!
[http://newyorkmounds.org](http://newyorkmounds.org)  thhe relationship between New york burial mounds and the Book of Mormon

 any ideas

---

### Post by jabberwoki on 2006-11-27
> **RavenOfOdin said:**
> **Q1.** Help! My packages are returning these errors!

```

<package name here> : unable to make backup link of </path/to/file here> : Operation not permitted.
dpkg-deb: Subprocess <package name here> killed by broken pipe: -1.
dpkg-deb: Error : Operation not permitted.

```

**A1.** Use the directory which is referenced by the */path/to* line and type, as root via sudo:

```

chattr -i *directory path here*/*

```

chattr -i (immutable) removes any special permissions on the file in question, like write-protect, so you can then create the backup link. If the error is instead:

```

<package name here> : unable to replace  </path/to/file here> 

```

do as above.

**Q2.** My packages won't configure via dpkg!

**A2.** At the command line type:

```

dselect

```

then at the menu, options of which should be 1 through 6, choose 4: [C]onfig. Follow the instructions it gives you after that and watch as dselect configures your packages.

**Q3.** My installer bails with something like "<file name> is trying to overwrite file in </path/to/file here> which belongs to package <package here>."

**A3.** To correct this error, go to console and type:

```

sudo dpkg -r <name of package>

```

and once it asks for your account password, type that password in and package removal will commence. You'll then be able to install your new package file over where the old one was.

**Q4.** Package A depends on Package B to install, but Package B depends on Package A to install! HELP!

**A4.** Was your install broken at some point along the line?
Did you need to remove packages which never got removed?
Go into the console, or your GNOME panel. Type:

```

sudo synaptic

```

or go to System > Accessories > Synaptic Package Manager.
In the "Filters" menu under "View", unmark everything except broken repositories, so only those display.  Then, mark the broken packages (symbolized by little red boxes) for reinstallation. If Synaptic wants to remove a bunch of packages while doing so, fine. Let it.

The package installation system is in my experience more intelligent via this than Adept, which whines on dependency problem creation.  It'll detect dependency problems and readjust accordingly.

Once again though, this is only my experience. Your mileage may vary, and before you remove *any* packages you should - just as a matter of common sense - know what you are removing.  

After this is done, your circular dependencies should resolve themselves.

That's it. I hope I helped a few of y'all out there with this, let me know if I made any mistakes or screwed anything up badly ... I hope not.
<package name here> : unable to make backup link of </path/to/file here> : Operation not permitted.


chattr -i directory path here/*

Hi I have this problem and i tried using this solution, I sudoed as root and issued following command  sudo chattr -i /usr/share/apt/.../hacks.mo

I didnt get a error as though it had worked but when checking the permissions thay had not changed and I did aptitude dist-upgrade but it produced the same error(as above)

I also tried sudo chattr -i /usr/share/apt/.../* but annother file in the directory producews this error, flag not recognized

The permissions on the file are owner > forbidden, Group > read, other > forbidden.  The group is a number as is the user and I cannot edit the permissions as root nor find the user or group in kuser either!

I,ve tried dkpg -i --force-overwrite <file> but this fails also, operation not permitted

I have also looked at the free space and it is not a problem

[http://wnywebdesigner.com](http://wnywebdesigner.com) standards based web development at a very resonable price!
[http://newyorkmounds.org](http://newyorkmounds.org)  thhe relationship between New york burial mounds and the Book of Mormon


**UPDATE**
I have resolved this problem, well by fluke anyway it seems I needed to run fsck to repair my filesystem the inode I was having trouble with was miss reporting its size 1.2GB? and was other problems fsck fixed the problems and I was able to finish the install(also had to reinstall grub twice!) but now I have a new problem I cannot run any apps as root, well not from the run box or gui anyway I will try the terminal. I will post this problem elsewhere thanks.

---

### Post by phormion on 2006-11-28
I've had troubles of my own with the Dapper -> Edgy upgrade. Here's a description of the problem, it concerns alsa sound output with a soundcard that can't do HW mixing, and also the solution. The ugly part is, this is missing from the release notes, although the guy who was assigned the bug specifically says it should be documented there. 

[http://ubuntuforums.org/showthread.php?t=307871](http://ubuntuforums.org/showthread.php?t=307871)

---

### Post by drakferion on 2007-09-12
I'm sorry if i'm posting this and someone else did it already...
I've searched the forum and read this thread until the second page - but honestly, i can't waste more time just to provide help.
If i did, i don't think i'd ever come back to help anyone. >_<


I have a freshly installed Kubuntu 7.04 system.
I updated/upgraded the system.
But despite having up-to-date gcc i didn't have libc-dev, which prevented me from compiling properly.

Perhaps this is a problem with the packaging system?
Thanks for your time.

(If you want to ensure a response from me, please email me. I created this account purely to report this problem, this is not a forum i visit. Thanks for understanding.)

---

