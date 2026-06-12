---
title: "Time to upgrade my 14.04 LTS"
date: 2019-01-10
forum: Installation &amp; Upgrades
---

### Post by gumbo64 on 2019-01-10
Come February my beloved 14.04 LTS  will no longer be supported so I guess I am forced to upgrade.

I wonder what would be the less painful way to do it. 
I am not at all concerned about hardware issues as I can easily test the new release live (or even with a permanent install on another drive), and I am not concerned about data loss. Most data are on a separate drive and I can easily backup the home folder to the same drive or others.

What worries me is retaining the software packages which I installed through the years and need to keep.
I don't want to be in the situation when I need a software and it's no longer available on my machine, or unusable.
Some required adding specific PPA's and for sure some are no longer available.
Major concern is also related to V-box as I use it A LOT to run Win7 for CAD applications which are not available on Linux.

Any advice as to what release I should upgrade to, in order to reduce the chance of issues, would also be much appreciated. 
I think I read somewhere some months ago, that in 18.04 it is no longer possible to launch programs as root (such as Nautilus for example).
Not sure if there is a workaround to this problem, but this fact alone would be enough to keep me from upgrading to 18.04.

As far as the machine the system is running on, it is I3 with an integrated Intel Video board and 6 gigs of RAM.
Wonder if I should evaluate upgrading to a lighter version of Ubuntu as the machine is not "old" but it's not new either, and how this would impact on the upgrade.

Any help would be greatly appreciated.

Edit: Forgot to mention I am only considering upgrades to LTS versions.

---

### Post by ajgreeny on 2019-01-10
I think that you should do a clean install as you will otherwise have to manage two separate upgrade processes, first from 14.04 to 16.04, and then from 16.04 to 18.04 which will both take a long time and will also double the opportunities for problems to occur.

I have never used the upgrade process from one OS version to the next so I am perhaps speaking from a partisan point of view, and I know some users manage online upgrades without too many problems, so it is your choice, but I know what I would do.

As to your list of manually installed applications that you want to be certain will still work, it is impossible to comment as we have no idea what they are, or were.  If you show us a list of those applications we may be able to help more with that query.

