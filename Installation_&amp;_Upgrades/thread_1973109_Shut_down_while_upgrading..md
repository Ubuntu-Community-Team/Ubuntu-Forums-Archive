---
title: "Shut down while upgrading."
date: 2012-05-04
forum: Installation &amp; Upgrades
---

### Post by mrsjcmking on 2012-05-04
Okay so I was trying to update Ubuntu to latest version on my laptop. The dog then jumped up at the laptop and pulled the cable out - which caused the laptop to shut down (yes our laptop is that rubbish!)

So I turned on the computer and it started in terminal mode - managed to get the desktop back but it is obviously not right.

I cant find anything in the dash except my own files, There is no update manager at all. the bar at the top (im sure it has a technical term) just has a clock and nothing so I cant even shut down/reboot (unless I just press the button on my laptop).

What do i do - my husband will murder me when he finds out I screwed up the computer.

I am a complete idiot so when explaining how to fix this imagine that you are explaining it to a 5 yr old.

I know how to run the terminal - ive tried lots of basic commands like the sudo apt upgrade and the sudo config thingy but nothing works

PLEASE HELP

---

### Post by billyseth on 2012-05-04
My #1 suggestion, is before you continue trying to fix stuff, you should boot into a live CD, and use that to make sure you back up all your important files to a USB drive or something else.

---

### Post by mrsjcmking on 2012-05-04
I dont have anything majorly important as we've not had ubuntu long and I haven't saved much on here

I'm not bothered about losing files I just want it fixed before 6pm tonight!

---

### Post by mrsjcmking on 2012-05-04
> **billyseth said:**
> My #1 suggestion, is before you continue trying to fix stuff, you should boot into a live CD, and use that to make sure you back up all your important files to a USB drive or something else.

What does boot into a live CD mean?

Seriously I have no idea about computers - imagine i'm blonde, roll your eyes and sigh before explaining it again really really really simply

---

### Post by mörgæs on 2012-05-04
The only thing that can assure you have something running that soon is a fresh install.

---

### Post by mrsjcmking on 2012-05-04
How do I do a fresh install???

---

### Post by ronaldbrijo on 2012-05-04
You need to use the install cd and boot the Pc with it in the cd drive. 

Ubuntu will then prompt you what to do.

---

### Post by mrsjcmking on 2012-05-04
Thank you Ronald - am now going on a CD hunt as I assume the man has it somewhere safe!

---

### Post by mrsjcmking on 2012-05-04
I only have 11.1 version on disc and I can't get it to run

I have also tried downloading the install and it wont work - just gets stuck at 11% and then says failed

---

### Post by mrsjcmking on 2012-05-04
It says this when trying to install from a disc - 

