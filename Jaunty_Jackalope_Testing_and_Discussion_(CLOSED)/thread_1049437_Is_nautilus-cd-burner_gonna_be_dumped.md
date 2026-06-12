---
title: "Is nautilus-cd-burner gonna be dumped?"
date: 2009-01-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Bou on 2009-01-24
I was just wondering, since it seems to have disappeared from the places menu as well as the "go to" menu in nautilus.

Thanks!

---

### Post by steeleyuk on 2009-01-24
Yes, eventually. Can't remeber if I saw it on the roadmap for 2.26 or 2.28 but they are shifting focus to Brasero.

---

### Post by gnomeuser on 2009-01-24
> **steeleyuk said:**
> Yes, eventually. Can't remeber if I saw it on the roadmap for 2.26 or 2.28 but they are shifting focus to Brasero.

Brasero has been proposed for this GNOME cycle, there are still integration issues but basically one should expect the functionality to remain just be ported to brasero.

---

### Post by ronacc on 2009-01-24
why don't they dump both nautilus cd burner and brasero and go to one that works, K3B .

---

### Post by Slug71 on 2009-01-24
> **ronacc said:**
> why don't they dump both nautilus cd burner and brasero and go to one that works, K3B .

Whats wrong with Brasero?
I think it works pretty well.

---

### Post by Bou on 2009-01-24
> **ronacc said:**
> why don't they dump both nautilus cd burner and brasero and go to one that works, K3B .

Because of all the dependencies, for example. And because NCB and brasero also work :confused:

---

### Post by perlluver on 2009-01-24
Depending on what you mean by works.  If you mean it crashes randomly, yes it does.  Reported the bugs too, but it is still broken.  Also when trying to burn an ISO, it just will not burn.  So I had to default to using gnomebaker.  I love Linux, and Ubuntu, I hope that these problems can be worked out before Jaunty.

---

### Post by UbuWu on 2009-01-24
> **Bou said:**
> I was just wondering, since it seems to have disappeared from the places menu as well as the "go to" menu in nautilus.

Yes, several programs have been removed from the default install mainly because of space restrictions. The most important are:

nautilus-cd-burner
tracker
deskbar-applet

[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/003246.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/003246.html)

---

### Post by Slug71 on 2009-01-24
Ive never had trouble with Brasero burning images.

---

### Post by ronacc on 2009-01-24
objections I have to brasero , sometimes refuses to burn a cd image to a dvd ( gives incorrect media error ). has poor speed control ( does not give the full range of speed choices) , does not allow you to chose to burn an image as "multi session" . reports suscessful burns when it has either burned a coaster or nothing at all to a disk . reports bad burns that actualy boot and run ( or play if audio) just fine , tends to truncate long mp3 files . burns far too high a percentage of coasters . Note the same objections apply to nautilus cd burner only more .

---

### Post by Gina on 2009-01-24
I agree.  K3b I've found reliable, easy to use, checks MD5Sum, verifies written data, no problem burning CD image to DVD etc.  We need a Gnome equivalent.  (Not that I've ever had any problem running KDE apps under Gnome.)

---

### Post by MacUntu on 2009-01-24
> **ronacc said:**
> objections I have to brasero , sometimes refuses to burn a cd image to a dvd ( gives incorrect media error ). has poor speed control ( does not give the full range of speed choices) , does not allow you to chose to burn an image as "multi session" . reports suscessful burns when it has either burned a coaster or nothing at all to a disk . reports bad burns that actualy boot and run ( or play if audio) just fine , tends to truncate long mp3 files . burns far too high a percentage of coasters . Note the same objections apply to nautilus cd burner only more .

Yup, most of that has happend to me too. I still fire up Nero on XP when it comes to burning CDs/DVDs.

---

### Post by merlyn on 2009-01-24
With regards to K3B being suggested as an alternative to Brasero, isn't an option for those who prefer to run a GNOME only desktop.

Brasero, for me at least, does still have problems however, such as

[LIST]
[*]random crashes
[*]failed burns at high or maximum speeds
[*]does not support all the media my device can, ie I have a +- multi drive, brasero only recognises - media
[/LIST]
Gnomebaker on the other hand is much more stable and capable of burning at any speed I choose. However it still only recognises - media.

Personaly, I'm happy to run K3B, (on GNOME), and based on my experience it suffers none of the problems mentioned above.

More importantly K3B will allow me to use any media my drive is capable of writing to, that is to say both - and + media.

For that reason it is my burning software of choice, even under GNOME.

Let's hope that at some time the GNOME offerings catch up.

---

### Post by ciscosurfer on 2009-01-24
K3B is amazing. Never had any trouble with it whatsoever. All GNOME-based burning apps have always given me trouble in some way. I suppose it could just be my burner, but then why does K3B work perfectly every time?

Someone should port K3B and make a GTK-based version (for all those who NEED a GNOME-only environment.)

---

