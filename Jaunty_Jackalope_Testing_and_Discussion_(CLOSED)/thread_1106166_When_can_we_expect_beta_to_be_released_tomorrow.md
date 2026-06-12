---
title: "When can we expect beta to be released tomorrow?"
date: 2009-03-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Melhisedek on 2009-03-25
I just can't wait :popcorn:

---

### Post by kanikilu on 2009-03-25
Dunno, but I'm dumping my useless Windows 7 VM to make room for Jaunty in VBox :D

---

### Post by rustutzman on 2009-03-25
Why wait for the beta when the alpha's are stable enough for testing. I'm using Jaunty on three different machines with zero problems. None of them are my primary machine though.

Russ

---

### Post by zeroandone on 2009-03-25
> **Melhisedek said:**
> I just can't wait :popcorn:
I can't either, though I am running Jaunty Alpha 6 now.:P

---

### Post by Maheriano on 2009-03-25
When will the final version be out? I'm scared to try something unstable.

---

### Post by Melhisedek on 2009-03-25
Oh? I didn't know about the alphas :/ Will the alpha update to beta tomorrow or will I have to reinstall? 
Also can someone point me to latest alpha please?

---

### Post by rustutzman on 2009-03-25
It should upgrade and you won't need to download much to do it either as you're almost there already.

Russ

---

### Post by Technoviking on 2009-03-25
> **Maheriano said:**
> When will the final version be out? I'm scared to try something unstable.

March 26th - Beta released
April 16th - Release Candidate 
April 23rd - Ubuntu 9.04 Final released

[https://wiki.ubuntu.com/JauntyReleaseSchedule](https://wiki.ubuntu.com/JauntyReleaseSchedule)

---

### Post by JACooks on 2009-03-25
> **Melhisedek said:**
> Oh? I didn't know about the alphas :/ Will the alpha update to beta tomorrow or will I have to reinstall? 
Also can someone point me to latest alpha please?

Latest is Alpha 6, see the release notes here that include both ways to upgrade from 8.10 or download the CD Image:

[http://www.ubuntu.com/testing/jaunty/alpha6](http://www.ubuntu.com/testing/jaunty/alpha6)

---

### Post by autocrosser on 2009-03-25
Alpha 6 works great on my i7 920---as for when the Beta is released---when it is ready ;)

And I'm running the Alpha on my main testing unit.........It has been so stable for me that I'm playing  with Plymouth development...

---

### Post by Melhisedek on 2009-03-25
Only thing that worries me is that btnx is broken now... I have G5 Logitech mouse and use "tilt middle mouse button" a lot ( I use it as a middle button press ) I hope I can get it sorted somehow

---

### Post by andrewabc on 2009-03-25
To those wanting to test beta, and havn't been following alphas, wait for the beta to be released. A waste of time downloading alpha 6, then installing 200 updates totalling 200mb, which could cause problems when updating.

As with every release, no one knows exactly when it will be released so don't ask the day before when it will be released on release day...

---

### Post by rbmorse on 2009-03-25
Alternatively, if you don't need the capabilities of the "Desktop CD" and are comfortable with the text mode or alternative installer you can install the daily update.  Should include all of the updates pushed since Alpha 6 was released. 

It won't fit on a CD, but I use Brasero to write it to a DVD+RW disk and it works just fine. 

UPDATE: Looks like today's daily will fit on a CD disc. 

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

---

### Post by Flarkis on 2009-03-25
for those of us using alpha it really isint going to mean much. More or less just a name change with the normal couple of updated packages. Hopefully they figured out the mucked up kde network manager before this goes out.

---

### Post by executorvs on 2009-03-25
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
this is the daily build only difference from beta is the updates put in today. it will update, you won't have to reinstall, and jaunty has been the most stable alpha I've ever used.

---

### Post by executorvs on 2009-03-25
This close to beta why not use the daily and avoid downloading the extra updates?

---

### Post by kevpan815 on 2009-03-25
> **Melhisedek said:**
> I just can't wait :popcorn:  It's still only 22:07 here in chicago!

---

### Post by ktp on 2009-03-25
Just install the daily and update.  I think I only did one install, the first Ubuntu install...everything else has been update.  Love it.

---

### Post by kevpan815 on 2009-03-26
> **Melhisedek said:**
> Oh? I didn't know about the alphas :/ Will the alpha update to beta tomorrow or will I have to reinstall? Also can someone point me to latest alpha please? Ubuntu lets you test both alphas and nightly builds.

---

### Post by rogerdean on 2009-03-26
I've been using Jaunty as the main OS on my work laptop since Alpha 4 (that's not a recommendation of course!). It's hugely better than Intrepid for me, and almost no breakage to speak of, certainly no productivity issues (except work not done due to me compulsively updating...)

