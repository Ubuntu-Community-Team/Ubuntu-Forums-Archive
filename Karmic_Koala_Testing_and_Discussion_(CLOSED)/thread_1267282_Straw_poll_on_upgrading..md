---
title: "Straw poll on upgrading."
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by castrojo on 2009-09-15
People keep just blindly running "apt-get dist-upgrade" for some reason and breaking their karmic installs instead of using "apt-get upgrade". I want to find out why people do this so people stop breaking their computers.

I am working on updating some [documentation](https://wiki.ubuntu.com/UbuntuDevelopment/UsingDevelopmentReleases), so if you could please respond with how and when you upgrade. Do you do it multiple times a day, do you have like a little ritual, or whatever. Thanks!

---

### Post by Vanishing on 2009-09-15
> **whiprush said:**
> People keep just blindly running "apt-get dist-upgrade" for some reason and breaking their karmic installs instead of using "apt-get upgrade". I want to find out why people do this so people stop breaking their computers.

I am working on updating some [documentation](https://wiki.ubuntu.com/UbuntuDevelopment/UsingDevelopmentReleases), so if you could please respond with how and when you upgrade. Do you do it multiple times a day, do you have like a little ritual, or whatever. Thanks!

are you quoting today's update?
well, if thats the case the you will get the borked updates if you do "apt-get udpate".:lolflag:

---

### Post by sena_akada on 2009-09-15
before the nvidia thing i would run aptitude update/aptitude full-upgrade whenever i used the pc

---

### Post by ffi on 2009-09-15
> **whiprush said:**
> People keep just blindly running "apt-get dist-upgrade" for some reason and breaking their karmic installs instead of using "apt-get upgrade". I want to find out why people do this so people stop breaking their computers.

I am working on updating some [documentation](https://wiki.ubuntu.com/UbuntuDevelopment/UsingDevelopmentReleases), so if you could please respond with how and when you upgrade. Do you do it multiple times a day, do you have like a little ritual, or whatever. Thanks!

I always thought this was the preferred method when you upgrade a distribution as you are sort of doing when running a development version

---

### Post by FuturePilot on 2009-09-15
I use Update-Manager to do updates. If it wants to do a Partial Upgrade I open Synaptic and carefully check the changes it wants to make before continuing. If it wants to remove things I know should not be removed I will wait a while and refresh the package lists a few hours later to see if the situation is different. It usually is. This is the way I avoid breakage and it works pretty well. During development cycles I usually check for updates 2 to 3 times a day. Otherwise if it's a stable release I just let Update-Manager do its daily check.

---

### Post by jmmL on 2009-09-15
I run a little script manually, but often multiple times per day during development. Until recently the script used "apt-get upgrade", but I switched over to "aptitude safe-upgrade" within the past 2 months or so. I'd say I've run into less trouble because of it.

Still got bitten by the recent libc6 and nvidia stuff though, and I'm going to hold off updating for the next 48 hours (I'll also be away from the computer!) to allow the ubuntu-boot ppa to settle down as well.

---

### Post by kansasnoob on 2009-09-15
On my normal working machine I update once a day using the Update manager GUI just so it's done and out of the way before I begin working.

On a development distro I may update/upgrade as often as 2 or 3 times a day. As far as using dist-upgrade I'd thought that was the proper way to do things during development, but I'm just a noob so maybe I "heard" wrong.

At this point I'd say I'm still just learning and if I break a development distro I don't sweat it. I just reinstall. Besides, I learn something new every time I reinstall. (For instance I just learned that you can do an OEM install from the live CD, rather than using the alternate.)

I take the "testing only" warning to heart!

OTOH I sometimes kick myself for not properly reporting things, for instance the Live CD eject problem w/Intrepid. I tried to report it before final release but I did a poor job :(

In spite of hours of reading I find that trial and error are often the only way I actually learn. All that aside I think you devs do a great job :)

---

### Post by Schendje on 2009-09-15
I'm new to testing development releases, could someone tell me the difference between the two commands?

I personally boot my testing machine up every few days, and when it says that it has a "Partial upgrade" I let it do it's thing. If I'm being a noob please tell me. :P

---

### Post by castrojo on 2009-09-15
> **Vanishing said:**
> are you quoting today's update?
well, if thats the case the you will get the borked updates if you do "apt-get udpate".

Really? Both initscripts and upstart are held back on 3 of my machines, so I'm not broken (yet anyway).

---

### Post by dinxter on 2009-09-15
update a few times a day, using synaptic to see whats going to happen and if it would be bad :)

---

### Post by dinxter on 2009-09-15
> **whiprush said:**
> Really? Both initscripts and upstart are held back on 3 of my machines, so I'm not broken (yet anyway).

much upstart goodness quick boot stuff is happening, should be ok(ish) now, more on the way no doubt

---

### Post by steeleyuk on 2009-09-15
> **whiprush said:**
> Really? Both initscripts and upstart are held back on 3 of my machines, so I'm not broken (yet anyway).

They were held back on my 64-bit machine, I didn't install them and continued with the remaining updates. It still got borked...

---

### Post by sena_akada on 2009-09-15
is aptitude full-upgrade an ok command to upgrade on alphas?

---

### Post by castrojo on 2009-09-15
> **jmmL said:**
> Still got bitten by the recent libc6 and nvidia stuff though, and I'm going to hold off updating for the next 48 hours (I'll also be away from the computer!) to allow the ubuntu-boot ppa to settle down as well.

Yeah, I think if you're using PPAs, (specifically PPAs that have boot packages) there will always be a high risk of breakage that will require manual intervention.

Surely we can find a way to help prevent the "Oh I just dist-upgraded and my kernels got removed lol" problems though.

---

### Post by zika on 2009-09-15
I prefer sudo apt-get safe-upgrade and resrt to sudo apt-get dist-upgrade only if I think I know what is going on. Synaptic is also a good tool for upgrade but I use it mainly to get information in case I'm not sure what is going on. Changelog is a good place to see what is going on, with the help of Karmic-changes mailing-list. I use Update Manager very rarely. The main reason I use apt-get is that I cann sift through its log-file if I'm not sure what happened. Today even that tool was broken since /dev/shm and /dev/pts were not created so log-file could not be updated...
It is important to notice that today's mess was not due to a partial-upgrade ...

---

### Post by Vanishing on 2009-09-15
> **whiprush said:**
> Really? Both initscripts and upstart are held back on 3 of my machines, so I'm not broken (yet anyway).

not for me...
well.only upstart is held back, but with a normal update, the system broke, however i think it has something to do with the ubuntu-boot ppa...
my bad..:lolflag:

---

### Post by zika on 2009-09-15
> **whiprush said:**
> Really? Both initscripts and upstart are held back on 3 of my machines, so I'm not broken (yet anyway).You were lucky not to do upgrade before they were kept back ... Before that they were "legal" and that intermediate version of upstart made a mess. This new version that was kept back is OK, hopefully ...

---

### Post by zika on 2009-09-15
> **Vanishing said:**
> not for me...
well.only upstart is held back, but with a normal update, the system broke, however i think it has something to do with the ubuntu-boot ppa...
my bad..:lolflag:No, the mess happened also to us that did not use that ppa.

---

### Post by ikt on 2009-09-15
> **whiprush said:**
> People keep just blindly running "apt-get dist-upgrade" for some reason and breaking their karmic installs instead of using "apt-get upgrade". I want to find out why people do this so people stop breaking their computers.

Is this the cause of all the karmic installs breaking?

usually use update-manager, when it wants to do a partial upgrade I let it.

---

### Post by kansasnoob on 2009-09-15
> **whiprush said:**
> Really? Both initscripts and upstart are held back on 3 of my machines, so I'm not broken (yet anyway).

