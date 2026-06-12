---
title: "Help - Installing Open Office 2.1"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by jcroot on 2006-12-14
Hi Guys!

I'm really new with Ubuntu and this community (forum) but I would like to learn more about Ubuntu, well I already have my Ubuntu OS installed in my PC... The only problem is that would like to know how can I upgrade the default OpenOffice 2.0.4 the comes with Ubuntu 6.10 version... Just in case, I'm using Ubuntu 6.10 version. 

I have OpenOffice 2.1 for Linux in a CD because I don't have internet connection at home, so I download it from work.

---

### Post by zgornel on 2006-12-15
I'm going to try it today, be back later with a replay on how it went ;)

---

### Post by jcroot on 2006-12-15
Ok thanks, waiting for a reply...

---

### Post by zgornel on 2006-12-15
> **jcroot said:**
> Ok thanks, waiting for a reply...
Installation worked ok. I'll give you a quick guide :) :
1. - Unpack the OO2.1 archive. (There should be a lot of RPMS)
2. - Enter the OOE680.../RPMS directory and write ```
sudo alien -d *.rpm
```. This will create debian packages out of the RPMS. Wait until all packages are created and enter the desktop-integration dir. Run the same command.
3. - Return to the initial directory and remove gnome-integration or kde-inegration packages (depending on what you are not running). If you are running both KDE and Gnome don't remove anything. Then, run ```
sudo dpkg -i *.deb
```. Enter the desktop-integration dir and install the *debian-menus* pakage.
4. Remove all RPMS and from main dir and all packages in desktop-integration but the debian-menus one.
5. The end.

Good luck ;)

P.S. The only thing I can complain about is the font quality (still better than in OO 2.0.4). Check my screenshots [here]("http://www.ubuntuforums.org/showthread.php?p=1892020")

---

### Post by lolwhites on 2006-12-17
Has anyone tried installing and running OO 2.1 in Dapper? If so, how did it go?

---

### Post by uBo on 2006-12-19
are we not going to get the update through the repos sometime soon? (edgy)

if not please tell me!

---

### Post by maynoth on 2006-12-19
no ubuntu never updates applications even if a newer version fixes bug (gaim 1.5 breezy)

asking about such in irc will get you perm banned... if you tick off a mod...

hopefully automatix will release an option to install the new OOO 2.1

---

### Post by arnieboy on 2006-12-21
> **maynoth said:**
> hopefully automatix will release an option to install the new OOO 2.1
Open Office by default on Debian Unstable and Ubuntu Edgy is broken. Since Ubuntu consists  99% of repackaged Debian Unstable, most of the bugs persist.
Using alien to convert the rpms distributed by OO have produced better results than the native packages distributed by Ubuntu. However, integration with Ubuntu in general will not work this way. Since OO is in Ubuntu "main", its a pity that the OO packages Ubuntu distributes do not go through the QA which they deserve.
We at Automatix do not see a better workaround than wait for Ubuntu to make better packages before we offer an upgrade.

---

### Post by TorchlightJay on 2006-12-21
I tried this and it won't install. It says something like

dpkg: regarding openoffice.org-debian-menus_2.1-5_all.deb containing openoffice.org-debian-menus:
 openoffice.org-core conflicts with openoffice.org-unbundled
  openoffice.org-debian-menus provides openoffice.org-unbundled and is to be installed.
dpkg: error processing openoffice.org-debian-menus_2.1-5_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 openoffice.org-debian-menus_2.1-5_all.deb

Should I uninstall 2.0.4 and make sure openoffice is 100% closed when I do this install? Thanks.

---

### Post by jetpeach on 2006-12-21
does anybody have a link to the rpms? i looked on the openoffice page, but only found the tarball.  i'm going to try to make a deb from it which i could then start a torrent here for, which would ease installation for everybody, but i've not yet had any luck making debs...

EDIT: i found the rpms inside the regular link from openoffice.
EDIT: Oh I found some deb linked in the other thread. Inside the top link, there is an english package included the debs.
[http://www.nic.funet.fi/pub/misc/openoffice/localized/finnish/stable/2.1.0/latest/](http://www.nic.funet.fi/pub/misc/openoffice/localized/finnish/stable/2.1.0/latest/)

---

### Post by hxx4 on 2006-12-21
> **jetpeach said:**
> does anybody have a link to the rpms? i looked on the openoffice page, but only found the tarball.  i'm going to try to make a deb from it which i could then start a torrent here for, which would ease installation for everybody, but i've not yet had any luck making debs...

Extract the tarball, the RPMS are in there.

---

### Post by TorchlightJay on 2006-12-22
the rpms are in the tarball

---

### Post by zeekoe on 2006-12-24
> **TorchlightJay said:**
> I tried this and it won't install. It says something like

dpkg: regarding openoffice.org-debian-menus_2.1-5_all.deb containing openoffice.org-debian-menus:
 openoffice.org-core conflicts with openoffice.org-unbundled
  openoffice.org-debian-menus provides openoffice.org-unbundled and is to be installed.
dpkg: error processing openoffice.org-debian-menus_2.1-5_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 openoffice.org-debian-menus_2.1-5_all.deb

Should I uninstall 2.0.4 and make sure openoffice is 100% closed when I do this install? Thanks.
Disclaimer: I don't know if this will break something in the future. It worked for me, your mileage may vary. I got the same problem. 'fixed' it by extracting openoffice.org-debian-menus_2.1-5_all.deb and manually copying everything to the correct location. The problem was that it still ran openoffice.org-2.0, of which most stuff was already removed.

---

### Post by towsonu2003 on 2006-12-24
see this, it's much easier to do:
[http://www.oooforum.org/forum/viewtopic.phtml?t=26173&highlight=](http://www.oooforum.org/forum/viewtopic.phtml?t=26173&highlight=)

it converts the installation into a folder, kind of like a portable application. it will not touch your apt / dpkg as long as you don't install the .deb files it mentions. I have 4 OOo versions sitting together peacefully right now. similar to how firefox distibutes its packages. 

A bug is filed on their distribution of RPMs: 
[http://www.openoffice.org/issues/show_bug.cgi?id=72921](http://www.openoffice.org/issues/show_bug.cgi?id=72921)

---

### Post by wilberfan on 2006-12-24
Ooops.  Never mind...didn't read far enough!   (D'oh!)

> **TorchlightJay said:**
> I tried this and it won't install. It says something like

dpkg: regarding openoffice.org-debian-menus_2.1-5_all.deb containing openoffice.org-debian-menus:
 openoffice.org-core conflicts with openoffice.org-unbundled
  openoffice.org-debian-menus provides openoffice.org-unbundled and is to be installed.
dpkg: error processing openoffice.org-debian-menus_2.1-5_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 openoffice.org-debian-menus_2.1-5_all.deb

Should I uninstall 2.0.4 and make sure openoffice is 100% closed when I do this install? Thanks.

I ran into this problem, too...   Uninstalling 2.0.4 wants to uninstall the ubuntu-desktop (!)   How should we proceed here?

---

### Post by towsonu2003 on 2006-12-24
> **wilberfan said:**
> 
I ran into this problem, too...   Uninstalling 2.0.4 wants to uninstall the ubuntu-desktop (!)   How should we proceed here?

is it okay to remove ubuntu-desktop? yes and no. 

it's a meta package (i.e. it's empty, it has no info other than the other packages it will install). but you will need ubuntu-desktop when you dist-upgrade (from dapper to edgy, from edgy to feisty and so on). 

Try using the link above :) It will not touch your system

---

### Post by true_friend on 2006-12-26
Hi folks..
found this thread when i was ready to install. unlike other members i had no problem in installation.. every thing gone smooth and old packages were replaced by new debians i had made from rpm..
but how do i run these applications now??
in Kmenue>Office it was located which is empty only Kontact is there..:-? 
i think i have to make shotcuts manually but do not know how??
plz help
Regards
True_Friend

---

### Post by true_friend on 2006-12-26
The Out Put of Konsole
....................................................................................................................
openoffice.org-base_2.1.0-7_i386.deb generated
openoffice.org-calc_2.1.0-7_i386.deb generated
openoffice.org-core01_2.1.0-7_i386.deb generated
openoffice.org-core02_2.1.0-7_i386.deb generated
openoffice.org-core03_2.1.0-7_i386.deb generated
openoffice.org-core03u_2.1.0-7_i386.deb generated
openoffice.org-core04_2.1.0-7_i386.deb generated
openoffice.org-core04u_2.1.0-7_i386.deb generated
openoffice.org-core05_2.1.0-7_i386.deb generated
openoffice.org-core05u_2.1.0-7_i386.deb generated
openoffice.org-core06_2.1.0-7_i386.deb generated
openoffice.org-core07_2.1.0-7_i386.deb generated
openoffice.org-core08_2.1.0-7_i386.deb generated
openoffice.org-core09_2.1.0-7_i386.deb generated
Warning: Skipping conversion of scripts in package openoffice.org-core10: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
openoffice.org-core10_2.1.0-7_i386.deb generated
openoffice.org-draw_2.1.0-7_i386.deb generated
openoffice.org-emailmerge_2.1.0-7_i386.deb generated
openoffice.org-gnome-integration_2.1.0-7_i386.deb generated
openoffice.org-graphicfilter_2.1.0-7_i386.deb generated
openoffice.org-impress_2.1.0-7_i386.deb generated
openoffice.org-javafilter_2.1.0-7_i386.deb generated
openoffice.org-kde-integration_2.1.0-7_i386.deb generated
openoffice.org-math_2.1.0-7_i386.deb generated
openoffice.org-onlineupdate_2.1.0-7_i386.deb generated
openoffice.org-pyuno_2.1.0-7_i386.deb generated
openoffice.org-testtool_2.1.0-7_i386.deb generated
openoffice.org-writer_2.1.0-7_i386.deb generated
openoffice.org-xsltfilter_2.1.0-7_i386.deb generated
ss@ss-desktop:~/Desktop/OOE680_m6_native_packed-1_en-US.9095/RPMS$ sudo dpkg -i *.deb
Password:
(Reading database ... 120785 files and directories currently installed.)
Preparing to replace openoffice.org-base 2.0.2-2ubuntu12.1 (using openoffice.org-base_2.1.0-7_i386.deb) ...
Unpacking replacement openoffice.org-base ...
Preparing to replace openoffice.org-calc 2.0.2-2ubuntu12.1 (using openoffice.org-calc_2.1.0-7_i386.deb) ...
Unpacking replacement openoffice.org-calc ...
Selecting previously deselected package openoffice.org-core01.
Unpacking openoffice.org-core01 (from openoffice.org-core01_2.1.0-7_i386.deb) ...
Selecting previously deselected package openoffice.org-core02.
Unpacking openoffice.org-core02 (from openoffice.org-core02_2.1.0-7_i386.deb) ...
Selecting previously deselected package openoffice.org-core03.
Unpacking openoffice.org-core03 (from openoffice.org-core03_2.1.0-7_i386.deb) ...
Selecting previously deselected package openoffice.org-core03u.
Unpacking openoffice.org-core03u (from openoffice.org-core03u_2.1.0-7_i386.deb) ...
Selecting previously deselected package openoffice.org-core04.
Unpacking openoffice.org-core04 (from openoffice.org-core04_2.1.0-7_i386.deb) ...
Selecting previously deselected package openoffice.org-core04u.
Unpacking openoffice.org-core04u (from openoffice.org-core04u_2.1.0-7_i386.deb) ...
Selecting previously deselected package openoffice.org-core05.
Unpacking openoffice.org-core05 (from openoffice.org-core05_2.1.0-7_i386.deb) ...
Selecting previously deselected package openoffice.org-core05u.
Unpacking openoffice.org-core05u (from openoffice.org-core05u_2.1.0-7_i386.deb) ...
Selecting previously deselected package openoffice.org-core06.
Unpacking openoffice.org-core06 (from openoffice.org-core06_2.1.0-7_i386.deb) ...
Selecting previously deselected package openoffice.org-core07.
Unpacking openoffice.org-core07 (from openoffice.org-core07_2.1.0-7_i386.deb) ...
Selecting previously deselected package openoffice.org-core08.
Unpacking openoffice.org-core08 (from openoffice.org-core08_2.1.0-7_i386.deb) ...
Selecting previously deselected package openoffice.org-core09.
Unpacking openoffice.org-core09 (from openoffice.org-core09_2.1.0-7_i386.deb) ...
Selecting previously deselected package openoffice.org-core10.
Unpacking openoffice.org-core10 (from openoffice.org-core10_2.1.0-7_i386.deb) ...
Preparing to replace openoffice.org-draw 2.0.2-2ubuntu12.1 (using openoffice.org-draw_2.1.0-7_i386.deb) ...
Unpacking replacement openoffice.org-draw ...
Selecting previously deselected package openoffice.org-emailmerge.
Unpacking openoffice.org-emailmerge (from openoffice.org-emailmerge_2.1.0-7_i386.deb) ...
Selecting previously deselected package openoffice.org-gnome-integration.
Unpacking openoffice.org-gnome-integration (from openoffice.org-gnome-integration_2.1.0-7_i386.deb) ...
Selecting previously deselected package openoffice.org-graphicfilter.
Unpacking openoffice.org-graphicfilter (from openoffice.org-graphicfilter_2.1.0-7_i386.deb) ...
Preparing to replace openoffice.org-impress 2.0.2-2ubuntu12.1 (using openoffice.org-impress_2.1.0-7_i386.deb) ...
Unpacking replacement openoffice.org-impress ...
Selecting previously deselected package openoffice.org-javafilter.
Unpacking openoffice.org-javafilter (from openoffice.org-javafilter_2.1.0-7_i386.deb) ...
Selecting previously deselected package openoffice.org-kde-integration.
Unpacking openoffice.org-kde-integration (from openoffice.org-kde-integration_2.1.0-7_i386.deb) ...
Preparing to replace openoffice.org-math 2.0.2-2ubuntu12.1 (using openoffice.org-math_2.1.0-7_i386.deb) ...
Unpacking replacement openoffice.org-math ...
Selecting previously deselected package openoffice.org-onlineupdate.
Unpacking openoffice.org-onlineupdate (from openoffice.org-onlineupdate_2.1.0-7_i386.deb) ...
Selecting previously deselected package openoffice.org-pyuno.
Unpacking openoffice.org-pyuno (from openoffice.org-pyuno_2.1.0-7_i386.deb) ...
Selecting previously deselected package openoffice.org-testtool.
Unpacking openoffice.org-testtool (from openoffice.org-testtool_2.1.0-7_i386.deb) ...
Preparing to replace openoffice.org-writer 2.0.2-2ubuntu12.1 (using openoffice.org-writer_2.1.0-7_i386.deb) ...
Unpacking replacement openoffice.org-writer ...
Selecting previously deselected package openoffice.org-xsltfilter.
Unpacking openoffice.org-xsltfilter (from openoffice.org-xsltfilter_2.1.0-7_i386.deb) ...
Setting up openoffice.org-base (2.1.0-7) ...
Setting up openoffice.org-calc (2.1.0-7) ...
Setting up openoffice.org-core01 (2.1.0-7) ...

Setting up openoffice.org-core02 (2.1.0-7) ...
Setting up openoffice.org-core03 (2.1.0-7) ...
Setting up openoffice.org-core03u (2.1.0-7) ...
Setting up openoffice.org-core04 (2.1.0-7) ...
Setting up openoffice.org-core04u (2.1.0-7) ...
Setting up openoffice.org-core05 (2.1.0-7) ...

Setting up openoffice.org-core05u (2.1.0-7) ...

Setting up openoffice.org-core06 (2.1.0-7) ...
Setting up openoffice.org-core07 (2.1.0-7) ...
Setting up openoffice.org-core08 (2.1.0-7) ...
Setting up openoffice.org-core09 (2.1.0-7) ...
Setting up openoffice.org-core10 (2.1.0-7) ...

Setting up openoffice.org-draw (2.1.0-7) ...
Setting up openoffice.org-emailmerge (2.1.0-7) ...
Setting up openoffice.org-gnome-integration (2.1.0-7) ...
Setting up openoffice.org-graphicfilter (2.1.0-7) ...
Setting up openoffice.org-impress (2.1.0-7) ...
Setting up openoffice.org-javafilter (2.1.0-7) ...
Setting up openoffice.org-kde-integration (2.1.0-7) ...
Setting up openoffice.org-math (2.1.0-7) ...
Setting up openoffice.org-onlineupdate (2.1.0-7) ...
Setting up openoffice.org-pyuno (2.1.0-7) ...

Setting up openoffice.org-testtool (2.1.0-7) ...
Setting up openoffice.org-writer (2.1.0-7) ...
Setting up openoffice.org-xsltfilter (2.1.0-7) ...
...........................................................................................

---

### Post by towsonu2003 on 2006-12-27
I'm inexperienced with kde. until someone who knows the answer comes along, do the following:
1. open a terminal
2. type oo and than hit <tab> (on your keyboard) twice. you will see a list of programs available for you to run. 
3. because I'm not sure which one you should run, please copy-paste the output here. the program is probably **soffice** though...

---

### Post by true_friend on 2006-12-27
ooffice         oofromtemplate  ooo-wrapper
the output of oo + two tabs given
i opened ooffice but it was an empty file asking for opening a new file or existing file..
normally it starts with whole tools and a blank document..

---

### Post by towsonu2003 on 2006-12-27
> **true_friend said:**
> ooffice         oofromtemplate  ooo-wrapper
the output of oo + two tabs given
i opened ooffice but it was an empty file asking for opening a new file or existing file..
normally it starts with whole tools and a blank document..

what happens when you do 
```

