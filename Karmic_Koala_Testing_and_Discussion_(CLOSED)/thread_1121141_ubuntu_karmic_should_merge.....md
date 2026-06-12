---
title: "ubuntu karmic should merge...."
date: 2009-04-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Mokoma on 2009-04-09
computer janitor with add/remove.

anyone agree?

---

### Post by gnomeuser on 2009-04-09
I would favor a solution implemented in PackageKit which would allow some integration and naturally benefit all distros who support the required parts in the backend. 

That being said the mailing list is a buzz with a possible design for a replacement for add/remove programs - though I have to say it looks overly complex for my liking so far.

---

### Post by Mokoma on 2009-04-09
> **gnomeuser said:**
> I would favor a solution implemented in PackageKit which would allow some integration and naturally benefit all distros who support the required parts in the backend. 

That being said the mailing list is a buzz with a possible design for a replacement for add/remove programs - though I have to say it looks overly complex for my liking so far.

yeah. removing third party programs in windows is still 10000000000000000000000 easier than linux :/

---

### Post by zekopeko on 2009-04-09
> **gnomeuser said:**
> I would favor a solution implemented in PackageKit which would allow some integration and naturally benefit all distros who support the required parts in the backend. 

That being said the mailing list is a buzz with a possible design for a replacement for add/remove programs - though I have to say it looks overly complex for my liking so far.

link to discussion please.

EDIT:never mind. found it on ubuntu-devel-disscus. or what ever it called

EDIT EDIT: @gnomeuser: what do you find complex in the proposal? i like the idea of installing packages and still be able to browse and queue others.

on another note: how about rsync-ing package update lists instead having to download the whole file to get them to show in update manager/synaptic/apt-get? any downsides to this?

---

### Post by Kareeser on 2009-04-09
Ubuntu Brainstorm it.

---

### Post by Mokoma on 2009-04-09
> **Kareeser said:**
> Ubuntu Brainstorm it.

how?

---

### Post by juancarlospaco on 2009-04-09
***sudo apt-get remove programname***

---

### Post by Mokoma on 2009-04-09
> **juancarlospaco said:**
> ***sudo apt-get remove programname***

does that work for EVERY third party program?

---

### Post by zekopeko on 2009-04-09
> **Mokoma said:**
> does that work for EVERY third party program?

if it's installed via deb. if you compile it you have to uninstall it from the source directory from which you compiled it.

it would be nice if , when compiling then installing, make would say to dpkg: "Dude here's a program that's installed from source compile. keep track of the files so that the user can delete the source compile directory"

---

### Post by Mokoma on 2009-04-09
> **zekopeko said:**
> if it's installed via deb. if you compile it you have to uninstall it from the source directory from which you compiled it.

it would be nice if , when compiling then installing, make would say to dpkg: "Dude here's a program that's installed from source compile. keep track of the files so that the user can delete the source compile directory"

awesome!! thanks

---

### Post by gnomeuser on 2009-04-09
> **zekopeko said:**
> link to discussion please.

EDIT:never mind. found it on ubuntu-devel-disscus. or what ever it called

EDIT EDIT: @gnomeuser: what do you find complex in the proposal? i like the idea of installing packages and still be able to browse and queue others.

on another note: how about rsync-ing package update lists instead having to download the whole file to get them to show in update manager/synaptic/apt-get? any downsides to this?

1) where would the fun be in that, this teaches the hoodlums to research. Call it a knowledge treasure hunt if you will. I always try to provide links but at 3am I get to lazy, that's just life I am afraid.

2) Fundamentally I think computers should only have one button. "do what I want".. and even that design I can optimize.  Regardless I think that updating and adding/removing applications are fundamentally two separate jobs. I think updating at best might work like in XP where the updates are being downloading inthe background using idle bandwidth then their either autoinstall or ask for confirmation. Customization is a separate use case, and still that is separate from installing support plugins (which should be handled automatically kinda like gstreamer now hooks up to packagekit to search for the plugins it needs).

So let's recap, this is the unholy love child of synaptic, add/remove programs and a mid sized russian personal carrier. It then swallows up even more functionality as times goes by, things like system clean up which also should be a background task (and with btrfs we may get good rollback to avoid breaking things here). Any which way I look at this it's just wrong.. it's spherically wrong.. fractally wrong even.

