---
title: "Why do I NEED Thai language support"
date: 2010-04-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by NZjelle on 2010-04-17
Update manager just offered me 2 updates for Thai language libraries. As I do not know the Thai language I declined those updates. I also went into Synaptic to try to remove those modules. To my great surprise I was then warned that removing the Libthai would also remove a ton of other programs, including Firefox and large parts of Gnome. After that warning I obviously backed off, and decided not to mess with those Thais. I am curious, however, why Ubuntu apparently needs the Thai language so badly?

---

### Post by esoleyman on 2010-04-17
> **NZjelle said:**
> Update manager just offered me 2 updates for Thai language libraries. As I do not know the Thai language I declined those updates. I also went into Synaptic to try to remove those modules. To my great surprise I was then warned that removing the Libthai would also remove a ton of other programs, including Firefox and large parts of Gnome. After that warning I obviously backed off, and decided not to mess with those Thais. I am curious, however, why Ubuntu apparently needs the Thai language so badly?

Ubuntu and GNOME have out-of-the-box support for Thai, Indic languages, Arabic, Hebrew, and a few others. The amount of space that these modules take up is minimal and gives those users abilities to read and write in their own languages.

---

### Post by NZjelle on 2010-04-17
> **esoleyman said:**
> Ubuntu and GNOME have out-of-the-box support for Thai, Indic languages, Arabic, Hebrew, and a few others. The amount of space that these modules take up is minimal and gives those users abilities to read and write in their own languages.
Thank you for fast response. I was aware of what you are indicating above, and I agree that it is very sensible. What I do not understand is why it looks as if it is practically impossible to remove them if I decide I do not need such support.

---

### Post by bennachie on 2010-04-17
Each distribution approaches this problem in a slightly different way. If you have an open Internet connection during an initial Ubuntu installation, the process appears to stall for some time while all the language packs are downloaded (given the duration of that pause, I find it hard to believe that the space occupied is "minimal"). I normally make sure the system is not connected to the Internet at this stage.

Fedora includes all languages in the CD (but leaves out OpenOffice to make room for them). I understand that the Fedora development team is currently re-examining this policy, and has explored the idea of making the 1GB USB stick the key target. Their current Beta ISO thus includes OO, but doesn't fit on a CD. However, the release version apparently will. 

By contrast, Mandriva offers a choice of four main versions of their One LiveCD (Europe/Americas, Africa/Asia, Africa/India and Asia/No-India). Which version you get depends on the choices you make during the download process. The Free DVD includes all the language packs, of course.

It seems at least possible that the basic download process could be built around the selected "preferred" language, and that the user could then be offered the option of "slipstreaming" in the language packs for any other languages they actually expect to use. I'd probably settle for just English and French. But I can understand the desire of development teams to focus on the already complex business of preparing release ISOs and to simplify this aspect of the process so far as possible, albeit at some cost in wasted disk space.

---

### Post by Didius Falco on 2010-04-17
You could install localepurge:

```
sudo apt-get install localpurge
```

Description:

> This is a script to recover disk space wasted for unneeded locales,
Gnome/KDE localizations and localized man pages. Depending on the
installation, it is possible to save some 200, 300, or even more
mega bytes of disk space dedicated for localization you will most
probably never have any use for. It is run automagically upon
completion of any apt installation actions.

Please note, that this tool is a hack which is *not* integrated with
Debian's package management system and therefore is not for the faint
of heart. This program interferes with the Debian package management
and does provoke strange, but usually harmless, behaviour of programs
related with apt/dpkg like dpkg-repack, reportbug, etc.
Responsibility for its usage and possible breakage of your system
therefore lies in the sysadmin's (your) hands.

Please definitely do abstain from reporting any such bugs blaming
localepurge if you break your system by using it. If you don't know
what you are doing and can't handle any resulting breakage on your own
then please simply don't use this package.

It's an unofficial, therefore unsupported, package, but I've been using it for a year with no problems.

When you first install it, it will present a list of all the localization files. simply use the up/down arrow keys to find the localization(s) you want to keep - it will highlight it. Then just press the space bar to select it. Use the Tab key to select exit when you are done. It will then delete all the localization files you did not select.

After that, every time you install something, it will automatically delete all but the ones(s) you selected.

Just like the author, though - I giver no warranty, other than I'll warrant that I've never had a problem from it.

---

