---
title: "Odd regression in Document Viewer"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bennachie on 2009-10-23
Has anyone else experienced the odd regression in Document Viewer 2.28.1 that renders only the images on a smallish subset of PDF documents? The attached bank statement - a sample one posted by NAB here in Australia - has this problem on my system with Ubuntu 9.10rc installed and fully updated.

The problem didn't exist in 9.10 beta.

---

### Post by Cybie257 on 2009-10-23
Interesting. I tried your pdf attachment and it shows up just fine with Adobe reader (9.10, latest updates, 64-bit). but with Doc Viewer, same version you mentioned, only the logo pic and some lines show up. 

Tried with other PDF docs i have and no problems. I'd say it's something to do with the pdf creator of that doc maybe??? 

You can try installing Adobe Reader for Linux if you need to see those docs.

-Cybie

---

### Post by bennachie on 2009-10-24
Thanks for your research, and for confirming the issue. I had already discovered that the document is rendered just fine by Adobe Reader (and works equally well with older versions of Document Viewer). I guess that this is an upstream bug rather than being specific to the Ubuntu version, but I'll check that - I'll need to work out where the problem should really be reported.

I'm not fond of having Adobe Reader installed on any of my systems - it's a bloated and buggy piece of software, which has a nasty habit of depositing bits of code into the most unlikely places.

---

### Post by Cybie257 on 2009-10-24
> **bennachie said:**
> 
I'm not fond of having Adobe Reader installed on any of my systems - it's a bloated and buggy piece of software, which has a nasty habit of depositing bits of code into the most unlikely places.

A can't disagree with that, but I will say that it seems to not be so bad on the Linux side. As for Windows, I think everything that MS and Adobe make have been designed around that same idea. To see how much ram and hard drive space it can possible takeup along with hogging every possible resource. LoL. Don't get me wrong, Adobe makes some nice pieces of software, it's just that it seems each new version that comes out, the more space and resources it takes in comparison to what little (true) difference there is from one version to the next. :)

-Cybie

---

### Post by bennachie on 2009-10-24
You're right, of course, but many of the same criticisms of Adobe Reader are relevant to the Mac OS-X environment as well. I've had less experience with the Linux version.

Incidentally, I've verified that the current problem crops up in all the major distros that include Evince 2.28.0 or 2.28.1 (I've run Live CDs of the latest Gnome versions of Mandriva, Fedora and openSUSE to check). The problem does not occur in the equivalent KDE versions, including Kubuntu. These use Okular as a document viewer. Mind you, even KDE 4.3.2 seems to me still to be a work in progress, and Kubuntu wouldn't actually be my distro of choice in that group.

I've lodged a bug report at:

[https://bugs.launchpad.net/bugs/459569](https://bugs.launchpad.net/bugs/459569)

Thanks again for your response.

---

### Post by skillllllz on 2009-10-24
I am experiencing this issue as well.

---

