---
title: "p7zip not installed by default anymore"
date: 2008-12-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Bou on 2008-12-22
Hi,

Until recently, p7zip was installed by default. However, I noticed that a recent ubuntu-desktop update dropped its dependency and it appears as "auto-unistallable" now. I'm just curious, do you guys know the reason?

---

### Post by Gina on 2008-12-22
I had to manually install that in order to use UNetbootin.   I wondered why the need to install it wasn't mentioned in the UNetbootin thread and Wiki.  Now I know.

---

### Post by plun on 2008-12-22
:confused::confused::confused:

[https://bugs.launchpad.net/ubuntu/+source/p7zip/+bug/282294](https://bugs.launchpad.net/ubuntu/+source/p7zip/+bug/282294)

EDIT

> file-roller (2.24.1-1ubuntu2) jaunty; urgency=low

  * Switch back from p7zip to unzip+zip; p7zip only provides zip support
    in the p7zip-full variant, which is significantly larger than
    unzip+zip combined, so we don't want to pull this onto the CDs (or
    into main). LP: #282294.

---

### Post by Starks on 2008-12-22
It's a miracle that Fedora has 20MB of spare disk space to play with. Ubuntu devs need to scrounge for every last kilobyte.

---

### Post by andrewabc on 2008-12-23
I am using intrepid and was disappointed that by default I could not decompress 7-zip files. I had to install some other stuff.

7-zip for windows is only 1mb installer. Is there a reason why so difficult to have something like that by default on ubuntu? 7-zip seems to handle most files.

---

### Post by amano on 2008-12-23
A bad decision in my eyes. With p7z-full installed by default Ubuntu would support all important plugins out of the box which is a good thing.

And file-roller keeps to depend more and more on p7zip. Thus it is getting crippled by this decision.

Probably we should file a bug to reintroduce the dependency. 

It is not that p7zip was a bloated monster.

---

### Post by Nullack on 2008-12-23
Yeah Ive reinstalled p7zip too.

AFAIK, the default setup wont handle RARs??

---

### Post by durand on 2008-12-24
I'm not exactly sure what the reason for this decision is but it feels pretty stupid to me. Reinstallled.

---

### Post by Gina on 2008-12-24
Well... they were a couple of megs above the 700MB CD limit on the Desktop CD version - I'm guessing that that was an easy way to get it down to 700MB :lolflag:

---

### Post by gjoellee on 2008-12-24
> **andrewabc said:**
> I am using intrepid and was disappointed that by default I could not decompress 7-zip files. I had to install some other stuff.

7-zip for windows is only 1mb installer. Is there a reason why so difficult to have something like that by default on ubuntu? 7-zip seems to handle most files.

It may by a 1mb installer, but the when installed everything usually takes more space. Ex: I installed a little program, the downloaded was about 7mb, the installed size was about 40mb

---

### Post by Arathorn on 2008-12-25
Yes but isn't the problem getting it on the install disc? The little space p7zip takes shouldn't be a problem, and at least when I install Kubuntu there's so much programs I'd never use, that I don't understand why they didn't cut any of those.

---

### Post by Gina on 2008-12-25
> **Arathorn said:**
> Yes but isn't the problem getting it on the install disc? The little space p7zip takes shouldn't be a problem, and at least when I install Kubuntu there's so much programs I'd never use, that I don't understand why they didn't cut any of those.I have thought much the same thing but on reflection, just because we don't use certain apps does not mean others don't and the developers have to decide priorities and take some pretty ruthless decisions in order to get the install down to the 700MB that will fit on a CD.

---

### Post by amano on 2008-12-25
Who is known to file convincing bug reports? This thing does require one for sure.

With every release file-roller depends more on p7zip thus installing it by default is a decision for the future...

And it is not a bloated monster. Compare it to mono and the likes. What about ekiga that nobody uses? do we really need tomboy installed by default?

What about gnome removing bonobo, gnome-vfs, libgnome, libgnomeUI, libglade dependencies? maybe those will make room for p7zip on the cd.

But opening a 7z file or a zip file (with all file-roller features available) is a core functionality in my eyes that should not be demoted that easily.

---

### Post by durand on 2008-12-26
> **amano said:**
> 
What about gnome removing bonobo, gnome-vfs, libgnome, libgnomeUI, libglade dependencies? maybe those will make room for p7zip on the cd.


We can't remove them as they are needed for a functional gnome desktop...

---

### Post by amano on 2008-12-26
Currently yes. But they are steering towards being deprecated soon. ;) All being part of "Project Ridley".

---