### Post by Artemis3 on 2010-04-17
Did you try System -> Administration -> Language Support? There is a button there that allows you to add/remove languages, and their components (you could leave their input methods, but remove the translations, for instance).

[img]http://ubuntu.sabza.org/wp-content/ubuntu-language-support.png[/img]

---

### Post by mc4man on 2010-04-17
In this case you're talking about 2 very small lib's - libthai0 and libthai-data
libthai0 is a dep of libpango1.0-0, which if removed will snowball and remove a large part of your install.
Much to do about absolutely nothing, and doesn't constitute "Thai language support"

> LibThai is a set of Thai language support routines aimed to ease
developers' tasks to incorporate Thai language support in their applications.
It includes important Thai-specific functions e.g. word breaking, input and
output methods as well as basic character and string supports.

This package contains the shared libraries needed to run programs that use
the LibThai library

---

### Post by Didius Falco on 2010-04-17
That is another method. The advantage of localepurge is that it removes more (for example, I just opened Language Support  and the first thing it did was tell me that it wanted to install the en_gb and en_au support, which I don't want or need) and will automagically remove the localizations that you haven't selected from future updates and installs.

Set and forget, just the way I like it. :)

---

### Post by NZjelle on 2010-04-17
> **mc4man said:**
> In this case you're talking about 2 very small lib's - libthai0 and libthai-data
libthai0 is a dep of libpango1.0-0, which if removed will snowball and remove a large part of your install.
Much to do about absolutely nothing, and doesn't constitute "Thai language support"
Thank you for the clarification. Assuming the libraries are small indeed I will accept your judgment that is "much to do about absolutely nothing". I suppose I will let Update Manager go ahead with their updates then. I am still surprised that the removal of such functionality, that I do not need, "will snowball and remove a large part of your install".

In any case, your clarification makes clear that this has nothing to with Lucid specifically, so I will leave everyone in peace. Over and out.

---

### Post by mc4man on 2010-04-17
> that I do not need
Indeed you don't, it's libpango that 'needs'/possibly uses this lib.
And libpango you do need..

---

### Post by VMC on 2010-04-17
> **Didius Falco said:**
> You could install localepurge:

```
sudo apt-get install localpurge
```

Description:



It's an unofficial, therefore unsupported, package, but I've been using it for a year with no problems.

When you first install it, it will present a list of all the localization files. simply use the up/down arrow keys to find the localization(s) you want to keep - it will highlight it. Then just press the space bar to select it. Use the Tab key to select exit when you are done. It will then delete all the localization files you did not select.

After that, every time you install something, it will automatically delete all but the ones(s) you selected.

Just like the author, though - I giver no warranty, other than I'll warrant that I've never had a problem from it.

Thanks for this information. I was using *bleachbit *just to remove localization, which on first use deletes more than 60mb's.

I will try *localpurge*.

---

### Post by emarkay on 2010-04-17
Yea, why is the owners manual of my bike in English, Spanish, French, German, Igpay Atinlay and Korean? 

Nothing like printing 200 pages when 50 will do.

"But to selectively offer the individual variants would take 3 minutes and cost 6.7 cents..."

Oh well, "It's a small world after all..."

---

### Post by VMC on 2010-04-17
There must be an associated ppa, because:

```
sudo apt-get install local**e**purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package localpurge
```

Edit: that's because I can't spell :redface:
Nevermind.

---

### Post by Didius Falco on 2010-04-17
> **VMC said:**
> There must be an associated ppa, because:

```
sudo apt-get install localpurge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package localpurge
```

It's in the Universe section, under System Administration in my Synaptic...I'll have a look around and report back.

On Edit: Maybe you should check and make sure Universe is enabled in your sources. Otherwise, it's available from here:

