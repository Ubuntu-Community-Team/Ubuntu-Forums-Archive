---
title: "Will kernel 2.6.27 hit Intrepid ?"
date: 2008-08-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Manosdoc on 2008-08-21
Having kernel 2.6.27-rc4 released and rc5 on the way, do you think 2.6.27 will make it to Intrepid ?:guitar:
Kernel freeze is about October and Intrepid is not an LTS.

---

### Post by Lazy79 on 2008-08-21
i do hope that it will hit 8.10 but i do not think it will hit intrepid.. :)

---

### Post by Knowles on 2008-08-21
I doubt it, feature freeze was on the 18th, though I would imagine, some pieces of 27 will get in, most likely security/performances patches.

---

### Post by ssam on 2008-08-21
It was discussed a few days ago, and its possible.
[http://irclogs.ubuntu.com/2008/08/19/%23ubuntu-kernel.html](http://irclogs.ubuntu.com/2008/08/19/%23ubuntu-kernel.html)

2.6.27 has a lot of new wireless drivers, and it would save backporting them. As we are just after an LTS i think intrepid should be experimental and reckless :-)

---

### Post by forger on 2008-08-21
> **Lazy79 said:**
> i do hope that it will hit 8.10 but i do not think it will hit intrepid.. :)

Ubuntu 8.10 's release codename is Intrepid Ibex - what did you mean by that?

---

### Post by caryb on 2008-08-21
I was wondering the same thing:confused: I put it down to me being tired & had penciled that post to be looked at again in the morn with fresh eyes:lolflag:


Cary

---

### Post by lswest on 2008-08-21
Maybe he meant he doubted it would get into the development stage (where it's codename is Intrepid Ibex) and might get into the final (when it's officially given the name 8.10).  Only way I can make sense of it, but I still think it's likely there's a typo or a mistake in the post :P  Would have been much easier to say maybe in the final release, if he did intend it the way I understood it.

My $0.02 on the matter,
Lswest

---

### Post by Teg_Navanis on 2008-08-21
Perhaps a pun on 'hit': [USS Intrepid]("http://en.wikipedia.org/wiki/USS_Intrepid_(CV-11)")

---

### Post by aamukahvi on 2008-08-21
[nevermind/]

---

### Post by Nullack on 2008-08-21
It should have it. Fedora 10 has it and they both release around the same time. There is alot of driver updates in 27 that will make more machines work on linux.

---

### Post by Exsecrabilus on 2008-08-21
I would like 2.6.27 to be included in Intrepid. Keeping with the latest version, I can't complain about that. :P

But just as a side note, I'd like to point out:

Most of you think LTS means extra stability, so the release after an LTS will get new features PLUS the ones held back from the LTS release. So no doubt 8.10 will be unstable and be the perfect time to try out millions of new stuff. This is wrong. An LTS means long-term support, so it receives longer support than other versions.....but it doesn't mean it's extra stable and there are no new features. Take a look at the horrible way the devs implemented PulseAudio, which made many of us frustrated that our sounds weren't working. If they devs thought that "Oh, stability, no new features." they wouldn't have done such a thing. Instead, they thought "It'll get sorted as Hardy matures with bug-fix updates." Also, 8.04 had just as many features as every other version, and many more bugs, if I recall my 8.04 installation days.
I'm not flaming nor flame-bating. It's just that if you look through my posts, I posted a topic on how 8.10 should have been LTS and were firmly told by a few people the same thing I mentioned now. I just remembered it because many of you were talking about Intrepid being "experimental and reckless."

---

### Post by autocrosser on 2008-08-21
Well--it looks like we will see about the next Alpha--I cross my fingers that it is in.....

---

### Post by ssam on 2008-08-21
> 
As many of you know, we've continued a tree called ubuntu-next which is
currently following 2.6.27 upstream kernel. It has been kept in sync
with intrepid's 2.6.26 based kernel tree.

In recent weeks it has become apparent that we will need several updates
to 2.6.26 in order to have a stable kernel for 8.10. These include:

 * Updated mac80211, which will require updated wlan drivers in order 
   to fix major regressions with suspend/resume and wlan devices.
 * Updated alsa-1.0.17 drivers for new codecs
 * xen64 paravirt
 * Updated KVM

These are just the major things we need to do. The good thing is, all of
this is already in 2.6.27, and is ready to be uploaded on a moments
notice. It has been tested by myself for quite some time, and others on
the team have also tested it.

Yesterday, we discussed the possibility of moving to 2.6.27 before
feature freeze on #ubuntu-kernel during out weekly IRC meeting. In
attendance were the kernel team, Steve Langasek, Chuck Short and Soren
Hansen. Soren and Chuck gave particularly good reasons for moving to
2.6.27, which included xen64 and updated KVM.

Steve had questions about the particulars of this move, and I believe we
answered all of his questions satisfyingly, but we agreed to take this
to a wider audience before making a commitment.

So fire away with any concerns or issues that this might cause. If we
are going to do it, it needs to be decided by early next week.

Thanks