### Post by durand on 2008-12-26
Yeah, I got confused with gvfs. But libglade? Surely thats important.

---

### Post by amano on 2008-12-26
If I am not mistaken libglade is supposed to be replaced by GtkBuilder. And Glade supports GTKbuilder from now on directly. 

Glade =! libglade

See: [http://www.micahcarrick.com/05-30-2008/gtk-builder-libglade-faq.html](http://www.micahcarrick.com/05-30-2008/gtk-builder-libglade-faq.html)

You can see that most (if not all) GNOME puzzle pieces drop off support for those deprecated libraries if you read [http://news.gnome.org](http://news.gnome.org) and above all [http://blogs.gnome.org/commitdigest/](http://blogs.gnome.org/commitdigest/)

In short: eel is now part of nautilus itself and the libglade functionality was moved to gtk+. Both libraries are of no use now as separate entities. gnome-vfs was replaced by gvfs and should be demotable soon. bonobo and libgnomeUI is ancient cruft as well.

---

### Post by gnomeuser on 2008-12-26
> **Starks said:**
> It's a miracle that Fedora has 20MB of spare disk space to play with. Ubuntu devs need to scrounge for every last kilobyte.

One of those miracles involve not having OpenOffice on there either.

I could understand all these tools for a liveUSB deployment where you have presistent storage but on a live cd why do I have Evolution (never mind that I and pretty much everyone have switched to webbased clients such as gmail).

---

### Post by Gina on 2008-12-26
I use Evolution - I like it.

---

### Post by Starks on 2009-01-28
Is this bug fixed? File-roller still hates 7zip files.

At any rate, has a bug report been filed yet or complained on the mailing lists?

---

### Post by bruce89 on 2009-01-28
> **amano said:**
> What about gnome removing bonobo, gnome-vfs, libgnome, libgnomeUI, libglade dependencies? maybe those will make room for p7zip on the cd.

They're not there yet. Personally I'd add Firefox and its dependencies to that list, to be replaced by WebKit and Epiphany (Next GNOME release hopefully). Yelp and Devhelp will depend on WebKit, so a decision will have to be made.

---

### Post by aldeby on 2009-01-28
What a stupid decision!

7z is the best free compression format available and that program also has support for a WIDE range of compression and decompression methods. If there was available a GUI for linux I would have ABANDONED file-roller ages ago.

Is there anyone anymore that use the obsolete zip format? I don't think so. RAR and 7z are far superior, alongwith bzip2

---

### Post by bruce89 on 2009-01-28
> **aldeby said:**
> 7z is the best free compression format available and that program also has support for a WIDE range of compression and decompression methods. If there was available a GUI for linux I would have ABANDONED file-roller ages ago.

That's the problem with it. UNIX tools are supposed to do one thing, and do it well (gzip and tar being separate tools); not that 7z has anything to do with UNIX.

There is lzma, which is just the compression method that 7z uses, but without the container format. You can use it along with tar to get something 7z like, but UNIXy.

> **aldeby said:**
> Is there anyone anymore that use the obsolete zip format? I don't think so. RAR and 7z are far superior, alongwith bzip2

Superior in which sense? Is it worth making an archive a few bytes smaller if you rely on a non-free tool (rar), or slow down compression hugely (7z).

---

### Post by cl333r on 2009-01-29
> **Starks said:**
> It's a miracle that Fedora has 20MB of spare disk space to play with. Ubuntu devs need to scrounge for every last kilobyte.

Ironically they do find space for Mono and to keep Tomboy-like toy apps installed by default while disregarding the C equivalents of the same apps that startup and run a lot faster and use like 1000% less memory (no need to host a VM). It is really bizarre to listen the(ir) biased responses like "we can't fear patents forever", it's not about patents, it's about C apps being better products, having faster startup, execution and using (much!) less memory.

When I do a "sudo apt-get remove --purge libmono0 mono-common" I get rid of 60MB (tomboy also removed), how do you like that?

---

### Post by kurros on 2009-01-29
> **cl333r said:**
> Ironically they do find space for Mono and to keep Tomboy-like toy apps installed by default while disregarding the C equivalents of the same apps that startup and run a lot faster and use like 1000% less memory (no need to host a VM). It is really bizarre to listen the(ir) biased responses like "we can't fear patents forever", it's not about patents, it's about C apps being better products, having faster startup, execution and using (much!) less memory.

When I do a "sudo apt-get remove --purge libmono0 mono-common" I get rid of 60MB (tomboy also removed), how do you like that?

Maybe this thread could be funneled into ideas to have file-roller offer to install what it needs for a particular archive like our gstreamer applications do with decoders.

Instead of coming up with mythical C apps that are "better products" than tomboy or f-spot to put on the install CD.

---

### Post by andrewabc on 2009-01-29
> **kurros said:**
> Maybe this thread could be funneled into ideas to have file-roller offer to install what it needs for a particular archive like our gstreamer applications do with decoders.

Instead of coming up with mythical C apps that are "better products" than tomboy or f-spot to put on the install CD.

Agree.

Instead of having user open a .7z and the program saying unable to open archive (or whatever the error is), tell the user what to install to open it.

I don't think basic user knows to go into synaptic, search for 7-zip, then decide which 7-zip to install (there is full 7-zip and a smaller version available).

---

### Post by bruce89 on 2009-01-29
> **andrewabc said:**
> Instead of having user open a .7z and the program saying unable to open archive (or whatever the error is), tell the user what to install to open it.

While I don't encourage the use of the 7z format, nautilus-packagekit would be very helpful.

---

### Post by cl333r on 2009-01-30
> **kurros said:**
> Maybe this thread could be funneled into ideas to have file-roller offer to install what it needs for a particular archive like our gstreamer applications do with decoders.

Instead of coming up with mythical C apps that are "better products" than tomboy or f-spot to put on the install CD.

"mythical" for those who don't know about it and didn't search.
This post might enlighten you about mythical apps:
[http://support.zenwalk.org/viewtopic.php?f=3&t=2732](http://support.zenwalk.org/viewtopic.php?f=3&t=2732)

---

### Post by Eclipse. on 2009-01-30
> **cl333r said:**
> Ironically they do find space for Mono and to keep Tomboy-like toy apps installed by default while disregarding the C equivalents of the same apps that startup and run a lot faster and use like 1000% less memory (no need to host a VM). It is really bizarre to listen the(ir) biased responses like "we can't fear patents forever", it's not about patents, it's about C apps being better products, having faster startup, execution and using (much!) less memory.

When I do a "sudo apt-get remove --purge libmono0 mono-common" I get rid of 60MB (tomboy also removed), how do you like that?

Please taee your mono/Novell hating opinions else where.Its an important part of Ubuntu and isnt going anywhere, not in the near future anyway.

Sick of all this ant-mono crap just because of an agreement with another company.

---

### Post by bruce89 on 2009-01-30
Actually, was p7zip ever installed by default? If so, what package was it that depended/recommended it?

---

### Post by directhex on 2009-01-30
> **cl333r said:**
> Ironically they do find space for Mono and to keep Tomboy-like toy apps installed by default while disregarding the C equivalents of the same apps that startup and run a lot faster and use like 1000% less memory (no need to host a VM). It is really bizarre to listen the(ir) biased responses like "we can't fear patents forever", it's not about patents, it's about C apps being better products, having faster startup, execution and using (much!) less memory.

When I do a "sudo apt-get remove --purge libmono0 mono-common" I get rid of 60MB (tomboy also removed), how do you like that?

Know your enemy.

It's clear from talking about things like VMs that you don't.

---

### Post by plun on 2009-01-30
> **directhex said:**
> Know your enemy.


Yeah ;)

MS and Novell are pure evil....;)

Read that somewhere....  :redface:

---

### Post by directhex on 2009-01-30
> **plun said:**
> Yeah ;)

