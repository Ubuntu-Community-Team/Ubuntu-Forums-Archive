---
title: "open office 3.2 release candidate rocks"
date: 2009-12-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by nanog on 2009-12-28
I've gotten rid of default open office on all of my installs!

The improvements:

*Huge decrease in start-up time and increased application spped
*Better support of MS Office documents including embedded ole data.
*Numerous bug fixes to impress (this program might actually become useable by the non-hobbyist).
*New graph types in calc.
*Improved copy and paste and merged field support in calc (finally!).

Whats not fixed:

*Arial narrow needs to be manually installed (*sigh*).
*Excel ole graphs in impress still have boundary bug. 
*Numerous font issues with ms office ole inserts in impress and calc.

---

### Post by nanog on 2009-12-28
And from the sound of things this will likely end up being default in lucid:

ccheney:
> Empty for now, will likely have OOo 3.2.0/3.2.1 debs for Karmic/Lucid later in the cycle.

[https://launchpad.net/~openoffice-pkgs](https://launchpad.net/~openoffice-pkgs)

---

### Post by sports fan Matt on 2009-12-28
how can one test this?

---

### Post by ranch hand on 2009-12-28
So where are you getting this?

---

### Post by ronacc on 2009-12-28
you can get a deb from here [http://download.openoffice.org/all_rc.html#untested-full](http://download.openoffice.org/all_rc.html#untested-full)

---

### Post by Merk42 on 2009-12-28
Is this all under the hood stuff or is there any noticeable GUI changes?

I see it's 3.3 which is the release of Renaissance aka "We'll just make our UI look like Microsoft Office even though we totally said we weren't just going to mimic the ribbon from Microsoft Office"

---

### Post by benjamimgois on 2009-12-28
Openoffice keeps getting better and better, let's hope that Oracle put some more effort on it's development and speed up the addition of new features and improve compatibility.

---

### Post by ranch hand on 2009-12-28
> **ronacc said:**
> you can get a deb from here [http://download.openoffice.org/all_rc.html#untested-full](http://download.openoffice.org/all_rc.html#untested-full)
Thanks for that.  I have all these installs, this one running Alpha Boinc, another one may as well run "untested" OO.o.

---

### Post by VMC on 2009-12-28
Great news. I hope its as good as the OP says it is. I remember years ago how sluggish it was. I'm impressed with its current startup and usage. OO is one of those tools that is totally dependent on your needs. I never had files even come close to exceeding any limits. I have read of some people maxing out its limits.

---

### Post by donniezazen on 2009-12-28
> **ronacc said:**
> you can get a deb from here [http://download.openoffice.org/all_rc.html#untested-full](http://download.openoffice.org/all_rc.html#untested-full)

So what do i do with all these 100s of .debs? I am trying to open update in terminal but nothing happens. Terminal just comes for 1 second and nothing happens.

Thanks,
SK

---

### Post by andrewabc on 2009-12-28
For those patient, the final release should be out in a week or two according to [Detailed schedule for OpenOffice.org 3.2](http://wiki.services.openoffice.org/wiki/OOoRelease32).

Hopefully the PPA gets updated so people can easily update to it.

EDIT:
Looks like 3 bugs so far needs to be fixed before release, so I'm guessing another RC will be released.

---

### Post by ronacc on 2009-12-28
> **soham_1207 said:**
> So what do i do with all these 100s of .debs? I am trying to open update in terminal but nothing happens. Terminal just comes for 1 second and nothing happens.

Thanks,
SK

you can install them with gdebi , most of the ooobasis3.2-en-us debs you will have to use dpkg --force on because they dont see that the first one is already installed , the update script is for updating the pkgs it isnt an installer , one by one is the only way or else make yourself a local repo and use synaptic , that would probably run into the same problem with depends .I'll agree it takes forever only 1/2 done myself:lolflag:

---

### Post by tacantara on 2009-12-28
> **ronacc said:**
> you can install them with gdebi , most of the ooobasis3.2-en-us debs you will have to use dpkg --force on because they dont see that the first one is already installed , the update script is for updating the pkgs it isnt an installer , one by one is the only way or else make yourself a local repo and use synaptic , that would probably run into the same problem with depends .I'll agree it takes forever only 1/2 done myself:lolflag:

I am running into a problem using the dpkg --force command, as it is looking for additional information.  I looked at the help screen for dpkg --force and it didn't help clarify anything.  How should I structure the dpkg --force command?

---

### Post by VMC on 2009-12-28
> **soham_1207 said:**
> So what do i do with all these 100s of .debs? I am trying to open update in terminal but nothing happens. Terminal just comes for 1 second and nothing happens.

Thanks,
SK

There's not 100's only 12 deb files.
 Does anyone know how to use gdebi to include the 12 or is there more to download? It complains of "Error: Dependency is not satisfiable: openoffice.org3".

---

### Post by ronacc on 2009-12-28
sudo dpkg --force-all -i <pkg name>                    you can just type the firstpart of the pkg name and hit tab and it will autocomplete . what I did was make a seperate dir for pkgs I was going to force and did them one at a time , that way you only have to type the 1st letter of the pkg name and then hit tab.

---

### Post by VMC on 2009-12-28
> **ronacc said:**
> sudo dpkg --force-all -i <pkg name>                    you can just type the firstpart of the pkg name and hit tab and it will autocomplete . what I did was make a seperate dir for pkgs I was going to force and did them one at a time , that way you only have to type the 1st letter of the pkg name and then hit tab.

Thanks. I read [APT HOWTO]("http://debian-br.sourceforge.net/docs/sgml/apt-howto-en/online/ch-basico.html") explaining how to do it locally.See Section 2.2, but it didn't make much sense. I need to figure "package priority section" out.

Maybe I'll try to force the issue.

Edit: Did you force them in any type of order?

---

### Post by ronacc on 2009-12-28
I just did them in the order they are in a nautilus window . you only have to install the language pak for your language.

---

### Post by VMC on 2009-12-28
> **ronacc said:**
> I just did them in the order they are in a nautilus window . you only have to install the language pak for your language.

I did as you said, and tried one at a time. Then got cute and did this:
$ sudo dpkg --force-all -i DEBS/*
```
Selecting previously deselected package ooobasis3.2-en-us.
(Reading database ... 125276 files and directories currently installed.)
Unpacking ooobasis3.2-en-us (from .../ooobasis3.2-en-us_3.2.0-8_i386.deb) ...
Selecting previously deselected package ooobasis3.2-en-us-base.
Unpacking ooobasis3.2-en-us-base (from .../ooobasis3.2-en-us-base_3.2.0-8_i386.deb) ...
Selecting previously deselected package ooobasis3.2-en-us-binfilter.
Unpacking ooobasis3.2-en-us-binfilter (from .../ooobasis3.2-en-us-binfilter_3.2.0-8_i386.deb) ...
Selecting previously deselected package ooobasis3.2-en-us-calc.
Unpacking ooobasis3.2-en-us-calc (from .../ooobasis3.2-en-us-calc_3.2.0-8_i386.deb) ...
Selecting previously deselected package ooobasis3.2-en-us-draw.
Unpacking ooobasis3.2-en-us-draw (from .../ooobasis3.2-en-us-draw_3.2.0-8_i386.deb) ...
Selecting previously deselected package ooobasis3.2-en-us-help.
Unpacking ooobasis3.2-en-us-help (from .../ooobasis3.2-en-us-help_3.2.0-8_i386.deb) ...
Selecting previously deselected package ooobasis3.2-en-us-impress.
Unpacking ooobasis3.2-en-us-impress (from .../ooobasis3.2-en-us-impress_3.2.0-8_i386.deb) ...
Selecting previously deselected package ooobasis3.2-en-us-math.
Unpacking ooobasis3.2-en-us-math (from .../ooobasis3.2-en-us-math_3.2.0-8_i386.deb) ...
Selecting previously deselected package ooobasis3.2-en-us-res.
Unpacking ooobasis3.2-en-us-res (from .../ooobasis3.2-en-us-res_3.2.0-8_i386.deb) ...
Selecting previously deselected package ooobasis3.2-en-us-writer.
Unpacking ooobasis3.2-en-us-writer (from .../ooobasis3.2-en-us-writer_3.2.0-8_i386.deb) ...
Selecting previously deselected package openoffice.org3-dict-en.
Unpacking openoffice.org3-dict-en (from .../openoffice.org3-dict-en_3.2.0-8_i386.deb) ...
Preparing to replace openoffice.org3-en-us 3.2.0-8 (using .../openoffice.org3-en-us_3.2.0-8_i386.deb) ...
Unpacking replacement openoffice.org3-en-us ...
dpkg: openoffice.org3-dict-en: dependency problems, but configuring anyway as you requested:
 openoffice.org3-dict-en depends on openoffice.org-ure; however:
  Package openoffice.org-ure is not installed.
 openoffice.org3-dict-en depends on ooobasis3.2-core01; however:
  Package ooobasis3.2-core01 is not installed.
 openoffice.org3-dict-en depends on ooobasis3.2-core02; however:
  Package ooobasis3.2-core02 is not installed.
 openoffice.org3-dict-en depends on ooobasis3.2-core03; however:
  Package ooobasis3.2-core03 is not installed.
 openoffice.org3-dict-en depends on ooobasis3.2-core04; however:
  Package ooobasis3.2-core04 is not installed.
 openoffice.org3-dict-en depends on ooobasis3.2-core05; however:
  Package ooobasis3.2-core05 is not installed.
 openoffice.org3-dict-en depends on ooobasis3.2-core06; however:
  Package ooobasis3.2-core06 is not installed.
 openoffice.org3-dict-en depends on ooobasis3.2-core07; however:
  Package ooobasis3.2-core07 is not installed.
 openoffice.org3-dict-en depends on openoffice.org3; however:
  Package openoffice.org3 is not installed.
Setting up openoffice.org3-dict-en (3.2.0-8) ...

dpkg: ooobasis3.2-en-us: dependency problems, but configuring anyway as you requested:
 ooobasis3.2-en-us depends on ooobasis3.2-core01; however:
  Package ooobasis3.2-core01 is not installed.
Setting up ooobasis3.2-en-us (3.2.0-8) ...
Setting up ooobasis3.2-en-us-base (3.2.0-8) ...
Setting up ooobasis3.2-en-us-binfilter (3.2.0-8) ...
Setting up ooobasis3.2-en-us-calc (3.2.0-8) ...
Setting up ooobasis3.2-en-us-draw (3.2.0-8) ...
Setting up ooobasis3.2-en-us-help (3.2.0-8) ...
Setting up ooobasis3.2-en-us-impress (3.2.0-8) ...
Setting up ooobasis3.2-en-us-math (3.2.0-8) ...
Setting up ooobasis3.2-en-us-res (3.2.0-8) ...
Setting up ooobasis3.2-en-us-writer (3.2.0-8) ...
dpkg: openoffice.org3-en-us: dependency problems, but configuring anyway as you requested:
 openoffice.org3-en-us depends on openoffice.org3; however:
  Package openoffice.org3 is not installed.
Setting up openoffice.org3-en-us (3.2.0-8) ...

```Looks like I need more deb files.


Edit: I found this set of [instructions]("http://download.openoffice.org/common/instructions.html#linux") for rpm files. It appears I did the same thing, except I use '*' instead of *.deb'.

[COLOR="Red"]**Edit2**[/COLOR]: I missed the core package. I only got the language packs. I'm downloading it now.

---

### Post by ronacc on 2009-12-28
if you only got 12 debs you need more , which set did you download ? I d/l the full installation set and got about 48 or 49 debs , a couple I didn't install the kde integration and the fr and es dicts .

---

### Post by caryb on 2009-12-28
If you go to the folder containing the debs in a terminal session (konsole in Kubuntu) & type sudo dpkg -i *.deb

It will install this for you, a gotcha for me is it didn't setup a menu item for the application so I added it myself. The path to the installed files is /opt/openoffice.org3/program/soffice


Cheers Cary

---

### Post by donniezazen on 2009-12-28
> **VMC said:**
> There's not 100's only 12 deb files.
 Does anyone know how to use gdebi to include the 12 or is there more to download? It complains of "Error: Dependency is not satisfiable: openoffice.org3".

**IMHO that was an expression. But i do have 50 .deb files as following.**

> 
desktop-integration
ooobasis3.2-base_3.2.0-8_i386.deb
ooobasis3.2-binfilter_3.2.0-8_i386.deb
ooobasis3.2-calc_3.2.0-8_i386.deb
ooobasis3.2-core01_3.2.0-8_i386.deb
ooobasis3.2-core02_3.2.0-8_i386.deb
ooobasis3.2-core03_3.2.0-8_i386.deb
ooobasis3.2-core04_3.2.0-8_i386.deb
ooobasis3.2-core05_3.2.0-8_i386.deb
ooobasis3.2-core06_3.2.0-8_i386.deb
ooobasis3.2-core07_3.2.0-8_i386.deb
ooobasis3.2-draw_3.2.0-8_i386.deb
ooobasis3.2-en-us_3.2.0-8_i386.deb
ooobasis3.2-en-us-base_3.2.0-8_i386.deb
ooobasis3.2-en-us-binfilter_3.2.0-8_i386.deb
ooobasis3.2-en-us-calc_3.2.0-8_i386.deb
ooobasis3.2-en-us-draw_3.2.0-8_i386.deb
ooobasis3.2-en-us-help_3.2.0-8_i386.deb
ooobasis3.2-en-us-impress_3.2.0-8_i386.deb
ooobasis3.2-en-us-math_3.2.0-8_i386.deb
ooobasis3.2-en-us-res_3.2.0-8_i386.deb
ooobasis3.2-en-us-writer_3.2.0-8_i386.deb
ooobasis3.2-gnome-integration_3.2.0-8_i386.deb
ooobasis3.2-graphicfilter_3.2.0-8_i386.deb
ooobasis3.2-images_3.2.0-8_i386.deb
ooobasis3.2-impress_3.2.0-8_i386.deb
ooobasis3.2-javafilter_3.2.0-8_i386.deb
ooobasis3.2-kde-integration_3.2.0-8_i386.deb
ooobasis3.2-math_3.2.0-8_i386.deb
ooobasis3.2-onlineupdate_3.2.0-8_i386.deb
ooobasis3.2-ooofonts_3.2.0-8_i386.deb
ooobasis3.2-oooimprovement_3.2.0-8_i386.deb
ooobasis3.2-ooolinguistic_3.2.0-8_i386.deb
ooobasis3.2-pyuno_3.2.0-8_i386.deb
ooobasis3.2-testtool_3.2.0-8_i386.deb
ooobasis3.2-writer_3.2.0-8_i386.deb
ooobasis3.2-xsltfilter_3.2.0-8_i386.deb
OOo.txt
openoffice.org3_3.2.0-8_i386.deb
openoffice.org3-base_3.2.0-8_i386.deb
openoffice.org3-calc_3.2.0-8_i386.deb
openoffice.org3-dict-en_3.2.0-8_i386.deb
openoffice.org3-dict-es_3.2.0-8_i386.deb
openoffice.org3-dict-fr_3.2.0-8_i386.deb
openoffice.org3-draw_3.2.0-8_i386.deb
openoffice.org3-en-us_3.2.0-8_i386.deb
openoffice.org3-impress_3.2.0-8_i386.deb
openoffice.org3-math_3.2.0-8_i386.deb
openoffice.org3-writer_3.2.0-8_i386.deb
openoffice.org-ure_1.6.0-8_i386.deb

Thanks.

---

### Post by VMC on 2009-12-28
> **caryb said:**
> If you go to the folder containing the debs in a terminal session (konsole in Kubuntu) & type sudo dpkg -i *.deb

It will install this for you, a gotcha for me is it didn't setup a menu item for the application so I added it myself. The path to the installed files is /opt/openoffice.org3/program/soffice


Cheers Cary

Exactly! When I saw it wasn't installed with an icon I went to the /opt to find it. I used the force, but now that I have all the files , I probably didn't to force the issue.

I like the blue startup. It will look great on a dressed up Kubuntu setup.  Then again, this comes from OO. Wait until Ubuntu gets hold of it :)

---

### Post by VMC on 2009-12-28
> **soham_1207 said:**
> **IMHO that was an expression. But i do have 50 .deb files as following.**I'm the one that messed up here. I tried to first install from the language package only, Which had only 12 deb files. I since then got all "100" of them. Thanks.

---

### Post by donniezazen on 2009-12-28
> **caryb said:**
> If you go to the folder containing the debs in a terminal session (konsole in Kubuntu) & type sudo dpkg -i *.deb

It will install this for you, a gotcha for me is it didn't setup a menu item for the application so I added it myself. The path to the installed files is /opt/openoffice.org3/program/soffice


Cheers Cary

Thanks it worked. But i am getting error while installing the desktop-integration deb (openoffice.org3.2-debian-menus_3.2-9472_all).

Error: Conflicts with the installed package 'openoffice.org-core'

Thanks.

---

### Post by caryb on 2009-12-28
> 
Thanks it worked. But i am getting error while installing the desktop-integration deb (openoffice.org3.2-debian-menus_3.2-9472_all).

Error: Conflicts with the installed package 'openoffice.org-core

Question did you uninstall your 3.1x install of OpenOffice 1st?


Cary

---

### Post by tacantara on 2009-12-28
> **caryb said:**
> It will install this for you, a gotcha for me is it didn't setup a menu item for the application so I added it myself. The path to the installed files is /opt/openoffice.org3/program/soffice


Cheers Cary

So, that's where all those files I unpackaged went to.  I tracked it down, and it opened just fine once I activated the soffice icon.  Thanks, Cary :)

---

### Post by VMC on 2009-12-28
> **caryb said:**
> If you go to the folder containing the debs in a terminal session (konsole in Kubuntu) & type sudo dpkg -i *.deb

It will install this for you, a gotcha for me is it didn't setup a menu item for the application so I added it myself. The path to the installed files is /opt/openoffice.org3/program/soffice


Cheers Cary

Actually there is another directory with the deb file that will install the needed menus:

"~/DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9472_all.deb"

I just updated and now I have the OO3.2 menus right along side my still installed OO3.1. Then both work.

---

### Post by caryb on 2009-12-28
> Actually there is another directory with the deb file that will install the needed menus"

"~/DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9472_all.deb"

I just updated and now I have the OO3.2 menus right along side my still installed OO3.1. Then both work.

Ta! now I can remove my crappy entry with no icon:guitar:


Cary

---

### Post by ronacc on 2009-12-28
yes mine seem to be playing nice together , I think the 3.2 install is self contained , I note that it is in /opt rather than /usr/lib

---

### Post by donniezazen on 2009-12-28
> **caryb said:**
> Question did you uninstall your 3.1x install of OpenOffice 1st?


Cary

Thank you. After removing, 3.1x it worked.

---

### Post by VMC on 2009-12-28
> **ronacc said:**
> yes mine seem to be playing nice together , I think the 3.2 install is self contained , I note that it is in /opt rather than /usr/lib

Yes, as such, but if you want the menus you have to remove OO-3.1. "sudo dpkg -i" told me that in no uncertain terms. So I removed OO-3.1 and now have a more professional look of OO-3.2. 

Now to get rid of that "Softmaker 2008" that I was pushing. OO-3.2 is faster, and more polished.

---

### Post by donniezazen on 2009-12-29
OOo 3.2 looks a lot like running Microsoft Office in wine. It does not look more Gnomish.. the interface fonts look awful.

---

### Post by ranch hand on 2009-12-29
I have this OS (yes a replacement for the Stoned Lizard that died) on small partitions and I just got rid of the 3.1 to save space.  This is testing and I have lots of installs, I do not need 2 versions of OO on here.

I use writer and gedit for different things but there applets are together as i use them a lot.  I must say that this writer is just not comparable in speed to the old one.  I had to wait several seconds for the old one to load.  This is just about instant.

I will have to see what the spreadsheet is like.

This is a neat one.  I like it.

---

### Post by caryb on 2009-12-29
> OOo 3.2 looks a lot like running Microsoft Office in wine. It does not look more Gnomish.. the interface fonts look awful.

Might have to install Gnome some day so I know what you are talking about:lolflag:


Cary (KDE User)

---

### Post by VMC on 2009-12-29
> **caryb said:**
> Might have to install Gnome some day so I know what you are talking about:lolflag:


Cary (KDE User)

I have Ubuntu installed and it looks beautiful to me. That's what struck me first.  More important is the speed! (and usefulness).

---

### Post by caryb on 2009-12-29
Having raised 6 kids I don't need to see any more "Poo brown" colouring in this lifetime.



Cary

BTW Please don't see this post as incitefull It's just my Aussie humour.

---

### Post by ranch hand on 2009-12-29
> **caryb said:**
> Having raised 6 kids I don't need to see any more "Poo brown" colouring in this lifetime.



Cary

BTW Please don't see this post as incitefull It's just my Aussie humour.
 I really like gnome and lxde but pretty much loath KDE (nice there is the choices in Linux) but the chocolate induced diahria brown is really not that attractive.

It is the work of minutes to change it but you have to look at it to install and boot and redo the looks.  By that time it has really gotten you down.

I have actually read (even in 9.10 testing forum) people saying how much they liked it.  I find that real hard to get my head around.

---

### Post by caryb on 2009-12-29
What I detest is the adulteration of things like the OOO startup screen & FF to Poo Brown as well. So you really cant escape it even in Kubuntuland.


Cary

---

### Post by k3lt01 on 2009-12-29
> **caryb said:**
> Having raised 6 kids I don't need to see any more "Poo brown" colouring in this lifetime.



Cary

BTW Please don't see this post as incitefull It's just my Aussie humour.Ah the old number 3 strikes again lol.

I'm finding the OOo servers a bit slow for some reason, I think I'll leave my download till the weekend. Hopefully the rest of the planet will be celebrating New Years so I can sit and download all night long.:lolflag:

---

### Post by nanog on 2009-12-29
You can get rid of the crappy kde-like menus by hacking the openoffice.or-style-human package to run under 3.2. Look at the "files installed" under package properties in synaptic and  install the necessary bits (e.g. /usr/share/basis3.1/share/config/images_human.zip and usr/share/doc/openoffice.org-style-human) into the appropriate /opt/open-office.org3 directory (e.g. /opt/openoffice.org/basis3.2/share/config/).

And BTW its incredibly annoying that openoffice.org styles are not portable. (I really, really hope Oracle/Sun drops openoffice so that it can be developed like a proper open source project.)

PS: When I said crappy KDE-like menus I meant KDE3...I like KDE4 menus. :)

---

### Post by ronacc on 2009-12-29
> **caryb said:**
> What I detest is the adulteration of things like the OOO startup screen & FF to Poo Brown as well. So you really cant escape it even in Kubuntuland.


Cary

on my sys 3.1 has the poo brown startup screen but 3.2 from oo.org has a nice sky blue one .

@ VMC dpkg bitched about oo 3.1 but didn't actualy uninstall it for me ( I used --force-all ) , the only thing I had to do was make a launcher for it , 3.2  did remove the 3.1 menu items .

---

### Post by sports fan Matt on 2009-12-29
sudo dpkg --force-all -i openoffice 3.2.0rc1
[sudo] password for office: 
dpkg: error processing openoffice (--install):
 cannot access archive: No such file or directory
dpkg: error processing 3.2.0rc1 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 openoffice
 3.2.0rc1

What am i doing wrong? downloaded then extracted OOO320_m8_native_packed-1_en-US.9472

---

### Post by caryb on 2009-12-29
I had the same problems, it seams the force is the problem try sudo dpkg -i *.deb

That way it sorts out the order to install without dependency problems


Cary

---

### Post by sports fan Matt on 2009-12-29
That gave me this :) sudo dpkg -i *.deb
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb

My question is since everything is in my downloads directory and that 1 set of files has been exctracted, what next?

---

### Post by ronacc on 2009-12-29
from the loooks of that error message the terminal he ran dpkg from wasn't in the dir where the packages were and dpkg couldn't find them , he either needs to cd to where the pkgs are or use the full path .

---

### Post by sports fan Matt on 2009-12-29
so it would be something like sudo dpkg -i downloads *.deb.  Im new to this part :)

---

### Post by donniezazen on 2009-12-29
> **nanog said:**
> You can get rid of the crappy kde-like menus by hacking the openoffice.or-style-human package to run under 3.2. Look at the "files installed" under package properties in synaptic and  install the necessary bits (e.g. /usr/share/basis3.1/share/config/images_human.zip and usr/share/doc/openoffice.org-style-human) into the appropriate /opt/open-office.org3 directory (e.g. /opt/openoffice.org/basis3.2/share/config/).

And BTW its incredibly annoying that openoffice.org styles are not portable. (I really, really hope Oracle/Sun drops openoffice so that it can be developed like a proper open source project.)

PS: When I said crappy KDE-like menus I meant KDE3...I like KDE4 menus. :)

Thanks for the idea. Do you wanna explain that and may be some screenshots of hacked and unhacked OO.

---

### Post by k3lt01 on 2009-12-29
> **sox fan Matt said:**
> so it would be something like sudo dpkg -i downloads *.deb.  Im new to this part :)cd into the directory that the .debs are in.

```
 cd ~/downloads/openoffice/
``` change the "openoffice" to the name of the directory, then
```
 sudo dpkg -i *.deb
```

---

### Post by sports fan Matt on 2009-12-29
ok..I have OOO320_m8_native_packed-1_en-US.9472 in my downloads folder.  Clicking on it gives me all the debs, but when I try to open the properties and run the command it doesnt work..im confused..lol

---

### Post by sports fan Matt on 2009-12-29
the name of the dir. is this: OOO320_m8_native_packed-1_en-US.9472..clicking on it gives me the debs if that helps.

---

### Post by ronacc on 2009-12-29
open a terminal and type cd  /home/<you>/OOO320         hit tab to autocomplete that should put you in that dir, type ls hit return and it will list the contents of the dir so you can make sure you are in the right place if you are run  sudo dpkg -i *.deb    . note if OOO320... isn't directly under your /home/<you>  add the rest of the path before hitting tab .

---

### Post by ranch hand on 2009-12-29
Extract your download.  Open the folder.  Inside there is a folder named "debs.  Right click on it and click on option "open in terminal".

Run the install command given earlier.

When that is done open that "debs" folder.  There is another folder in there with the menu stuff in it.

Repeat steps from above.

---

### Post by ronacc on 2009-12-29
to use "open in terminal" he has to have it installed , its not default .
If you don't have it installed use synaptic or else open a term and type
```
sudo apt-get install nautilus-open-terminal
``` then hit return .

---

### Post by k3lt01 on 2009-12-29
> **sox fan Matt said:**
> the name of the dir. is this: OOO320_m8_native_packed-1_en-US.9472..clicking on it gives me the debs if that helps.Open your terminal and put in this code
```
 cd ~/Downloads/OOO320_m8_native_packed-1_en-US.9472/
```
now your in there
```
sudo dpkg -i *.deb
```watch it install. Now go into the Dekstop intergration folder and click on the .deb in there and watch it install following any prompts you are given.

---

### Post by VMC on 2009-12-29
> **ronacc said:**
> on my sys 3.1 has the poo brown startup screen but 3.2 from oo.org has a nice sky blue one .

@ VMC dpkg bitched about oo 3.1 but didn't actualy uninstall it for me ( I used --force-all ) , the only thing I had to do was make a launcher for it , 3.2  did remove the 3.1 menu items .

Yes, the OO-3.2 has the nicer looking blue icons and backgrounds and such.

It sounds like you want to keep OO-3.1, and I did too at first. Then I decided I didn't need it, so after uninstalling OO-3.1 then "openoffice.org3.2-debian-menus_3.2-9472_all.deb" installed without  any more problems. I didn't need to force anything.

---

### Post by ronacc on 2009-12-29
I try to at least keep the default versions around on my test box so I don't get so far out of line with what we are testing that my bug reports wouldn't be meaningful .

---

### Post by ranch hand on 2009-12-29
Have any of you guys tried "open in terminal" on 10.04 or 9.10 for that matter.

I am on my main drive right now and can't check on this but I did not install that on any of my 10.04 installs.  I did install "nautilus-gksu" but that made no mention of any other packages.

I am on 9.04 right now and it had to be installed here.

---

### Post by ronacc on 2009-12-29
"open in terminal" is not a default part of nautilus and is not part of the default install , you have to install the package nautilus-open-terminal to have it . and yes it works fine on 10.04 .

---

### Post by phillw on 2009-12-29
Now, don't all laugh ... what is nautilus ? I suppose I'd better have a play with it, just so I can answer people who're having problems with it .... is SSSSOOOOO love it when they go ```
sudo firefox
``` ... evidently they do the same with nautilus - I've never had a play at un-screwing the permissions with that one. But, I'm curious to know what it does that I can't do without it.

Thanks -- yeah, sooo, a n00b question ;-)

Phill.

---

### Post by sports fan Matt on 2009-12-30
Error: Conflicts with the installed package 'openoffice.org-core' when I try and install with the desktop intergretion.  Does OOO need to be uninstalled before I run that deb in the desktop folder?

Will check in the morning.

---

### Post by k3lt01 on 2009-12-30
Back in Feisty I installed OOo 2.3 (Ubuntu was still using OOo 2.2) and I had to uninstall 2.2 before 2.3 would install as some of the components had conflicts.

---

### Post by ronacc on 2009-12-30
> **phillw said:**
> Now, don't all laugh ... what is nautilus ? I suppose I'd better have a play with it, just so I can answer people who're having problems with it .... is SSSSOOOOO love it when they go ```
sudo firefox
``` ... evidently they do the same with nautilus - I've never had a play at un-screwing the permissions with that one. But, I'm curious to know what it does that I can't do without it.

Thanks -- yeah, sooo, a n00b question ;-)

Phill.

nautilus is the file-manager in Gnome ,the one that opens when you click places>home . Ubuntu quit using the name nautilus a couple of iterations back for some reason . There are extensions for it that add extra functionality like nautilus-open-terminal (which opens a terminal in the dir you are browsing at the time) and others for other actions .Sudo nautilus gives you a file manager with root privileges so use it with caution.

---

### Post by VMC on 2009-12-30
Open terminal is part of the "[nautilus script]("http://g-scripts.sourceforge.net/index.php")".

Here is the script from that G-script (nautilus-scripts.tar.gz):
```
#!/usr/bin/perl -w
#
# Open terminal here
#
# Nautilus script that opens a gnome-terminal at the current location, if it's
# a valid one. This could be done in shell script, but I love Perl!.
#
# 20020930 -- Javier Donaire <jyuyu@fraguel.org>
# http://www.fraguel.org/~jyuyu/
# Licensed under the GPL v2+
#
# Modified by: Dexter Ang [thepoch@mydestiny.net]
# 2003-12-08: Modified for Gnome 2.4
#		- Added checking if executed on Desktop "x-nautilus-desktop:///"
#		  so that it opens in /home/{user}/Desktop

use strict;

$_ = $ENV{'NAUTILUS_SCRIPT_CURRENT_URI'};
if ($_ and m#^file:///#) {
  s/%([0-9A-Fa-f]{2})/chr(hex($1))/eg;
  s#^file://##;
  exec "gnome-terminal --working-directory='$_'";
}

# Added 2003-12-08 Dexter Ang
if ($_ == "x-nautilus-desktop:///") {
  $_ = $ENV{'HOME'};
  $_ = $_.'/Desktop';
  exec "gnome-terminal --working-directory='$_'";
}
```

---

