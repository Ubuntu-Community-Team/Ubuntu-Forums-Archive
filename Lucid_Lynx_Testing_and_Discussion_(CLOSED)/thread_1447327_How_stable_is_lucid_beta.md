---
title: "How stable is lucid beta?"
date: 2010-04-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Roger Allott on 2010-04-05
For various reasons, I'm very keen to install lucid 10.04 x64.

What is the general advice? Should I wait until 29th April when the full release is out, or should I give the beta version a go?

---

### Post by Calash on 2010-04-05
In general it is better to wait for at least the RC before jumping onto a new release.

With any Beta you have to remember that you are a tester first.  Expect things to break and be prepared to give feedback when they do so the developers can improve the product.


Read over all of the information in the development forum before taking the plunge.  There is a lot of important information that you will need to know.

Overall it is fairly stable.  I get some odd crashes but so far none of them have been too bad.  It is very Social Networking enabled, something I am still not sure if I like yet or not.  Very fast startup times too.

---

### Post by Paqman on 2010-04-05
> **Roger Allott said:**
> Should I wait until 29th April when the full release is out, or should I give the beta version a go?

Unless you're completely confident with troubleshooting (and accurately reporting!) bugs and problems, stick to the stable release. As a minimum i'd recommend a good working knowledge of package management, Grub, the command line, how to chroot, and using Launchpad. If you can do all that, then you'll probably make a good tester.

Also bear in mind that the development branch can mean hundreds of MB of updates every day, so if you're on a capped connection I wouldn't advise it.

What problems are you trying to fix anyway?

---

### Post by philinux on 2010-04-05
Advice above is good also read the sticky threads here [http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

---

### Post by 3rdalbum on 2010-04-05
If this is a computer that you use to make money with, then don't use beta software.

You've been an Ubuntu user for a year and a bit, so you've probably got a fighting chance in the unlikely event that something breaks. Lucid has been very stable for me and for a lot of other people; I encountered one serious breakage and heard about another, and I've been using Lucid since Alpha 3. I fully believe that Ubuntu could do a good rolling-release distro based on how excellent Lucid's development cycle has been.

Go for it, and don't forget to submit bug reports wherever you see problems; you may get a quicker response from the Ubuntu developers if you use Apport (either the notification that a program has crashed, or the 'apport-bug' command) because it will gather all relevent information for you.

---

### Post by Paqman on 2010-04-05
> **3rdalbum said:**
> (either the notification that a program has crashed, or the 'apport-bug' command)

It's
```
ubuntu-bug *packagename*
```

isn't it?

---

### Post by phibxr on 2010-04-05
My most annoying problem with the Beta so far has been that there hasn't been any problems, so I don't have anything to report to the developers. <_<

---

### Post by Penguin Guy on 2010-04-05
> **Roger Allott said:**
> How stable is lucid beta?
Not very stable, that's why it's called a 'beta'. Things will break, you will need to have some level of experience to fix them.

---

### Post by ratcheer on 2010-04-05
I am reinstalling on a weekly basis for my testing team duties. I am seeing major changes from week to week, even daily.

I recommend waiting for the production release on April 29. If you have a spare partition of about 4 GB or so, install Lucid as a test, but don't overlay your main installation, yet.

Tim

---

### Post by 3rdalbum on 2010-04-06
> **Paqman said:**
> It's
```
ubuntu-bug *packagename*
```

isn't it?

ubuntu-bug has been superceded by apport-bug. If you type 'ubuntu-bug' it will call apport-bug.

---

### Post by garvinrick4 on 2010-04-06
To me it is important to start with the first Alpha so I understand the quarks and bugs of
my system while doing daily upgrades. I do seem to have to use a Live CD from time to
time to keep it going but that is expected. If you cannot use a Live CD you will be doing a
lot of clean installs. Right now it is pretty stable for me, plymouth, mountall and such have
been the major bugs for me. Early on Samba was on the fritz. All in all it has been a better
Alpha and Beta for me than previous versions, either because of the developers or myself getting a little better at understanding what it takes to keep a unstable OS running. 
Any which way if you have one stable OS and want to update or clean install another
to 10.04 lucid jump on in it is in a upgrade freeze right now. If something is buggy just Google a lot and read the Lucid Lynx Testing Forum. Just do not be one of those moaners if everything does not act perfectly. There seems to be enough of those for the time being.
Have fun and enjoy.

---

### Post by stinger30au on 2010-04-07
i installed 10.04 beta about 2 days ago on my main pc

it has not skipped a beat since install.... touch wood

YMMV though

---

### Post by haddog on 2010-04-07
Lucid Beta 1 has been good for me, actually solid I'm using the Ubuntu Netbook Edition on a Dell Mini. Beta 2 is supposed to be out Thursday April 8.

---

### Post by atlee on 2010-04-07
I would say being stable all has to do with different hardware configs for me my hardware has been fairly stable with 10.04, everything works fine, i do get crashes but mainly applet crashes but all my everyday apps work, nvidia still has a issue but i got around that, I'm looking forward to Beta 2 tomorrow but i don't think it will make a huge difference as its still beta.

---

### Post by praveenthivari on 2010-04-07
Ok I think it depends on ur needs basically. If u want to try out all the features, u may hv some problems. 

At present there seems to be some random crashes of some programs like 'gvfs' or something like that. The plymouth problem!!!. 

Such minor but a bit annoying but not any show stopper. Otherwise pretty solid.:-)