ooffice --writer
``` and check the version using Help > About?

---

### Post by Hagar Delest on 2006-12-28
[QUOTE="Terminal"]Warning: Skipping conversion of scripts in package openoffice.org-core10: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
openoffice.org-core10_2.1.0-7_i386.deb generated[/QUOTE]
This may be the reason why the installation is broken. Try this : [http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370](http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370)

---

### Post by true_friend on 2006-12-28
i have checked the version from synaptic..
it is telling 2.1.. all components...
but its running issue.
:( :(

---

### Post by true_friend on 2006-12-28
i checked installation directory which was /opt/openoffice.org2.1  i tried to open it by openoffice --writer but it crashed after loading..start screen comes up it loads but then disappears konsole says fialed to open device..

---

### Post by towsonu2003 on 2006-12-28
I'd just remove and purge (the "remove completely" option in synaptic) openoffice packages that you installed using alien & rpm. then I'd install openoffice.org from Ubuntu's repositories, and use the ["other" way]("http://ubuntuforums.org/showthread.php?t=324872") to install the new version. 

when you remove OOo, synaptic will want to uninstall ubuntu-desktop. that is fine. say yes, let it remove, and then re-install ubuntu-desktop (which will make you install ubuntu's OOo ayway).

---

### Post by true_friend on 2006-12-29
i think i have to give it a try..

---

### Post by Hagar Delest on 2006-12-29
> **true_friend said:**
> it crashed after loading..start screen comes up it loads but then disappears konsole says fialed to open device..
Before reinstalling anything, I think you should check the error message (Google or OOo forum) and see if there is no conflict with your graphic card drivers.

---

### Post by true_friend on 2006-12-29
ooooooooooooo
another possible issue.. :(

---

### Post by sgla1 on 2006-12-29
I have installed open office 2.1 on edgy as follows:

1) download OO 2.1 from openoffice.org
2) remove the Ubuntu version of open office -- it's broken anyway 
```
 dpkg -l | grep -i openoffice | cut -d " " -f 3 | sudo xargs apt-get -y --purge remove
