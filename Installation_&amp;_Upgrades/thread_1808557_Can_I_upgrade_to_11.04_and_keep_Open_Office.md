---
title: "Can I upgrade to 11.04 and keep Open Office?"
date: 2011-07-20
forum: Installation &amp; Upgrades
---

### Post by Hralgmir on 2011-07-20
I installed Ubuntu 10.10 in the spring. Now there is the 11.04 version available as an upgrade. I recall downloading many 10's of MB of Open Office updates only recently. I only use it on odd occasions anyway. Is there an easy way to upgrade to the latest version but without bothering to change to Libreoffice, thus saving a lot of downloading? Is it possible to selectively upgrade in this way? I would like to maintain compatibility with the easy Update Manager system, rather than end up having to manage everything from henceforth in the terminal, which could get difficult as it would be necessary to know what items needed updating. I suppose I could copy all the Open Office files  and stash them away somewhere, then uninstall Libreoffice, but that would rather defeat the point of avoiding downloading surplus material.

---

### Post by MAFoElffen on 2011-07-20
> **Hralgmir said:**
> I installed Ubuntu 10.10 in the spring. Now there is the 11.04 version available as an upgrade. I recall downloading many 10's of MB of Open Office updates only recently. I only use it on odd occasions anyway. Is there an easy way to upgrade to the latest version but without bothering to change to Libreoffice, thus saving a lot of downloading? Is it possible to selectively upgrade in this way? I would like to maintain compatibility with the easy Update Manager system, rather than end up having to manage everything from henceforth in the terminal, which could get difficult as it would be necessary to know what items needed updating. I suppose I could copy all the Open Office files  and stash them away somewhere, then uninstall Libreoffice, but that would rather defeat the point of avoiding downloading surplus material.
Okay now... I keep hearing this, complaints of this and confusion over this. Here is the story I was told- (I'm trying to be "informative," not slanderous to the companies involved.)  

Once open a time, in the friendly open-sourced community, their was a company that supported the opensource concept of software to all (Sun Microsystems.)  I know I'm embellishing... But might as well make this entertaining.

Sun was bought out by Oracle.  Oracle didn't have the same concepts on giving things away, that it didn't bring them money to their coffer's.  Among many other products... One of those products was "OpenOffice."  Oracle supported it for a "time" beyond it's incidental acquisition of it, then dropped it.  Usually when a company has an psuedo-opensourced product, it ensures that it doesn't have any sold support for it...

Low and behold, a Country had adopted OpenOffice as it's official Office Suite- Brazil.  So instead of OpenOffice completely going away, Brazil took it up to continue development and support... ergo. the name-change. (Same name / different translation)  [COLOR=Teal]It "is" the same product.
[COLOR=Black]
When this product changed hands, they changed the name.  (I'm guessing, their own poetic justice.)  When you upgrade, it should take all your profiles and extensions from OpenOffice and Upgrade it to it's new namesake...  All past data files, should be handled to same as it did previously.
[/COLOR][/COLOR]

---

### Post by lykwydchykyn on 2011-07-20
> **MAFoElffen said:**
> Okay now... I keep hearing this, complaints of this and confusion over this. Here is the story I was told- (I'm trying to be "informative," not slanderous to the companies involved.)  

Once open a time, in the friendly open-sourced community, their was a company that supported the opensource concept of software to all (Sun Microsystems.)  I know I'm embellishing... But might as well make this entertaining.

Sun was bought out by Oracle.  Oracle didn't have the same concepts on giving things away, that it didn't bring them money to their coffer's.  Among many other products... One of those products was "OpenOffice."  Oracle supported it for a "time" beyond it's acquisition of it, then dropped it.  Usually when a company has an psuedo-opensourced product, it ensures that it doesn't have any sold support for it...

Low and behold, a Country had adopted OpenOffice as it's official Office Suite- Brazil.  So instead of OpenOffice completely going away, Brazil took it up to continue development and support... ergo. the name-change. (Same name / different translation)  [COLOR=Teal]It "is" the same product.[/COLOR]

erm.... that's not really at all what happened.


To answer the OP's question, I don't think you can do a selective upgrade for a release-upgrade like that.  If you really want to keep running openoffice, you can just uninstall the openoffice from your package manager, download the openoffice debs from openoffice.org, and install them after you do your release upgrade.

But first, consider this:

 - What has, to this point, been called "openoffice.org" in the repositories was *not* openoffice.org.  It was a heavily patched version of openoffice from a project called **go-oo**, a community version mostly led by Novell and used by just about every Linux distro in existence for several years.

 - When LibreOffice split from OpenOffice.org, go-oo was folded in to the LibreOffice code base, and the vast majority of go-oo developers joined up with LibreOffice.

 - Consequently, if you stick with LibreOffice, you are going to end up with something much closer to what you have been running than if you download the "official" OpenOffice.org debs.

 - What's more, OpenOffice.org has been dropped by Oracle and donated to the Apache foundation, where it will probably languish for some time until a community can be built around it.  So it's likely to fall behind LibreOffice for at least the foreseeable future.

---

### Post by MAFoElffen on 2011-07-20
> **lykwydchykyn said:**
> erm.... that's not really at all what happened.


To answer the OP's question, I don't think you can do a selective upgrade for a release-upgrade like that.  If you really want to keep running openoffice, you can just uninstall the openoffice from your package manager, download the openoffice debs from openoffice.org, and install them after you do your release upgrade.

But first, consider this:

 - What has, to this point, been called "openoffice.org" in the repositories was *not* openoffice.org.  It was a heavily patched version of openoffice from a project called **go-oo**, a community version mostly led by Novell and used by just about every Linux distro in existence for several years.

 - When LibreOffice split from OpenOffice.org, go-oo was folded in to the LibreOffice code base, and the vast majority of go-oo developers joined up with LibreOffice.

 - Consequently, if you stick with LibreOffice, you are going to end up with something much closer to what you have been running than if you download the "official" OpenOffice.org debs.

 - What's more, OpenOffice.org has been dropped by Oracle and donated to the Apache foundation, where it will probably languish for some time until a community can be built around it.  So it's likely to fall behind LibreOffice for at least the foreseeable future.Thanx for correcting me: I knew "the version" I heard was somewhat "hearsay."
Still sounds like there was some truth to it... and like "OpenOffice" itself is at least stalled for a time.

---

### Post by Hralgmir on 2011-07-22
Thankyou for the help. Most of the time I just need something to make a few notes in, so Gedit is sufficient, unless I need to open an unusual file type. I was interested to see if there was some simple command to upgrade to 11.04 --minus the bits I don't really need or similar that I hadn't heard about, as there are many different things the terminal can do which I don't know about. It sounds like Libre Office is probably better, which is why it has been included. It is interesting to see the reasons behind the change, in that Libre Office should be better maintained and kept up to date going forwards.

---