Archive:  /media/Ubuntu 11.10 i386/ubuntu/wubi.exe
[/media/Ubuntu 11.10 i386/ubuntu/wubi.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/Ubuntu 11.10 i386/ubuntu/wubi.exe or
          /media/Ubuntu 11.10 i386/ubuntu/wubi.exe.zip, and cannot find /media/Ubuntu 11.10 i386/ubuntu/wubi.exe.ZIP, period.

---

### Post by ronaldbrijo on 2012-05-04
are you installing from within windows?

---

### Post by mrsjcmking on 2012-05-04
Uhm I don't think so.

Basically I had Ubuntu, I went to update, the dog pulled the cable out and the laptop died halfway through the update so my computer thinks I am running ubuntu 12.04 but it is missing quite a few features - the update manager and all the apps on the dash being the main things. When I search for anything on the dash it can't find it. All i have left are my files.

It seems to have half updated - but I can't finish it because I dont have the update manager!!!

---

### Post by ronaldbrijo on 2012-05-04
Ok, lets try something else...

U say you can get to terminal?

So use the following commands to try and force an upgrade\update:

sudo sed -i 's/oneiric/precise/g' /etc/apt/sources.list sudo apt-get update sudo apt-get dist-upgrade sudo apt-get upgrade

---

### Post by ronaldbrijo on 2012-05-04
sudo sed -i 's/oneiric/precise/g' /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get upgrade

---

### Post by mrsjcmking on 2012-05-04
the first one it tells me doesnt exist

I tried the second one and it went through a long list of things and seemed to work

do i try the other 2 as well?

---

### Post by mrsjcmking on 2012-05-04
okay so I tried the last 2 and they both come up with the same thing...this

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 aptdaemon : Depends: python-aptdaemon (= 0.43+bzr805-0ubuntu1) but 0.43+bzr697-0ubuntu1.2 is installed
 python-aptdaemon.gtk3widgets : Depends: python-aptdaemon (= 0.43+bzr805-0ubuntu1) but 0.43+bzr697-0ubuntu1.2 is installed
 python-aptdaemon.gtkwidgets : Depends: python-aptdaemon (= 0.43+bzr805-0ubuntu1) but 0.43+bzr697-0ubuntu1.2 is installed
 software-center : Depends: software-center-aptdaemon-plugins but it is not installed
                   Depends: python-debtagshw but it is not installed
                   Recommends: xz-lzma but it is not installed
E: Unmet dependencies. Try using -f.

---

### Post by ronaldbrijo on 2012-05-04
yes do that

---

### Post by ronaldbrijo on 2012-05-04
try  

sudo apt-get -f install

---

### Post by mrsjcmking on 2012-05-04
I think its working...how will I know if its worked?

---

### Post by mrsjcmking on 2012-05-04
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  libreoffice-l10n-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gir1.2-gudev-1.0 python-aptdaemon python-debtagshw
  software-center-aptdaemon-plugins
The following NEW packages will be installed
  gir1.2-gudev-1.0 python-debtagshw software-center-aptdaemon-plugins
The following packages will be upgraded:
  python-aptdaemon
1 upgraded, 3 newly installed, 0 to remove and 475 not upgraded.
6 not fully installed or removed.
Need to get 0 B/102 kB of archives.
After this operation, 309 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 158674 files and directories currently installed.)
Preparing to replace python-aptdaemon 0.43+bzr697-0ubuntu1.2 (using .../python-aptdaemon_0.43+bzr805-0ubuntu1_all.deb) ...
Unpacking replacement python-aptdaemon ...
Selecting previously unselected package software-center-aptdaemon-plugins.
Unpacking software-center-aptdaemon-plugins (from .../software-center-aptdaemon-plugins_0.1.2_all.deb) ...
Selecting previously unselected package python-debtagshw.
Unpacking python-debtagshw (from .../python-debtagshw_1.9+git20120320_all.deb) ...
Selecting previously unselected package gir1.2-gudev-1.0.
Unpacking gir1.2-gudev-1.0 (from .../gir1.2-gudev-1.0_175-0ubuntu9_i386.deb) ...
Setting up python-aptdaemon (0.43+bzr805-0ubuntu1) ...
Setting up aptdaemon (0.43+bzr805-0ubuntu1) ...
Setting up python-aptdaemon.gtk3widgets (0.43+bzr805-0ubuntu1) ...
Setting up language-selector-gnome (0.79) ...
Setting up software-center-aptdaemon-plugins (0.1.2) ...
Setting up python-debtagshw (1.9+git20120320) ...
Setting up software-center (5.2.1) ...
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
Software catalog update was successful.
Setting up python-aptdaemon.gtkwidgets (0.43+bzr805-0ubuntu1) ...
Setting up python-aptdaemon-gtk (0.43+bzr805-0ubuntu1) ...
Setting up gir1.2-gudev-1.0 (175-0ubuntu9) ...


Thats what it says now...

---

### Post by Gremlinzzz on 2012-05-04
> **ronaldbrijo said:**
> are you installing from within windows?

is it a wubi or dual boot installation:popcorn: or pure Ubuntu:popcorn:

---

### Post by mrsjcmking on 2012-05-04
> **Gremlinzzz said:**
> is it a wubi or dual boot installation:popcorn: or pure Ubuntu:popcorn:


?!?!?!

I have no idea what any of that means...

---

### Post by Gremlinzzz on 2012-05-04
> **mrsjcmking said:**
> ?!?!?!

I have no idea what any of that means...

I think im to late to the party sounds like ronaldbrijo fixed it:popcorn:

installations
Wubi installing inside of windows like a program
Dual boot installing side by side with windows in a partition made on the harddrive.
Pure Ubuntu means no windows just Ubuntu on your laptop

---

### Post by mrsjcmking on 2012-05-04
nope still not working properly...argh i hate computers

I think the hubby is going to have to do it from scratch

---

### Post by ronaldbrijo on 2012-05-04
Sorry mrsjcmking... had to logout for a bit...

Any progress?

---

### Post by hyperlocalguy on 2012-05-06
Was this ever resolved? I have the exact same aptdaemon dependency error.  (and I see where it's mentioned as a bug in other places).  sudo apt-get -f install can't seem to do anything about it.  (I was upgrading from the previous version to 12.04)

Additional info: dpkg: error:parsing file '/var/lib/dpkg/status' near line 34293... Returned an error code (2)

It refers to a package I have attempted to remove in the past, but have been unsuccessful so far.

Can anyone advise me?

---

