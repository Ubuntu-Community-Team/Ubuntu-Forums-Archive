---
title: "How do I install software?"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by Ragtop on 2009-12-06
...the volunteerism, community spirit, and so on and so on in the Linux and Ubuntu communities.  But for SOME reason I thought software installation would be as easy as windows, maybe just because the users' UI is so cool and friendly.  

That said, can someone please tell me where to get the info on how to get past the first step after downloading firefox with file roller.  There's a list of files of types I've never heard of (and some I have) but no HINT of what to do next to get an operating Firefox browser running under Ubuntu.

I hope this doesn't seem too whiney or needy, but I truly am spoiled by that big bully in Redmond.  I really think I can get competent with linux systems, but just need some basics to get started.

Thanks to all the volunteers, and all the best to all!

BC

---

### Post by darkod on 2009-12-06
Ubuntu comes with firefox, no need to download it.
Alternatively, just open terminal (Applications-Accessoris) and execute:
sudo apt-get install firefox

---

### Post by phillw on 2009-12-06
+1

Hi.

And you'll be pleased to know it also comes with an equivalent to MS Office already on your computer for you.

If you're running 9.10 then getting software is as easy as clicking on Applications --> Ubuntu Software Centre -- Go have a look - there are hundreds of programmes out there for you to try -- the VAST majority of them are completely free !!!

Regards,

Phill.

---

### Post by issih on 2009-12-06
Ok...You need to drop the windows way of thinking.

If you need an application for something, the best thing to do is download it from the "repositories". These are basically large lists of software that are suitable for your installation. The system works so that if you need bit of software x in order to run y, then it will automatically grab x as you download y. It basically deals with all dependancy issues and everything else for you.

To grab things from the repositories you can do one of three things:

1) open up the ubuntu software centre (its link is right there under Applications). search for some software that matches what you want, then hit install...thats it done.

2) Use Synaptic package manager (under System->Administration) which basically is another way to access the repositories, but gives you slightly more fine grained control over what "packages" (which is what the individual bits of software are called) you install, rather than simply offering you different applications or bundles of things.
From here you can install code libraries, codecs, development manuals, source code, etc, as well as the applications made available via the software centre.

3) Use the apt-get command in a terminal. This is basically the command line program that provides the heavy lifting that the above 2 use, and it is often how you will be advised to install something in these forums, becuase it is much simpler to tell you to run:

```
sudo apt-get install xxxxxx
```

to install package xxxxxx than tell you to open synaptic search for it mark it for install and hit apply.