One of the two finally upgraded for me, I think upstart (maybe 30 minutes ago), but I'm still broke - I just freeze at kdm.

Of course I'm running multiple desktops on the same distro, so that may in itself be a problem at this point.

To be specific I'm playing with E17 and LXDE, but since gdm provided no gui to change sessions during boot I switched to kdm ............ so I can't say mine is in any way a "typical" install.

---

### Post by lisati on 2009-09-15
> **whiprush said:**
> People keep just blindly running "apt-get dist-upgrade" for some reason and breaking their karmic installs instead of using "apt-get upgrade". I want to find out why people do this so people stop breaking their computers.


Perhaps semantics play a part in the potential for confusion and/or disaster. If I didn't know better (mainly from browsing these forums) I might have mistakenly thought that "apt-get upgrade" does what "apt-get dist-upgrade" does.

---

### Post by psyke83 on 2009-09-15
> **whiprush said:**
> People keep just blindly running "apt-get dist-upgrade" for some reason and breaking their karmic installs instead of using "apt-get upgrade". I want to find out why people do this so people stop breaking their computers.

I am working on updating some [documentation](https://wiki.ubuntu.com/UbuntuDevelopment/UsingDevelopmentReleases), so if you could please respond with how and when you upgrade. Do you do it multiple times a day, do you have like a little ritual, or whatever. Thanks!

This is a serious problem, but I believe that the Ubuntu developers (specifically, whoever programmed Update Manager) are also Partially* to blame for this behaviour.

When the repository is in an inconsistent state, Update Manager will warn users that a full upgrade is not possible, and will offer two dialog choices - Partial Upgrade or Cancel (that's my vague recollection, I'm not on Ubuntu at the moment so correct me if I'm wrong). This implies that there is only the choice to do a Partial Upgrade or nothing at all, when in fact it's possible to choose cancel, and then upgrade some packages whilst holding back packages that have pending dependencies. 

From this choice, users tend to blindly perform a "Partial Upgrade" without truly understanding that it can (and usually does) break their system. This actually seems logical if you take a step back - a "Partial Upgrade" implies that it will upgrade only parts of the system. Shouldn't a Partial Upgrade therefore equate to a "apt-get upgrade" or "aptitude safe-upgrade"? It's a linguistic problem.

*Pun intended ;)

---

### Post by dinxter on 2009-09-15
[quote=whiprush;7954130]
Surely we can find a way to help prevent the "Oh I just dist-upgraded and my kernels got removed lol" problems though./quote]
i'm not sure, 
apt-get dist-upgrade uses 'smart' upgrades so conflict resolution could easily remove something key, especially if packages are out of sync as they often are in development
but apt-get upgrade wont remove anything even if it is the 'right' thing to do.
perhaps running apt-get dist-upgrade --simulate before running apt-get dist-upgrade proper is sane, in the end you still need to know whats safe to remove and what isnt though
[EDIT] Bloomin' quotes :)

---

### Post by castrojo on 2009-09-15
> **zika said:**
> You were lucky not to do upgrade before they were kept back ... Before that they were "legal" and that intermediate version of upstart made a mess. This new version that was kept back is OK, hopefully ...

One of mine is properly hosed now, so between both of our machines we probably witnessed the entire cycle. Prior to this I've been rebooting this one laptop over the last few hours and it was fine until just now. 

* Makes explosion sounds *

---

### Post by FuturePilot on 2009-09-15
> **zika said:**
> I prefer sudo apt-get safe-upgrade and resrt to sudo apt-get dist-upgrade only if I think I know what is going on. Synaptic is also a good tool for upgrade but I use it mainly to get information in case I'm not sure what is going on. Changelog is a good place to see what is going on, with the help of Karmic-changes mailing-list. I use Update Manager very rarely. The main reason I use apt-get is that I cann sift through its log-file if I'm not sure what happened. Today even that tool was broken since /dev/shm and /dev/pts were not created so log-file could not be updated...
It is important to notice that today's mess was not due to a partial-upgrade ...

Do you mean /var/log/dpkg.log? That is written to no matter what method you use. apt-get is just a front end to dpkg, so is synaptic, aptitude, update-manager, etc.

---

### Post by sena_akada on 2009-09-15
is aptitude full-upgrade safe or not? :/

---

### Post by zika on 2009-09-15
> **FuturePilot said:**
> Do you mean /var/log/dpkg.log? That is written to no matter what method you use. apt-get is just a front end to dpkg, so is synaptic, aptitude, update-manager, etc.You might be right. I'll investigate that a little bit more. I might have been mislead all the time ... Good point and a relief ...
P.S. No, I'm using /var/log/aptitude ...

---

### Post by Keyper7 on 2009-09-15
> **whiprush said:**
> People keep just blindly running "apt-get dist-upgrade" for some reason and breaking their karmic installs instead of using "apt-get upgrade". I want to find out why people do this so people stop breaking their computers.

I'm a good candidate to answer that.

My personal theory, based on personal experience: the expression "partial upgrade" is *awfully anti-intuitive*.

I only recently started using the graphical update manager instead of apt-get directly and had no idea that "partial upgrade" was the equivalent of dist-upgrade. When I saw the warning, I simply assumed that some dependencies weren't being satisfied (due to an incomplete repository update or whatever) and the partial upgrade would only install the consistent part. Furthermore, the manager does not hesitate in recommending the partial upgrade (in fact, it almost orders it), giving the false impression that it's the safest alternative.

---

### Post by castrojo on 2009-09-15
> **Keyper7 said:**
> I'm a good candidate to answer that.
My personal theory, based on personal experience: the expression "partial upgrade" is *awfully anti-intuitive*.

I'll bring this up to someone, at a minimum we could do a better job education about what exactly that button does.

---

### Post by ljrmorgan on 2009-09-15
I think perhaps if you are going to say that people shouldn't use dist-upgrade, you should maybe explain what's so wrong with it. A few people have said they use it and aren't sure why they shouldn't.

I personally fall into the "I thought we were meant to" camp too.

---

### Post by sena_akada on 2009-09-15
[img]http://jamie-online.com/random-jamz/wp-content/uploads/2009/06/facepalm.jpg[/img]

---

### Post by kansasnoob on 2009-09-15
I'd say at this point, with a smile on my face, we have many different habits!

Now, let's all smile :)

I'm curious what todays daily release will render :confused:

---

### Post by kansasnoob on 2009-09-15
@sena_akada,

That was the best laugh I've had all day!

---

### Post by steeleyuk on 2009-09-15
> **kansasnoob said:**
> I'd say at this point, with a smile on my face, we have many different habits!

Now, let's all smile :)

I'm curious what todays daily release will render :confused:

A broken system no doubt. :P

---

### Post by qamelian on 2009-09-15
> **FuturePilot said:**
> I use Update-Manager to do updates. If it wants to do a Partial Upgrade I open Synaptic and carefully check the changes it wants to make before continuing. If it wants to remove things I know should not be removed I will wait a while and refresh the package lists a few hours later to see if the situation is different. It usually is. This is the way I avoid breakage and it works pretty well. During development cycles I usually check for updates 2 to 3 times a day. Otherwise if it's a stable release I just let Update-Manager do its daily check.

I do the same. It's sane, and almost guaranteed safe. I trust the update manager enough to know that if it doesn't want to upgrade something there is a darn good reason and I should take a closer look before proceeding. It's amazing how much time I spend not fixing my test box as a result! :)

---

### Post by kansasnoob on 2009-09-15
> **ljrmorgan said:**
> I think perhaps if you are going to say that people shouldn't use dist-upgrade, you should maybe explain what's so wrong with it. A few people have said they use it and aren't sure why they shouldn't.

