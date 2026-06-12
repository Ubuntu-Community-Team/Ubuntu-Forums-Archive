---
title: "Linux 2.6.33 Kernel Released"
date: 2010-02-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2010-02-24
[Linux 2.6.33 Kernel Released](http://www.phoronix.com/scan.php?page=news_item&px=ODAxMg)

Will this be used for 10.04?
Last I heard they were using older kernel. Wouldn't this make it harder to keep up to date? I know kernel team are going to work on older version for longer time for certain distros... Still got 2 months of testing.

---

### Post by vade on 2010-02-24
I read somewhere that it was already decided to use .32 in Lucid. Unfortunately, I guess.

---

### Post by jppr on 2010-02-24
[https://wiki.ubuntu.com/specs/KernelLucidKernelDecision](https://wiki.ubuntu.com/specs/KernelLucidKernelDecision)

---

### Post by praveenmarkandu on 2010-02-24
yep no chance of 2.6.33 being released with lucid. im not sure how easy it would be to upgrade your kernel though or what might be the implications of it. If im not mistaken i've seen some debs around so it might not even need compiling.

---

### Post by gnomeuser on 2010-02-24
There might be .33 at some point. If I recall correctly Canonical will support such an upgrade on certain setups they know to work (probably partner OEMs) but it might become possible.

Personally I am very pleased that we got a -preempt kernel version to install.

---

### Post by epi 1:10,000 on 2010-02-24
I wish they would use 2.6.33 for the better Intell Core iX support!

---

### Post by antiram on 2010-02-24
it will be here at ~12:00 gmt. 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

with ATA Trim support for ssd, better btrfs. Where is the problem?

---

### Post by andrewabc on 2010-02-24
> **antiram said:**
> it will be here at ~12:00 gmt. 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

with ATA Trim support for ssd, better btrfs. Where is the problem?

Wait so it will be in 10.04? Or just ppa format?

I have SSD so I think having a kernel that supports TRIM by default (I assume that's what it means) is quite important. I'd rather not have to mess around with ppa for something as important as a kernel.

---

### Post by OlyPerson on 2010-02-24
> **andrewabc said:**
> Wait so it will be in 10.04? Or just ppa format?

I have SSD so I think having a kernel that supports TRIM by default (I assume that's what it means) is quite important. I'd rather not have to mess around with ppa for something as important as a kernel.

Lucid will have 2.6.32 so you'll probably want to mess around and get 2.6.33 once it's all ready.  I really wished they had pushed 2.6.33 for Lucid since it supports Intel's Core iX which more and more computers are being shipped with.  I feel they're falling behind.

---

### Post by andrewabc on 2010-02-24
Would .33 be required before installing to enable TRIM on SSD?
Or if updated to .33 after ubuntu installed, does it enabled TRIM? I thought if TRIM turned off, and files created, then TRIM turned on it kinda screwed things up for old files? I'm probably mistaken.

---

### Post by xebian on 2010-02-24
I've seen them waffle a lot here so I won't be surprised if it gets the nod.  Need to cry louder and start a petition/poll.

---

### Post by andrewabc on 2010-02-24
> **xebian said:**
> I've seen them waffle a lot here so I won't be surprised if it gets the nod.  Need to cry louder and start a petition/poll.

So true. They've got 2 months before final. And even if not all new bugs fixed, they can fix more after release like they do for every ubuntu release.

Of course .32 is going to be supported longer because ubuntu and another distro or so wee planning on using it. So if they pick .33 maybe it would not be supported as long as .32?
But do they have to backport most of .33 to .32?
If coreiX not supported, and TRIM for SSD not supported, that is pretty lame. SSD should be more mainstream by end of year. And with servers and production machines need SSD for speed. Kinda suck for TRIM to not work out of box.

---

### Post by Slug71 on 2010-02-24
.32 itself is going to be a LTS kernel. Thats why it was chosen and it is very unlikely that will change. Your better off asking for iX and TRIM support to be patched to the .32 kernel.

---

### Post by tad1073 on 2010-02-24
when do you think it will be packaged up into  .deb?

---

### Post by nhasian on 2010-02-25
agreed.  but its not difficult to upgrade to a newer kernel.  I'm already running 2.6.33 and i'm still using Ubuntu Karmic Koala 9.10
SSD is still pretty expensive now but i'll bet in the 2nd half of this year when intel releases their 3rd gen SSD drives they will be in everyone's price range.

> **andrewabc said:**
> pretty lame. SSD should be more mainstream by end of year. And with servers and production machines need SSD for speed. Kinda suck for TRIM to not work out of box.

---

### Post by fackamato on 2010-02-25
> **nhasian said:**
> agreed.  but its not difficult to upgrade to a newer kernel.  I'm already running 2.6.33 and i'm still using Ubuntu Karmic Koala 9.10
SSD is still pretty expensive now but i'll bet in the 2nd half of this year when intel releases their 3rd gen SSD drives they will be in everyone's price range.

Did you grab the sources via git? There's nothing on kernel.ubuntu.com .

---

### Post by antiram on 2010-02-25
> **andrewabc said:**
> Would .33 be required before installing to enable TRIM on SSD?
Or if updated to .33 after ubuntu installed, does it enabled TRIM? I thought if TRIM turned off, and files created, then TRIM turned on it kinda screwed things up for old files? I'm probably mistaken.
you have to use "discard" as mount option option with .33. After that files will be trimmed immediately after delete. For indilinx drives is firmware 1916 (ocz 1.5) required because a firmware bug with causes slowdowns with older trim-ready firmwares.

there is also a userspace solution, which trims the whole free space with one run
[http://www.ocztechnologyforum.com/forum/showthread.php?60882-wiper.sh-discussion-thread-(Linux-TRIM-tool](http://www.ocztechnologyforum.com/forum/showthread.php?60882-wiper.sh-discussion-thread-(Linux-TRIM-tool))
for intel ssds is a patched version required
[http://www.ocztechnologyforum.com/forum/showthread.php?60882-wiper.sh-discussion-thread-(Linux-TRIM-tool)&p=469036&viewfull=1#post469036](http://www.ocztechnologyforum.com/forum/showthread.php?60882-wiper.sh-discussion-thread-(Linux-TRIM-tool)&p=469036&viewfull=1#post469036)

---

### Post by gnomeuser on 2010-02-25
> **Slug71 said:**
> .32 itself is going to be a LTS kernel. Thats why it was chosen and it is very unlikely that will change. Your better off asking for iX and TRIM support to be patched to the .32 kernel.

The thing is that the list of things that would be great to backport for fixes, support or enhancements is growing quite large.

Support for Radeon r6xx/r7xx cards and stable KMS support.
Support for a greater range of nvidia cards (we already backport this).
Support for i915 overlay with KMS. 
Support for page flipping (needed for tear free graphics).
Support for new ethernet and wifi chips as well as improvements to the existing drivers.
Support for new SATA chips and enhancements to existing drivers.
Improvements to the IO scheduler which enhances performance.
Improvements to the pref event system.
Removing BKL from ReiserFS and other filesystem improvements including ones for ext4.
SSD trim support.
Security enhancements to TCP Syn Cookies
Improvements to sound, usb, firewire stacks and new support (especially the sound driver updates will help make Ubuntu on the desktop more pleasant here).
Support for more ARM magic which I believe is currently being patched in to our kernel.
Finally there is compcache in the kernel now (Staging but still) this I believe is code that is current being backported, work we could save.

The list is growing and I used to be a firm .32 believer but if the argument is that we should backport the important bits from .33 to .32 that is going to be a lot of work. We also see increased support for things that are important to Ubuntu from video, sound, usb, security and performance.

I am starting to think that perhaps there would be validity in at least trying to add the remaining Ubuntu patches such as AppArmor and other nice things. Providing that as a PPA for testing would at least give us an idea of what regressions we can expect, what fixes it provides and what enhancements provides an enhanced user experience. After such testing is done one would be able to make a significantly more compelling argument for going one way or the other.

---

### Post by kyleabaker on 2010-02-25
> **gnomeuser said:**
> I am starting to think that perhaps there would be validity in at least trying to add the remaining Ubuntu patches such as AppArmor and other nice things. Providing that as a PPA for testing would at least give us an idea of what regressions we can expect, what fixes it provides and what enhancements provides an enhanced user experience. After such testing is done one would be able to make a significantly more compelling argument for going one way or the other.
I agree completely. I'm fine for now with .32, but the improvements in .33 are looking better everytime I read about it!

---

### Post by gnomeuser on 2010-02-25
> **kyleabaker said:**
> I agree completely. I'm fine for now with .32, but the improvements in .33 are looking better everytime I read about it!

Text can be deceptive, I would really like some good hard data.

I can't seem to reach kernel.ubuntu.com/git currently but I would suspect that AppArmor might be a problem to port to .33. For now testers might want to using the mainline builds to see if hardware and basic functionality is present and if that is encouraging we can see about porting Ubuntu specific additions.

---

### Post by plun on 2010-02-25
Ready and baked......


[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/)


--

---

### Post by ibuclaw on 2010-02-25
Furthermore, the 2.6.32 kernel will be an LTS on the Linux upstream side too, and will be supported for 2-3 years (rather than 6 months / until the next kernel is released).

One more reason to stick with 2.6.32 in Lucid.

[http://www.kroah.com/log/linux/stable-status-01-2010.html](http://www.kroah.com/log/linux/stable-status-01-2010.html)

Regards
Iain

---

### Post by Buffalo Soldier on 2010-02-25
> **ibuclaw said:**
> Furthermore, the 2.6.32 kernel will be an LTS on the Linux upstream side too, and will be supported for 2-3 years (rather than 6 months / until the next kernel is released).

One more reason to stick with 2.6.32 in Lucid.

[http://www.kroah.com/log/linux/stable-status-01-2010.html](http://www.kroah.com/log/linux/stable-status-01-2010.html)

Regards
Iain

I never knew there's an LTS kernel. This is good news. If that's the case, then I believe we should stick with 2.6.32 kernel.

---

### Post by OlyPerson on 2010-02-25
> **ibuclaw said:**
> Furthermore, the 2.6.32 kernel will be an LTS on the Linux upstream side too, and will be supported for 2-3 years (rather than 6 months / until the next kernel is released).

One more reason to stick with 2.6.32 in Lucid.

[http://www.kroah.com/log/linux/stable-status-01-2010.html](http://www.kroah.com/log/linux/stable-status-01-2010.html)

Regards
Iain

Yes, but Lucid is LTS so 5 years support which means that they'll either have to update the kernel at some point or use an unsupported one for 2-3 years.  Either way, the argument for using 2.6.33 are pretty good.

---

### Post by OliW on 2010-02-25
Well... Nads.

I know there are good solid reasons for sticking with .32 but I can't say I'm not a little disappointed too. I own an i7, an SSD and a nvidia card so would benefit from better iX dynamic clocking support, kernel TRIM and the nvidia noveau DRM.

Oh well... It's just another 8 months to wait >_<

---

### Post by snowpine on 2010-02-25
Just install .33 yourself if you need/want it. It is no big deal. :) Better to put this choice in the hands of the users than to rush a brand-new and relatively untested kernel into a "stable" LTS release. (IMHO)

---

### Post by kahumba on 2010-02-25
During the 3-5 years the .32 kernel will be too old, even if something gets back-ported - bad choice.
Pulling in the bleeding-edge compromises stability so it's also a bad choice.

So why not use the best of 2 worlds: update the kernel (say) once a year to the last stable kernel version.

Example: 2.6.34 will be the next stable kernel, it'll be released in like 2-3 months. Then wait for another (say) 3 months for it to be "rock solid" and start testing it if it's really stable enough for the LTS. Once ready pull it in as an update.

This way the LTS **avoids** either of the 3 extremes: to be too old, too unstable or having to back-port too much (if possible at all).
Thus the LTS will be a good choice even in 2 years and **everybody** will be happy.

---

### Post by snowpine on 2010-02-25
Canonical is still supporting 2.6.15 for Dapper servers and 2.6.24 for Hardy; I am sure they can support 2.6.32 too if they put their minds to it. I happily use 2.6.18 every day on my CentOS box. Heck, there are lots of servers out there still running 2.4 kernels. Nobody wants a new kernel forced on them midway through an LTS cycle; kind of defeats the purpose.

---

### Post by kahumba on 2010-02-25
According to your logic all updates should also be considered "forced on them".
Updates make things better, right? So does a new stable and well tested kernel.
Don't confuse serving updates with forcing something.

---

### Post by snowpine on 2010-02-25
> **kahumba said:**
> According to your logic all updates should also be considered "forced on them".
Updates make things better, right? So does a new stable and well tested kernel.
Don't confuse serving updates with forcing something.

Ubuntu has **never** jumped kernel versions within a release cycle (to my knowledge). Why would on earth would they use their LTS customers as guinea pigs for a rolling-release-kernel experiment? ;)

Here is an excellent article on the topic (not Ubuntu specific but still relevant): [http://www.redhat.com/security/updates/backporting/?sc_cid=3093](http://www.redhat.com/security/updates/backporting/?sc_cid=3093)

The bottom line is that, in the corporate world, change = expense. Businesses commit to LTS releases specifically because they are guaranteed not to change.

---

### Post by ghostborg on 2010-02-25
I installed Lucid 10.04 Alpha 2 from cdrom and was wondering if there is anything I need to do to get Alpha 3 ?
I have just been doing the normal Update manager which seems to just install normal daily updates.

My system tells me I have:
Release 10.04 (lucid)
Kernel Linux 2.6.32-14
GNOME 2.29.91

It does not indicate Alpha 2 , 3 etc.

Thanks.

---

### Post by gnomeuser on 2010-02-25
> **ibuclaw said:**
> Furthermore, the 2.6.32 kernel will be an LTS on the Linux upstream side too, and will be supported for 2-3 years (rather than 6 months / until the next kernel is released).

One more reason to stick with 2.6.32 in Lucid.

[http://www.kroah.com/log/linux/stable-status-01-2010.html](http://www.kroah.com/log/linux/stable-status-01-2010.html)

Regards
Iain

The attraction of .32 isn't so much that the -STABLE team will support it for 2 maybe 3 years. Lucid on the server is supported for 5 years. The attraction is that this will also be the kernel used in the upcoming Red Hat and Novell enterprise releases. They have massive amounts of staff backporting fixes and Red Hat supports their releases with API stablity for up to 10 years. Read we can rely on them to carry a significant portion of the work maintaining such a kernel.

---

### Post by Merk42 on 2010-02-25
> **ghostborg said:**
> I installed Lucid 10.04 Alpha 2 from cdrom and was wondering if there is anything I need to do to get Alpha 3 ?
I have just been doing the normal Update manager which seems to just install normal daily updates.

My system tells me I have:
Release 10.04 (lucid)
Kernel Linux 2.6.32-14
GNOME 2.29.91

It does not indicate Alpha 2 , 3 etc.

Thanks.

No, Alpha 2 + Updates = Alpha 3

---

### Post by ghostborg on 2010-02-25
Thank you, Merk42.

---

### Post by OliW on 2010-02-25
> Updates make things better, right?When it comes to servers and enterprise, not neccessarily.

Updates do tend to add functionality but if you know Lucid works on your hardware now, you can be fairly assured it will work on the same hardware in 3 years time. The LTS system is aimed at static environments like this where things need to "just work" for a very long time.

---

### Post by libihero on 2010-02-25
i'm on karmic, and both kernels 2.6.32 and .33 disable my wireless :S
is there a fix for it?

---

### Post by Reiger on 2010-02-25
So I gave it a spin, enabled radeon KMS. And got a black-out (X300/X200M). Back to 2.6.32-14.

---

### Post by praveenmarkandu on 2010-02-25
just checking, if i want 2.6.33 installed on my karmic all i need to do is run the deb from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/) right?

what are the chances of something going wrong or regressions? will should still have my 2.6.31 kernels to fallback too in grub right?

---

### Post by praveenmarkandu on 2010-02-25
> **libihero said:**
> i'm on karmic, and both kernels 2.6.32 and .33 disable my wireless :S
is there a fix for it?

i think you have to build your drivers again because your drivers are built against your kernel. in 2.6.31 i remembered broadcom sta proprietary drivers were not installed by default. i had to select the karmic cd in repositories and sources and install bcmwl-kernel-source. 

i could be wrong though so best wait for a second opinion

---

### Post by pferraro on 2010-02-26
> **praveenmarkandu said:**
> i think you have to build your drivers again because your drivers are built against your kernel. in 2.6.31 i remembered broadcom sta proprietary drivers were not installed by default. i had to select the karmic cd in repositories and sources and install bcmwl-kernel-source. 

i could be wrong though so best wait for a second opinion

It may just be a matter of installing the headers packages - so dkms can do its job.

---

### Post by zika on 2010-02-26
> **praveenmarkandu said:**
> just checking, if i want 2.6.33 installed on my karmic all i need to do is run the deb from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33/") right?

what are the chances of something going wrong or regressions? will should still have my 2.6.31 kernels to fallback too in grub right?You need 3 .deb. Image, headers and one having "all" in its name... Just choose (32-bit or 64-bit, 2 .deb) and "all" set.

---

### Post by libihero on 2010-02-26
how would i install the headers? my wifi doesnt work in lucid either :(

---

### Post by zika on 2010-02-26
Download all .deb files You need (3 of them), then in CLI, being in the folder You've put them, use```
sudo dpkg -i *.deb
```or just pick them one by one... There is preferred order and that is the reason I just install them with *.deb...
There is also GUI way by double-clicking on them, but I'm just a CLI guy...

---

### Post by libihero on 2010-02-26
do u mean the kernel headers? i've downloaded em, like in that specific order... :(

---

### Post by zika on 2010-02-27
> **libihero said:**
> do u mean the kernel headers? i've downloaded em, like in that specific order... :([http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633_2.6.33-020633_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633_2.6.33-020633_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633-generic_2.6.33-020633_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-headers-2.6.33-020633-generic_2.6.33-020633_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-image-2.6.33-020633-generic_2.6.33-020633_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/linux-image-2.6.33-020633-generic_2.6.33-020633_amd64.deb)
(for 64-bit, for example...)

---

### Post by aviramof on 2010-02-27
i have decided to install it now because i don't like to use old versions of anything and i need better ati support let's hope it would work better for me.

well i can say one thing it's much better then the previous kernel i can now see the computer on my tv screen in normal colors not pink green or solorize and that it all i need.

---

### Post by libihero on 2010-02-27
ya i did download those when i downloaded the kernel :S
and when i downloaded lucid im still having the same problem

---

### Post by ViperScull on 2010-02-27
lucid alpha 3 + kernel 2.6.33-999-generic

·system won't suspend.
·Speaker icon on the system tray shows no volume at all, but volume isn't off. In sound preferences the volume is the actual.
.After updates, mono-runtime is held. It's the version 2.4.4 that needs mono-gac 2.4.4, but there is no update for mono-gac which remains in 2.4.3

---

### Post by Frank-NL on 2010-02-27
Mono rutime is held back here too but that's got nothing to do with the kernel. I'm on the stock .32 kernel so it's probably the repository not updated yet.

---

### Post by xebian on 2010-02-27
> **libihero said:**
> ya i did download those when i downloaded the kernel :S
and when i downloaded lucid im still having the same problem

Not sure but from your previous post you are asking how to install the headers?

So after you downloaded the *.deb files, open a terminal and go to where you saved the files.  At the prompt,

sudo dpkg -i linux*.deb

would install them.

---

### Post by antiram on 2010-02-27
> **ViperScull said:**
> lucid alpha 3 + kernel 2.6.33-999-generic

·system won't suspend.
·Speaker icon on the system tray shows no volume at all, but volume isn't off. In sound preferences the volume is the actual.
.After updates, mono-runtime is held. It's the version 2.4.4 that needs mono-gac 2.4.4, but there is no update for mono-gac which remains in 2.4.3
use the STABLE 2.6.33 from here
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/)

you are using a pre .34-rc1 compiled within the 2 week merge window.

---

### Post by zika on 2010-02-27
> **ViperScull said:**
> lucid alpha 3 + kernel 2.6.33-999-generic

·system won't suspend.
·Speaker icon on the system tray shows no volume at all, but volume isn't off. In sound preferences the volume is the actual.
.After updates, mono-runtime is held. It's the version 2.4.4 that needs mono-gac 2.4.4, but there is no update for mono-gac which remains in 2.4.3As far as I can see, none of those problems is related to 2.6.33... I have them regardless of 2.6.32-14, 2.6.33-999...

---

### Post by zika on 2010-02-27
> **antiram said:**
> use the stable 2.6.33 from here
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/]("http://kernel.ubuntu.com/%7ekernel-ppa/mainline/v2.6.33/")

you are using a pre .34-rc1 compiled within the 2 week merge window.#45

---

### Post by libihero on 2010-02-27
> **xebian said:**
> Not sure but from your previous post you are asking how to install the headers?

So after you downloaded the *.deb files, open a terminal and go to where you saved the files.  At the prompt,

sudo dpkg -i linux*.deb

would install them.

i did do that thought. it started with .32 kernel with me when i tried to install that kernel on karmic.
however, on lucid, which naturally has the .32 kernel, the same problem exists... so i dunno if its a bug or what... and it continued onto .33

---

### Post by yoav_by on 2010-02-28
Hi Folks,

I want to install 2.6.33 for it's TRIM support (having intel SSD). I've never installed a kernel before and my question is: will the old kernel still be available to boot from if there's any problem with the new one? Sorry if that's a stupid question, Linux is still a new adventure for me :)

TIA

---

### Post by LiquidMeson on 2010-02-28
> **yoav_by said:**
> will the old kernel still be available to boot from if there's any problem with the new one? Sorry if that's a stupid question, Linux is still a new adventure for me :)
TIA
No such thing as a stupid question!(unless its intentionally stupid), as like regular kernel updates, your old kernel's should always be available in your grub menu (hold shift at startup) unless you remove them. I've installed the 2 header and one image .deb file from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/) and they worked great.

---

### Post by sgosnell on 2010-02-28
You don't need to install the headers unless you intend to compile kernel stuff, nor do you need the source code.  All I ever install is the generic kernel, and have had no problems with the past several kernel versions, including lots of release candidates.

If you install a new kernel, the old ones will still be in the boot menu, and you can access it by pressing Esc as soon as the grub page appears.  I keep 3 or more most of the time, just in case I get a nasty regression, but haven't had many problems.  I did have to remove the .31 kernel when it first came out because my system wouldn't boot with it, but that was easy to do.  You can remove any kernel with Synaptic.

---

### Post by yoav_by on 2010-03-01
Thanks for the info. I installed 2.6.33 and it booted fine, but I wasn't able to install nvidia's drivers from the repo. Downloaded drivers from nvidia site, but it warned me not to continue with installation because the kernel was compiled with GCC 4.2 while I have 4.4. I suppose the next step is to install GCC 4.2 and try again. Will try that tomorrow and see what happens.

---

### Post by sgosnell on 2010-03-01
I don't think you'll have a problem with the drivers as is.  Compiling with a newer compiler should be fine, it's just that it may be a problem with an older one.

---

### Post by yoav_by on 2010-03-01
> **sgosnell said:**
> I don't think you'll have a problem with the drivers as is.  Compiling with a newer compiler should be fine, it's just that it may be a problem with an older one.

The nvidia installer says that the kernel will refuse to load modules compiled with GCC other then 4.2.

---

### Post by sgosnell on 2010-03-01
I would be surprised if the nvidia installer knew about 2.6.33.  That was only released within the past week.  I don't see what you have to lose by trying.  You can always remove it if it doesn't work, and the kernel does indeed refuse to load it, but I'd bet a fair amount of money that it will load it.

---

### Post by CylnZ on 2010-03-03
Hi. I installed 2.6.33 from the nfo in this thread on my acer 5620- kubuntu 9.10, kde 4.4 and noticed an immediate improvement in almost all aspects of use.  I'm having a strange issue with my other laptop, a gateway 6860fx that has an nvidia 8800gts chip. I can run the system in failsafe, or reduced graphics alright, but if I choose to login to a console, or c+a+f1 all I get is a blinking cursor in the left corner. I then have to c+a+d and restart the system.  Of course, if I simply go back to 2.6.31 everything is fine again. I've had it where I couldnt get X to run at all plenty of times in the past, but I have to say, this is the first time i could get X but not a console. I'm sure I'll get it figured out.

Just wanted to say thanks for the nfo. My 5620 has never run better on any OS I've tried than the current config.

---

### Post by autark on 2010-03-05
Today I installed the 2.6.33 kernel. That fixed my problems with nvidia-current after resuming from sleep (graphics corruption, difficult to get back to the graphics display). If somebody could find out what to backport to get the fix into 2.6.32, that would be fine.

---

### Post by cascade9 on 2010-03-05
> **epi 1:10,000 said:**
> I wish they would use 2.6.33 for the better Intell Core iX support!

+1. TRIM is pretty important as well IMO. 

Making 10.04 a LTS version with a kernel that is going to cause problems for iX users is not a good idea IMO. 

I'd suggest that maybe 10.04 should be dropped back to a 'normal' version, and 10.10 should be the next LTS version, but I know thats not going to happen. I even think that they should do a 6.06 (wait for the .33 or .34 then release it, even if it is a few months 'late') but I dont think that will happen either. 

This is why I think that having set release dates/LTS versions is silly, but I'm blowing against the wind I bet.

---

### Post by aviramof on 2010-03-05
i think the same they should release lucid with 2.6.33 not 2.6.32 33 is much better in the end.

---

### Post by tekstr1der on 2010-03-05
> **cascade9 said:**
> Making 10.04 a LTS version with a kernel that is going to cause problems for iX users is not a good idea IMO.

The patch from 2.6.33 to support turbo modes for desktop/mobile Core i5/i7 processors has been applied to 2.6.32 and is included in in Ubuntu Lucid kernel.

For more info, please see: [https://bugs.launchpad.net/ubuntu/+bug/429036](https://bugs.launchpad.net/ubuntu/+bug/429036)

I was very concerned about this issue myself as I have ordered a new lappy with core i7-640LM.

---

### Post by sgage on 2010-03-05
I installed the 2.6.33 kernel this morning, and so far it has worked perfectly with my nvidia 8500gt card. Plymouth works (more-or-less - still have to double login), and most important to me, resume from suspend works perfectly!

BTW, I installed the nvidia-current drivers AFTER installing 2.6.33, and the 'hardware drivers' tool worked fine.

---

### Post by yoav_by on 2010-03-05
Success! New nvidia drivers installed on 2.6.33 and everything seems to work fine :)

---

### Post by novafluxx on 2010-03-06
There's almost ALWAYS a new kernel out shortly before Ubuntu releases. That seems to be par for the course. I suppose there's nothing wrong with using a tried and tested kernel. 2.6.32 is stable and mature.

---

### Post by aviramof on 2010-03-06
but it's not stable or mature 2.6.33 drm is better then 2.6.33 in fact i have been told in launchpad bug report that the kernel developers team is about to incorporate 2.6.33 drm to the current kernel:
[https://bugs.launchpad.net/bugs/526375](https://bugs.launchpad.net/bugs/526375)

---

### Post by sgosnell on 2010-03-06
If you want 2.6.33, just install it.  You don't have to stay with the kernel that ships with a version.  I was running 2.6.33 on 9.04 before I upgraded (?) to 9.10, and I've been using it with 10.04 from alpha 2.  Works great.  You can also revert to an older kernel if you want.

---

### Post by itachi46 on 2010-03-11
installed 2.6.33 plymouth stopped working (i get the blue bar) and mesa stopped working.. so i installed the nvidia driver and now compiz is working but still not plymouth (and the double log in)

i also get an error in the beginning about failing to mount none to /dev and before that its says something about link detect fail (scontrol 0) or something :s

---

### Post by sgosnell on 2010-03-11
There is a plymouth thread in the Lucid testing forum, and it appears it isn't working for a lot of people, with any kernel.  It still has a way to go before it's ready, and the intent seems to be to get it ready for the beta release, but I wouldn't bet much money on it.

---

### Post by itachi46 on 2010-03-11
well i had it working for 2.6.32 im almost certain its something to do with the nouveau within the 2.6.33 kernel as opposed to the one for 2.6.32

---

### Post by BOFslime on 2010-03-13
I have 2.6.33 (final) installed and that all works fine, my issue is with getting my nvidia drivers installed.  I bypass the gcc 4.2/4.4 warning but it errors saying it can't find the source files for my build.  I have the headers installed so there should be no problem with this, and I see many others seemingly having no problems getting the nvidia drivers installed.

idea's?

---

### Post by yoav_by on 2010-03-13
> **BOFslime said:**
> I have 2.6.33 (final) installed and that all works fine, my issue is with getting my nvidia drivers installed.  I bypass the gcc 4.2/4.4 warning but it errors saying it can't find the source files for my build.  I have the headers installed so there should be no problem with this, and I see many others seemingly having no problems getting the nvidia drivers installed.

idea's?
This looks like a problem with nvidia drivers. Current version is 190.53 and I had the same problem with them. However, I was able to find a newer version (195.36.08 ) and it installs fine. This new version was available in nvidia's site, but was removed for some reason.

---

### Post by yoav_by on 2010-03-13
> **BOFslime said:**
> I have 2.6.33 (final) installed and that all works fine, my issue is with getting my nvidia drivers installed.  I bypass the gcc 4.2/4.4 warning but it errors saying it can't find the source files for my build.  I have the headers installed so there should be no problem with this, and I see many others seemingly having no problems getting the nvidia drivers installed.

idea's?

You might want to try d/l them from here:

[http://news.softpedia.com/news/Download-Nvidia-195-36-08-Linux-Display-Driver-136508.shtml]("http://news.softpedia.com/news/Download-Nvidia-195-36-08-Linux-Display-Driver-136508.shtml")

---

### Post by cascade9 on 2010-03-13
I had issues with the 2.6.33 kernel for a few days, with the nvidia-kernel-source refusing to compile. Thats been fixed for me with the newest update (on debian sid here). 

There is a patch for 2.6.33 + 190.53, see here- 

[http://www.nvnews.net/vbulletin/showthread.php?t=142794](http://www.nvnews.net/vbulletin/showthread.php?t=142794)

> **yoav_by said:**
> This looks like a problem with nvidia drivers. Current version is 190.53 and I had the same problem with them. However, I was able to find a newer version (195.36.08 ) and it installs fine. This new version was available in nvidia's site, but was removed for some reason.

Removed because it may suffer the same bug that the 196.75 WHQL drives have- possible overheating!

> [It started with the GeForce 196.75 WHQL driver]("http://www.dvhardware.net/article41520.html"), which was pulled last week. The driver &#8216;recall&#8217; has been extended to include versions 195.36.03 and 195.36.08 *nix drivers.[http://www.maximumpc.com/article/news/nvidia_removes_linux_solaris_drivers_due_overheating_bug](http://www.maximumpc.com/article/news/nvidia_removes_linux_solaris_drivers_due_overheating_bug)

I'd avoid using the 195.36.xx drivers at all. 

You can get 195.30 drivers (beta, but I'm guessing its not very beta) from here- 

[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)

---

### Post by BOFslime on 2010-03-13
YES! that patch worked flawlessly.  Thanks so much!

---

### Post by grandtoubab on 2010-03-15
Hello
I am using the kernel 2.6.33 from the Ubuntu ppa [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/) as descibed above  in this discussion.
But it appears now there is a patch to go to 2.6.33.1 at [http://www.kernel.org/](http://www.kernel.org/)
How do we apply the patch in Ubuntu?

---

### Post by tekstr1der on 2010-03-15
> **grandtoubab said:**
> Hello
I am using the kernel 2.6.33 from the Ubuntu ppa [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/) as descibed above  in this discussion.
But it appears now there is a patch to go to 2.6.33.1 at [http://www.kernel.org/](http://www.kernel.org/)
How do we apply the patch in Ubuntu?

Simply wait for the ubuntu-optimized mainline kernel to be build. 2.6.33-1 was just released today. They are usually pretty quick about it (a day or two).

---

### Post by xebian on 2010-03-15
> **grandtoubab said:**
> Hello
I am using the kernel 2.6.33 from the Ubuntu ppa [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/) as descibed above  in this discussion.
But it appears now there is a patch to go to 2.6.33.1 at [http://www.kernel.org/](http://www.kernel.org/)
How do we apply the patch in Ubuntu?

You just wait a while and a 33.1 version will be available.

---

### Post by OliW on 2010-03-15
Does the mainline kernel have any Ubuntu patches?

Is there a version somewhere where somebody does maintain a release-quality kernel, patched up with restricted drivers and NFS turned on?

Why isn't NFS server kernel module enabled in mainline?

---

### Post by xebian on 2010-03-15
> **OliW said:**
> Does the mainline kernel have any Ubuntu patches?

Is there a version somewhere where somebody does maintain a release-quality kernel, patched up with restricted drivers and NFS turned on?

Why isn't NFS server kernel module enabled in mainline?


Ubuntu patched release  quality kernels are in the repo.](*,)

---

### Post by Pencioner on 2010-03-16
> **xebian said:**
> You just wait a while and a 33.1 version will be available.

and it arrived...

BTW, with 2.6.33 i had problems with nfs3 exports stopped to mount from another box with message like server doesn't respond or so... and as i can conlude from reading changelog, chances to get it working on 33.1 are very little... had to switch back to 2.6.32

---

### Post by OliW on 2010-03-16
> **Pencioner said:**
> BTW, with 2.6.33 i had problems with nfs3 exports stopped to mount from another box with message like server doesn't respond or so... and as i can conlude from reading changelog, chances to get it working on 33.1 are very little... had to switch back to 2.6.32

If you issue a "/etc/init.d/nfs-kernel-server restart", on the 2.6.33 mainline kernel you'll see: "Not starting NFS kernel daemon: no support in current kernel."

I don't know why it's been built this way but it's really annoying. I'll see if I can find who builds them and send my moaning in that direction.

---

### Post by xebian on 2010-03-16
> **Pencioner said:**
> and it arrived...

BTW, with 2.6.33 i had problems with nfs3 exports stopped to mount from another box with message like server doesn't respond or so... and as i can conlude from reading changelog, chances to get it working on 33.1 are very little... had to switch back to 2.6.32

We know 33.1 has been released but the kernel-mainline build is not yet done.

---

### Post by fjf on 2010-03-17
Anyone knows how to mount a SSD to make trim work?.  I cannot find any info by googling this.  I've read something about a discard option, but no details.  Is this so new no one tried?

---

### Post by andrewabc on 2010-03-17
> **fjf said:**
> Anyone knows how to mount a SSD to make trim work?.  I cannot find any info by googling this.  I've read something about a discard option, but no details.  Is this so new no one tried?

Not sure exactly what you mean, but if you really want TRIM, check out sticky threads posted [here](http://www.ocztechnologyforum.com/forum/forumdisplay.php?237-Vertex-Agility-Turbo-Solid-V2-Summit-Colossus-on-Linux-and-Apple-OSX)

---

### Post by OliW on 2010-03-17
> **andrewabc said:**
> Not sure exactly what you mean, but if you really want TRIM, check out sticky threads posted [here](http://www.ocztechnologyforum.com/forum/forumdisplay.php?237-Vertex-Agility-Turbo-Solid-V2-Summit-Colossus-on-Linux-and-Apple-OSX)SSDs need TRIMming every so often to properly release blocks so the built-in controller knows where it can write more readily. If you don't TRIM, the performance of an SSD drops significantly over time.

2.6.33 has TRIM built in... But like everybody else, it seems, I can't find any documentation on how it actually works or what I need to hump in order to turn it on.

---

### Post by fjf on 2010-03-17
Yes it seems it is turned off by default because they dont know if it really works without destroying the data in the SDD.

I found some info here:  [http://www.ocztechnologyforum.com/forum/showthread.php?63843-The-truth-about-firmware-1.4-and-Linux&p=479400&viewfull=1#post479400]("http://www.ocztechnologyforum.com/forum/showthread.php?63843-The-truth-about-firmware-1.4-and-Linux&p=479400&viewfull=1#post479400")

---

### Post by ViperScull on 2010-03-17
> **fjf said:**
> Anyone knows how to mount a SSD to make trim work?.  I cannot find any info by googling this.  I've read something about a discard option, but no details.  Is this so new no one tried?

What's your SSD model?

TRIM has to be supported by the firmware also. In order to trim it, you need kernel 2.6.33 and a firmware capable of doing it.

**OCZ** SSDs need to have firmware 1.5. 

**Intel** SSDs:
·G2: can't be automatically trimmed in an AMD motherboard, because it needs Intel drivers to do it. Also, i think (not completely sure about this) they only can be automatically trimmed in Windows 7, because Intel firmware needs Microsoft drivers.
·G1: Tehir firmwares don't support trim at all.

You can manually (you don't need kernel 2.6.33) trim Intel and OCZ SSDs manually via wiper.sh and its GUI. For further information, check out the link andrewabc wrote on a previous post.

Apart from the new controllers Sandforce, there are 3 controllers in which most of the SSDs are based. Indilix (most OCZs, g.skill...), Intel (Intel), and Samsung (Samsung, Corsair P, OCZ summit..).

Indilix based SSDs should be trimmed with their latest firmware. In fact you can use OCZ 1.5 in for example a G.Skil Falcon. Samsung supports TRIM now, but old models don't, and they can't be updated.

Anyway, for the time being, if i were you i would stick with wiper.sh, cause TRIM is not as mature as i'd like.

---

### Post by antiram on 2010-03-17
mount option for trim is "discard", works with btrfs, ext4 and some other (xfs and fat or so). Indilinx with 1916=1.5, 1819 has slowdowns with kernel trim. Intel should also work

---

### Post by OliW on 2010-03-17
> **ViperScull said:**
> **OCZ** SSDs need to have firmware 1.5.

Just one note on OCZ firmware, don't blindly apply firmware updates. For example, **putting 1.5 on top of 1.42 will brick your SSD**, your PC will die, your girlfriend will leave you and you'll likely rip the fabric of space and time.

Read [this thread]("http://www.ocztechnologyforum.com/forum/showthread.php?67815-1-5-FW-update-for-Agility-Vertex-EX-drives-and-Turbo") ***in full*** for instructions.

**1.42 does support TRIM... So you don't need to update anyway.**

---

### Post by Trident911 on 2010-03-17
I have spent the last 4 sleepless nights trying to figure out how to get a WIDE range of Linux Distros to support/optimize TRIM in my 2x X25-M drives in Raid0. I have been working with Ubuntu Server (9.10 and also 10.4), both with Ext4, latest Kernel 2.6.33.1 (which supposively has TRIM support enabled - heard conflict reports?).
 
For the life of me, it seems SSDs are just to new to both Windows/Linux worlds - the number of optimzations I've had to follow:
 
- Alignment of earse blocks
- Changing of I/O Schedulers to 'noop' or 'deadline'
- Addition of 'noatime' and 'nodiratime'
- Moving logs off to RAMDisk
- Recompiling of latest Kernels
- Disabling Swap
- Firmware is latest (FYI)
 
... The list is endless - so I come here, with hope that users of this board would be able to point me in the right direction to get things up and running.
 
Can anyone shed some light onto this, this seems to be the most active topic concerning Ubuntu + SSD + Trim. Do I simply have to pass 'discard' as a boot option then good to go?
 
Cheers,
Trident911

---

### Post by andrewabc on 2010-03-17
- Alignment of earse blocks -> did that
- Changing of I/O Schedulers to 'noop' or 'deadline' ->didn't do
- Addition of 'noatime' and 'nodiratime' ->didn't do
- Moving logs off to RAMDisk ->didn't do
- Recompiling of latest Kernels - didn't do
- Disabling Swap - didn't do. no need as swap never gets used for me, I just turned it down to decrease probability of it being used.
- Firmware is latest (FYI) - havn't done yet, but recommended.

Had 60gb ocz SSD since October, only 6gb used. Data is on hard drive.
Also TRIM does NOT work in RAID0 on any OS.
Garbage collection will work though.

EDIT:
Oops, you have intel SSD. They don't have garbage collection firmware, OCZ/indilinx does.
RAIDing intel won't get you TRIM. Don't waste time trying.

---

### Post by Dayofswords on 2010-03-17
it seems it was just an unfornate scheduling issue and 2.6.32 was there when a kernel was needed


then again, what do i know?!

---

### Post by ext73 on 2010-03-19
Hi I`m building kernels for netbook and laptops, and I noticed that kernel 2.6.33.1 is slower than 2.6.33 ... vide Doom3, Quake 4 or Pray ... here is my build of 2.6.33 -> [**[COLOR="DarkRed"]ubuntu.forum.pl[/COLOR]**]("http://forum.ubuntu.pl/showthread.php?t=109452&page=16")

---

### Post by Pencioner on 2010-03-22
> **OliW said:**
> If you issue a "/etc/init.d/nfs-kernel-server restart", on the 2.6.33 mainline kernel you'll see: "Not starting NFS kernel daemon: no support in current kernel."

I don't know why it's been built this way but it's really annoying. I'll see if I can find who builds them and send my moaning in that direction.

I'm not using mainline kernel, i'm building vanilla one with make-kpkg ... and i'm using the same config as when building 2.6.32 (2.6.32.10 was the last one, and it works fine)

---

### Post by _h_ on 2010-03-22
> **ext73 said:**
> Hi I`m building kernels for netbook and laptops, and I noticed that kernel 2.6.33.1 is slower than 2.6.33 ... vide Doom3, Quake 4 or Pray ... here is my build of 2.6.33 -> [**[COLOR=DarkRed]ubuntu.forum.pl[/COLOR]**]("http://forum.ubuntu.pl/showthread.php?t=109452&page=16")

Alot of people here probably can't understand Polish. :(

---

### Post by 98cwitr on 2010-04-14
stable release of 2.6.33.2 as of 4-1 

[http://www.kernel.org](http://www.kernel.org)

---

### Post by a-user on 2010-04-14
@[Trident911]("http://ubuntuforums.org/member.php?u=1038081"): now that you brought that up i wonder how noop as schedular performed compaired to cfg for you?

i'm using the default lucid kernel 2.32 and a corsair v64 ssd. i observed that hdparm -tT gives me over 25% higher performance with the default cfg schedular than with any ot the others.

some where on the net i read that switching to noop is only recomended for the older kernels where cfg was not optimized for ssds. well, not sure about that, but at least the simple hdparm bench shows me a significant higher performance with cfg as schedular.

in numbers:
with cfg i get arround 100MB/s buffered readings
with the others around 79MB/s

note, this is not DIRECT mode, where ofocurse i get my 240 MB/s.

---

### Post by aviramof on 2010-04-14
> **98cwitr said:**
> stable release of 2.6.33.2 as of 4-1 

[http://www.kernel.org](http://www.kernel.org)

the problem is that there are no debs files and not everyone know how to compile kernel from source or even to install the patch so if you can explain how to do that that would be great and one more thing at the moment 2.6.33 don't work with fglrx so it's not easy to work with and with another kernel that does work with fglrx.

---

### Post by Eclipse. on 2010-04-14
> **aviramof said:**
> the problem is that there are no debs files and not everyone know how to compile kernel from source or even to install the patch so if you can explain how to do that that would be great and one more thing at the moment 2.6.33 don't work with fglrx so it's not easy to work with and with another kernel that does work with fglrx.

Where have you been?

There has been debs of mainline builds and stable kernels for a while, they are provided by the Ubuntu Kernel Team.

---

### Post by OliW on 2010-04-14
> **aviramof said:**
> the problem is that there are no debs files and not everyone know how to compile kernel from source or even to install the patch so if you can explain how to do that that would be great and one more thing at the moment 2.6.33 don't work with fglrx so it's not easy to work with and with another kernel that does work with fglrx.

[LIST=1]
[*]As Eclipse. just said, there are.
[*]Not everybody knows how to speak Japanese but they can learn if they want to! There are plenty of kernel-building docs out there. What you mean is you haven't seen any because you haven't searched for them.
[*]fglrx probably (I'm not sure because I'm a nvidia user) needs the restricted modules building for it... For my nvidia card, I just download and install the driver manually from the nvidia website. I assume AMD/ATI have a similar process.
[/LIST]

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) is a good starting point.

---

### Post by aviramof on 2010-04-14
there are debs for 2.6.33 not 2.6.33-2 and i tried to compile from source and install the patch from the bz2 files but with no luck and as for the flgrx the problem is that jockey doesn't work so well there it simply doesn't install the restricted modules i posted bug report about it and someone said it's 
a problem with the headers of 2.6.33

---

### Post by MarkieB on 2010-04-15
no longer participating in ubuntuforums.org

---

### Post by aviramof on 2010-04-15
i wish it was that easy:

```
&#1499;&#1513;&#1500;&#1493;&#1503; &#1489;&#1492;&#1489;&#1488;&#1514; http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found
&#1499;&#1513;&#1500;&#1493;&#1503; &#1489;&#1492;&#1489;&#1488;&#1514; http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/lucid/main/source/Sources.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by djchandler on 2010-04-16
We really need this kernel. k10temp is not in the current kernel (2.6.32-21) and I'm having a somewhat serious problems with heat on my laptop. k10temp isn't in the repository either. I could build from source, but that's no longer beta testing 10.04 if 2.6.33-x isn't in the RC or final release.

It isn't as much of an issue in a desktop. But having a laptop shutdown after watching 5 minutes of video isn't going to win us any friends. I'm using fglrx for video, and there's a known bug in xorg driver for ATI that cooks this thing even faster.

So the freeze for the RC was yesterday, 4/15. Anybody know if 2.6.33-x made it into the RC?

> deb [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu) lucid main

There's not a Lucid directory there that I can find, just Hardy and Karmic. Has someone put the kibosh on the Lucid repository?

---

### Post by petejk on 2010-04-16
I went through a bit of trial and error before successfully using a kernel I'd compiled on Lucid. I could get a successful compile, but not a successful boot. But I pieced this together from various guides. Bold is for 2.6.34-rc4 - for 2.6.33-2 where it differs, italics.

**cd /usr/src**

[B]sudo wget http://www.kernel.org/pub/linux/kernel/v2.6/testing/linux-2.6.34-rc4.tar.bz2
[/B]*sudo wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.33.2.tar.bz2*
[latest source from kernel.org]

**sudo tar -jxf linux-2.6.34-rc4.tar.bz2**[I]
sudo tar -jxf linux-2.6.33.2.tar.bz2[/I]
[unpack]

[B]cd linux-2.6.34-rc4
[/B]*cd linux-2.6.33.2*

[B]sudo cp -vi /boot/config-`uname -r` .config
[/B][copy your existing configuration]

[B]sudo make menuconfig
[/B][apply this config to new kernel build and launch config tool]
[optional, but I disable the kernel hacking --> kernel debugging option]
[save then exit]

[B]sudo make-kpkg clean
[/B]
[B]sudo INSTALL_MOD_STRIP=1 CONCURRENCY_LEVEL=3 fakeroot make-kpkg --initrd kernel_image kernel_headers modules_image
[/B][set concurrency level to your number of cores plus 1 ; in my case dual core, so value 3]
[When the compile's complete, install headers then image .deb file. Either use the terminal or **sudo nautilus**, browse to** /usr/src **and double click the .debs]

[After headers and image debs are installed..]
**sudo update-initramfs -c -k 2.6.34-rc4**
*sudo update-initramfs -c -k 2.6.33.2*

**sudo update-grub**
**sudo make modules_install**

Now reboot!

Pete

---

### Post by Longinus00 on 2010-04-16
> **djchandler said:**
> 
So the freeze for the RC was yesterday, 4/15. Anybody know if 2.6.33-x made it into the RC?


The kernel decision for lucid was decided months ago, it's not going to change.

Also, why not just compile k10temp as a module and load it into the kernel?

---

### Post by andrewthomas on 2010-04-16
> **aviramof said:**
> i wish it was that easy:

```
&#1499;&#1513;&#1500;&#1493;&#1503; &#1489;&#1492;&#1489;&#1488;&#1514; http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found
&#1499;&#1513;&#1500;&#1493;&#1503; &#1489;&#1492;&#1489;&#1488;&#1514; http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/lucid/main/source/Sources.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
The ppa is no longer maintained.  You have to download and install the debs manually.

---

### Post by aviramof on 2010-04-16
i never used the ppa i downloaded the 2.6.33 debs and that is how i installed 2.6.33 but now there is 2.6.33-2 and it's not debs you need to compile the source or the patch yourself and i didn't had much luck doing it. 

and beside there is still a problem with fglrx driver not working with this kernel so i can't use it now although he's better then 2.6.32-21 that for sure.

---

### Post by djchandler on 2010-04-18
> **Longinus00 said:**
> The kernel decision for lucid was decided months ago, it's not going to change.

Also, why not just compile k10temp as a module and load it into the kernel?

Thanks. I was just hoping that someone would change their mind if that new kernel fixed other issues we still seem to be dealing with.

Compiling the module is a reasonable solution for me, but it won't help someone who has neither the knowledge, patience or inclination. Since we're beta testing, or have been, it's kind of a challenge to keep up with all the fixes. If you go to the trouble of rigging a workaround, the next update could break things. I'm a bit conservative--wait and see will be my position until the final is released.

---

### Post by aviramof on 2010-04-18
i belive that once a proper fglrx driver be released there would be no reason for me not to use the 2.6.33 kernel but i would like to see debs files for 2.6.33-2 kernel because compiling kernel from source or from patch might be a bit complicated for most people 
i personally have not yet tried it not a lot anyway but the important thing now is to have 
a working fglrx driver or eles i want be able to use this kernel at all.

---

### Post by clhsharky on 2010-04-18
aviramof


How long are you going to beat that dead horse?

No matter how much you want it, its not going to happen.

Its been explained to you, but your not listening, get over it.

---

### Post by aviramof on 2010-04-18
what don't i understand excecly that the ppa is no longer maintain?that i need to download debs manually from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") ?
well i have i have downloaded this files from the start when this thread was brand new
_linux-headers-2.6.33-020633_2.6.33-020633_all.deb_
linux-image-2.6.33-020633-generic_2.6.33-020633_i386.deb
linux-source-2.6.33_2.6.33-020633_all.deb

but there are no debs for 2.6.33-2 and jockey don't want to install fglrx in this kernel.

by the way i just downloaded and tried to install
linux-headers-2.6.33-020633-generic_2.6.33-020633_i386.deb  

and got this:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/565804](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/565804)

i tried it from 2.6.32-21 and from 2.6.33-020633

---

### Post by clhsharky on 2010-04-18
Hi aviramof

I do understand you wanting to use the latest stable kernel for its benefits. But Lucid is going to be a LTS so its more conservitive and staying with .32 kernel that will be mantained for 4years. It falls in line with other distros long term support.

>  Ubuntu	        Debian	        RHEL	SLES
Kernel	2.6.32 + drm-33	2.6.32 + drm-33	2.6.32	2.6.32
GCC	4.4	        
Python	2.6	        
OpenOff 3.2	        
Perl	5.10.1	        
Boost	1.40	        
XServer 1.7	        
Mesa	7.7	        
Mono 	2.4-snapshot	

The problem is ATI fglrx not supporting other kernels, only official releases kernels of these 4 distros. All other distros have to follow along for fglrx support.

 This is but one reason why many people aren't happy ATI.
Have you ever wondered why so many are interested in the development of OSS drivers. It doesnt suffer from this kernel dilemma.

Sharky

---

### Post by questioning on 2010-04-18
you guys could also try the liquorix kernels

[http://www.liquorix.net/](http://www.liquorix.net/)

---

### Post by aviramof on 2010-04-18
i would wait for ati to officially release then 10.04 driver then i will try to find solution to the 
fglrx problem with 2.6.33 kernel and at the moment i don't like 2.6.32-21 it still have some problem maybe when final 32 kernel be released then i could decide weather to stay with it or to resume using 2.6.33 with some workaround fglrx driver or even 2.6.34 if it would be official released by that time.

---

### Post by clhsharky on 2010-04-18
HI questioning

liquorix kernels don't matter to me but it might to others, thanks.

I do test Ubuntu released kernels, but im on .34rc4 kernel with fresh git+Gallium OSS.

Sharky

---

### Post by clhsharky on 2010-04-18
aviramof

I agree with you that your best bet for fglrx,  will be with the released fglrx driver latter this month with patches from Kano at Phoronix.
 Just wondering what is it you need fglrx+.33kernel for?

Sharky

---

### Post by aviramof on 2010-04-18
since i have fglrx installed from 2.6.32-21 when i enter 2.6.33 nothing works compiz doesn't work and when i scroll pages like threads in this forum every movment refresh the entire screen so scrolling is not smooth. 

and of course clone view and dual view  and catalyst don't work well and i have two tv's connected to this computer with dvi hdmi cables and i use my computer to see videos in this tv's 720p tv sereis and 1080p movies without fgrlx driver i can't do that smoothly espescilty 1080p movies don't work well at all.

and as for 2.6.33 he's more stable then the current 2.6.32 first of all there is no white line at the top of the screen at boot process no purple boxes when i log off perhaps better drm support and basicly better then 2.6.32. 

in the current kernel i can't even run movies and compiz at the same time i must switch to metacity for that but perhaps it's a problem with the current fglrx driver that would be fix later or once 2.6.33 would have an fglrx driver he would work even better then the current kernel does with fglrx.

and beside this kernel is a good backup against your unstable kernels if i didn't have it installed when the "new" 2.6.32-20 was released and crashed i would have been force to format again becasue i already deleted 2.6.32-19 at that time.

---

### Post by clhsharky on 2010-04-18
HI aviramof

OK thanks
Have to go now, will think about it.


Sharky

---

### Post by clhsharky on 2010-04-19
HI aviramof

If you want to build Kernel 2.6.33.2 or any of the stable or newer, you can use Kernelcheck+kernel-package. Kernelcheck has GUI and can download deb here
 
[http://launchpadlibrarian.net/44725226/kernelcheck_1.2.5-4_all.deb](http://launchpadlibrarian.net/44725226/kernelcheck_1.2.5-4_all.deb)
[http://www.webupd8.org/2010/04/kernelcheck-fixed-deb-download-ubuntu.html](http://www.webupd8.org/2010/04/kernelcheck-fixed-deb-download-ubuntu.html)

And kernel-package from repos, I must warn you it takes hours.This is not like image you DL, its a custom build but you and can add patches and more. But not hard to use.

About other problems ' Man you NEED a Nvidia card ' I know you got what you got and doing the best you can with it. Just compiled .33.2= success on ext3

Latter
Sharky

---

### Post by a-user on 2010-04-19
does work k10temp for anybody correct? i have an athlon II X3 405e and the temps it shows are about 10°C too low. Currently i unlocked the fourth core so it say Phenom II B05e. And with this unlocked core k10temp allways tells we 0°C.

totally useless for me currently.

---

### Post by ViperScull on 2010-04-19
> **a-user said:**
> does work k10temp for anybody correct? 

Works for me. I got an Athlon II X4 620

---

### Post by a-user on 2010-04-19
did you compaired the temps with the ones in the bios? are they the same or do they differ by about 10° as in my case (when i didn't enabled the fourth core)?

cause i read that many ppl reported that k10temp is not showing the proper temps.

btw. maybe there is a newer version. where do you get the actual one?

---

### Post by DougieFresh4U on 2010-04-23
At the moment I am using the
**2.6.34 kernel** and all seems to be good except my USB problem which has been a whole separate issue.

---