### Post by caryb on 2009-01-24
The argument of a Gnome only desktop is narrow minded at best! I use KDE but do use best of breed apps! for example I use gparted & tsclient etc. We could better *buntu by not working on duplicate apps when 1 is superior to others. Why not have standard apps across the Ubuntu suit of Distro's & make them best of breed?


Cary

---

### Post by ronacc on 2009-01-24
that would indeed yield an awesome distro if it could be made to work , and on my "work" system I do use the "Chinese restaurant" method of picking apps ( take one from column A and 2 from column B) that does not work for everything . K3B runs fine under gnome but another of my favorites , super karamba , doesn't do as well . I fear that the logistics of a truly "mix n match" offering would be a nightmare , but where it does work well why not go with the best .

---

### Post by syko21 on 2009-01-24
The amount of dependencies on a default installation like that would be enormous and put us squarely in the realm of only live-dvd media.

---

### Post by gregh on 2009-01-24
Dependencies would be a nightmare if you wanted a lean system. 
I like k3b as much as the next person but i don't install it at the moment because of all the KDE libraries i currently don't want.

I have nothing against KDE it's just I use Gnome and need it to be as light weight as possible, other people are different to me. 
For me, a Gnome burner with all the advantages of k3b would be great.

my 2c

---

### Post by ronacc on 2009-01-24
sort of OT , there is a KDE/Superkaramba app , solarviewer , that puts the current soho satelite images on your desktop , does anyone know of a gnome equivalent ?

---

### Post by Slug71 on 2009-01-25
> **ronacc said:**
> sort of OT , there is a KDE/Superkaramba app , solarviewer , that puts the current soho satelite images on your desktop , does anyone know of a gnome equivalent ?

I too want to know this. That sounds cool.

---

### Post by Slug71 on 2009-01-25
I'm sure Brasero will catchup to K3B.
If version numbers are anything to go by then Brasero is still slightly behind K3B. 
Brasero 0.9.1(released 5 days ago)
K3B 1.0.5

K3B will probably have version 1.1 out soon though.

---

### Post by cl333r on 2009-01-25
Unfortunately .. version numbers.. are just that :)

---

### Post by mikeize on 2009-01-25
Too bad.  I love having the integrated burner.  I really only use it for burning ISOs, but I would miss it were it gone.  Never had a single problem with it, and I use it regularly.  For other burning, I use K3b in gnome... it's the best.

Glad to hear that tracker is getting dropped.  Ugh.  That was the first program I ever disabled in Ubuntu.  Such a resource hog.

---

### Post by bruce89 on 2009-01-25
> **mikeize said:**
> Too bad.  I love having the integrated burner.  I really only use it for burning ISOs, but I would miss it were it gone.  Never had a single problem with it, and I use it regularly.  For other burning, I use K3b in gnome... it's the best.

Brasero has a Nautilus extension which is much the same as the n-c-b ISO thingy.

---

### Post by Gina on 2009-01-25
> **mikeize said:**
> Too bad.  I love having the integrated burner.  I really only use it for burning ISOs, but I would miss it were it gone.  Never had a single problem with it, and I use it regularly.  For other burning, I use K3b in gnome... it's the best.If you use K3b why use anything else for burning?  It does the lot.

---

### Post by ssam on 2009-01-25
will we still be ablt to right click on an .iso file and choose write to disk.

---

### Post by Bou on 2009-01-25
> **ssam said:**
> will we still be ablt to right click on an .iso file and choose write to disk.

Of course. Or you can just double-click it.

---

### Post by MaX on 2009-01-25
I have a question, of all of you that has had problems with Brasero, how many of you have contributed with a bug report or crash stack?

It's hard for the program to get better if people don't help.

---

### Post by MacUntu on 2009-01-25
> **caryb said:**
> by not working on duplicate apps when

I disagree. Diversity is crucial for evolution.

Having two apps for the same task in ONE distribution is something that needs to be avoided, though.

---

### Post by Yellow Pasque on 2009-01-25
> I fear that the logistics of a truly "mix n match" offering would be a nightmare
Actually, it works quite well if you choose programs that don't rely on unnecessary integration and are written by devs that remember that Linux is SUPPOSED to be modular (it ain't Windows). Xfce is a great environment for this approach.

---

### Post by bruce89 on 2009-01-25
> **Temüjin said:**
> Xfce is a great environment for this approach.

I don't think that concept is limited to Xfce. GNOME for one has a module proposal period every cycle, which Ubuntu promptly disregards.

---

### Post by merlyn on 2009-01-25
> **caryb said:**
> The argument of a Gnome only desktop is narrow minded at best! I use KDE but do use best of breed apps! for example I use gparted & tsclient etc. We could better *buntu by not working on duplicate apps when 1 is superior to others. Why not have standard apps across the Ubuntu suit of Distro's & make them best of breed?Cary

G'day Cary.

I agree that a best of breed policy, (for want of a better word), when choosing  applications is a good way to go. 

Hence, for example I use K3B, as my burning application of choice even though I currently use GNOME.