sudo apt-get autoremove
```
3) convert the downloaded openoffice files from rpm to deb:
```
cd dir_where_you_extracted_the_OO_zip_file
cd RPMS
sudo alien --scripts --keep-version *.rpm
```
4) install the new version of openoffice:
```
sudo dpkg -i *.deb
cd desktop-integration/
sudo dpkg -i *.deb

```

This should work for dapper as well; ymmv :-)

Reference: [http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370](http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370)

Steve G

---

### Post by true_friend on 2006-12-29
At last
i have installed it. 
thnx
i removed firstly installed packages from synaptic and then followed "sgla1" commands.
Thnx fol all.
Regards
True_Friend

---

### Post by wilberfan on 2006-12-30
With the exception of having to cd down one more layer into the "RPMS" folder, it worked *perfectly!*   :mrgreen: 

Nice goin'!    And thanks!

---

### Post by david.rahrer on 2006-12-30
> **arnieboy said:**
> Using alien to convert the rpms distributed by OO have produced better results than the native packages distributed by Ubuntu. However, integration with Ubuntu in general will not work this way.
Can you explain what "integration" will be lost by installing OO 2.1 using the instructions in this thread?  I'm still confused over these different flavors of the same app.  Thanks.

---

### Post by teejay17 on 2006-12-30
> **maynoth said:**
> no ubuntu never updates applications even if a newer version fixes bug (gaim 1.5 breezy)

asking about such in irc will get you perm banned... if you tick off a mod...

hopefully automatix will release an option to install the new OOO 2.1
Why would asking such an innocent question get a person permanently banned? Why would such a question tick off a mod to such an extent?

---

### Post by tomcat1965 on 2006-12-31
I just posted a torrent on linuxtracker [http://linuxtracker.org/torrents-details.php?id=3349]("http://linuxtracker.org/torrents-details.php?id=3349")

It's a package of the .debs for open office for gnome desktop,install them to your /opt directory and use "sudo chmod 777 *.deb" then "sudo dpkg -i *.deb" followed by "cd desktop-integration" and "sudo dpkg -i openoffice.org-debian-menus*.deb" to add open office menu to Applications>Office and you're all set.

Of course you could just install Gnome office as Abiword is really excellent,nice fonts,loads fast,all the stuff you need if you're not a large company and is a pleasure to use. Inkscape is really good too if you're into artwork.8)

---

### Post by davarino on 2006-12-31
> **teejay17 said:**
> Why would asking such an innocent question get a person permanently banned? Why would such a question tick off a mod to such an extent?

I suspect that Maynoth was simply venting about a bad past experience with a mod. I've never had any problem with them, but it's easy to imagine that one or two former wikipedia-obsessives have discovered a new lair for their personality malfunctions to flourish.

A good mod does have to be a bit of a mother-hen about things. And that will reflect in their responses to those questions that "*everybody* should know the answers to."

Look, if you ask even your mother a question that she thinks is obvious, when everything is on fire in the kitchen, she will probably not give you a perfectly loving answer... the same with a mod.

---

### Post by NumberOne on 2006-12-31
Thanks sglal,
just followed your post to install OO 2.1 and it worked perfectly.

---

### Post by Irony on 2007-01-03
jetpeach's link of;

[http://www.nic.funet.fi/pub/misc/openoffice/localized/finnish/stable/2.1.0/latest/](http://www.nic.funet.fi/pub/misc/openoffice/localized/finnish/stable/2.1.0/latest/)

contains the .deb files which work fine in Dapper.

Simply download and extract the deb files then cd to the extracted files then dpkg it, e.g.;

[PHP]irony@ubuntu:~$ cd /mnt/hda11_stuff/ooo/DEBS[/PHP]
[PHP]irony@ubuntu:/mnt/hda11_stuff/ooo/DEBS$ sudo dpkg -i *.deb[/PHP]

And that's it - everything is added to the applications menu.

Uninstall OOo first via synaptic. Or do;

[PHP]dpkg -l | grep -i openoffice | cut -d " " -f 3 | sudo xargs apt-get -y --purge remove[/PHP]

which seems to be more thorough.

---

### Post by lonniehenry on 2007-01-05
Thanks Irony ,  your easy way of installing OO 2.1 was so easy.  I tried other methods to update OO but yours was great.  No problems at all.  I love it that there is always someone out in the forums that can solve whatever problem that comes along.  That's why I only use Ubuntu now.

---

### Post by jcroot on 2007-01-06
> **Irony said:**
> jetpeach's link of;

[http://www.nic.funet.fi/pub/misc/openoffice/localized/finnish/stable/2.1.0/latest/](http://www.nic.funet.fi/pub/misc/openoffice/localized/finnish/stable/2.1.0/latest/)

contains the .deb files which work fine in Dapper.

Simply download and extract the deb files then cd to the extracted files then dpkg it, e.g.;

[PHP]irony@ubuntu:~$ cd /mnt/hda11_stuff/ooo/DEBS[/PHP]
[PHP]irony@ubuntu:/mnt/hda11_stuff/ooo/DEBS$ sudo dpkg -i *.deb[/PHP]

And that's it - everything is added to the applications menu.

Uninstall OOo first via synaptic. Or do;

[PHP]dpkg -l | grep -i openoffice | cut -d " " -f 3 | sudo xargs apt-get -y --purge remove[/PHP]

which seems to be more thorough.

This sounds to simple man thanks, but one question I don't understand this part of the code:

cd /mnt/hda11_stuff/ooo/DEBS

I entered this command and it says: No such file or directory.

What is wrong? Do I have to change the hda11_stuff? what is hda11_stuff?

---

### Post by jcroot on 2007-01-06
This is what I did:

Open Terminal, then enter this code:

cd /home/supremo/Desktop/DEBS

After entering this code I see:

supremo@supremo-desktop:~/Desktop/DEBS

So I typed: /home/supremo/Desktop/DEBS$ sudo dpkg -i *.deb

And it says: 

bash: /home/supremo/Desktop/DEBS$: No such file or directory
supremo@supremo-desktop:~/Desktop/DEBS$ 

What I'm doing wrong? I have a folder called "DEBS" in my Desktop. with all the debs files...

---

### Post by Irony on 2007-01-06
You are not doing it accurately.

Open up a terminal then do;

[PHP]cd[/PHP]

Then drag the DEBS folder into the terminal, then hit enter.

This dragging will give you the exact path to the directory (rather than possibly typing it inaccurately).

Then do;

[PHP]sudo dpkg -i *.deb[/PHP]

Make sure you copy and paste these commands, i.e. highlight the above commands and then middle click into the terminal - middle clicking pastes whatever you've highlighted.

---

### Post by jcroot on 2007-01-06
Thanks for your help man...

This is the file that I download: OOo_2.1.0_LinuxX86-64_install_en-US_deb.tar.gz

My PC is no 64 but it's 86. I did what you told me to do:

Open Terminal

Typed: cd

then I drag the debs folder so the full path will be:

cd /home/supremo/Desktop/DEBS

The output for the above code is:
supremo@supremo-desktop:~/Desktop/DEBS$

Then I entered: sudo dpkg -i *.deb  
It asked me for my password, I enter my password and it looks like installing some files, when it finish I don't know where to find my OpenOffice in the menu? I can't find the openoffice 2.1

Thanks for your help.

---

### Post by jcroot on 2007-01-06
I would like some help please. ;)

---

### Post by jcroot on 2007-01-06
Can somebody please help me? I really need my Office to be install in my Ubuntu Machine, for now I'm using Windows...

---

### Post by david.rahrer on 2007-01-07
I followed sgla1's instructions from earlier in this thread without a problem.  However, I would still appreciate knowing what integration might have been lost moving from the Ubuntu "version" of OO to this one.  I don't entirely understand what is behind the different flavors of apps yet.  What is the difference besides the newer version?

---

### Post by Irony on 2007-01-07
Assuming you have installed a 32 bit Ubuntu operating system then you need the following link;

[http://www.nic.funet.fi/pub/misc/openoffice/localized/finnish/stable/2.1.0/latest/OOo_2.1.0_LinuxIntel_install_en-US_deb.tar.gz](http://www.nic.funet.fi/pub/misc/openoffice/localized/finnish/stable/2.1.0/latest/OOo_2.1.0_LinuxIntel_install_en-US_deb.tar.gz)

Make sure you first uninstall OOo with;

[PHP]dpkg -l | grep -i openoffice | cut -d " " -f 3 | sudo xargs apt-get -y --purge remove[/PHP]

---

### Post by jcroot on 2007-01-07
I'm still not able to see the Menu for Openoffice, can somebody please give me some help with this?

---

### Post by jcroot on 2007-01-07
I finally got my OpeOffice 2.1 installed in my Ubuntu Machine. I just followed sgla1's instructions, thanks man it was easy...

I didn't follow your instructions at the first time because I tought it will be dificult (I mean converting rpm to deb) but it was simple.

---

### Post by be4truth on 2007-01-08
I installed OOo2.1 on a fresh dapper+Kubuntu-Desktop+Automtix+full system update and it works fine.:)

---

### Post by djconnel on 2007-01-11
> **TorchlightJay said:**
> 
Should I uninstall 2.0.4 and make sure openoffice is 100% closed when I do this install? Thanks.

Yes -- I had the same problem, and after purging 2.0.x, the installation went smoothly.

Dan

---

### Post by Quillz on 2007-01-12
> **sgla1 said:**
> I have installed open office 2.1 on edgy as follows:

1) download OO 2.1 from openoffice.org
2) remove the Ubuntu version of open office -- it's broken anyway 
```
 dpkg -l | grep -i openoffice | cut -d " " -f 3 | sudo xargs apt-get -y --purge remove
