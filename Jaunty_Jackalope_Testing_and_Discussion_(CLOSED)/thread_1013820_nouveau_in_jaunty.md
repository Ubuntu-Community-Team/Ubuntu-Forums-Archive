---
title: "nouveau in jaunty"
date: 2008-12-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mariuz on 2008-12-17
seems that nouveau driver is included in jaunty 

[http://www.phoronix.com/scan.php?page=news_item&px=NjkxNg](http://www.phoronix.com/scan.php?page=news_item&px=NjkxNg)

but got an error when i try to install it 
$ sudo apt-get install xserver-xorg-video-nouveau

> The following packages have unmet dependencies:
  xserver-xorg-video-nouveau: Depends: linux-nouveau-modules but it is not installable

---

### Post by chrismine on 2008-12-17
I would love to try it because my xorg is borked!

---

### Post by Naddiseo on 2008-12-17
I htink you still need RAOF's ppa. [http://nouveau.freedesktop.org/wiki/UbuntuPackages](http://nouveau.freedesktop.org/wiki/UbuntuPackages)

I noticed that I have to use the intrepid repos from the ppa though, so that I get drm-modules.

---

### Post by RAOF on 2008-12-18
Yeah.  The DDX component of nouveau has been synced from Debian.  It still needs the kernel modules, which aren't in Jaunty yet.  I've got the start of a DKMSified kernel source package; it just needs a little tidying up before it goes in Jaunty.

---

### Post by Gourgi on 2008-12-18
from the [JauntyJackalope/TechnicalOverview]("https://wiki.ubuntu.com/JauntyJackalope/TechnicalOverview") : 
> 
Known Issues
-nouveau is available in Alpha-2 universe as an EXPERIMENTAL X driver for expert nVidia users only. We are accepting patches but not bug reports at this time. Regular users should stick with -nv for now.

what is the point of releasing the driver if you don't want bug reports for it but **only** patches?

If your -nouveau users are experienced enough to submit bugs then they would have used raof's ppa or upstream git version and they'd submitted the patches already.they wouldn't wait to test the jaunty's alpha 2 version of nouveau.

what i mean is that from my point of view, if something is not mature enough to handle bug reports yet then it should not be released, even in development cycle. i think of development releases as a way to interact with community and get their opinions,bugs, interests, patches but not **only** patches.

and btw i own an nvidia card  and i really care a lot about having an open source driver for it. i haven't used nouveau since intrepid's development cycle but i will definitely give it a try (although i can't submit patches)

PS , the wiki here [http://nouveau.freedesktop.org/wiki/UbuntuPackages](http://nouveau.freedesktop.org/wiki/UbuntuPackages) should be updated to include also intrepid and jaunty
> Add the sources.list entry specific to Gutsy or Hardy respectively. 

---

### Post by FarJumper on 2008-12-25
I added RAOF repository and I have the same error here because jaunty version hides the RAOF's one.

The second issue is that I can't install drm-modules (mentioned here: [http://nouveau.freedesktop.org/wiki/UbuntuPackages](http://nouveau.freedesktop.org/wiki/UbuntuPackages))

```
vbuell@vbuell-home:~$ sudo m-a a-i drm-modules
drm-modules, what is drm-modules?

```

---

### Post by Naddiseo on 2008-12-25
Yeah, I've been having the same problems with nouveau in jaunty the past couple weeks. I think it's related to the Xorg stuff. I've gone back to intrepid until I get some time to tinker again.

---

### Post by melalcoolique on 2009-04-06
Hi there !

Any news about Nouveau in Jaunty?

As far as i know, Nouveau works quite well in Fedora with 8xxx series. No 3d through.

[https://fedoraproject.org/wiki/QA/Test_Days/2009-03-26]("https://fedoraproject.org/wiki/QA/Test_Days/2009-03-26")

---

### Post by RAOF on 2009-04-07
> **melalcoolique said:**
> ...
Any news about Nouveau in Jaunty?
...

Yes.  You can install **xserver-xorg-video-nouveau**, and it'll work pretty much exactly the same way as it does in Fedora, barring the KMS for nv5x/nv6x cards - we don't build from the modesetting branch.

---

### Post by taavikko on 2009-04-13
Is there more to installing nouveau, than "aptitude install nouveau"
and "sed -i 's/nvidia/nouveau/g' xorg.conf"

Running NV41.8 (Go 6800 mobile from FS laptop)

If Driver "nouveau", kdm fails to start, and been prompted to login in terminal
If no driver specified, kdm starts and Im able to login, but isn't it then using nv.

Will attach relevant logs, when restarting the laptop (it's a bit hassle :( )

---

### Post by taavikko on 2009-04-15
> **taavikko said:**
> 
Will attach relevant logs, when restarting the laptop (it's a bit hassle :( )

Here they are, nouveau just wont start :( (kdm fails to start -> Xorg fails to start)
dkms builded the module...

Had to switch back to nvidia's binaries... For time being.

---

### Post by RAOF on 2009-04-15
Hm.  That looks like the most current driver - it looks like you've hit a bug.  Could you please file that upstream on freedesktop.org, or on launchpad.net and I'll get around to forwarding it upstream.

You'll want to attach the files you've attached here.

---

### Post by taavikko on 2009-04-15
> **RAOF said:**
> Hm.  That looks like the most current driver - it looks like you've hit a bug.  Could you please file that upstream on freedesktop.org, or on launchpad.net and I'll get around to forwarding it upstream.

You'll want to attach the files you've attached here.

Ok, I'll file it on LP, since haven't tried it on any other distro...

---

### Post by taavikko on 2009-04-15
[https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/361594](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/361594)

any other info needed?

---

### Post by RAOF on 2009-04-16
That looks about right to start with.  I'll try to get around to forwarding it upstream soon!

---

### Post by Polygon on 2009-04-16
too bad nouveau doesn't support my laptops video card, or else i would use it....

---

### Post by RAOF on 2009-04-16
> **Polygon said:**
> too bad nouveau doesn't support my laptops video card, or else i would use it....

Too new?  I think the version of nouveau in Jaunty should cover pretty much all cards from the TNT2 to the Geforce 9 series, with somewhat spottier coverage of geforce9, particularly IGP.

If nouveau really doesn't support your card (and the nvidia driver does!), you could help the developers in #nouveau on freenode with some information - I suspect an MMIO trace of the nvidia driver starting up would be what is needed, if you wanted to help.

---