---

### Post by recluce on 2010-04-07
Lucid is extremely stable for an *unstable* OS. Obviously, experiences vary depending on individual hardware, installed packages and user expectation as well as user expertise.

For me, the only real problems were plymouth (mostly solved) and apport (which just crashes on me with weird/wrong error reports - I will reinistall it with beta2 release). 

All that being said, I will still not thrust any important work and data to Lucid, for the moment I quadruple boot (Windows XP and Windows 7 are there for testing purposes) into Jaunty for work and into Lucid for the fun of it.

---

### Post by seenthelite on 2010-04-07
How stable is lucid beta, well I have had it installed since the alpha release and it is extremely stable on both my installs, Kubuntu on one box and Ubuntu on this one. But they are not my main OS yet. I have only installed each of these once and usually update twice a day when updates are available, no crashes, no bugs, no problems. My testing, as a novice, simply has been to install and use it as I would normally use any OS. If or when I see a bug I will report it.

---

### Post by phillw on 2010-04-07
Hi

I gave up trying to break it :) and I cannot break Lubuntu 10.04 either 
:lolflag:

Still have my backups, and lots of them and still doing them.

+1 to having it on a seperate partition, copy over what you need from your stable release /home (e.g. .mozilla if you want your bookmarks, history, saved passwords etc. .purple if you use pidgin etc.)