3) That might work, however it might put an undue CPU load on our mirrors. It really doesn't scale as well either, the more users we get the more mirrors we will need, and not just for bandwidth but to deal with the CPU load incured from thousands of people rsyncing every minute. Remembering that we have to convince kind mirrors to do this work for us, and coming to them with the offer "well people, remember when we just raped your bandwidth.. well now we are going to melt your CPUs as well". Not sure that would work so well for a sales pitch.

---

### Post by zekopeko on 2009-04-09
@gnomeuser

just fount the wiki page: [https://wiki.ubuntu.com/AppCenter](https://wiki.ubuntu.com/AppCenter)

i think that the mockup is a nice start.
one of the things i would add would be different view buttons for experienced users. like itunes since the app is similar.
and i hope that they policykit-it as hell. sudo  is so 2007 :D.
the only thing i would add from package-kit would be the nice codec/font install hooks. but perhaps there is more to package-kit that i'm missing so you could perhaps enlighten me to the advantages.

---

### Post by Methuselah on 2009-04-09
> **zekopeko said:**
> 
it would be nice if , when compiling then installing, make would say to dpkg: "Dude here's a program that's installed from source compile. keep track of the files so that the user can delete the source compile directory"

I think you can use checkinstall...

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by zekopeko on 2009-04-09
> **gnomeuser said:**
> 1) where would the fun be in that, this teaches the hoodlums to research. Call it a knowledge treasure hunt if you will. I always try to provide links but at 3am I get to lazy, that's just life I am afraid.

2) Fundamentally I think computers should only have one button. "do what I want".. and even that design I can optimize.  Regardless I think that updating and adding/removing applications are fundamentally two separate jobs. I think updating at best might work like in XP where the updates are being downloading inthe background using idle bandwidth then their either autoinstall or ask for confirmation. Customization is a separate use case, and still that is separate from installing support plugins (which should be handled automatically kinda like gstreamer now hooks up to packagekit to search for the plugins it needs).

So let's recap, this is the unholy love child of synaptic, add/remove programs and a mid sized russian personal carrier. It then swallows up even more functionality as times goes by, things like system clean up which also should be a background task (and with btrfs we may get good rollback to avoid breaking things here). Any which way I look at this it's just wrong.. it's spherically wrong.. fractally wrong even.

3) That might work, however it might put an undue CPU load on our mirrors. It really doesn't scale as well either, the more users we get the more mirrors we will need, and not just for bandwidth but to deal with the CPU load incured from thousands of people rsyncing every minute. Remembering that we have to convince kind mirrors to do this work for us, and coming to them with the offer "well people, remember when we just raped your bandwidth.. well now we are going to melt your CPUs as well". Not sure that would work so well for a sales pitch.

1. :D

2. agree on the hooks part. but the whole package management thing is about installing/removing stuff. so why have 4 or 5 tools that do the same things but specific parts? updating is still installing one could argue. i think that the whole point of the app is to merge synaptic/update-manager/add-remove/gnome-app-install in one slick package.

3. why don't server simply create a signed diff of the package list and provide that diff as a file thaat will be merge on the users computer. like installing a small package that once installed runs a script that merges it with the local package list. just to clarify. i'm not talking about deltas for packages. just for the package lists (me thinks those are package.tar.gz right?). this would help dial-up users not have to download MB's of data just to see if there is an update to a single package.

---

### Post by zekopeko on 2009-04-09
> **Methuselah said:**
> I think you can use checkinstall...

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

as far as i know checkinstall is a poor mans deb creator. but it was at least a year since i tried  it. but thee whole point of that was that my "checkinstall" part should happen by default. if i delete the source directory i'm littering my system with files that are in like 5 different places.

---

### Post by Mokoma on 2009-04-09
surely it makes sense to put all add/remove of ALL packages within touching distance of each other. you dont build a car with the steering wheel in the front and the gearstick in the boot :D
maybe a stupid analagy but it will have to do

---

### Post by swoll1980 on 2009-04-09
They should merge Computer Janitor with the trash can. (a real one, not the one on your Desktop) A distro aimed at noobs should slap themselves for even considering such a thing.

---

### Post by Simian Man on 2009-04-09
So basically they are re-inventing PackageKit?  Am I missing something?

---

### Post by ghindo on 2009-04-09
I really would like to see PackageKit in 9.10 by default instead of these Ubuntu-specific hacks.

---