MS and Novell are pure evil....;)

Read that somewhere....  :redface:

Spray-painted on the side of a train?

---

### Post by bruce89 on 2009-01-30
> **cl333r said:**
> It is really bizarre to listen the(ir) biased responses like "we can't fear patents forever", it's not about patents, it's about C apps being better products, having faster startup, execution and using (much!) less memory.

Try convincing them to stop writing Python programs. In other words, ain't going to happen.

I don't think it'd take much effort to port C# programs to Vala actually, but it'd probably be a waste of time.

---

### Post by directhex on 2009-01-30
> **bruce89 said:**
> Try convincing them to stop writing Python programs. In other words, ain't going to happen.

I don't think it'd take much effort to port C# programs to Vala actually, but it'd probably be a waste of time.

The "write in C" crowd are oblivious to the very reason Mono was started in the first place, and to the reasons people write in languages like Python.

Ignorance is not, however, a crime

---

### Post by Starks on 2009-01-31
Mono just screams **BULKY!** to me.

---

### Post by nystire on 2009-01-31
> **Starks said:**
> Mono just screams **BULKY!** to me.

Why? It's an extremely elegant solution to cross-platform applications, which means that Windows users can move to Ubuntu (hopefully) without giving up their favourite applications.

---

### Post by Starks on 2009-01-31
> **nystire said:**
> Why? It's an extremely elegant solution to cross-platform applications, which means that Windows users can move to Ubuntu (hopefully) without giving up their favourite applications.