sudo apt-get autoremove
```
3) convert the downloaded openoffice files from rpm to deb:
```
cd dir_where_you_extracted_the_OO_zip_file
cd RPMS
sudo alien --scripts --keep-version *.rpm
```
4) install the new version of openoffice:
```
sudo dpkg -i *.deb
cd desktop-integration/
sudo dpkg -i *.deb

```

This should work for dapper as well; ymmv :-)

Reference: [http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370](http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370)

Steve G
Thanks! This seems to have worked for me.

---

### Post by davarino on 2007-01-31
> **lolwhites said:**
> Has anyone tried installing and running OO 2.1 in Dapper? If so, how did it go?
In short, yes, I have OO.o 2.1 running on a Dapper system and it runs just fine.

---

### Post by Arup on 2007-02-10
Worked like a charm, thank you very much.

---

### Post by Maestro23 on 2007-02-10
Props to sgla1.  Instructions worked like a charm. Thank you very much.:guitar:

---

### Post by ernstblaauw on 2007-02-13
I installed the 2.2 beta using the steps 1-4 from [this guide]("http://installation.openoffice.org/servlets/ReadMsg?list=dev&msgNo=609"). I can start Openoffice.org now by typing ```
/opt/ooo-dev2.2/program/soffice
```. 
Of course, I would like to have desktop integration. Has anyone an idea how to add menus to the Gnome menu? 
I cannot change existing Openoffice.org menu items: Despite I have OOo 2.0.4 also installed, I don;t have any menu items for that version.

**Update:**
By installing the meta package ubuntu-desktop, I got the menu items back for OpenOffice.org and thus changed it for the beta. However, the beta is constantly crashing: I never reach the stage I open a file succesfully. My question now is: How to install a beta correctly?

---

### Post by davarino on 2007-02-16
> **ernstblaauw said:**
> [T]he beta is constantly crashing: I never reach the stage I open a file succesfully. My question now is: How to install a beta correctly?

I would imagine that you use the same procedure as for the non-*ß*, just change the file's version numbers as appropriate. It *should* be no more difficult than that. (But "should" is a very difficult word to attach a meaning to: it's like trying to nail marmalade to the ceiling.)

At the risk of being a spoil sport, I would guess that if you need to ask how to install a beta you are fairly new to Linux... and if you are fairly new to Linux you probably *still* want to enjoy your time with it. This implies (to me) that maybe you should keep away from beta ware until you're a little more comfortable with things blowing up in your face. They ***do*** blow up with beta ware... that's why they're called "beta" instead of "better".

After all, what was so bad about 2.1? :D It's not such a great sin to wait a little.

---

### Post by ernstblaauw on 2007-02-17
> **davarino said:**
> I would imagine that you use the same procedure as for the non-*ß*, just change the file's version numbers as appropriate. It *should* be no more difficult than that. (But "should" is a very difficult word to attach a meaning to: it's like trying to nail marmalade to the ceiling.)

At the risk of being a spoil sport, I would guess that if you need to ask how to install a beta you are fairly new to Linux... and if you are fairly new to Linux you probably *still* want to enjoy your time with it. This implies (to me) that maybe you should keep away from beta ware until you're a little more comfortable with things blowing up in your face. They ***do*** blow up with beta ware... that's why they're called "beta" instead of "better".

After all, what was so bad about 2.1? :D It's not such a great sin to wait a little.
Well, I don't think it crashes because it is a beta (using another installer, it runs well now), but because I do something wrong when aliening. You're right, maybe I shouldn't do that ;-). However, I like to have the latest versions :-).

---

### Post by davarino on 2007-02-17
Yes, yes, yes. "The Shiny New Penny Syndrome." I fall prey to it myself, far too often. :roll:

---

### Post by lolwhites on 2007-02-18
OK, I've downloaded the 2.1 tarball to my desktop. As I'm still fairly new to this, can someone explain in plain English what I need to do? Thanks.

---

### Post by lolwhites on 2007-02-24
No worries, got it sorted. Thanks everybody.

---

### Post by dc81 on 2007-03-02
> **zgornel said:**
> Installation worked ok. I'll give you a quick guide :) :
1. - Unpack the OO2.1 archive. (There should be a lot of RPMS)
2. - Enter the OOE680.../RPMS directory and write ```
sudo alien -d *.rpm
```. This will create debian packages out of the RPMS. Wait until all packages are created and enter the desktop-integration dir. Run the same command.
3. - Return to the initial directory and remove gnome-integration or kde-inegration packages (depending on what you are not running). If you are running both KDE and Gnome don't remove anything. Then, run ```
sudo dpkg -i *.deb
```. Enter the desktop-integration dir and install the *debian-menus* pakage.
4. Remove all RPMS and from main dir and all packages in desktop-integration but the debian-menus one.
5. The end.

Good luck ;)

P.S. The only thing I can complain about is the font quality (still better than in OO 2.0.4). Check my screenshots [here]("http://www.ubuntuforums.org/showthread.php?p=1892020")

I am really new to this ubuntu thing.  When I tried the above, on the command line, it prompted me for a password on the command line, but when I tried to type the password, the command line was unresponsive.  It didn't let me type the password.  What am I doing wrong?

Thank you,

---

### Post by davarino on 2007-03-04
> (W)hen I tried to type the password, the command line was unresponsive. It didn't let me type the password. What am I doing wrong?

Using sudo, you should type in your user password that you use on the Ubuntu (brown) log-in screen. **You will see no "echo" of what you are typing.** When you have finished typing the user password, press "Enter".

---

### Post by mootpoint on 2007-03-06
zgornel -- thanks, your directions in your post of 12/15/2006 work flawlessly! 

All -- if you need to do a bunch of work as root, you can use the command "sudo bash." After you enter your password, you get a bash shell as root, and don't have to repeatedly type "sudo." 

However, if you do so, BE CAREFUL, and exit when you don't need root any more. This is a workaround if you're used to "su root" on *nix systems, and is DANGEROUS to use if you don't NEED root access to do what you're doing. 

Unless, of course, your brain and fingers work perfectly every time ...

m00t

---

### Post by gorg on 2007-03-08
ok, i got this--/home/worm/Desktop/openoffice.org-en-us_2.1.0-6_i386.deb
its installed in the opt folder ,  but how do i get it to show up in applications-office?

---

### Post by starcraft.man on 2007-03-08
Thanks a bunch Sgla1, worked great the first time for me :).

---

### Post by gorg on 2007-03-08
> **jetpeach said:**
> does anybody have a link to the rpms? i looked on the openoffice page, but only found the tarball.  i'm going to try to make a deb from it which i could then start a torrent here for, which would ease installation for everybody, but i've not yet had any luck making debs...

EDIT: i found the rpms inside the regular link from openoffice.
EDIT: Oh I found some deb linked in the other thread. Inside the top link, there is an english package included the debs.
[http://www.nic.funet.fi/pub/misc/openoffice/localized/finnish/stable/2.1.0/latest/](http://www.nic.funet.fi/pub/misc/openoffice/localized/finnish/stable/2.1.0/latest/)

i went and got this deb package and used the deb installer, but how do i get oo to show up in applications>office?
thanks

---

### Post by davarino on 2007-03-10
> **gorg said:**
> ok, i got this--/home/worm/Desktop/openoffice.org-en-us_2.1.0-6_i386.deb
its installed in the opt folder ,  but how do i get it to show up in applications-office?

Go to Applications > Alacarte Menu Editor. (Assuming that the Alacarte Menu Editor is installed...)

Scroll down to "Office" and let it be highlighted. Then do File > New Entry. Enter the information that is appropriate (Name = whatever name you want to give it, Command = probably /opt/openoffice.org2.1/program ), click OK, and you're ready to go.

You probably won't be able to set up program icons on the menu this way, but everything else ought to be just fine.

---

### Post by gorg on 2007-03-11
thanks, that put it there, but when i click on it , i get ____Details: Failed to execute child process "/opt/openoffice.org2.1/program" (Permission denied)

---

### Post by jcconnor on 2007-03-13
Thanks for the help on this one.  Looks like everything is working great!!  One quick question on the purge method - (I had to do that cause I kinda dorked my install initially) - does it remove the ubuntu-desktop as some of the other folks were asking about?  I didn't notice anything on that but the messages were kinda flying by and I may have missed it.

Thanks,

John

---

### Post by Catsworth on 2007-03-15
> **sgla1 said:**
> I have installed open office 2.1 on edgy as follows:

1) download OO 2.1 from openoffice.org
2) remove the Ubuntu version of open office -- it's broken anyway 
```
 dpkg -l | grep -i openoffice | cut -d " " -f 3 | sudo xargs apt-get -y --purge remove