I'll download the beta iso and do a fresh install now I think, just for the sake of a cleanup

I say the team has done a superb job with this one



EDIT: oh yes, and using Thunderbird 3 beta on top. No bother. Here's the repo for that
```
sudo echo 'deb [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) jaunty main' >> /etc/apt/sources.list
```
To import the signing key -
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com ABA8EAFDEB749654ED5BA911632D16BB0C713DA6
```

---

### Post by kevpan815 on 2009-03-26
I like Alpha 6 as well! That is some thing only Microsoft Employee's get 2 test with Windows.

---

### Post by taavikko on 2009-03-26
> **rogerdean said:**
> 

EDIT: oh yes, and using Thunderbird 3 beta on top. No bother. Here's the repo for that
```
sudo echo 'deb [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) jaunty main' >> /etc/apt/sources.list
```
To import the signing key -
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com ABA8EAFDEB749654ED5BA911632D16BB0C713DA6
```

That command above shouldn't work, since shell doesn't redirect sudo.
Correct would be
```
echo "deb [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) jaunty main" |sudo tee -a /etc/apt/sources.list
```



Edit: about the beta, Downloading daily build from yesterday or from today should be pretty much the same as official beta going to be released sometime today.

---

### Post by zeroandone on 2009-03-26
I got up at 6am this morning to upgrade my machine but only found that it is not available yet:(. Will Jaunty beta release still be on schedule?

---

### Post by coffeecat on 2009-03-26
> **zeroandone said:**
> I got up at 6am this morning

Which part of the world do you live in? If you live in the Eastern hemisphere, it's going to be a long day for you. :wink:

---

### Post by int on 2009-03-26
Why not install from [cdimage]("http://cdimage.ubuntu.com/daily-live/current/") the livecd from today..

I think it is prety the Ubuntu Beta 9.04 (less one or two updates, nothing that matters)

---

### Post by zeroandone on 2009-03-26
> **coffeecat said:**
> Which part of the world do you live in? If you live in the Eastern hemisphere, it's going to be a long day for you. :wink:
I am in central area of US.:(

---

### Post by zeroandone on 2009-03-26
> **int said:**
> Why not install from [cdimage]("http://cdimage.ubuntu.com/daily-live/current/") the livecd from today..

I think it is prety the Ubuntu Beta 9.04 (less one or two updates, nothing that matters)
Thank you for the information. I wish I knew that earlier. But now I guess I will just wait hoping the beta release is still on schedule.

---

### Post by andrewabc on 2009-03-26
> **zeroandone said:**
> I am in central area of US.:(

Probably won't come out until tonight.
Either way, once it is released someone will probably make a thread announcing it has been released.

---

### Post by zeroandone on 2009-03-26
> **andrewabc said:**
> Probably won't come out until tonight.

Are you serious? It's gonna kill me!!!:(:(
I may just reinstall my machine from the daily cdimg.

---

### Post by andrewabc on 2009-03-26
> **zeroandone said:**
> Are you serious? It's gonna kill me!!!:(:(
I may just reinstall my machine from the daily cdimg.

Or you could wait until beta is released.
Could be in 5 minutes or 24 hours. Who knows?

Read my post in the other thread you replied to.

---

### Post by rbmorse on 2009-03-26
That's not a bad plan.  Once the beta gets released the servers go instantly into extremely slow mode in anticipation of the hammering they will be under for the next 48 hours.  Taking the latest daily now will avoid that.

---

### Post by autocrosser on 2009-03-26
Hey---like I said---It will be ready when it is ready......most likely 5~8 pm Pacific time.....but you can never guess--I have seen point releases delayed a couple of days depending on the build.....

---

### Post by xebian on 2009-03-26
> **autocrosser said:**
> Hey---like I said---It will be ready when it is ready......most likely 5~8 pm Pacific time.....but you can never guess--I have seen point releases delayed a couple of days depending on the build.....

If you look at the daily build time stamp, it's 2 days old.:P


[I]Filename=jaunty-alternate-amd64.iso
Template=jaunty-alternate-amd64.template
Template-MD5Sum=FTe7qAqjpH4yVPZDW7XV4A 
ShortInfo='Ubuntu 9.04 "Jaunty Jackalope" - Beta amd64'
Info='Generated on Tue, 24 Mar 2009 06:55:56 +0000'
# Template Hex MD5sum 1537bba80aa3a47e3254f6435bb5d5e0
# Template size 1994925 bytes
# Image size 728612864 bytes[/I]

---

### Post by zeroandone on 2009-03-26
> **xebian said:**
> If you look at the daily build time stamp, it's 2 days old.:P

Yeah, I noticed that too. I think the development team froze up the build for the beta release.

I have decided to wait until the beta release is officially ready. Patience, patience, patience...

---

### Post by foxy123 on 2009-03-26
So what time will it happen?

---

### Post by xebian on 2009-03-26
> **zeroandone said:**
> Yeah, I noticed that too. I think the development team froze up the build for the beta release.

I have decided to wait until the beta release is officially ready. Patience, patience, patience...

You can get it now while the server is not busy.  I'm sure they will link to this daily build as the beta release any moment from now, and then the herds will be on a stampede, and the servers will be slow and swamped.:P

---

### Post by loomsen on 2009-03-26
As always, if u have a reasonable internet connection, I'd suggest grabbing the netboot iso:

[http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-amd64/current/images/netboot/)

mini.iso should be what u want.

You won't have a graphical installer tool tho... but the VGA installer isn't too hard to handle neither. 
After base system setup you'll be asked which metapackages to pull in. In doubt. just get ubuntu-desktop, and you'll download the latest available builds without having to upgrade the whole system after setup.

Netinstall isos for the win!

---

### Post by coffeecat on 2009-03-26
> **loomsen said:**
> As always, if u have a reasonable internet connection, I'd suggest grabbing the netboot iso:

[http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-amd64/current/images/netboot/)

mini.iso should be what u want.

Already downloaded! Thanks for that. I always prefer a net install. Didn't know it was possible with Ubuntu until I saw your post.

---

### Post by cecilpierce on 2009-03-26
Anybody want to guess ? I'll say 10 hrs, 30 min.

---

### Post by foxy123 on 2009-03-26
> **cecilpierce said:**
> Anybody want to guess ? I'll say 10 hrs, 30 min.

you mean from now?

---

### Post by coffeecat on 2009-03-26
> **coffeecat said:**
> Already downloaded!

That was the 64-bit version. :( Anyone wanting the 32-bit, go here:

[http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/)

---

### Post by cecilpierce on 2009-03-26
foxy123: yes

---

### Post by foxy123 on 2009-03-26
> **cecilpierce said:**
> foxy123: yes

I actually hope for 4-5 hours...

---

### Post by coffeecat on 2009-03-26
Posting from what I assume to be equivalent to the Jaunty Beta, courtesy of this post:

> **loomsen said:**
> As always, if u have a reasonable internet connection, I'd suggest grabbing the netboot iso:

[http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-amd64/current/images/netboot/)

mini.iso should be what u want.

You won't have a graphical installer tool tho... but the VGA installer isn't too hard to handle neither. 
After base system setup you'll be asked which metapackages to pull in. In doubt. just get ubuntu-desktop, and you'll download the latest available builds without having to upgrade the whole system after setup.

Netinstall isos for the win!

So thanks **loomsen** for that.

All pretty painless - took about an hour which is pretty good considering that it has to download everything. You get to choose the mirror appropriate to your country, so that might be a good thing for when the servers get hammered for the beta iso - assuming they're different. **loomsen**'s link is for the 64-bit. If you want the link for the 32-bit, have a look at my earlier post.

The text install is very similar to what you get with the alternate CD, and you can mix and match Ubuntu desktop, Kubuntu desktop, server, samba, Edubuntu, you-name-it at one point.

Looks good so far. Now to see what I can break....

---

### Post by Sillywombat on 2009-03-26
> **foxy123 said:**
> I actually hope for 4-5 hours...


Ill go with 3 to 4 hours. hehe

By the way, will the beta build just show up in [http://cdimage.ubuntu.com/daily/current/]("http://cdimage.ubuntu.com/daily/current/")  ???

---

### Post by zeroandone on 2009-03-26
> **Sillywombat said:**
> Ill go with 3 to 4 hours. hehe

By the way, will the beta build just show up in [http://cdimage.ubuntu.com/daily/current/]("http://cdimage.ubuntu.com/daily/current/")  ???
Looks like it is the beta. I am going to get it now.

---

### Post by Melhisedek on 2009-03-26
I tried the daily build, 32-bit but it said it couldn't install GRUB :/ There was some error so I'm waiting for the beta to get graphical installer

---

### Post by GordonTGopher on 2009-03-26
> **Sillywombat said:**
> Ill go with 3 to 4 hours. hehe

By the way, will the beta build just show up in [http://cdimage.ubuntu.com/daily/current/]("http://cdimage.ubuntu.com/daily/current/")  ???

Don't know, but this page [http://cdimage.ubuntu.com/releases/jaunty/]("http://cdimage.ubuntu.com/releases/jaunty/") will change:P

Gordon

---

### Post by zeroandone on 2009-03-26
> **Melhisedek said:**
> I tried the daily build, 32-bit but it said it couldn't install GRUB :/ There was some error so I'm waiting for the beta to get graphical installer
Oops, better keep waiting.

---

### Post by foxy123 on 2009-03-26
I think it will be here: [http://cdimage.ubuntu.com/releases/jaunty/beta](http://cdimage.ubuntu.com/releases/jaunty/beta) or 
[http://cdimage.ubuntu.com/xubuntu/releases/jaunty/beta](http://cdimage.ubuntu.com/xubuntu/releases/jaunty/beta) for Xubuntu, which I am actually waiting for...

---

### Post by grinias on 2009-03-26
It is here now:

[https://wiki.kubuntu.org/JauntyJackalope/Beta/Kubuntu]("https://wiki.kubuntu.org/JauntyJackalope/Beta/Kubuntu")

---

### Post by andrewabc on 2009-03-26
> **grinias said:**
> It is here now:

[https://wiki.kubuntu.org/JauntyJackalope/Beta/Kubuntu]("https://wiki.kubuntu.org/JauntyJackalope/Beta/Kubuntu")

No it's not. The download link does not work. That is just the preparation for the release.

---

### Post by zeddock on 2009-03-26
Beta source directory just hit. Can't be much longer!

[http://cdimage.ubuntu.com/releases/jaunty/beta/](http://cdimage.ubuntu.com/releases/jaunty/beta/)

zeddock

---

### Post by zeddock on 2009-03-26
Showing on SoftPedia now but nothing under the links!!!!

Soon!

Soon!


zeddock

---

### Post by Enigmatic on 2009-03-26
They seem to be up here: [http://releases.ubuntu.com/jaunty/](http://releases.ubuntu.com/jaunty/)

---

### Post by zeddock on 2009-03-26
Torrent is loaded. No DL movement yet from SoftPedia.
[http://linux.softpedia.com/progDownload/Ubuntu-Jaunty-Jackalope-Download-43130.html](http://linux.softpedia.com/progDownload/Ubuntu-Jaunty-Jackalope-Download-43130.html)

zeddock

---

### Post by tsger on 2009-03-26
> **Enigmatic said:**
> They seem to be up here: [http://releases.ubuntu.com/jaunty/](http://releases.ubuntu.com/jaunty/)

The md5 sums listed there are different from the ones found here:

[http://cdimage.ubuntu.com/releases/jaunty/beta/](http://cdimage.ubuntu.com/releases/jaunty/beta/)

I'll download the file from the "cdimage" url.

---

### Post by Sandsound on 2009-03-26
> **Enigmatic said:**
> They seem to be up here: [http://releases.ubuntu.com/jaunty/](http://releases.ubuntu.com/jaunty/)

Cool 8-)

Downloading with 840 KB/sec.
Ubuntu servers rock :guitar:

---

### Post by dBuster on 2009-03-26
Here is a link with different downloads such as the netbook and even a distro for the ARM processors...

[http://cdimage.ubuntu.com/releases/jaunty/beta/]("http://cdimage.ubuntu.com/releases/jaunty/beta/")

---

### Post by tsger on 2009-03-26
> **Enigmatic said:**
> They seem to be up here: [http://releases.ubuntu.com/jaunty/](http://releases.ubuntu.com/jaunty/)


That is definitely different from the final.  The final beta live dvd looks to be over 4GB in size!  Why on earth is it so big, when all the alpha builds could fit on one cd?

---

### Post by andrewabc on 2009-03-26
> **tsger said:**
> That is definitely different from the final.  The final beta live dvd looks to be over 4GB in size!  Why on earth is it so big, when all the alpha builds could fit on one cd?

I don't see a DVD on there or any files over 700mb.

---

### Post by Basiic on 2009-03-26
> **andrewabc said:**
> I don't see a DVD on there or any files over 700mb.

ubuntu-9.04-beta-dvd-i386.iso                24-Mar-2009 08:17  4.2G
ubuntu-9.04-beta-dvd-amd64.iso               24-Mar-2009 08:10  4.3G

Anyone have any idea why its such a huge file?  There is still no updates through update manager, I am running jaunty alpha 6. :(

---

### Post by dBuster on 2009-03-26
> **andrewabc said:**
> I don't see a DVD on there or any files over 700mb.

If your looking for:

Install/live DVD
UNR USB image
MID USB image
Desktop SD card image

Use this link:  [http://cdimage.ubuntu.com/releases/jaunty/beta/]("http://cdimage.ubuntu.com/releases/jaunty/beta/")

If your looking for:  

Desktop CD
Server install CD
Alternate install CD

Use this link:  [http://releases.ubuntu.com/9.04/]("http://releases.ubuntu.com/9.04/")

---

### Post by tsger on 2009-03-26
> **andrewabc said:**
> I don't see a DVD on there or any files over 700mb.

Look here: [http://cdimage.ubuntu.com/releases/jaunty/beta/](http://cdimage.ubuntu.com/releases/jaunty/beta/)

---

### Post by andrewabc on 2009-03-26
The link that the person quoted showed no DVDs.
That is where confusion came from.

---

### Post by dBuster on 2009-03-26
> **andrewabc said:**
> The link that the person quoted showed no DVDs.
That is where confusion came from.

> If your looking for:

Install/live DVD
UNR USB image
MID USB image
Desktop SD card image

Use this link: [http://cdimage.ubuntu.com/releases/jaunty/beta/](http://cdimage.ubuntu.com/releases/jaunty/beta/)


Hope this clears up any confusion...  If you do not see a link scroll down the list of files are there...

---

### Post by tsger on 2009-03-26
Well, it is strange, on Distrowatch ([http://distrowatch.com/?newsid=05396](http://distrowatch.com/?newsid=05396)) the beta image is 697 MB, so I have no idea why there are DVD images on this site --> [http://cdimage.ubuntu.com/releases/jaunty/beta/](http://cdimage.ubuntu.com/releases/jaunty/beta/). 

Think I'll download from the following Distrowatch link:

[http://mirrors.cat.pdx.edu/ubuntu-releases/9.04/ubuntu-9.04-beta-desktop-i386.iso](http://mirrors.cat.pdx.edu/ubuntu-releases/9.04/ubuntu-9.04-beta-desktop-i386.iso)

---

### Post by Therion on 2009-03-26
DVD downloads for Ubuntu are standard issue: [http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/)

The reason they're so much bigger is, primarily, because they come with several additional language packs installed.

---

### Post by tsger on 2009-03-26
> **Therion said:**
> DVD downloads for Ubuntu are standard issue: [http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/)

The reason they're so much bigger is, primarily, because they come with several additional language packs installed.

Hey, cool, thanks for the explanation!

---

### Post by dBuster on 2009-03-26
> **tsger said:**
> Well, it is strange, on Distrowatch ([http://distrowatch.com/?newsid=05396](http://distrowatch.com/?newsid=05396)) the beta image is 697 MB, so I have no idea why there are DVD images on this site --> [http://cdimage.ubuntu.com/releases/jaunty/beta/](http://cdimage.ubuntu.com/releases/jaunty/beta/). 

Think I'll download from the following Distrowatch link:

[http://mirrors.cat.pdx.edu/ubuntu-releases/9.04/ubuntu-9.04-beta-desktop-i386.iso](http://mirrors.cat.pdx.edu/ubuntu-releases/9.04/ubuntu-9.04-beta-desktop-i386.iso)

My original posting shows both download sites from Ubuntu, one of them being the CD version sub 700mb and then the DVD version link as well....

---

### Post by BGFG on 2009-03-26
Dudes and dudettes, 11:26 in the pm and no updates yet. using the main server. What is up ? ;)

---

### Post by novafluxx on 2009-03-27
I guess this is the beta? I just did an update and no new packages...hmm



Well I hope these sound issues get resolved lol

I had high hopes for the beta, so far its pretty lackluster considering its the final release BEFORE the FINAL release :-)


I'm sure we'll see some updates over the next month though

---

### Post by jocko on 2009-03-27
> **BGFG said:**
> Dudes and dudettes, 11:26 in the pm and no updates yet. using the main server. What is up ? ;)
The reason there are haven't been any updates the last few days is probably because the beta was released yesterday... If you already have jaunty installed and updated you already had every package from the beta a few days ago.
Did you think they were going to release all new (and untested) versions of every package?
alpha/beta/rc are just milestones in the development when certain goals of the development and testing have been reached. There may be some extra work put into making sure the cd images are working properly, so that new testers may join in.
Someone who already use jaunty during it's development will not really notice the transitions between different alphas, beta, release candidate and final release (other than a noticeable decrease in the number of updates for a few days). All the packages that will be part of the next alpha/beta/rc have to be in the repos BEFORE that release, otherwise there would be no way for the users to test them...

---

### Post by taavikko on 2009-03-27
> **novafluxx said:**
> 
I had high hopes for the beta, so far its pretty lackluster considering its the final release BEFORE the FINAL release :-)


Actually there will be a "Release Canditate" a week prior to official release
[https://wiki.ubuntu.com/JauntyReleaseSchedule](https://wiki.ubuntu.com/JauntyReleaseSchedule)

---

### Post by jocko on 2009-03-27
> **novafluxx said:**
> I guess this is the beta? I just did an update and no new packages...hmm



Well I hope these sound issues get resolved lol

I had high hopes for the beta, so far its pretty lackluster considering its the final release BEFORE the FINAL release :-)


I'm sure we'll see some updates over the next month though
There's still the release candidate to look forward to.

What do you mean with the beta being lackluster? compared to a fully updated jaunty installed at one of the alpha stages? You know that *you* are the tester. The packages that were to become part of the beta were in the repos before the beta was officially released (some for only a few days, others for months).
Or do you mean jaunty as a whole seems lackluster compared to intrepid?

---

### Post by novafluxx on 2009-03-27
> **taavikko said:**
> Actually there will be a "Release Canditate" a week prior to official release
[https://wiki.ubuntu.com/JauntyReleaseSchedule](https://wiki.ubuntu.com/JauntyReleaseSchedule)
Thats right! I forgot, sorry!
> **jocko said:**
> There's still the release candidate to look forward to.

What do you mean with the beta being lackluster? compared to a fully updated jaunty installed at one of the alpha stages? You know that *you* are the tester. The packages that were to become part of the beta were in the repos before the beta was officially released (some for only a few days, others for months).
Or do you mean jaunty as a whole seems lackluster compared to intrepid?

Yes, the RC! I totally forgot!

I'm having pretty annoying problems with audio in Jaunty, one being sometimes sounds in pidgin are replaced by static-like "squirts" or bursts, that I didn't have in 8.10, and another that, not being a very good tester, is very difficult for me to describe them, in fact, I did a remote desktop with a buddy to show him [he uses OpenSolaris] because I can't explain it, and it was much easier just showing him.

I go on the assumption that I'm not the only one with these problems, and if I am, they won't fix something for 1 man!

Lackluster was only meant to define my audio issues! Sorry for the confusion.

---

### Post by jocheem67 on 2009-03-27
I had sound-issues, but solved them by removing pulse...
No sound in wine though either ( I like foobar2000 a lot ), I did apply a workaround though by using jack..

---

### Post by maverick340 on 2009-03-27
Beta out , innit ?

---

### Post by taavikko on 2009-03-27
> **maverick340 said:**
> Beta out , innit ?

As everyone always wondering and such, please subscribe to [http://lists.ubuntu.com/mailman/listinfo/ubuntu-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-announce)
To find out

And yes, it's been released.

---

### Post by jocheem67 on 2009-03-27
Downloaded the iso..

I'm in Holland CET

---

### Post by Sillywombat on 2009-03-27
Right, most of the whinners have managed to get their hands on a working beta distro at this point.

So i think im saying for everyone here:
"YeeehaaaaAA!!"

---

