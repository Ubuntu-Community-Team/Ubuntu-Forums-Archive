---
title: "OpenOffice 3.2 released"
date: 2010-02-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2010-02-11
When will it make it into the repos and PPA?
I want to update my 9.10 install.

[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

I know Chris said he was waiting for final release before putting anything up in PPA.
Probably wait for Lucid version to be put up first?

[http://packages.ubuntu.com/lucid/openoffice.org](http://packages.ubuntu.com/lucid/openoffice.org)
Has RC4

Lots of good improvements in 3.2
[http://www.openoffice.org/dev_docs/features/3.2/](http://www.openoffice.org/dev_docs/features/3.2/)

---

### Post by zika on 2010-02-11
Lucid has OO3.2 already...

---

### Post by Merk42 on 2010-02-11
> **zika said:**
> Lucid has OO3.2 already...

Lucid currently has Release Candidate 4, not final. As there was an RC5 that means there are some differences between it and the final version.

---

### Post by zika on 2010-02-11
> **Merk42 said:**
> Lucid currently has Release Candidate 4, not final. As there was an RC5 that means there are some differences between it and the final version.Right. So I was a bit non-focused on that... Nevertheless, there is a visible improvement...

---

### Post by andrewabc on 2010-02-11
I said in my original post lucid has RC4. :)

I was posting in this forum because it's better place to get response from Chris about PPA question.

Anyone notice good/bad differences between 3.2 and 3.1.1 ?
I'm mostly happy with lots of calc improvements. I think I pointed out a couple [crash bugs](http://qa.openoffice.org/issues/show_bug.cgi?id=102456) that happen since Jaunty that are fixed. Hopefully they are.

---

### Post by Doctor Drive on 2010-02-11
> 
When will it make it into the repos and PPA?


I'm wondering about that too...

---

### Post by xebian on 2010-02-11
> **andrewabc said:**
> I said in my original post lucid has RC4. :)

I was posting in this forum because it's better place to get response from Chris about PPA question.

Anyone notice good/bad differences between 3.2 and 3.1.1 ?
I'm mostly happy with lots of calc improvements. I think I pointed out a couple [crash bugs](http://qa.openoffice.org/issues/show_bug.cgi?id=102456) that happen since Jaunty that are fixed. Hopefully they are.

I have been using the debs direct from OO and they look good in 9.10 & 10.04.  Looks like the RC5 and final are of the same build m12.  Haven't done any rigorous testing but as a rule of thumb ver 3.2 should be better than 3.1.  Don't you think so?

---

### Post by meho_r on 2010-02-11
I too prefer direct download from official website. Works fine.

---

### Post by FrancoNero on 2010-02-11
i'm a bit confused. their download is like a package full of .deb files... how do i install it? (running Karmic)

---

### Post by joseelsegundo on 2010-02-11
Instructions for installing OpenOffice are here:

[http://wiki.services.openoffice.org/wiki/Documentation/Administration_Guide/Linux]("http://wiki.services.openoffice.org/wiki/Documentation/Administration_Guide/Linux")

Scroll down to "DEB Based Linux Distributions" and ignore the part about running alien, since you already have the debs and don't need to convert from rpm.

Perform all the steps under "install" and then bask in the warm glow of OpenOffice 3.2.

---

### Post by JackRock on 2010-02-11
> **joseelsegundo said:**
> Instructions for installing OpenOffice are here:

[http://wiki.services.openoffice.org/wiki/Documentation/Administration_Guide/Linux](http://wiki.services.openoffice.org/wiki/Documentation/Administration_Guide/Linux)

Scroll down to "DEB Based Linux Distributions" and ignore the part about running alien, since you already have the debs and don't need to convert from rpm.

Perform all the steps under "install" and then bask in the warm glow of OpenOffice 3.2.

I get this at the last step:

> jackrock@Desktop:~/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/desktop-integration$ sudo dpkg -i openoffice.org3.2-debian-menus_3.2-9472_all.deb
dpkg: regarding openoffice.org3.2-debian-menus_3.2-9472_all.deb containing openoffice.org-debian-menus:
 openoffice.org-debian-menus conflicts with openoffice.org-bundled
  openoffice.org-core provides openoffice.org-bundled and is present and installed.
dpkg: error processing openoffice.org3.2-debian-menus_3.2-9472_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 openoffice.org3.2-debian-menus_3.2-9472_all.deb

Any help would be appreciated.  I've tried removing 3.1 through both Terminal (apt-remove) and Synaptic before doing this process.  I've also tried upgrading while OO3.1 was still installed.  Always comes back the same message.

I'm on 9.10 x64

---

### Post by JackRock on 2010-02-11
Solved it with this thread: ttp://ubuntuforums.org/showthread.php?p=8811553

---

### Post by Doctor Drive on 2010-02-11
I prefer to use native ubuntu packages.
They're better supported, more comfortable too fetch extra packages related to OO.o

---

### Post by xebian on 2010-02-11
> **JackRock said:**
> I get this at the last step:



Any help would be appreciated.  I've tried removing 3.1 through both Terminal (apt-remove) and Synaptic before doing this process.  I've also tried upgrading while OO3.1 was still installed.  Always comes back the same message.

I'm on 9.10 x64

sudo apt-get purge OO3.1 <--shhud put the actuall package name

---

### Post by xebian on 2010-02-11
Purge all OO by

```

sudo dpkg -l | grep openoffice | cut -f 3 -d " " | xargs -x apt-get -y purge

```

Then reinstall OO3.2

---

### Post by varsamakos on 2010-02-11
Out of curiosity, when will OO.o 3.2 make it in official repos ?

---

### Post by xebian on 2010-02-11
> **varsamakos said:**
> Out of curiosity, when will OO.o 3.2 make it in official repos ?

You need to go to Delphi and ask the Oracle.  ;)

---

### Post by varsamakos on 2010-02-11
I thought that we can do a prediction based on previous announcements. Thanks for answering.

---

### Post by xebian on 2010-02-11
> **varsamakos said:**
> I thought that we can do a prediction based on previous announcements. Thanks for answering.

Well it was just out today 2/11 from Oracle (btw they own it now).  So, apparently Ubuntu devs has to look at it, do some development(presumably), integration, polishing, then beta testing, then RC testing, ..,etc.  OO is a huge project so there you can see how long it might take.  You might see it first in Lucid, and then backported to karmic & others.

---

### Post by ezsit on 2010-02-11
I've been running 3.1.1 in Intrepid since it was released, how long can it take to get 3.2 in Lucid. Its not like OO is going to break something else. Installing direct from OpenOffice.org seems to be better than whatever Ubuntu does to the packages anyhow. Just do it yourself and be happy.

---

### Post by andrewabc on 2010-02-11
> **ezsit said:**
> I've been running 3.1.1 in Intrepid since it was released, how long can it take to get 3.2 in Lucid. Its not like OO is going to break something else. Installing direct from OpenOffice.org seems to be better than whatever Ubuntu does to the packages anyhow. Just do it yourself and be happy.

3.2 RC4 is in lucid. So not long.


> **xebian said:**
> Well it was just out today 2/11 from Oracle (btw they own it now).  So, apparently Ubuntu devs has to look at it, do some development(presumably), integration, polishing, then beta testing, then RC testing, ..,etc.  OO is a huge project so there you can see how long it might take.  You might see it first in Lucid, and then backported to karmic & others.

I noticed the red oracle brand all over openoffice website.

My guess:
lucid: 1 week. It already has RC4 so pretty much the same thing that final will be.
PPA: whenever Chris gets around to it, most likely same time or shortly after lucid. Since he uploads Lucid openoffice as well.

Best solution is to wait for PPA for non lucid ubuntu.

---

### Post by Ibidem on 2010-02-11
> **xebian said:**
> Purge all OO by

```

sudo dpkg -l | grep openoffice | cut -f 3 -d " " | xargs -x apt-get -y purge

```Then reinstall OO3.2
That command does not work here. 
Synaptic and Aptitude run, but the command given complains that it can't open the lock file or the administration directory.  It worked when I added "sudo" between -x and apt-get
sudo is only working on dpkg -l, not the following piped stuff.
 
Did you try the command before running?

Ibidem

---

### Post by xebian on 2010-02-11
> **Ibidem said:**
> That command does not work here. 
Synaptic and Aptitude run, but the command given complains that it can't open the lock file or the administration directory.  It worked when I added "sudo" between -x and apt-get
sudo is only working on dpkg -l, not the following piped stuff.
 
Did you try the command before running?

Ibidem

Sorry.  I run it mostly in a root terminal.  I added the sudo just to let others know it has to be run as root.

Of course can't run dpkg with synaptic or aptitude running.

---

### Post by VMC on 2010-02-11
> **Ibidem said:**
> That command does not work here. 
Synaptic and Aptitude run, but the command given complains that it can't open the lock file or the administration directory.  It worked when I added "sudo" between -x and apt-get
sudo is only working on dpkg -l, not the following piped stuff.
 
Did you try the command before running?

Ibidem
Maybe put a "&&" and the last "|" so it waits for completion.

---

### Post by Ibidem on 2010-02-11
```
sudo dpkg -l | grep openoffice | cut -f 3 -d " " | xargs -x sudo apt-get -y purge

```
That is what worked for me.

---

### Post by altonbr on 2010-02-11
There's a nice little thread explaining how to install OpenOffice.org 3.2 here: [http://ubuntuforums.org/showthread.php?t=1404156](http://ubuntuforums.org/showthread.php?t=1404156)

Seems to have pretty good success with its users.

---

### Post by vishalrao on 2010-02-12
What about the SUN logo in the splash screen?

Isn't SUN dead and gone? What's the status? Do we now get to see Oracle's logo up there?

Or are we all doomed?

---

### Post by SecretCode on 2010-02-12
VirtualBox has a modified logo: 
[IMG]http://www.virtualbox.org/graphics/vbox_logo2_gradient.png[/IMG] 
(from [VirtualBox](http://www.virtualbox.org/)). I wouldn't be surprised if OpenOffice gets one soon.

---

### Post by xebian on 2010-02-12
> **vishalrao said:**
> What about the SUN logo in the splash screen?

Isn't SUN dead and gone? What's the status? Do we now get to see Oracle's logo up there?

Or are we all doomed?

Sun as a corporation has set and never to rise again but the Sun/Java trademarks, logo AFAIK are still valid and now owned by Oracle.

---

### Post by mattman85 on 2010-02-12
Does anyone know if the bug from 3.0-3.1.1 is fixed in 3.2 where tables in M$ doc files that are autofit don't show up properly?  I have resumes where, when I open them in OOo 3.0/3.1.1, I only see a blank document, but I can click anywhere and start typing, but it won't show what I type.  If I then adjust the ruler on either side, my tables show up.  This has had a bug ticket reported, and never had a good fix...

---

### Post by xebian on 2010-02-12
> **mattman85 said:**
> Does anyone know if the bug from 3.0-3.1.1 is fixed in 3.2 where tables in M$ doc files that are autofit don't show up properly?  I have resumes where, when I open them in OOo 3.0/3.1.1, I only see a blank document, but I can click anywhere and start typing, but it won't show what I type.  If I then adjust the ruler on either side, my tables show up.  This has had a bug ticket reported, and never had a good fix...

You are the best person to tell us by checking 3.2 with your doc,
Or you can attach the offending doc and we'll check it out for you.

---

### Post by donniezazen on 2010-03-10
Is there any way to verify m12 packages so they don't appear in obsolete packages in synaptics.

Thanks

---

### Post by andrewabc on 2010-03-17
Anyone have any ideas when openoffice 3.2 final will be released?
Currently only has RC4 and PPA hasn't been updated.

[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)
[http://packages.ubuntu.com/lucid/openoffice.org](http://packages.ubuntu.com/lucid/openoffice.org)

Calc (forum member) on vacation? Or waiting for something?

---

### Post by fab.head on 2010-03-19
> **andrewabc said:**
> Anyone have any ideas when openoffice 3.2 final will be released?
Currently only has RC4 and PPA hasn't been updated.

[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)
[http://packages.ubuntu.com/lucid/openoffice.org](http://packages.ubuntu.com/lucid/openoffice.org)

Calc (forum member) on vacation? Or waiting for something?

The PPA now says:
> If you want OOo 3.2.0 upgrade to Ubuntu 10.04 (Lucid).

OOo 3.1.1 debs for Ubuntu 8.04 (Hardy) - completely unsupported (it has security holes), I will likely remove this soon.
OOo 3.2.0 debs for Ubuntu 9.10 (Karmic) - unsupported - they will probably be up soon (by ~ Apr 2).

So, just a bit of patience and the final version will be there :)

---

### Post by xebian on 2010-03-19
If you want OO 3.2 go to openoffice.org and download the debs from there. No waiting.

---

### Post by fab.head on 2010-03-19
> **xebian said:**
> If you want OO 3.2 go to openoffice.org and download the debs from there. No waiting.

That breaks the language support, though.

---

### Post by xebian on 2010-03-19
> **fab.head said:**
> That breaks the language support, though.

You download the debs for your language and then on top of that  download the appropriate language pack.  Don't tell me ubuntu has more translator than OO.  You could be right but I doubt it.

---

### Post by mattman85 on 2010-03-19
> **xebian said:**
> You are the best person to tell us by checking 3.2 with your doc,
Or you can attach the offending doc and we'll check it out for you.

I finally got around to doing a fresh install of 3.2.  the first thing I did was open up my documents that didn't work in 3.0.x-3.1.x.  they opened fine!  I could tell where it overlapped the margins and everything..

---

### Post by PenguinInside on 2010-03-19
Wow, it's great that the startup time went from 10 to 6 seconds!

That'll make it easier to pull up Writer when you want to jot something down as opposed to having it open all the time.

---

### Post by andrewabc on 2010-03-19
> **fab.head said:**
> The PPA now says:


So, just a bit of patience and the final version will be there :)

Thanks for info.

> That'll make it easier to pull up Writer when you want to jot something down as opposed to having it open all the time. 

For those real small text I need to input, I just create an empty file on desktop, and type away.

---

### Post by CoreyB. on 2010-03-19
> **xebian said:**
> If you want OO 3.2 go to openoffice.org and download the debs from there. No waiting.

The OpenOffice in Ubuntu is a lot different from the OpenOffice on the OpenOffice.org website.  The official Ubuntu one is based on [Go-oo]("http://go-oo.org/").

---

### Post by xebian on 2010-03-19
> **CoreyB. said:**
> The OpenOffice in Ubuntu is a **_[COLOR="Red"]lot different[/COLOR]_** from the OpenOffice on the OpenOffice.org website.  The official Ubuntu one is based on [Go-oo]("http://go-oo.org/").

A lot different?  You must be joking, or you don't know what a lot means. 

I can safely say a little different. The only thing I see different is the 'brown' theme.

---

### Post by Sslaxx on 2010-03-20
Using Xubuntu, Beta 1. Is anyone having this kind of problem with packages being deemed "no longer required"?

For example:[QUOTE="stuart@sslaxxworks:~$ sudo apt-get install ttf-symbol-replacement ttf-tahoma-replacement"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  texlive-base-bin-doc openoffice.org-writer openoffice.org-impress openoffice.org-filter-mobiledev ttf-sil-gentium librdf0 openoffice.org-draw adblock-plus ttf-dejavu-extra nvidia-185-libvdpau
  openoffice.org-java-common nvidia-185-kernel-source openoffice.org-report-builder-bin java-common openoffice.org-hyphenation-en-us libaccess-bridge-java-jni libservlet2.4-java libaccess-bridge-java
  icedtea-6-jre-cacao librasqal2 redland-utils openoffice.org-math default-jre ttf-sil-gentium-basic python-uno openjdk-6-jre-headless openoffice.org tzdata-java openjdk-6-jre libjline-java
  openjdk-6-jre-lib openoffice.org-thesaurus-en-au openoffice.org-hyphenation xul-ext-adblock-plus openoffice.org-base-core openoffice.org-thesaurus-en-us openoffice.org-officebean
  openoffice.org-emailmerge ttf-dejavu rhino libhsqldb-java libraptor1 libservlet2.5-java openoffice.org-base default-jre-headless ca-certificates-java openoffice.org-calc raptor-utils[/QUOTE]

And if for some reason you do try apt-get remove openoffice.org-calc, it tries to remove the openoffice.org meta-package too. Looks like dependencies may not be set up correctly?

---

### Post by PenguinInside on 2010-03-20
> **xebian said:**
> A lot different?  You must be joking, or you don't know what a lot means. 

I can safely say a little different. The only thing I see different is the 'brown' theme.

Why do you say this? Has Go-oo (a Novell fork of OpenOfffice with certain changes) been abandoned? According to forum posts, Ubuntu OO is indeed based on Go-oo (at least partly).

---

### Post by andrewabc on 2010-03-21
> **PenguinInside said:**
> Why do you say this? Has Go-oo (a Novell fork of OpenOfffice with certain changes) been abandoned? According to forum posts, Ubuntu OO is indeed based on Go-oo (at least partly).

I think he meant that oo-go and oo.org are basically the same software with minor differences that regular user wouldn't be able to tell difference between.

---

### Post by andrewabc on 2010-03-28
3.2.0 is up
[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

says unsupported for anything other than 10.04 (I presume if bugs/stability problems no one will look at it).

With 10.04 released in a month, guess I'll just wait for that instead of messing around with 3.2.0 on 9.10.

Feel free to let us know how the PPA upgrade goes on 9.10 etc.

---

### Post by jcrow on 2010-03-31
I installed go-oo 3.2 on a karmic machine and it was pretty stable, except the row height on xls docs is always screwed up. I just migrated to another computer at work with a fresh lucid install. Openoffice crashes a lot and does not want to open opendocument documents. I installed symphony 3.2 to supplement OOO until it is fixed.

---

### Post by andrewabc on 2010-03-31
> **jcrow said:**
> I installed go-oo 3.2 on a karmic machine and it was pretty stable, except the row height on xls docs is always screwed up. I just migrated to another computer at work with a fresh lucid install. Openoffice crashes a lot and does not want to open opendocument documents. I installed symphony 3.2 to supplement OOO until it is fixed.

Please file bugs! Or find some and post here to see if others have them.

I have important opendocument spreadsheet and hope it doesn't crash much when I upgrade for Lucid final :(

---

### Post by MarkieB on 2010-04-14
no longer participating in ubuntuforums.org

---

### Post by calc on 2010-04-17
> **MarkieB said:**
> talking of openoffice 3.2, I'm seeing some apparent corruption

bug [URL="https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/562967"]#562967
[/URL] 
has anybody seen similar before? Maybe has suggestions of 32-bit libs I need / additional 64-bit libs?

That looks like a graphics driver problem and looking at the bug report you are using nvidia so I am not surprised.

---

### Post by calc on 2010-04-17
I just uploaded new openoffice.org 3.2.0-7ubuntu1 debs for 8.04 (hardy) and 9.10 (karmic), they should be finished building within 12 hours.

---

### Post by calc on 2010-04-17
> **xebian said:**
> A lot different?  You must be joking, or you don't know what a lot means. 

I can safely say a little different. The only thing I see different is the 'brown' theme.

Well the ooo-build patches (go-oo) are over 153 MB and contain over 1100 individual patches, so its more than just a little different.

---

### Post by uRock on 2010-04-17
> **calc said:**
> I just uploaded new openoffice.org 3.2.0-7ubuntu1 debs for 8.04 (hardy) and 9.10 (karmic), they should be finished building within 12 hours.

Awesome, Thanx!

---

### Post by calc on 2010-04-17
> **Sslaxx said:**
> Using Xubuntu, Beta 1. Is anyone having this kind of problem with packages being deemed "no longer required"?

For example:

And if for some reason you do try apt-get remove openoffice.org-calc, it tries to remove the openoffice.org meta-package too. Looks like dependencies may not be set up correctly?

Why would you think it would do anything different? :-) The openoffice.org depends on openoffice.org-calc to pull it in, if you try to remove openoffice.org-calc it must remove the openoffice.org package. It looks like what you are actually seeing is apt doing its normal autoremoval of packages you didn't explicitly install.

---

### Post by Linuxforall on 2010-04-17
Thanks for all your hard work calc, that keeps us happy with the latest OO3.2 in Ubuntu. Good that you supported Hardy even though Lucid LTS is right around the corner.

---

### Post by andrewabc on 2010-04-17
Looks like I'm going to install 3.2 on karmic even though I'll be formatting it in 2 weeks.
I was using a large spreadsheet and got the dreaded [copy/doubleclick/enter/undo/undo/crash bug](http://www.openoffice.org/issues/show_bug.cgi?id=102456) which is supposed to be fixed in 3.2

Having openoffice crash every couple minutes sucks.

Hmm. I just installed 3.2 and the menu text is not white. Doesn't work with dust theme I guess. Works with the other themes, and the text is always black.

Odd how dust theme worked fine with 3.1
Maybe I need to restart computer? Anyone know if similar problem in 10.04 and dust theme?

---

### Post by uRock on 2010-04-17
I had that problem in Karmic with 3.1 and the black theme I was using. This can be fixed by customizing in the Appearance applet.

---

### Post by andrewabc on 2010-04-17
> **uRock said:**
> I had that problem in Karmic with 3.1 and the black theme I was using. This can be fixed by customizing in the Appearance applet.

Hmm, I can't find the part in appearance to change only the text menus at top of openoffice.

Firefox has white text menus, so not sure why openoffice is different now.
EDIT:
whoops firefox is different because I have firefox dust theme (but vlc has white menu text so I'm not sure, must be openoffice problem).

---

### Post by calc on 2010-04-17
> **andrewabc said:**
> Looks like I'm going to install 3.2 on karmic even though I'll be formatting it in 2 weeks.
I was using a large spreadsheet and got the dreaded [copy/doubleclick/enter/undo/undo/crash bug](http://www.openoffice.org/issues/show_bug.cgi?id=102456) which is supposed to be fixed in 3.2

Having openoffice crash every couple minutes sucks.

Hmm. I just installed 3.2 and the menu text is not white. Doesn't work with dust theme I guess. Works with the other themes, and the text is always black.

Odd how dust theme worked fine with 3.1
Maybe I need to restart computer? Anyone know if similar problem in 10.04 and dust theme?

It seems to work ok with Dust on Lucid but maybe something was changed in the theme itself in the new version, I'm not sure.

---

### Post by andrewabc on 2010-04-17
> **calc said:**
> It seems to work ok with Dust on Lucid but maybe something was changed in the theme itself in the new version, I'm not sure.

ok, that is the important info I was looking for.

thanks.

Guess I could test beta2 liveusb I have and see for myself.

---

### Post by MarkieB on 2010-04-18
no longer participating in ubuntuforums.org

---

### Post by flipper9 on 2010-04-20
The only shows-topper for me is that you can't do full-screen presenter presentations under Lucid.  A bug was filed, but they said it won't get fixed until after the LTS release.  Basically if you upgrade to Lucid, you will still see the Gnome toolbar at the top of your screen and your slide will be shifted down with any slides that have text at the bottom cut-off.  The only work-around seems to auto-hide your gnome toolbar, manually hide it, disable compiz, or use Microsoft Powerpoint viewer instead under wine or the full version in Virtualbox.

---

### Post by uRock on 2010-04-20
Or just stay with Karmic until the bug is fixed. Have you tried uninstalling the maintainer's version and installing the deb from OO.o?

---

### Post by dgermann on 2010-04-21
Hi--

Where do things stand on PPA for Hardy?

Update manager shows it is all set to go, but the PPA site still shows a failed to build one package, although I am not sure I am reading that PPA site correctly.

Is it safe to download and install now? I'm in a production environment....

Thanks for all the hard work here!

---

### Post by andrewabc on 2010-04-21
There are no Hardy version available so I wouldn't upgrade.
As you said, Hardy version failed to build.

So I'd wait and see what happens.

---

### Post by dgermann on 2010-04-21
andrewabc--

Thanks! So I was reading it correctly.

Anybody hear any ETA on the Hardy version?

---

### Post by calc on 2010-04-27
> **dgermann said:**
> Hi--

Where do things stand on PPA for Hardy?

Update manager shows it is all set to go, but the PPA site still shows a failed to build one package, although I am not sure I am reading that PPA site correctly.

Is it safe to download and install now? I'm in a production environment....

Thanks for all the hard work here!

No the Hardy version built fine nearly two weeks ago.

It failed only on lpia which is a platform that Ubuntu has dropped. It was still around for Hardy so launchpad attempted to build on it but since I had removed the code from the OpenOffice.org build that was backported the build failed on that architecture.

---

### Post by frogotronic on 2010-04-27
Hi,

   The openoffice-presenter-console double/treble/multi sound bug is a showstopper for me.  Supposedly it's been patched/fixed in 3.3, so I won't be upgrading until 3.3 gets (if it) packaged for Lucid.

- CH   :(

---

### Post by Merk42 on 2010-04-27
> **cement_head said:**
> Hi,

   The openoffice-presenter-console double/treble/multi sound bug is a showstopper for me.  Supposedly it's been patched/fixed in 3.3, so I won't be upgrading until 3.3 gets (if it) packaged for Lucid.

- CH   :(

So, you won't upgrade to Lucid because it doesn't come with OpenOffice.org 3.3 (which isn't even out) when whatever version of Ubuntu you're using now clearly doesn't come with OpenOffice.org 3.3 either? :confused:

---

### Post by frogotronic on 2010-04-27
Hi,

3.1 (stock in Karmic) does not have bug.

3.2 has bug (PPA-Scribblers)

3.3 has bug fixed.

Sorry if that was badly described.

So...I'll wait unit 3.3 is available.

- CH

---

### Post by andrewabc on 2010-04-27
> **Merk42 said:**
> So, you won't upgrade to Lucid because it doesn't come with OpenOffice.org 3.3 (which isn't even out) when whatever version of Ubuntu you're using now clearly doesn't come with OpenOffice.org 3.3 either? :confused:

I think the bigger problem is that [3.3](http://wiki.services.openoffice.org/wiki/OOoRelease33) won't be released until Christmas at earliest.

I suggest **cement_head** try to get his bug fixed for [3.2.1](http://wiki.services.openoffice.org/wiki/OOoRelease321)
3.2.1 might be out in a couple months at earliest, and definitely used for ubuntu 10.10 as 3.3 won't be out by then.
It's also possible the bug only happens with go-oo and not original openoffice.org

I wouldn't stick with 3.1, lots of bugs were fixed for 3.2 (unless bugs fixed never affected you anyway).

Have a link for the openoffice-presenter-console double/treble/multi sound bug?
Maybe there is none made, so file one at openoffice bug tracker. It's a pain, but it can sometimes work.

EDIT:
Read you last post cement head, and understand you now. Bug was fixed for 3.3 release.

---

### Post by rewyllys on 2010-04-27
> **calc said:**
> I just uploaded new openoffice.org 3.2.0-7ubuntu1 debs for 8.04 (hardy) and 9.10 (karmic), they should be finished building within 12 hours.

Calc, I just saw this thread for the first time, so please excuse my belated thanks to you for enabling me to update (easily, that is) to OpenOffice 3.2 while I'm still in Karmic on both my machines.  I've been looking at 3.2 in my VirtualBox installation of Lucid, so I already know that I like the improvements in it.  Thanks again.:popcorn:

---

### Post by rewyllys on 2010-04-27
Well, now I'm confused!:(  Neither Synaptic Package Manager nor the Ubuntu Software Center seems to be aware of OpenOffice 3.2.

If anyone can clarify the matter for me, I'll be most grateful. 

Thanks in advance for help.

---

### Post by dgermann on 2010-04-27
Calc--

Many thanks! That's the news I was hoping for.

So I am off to install this now!

rewyllys--

I suspect you need to add ppa to your sources.list. Check out [https://launchpad.net/~openoffice-pkgs/+archive/ppa]("https://launchpad.net/~openoffice-pkgs/+archive/ppa") for what to add to your list.

---

### Post by calc on 2010-04-28
> **cement_head said:**
> Hi,

   The openoffice-presenter-console double/treble/multi sound bug is a showstopper for me.  Supposedly it's been patched/fixed in 3.3, so I won't be upgrading until 3.3 gets (if it) packaged for Lucid.

- CH   :(

OOo 3.3 is so delayed it might not even be done in time for Maverick. They have yet to even branch it which is the first step in stabilizing it for release.

[OOo 3.3 Release Schedule]("http://wiki.services.openoffice.org/wiki/OOoRelease33")

Last time I talked to one of the upstream developers they thought it would be available in time for Maverick but I really don't see how that will be possible as they usually take 4-5 months to stabilize a release.

---

### Post by frogotronic on 2010-04-28
> **andrewabc said:**
> I think the bigger problem is that [3.3](http://wiki.services.openoffice.org/wiki/OOoRelease33) won't be released until Christmas at earliest.

I suggest **cement_head** try to get his bug fixed for [3.2.1](http://wiki.services.openoffice.org/wiki/OOoRelease321)
3.2.1 might be out in a couple months at earliest, and definitely used for ubuntu 10.10 as 3.3 won't be out by then.
It's also possible the bug only happens with go-oo and not original openoffice.org

I wouldn't stick with 3.1, lots of bugs were fixed for 3.2 (unless bugs fixed never affected you anyway).

Have a link for the openoffice-presenter-console double/treble/multi sound bug?
Maybe there is none made, so file one at openoffice bug tracker. It's a pain, but it can sometimes work.

EDIT:
Read you last post cement head, and understand you now. Bug was fixed for 3.3 release.

Hi,

   I filed a bug report at Openoffice.org and at GO-OO.  GO-OO got back to me and we worked out that it wasn't the GO-OO build, but that it was upstream in the vanilla oo.org.  The Bug report at openoffice is here:  [http://www.openoffice.org/issues/show_bug.cgi?id=110669](http://www.openoffice.org/issues/show_bug.cgi?id=110669)

And show that it is fixed for 003.3

And I agree with you that this bug should get patched for 3.2.1 as it appears to be a very small patch for openoffice.org-presenter-console (the extension), not the main body of packages.

- CH

---

### Post by frogotronic on 2010-04-28
> **calc said:**
> OOo 3.3 is so delayed it might not even be done in time for Maverick. They have yet to even branch it which is the first step in stabilizing it for release.

[OOo 3.3 Release Schedule]("http://wiki.services.openoffice.org/wiki/OOoRelease33")

Last time I talked to one of the upstream developers they thought it would be available in time for Maverick but I really don't see how that will be possible as they usually take 4-5 months to stabilize a release.

Thanks Calc for the update.  I wonder if the presenter-console could be patched at GO-OO or at Ubuntu for 3.2.1?

I guess that depends on how much the packages have changed and how much of that infinite pile of free time you have :wink: to work on this.

Anyway, 3.1 in Karmic is pretty awesome right now.

- CH

---

### Post by frogotronic on 2010-04-28
> **rewyllys said:**
> Well, now I'm confused!:(  Neither Synaptic Package Manager nor the Ubuntu Software Center seems to be aware of OpenOffice 3.2.

If anyone can clarify the matter for me, I'll be most grateful. 

Thanks in advance for help.

Add the following PPA to your Software Sources:

[https://launchpad.net/~openoffice-pkgs/+archive/ppa]("https://launchpad.net/~openoffice-pkgs/+archive/ppa")

- CH

---

