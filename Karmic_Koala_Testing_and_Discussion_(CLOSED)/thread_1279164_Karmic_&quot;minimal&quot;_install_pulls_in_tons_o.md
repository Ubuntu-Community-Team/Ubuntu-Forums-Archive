---
title: "Karmic &quot;minimal&quot; install pulls in tons of rubbish"
date: 2009-09-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Gullible Jones on 2009-09-30
I'm trying to install a minimal Karmic base system with the netboot CD... Problem is, even when I select no tasks whatsoever, it decides to pull in more than 120 extra packages including Gnome, OpenOffice, and OpenJDK - basically the whole Ubuntu/Gnome package. I've tried using the "manual package selection" option, but that causes the installer to bug out claiming that it can't install x11-common... Help?

---

### Post by Gullible Jones on 2009-10-04
*bump*

Anyone? :(

---

### Post by wojox on 2009-10-05
Throw me a link to the mini.iso. I've been looking for it. I built Jaunty that way and was waiting to do the same for Karmic.

---

### Post by nanog on 2009-10-05
Ouch. Please file a bug.

---

### Post by kerry_s on 2009-10-05
> **wojox said:**
> Throw me a link to the mini.iso. I've been looking for it. I built Jaunty that way and was waiting to do the same for Karmic.

[http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/mini.iso)

---

### Post by Gullible Jones on 2009-10-05
It would be alpha6 not current, current is beta.

---

### Post by loomsen on 2009-10-05
get a netinstall iso and do a netinstall. It actually doesnt matter what you install because you'll most likely do an upgrade anyway.

---

### Post by renkinjutsu on 2009-10-05
> **wojox said:**
> Throw me a link to the mini.iso. I've been looking for it. I built Jaunty that way and was waiting to do the same for Karmic.

sorry to hijack your thread, but

wojox, did you use the mini iso with Unetbootin? i remember it just never worked for me, and i ended up burning a ~5mb iso to a CD :(

edit: did some snooping around, and they actually do provide usb images for netinstall! .. [http://archive.ubuntu.com/ubuntu/dists/karmic/main]("http://archive.ubuntu.com/ubuntu/dists/karmic/main")
browse around in there, and you'll find the img files

---

### Post by slakkie on 2009-10-05
I just installed the mini.iso inside a vm. I don't have the issue you report. Did the manual package selection, selected nothing, then quit aptitude. It installs a "few" packages, 420 in total.

420 /home/wesleys/karmic-mini.list

I have two gnome packages, but both of them are language-packs. Some (3) x11 packages:

libx11-6                                        install
libx11-data                                     install
x11-common                                      install

If you want a detailed list of all the packages it installed for me, have a look at [http://opperschaap.net/~wesleys/karmic-mini.list](http://opperschaap.net/~wesleys/karmic-mini.list)

Looking closer, I don't get why it installs openoffice though..

---

### Post by Gullible Jones on 2009-10-05
Yep that's basically my issue, 420 packages is way too many for a minimal system. Is this with the alpha6 mini.iso or the current one?

---

### Post by slakkie on 2009-10-05
> **Gullible Jones said:**
> Yep that's basically my issue, 420 packages is way too many for a minimal system. Is this with the alpha6 mini.iso or the current one?

The current one. I don't know how many packages will be installed when you boot by typing in cli when loading the CD.

---

### Post by wojox on 2009-10-05
> **renkinjutsu said:**
> sorry to hijack your thread, but

wojox, did you use the mini iso with Unetbootin? i remember it just never worked for me, and i ended up burning a ~5mb iso to a CD :(

edit: did some snooping around, and they actually do provide usb images for netinstall! .. [http://archive.ubuntu.com/ubuntu/dists/karmic/main]("http://archive.ubuntu.com/ubuntu/dists/karmic/main")
browse around in there, and you'll find the img files

No I downloaded the mini.iso from here:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

and pulled in whatever packages I wanted from the terminal.

The only thing I could suggest to the OP, is download the server edition and build it that way.

Thanks for the link kerry.

---

### Post by ikisham on 2009-10-05
That may be some experimenting they're doing...I've installed Karmic mini about a month ago and it hadn't openoffice.

---

### Post by slakkie on 2009-10-05
BTW, I reported a bug for it: [https://bugs.launchpad.net/bugs/443167](https://bugs.launchpad.net/bugs/443167)

---