sudo apt-get autoremove
```
3) convert the downloaded openoffice files from rpm to deb:
```
cd dir_where_you_extracted_the_OO_zip_file
cd RPMS
sudo alien --scripts --keep-version *.rpm
```
4) install the new version of openoffice:
```
sudo dpkg -i *.deb
cd desktop-integration/
sudo dpkg -i *.deb

```

This should work for dapper as well; ymmv :-)

Reference: [http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370](http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370)

Steve G




I simply can't thank you enough for this.

A perfect set of instructions, which worked first time.

Thank you so much!

---

### Post by davarino on 2007-03-17
> **gorg said:**
> thanks, that put it there, but when i click on it , i get ____Details: Failed to execute child process "/opt/openoffice.org2.1/program" (Permission denied)

Oops.

Probably you should have inserted

**openoffice.org-2.1 -writer %U**

in the "Command" box in Alacarte. That *ought* to bring up Writer with no problem.

I'm sorry.

---

### Post by twitami on 2007-03-22
Ok, I followed slga's instructions too. Everything went ok untill the last step (installing the integration). It starts out, then says , "conflicting packages - not installing openoffice.org.debian - menus". The regular install all went fine, and I followed ALL the steps, including the first one to remove the current version. Any ideas what went wrong? Of course, there isn't anything in Applications now. 

Thanks for the help, I am a one week old Linux user as of today! Overall I am VERY impressed with Ubuntu and Linux in general. It is a bummer that the updater doesnt just update OPenOffice to the 2.1 version. Really one of only a few things I have found in Ubantu that make it not quite a Windows replacement for my retired parents :)

---

### Post by tuga on 2007-03-25
Thank you sgla1.

---

### Post by SonyaBla on 2007-03-30
Spam.

---

### Post by soco on 2007-03-30
> **sgla1 said:**
> I have installed open office 2.1 on edgy as follows:

1) download OO 2.1 from openoffice.org
2) remove the Ubuntu version of open office -- it's broken anyway 
```
 dpkg -l | grep -i openoffice | cut -d " " -f 3 | sudo xargs apt-get -y --purge remove