I personally fall into the "I thought we were meant to" camp too.

+1!

I never use it on my normal working desktop, I only use the GUI, but I'd been taught that "dist-upgrade" was the right thing to do on a development distro.

---

### Post by NCLI on 2009-09-15
I fall into the "I wonder what will happen if I press this button" category :)

Sometimes I get cool new features, and sometimes my machine refuses to boot. Exciting!! :popcorn:

---

### Post by FuturePilot on 2009-09-15
> **qamelian said:**
>  It's amazing how much time I spend not fixing my test box as a result! :)

So true :)

---

### Post by kansasnoob on 2009-09-15
> **steeleyuk said:**
> A broken system no doubt. :P

I must see though. We're looking at poor updating behavior as the cause.

Is that the cause?

And I use so many CD's one more is diddly to me!

---

### Post by MKdx on 2009-09-15
One a stable release, once a week.

On a development one, I refresh the packages list few times a day. However, I do update every other day, or depending on what the updated packages are.

Update-manager is not bad for partial-upgrade, if you click [details] on the interface, it will list the packages to be removed first, followed by updates and new additions.

It would probably be better to highlight the removed packages and make this part more visible.. somehow.

---

### Post by kansasnoob on 2009-09-15
Downloading the daily build now, slowly (weird since I have a 5000 kbps connection), but I also see it's oversize which means I'll have to use a DVD which costs me 50 cents more!

Note to self: Must buy larger quantities of DVD's!

---

### Post by Schendje on 2009-09-15
> **kansasnoob said:**
> Downloading the daily build now, slowly (weird since I have a 5000 kbps connection), but I also see it's oversize which means I'll have to use a DVD which costs me 50 cents more!

Note to self: Must buy larger quantities of DVD's!

USB sticks not working? Way better than burning discs all the time. :guitar:

---

### Post by joey-elijah on 2009-09-15
Regarding the "partial upgrade" thing - can i think this thread for enlightening me! 

As has been said - it's name is really quite counter intuitive. I always assumed that a partial upgrade was better than no upgrade at all...

---

### Post by kansasnoob on 2009-09-15
> **joey-elijah said:**
> Regarding the "partial upgrade" thing - can i think this thread for enlightening me! 

As has been said - it's name is really quite counter intuitive. I always assumed that a partial upgrade was better than no upgrade at all...

On my actual work machine I'd never do a partial upgrade. But I don't think I've ever been offered one.

I'll say this, I discovered Gutsy through the original gOS and I found that the Gnome desktop best suited me. We all differ there, that's why there are many official and unofficial forks of Ubuntu.

Now, from Gutsy I jumped into Hardy and pulse audio just kept screwing with me! Really bad for several months, but it finally got straightened out.

Intrepid had lots of problems for me, ranging from poor camera support to drive recognition, so I skipped it - I stayed with Hardy.

Now, Jaunty was a keeper! With a few tweaks Jaunty was every bit as good as (and better than) Gutsy. No doubt the desire is to make every release truly better than the last, but just look at what's happening!

#1: hal is being deprecated! 
#2: We're on the bleeding edge with Gnome!
#3: Grub-2 is going mainstream!
#4: Xorg just keeps getting better!

Lots of changes! And if Karmic doesn't suit me I can stay with Jaunty as my main desktop and try to shape the next version!

When was the last time you helped to shape what happened with Win?

---

### Post by kansasnoob on 2009-09-15
> **Schendje said:**
> USB sticks not working? Way better than burning discs all the time. :guitar:

I could do USB but most people will still install using a Live CD, so I test using CD's.

Plastic is cheap! And I shred and recycle.

---

### Post by inportb on 2009-09-15
I dist-upgrade because I feel like it. Is that a good-enough reason? :P
Actually, I just want to make sure I get all the updates, because things get held back when other packages need to be installed/removed. And yeah, I got hit by the borked update today; it was fun! What, people didn't enjoy it?

---

### Post by kansasnoob on 2009-09-15
Well that was fun!

Manual partitioning fails on the daily CD!

I'll click on a partition, in this case either sda10 or sda11, and they seem to take the changes, but then nothing happens!

So, my take only, todays updates broke everything!

And, yes, I did check md5sums and I also ran the "check cd for defects" thing and all were good!

IMHO this had less to do with personal procedure than it did totally crappy updates!

Oops! Did I say that?

Somebody messed up.

---

### Post by psyke83 on 2009-09-15
> **kansasnoob said:**
> Well that was fun!

Manual partitioning fails on the daily CD!

I'll click on a partition, in this case either sda10 or sda11, and they seem to take the changes, but then nothing happens!

So, my take only, todays updates broke everything!

And, yes, I did check md5sums and I also ran the "check cd for defects" thing and all were good!

IMHO this had less to do with personal procedure than it did totally crappy updates!

Oops! Did I say that?

Somebody messed up.

The same advice applies: [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-September/009331.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-September/009331.html)

---

### Post by ezsit on 2009-09-15
kansasnoob wrote:
> Plastic is cheap! And I shred and recycle.

AFAIK, shredded bits of plastic are way to small for most recycling plants to catch, those pieces fall right through the sorting machines and wind up in the regular trash anyways. It's a good thought, but probably doing no real good.

---

### Post by ranch hand on 2009-09-15
I have four 32bit 9.10 versions, five 64bit versions.

One of my 64 bit versions has not booted for a week.  I finally got chroot access and did an apt-get dist-upgrade.

The reason for that was that I had been poking around in the busted bugger for a while trying to get it to work and kept coming up with files missing or empty.

apt-get gave me a figure of over 70 partially installed OR deleted files.

I figured that a dist-upgrade would be the easiest way to at least get the right files on board.

I download and install (if possible) a clean install of each A.

I also dist-upgrade  a 9.04 install to 9.10.

This is my only use of dist-upgrade.

On my production drive all changes in release are done with a clean install and filled in by /home backup - directory by directory or even file by file

---

### Post by kansasnoob on 2009-09-15
> **psyke83 said:**
> The same advice applies: [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-September/009331.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-September/009331.html)

I totally agree! I wasn't complaining, Just saying that it's NOT just due to updating/upgrading technique.

I actually enjoy the dev process and maybe, just maybe, some day I'll be able to actually help.

---

### Post by psyke83 on 2009-09-15
> **kansasnoob said:**
> I could do USB but most people will still install using a Live CD, so I test using CD's.

Plastic is cheap! And I shred and recycle.

Is CD-RW/DVD+/-RW media restricted in certain countries? That's a much more efficient form of recycling, too.

---

### Post by kansasnoob on 2009-09-15
> **ezsit said:**
> kansasnoob wrote:


AFAIK, shredded bits of plastic are way to small for most recycling plants to catch, those pieces fall right through the sorting machines and wind up in the regular trash anyways. It's a good thought, but probably doing no real good.

I know better, I actually worked at a smelting facility!

We used to hear the same BS about aluminum! IE: it costs more to recycle an aluminum can than a new can costs!

Now it's: "it costs more to produce ethanol than it saves"!

And FTM I don't shred the discs that have no personal data on them, they just go in the bin as a full coaster. I doubt Shuttleworth encrypts his financial info on every copy of Ubuntu :P

---

### Post by trulan on 2009-09-15
Wow!  How did both my machines survive the past few days?  But they did, I only had one 'I can't boot' go-round between the real-time kernel and the nvidia drivers, and even then it still booted on the generic kernel.  Other than that I have had no boot troubles.  I have stayed away from the boot ppa.

I update once a day, every morning.  I use update manager.  When it recommends a partial upgrade I very carefully check what it wants to remove.  I think I let it do it twice.  And every now and then I go into Synaptic and click on the 'residual configs' button - that way I can check if the packages it removed can be reinstalled.  So far only a handful have been permanently exiled.

