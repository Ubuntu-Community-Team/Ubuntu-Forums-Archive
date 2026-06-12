---
title: "Why Ubuntu doesn't make PIDGIN in repository?"
date: 2007-06-20
forum: Installation &amp; Upgrades
---

### Post by crossz on 2007-06-20
Normally ubuntu and other distributions do not add commercial softwares in their repositories.
But why Ubuntu doesn't add PIDGIN currently? while Fedora 7 did almost one month ago.

Cross

---

### Post by Jonne on 2007-06-20
Pidgin isn't commercial at all, what are you talking about?

Ubuntu Feisty ships with GAIM, which is the same program as Pidgin with another name (although it's a slightly older version). When you'll upgrade to Gutsy or if it gets added to backports, you'll have Pidgin.

---

### Post by joselin on 2007-06-20
Nop, pigdin is not in backports repositories nowadays.

Regards.

---

### Post by screaminj3sus on 2007-06-20
I really think they need to add pidgin to the repo's, I mean right now they include a gaim BETA, which I have had some problems with, all of which are fixed in pidgin (especially file transfers)

---

### Post by joe.turion64x2 on 2007-06-20
> **crossz said:**
> Normally ubuntu and other distributions do not add commercial softwares in their repositories.
But why Ubuntu doesn't add PIDGIN currently? while Fedora 7 did almost one month ago.

Cross
You must have in mind that Fedora is a cutting edge distro: it is designed to have always the very latest software, while Ubuntu is not (it does not necessarily bundle the very latest versions available). For example, I have not installed Fedora 7 in my laptop yet because the ATI drivers provided by AMD (the latest) don't work well with the latest Xorg version (bundled with Fedora 7 of course). Then I found out that Feisty doesn't have the latest Xorg.

Joe.

---

### Post by lingenfr on 2007-06-25
OK. All the Fedora and commercial irrelevancy aside... Is someone going to add Pidgin to the repository? It has been out quite some time. It is released, not beta, etc. so I don't want to upgrade to gutsy just to get it. If not, I suppose I will build it myself. Not griping and am most appreciative to have *buntu at all, just please cut the baloney and either add it or let us know why not. Thanks.

---

### Post by dseybert on 2007-06-26
Please let us know if you build it. I also would like to install Pidgin.

---

### Post by rillip on 2007-06-26
I don't think anyone here can answer whether or not it will be added to the repos anytime soon... probably need to take this to a suggestion area.

---

### Post by kelvin spratt on 2007-06-26
[http://www.getdeb.net/](http://www.getdeb.net/) you can get it here if you want it

---

### Post by lingenfr on 2007-06-28
That's helpful. Thanks. I thought that they changed the name due to some litigation about trademark infringement. It seems to me that the *buntu folks would help them out and get the infringing software out of circulation sooner rather than later. OK, I'm done, thanks again.

---

### Post by bjb.butler on 2007-06-28
A couple things:

Fedora's main purpose is to test out new software and new technologies, and prep them to be added to  
Red Hat Enterprise. Its sort-of like permanent beta release of Red Hat.

-------------------------------------------------------------------------------
Now about pidgin:

Is anyone planning on making a .deb of the latest pidgin release?

---

### Post by rocknrolf77 on 2007-07-09
If you read the other posts, you can find it at [www.getdeb.net](www.getdeb.net) ;)

---

### Post by gizmoarena on 2007-07-10
what about the SSL support problem?

---

### Post by jdackle on 2007-08-21
> **gizmoarena said:**
> what about the SSL support problem?

The thread [HOW TO: Pidgin 2.1.0 From Source]("http://ubuntuforums.org/showthread.php?t=529286") mentions the SSL problem and leads to think the provided script fixes it. I haven't tested for this myself but you can check that thread anyways...

Cheers!

---

### Post by thephotoman on 2007-08-21
I can provide a quick answer as to why Pidgin is not in backports.  I've tried to backport it myself in a fully compatible way, and wound up having major problems.  Please note that I am not an official backports developer or packager.

Go through and find all the packages that depend on Gaim.  You'll find that there are quite a few of them.  The thing is that they all very specifically depend on a package called "Gaim".  Not "libpurple" (the backend for Pidgin) or "Pidgin", but "Gaim".  These packages range from gaim-guifications to Evolution (another large mess of a program).

In order to upgrade from the last Gaim beta, which is what ships in Feisty, to Pidgin, each one of these packages would have to be recompiled using libpurple and pidgin in their configuration files and the package metadata file that lists all .deb package dependencies, then re-uploaded to the servers.  This is a non-trivial task, simply because of the necessity to recompile all 50 packages from scratch.

What's more, some of those 50 packages are broken by changes made between the last Gaim beta and Pidgin.  This means that those packages would need to be completely backported, requiring more time.  Since Backports has a requirement that any changes be trivial and not break the existing system, Pidgin wouldn't be included anyway.

Things like this have happened before.  When Firefox went from 1.0 to 1.5, Hoary users were told that there was no truly good way to put 1.5 on their machines until Breezy came out.  Likewise, I seem to recall a couple of other instances when projects changed their names and were not backported until the new Ubuntu release.

In short, if you want Pidgin 2.1 now, please use Gutsy.  Sure, there are bugs, but at the same time, it's relatively stable.

A note for future concerns: Firefox 3 is already in the repositories as granparadiso, and OpenOffice is a development version, as both projects will have releases shortly after Gutsy is hard frozen.  Thus, these packages should be easier to backport when they are released, even if they won't have the naming or branding to which you are accustomed.

---

### Post by frederik.nnaji on 2007-09-12
well it's quite simple in LinuxMint, which is a derivative of Ubuntu feisty
linux mint ships with pidgin instead of gaim

i would personally consider that not only step forward, but also an effort towards making the linux desktop more acute and up-to-date... hope that the people responsible for building the repos will make that move soon, too.
pidgin is a crucial piece of software in regard to platform interoperability

;)