Your major concern about VBox is one you can forget; I use VBox-6.0 which I keep updated using the Oracle repos, set up according to the info in the **"Debian-based-Linux-Distributions"** section at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads).  It is working fine with Windows-XP and also Windows-7 so you ought not to have a problem with that; I just ensure I have a good working snapshot of both of those just in case they become corrupted or virus infected.  Make sure you install the correct same version of the Guest additions pack which you can download from [https://download.virtualbox.org/virtualbox/6.0.0/Oracle_VM_VirtualBox_Extension_Pack-6.0.0.vbox-extpack](https://download.virtualbox.org/virtualbox/6.0.0/Oracle_VM_VirtualBox_Extension_Pack-6.0.0.vbox-extpack) and you should get great performance, or at least as good as you did in 14.04 if you allocate the same amount of RAM to the guest
.

There are also ways to overcome the potential problems of not being able to use gksudo (no longer available) if you wish to use nautilus as root, very dangerous but I'm aware many use it that way, so we can work around that problem with you if you if you are unable to, or do not want to do things in command line.

I think your machine should be able to run the gnome version (the default now) of Ubuntu even in VBox, but as you can see, I use Xubuntu and have done so for many years, preferring Xfce4 to any other DE available.

Again it's your choice; use whichever DE you want or which works best for you.

---

### Post by CatKiller on 2019-01-10
Since you're already familiar with VMs, you can play with both 16.04 and 18.04 in a VM to see what's available for each of them.

It's possible to export a list of all the packages you've installed so that you can then simply install all of them again in one go.

All the environments are pretty snappy these days - there's not much between them for system requirements as long as you're on 64-bit. It's only really web content that drives the need for bigger and faster now, and that's going to be the same whichever environment you prefer.

---

### Post by gumbo64 on 2019-01-10
What if I run 

sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade -y: 
sudo do-release-upgrade

and maybe 

sudo apt-get autoremove -y

As far as GKSU, can I install it from 

[https://pkgs.org/download/gksu](https://pkgs.org/download/gksu)

or follow this guide 

[https://ubuntu-mate.community/t/for-anyone-who-still-needs-or-wants-gksu/16744/5](https://ubuntu-mate.community/t/for-anyone-who-still-needs-or-wants-gksu/16744/5)

---

### Post by gumbo64 on 2019-01-10
And a list of the most commonly used applications:

Blender
QCad
Freecad
Meshmixer
Meshlab
Ultimaker Cura

Gimp 
Inkscape
Phatch

Disks 
Freefilesync
TarGui
FSlint
GrSync with GUI
Kompare
Meld
Unison
Filelight

Shotcut
Kdenlive
SynfigStudio
SimpleScreeRecorder
Audacity

Cairodock
Filezilla 
Unetbootin
Vbox
Firefox bookmarks

Some of these apps have settings and profiles which would take a lot of time to recreate if at all possible...like the printer profile settings in Cura, just to name one.

---

### Post by CatKiller on 2019-01-10
> **gumbo64 said:**
> Some of these apps have settings and profiles which would take a lot of time to recreate if at all possible

Settings are kept in your Home folder. You should be back that up, generally, anyway. Many people choose to keep /home as a separate partition to make reinstalls easier.

If you go for 16.04 you don't need to upgrade unless you want to before 2021. If you go for 18.04 you get till 2023. Either option is fine.

I've never had any real problems with upgrading-in-place, but others have. It's something to be aware of as a possible outcome.

[This]("https://unix.stackexchange.com/questions/3595/list-explicitly-installed-packages/3624#3624") seems like a fairly in-depth answer to getting the list of packages that you've explicitly installed yourself. There are simpler ways of simply getting a list of all the installed packages if you just want replication.

---

### Post by gumbo64 on 2019-01-10
Is it possible to make copy of the whole drive onto another drive to see what happens when I upgrade ?
I remember it required a specific procedure with windows, like creating a "ghost" image of the original drive. Many years since I switched to Linux so this could be out of date now.
Anyway, is a "special" procedure required also in linux/ubuntu or a simple "copy" of the original drive will do, for testing purposes ?

---

### Post by CatKiller on 2019-01-10
It depends how precise you want the copy to be.

dd will copy everything bit-for-bit, so it will be an exact clone. You won't be able to boot with both copies attached, since the UUIDs of the partitions (used to identify which partition to boot from) will be replicated too, and it will take ages because it will copy the empty parts too.

Any of Déjà Dup, rsync or tar will be fine for just copying the files. If you're on UEFI you'd need to make a new EFI partition (which I'm hazy on), or on BIOS you'd need to install GRUB to the MBR, before you could boot from the new drive.

If it were me, I'd play around with both 16.04 and 18.04 in VMs to see which I disliked the least, make sure my backups were adequate, and then do the upgrade(s). If it all works: great, if not: fresh install and restore settings from backup. Then look at it again in a couple of years.

---

### Post by mastablasta on 2019-01-11
1. do a fresh install. there were so many changes between 14.04 and 16.04 in user interface as well as in background (systemd, grub changes...). i spent 6 hours on upgrade ending up in kernel panic system, then i did a clean install on 18.04 in 20 minutes.

2.
> **gumbo64 said:**
> Is it possible to make copy of the whole drive onto another drive to see what happens when I upgrade ?
I remember it required a specific procedure with windows, like creating a "ghost" image of the original drive. Many years since I switched to Linux so this could be out of date now.
Anyway, is a "special" procedure required also in linux/ubuntu or a simple "copy" of the original drive will do, for testing purposes ?

clonezilla will do that for you easily. they have a step by step guide (print it before launching clonezilla which uses text based menus. 

you can also just backup /home and /etc and restore only what is needed (maybe some settings etc.). settings for apps like firefox , filezilla... are all in hidden folders in /home

3. gksu is no longer supported. however instead of that you can use:

sudo -H *applicationname*

for more informaiton see here: [https://askubuntu.com/questions/270006/why-should-users-never-use-normal-sudo-to-start-graphical-applications](https://askubuntu.com/questions/270006/why-should-users-never-use-normal-sudo-to-start-graphical-applications)
here along with the second option - pkexec: [https://askubuntu.com/questions/287845/how-to-configure-pkexec](https://askubuntu.com/questions/287845/how-to-configure-pkexec)

debate on what to use in forums: [https://ubuntuforums.org/showthread.php?t=2130734](https://ubuntuforums.org/showthread.php?t=2130734)


Before upgrade you SHOULD backup at least all your data and at minimum the /home folder!!!

---

### Post by pauljw on 2019-01-11
Just to play devils advocate here, I have now done my 2nd version upgrade without doing a clean install.  My machine came with 13.10 installed and I upgraded to 14.04 when it became available.  Just last spring I upgraded to 16.04, again, no clean install and everything went very smoothly.  I don't see a need for you to go any further than 16.04 at this time.  I have virtualbox installed also and didn't experience any issues there.  As always, be sure to have your current setup fully up to date, then backup at least /home or use clonezilla to create an image, then i deselect ppa's and do the upgrade.  

My system is a Sys76 Gazelle Pro i7 w/16GB memory and 1T drive.

Good luck which ever way you choose, but thought your should know that not all of us just choose to wipe everything and start fresh.

---

### Post by gumbo64 on 2019-01-11
Thank you all for the advice !

One last question, I read 18.04 is supposed to get 10 years support instead of 5 but not sure if this long term support is offered also to desktop users. Any reliable news on the subject ?

---

### Post by deadflowr on 2019-01-12
> **gumbo64 said:**
> Thank you all for the advice !

One last question, I read 18.04 is supposed to get 10 years support instead of 5 but not sure if this long term support is offered also to desktop users. Any reliable news on the subject ?

It's 5 years for all, 5 extra years for those who purchase Ubuntu Advantage.
Indeterminate what will be included (packages-wise) for the extended maintenance support period.
But based on the ESM current list for 12.04, it'll be server-side heavy:
[https://wiki.ubuntu.com/SecurityTeam/ESM/12.04#Maintained_Packages]("https://wiki.ubuntu.com/SecurityTeam/ESM/12.04#Maintained_Packages")

---