---

### Post by psyke83 on 2009-09-15
> **kansasnoob said:**
> I totally agree! I wasn't complaining, Just saying that it's NOT just due to updating/upgrading technique.

I actually enjoy the dev process and maybe, just maybe, some day I'll be able to actually help.

Right, but this is a fairly rare case. Lots of the packages have been updated with boot improvement in mind, and obviously something went awry. It's understandable when you consider that lots of pieces are getting changed simultaneously.

On the other hand, Partial Upgrades cause all kinds of havoc for users on a regular basis.

---

### Post by kansasnoob on 2009-09-15
> **psyke83 said:**
> Is CD-RW/DVD+/-RW media restricted in certain countries? That's a much more efficient form of recycling, too.

I probably should use RW discs, but I simply find it to be one more thing to keep on hand.

I seldom use DVD's, but I hand out a lot of CD's with data that can be read by Works, Open Office, etc. I think the last batch cost me about 16 cents per disc.

Since it always involves someone else's data I couldn't just write over someone else's data, because any amateur forensic sleuth could dig up the previous data.

---

### Post by kansasnoob on 2009-09-15
> **psyke83 said:**
> Right, but this is a fairly rare case. Lots of the packages have been updated with boot improvement in mind, and obviously something went awry. It's understandable when you consider that lots of pieces are getting changed simultaneously.

On the other hand, Partial Upgrades cause all kinds of havoc for users on a regular basis.

And that's why Karmic says "for testing purposes only"!

As I said I'm not complaining. I just don't think we can nail this down to updating technique.

---

### Post by psyke83 on 2009-09-15
> **kansasnoob said:**
> And that's why Karmic says "for testing purposes only"!

As I said I'm not complaining. I just don't think we can nail this down to updating technique.

Don't worry, I didn't consider your post to be a complaint in any form ;).

Karmic is for testing purposes indeed, and it seems that whiprush wants to find out why people aren't following the "correct" (or safest) testing procedure with regards to upgrading.

---

### Post by ronacc on 2009-09-15
I update at least twice a day using various methods , apt-get , update manager and synaptic as strikes my fancy at the moment, if something wants to do a partial upgrade or dist-upgrade , I carefully check what it wants to do will be before I proceed .

---

### Post by ayates on 2009-09-15
> **zika said:**
> I prefer sudo apt-get safe-upgrade and resrt to sudo apt-get dist-upgrade only if I think I know what is going on. Synaptic is also a good tool for upgrade but I use it mainly to get information in case I'm not sure what is going on. Changelog is a good place to see what is going on, with the help of Karmic-changes mailing-list. I use Update Manager very rarely. The main reason I use apt-get is that I cann sift through its log-file if I'm not sure what happened. Today even that tool was broken since /dev/shm and /dev/pts were not created so log-file could not be updated...
It is important to notice that today's mess was not due to a partial-upgrade ...

This is the way I normally do it. If something looks fishy, I  try to install the packages individually to see what's holding things up.

---

### Post by Gourgi on 2009-09-15
i _never_ do a partial/dist-upgrade! 
i install what is to be installed and then check the held-back packages,read their changelogs,search this forum and mailing lists for new arriving packages and the final decide if i upgrade the rest or wait.
It is a bit time-consuming procedure but i indeed learned the "dist-upgrade" lesson from Hardy's development times :-D
After a couple of development releases participation you get some experience at this hold-back situations.

As for todays updates, in my case i tried to do a regular apt-get update but apt was broken (or dbus was not running?? )
```
Failed to open connection to "system" message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
E: Problem executing scripts APT::Update::Post-Invoke-Success '/usr/bin/dbus-send --system --dest=org.debian.apt --type=signal /org/debian/apt org.debian.apt.CacheChanged'
E: Sub-process returned an error code
```

so a gave (the great) ```
aptitude update && aptitude safe-upgrade
``` which also lead me to a broken system :-S.

Time is my friend, i'll wait ... ;)

---

### Post by xebian on 2009-09-15
WOW.  Blaming it on the package manager.   If the package is bad, it will be bad no matter how you upgraded.  APT is just doing what you set in rules.  GIGO.

---

### Post by andrewabc on 2009-09-15
> **whiprush said:**
> I'll bring this up to someone, at a minimum we could do a better job education about what exactly that button does.

About partial upgrade, I've been testing ubuntu testing versions for more than a year (started with gutsy). And I thought it was known that when testing, if you get a "partial upgrade" wait a day or two and see if it goes away, and check forum to see if other people have same problem. "Partial upgrade" has the potential to break the OS, more often than non partial upgrade updates. Although partial upgrade is needed when a package gets renamed/removed.

Before I read this thread I had no idea people were frequently manually going into command line and inputting distro upgrade command. I thought most people used update manager, and occasional synaptic for partial upgrade.

I currently don't have karmic installed anywheres, as jaunty works fine on my computers, but will be putting it on the computers once released. For past several releases I had ubuntu+1 installed somewheres.

> **kansasnoob said:**
> I could do USB but most people will still install using a Live CD, so I test using CD's.

Plastic is cheap! And I shred and recycle.
When I download new alpha or whatever, I burn to cd-rw, and to liveusb as liveusb is much faster/responsive. But I test livecd as liveusb does not work on one computer. I install from livecd.

I have currently have cd-rw with ubuntu:
-32bit jaunty (installed on 2002 computer)
-64bit jaunty (installed on newest computer)
-kubuntu/xubuntu jaunty (never installed, but keep for safe keeping and to show off if needed)
-whatever latest dev build (alpha/beta/rc).

USE CD-RW! Buy a 10 pack and it will hold all the distros (rescue cds, antivirus livecds) you need. Burning to cd-r is pointless as it is out of date 6 months later and will be tossed out. I have 6.06 burned to cd-r. Useless now, although I might put it in to see what it was like way back when.

---

### Post by dinxter on 2009-09-16
it would probably be simpler if there was some sort of meta package, like ubuntu-minimal, ubuntu-desktop, etc that depended on the bare essentials that shouldnt be removed. eg, ubuntu-essential, depends on linux, udev, and whatever else. at least then you could give advice like, "dist-upgrade will do what you want as long as you never remove ubuntu-essential". easier than people having to know what packages need to always be prevented from removal or tears will result.
unfortunately the Priority: required tag includes a lot of packages that i wouldnt really consider essential

[EDIT] i know theres supposed to be a dpkg 'essential' tag but i dont see anything using it, maybe someone else can shed some light

[EDITEDIT] ah, its Essential: yes, but it only covers a few packages, not a full set that users would consider essential 
$apt-cache dumpavail|grep  -B 5 "Essential: yes"|grep Package

---

### Post by mpsii on 2009-09-16
update-manager -d for the win!

---

### Post by dinxter on 2009-09-16
looks like ubuntu-minimal is the package designed to do what i was talking about before

Package: ubuntu-minimal
Description: Minimal core of Ubuntu
 This package depends on all of the packages in the Ubuntu minimal system,
 that is a functional command-line system with the following capabilities:  
- Boot
  - Detect hardware
  - Connect to a network
  - Install packages
  - Perform basic diagnostics

unfortunately it'll happily let you strip out your kernel, probably a bug if anything, theres maybe one or two more dependencies that would ensure a recoverable system if ubuntu-minimal isnt removed though

---

### Post by slakkie on 2009-09-16
> **dinxter said:**
> looks like ubuntu-minimal is the package designed to do what i was talking about before

Package: ubuntu-minimal
Description: Minimal core of Ubuntu
 This package depends on all of the packages in the Ubuntu minimal system,
 that is a functional command-line system with the following capabilities:  
