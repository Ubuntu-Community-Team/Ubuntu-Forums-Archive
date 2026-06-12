---
title: "anki package outdated"
date: 2013-01-04
forum: Installation &amp; Upgrades
---

### Post by crysman on 2013-01-04
Please, could we have actualised *anki* package? Because in Ubuntu repository, there is 1.2.11 version, but oficially, there has been [2.x release]("http://ankisrs.net/anki2.html") for some time already...

I would prefer not to install software manually, but via apt-get...

---

### Post by dino99 on 2013-01-04
you can download an already deb package, from the debian link:

[http://ankisrs.net/anki2.html](http://ankisrs.net/anki2.html)

download it into an empty folder, then from it:

sudo dpkg -i *

[https://bugs.launchpad.net/ubuntu/+source/anki/+bug/1066487](https://bugs.launchpad.net/ubuntu/+source/anki/+bug/1066487)

---

### Post by crysman on 2013-01-05
> **dino99 said:**
> you can download an already deb package, from the debian link:

[http://ankisrs.net/anki2.html](http://ankisrs.net/anki2.html)

download it into an empty folder, then from it:

sudo dpkg -i *

[https://bugs.launchpad.net/ubuntu/+source/anki/+bug/1066487](https://bugs.launchpad.net/ubuntu/+source/anki/+bug/1066487)

But if I do so, then the package will not be updated automatically, or will it?

---

### Post by crysman on 2013-01-27
> **crysman said:**
> But if I do so, then the package will not be updated automatically, or will it?

I would rather have Anki 2 in official Ubuntu releases - how to achieve that? I've also left a query in the Anki 2 help forum here:
[https://groups.google.com/forum/?fromgroups=#!topic/ankisrs/0pCBZUMbGMI](https://groups.google.com/forum/?fromgroups=#!topic/ankisrs/0pCBZUMbGMI)

---

### Post by mcduck on 2013-01-27
In general, you don't ever get that kind of updates in Ubuntu. The package versions are frozen during the development of Ubuntu release, and after that you only get updates to fix serious bugs and to provide security fixes. Never just to give latest version of a package or add new features.

There are some exceptions, but the rules for such updates are very strict.

If you want to get more up-to-date version of a package and updates for it, try looking if you can find a PPA or some other third-party repository providing the package.

---

### Post by whatthefunk on 2013-01-27
> **crysman said:**
> But if I do so, then the package will not be updated automatically, or will it?

I installed from the .deb package on the anki homepage and while it doesnt automatically update, the program tells me when there is a more recent version and then all I have to do is follow the link and re-download the .deb file.  Not as easy as auto-updates, but not difficult either.

The problem with the Ubuntu repos is that Anki 2.0 was released just before Ubuntu 12.10 and thus did not make it into the repos.  Hopefully it will be included in the 13.04 repos.

---

### Post by Dave_L on 2013-01-27
Anki 2 can also be kept up to date via its git repository. I find that more convenient than using the .deb:

[https://github.com/dae/anki](https://github.com/dae/anki)
[https://github.com/dae/anki/blob/master/README.development](https://github.com/dae/anki/blob/master/README.development)

---

### Post by dino99 on 2013-01-27
add your voice

[https://bugs.launchpad.net/ubuntu/+source/anki/+bug/1066487](https://bugs.launchpad.net/ubuntu/+source/anki/+bug/1066487)

---

### Post by crysman on 2013-01-28
> **dino99 said:**
> add your voice

[https://bugs.launchpad.net/ubuntu/+source/anki/+bug/1066487](https://bugs.launchpad.net/ubuntu/+source/anki/+bug/1066487)

That should help. I signed that, too, thanks.

---

### Post by Dave_L on 2013-01-28
I voted too.

But even if Anki 2 were in the repo, it would quickly become out of date, since Anki has been getting updated every week or so, with bug fixes or feature additions.

What's needed is a volunteer, or volunteers, to keep the repo package updated on a continuing basis.

---

### Post by mcduck on 2013-01-28
> **Dave_L said:**
> I voted too.

But even if Anki 2 were in the repo, it would quickly become out of date, since Anki has been getting updated every week or so, with bug fixes or feature additions.

What's needed is a volunteer, or volunteers, to keep the repo package updated on a continuing basis.

That's never going to happen for the package in the official repositories. However people interested in doing that could very well set up (and maintain ) a PPA repository. Which is the exact things what the PPA's are for....

---

### Post by Mrokii on 2013-03-18
How much work/knowledge is needed to set up a PPA? Or what requirements are needed at all?

---

### Post by Dave_L on 2013-03-18
> **Mrokii said:**
> How much work/knowledge is needed to set up a PPA? Or what requirements are needed at all?

[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

I think the bulk of the effort is assembling the package, and then keeping it up to date.

---

### Post by Dave_L on 2013-03-18
> **Dave_L said:**
> [https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

I think the bulk of the effort is assembling the package, and then keeping it up to date.

Actually, since Anki is already available as a downloadable .deb (at [http://ankisrs.net/](http://ankisrs.net/)), I wonder if it's as simple as uploading the .deb to a PPA. I skimmed through the above launchpad.net article, but I didn't understand all the details.

Creating a PPA is itself simple; it's an option in one's launchpad.net account.

---

### Post by whatthefunk on 2013-03-19
Do you even need a ppa?  Once Anki is installed, it automatically updates when you open the program.

---

### Post by Dave_L on 2013-03-19
> **whatthefunk said:**
> Do you even need a ppa?  Once Anki is installed, it automatically updates when you open the program.

Doesn't that feature merely download the .deb with your browser?  That's different from using a PPA or repository within a package manager such as synaptic, which provides you with other capabilities.

---

