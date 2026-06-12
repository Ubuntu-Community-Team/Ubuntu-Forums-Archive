---
title: "Running in Virtual Machines"
date: 2008-07-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bodhi.zazen on 2008-07-18
Sure would be nice if testing releases worked in virtual machines.

I was able to get it up and running on VMWare Server (1.0.6 and 2.0 RC1).

The trick has been :

Post install I needed to exit /etc/X11/corg.conf and replace "vmmouse" with "mouse"

The the other trick is to boot to recovery mode and at the recovery menu select continue with regular boot.

As far as VMWare Tools, they seem to work fine in 1.0.6, but they break X (in that they limit the resolution) in 2.0 RC1.

Hope this post helps some wanting to run in virtual environments.

---

### Post by Rocket2DMn on 2008-07-18
RE: vmmouse, see 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-vmmouse/+bug/248521](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-vmmouse/+bug/248521)
and
[https://bugs.launchpad.net/ubuntu/+bug/248816](https://bugs.launchpad.net/ubuntu/+bug/248816)

---

### Post by Shazaam on 2008-07-18
Intrepid is even more fun using Virtualbox. Usually I get a successful boot 1 out of 9 to 10 times. The error message is usually "kernel bug" repeated endlessly till it locks up.
When it does boot it is stable. I think I will wait a while and try the beta when it comes out.

---

### Post by bodhi.zazen on 2008-07-19
Thanks for the info Shazaam.

It is difficult to test as 8.10 is not available as a live CD, which means 20-30 minutes + 3.5 Gb of hard drive space per test machine ... ouch.

I *may* try kvm ...

---

### Post by fifth on 2008-07-19
> **Shazaam said:**
> Intrepid is even more fun using Virtualbox. Usually I get a successful boot 1 out of 9 to 10 times. The error message is usually "kernel bug" repeated endlessly till it locks up.
When it does boot it is stable. I think I will wait a while and try the beta when it comes out.

Think your lucky to get it running in VirtualBox at all for now;

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246067](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246067)

---

### Post by philinux on 2008-07-19
> **fifth said:**
> Think your lucky to get it running in VirtualBox at all for now;

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246067](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246067)

Yep I gave up on Vbox as guest additions no longer worked after a kernel upgrade.

Installed on spare HD instead.

---

### Post by Canis familiaris on 2008-07-19
> **bodhi.zazen said:**
> 
I *may* try kvm ...
KVM is cool. It can run 64bit OS too. Virtualbox cant. I dunno about VMWare.
However KVM needs a better interface seriously.

---

### Post by xebian on 2008-07-19
> **Anurag_panda said:**
> KVM is cool. It can run 64bit OS too. Virtualbox cant. I dunno about VMWare.
However KVM needs a better interface seriously.

I'd like to try KVM as vbox won't work. Is there a good wiki for KVM?  Isn't supposed to be better in 2.6.26 ?

---

### Post by bodhi.zazen on 2008-07-19
> **Anurag_panda said:**
> KVM is cool. It can run 64bit OS too. Virtualbox cant. I dunno about VMWare.
However KVM needs a better interface seriously.

If you are familiar with qemu, the same commands apply to kvm. It is easiest to run kvm from the command line, although you can write a launcher script for each machine.

In a terminal just enter :

```
kvm --help
```The gui tools for kvm look nice, but functionality is limited and they need to write wrapper scripts so that they do not need to be run as root.

The gui tools automate the process and can monitor resources.

VMWare will also do 64 bit, VMWare Server 1..0.6 is nice, Server 2.0 RC1 is buggy.

---

### Post by olskar on 2008-07-19
There is daily live cd I think :)

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by bodhi.zazen on 2008-07-19
> **olskar said:**
> There is daily live cd I think :)

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Sweet link olskar, thank you (I am aware of the daily builds from previous release cycles, I did not know they had started with 8.10, lol)

---

### Post by mitchellcipriano on 2008-07-20
> **fifth said:**
> Think your lucky to get it running in VirtualBox at all for now;

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246067](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246067)

I have it running in VirtualBox. The only thing I needed to do to get a good install was to set the video memory to 64MB. The guest additions do not run, but otherwise it all seems to work great.

---

### Post by bodhi.zazen on 2008-07-20
mitchellcipriano: Thanks for the info re: Virtualbox (save me some time ... ).

To any interested,

I tested the daily builds (desktop) iso images in KVM.

I could not get the x86_64 image to boot.

The i386 image boots if you add "no-kvmclock" to the boot options.

Once gnome starts you have a similar vmware mouse problem (similar to VMWare server).

The images are reported to boot in qemu, but that was not my experience. Neither the x86_64 or i386 image booted in qemu (not extensively tested mind you).

Considering this is Alpha 2 that is about the extent of my testing in virtual environments.

---

