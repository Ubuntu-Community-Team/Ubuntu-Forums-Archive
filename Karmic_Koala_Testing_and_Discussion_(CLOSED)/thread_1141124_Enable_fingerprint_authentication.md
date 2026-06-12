---
title: "Enable fingerprint authentication"
date: 2009-04-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by captive on 2009-04-28
Gnome 2.26 comes with fprintd support BUT there no compatible libusb available for Jaunty (you should use git version or a ppa updated package). As result of this enrolling of fingerprints is not available in personal infos.
Enabling authentication on Jaunty requires, moreover, some hard tweaking on configuration files, while fingeprint authentication should be everything but a geek-thing (real geeks use complex hand-typed passwords, isn't it? ;) ).
I think libpam-fprint authentication should be available but optional by default.

---

### Post by tgpraveen on 2009-04-28
i think is a goal of fedora 11. so we could use some of their code.

---

### Post by Toe on 2009-04-28
I'd love to see this feature, too.
Should make fingerprint authentication much easier.

By the way, there's a Wishlist bug for this feature at launchpad: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/346083](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/346083)

---

### Post by caryb on 2009-04-28
Would love this to work with Kubuntu/KDE4:confused:


Cary

---

### Post by ktp on 2009-04-28
> **captive said:**
> gnome 2.26 comes with fprintd support but there no compatible libusb available for jaunty (you should use git version or a ppa updated package). As result of this enrolling of fingerprints is not available in personal infos.
Enabling authentication on jaunty requires, moreover, some hard tweaking on configuration files, while fingeprint authentication should be everything but a geek-thing (real geeks use complex hand-typed passwords, isn't it? ;) ).
I think libpam-fprint authentication should be available but optional by default.

+1

---

### Post by Gina on 2009-04-29
It would be nice to have an alternative to typing in the password every time an admin task is performed.

---

### Post by gnomeuser on 2009-04-29
I would love to be able to use my frintprint reader to authenticate for login and when doing things like installing packages.

---

### Post by captive on 2009-04-29
Just to add one more thing, fprint demo lets you enroll just one fingerprint scan per finger, it would be useful to have 2-3 scans per  finger to compare the fingerprint with, it'll reduce recognition errors.

---

### Post by rockin_goliath on 2009-04-29
I don't really get the whole fingerprint reader thing. Why would you use your fingerprint to authenticate a device that is covered in your fingerprints? There is nothing like a good password.

---

### Post by skeetre on 2009-04-29
I'd like to see the fingerprint authentication tweaked for Ubuntu also. I've read up on it for Fedora 11 and it looks pretty nifty.

It's a bit off topic, but my Asus laptop came with support for facial recognition login using the webcam. I thought that was pretty neat. I don't see that it would be too hard to implement with linux either, but I haven't read anything about it anywhere else.

---

### Post by coolen on 2009-04-30
> **tgpraveen said:**
> i think is a goal of fedora 11. so we could use some of their code.

Brief aside: I love that about open source. Hey, there's this feature we'd really like to implement. Our competitor over there's been working on it, too, so we can grab some of their code to help us out.

Also helps when we're more competing with the proprietary world than each other :P


I'd love this. My laptop has a fingerprint scanner, but unfortunately, it does not work under Linux. No big surprise there, but having some of the big distros behind fingerprint reading might inspire progress?

---

### Post by Gina on 2009-04-30
Being the only one in the house who uses or knows anything about computers, there is no security issue regarding users.  My OH thinks they're black magic and my attempts to get him even slightly interested have failed.  So anything to help lazy 'ol me to do less typing of passwords is welcome.
:lolflag:

---

### Post by taavikko on 2009-04-30
> **gnomeuser said:**
> I would love to be able to use my frintprint reader to authenticate for login and when doing things like installing packages.

As to my understanding, this feature is going to be included in F11?
At UDS it will be decided whether to pursue this on 9.10 or not.

my question, is there more to installing and configuration than "libpam-fprintd" and modifying correspondent files?

Have read wiki's and still baffled :D

---

### Post by xebian on 2009-04-30
PC's with fingerprint readers are not that many compared to built-in camera.  So I think IMHO, a facial recognition feature is a better option for resource allocation.

If the face is not recognized then blackens the screen, and/or suspend/hibernate.

I've read somewhere that future monitor will be able to reduce power if no one is seen in front of the monitor.  K/Ubuntu could take the lead here for being 'green'.

---

### Post by Gina on 2009-04-30
Well, I've got several webcams lying around so that would do just as well :lolflag:

---

### Post by crjackson on 2009-04-30
> **xebian said:**
> PC's with fingerprint readers are not that many compared to built-in camera.  So I think IMHO, a facial recognition feature is a better option for resource allocation.

If the face is not recognized then blackens the screen, and/or suspend/hibernate.

I've read somewhere that future monitor will be able to reduce power if no one is seen in front of the monitor.  K/Ubuntu could take the lead here for being 'green'.

I see no reason why both shouldn't be available. Cameras aren't allowed where I work (except for security of course) and we have thousands of laptops with FPR's used with MS*. Our main servers already use a combination of Unix and Linux. IT wants to migrate workstations to nix based platforms. This type of support would be a push in the right direction.

---

### Post by caryb on 2009-04-30
> **crjackson said:**
> i see no reason why both shouldn't be available. Cameras aren't allowed where i work (except for security of course) and we have thousands of laptops with fpr's used with ms*. Our main servers already use a combination of unix and linux. It wants to migrate workstations to nix based platforms. This type of support would be a push in the right direction.

+1

---

### Post by Gina on 2009-05-01
+1

---