[http://ubuntuforums.org/showthread.php?t=1352578&highlight=phillw](http://ubuntuforums.org/showthread.php?t=1352578&highlight=phillw)

Regards,

Phill.

---

### Post by Roger Allott on 2010-04-07
Many thanks for all of your responses. I think I'm not yet ready to run a pre-launch linux, but maybe I'll do so for the next release and contribute some bug reports to the development team.

One question though. A few of you have mentioned 'plymouth'. What is that? Is it new for lucid?

---

### Post by QLee on 2010-04-07
[QUOTE=Roger Allott]Many thanks for all of your responses. I think I'm not yet ready to run a pre-launch linux, but maybe I'll do so for the next release and contribute some bug reports to the development team.[/QUOTE]

Probably a wise decision, you know how comfortable you are with troubleshooting better than anyone else could.

[QUOTE=Roger Allott]One question though. A few of you have mentioned 'plymouth'. What is that? Is it new for lucid?[/QUOTE]

In anticipation of your becoming a "tester", I suggest you become familiar with the search function of the forum, I think often that is the first, best, place to start. For example, you might investigate the posts about plymouth if you want to understand what those "mentions" are about. The "plymouth" they are referring to in this case, is a splash screen.

---

### Post by philinux on 2010-04-07
> **Roger Allott said:**
> One question though. A few of you have mentioned 'plymouth'. What is that? Is it new for lucid?

Use the pull down link "Search This Forum" you will see a large plymouth thread it also has video links.

---

### Post by fedexnman on 2010-04-07
if you have a nvidia graphics card, you better wait til 29th april, i hope this stuf gets iron'd out, soon

---

### Post by BrokeMahPC on 2010-04-07
Generally not bad on beta1  - everything worked fine until I started trying to customize things and installed the proprietary ATI driver! The open source ATI driver that installed with ubuntu was fine - I think it even has 3d support.

-The ATI proprietary driver broke Plymouth
-I fixed Plymouth but the fix broke suspend / resume and the Gnome panel
-I fixed Gnome panel with: gconftool --recursive-unset /apps/panel && killall gnome-panel
-Upon resume ubuntu GDM crashes (generates a serious kernel crash report) and you have to Ctrl+Alt+F1 to sudo reboot.

So if you want to use it fine - just don't mess with it too much, but I suppose with beta's we are supposed to play with them till they break! But it's always best to wait for the official release. In the past upgrading from beta2 - release did not go well and I suspect with the plymouth / video driver problems that many are having this will be the case at the end of the month!

In short, wait for them to fix Plymouth before you use 10.04 for anything important, and take care with the Nvidia and ATI proprietary drivers.

---

### Post by Uncle Spellbinder on 2010-04-07
> **fedexnman said:**
> if you have a nvidia graphics card, you better wait til 29th april, i hope this stuf gets iron'd out, soonNot really


Been running Lucid since Alpha 2. I have a nVidia 9800GT. With the exception of some issues with Plymouth in Alpha 3, everything has been smooth sailing.

---

### Post by fedexnman on 2010-04-07
> **Uncle Spellbinder said:**
> Not really


Been running Lucid since Alpha 2. I have a nVidia 9800GT. With the exception of some issues with Plymouth in Alpha 3, everything has been smooth sailing.

 what drivers are you using i have that same card, and im having nothing but problems, plymouth screen not showing ,black screen, top panel not loading ?

---

### Post by Uncle Spellbinder on 2010-04-07
> **fedexnman said:**
> what drivers are you using i have that same card, and im having nothing but problems, plymouth screen not showing ,black screen, top panel not loading ?
nvidia-current (which is 195.36.15) from the repositories.

---

### Post by Roger Allott on 2010-04-07
> **BrokeMahPC said:**
> 
In short, wait for them to fix Plymouth before you use 10.04 for anything important, and take care with the Nvidia and ATI proprietary drivers.

The desktop I was planning to resuscitate with lucid has nVidia, but my main laptop has intel. I suppose I'll install lucid on the laptop on the 29th, but wait for a few days to see whether I should try it on the desktop. I'll monitor the Abs Beg sub-forum here to see if there are any residual gremlins in the launch version.

---

### Post by fedexnman on 2010-04-07
> **Uncle Spellbinder said:**
> nvidia-current (which is 195.36.15) from the repositories.

lol , lucky you man !! ive done that and its been a disaster for me and ive been reading others having problems with ati, nvidia not jiving with plymouth.

---

### Post by wkulecz on 2010-04-07
> **fedexnman said:**
> if you have a nvidia graphics card, you better wait til 29th april, i hope this stuf gets iron'd out, soon

No issues for me with a Nvidia Geforce 5500 (or is it 6200, I forget which are in what systems) using the proprietary drivers.  The open source "nouveau" drivers didn't last two minutes for me -- lots of screen redraw problems when uncovering windows.

Actually 10.04Beta has lasted the longest yet without a lock up when letting a random screensaver run, and I haven't had a lockup yet since I disabled the screensaver and got rid of the desktop "slide show" background -- its cool, but not useful if the system is dead when I get back the next day.

Its Beta, mostly I'm finding stuff (apps) is missing and I've issues of very slow DNS lookups that can make Firefox nearly unusable on some sites.

I just hope all the apps I need are ready and in the repos at release.

Edit:


What is Plymouth, and why do I need it?  I got a crash from it initially and the bug report was already filed, but other than missing Glade3 and some other development tools, its working well for me so far -- I'm trying to use it as much as I can.

---