- Boot
  - Detect hardware
  - Connect to a network
  - Install packages
  - Perform basic diagnostics

unfortunately it'll happily let you strip out your kernel, probably a bug if anything, theres maybe one or two more dependencies that would ensure a recoverable system if ubuntu-minimal isnt removed though

AFAIK if you want to remove a running kernel you get like a zillion warning messages. If people ignore that.. ey.. their beef.. 

[http://pb.opperschaap.net/~wesleys/ubuntu_old_releases/ubuntu_eol_upgrade_kernel_warning.png](http://pb.opperschaap.net/~wesleys/ubuntu_old_releases/ubuntu_eol_upgrade_kernel_warning.png)

Eitherway, my way of upgrading:

```

purge_pkg () {
        sudo aptitude purge $(dpkg -l | grep '^rc' | awk '{print $2}')
        sudo aptitude clean
}

apt_update () {
        local date_stamp=$(stat -c "%Z" /var/cache/apt/pkgcache.bin)
        local now=$(date "+%s")
        now=$((now - 3600))
        [ $date_stamp -lt $now ] || [ -n "$1" ] && sudo aptitude update && sudo apt-file update
}


safe_upgrade () {
        apt_update
        sudo aptitude safe-upgrade && purge_pkg
}

```

---

### Post by dinxter on 2009-09-16
a quick look suggests that if you never remove linux and ubuntu-minimal then you should have some sort of usefully bootable system (aside from bugs). someone might want to look at that in more detail but if your looking for a wiki advice entry whiprush then maybe "never remove these!" would be the one :)

---

### Post by psyke83 on 2009-09-16
> **dinxter said:**
> a quick look suggests that if you never remove linux and ubuntu-minimal then you should have some sort of usefully bootable system (aside from bugs). someone might want to look at that in more detail but if your looking for a wiki advice entry whiprush then maybe "never remove these!" would be the one :)

I don't think it's a perfect safety net like you seem to believe. Try to remove xserver-xorg-video-vesa and xserver-xorg-video-{your driver}.

I don't think that will remove the ubuntu-minimal metapackage, but you'll now have to re-define "usefully bootable" as "it can only boot to a command prompt". If you also remove any packages that are required for networking, then it could be difficult to repair.

My suggestion would be to make the description of Partial Upgrades better explained, and much more difficult to perform in Update Manager.

In apt-get, make sure that when a user does a "dist-upgrade" which requires removal of packages, the default question of whether you wish to continue is "No". Perhaps add some text which warns that during the development process, packages should not be removed unless you have verified that they are no longer needed. You could even force users to manually type "Yes, I understand" (and we could revert apt-get to the more permissive behaviour for the final release).

---

### Post by dinxter on 2009-09-16
> **psyke83 said:**
> I don't think it's a perfect safety net like you seem to believe. Try to remove xserver-xorg-video-vesa and xserver-xorg-video-{your driver}.

oh trust me i know its no safety net! but although xorg packages remove i was talking in terms of the goal of ubuntu-minimal, to get you to a recovery console and let you fix things and install packages. this doesnt require xorg, but for reasons i dont know ubuntu-minimal doesnt require a linux-image. so keeping those 2 packages should avoid the complete bedraggling of your system on a 'smart' upgrade

---

### Post by Sophont on 2009-09-16
sudo aptitude safe-upgrade - several times a week - for any non-trivial update set I'll look at this forum first.

I wait out partial updates.

Plus I have a second Karmic in VB that I upgrade first to see if it's safe. :-)

---

### Post by bumanie on 2009-09-16
I have not read every post here, but the original premise that many people are doing xxx...dist-upgrade and breaking karmic, does not apply to me. I never do a dist-upgrade, but my karmic install is broken (only ever do sudo apt-get update && sudo apt-get upgrade). This is the last error message I am getting

> init: unable to connect to the system bus: Failed to  connect to socket /var/run/dbus/system_bus_socket: No such file or directory

Before that, I had a frozen desktop, dead keyboard and mouse and grub 1.97 beta 3 did not install, nor did apic. I have run another update via tty1, but can't get past the above error, because I have no idea what it means.

---

### Post by gmc on 2009-09-16
> **kansasnoob said:**
> **And that's why Karmic says "for testing purposes only"!**

Uh, that should read "for testing (your patience) purposes only" with yesterday's *breakage*, I got more than my money's worth... :-)

G

---

### Post by ruik on 2009-09-16
I always use aptitude safe-upgrade.

---

### Post by Paqman on 2009-09-16
I do the same as several others here:
[LIST]
[*]If all seems normal, let Update Manager do it's thing.
[*]If the Partial Upgrade rears it's ugly head, open Synaptic and see wht it recommends
[/LIST]

This is almost always enough to get the update done without a visit from the bork fairies.

I've always found the idea of "partial upgrade" to sound inherently unstable to me. After all, if all the dependencies were satisfied, the package manager wouldn't be complaining. However, I can understand why some people have assumed "partial > none"

Maybe just a change of terminology would help? How many people would run an "Incomplete Upgrade" or even an "Unstable Upgrade"?

---

### Post by Sophont on 2009-09-17
> **Paqman said:**
> 
Maybe just a change of terminology would help? How many people would run an "Incomplete Upgrade" or even an "Unstable Upgrade"?

"Incomplete Upgrade" is a great replacement for "Partial Upgrade".
That would clearly tell people to wait unless they know what they are doing.

File a bug with this proposal.

---

### Post by Keyper7 on 2009-09-17
> **Paqman said:**
> I've always found the idea of "partial upgrade" to sound inherently unstable to me.

For me it's the opposite. It sounded like UM was saying "hey, installing everything is a bad idea, so I'll install only the part that will certainly cause no problems".

[QUOTE=Sophont]"Incomplete Upgrade" is a great replacement for "Partial Upgrade".
That would clearly tell people to wait unless they know what they are doing.[/QUOTE]

I think "incomplete" suffers from the same problem.

---

### Post by psyke83 on 2009-09-17
> **Keyper7 said:**
> For me it's the opposite. It sounded like UM was saying "hey, installing everything is a bad idea, so I'll install only the part that will certainly cause no problems".

I think "incomplete" suffers from the same problem.

Yes, I agree. In my opinion, "Partial Upgrade" should become the equivalent of "apt-get upgrade" or "aptitude safe-upgrade".

Additionally, the way that Update Manager pops a dialog offering a choice of "Partial Upgrade" (in its current form) or "Cancel" is counter-intuitive; users should not even get prompted to perform an unsafe operation so easily.

---

### Post by DougieFresh4U on 2009-09-17
I always use 'aptitude upgrade' then 'aptitude dist-upgrade'.
If it wants to remove something, I abort and check the packages out in 'Synaptic' that it wants to remove before continuing on.
I never use 'update manager' or 'Synaptic' for updating. I feel that I have more control over what is happening using 'terminal'.
Sadly, I missed the 'borked' drama. (sic)

---

### Post by infamousrev on 2009-09-17
> **bumanie said:**
> I have not read every post here, but the original premise that many people are doing xxx...dist-upgrade and breaking karmic, does not apply to me. I never do a dist-upgrade, but my karmic install is broken (only ever do sudo apt-get update && sudo apt-get upgrade). This is the last error message I am getting

init: unable to connect to the system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

Before that, I had a frozen desktop, dead keyboard and mouse and grub 1.97 beta 3 did not install, nor did apic. I have run another update via tty1, but can't get past the above error, because I have no idea what it means.



I had the exact same error, here is how I fixed it.

My guess is your trying to upgrade from a chroot like this

mount /dev/disk /mnt
mount --bind /dev /mnt/dev
mount --bind /dev/pts /mnt/dev/pts
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
chroot /mnt
aptitude update
aptitude full-upgrade


