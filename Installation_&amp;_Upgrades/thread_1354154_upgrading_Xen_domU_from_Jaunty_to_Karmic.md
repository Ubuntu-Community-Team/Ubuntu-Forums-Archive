---
title: "upgrading Xen domU from Jaunty to Karmic"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by winnall on 2009-12-13
I've been happily running Ubuntu Jaunty under a Debian Xen AMD64 kernel, both as a dom0 and as domU's. The kernel version is vmlinuz-2.6.26-2-xen-amd64.

Today I thought I'd try to upgrade one of my domU's to Karmic. Everything went fine until I tried to restart the domU with the Karmic installation. During booting, after the error

[INDENT]init: ureadahead main process (857) terminated with status 5[/INDENT]

the domU machine hangs.

Research on the net reveals that ureadahead is new in Karmic and that it needs kernel patches to work. So apparently I need a Xen kernel with the ureadahead patches applied.

What's the best way to go about this? Should I download the latest Ubuntu kernel, apply the ureadahead patch, configure whatever it needs for Xen and sail away happily into the sunset? Does anyone have any advice or better solutions (like: "download exactly that already compiled from [somewhere]")?

Or have I misunderstood anything anywhere?

I'm being cautious because I've got exactly one machine which is used in production, so the fix has to work quickly. The domU I scuppered was spare, but there are other domU's on the machine doing important work.

Steve

---

### Post by winnall on 2009-12-15
I've spent some time trying to resolve this problem.

I started by building a kernel based on the instructions in the following articles, which are clear and consise:

[INDENT][http://virtually-a-machine.blogspot.com/2009/12/experimental-xen-and-ubuntu-part-1.html](http://virtually-a-machine.blogspot.com/2009/12/experimental-xen-and-ubuntu-part-1.html)
[http://virtually-a-machine.blogspot.com/2009/12/experimental-xen-and-ubuntu-part-2.html](http://virtually-a-machine.blogspot.com/2009/12/experimental-xen-and-ubuntu-part-2.html)[/INDENT]

Coming from Jaunty, you definitely need to build a new xen-hypervisor too, because the Jaunty /boot/xen-3.3.gz doesn't work with the kernel build described in the first article ("could not set up dom0 guest OS"). I built and installed xen-hypervisor-3.4.2, and the machine booted with that.

The instructions above included installing a new version of xen-utils, which built but failed to install because xen-utils-3.3 was already present. When I removed xen-utils-3.3 and installed xen-utils-3.4.2, it modified the Python installation so that commands like

[INDENT]xm create ...[/INDENT]

no longer worked ("no module named xen.xm"). This is because stuff which should be in /usr/lib/python2.6/dist-packages is placed into /usr/lib/python2.6/site-packages. Some soft links solved that problem.

The next problem was the error message "proc/xen/capabilities - no such file or directory" when I was trying to find out why xend wasn't running ("/etc/init-d/xend status"). This was fixed by putting the following line into /etc/fstab:

[INDENT]xenfs /proc/xen xenfs defaults 0 0[/INDENT]

And that's as far as I have got because I'm unable to make xend start up and keep running. I guess that I have to compile a newer version of whatever provides xend, but I feel too far out on a limb now. And I have other things to do...

It may be that all my problems would be solved if I just upgraded my dom0 OS from Jaunty to Karmic at this point.  However, that's too great a risk for me at the moment because I rely on this machine for important stuff. I do actually have a domU with Karmic on it, but I can't run it because xend isn't running. And until the Karmic domU runs, I won't feel safe upgrading the dom0.

So, we going to have wait for the happy ending, unless someone can provide some wisdom and words of advice.

Steve

---

### Post by intel352 on 2009-12-18
any luck? having similar error on Ubuntu Server 9.04 upgraded to 9.10, with Rackspace Cloud...

---

### Post by winnall on 2009-12-19
Sorry, I'd reached the point where the next step was to upgrade the dom0 to Karmic without knowing if it would work. I've only got one (physical) machine and if I mess up the dom0, everything dies. So I've put the whole thing on ice for the time being and am sticking with Jaunty.

I must confess that I'm rethinking Ubuntu as my server OS of choice if they're not going to support Xen.

Steve

---

### Post by intel352 on 2009-12-19
really, a better VM platform is VMWare's ESX(i). We use that at work, it's a very thin linux layer that hosts any OS you want, and the client OSes don't have to be customized to even function (which is what we have to do to get Ubuntu guest working with XEN/Hypervisor).

Just FYI, there are two versions, one is ESX, other is ESXi, one of them is a free community release (but I recommend the paid version, as you get an excellent management gui with it).

---

### Post by intel352 on 2009-12-19
damn, just found out that Rackspace's virtualization method doesn't allow you to run a custom kernel. So it keeps trying to load the older kernel from 9.04 with 9.10. Explains why it ignored the newer compiled kernel, had no grub, etc...

wth...

---

### Post by winnall on 2009-12-19
Thanks for the tip about VMWare ESXi. I'll bear it in mind, but since I've only just recently set up my Xen installation, I'd like to give it time to amortise itself. ](*,)

Steve

---

### Post by riedl on 2010-02-06
Hello winnall.  I've been running Xen for a long time on Hardy.  I recently upgraded one of my 'spare' domUs up to karmic, like you.  I had the same problem.  Turns out it's due to a required kernel upgrade: karmic requires at least a 2.6.26 kernel (apparently karmic relies on the /proc/<pid>/mountinfo which is only available in more recent kernels).

The good news is that it's not hard to get your domU to boot with the more recent kernels that come with karmic out of the box.  All you have to do is install the linux-virtual package, which comes with a compiled kernel, initrd, and /lib/modules.  You then copy the kernel and initrd into the /boot of the dom0 (!), and replace the links in your .cfg file for the domU with links to the new kernel and initrd.  I'm happily using the 2.6.31-19-server kernel, and I didn't have to compile anything!

In the interests of full disclosure, though: my console doesn't work still.  I can ssh in, but cannot get xm console to let me login.

Best,
John

---

### Post by winnall on 2010-02-12
Hi John

Thanks for the feedback. I'm busy with something else at the moment, but I'll take a look at it all again when I have time.

Regards
Steve

---

### Post by belgarath@banda.pl on 2010-04-09
there is a guide on how to update from jaunty to karmic and still use PV 
[http://blog.webangel.ie/2010/04/ubuntu-upgrade-to-9-1010-04-for-xen-domu/]("http://blog.webangel.ie/2010/04/ubuntu-upgrade-to-9-1010-04-for-xen-domu/")

---

