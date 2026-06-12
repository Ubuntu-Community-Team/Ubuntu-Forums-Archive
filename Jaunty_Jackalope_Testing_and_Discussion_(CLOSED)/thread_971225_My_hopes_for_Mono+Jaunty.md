---
title: "My hopes for Mono+Jaunty"
date: 2008-11-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by gnomeuser on 2008-11-04
Today Mono branches for 2.2[1], slated to come out in December, a target they are well on their way to meeting. The roadmap[2] puts 2.4 in April 2009, which some highly interesting planned features, most important will probably be MonoDevelop 2.0 with integrated debugging support (aside the normal things likce better coverage, bugfixes and performance increases)

I hope Ubuntu will aggressively adopt snapshots as they come out. Upstream has very good QA so stability can be expected to be good. The updates are timely and well tested. As such the risk from early adoption should be minimal. Unfortunately the delivery date for Jaunty is also late April so Mono 2.4 would have to enter at the branch time (should likely as with 2.2 be expect a month prior to release). After the branch point the churn is minimal so updates should be safe to issue and if a conflict occurs between the final release dates then a post release update would be very low risk. Not doing this would once again mean shipping an Ubuntu without the latest version of Mono which would be a shame.

Additionally I hope to see Monotorrent and Monsoon in the repos as well as Moonlight. The latter hopefully default in the install so Silverlight websites will work out of the box on Ubuntu. Outside having the ever increasing number of Silverlight pages working for users, Moonlight presents an interesting approach to GUI development for us on the desktop. Novell have already done some testing on this and it shows great promise in delivering very sexy looking applications which are also easy to create.