However this will fail because the upgrade assumes dbus is running and will look in the directory /var/run for it.

This solved my issue:

mount /dev/disk /mnt
mount --bind /dev /mnt/dev
mount --bind /dev/pts /mnt/dev/pts
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
**mount --bind /var/run /mnt/var/run**
chroot /mnt
aptitude update
aptitude full-upgrade

---

### Post by zika on 2009-09-17
For example, what is the desired action on this result of **sudo aptitude safe-upgrade**```
Current status: 2 updates [+1].
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Resolving dependencies...
Resolving dependencies...
Resolving dependencies...
Resolving dependencies...
Resolving dependencies...
Resolving dependencies...
Resolving dependencies...
Resolving dependencies...
Resolving dependencies...
Resolving dependencies...
Resolving dependencies...
Resolving dependencies...
Resolving dependencies...
Resolving dependencies...
Resolving dependencies...
Resolving dependencies...
The following packages have unmet dependencies:
  erlang-base-hipe: Conflicts: erlang-base but 1:13.b.1-dfsg-2 is installed.
  erlang-base: Conflicts: erlang-base-hipe but 1:13.b.1-dfsg-2 is to be installed.

```...?

At the same time **sudo apt-get upgrade** gives```
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  couchdb
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

``` ...

So much about **safe** ...

---

### Post by psyke83 on 2009-09-17
> **zika said:**
> So much about **safe** ...

What was unsafe from that result? It refused to upgrade packages due to conflicts.

---

### Post by zika on 2009-09-17
> **psyke83 said:**
> What was unsafe from that result? It refused to upgrade packages due to conflicts.Yes, You are right, and I am happy about that but I did not like the way it did that. It looked to me at the first moment that database, or whatever is borked and that this is a sign of it dying. I'm glad I was wrong... Sorry.

EDIT:Good example of ambiguity with different installation tools is evident on my machine at this moment:

1. **sudo aptitude safe-upgrade** gives```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Resolving dependencies...
The following NEW packages will be installed:
  ubuntu-xsplash-artwork{a} 
The following packages will be REMOVED:
  couchdb{u} 
The following packages will be upgraded:
  desktopcouch firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support gdm gstreamer0.10-alsa gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-tools gstreamer0.10-x libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 python-desktopcouch python-desktopcouch-records python-gst0.10 
  python-ubuntuone-client ubuntuone-client ubuntuone-client-gnome xsplash 
20 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 5410kB of archives. After unpacking 639kB will be used.
Do you want to continue? [Y/n/?] n
Abort.
```2. **sudo apt-get upgrade** gives```
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gdm xsplash
The following packages will be upgraded:
  desktopcouch firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support gstreamer0.10-alsa gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-tools gstreamer0.10-x libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 python-desktopcouch python-desktopcouch-records python-gst0.10
  python-ubuntuone-client ubuntuone-client ubuntuone-client-gnome
18 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 4106kB of archives.
After this operation, 16.4kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```3. **update-manager** does not offer any packages to be removed or kept back
4. **synaptic** does not offer any packages to be removed or kept back

What is a user to do in such a situation? Should couchdb be removed (as suggested in 1.) or not ...? Should gdm and xsplash be upgraded or not ... (in 2. it is suggested that they are kept back ...)

---

### Post by seeker5528 on 2009-09-17
> **zika said:**
> 
What is a user to do in such a situation? Should couchdb be removed (as suggested in 1.) or not ...? Should gdm and xsplash be upgraded or not ... (in 2. it is suggested that they are kept back ...)

Those are not suggestions, those are what you are being told will happen if you proceed.

> 4. **synaptic** does not offer any packages to be removed or kept back

If you do the Synaptic equivalent of 'apt-get upgrade' the result should be exactly the same. If you do the Synaptic equivalent of 'apt-get dist-upgrade' results may not necessarily be identical with 'apt-get dist-upgrade' every time, but you get the same type of an upgrade.

If I remember correctly the default-upgrade is the Synaptic equivalent of upgrade and the smart-upgrade is the Synaptic equivalent of dist-upgrade.

You can choose the type of upgrade you want Synaptic to do on the 'system --> preferences' menu.

Personally I use Synaptic all the time unless I have to work around something that requires some type of apt-get options to be given at the command line or can't start an xsession for some reason or another. I almost never tell it to select all the packages, preferring to individually select packages or small groups of related packages, so if dependency resolution fails I see it right away and move to the next package/group of packages and if I don't like the additional changes I can say 'screw that' right away and come back to it later to investigate the situation more after getting other updates.

Synaptic gives you an item on the package menu for downloading the change log for package that is selected in the main window. If you choose (on the 'settings --> preferences' menu) to view the package information in the main window, you have quick access to dependencies, dependents, installed files, etc....

Later, Seeker

---

### Post by Amaranth on 2009-09-17
> **FuturePilot said:**
> I use Update-Manager to do updates. If it wants to do a Partial Upgrade I open Synaptic and carefully check the changes it wants to make before continuing. If it wants to remove things I know should not be removed I will wait a while and refresh the package lists a few hours later to see if the situation is different. It usually is. This is the way I avoid breakage and it works pretty well. During development cycles I usually check for updates 2 to 3 times a day. Otherwise if it's a stable release I just let Update-Manager do its daily check.

This is what everyone should be doing. Otherwise things will break a lot. Note, however, that this would not have saved you from the recently upstart problems. Some things you just can't avoid getting hit by (unless you wait to see if someone killed their system on the forums).

Oh, and maybe don't upgrade so many times a day during development, that'll save you some trouble too. :)

---

### Post by psyke83 on 2009-09-17
> **Amaranth said:**
> This is what everyone should be doing. Otherwise things will break a lot. Note, however, that this would not have saved you from the recently upstart problems. Some things you just can't avoid getting hit by (unless you wait to see if someone killed their system on the forums).

Oh, and maybe don't upgrade so many times a day during development, that'll save you some trouble too. :)

I agree, however...

Would it be possible to modify the build/release system to do sanity checks against built packages? If the build system is smart enough to know when package X requires package Y, then it can delay the release of package X until package Y is available. That would reduce (or eliminate?) unsafe Partial Upgrade scenarios.

---

### Post by dagrump on 2009-09-17
Put a skull & cross-bones on partial upgrade, problem fixed. Next?  :)  :)

/as I run, well, I ran some.

I run dist-upgrade an see what it wants to do, if it wants to remove stuff, I hit "n" & enter. Then try a simple upgrade, if doesn't want to remove stuff, I go w/ that.
I really don't care if I break things it's just smoother if I don't handicap myself from the get. If I break it, it's broke, I'm getting good at. 
Partial upgrade=Bad Mojo, quick way to a bad ending.

---

### Post by Amaranth on 2009-09-18
It would be nice to have soyuz or whatever not publish packages until all dependencies are satisfied but I'm not sure how likely that is to happen. I have seen some other developers talking about it recently though.

---