My comment, & to quote from my earlier post, (is this bad form?),
> **merlyn said:**
> With regards to K3B being suggested as an alternative to Brasero, isn't an option for those who prefer to run a GNOME only desktop.
was an oblique reference to an earlier post in this thread where it was mentioned that people may not want to install K3B under GNOME due to additional dependencies.

[OT] btw, have you ever attended a humbug meeting? [/ot]

> **Slug71 said:**
> I'm sure Brasero will catchup to K3B.
If version numbers are anything to go by then Brasero is still slightly behind K3B. 
Brasero 0.9.1(released 5 days ago)
K3B 1.0.5

Hi Slug71,

An applications version number is an indication of it's developmental maturity rather than it's feature set.

In this case my comment with regard to the 'catching up' that Brasero & Gnomebaker need to do, is in feature parity with K3B with regard to media support.

Currently both Brasero & Gnomebaker will only recognise - media.

K3B on the will recognise both + and - media. 

Thus utilising the full capability of my burning hardware, hence for me K3B is definitley the best of breed when it comes to burning applications.

---

### Post by bruce89 on 2009-01-25
> **merlyn said:**
> An applications version number is an indication of it's developmental maturity rather than it's feature set.

Version numbers have no meaning at all, look at Firefox.

---

### Post by Gina on 2009-01-25
About the only software I've come across where version numbers actually mean something is Ubuntu :lolflag:

---

### Post by merlyn on 2009-01-25
> **bruce89 said:**
> Version numbers have no meaning at all, look at Firefox.

> **Gina said:**
> About the only software I've come across where version numbers actually mean something is Ubuntu :lolflag:

I sincerely apologise for using a 'generalism'.

However as an application 'progresses' in it's 'development' it is reasonable to state that, with each successive release, bugs are fixed, (though there may be regressions and/or new bugs), and / or new features introduced, gui modifications made, (if aplicable).

In some cases a feature may also be removed.

Subsequently the version number also changes, for example 1.01.01 to 1.01.05 or some such.

I certainly hope that it is not going to become necessary, to provide an explanation for each and every statement made in a post.

That would be tiresome. ;)

---

### Post by Gina on 2009-01-26
I was agreeing with you in general - sorry if you thought I was criticising your post :)

---

### Post by amano on 2009-01-26
> **bruce89 said:**
> Brasero has a Nautilus extension which is much the same as the n-c-b ISO thingy.

Yes. That was an upstream decision. n-c-b will be dumped and be replaced by the brasero nautilus extension that does mostly the same...

---

### Post by Slug71 on 2009-01-26
Brasero 0.9.1 just came to Jaunty.

---

### Post by bruce89 on 2009-01-26
> **merlyn said:**
> I sincerely apologise for using a 'generalism'.

However as an application 'progresses' in it's 'development' it is reasonable to state that, with each successive release, bugs are fixed, (though there may be regressions and/or new bugs), and / or new features introduced, gui modifications made, (if aplicable).

In some cases a feature may also be removed.

Subsequently the version number also changes, for example 1.01.01 to 1.01.05 or some such.

I certainly hope that it is not going to become necessary, to provide an explanation for each and every statement made in a post.

That would be tiresome. ;)

Don't worry, I just wanted to get my usual dig in about Firefox's version number bloat.

TeX's version number is the best, the new digit from &#960; is added to the end.

---

### Post by Foaming Draught on 2009-01-27
I don't want to have to use a KDE app, but I've already loaded kturberling ("potato man") for my niece, so I might as well have k3b as well, and use Linux to burn .iso instead of DeepBurner under XP.  Brasero just will not burn an .iso, or at least not dependably and/or regularly.  It doesn't, and I'm afraid that I don't believe folk here who are saying that it does.

As to posting a bug report, what's wrong with brasero is features, or lack thereof, so what's the point of wasting bandwidth?  I can't control its recording speed, that's a glaring deficiency.  .iso should be burned at x2, x4 at the very fastest.

---

### Post by syko21 on 2009-01-27
> **ronacc said:**
> objections I have to brasero , sometimes refuses to burn a cd image to a dvd ( gives incorrect media error ). has poor speed control ( does not give the full range of speed choices) , does not allow you to chose to burn an image as "multi session" . reports suscessful burns when it has either burned a coaster or nothing at all to a disk . reports bad burns that actualy boot and run ( or play if audio) just fine , tends to truncate long mp3 files . burns far too high a percentage of coasters . Note the same objections apply to nautilus cd burner only more .

why bother with brasero? I always right click on the iso and use the Write to Disc option. Works flawlessly every time for me.

---

### Post by ronacc on 2009-01-27
because I do more than just burn ISOs and also want more control over how the ISO is burned .

---

### Post by steeleyuk on 2009-01-27
> **syko21 said:**
> why bother with brasero? I always right click on the iso and use the Write to Disc option. Works flawlessly every time for me.

Brasero can do exactly the same. It just offers more if you need it...

---

