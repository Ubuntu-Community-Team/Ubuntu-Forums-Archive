---
title: "OpenOffice.org 3.1.0"
date: 2009-05-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by calc on 2009-05-06
I have just uploaded OpenOffice.org 3.1.0~rc2 to the PPA for hardy/intrepid/jaunty and directly to the archive for karmic. The 'final' OOo 3.1.0 debs should be available in a week or so. Note that rc2 actually ended up being 'final' in that official OpenOffice.org just renamed their packaging so it won't really change much other than more Go-OO.org ooo-build fixes when the 'final' debs are uploaded.

Have fun! :)

---

### Post by Nullack on 2009-05-06
thanks

---

### Post by BGFG on 2009-05-06
Great stuff, thanks a lot :)

---

### Post by andrewabc on 2009-05-06
For those who are not using karmic and need to manually input repository to get newest version, is there a simple howto?

I've previously used:
[How to Install OpenOffice.org 3.0 on Ubuntu 8.10](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

Is it the same PPA and steps to use for Jaunty/intrepid users to get 3.1 now?

I'm on jaunty with 3.0.1 and want 3.1.

also for those wondering on release dates for OOo:
[http://wiki.services.openoffice.org/wiki/OOoRelease31](http://wiki.services.openoffice.org/wiki/OOoRelease31)

If 3.1.1 is magically released before September 1st (say beta freeze?), I presume it would make it into karmic final? Of course they are always late delivering, so probably won't happen.

---

### Post by calc on 2009-05-06
> **andrewabc said:**
> For those who are not using karmic and need to manually input repository to get newest version, is there a simple howto?

I've previously used:
[How to Install OpenOffice.org 3.0 on Ubuntu 8.10](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

Is it the same PPA and steps to use for Jaunty/intrepid users to get 3.1 now?

Yes, OOo 3.0.1 is no longer in the PPA and has been replaced with OOo 3.1.0.

> **andrewabc said:**
> I'm on jaunty with 3.0.1 and want 3.1.

also for those wondering on release dates for OOo:
[http://wiki.services.openoffice.org/wiki/OOoRelease31](http://wiki.services.openoffice.org/wiki/OOoRelease31)

If 3.1.1 is magically released before September 1st (say beta freeze?), I presume it would make it into karmic final? Of course they are always late delivering, so probably won't happen.

[http://wiki.services.openoffice.org/wiki/OOoRelease311](http://wiki.services.openoffice.org/wiki/OOoRelease311)

That page says that it is scheduled for the beginning of August so it should be released by the time of Feature Freeze (Aug 27) unless they are somehow extremely delayed. So that should be the version that will be in the Ubuntu 9.10 (Karmic) release.

---

### Post by andrewabc on 2009-05-06
> **calc said:**
> Yes, OOo 3.0.1 is no longer in the PPA and has been replaced with OOo 3.1.0.

I followed the links instructions. I go into synaptic and mark all upgrades since update manager says partial upgrade required (new kernel?)
It wants to remove:
openoffice.org-calc
openoffice.org-draw
openoffice.org-impress
openoffice.org-math
openoffice.org-writer

And the only OOo stuff I notice it will install is:
openoffice.org-common
openoffice.org-emailmerge
openoffice.org-style-human

Why aren't calc/draw/impress/math/writer being installed again?

See attached images. I have proposed repository enabled (since I have no sound in Jaunty, and would like an update for that soon).
Also, I'm using 64 bit, so I'm guessing the PPA knows which version to get?

---

### Post by Kow on 2009-05-06
> **andrewabc said:**
> I followed the links instructions. I go into synaptic and mark all upgrades since update manager says partial upgrade required (new kernel?)
It wants to remove:
openoffice.org-calc
openoffice.org-draw
openoffice.org-impress
openoffice.org-math
openoffice.org-writer

And the only OOo stuff I notice it will install is:
openoffice.org-common
openoffice.org-emailmerge
openoffice.org-style-human

Why aren't calc/draw/impress/math/writer being installed again?

See attached images. I have proposed repository enabled (since I have no sound in Jaunty, and would like an update for that soon).
Also, I'm using 64 bit, so I'm guessing the PPA knows which version to get?

OO is a gigantic package. Probably hasn't finished building yet.

---

### Post by Jingo on 2009-05-07
Seems the  openoffice.org-l10n failed building.
[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

Should I wait until its fixed ?
Whats the impact?

---

### Post by calc on 2009-05-07
Hold off on upgrading until it shows a full upgrade. The openoffice.org-l10n source package failed to build due to a minor bug, which I believe I have fixed in the bzr repo. Also, there is currently a bug in the karmic linux-libc-dev which is causing many packages to fail to build for karmic. So once it is fixed and I am able to verify there are no other issues I will be uploading the OOo 1:3.1.0-1ubuntu1 debs to both karmic and the ppa.

Sorry for the delay...

---

### Post by six-geek on 2009-05-07
Cheers for updating the final version on ppa.

---

### Post by int on 2009-05-07
Many thanks calc

---

### Post by meborc on 2009-05-07
let us know when the PPA is working for jaunty :)

---

### Post by Meson on 2009-05-07
Is 3.1 ever going to be in the official Jaunty repositories or will we have to wait until Karmic?

---

### Post by mister_pink on 2009-05-07
> **Meson said:**
> Is 3.1 ever going to be in the official Jaunty repositories or will we have to wait until Karmic?

Unlikely - maybe backports if you're lucky. Standard policy is only bug fixes and security patches go to the repos after a release.

---

### Post by xebian on 2009-05-07
The debs direct from OO work just fine.  No waiting.:guitar:

---

### Post by Meson on 2009-05-07
> **xebian said:**
> The debs direct from OO work just fine.  No waiting.:guitar:

Uninstall the repository version first or do they install cleanly over the existing installation.


Right now I like the PPA the best because hopefully it will stay up to date. But I'll have to wait because right now it says "Failed to detect distribution" and the update manager only offers to uninstall OO.o =(

---

### Post by xebian on 2009-05-07
> **Meson said:**
> Uninstall the repository version first or do they install cleanly over the existing installation.


Right now I like the PPA the best because hopefully it will stay up to date. But I'll have to wait because right now it says "Failed to detect distribution" and the update manager only offers to uninstall OO.o =(

dpkg is smart enough but you can uninstall first if you want.

OO has online update tool.

---

### Post by smacfarl on 2009-05-07
So if download the debs from OO they will automatically uninstall OO 3.0 after 3.1 is installed as some type of post install trigger? And further we can use OO 3.1 itself to do updates on itself without synaptic?

What are the implications with my future Ubuntu upgrade path?

I am running 9.04.

---

### Post by jblackhall on 2009-05-08
> **smacfarl said:**
> So if download the debs from OO they will automatically uninstall OO 3.0 after 3.1 is installed as some type of post install trigger? And further we can use OO 3.1 itself to do updates on itself without synaptic?

What are the implications with my future Ubuntu upgrade path?

I am running 9.04.

If you can wait a day or two for the PPA to get sorted out, it's probably for the better.  The PPA version is a backport from the development version of Ubuntu Karmic Koala.  It's based on go-oo.org, which is a specially modified version of OO.o containing linux-specific improvements.  If you download the version from the OO.o website, you won't get to take advantage of those.

---

### Post by xebian on 2009-05-08
> **jblackhall said:**
> If you can wait a day or two for the PPA to get sorted out, it's probably for the better.  The PPA version is a backport from the development version of Ubuntu Karmic Koala.  It's based on go-oo.org, which is a specially modified version of OO.o containing linux-specific improvements.  If you download the version from the OO.o website, you won't get to take advantage of those.

Would you mind listing specifically what is better in Go-OO vs. the original OO?  Don't they get contributed back upstream? Thanks.

---

### Post by GAJAN on 2009-05-08
Thanks for this new release! So far, works excellent.
However, it seems to me that the help files are not included in this repository. Would it be possible to add these too?

Thanks,

Gerbert

---

### Post by mister_pink on 2009-05-08
> **xebian said:**
> Would you mind listing specifically what is better in Go-OO vs. the original OO?  Don't they get contributed back upstream? Thanks.
They usually do eventually, but it often takes ages. Sun are notoriously difficult for putting in patches from other people. I don't know what's different at the moment, but I know for example that go-OO had the new office 2007 format support before the official openoffice.

---

### Post by jblackhall on 2009-05-08
> **xebian said:**
> Would you mind listing specifically what is better in Go-OO vs. the original OO?  Don't they get contributed back upstream? Thanks.

[http://go-oo.org/discover/](http://go-oo.org/discover/)

No, they don't all get contributed back upstream.  Upstream  OO.o does accept a few of their patches I think, but most of the enhancements do not get accepted.  The entire purpose of Go-oo (from my understanding) is to maintain these enhancements (and add more) so that they can be added on to the upstream version and distributed.

---

### Post by Starks on 2009-05-08
3.1 still suffers from embarrassing bulleted outline indent inconsistencies and nobody cares about the bugs that have been filed against it.

---

### Post by uatschitchun on 2009-05-09
What about packages like:
openoffice.org-kab
openoffice.org-kde
?

---

### Post by kulight on 2009-05-09
> **andrewabc said:**
> I followed the links instructions. I go into synaptic and mark all upgrades since update manager says partial upgrade required (new kernel?)
It wants to remove:
openoffice.org-calc
openoffice.org-draw
openoffice.org-impress
openoffice.org-math
openoffice.org-writer

And the only OOo stuff I notice it will install is:
openoffice.org-common
openoffice.org-emailmerge
openoffice.org-style-human


im still having that on jaunty i didnt understand if it have been fixed or not...

---

### Post by Aearenda on 2009-05-09
PPA users, keep an eye on the build status at [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa) before trying the upgrade.

---

### Post by wjp.reg on 2009-05-09
Will OO for ubuntu EVER "feature" address datasource wizard options for something other than evolution, or dBase, i.e. Thunderbird/Mozilla?  Like many, I prefer Thunderbird over Evolution for various reasons, and need access to my address book(s).  As a result, I have had to download, update and install OO from the OO.org site since forever.

Can the maintainers address this shortcoming? :confused:

---

### Post by Jingo on 2009-05-09
> **Starks said:**
> 3.1 still suffers from embarrassing bulleted outline indent inconsistencies and nobody cares about the bugs that have been filed against it.
Any links for the bugreports?

I think the bulleting regression almost renders ooo 3.x useless. 2.x series worked well.

---

### Post by vnieto on 2009-05-09
I try to install from launchpad repositories and have this:
"vnieto@vnieto-laptop:~$ sudo apt-get dist-upgrade

Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Calculando la actualización... Listo
Los siguientes paquetes se ELIMINARÁN:
  language-support-en language-support-es language-support-translations-en
  language-support-translations-es openoffice.org-help-en-gb
  openoffice.org-help-es openoffice.org-l10n-en-gb openoffice.org-l10n-en-za
  openoffice.org-l10n-es thunderbird-locale-en-gb thunderbird-locale-es-ar
  thunderbird-locale-es-es
Se instalarán los siguientes paquetes NUEVOS:
  linux-restricted-modules-2.6.28-12-generic
Se actualizarán los siguientes paquetes:
  linux-restricted-modules-generic openoffice.org-base-core
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-gnome openoffice.org-gtk
  openoffice.org-impress openoffice.org-math openoffice.org-style-human
  openoffice.org-writer python-uno
13 actualizados, 1 se instalarán, 12 para eliminar y 0 no actualizados.
Necesito descargar 65,7MB de archivos.
Se liberarán 62,3MB después de esta operación.
"
is sugest me remove the locales packages.

Can I install the spanish version?

---

### Post by Starks on 2009-05-09
> **Jingo said:**
> Any links for the bugreports?

I think the bulleting regression almost renders ooo 3.x useless. 2.x series worked well.
With pleasure.

[http://qa.openoffice.org/issues/show_bug.cgi?id=98748](http://qa.openoffice.org/issues/show_bug.cgi?id=98748)

This bug needs votes and comments.

---

### Post by calc on 2009-05-10
> **wjp.reg said:**
> Will OO for ubuntu EVER "feature" address datasource wizard options for something other than evolution, or dBase, i.e. Thunderbird/Mozilla?  Like many, I prefer Thunderbird over Evolution for various reasons, and need access to my address book(s).  As a result, I have had to download, update and install OO from the OO.org site since forever.

Can the maintainers address this shortcoming? :confused:

This is because that OOo feature only compiles against an ancient version of mozilla. So when we build OOo for Ubuntu that feature doesn't work. I don't know if they ever intend to actually fix that problem though.

---

### Post by wjp.reg on 2009-05-10
> **calc said:**
> This is because that OOo feature only compiles against an ancient version of mozilla. So when we build OOo for Ubuntu that feature doesn't work. I don't know if they ever intend to actually fix that problem though.

That's unfortunate ..

---

### Post by zoro on 2009-05-11
Interested in hearing about when I can just upgrade to the latest version. It really is taking a while for the new debs to appear in the repos.

---

### Post by davideotape on 2009-05-11
> **zoro said:**
> Interested in hearing about when I can just upgrade to the latest version. It really is taking a while for the new debs to appear in the repos.

I upgraded this morning the usual way through synaptic. I presume you're on 9.10?

---

### Post by six-geek on 2009-05-11
Indeed.

I'm writing my diploma thesis and for that is the AA feature a really benefit. So I use actually the RC2 version from the PPA.

Somewhere in the web I read that the RC2 version is very comparable to the final version. But unfortunately I have to work without the german language menu (but this is not a big deal) and without the kde implementation. OOo looks a bit strange without kde implementation. But it's fine. I won't complain about a free office suit that works so great.:)

---

### Post by zoro on 2009-05-11
> **davideotape said:**
> I upgraded this morning the usual way through synaptic. I presume you're on 9.10?

Of course not. I obviously didn't read the forum name when I found this thread via google.

Sorry for bothering you :)
*saunters back to look for some Jaunty OO3.1 lovin'*

---

### Post by davideotape on 2009-05-11
> **six-geek said:**
> Somewhere in the web I read that the RC2 version is very comparable to the final version.

[http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml) - See the editors note that's in green

---

### Post by six-geek on 2009-05-11
> **davideotape said:**
> [http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml) - See the editors note that's in green

All right. Sounds good.
Anyway, big thanks to Chris Cheney.

---

### Post by dgermann on 2009-05-12
Hi--

Not sure I am posting in the best thread for this, so if not, could you point me to the best one? Thanks.

Running several 8.04 machines in a production environment. About two days ago I got the notice that 3.1.0 was ready for download via update manager. I installed, and ended up with two issues (I tried just tonight on another machine and still have these issues):

1. Tools > Customize > Keyboard was all blown to bits. For instance, destructive backspace would not backspace; F3 would give no auto text; and all my special key assignments were gone.

(As an aside, I had saved all those key assignments to a file using Tools > Customize > Keyboard > Save; however, using Load on the same page will not load up that file. How do you load these keyboard settings?)

2. There is no Help (F1) at all. It says the help file is not installed. Synaptic says it is installed. I'm presuming it just needs to be told where it is....

Thanks for whatever help you can give me.

---

### Post by taavikko on 2009-05-13
@dgerman, so you have enabled some third party repositories,
that provides latest OOo.

generally bad idea when running production machines.

now for the proposition fix.

-Disable that 3rd party repo via software-source or manually editing sources.list

-purge the openoffice, either synaptic or manually via apt(CLI)

-Force the version, via synaptic or manually
```
sudo aptitude install openoffice.org-core=2.4.1-1ubuntu2.1
```

That should be latest in hardy's repos.
Hope this helps.

---

### Post by zika on 2009-05-13
is it me or is it the launchpad but I do get offered in synaptic, after adding ppa's, only a sort of  partial upgrade with all essential packages threatened to be removed and  some general to be installed ...

calc, draw, impress, math, writer to be removed...

common, emailmerge, java-common, ttf-opensymbol, uno-libs3, ure to be  installed ...

I'll wait ... for what ... ?

---

### Post by dgermann on 2009-05-13
taavikko--

Thank you for helping me!

(This morning I see I am in the Karmic Koala Testing and Discussion forum, so I *am* in the wrong spot! Sorry to bother everybody.)

You are right that this is generally a bad idea to enable other repositories. In this production environment it is necessary for me to have OOo 3, since 2.4 does not provide file locking.

So going back to 2.4 is not an option for me.

I will poke around for some other threads that deal directly with this. Thanks!

---

### Post by xhilyn on 2009-05-13
I have done the upgrade via synaptic but now none of my database's work.

I'm running Jaunty 9.04.
If I select a database it opens base but then shows an error saying there is no connection to the data source.

"no SDBC driver was found for the given URL"

Pressing More gives two errors and one information tab

error 1
The connection to the data source "Books" could not be established.

error 2
SQL Status: HY000

The connection to the external data source could not be established. No SDBC driver was found for the given URL.

info tab
A connection for the following URL was requested: sdbc:embedded:hsqldb

I've tried all my Databases and none of them work.

Any Ideas?

If not how can I go back to version 3.0 as I need my databases.

Thanks

xhi

---

### Post by meborc on 2009-05-13
weren't there big changes in databases in 3.1 ... i remember hearing that it may lead to losing backward compatibility 

something about location of information now being stored all in one location... sorry, can't find the source right now

to get the old one back, remove openoffice completely... remove the PPA repository... refresh the listing and reinstall openoffice

---

### Post by taavikko on 2009-05-13
> **dgermann said:**
> taavikko--

Thank you for helping me!

(This morning I see I am in the Karmic Koala Testing and Discussion forum, so I *am* in the wrong spot! Sorry to bother everybody.)

You are right that this is generally a bad idea to enable other repositories. In this production environment it is necessary for me to have OOo 3, since 2.4 does not provide file locking.

So going back to 2.4 is not an option for me.

I will poke around for some other threads that deal directly with this. Thanks!

Try this to get OOo-3 in hardy 
[http://ubuntu-snippets.blogspot.com/2008/10/ppa-for-openofficeorg-30.html](http://ubuntu-snippets.blogspot.com/2008/10/ppa-for-openofficeorg-30.html)

I have no idea of ppa's to use when concerning OOo & hardy, since I don't use either one...

---

### Post by xhilyn on 2009-05-13
> **meborc said:**
> weren't there big changes in databases in 3.1 ... i remember hearing that it may lead to losing backward compatibility 

something about location of information now being stored all in one location... sorry, can't find the source right now

to get the old one back, remove openoffice completely... remove the PPA repository... refresh the listing and reinstall openoffice


Thanks for the quick answer but if that is true then that information really should be somewhere that can be found easily as a warning to users of the Base app. I have found no such info anywhere on the OOo site or anywhere else.

I'm also having a dependancy problem trying to reinstall OOo 3.0 now.

Thanks anyway

xhi

---

### Post by dgermann on 2009-05-13
taavikko--

Thanks for helping me!

Yup, those are the repos I am using.

The latest offering via update manager does not show a help-en-us in the list, so I think I may wait it out a couple days and see if one shows up.

Any ideas on how to load the OOo keyboard shortcut file?

Thank you very much.

---

### Post by xhilyn on 2009-05-13
Hi all

I'm now stuck in a dependency loop.

I uninstalled openoffice.org 3.1 and deleted to repositories and updated the sources but now When I try to install Openoffice.org it says it can't because it needs openoffice.org-writer2latex.

But when I try to install openoffice.org-writer2latex it tells me it cant because it needs openoffice.org core and round and round I go.

So it seems that I have broken something.

Does it mean that I will have to reinstall the entire system.

I'm afraid this is all beyond my understanding so I will need some help to clear up the mess.

Thanks in advance of any help anyone can offer.

xhi

---

### Post by lean on 2009-05-13
> **xhilyn said:**
> Hi all

I'm now stuck in a dependency loop.

I uninstalled openoffice.org 3.1 and deleted to repositories and updated the sources but now When I try to install Openoffice.org it says it can't because it needs openoffice.org-writer2latex.


You need to do an apt-get clean to get rid of the caches deb files.

---

### Post by jblackhall on 2009-05-13
For those of you with problems upgrading to 3.1.0 from the PPA, there's a problem with part of it building correctly, see [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa) (the Build Status column).  If you attempt to update/upgrade when things aren't built correctly, those packages show up as missing, and they will be removed when you attempt to upgrade.  Your best bet if you want a clean upgrade is to wait until you see all green checkmarks on that page for your release.  To all of you who knew that already, carry on :)

---

### Post by xhilyn on 2009-05-14
> **lean said:**
> You need to do an apt-get clean to get rid of the caches deb files.

Thanks for the reply.

I tried what you suggested but it made no difference to my dependency loop.

Thanks anyway

xhi

---

### Post by CSimpson on 2009-05-14
Xhilyn, I had much the same problem when trying to downgrade back to the version in the Jaunty repos.  It turned out, when I ran a search for "openoffice.org" in synaptic, that there were several packages still purporting to be version 3.1 packages, and all I had to do was remove those and then everything was back to normal.  I can't remember what those packages were, mind, so you'll just have to do some hunting (sorry).

Once I'd removed these rogue packages, everything worked just fine, though I do remember that for some reason I had to install the package openoffice.org-gtk myself, as this was not pulled in by the "openoffice.org" meta-package.

**EDIT:**

Alright, I had some time, so I went back through the process of upgrading and downgrading again, to replicate the problem, and go through solving that problem again.  I typed up what I was doing in gedit, as I did it.  This is what I came up with:

> upgraded to the OO.o Scribblers' 3.1
    some packages were removed due to l10n issues
        took note of these, you might have a similar set missing for any of your locales- they are (for me):
            language-support-translations-en
            language-support-translations-ja
            openoffice.org-help-en-gb
            openoffice.org-help-ja
            openoffice.org-l10n-en-gb
            openoffice.org-l10n-en-za
            openoffice.org-l10n-ja
            openoffice.org-writer2latex
            thunderbird-locale-en-gb
            thunderbird-locale-ja
> disabled OO.o Scribblers' repo
> uninstalled OO.o 3.1 by meta packages "openoffice.org" and "openoffice.org-core"
> tried to reinstall OO.o from jaunty repos (default) using meta package "openoffice.org"
    encountered terrible loop of dependancy death!
> searched for "openoffice.org" in synaptic
    the following packages are still claiming to be version 3.1
        openoffice.org-common
        openoffice.org-style-human
        openoffice.org-style-tango
        ure
        uno-libs3
> removed those packages listed above.
> installing OO.o 3.0 via the "openoffice.org" meta package now works!  But...
> the following packages are not installed:
        openoffice.org-gtk
        openoffice.org-style-tango
        language-support-translations-en (which also pulls in openoffice.org-help-en-gb, openoffice.org-help-en-us, openoffice.org-l10n-en-gb, openoffice.org-l10n-en-za and thunderbird-locale-en-gb)
        language-support-translations-ja (which also pulls in openoffice.org-help-ja, openoffice.org-l10n-ja and thunderbird-locale-ja)
> so I installed them myself!

And that's the entire process I went through in upgrading, finding it not quite satisfactory, and downgrading again.  The difference for you will depend on whatever locales you have installed, and I guess whether or not you have openoffice.org-style-tango installed, but other than that I imagine your experience is the same as mine.

---

### Post by xebian on 2009-05-14
If you are in Karmic, there is no need to get it from the ppa because it's already in Karmic repos. Last time I checked, there is no dependency on write2latex

```

Package: openoffice.org         
Priority: optional              
Section: editors                
Installed-Size: 44              
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian OpenOffice Team <debian-openoffice@lists.debian.org>
Architecture: amd64                                                             
Version: 1:3.1.0-1ubuntu1                                                       
Replaces: openoffice.org-debian-files, openoffice.org2 (<< 1:3.1.0-1ubuntu1)    
Provides: openoffice.org2                                                       
Depends: openoffice.org-core (= 1:3.1.0-1ubuntu1), openoffice.org-writer, openoffice.org-calc, openoffice.org-impress, openoffice.org-draw, openoffice.org-math, openoffice.org-base, openoffice.org-report-builder-bin, ttf-dejavu, openoffice.org-officebean, openoffice.org-filter-mobiledev, openoffice.org-java-common (>> 2.2.0-4)
Recommends: openoffice.org-filter-binfilter, ttf-liberation | msttcorefonts
Suggests: hunspell-dictionary, myspell-dictionary, openoffice.org-help-3.1, openoffice.org-l10n-3.1, menu, unixodbc, cups-bsd, libsane, openoffice.org-hyphenation, openoffice.org2-thesaurus, libxrender1, libgl1, openoffice.org-gnome, iceweasel | firefox | icedove | thunderbird | iceape-browser | mozilla-browser, default-jre | java-gcj-compat | openjdk-6-jre | sun-java5-jre | sun-java6-jre, openclipart-openoffice.org, pstoedit, graphicsmagick-imagemagick-compat | imagemagick, libpaper-utils, gstreamer0.10-plugins-base, gstreamer0.10-plugins-good, gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-bad, gstreamer0.10-ffmpeg
Conflicts: openoffice.org-java-common (<< 1:3.0.0), openoffice.org2 (<< 1:3.1.0-1ubuntu1)
Filename: pool/main/o/openoffice.org/openoffice.org_3.1.0-1ubuntu1_amd64.deb


```

---

### Post by zika on 2009-05-14
@CSimpson: it might have helped You if You've used the Origin button in Synaptic ... :)
very detailed review of the process, thank You.

---

### Post by myhelipad on 2009-05-15
Hi there..,

A few days ago I just upgrade OpenOffice.org 3.0.1 to OpenOffice.org 3.1 on my Ubuntu 9.04.

I'm having problem with help file is not there, any solution to install its back.

Regards.

---

### Post by bhaverkamp on 2009-05-15
I did this upgrade and now I am left with no OO at all. When I try to reload from jaunty repository I get conflicts with the writer2latex package which aborts the whole upgrade. Anybody have any ideas to to revert back to 3.0. I should just stop dicking around with these packages and leave them alone.

---

### Post by bhaverkamp on 2009-05-15
Your directions fixed my issues to. Thanks for the post.

---

### Post by Gina on 2009-05-15
I did a fresh install using the Alpha 1 distro and I now have OOo 3.1.0 working.  I had messed up my previous Karmic trying to get OOo working.

---

### Post by myhelipad on 2009-05-15
> **Gina said:**
> I did a fresh install using the Alpha 1 distro and I now have OOo 3.1.0 working.  I had messed up my previous Karmic trying to get OOo working.

Hi Gina;

Can you explain a bit how do you do the installation, is the same procedure installation in Ubuntu 9.04 Jaunty Jackalope. I've done it but no help file install, after update language support I lost all my OO 3.1 on Applications Menu. Now I plan to reinstall back.

Regards

---

### Post by Gina on 2009-05-15
> **myhelipad said:**
> Hi Gina;

Can you explain a bit how do you do the installation, is the same procedure installation in Ubuntu 9.04 Jaunty Jackalope. I've done it but no help file install, after update language support I lost all my OO 3.1 on Applications Menu. Now I plan to reinstall back.

RegardsYes, I did it the same way as other installations.  Downloaded the Alpha 1 ISO (the Alternate AMD64 version, in fact) put it on USB memory stick using the **USB Startup Disk Creator** (System > Admin menu) and installed from that.  I used the same partition as before, deleting the old Karmic system but keeping the same /home partition.

---

### Post by jppr on 2009-05-15
i just only update system and now is ooo 3.1.0 upgradet.

---

### Post by DougieFresh4U on 2009-05-15
Not sure if I have correct version (newest) as when 3.0 was let out in early Jaunty or was it Intrepid,the start up showed 2.xx but when you opened up OO and went to 'Help' and 'About OO' it showed the correct version (newest) Therefore now, when starting up OO I am seeing '3.0' but 'About OO' is showing '3.1'

---

### Post by davideotape on 2009-05-15
> **DougieFresh4U said:**
> Not sure if I have correct version (newest) as when 3.0 was let out in early Jaunty or was it Intrepid,the start up showed 2.xx but when you opened up OO and went to 'Help' and 'About OO' it showed the correct version (newest) Therefore now, when starting up OO I am seeing '3.0' but 'About OO' is showing '3.1'

I think you've probbably found a bug there :D. I'm also getting the same behaviour.

---

### Post by DougieFresh4U on 2009-05-15
> **davideotape said:**
> I think you've probbably found a bug there :D. I'm also getting the same behaviour.
As I had said, It started that way in other releases, don't know why but it sorted out eventually
Thanks for reply  :)

---

### Post by davideotape on 2009-05-15
> **davideotape said:**
> I think you've probbably found a bug there :D. I'm also getting the same behaviour.

On the subject of bugs, report a problem doesn't seem to be working in openoffice either. Anyone else getting this problem?

---

### Post by Gina on 2009-05-15
> **davideotape said:**
> I think you've probbably found a bug there :D. I'm also getting the same behaviour.Me too.

---

### Post by davideotape on 2009-05-15
> **Gina said:**
> Me too.

Maybe we should start a fan club!

---

### Post by ZYV on 2009-05-17
It would be very nice if Chris could elaborate on when the l10n packages are expected to be fixed. The last upload is from 12 May and is broken.  I'm waiting to update to 3.1.0 as the other users in this thread, but this issue stops me from doing so. ):P

---

### Post by xhilyn on 2009-05-17
[QUOTE=CSimpson;7278008]Xhilyn, I had much the same problem when trying to downgrade back to the version in the Jaunty repos.  It turned out, when I ran a search for "openoffice.org" in synaptic, that there were several packages still purporting to be version 3.1 packages, and all I had to do was remove those and then everything was back to normal.  I can't remember what those packages were, mind, so you'll just have to do some hunting (sorry).

Once I'd removed these rogue packages, everything worked just fine, though I do remember that for some reason I had to install the package openoffice.org-gtk myself, as this was not pulled in by the "openoffice.org" meta-package./QUOTE]

Thanks very much for your answer but I gave up in the end and just reinstalled the whole system as I decided that it was getting too much of a mess.

It also seems that the build is broken anyway so I will wait for a while before I try again.

So thanks again for your trouble.

xhi

---

### Post by michael37 on 2009-05-20
Glad I found this thread.  I didn't upgrade after getting a nasty suggestion to uninstall all English support.  

```

mike@mike:~$ sudo apt-get install openoffice.org
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  openoffice.org-base openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-evolution
  openoffice.org-filter-binfilter openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-math openoffice.org-officebean openoffice.org-style-human openoffice.org-writer
  python-uno uno-libs3 ure
Suggested packages:
  cups-bsd gstreamer0.10-ffmpeg hunspell-dictionary menu openclipart-openoffice.org
  openoffice.org-help-3.1 openoffice.org-l10n-3.1 pstoedit libmyodbc odbc-postgresql
  libsqliteodbc tdsodbc mdbtools libmysql-java libpg-java libjtds-java openoffice.org-gcj
  openoffice.org-report-builder openoffice.org-style-crystal openoffice.org-style-hicontrast
  openoffice.org-style-industrial openoffice.org-style-tango xfonts-mathml cli-uno-bridge
Recommended packages:
  evolution openoffice.org-emailmerge
The following packages will be REMOVED:
  language-support-en language-support-translations-en mozilla-firefox-locale-en-gb
  openoffice.org-help-en-gb openoffice.org-l10n-en-gb openoffice.org-l10n-en-za
  openoffice.org-writer2latex
The following packages will be upgraded:
  openoffice.org openoffice.org-base openoffice.org-base-core openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution
  openoffice.org-filter-binfilter openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-math openoffice.org-officebean openoffice.org-style-human openoffice.org-writer
  python-uno uno-libs3 ure
19 upgraded, 0 newly installed, 7 to remove and 1 not upgraded.
Need to get 76.9MB of archives.
After this operation, 25.9MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

**n** is the correct answer... as of May 20th.

---

### Post by fab.head on 2009-05-20
> **calc said:**
> Hold off on upgrading until it shows a full upgrade. The openoffice.org-l10n source package failed to build due to a minor bug, which I believe I have fixed in the bzr repo. Also, there is currently a bug in the karmic linux-libc-dev which is causing many packages to fail to build for karmic. So once it is fixed and I am able to verify there are no other issues I will be uploading the OOo 1:3.1.0-1ubuntu1 debs to both karmic and the ppa.

Sorry for the delay...

hi calc, when do you think you will be able to publish the openoffice.org-l10n package for Jaunty?

[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

here it says that the openoffice.org-l10n packages for Jaunty, Intrepid and Hardy failed to build

thanks :)

---

### Post by andrewabc on 2009-05-20
I hope it is updated soon. I spent many hours the other day working on a 150k cell spreadsheet and the amount of bugs in 3.0.1 is unbearable. I could even make calc repeatedly crash just by copy/pasting some cells that contained formulas and then double clicking on any other cell. Thank goodness the crash recovery works so good.

I tried googling, but I couldn't find an answer.

Let's say I copy a cell or a bunch of cells. I then paste them to wherever (doesn't matter ignore the pasted cells, what matters is there is now copied cells still highlighted ready to be copied again.)
If I double click on any cell (whether it has formula/text or is blank), then press enter, it pastes the highlighted/copied cells there. Very annoying when I just want to see the formula for a specific cell.


Easy example: In cell A1 put
=1+1
Then ctrl+c C1 (any other cell even blank one). Then double click on cell that contains =1+1 and press enter without typing anything. It will input the location of A1. It then looks like
=1+1A1
So then I have to delete the newly input cell location.
Try this again but select and copy many cells, and then double click A1 and press enter. It copies/pastes all those copied cells.

How do I disable this? It is making calc difficult to use. There don't appear to be any options in ->tools->options->calc that would resolve this.

---

### Post by Orion2000za on 2009-05-21
I would and will avoid this upgrade until all is sorted out and recommend the same to others. I had hell to get back to Ooo 3 and existing help-files and functionality. Lucky for me I use AptonCD now and then to backup my machine. 

While I appreciate the work done by the Scribblers I do not understand why you choose to release a build that is incomplete this time? 

Back on 3.0 and helpfiles, KDE integration, language files etc. work as expected.

---

### Post by myhelipad on 2009-05-21
I think better just hold upgrading is the good idea, i'll take same decision.:popcorn:

---

### Post by fab.head on 2009-05-22
I'm trying to understand what are the real advantages of using the OOo 3.1 version from the PPA over the version which can be downloaded directly from openoffice.org (compatibility? better DE integration? look?).

Is there anyone who can explain this to me?

Many thanks :)

---

### Post by Aearenda on 2009-05-22
I'm no expert on this, but as I understand it the integration is better (eg, systray quickstarter) plus all the extras listed at [http://www.go-oo.org/](http://www.go-oo.org/) (which is not yet at 3.1).

---

### Post by dgermann on 2009-05-23
fab.head--

For me the advantage has been that update manager handles all the updates.

When I have downloaded directly from the OOo site, then when it is time to upgrade, I get a nag green download arrow and have to go download it and go through the steps to install the whole thing all over. Plus, I have to make sure that I have removed all the prior versions of OOo first, which I did not do once, and now Gnome Search for Files does not know how to open OOo docs.

---

### Post by ZYV on 2009-05-23
> **dgermann said:**
> For me the advantage has been that update manager handles all the updates.

Bah, now that the l10n packages are broken for a few weeks and we don't have any ETA on when this will be fixed (nor the reasons for the breakage), many people already unknowingly screwed up their installs and had to revert to the official deb's... :(

---

### Post by marijus on 2009-05-23
> **ZYV said:**
> Bah, now that the l10n packages are broken for a few weeks and we don't have any ETA on when this will be fixed (nor the reasons for the breakage), many people already unknowingly screwed up their installs and had to revert to the official deb's... :(

well... what do you expect from alpha-1?

---

### Post by ZYV on 2009-05-23
> **marijus said:**
> well... what do you expect from alpha-1?

Don't get me wrong, I am very grateful to everybody involved for providing the native builds of the latest and greatest OO for Ubuntu. But this has exactly **nothing** to do with Alpha-1. This PPA serves Hardy, Intrepid and Jaunty users as well. And the broken l10n package broke the updates (and even messed up the system for those unfortunates who were not attentive enough while applying updates) for all of those three. Now they don't have the opportunity to use 3.x series via this PPA at all and the only option is to downgrade to stock 2.4.x.

---

### Post by michael37 on 2009-05-23
> **ZYV said:**
> Don't get me wrong, I am very grateful to everybody involved for providing the native builds of the latest and greatest OO for Ubuntu. But this has exactly **nothing** to do with Alpha-1. This PPA serves Hardy, Intrepid and Jaunty users as well. And the broken l10n package broke the updates (and even messed up the system for those unfortunates who were not attentive enough while applying updates) for all of those three. Now they don't have the opportunity to use 3.x series via this PPA at all and the only option is to downgrade to stock 2.4.x.

I am puzzled too.  I have one computer which I was lucky to updated to 3.0.1 from PPA.  Another one is stuck with thoroughly outdated 2.4.  I wish PPA still provided 3.0.1 packages.

---

### Post by fab.head on 2009-05-24
Aearenda and dgermann, many thanks :)

---

### Post by Meson on 2009-05-27
I know everyone is extremely anxious about this. I just happened to check [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa) and saw that there is some activity with the Jaunty version =)

Thought I'd let you all know.

---

### Post by JohnJackson on 2009-05-27
> **Meson said:**
> I know everyone is extremely anxious about this. I just happened to check [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa) and saw that there is some activity with the Jaunty version =)

Thought I'd let you all know.

Very considerate of you. It seems to work.

---

### Post by ZYV on 2009-05-28
Wow, Jaunty packages are built, Intrepid's are building and how knows... maybe the next day we're going to see the updates packages for Hardy :D

---

### Post by jblackhall on 2009-05-28
Thank you Chris!

---

### Post by HotShotDJ on 2009-05-28
> **Meson said:**
> I know everyone is extremely anxious about this. I just happened to check [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa) and saw that there is some activity with the Jaunty version =)

Thought I'd let you all know.

> **JohnJackson said:**
> Very considerate of you. It seems to work.
I thought I'd add that I just upgraded my standard Jaunty installation of OpenOffice to the ppa version successfully.  I don't see any obvious bugs.  However, the splash screen still reports it as 3.0 and the "About OpenOffice" dialog also says 3.0 in the title, but does report it as "OpenOffice.org 3.1.0 OOO310m11 (Build:9399). (see attached screenshot)

---

### Post by davideotape on 2009-05-28
> **HotShotDJ said:**
> I thought I'd add that I just upgraded my standard Jaunty installation of OpenOffice to the ppa version successfully.  I don't see any obvious bugs.  However, the splash screen still reports it as 3.0 and the "About OpenOffice" dialog also says 3.0 in the title, but does report it as "OpenOffice.org 3.1.0 OOO310m11 (Build:9399). (see attached screenshot)

There was a thread or discussion about the splash screen somewhere in these forums. We decided to start a "My openoffice splash screen is incorrect" fan club. Interested in joining? :P

---

### Post by HotShotDJ on 2009-05-28
> **davideotape said:**
> There was a thread or discussion about the splash screen somewhere in these forums. We decided to start a "My openoffice splash screen is incorrect" fan club. Interested in joining? :PThank you for your kind invitation -- perhaps I'll seek out the thread to which you referred, although I'm not all that concerned about it... as long as I have the version of OOo that I want, which I do.  :cool:

P.S.:  I LOVE the quote in your signature. :p

---

### Post by davideotape on 2009-05-28
> **HotShotDJ said:**
> Thank you for your kind invitation -- perhaps I'll seek out the thread to which you referred, although I'm not all that concerned about it... as long as I have the version of OOo that I want, which I do.  :cool:

P.S.:  I LOVE the quote in your signature. :p

Sorry, I'd have found it myself but I'm on my iPod touch. And thanks for thanks :D

---

### Post by zika on 2009-05-28
After fiasco with ppa for one of the previous upgrades of OO I was very reluctant to do this upgrade. It worked like a charm! Thank You.

---

### Post by khelben1979 on 2009-05-28
I wish I could go for this latest version on Debian Lenny, but I suspect that the ppc linux architecture isn't supported yet. Unofficial builds just that has been discussed in this thread is what I'm looking for. Even 3.0 will do pretty nicely. I'm sitting on 2.4.

---

### Post by ZYV on 2009-05-29
Hey!

The builds for Hardy were finally finished by this morning so I took a deep breath and tried an upgrade. The automatic upgrade didn't work for some reason, so I removed everything that had to do with OpenOffice using Synaptic and then typed sudo aptitude install openoffice.org.

I do confirm the About box problem, but the most scary part is that now my office suite looks like this ancient Redmond theme and it's so disgusting... Could anybody please tell be whether it's the same for them or I'm just missing something?

Thanks!

P.S. Oh, I figured it out... you need to install openoffice.org-gtk for it to look good!

P.P.S. Thanks Chris and everybody for your efforts!

---

### Post by andrewabc on 2009-05-29
Thanks for the update.

I have one serious bug, that should not be there. It was there for 3.0.1 as well.

1. Create new spreadsheet.
2. input a couple random letters into cell A1
3. copy cell A1 (ctrl+c)
4. double click with mouse on cell C1 and press enter. It copies cell C1 into it. Anyone know how to stop that behaviour? It is useless and annoying. I don't think it did this on windows version of 2.4.1
5. then press ctrl+z twice (first time removes copied cell, second time crashes openoffice).
6. openoffice crashes.

Is this just on the linux distro version? I seriously doubt they would release it when undo always crashes openoffice.

---

### Post by ZYV on 2009-05-29
Same thing for Hardy...

---

### Post by michael37 on 2009-05-29
Chris, could you please build lpia architecture for openoffice.org-l10n?

I see i386 is working now.

---

### Post by calc on 2009-06-01
> **michael37 said:**
> Chris, could you please build lpia architecture for openoffice.org-l10n?

I see i386 is working now.

openoffice.org-l10n is an arch all package, it only builds on i386 and is available for all others automatically.

---

### Post by dgermann on 2009-06-01
Hi--

My keyboard shortcuts are all messed up, now that I have upgraded from 3.0 to 3.1 using this ppa method.

Have tried also downloading the debs from the OOo site and installing using dpkg -i, but that will not even load for me--it crashes over and over.

Using 8.04.1 hardy.

Examples: Ctrl-Home does nothing. Shift-home and Shift-end do nothing. Until I fixed it, Backspace did nothing.

Anybody else experiencing this? Have the same thing on three machines.
I hope somebody has a fix!

---

### Post by xebian on 2009-06-01
> **andrewabc said:**
> Thanks for the update.

I have one serious bug, that should not be there. It was there for 3.0.1 as well.

1. Create new spreadsheet.
2. input a couple random letters into cell A1
3. copy cell A1 (ctrl+c)
4. double click with mouse on cell C1 and press enter. It copies cell C1 into it. Anyone know how to stop that behaviour? It is useless and annoying. I don't think it did this on windows version of 2.4.1
5. then press ctrl+z twice (first time removes copied cell, second time crashes openoffice).
6. openoffice crashes.

Is this just on the linux distro version? I seriously doubt they would release it when undo always crashes openoffice.

I only use the debs direct from OO, and I could never duplicate your problem.

---

### Post by xebian on 2009-06-01
> **dgermann said:**
> Hi--

My keyboard shortcuts are all messed up, now that I have upgraded from 3.0 to 3.1 using this ppa method.

Have tried also downloading the debs from the OOo site and installing using dpkg -i, but that will not even load for me--it crashes over and over.

Using 8.04.1 hardy.

Examples: Ctrl-Home does nothing. Shift-home and Shift-end do nothing. Until I fixed it, Backspace did nothing.

Anybody else experiencing this? Have the same thing on three machines.
I hope somebody has a fix!

Suggest you try on 1 machine, and remove every OO and then re-install using the debs from OO.

---

### Post by andrewabc on 2009-06-02
> **xebian said:**
> I only use the debs direct from OO, and I could never duplicate your problem.

There is a big discussion going on in this thread:
[Why OpenOffice is not being used by corporations?](http://ubuntuforums.org/showthread.php?t=1173176&page=3)

So far it appears to be a 64 bit only crash.
On fresh liveusb, 32 bit doesn't crash, while 64 bit does.

---

### Post by zika on 2009-06-03
After update-ing to 3.1.0 (from aforementioned ppa) I can not see any mathematics in:[http://matematika.etf.rs/predmeti/M2_rokovi/razni_rokovi/matematika%202%20_jun%20_2008_%20integralni_%20ispit_zadaci.doc](http://matematika.etf.rs/predmeti/M2_rokovi/razni_rokovi/matematika%202%20_jun%20_2008_%20integralni_%20ispit_zadaci.doc) Any ideas?

---

### Post by panaut0lordv on 2009-06-04
Well, I can't, neither.

---

### Post by zika on 2009-06-04
> **panaut0lordv said:**
> Well, I can't, neither.
I was pushing Jaunty these days to the limit with too many ppa's and such and it gave up last night. Data were saved but the system was reinstalled, which is not so bad. I'm again on OO3.0 and everything is OK. I was right being reluctant using OO from ppa ... :) So, I've been bitten twice and ... I will revert to my default behavior of using only Ubuntu approved packages ... less fun and adrenalin but more bread providing things get done that way ... :) Or, I might go Karmic way ... :)

---

### Post by ZYV on 2009-06-04
Well, I do see math here on Hardy, but it does not look very well. I am not sure whether to consider it as a regression or not, because I don't know how it looked on OOo3.

---

### Post by lvlo on 2009-06-04
I have found one little issue: in all openoffice.org-*.desktop files "StartupNotify" parameter is "False", but must be "True" by default.

UPD: should I fill a bug report?

---

### Post by mtrainer on 2009-06-17
I use a ubuntu hardy in a KDE 3.5 environment with no gconfd installed.  Openoffice 3.0.1 previously from the ppa repository had a openoffice.org-kde package.  The openoffice 3.1 in the ppa repository now doesn't have openoffice.org-kde package any more.  Is this going to be fixed?  When I do an apt-get install -s openoffice.org to see what it would do it intends install gconf packages also.

Murray

---

### Post by Progressive on 2009-06-18
They've ported OpenOffice.org to Qt 4!

[http://www.kdedevelopers.org/node/3983](http://www.kdedevelopers.org/node/3983)

When will this show up in the repos?

---

### Post by meborc on 2009-06-19
> **Progressive said:**
> They've ported OpenOffice.org to Qt 4!

[http://www.kdedevelopers.org/node/3983](http://www.kdedevelopers.org/node/3983)

When will this show up in the repos?

that is a surprise :) and a good one

can't wait to try it out

---

### Post by calc on 2009-06-28
> **Progressive said:**
> They've ported OpenOffice.org to Qt 4!

[http://www.kdedevelopers.org/node/3983](http://www.kdedevelopers.org/node/3983)

When will this show up in the repos?

The patches are actually in ooo-build for OOo 3.11. So once we get OOo 3.1.1 packages in Ubuntu the support will be there. That will probably be around the end of July.

---

### Post by Closed_Port on 2009-06-28
I just encountered an issue today with OOO 3.1 on jaunty.

When control clicking on a link in writer, the external program (in my case firefox) doesn't open, but Openoffice tries to open the link itself.

Is anyone else seeing this problem?

---

### Post by zoomy942 on 2009-06-28
i would upgrade my office install, but i didnt find a jaunty how to on the webz

---

### Post by andrewabc on 2009-06-28
> **zoomy942 said:**
> i would upgrade my office install, but i didnt find a jaunty how to on the webz

It is the same as intrepid. Use PPA
[http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu)

[This](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml) article explains how to do it for openoffice 3.0 for ubuntu 8.10. Same procedure for OOo3.1 and ubuntu 9.04
I'm not sure if the key works, but I followed that article and I have 3.1

---

### Post by philcamlin on 2009-06-28
thanks fr the info :popcorn:

---

### Post by zoomy942 on 2009-06-29
so i went to install it, and everything went okay, opens into 3.1, but i noticed this in the terminal window.

```
Setting up openoffice.org-emailmerge (1:3.1.0-5ubuntu1~jaunty1) ...
Adding extension /usr/lib/openoffice/basis3.1/program/mailmerge.py...javaldx: Could not find a Java Runtime Environment! 
Please ensure that a JVM and the package openoffice.org-java-common
is installed.
If it is already installed then try removing ~/.openoffice.org/3/user/config/javasettings_Linux_*.xml
javaldx: Could not find a Java Runtime Environment! 
Please ensure that a JVM and the package openoffice.org-java-common
is installed.
If it is already installed then try removing ~/.openoffice.org/3/user/config/javasettings_Linux_*.xml
 done.

```

seems to be mad about some JVM missing, but i didnt think anything of it becasue it still seems to work okay.  Is this a vital component?

---

### Post by andrewabc on 2009-06-29
> **zoomy942 said:**
> so i went to install it, and everything went okay, opens into 3.1, but i noticed this in the terminal window.

```
Setting up openoffice.org-emailmerge (1:3.1.0-5ubuntu1~jaunty1) ...
Adding extension /usr/lib/openoffice/basis3.1/program/mailmerge.py...javaldx: Could not find a Java Runtime Environment! 
Please ensure that a JVM and the package openoffice.org-java-common
is installed.
If it is already installed then try removing ~/.openoffice.org/3/user/config/javasettings_Linux_*.xml
javaldx: Could not find a Java Runtime Environment! 
Please ensure that a JVM and the package openoffice.org-java-common
is installed.
If it is already installed then try removing ~/.openoffice.org/3/user/config/javasettings_Linux_*.xml
 done.

```

seems to be mad about some JVM missing, but i didnt think anything of it becasue it still seems to work okay.  Is this a vital component?

Nope, java is not critical. It is only needed for some wizards and stuff.
Go to writer or calc and
tools->options->java->make sure it is unchecked. Then it should never load.

---

### Post by zika on 2009-06-29
> **andrewabc said:**
> Nope, java is not critical. It is only needed for some wizards and stuff.
Go to writer or calc and
tools->options->java->make sure it is unchecked. Then it should never load.
You can alternatively use the Java runtime You probably have with Your Java plugin. So, just, at the same place in Options, point OO to it ... :)

---

### Post by zoomy942 on 2009-06-29
Excellent.  Thanks guys.  I went to that spot and unchecked the box, but i noticed there werent any JVM's listed either.

---

### Post by zika on 2009-06-29
> **zoomy942 said:**
> Excellent.  Thanks guys.  I went to that spot and unchecked the box, but i noticed there werent any JVM's listed either.You have to "hunt" Java manually ... For example I keep it in /opt/java and update only that folder when new hre is available. In other places I just keep symbolic links. OO is Ok with that and use that without complaints ... :)

---

### Post by zoomy942 on 2009-06-29
excellent.  thansk for the replies.  since it's working okay, i'll leave it unchecked.  i dont think i have ever used any of the wizards anyway.

---