The command is broken down into - sudo (tells the computer to run the command as the administrative user), apt-get (the name of the command to run, an action (install, remove or purge which do what you'd expect, with purge removing config files as well as the binaries) and finally xxxxxx the name of the package you want to process.


Getting software in this way is far easier than windows as in most cases you open the software centre, search for something suitable and hit install...thats it, nothing more. You should always get things from the repositories wherever possible as it will make your life much easier and minimise the chances of you having any compatability issues.

The only problems arise if the things you want are not available via the repositories. At this point you can try looking for an install file online. For ubuntu you want something compiled into a .deb file (e.g. skype provide one) the site getdeb.net has lots of them (mostly of sparkly new builds of things that are not in the repositories)

You can also add ppas which are basically tiny little repositories of additional software run either by companies or individuals, once you have added a ppa to your system the software in it becomes available via synaptic, apt-get, etc.

Finally (and I mean finally as unless you are fairly technical you may get very frustrated) you can compile things from source..but generally unless you have a good reason you should probably avoid this.

The above is only really the basics, but hopefully it will help you find your feet.

Oh and in case you handed noticed, firefox is installed by default anyway :s

---

### Post by issih on 2009-12-06
Ooh I just found something new..

The getdeb site I mentioned has changed, and illustrates one of my points nicely:

The old site:

[http://old.getdeb.net/](http://old.getdeb.net/)

is as I suggested (and as the name implies) somewhere to download ".deb" install files.

However they now have a new site, which is intended to provide access to the software via their ppa repository:

[http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)

The page at:

[http://www.getdeb.net/updates/#how_to_install](http://www.getdeb.net/updates/#how_to_install)

shows how to enable the repository, at which point all the software is available via synaptic and apt-get.

The site then makes use of a feature called apt-url which enables web links to instruct the package management system to install a specific package from the repositories.

Hope all that helps :s

---

### Post by Ragtop on 2009-12-06
Thanks for the replies (QUICK replies, too!)  unfortunately, I guess Dell in their refurb process hosed this poor little box terribly.  

First, it came with no software installed and I had to go out and buy a CDrom player and change the boot order to load what should have been there in the first place.

Second, it came with a disk labeled "Ubuntu 8.04+LTS Recovery Media", from which I have loaded and run the system.

Third, the Icon labeled "web browser" on the default desktop takes me to a Yahoo browser loaded up with real-estate gobbling Yahoo crap.

Fourth, navigating to the Mozilla site and downloading Firefox puts the icon labeled "firefox 3.5.5.tar.bz on the desktop.

Fifth, double clicking on _that_ icon takes me back to the point I described in my first post in this thread.

One possible answer that presents to me is a thumb drive that a friend presented me with that has a bunch of linux distros, including "ubuntu-9.10-desktop-i386"

A few questions follow on to having this thumbdrive:

Do I _really_ want to upgrade from Dell's supplied 8.04? 

Is this the best version available now for the Mini-9?

and 

Will it boot and/or auto-install from the thumbdrive?

I am grateful for the guidance, and think "we' are closing in on the answers I'd like to have.    I'm just wishing to NOT foul this up and continue to learn from the community members.

All the best to y'all!

BC

---

### Post by darkod on 2009-12-06
Download the 32bit (i386) or 64bit desktop image here:
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

That's the latest 9.10 version. There is option when you boot with the cd to Try Ubuntu first. Use it to see how you like it. Then you can install it if all is working fine, etc.
Yes, 8.04 would come with old version of firefox.
And .tar.gz is archive, like .zip. If you right-click on it you can open it with archive manager and extract the file(s).

---

### Post by phillw on 2009-12-06
Don't diss Dell too badly - they only supply LTR (Long Term Releases).
8.04 is the Last one, the next one arrives with 10.04 (April 2010)

Upgrading from 8.04 all the way to 9.10 is not really recommended. As long as you can boot from a LiveCD then you are okay to do a clean install of 9.10.

Just be aware, it may take a little while to get all the sound / video etc sorted, so keep your 8.04 disk & 9.10 disks handy :-)

There is a forum area especially for Dell Computers --> [http://ubuntuforums.org/forumdisplay.php?f=342](http://ubuntuforums.org/forumdisplay.php?f=342)

They will be able to help with any specific problems you have with your machine, for general stuff, pop by here and ask !!

Regards,

Phill.

---

### Post by issih on 2009-12-06
You are currently using UNR...which is ubuntu netbook remix. Basically its still ubuntu, but the user interface is tweaked a bit to be more usable on a small screen:

[https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)

You can choose to stick with the 8.04 version (which is still supported at the moment, as it was the previous Long Term Support (LTS) release). Or you can grab a newer one as others have said, if you choose to get a newer version its up to you if you want the remix version or the full blown desktop install, both are available at the link you were given earlier:

[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

You probably will find that dell have put some bloatware on the image that they supply though...leopards spots and all that.

Newer releases tend to have newer versions of software available via the repositories (e.g. firefox will be V2.x rather than 3.x in 8.04), so if you choose to stick with the earlier version and you want newer stuff you need to enable the backports repository - which provides newer software for older versions. or add the getdeb repository as described previously.

One other thing to be aware of is that the equivalent of software centre in 8.04 is "add/remove programs".

All in all..stop trying to download firefox via a webbrowser its not how it is done in ubuntu (at least not as a first port of call)

---

### Post by Flying caveman on 2009-12-06
Weird, when I bought a Ubuntu pre-installed netbook it worked great until I decided to install updates.  (so about 5 minutes) I can't remember exactly what happened, I think it had a weird partitioning scheme that didn't allow any room for updates.  I can totally see someone who is trying Ubuntu for the first time and not knowing what to do.  I smell a conspiracy.  Too bad there isn't a big Linux corporation to sue companies for selling special versions that self destruct.  The regular Ubuntu version I installed works and continues to work perfectly.

I saw a poll on these forums asking about people who bought a pre-installed Linux system and had kept the same install.  Something like 90% had installed a different OS.  Sorry can't find the link to the poll.  It says alot about Linux users.

Anyway, I would download a regular Ubuntu .iso and use Unetbootin to make a bootable USB drive.

---

### Post by Ragtop on 2009-12-06
OK, then, my questions seem to have evolved, thanks to your generous input.  Now I wonder:

Is there any real quantifiable reason to update from 8.04 now rather than wait 5 months for the next long term support version?  

I'm still puzzled by the fact that nowhere in the web browser is there any reference to Mozilla or Firefox.  It operates the same way, near as i can tell, but I want the real thing.  That yahoo toolbar is useless to me, and annoying as it steals that fraction of precious vertical desktop space.

Supposing that I can get "Genuine" Firefox through the software _centre_ (love that Brit accent:D) , I should be able to update it through the Mozilla update process, right???

Interestingly, when I clicked on the "Firefox" bar in the "Add/Remove Applications" window I got an error msg telling me that I "Cannot remove 'firefox3.0' to remove firefox 3.0 and the dependent applications use the Synaptic package manager."  Which goes back to the earlier suggestion by "issih".  perhaps those dependent applications are the yahoo crap i've been upset about?.

Onward thru the fog!

BC

---

### Post by issih on 2009-12-06
Aha...well it looks like dell have supplied their own version, with firefox 3.x running on 8.04 and a few customisations.

[http://www.mydellmini.com/forum/ubuntu-netbook-remix/2331-warning-about-most-recent-dell-ubuntu-update.html](http://www.mydellmini.com/forum/ubuntu-netbook-remix/2331-warning-about-most-recent-dell-ubuntu-update.html)

to remove the toolbar the following should work, but I don't know, I'm cobbling together from links as I don't run unr.

open a terminal and enter:

```
sudo apt-get remove yahoo-toolbar-extension
```

then enter your login password when prompted and hit enter (nothing will be echoed to the screen..just do it)

After that you will have firefox...its just been customised by dell to have a silly name, the version is a smidge old it 3.05 rather than 3.5, but it is firefox I assure you.

---

### Post by Ragtop on 2009-12-06
And, just as you said, and in the immortal words of Gomer Pyle, U.S.M.C. "SHAZAAAM!", it's GONE! :lolflag: Darn, this command line (terminal mode) is pretty cool.  
Thank you, issih!

As a matter of general interest, now the silly pink bar at the top just says "web browser" at the end, but it is indeed Firefox! 

OKAY, sometimes it's the small victories!

ATB

BC

---

### Post by issih on 2009-12-07
Do bear in mind that you could have done the same by opening synaptic package manager...searching for yahoo and removing the package graphically.

Its just easier for me to tell you to enter one line...

---

### Post by Ragtop on 2009-12-07
Yes, I got that from your previous post, and understand.  I'll need to get more familiar with package manager. :oops:

Thanks again!

BC

---