### Post by zika on 2009-09-18
> **seeker5528 said:**
> Those are not suggestions, those are what you are being told will happen if you proceed.
If you do the Synaptic equivalent of 'apt-get upgrade' the result should be exactly the same. If you do the Synaptic equivalent of 'apt-get dist-upgrade' results may not necessarily be identical with 'apt-get dist-upgrade' every time, but you get the same type of an upgrade.
If I remember correctly the default-upgrade is the Synaptic equivalent of upgrade and the smart-upgrade is the Synaptic equivalent of dist-upgrade.
You can choose the type of upgrade you want Synaptic to do on the 'system --> preferences' menu.
Personally I use Synaptic all the time unless I have to work around something that requires some type of apt-get options to be given at the command line or can't start an xsession for some reason or another. I almost never tell it to select all the packages, preferring to individually select packages or small groups of related packages, so if dependency resolution fails I see it right away and move to the next package/group of packages and if I don't like the additional changes I can say 'screw that' right away and come back to it later to investigate the situation more after getting other updates.
Synaptic gives you an item on the package menu for downloading the change log for package that is selected in the main window. If you choose (on the 'settings --> preferences' menu) to view the package information in the main window, you have quick access to dependencies, dependents, installed files, etc....
Later, SeekerI know (almost) and agree with all You said. But, still, situation did not change, there are only more upgrades available, should I upgrade gdm and xsplash and should I remove couchdb ... ? :)
Which (one) option to choose 1., 2., 3., or 4. ...?
EDIT: Just to clear my point: Result should not be so different between applications. (I did all the upgrades , for gdm and xsplash also, and removed couchdb, just for the sake of others reading this thread)

---

### Post by seeker5528 on 2009-09-18
> **zika said:**
> I know (almost) and agree with all You said. But, still, situation did not change, there are only more upgrades available, should I upgrade gdm and xsplash and should I remove couchdb ... ? :)
Which (one) option to choose 1., 2., 3., or 4. ...?

With couchdb, being in Synaptic and choosing to download the changelog shows:

>  * Split couchdb into couchdb (to hold only the init) and couchdb-bin (to hold everything else). (LP: #427036)

And for desktop couch:

>  Depend on couchdb-bin instead of couchdb

Which really says nothing about whether you should remove couchdb, but seems like for most people it should not be missed if it is gone.

For the others, with 'apt-get upgrade' being the "safe" option that it is, it will not upgrade a package that pulls in something new. Synaptic shows me xsplash depends on:

```
ubuntu-xsplash-artwork | xsplash-artwork
```

so if one or the other of these is not already installed, or some other package that provides one of these, xsplash won't be upgraded.

The current GDM conflicts with 
```
xsplash (< 0.8)
```

So I'm assuming the xsplash in question (the currently installed version) is less than 0.8 and since with 'apt-get upgrade' xsplash will be held back because that would require installing a new package, gdm gets held back too because the newer GDM package conflicts with the currently installed xsplash.

Assuming these are all packaged correctly and work correctly upgrading them should not be an issue. 

It would be nice to have something equivalent to apt-listbugs that worked with Ubuntu. On Debian unstable apt-listbugs has saved me several times because more often than not packages that have bugs that will affect a high percentage of users have bug reports posted against them before I've even had a chance to try installing them, so at least some of the time you get the 'package fubar has blah blah blah bug(s) against it, do you want to continue?' type of a message with an option to hit '(y/n)'.

Later, Seeker

---

### Post by PGHammer on 2009-09-18
> **seeker5528 said:**
> With couchdb, being in Synaptic and choosing to download the changelog shows:



And for desktop couch:



Which really says nothing about whether you should remove couchdb, but seems like for most people it should not be missed if it is gone.

For the others, with 'apt-get upgrade' being the "safe" option that it is, it will not upgrade a package that pulls in something new. Synaptic shows me xsplash depends on:

```
ubuntu-xsplash-artwork | xsplash-artwork
```

so if one or the other of these is not already installed, or some other package that provides one of these, xsplash won't be upgraded.

The current GDM conflicts with 
```
xsplash (< 0.8)
```

So I'm assuming the xsplash in question (the currently installed version) is less than 0.8 and since with 'apt-get upgrade' xsplash will be held back because that would require installing a new package, gdm gets held back too because the newer GDM package conflicts with the currently installed xsplash.

Assuming these are all packaged correctly and work correctly upgrading them should not be an issue. 

It would be nice to have something equivalent to apt-listbugs that worked with Ubuntu. On Debian unstable apt-listbugs has saved me several times because more often than not packages that have bugs that will affect a high percentage of users have bug reports posted against them before I've even had a chance to try installing them, so at least some of the time you get the 'package fubar has blah blah blah bug(s) against it, do you want to continue?' type of a message with an option to hit '(y/n)'.

Later, Seeker

I was finally able to upgrade my Wubi Jaunty to M6 Karmic (Kubuntu); the apparent stickage was in the repo mirrors for Kubuntu-desktop (all previous attempts at doing an upgrade either stalled or (in the case of Update Manager) failed due to kubuntu-desktop issues.  Apparently the GRUB issue that has affected normal upgrades (and new installs via Wubi) does not affect in-place upgrades (even Wubi installs).

So far, so good!

---

### Post by autocrosser on 2009-09-18
I look at the forum & developer-list before I upgrade--I then start update-manager & update the sources list--if I'm presented with a "partial-upgrade", I fire-up Synaptic & explore what would be removed with a "full-upgrade"--then I decide if & what updates I'm doing at that time --also if I need to pin anything whilst I do upgrades...Each step along the way I check to see what "might" happen...And I rarely get caught with my "pants down".

---

### Post by kansasnoob on 2009-09-24
I wanted to give this a bump!

While the original intent was to document/modify updating behavior I think at this point we should focus on "who should or should not" run a development release.

I'm not going to go into detail, but it seems that simply stating, "for testing only" is not strong enough language.

**What needs to be done to keep folks from upgrading a production machine to a development version!**

---

### Post by novafluxx on 2009-09-24
> **whiprush said:**
> People keep just blindly running "apt-get dist-upgrade" for some reason and breaking their karmic installs instead of using "apt-get upgrade". I want to find out why people do this so people stop breaking their computers.

I am working on updating some [documentation](https://wiki.ubuntu.com/UbuntuDevelopment/UsingDevelopmentReleases), so if you could please respond with how and when you upgrade. Do you do it multiple times a day, do you have like a little ritual, or whatever. Thanks!

I believe its misinformation, and misunderstanding of how things work. People are presented with the option of a partial upgrade, and don't know if its ok or not, becuase Update Manager doesn't really warn well enough about the implications.

I myself had no idea I wasn't supposed to be doing partial upgrades until I came here and randomly found a post about it, so after a clean install of Alpha 6 I'm only doing normal upgrades in update manager, and I'm not using apt-get or aptitude.

I need to RTFM though, so bring on the updated documentation!

---

### Post by ranch hand on 2009-09-24
I don't like the idea that there are folks selected who should not run alphas.  It is their box, if they want to brick the whole thing it is up to them.

I agree that doing this on a production environment is just stupid.  The warning that comes up, that you have to click past to install, seems to me to be all the warning needed.  I think that the results of ignoring that and installing anyway will be a good teaching device.

This is free open GNU Linux.  Freedom has costs.  Ignoring warnings is one of those freedoms that you may have to "pay" for.

The frustration of reading posts about how this or that sucks, "this release makes Ubuntu look bad" and the like does make you wonder what universe some of the posters are living in.  There really is a difference in an alpha and a stable release.

At the end, though, it is a personal decision and  folks need to make it for themselves.

---

### Post by nanog on 2009-09-24
I dist-upgrade because its a development cycle and I ***EXPECT*** breakage.

If you don't know how to chroot and/or downgrade you should wait until beta (or later).

---

### Post by zika on 2009-10-07
Good example of difference between approaches of different upgrade managers is (from several minutes ago)
1.
```
~$ sudo aptitude upgrade
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  autoconf{u} automake{u} autotools-dev{u} intltool{u} m4{u} 
  python-distutils-extra{u} 
The following packages will be upgraded:
  gnome-themes-ubuntu libc-bin libc-dev-bin libc6 libc6-dev libglib2.0-0 
  libglib2.0-data libicu40 linux-headers-2.6.31-12 onboard 
  ubuntu-gdm-themes xserver-xorg-input-wacom 
12 packages upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
Need to get 28.5MB of archives. After unpacking 5,186kB will be freed.
Do you want to continue? [Y/n/?] 
```2.
```
~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  gnome-themes-ubuntu libc-bin libc-dev-bin libc6 libc6-dev libglib2.0-0
  libglib2.0-data libicu40 linux-headers-2.6.31-12 onboard ubuntu-gdm-themes
  xserver-xorg-input-wacom
12 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 28.5MB of archives.
After this operation, 16.4kB disk space will be freed.
Do you want to continue [Y/n]? 
```A little poll, which one would an average user choose ...?
All the packages offered to be deleted were installed today for the first time. Several hours ago.
Or, should I loose (that) a(p)titude ...?

---

### Post by Regenweald on 2009-10-07
I use:
```

sudo aptitude update

```
and
```

sudo aptitude safe-upgrade
``` exclusively. As for why?
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Resolving dependencies...
[B]The following packages have been kept back:
  grub-common{a} grub-pc [/B]
The following packages will be upgraded:
  cpp-4.4 gcc-4.4 gcc-4.4-base gnome-themes-ubuntu lib32gcc1 lib32stdc++6 
  libc-bin libc-dev-bin libc6 libc6-dev libc6-i386 libgcc1 libgfortran3 
  libgl1-mesa-glx libglib2.0-0 libglib2.0-data libglu1-mesa libgomp1 
  libicu40 libstdc++6 linux-headers-2.6.31-12 
  linux-headers-2.6.31-12-generic linux-libc-dev xulrunner-1.9.1 
The following packages are RECOMMENDED but will NOT be installed:
  libgl1-mesa-dri 
24 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 48.2MB of archives. After unpacking 24.6kB will be used.
Do you want to continue? [Y/n/?] y

```
note what has been kept back. Aptitude is the superior tool. Please use it.

---

### Post by DougieFresh4U on 2009-10-07
Don't really know why, but I always use 
```
sudo aptitude update
sudo aptitude dist-upgrade
```
Haven't used apt-get for a long time

---

### Post by zika on 2009-10-07
> **DougieFresh4U said:**
> Don't really know why, but I always use 
```
sudo aptitude update
sudo aptitude dist-upgrade
```Haven't used apt-get for a long timeMe too, exactly. The only difference is that I use safe-upgrade.
So would You remove packages from above list? I tried apt-get just to cross-check and got nowhere ... I see that these packages are not very important but could become a stumbling block if removed, especially because they are less than a day old ...

---

### Post by DougieFresh4U on 2009-10-07
> **zika said:**
> Me too, exactly. The only difference is that I use safe-upgrade.
So would You remove packages from above list? I tried apt-get just to cross-check and got nowhere ... I see that these packages are not very important but could become a stumbling block if removed, especially because they are less than a day old ...

I usually will not remove packages. If I see a newer one is to be installed, I will proceed with update/upgrade.

---

### Post by zika on 2009-10-07
> **DougieFresh4U said:**
> I usually will not remove packages. If I see a newer one is to be installed, I will proceed with update/upgrade.In this case, with any kind of options, in aptitude, that (not removing the packages) is impossible. At least with skills of mine.

---

### Post by Regenweald on 2009-10-07
In my case, I allow aptitude to remove the packages(if any) then with a later round of updates it puts them back in(dependencies I guess). safe-upgrade has not failed me yet.

---

### Post by VMC on 2009-10-07
> **zika said:**
> Good example of difference between approaches of different upgrade managers is (from several minutes ago)
...
A little poll, which one would an average user choose ...?
All the packages offered to be deleted were installed today for the first time. Several hours ago.
Or, should I loose (that) a(p)titude ...?

[**_[COLOR="Red"]apt-get vs aptitude[/COLOR]_**]("http://pthree.org/2007/08/12/aptitude-vs-apt-get/")

Somewhere I was told not to use either or but rather stick with one or the other. Something to do with their databases. That may be why you see the differences.

---

### Post by zika on 2009-10-07
I was brave and removed offered packages. I am not sure if that was the reason or something else but I'm now on new reinstalled Karmic ... Beware ... It crashed my file-system and it was unrepairable. I'm very stubborn guy and rarely do re-install but this was awful.  Screens and screens of errors ...

---

### Post by emarkay on 2009-10-07
EXCELLENT!

Please clarify and define the whole "partial upgrade" issue in a way that is obvious for "noobs". I suggest something like a "Read This First" section; a page where you are told about the things will break your install or contaminate your install (invalidating any testing), then referencing the specifics in depth later.  

For Jaunty, I have security updates set to automatic, and when I see that dialog I then also "Check" to see if there are others.

Otherwise I usually check every morning or if I power on.

For the Beta testing, I still have security set to automatic, and am updating only once or twice a day unless told to here and never a "Partial Update".

Also maybe ensure you explain the similarities /differences between the "Update Manager" Synaptic "Mark all Upgrades" the "apt-get upgrade" and the Recovery "Fix Broken Packages" as they all seem to involve updating and replacing files!

Also, I filed Launchpad bug on "Update/Upgrade" as it should be "Upgrade Manager" by convention.
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/445654](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/445654)

---

### Post by Roger E Critchlow Jr on 2009-10-07
What I don't understand, and I apologize for not reading all the other responses here, is why the repos cannot get their acts together to avoid this issue instead of pushing it out into the laps of all the users?

If you take a repo which has packages which make a consistent set, ie every package which has a dependency finds a package which fulfills that dependency in the repo and the core subset of required packages are all installable, and you add some packages which are inconsistent, it is immediately obvious that the repo is horked.  This may not be solvable in general, but most of the problems come with maintaining the core packages that many or most installations share.

So, if an update to a repo puts it into an inconsistent state, don't push the update, throw the packages back to the developer.  Or fork a branch in the repo and push the inconsistencies onto that branch and merge them back in when the developer solves the inconsistencies.  But don't publish the broken repos for the whole world to debug in parallel.

The currrent practise of throwing anything out into the repo to see if it sticks is an incredible waste of everyone's time.  Look at the volume of comments in the forum dedicated to deciding whether the current repo state is safe or not.  That's all time that might have been spent identifying problems in the release.  

Why can't the repos for the core of ubuntu always be safe for upgrade?

-- rec --

---

### Post by VMC on 2009-10-07
> **emarkay said:**
> 
Please clarify and define the whole "partial upgrade" issue in a way that is obvious for "noobs". I suggest something like a "Read This First" section; a page where you are told about the things will break your install or contaminate your install (invalidating any testing), then referencing the specifics in depth later.  

This has been discussed at length at almost every "partial upgrade" topic I have seen.

Read 23meg's [**_sticky_**]("http://ubuntuforums.org/showthread.php?t=1280021") , 3rd bullet.

---

### Post by whoop on 2009-10-07
Actually, I always do a dist-upgrade...
Unless:
Something critical gets removed, which isn't replaced by something else with the same functionality (within the same dist-upgrade).

Maybe I'm stupid or something :P But none of the dist-upgrades I did over the past couple of years made me feel stupid...

---

### Post by slakkie on 2009-10-07
> **Roger E Critchlow Jr said:**
> 
Why can't the repos for the core of ubuntu always be safe for upgrade?


Because it is a development release? I haven't seen any partial upgrades on normal releases. Not that I've ever witnessed a partial upgrade, but that is because I'm upgrading via aptitude.

With a normal release, yes, I can see that you want all deps to be resolved. But with a development release it is the user that should look carefully what to upgrade and what not. Development is ongoing and they push their packages out, regardless of their dependencies (could be other maintainers).

That is why there are repo freezes, to make sure everything for a set release gets stable.

---

