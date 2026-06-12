---
title: "Broken Packages - Upon Samba Installation"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by uamusa on 2007-05-03
Ubuntu Edgy Eft 6.10

When looking at the package manager is indicates the below mentioned dependencies are installed already.  If anyone could advise on where I've gone wrong it would be GREATLY appreciated.  Thanks in Advance -Chris

Input:

root@linserver:/home/chris# apt-get install samba samba-common samba-doc libcupsys2-gnutls10 libkrb53 winbind smbclient

Result:

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba-common is already the newest version.
libkrb53 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openoffice.org-l10n-en-gb: Depends: openoffice.org-common (>= 2.0.4~rc3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.5) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
  openoffice.org-l10n-en-za: Depends: openoffice.org-common (>= 2.0.4~rc3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.5) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
E: Broken packages

---

### Post by zvacet on 2007-05-03
**synaptic>edit>fix broken packages**

---

### Post by uamusa on 2007-05-03
In Synaptic Package Manager , I did as you suggested and clicked "Fix Broken Packages". And in the status bar of the window it showed:  "Successfully fixed dependency problems"  

HOWEVER

When returning to terminal window to try again, I'm getting the same error as in the initial post.  Any other possibilities you're aware of?

---

### Post by Exom on 2008-06-19
> **zvacet said:**
> **synaptic>edit>fix broken packages**
Very thanks i solved the problem. :)

---

