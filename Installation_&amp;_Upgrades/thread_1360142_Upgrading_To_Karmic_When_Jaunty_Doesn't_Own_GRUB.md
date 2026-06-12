---
title: "Upgrading To Karmic When Jaunty Doesn't Own GRUB?"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by -kg- on 2009-12-20
The title pretty much says it all.  Here's the situation:

I decided to install a couple of other Linux distros on my laptop for experimentation purposes.  Last night I installed Sabayon and I have a fresh copy of Fedora 12 ready to go on, as well.

I originally intended to do a fresh install of Karmic because Sabayon's GRUB required the /boot partition to be on ext3 and I was unsure whether it would detect my Jaunty installation, which is on ext4 partitions.  It did, and all was well, so I decided instead to install Fedora 12 and do an upgrade from Jaunty to Karmic as an experiment, to see how it would go.  No problem if it doesn't work to my satisfaction...I'll do a fresh install if it doesn't.

Then something occurred to me; if I perform an upgrade to Karmic without Jaunty owning GRUB Stage 1 (in the MBR), will the upgrade process install it's GRUB in the MBR area or will I lose access to it?

I have no problem editing the menu.lst (since I assume the only thing that would change is the kernel version) and I have no problem doing a fresh install if things go awry.  I just want to experiment with doing an upgrade versus a fresh install since I usually do a fresh install when upgrading.  I'll likely do a fresh install after the experiment anyway.

The only reason I ask this is that I haven't installed Fedora yet.  If the upgrade process installs GRUB 2 in the MBR, then I'll probably go ahead an install Fedora now.  However, if it doesn't I'll install it after the upgrade and let Fedora's installer detect it so I can access it and evaluate it.

The only concern I have for my present installation is my BOINC projects.  I have the client set to accept no new projects and once I run them out I'll start the upgrade process.  The rest is (or will be) backed up to external hard drive.

Can I expect any issues?

---

### Post by slakkie on 2009-12-20
Hi, you could have a look at this: [http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/](http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/)

---

### Post by -kg- on 2009-12-20
An excellent idea, and one I should have remembered, though I only knew of it with an OS in control.

I like the idea of an autonomous /boot partition controlled by no one OS and from which you chainload all OSes.  When you add or delete a new OS, all you need to do is edit the menu.lst and add or delete the reference to that OS.

Of course, when you delete an OS (and ostensibly the partition that it's on), you will need to edit all the entries that are affected, since deleting a partition changes the partition numbers of any partition that has a higher number.

One thing confuses me, though.  From the website:

> I created this in one hour or so to be able to have grub-legacy (used by my Ubuntu 9.10 OS) and grub2 (used by Debian testing/unstable) on one system and to have a single bootloader which can boot any OS, without having to worry about anything.

I was under the impression that Karmic used GRUB2, not the legacy GRUB.  I know I'm not mistaken, because I just researched it.  Perhaps I should ask that question on the website itself.

Anyway, thanks, slakkie!

---

### Post by drs305 on 2009-12-20
> **-kg- said:**
> I was under the impression that Karmic used GRUB2, not the legacy GRUB.  I know I'm not mistaken, because I just researched it.  Perhaps I should ask that question on the website itself.

Grub 2 is installed on a clean Karmic install, but if Jaunty is upgraded Grub legacy is retained unless the user chooses to upgrade it.

And it is possible to remove G2 and revert to Grub legacy if the user chooses to do so.

---

### Post by slakkie on 2009-12-20
> **-kg- said:**
> An excellent idea, and one I should have remembered, though I only knew of it with an OS in control.

I like the idea of an autonomous /boot partition controlled by no one OS and from which you chainload all OSes.  When you add or delete a new OS, all you need to do is edit the menu.lst and add or delete the reference to that OS.

Of course, when you delete an OS (and ostensibly the partition that it's on), you will need to edit all the entries that are affected, since deleting a partition changes the partition numbers of any partition that has a higher number.


I normally just install over the old OS (so everything is wiped, but not the partition itself).

> 
One thing confuses me, though.  From the website:

I was under the impression that Karmic used GRUB2, not the legacy GRUB.  I know I'm not mistaken, because I just researched it.  Perhaps I should ask that question on the website itself.


Yes, but like drs305 said, if you upgrade to 9.10 you keep grub-legacy. Debian for example just converts it to grub2 when upgrading from stable to testing.

Ps. I'm the author of that blogpost :)

---

### Post by -kg- on 2009-12-20
Thanks!  This has been an informative thread indeed.

It seems that I have around 4 1/2 hours left on my remaining BOINC task, so once that completes I'm going to give the upgrade a try.  I also found that I installed Sabayon 4.2 when 5.1 is available.  I'm downloading that now via torrent and will reinstall it.

I'm fairly sure that Sabayon 5.1 now uses GRUB2 (talk about grub.conf in the forums), so when I do the reinstall I'll leave the /boot partition created when I installed 4.2 and use it for the method you suggested.

In the mean time, once my BOINC projects are finished I will do the upgrade and see what I end up with.

Thanks again to both of you!

---