[https://launchpad.net/ubuntu/lucid/i386/localepurge/0.6.2](https://launchpad.net/ubuntu/lucid/i386/localepurge/0.6.2)

On 2nd Edit:

It's definitely in the Universe repo: [http://packages.ubuntu.com/lucid/admin/localepurge](http://packages.ubuntu.com/lucid/admin/localepurge)

---

### Post by tokyobadger on 2010-04-17
[quote="Ubuntu Philosophy: Core Philosophical Ideal #2"][Every computer user should be able to use their software in the language of their choice.](http://www.ubuntu.com/community/ubuntustory/philosophy)[/quote]
Part of the reason we get to enjoy high quality software for free is the commitment to make the platform as accessible and attractive to as broad a group of developers and users as possible. Not every developer who contributes is from an English-speaking country.

You might as well ask, 'Why does the installer need to support 50+ different keyboard layouts beyond the QWERTY that I need?'

All you've got on your install in terms of Thai (and other languages) is enabling infrastructure, no different from Windows or OSX.

I'm sure you could find a distro that was built for English only, maybe LFS, but I guarantee you wouldn't get the level of polish and support that Ubuntu offers.

---

### Post by Didius Falco on 2010-04-17
> **tokyobadger said:**
> Part of the reason we get to enjoy high quality software for free is the commitment to make the platform as accessible and attractive to as broad a group of developers and users as possible. Not every developer who contributes is from an English-speaking country.

You might as well ask, 'Why does the installer need to support 50+ different keyboard layouts beyond the QWERTY that I need?'

All you've got on your install in terms of Thai (and other languages) is enabling infrastructure, no different from Windows or OSX.

I'm sure you could find a distro that was built for English only, maybe LFS, but I guarantee you wouldn't get the level of polish and support that Ubuntu offers.

+1 on the above. The only reasons I use localepurge are that, unfortunately, aside from a smattering of words in various languages (many of which are not of any use in polite society...), English is my sole language. That and an obsession with removing cruft. 

My desk is a mess, but my filesystems are lean and mean.

---

### Post by VMC on 2010-04-17
> **Didius Falco said:**
> I_..._
You missed my edit above...

BTW, did I choose the correct US language. Not sure about the other two:

---

### Post by Yellow Pasque on 2010-04-17
Yeah, it seems like bloat to me too: Here's the offical bug report: [https://bugs.launchpad.net/ubuntu/+source/libthai/+bug/509919](https://bugs.launchpad.net/ubuntu/+source/libthai/+bug/509919)

---

### Post by tokyobadger on 2010-04-17
@Didius Falco: Glad we agree on the principle. A few questions came to mind however:
1) would localepurge actually get rid of libthai and libthai-data? it's described as a tool that gets rid of locale files and mult-language man files
2) how do you define cruft? on gentoo, I'd call cruft the tarballs that get left in /usr/portage/distfiles or the portage error logs in /var/tmp/portage when an ebuild fails and similar; since localepurge does not work in coordination with Debian/Ubuntu's package manager doesn't it increase the risk of 'cruft'?
3) given the cost of hard disk storage these days, it seems a lot of extra effort (and risk for the uninitiated) to save 100 ~ 200 Mb of space - does it have a positive impact on system responsiveness, app-launching?

I referenced Gentoo above, and I realized that on my Gentoo (Funtoo) install, I did choose which locales were installed; the package management there after sets unwanted language flags as '-fr, -ch' etc unless you specifically require a package to be built with other language support. I think Arch also does this, I can't recall at the mo'. So, you can have lean and mean built from the ground up without going to the pain of LFS - the pain there continues after (hopefully) successful building, because there is no default package manager to keep the system updated :)

---

### Post by Longinus00 on 2010-04-17
```
$ dpkg -s libthai0 | grep Size && dpkg -s libthai-data | grep Size
Installed-Size: 116
Installed-Size: 596

```

You would save more space by uninstalling all the unicode fonts on your system and replacing them with asci only versions. That'll prevent them foreign languages from showing up.

```
$ dpkg -s ttf-freefont | grep Size
Installed-Size: 4172

```

---

### Post by tokyobadger on 2010-04-17
> **Temüjin said:**
> Yeah, it seems like bloat to me too: Here's the offical bug report: [https://bugs.launchpad.net/ubuntu/+source/libthai/+bug/509919](https://bugs.launchpad.net/ubuntu/+source/libthai/+bug/509919)
The vulnerability was found in January and fixed in all major distributions and was actually pango/glib not libthai - did you read what you posted?

I think the bug poster doesn't know what he's asking.

In terms of bloat /usr/share/libthai is worth a staggeringly profligate 531.9KB of your hard drive; why not have a look at /usr/share/i18n ?

