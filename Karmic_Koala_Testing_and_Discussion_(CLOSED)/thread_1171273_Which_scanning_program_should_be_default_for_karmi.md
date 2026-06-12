---
title: "Which scanning program should be default for karmic?"
date: 2009-05-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by davideotape on 2009-05-27
This is another hot topic up for discussion at uds this week. So far it's been xsane all the way, but now gnome-scan has come along, and there is talk of xsane being replaced for 9.10.

More information:

Gnome-scan: [http://projects.gnome.org/gnome-scan/index](http://projects.gnome.org/gnome-scan/index)
Xsane: [http://www.xsane.org/](http://www.xsane.org/)

Personally, I've just downloaded gnome-scan, and it's much friendlier to use than xsane, therefore it's getting my vote.

---

### Post by super.rad on 2009-05-27
Anything is friendlier than xsane, so my vote goes to gnome-scan aswell

---

### Post by Reiger on 2009-05-27
I uses neither because my printer/scanner is two floors downstairs and has an additional for-mass-storage USB port.

---

### Post by binbash on 2009-05-27
Gnome-scan

---

### Post by SuperSonic4 on 2009-05-27
X-Sane, it has fewer deps than gnome-scan. A KDE frontend would be better but there seem to be few.

It would be better if there were better plugins to act as frontends to sane from OOo, gimp, etc

---

### Post by ghindo on 2009-05-27
What is the size of gnome-scan compared to Xsane?  How actively developed is gnome-scan compared to Xsane?  (It doesn't look like gnome-scan has been updated since 2006 or so, whereas Xsane seems very current.)  Is there really a compelling need to switch programs?

---

### Post by davideotape on 2009-05-27
> **ghindo said:**
> What is the size of gnome-scan compared to Xsane?  How actively developed is gnome-scan compared to Xsane?  (It doesn't look like gnome-scan has been updated since 2006 or so, whereas Xsane seems very current.)  Is there really a compelling need to switch programs?

Gnome scan was ~756KB worth of download for me, including 6 dependancies. Not sure if it uses any of the stuff that is already installed in ubuntu though.

---

### Post by SuperSonic4 on 2009-05-27
```
==> gnome-scan dependencies:
 - gegl (already installed)
 - gimp (already installed)
 - sane (already installed)
 - intltool (package found)
```

Shaman (a Pacman frontend) says:

```
==> xsane dependencies:
 - gtk2
 - lcms
 - sane
 - zlib

```

---

### Post by xens on 2009-05-27
Gnome-scan isn't actively maintained, only one people working on it. Canonical should help useful project like that! It's a must have for a distro like ubuntu

---

### Post by davideotape on 2009-05-27
Why does gnome scan depend on gimp? Not that that's a problem because it's already on the liveCD.

---

### Post by olskar on 2009-05-27
Xsane is horrible! Anything but that! It's a disgrace to have that in a distro that otherwise is rather good-looking

---

### Post by super.rad on 2009-05-27
> **SuperSonic4 said:**
> A KDE frontend would be better but there seem to be few.


Skanlite is pretty good, that's what I've used when on KDE

---

### Post by davideotape on 2009-05-27
> **olskar said:**
> Xsane is horrible! Anything but that! It's a disgrace to have that in a distro that otherwise is rather good-looking

Though it look ghastly, it's not exactly the hardest thing in the world to use. Counld do with a beginners mode to get rid of the not-used-very-often features. But why work on xsane when gnome-scan does the same thing much more nicely. Only problem I've noticed is that you have to press two more buttons after pressing the scan option. IMHO, pressing scan should just scan, no questions asked.

---

### Post by olskar on 2009-05-27
> **davideotape said:**
> Though it look ghastly, it's not exactly the hardest thing in the world to use. Counld do with a beginners mode to get rid of the not-used-very-often features. But why work on xsane when gnome-scan does the same thing much more nicely. Only problem I've noticed is that you have to press two more buttons after pressing the scan option. IMHO, pressing scan should just scan, no questions asked.

I can agree it is usable, but the looks is making people blind

---

### Post by MacUntu on 2009-05-27
Scanned a lot of books with Xsane, gotta give gnome-scan a try.

---

### Post by MadsRH on 2009-05-27
Xsane isn't exactly "Scanning for human beings" :lolflag:


Gnome-scan +1

---

### Post by ktp on 2009-05-27
> **MadsRH said:**
> Xsane isn't exactly "Scanning for human beings" :lolflag:

Then we can't have it in Linux for Human Beings!!

---

### Post by BwackNinja on 2009-05-28
Installed gnome-scan, but the one in the repos hangs at open, and the one in the developer's ppa (which is 0.6, the one in the repos is 0.4) crashes for me with an x error. It might be my x input 2 that's giving me some problems, but regardless, I'm going for gnome-scan.

PPA: [https://launchpad.net/~bersace/+archive/ppa](https://launchpad.net/~bersace/+archive/ppa)

---

### Post by CarpKing on 2009-05-29
Xsane has a pretty terrible UI.  If Gnome-scan can be whipped into shape, I say go for it.

---

### Post by ghindo on 2009-05-30
From the "desktop-karmic-gnomescan" gobby document:> we all agree that xsane isn't an option

alternatives are gscan2pdf and gnomescan

gscan2pdf has docs, but not GNOME like docs, uses it's own system
 - has lots of deps
 
gnomescan
 - light on deps compared to gscan2pdf
 - UI looks very "GNOMEish"
 
 
gnomescan isn't packaged for debian

gnomescan in jaunty is very old, version 0.4.1, latest upstream is 0.7.1

Actions should be package latest gnomescan and send to PPA. Test and If it works, decide.


gnomescan seems to work, 0.6.2 is in [https://edge.launchpad.net/~bersace/+archive/ppa](https://edge.launchpad.net/~bersace/+archive/ppa)
 - only tested scanning from an image, not from a scanner
 

Lars will do a test with a real scanner, multi-page

Ken VanDine - will update the package to latest stable for karmic

---

### Post by NCLI on 2009-05-30
Xsana is hands down the worst scanning app I've ever used, so my vote goes to Gnome-scan.

---

### Post by Lorenz on 2009-05-30
I have only known xsane so far and I agree, the graphical interface is horrible. it has lots of settings, but the only one I needed so far is the DPI. Installed gnome scan now and I agree it seems much nicer! also works fine :)

---

### Post by durand on 2009-05-30
I used to use xsane a long time ago but I think gnome-scan fits into ubuntu a hell of a lot better. I'm not sure what that gobby document meant about it not being packaged though...
```
sudo aptitude install flegita
```

---

### Post by Peter76 on 2009-05-31
I always thought Gnome-scan was dead, but after reading this thread I added the PPA and installed it. Looks like a stable app te me which does the job most of us want it to do: scanning something.
Those who want something more out af a scanning app can always install XSane.
Hop Gnomescan will be default for KK

---

### Post by davideotape on 2009-05-31
> **Peter76 said:**
> I always thought Gnome-scan was dead, but after reading this thread I added the PPA and installed it. Looks like a stable app te me which does the job most of us want it to do: scanning something.
Those who want something more out af a scanning app can always install XSane.
Hop Gnomescan will be default for KK

I thought that gnome-scan was in the karmic repositories?

---

### Post by BwackNinja on 2009-05-31
> **davideotape said:**
> I thought that gnome-scan was in the karmic repositories?
an old version, yes.

---

### Post by davideotape on 2009-05-31
> **BwackNinja said:**
> an old version, yes.

When how old is the old version compared to the version in the ppa then?

---

### Post by olskar on 2009-05-31
> **davideotape said:**
> When how old is the old version compared to the version in the ppa then?

I think version 0.4.1, latest upstream is 0.7.1

---

### Post by cdEWoozy on 2009-05-31
> **olskar said:**
> I think version 0.4.1, latest upstream is 0.7.1

0.4.1 was released two years ago, in May 2007.

0.7.1 was released in January 2009:
> After one month of heavy development, i release GNOME Scan 0.7.1. This release is an alpha “preview” of the 0.8 series. It has several regression, however it already show improvments in behaviour, features and support.

See [http://blogs.gnome.org/gnome-scan/](http://blogs.gnome.org/gnome-scan/).

---

### Post by davideotape on 2009-05-31
> **cdEWoozy said:**
> 0.4.1 was released two years ago, in May 2007.

0.7.1 was released in January 2009:


See [http://blogs.gnome.org/gnome-scan/](http://blogs.gnome.org/gnome-scan/).

Why has it not been updated for over two years in the repositories then?

---

### Post by olskar on 2009-05-31
> **davideotape said:**
> Why has it not been updated for over two years in the repositories then?

That is a good question, indeed.

---

### Post by Mark76 on 2009-05-31
Gnomescan depends on GIMP? :confused:

I really wish Ubuntu would get back to the unix philosophy of keeping applications as separate as possible. Rather than the Microsoft philosophy of "If you want this you have to have that too".

---

### Post by cdEWoozy on 2009-05-31
> **davideotape said:**
> Why has it not been updated for over two years in the repositories then?

That's a good question. After reading a bit further, I learned that version 0.5 apparently was a complete rewrite of gnome-scan. Maybe nobody wanted to maintain the rewrite-version, so the old one (0.4.1, the last release before the rewrite) stayed in the debian repos.

See [http://blogs.gnome.org/gnome-scan/2007/06/12/gnome-scan-051-%c2%ab-le-jeu-en-valait-la-chandelle-%c2%bb/](http://blogs.gnome.org/gnome-scan/2007/06/12/gnome-scan-051-%c2%ab-le-jeu-en-valait-la-chandelle-%c2%bb/):
> It’s time for a release after the reset of the project. Gnome Scan 0.5.1 has almost all features of 0.4 and tons of both user visible and internals improvements.

[...]

I provide Ubuntu Feisty Fawn .deb source and i386 .deb at deb [http://bersace03.free.fr/ubuntu](http://bersace03.free.fr/ubuntu) feisty universe .

and [http://live.gnome.org/GnomeScan](http://live.gnome.org/GnomeScan):
> Interesting bits comes with 0.5 series. Gnome Scan has been totally rewritten after some weeks of design (see /Spec) and important decision : make Gnome Scan more dynamic (e.g. less hard coded features). Device properties and processing are no more hard-coded. Another extremly important note about this series is the use of Gegl as ground for processing.

---

### Post by davideotape on 2009-05-31
I've been having a look round the sites and information is all over the place. Can't find much on the newest one. Can someone post a link to the ppa please?

---

### Post by cdEWoozy on 2009-05-31
> **davideotape said:**
> I've been having a look round the sites and information is all over the place. Can't find much on the newest one. Can someone post a link to the ppa please?

[https://launchpad.net/~bersace/+archive/ppa](https://launchpad.net/~bersace/+archive/ppa)

The newest version there is 0.6.2. Could that be the latest stable release? Etienne Bersac (who is developing gnome-scan and also provided this PPA) mentioned 0.7.1 being an alpha preview of the 0.8-series in his blog.

Also noteworthy (from [May 8th, 2009]("http://blogs.gnome.org/gnome-scan/2009/05/08/allocating-time/")):
> Since january, i&#8217;m obviously too involved in projects, scouting, work and life in general. I couldn&#8217;t allocate time for GNOME scan, only the minimal for git migration. Today i migrated GNOME scan to vala master. I can&#8217;t predicate 0.8 release.

---

### Post by davideotape on 2009-05-31
Looks like it's in need of some love :D I'm using 0.4 (or whatever's in the repos), and it works fine for me.

---

### Post by cdEWoozy on 2009-05-31
0.4.1 segfaults after searching for a scanner and finding my webcam instead. I do not have a scanner and find it rather funny that it wants to use my webcam for this purpose, but it still should not segfault.

```
(flegita:9940): GnomeScan-DEBUG: sane_get_devices (0x7fff1039a578, FALSE)
(flegita:9940): GnomeScan-DEBUG: Creating unknown Scanner Noname Laptop_Integrated_Webcam_0.3M (v4l:/dev/video0)
[...]
Segmentation fault
```

0.6.2 from the PPA does it right:
```
** (flegita:10536): DEBUG: Ignoring virtual device v4l:/dev/video0
** (flegita:10536): DEBUG: SANE device v4l:/dev/video0 failed or ignored
```

Apparently there is the possibility to "scan" from an image file, which I tested:
You can't set many options (only 3, if you count the filename as an option) and it is a bit irritating that it completely exits if you click on "Stop" after it has finished scanning. "Forward" also is not the best label to give a button that instantly initiates another scan in this context.
But generally it works and gives you a result without much effort. Maybe you can set more options if you actually have a scanner attached.

Could somebody with access to a scanner test the PPA-version (0.6.2) and post his findings?

I've attached screenshots from a simulated scanning process.

---

### Post by MadsRH on 2009-05-31
So, nothing new from UDS?

Is Xsane still default?

---

### Post by BwackNinja on 2009-05-31
Downgraded from Xi2, flegita still crashes for me when I click my scanner (Lexmark x1185), though downgrading stopped X from hanging when trying to do just about anything in GIMP.

If it doesn't work at all for me, then I wonder where my vote will go...

---

### Post by autocrosser on 2009-05-31
Well--I tried the default .4 gnome-scan then the PPA .6-----both did a rather poor job with my HP 4370 scanner....no real colour define or way to work with the pre-scan image--also no way to scan negatives that the 4370 has special hardware to work with.

Xsane still has a pinkish-colour to the scan, but it can be tuned out rather easily--Also, the option set for Xsane is far & above superior to Gnome-scan---My vote would be to default Gnome-scan, but make Xsane the option for anything above casual scanning---anyone that "really" wants to work with the scan image will find GS VERY limited.

(I must add that I've used Xsane for well on 8 years now & know how to make it do what I want it to....)

---

### Post by Hyper Tails on 2009-05-31
I would say gnome-scan..

---

### Post by ghindo on 2009-06-04
Apparently there's been a bug report open in Launchpad for two years about Gnome Scan that's being acted upon now:

[https://bugs.launchpad.net/ubuntu/karmic/+source/gnomescan/+bug/193818](https://bugs.launchpad.net/ubuntu/karmic/+source/gnomescan/+bug/193818)

---

### Post by Bou on 2009-06-28
I've just tried to use Gnomescan and the scans it creates lack a lot of contrast. Is there any way to tweak brightness / contrast / hue / saturation?

---