I know that. However, my distrust for anything that channels .NET is quite strong.

---

### Post by directhex on 2009-01-31
> **Starks said:**
> Mono just screams **BULKY!** to me.

Possibly to you, but not to anyone else. Mono is tiny, all things considered, thanks to the hard work of the pkg-mono team.

Firstly, on Debian/Ubuntu, there is no "mono" - there is a minimal installation (mono-runtime) and any libraries used by an application (e.g. libmono-cairo2.0-cil). Usually these libraries are fairly small, and the minimal install is currently 7 meg on disk.

Secondly, Mono apps share most of their dependencies - much like any other framework - and those shared dependencies are not actually all that large. For example, installing F-Spot on its own pulls in 53.2 MiB on disk, and installing Tomboy pulls in 46.9 MiB - but installing both together, due to shared dependencies, pulls in 68.1 MiB. Add, say, Graphmonkey on top, and as a simple app, Graphmonkey only pulls in an extra 100 KiB onto your disk. Compare the shared dependencies of these heavyweight Gnome# apps with a simple Java app - Freeguide (TV guide app) needs 115 MiB on disk, JEdit needs 121 MiB. Hell, compare Monodevelop (73.7 MiB) with Eclipse (265 MiB). Are Mono apps heavier than others, e.g. Python? In disk space terms, impossible to say - as Python is already installed, its dependencies are "hidden". In other terms (e.g. RAM use) then Python apps are far more bloated, and Java apps even worse

Oh, and the numbers for Mono apps will DECREASE by ~20-40% by the time Jaunty releases thanks to more work by packagers

---

### Post by marmuta on 2009-01-31
Let's see...

> It's clear from talking about things like VMs that you don't.

Ignorance is not, however, a crime
Ad hominem arguments - check

> The "write in C" crowd are oblivious to the very reason Mono was started in the first place, ...

> Mono just screams BULKY! to me.
Possibly to you, but not to anyone else.
Ridiculing and marginalizing other opinions - check

> Mono is tiny, all things considered...
Usually these libraries are fairly small, and the minimal install is currently 7 meg on disk.
Exaggeration and unrealistic assumptions - check

> > ...it's about C apps being better products, having 
> faster startup, execution and using (much!) less memory.
Compare the shared dependencies of these heavyweight Gnome# apps with a simple Java app 
Changing topic to reach more favorable conclusions - check

Makes me wonder why mono can't stand on its own, but has to be sold like that...

---

### Post by directhex on 2009-01-31
> **marmuta said:**
> Let's see...

Ad hominem arguments - check

Using terms like "ad hominem" to hide the fact that you're wrong - Mono does not and has never used a VM - check

> Ridiculing and marginalizing other opinions - check

Jumping on any attempt to correct falsehoods which don't suit your worldview - check

> Exaggeration and unrealistic assumptions - check

Exaggeration? I note you declined to use the actual measured numbers here, and just call it "exaggeration". I wonder why.

Demagogy? Check.

> Changing topic to reach more favorable conclusions - check

Makes me wonder why mono can't stand on its own, but has to be sold like that...[/QUOTE]

It has stood on its own for years. Some people just love to make up things about it to attack it, usually because ZOMG TEH MICRO$HAFTZ!

You want to argue for C apps? Fine. But, again, you're evidently ignorant of any Mono exists in the first place. Been hanging around with the Boycott Novell idiots?

---

### Post by marmuta on 2009-01-31
I'm on neither side of the fence. Just wondering why mono would need pushy salesman tactics. No offense, I'm genuinely curious.

---

### Post by directhex on 2009-01-31
> **marmuta said:**
> I'm on neither side of the fence. Just wondering why mono would need pushy salesman tactics. No offense, I'm genuinely curious.

Correcting falsehoods counts as being a pushy salesman?

---

### Post by marmuta on 2009-01-31
Arguing that seems pointless. I've made my point and leave it at that.

---

### Post by bruce89 on 2009-01-31
> **directhex said:**
> The "write in C" crowd are oblivious to the very reason Mono was started in the first place, and to the reasons people write in languages like Python.

Ignorance is not, however, a crime

I'm not ignorant thank you, I was just pointing out that saying Mono is wrong is much the same as saying Python is.

Anyway, this is completely off topic.

---