---

### Post by eentonig on 2007-09-12
*** 6 month release cycle ***

---

### Post by frederik.nnaji on 2007-09-12
does the release cycle apply to the repositories?
will gaim and pidgin conflict so extensively, that adding pidgin to the feisty repos would be impossible?

---

### Post by eentonig on 2007-09-12
As far as my knowledge goes. Yes, the (official) repositories are tied to the release cycle. 

Backports are there to allow for new programs to be made available in prior releases. But only if the changes are minor and do not risk to create havoc.

One of the main purposes of the repos is to offer programs that are garantueed to work on the release they serve. It would be impossible to AND develop and build the new release and fill the repositories. AND keep updating the current release repositorie with new applications and make sure they work.

If you really want Pidgin, nothing is stopping you to compile it yourself or install it from a third party repositorie that made a .deb available for it. But it's not up to Ubuntu to make sure that Pidgin is backwards compatible.

---

### Post by frederik.nnaji on 2007-09-12
> **eentonig said:**
> As far as my knowledge goes. Yes, the (official) repositories are tied to the release cycle. 

Backports are there to allow for new programs to be made available in prior releases. But only if the changes are minor and do not risk to create havoc.

One of the main purposes of the repos is to offer programs that are garantueed to work on the release they serve. It would be impossible to AND develop and build the new release and fill the repositories. AND keep updating the current release repositorie with new applications and make sure they work.

If you really want Pidgin, nothing is stopping you to compile it yourself or install it from a third party repositorie that made a .deb available for it. But it's not up to Ubuntu to make sure that Pidgin is backwards compatible.


well that's pretty cleared up now, thanks stacks!
i installed pidgin from getdeb.net ,  that's a very cool page, and the installation with gkdebi is very simple and easy too!

glad things still work out this fine!

greetings from Berlin

fred

---