### Post by Shazaam on 2008-08-03
Installed Alpha3 in both VirtualBox and VMware Player. Vbox install still churns out multiple complaints about a kernel bug during bootup then locks up (normal and recovery boot). Tried mitchellcipriano's tweak but no luck. Player install will let me log in but locks up at the tan transition screen (between login and full desktop). Player install WILL let me drop to a console login after choosing recovery mode from grub. Tried editing xorg.conf but no luck yet.

---

### Post by bodhi.zazen on 2008-08-03
Yes, Alpha 3 is broken again for me too :(

---

### Post by plun on 2008-08-03
Virtualbox 1.6.4 was just released, I personally have no scruples
about a non OSE version.

Changelog
[http://www.virtualbox.org/wiki/Changelog](http://www.virtualbox.org/wiki/Changelog)

Download from Sun
[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

OSE version is available as sourcecode
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)


Downloading daily build for a test.... :)

---

### Post by plun on 2008-08-03
Followup:

No Luck with Vb 1.6.4, hard-freeze when Ubiquity starts....

Ctrl-Alt-Backspace for restart.

---

### Post by mitchellcipriano on 2008-08-03
I have alpha 3 running in Vbox. I did not do a fresh install, but upgraded. It all seems to work well.

---

### Post by RAOF on 2008-08-04
For those interested in a KVM interface, the virt-manager package (you also need libvirt-bin installed) provides a nice interface to QEMU/KVM/Xen hosts, either locally or over a network.

---

### Post by tech0007 on 2008-08-04
Tried installing alpha 3 in vbox 1.6.2 and i got this on bootup.  Debian lenny works better. how come?

---

### Post by bodhi.zazen on 2008-08-04
> **RAOF said:**
> For those interested in a KVM interface, the virt-manager package (you also need libvirt-bin installed) provides a nice interface to QEMU/KVM/Xen hosts, either locally or over a network.

virt-manager is a nice start, but, IMO, it is not as polished an interface as compared to either VirtualBox or VMWare.

Also there are a number of options that are not yet available in virt-manager, the most glaring, for me, I can not use a bridged network without running virt-manager as root.

Personally I am quite familiar with qemu and so running kvm from the command line makes sense, and is the only way to access all the features of KVM.

Hopefully virt-manager will continue to be developed, gaining polish and functionality.

---

### Post by bodhi.zazen on 2008-08-05
Update :

Alpha 3 , 32 bit, works in KVM

X will fail -> go to a console with (in KVM) ctrl-alt-2

enter 

sendkeys ctrl-alt-f1

to to kvm

ctrl-alt-1

edit /etc/X11/xorg.conf, change "vmmouse" to "mouse"

restart X

sudo /etc/init.d/gdm restart

:)

---

### Post by darco on 2008-08-05
I am using VMWare Server and was able to boot and update Ibex just fine. Been playing with it for a day now but now after logging in I get a blank desktop with the twirling disc dead in its track. Does this mean X did not load?
thxs
darco

---

### Post by bodhi.zazen on 2008-08-05
> **darco said:**
> I am using VMWare Server and was able to boot and update Ibex just fine. Been playing with it for a day now but now after logging in I get a blank desktop with the twirling disc dead in its track. Does this mean X did not load?
thxs
darco

There is a discussion of this here :

[http://www.ubuntu.com/testing/intrepid/alpha3](http://www.ubuntu.com/testing/intrepid/alpha3)

Under "Caveats"

linking here : [https://bugs.launchpad.net/bugs/246969](https://bugs.launchpad.net/bugs/246969)

I was running Alpha 2 in VMWare, but it locked up with alpha 3. I have not tried to fix it yet.

---

### Post by darco on 2008-08-05
ok thanks...that seems to work. Sorry for posting, I had that link bookmarked since I had a VB issue but didnt notice the VMWare comment.

darco

---

### Post by bodhi.zazen on 2008-09-06
Just a *BRIEF* update for anyone interested :

I took alpha 5 (x86_64) for a spin :

VMWare : X is working in vmware , gnome sometimes crashes.

Virtualbox : virtualbox does not support 64 bit guests and I did not want to download the 32 bit version just to test in virtualbox, sorry.

KVM : X is not working in KVM, the virtual machine seems to lock up and I could not get to a consule with sendkeys ctrl-alt-f1

---

### Post by Shazaam on 2008-10-13
32bit Ibex beta downloaded today, installed on VBox (non OSE). Boots and works fine (didn't need any extra kernel parameters) but GuestAdditions will not compile (module build error). Installed and ran on VMware Player with no problems.

---

### Post by bodhi.zazen on 2008-10-13
The beta runs in KVM without any problems.

---

### Post by MoebusNet on 2008-10-24
Running Ubuntu 8.10rc w/Guest Additions (guest) in VBox 2.0.2 on Ubuntu 8.04 (host w/-19 kernel). Everything seems to be working except full-screen.

---

### Post by bodhi.zazen on 2008-10-24
X is not working form me in KVM (64 bit host, both 64 bit and 32 bit guests affected).

I reported the bug on LP last night.

---