sudo apt-get autoremove
```
3) convert the downloaded openoffice files from rpm to deb:
```
cd dir_where_you_extracted_the_OO_zip_file
cd RPMS
sudo alien --scripts --keep-version *.rpm
```
4) install the new version of openoffice:
```
sudo dpkg -i *.deb
cd desktop-integration/
sudo dpkg -i *.deb

```

This should work for dapper as well; ymmv :-)

Reference: [http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370](http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370)

Steve G


This works for the new OO 2.2 JRE too.  I deleted out in the folder desktop-integration the SUSE, KDE, etc and just left the debian.

---

### Post by Timokl on 2007-03-30
> **towsonu2003 said:**
> is it okay to remove ubuntu-desktop? yes and no. 

it's a meta package (i.e. it's empty, it has no info other than the other packages it will install). but you will need ubuntu-desktop when you dist-upgrade (from dapper to edgy, from edgy to feisty and so on). 

Try using the link above :) It will not touch your system

After trying the link above, I ended up with a removed ubuntu-desktop which also included a removed x-server. I was able to install OpenOffice 2.1 by then. :-)

Not really a big deal, as I simply rebooted in text mode and re-installed ubuntu-desktop using apt-get (for which to do I had to remove OpenOffice 2.1).

So, now I ended up at the same point where I had been before. :lolflag:

Is there any way to remove the Ubuntu-OpenOffice without removing nearly everything else, too?

---

### Post by mrund on 2007-04-06
Oh man, I downloaded the OO 2.1 tarball (there's no Swedish version yet of the new v2.2), but installation is just way beyond this n00b. Any chance of new OO versions turning up on Synaptic? Otherwise I'll have to invite a friendly linux wiz to dinner.

---

### Post by Hagar Delest on 2007-04-06
> **mrund said:**
> Oh man, I downloaded the OO 2.1 tarball (there's no Swedish version yet of the new v2.2)
You can install the Swedish *language pack*. I've seen a package with the **sv** identifier for Sweden I guess : [http://mirror.switch.ch/ftp/mirror/OpenOffice/extended/2.2.0rc4/]("http://mirror.switch.ch/ftp/mirror/OpenOffice/extended/2.2.0rc4/"). File name is *OOo_2.2.0rc4_20070321_LinuxIntel_langpack_sv.tar.gz*.

Note that the install is really not hard, you just have to copy/paste the commands quoted here (and adapt them for 2.2). No big deal at all.

---

### Post by mrund on 2007-04-06
My first question is where to put the contents of the tarball. In Windows, you generally put such installation files somewhere temporary and then delete them after installation, when the actual program code has ended up in a subdirectory of Program Files. I did that the other day in Ubuntu and discovered that my "temporary" folder on the desktop had in fact been the program I'd installed.

Who decides what programs to offer in the Synaptic package handler?

---

### Post by Hagar Delest on 2007-04-06
> **mrund said:**
> My first question is where to put the contents of the tarball. In Windows, you generally put such installation files somewhere temporary and then delete them after installation, when the actual program code has ended up in a subdirectory of Program Files. I did that the other day in Ubuntu and discovered that my "temporary" folder on the desktop had in fact been the program I'd installed.
It depends on the program. Sometimes, the tarball contains directly the program ready to use (nothing to do at all). Any .deb package is handled by dpkg and therefore will be installed where it has been designed to be installed and will be seen by Synaptic.

> **mrund said:**
> Who decides what programs to offer in the Synaptic package handler?
Ubuntu team. But there is no update for any application (except security issues). To upgrade, you must upgrade the **whole** distribution. This is why you need to install by hand if you want to keep your current flavor.

---

### Post by mrund on 2007-04-06
Open Office is distributed as RPM files, which I gather may be converted to .deb packages. What do you do with the .deb files after installation?

*But there is no update for any application (except security issues). To upgrade, you must upgrade the whole distribution. This is why you need to install by hand if you want to keep your current flavor.*

This confuses me. Are you suggesting that a certin OO version is hard-coded into every Ubuntu distro, and that upgrading OO before a new operating system distro comes along is seen as unnecessary?

Is there any move in the Linux world toward the SETUP.EXE model for program installation, where the makers of software automate the installation process as far as possible?

---

### Post by Hagar Delest on 2007-04-06
> **mrund said:**
> Open Office is distributed as RPM files, which I gather may be converted to .deb packages. What do you do with the .deb files after installation?
Just run the commands quoted, they will handle the .debs.
I think you should read some user guide about Ubuntu or Linux about packages installation.

> **mrund said:**
> *But there is no update for any application (except security issues). To upgrade, you must upgrade the whole distribution. This is why you need to install by hand if you want to keep your current flavor.*

This confuses me. Are you suggesting that a certin OO version is hard-coded into every Ubuntu distro, and that upgrading OO before a new operating system distro comes along is seen as unnecessary?
Yes for the first question. Once a flavor has been released, quite no upgrade for its content because all the integration/dependancies, ... are considered as validated and stable.
No for the second question. Even if it may lead to problems due to dependancies broken, conflicts with other packages, you still can upgrade any soft but with their own method : either a .deb (even converted from RPMs like OOo) or by tarball and direct unzip or by /.make & /.install. Note that I've never had any issue upgrading either OOo or VLC, ...

> **mrund said:**
> Is there any move in the Linux world toward the SETUP.EXE model for program installation, where the makers of software automate the installation process as far as possible?
This is not the thread to discuss this. I'm sure there are some in this forum already.

---

### Post by mrund on 2007-04-06
Many thanks. Which OOo version will be shipped with Feisty?

---

### Post by Hagar Delest on 2007-04-06
It should be 2.2 I guess.

---

### Post by jlh on 2007-06-03
> **sgla1 said:**
> I have installed open office 2.1 on edgy as follows:

1) download OO 2.1 from openoffice.org
2) remove the Ubuntu version of open office -- it's broken anyway 
```
 dpkg -l | grep -i openoffice | cut -d " " -f 3 | sudo xargs apt-get -y --purge remove