[1] [http://lists.ximian.com/pipermail/mono-devel-list/2008-November/029629.html](http://lists.ximian.com/pipermail/mono-devel-list/2008-November/029629.html)
[2] [http://mono-project.com/Roadmap](http://mono-project.com/Roadmap)

---

### Post by ShirishAg75 on 2008-11-04
I am not at all thrilled about mono for it could at any point have any patent issues or stuff like that. In fact the sore point has been that GNOME has been using quite a bit of Mono lately which is not good atleast from my perspective.

---

### Post by directhex on 2008-11-05
> **gnomeuser said:**
> Upstream has very good QA

Upstream has terrible QA, which is why releases can take so long to come out (especially 2.0). Just take a peek at the patch set we've been forced to apply to previous releases.

And an unfortunate blocker on updating major things like Mono which are driven at the Debian end is the continued delay in the release of Debian Lenny. I'll mail upstream to make them aware of the Jaunty schedule - they may tag an RC build a little early to help us (the packagers mailing list was warned of 2.0 about half a week early)

If it makes you feel any better, Moonlight packages are prepared and ready for upload - I'm waiting for the imminent 1.0 release before doing so.

Monodevelop... well, we've been warned more than once not to put one of the 1.9 alphas into a stable release, so we've done as told. Once 2.0 is released "proper", packaging will start

Monsoon... well, packagers welcome, but we have a lot on our plate with Mono and Monodevelop and Moonlight, and the changes needed to every single Mono package following packaging restructure in out 2.0 packages (which will shrink Tomboy dependencies by about 20-40%)

---

### Post by Half-Left on 2008-11-05
> **ShirishAg75 said:**
> I am not at all thrilled about mono for it could at any point have any patent issues or stuff like that. In fact the sore point has been that GNOME has been using quite a bit of Mono lately which is not good atleast from my perspective.

Mono doesn't come with GNOME or is part of GNOME(Tomboy is optional). I wish people would go and educated them selfs what Ubuntu use and GNOME use, Ubuntu doesn't = GNOME since they have pretty much no say.

Just so you all know.

Tomboy is a mono app and IS NOT a dependency with the GNOME build and is optional, you can remove it without removing any part of GNOME.

---

### Post by plun on 2008-11-05
Yup... I also hope so.

Miguel de Icazas PDC talk is up at Channel 9

[http://channel9.msdn.com/pdc2008/PC54/](http://channel9.msdn.com/pdc2008/PC54/)

You need Silverlight for watching....):P


I cannot understand how the DRM content protection will be solved in Moonlight...:confused:

Maybe we must "offer" that....?

---

### Post by gnomeuser on 2008-11-05
> **plun said:**
> Yup... I also hope so.

Miguel de Icazas PDC talk is up at Channel 9

[http://channel9.msdn.com/pdc2008/PC54/](http://channel9.msdn.com/pdc2008/PC54/)

You need Silverlight for watching....):P


I cannot understand how the DRM content protection will be solved in Moonlight...:confused:

Maybe we must "offer" that....?

The same way we do everywhere else, it is implemented in the media decoder not Moonlight as such. Moonlight currently uses ffmpeg for the free codecs option or a set of licensed codecs supplied by Microsoft and ported by Novell (the latter closed source). I believe they are planning a port to GStreamer (at least Miguel has stated in a talk that Arron Bockover was doing the work).

Regardless, DRM is not a Moonlight problem, the support comes in the framework that is used to decode the media and as it is already known, DRM is entirely breakable. We support it today in a few formats, Moonlight does not add to or detract from the DRM problem, it merely adds support for the growing number of Silverlight websites and you even get gratis licensed codec support for use in websites (as paid for by Microsoft). I am very pleased that Linux users will not once again have to sit in the snow as we have done with Flash for years as Moonlight is a 100% proven compatible implementation, tested against the same set of conformance tests as Microsoft uses. I like that our users can access content on equal footing using only Free Software.

---

### Post by directhex on 2008-11-05
> **plun said:**
> You need Silverlight for watching....):P

[http://mschnlnine.vo.llnwd.net/d1/pdc08/WMV-HQ/PC54.wmv](http://mschnlnine.vo.llnwd.net/d1/pdc08/WMV-HQ/PC54.wmv)

Or Moonlight 1.0, which is branched in SVN

> Maybe we must "offer" that....?

Unless I hear massive demand to the contrary, Moonlight in Ubuntu will be linked against the Free codecs already provided in the distro (i.e. ffmpeg, or gstreamer if/when they port it to gstreamer). The MS codecs will not be supported without a rebuild. Perhaps I could package both as interchangeable, perhaps not.

---

### Post by David A Knight on 2008-11-05
> **ShirishAg75 said:**
> I am not at all thrilled about mono for it could at any point have any patent issues or stuff like that. In fact the sore point has been that GNOME has been using quite a bit of Mono lately which is not good atleast from my perspective.

And how is Mono more vunerable to aleged patent infringment than any other open source software? Answer? It isn't.  It is about time people dropped the patent infringment nonsense or nothing in open source would be done at all.  

How much of GNOME has been using mono?  We have Fspot, we have Tomboy, we have... errr, Banshee, which isn't part of GNOME, we have.... errr.... what?  Nothing else that is officially part of GNOME comes to mind.  Now if you put a developer hat on you have to think, why code in C when you can use C#, the difference is huge.  C# is a big big win for maintainability and productivity.  Yeah you can use Python or some other language (Not a fan of Python at all) but Mono and the languages its CLR supports is a very tempting option.  Even if MS get awkward about the parts that are not ECMA standards who cares?  GTK# and the other Linux/Unix related libraries that Mono encompasses has nothing to do with MS, the core CLR/C# are standards we can just work from there.

---

### Post by David A Knight on 2008-11-05
> **directhex said:**
> Upstream has terrible QA, which is why releases can take so long to come out (especially 2.0). Just take a peek at the patch set we've been forced to apply to previous releases.


Simple question, why haven't these patches been submitted to upstream?  If these patches had to be applied to previous versions they should have been submitted, and so 2.0 should not require them.  Something has broken down somewhere.

> **directhex said:**
> 
Monodevelop... well, we've been warned more than once not to put one of the 1.9 alphas into a stable release, so we've done as told. Once 2.0 is released "proper", packaging will start


Understandable to some extent, but having tracked trunk of Monodevelop from svn I'm not sure if that was the right decision as there were some great improvements in features and stability although in the past few weeks trunk has gone to a 2.0 dependency, but then it is now a 2.0 alpha rather than 1.9.

---

### Post by zekopeko on 2008-11-05
i hope this will all happen. as an observer i can only say that mono is really accelerating it's development IMO.
and there is great software out there based on mono. gnome-do FTW :D

---

### Post by directhex on 2008-11-06
> **David A Knight said:**
> Simple question, why haven't these patches been submitted to upstream?  If these patches had to be applied to previous versions they should have been submitted, and so 2.0 should not require them.  Something has broken down somewhere.

They're mostly fixes taken from post-2.0 Mono SVN. There is now dialogue between pkg-mono and upstream which wasn't previously there, but stable releases still have critical bugs in them that we need to fix and QA

> Understandable to some extent, but having tracked trunk of Monodevelop from svn I'm not sure if that was the right decision as there were some great improvements in features and stability although in the past few weeks trunk has gone to a 2.0 dependency, but then it is now a 2.0 alpha rather than 1.9.

If upstream are telling us not to release an alpha in a stable OS, we'll respect that. I *KNOW* the 1.0 packages suck right now, I really do, but I don't like the alternative of ignoring Upstream warnings. That said, 2.0 should be final well in time for Jaunty

---

### Post by sdowney717 on 2008-11-06
give me an example of a .net application I can run with mono on linux.
something I can download.

---

### Post by gnomeuser on 2008-11-06
> **sdowney717 said:**
> give me an example of a .net application I can run with mono on linux.
something I can download.

Anything that depends on Mono in the repos. MonoDevelop, banshee, f-spot, gnome-do and many others are .NET apps, written in C#. They are compiled into the very same CLR as the Microsoft reference implementation uses. Mono lives up to the ECMA standard.

If you want a sample program not written specifically by Linux people, the MOMA code analyser will tell you if a given .NET application will run using Mono. Of which roughly 60% should do without any changes.

E.g. WinRickVoter, a small program that will submit votes for Rick Ashley as the best act ever in a MTV contest. Written in Windows, for the Microsoft implementation. No source code comes with it.. and yet, Mono runs it without a single problem. Just one small example.

[http://www.bestactever.com/scripts/WinRickVoter.latest.zip](http://www.bestactever.com/scripts/WinRickVoter.latest.zip)

Novell are actively helping many companies to make their code able to run using Mono, they released tools to analysis the areas that Mono need to implement to get support as well as which areas the companies can change (e.g. embedding IE directly, which can be done with a wrapper instead that will embedded the gecko rendering engine from Firefox instead when on Linux). Novell are also porting applications for companies who want to move to Linux, the biggest of such projects is probably the Unity game design platform which now not only will run using Mono, it actually embeds Mono to do scripting (which is really really fast).

---

### Post by ruik on 2008-11-06
> **sdowney717 said:**
> give me an example of a .net application I can run with mono on linux.
something I can download.

[http://www.majestic12.co.uk/projects/dsearch/download.php](http://www.majestic12.co.uk/projects/dsearch/download.php)

---

### Post by sakabato on 2008-11-06
> **sdowney717 said:**
> give me an example of a .net application I can run with mono on linux.
something I can download.

NUnit: (with winforms GUI): [http://www.nunit.org/index.php?p=download](http://www.nunit.org/index.php?p=download)


NClass:  (with Winforms) : [http://nclass.sourceforge.net/downloads.html](http://nclass.sourceforge.net/downloads.html)


.NET Reflector (with Windows Forms):[http://www.red-gate.com/products/reflector/](http://www.red-gate.com/products/reflector/)

Following frameworks (originally prepared for windows .net):
DB4O, NHibernate, Rhino Mocks, Log4net


Others: Any Console or Windows forms application doesn't use P/INvoke, Any ASP.NET application doesn't use web parts

---

### Post by Shin_Gouki2501 on 2008-11-07
i never understand in the first place why so many "linux" people like mono more than java 
:/

imo java is far for heading towards opensource then  mono is..

---

### Post by directhex on 2008-11-07
> **Shin_Gouki2501 said:**
> i never understand in the first place why so many "linux" people like mono more than java 
:/

imo java is far for heading towards opensource then  mono is..

Really? That's odd, because I was under the impression that Mono has been Free Software since mid 2002 (i.e. first release). Where is it meant to head from "completely free software", exactly?

As for why... Perhaps because with .NET you can write in the language of your choice yet still get the benefits of a central runtime (a bit like if you could effectively compile python to .class and interop fine with any .class). Or because Mono in a distro like Ubuntu is a tiny fraction of the size on disk that Java would require, due to superior packaging concepts? Or the way Mono apps look like native C apps, whilst Swing sucks and non-Swing with Java sucks worse? Or because people are learning C# and VB.NET et al, and are delighted to have access to the same languages they already know when migrating from legacy OSes?

There's a selection of reasons for you.

---

### Post by plun on 2008-11-07
> **gnomeuser said:**
> 
Novell are actively helping many companies to make their code able to run using Mono, they released tools to analysis the areas that Mono need to implement to get support as well as which areas the companies can change (e.g. embedding IE directly, which can be done with a wrapper instead that will embedded the gecko rendering engine from Firefox instead when on Linux). Novell are also porting applications for companies who want to move to Linux, the biggest of such projects is probably the Unity game design platform which now not only will run using Mono, it actually embeds Mono to do scripting (which is really really fast).

Well...

A blog from ZDnet and this guy is a Adobe employee

[http://blogs.zdnet.com/Stewart/?p=944](http://blogs.zdnet.com/Stewart/?p=944)

> **Linux**
In the Q&A, Tim Anderson asked about Linux support. Right now Silverlight has partial support for 1.0 (**_though it doesn&#8217;t include video or MP3 playback_**, two of the main features of Silverlight 1.0) an**_*d there is no support for 2 on Linux right now*_**. As Tim notes, it&#8217;s misleading to tout the cross platform aspect of Silverlight without an actual release. It&#8217;s also surprising that there was absolutely nothing in terms of a roadmap for Linux. My hunch is that they wanted something to announce for PDC and this may be it. As Brian Goldfarb mentioned in the Q&A session, **Miguel de Icaza, who runs the Moonlight effort, has a session at PDC although his session doesn&#8217;t say anything about Silverlight/Moonlight** so I&#8217;m not sure what to make of that.

**Net services without DRM protection  ?**   I find it rather useless it this question cannot be resolved.

Maybe a few companys can find a few solutions.... but they probably goes directly to Azure.

Totally worthless for a end-user....  "Singing in the rain" again

---

### Post by directhex on 2008-11-07
> **plun said:**
> **Net services without DRM protection  ?**   I find it rather useless it this question cannot be resolved.

Maybe a few companys can find a few solutions.... but they probably goes directly to Azure.

Totally worthless for a end-user....  "Singing in the rain" again

Nobody to give an impartial info on an Adobe Flash competitor like an Adobe guy.

Moonlight 1.0 has been branched, has *complete* 1.0 support, and will use media either by being compiled against FFmpeg or by using the built-in binary-codecs-from-microsoft function of Moon 1.0. The packages in Jaunty will use FFmpeg.

The preview 0.8 Firefox extensions hidden on go-mono.com don't have media - that doesn't mean it can't be done:

[[img]http://www2.apebox.org/wordpress/wp-content/gallery/00-single/normal_moonlight.png[/img]](http://www2.apebox.org/wordpress/wp-content/gallery/00-single/moonlight.png)

So tell me, where is Adobe's AMD64 support? I have 64-bit Moon here.

---

### Post by Magnes on 2008-11-07
It should be made possible to easily install the closed codecs from Microsoft also. I suppose alternative packages will be made by many but maybe they could be made available in comercial repository? I don't know what the EULA is for the codecs.

---

### Post by plun on 2008-11-07
> **directhex said:**
> 
So tell me, where is Adobe's AMD64 support? I have 64-bit Moon here.

Well, I never uses 64 bits for clients....never address so large memory so I cannot see any reason running 64 bit on an client.

But... Adobe 10 seems to work with IA 64 libs

In this case about Moonlight its about DRM protected contents and nearly all "big media sharks" uses DRM for media.

Except for example **low quality movies** from YouTube...

So I find Moonlight **_2.0_** rather worthless if 90% of all content cannot be viewed...  "Singing in the rain with RMS"...

---

### Post by directhex on 2008-11-07
> **Magnes said:**
> It should be made possible to easily install the closed codecs from Microsoft also. I suppose alternative packages will be made by many but maybe they could be made available in comercial repository? I don't know what the EULA is for the codecs.

Moon 1.0 in Ubuntu will come with media support built in, via FFmpeg

Moon 1.0 from Novell (via a .xpi file) will have no media support - but automatically download & add codecs from Microsoft when required

---

### Post by plun on 2008-11-07
> **directhex said:**
> 
Moon 1.0 from Novell (via a .xpi file) will have no media support - but automatically download & add codecs from Microsoft when required

Moon 1.0 cannot be used....

Its a joke to test the plugin with test pages.

[http://go-mono.com/moonlight/MoonlightStatus.aspx](http://go-mono.com/moonlight/MoonlightStatus.aspx)

I define it as worthless "junk"...  IMHO

---

### Post by chrisccoulson on 2008-11-07
> **gnomeuser said:**
> Additionally I hope to see Monotorrent and Monsoon in the repos as well as Moonlight. The latter hopefully default in the install so Silverlight websites will work out of the box on Ubuntu. 

I'm currently working on packaging the latter for Jaunty. Although it will probably be in Universe to start off with, so not installed by default.

---

### Post by directhex on 2008-11-07
> **plun said:**
> Moon 1.0 cannot be used....

Its a joke to test the plugin with test pages.

[http://go-mono.com/moonlight/MoonlightStatus.aspx](http://go-mono.com/moonlight/MoonlightStatus.aspx)

I define it as worthless "junk"...  IMHO

You can define it as mature cheddar if you like, doesn't make you right.

How does a list of real-world sites which all show as at least "working but slow" count as "worthless junk"? Moonlight is tested against the very same set of hundreds of Microsoft test cases (i.e. the ones MS use to ensure new versions won't break old sites), and ALSO tested on real-world pages as linked.

---

### Post by directhex on 2008-11-07
> **chrisccoulson said:**
> I'm currently working on packaging the latter for Jaunty. Although it will probably be in Universe to start off with, so not installed by default.

Please get into contact with pkg-mono at Debian, rather than letting things go into Ubuntu only. We can help you with your packaging, and ensure that both distros benefit from your efforts

---

### Post by plun on 2008-11-07
> **directhex said:**
> You can define it as mature cheddar if you like, doesn't make you right.

How does a list of real-world sites which all show as at least "working but slow" count as "worthless junk"? Moonlight is tested against the very same set of hundreds of Microsoft test cases (i.e. the ones MS use to ensure new versions won't break old sites), and ALSO tested on real-world pages as linked.

Of course it is worthless junk if it doenst work !
Gnash is the same.

and there is no Moonlight 2.0.

And it must also work for DRM protected content....!

For example this supplier will run Siverlight/Moonlight

[http://www.movenetworks.com/](http://www.movenetworks.com/)

They are for sure sitting in MS-Redmonds knee...

There is no room for "Singing in the rain with RMS"

Check Windows 7 !!!!!

---

### Post by directhex on 2008-11-07
> and there is no Moonlight 2.0.

Silverlight 2.0 has been out for 3 weeks. Seriously, how fast do you expect developers to develop?

> For example this supplier will run Siverlight/Moonlight

Future tense. It doesn't right now, which is why it doesn't work with Moon.

[http://www.movenetworks.com/](http://www.movenetworks.com/)

They are for sure sitting in MS-Redmonds knee...[/quote]

So they're planning on dumping their current proprietary Windows plugin for Silverlight. That's a bad thing?

> There is no room for "Singing in the rain with RMS"

Erm... what?

> Check Windows 7 !!!!!

I love it when people try to change the topic on Mono threads. "Look, C# is easy to develop" "Windows 7 will require a DNA sample in order to work!" "Erm... quite"

---

### Post by plun on 2008-11-07
Well... of course and Ballmer is smart...

[http://www.movenetworks.com/blog/move-networks-announces-strategic-partnership-with-microsoft](http://www.movenetworks.com/blog/move-networks-announces-strategic-partnership-with-microsoft)

Swedish public Television already uses Moves junk for HD broadcasts.

DRM protected of course....


I will follow Miguels blog
[http://tirania.org/blog/](http://tirania.org/blog/)

And also Moonlights download page:
[http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)


Todays version is a joke....totally useless.


EDIT

RMS does not use such functions and then its easy for him to "Singing in the rain"
if something doesnt work.....Fedora can somtimes also use the same ideas.

---

### Post by chrisccoulson on 2008-11-07
> **directhex said:**
> Please get into contact with pkg-mono at Debian, rather than letting things go into Ubuntu only. We can help you with your packaging, and ensure that both distros benefit from your efforts

It seems Debian are actually already working on packaging it at the moment

---

### Post by plun on 2008-11-07
> **chrisccoulson said:**
> It seems Debian are actually already working on packaging it at the moment

What I have seen its more about what they must remove from NET functionality...  maybe all license issues is resolved but a check with upstream version cannot be wrong.

[http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)

Also according to a Launchpad bug report I read about upgrading to ver 2.0.

It was "mission impossible", ... "too many bugs"... the same as with OpenOffice 3.0 :confused:   

Maybe better to skip all Debian discussions...

---

### Post by directhex on 2008-11-07
> **plun said:**
> It was "mission impossible", ... "too many bugs"... the same as with OpenOffice 3.0 :confused:   

**MY** bug report. You're misrepresenting several things, including a little thing called "Feature Freeze"

You noticed Intrepid released without OOo3, yes? Same reason. Big upstream, LOTS of QA required.

> **plun said:**
> Well... of course and Ballmer is smart...

Ballmer is a fat ape. I have nothing positive to say about him or the way he manages the business end of his company.

> Swedish public Television already uses Moves junk for HD broadcasts.

DRM protected of course....

Then roll on the death of Move's junk, in favour of a more cross-platform Silverlight. Absolute worst case scenario, it would mean opening up their service to people running MacOS, if not people running Moon on Linux too

> RMS does not use such functions and then its easy for him to "Singing in the rain"
if something doesnt work.....Fedora can somtimes also use the same ideas.

Fedora disables a LOT of useful functionality, leading to a castrated distro which frustrates users. Reckon that's the way to attract people away from Windows?

> **plun said:**
> What I have seen its more about what they must remove from NET functionality...  maybe all license issues is resolved but a check with upstream version cannot be wrong.

Mono 1.9.1 and lower in Debian have some ASP.NET functionality removed, as it is Creative Commons licensed (and CC is not Free Software). Mono 2.0 has the disabled functionality replaced. Moonlight packages have no removed functionality - other than any possible loss coming from using Free FFmpeg instead of Microsoft's binary codecs

> **plun said:**
> And also Moonlights download page:
[http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)


Todays version is a joke....totally useless.

0.8 isn't enormously functional, which is why I haven't bothered to upload packages.

But you were claiming to have tested 1.0. Which is it - 0.8 packages with 0 media support, or hand-built 1.0? 'cos 1.0's a pig to build from SVN right now.

---

### Post by Shin_Gouki2501 on 2008-11-09
why NOT to go with mono:
[http://flyingfrogblog.blogspot.com/2008/10/mono-20.htm](http://flyingfrogblog.blogspot.com/2008/10/mono-20.htm)

---

### Post by smartboyathome on 2008-11-09
> **Shin_Gouki2501 said:**
> why NOT to go with mono:
[http://flyingfrogblog.blogspot.com/2008/10/mono-20.htm](http://flyingfrogblog.blogspot.com/2008/10/mono-20.htm)

Page not found? And besides, what people spread about Mono is mostly FUD, imo, and I haven't seen much hard evidence against it, and mostly a bunch of "what if" scenarios involving Microsoft getting greedy.

---

### Post by directhex on 2008-11-09
> **Shin_Gouki2501 said:**
> why NOT to go with mono:
[http://flyingfrogblog.blogspot.com/2008/10/mono-20.htm](http://flyingfrogblog.blogspot.com/2008/10/mono-20.htm)

Sorry, the page you were looking for in the blog The Flying Frog Blog does not exist. 

Do people even check the links they're copy-pasting from discredited sources, when pushong the anti-Mono line?

---

### Post by plun on 2008-11-09
> **directhex said:**
> **MY**
But you were claiming to have tested 1.0. Which is it - 0.8 packages with 0 media support, or hand-built 1.0? 'cos 1.0's a pig to build from SVN right now.

Well according to Moonlights **click & run** Firefox addon install the experimental version is 1.0

[http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

It is presented as 0.8 within "addons".... doesn't work nevertheless.
Maybe also a Firefox challenge...:confused:


Agrees about building this "pig"....:---)

I took the svn code for 2.0 and those da--ed monopackages in a mess and no build-dep for gtk-sharp and gnome-sharp

It brakes...

Found a dutch howto....

[http://kees.tweakblogs.net/blog/801/silverlight-ek-streams-onder-linux.html](http://kees.tweakblogs.net/blog/801/silverlight-ek-streams-onder-linux.html)

Building the whole Mono stack....  #-o

Must be a script somewhere....:lolflag:

---

### Post by smartboyathome on 2008-11-09
Heres the real link:
[http://flyingfrogblog.blogspot.com/2008/10/mono-20.html](http://flyingfrogblog.blogspot.com/2008/10/mono-20.html)

But this is saying a couple things wrong right off the bat. Mono was intended to bring the .NET *ECMA STANDARD* to Linux, not Microsoft's whole .NET language. It keeps the patented stuff separate upon install, and a lot of the claims are not backed up by evidence (ie, "Mono's code generator generates native code that is slower than almost all other compiled languages."). It also starts bashing Mono for using a stable base instead of taking years to build a new one (which he probably would have flamed on as well since it would taken longer to do that).

---

### Post by directhex on 2008-11-09
> **plun said:**
> Well according to Moonlights **click & run** Firefox addon install the experimental version is 1.0

[http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

It is presented as 0.8 within "addons".... doesn't work nevertheless.
Maybe also a Firefox challenge...:confused:

Ah. There's the confusion. It's *Moonlight* 0.8, which has support for *Silverlight* 1.0. Like I said, 0.8 isn't complete enough for me to bother uploading packages.

> Agrees about building this "pig"....:---)

The tarballs aren't that bad. SVN is a royal pain though, as you need to do a lot of things which are free with tarballs.

> I took the svn code for 2.0 and those da--ed monopackages in a mess and no build-dep for gtk-sharp and gnome-sharp

It brakes...

Found a dutch howto....

[http://kees.tweakblogs.net/blog/801/silverlight-ek-streams-onder-linux.html](http://kees.tweakblogs.net/blog/801/silverlight-ek-streams-onder-linux.html)

Building the whole Mono stack....  #-o

Must be a script somewhere....:lolflag:

Possibly. I'd wait for packages if I were you. - which will happen once there's a newer tarball.

---

### Post by gnomeuser on 2008-11-09
> **Shin_Gouki2501 said:**
> why NOT to go with mono:
[http://flyingfrogblog.blogspot.com/2008/10/mono-20.htm](http://flyingfrogblog.blogspot.com/2008/10/mono-20.htm)

You mean [http://flyingfrogblog.blogspot.com/2008_10_01_archive.html](http://flyingfrogblog.blogspot.com/2008_10_01_archive.html)

Aside that I see no sign in that post fundamentally opposing Mono, it is one developers opinion that the current Mono garbage collector is insufficient. Not backed by data, just opinion. Now that might be valid, the GC in Mono works but it is not a superior design - something the Mono community is working on. The roadmap[1] says that a compacting GC will become available with Mono 2.8 (set for Sept. 2008), this would fix that one issue. Note it had no legal objection nor fundamentally a technical one. So what if we are slower in some cases compared to the Microsoft reference implementation, there are others where we are significantly faster (just look at Mono.Simd something MS.NET does not currently include). So why avoid an open implementation of .NET again, it brings great technology to Linux and.. surprise it's Free Software so if you find a bug report it, don't whine in a blog, we can fix it remember (and surprise.. we are).

[1] [http://www.mono-project.com/Roadmap](http://www.mono-project.com/Roadmap)

---

### Post by plun on 2008-11-09
> **directhex said:**
> Ah. There's the confusion. It's *Moonlight* 0.8, which has support for *Silverlight* 1.0. Like I said, 0.8 isn't complete enough for me to bother uploading packages.

The tarballs aren't that bad. SVN is a royal pain though, as you need to do a lot of things which are free with tarballs.

Possibly. I'd wait for packages if I were you. - which will happen once there's a newer tarball.

Yup maybe...1.0 should be branched also now according to Moonlights mailinglist.


Code must be tested...RSVGSHARP fixed but now the dirty codecs challenge.
libavcodec/ffmpeg mess...

Testing...

---

### Post by Shin_Gouki2501 on 2008-11-09
yes sorry i missed the "l"
and not backed up? ho i remember reading about nice windows forms error which was GC related i try to digg it out.

---

### Post by gnomeuser on 2008-11-09
> **Shin_Gouki2501 said:**
> yes sorry i missed the "l"
and not backed up? ho i remember reading about nice windows forms error which was GC related i try to digg it out.

You remember? Some of us use this all day without problem, every day. Your article had no data to back it up, you digging up a second article will not change that. My ultimate question again would be why whine about a bug on a blog when we have bugzilla.. fixing problems is possible (this is free software we do it every day), hell in the time between the occurance of your nebulous memory as well as the date of the article, the bug might just be fixed.

It is a bug, all software has bugs.. Mono is software, thus Mono has bugs nobody is denying that.. get over it. What matters is what we do about bugs, I favor addressing them with bug reports and fixes, you appear to favor using them as ammo in some kind of ill guided, misinformed quest for vengance.

---

### Post by Shin_Gouki2501 on 2008-11-10
there is a nice post in this forums which explains the greatest?! problem of linux: stop preaching / mention.
Do you see me preaching?

I concur with the 2nd comment of the post. The title of this thread was "my hopes for Mono+ Jaunty" so i said my opinion that <<i>> couldn't understand why mono is so popular on the desktop since i spent some time with java on the desktop and that was fine for me. I hope you understand now better.

---

### Post by bash on 2008-11-10
Changing topic: Has anyone managed to get the Moonlight Firefox plugin to work with websites using Silverlight. Installed it, but on all the silverlight websites I tried, I got the message to go download the Silverlight plugin.

---

### Post by gnomeuser on 2008-11-10
> **bash said:**
> Changing topic: Has anyone managed to get the Moonlight Firefox plugin to work with websites using Silverlight. Installed it, but on all the silverlight websites I tried, I got the message to go download the Silverlight plugin.

I have had it working but not a recent version, I am waiting for 1.0 I figure it wasn't worth compiling SVN now.

(happy to change the subject from Mono bashing)

---

### Post by plun on 2008-11-10
> **bash said:**
> Changing topic: Has anyone managed to get the Moonlight Firefox plugin to work with websites using Silverlight. Installed it, but on all the silverlight websites I tried, I got the message to go download the Silverlight plugin.

Nope... its worthless, IMHO

I have installed latest Mono 2.0 environment without "limitations" and are trying to build this "pig"... FF3 dependencies seems to be difficult...:)

---

### Post by directhex on 2008-11-10
> **bash said:**
> Changing topic: Has anyone managed to get the Moonlight Firefox plugin to work with websites using Silverlight. Installed it, but on all the silverlight websites I tried, I got the message to go download the Silverlight plugin.

Unfortunately, many sites have made the move from Silverlight 1.0 (which Moonlight 1.0 supports) to Silverlight 2.0 (which Moon doesn't yet support in any meaningful way).

This is the problem with young projects like Moonlight - I have no doubt that 2.0 support will appear quickly though, since a big chunk of the important code is already available as part of Mono, and Microsoft released a second chunk as Free Software to help development of Silverlight clones

---

### Post by plun on 2008-11-10
Well, what a mess...  Microsoft, Microsoft, Microsoft..

[[img]http://ubuntu-pics.de/thumb/5477/test1_3GEck3.jpg[/img]](http://ubuntu-pics.de/bild/5477/test1_3GEck3.jpg)

[[img]http://ubuntu-pics.de/thumb/5476/ms_7raUr8.jpg[/img]](http://ubuntu-pics.de/bild/5476/ms_7raUr8.jpg)

[[img]http://ubuntu-pics.de/thumb/5478/codecs_2Xs6Eu.jpg[/img]](http://ubuntu-pics.de/bild/5478/codecs_2Xs6Eu.jpg)

Latest SVN compiled....

Maybe the codecs are there somewhere  :confused:  


And no eulas, please...   FF3 was enough...!

EDIT its there

[[img]http://ubuntu-pics.de/thumb/5479/eula_q8TD2I.jpg[/img]](http://ubuntu-pics.de/bild/5479/eula_q8TD2I.jpg)

---

### Post by directhex on 2008-11-10
> **plun said:**
> Well, what a mess...  Microsoft, Microsoft, Microsoft..

[[img]http://ubuntu-pics.de/thumb/5477/test1_3GEck3.jpg[/img]](http://ubuntu-pics.de/bild/5477/test1_3GEck3.jpg)

[[img]http://ubuntu-pics.de/thumb/5476/ms_7raUr8.jpg[/img]](http://ubuntu-pics.de/bild/5476/ms_7raUr8.jpg)

[[img]http://ubuntu-pics.de/thumb/5478/codecs_2Xs6Eu.jpg[/img]](http://ubuntu-pics.de/bild/5478/codecs_2Xs6Eu.jpg)

Latest SVN compiled....

Maybe the codecs are there somewhere  :confused:  

They're not ready yet. Compile against ffmpeg if you want media support.

> And no eulas, please...   FF3 was enough...!

EDIT its there

[[img]http://ubuntu-pics.de/thumb/5479/eula_q8TD2I.jpg[/img]](http://ubuntu-pics.de/bild/5479/eula_q8TD2I.jpg)

Unfortunately, as they're distributing Microsoft's codecs, it's up to Microsoft if they want people to agree to a EULA

To repeat though, the packages in Ubuntu will not use the Microsoft Media Pack, and therefore will not require a EULA

---

### Post by plun on 2008-11-10
> **directhex said:**
> 
To repeat though, the packages in Ubuntu will not use the Microsoft Media Pack, and therefore will not require a EULA

Well, I am sitting and laughing after this "battle"....:lolflag:

Its useless without codecs... what should we watch  :confused:


[http://www.mono-project.com/MoonlightBeta1](http://www.mono-project.com/MoonlightBeta1)


"Fully working sites"....  :lolflag:

---

### Post by directhex on 2008-11-10
> **plun said:**
> Its useless without codecs... what should we watch  :confused:

Sorry, which part of "ffmpeg" isn't clear?

Please read the Codecs section of [http://wiki.debian.org/Teams/DebianMonoGroup/Moonlight](http://wiki.debian.org/Teams/DebianMonoGroup/Moonlight)

---

### Post by plun on 2008-11-10
> **directhex said:**
> Sorry, which part of "ffmpeg" isn't clear?

Please read the Codecs section of [http://wiki.debian.org/Teams/DebianMonoGroup/Moonlight](http://wiki.debian.org/Teams/DebianMonoGroup/Moonlight)

OK....  ffmpeg without restrictions broke... I live in a software patent free nation.

Going to read the Debian URL.  Thanks !!

../../src/.libs/libmoon.so: undefined reference to `lame_set_out_samplerate'
../../src/.libs/libmoon.so: undefined reference to `lame_set_disable_reservoir'
../../src/.libs/libmoon.so: undefined reference to `lame_encode_buffer'
../../src/.libs/libmoon.so: undefined reference to `NeAACDecDecode'
../../src/.libs/libmoon.so: undefined reference to `theora_encode_comment'
../../src/.libs/libmoon.so: undefined reference to `theora_info_clear'
../../src/.libs/libmoon.so: undefined reference to `x264_param_default'
../../src/.libs/libmoon.so: undefined reference to `lame_set_brate'
../../src/.libs/libmoon.so: undefined reference to `x264_encoder_headers'
../../src/.libs/libmoon.so: undefined reference to `faacEncGetCurrentConfiguration'
../../src/.libs/libmoon.so: undefined reference to `lame_set_bWriteVbrTag'
../../src/.libs/libmoon.so: undefined reference to `theora_info_init'
../../src/.libs/libmoon.so: undefined reference to `NeAACDecSetConfiguration'
../../src/.libs/libmoon.so: undefined reference to `NeAACDecOpen'
../../src/.libs/libmoon.so: undefined reference to `faacEncSetConfiguration'
../../src/.libs/libmoon.so: undefined reference to `NeAACDecInit2'
../../src/.libs/libmoon.so: undefined reference to `NeAACDecInit'
../../src/.libs/libmoon.so: undefined reference to `faacEncGetDecoderSpecificInfo'
../../src/.libs/libmoon.so: undefined reference to `x264_encoder_open'
../../src/.libs/libmoon.so: undefined reference to `lame_close'
../../src/.libs/libmoon.so: undefined reference to `x264_encoder_encode'
../../src/.libs/libmoon.so: undefined reference to `lame_set_VBR'
../../src/.libs/libmoon.so: undefined reference to `lame_get_framesize'
../../src/.libs/libmoon.so: undefined reference to `faacEncOpen'
../../src/.libs/libmoon.so: undefined reference to `lame_init'
../../src/.libs/libmoon.so: undefined reference to `lame_set_quality'
../../src/.libs/libmoon.so: undefined reference to `x264_nal_encode'
../../src/.libs/libmoon.so: undefined reference to `lame_set_in_samplerate'
../../src/.libs/libmoon.so: undefined reference to `theora_comment_clear'
../../src/.libs/libmoon.so: undefined reference to `theora_encode_header'
../../src/.libs/libmoon.so: undefined reference to `lame_set_mode'
../../src/.libs/libmoon.so: undefined reference to `lame_set_num_channels'
../../src/.libs/libmoon.so: undefined reference to `faacEncEncode'
../../src/.libs/libmoon.so: undefined reference to `NeAACDecGetErrorMessage'
../../src/.libs/libmoon.so: undefined reference to `theora_encode_packetout'
../../src/.libs/libmoon.so: undefined reference to `x264_encoder_close'
../../src/.libs/libmoon.so: undefined reference to `faacEncClose'
../../src/.libs/libmoon.so: undefined reference to `theora_encode_tables'
../../src/.libs/libmoon.so: undefined reference to `lame_encode_flush'
../../src/.libs/libmoon.so: undefined reference to `lame_encode_buffer_interleaved'
../../src/.libs/libmoon.so: undefined reference to `NeAACDecClose'
../../src/.libs/libmoon.so: undefined reference to `theora_clear'
../../src/.libs/libmoon.so: undefined reference to `lame_init_params'
../../src/.libs/libmoon.so: undefined reference to `NeAACDecGetCurrentConfiguration'
../../src/.libs/libmoon.so: undefined reference to `theora_comment_init'
../../src/.libs/libmoon.so: undefined reference to `theora_encode_init'
../../src/.libs/libmoon.so: undefined reference to `theora_encode_YUVin'
../../src/.libs/libmoon.so: undefined reference to `lame_set_VBR_q'
collect2: ld returned 1 exit status
make[3]: *** [mopen1] Error 1
make[3]: Leaving directory `/home/plun/moon/tools/mopen'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/plun/moon/tools'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/plun/moon'
make: *** [all] Error 2


No code box.... sorry... The Ubuntu-Mozilla team also builds...

---

### Post by plun on 2008-11-10
Followup... recompiled ffmpeg with a plain configure first  :)

```
plun@plun:~/moon$ firefox
windowless mode
DownloaderRequest: http://mschnlnine.wmod.llnwd.net/a1809/d1/ch9/5/8/0/2/4/4/Visual-Studio-2010-and-NET-Framework-40-Week.wmv
ASF warning: No validation implemented for ASF_METADATA_LIBRARY.
DownloaderRequest: http://mschnlnine.wmod.llnwd.net/a1809/d1/ch9/5/8/0/2/4/4/Visual-Studio-2010-and-NET-Framework-40-Week.wmv
[wmv3 @ 0xaa747c0]Extra data: 8 bits left, value: 0
AudioPlayer: Using PulseAudio.

```

But I clicked on the Window... VLCs Mozilla plugin also needs a "click".

Testing standard ffmpeg..

---

### Post by plun on 2008-11-12
Followup,  SVN ver 1.9 up and running.

Mono and MCS installed for full Silverlight 2.0 support

```
Moonlight configuration
=======================

  General configuration:
	Using cairo: embedded
	Test Harness: no (reason: failed to find ImageMagick++ >= 6.2.8)
	Performance Suite: yes 

  Media Support: 
	FFmpeg: yes 
	Alsa: yes 
	Pulseaudio: yes 

  Silverlight Support:
	Silverlight 1.0: yes (bug compatibility: yes)
	[B]Silverlight 2.0 (managed code): yes 
          Browser plugin assemblies: yes 
          Desktop application assemblies: yes 
[/B]
  Browser Support:
	Firefox: yes
          Plugin Installer (.xpi): no
          Gecko 1.8 (Firefox 2): no (reason: missing FF2 development packages)
          Gecko 1.9 (Firefox 3): yes 

```

>  Done. The new package has been installed and saved to

 /home/plun/moon/moon_1.9-1_i386.deb

 You can remove it from your system anytime using: 

      dpkg -r moon




- Codecs install works....


- This site is still broken, a good reference for main stream users.

[http://www.nbcolympics.com/video/](http://www.nbcolympics.com/video/)


A lot works....

---

### Post by directhex on 2008-11-12
> **plun said:**
> A lot works....

Impressive given 2.0 support only had developers start working on it about a week ago

---

### Post by plun on 2008-11-12
> **directhex said:**
> Impressive given 2.0 support only had developers start working on it about a week ago

Well, I have no clues about what I watching....

Just took MS showcase which Moonlights beta page points to..

[http://silverlight.net/showcase/](http://silverlight.net/showcase/)


"Real" HD content seems to be protected....


The quality is really good... seems "lighter" then Adobe HD streams.

---

### Post by plun on 2008-11-23
Mono 2 SVN...

[https://lists.ubuntu.com/archives/jaunty-changes/2008-November/001014.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-November/001014.html)

I rebuilt my Moonlight plugin yesterday and the Eula and codecs are gone..:)

FF3.1 crashes sometimes so I hope we can start testing this as soon as possible  !

Not wait and wait...:)

---

### Post by Gina on 2008-11-23
It's my view that if we're going to have something in a release it should be included for testing at the earliest opportunity.  It goes without saying - the more testing the better.

---

### Post by plun on 2008-11-23
> **Gina said:**
> It's my view that if we're going to have something in a release it should be included for testing at the earliest opportunity.  It goes without saying - the more testing the better.

Yup... both Hardy and Intrepid has ended up in a mess around alpha 6/betas.

There are a handful important functions for a mainstream user and lets test those as early as possible....  SVN/GIT snapshots is a good way.

But... only this "handful"...  FF3.1, OO-3, PulseAudio, the kernel, maybe PackageKit.

Maybe also Ubuntu can contribute to upstream...:guitar:


:)

---

### Post by directhex on 2008-11-23
First things first - fixing Mono 2.0.1 FTBFS on armel

---

### Post by plun on 2008-12-02
> **directhex said:**
> First things first - fixing Mono 2.0.1 FTBFS on armel

Ok  ;)

Moonlight Beta 1 is out.   FF3.1 also for us....

[http://tirania.org/blog/archive/2008/Dec-02-1.html](http://tirania.org/blog/archive/2008/Dec-02-1.html)

> **We have released the first beta of Moonlight 1.0.**

This release supports the Microsoft Media Pack for playing back video and audio files. These are the same video and audio decoders that Microsoft uses in Silverlight 2.0.

Check our Moonlight roadmap for details on upcoming versions.

You can try some of the sites tests that we used to test Moonlight.

Here are some Silverlight 1.0 materials:

    * How To Videos on Silverlight 1.0
    * Essential Silverlight Training.
    * Silverlight 1.0 Unleashed. This is my favorite Silverlight 1.0 book, one of the books that we used to get some of the Moonlight team members up to speed. 

You can also read the Silvelright's XAML vocabulary description and its XAML Foundation Specification.

**Posted by Miguel de Icaza on 02 Dec 2008**

---

### Post by directhex on 2008-12-03
> **plun said:**
> Ok  ;)

Moonlight Beta 1 is out.   FF3.1 also for us....

[http://tirania.org/blog/archive/2008/Dec-02-1.html](http://tirania.org/blog/archive/2008/Dec-02-1.html)

```
jms@destiny:~$ head -1 Projects/pkg-mono/moon/trunk/debian/changelog 
moon (1.0~beta1-1) UNRELEASED; urgency=low
```

---

### Post by neighborlee on 2008-12-21
> **ShirishAg75 said:**
> I am not at all thrilled about mono for it could at any point have any patent issues or stuff like that. In fact the sore point has been that GNOME has been using quite a bit of Mono lately which is not good atleast from my perspective.

Tomboy is directly mentioned here:
[http://library.gnome.org/misc/release-notes/2.22/](http://library.gnome.org/misc/release-notes/2.22/) , though I dont see it in 2.24 release notes, though again it shows up in 2.26 goals it seems ( gnomes page ).

[http://www.groklaw.net/articlebasic.php?story=20080528133529454](http://www.groklaw.net/articlebasic.php?story=20080528133529454) 

"Moonlight is usable for anyone on any distribution of Linux (redhat, ubuntu, etc.) -- it is not limited just to Novell as Mono is."

Now, so we see the mono is only useable for novel customers , severely debunking any claims that mono is 'ok' for linux, and we all know what debian and fedora think of moonlight , which isnt much:

[http://lists.debian.org/debian-devel/2008/10/msg00102.html](http://lists.debian.org/debian-devel/2008/10/msg00102.html) < from debian-devel list.

[http://groups.google.com/group/tiraniaorg-blog-comments/browse_thread/thread/2a07b8b50038d8c8/d582162af2d63d57](http://groups.google.com/group/tiraniaorg-blog-comments/browse_thread/thread/2a07b8b50038d8c8/d582162af2d63d57) :

> use a distro that is not mainstream or just doesn't have a deal with
> the daemon.. err Microsoft.. like Novell has.. Will I have to suffer
> the shadow of Microsoft patents  over Silverlight when using or
> developing Moonlight?

 " Not as long as you get/download Moonlight from Novell which will include
patent
coverage.

Miguel "

[http://fedoraproject.org/wiki/ForbiddenItems#Moonlight](http://fedoraproject.org/wiki/ForbiddenItems#Moonlight) < Fedora's Stance.

Okay there you have it, I report you decide.

These things are far too important, for everyone not to be made clearly aware of, and I suggest that debian and fedora taking such stances on these things should throw a huge red flag .

cheers
nl

---

### Post by gnomeuser on 2008-12-21
> **neighborlee said:**
> 
[http://fedoraproject.org/wiki/ForbiddenItems#Moonlight](http://fedoraproject.org/wiki/ForbiddenItems#Moonlight) < Fedora's Stance.


As I was involved in the talks that let to this being issued let me tell you that despite repeated requests Red Hat Legal has not published any patents which they believe are infringed upon. Upon requesting such a list the answer was "It's to much work, and to expensive, to conduct a proper review - we are going to assume it's encumbered".

So Red Hat Legal has basically just evaluated in favor of not doing a proper patent review. Why is this important to note, because the Mono project' stance on patents is the following. If one is found it will be worked around, if that is not possible they will fight it to the best of their ability (and OIN has the full backlog of all Novell patents to do this with, basically this would be Mutually Asssured Destruction which nobody is interested in). 

So Red Hat not not being helpful in actually pointing out what they believe the problem is so it can be fixed following the officially stated policy by the upstream. 

Remembering that for ages Fedora had Mono on the forbidden list as well, which changed overnight when Red Hat joined the OIN. Red Hat has all days had a strange relationship with Mono, trying to hamper it's progress where ever they could without giving much reason aside the usual "we believe it might be covered by patents but we are certainly not going to back that accusation up with facts".

This one issue, despite my great love for Fedora and admiration for Red Hat and what they have done for the Free Software community in general has left me with an exceedingly bad taste in my mouth.

---

### Post by directhex on 2008-12-21
> **gnomeuser said:**
> Red Hat has all days had a strange relationship with Mono, trying to hamper it's progress where ever they could

Red Hat have business reasons to push Java instead. Similar reasons to why Sun doesn't allow contributions to OOo which add functionality currently found only in their closed StarOffice.

---

### Post by gnomeuser on 2008-12-21
> **directhex said:**
> Red Hat have business reasons to push Java instead. Similar reasons to why Sun doesn't allow contributions to OOo which add functionality currently found only in their closed StarOffice.

I was to polite to say that but yes, they have invested heavily in Java which makes it even less appealing to them to conduct (and let's not forget pay for) a patent review of Moonlight.

---

### Post by directhex on 2008-12-21
> **gnomeuser said:**
> I was to polite to say that

Call a spade a shovel.

Oh, and for those reading along at home, no, I won't respond directly to anything from the poster a couple of posts ago, but suffice it to say some of his claims are categorically false.

---

### Post by RAOF on 2008-12-22
> **neighborlee said:**
> ...
[http://fedoraproject.org/wiki/ForbiddenItems#Moonlight](http://fedoraproject.org/wiki/ForbiddenItems#Moonlight) < Fedora's Stance.
...

Man, that sucks.

What about Flash patents? :)  They actively promote swfdec and gnash there.

---