Ben Collins
[http://thread.gmane.org/gmane.linux.ubuntu.devel/26242](http://thread.gmane.org/gmane.linux.ubuntu.devel/26242)

---

### Post by Manosdoc on 2008-08-21
As most believe, Intrepid should have the latest 2.6.27
The timeline is good enough to cathc up,even until October.

---

### Post by BC7333 on 2008-08-21
Sooner better than later.. quite a few of my issues could already be resolved. With a couple of alpha's still to come almost perfect timing.

---

### Post by Manosdoc on 2008-08-21
I agree.
Lots of devices will work (specially in Laptops) with native support, and others will be updated too.

Also 2.6.27 has much more improvements like the latest re-write of usb driver

---

### Post by aamukahvi on 2008-08-21
Is Kernel Mode Setting in 2.6.27?

---

### Post by JerecDrak2 on 2008-08-21
> **aamukahvi said:**
> Is Kernel Mode Setting in 2.6.27?

I was wondering this too, I've heard lots of people mention modesetting being in 2.6.27 but I can't find anything about this feature in any "official" documentation...

---

### Post by olskar on 2008-08-21
> **aamukahvi said:**
> Is Kernel Mode Setting in 2.6.27?

It should be

[http://www.phoronix.com/scan.php?page=article&item=kernel_modesetting&num=1](http://www.phoronix.com/scan.php?page=article&item=kernel_modesetting&num=1)

---

### Post by Slug71 on 2008-08-21
Yes bring on 2.6.27!! I see my sound and wireless issues going bye-bye with that.

---

### Post by RAOF on 2008-08-22
> **aamukahvi said:**
> Is Kernel Mode Setting in 2.6.27?

Pretty sure the answer is "no".  It's still in the modesetting-101 branch of drm.  I don't think it's been added to master, let alone the upstream kernel.  I could be wrong, though.

---

### Post by BC7333 on 2008-08-22
Don't suggest trying .27 .. but I did.. works fine here so far, wireless is 'snappier' suggesting some of the wireless fixes.. well.. work.  (intel 3945abg here)

knock knock knock..

---

### Post by gmclachl on 2008-08-22
As far as I know the nvidia drivers will not compile against 2.6.27 unless I think CONFIG_PARAVIRT is set to N 

This could cause a few issues.

George

---

### Post by matthewbpt on 2008-08-22
Is the new Broadcom Wireless driver included in this kernel? I'd really like to stop using ndiswrapper.

---

### Post by Slug71 on 2008-08-22
How do i apply the 2.6.27-rc4 patch?

---

### Post by vishalrao on 2008-08-23
+1 for .27 in Intrepid, if anyone is counting votes :)

---

### Post by plun on 2008-08-23
> **Slug71 said:**
> How do i apply the 2.6.27-rc4 patch?

Just read news from Ben Collins blog, latest in "Kernel Next" is RC3

[http://blog.phunnypharm.org/](http://blog.phunnypharm.org/)

Patches are built upstream
[http://lkml.org/lkml/2008/8/20/316](http://lkml.org/lkml/2008/8/20/316)

[http://lkml.org/lkml/2008/8/22/127](http://lkml.org/lkml/2008/8/22/127)

---

### Post by pferraro on 2008-08-23
FYI...
[http://launchpad.net/distros/ubuntu/intrepid/+source/linux/2.6.27-1.1](http://launchpad.net/distros/ubuntu/intrepid/+source/linux/2.6.27-1.1)

---

### Post by plun on 2008-08-23
> **pferraro said:**
> FYI...
[http://launchpad.net/distros/ubuntu/intrepid/+source/linux/2.6.27-1.1](http://launchpad.net/distros/ubuntu/intrepid/+source/linux/2.6.27-1.1)

Great news 

[http://blog.phunnypharm.org/2008/08/intrepid-ibex-810-moves-to-2627.html](http://blog.phunnypharm.org/2008/08/intrepid-ibex-810-moves-to-2627.html)

> Saturday, August 23, 2008
**Intrepid Ibex (8.10) Moves to 2.6.27**
After considerable discussion on ubuntu-devel mailing list, and in the Ubuntu Kernel Team's last IRC meeting, we've made the move to 2.6.27 for Intrepid in the hopes that it will provide a more robust experience for our users.

The source package was just uploaded to the archive for building, so in about 24 hours, we should so it on mirrors. 

---

### Post by autocrosser on 2008-08-23
I just sent a note to tselliot to ask about the possible problems with 2.6.27 & the new Nvidia drivers--hope to get a answer back in the next 6/12 hrs. Would be good to know if we need to roll our own drivers or if the current driver set will "just work" in the new kernel-------

---

### Post by caryb on 2008-08-23
> amd64 build of linux 2.6.27-1.2 in ubuntu intrepid RELEASE
Build started 17 minutes ago on yellow (amd64) :guitar:


Cary

---

### Post by autocrosser on 2008-08-24
i386 & amd64 builds are done :):):) !!!

[https://launchpad.net/ubuntu/intrepid/+source/linux/2.6.27-1.2](https://launchpad.net/ubuntu/intrepid/+source/linux/2.6.27-1.2)

We "should" start seeing them soon---Also-tselliot is working on the Nvidia drivers. I would wait if you want to use a Nvidia card....looks like a few "issues" need to be worked out.....

[http://thread.gmane.org/gmane.linux.ubuntu.devel/26242](http://thread.gmane.org/gmane.linux.ubuntu.devel/26242)

---

### Post by Nullack on 2008-08-24
Now that RC4 is out the patching of NVIDIA is in Linus' tree so its easier to get it happening. Im looking forward to seeing this enter the Intrepid repos.

---

### Post by plun on 2008-08-24
Yup, a new one is being built

[https://lists.ubuntu.com/archives/intrepid-changes/2008-August/005724.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-August/005724.html)

Mr Molnars patches:
[http://lkml.org/lkml/2008/8/22/127](http://lkml.org/lkml/2008/8/22/127)

I haven't compared changes...:)

---

### Post by BC7333 on 2008-08-24
Good news indeed!

Happy to see Ubuntu moving towards forward rather than backward compatibility.

Ever since Gutsy have been using upgraded kernels with just a few minor glitches.

Says a whole lot for the kernel team..

---

### Post by gmclachl on 2008-08-24
2.6.27-rc4 didn't have the patch for nvidia in it, however Linus's tree has and I noticed that the ubuntu-next tree has it as well. So hopefully we will be able to build the nvidia drivers against it. 

George

---

### Post by hexion on 2008-08-24
It's official now. In 24 hours the new images will hit the repos :guitar:

[http://blog.phunnypharm.org/2008/08/intrepid-ibex-810-moves-to-2627.html](http://blog.phunnypharm.org/2008/08/intrepid-ibex-810-moves-to-2627.html)

---

### Post by olskar on 2008-08-24
Yay, does this also fix the problem with not being able to run Intrepid in VirtualBox?

---

### Post by Slug71 on 2008-08-24
This is awesome news!

---

### Post by Nullack on 2008-08-24
The build failed on the build farm so it'll take a bit more before we can test it.

[https://launchpad.net/ubuntu/+source/linux/2.6.27-1.1/+build/699341](https://launchpad.net/ubuntu/+source/linux/2.6.27-1.1/+build/699341)

---

### Post by blackphiber on 2008-08-24
> **Nullack said:**
> The build failed on the build farm so it'll take a bit more before we can test it.

[https://launchpad.net/ubuntu/+source/linux/2.6.27-1.1/+build/699341](https://launchpad.net/ubuntu/+source/linux/2.6.27-1.1/+build/699341)

[https://launchpad.net/ubuntu/+source/linux/2.6.27-1.2/+build/699405](https://launchpad.net/ubuntu/+source/linux/2.6.27-1.2/+build/699405)

---

### Post by caryb on 2008-08-24
That is only the amd64 version, to my knowledge it has to complete across the board before it is released.


Cary

---

### Post by autocrosser on 2008-08-24
Looks like only i386 & amd64 built---

[https://launchpad.net/ubuntu/+source/linux/2.6.27-1.2](https://launchpad.net/ubuntu/+source/linux/2.6.27-1.2)

---

### Post by Exsecrabilus on 2008-08-25
> **caryb said:**
> That is only the amd64 version, to my knowledge it has to complete across the board before it is released.


Cary
Nullack pointed out the amd64 version failed, so Blackphiber countered it with a success of the amd64. The other version is irrelevant, as they are posting about the amd64 version.

---

### Post by Slug71 on 2008-08-25
Hopefully we may see it today

---

### Post by autocrosser on 2008-08-25
Well--Matt Z has raised objections to the move--I'm pasting the thread from devel-list.  Let's keep our fingers crossed that Ben has good answers----

On Wed, Aug 20, 2008 at 04:02:47PM -0400, Ben Collins wrote:
[INDENT]> As many of you know, we've continued a tree called ubuntu-next which is
> currently following 2.6.27 upstream kernel. It has been kept in sync
> with intrepid's 2.6.26 based kernel tree.
[/INDENT]
I have been in all-day meetings this past week and did not see this thread
until now.  I think this change requires stronger justification than I've
seen so far.

[INDENT]> In recent weeks it has become apparent that we will need several updates
> to 2.6.26 in order to have a stable kernel for 8.10. These include:
> 
>  * Updated mac80211, which will require updated wlan drivers in order 
>    to fix major regressions with suspend/resume and wlan devices.
>  * Updated alsa-1.0.17 drivers for new codecs
>  * xen64 paravirt
>  * Updated KVM
> 
> These are just the major things we need to do.
[/INDENT]
Why are these needed in order to have a stable kernel for 8.10?  Major
updates are the opposite of stability.  What we want is a kernel which fixes
more bugs than it introduces while introducing the most important driver
updates we need for the release.

[INDENT]> The good thing is, all of this is already in 2.6.27, and is ready to be
> uploaded on a moments notice. It has been tested by myself for quite some
> time, and others on the team have also tested it.
[/INDENT]
The amount of testing it has received is trivial compared to what 2.6.26 has
seen.  It's been tested on our certified systems and by many thousands of
community members on their own hardware.  The fact that it's been smoke
tested by a few people doesn't give me much confidence that it's free of
serious regressions.

[INDENT]> Yesterday, we discussed the possibility of moving to 2.6.27 before
> feature freeze on #ubuntu-kernel during out weekly IRC meeting. In
> attendance were the kernel team, Steve Langasek, Chuck Short and Soren
> Hansen. Soren and Chuck gave particularly good reasons for moving to
> 2.6.27, which included xen64 and updated KVM.
[/INDENT]
Where can I find the summary and log of the meeting?

[INDENT]> Steve had questions about the particulars of this move, and I believe we
> answered all of his questions satisfyingly, but we agreed to take this
> to a wider audience before making a commitment.
> 
> So fire away with any concerns or issues that this might cause. If we
> are going to do it, it needs to be decided by early next week.
[/INDENT]
I was in meetings all week and didn't see this until now.  Mario has raised
a concern in this thread which I think needs to be addressed.  I also have
the following questions:

What are the known regressions from 2.6.26 to 2.6.27?

Which systems has 2.6.27 been tested on?  What test plan was followed?

In which areas are further regressions to be expected in 2.6.27 (which parts
of the kernel have changed in the most significant ways)?

What were the results of certification testing with 2.6.27?

-- 
 - mdz

---

### Post by Slug71 on 2008-08-25
Well i wish they would release the I386 and AMD64 kernels, this way it will be on a lot more systems for testing. Or at least make it available for those that do want to try it. I just want my wireless working which means i can use my printer too. My roommates will be a lot happier too since they dont have to and ask to plug the router in all the time.

---

### Post by bpl07 on 2008-08-25
> **Slug71 said:**
> Well i wish they would release the I386 and AMD64 kernels, this way it will be on a lot more systems for testing. Or at least make it available for those that do want to try it.

You can get the builds from the [ubuntu next server]("http://kernel.ubuntu.com/pub/next/2.6.27-rc3/").  I've been running the AMD64 rc3 release for a week or so now, everything is working great.  Make sure you get the debs from the "all" section as well, which include updates to libc6-dev and the linux-headers required to install the generic/server headers.

---

### Post by plun on 2008-08-25
> **autocrosser said:**
> Well--Matt Z has raised objections to the move--I'm pasting the thread from devel-list.  Let's keep our fingers crossed that Ben has good answers----



Well, just to read for everyone.

[https://lists.ubuntu.com/archives/ubuntu-devel/2008-August/thread.html](https://lists.ubuntu.com/archives/ubuntu-devel/2008-August/thread.html)

It would be really sad to drop 2.6.27 because one important goal for Intrepid is a normal user which just wants a working wireless PC everywhere

> A particular focus for us will be **pervasive internet access**, the ability to tap into bandwidth whenever and wherever you happen to be. No longer will you need to be a tethered, domesticated animal -you'll be able to roam (and goats do roam!) the wild lands and
access the web through a variety of wireless technologies. We want
you to be able to move from the office, to the train, and home,
staying connected all the way.
[https://lists.ubuntu.com/archives/ubuntu-devel/2008-February/025136.html](https://lists.ubuntu.com/archives/ubuntu-devel/2008-February/025136.html)


Mr Collins gave good answers anyway....:)

---

### Post by jfernyhough on 2008-08-25
Has anyone has 2.6.27 working with Nvidia blobs and DKMS? I've tried both kernelcheck and the ubuntu-next images and the DKMS build process fails for each.

---

### Post by plun on 2008-08-25
> **jfernyhough said:**
> Has anyone has 2.6.27 working with Nvidia blobs and DKMS? I've tried both kernelcheck and the ubuntu-next images and the DKMS build process fails for each.

Nope... all patches fails for me.  :^o

Within nvnews you have 2 threads, one OpenSuse RC3 and one RC1 thread with several patches, within this forum you have Amaranths Zen patch which also fails.

No answer from Linus if this is merged ???[http://lkml.org/lkml/2008/8/22/127](http://lkml.org/lkml/2008/8/22/127)

Our kernel team fixes this.....:)

---

### Post by gmclachl on 2008-08-25
I really think the biggest issue here is the wireless drivers. We face a regression. There are going to be a lot of people whose wireless worked in hardy (with a bit of tinkering) to not working at all. That will leave a lot of people unhappy, it is after all one of the major gripes with users.

While I can agree with Matt Z to a certain extent about the lack of testing, surely this is the point of "Alpha" releases. I think we should push forward with 2.6.27* 

* I have been using ubuntu-next and torvalds git tree and haven't faced any issues, so I may be biased.

George

---

### Post by mc4100 on 2008-08-25
2.6.27 is working flawlessly with Intel 3945 ABG, finally!
No issues I can see.

---

### Post by Slug71 on 2008-08-25
> **bpl07 said:**
> You can get the builds from the [ubuntu next server]("http://kernel.ubuntu.com/pub/next/2.6.27-rc3/").  I've been running the AMD64 rc3 release for a week or so now, everything is working great.  Make sure you get the debs from the "all" section as well, which include updates to libc6-dev and the linux-headers required to install the generic/server headers.

Got these installed fine
linux-image-2.6.27-1-generic_2.6.27-1.1_amd64.deb
linux-libc-dev_2.6.27-1.1_amd64.deb

but 
linux-headers-2.6.27-1-generic_2.6.27-1.1_amd64.deb

would not install

---

### Post by caryb on 2008-08-25
It worked but CGA graphics went out in the 80's:lolflag: I guess I will wait for Nvidia support before I try again.


Cary

---

### Post by jfernyhough on 2008-08-25
> **Slug71 said:**
> Got these installed fine
linux-image-2.6.27-1-generic_2.6.27-1.1_amd64.deb
linux-libc-dev_2.6.27-1.1_amd64.deb

but 
linux-headers-2.6.27-1-generic_2.6.27-1.1_amd64.deb

would not installYou also need [linux-headers-2.6.27-1_2.6.27-1.1_all.deb](http://kernel.ubuntu.com/pub/next/2.6.27-rc3/all/linux-headers-2.6.27-1_2.6.27-1.1_all.deb) installed, there's a dependency.

---

### Post by Slug71 on 2008-08-25
Thanks, that did it.

---

### Post by Slug71 on 2008-08-25
Still no freakin wireless for me!

---

### Post by DougieFresh4U on 2008-08-25
Thanks to all who posted various links.
Works for me, as well as wireless :)

---

### Post by Slug71 on 2008-08-25
I think my configuration is messed up, when i enter the command alsamixer it still says v1.0.16 and not v1.0.17 too.

---

### Post by syko21 on 2008-08-26
Is the rc3 kernel from the ubuntu next tree the latest build? Mine kernel panic's a lot even when I'm not doing anything on the machine.

Core 2 Duo T5600 1.83 Ghz
Nvidia 7400 Go
Intel 4965

PS> Is there an expected time we can see this hitting the repositories?

---

### Post by Nullack on 2008-08-26
Clearly there is some issues needing to be worked out before it arrives into the repos. However I think sticking with .26 would be a huge mistake.

---

### Post by BC7333 on 2008-08-26
> **Slug71 said:**
> Still no freakin wireless for me!

Which card do you have?  Maybe it is being addressed here:

[http://linuxwireless.org/en/users/Drivers](http://linuxwireless.org/en/users/Drivers)

One thing I noted is that I have to turn my wireless card on during boot using Fn-F8  If you have a laptop you might have a similar key combo to turn yours on.

---

### Post by Slug71 on 2008-08-26
> **BC7333 said:**
> Which card do you have?  Maybe it is being addressed here:

[http://linuxwireless.org/en/users/Drivers](http://linuxwireless.org/en/users/Drivers)

One thing I noted is that I have to turn my wireless card on during boot using Fn-F8  If you have a laptop you might have a similar key combo to turn yours on.

Yes it is there, the B43/B43Legacy. I have the Broadcom 4310 USB controller (Rev01).
And yes i am using a laptop.

---

### Post by Slug71 on 2008-08-26
Hmmm, just read through the notes under the b43/b43legacy and it appears the BCM4310 is not yet supported. That blows.

---

### Post by plun on 2008-08-26
> **Slug71 said:**
> Hmmm, just read through the notes under the b43/b43legacy and it appears the BCM4310 is not yet supported. That blows.

"Fwiw"....   b43-fwcutter was updated today.

[https://lists.ubuntu.com/archives/intrepid-changes/2008-August/005792.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-August/005792.html)

---

### Post by Ub1476 on 2008-08-26
I hope they get to use the .27 kernel. It supports the new INTEL GMA x4500 which .26 doesn't, which is important I think. I'll be installing the Alpha as soon as I get my laptop Septemer 6th.

---

### Post by BC7333 on 2008-08-26
> **Slug71 said:**
> Yes it is there, the B43/B43Legacy. I have the Broadcom 4310 USB controller (Rev01).
And yes i am using a laptop.

Then chances are that the problem has already been addressed and resolved.  Might want to try compiling from compatwireless.

I guess the compatwireless work will all merge into intrepid soon.

---

### Post by Slug71 on 2008-08-26
Yeh it said they were busy with it and Plun said earlier the b43-fwcutter was updated today. So ill give that a shot.

---

### Post by jfernyhough on 2008-08-26
Grr... I downloaded the 2.6.27-1 source from launchpad and had just finished compiling when the binaries were made available. Typical. Anyhow, nvidia still complains about multiple versions in DKMS. Gah.

---

### Post by plun on 2008-08-26
> **jfernyhough said:**
> Grr... I downloaded the 2.6.27-1 source from launchpad and had just finished compiling when the binaries were made available. Typical. Anyhow, nvidia still complains about multiple versions in DKMS. Gah.

Well... you are not alone with the PC filled with blobs...:)

```
plun@dunder:~$ **locate nvidia.ko**
/home/plun/.local/share/Trash/files/NVIDIA-Linux-x86_64-177.13-pkg2/usr/src/nv/.nvidia.ko.cmd
/home/plun/.local/share/Trash/files/NVIDIA-Linux-x86_64-177.13-pkg2/usr/src/nv/nvidia.ko
/lib/modules/2.6.26-3-generic/kernel/drivers/video/nvidia/nvidia.ko
/lib/modules/2.6.26-3-generic/updates/dkms/nvidia.ko
/lib/modules/2.6.26-5-generic/kernel/drivers/video/nvidia.ko
/lib/modules/last-good-boot/updates/dkms/nvidia.ko
/var/lib/dkms/nvidia/177.13/2.6.26-5-generic/i686/module/nvidia.ko
/var/lib/dkms/nvidia/177.13/build/.nvidia.ko.cmd
/var/lib/dkms/nvidia/177.13/build/nvidia.ko
/var/lib/dkms/nvidia/177.67/2.6.26-5-generic/i686/module/nvidia.ko
/var/lib/dkms/nvidia/177.67/build/.nvidia.ko.cmd
/var/lib/dkms/nvidia/177.67/build/nvidia.ko
/var/lib/dkms/nvidia/177.68/2.6.26-5-generic/i686/module/nvidia.ko
/var/lib/dkms/nvidia/177.68/build/.nvidia.ko.cmd
/var/lib/dkms/nvidia/177.68/build/nvidia.ko
/var/lib/dkms/nvidia/original_module/2.6.26-3-generic/i686/collisions/kernel/drivers/video/nvidia.ko
/var/lib/dkms/nvidia/original_module/2.6.26-3-generic/i686/collisions/kernel/drivers/video/nvidia/nvidia.ko
/var/lib/dkms/nvidia/original_module/2.6.26-5-generic/i686/collisions/kernel/drivers/video/nvidia.ko
/var/lib/dkms/nvidia/original_module/2.6.26-5-generic/i686/collisions/updates/dkms/nvidia.ko

```

Driver removal

```
sudo sh NVIDIA-Linux-x86-177.68-pkg1.run --uninstall
```

Time for restart....:lolflag:

---

### Post by plun on 2008-08-26
Well.. no restart... be careful..

```
The following NEW packages will be installed
  nvidia-glx-177
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/8563kB of archives.
After this operation, 24.9MB of additional disk space will be used.
(Reading database ... 348447 files and directories currently installed.)
Unpacking nvidia-glx-177 (from .../nvidia-glx-177_177.68-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/nvidia-glx-177_177.68-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libGL.so.1', which is also in package libgl1-mesa-glx
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-177_177.68-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

:---)

EDIT

- Forced overwrite

- nVidia-glx-177 broken> failsafe start

- tty > install nVidias driver > Ok

- High CPU

- Everything works

- envyng-core was just upgraded...!  Broken >  [https://bugs.launchpad.net/ubuntu/+source/envyng-gtk/+bug/261656](https://bugs.launchpad.net/ubuntu/+source/envyng-gtk/+bug/261656)

- Jockey broken

- Sound crackling

- Graphic distorsion....

---

### Post by caryb on 2008-08-26
In the same vein...

Setting up linux-headers-2.6.27-1 (2.6.27-1.2) ...
Setting up linux-headers-2.6.27-1-generic (2.6.27-1.2) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.27-1-generic
 *  nvidia (177.68)...nvidia: Multiple versions in DKMS. Unsure what to do. Resolve manually


Cary

---

### Post by jfernyhough on 2008-08-26
> **plun said:**
> Well... you are not alone with the PC filled with blobs...:)

```
plun@dunder:~$ **locate nvidia.ko**
/var/lib/dkms/nvidia/177.13/build/nvidia.ko
/var/lib/dkms/nvidia/177.67/build/nvidia.ko
/var/lib/dkms/nvidia/177.68/build/nvidia.ko

```

GENIUS!!!

Deleted the extraneous directories for non-existent drivers (177.13, 177.67), triggered a reinstall of 2.6.27-1, and BINGO, module built perfectly.

cd /var/lib/dkms/nvidia
sudo rm -fR 177.13 177.67
sudo aptitude reinstall linux-image-2.6.27-1-generic

---

### Post by plun on 2008-08-26
> **jfernyhough said:**
> GENIUS!!!



Well, all credits to "tseliot" aka Alberto within another tread....:)

[http://ubuntuforums.org/showpost.php?p=5385241&postcount=49](http://ubuntuforums.org/showpost.php?p=5385241&postcount=49)


Going todo the same as you.....

EDIT

Thanks !

The sphere is alive....
[[img]http://ubuntu-pics.de/thumb/2479/aliveRAS7B.jpg[/img]](http://ubuntu-pics.de/bild/2479/aliveRAS7B.jpg):lolflag:

---

### Post by plun on 2008-08-27
Bug filed against multiple versions in DKMS

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/261816](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/261816)

---

### Post by autocrosser on 2008-08-27
Looks like Matt Z is on board with the kernel change!!  From devel-list:



Date: Tue, 26 Aug 2008 17:43:58 +0100
From: Matt Zimmerman
Subject: Re: Re: Re: [RFC] Moving Intrepid to 2.6.27 kernel
To: Ubuntu Devel [EMAIL="ubuntu-devel@lists.ubuntu.com"]<ubuntu-devel@lists.ubuntu.com>[/EMAIL]
Message-ID: [EMAIL="20080826164358.GH17693@alcor.net"]<20080826164358.GH17693@alcor.net>[/EMAIL]
Content-Type: text/plain; charset=us-ascii

On Tue, Aug 26, 2008 at 09:25:06AM -0700, Jeff Schroeder wrote:
[INDENT]> On Tue, Aug 26, 2008 at 8:59 AM,  [EMAIL="ubuntu-devel-request@lists.ubuntu.com"]<ubuntu-devel-request@lists.ubuntu.com>[/EMAIL] wrote:
[INDENT]> > From: Matt Zimmerman
> > Subject: Re: Re: [RFC] Moving Intrepid to 2.6.27 kernel
> >
> > On Mon, Aug 25, 2008 at 05:47:46AM -0700, Jeff Schroeder wrote:
[INDENT]> >> On Mon, Aug 25, 2008 at 4:00 AM,  [EMAIL="ubuntu-devel-request@lists.ubuntu.com"]<ubuntu-devel-request@lists.ubuntu.com>[/EMAIL] wrote:
[INDENT]> >> > I was in meetings all week and didn't see this until now.  Mario has raised
> >> > a concern in this thread which I think needs to be addressed.  I also have
> >> > the following questions:
[/INDENT]> >>
> >> Mario's concern is bunk with commit
> >> 7946612de2087e163308e26034286fc2dc9dacf1 fyi.
> >> [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=7946612de2087e163308e26034286fc2dc9dacf1](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=7946612de2087e163308e26034286fc2dc9dacf1)
[/INDENT]> >
> > I assume you mean that his concern is in fact valid, but will be addressed
> > when we bring this patch into our 2.6.27 tree.  Thanks for confirming this.
[/INDENT]> 
> Well I'd kind of assumed that you guys will be basing the final kernel
> off of a stable
> kernel.org release and not a -rcX. That would infer that the above
> patch will be pulled in  :) 
[/INDENT]
Of course we will aim to ship the final 2.6.27, but with a release date
looming, the fact that something should be fixed as we track upstream
doesn't mean that we can stop paying attention to it.

If possible, we should avoid breaking this in Intrepid in the first place,
rather than breaking it and fixing it later.

[INDENT]> Is there anyway to add in a whitelist of people who post constructive
> comments and don't have the time to become full on core-devs? The
> moderation is really annoying and I'm not posting spam to the lists. Can
> you talk to the other Canonical-ers about this?
[/INDENT]
There is supposed to be; exactly this has been intended from the start.
There seem to be some problems with the implementation, though, and there's
a ticket open with the Canonical IS team about it (#26726).

-- 
 - mdz

---

### Post by gmclachl on 2008-08-27
I am not quite sure what the concern is over this patch. It has made it's way into the torvalds git tree.

I wonder if it is a technical concern? Can't see how.

George

---

### Post by plun on 2008-08-27
> **gmclachl said:**
> I am not quite sure what the concern is over this patch. It has made it's way into the torvalds git tree.

I wonder if it is a technical concern? Can't see how.

George

Well...  "mdz" has a position and obligation to ask about development issues.

In this case I am rather sure that Linus T  himself hunting down all regressions... he has been rather "wild" last days...just to read lkml.org  :oops:

And... most important, We MUST file bugs during/before we are solving issues.

---

### Post by gmclachl on 2008-08-27
> **plun said:**
> Well...  "mdz" has a position and obligation to ask about development issues.

In this case I am rather sure that Linus T  himself hunting down all regressions... he has been rather "wild" last days...just to read lkml.org  :oops:

And... most important, We MUST file bugs during/before we are solving issues.

I am sure he has however my point was to why he thought it was an issue. It wasn't even a question directed at him but more a case of thinking out loud. 

George

---

### Post by plun on 2008-08-27
> **gmclachl said:**
> I am sure he has however my point was to why he thought it was an issue. It wasn't even a question directed at him but more a case of thinking out loud. 

George

OK... who knows ?  , if you are chairman of [Ubuntus technical board]("https://launchpad.net/~mdz") you can perhaps ask whatever you want...:)  No meaning to speculate either.


I am also rather sure that this decision has a great community support and
that Intrepid will be absolutely great....

[IMG]http://www.ubuntu-pics.de/counter/[/IMG]

---

### Post by fluteflute on 2008-08-27
> The following NEW packages will be installed:
  kbd-compat{a} linux-headers-2.6.27-1{a} linux-headers-2.6.27-1-generic{a} 
  linux-image-2.6.27-1-generic{a} 
  linux-restricted-modules-2.6.27-1-generic{a} 
The following packages will be upgraded:
  language-selector language-selector-common linux-generic 
  linux-headers-generic linux-image-generic linux-restricted-modules-common 
  linux-restricted-modules-generic nvidia-common ubuntu-desktop 
  ubuntu-minimal ubuntu-standard ufw 

It's here!

---

### Post by ViRMiN on 2008-08-27
> **fluteflute said:**
> It's here!

I'm running it now, but, struggling to get VMware working... ah, the fun of alpha's, can't beat it!

---

### Post by Nullack on 2008-08-27
> **jfernyhough said:**
> GENIUS!!!

Deleted the extraneous directories for non-existent drivers (177.13, 177.67), triggered a reinstall of 2.6.27-1, and BINGO, module built perfectly.

cd /var/lib/dkms/nvidia
sudo rm -fR 177.13 177.67
sudo aptitude reinstall linux-image-2.6.27-1-generic

Or for those on apt-get instead:

```
sudo apt-get install --reinstall linux-image-2.6.27-1-generic
```

---

### Post by klange on 2008-08-27
Updating right now...
Installing...

---

### Post by taavikko on 2008-08-27
> **Nullack said:**
> Or for those on apt-get instead:

```
sudo apt-get install --re-install linux-image-2.6.27-1-generic
```

Hmm, why "--re-install"?
wouldn't "--reinstall" work much better ;)

---

### Post by plun on 2008-08-27
nVidia DKMS bug is triaged and Alberto works with it

[https://bugs.launchpad.net/bugs/261816](https://bugs.launchpad.net/bugs/261816)

just to reinstall after "blob" removal  :)

---

### Post by Nullack on 2008-08-27
> **taavikko said:**
> Hmm, why "--re-install"?
wouldn't "--reinstall" work much better ;)

Typo fixed :)

---

### Post by Steveway on 2008-08-27
Well, I rebuild the nouveau driver like usual but it doesn't seem to work yet. dmesg spits out a lot of errors like those:
> [  186.840017] nouveau: disagrees about version of symbol drm_get_resource_start
[  186.840017] nouveau: Unknown symbol drm_get_resource_start
[  186.840017] nouveau: Unknown symbol drm_cleanup_pci
[  186.840017] nouveau: disagrees about version of symbol drm_core_ioremap
[  186.840017] nouveau: Unknown symbol drm_core_ioremap
[  186.841821] nouveau: disagrees about version of symbol drm_rmmap
[  186.841856] nouveau: Unknown symbol drm_rmmap
[  186.841999] nouveau: Unknown symbol drm_bo_move_accel_cleanup

Well, that means nv-driver until that is fixed.

---

### Post by gmclachl on 2008-08-27
I seem to have spoken too soon. I have been running 2.7.27 from git and ubuntu-next without any problems. I updated and x is far from happy 

 5227 root      20   0  104m  36m  10m R   63  1.6  11:13.10 Xorg  


 It's using up a lot of CPU cycles


 *EDIT* Another reboot seems to have done the trick. 
George

---

### Post by Nullack on 2008-08-27
> **plun said:**
> nVidia DKMS bug is triaged and Alberto works with it

[https://bugs.launchpad.net/bugs/261816](https://bugs.launchpad.net/bugs/261816)

just to reinstall after "blob" removal  :)

Excellent work there Plun! :)

---

### Post by nanog on 2008-08-27
So far wireless (iwl3945), suspend, hibernate, nvidia(8400gs), compiz, function keys etc. working fine with 2.6.27.1 on a m1330 amd64. At least on my test laptop this is a notable improvement over 2.6.26.

---

### Post by Slug71 on 2008-08-27
Well just did updates an hour or so ago and now my wireless card is working but im still not able to connect. Im using WAP and MAC filtering.

When i run Update Manager now i also keept getting the message, Not all updates can be installed please do partial upgrade.

---

### Post by plun on 2008-08-27
> **Nullack said:**
> Excellent work there Plun! :)

Well, we are a **group** of crazy testers, maintainers and developers which cannot be stopped....:biggrin:

---

### Post by gmclachl on 2008-08-27
> **Slug71 said:**
> Well just did updates an hour or so ago and now my wireless card is working but im still not able to connect. Im using WAP and MAC filtering.

When i run Update Manager now i also keept getting the message, Not all updates can be installed please do partial upgrade.

I couldn't get ath9k working with WEP had to fall back to mac address filtering only

*Edit* 
I just noticed that the ath9k module was not loaded. I was using ath5k, which didn't work for me in 2.6.26. Anyway I added ath9k to /etc/modules and rebooted and the difference in signal is staggering. 


George

---

### Post by Slug71 on 2008-08-27
disabled the WAP and wireless is working.

---

### Post by caryb on 2008-08-27
After deleting the 2nd Nvidia file as per previous post & reloading the kernel I have...
uname -a
Linux stinkpad 2.6.27-1-generic #1 SMP Sat Aug 23 23:19:01 UTC 2008 x86_64 GNU/Linux

With full graphics, wireless etc:)


Cary

---

### Post by Gourgi on 2008-08-27
just install 2.6.27 and i have a 800x600 resolution in my screen :(
i used nvidia-glx-177 in 2.6.26.5 kernel with no problems to my 6600gt, any suggestions?
nvidia's beta .run installer warns me about running a Xen kernel and exits.
also, jockey is still broken?

also after X warned me about running low resolution i tried using nv with my screen's native resolution but i'm stuck with 800x600. 

damn! no cube :lolflag:

--------
[COLOR="Red"]EDIT[/COLOR]: i nv is finally working correct @ 1680x1050, no update for nvidia driver but i found this thread [http://ubuntuforums.org/showthread.php?t=902887](http://ubuntuforums.org/showthread.php?t=902887) , i 'll wait some updates there too 

damn! no cube [COLOR="Red"]yet[/COLOR] :lolflag:
[COLOR="Red"]
jockey is still broken?[/COLOR]

---------
[COLOR="Orange"]Edit2 : [/COLOR] jockey is "working" (says i use nvidia but i'm still in nv! ) after installing nvidia-177-modaliases

---

### Post by caryb on 2008-08-27
On page 2 I found this from jfernyhough that worked!

> Deleted the extraneous directories for non-existent drivers (177.13, 177.67), triggered a reinstall of 2.6.27-1, and BINGO, module built perfectly.

cd /var/lib/dkms/nvidia
sudo rm -fR 177.13 177.67
sudo aptitude reinstall linux-image-2.6.27-1-generic

---

### Post by GuitarRocker2562 on 2008-08-27
Omg, my wireless "just works". Since I have been using NM 0.7 I have been unable to reconnect to my WPA network, now it works!

---

### Post by autocrosser on 2008-08-27
I'm in--all "seems" to work well--will post with any probs (if I have any ;)  ).

Update: "seems" to be less crash-able that the .26 kernel--I would have crashed at least once by now---so far, so good.......

---

### Post by stari4ek on 2008-08-28
can anyone send me files from /etc/kernel/postinst.d, I've ruined it =(
or maybe the name of package, which provide all scripts from it? 

thanx in advance.

---

### Post by stari4ek on 2008-08-28
I have some weird problems with booting to 2.7.1.
my system hangs at starting linux-restricted-modules-common during early boot (S0 stage). If I disable it (chmod -x) system starts well. nvidia driver works, etc...

I've checked script - it calls lrm-manager --quick on start.
If I run 
$lrm-manager
after some work and updating initram it finishes
but if i call
$lrm-manager --quick
it hangs system with 100% cpu load.

Does anybody have the same problem?

---

### Post by nanog on 2008-08-28
Ooops...suspend stopped working. Anyone else have this problem? (I may have tweaked acpi settings and broken something.)

---

### Post by jbernardo on 2008-08-28
I've had quite a few hangs at boot on a Aspire One with 2.6.27, after the "Setting System Clock" log entry. If I remove the "Quiet" option from the kernel command line, it boots without any more problems. Also, the Atheros drivers are still quite unstable, the latest madwifi snapshot works a lot better.

---

### Post by aamukahvi on 2008-08-28
My rtl8168 started working again :) (didn't work on 2.6.26 without from-source-compiled drivers).

---

### Post by klange on 2008-08-28
I get some problems during boot.
First time I booted 27, I saw a crash and a stacktrace shortly after caching boot files.
Today I booted to a freeze when setting the clock, then rebooted to the same crash and stacktrace.

---

### Post by Slug71 on 2008-08-28
Finally im 2.6.27 seems to be in my favour. Wireless is working sweet, which has allowed me to install my printer and finally my integrated mic is also working.

Hopefully they'll fix WPA and WEP soon so i can reinable my WPA.

---

### Post by plun on 2008-08-28
From Ben Collins and the kernel team

> **Call for testing of 2.6.27 kernel in Intrepid**

As you may have noticed, we've moved to a 2.6.27 kernel in Intrepid this 
week. We'd like to ask everyone to really give it a good kicking around 
to ensure we aren't introducing major regressions from 2.6.26.

If you have problems with this kernel, and the problem doesn't exist in 
2.6.26, please note that in any bug reports you file.

Thanks from the Ubuntu Kernel Team

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-August/000476.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-August/000476.html)



---

### Post by ssam on 2008-08-28
> **WindowsSucks said:**
> I get some problems during boot.
First time I booted 27, I saw a crash and a stacktrace shortly after caching boot files.
Today I booted to a freeze when setting the clock, then rebooted to the same crash and stacktrace.

do you have a digital camera? if so please photograph the message and report a bug.

---

### Post by InfinityCircuit on 2008-08-28
> **stari4ek said:**
> can anyone send me files from /etc/kernel/postinst.d, I've ruined it =(
or maybe the name of package, which provide all scripts from it? 

thanx in advance.

Are you sure about that?

```

dmr@hyperion:/proc$ dpkg -S /etc/kernel/postinst.d
dpkg: /etc/kernel/postinst.d not found.
dmr@hyperion:/proc$ cd /etc/kernel/
dmr@hyperion:/etc/kernel$ ls
prerm.d
dmr@hyperion:/etc/kernel$ uname -a
Linux hyperion 2.6.27-1-generic #1 SMP Sat Aug 23 23:20:09 UTC 2008 i686 GNU/Linux

```

---

### Post by stari4ek on 2008-08-28
> **InfinityCircuit said:**
> Are you sure about that?

```

dmr@hyperion:/proc$ dpkg -S /etc/kernel/postinst.d
dpkg: /etc/kernel/postinst.d not found.
dmr@hyperion:/proc$ cd /etc/kernel/
dmr@hyperion:/etc/kernel$ ls
prerm.d
dmr@hyperion:/etc/kernel$ uname -a
Linux hyperion 2.6.27-1-generic #1 SMP Sat Aug 23 23:20:09 UTC 2008 i686 GNU/Linux

```

find /etc/kernel
/etc/kernel
/etc/kernel/header_postinst.d
/etc/kernel/header_postinst.d/dkms
/etc/kernel/header_postinst.d/nvidia-common
/etc/kernel/postinst.d
/etc/kernel/prerm.d
/etc/kernel/prerm.d/dkms
/etc/kernel/prerm.d/last-good-boot

and i remember, that i had 2 files in postinst.d, before i killed them =). something about nvidia
as result nvidia driver doesn'r recompiles on kernel change - i force through reinstalling nvidia package

---

### Post by wilbur.harvey on 2008-08-28
I have been trying to get my vmware server running with the latest 2.6.27 kernel(from yesterday)

First I get this:
Your kernel was built with "gcc" version "4.3.1", while you are trying to use "/usr/bin/gcc" version "4.3.2".

Then I get this:
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/./include/x86.h:38,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:101:
/tmp/vmware-config1/vmmon-only/./include/x86paging.h:76:1: warning: "PTE_PFN_MASK" redefined

Then I get this:
In file included from /tmp/vmware-config1/vmmon-only/linux/vmhost.h:27,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:121:
/tmp/vmware-config1/vmmon-only/./include/compat_semaphore.h:23:27: error: asm/semaphore.h: No such file or directory
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-1-generic'

I assume we will get a new kernel compiled with the current compiler soon, but I don't think that is the problem.

---

### Post by InfinityCircuit on 2008-08-29
vmware will take manual patching to work with 2.6.27 at the moment, as far as I know.

To fix the previous problem with nvidia you should reinstall the nvidia drivers with "-o DPkg::Options::="--force-confmiss --force-confnew""

---

### Post by Gina on 2008-08-29
(Repeating much of what I wrote in another thread but applies here too) 

No joy booting after updating to kernel 27.1 (on P4 machine).  Hangs early on for a considerable time - went away and left it a while.  When I came back it had changed to text mode and stopped at "Starting Bluetooth".  Went away again but after the best part of an hour it was still the same.  Ctrl-Alt-Del worked and started shut down process but everything stopped again at "Stopping Bluetooth" and Ctrl-Alt-Del just repeated the above.  The only way out was a power-off.  Will be investigating later when I have time.

---

### Post by gjoellee on 2008-08-29
check this out :)
> ubuntu@ubuntu-desktop:~$ uname -r
2.6.27-1-generic

---

### Post by ViRMiN on 2008-08-29
XXX@XXX:~$ uname -a
Linux XXX.XXX 2.6.27-2-generic #1 SMP Thu Aug 28 17:18:43 UTC 2008 x86_64 GNU/Linux

:tongue:

---

### Post by gjoellee on 2008-08-29
update just came!
 	Quote:
 	 	 		 			 				ubuntu@ubuntu-desktop:~$ uname -r
2.6.27-2-generic

---

### Post by andyrogers2008 on 2008-08-29
Hi All

I am new to this Ubuntu forum, and have been using Ubuntu 100% of the time since i got converted 4 months ago from Windows.

I have been using Ubuntu 8.04.1 and have upgraded to Intrepid Aplha 3 & 4 using kernel 2.6.26 with no problems on my HP Laptop DV6285eu, however since I applied the latest round of Kernel updates from 2.6.26 to 2.6.27-2.3 Ubuntu will no longer boot for me.

After I have chosen the new Kernel from the grub menu, I get the usuall blank screen which then should goto the Ubuntu splash logo, but it does not it just says at the bottom of the screen on  the left :-

Kernel Alive
Kernel is Really Alive

I leave my laptop for a few minutes but it just stays at this.

Does anyone have any ideas how to fix/get past this?

Is this a known bug of this newer Kernel?

Has anyone else experienced this?

Thanks in advance.

Andy

---

### Post by ViRMiN on 2008-08-29
> **gjoellee said:**
> update just came!
     Quote:
                                                 ubuntu@ubuntu-desktop:~$ uname -r
2.6.27-2-generic

Cool!  Despite being in the UK I do use the main server tbh...

---

### Post by ViRMiN on 2008-08-29
> **andyrogers2008 said:**
> Hi All

Iam new to thi Ubuntu forum, and have been using Ubuntu 100% of the time since i got converted 4 months ago from Windows.

I have been using Ubuntu 8.04.1 and have upgraded to Intrepid Aplha 3 & 4 using kernel 2.6.26 with no problems on my HP Laptop DV6285eu, however since I applied the latest round of Kernel updates from 2.6.26 to 2.6.27-2.3 Ubuntu will no longer boot for me.

After I have chosen the new Kernel from the grub menu, I get the usuall blank screen which then should goto the Ubuntu splash logo, but it does not it just says at the bottom of the screen on  the left :-

Kernel Alive
Kernel is Really Alive

I leave my laptop for a few minutes but it just stays at this.

Does anyone have any ideas how to fix/get past this?

Is this a known bug of this newer Kernel?

Has anyone else experienced this?

Thanks in advance.

Andy

Not really a cure, but, if you still have the 2.4.26 kernel installed, hit [Esc] at the grub loader and select the older kernel to continue with it... have a look at the bug reports to see if anyone's got a similar issue, if not, create a new one :)

---

### Post by Slug71 on 2008-08-29
> **Slug71 said:**
> Finally im 2.6.27 seems to be in my favour. Wireless is working sweet, which has allowed me to install my printer and finally my integrated mic is also working.

Hopefully they'll fix WPA and WEP soon so i can reinable my WPA.

WPA fixed with 2.6.27-2!

---

### Post by Crafty Kisses on 2008-08-29
> Looks like Matt Z is on board with the kernel change!! From devel-list:



Date: Tue, 26 Aug 2008 17:43:58 +0100
From: Matt Zimmerman
Subject: Re: Re: Re: [RFC] Moving Intrepid to 2.6.27 kernel
To: Ubuntu Devel <ubuntu-devel@lists.ubuntu.com>
Message-ID: <20080826164358.GH17693@alcor.net>
Content-Type: text/plain; charset=us-ascii

On Tue, Aug 26, 2008 at 09:25:06AM -0700, Jeff Schroeder wrote:

    > On Tue, Aug 26, 2008 at 8:59 AM, <ubuntu-devel-request@lists.ubuntu.com> wrote:

        > > From: Matt Zimmerman
        > > Subject: Re: Re: [RFC] Moving Intrepid to 2.6.27 kernel
        > >
        > > On Mon, Aug 25, 2008 at 05:47:46AM -0700, Jeff Schroeder wrote:

            > >> On Mon, Aug 25, 2008 at 4:00 AM, <ubuntu-devel-request@lists.ubuntu.com> wrote:

                > >> > I was in meetings all week and didn't see this until now. Mario has raised
                > >> > a concern in this thread which I think needs to be addressed. I also have
                > >> > the following questions:

            > >>
            > >> Mario's concern is bunk with commit
            > >> 7946612de2087e163308e26034286fc2dc9dacf1 fyi.
            > >> [http://git.kernel.org/?p=linux/kerne...286fc2dc9dacf1](http://git.kernel.org/?p=linux/kerne...286fc2dc9dacf1)

        > >
        > > I assume you mean that his concern is in fact valid, but will be addressed
        > > when we bring this patch into our 2.6.27 tree. Thanks for confirming this.

    >
    > Well I'd kind of assumed that you guys will be basing the final kernel
    > off of a stable
    > kernel.org release and not a -rcX. That would infer that the above
    > patch will be pulled in

Of course we will aim to ship the final 2.6.27, but with a release date
looming, the fact that something should be fixed as we track upstream
doesn't mean that we can stop paying attention to it.

If possible, we should avoid breaking this in Intrepid in the first place,
rather than breaking it and fixing it later.

    > Is there anyway to add in a whitelist of people who post constructive
    > comments and don't have the time to become full on core-devs? The
    > moderation is really annoying and I'm not posting spam to the lists. Can
    > you talk to the other Canonical-ers about this?

There is supposed to be; exactly this has been intended from the start.
There seem to be some problems with the implementation, though, and there's
a ticket open with the Canonical IS team about it (#26726).

-- 
- mdz


That's awesome. :)

---

### Post by Slug71 on 2008-08-29
Codename, 2.6.27-2 came in yesterday with the updates. I was already running 2.6.27-1 before that though so i dont know if it came in for the 2.6.26 users.
You can get the 2.6.27-1 build link in this thread on page 6. "ubuntu next server".

---