sudo apt-get autoremove
```
3) convert the downloaded openoffice files from rpm to deb:
```
cd dir_where_you_extracted_the_OO_zip_file
cd RPMS
sudo alien --scripts --keep-version *.rpm
```
4) install the new version of openoffice:
```
sudo dpkg -i *.deb
cd desktop-integration/
sudo dpkg -i *.deb

```

This should work for dapper as well; ymmv :-)

Reference: [http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370](http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370)

Steve G

This is a good set of instructions to remove and re-install OpenOffice.  However, when I do this, I find that all my existing .odt files are still set to open using the now-removed version of OpenOffice, and not the new one that I have installed.

There must be a way to reset all the existing files to open using the newly installed version, but I don't know what it is.

---

### Post by ernstblaauw on 2007-06-08
I'm running Feisty Fawn 64-bit, with OOo 2.2.0. I wanted to upgrade to 2.2.1 RC, so I downlaoded the latest RC from [http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/](http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/).
However, if I try to instalkl the deb wth dpkg, I get the following error:
```
dpkg: regarding openoffice.org-base_2.2.1-17_amd64.deb containing openoffice.org-base:
 openoffice.org-base conflicts with openoffice.org-bundled
  openoffice.org-core provides openoffice.org-bundled and is installed.
dpkg: error processing openoffice.org-base_2.2.1-17_amd64.deb (--install):
 conflicting packages - not installing openoffice.org-base
dpkg: regarding openoffice.org-calc_2.2.1-17_amd64.deb containing openoffice.org-calc:
 openoffice.org-calc conflicts with openoffice.org-bundled
  openoffice.org-core provides openoffice.org-bundled and is installed.
....
...

```
It goes on for all packages. But when I uninstall the already installed openoffice, also progrms like thunderbird should be uninstalled. Is it possible to just installt he new OOo without uninstalling 2.2.0?

---

