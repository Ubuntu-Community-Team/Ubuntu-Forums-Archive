---
title: "Openoffice 2.4"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by Cr@sh_Ov3rride on 2008-08-01
Hello,

i'm using ubuntu 7.10 and i don't want to upgrade it to 8.04 (i've tested and didn't like some things) but i'd like to upgrade the openoffice to the 2.4 version...

how can i do it? download openoffice 2.4 and uninstall the current version or do something else?


thanks

---

### Post by michael_1234 on 2008-08-01
Unfortunately openoffice isn't available via the backports ( [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports) ), or else you could have just enabled that repository & installed it.

You could try, as you mention, just downloading the OpenOffice linux distro from openoffice.org, but note that the generic default tar.gz is actually a bundle of rpm's and an installer. Try the "other" downloads, and they have ".deb" packages, [http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US) 

The "deb" package is a collection of "deb's" and an update script.

The install instructions do say that the "deb" packages are not build by OOo & are not supported, though.  [http://download.openoffice.org/common/instructions.html#linux](http://download.openoffice.org/common/instructions.html#linux)  

And, of course (a quick note from personal experience) this could just open a can of worms, where you'll be installing one "newer" software package that has dependencies on other newer software packages , etc, until you end up with basically a new-ish system.  Hopefully that's not the case for you.

-m

---

### Post by michael_1234 on 2008-08-01
btw, 
  ...I personally did NOT try installing OOo 2.4 on 7.10 -- I just upgraded my 7.10 to 8.04....  And, I'm using OOo 2.4 pretty much all the time (and trying to get other people to start using this at the office, too :-/ )  So far, actually, I don't mind 8.04. And, primarily, I do like having the newer software available to me via the package manager.

OOo 2.4 has no real issues ... or, actually, noticable advantages ... over OOo 2.3 as far as I can tell.  Though, I do update my various OOo installations when a new version does come out (i'm using it on mac, win, various linux).

good luck,
-m

---

### Post by Cr@sh_Ov3rride on 2008-08-01
Ok!

Thank you for the help, i'm going to try it on virtual machine to do it later on my notebook without mistakes!

---