**EDIT** you won't get rid of libthai with localepurge or bleachbit on ubuntu. It is a dependency of pango which reflects Ubuntu's philosophy of building an OS from the ground up that works for everyone. [ see here ](http://packages.ubuntu.com/karmic/libpango1.0-0) (yes it's Karmic, but I wouldn't expect Lucid to be any different). That's why you'll trash your install if you try and uninstall it (as a couple of people in the comments to the above bugpost belatedly discovered.
For comparison, look at [gentoo's ebuild for pango, especially the RDEPENDS section](http://sources.gentoo.org/viewcvs.py/gentoo-x86/x11-libs/pango/pango-1.26.2.ebuild?view=markup)

So your options are, accept Ubuntu for what it is, or switch to a distro that gives you more fine-grained control over what does and doesn't get included in the build.

---

### Post by Didius Falco on 2010-04-17
> **VMC said:**
> You missed my edit above...

BTW, did I choose the correct US language. Not sure about the other  two:

Not only did I miss your edit, I missed the spelling error in the command too. :)

That's the "en" localization I'm using, with no problems.
 
> **tokyobadger said:**
> @Didius Falco: Glad we agree on the principle. A few questions came to mind however:
1) would localepurge actually get rid of libthai and libthai-data? it's described as a tool that gets rid of locale files and mult-language man files
2) how do you define cruft? on gentoo, I'd call cruft the tarballs that get left in /usr/portage/distfiles or the portage error logs in /var/tmp/portage when an ebuild fails and similar; since localepurge does not work in coordination with Debian/Ubuntu's package manager doesn't it increase the risk of 'cruft'?
3) given the cost of hard disk storage these days, it seems a lot of extra effort (and risk for the uninitiated) to save 100 ~ 200 Mb of space - does it have a positive impact on system responsiveness, app-launching?

1. Nope, it doesn't pull dependencies, only the localizations and man files in other languages - which can be a pretty good savings in space.

2. Yes, you are using the classic definition - to me, it's anything that is on my install that isn't absolutely necessary or there by my choice. For example, Evolution is a default install in Ubuntu. I don't use it, so I get rid of everything I can of it. There are a couple of files that provide other things that are useful to me, like the time and weather, and a small calendar, so I keep those - besides they are marked as "essential" and rightly so, though I wish they'd change the names from Evolution so  that purging evolution doesn't take Ubuntu down to just a "U". There are other packages that I treat the same way.

I routinely purge old packages and all but the two latest kernels, My Home directory contains nothing but package configuration files, because I have a separate Data partition to store all my own stuff and downloads. 

3. I haven't done any testing to determine one way or the other, as far as speed goes. It feels better to me and, bottom line, that's why I do it. 

I've been using localepurge for a year or so, through 4 versions, 5 counting Lucid, and have never had a problem with it.

Besides, I learn the most from my mistakes. I keep current backups, so the most I'll lose is some time, and there hasn't ever been a mistake I made I didn't learn something from.

I'm not quite ready for the build-it-from-the-ground-up experience, but I'm experimenting with customized builds of Ubuntu so as to get to that point.

Still, I do wish I spoke/read/wrote more than one language. I don't, so anything but English is wasted on me - and sometimes even English is hard. :P

---

### Post by tokyobadger on 2010-04-18
@Didius Falco: Fair play to you. That I think is the nice thing about linux / *BSD - the amount of choice you have.

I've been a linux user since 1997, a Gentoo user since 2002 (when I finally stopped distro hopping), and an Arch user since 2006. I have until recently been more in favour of those DIY distros but of late I find that I have limited time.

I've been testing FreeBSD, Fedora12, and now Lucid. I've tried Ubuntu several times in the past but never liked it until now. Lucid is a very impressive release and I reckon it carries a level of sophistication close to OSX (which I also use on an old G4 PowerBook). Speedwise, I don't see any great difference between Gentoo, Arch and Ubuntu (all amd64).

Personally I'm a fan of Evolution and Gnome in general though I do use Openbox, e17, and KDE4 on the various installs I have. My plan during the testing pahse of Lucid is to keep it as vanilla as possible to ensure easier troubleshooting.

I actually need multiple languages (privately and professionally) so it's nice not to have to manually set it up. I think that's another appealing aspect of Lucid, the level of 'just works TM'.

And I fully agree, mistakes are a great learning tool - I've made some absolute clangers in the past - fdisked the wrong drive, recursively reset the permissions on the *entire* system, etc.

I wish you luck and fun on your linux journey. FWIW, I'd skip LFS though - it's great for learning how a linux distro hangs together and you really get to value the work devs do in giving us these great distros. You also come to learn the power of package management. Gentoo you could consider an automated LFS and Arch an automated precompiled binary version.

---

