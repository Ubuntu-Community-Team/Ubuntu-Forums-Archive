---
title: "Kernel 2.6.29 in Jaunty"
date: 2009-01-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kosimo on 2009-01-11
2.6.29-rc1 has been released today, and I'm wondering if we'll be on time to have a stable release for the inclusion in Jaunty. 

What do you think?

Thanks

---

### Post by Eclipse. on 2009-01-11
Me thinks we will get .29 into jaunty.

We were in a similar situation with intrepid over .26/.27 (infact I think it was later in the release cycle) and after the kernel devs had a meeting they went with .27 although there could have been special reasons for it, I know .27 had alot of improvements.I guess it will all come down whats new in .29 and what improvements it would give the users.

EDIT: It was between alpha 4/5 that we made the switch to .27 and it was still in the -rc stages if I remember at that point so yeah, mabey.

---

### Post by Slug71 on 2009-01-11
Its my belief Jaunty will ship with .29.

---

### Post by ShirishAg75 on 2009-01-11
It would be a close call. Remember that it takes 3 months for the kernel to be stabilized and outta door. Atleast that has been the cycle for the last few releases. Even if its 2.5 months its a pretty small window.

---

### Post by Slug71 on 2009-01-11
> **ShirishAg75 said:**
> It would be a close call. Remember that it takes 3 months for the kernel to be stabilized and outta door. Atleast that has been the cycle for the last few releases. Even if its 2.5 months its a pretty small window.

That would be true.

---

### Post by foxmulder881 on 2009-01-12
I'm currently working on compiling it now. Reason: I want to give Btrfs a test out and see how it competes with Ext4.

---

### Post by LordVeovis on 2009-01-12
> **foxmulder881 said:**
> I'm currently working on compiling it now. Reason: I want to give Btrfs a test out and see how it competes with Ext4.

I didn't know Btrfs was included in .29??  Do you have a link with info about it?

---

### Post by plun on 2009-01-12
> **foxmulder881 said:**
> I'm currently working on compiling it now. Reason: I want to give Btrfs a test out and see how it competes with Ext4.

I tested yesterday and the build broke, but a new gccplus seems to be out this morning. 

A RC1 can be extremly unstable as Linus wrote..

[http://marc.info/?l=linux-kernel&m=123163282323725&w=2](http://marc.info/?l=linux-kernel&m=123163282323725&w=2)

> Anyway, give it a good testing. And please do keep in mind that while new 
filesystems can be intruiging and exciting, "new" also means "not widely 
tested". I'm sure the btrfs people will appreciate people testing, but I 
would suggest that you go very very carefully (squashfs is read-only, [B]so 
it's presumably less likely to eat your data, but who knows - the 
perversity of the universe is endless).[/B]

				Linus

---

### Post by amano on 2009-01-12
The question should be if .29 offers things that would be very useful for jaunty.

If those are just some intereseting drivers they could be backported. And thus leading to a more stable kernel release.

In the last circle, those drivers were so hard to backport that they finally decided, it was easier to risk going to the latest kernel.

What will .29 offer?: SquashFS built in. Otherwise I smell rather experiemtal stuff like the ButterFS which we will not see active in the standard jaunty kernel anyway.

---

### Post by marijus on 2009-01-12
did anyone manage to build 2.6.29-rc1?
i tried yesterday but build failed...

any help appreciated!
regards, marijus

---

### Post by Slug71 on 2009-01-12
> **amano said:**
> The question should be if .29 offers things that would be very useful for jaunty.

If those are just some intereseting drivers they could be backported. And thus leading to a more stable kernel release.

In the last circle, those drivers were so hard to backport that they finally decided, it was easier to risk going to the latest kernel.

What will .29 offer?: SquashFS built in. Otherwise I smell rather experiemtal stuff like the ButterFS which we will not see active in the standard jaunty kernel anyway.

KMS would probably be the main reason.

---

### Post by Eclipse. on 2009-01-12
> **foxmulder881 said:**
> I'm currently working on compiling it now. Reason: I want to give Btrfs a test out and see how it competes with Ext4.

Why not just get the module source and build it into your current kernel, seems a much better idea than attempting to compile a really unstable kernel just to try out on feature.

---

### Post by amano on 2009-01-12
> **Slug71 said:**
> KMS would probably be the main reason.
Since the drivers of the major GPU vendors nVidia and ATI will not support that in time for Jaunty and Plymouth integration was moved to Ubuntu 9.10, there is not too much point to have it for Jaunty. Because nobody will benefit from its abstract inclusion if no drivers hook it up.

---

### Post by Slug71 on 2009-01-12
> **amano said:**
> Since the drivers of the major GPU vendors nVidia and ATI will not support that in time for Jaunty and Plymouth integration was moved to Ubuntu 9.10, there is not too much point to have it for Jaunty. Because nobody will benefit from its abstract inclusion if no drivers hook it up.

True that, i think that was the reason most people looked forward to having 2.6.29 though.

---

### Post by quickshade on 2009-01-12
How about the fact that we could support a newer kernel instead of backporting features and help the kernel developers with new features and fixing bugs, instead of backporting a few drivers and then saying "screw you" to all the kernel developers who are working hard on .29 and not getting any help from the distros. Of course the bigger question is, why do we release 4-5 kernels a year with minor improvements every time, why not 1-2 main releases each year but a bigger feature set, and smaller bug fixing releases every 2-3 months.

---

### Post by MacUntu on 2009-01-12
Yeah... the good into the pot, the bad into the crop - that's not how it works or how it should work.

---

### Post by foxmulder881 on 2009-01-12
> **LordVeovis said:**
> I didn't know Btrfs was included in .29??  Do you have a link with info about it?

[http://www.phoronix.com/scan.php?page=news_item&px=Njk4Mw](http://www.phoronix.com/scan.php?page=news_item&px=Njk4Mw)

[http://www.phoronix.com/scan.php?page=news_item&px=Njk4NA](http://www.phoronix.com/scan.php?page=news_item&px=Njk4NA)

---

### Post by Slug71 on 2009-01-12
> **quickshade said:**
> How about the fact that we could support a newer kernel instead of backporting features and help the kernel developers with new features and fixing bugs, instead of backporting a few drivers and then saying "screw you" to all the kernel developers who are working hard on .29 and not getting any help from the distros. Of course the bigger question is, why do we release 4-5 kernels a year with minor improvements every time, why not 1-2 main releases each year but a bigger feature set, and smaller bug fixing releases every 2-3 months.

I have never understood this myself why they dont just work longer on a kernel and do less releases. Theyre gonna have to think about it at some point if theres gonna be no 3.x.x Kernel.

---

### Post by caryb on 2009-01-12
> Theyre gonna have to think about it at some point if theres gonna be no 3.x.x Kernel. 

I read a interview with Linus a while back & at that time he was not keen on a 3. kernel



Cary

---

### Post by LordVeovis on 2009-01-12
> **foxmulder881 said:**
> [http://www.phoronix.com/scan.php?page=news_item&px=Njk4Mw](http://www.phoronix.com/scan.php?page=news_item&px=Njk4Mw)

[http://www.phoronix.com/scan.php?page=news_item&px=Njk4NA](http://www.phoronix.com/scan.php?page=news_item&px=Njk4NA)

Thanks

---

### Post by Kosimo on 2009-01-17
2.6.29-rc2 has been released today

[Link]("http://www.kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.29-rc2")

---

### Post by Slug71 on 2009-01-17
> **Kosimo said:**
> 2.6.29-rc2 has been released today

[Link]("http://www.kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.29-rc2")

Yep, Pulseaudio 0.9.14 was also released a few days before that so it should be in the .29 Kernel.

---

### Post by Kosimo on 2009-01-17
> **Slug71 said:**
> Yep, Pulseaudio 0.9.14 was also released a few days before that so it should be in the .29 Kernel.

Wow... I didn't know that pulseaudio was inside the kernel! :KS

Any good update on that release?

---

### Post by Slug71 on 2009-01-17
> **Kosimo said:**
> Wow... I didn't know that pulseaudio was inside the kernel! :KS

Any good update on that release?

Gets packaged with the Kernel if i'm not mistaken. Seems there are quite a few fixes in it.

---

### Post by amano on 2009-01-17
No. There are separate packages for pulseaudio. AFAIK Pulseaudio is completely userland based by design and interfaces mostly with alsa. And alsa itself interfaces with the alsa kernel drivers. Thus alsa is partly kernel based, but NOT pulseaudio, which is mostly a layer between the apps and alsa.

In relation to this thread having pulseaudio .14 in jaunty is possible without question! Even with linux 2.6.28.

I don't see too much reasons to switch to 2.6.29. The ext4 online defrag is delayed and requires a rewrite. The new intel driver 2.6 will work with the current GEM module from 2.6.28. All other drivers won't benefit from GEM anyway for the time being. And KMS is pretty useless without having drivers hooking it up. And the staging drivers are not ready for distribution usage. All in all the improvements of this kernel feel rather abstract and experimental.

What is left from the upate are normal driver updates as usual. I cannot judge if there is enough interesting stuff in there that justifies a new testing cycle instead of stabilizing things right from now on.

---

### Post by Slug71 on 2009-01-17
Thanks for clearing that up Amano, I too dont see a need for moving to the .29 Kernel but im sure there would be a lot of people that would like to make a test btrfs partition.

---

### Post by jsmidt on 2009-01-18
> **amano said:**
> Since the drivers of the major GPU vendors nVidia and ATI will not support that in time for Jaunty and Plymouth integration was moved to Ubuntu 9.10, there is not too much point to have it for Jaunty. .

Actually, you will find the devs are going to create a PPA for Plymouth/KMS for testing purposes to easy the transition for 9.10.

If the 2.6.29 was default, that would make make it easier for Ubuntu to get testers.

---

### Post by Slug71 on 2009-01-18
> **jsmidt said:**
> Actually, you will find the devs are going to create a PPA for Plymouth/KMS for testing purposes to easy the transition for 9.10.

If the 2.6.29 was default, that would make make it easier for Ubuntu to get testers.

Oh yeh i forgot about that. I just wonder if the drivers will be down in time?
Having a Kernel wit KMS support and PPA for Plymouth but no drivers could turn out to be a big mess.

---

### Post by Pettman on 2009-01-18
> **amano said:**
> Since the drivers of the major GPU vendors nVidia and ATI will not support that in time for Jaunty and Plymouth integration was moved to Ubuntu 9.10, there is not too much point to have it for Jaunty. Because nobody will benefit from its abstract inclusion if no drivers hook it up.

Intel graphics cards will support it and there are quite a lot of people using gpu:s from intel, especially with a lot of netbooks using gpu:s from intel.

---

### Post by amano on 2009-01-18
Please consider the things that could be broken if Ubuntu ships a bleeding edge kernel. nVidia and ATI have to update their drivers in time for a new kernel and the experience from Ubuntu 8.10 told us that it was very hard to get an ATI driver in time (thus Ubuntu had to ship a beta catalyst driver).

This should be considered and the nVidia and ATI developers contacted for these reasons.

---

### Post by MadsRH on 2009-01-18
> **Pettman said:**
> Intel graphics cards will support it and there are quite a lot of people using gpu:s from intel, especially with a lot of netbooks using gpu:s from intel.

So Nvidia and ATI users will be booting in text mode?

---

### Post by Slug71 on 2009-01-18
> **MadsRH said:**
> So Nvidia and ATI users will be booting in text mode?

Yes if you install it and your drivers dont yet support KMS.

---

### Post by Miguel on 2009-01-18
I'm willing to bet a beer that radeon and radeonhd will have KMS before the end of the year. Nvidia users are spoilt enough with good performance and VDAPU ;-)

BTW: I can choose between an ATi HD 3470 and an Intel 4500MHD on my laptop (Thinkpad T400), but I've found I only use the ATi very ocassionally when booting into windows to play.

---

### Post by Slug71 on 2009-01-18
> **Miguel said:**
> I'm willing to bet a beer that radeon and radeonhd will have KMS before the end of the year. Nvidia users are spoilt enough with good performance and VDAPU ;-)

BTW: I can choose between an ATi HD 3470 and an Intel 4500MHD on my laptop (Thinkpad T400), but I've found I only use the ATi very ocassionally when booting into windows to play.

Yeh we'll definitely see drivers by the end of the year. We'll see better drivers not long after Jaunty release, just not in time for Jaunty which is why Plymouth was left out until 9.10.

---

### Post by mariuz on 2009-01-19
i have just rebuilded my vanilla rc kernel 

here is my guide for 2.6.29 

[http://mapopa.blogspot.com/2009/01/building-kernel-2.html](http://mapopa.blogspot.com/2009/01/building-kernel-2.html)

I have only tested it on an cloudbook (everex netbook)
and with via videocard 
The great news is that wireless chip rtl8187 now shows an better range (100%)
before was 16% 

I will say how it works with nvidia if it does:popcorn:

---

### Post by gtdaqua on 2009-01-19
Jaunty release schedule [states that kernel version finalization]("https://wiki.ubuntu.com/JauntyReleaseSchedule") must happen before April 9th. A Full two months out from today. That's plenty of time for .29 to come out. 

Linus released the first rc of .27 on Jul 28 and the final version on Oct 9. Thats a little over two months.
Linus released the next .28-rc1 on Oct 23 and .28 final on Dec 24. Thats [strike]one[/strike] two months he needed to finalize. So on this scale, .29 will be out before Jaunty Kernel Freeze (Apr 9) and who knows, may be Linus will be releasing 2.6.30 final before Apr 9.

Developers obviously will be considering kernel updates as they come out because the last three kernel updates have focused on graphics and wireless sorting several bugs out.

---

### Post by Podex on 2009-01-20
> **gtdaqua said:**
> Jaunty release schedule [states that kernel version finalization]("https://wiki.ubuntu.com/JauntyReleaseSchedule") must happen before April 9th. A Full two months out from today. That's plenty of time for .29 to come out. 

Linus released the first rc of .27 on Jul 28 and the final version on Oct 9. Thats a little over two months.
Linus released the next .28-rc1 on Oct 23 and .28 final on Dec 24. Thats one month he needed to finalize. So on this scale, .29 will be out before Jaunty Kernel Freeze (Apr 9) and who knows, may be Linus will be releasing 2.6.30 final before Apr 9.

Developers obviously will be considering kernel updates as they come out because the last three kernel updates have focused on graphics and wireless sorting several bugs out.

From Oct 23 to Dec 24 is 2 months, not one. So the average is more like 2 months.
Also I think a new kernel version should happen before Feature Freeze (February 19), because I'm pretty sure they count a new kernel as a feature.

---

### Post by mariuz on 2009-01-20
kernel 2.6.29 rc2 boots and works quite fine with nvidia 
(installed from their website)

[http://mapopa.blogspot.com/2008/12/tips-for-using-nvidia.html](http://mapopa.blogspot.com/2008/12/tips-for-using-nvidia.html)


I post this from that machine here is the screenshot

---

### Post by gtdaqua on 2009-01-20
> **Podex said:**
> From Oct 23 to Dec 24 is 2 months, not one. So the average is more like 2 months.
Also I think a new kernel version should happen before Feature Freeze (February 19), because I'm pretty sure they count a new kernel as a feature.

My mistake! I will edit it.

---

### Post by mortski on 2009-01-21
As of rc1, 2.6.29 has the new hrtimer backend for the alsa timer interface. This replaces the use of snd-rtctimer which is no longer available. This is important for, among others I assume, MIDI apps such as Rosegarden.

---

### Post by plun on 2009-01-23
Well.... 17s as boot-time  :D

---

### Post by Kosimo on 2009-01-28
2.6.29rc3 has just been released! ;)

[http://www.phoronix.com/scan.php?page=news_item&px=NzAyMQ](http://www.phoronix.com/scan.php?page=news_item&px=NzAyMQ)

---

### Post by forcecore on 2009-01-29
looks like 2.6.29 gives even more speed so it must be included in 9.04 even if it passes some day over feature freeze.

---

### Post by smani on 2009-01-29
As Jaunty focuses on making suspend/resume work for good, I'd say .29 is a must, as it seems to contain a fix for a timing bug in the kernel, see [http://torvalds-family.blogspot.com/2008/12/life-is-good-again.html](http://torvalds-family.blogspot.com/2008/12/life-is-good-again.html) and [http://www.phoronix.com/scan.php?page=news_item&px=NzAyMQ](http://www.phoronix.com/scan.php?page=news_item&px=NzAyMQ).

---

### Post by Starks on 2009-01-30
I thought .29 was confirmed for Jaunty.

At any rate, I'd rather not use kernelcheck if .29 will be hitting the repos.

---

### Post by jnw222 on 2009-01-31
links for pre-made kernels based on linux 2.6.29-rc3 (minamal drivers and no ubuntu patches (-:-)
[image]("http://www.jnw222.parahosting.net/linux/linux-image-2.6.29-rc3-3_2.6.29-rc3-3-10.00.Custom_i386.deb")

[headers]("http://www.jnw222.parahosting.net/linux/linux-headers-2.6.29-rc3-3_2.6.29-rc3-3-10.00.Custom_i386.deb")

[source code]("http://www.jnw222.parahosting.net/linux/linux-2.6.29-rc3.tar.bz2")

kernel boots in 4 secs on my laptop whole system around 50 secs, like 10 seconds faster that with 2.6.28

btw off topic: grub2?

---

### Post by Slug71 on 2009-02-01
> **Starks said:**
> I thought .29 was confirmed for Jaunty.

At any rate, I'd rather not use kernelcheck if .29 will be hitting the repos.

I'm pretty sure we'll get .29.
If i remember correctly we got the .27 Kernel at around RC-7 for Intrepid.

> **jnw222 said:**
> links for pre-made kernels based on linux 2.6.29-rc3 (minamal drivers and no ubuntu patches (-:-)
[image]("http://www.jnw222.parahosting.net/linux/linux-image-2.6.29-rc3-3_2.6.29-rc3-3-10.00.Custom_i386.deb")

[headers]("http://www.jnw222.parahosting.net/linux/linux-headers-2.6.29-rc3-3_2.6.29-rc3-3-10.00.Custom_i386.deb")

[source code]("http://www.jnw222.parahosting.net/linux/linux-2.6.29-rc3.tar.bz2")

kernel boots in 4 secs on my laptop whole system around 50 secs, like 10 seconds faster that with 2.6.28

btw off topic: grub2?

What about grub2?

It wont be in Jaunty if thats what youre asking.
Hopefully 9.10-KK.

But yes from what i'm reading about boot times with the .29 Kernel, its almost a must for this release since that is one of the main focuses of this release.

---

### Post by ViperScull on 2009-02-08
jnw22 thanks for the links. I tried to do it by myself, but I couldn't.

Could you explain me the detailed steps for the compiling and the packaging you did?

I've seen also you have had to patch it since it's not a full version, haven't you?

One more thing. Since the latest kernels support ext4, is there any way to install Intrepid in ext4?

---

### Post by Slug71 on 2009-02-08
RC-4 is out. :D

---

### Post by plun on 2009-02-08
> **Slug71 said:**
> RC-4 is out. :D

Yup, it is.....:popcorn:


I cannot see any big difference...;)

[[img]http://ubuntu-pics.de/thumb/9496/jaunty_20090209_2_zXKVcW.png[/img]](http://ubuntu-pics.de/bild/9496/jaunty_20090209_2_zXKVcW.png)

Testing....

---

### Post by IntuitiveNipple on 2009-02-10
Sorry to kill the hopes, speculation and gossip, but:

[SIZE="4"]**Ubuntu 9.04 (Jaunty) will ship with kernel version[COLOR="Red"] 2.6.28[/COLOR]**.[/SIZE]

---

### Post by Eclipse. on 2009-02-10
> **IntuitiveNipple said:**
> Sorry to kill the hopes, speculation and gossip, but:

[SIZE="4"]**Ubuntu 9.04 (Jaunty) will ship with kernel version[COLOR="Red"] 2.6.28[/COLOR]**.[/SIZE]

Do you have a source for that?

Thanks

---

### Post by IntuitiveNipple on 2009-02-10
> **Eclipse. said:**
> Do you have a source for that?
Yes - the Kernel Team.

---

### Post by Eclipse. on 2009-02-10
> **IntuitiveNipple said:**
> Yes - the Kernel Team.

I mean something clickable (first hand information), I actually checked the IRC meeting logs yesterday to see if anything had been discussed.

PS I'm not saying your wrong or anything, I personally dont even see much point in shipping .29 apart from btrfs.

---

### Post by IntuitiveNipple on 2009-02-10
> **Eclipse. said:**
> I mean something clickable (first hand information), I actually checked the IRC meeting logs yesterday to see if anything had been discussed.

PS I'm not saying your wrong or anything, I personally dont even see much point in shipping .29 apart from btrfs.

I added it as an agenda-item to the team meeting yesterday so it could be confirmed. It's in the meeting log.

---

### Post by Nullack on 2009-02-11
If thats true, the decision needs to be reversed. Pressure needs to be applied. We have to have .29.

---

### Post by ronacc on 2009-02-11
it's a marketing ploy ,if we get everything we want in 9.04 what will bring us back for 9.10 ?  :lolflag:

---

### Post by gtdaqua on 2009-02-11
.29 adds several compatability on various drivers. Also, I don't think there needs to be a pressure on the developers to integrate this kernel. Its only Feb now. Hopefully the .29-final will come out before this month ends and it will be merged with jaunty.

---

### Post by plun on 2009-02-11
> **ronacc said:**
> it's a marketing ploy ,if we get everything we want in 9.04 what will bring us back for 9.10 ?  :lolflag:

Well...who knows  :confused:  Maybe its more to please Debian ?

But maybe someone can explain this better....?

Alpha 4 is nevertheless the last milestone for new functions.
Alpha 5 and 6 must be for hardened a distribution.

It must be "The Debian agenda"....:lolflag:

---

### Post by Slug71 on 2009-02-11
> **ronacc said:**
> it's a marketing ploy ,if we get everything we want in 9.04 what will bring us back for 9.10 ?  :lolflag:

Well i dont know about you but i'll be back for:

1. Packagekit
2. Plymouth
3. Login Experience/Facebrowser

And hopefully Gnome-do and Wallpaper-tray will be installed by default too. :)

---

### Post by Cloud79 on 2009-02-11
> **nullack said:**
> if thats true, the decision needs to be reversed. Pressure needs to be applied. We have to have .29.

+1

---

### Post by klim8 on 2009-02-11
[https://lists.ubuntu.com/archives/kernel-team/2009-February/004321.html](https://lists.ubuntu.com/archives/kernel-team/2009-February/004321.html)

---

### Post by Slug71 on 2009-02-11
Another decision i just dont get. Why????
I dont really see a need for it since we dont have driver support for KMS but i thought the reason to include it was shifted for Btrfs support so that developers and crazy testers could start playing with it.

Perhaps the biggest drawback for me is that, that means we will begin Alpha testing for 9.10 with the 2.6.28 Kernel. 
Absolutely ridiculous.

---

### Post by Nullack on 2009-02-11
I have kicked off the discussion by posting on the Ubuntu developer discuss mailing list. I encourage everyone to support the discussion on the mailing list.

---

### Post by Eclipse. on 2009-02-11
> **Slug71 said:**
> Another decision i just dont get. Why????
I dont really see a need for it since we dont have driver support for KMS but i thought the reason to include it was shifted for Btrfs support so that developers and crazy testers could start playing with it.

Perhaps the biggest drawback for me is that, that means we will begin Alpha testing for 9.10 with the 2.6.28 Kernel. 
Absolutely ridiculous.

I highly doubt 9.10 will use .29, more likely we will have .30 or .31 depending on how upstream development goes.

I think shipping with .28 is the best option, the vast majority of its features are experimental.Using .28 will ensure a well polished kernel for release.

---

### Post by Slug71 on 2009-02-11
> **Eclipse. said:**
> I highly doubt 9.10 will use .29, more likely we will have .30 or .31 depending on how upstream development goes.

I think shipping with .28 is the best option, the vast majority of its features are experimental.Using .28 will ensure a well polished kernel for release.

I realize that 9.10 will likely ship with 2.6.30/31, probably .31 but 9.10 is also going to have Plymouth which depends on a Kernel that has KMS.

The later we have that Kernel and Plymouth in 9.10 is like throwing all the passed time which could have been used for testing, bug filing/fixing down the tubes.

Take Jaunty for instance. We only got the 2.6.28 Kernel and Ext4 towards the end of Alpha-2. If that happens with 9.10 we're pretty much throwing away almost 2 months of testing, bug filing/fixing.

With .29 in from the begining of the cycle and KMS there. Plymouth can be brought in earling during the dev cycle opening up the test window.
Same goes with Login Experience and Packagekit.

---

### Post by Eclipse. on 2009-02-11
> **Slug71 said:**
> I realize that 9.10 will likely ship with 2.6.30/31, probably .31 but 9.10 is also going to have Plymouth which depends on a Kernel that has KMS.

The later we have that Kernel and Plymouth in 9.10 is like throwing all the passed time which could have been used for testing, bug filing/fixing down the tubes.

Take Jaunty for instance. We only got the 2.6.28 Kernel and Ext4 towards the end of Alpha-2. If that happens with 9.10 we're pretty much throwing away almost 2 months of testing, bug filing/fixing.

With .29 in from the begining of the cycle and KMS there. Plymouth can be brought in earling during the dev cycle opening up the test window.
Same goes with Login Experience and Packagekit.

If KMS was wanted then the kernel team could easily include it in .28, like has happened in Fedora 10..Regarding Plymouth we should be fully concentrating on getting the boot time down so that we dont even have to see Plymouth, which the developers seem to be doing.

---

### Post by Slug71 on 2009-02-11
> **Eclipse. said:**
> If KMS was wanted then the kernel team could easily include it in .28, like has happened in Fedora 10..Regarding Plymouth we should be fully concentrating on getting the boot time down so that we dont even have to see Plymouth, which the developers seem to be doing.

Getting a boot time down to those sort of times is IMO just not going happen.

---

### Post by Manosdoc on 2009-02-11
Very Bad.
Very bad attitude From Tim when Explaining "Is it enough to stop rumors ?"
It would be better to say why.
Anyway.
They will find lot of people switching to Fedora..

---

### Post by Nullack on 2009-02-11
Well I think the explanation on the devel discuss is fair. In particular, backporting any missing important fixes into .28 from .29 that upstream havent done is good.

---

### Post by inportb on 2009-02-12
Well, KMS would not mean much for me until the radeon driver supports it... but when it does, Fedora might be a nice distro to try :P

---

### Post by jnw222 on 2009-02-12
kernel 2.6.29-rc4 is coming soon
but one problem
my host only allows 3 gb of bandwith per month (120 or so downloads) AND IT IS KILLED by like 130 downloads (24 source. 96 image 58 headers)

status:compiling may not be totaly generic, may have left some important drivers out, but you cant download it until by bandwidth resets
 (
or can someone tell me of a good host with massive bandwidth (google page creator...)

---

### Post by Starks on 2009-02-12
Any chance at a linux-meta ppa for .29?

---

### Post by forcecore on 2009-02-13
but does ubuntu uses critical patches from .29 and does .28 has same fast bootup like this test was by ubuntuforums user plun: 
[http://ubuntuforums.org/attachment.php?attachmentid=100858&d=1232752505](http://ubuntuforums.org/attachment.php?attachmentid=100858&d=1232752505)

---

### Post by caryb on 2009-02-13
Why not make it a optional install like KDE4 in Hardy:confused:


Cary

---

### Post by phrostbyte on 2009-02-13
> **caryb said:**
> Why not make it a optional install like KDE4 in Hardy:confused:


Cary

I think it's a bit different because the kernel, being the thing that basically supports and serves the entire operating system, can effect all running programs. So it will make bug reporting and stuff confusing. Overall though I support the decision, especially if it ends up that .29 is released in April. If it's released next week or something then they should ship .29 but whatever. :P

---

### Post by plun on 2009-02-14
2.6.29-RC5 is out....

> It's a (faked) magical moment to release a kernel, so there it is. 

The dirstat shows it all:

  88.6% drivers/net/
   4.9% drivers/staging/at76_usb/

ie practically all of the changes come from some driver updates, the bnx2 
firmware update, and one of the staging drivers. And even there, the bulk 
of the changes to the at76_usb driver was actually a revert.

All the rest is pretty much a collection of trivial small fixes. Yes, 
there's a Intel SVDO update that shows up in diffstat, but the rest 
really is pretty tiny.

Which is just how I like it.

So go out and test the heck out of it, because I'm going to spend the 
three-day weekend drunk at the beach. Because somebody has to do it.

		Linus



[http://lkml.org/lkml/2009/2/13/346](http://lkml.org/lkml/2009/2/13/346)


Start Kernelcheck....:)

---

### Post by slavik on 2009-02-14
> **Slug71 said:**
> I have never understood this myself why they dont just work longer on a kernel and do less releases. Theyre gonna have to think about it at some point if theres gonna be no 3.x.x Kernel.
release early, release often. would you like to test 20 features or 5? there are many people who build their own kernel.

---

### Post by plun on 2009-02-14
> **slavik said:**
> release early, release often. would you like to test 20 features or 5? there are many people who build their own kernel.

@slavik...   can you please merge [the other thread]("http://ubuntuforums.org/showthread.php?t=1068956") about this  which someone started ?  

In the other thread Phoronix also misses the point....


For all Lazy, Pete Graners complete message


[http://blog.redvoodoo.org/2009/02/jaunty-kernel-bits.html](http://blog.redvoodoo.org/2009/02/jaunty-kernel-bits.html)


> **Jaunty Kernel Bits**

It has been a long few weeks, with that said I'll try and recap some of the more interesting things that have been going on with Ubuntu, specifically the kernel happenings in the Jaunty Jackalope release.

The Platform Team met in Berlin for the Jaunty Platform Sprint for the week of 2-6 Feb. This was an incredible event with the vast majority of the Canonical Engineering teams. We had both cross team and individual sub-team tracks. The kernel track covered all of the release roadmap items and administrative topics.

I'll talk about some of the roadmap items and the most interesting highlights...

***Kernel Version***

The Jaunty Kernel version will be 2.6.28. We considered 2.6.29, it was not selected however due to all of the major changes. The primary reasons were due to the large number new features that are scheduled to land in it. Regression of functionality is a large concern and there would be a good chance of that happening given when estimated date that Linus will declare it baked. Unfortunately it just doesn't line up with the Jaunty release cycle. On the bright side... for Jaunty+1 we will have time to shake out any issues and are looking towards 2.6.30 or .31

***Suspend & Resume***

We are making the suspend & resume one of our top priorities for this cycle. We ran a suspend and resume workshop with every notebook at the sprint.

Surprisingly we had a small number of failures. Most of them were on resume with NVidia video. We did not test the priority divers only the free ones. Out of 65 machines tested (various models) there were 12 failures.

We will be issuing a Call For Testing at the Beta release, however for those of you that want to play along at home early you can visit the Suspend/Resume wiki here: [https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting](https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting) and some more of the background material is here: [https://wiki.ubuntu.com/KernelTeam/SuspendResume](https://wiki.ubuntu.com/KernelTeam/SuspendResume)

Some other notable suspend and resume news for Jaunty...

    * There is a new testing script to test (and stress test) suspend resume.
    * Suspend/Resume script will also be integrated into checkbox (aka System->Administration->System Testing) for ease of testing.
    * If a suspend/resume cycle fails it is detected by apport and the user will have the option of filing a bug

**_Vanilla Kernel Builds_**

[B]Starting with Alpha 5 we will have available .deb packaged pure upstream vanilla kernels available.

The primary intent for doing this is to allow our community to test kernels without the Ubuntu "sauce", that is things that we add to the kernel to support the Ubuntu distribution. The goal is to help get wider testing of the upstream kernel source by leveraging interesting Ubuntu Community members.[/B]

In addition to Jaunty we are doing this for Hardy, Intrepid and the current active kernel development branch. The planned update schedule for each of these is:

    * Hardy, Intrepid - Upon a stable upstream point release i.e. 2.6.27.3
    * Jaunty - Every RC until release final is declared. Then it will fall into the same cycle as Hardy & Intrepid
    * Current active devel branch - Currently 2.6.29 updated on every RC release

**_The plan is to have them available in the Ubuntu-Kernel-Team PPA, until them you can find them at:_** [http://kernel.ubuntu.com/~apw](http://kernel.ubuntu.com/~apw)

There is a lot more and I'll talk more about them later. As usual I'm on a plane back from Europe and my battery is beginning to run low, so thats prob about enough for this post.

~pete 



So it will be bleeding-edge kernels also for Ubuntu for users that dont want to build a kernel.

BUT... building a kernel is fun and interesting...:guitar:

---

### Post by autocrosser on 2009-02-14
Yes--please merge the threads--I have a idea that needs to be pushed & it's in the other thread.........

---

### Post by Starks on 2009-02-15
So... What does this mean?

2.6.29 will get packaged for the repos, but won't ship with Jaunty?

---

### Post by inportb on 2009-02-15
> **Starks said:**
> So... What does this mean?

2.6.29 will get packaged for the repos, but won't ship with Jaunty?

I see some interesting kernels at [http://kernel.ubuntu.com/~apw/](http://kernel.ubuntu.com/~apw/) :P

---

### Post by Starks on 2009-02-15
Too bad the framebuffer bootlogo and intel kms aren't enabled.

Guess I'll have to roll a 20-sided kernel and hope for a +5 Usability.

---

### Post by inportb on 2009-02-15
What do the fancy splash and KMS have to do with usability? It looks like you're going for +x Charisma.

---

### Post by Starks on 2009-02-15
> **inportb said:**
> What do the fancy splash and KMS have to do with usability? It looks like you're going for +x Charisma.

Hush. I am the dungeon master.

---

### Post by jnw222 on 2009-02-18
dang, someone else took my hobby of making-rc kernels
i am going to stop trying to uplaod my kernels, as someone else is

---

### Post by khiraly on 2009-02-21
Hi!

I have installed 2.6.29-rc5 from here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29-rc5/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29-rc5/)

And there is a huge performance benefit in video acceleration.
I have a intel 4500MHD video card inside my laptop, with the 2.6.28 kernel switching between workspaces or the expo effect is not really smooth, kind of laggish.

With the 2.6.29-rc5 kernel it is smooth all the time, really eyecandy.

So if you have an intel videocard, I highly recommend to upgrade to this kernel. And upgrade is as simple as doing some dpkg -i on the downloaded debs. (and install the requisite, if it fails).

However the suspend and resume is broken as before (see bug: [#324808]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/324808"))

Best regards, 
 Khiraly

---

### Post by khiraly on 2009-02-21
I got curious if it is really a graphical accerelation benefit, and I tried out Enemy terrority with this new kernel.

With 2.6.28 kernel the Enemy terrority performance was between 9-14fps, and more often 9 fps.

With this new 2.6.29 kernel, the performance is 19fps average, if I see against a simple wall it can go as high as 29-30fps, and the 14fps is the lowest however.

So from my experience it is at least **double** performance as before. I'm impressed.

Actually Enemy Terrority became playable under this new kernel.

---

### Post by Tich666 on 2009-02-21
Great news!
I also have the 4500MHD and I'm hoping for improved performance with the .29 kernel, guess I'll give it a try soon. :)

---

### Post by 3togo on 2009-02-21
30fps? At this frame rate, it is more than just playable. Rather, it is definitely very killable. You can't survive the dog fight, can you ?

> **khiraly said:**
> I got curious if it is really a graphical accerelation benefit, and I tried out Enemy terrority with this new kernel.

With 2.6.28 kernel the Enemy terrority performance was between 9-14fps, and more often 9 fps.

With this new 2.6.29 kernel, the performance is 19fps average, if I see against a simple wall it can go as high as 29-30fps, and the 14fps is the lowest however.

So from my experience it is at least **double** performance as before. I'm impressed.

Actually Enemy Terrority became playable under this new kernel.

---

### Post by khiraly on 2009-02-21
> **3togo said:**
> 30fps? At this frame rate, it is more than just playable. Rather, it is definitely very killable.

If 30fps would be the minimum, I wouldnt complain;)

But when on a large map it is constantly around 14fps, it is just around playable.

> You can't survive the dog fight, can you ?

Would you elaborate? I do not understand...

Anyway I didnt buy this laptop for gaming, but it is nice to have an average 3D performance with **open source** driver, with full xrandr support(rotating), nice effects(compiz), and hotplugging external monitor. So Im more or less happy with this buy. Just there is that little irritating suspend bug([#324808]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/324808")).

---

### Post by El Rey de Todo on 2009-02-22
I've grabbed the kernels from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29-rc5/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29-rc5/), but KMS doesn't seem to be enabled:

$ grep KMS /boot/config-2.6.29-020629rc5-generic
# CONFIG_DRM_I915_KMS is not set

Furthermore, adding "i915.modeset=1" to my kernel line results in an error about unknown boot option at boot.

I'm going to try compiling from the source, but I just thought I'd ask if anyone else had observed this?

---

### Post by khiraly on 2009-02-23
> **El Rey de Todo said:**
> I've grabbed the kernels from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29-rc5/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29-rc5/), but KMS doesn't seem to be enabled:

$ grep KMS /boot/config-2.6.29-020629rc5-generic
# CONFIG_DRM_I915_KMS is not set


I do not have this option either:

$ grep KMS /boot/config-2.6.29-020629rc5-generic 
# CONFIG_DRM_I915_KMS is not set


Without KMS I have at least double performance. So if KMS helps a little, Enemy terrority should be definietly playable. (at 800x600)

---

### Post by El Rey de Todo on 2009-02-23
I poked around in the menuconfig and I actually can't find a place to enable KMS. I did see an option to turn it on by default, but I figure the kernel boot argument should be sufficient (and esier to disable in case it doesn't work!). Why would it offer me an option to turn on by default if the option wasn't being compiled in at all? Maybe CONFIG_DRM_I915_KMS doesn't mean what I think it means...

Anyone know if there's a log message somewhere I can check to see if KMS is actually enabled?

---

### Post by plun on 2009-02-23
RC6 is out.... cannot see any diff with my 1000Hz kernel.

[http://groups.google.com/group/fa.linux.kernel/browse_thread/thread/70eab1d351194ec7/b26e6e1cf451c520?show_docid=b26e6e1cf451c520](http://groups.google.com/group/fa.linux.kernel/browse_thread/thread/70eab1d351194ec7/b26e6e1cf451c520?show_docid=b26e6e1cf451c520)


> This is mostly lots of small fixes, with the stats being dominated by some
DocBook movement and an ia64 defconfig addition:

  20.4% Documentation/DocBook/
   3.9% Documentation/
   2.0% arch/arm/
  30.2% arch/ia64/configs/
   5.5% arch/x86/
   2.4% arch/
   3.8% drivers/gpu/drm/i915/
   2.3% drivers/scsi/
  12.6% drivers/
   2.2% fs/btrfs/
   5.5% fs/cifs/
   2.3% fs/

(the above is the "non-cumulative" dirstat, which doesn't add up
subdirectories cumulatively, and thus highlights individual directories
that contain changes, rather than the top-level directories).

But most of the changes are really pretty small, and the shortlog gives a
feel for it. About 350 files changed, averaging roughly 20 lines of
changes per file - but the average is somewhat misleading, because most
changes are just a couple of lines, and then the "big" changes are about
moving a few hundred lines of documentation or the 1601 lines of
defconfig.

Regressions fixed, small cleanups, and some changes to help future
merging.

                Linus 

---

### Post by Mutiny32 on 2009-02-24
I think 2.6.29 it should be included in Jaunty. The whole mission of Jaunty was to be bleeding-edge and not-so LTS stable. But apparently that memo was lost somewhere. 

Hell, I think the current kernel should be built off of the 2.6.29 RC builds, as it is now at RC6.

By backporting kernel patches to 2.6.28, time and resources are wasted, not to mention the enabling of forward progress.

Oh, and I see the 2.6.29 kernels have been moved to a PPA, but I see no GPG key.

---

### Post by Nullack on 2009-02-24
> **Mutiny32 said:**
> I think 2.6.29 it should be included in Jaunty. The whole mission of Jaunty was to be bleeding-edge and not-so LTS stable. But apparently that memo was lost somewhere.

Thats incorrect. Releases are supposed to work, and .29 fixes are being backported into Ubuntu's kernel revision.

---

### Post by Kow on 2009-02-24
> **Mutiny32 said:**
> I think 2.6.29 it should be included in Jaunty. The whole mission of Jaunty was to be bleeding-edge and not-so LTS stable. But apparently that memo was lost somewhere. 

Hell, I think the current kernel should be built off of the 2.6.29 RC builds, as it is now at RC6.

By backporting kernel patches to 2.6.28, time and resources are wasted, not to mention the enabling of forward progress.

Oh, and I see the 2.6.29 kernels have been moved to a PPA, but I see no GPG key.

You sound like someone who should be using debian sid.

---

### Post by ronacc on 2009-02-25
I just installed .29-rc6 on amd64 , it not only booted to destop with the DKMS installed nvidia 180.29 driver it resolved a kerneloops I was having with .28-8 .

---

### Post by rogerdean on 2009-02-25
Hello all

I'd like to try the RC6 kernel to see if it sorts out my intel graphics. Khiraly, you say it's easy, but I'm a little out of my comfort zone, so could you (or someone) take me through it step-by-step?

Perhaps someone who needs a howto shouldn't be messing with the kernel, but I'd like to learn!

Cheers
Roger

---

### Post by lithorus on 2009-02-26
> **rogerdean said:**
> Hello all

I'd like to try the RC6 kernel to see if it sorts out my intel graphics. Khiraly, you say it's easy, but I'm a little out of my comfort zone, so could you (or someone) take me through it step-by-step?

Perhaps someone who needs a howto shouldn't be messing with the kernel, but I'd like to learn!

Cheers
Roger

Download debs from here [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29-rc6/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29-rc6/)

---

### Post by rogerdean on 2009-02-26
Right, will give that a go tonight. Is that really all there is to it?
R

---

### Post by rogerdean on 2009-02-26
apologies, duplicate post

---

### Post by jfernyhough on 2009-02-26
Apart from installing and rebooting. :P

---

### Post by rogerdean on 2009-02-26
Worked like a charm, thanks folks! Google Earth performance is now back to what it was in Hardy. So, does anyone know what might happen if I installed that kernel into Intrepid? Any particular reason it wouldn't work?
Cheers

---

### Post by Kosimo on 2009-02-26
Shame that we're not gonna see this kernel in Jaunty... :(

I'm sure that developers have their reason, and testing needs a lot of time and efforts that has been made already for 2.6.28 and moving to 2.6.29 would force them to start again. But I'm sure that 2.6.29 would be a better kernel in all senses, specially for drivers support in new hardware.

---

### Post by FireFoxer on 2009-02-26
> **lithorus said:**
> Download debs from here [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29-rc6/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29-rc6/)

Should I download the image deb or the headers deb?

---

### Post by ronacc on 2009-02-26
you should d/l the image and the headers for your arch + both of the all debs .

---

### Post by DougieFresh4U on 2009-02-26
Maybe a silly question, there are the .debs for 'image, headers, and source, is there not usually  a 'restricted' also and a couple of others?
Just wondering:-?

---

### Post by FireFoxer on 2009-02-27
Downloaded the needed files and used dpkg -i on them and it worked like a charm.

Thanks guys!

---

### Post by smbm on 2009-02-27
The performance improvements this kernel has brought to my setup are quite staggering!

It's a shame it's not going to make it into the final version. I guess the dev's have their reasons though.

Roll on 9.10.

---

### Post by Kosimo on 2009-02-27
How "dangerous" would it be to install this 2.6.29 kernel debs and keep using it in a everyday use computer?

---

### Post by smbm on 2009-02-27
I've had it running and been doing stuff on it all day and it seems pretty solid. In fact so far for me it's been more trouble free then 2.6.28. 

I probably wouldn't use any testing stuff on a proper production machine though. 

Good luck.

EDIT: I'll probably be using this kernel after release too if it's anything like this.

---

### Post by Kosimo on 2009-02-27
> **smbm said:**
> I've had it running and been doing stuff on it all day and it seems pretty solid. In fact so far for me it's been more trouble free then 2.6.28. 

I probably wouldn't use any testing stuff on a proper production machine though. 

Good luck.

EDIT: I'll probably be using this kernel after release too if it's anything like this.

I am using this kernel in a vmware machine and now, (for example) I'm unable to do the latest distribution upgrade. Can you do it?

---

### Post by smbm on 2009-02-27
There are some packages held back.

I think that's affecting everyone though.

There's a thread about it:

[http://ubuntuforums.org/showthread.php?t=1082102](http://ubuntuforums.org/showthread.php?t=1082102)

---

### Post by Kosimo on 2009-02-27
> **smbm said:**
> There are some packages held back.

I think that's affecting everyone though.

There's a thread about it:

[http://ubuntuforums.org/showthread.php?t=1082102](http://ubuntuforums.org/showthread.php?t=1082102)

We'll have this problem solved tomorrow then! ;)

---

### Post by Kow on 2009-02-27
> **Kosimo said:**
> How "dangerous" would it be to install this 2.6.29 kernel debs and keep using it in a everyday use computer?

Exactly as dangerous as using a RC kernel. 2.6.29 has a lot of changes so there may be quite a few regressions into userland. The first thing to do without is apparmour.

---

### Post by Starks on 2009-02-27
Is it possible to enable Intel KMS with these builds or do I need to roll?

---

### Post by portis on 2009-02-27
KMS support is not compiled in it. Boot with i915.modeset=1 leads to an unknown option warning.

> **Starks said:**
> Is it possible to enable Intel KMS with these builds or do I need to roll?

---

### Post by Starks on 2009-02-27
> **portis said:**
> KMS support is not compiled in it. Boot with i915.modeset=1 leads to an unknown option warning.
How do I roll it in without having it enabled by default?

Menuconfig seems to only offer Intel KMS if it is enabled by default.

Unfortunately, that doesn't allow me to disable it.

---

### Post by jerrylamos on 2009-02-27
Well, maybe I didn't install 2.6.29 right.  On my IBM ThinkCentre  with Intel i845 video the Intel Driver didn't work unless I did Option "NoAccel" at which point glxgears were slower than jaunty, vesa slower than jaunty, uxa didn't work period.  Intrepid much much better.

Jerry

---

### Post by night-wing on 2009-02-28
Ok, maybe that's just a silly question...

...but: What are the advantages when upgrading to kernel 2.6.29 instead of using the 2.6.28?

---

### Post by khiraly on 2009-02-28
Im also interested this KMS support in kernel. As the new intel driver (2.6.2) just released, and as I read it is mainly *bugfix* release, im wondering if my problems would simply go away.

My problem currently that on this laptop (4500mhd), after suspend/resume the compiz has glitches, 3D performance is like with .28 kernel (about half) and even wesnoth has problems when panning the screen. 


So Is there a prepackaged (KMS enabled) kernel mainly for intel driver testing?

If not how can we (I) help out the ubuntu packagers to creating one?

I would love to have 2.6.29 KMS enabled kernel with intel 2.6.2 driver and with the new xserver version. Im expecting performance gain and suspend/resume bugfix.

Khiraly

---

### Post by Tich666 on 2009-02-28
> **khiraly said:**
> I would love to have 2.6.29 KMS enabled kernel with intel 2.6.2 driver and with the new xserver version. Im expecting performance gain and suspend/resume bugfix.

That would be just too good to be true.

I'm afraid unless I learn how to compile the kernel and intel gfx drivers myself it'll be another year or so until my 4500mhd has even touched its performance potential.

What irks me most is that all these nice features (compositing with dual displays, x264 decoding acceleration, etc.) work on vista but on linux it's all a big mess or not working at all.

---

### Post by khiraly on 2009-02-28
> **Tich666 said:**
> That would be just too good to be true.

...

What irks me most is that all these nice features (compositing with dual displays, x264 decoding acceleration, etc.) work on vista but on linux it's all a big mess or not working at all.

Could you please tell me what is the average fps in enemy terrority under windows?

In linux with 2.6.28 kernel is 9-14 fps, with 2.6.29 kernel is 18-29 fps at 800x600 resolution (default one).

Just to compare how far we are from the windows version...

---

### Post by caryb on 2009-02-28
If you can tell me how to check I will do it for you as atm I'm on Vista (due to the breakages)



Cary

---

### Post by khiraly on 2009-03-01
> **caryb said:**
> If you can tell me how to check I will do it for you as atm I'm on Vista (due to the breakages)
Cary
You download the enemy territory game:
[http://enemy-territory.hu/ANONYMOUS/et_windows_v1.0.zip](http://enemy-territory.hu/ANONYMOUS/et_windows_v1.0.zip)

And the 2.6b update for it:
[http://enemy-territory.hu/ANONYMOUS/ET-2.60b-win32.zip](http://enemy-territory.hu/ANONYMOUS/ET-2.60b-win32.zip)

You launch the game, select **play online**, and click on the **connect to ip** button, and connect to a server where the **jaymod** modification is enabled. (Example: 91.120.21.81:27960).

When connecting it will automagically download the necessary maps, and the jaymod modification too.

After login, you go in the menu and jaymod, and select the **show fps** button. After selecting it, will display the current fps live at the right-middle of screen.

When you navigate in the game (as spectator, if you do not want to play actually) you can observe the fps. If the environment is simple (like you are watching a single wall) it can go up till 29fps. But the average for me is 18-24fps.

Thank you for testing it.

---

### Post by stefanwa on 2009-03-01
Does anyone use the official Nvidia drivers with the latest 2.6.29 kernel here? I tried installing them, but the installer always complains about the missing source tree. Of course I have installed the new header files and the sources in the correct(?) /usr dirs, but it's still a no go. I managed to start compiling the kernel modules at a point, but it stopped with some genksyms error.

Any hints? Thanks!

---

### Post by khiraly on 2009-03-01
And does anybody successfully installed **Virtualbox**?

I tried to install it, but I got this error:
```

Unpacking: virtualbox-ose-source innen: .../virtualbox-ose-source_2.1.0-dfsg-2ubuntu1_all.deb ...
Processing triggers for man-db ...
: virtualbox-ose (2.1.0-dfsg-2ubuntu1) ...
 * Starting VirtualBox kernel module...
   ...fail!

Setting up: dkms (2.0.21.1-0ubuntu1) ...
 * Running DKMS auto installation service for kernel 2.6.29-020629rc5-generic
   ...done.

Setting up: virtualbox-ose-source (2.1.0-dfsg-2ubuntu1) ...
 * Reloading kernel event manager...
   ...done.
Adding modules to DKMS build system
Doing initial module builds

Error! Bad return status for module build on kernel: 2.6.29-020629rc5-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/vboxdrv/2.1.0/build/ for more information.
Installing initial modules

Error! Could not locate vboxdrv.ko for module vboxdrv in the DKMS tree.
You must run a dkms build for kernel 2.6.29-020629rc5-generic (i686) first.
Done.
 * Stopping VirtualBox kernel module...
   ...done.
 * Starting VirtualBox kernel module...
   ...fail!

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

---

### Post by khiraly on 2009-03-02
> **khiraly said:**
> And does anybody successfully installed **Virtualbox**?


I figured out, that virtualbox is not compatible with the 2.6.29 kernel. It needs a small patch to be able to install it:
```



--- a/vboxdrv/linux/SUPDrv-linux.c 2008-12-29 16:15:53.000000000 +0000
+++ b/vboxdrv/linux/SUPDrv-linux.c        2009-01-04 00:02:20.346070537 +0000
@@ -703,7 +703,7 @@
     /*
      * Only root is allowed to access the device, enforce it!
      */
-    if (current->euid != 0 /* root */ )
+    if (current->cred->euid != 0 /* root */ )
     {
         Log(("VBoxDrvLinuxCreate: euid=%d, expected 0 (root)\n", current->euid));
         return -EPERM;
@@ -716,8 +716,8 @@
     rc = supdrvCreateSession(&g_DevExt, true /* fUser */, (PSUPDRVSESSION *)&pSession);
     if (!rc)
     {
-        pSession->Uid = current->uid;
-        pSession->Gid = current->gid;
+        pSession->Uid = current->cred->uid;
+        pSession->Gid = current->cred->gid;
     }

     pFilp->private_data = pSession; 

```

Here is a little howto how to modify the .deb archive.

1. Download the [virtualbox-ose-source_2.1.0-dfsg-2ubuntu1_all.deb](http://ubuntu.ipacct.com/ubuntu/pool/universe/v/virtualbox-ose/virtualbox-ose-source_2.1.0-dfsg-2ubuntu1_all.deb) file. Or find it in **/var/cache/apt/archives** directory. (If you already tried install virtualbox, it should be there)

2. Put this file into a working(tmp) directory:
```
mkdir try1; cp virtualbox*deb try1/; cd try1 
```

3. extract the .deb file (.deb file is simply an **ar** archive)
```
ar xv virtual*deb
```

4. extract the data.tar.gz file
```
tar -xzvf data.tar.gz
```

5. apply the patch, or hand-modify the **usr/src/vboxdrv-2.1.0/linux/SUPDrv-linux.c** file.

6. recreate the data.tar.gz file
```
rm data.tar.gz; tar -czvf data.tar.gz usr/
```

7. recreate the .deb archive
```

rm virtualbox*deb
ar rcv virtualbox-ose-source_2.1.0-dfsg-2ubuntu1_all.deb debian-binary control.tar.gz data.tar.gz
```

**Note:** the order is important (how to add files into the ar archive). So first add the debian-binary file, after control.tar.gz and finally the data.tar.gz file. If you create the ar archive in the wrong order, the dpkg command will not recognize the .deb file as a .deb file.

**OR**

1. If you trust me, you can download the already modified .deb file from here: [virtualbox.tar.gz](http://khiraly.googlepages.com/virtualbox.tar.gz)

(I packed into a .tar.gz file, because googlepages truncates the long filename.)
 
2. tar -xzvf virtualbox.tar.gz; dpkg -i virtualbox*deb

Hope it helps somebody.

Best regards, 
 Khiraly

---

### Post by khiraly on 2009-03-02
> **khiraly said:**
> I figured out, that virtualbox is not compatible with the 2.6.29 kernel. It needs a small patch to be able to install it:


It looks like I figured out myself;) It is not quite true, I have seen the solution on this site: [http://forums.virtualbox.org/viewtopic.php?t=12854](http://forums.virtualbox.org/viewtopic.php?t=12854)

(It is currently unavailable, but it exists in the google cache)

---

### Post by rogerdean on 2009-03-02
I installed the latest closed-source Intrepid .deb from the VB site. Then I installed the .29 kernel. Everything seems to be working fine...

---

### Post by Kosimo on 2009-03-04
Guys, 2.6.29-rc7 is out!

Just one more RC and this kernel will be ready

[http://www.phoronix.com/scan.php?page=news_item&px=NzExMw](http://www.phoronix.com/scan.php?page=news_item&px=NzExMw)

---

### Post by jfernyhough on 2009-03-04
Prebuilt: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by Kosimo on 2009-03-04
Linus notes for this new RC7

> The bulk of the patch is a couple of new drivers (ATL1c network driver and 
firewire FireDTV DVB receiver). That's due to the whole "new drivers can't 
regress" thing, although obviously if you compile them in, they may give 
you problems whether you have the hardware or not, as we found with the 
FireDTV driver ;)

But apart from the new drivers, it should all be just small fixes.  The 
shortlog (appended) tells the story.

I'm hoping we're getting closer to a final 2.6.29, but judging by the 
regression list, I suspect we'll have at least an -rc8 still coming up.

		Linus


---

### Post by smbm on 2009-03-04
rc7 seems to work okay here

---

### Post by ruik on 2009-03-04
RC7 working fine here too.

---

### Post by Tich666 on 2009-03-04
Yep, RC7 working great here too, even fixed the suspend/hibernate crash of xorg for me. :)

---

### Post by paul_in_london on 2009-03-05
> **jfernyhough said:**
> I did to begin with and DKMS would build (but something would break later in the install so the custom kernel would stay unconfigured and apt/aptitude etc would complain every time I installed something new).

I'm now using the 29-rc6 kernel from the kernel team's "repo" (i.e. file dump): [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) . Everything works.

Oh, and as I type I notice rc7 is built. Nice. So in a moment I'll be running 29-rc7. ;)

Nice one centurion! I'll give 29-rc7 a whirl when I get a chance. (Wasn't sober enough when I got back from the pub last night).

Am I right in thinking that these 2.6.29 kernels don't have a corresponding version of the linux-restricted-modules package?

Do I need one to get nvidia working with 29-rc6 or 29-rc7 and if not does it make much difference?

Thanks again for the info. :)

---

### Post by jfernyhough on 2009-03-05
Yup, these versions have no restricted or proprietary stuff, but Nvidia will still work as the drivers are a separate blob (i.e. not part of linux-restricted-modules). DMKS will simply rebuild the modules as for any new kernel.

---

### Post by paul_in_london on 2009-03-05
Top man! I'll try that soon. Many thanks.

---

### Post by rudenko_ruslan on 2009-03-13
Now it's time for -rc8:
[QUOTE=Linus Torvalds]This -rc isn't any more interesting than most, although I have to say that 
personally, it was interesting to see that we have actually been hitting a 
Atom CPU errata, and it took some effort from people to hunt it down.  
That was interesting, if only because it's a pretty rare occurrence.

We have a workaround (although not necessarily the final one) for that in 
this -rc, along with a lot of other mostly tiny changes. There's some 
bigger stuff in blackfin (the bulk of which was removals, in the form of 
'drop untested and useless "generic" board file') and some MIPS defconfig 
updates.

The only other non-small patch should be the addition of the at91 IDE 
driver. Other than that it's all pretty small.

In fact, it seems to be stabilizing to the point where I'm hoping that 
we're approaching a final 2.6.29, and this might be the last -rc. We'll 
have to see.[/QUOTE]
[http://lkml.org/lkml/2009/3/13/8](http://lkml.org/lkml/2009/3/13/8)

:-k

---

### Post by plun on 2009-03-13
> **rudenko_ruslan said:**
> Now it's time for -rc8:

[http://lkml.org/lkml/2009/3/13/8](http://lkml.org/lkml/2009/3/13/8)

:-k

Thanks..  compiled it and I cannot judge that this one is better then Ubuntus latest kernel...;)

Everything works with both for me and both are "snappy"....

---

### Post by MacUntu on 2009-03-13
I can almost smell 2.6.30-rc1. :D

---

### Post by khtaam on 2009-03-13
@plun

how do you compile it? do you use make-kpkg?
because I have tried it but it creates a deb that is larger than 200 MB, while the precompiled ones are about 20 MB.

---

### Post by jfernyhough on 2009-03-13
Apart from getting the pre-compiled versions from the Kernel Team, the easiest way I've found so far is using KernelCheck.

---

### Post by applemacmad on 2009-03-22
plun, have you been compiling your kernels under jaunty for jaunty? How did you go about doing it.
I've not had any success with any of my compiled kernels, using the jaunty 2.6.28 source, the vanilla 2.6.28 source and 2.6.29rc8, using both the ubuntu config and a custom/optimised one for my acer aspire one. 
The kernels compile and install correctly, however, when I boot I get the error message:
```
FATAL: could not load /lib/modules/<kernel name>/modules.dep : No such file or directory
```
Then it drops to the command line saying that root device could not be found.
I've used the same method to compile plenty of kernels before... but I've never got it working on Jaunty.
I'm using the "old fashioned" way, referenced here:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Any tips?

---

### Post by DougieFresh4U on 2009-03-22
I was using .29 kernel for a while, then last week when the driver for ATI came about I had to go back to the .28 kernel as the 'fglrx' was not playing nicely with .29 kernel. 
Can some one assist me in getting it to work with .29? All I got was a 'colorful' screen and no login screen.

---

### Post by plun on 2009-03-22
> **applemacmad said:**
> plun, have you been compiling your kernels under jaunty for jaunty? How did you go about doing it.
I've not had any success with any of my compiled kernels, using the jaunty 2.6.28 source, the vanilla 2.6.28 source and 2.6.29rc8, using both the ubuntu config and a custom/optimised one for my acer aspire one. 
The kernels compile and install correctly, however, when I boot I get the error message:
```
FATAL: could not load /lib/modules/<kernel name>/modules.dep : No such file or directory
```
Then it drops to the command line saying that root device could not be found.
I've used the same method to compile plenty of kernels before... but I've never got it working on Jaunty.
I'm using the "old fashioned" way, referenced here:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Any tips?


OK, I am lazy and always using Kernelcheck ;)

[http://ubuntuforums.org/showthread.php?t=618563](http://ubuntuforums.org/showthread.php?t=618563)

It breaks in the end and a reboot and a sudo dpkg --reconfigure -a is needed.

Both deb files builds just fins /usr/scr, image and headers

No problems with modules.  Ubuntus kernel -11 is just fine nevertheless.

---

### Post by pomalin on 2009-03-22
If the 2.6.29 is include I will be so happy, so so happy, because the 2.6.28 serie (all the serie) don't boot on my computer. And I compiled the 2.6.29-rc8 and it boot, so pleeease include the 2.6.29 pleease, and I will be able to use the live cd to have a fresh jaunty install instead of use the intrepid and upgrade to jaunty.

---

### Post by plun on 2009-03-22
> **pomalin said:**
> If the 2.6.29 is include I will be so happy, so so happy, because the 2.6.28 serie (all the serie) don't boot on my computer. And I compiled the 2.6.29-rc8 and it boot, so pleeease include the 2.6.29 pleease, and I will be able to use the live cd to have a fresh jaunty install instead of use the intrepid and upgrade to jaunty.

2.6.29 is not going to be included in Jaunty.

You can get it here nevertheless.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by pomalin on 2009-03-22
I see that, and it's so frustating to think I will burn jaunty cd just for friends.
See my bugreport here :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343268]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343268")

---

### Post by applemacmad on 2009-03-22
I've compiled a kernel from 2.6.29rc8 with KMS support. Plymouth looks great... except it won't boot further than that :x
KernelCheck is refusing to run for me... I'll try on another system tomorrow if I have no luck :(

---

### Post by Mutiny32 on 2009-03-23
Official word from Linus [here]("http://lkml.org/lkml/2009/3/23/449") and kernel.org shows it as well.

Too bad you guys are choosing to stick with 2.6.28 even before the kernel freeze for Jaunty.

---

### Post by andrewabc on 2009-03-23
Sad it wont be in.

---

### Post by Mutiny32 on 2009-03-23
Personally, I think it's a bad decision to not release it with the latest stable kernel iteration. It's a change from what has been done in the past and it hints of bureaucracy starting to develop in the community; the type that slows more bold advances that Ubuntu is known for.

---

### Post by Simian Man on 2009-03-23
> **Mutiny32 said:**
> the type that slows more bold advances that Ubuntu is known for.

Which bold advances are you thinking of exactly?  Ubuntu is never particularly up-to-date in the Linux world, but shipping with an already old kernel is craziness.

---

### Post by Nullack on 2009-03-23
Youd be complaining louder with regressions from an immature set of new features.

Besides the kernel team have brought in upstream fixes from the .29 tree.

---

### Post by Mutiny32 on 2009-03-23
> **Simian Man said:**
> Which bold advances are you thinking of exactly?  Ubuntu is never particularly up-to-date in the Linux world, but shipping with an already old kernel is craziness.

I'm thinking about if I wanted stable, time-tested features, I'd go upstream. You know, Debian. 

And don't tell me to use Debian unstable. That's not my point.

---

### Post by Simian Man on 2009-03-23
> **Nullack said:**
> Youd be complaining louder with regressions from an immature set of new features.

Besides the kernel team have brought in upstream fixes from the .29 tree.

Personally I trust Linus and the rest of the kernel devs not to make mistakes *way* more than I'd trust Ubuntu packagers to incorporate fixes correctly.

---

### Post by Nullack on 2009-03-23
Perhaps you should take a visit to the kernel oops website :)

---

### Post by Mutiny32 on 2009-03-23
> **Nullack said:**
> Youd be complaining louder with regressions from an immature set of new features.

Besides the kernel team have brought in upstream fixes from the .29 tree.

Are they going to backport btrfs? Fixes for Ext4? Native drivers like the one for my rt2860 Wireless-N card? (Which BTW, STILL doesn't work correctly with the now deprecated debian driver package for it) 

Sounds like a waste of time to me, especially when a majority of the Ubuntu patches are already there in the new Kernel. 

And then you have the kernel deadline, which is a bit off and now you're going to have users asking "wtf why are we releasing with an old kernel?"

---

### Post by Nullack on 2009-03-23
Go and have a look at the Ubuntu kernel git. Its allready got the ext4 fixes.

---

### Post by Simian Man on 2009-03-23
There's a decent history of Debian meddling with stuff for their distribution rather than working upstream like they should.  This leads to breakage in the worst case and wasted time in the best.  It just isn't maintainable.  Ubuntu shouldn't follow this precedent but should ship with the real Linux kernel.

[quote=Mutiny32]I'm thinking about if I wanted stable, time-tested features, I'd go upstream. You know, Debian.

And don't tell me to use Debian unstable. That's not my point.[/quote]
I was agreeing with you :).

---

### Post by Nullack on 2009-03-23
If your really keen to use .29, the kernel team have a compile you can download.

---

### Post by Mutiny32 on 2009-03-23
> **Simian Man said:**
> There's a decent history of Debian meddling with stuff for their distribution rather than working upstream like they should.  This leads to breakage in the worst case and wasted time in the best.  It just isn't maintainable.  Ubuntu shouldn't follow this precedent but should ship with the real Linux kernel.


I was agreeing with you :).
Oh ;)

I just think maintaining Jaunty on the 2.6.28 kernel and backporting everything to it until the next release cycle rolls around is going to cause more headaches in the future than biting the bullet now; actually using these three weeks to make sure all ubuntu-specific and other patches work with 2.6.29 and if something mild is broken at release, release a patch for it.

I don't know of a single person who installs ANY Linux distribution and then doesn't immediately patch it unless they have damn good reason not to. In Ubuntu's case, this is done by default with the Update Manager unless deliberately changed.

---

### Post by Mutiny32 on 2009-03-23
> **Nullack said:**
> If your really keen to use .29, the kernel team have a compile you can download.
I know they have a PPA. But it doesn't work with restricted modules.

---

### Post by novafluxx on 2009-03-23
Its released, stable, more than 1 month before Jaunty is due out...Jaunty isn't even beta yet...why oh why can't they just use the newest stable kernel?

---

### Post by Mutiny32 on 2009-03-23
> **novafluxx said:**
> Its released, stable, more than 1 month before Jaunty is due out...Jaunty isn't even beta yet...why oh why can't they just use the newest stable kernel?
Because they already made up their mind about it two months ago. Before they had any clue about the release date of 2.6.29, other than it might be out before Jaunty goes final. 

Of course, Linus could pick a bone with this decision to not adopt and keep moving forward; sparking attention of users on Ubuntu becoming more conservitive and "old", or Mark could just say "stfu we're going to 2.6.29" and save the hassle. Neither of which I think will happen, because it's not that simple.

---

### Post by Mr. Picklesworth on 2009-03-23
> **Simian Man said:**
> There's a decent history of Debian meddling with stuff for their distribution rather than working upstream like they should.  This leads to breakage in the worst case and wasted time in the best.  It just isn't maintainable.  Ubuntu shouldn't follow this precedent but should ship with the real Linux kernel.


I was agreeing with you :).

Exactly! They should learn from Fedora, which has established itself as a distro (perhaps *the* distro) that pushes innovation upstream and has all the neat changes - not only in, but *stable* - as soon as they happen.

---

### Post by Nullack on 2009-03-23
A vast number of people would disagree with your opinion that Fedora releases are stable. The term bleeding edge from an arterial cut and being barely kept alive through transfusions comes to mind :D

---

### Post by Mutiny32 on 2009-03-23
> **Nullack said:**
> A vast number of people would disagree with your opinion that Fedora releases are stable. The term bleeding edge from an arterial cut and being barely kept alive through transfusions comes to mind :D

Our beef is that Ubuntu has traditionally been on the bleeding edge of keeping things up-to-date. The decision of sticking to an old kernel when a new stable one has been released, especially before this release emerges from alpha, is not adherent to the spirit of the entire project.

---

### Post by ronacc on 2009-03-23
I ran the .29 from the PPA for a few days and it ran fine . I droped back to the .28 for testing consistancy .

---

### Post by Mutiny32 on 2009-03-23
> **ronacc said:**
> I ran the .29 from the PPA for a few days and it ran fine . I droped back to the .28 for testing consistancy .


Yeah, the kernel team has been concurrently working on both, so it should be relatively painless.

Stubbornness has more to do with this than whether it works or not, I think.

---

### Post by rbmorse on 2009-03-24
I'm with Nullack on this one. Besides, all you guys will be teasing the koala two weeks after Jaunty goes final, anyway.

---

### Post by MacUntu on 2009-03-24
2.6.29 isn't stable - it's believed to be stable. That's why you cannot include it that close to the release.

---

### Post by quickshade on 2009-03-24
I think backporting is becoming a bigger problem in distros, they all focus on stable, but in reality your backport features from a soon to be current release to an older release that has been around for a while, creating more problems, solving those problems only to have an older kernel with some fixes in it and not helping out the real kernel developers. If we would stick with the current kernel, we could test it, make sure it is stable and apply fixes if needed. Instead of backporting them to an older kernel. Just seems like a waste of resources and time.

---

### Post by novafluxx on 2009-03-24
> **quickshade said:**
> I think backporting is becoming a bigger problem in distros, they all focus on stable, but in reality your backport features from a soon to be current release to an older release that has been around for a while, creating more problems, solving those problems only to have an older kernel with some fixes in it and not helping out the real kernel developers. If we would stick with the current kernel, we could test it, make sure it is stable and apply fixes if needed. Instead of backporting them to an older kernel. Just seems like a waste of resources and time.

I agree with you quickshade. I'm excited about 9.04 and would be so pleased if it included 2.6.29

Besides if there's any issues with it, they can be patched AFTER 9.04 launches, contributing to the current kernel by contributing fixes. Its not a long-term release, its a normal 6 month release, so why not include the latest kernel?

---

### Post by Mutiny32 on 2009-03-24
> **MacUntu said:**
> 2.6.29 isn't stable - it's believed to be stable. That's why you cannot include it that close to the release.

Look, I'll take the word of the man who invented Linux that it's stable, ok? It had 8 release candidates. That, on average is 6 more than Microsoft has and that is just a point release. 

There is also a reason there is a deadline for a kernel freeze in Ubuntu. As it stands, the kernel was frozen awhile back to 2.6.28. It is self-evident because all patches are being backported (see: waste of time) to that kernel release. 

If the Ubuntu team decides to stay with 2.6.28, they will be doing a hell of a lot of backporting in the 9.04 release. When it comes to start putting up a kernel for Karmic, all of those patches will have to be ported back to the latest kernel and there is no guarantee that this won't break stuff. 

So. There are nearly 3 weeks for the REAL kernel freeze. The Kernel team has been maintaining the 2.6.29 kernel and has had their own PPA already in place.

---

### Post by gtdaqua on 2009-03-24
The product has not even entered beta stage although it has frozen stuff for beta stage. Still, if the developers wished, they can integrate .29 but I don't think they will.

---

### Post by Kosimo on 2009-03-24
2.6.29 STABLE   Released!!!!


[http://www.phoronix.com/scan.php?page=news_item&px=NzE2NA](http://www.phoronix.com/scan.php?page=news_item&px=NzE2NA)

---

### Post by Kosimo on 2009-03-24
Linus note:


> It's out there now, or at least in the process of getting mirrored out.

The most obvious change is the (temporary) change of logo to Tuz, the 
Tasmanian Devil. But there's a number of driver updates and some m68k 
header updates (fixing headers_install after the merge of non-MMU/MMU) 
that end up being pretty noticeable in the diffs.

The shortlog (from -rc8, obviously - the full logs from 2.6.28 are too big 
to even contemplate attaching here) is appended, and most of the non-logo 
changes really shouldn't be all that noticeable to most people. Nothing 
really exciting, although I admit to fleetingly considering another -rc 
series just because the changes are bigger than I would have wished for 
this late in the game. But there was little point in holding off the real 
release any longer, I feel.

This obviously starts the merge window for 2.6.30, although as usual, I'll 
probably wait a day or two before I start actively merging. I do that in 
order to hopefully result in people testing the final plain 2.6.29 a bit 
more before all the crazy changes start up again.

		Linus


---

### Post by Sealbhach on 2009-03-24
Ubuntu is not a hobby distro, Canonical want Ubuntu to be a serious player in the commercial world - that means they will have to conservative about versions the releases they use. 

So I understand them not including the new kernel because they probably don't have the time to test it properly.


.

---

### Post by plun on 2009-03-24
Yup released and crashing.....;)

It builds just fine but my networking goes down after a while...no clues within logs either.

Its a 1000Hz kernel so I am going to compare it with "mainline" when its ready.

---

### Post by zevans on 2009-03-24
So it's now released, it fixes a number of Xorg related bugs, and the Intel chipset drivers finally work properly and provide a useful degree of acceleration.

In other words, if Jaunty is going to be useful to netbook users, we NEED 2.6.29!

---

### Post by Manosdoc on 2009-03-24
We're in Alpha, and they keep 2.6.28

Too shame. They will see in real world people switching to 29 through Launchpad. What a great desicion...

---

### Post by eyelessfade on 2009-03-24
The problem is you think 2.6.29 is rock stable and good to go.
Well let me tell you something. There is a reason why there isn't a 2.7.x kernel anymore, and that is because Torvalds think its the distros job to make a kernel stable and not the kernel-dev team. 

One month to test a new bleeding edge kernel which can effect thousands of other packages is just not possibly. If someone wanted the newest pidgin package I'm right behind you because that is a standalone package, and not a foundation. If you want bleeding edge kernels, use the ppa. Thats what they are there for.

---

### Post by Sealbhach on 2009-03-24
For business critical systems you need a well established tested system. You can't take the risk of bleeding edge.

---

### Post by Benjamin_Lebsanft on 2009-03-24
Sealbhach: Since when is jaunty targetted at business critical systems? Therefore we have LTS releases I thought.

---

### Post by Nullack on 2009-03-24
No, all that LTS provides is a longer term security warranty.

---

### Post by snowpine on 2009-03-24
Please people--Ubuntu is not a "bleeding edge" distro. It is derived from a 6-month-old snapshot of Debian Sid, and since the Debian project focused the last 6-12 months on prepping Lenny for stable release, 9.04 is going to be a fairly conservative release for Ubuntu. (This is the reason why OpenOffice 3.0 wasn't in Intrepid, for example; Debian Sid was frozen at 2.4.x until about a month ago.) 6.26.29 isn't in Debian yet, so it's not going to be in Jaunty.

---

### Post by Benjamin_Lebsanft on 2009-03-24
Ok but in the beginning of ubuntu it was that way, bleeding edge and dapper got stability for LTS. Now we're getting stable releases all the time, it's getting boring ;)

---

### Post by KCG102282 on 2009-03-24
> **Mutiny32 said:**
> I'm thinking about if I wanted stable, time-tested features, I'd go upstream. You know, Debian. 

And don't tell me to use Debian unstable. That's not my point.
What is your point?

---

### Post by Perpetual on 2009-03-24
Since 2.6.27 and 2.6.28 broke [booting with a lot of hp laptops]("https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/272247") it would be nice to see the 2.6.29 kernel.  I have a feeling though that since this has [not been fixed upstream]("http://bugzilla.kernel.org/show_bug.cgi?id=11973") that it will not be fixed in 2.6.29.  It's a shame and I am not blaming Ubuntu for this as all distributions are failing now.

---

### Post by Sealbhach on 2009-03-24
Use Arch or something if you want the latest. Use Ubuntu if you can't afford your system to break.


.

---

### Post by Closed_Port on 2009-03-24
> **eyelessfade said:**
> The problem is you think 2.6.29 is rock stable and good to go.
Well let me tell you something. There is a reason why there isn't a 2.7.x kernel anymore, and that is because Torvalds think its the distros job to make a kernel stable and not the kernel-dev team. 

One month to test a new bleeding edge kernel which can effect thousands of other packages is just not possibly. If someone wanted the newest pidgin package I'm right behind you because that is a standalone package, and not a foundation. If you want bleeding edge kernels, use the ppa. Thats what they are there for.
Exactly!

It's actually quite funny to see some people who don't seem to know much about how the kernel is developed and what a stable release means act as if not senselessly dropping an untested kernel into a stable release is an insult to Torvalds.

---

### Post by int on 2009-03-24
> **snowpine said:**
> Please people--Ubuntu is not a "bleeding edge" distro. It is derived from a 6-month-old snapshot of Debian Sid, and since the Debian project focused the last 6-12 months on prepping Lenny for stable release, 9.04 is going to be a fairly conservative release for Ubuntu. (This is the reason why OpenOffice 3.0 wasn't in Intrepid, for example; Debian Sid was frozen at 2.4.x until about a month ago.) 6.26.29 isn't in Debian yet, so it's not going to be in Jaunty.

This is not true, Ubuntu have lots of packages that aren't in Debian Testing/Experimental..

Openoffice 3.0 wasn't in Intrepid because it's well known that all major release from OpenOffice have lots of bugs.. So the 3.0.1 release after Intrepid.

It's well known that all major release from Kernel have regressions..

It's well known that if Ubuntu dev move to 2.6.29, will be lot's of people complaining that ubuntu don't have support to "graphics modesetting, WiMAX and AP wifi support, inclusion of squashfs and a preliminary version of btrfs, a more scalable version of RCU, ecryptfs filename encryption, ext4 no journal mode, support for filesystem freeze and other improvements".

I like being in "bleeding edge", but Ubuntu 9.04 are now in Freeze, "The purpose is to stabilize the archive".

---

### Post by MacUntu on 2009-03-24
> **Mutiny32 said:**
> Look, I'll take the word of the man who invented Linux that it's stable, ok?

Have you even read his release notes?

---

### Post by plun on 2009-03-24
Ubuntus build available

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/)

Testing...;)

---

### Post by Kosimo on 2009-03-24
> **plun said:**
> Ubuntus build available

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/)

Testing...;)

There's any PPA for this?

---

### Post by plun on 2009-03-24
> **Kosimo said:**
> There's any PPA for this?

This is Ubuntus official Vanilla ppa.

You just download/install  headers-all.deb, headers for your flavor and image for your flavor

I also noticed that Maintainers version must be choosed for grub/menu.lst, maybe a bug... ?

Happy kernel testing...:D

---

### Post by Afi on 2009-03-24
Thank you!

---

### Post by Kosimo on 2009-03-24
> **plun said:**
> This is Ubuntus official Vanilla ppa.

You just download/install  headers-all.deb, headers for your flavor and image for your flavor

I also noticed that Maintainers version must be choosed for grub/menu.lst, maybe a bug... ?

Happy kernel testing...:D

Thanks for the answer, but I meant is if there's any repository to add so I don't have to download and install this debs

---

### Post by plun on 2009-03-24
> **Kosimo said:**
> Thanks for the answer, but I meant is if there's any repository to add so I don't have to download and install this debs

Pete Graner, Ubuntu/Canonicals kernel manager wrote about it and I think this is probably on purpose.

[http://blog.redvoodoo.org/](http://blog.redvoodoo.org/)

> [B]Vanilla Kernel Builds
[/B]
Starting with Alpha 5 we will have available .deb packaged pure upstream vanilla kernels available.

The primary intent for doing this is to allow our community to test kernels without the Ubuntu "sauce", that is things that we add to the kernel to support the Ubuntu distribution. The goal is to help get wider testing of the upstream kernel source by leveraging interesting Ubuntu Community members.

"Nema problema" with deb files....;)

---

### Post by applemacmad on 2009-03-24
Is Intel KMS support enabled in the official 2.6.29 builds?

---

### Post by zika on 2009-03-24
since I see You already installed 2.6.29 on Your machines I wanted to ask: on my amd_64 9.04 alpha installation what am I to exepect if I follow the order: install ...hearders_all.deb, ...headers-amd_64.deb, ...image-amd_64.deb? what are the benefits and what are the caveats I should expect? what are the dangerous curves I should avoid ...? in a nut-shell I need some guidance not to mess up with a pretty solid and fast installation Jaunty gave me .. :)

---

### Post by Mutiny32 on 2009-03-24
> **MacUntu said:**
> Have you even read his release notes?
Where he said something about the fact that he thought about giving it one more RC because of the amount of patches added? No, Never read that.

He basically said that it's gotta be released sooner or later. He wasn't saying it was unstable, he was saying that a ton of fixes were committed up to the last RC and he didn't want to keep it in limbo forever. 

Like I said. It's labeled as "Stable" by the man who maintains it and has a very, very cautious tongue on labeling something. 

And to re-iterate; there have been *eight* ( 8 ) **Release Candidates** for 2.6.29. Release Candidate means that they are considered stable enough to release to the masses without fear of major issues. 

9.04 is still in alpha phase. There is no reason why 2.6.29 shouldn't be included in the final release of 9.04.

---

### Post by plun on 2009-03-24
> **zika said:**
> since I see You already installed 2.6.29 on Your machines I wanted to ask: on my amd_64 9.04 alpha installation what am I to exepect if I follow the order: install ...hearders_all.deb, ...headers-amd_64.deb, ...image-amd_64.deb? what are the benefits and what are the caveats I should expect? what are the dangerous curves I should avoid ...? in a nut-shell I need some guidance not to mess up with a pretty solid and fast installation Jaunty gave me .. :)

The primary goal from Pete Graners blog:

> The goal is to help get wider testing of the upstream kernel source by leveraging interesting Ubuntu Community members. 

Then its deb files so you cannot mess up things....;)

another goal is maybe to check something which is broken in 2.6.28 and compare it with 2.6.29.

There are tons with reasons for testing a kernel...

---

### Post by Mutiny32 on 2009-03-24
> **KCG102282 said:**
> What is your point?
Debian unstable is like driving a car that has a wheel with one lug-nut that's loose. It'll most likely start-up and drive, but you're probably going to crash and burn sooner than later.

---

### Post by KCG102282 on 2009-03-24
:d

---

### Post by KCG102282 on 2009-03-24
> **Mutiny32 said:**
> Debian unstable is like driving a car that has a wheel with one lug-nut that's loose. It'll most likely start-up and drive, but you're probably going to crash and burn sooner than later.


That is so far from the truth its funny :) If you would have said that about Debian Experimental I would agree :D

---

### Post by Simian Man on 2009-03-24
> **Nullack said:**
> A vast number of people would disagree with your opinion that Fedora releases are stable. The term bleeding edge from an arterial cut and being barely kept alive through transfusions comes to mind :D

When there is a problem with Fedora - which in my experience is rare - it is almost always caused by an upstream bug.  Fedora devs find them and then submit bugfixes directly to the upstream project.  This benefits everybody.  With Ubuntu, on the other hand, bugs are often caused by packagers (who often aren't the best programmers) fiddling with the sources unnecesarily.  So I *seriously* doubt that Ubuntu's heavily patched 2.6.28 kernel will be more stable than the official 2.6.29.

---

### Post by Kosimo on 2009-03-24
> **plun said:**
> The primary goal from Pete Graners blog:



Then its deb files so you cannot mess up things....;)

another goal is maybe to check something which is broken in 2.6.28 and compare it with 2.6.29.

There are tons with reasons for testing a kernel...

Sorry for my ignorance but, one question that comes up to my mind is: what about the official ubuntu kernel's "sub-versions"? Once 2.6.27 was released, ubuntu keep updating it to 2.6.27-1, -2, ecc.
This won't happen with 2.6.29 kernel release. So we can say that it won't me that "maintained" like any normal release isn't it?

---

### Post by Nullack on 2009-03-24
Patches are trivial next to new functionality like KMS, btrfs etcetc. In fact most of the fixes are only a few lines each worth of changes vs thousands of news lines in new typical new functionality.

Linus has openly said before he does allow regressions through to stable. His idea of stable is not the same as red hats idea of stable - look at what kernel version red hats enterprise software uses......

People who want to bleed on the edge can:

1. Modify ubuntu with custom configs
2. Use an alternate os, such as fedora

---

### Post by plun on 2009-03-24
> **Kosimo said:**
> Sorry for my ignorance but, one question that comes up to my mind is: what about the official ubuntu kernel's "sub-versions"? Once 2.6.27 was released, ubuntu keep updating it to 2.6.27-1, -2, ecc.
This won't happen with 2.6.29 kernel release. So we can say that it won't me that "maintained" like any normal release isn't it?

all ubuntu kernels are within the main archive

and this is pure vanilla kernels.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by zika on 2009-03-24
> **plun said:**
> all ubuntu kernels are within the main archive
and this is pure vanilla kernels.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
can You elaborate on the difference. if I install 29 could I (would I) make some damage or I could (almost always) revert back to 28 ... (ubuntu version) ... ? indulge my ignorance ... :)

---

### Post by Kosimo on 2009-03-24
> **plun said:**
> all ubuntu kernels are within the main archive

and this is pure vanilla kernels.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

If you see the 2.6.27 list you'll see many (sub-versions)
I think that we won't see any sub-version on 2.6.29

---

### Post by plun on 2009-03-24
> **zika said:**
> can You elaborate on the difference. if I install 29 could I (would I) make some damage or I could (almost always) revert back to 28 ... (ubuntu version) ... ? indulge my ignorance ... :)

You are installing deb files and built in deb files there are several Debian rules for software.

You don't mess up a PC with deb files....;)

These deb files also comes from Ubuntu and are built within Ubuntu environment.

But... stay away if you are unsure...;)

---

### Post by snowpine on 2009-03-24
> **Mutiny32 said:**
> Debian unstable is like driving a car that has a wheel with one lug-nut that's loose. It'll most likely start-up and drive, but you're probably going to crash and burn sooner than later.

That's absurd; Debian Unstable is plenty stable for the average Linux desktop user (I wouldn't recommend it for a server, though). Packages must pass through Experimental to get into Unstable, so it is not as "bleeding edge" as you might think. While it is true Ubuntu "fixes" many of the bugs in Debian Unstable, they also introduce new bugs. IMHO, a carefully maintained Unstable/Sid install (I am partial to Sidux) is no more likely to "crash and burn" than the current Ubuntu release.

---

### Post by KCG102282 on 2009-03-24
> **snowpine said:**
> That's absurd; Debian Unstable is plenty stable for the average Linux desktop user (I wouldn't recommend it for a server, though). Packages must pass through Experimental to get into Unstable, so it is not as "bleeding edge" as you might think. While it is true Ubuntu "fixes" many of the bugs in Debian Unstable, they also introduce new bugs. IMHO, a carefully maintained Unstable/Sid install (I am partial to Sidux) is no more likely to "crash and burn" than the current Ubuntu release.

Agreed :)

---

### Post by Simian Man on 2009-03-24
> **Nullack said:**
> Patches are trivial next to new functionality like KMS, btrfs etcetc. In fact most of the fixes are only a few lines each worth of changes vs thousands of news lines in new typical new functionality.

No they aren't.  New features like KMS and btrfs are wholly independent from the rest of the kernel - that's the point of kernel modules :).  Linux has support for dozens of file systems, but as long as you don't use them they won't affect you.  Yes these new features are obviously a lot more difficult to write, but their inclusion will not lead to instability.

What can lead to problems is applying patches and bug-fixes to already existing code bases.  Any programmer will tell you that you can't judge complexity by line count and "only a few lines" can introduce very subtle problems if not done carefully.  *That's* where regressions come from.

---

### Post by zika on 2009-03-24
first impression is: no difference. that is a good impression I think. ... :) I'll explore further ... :)

the only thing I can see now not working is apparmor module not being loaded at boot. (both on my amd_64 and i386 machine).

---

### Post by snowpine on 2009-03-24
2.6.29 just appeared while upgrading my sidux box; I am installing it right now! I am excited because I hear the new kernel has some nice new features for Intel Atom processors like the one in my Mini 9; does anyone know more details about this?

---

### Post by smbm on 2009-03-24
I'm running 2.6.29 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

As far as I can see so far graphics performance is massively improved on my Intel x3100. The performance/ondemand cpu scaling bug hasn't been fixed in 2.6.29 yet. Sound seems stable so far.

Does anyone know if we should be filing bugs against these on Launchpad or sending emails to devs? 

Presumably they want to know about bugs for them even if they're officially unsupported.

I will continue to run 2.6.28 day to day I think, so I can continue with the general Jaunty testing.

Thanks in advance.

---

### Post by sgosnell on 2009-03-24
Stable means different things to different people in different contexts.  In Debian, stable means development is finished, and there will be no more changes, ever.  It has nothing to do with crashes or anything else.  

If you want .29, then all you have to do is download and install it.  It's easy to do, and I've been running the various release candidates for some time.  I've had no crashes at all, and everything seems to work as well as in .28, if not better.

---

### Post by pomalin on 2009-03-24
As I say in a another place and in the bug I filled, the 2.6.28 serie, from ubuntu or from kernel.org don't boot on my system, the only way for me to see something instead of the blinking cursor after the message : Starting Up ...   is to boot with earlyprintk and I see some oops, and everything stop, so, for me the 2.6.29 kernel mean I can boot, and having it include in jaunty mean I will be able to boot the live cd and install a fresh version, instead of upgrading from intrepid. So If a dev is looking at this, and at my bugreport here : [https://bugs.launchpad.net/bugs/343268]("https://bugs.launchpad.net/bugs/343268") please do something, I aware that nobody will change something for only one person, but, I can't believe I'm the only one in the world with this hardware.

---

### Post by plun on 2009-03-24
I have the same error with networking after a while, it just stops.

also a hanging during restart....  alt-sysrq-b is needed.

Back on 2.6.28-11....;)

---

### Post by zika on 2009-03-24
as a matter of fact I have impression that my networking is better with 29 but that is difficult to conclude anything since it is prone to influence outside my environment that are unpredictable ... I will persist a little bit more...

---

### Post by El Rey de Todo on 2009-03-24
Anyone else having their screen go completely blank during boot of a 2.6.29 kernel? This actually started happening starting sometime around rc7. I've been back on 2.6.28 ever since then. One of my nightly updates caused the screen to go blank on the next reboot, and the kernel was *not* upgraded that night. Several X packages were.

This affects both my home and work laptops, which are different in practically every way: different generations of the intel graphics chip, one's 32-bit the other is 64-bit, different hardware brands, same Jaunty :-)

Any ideas?

---

### Post by sgosnell on 2009-03-24
If you install .29 via the .deb file, you will still have your current kernel present, and you can boot to either via Esc at bootup.  As far as I can tell, .29 is very stable, maybe moreso than .28.  It works better on my Asus EEE.

---

### Post by snowpine on 2009-03-24
> **sgosnell said:**
> If you install .29 via the .deb file, you will still have your current kernel present, and you can boot to either via Esc at bootup.  As far as I can tell, .29 is very stable, maybe moreso than .28.  It works better on my Asus EEE.

Do you notice any performance/battery life/boot time improvements on your eee?

---

### Post by vredley on 2009-03-24
> **snowpine said:**
> Do you notice any performance/battery life/boot time improvements on your eee?
Graphics are worse with 2.6.29; boot time is about the same (maybe slightly faster); wi-fi is a lot better. I haven't measured the battery life.

---

### Post by sgosnell on 2009-03-24
I see no difference in graphics.  Boot time is perhaps better, I haven't timed it.  No idea about battery time, I use AC most of the time, and don't tweak things for battery life anyway.

---

### Post by plun on 2009-03-24
> **El Rey de Todo said:**
> Anyone else having their screen go completely blank during boot of a 2.6.29 kernel? This actually started happening starting sometime around rc7. I've been back on 2.6.28 ever since then. One of my nightly updates caused the screen to go blank on the next reboot, and the kernel was *not* upgraded that night. Several X packages were.

Any ideas?

Yes, I notice the same as you, also running Plymouth and its broken with this kernel.

I am going to take a look at lkml.org about this and my trouble with networking.

EDIT

Networking [http://lkml.org/lkml/2009/3/24/215](http://lkml.org/lkml/2009/3/24/215)

--

---

### Post by Mutiny32 on 2009-03-24
> **KCG102282 said:**
> That is so far from the truth its funny :) If you would have said that about Debian Experimental I would agree :D
Err...that's what I meant. Sorry, used the wrong word.

---

### Post by int on 2009-03-24
The GNOME 2.26 is only in Ubuntu, and not in Debian unstable or experiment.

It's simple, Fedora have two month to release and ubuntu only have one.

---

### Post by Mutiny32 on 2009-03-24
2.6.29 has native drivers for my ralink 2860 802.11n card that actually work with WPA. The ones that are now deprecated and packaged with Ubuntu as a deb don't. So there's something good.

---

### Post by vredley on 2009-03-24
> **sgosnell said:**
> I see no difference in graphics.
Do you have UXA enabled? It is much faster than EXA with kernel 2.6.28, but enabling it with 2.6.29 doesn't seem to make any difference. However, my system locks up after about an hour with .28, and I strongly suspect Compiz and/or UXA are to blame. I also get an error message sometimes when booting with .28 &#8211; something like 'IO_DRIVE_CMD Failed', which in turn causes auto-login to fail. So I think .29 is a better bet, at least for the moment.

---

### Post by klange on 2009-03-24
Why is the kernel in the PPA compiled without KMS? This is the only reason I would ever have for upgrading, and it's disabled? It's probably the biggest feature in .29.

---

### Post by amano on 2009-03-24
But it is only a feature if something hooks up with it. And currently nothing does. What part of ubuntu would profit of KMS? Nothing.

---

### Post by avb on 2009-03-24
> **klange said:**
> Why is the kernel in the PPA compiled without KMS? This is the only reason I would ever have for upgrading, and it's disabled? It's probably the biggest feature in .29.

For now only intel support for kms. Driver will hang a pc once kernel is using kms and driver is not.

---

### Post by tghe-retford on 2009-03-24
Something must have changed between RC8 and the final release, because I have been having problems with my network. It might be a couple of minutes to a couple of hours, but I lose my Ethernet connection. I have had to drop back to RC8 and the network is working fine.

For your information, I am using the ASUS P5N-E SLI motherboard onboard Marvell 88E1116 PHY Gigabit LAN controller.

---

### Post by xebian on 2009-03-24
My only question is why it's not compiled with gcc 4.3?  

Otherwise, working nicely here with AMD x2 5600. ASUS mobo nvGeForce7200 64-bit Kubuntu 4.2.1 - Intrepid and Jaunty, nv 180.41, 64-bit flash, mplayer, amarok2, kaffeine, vbox 2.1.4, kde4 composting.

Other minor things which I can live without
- apparmor fail to load - module might need recompile?
- not sure why but everytime I boot back, mobo check for nic cable tells me it's not connected.  But it's not show stopper.  Not getting this from my Debian/sidux 29 kernel though.  :(

---

### Post by inportb on 2009-03-24
> **avb said:**
> For now only intel support for kms. Driver will hang a pc once kernel is using kms and driver is not.

That is true to an extent. However, the kernel supposedly still supports non-kms modules and could fall back to low-graphics boot if necessary.

---

### Post by eluminx on 2009-03-24
> **tghe-retford said:**
> Something must have changed between RC8 and the final release, because I have been having problems with my network. It might be a couple of minutes to a couple of hours, but I lose my Ethernet connection. I have had to drop back to RC8 and the network is working fine.

For your information, I am using the ASUS P5N-E SLI motherboard onboard Marvell 88E1116 PHY Gigabit LAN controller.

i am having the same issue, i had to revert back to rc8 as well.  At first i thought it was my router but i quickly realised it was the installation of the new kernel.  Anyone have more info on this????

---

### Post by sgosnell on 2009-03-25
> Do you have UXA enabled?I don't know.  I'm just using the default install, nothing special.  I have no desire for fancy 3D stuff.

---

### Post by plun on 2009-03-25
> **klange said:**
> Why is the kernel in the PPA compiled without KMS? This is the only reason I would ever have for upgrading, and it's disabled? It's probably the biggest feature in .29.

I checked this setting and this is the description

> **Enable modesetting on intel by default (DRM_I915_KMS)**

Choose this option if you want kernel modesetting enabled by default,
and you have a new enough userspace to support this. [B]Running old
userspaces with this enabled will cause pain[/B]. Note that this causes
the driver to bind to PCI devices, which precludes loading things
like intelfb.


Userspace ????

Send a mail to Pete Graner or a IRC question to the kernel team.

---

### Post by RAOF on 2009-03-25
> **plun said:**
> ...

Userspace ????
...

Userspace, as in "everything not the kernel".  IE: the X Intel driver - xserver-xorg-video-intel.  If that needs a build-time switch for kms, or Jaunty's version is too old for kms, then that's why kms isn't turned on there :).

---

### Post by klange on 2009-03-25
This was a major over-site on the side of the Kernel, as it creates a rather obtrusive chicken-egg situation... Guess I'll wait another 6 months...

---

### Post by eyelessfade on 2009-03-25
And to all you 2.6.29 in jaunty now!!!11 people [kernel-dev]("http://thread.gmane.org/gmane.linux.kernel/811167/focus=811699")

---

### Post by cl333r on 2009-03-25
> **vredley said:**
> Graphics are worse with 2.6.29; boot time is about the same (maybe slightly faster); wi-fi is a lot better. I haven't measured the battery life.

I think you mean worse drivers stack, not the kernel's ability to do basic graphics stuff, cause according to phoronix image processing and other stuff is almost 2x faster in 2.6.29:

[http://www.phoronix.com/scan.php?page=article&item=linux_2629_benchmarks&num=5](http://www.phoronix.com/scan.php?page=article&item=linux_2629_benchmarks&num=5)
and
[http://www.phoronix.com/scan.php?page=article&item=linux_2629_benchmarks&num=6](http://www.phoronix.com/scan.php?page=article&item=linux_2629_benchmarks&num=6)

Good news affecting Firefox and the likes:
> When it came to the SQLite performance, a serious performance regression began with the Linux 2.6.26 kernel ... Fortunately, this regression is now fixed. This is quite important considering SQLite is used by Mozilla Firefox, Adobe, and many other desktop applications.
[http://www.phoronix.com/scan.php?page=article&item=linux_2629_benchmarks&num=4](http://www.phoronix.com/scan.php?page=article&item=linux_2629_benchmarks&num=4)

---

### Post by landal on 2009-03-25
No way to see a build for lpia?

a good ppa will be with other port than only i386 and amd64 (even if it's a good start :))

---

### Post by snowpine on 2009-03-25
> **landal said:**
> No way to see a build for lpia?

a good ppa will be with other port than only i386 and amd64 (even if it's a good start :))

I can't remember the source for this (sorry), but I think I read that Atom support is built in to 2.6.29, therefore there is no need for a separate 2.6.29 lpia?

---

### Post by novafluxx on 2009-03-25
> **eyelessfade said:**
> And to all you 2.6.29 in jaunty now!!!11 people [kernel-dev]("http://thread.gmane.org/gmane.linux.kernel/811167/focus=811699")

Good thing I plan to use ext4 from now on eh?!

---

### Post by novafluxx on 2009-03-25
> **Sealbhach said:**
> Ubuntu is not a hobby distro, Canonical want Ubuntu to be a serious player in the commercial world - that means they will have to conservative about versions the releases they use. 

So I understand them not including the new kernel because they probably don't have the time to test it properly.


.

Yet they have the time to backport all the features? :lolflag:

---

### Post by Starks on 2009-03-25
> **eyelessfade said:**
> And to all you 2.6.29 in jaunty now!!!11 people

I think Linus is a pretty cool guy. eh writes kernels and doesn't afraid of anything. </meme>

---

### Post by Zorael on 2009-03-25
While not the best benchmark ever, I get +150fps in glxgears on my netbook (~590 -> ~740). However, once again I get [video corruption](https://bugs.kde.org/show_bug.cgi?id=170462) in KDE4.

It was earlier fixed by disabling an old fedora patch when compiling xserver-xorg-core, but something with the new kernel triggers it again.

I'm going to try to compile my own kernel, importing the 2.6.28-11 .config file and then tweaking it a bit. Not sure what good it'll do me, though. Perhaps it's an xserver-xorg-video-intel bug to begin with.

---

### Post by emil.s on 2009-03-25
Hi all!

Have my own 2.6.29 up and running with KMS support compiled in. But as expected, it freezes when adding "i915.modeset=1" to the kernel. 

Except the kernel, it's an up2date Kubuntu Jaunty installation on a Lenovo Thinkpad with an integrated "Intel GM965/GL960" graphics card.

Se what do I need to do (get from SVN and compile myself) to get KMS working? :)

---

### Post by xtoudi on 2009-03-25
> **emil.s said:**
> Hi all!

Have my own 2.6.29 up and running with KMS support compiled in. But as expected, it freezes when adding "i915.modeset=1" to the kernel. 

Except the kernel, it's an up2date Kubuntu Jaunty installation on a Lenovo Thinkpad with an integrated "Intel GM965/GL960" graphics card.

Se what do I need to do (get from SVN and compile myself) to get KMS working? :)

The same here. Dell Latitude D630 with Intel GM965/GL960.
Kernel 2.6.29 with: 
  CONFIG_DRM_I915=y
  CONFIG_DRM_I915_KMS=y
    ...and some other stuff.
With i915.modeset=1 (or without) screen is blank. With VGA mode I can only see that: "loading hardware drivers ...." - and thats all. But I think it's starting .... I do not know what happens later - Xorg is blank - every TTY tha same.

EDIT:
config taken from "config-2.6.29-020629-generic" and in my case this is Ubuntu Jaunty:)

---

### Post by marijus on 2009-03-25
@ emil.s, xtoudi

you will have to rebuild libdrm and xserver-xorg-video-intel (best from git) if you want kms to work...

---

### Post by xtoudi on 2009-03-26
> **marijus said:**
> @ emil.s, xtoudi

you will have to rebuild libdrm and xserver-xorg-video-intel (best from git) if you want kms to work...



Yes, I think you're right ... after a many compilation of kernel ... I've got working KMS and not working with this xorg :-).
System is booting very well with highres ... and startX and crash:-)
I'll try recomp what you said.

---

### Post by applemacmad on 2009-03-26
> **xtoudi said:**
> Yes, I think you're right ... after a many compilation of kernel ... I've got working KMS and not working with this xorg :-).
System is booting very well with highres ... and startX and crash:-)
I'll try recomp what you said.

Same here.

Are any special flags or arguments needed or do I need to pull it from a certain branch when compiling?

---

### Post by xtoudi on 2009-03-26
Now I've got xf86-video-intel-2.7-rc1 and libdrm-2.4.5. Sth is working ... but TTY is totally messed up!! X even worst.
xf86-video-intel-2.7-rc1 and libdrm-2.4.5 compiled without any special settings. hmmmmm I really don't know ... some special settings during compilation?

---

### Post by ffi on 2009-03-26
I think it would be better to include .29 as upgrading from .28 to .29 is a pain with ext4 partitions because of the deprication of the extends option. (ie. partitions with extends in their options won't mount anymore in .29)

Mdv uses .29 and for me (w/ asus m51 series laptop) this kernel has been a real progress, wireless wise, suspend and resume and powermanagement (basicly none of these worked properly in 28 but do work in 29)

---

### Post by yaztromo on 2009-03-29
Just upgraded to 2.6.29 final using the ppa to get around the ext4 soft lockup bug. Couldn't be easier with the provided debs. 2.6.29 is sweet :D

---

### Post by amano on 2009-03-29
Ext4 soft lockup bug?

At least the Ext4 data loss patches will we added to the 2.6.30 kernel. I hope that those can be backported to 2.6.28.

---

### Post by yaztromo on 2009-03-29
> **amano said:**
> Ext4 soft lockup bug?

At least the Ext4 data loss patches will we added to the 2.6.30 kernel. I hope that those can be backported to 2.6.28.

Soft lockup bug here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330824](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330824)

I assume it will be fixed in time for release.

I keep losing my ethernet with 2.6.29. It works for an hour or two then dies.

Edit: Reverting back to RC8 seems to have fixed the network for now. A few other people on this thread have got the same issue. My ethernet card is a "Lite-On Communications Inc LNE100TX"

---

### Post by tghe-retford on 2009-03-29
> **yaztromo said:**
> I keep losing my network with 2.6.29. It works for an hour or two then dies.
I had the same problem (although mine can die after a couple of minutes), along with someone else. I had to drop back to 2.6.29-RC8 to ensure I could keep my network going.

[http://ubuntuforums.org/showpost.php?p=6951590&postcount=242](http://ubuntuforums.org/showpost.php?p=6951590&postcount=242)

---

### Post by yaztromo on 2009-03-29
This looks like the issue

[http://groups.google.com/group/fa.linux.kernel/browse_thread/thread/8fbdcc815673c86f/d161220134ae467e?show_docid=d161220134ae467e](http://groups.google.com/group/fa.linux.kernel/browse_thread/thread/8fbdcc815673c86f/d161220134ae467e?show_docid=d161220134ae467e)

---

### Post by Zorael on 2009-03-29
Would anyone mind sharing the steps I'd need to take to compile the intel driver and needed drm/mesa libraries from git? For instance, do I need to explicitly enable KMS-awareness when compiling? Seeing as it's supposedly explicitly disabled in the intel driver I have from the xorg-edgers ppa.

```
Changes: 
 xserver-xorg-video-intel (2:2.6.99.1+git20090327.69c84f2c-0ubuntu0tormod) jaunty; urgency=low
 .
   * Checkout from git 20090327 (master branch) up to commit
     69c84f2c8204771b68f40ed64e64657237b54546
   * Only added debian/ tree from origin/debian-experimental
   *** Disable kernel mode setting**
   * Dropped debian/patches/*
   * Add lpia architecture
   * Add depends on libdrm-intel1 (lp 303177)
   * + hand-patched the one Debian patch
```

---

### Post by El Rey de Todo on 2009-03-29
I've actually compiled the intel driver from source at work b/c I was trying to help the intel guys track down a bug I was seeing.. Here's some pointers:

Paths to GIT repos. I only needed the first and fourth - the xf86-video-intel and the Mesa DRM driver.
[http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)

```
$ git clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-intel
$ git clone git://anongit.freedesktop.org/git/mesa/drm
```

Instructions to build and install:
[http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html)

Installation was pretty easy, the main problem was getting the build dependencies installed. That turned out to be easy too after I asked for help:
```
$ sudo apt-get build-dep xserver-xorg-video-intel
$ sudo apt-get build-dep libdrm-intel1
```

After that, each required the same simple steps to configure and build and install:
```
$ cd drm
$ ./autogen.sh --prefix=/usr
$ make
$ sudo make install
```

I didn't use any specific configuration options but if anyone has suggestions I'd love to hear them! Hope that helps!

---

### Post by DougieFresh4U on 2009-03-29
I was using the .29 kernel until they released the 'fglrx' for ATI last week. When I installed the 'fglrx propietary driver' machine would not boot. Machine is AMD Athlon  5200 dual core and ATI Radeon 3200 onboard graphics.
So I went back to .28 kernel. I am wondering what do I need to do to get 'fglrx' working with .29 kernel. When I boot up, it doesn't make it to login screen. I get nice colorful 'ubuntu' all over the screen.
Thanks for any help that can be provided.

---

### Post by mamamia88 on 2009-03-29
i'd rather they wait until it's ready and add it later in an update then try to force  it in by release

---

### Post by ysNoi on 2009-03-30
I'm excited for the final release....! :guitar::guitar:

---

### Post by plun on 2009-03-31
> **yaztromo said:**
> 
I keep losing my ethernet with 2.6.29. It works for an hour or two then dies.

Edit: Reverting back to RC8 seems to have fixed the network for now. A few other people on this thread have got the same issue. My ethernet card is a "Lite-On Communications Inc LNE100TX"

The network error seems to be fixed (testing just now) with git7 patches from kernel.org

Probably soon a stable update for 2.6.29.

---

### Post by zevans on 2009-03-31
> **plun said:**
> The network error seems to be fixed (testing just now) with git7 patches from kernel.org

Probably soon a stable update for 2.6.29.

I tried git6 just now (couldn't see a git7?!) and it feels faster, but that might because I compiled it with Atom-specific support and without a load of cruft (took out IP v6, etc.)

Wireless is working again, using the staging rtl8187se driver - like you this worked in RC8 and stopped working in the release.

However I have the X hang back again in git6 - stable 2.6.29 is OK with UXA and pretty fast, git6 LESS stable. (I'm on Intel, using DRI2.)

.29 either flavour is still WAY faster than .28.

---

### Post by Zorael on 2009-03-31
> **zevans said:**
> I tried git6 just now (couldn't see a git7?!) and it feels faster, but that might because I compiled it with Atom-specific support and without a load of cruft (took out IP v6, etc.)
Praytell, how do I enable that Atom-specific support? The "latest" processor family I can pick is Core2.

---

### Post by zevans on 2009-03-31
> **Zorael said:**
> Praytell, how do I enable that Atom-specific support? The "latest" processor family I can pick is Core2.

Core2/newer Xeon is indeed the correct one for Atom. Make sure you also have SMT (Hyperthreading) also enabled.

---

### Post by plun on 2009-03-31
> **zevans said:**
> I tried git6 just now (couldn't see a git7?!) 

Git8 for the moment  >>>>   [http://kernel.org/](http://kernel.org/)

Patch command before compiling
```

bzcat patch-2.6.29-git8.bz2| patch -p1
```

---

### Post by mendres on 2009-03-31
Glad to hear about the networking issue being a general error. Hope to see the patched package on the Ubuntu Kernel PPA the next days. ;)

---

### Post by xebian on 2009-04-03
Just saw 29.1 released but the ppa build is not there yet..hopefully soon?

Edit: just saw it there now

---

### Post by plun on 2009-04-03
Yup, built

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.1/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.1/)

.
.

---

### Post by Hero of Time on 2009-04-03
So, should it have a fix for loosing all network connections? I installed 2.6.29 yesterday, booted it today and with less than an hour of uptime, I lost my entire network, both wireless and wired.

And anyone got the framebuffer during boot working? All I get is a black screen. In a VM, where I tested it first, I see the resolution going up, but there too no video until X is started (switching to a TTY doesn't work, same blackness).

---

### Post by yaztromo on 2009-04-03
Yes I believe the network fix was scheduled for 2.6.29.1. My sound doesn't work in RC8 so hoping this kernel will be better.

---

### Post by zika on 2009-04-03
I've installed 2.6.29.1 from mainline. it does not show in synaptic. in case I want to remove it what should I do? (Jaunty, amd_64)

---

### Post by xebian on 2009-04-03
> **zika said:**
> I've installed 2.6.29.1 from mainline. it does not show in synaptic. in case I want to remove it what should I do? (Jaunty, amd_64)

Same way as how you installed it.  Except this time it's remove instead of install.
):P

---

### Post by smbm on 2009-04-03
> **zika said:**
> I've installed 2.6.29.1 from mainline. it does not show in synaptic. in case I want to remove it what should I do? (Jaunty, amd_64)

Or go to Origin in Synaptic (bottom right) and then goto Local/main in the panel above it, they should be there.

---

### Post by zika on 2009-04-03
they showed up in (local or obsolete) once I boot-ed in 2.6.28 ... thanks ... I looked there while in 2.6.29.1 but they showed up just now after boot. not a big deal but I do not like to have them lurking around not-accounted ... ;)

---

### Post by smbm on 2009-04-03
> **zika said:**
> they showed up in (local or obsolete) once I boot-ed in 2.6.28 ... thanks ... I looked there while in 2.6.29.1 but they showed up just now after boot. not a big deal but I do not like to have them lurking around not-accounted ... ;)

Yeah, I imagine removing a running kernel would be bad form. Glad you found it.

---

### Post by zika on 2009-04-03
> **smbm said:**
> Yeah, I imagine removing a running kernel would be bad form. Glad you found it.
I did not want to remove moving kernel ... :) I just wanted to see if it is properly installed. 2.6.28 shows up in synaptic even though it is now the only kernel on that partition ... I removed it now that I had everything checked since it does not give me any improvement (on the contrary).

one more question. every time after such a stretching (after clean total removal via synaptic) I'm left with initrd.img.old and vmlinuz.old (links) in / and no initrd.img and vmlinuz. I do sudo mv and rename them but is that a right way to do that? no side-effects yet but I'm a bit scared ... :)

---

### Post by yaztromo on 2009-04-03
Can confirm for thos that had problems with networking that it is fixed in this kernel.

ALSA still wouldn't work so I removed it and installed OSS which works lovely, even with flash 10.

---

### Post by Hero of Time on 2009-04-03
I don't have any issues with audio. Alsa, running through Pulse, works just fine.

Oh, and I have both .29 kernels in my synaptic, while I'm in .29.

---

### Post by zika on 2009-04-03
> **hero of time said:**
> i don't have any issues with audio. Alsa, running through pulse, works just fine.
+1

---

### Post by DougieFresh4U on 2009-04-03
I have the ATI Radeon 3200 onboard graphics. I cannot get fglrx to work with the .29, but it will work with .28. When I boot into .29, it gets to login screen as I can hear the system sound, but I have a black screen with 'ubuntu' mixed all around it. I have even typed my user name and password, not seeing login screen and it gets to the desktop, but not one that I can see, I am going by the system sounds I have set, so I know desktop is there(strange?)
What should I be doing to get 'fglrx' to work with .29?

---

### Post by mendres on 2009-04-03
Networking issue seems to be fixed finally :cool:

---

### Post by excogitation on 2009-04-04
> **plun said:**
> Yup, built

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.1/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.1/)

.
.

Just tried this build on my Wind U100 but it doesn't come with the rt2860sta module - do I need to build it from source or can I get it somewhere?

---

### Post by MindFlayer on 2009-04-04
> **excogitation said:**
> Just tried this build on my Wind U100 but it doesn't come with the rt2860sta module - do I need to build it from source or can I get it somewhere?

I've got a similar problem with the FireDTV module. I really wish it was compiled in there by default so I wouldn't have to mess with it by myself.

---

### Post by olskar on 2009-04-04
Reading this thread makes me feel a little sorry 2.6.29 will not be in Jaunty by default, seems to fix a lot of problems..

---

### Post by zika on 2009-04-04
is it me, is it how 2.6.29.1 was compiled on mainline, is it ... but "2.6.28-11-generic #40-Ubuntu SMP" works better ... with #38 and 2.6.29 was the other way around ... so at this moment I support decision of Ubunty team ...

---

### Post by DougieFresh4U on 2009-04-04
> **DougieFresh4U said:**
> I have the ATI Radeon 3200 onboard graphics. I cannot get fglrx to work with the .29, but it will work with .28. When I boot into .29, it gets to login screen as I can hear the system sound, but I have a black screen with 'ubuntu' mixed all around it. I have even typed my user name and password, not seeing login screen and it gets to the desktop, but not one that I can see, I am going by the system sounds I have set, so I know desktop is there(strange?)
What should I be doing to get 'fglrx' to work with .29?

Some one please rescue me!

---

### Post by zika on 2009-04-04
> **DougieFresh4U said:**
> Some one please rescue me!
try to find a way of installing (I think it is dkms) fglrx-module in Your kernel. that is the difference between Your 2.6.28 and 2.6.29 ... as far as I know ...

p.s. did You try kernel boot option "nopat" i.e. "pat={off,on,force}" ... ? I would be grateful if someone could explain this option in detail ...

p.p.s. after some "research" I found that PAT is not switched on in 2.6.28. You could check for 2.6.29 with, for example *grep PAT /boot/config-2.6.29...* let it complete itself ...

---

### Post by t.alex on 2009-04-04
> **DougieFresh4U said:**
> Some one please rescue me!

Some interesting reading ->[patch: vanilla fglrx for 2.6.29]("http://www.phoronix.com/forums/showthread.php?t=16173")

---

### Post by zika on 2009-04-04
> **t.alex said:**
> Some interesting reading ->[patch: vanilla fglrx for 2.6.29]("http://www.phoronix.com/forums/showthread.php?t=16173")
the same article I found and started exploration on PAT... ;)

---

### Post by Hero of Time on 2009-04-04
I still don't know how to use the framebuffer like with the older kernels (vga=xxx parameter at boot). And the TTY text goes beyond my screen display. The last few lines are shown off screen. Anyone has a solution?

---

### Post by DougieFresh4U on 2009-04-04
> **zika said:**
> try to find a way of installing (I think it is dkms) fglrx-module in Your kernel. that is the difference between Your 2.6.28 and 2.6.29 ... as far as I know ...

p.s. did You try kernel boot option "nopat" i.e. "pat={off,on,force}" ... ? I would be grateful if someone could explain this option in detail ...

p.p.s. after some "research" I found that PAT is not switched on in 2.6.28. You could check for 2.6.29 with, for example *grep PAT /boot/config-2.6.29...* let it complete itself ...

> **t.alex said:**
> Some interesting reading ->[patch: vanilla fglrx for 2.6.29]("http://www.phoronix.com/forums/showthread.php?t=16173")

Thanks to both of you for replies.
I didn't think any one else was having problem as I posted last week about it and no response. I read the link given, but didn't really get any thing out of it. I am sure a fix will be along......sometime down the road.

---

### Post by DougieFresh4U on 2009-04-06
Does any body know any "sudo" magic to get 'fglrx' to work  with this kernel?
I have 'ATI Radeon HD 3200'.

---

### Post by Zorael on 2009-04-06
> **DougieFresh4U said:**
> Does any body know any "sudo" magic to get 'fglrx' to work  with this kernel?
[[IMG]http://imgs.xkcd.com/comics/sandwich.png[/IMG]](http://xkcd.com/149/)

Had to be linked. Carry on.

---

### Post by dirtylobster on 2009-04-07
lol

---

### Post by Kosimo on 2009-04-07
> **Zorael said:**
> [[IMG]http://imgs.xkcd.com/comics/sandwich.png[/IMG]](http://xkcd.com/149/)

Had to be linked. Carry on.

loooooooooooooooooooooooooooooooooooooooool !!!!!


ahahahahahahahhaahhahahahahahaahhahaahahhahaa :lolflag:

---

### Post by Hero of Time on 2009-04-07
That comic is ancient now. If you want something new, check this: [http://www.youtube.com/watch?v=lQOkMz3kiS0](http://www.youtube.com/watch?v=lQOkMz3kiS0) ;).

---

### Post by DougieFresh4U on 2009-04-07
My plea for help has created a 'monster'. :lolflag:
Unfortunatetely, aside from all jokes, I am still having the issue with getting 'fglrx' to work in .29 kernel

---

### Post by Hero of Time on 2009-04-07
Well, I'd love to get the fglrx on my laptop too, but as I would need to reboot, I wait until Jaunty is in RC or final stage. So have patience for a week or two, then I will do a major overhaul of my laptop with ATi and see how it all goes.

---

### Post by MacUntu on 2009-04-08
Has anyone tested 2.6.30-rc1 yet? I'm currently compiling...

---

### Post by DougieFresh4U on 2009-04-08
> **MacUntu said:**
> Has anyone tested 2.6.30-rc1 yet? I'm currently compiling...

Didn't even know there was .30
Any links for trying it out?

---

### Post by Kosimo on 2009-04-08
> **DougieFresh4U said:**
> Didn't even know there was .30
Any links for it?

[http://www.phoronix.com/scan.php?page=news_item&px=NzE5MA](http://www.phoronix.com/scan.php?page=news_item&px=NzE5MA)

---

### Post by ronacc on 2009-04-08
the timings about right for koala:p

---

### Post by plun on 2009-04-08
> **MacUntu said:**
> Has anyone tested 2.6.30-rc1 yet? I'm currently compiling...

Yup....):P

and Plymoth and GnomeShell.....;)


The nVidia driver must be patched or to change a file.
[http://www.nvnews.net/vbulletin/showpost.php?p=1977753&postcount=5](http://www.nvnews.net/vbulletin/showpost.php?p=1977753&postcount=5)

```
sudo sh NVIDIA-Linux-x86_64-185.19-pkg2.run --apply-patch patch-185.19-2.6.29git10.txt
```

:guitar:

---

### Post by DougieFresh4U on 2009-04-08
> **plun said:**
> Yup...

I'm 'hungry', where can I get it or is it not that easily available? ):P
And will 'fglrx' work with it, as it doesn't work in .29?

---

### Post by plun on 2009-04-08
> **DougieFresh4U said:**
> I'm 'hungry', where can I get it or is it not that easily available? ):P
And will 'fglrx' work with it, as it doesn't work in .29?

OK...

a so called vanilla kernel comes from kernel.org

[http://kernel.org/](http://kernel.org/)

This howto describes how a kernel can be built with Ubuntu

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)


fglrx....  maybe this works for both 2.6.29 and -30 ???

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

3rd alternative,  "Installing the restricted drivers manually "


;)

---

### Post by MacUntu on 2009-04-08
Only problem I encountered so far:

```
[   14.583204] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   14.583209] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   14.583332] iwl3945 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.583347] iwl3945 0000:05:00.0: setting latency timer to 64
[   14.642025] iwl3945 0000:05:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   14.642030] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   14.642201] iwl3945 0000:05:00.0: irq 30 for MSI/MSI-X
[   14.680128] iwl3945 0000:05:00.0: Failed to register hw (error -2)
[   14.680326] iwl3945 0000:05:00.0: PCI INT A disabled
[   14.680334] iwl3945: probe of 0000:05:00.0 failed with error -2

```

Manually loading worked fine, though.

---

### Post by DougieFresh4U on 2009-04-08
> **plun said:**
> OK...

a so called vanilla kernel comes from kernel.org

[http://kernel.org/](http://kernel.org/)

This howto describes how a kernel can be built with Ubuntu

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)


fglrx....  maybe this works for both 2.6.29 and -30 ???

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

3rd alternative,  "Installing the restricted drivers manually "


;)

Thank you plun, will work on it this afternoon  8-[
I guess asking for .deb or ppa was "out of the question"  :lolflag:

---

### Post by MacUntu on 2009-04-08
> **DougieFresh4U said:**
> Thank you plun, will work on it this afternoon  8-[
I guess asking for .deb or ppa was "out of the question"  :lolflag:

Maybe you'll find it here sooner or later: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by zevans on 2009-04-08
> **Kosimo said:**
> [http://www.phoronix.com/scan.php?page=news_item&px=NzE5MA](http://www.phoronix.com/scan.php?page=news_item&px=NzE5MA)

I'm running it now - still got random lockups on Intel with UXA enabled. Progress of sorts though: now I don't seem to get any error messages at all anywhere in /var/log when it happens!

---

### Post by zevans on 2009-04-08
Ahhhh getting somewhere - I turned on some of the debug stuff in the kernel. Now sure enough after a hang I can wait a couple of minutes and find out some info on which thread it is that's stuck...

```

Apr  8 17:55:11 vademecum kernel: [ 1560.772151] INFO: task events/0:9 blocked for more than 120 seconds.
Apr  8 17:55:11 vademecum kernel: [ 1560.772167] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Apr  8 17:55:11 vademecum kernel: [ 1560.772181] events/0      D 000000f9     0     9      2
Apr  8 17:55:11 vademecum kernel: [ 1560.772200]  f7875f40 00000046 4d529114 000000f9 c17097b0 f7875f04 c011f63b c0568d24
Apr  8 17:55:11 vademecum kernel: [ 1560.772229]  c056c7b0 f7836b70 f7836de8 c17097b0 00000000 0002f0a7 c04d9300 00000000
Apr  8 17:55:11 vademecum kernel: [ 1560.772256]  c056c7b0 f6ffa540 f7836b70 c1705d24 f7836de8 21efcc7d 000000f9 00000000
Apr  8 17:55:11 vademecum kernel: [ 1560.772283] Call Trace:
Apr  8 17:55:11 vademecum kernel: [ 1560.772311]  [<c011f63b>] ? set_next_entity+0x10f/0x16c
Apr  8 17:55:11 vademecum kernel: [ 1560.772335]  [<c03ad7cc>] __mutex_lock_slowpath+0xc0/0x124
Apr  8 17:55:11 vademecum kernel: [ 1560.772353]  [<c0132f39>] ? add_timer+0x11/0x18
Apr  8 17:55:11 vademecum kernel: [ 1560.772370]  [<c03ad65a>] mutex_lock+0x1a/0x28
Apr  8 17:55:11 vademecum kernel: [ 1560.772415]  [<f8cb6d66>] i915_gem_retire_work_handler+0x22/0x58 [i915]
Apr  8 17:55:11 vademecum kernel: [ 1560.772435]  [<c013933f>] worker_thread+0x13f/0x1f0
Apr  8 17:55:11 vademecum kernel: [ 1560.772474]  [<f8cb6d44>] ? i915_gem_retire_work_handler+0x0/0x58 [i915]
Apr  8 17:55:11 vademecum kernel: [ 1560.772493]  [<c013c910>] ? autoremove_wake_function+0x0/0x34
Apr  8 17:55:11 vademecum kernel: [ 1560.772511]  [<c0139200>] ? worker_thread+0x0/0x1f0
Apr  8 17:55:11 vademecum kernel: [ 1560.772527]  [<c013c5e3>] kthread+0x37/0x6c
Apr  8 17:55:11 vademecum kernel: [ 1560.772541]  [<c013c5ac>] ? kthread+0x0/0x6c
Apr  8 17:55:11 vademecum kernel: [ 1560.772559]  [<c0103bcf>] kernel_thread_helper+0x7/0x10

```

I'm off to launchpad to try and log a bug report or add to one that's already out there... I think this must be with the underlying i915 module given that it happens with EXA -and- UXA.

---

### Post by sgosnell on 2009-04-09
It's in the kernel.ubuntu.com repository now.  Just download the .deb and install...

---

### Post by zika on 2009-04-09
> **sgosnell said:**
> It's in the kernel.ubuntu.com repository now.  Just download the .deb and install...
I was not impressed with 2.6.29{,1} but this one (2.6.30.rc1) is promising in many respects. it is fast. what about some stuff (Apparmor and some /.../user...) not  getting OK in boot screen? with 29 I've got problems only with Apparmor ...

edit: 2.6.30.rc1:fast as a snake! without ext4... on ext3 ... I love it!

this is the first time that FF3.5 is faster than FF3.6 ... many other things are simply flying ...

it seems that2.6.30 does not support data=ordered on ext3?

for us with ATI cards (mine is RV635) this is encouraging (especially after repository freeze without any improvement for xor-xserver-video-ati (i.e. radeon)):> The Direct Rendering Manager (DRM) of Linux 2.6.30 will offer rudimentary support for the R6xx and R7xx GPUs used in the series 2000, 3000 and 4000 Radeon models. Together with suitable X.org graphics drivers, this enables 2D and video acceleration; access to these GPUs' 3D units is still in development.

---

### Post by loomsen on 2009-04-09
> **MacUntu said:**
> Only problem I encountered so far:

```
[   14.583204] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   14.583209] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   14.583332] iwl3945 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.583347] iwl3945 0000:05:00.0: setting latency timer to 64
[   14.642025] iwl3945 0000:05:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   14.642030] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   14.642201] iwl3945 0000:05:00.0: irq 30 for MSI/MSI-X
[   14.680128] iwl3945 0000:05:00.0: Failed to register hw (error -2)
[   14.680326] iwl3945 0000:05:00.0: PCI INT A disabled
[   14.680334] iwl3945: probe of 0000:05:00.0 failed with error -2

```

Manually loading worked fine, though.

I used to encounter such kind of problems in debian ever since, IWL agn 4965 here. 

Debian installs always caused complete lockups (not even SysRq Magic working) caused by the iwl4965 kernel module. Lately I wasn't even able to install debian because of that driver. 
I've never encountered any problems using the iwlwifi driver ubuntu ships with tho. (I wasn't even able to trace what exactly causes the lockups in debian installs)

---

### Post by sgosnell on 2009-04-09
.30rc1 won't boot on my EEE.  It hangs at the username input screen, and won't accept anything there, and won't do anything else, even after a long wait.  I'll wait for rc2, I guess.  .29 works well for me, and is very fast.  It probably depends a lot on your hardware.

---

### Post by dirtylobster on 2009-04-10
> **sgosnell said:**
> .30rc1 won't boot on my EEE.  It hangs at the username input screen, and won't accept anything there, and won't do anything else, even after a long wait.  I'll wait for rc2, I guess.  .29 works well for me, and is very fast.  It probably depends a lot on your hardware.

Same here on my Eee 1000H. And Apparmor FAILs at boot.

---

### Post by Zorael on 2009-04-10
30rc1 wouldn't even compile for me, but 29.1 seems stable enough (with KMS to boot, yay), so I'll just stick with that for the time being, methinks.

---

### Post by MikeDK on 2009-04-13
> **foxmulder881 said:**
> I'm currently working on compiling it now. Reason: I want to give Btrfs a test out and see how it competes with Ext4.

please report back how well it works with ext4.

interesting to know how it goes with the new filesystem

Kind Regards MikeDK

---

### Post by sgosnell on 2009-04-13
Zorael, why are you compiling it?  Are there special modules you need?

---

### Post by Zorael on 2009-04-13
> **sgosnell said:**
> Zorael, why are you compiling it?  Are there special modules you need?
Enabling kernel modesetting per default, and applying a patch so that dithering works properly for my video chipset.

---

### Post by sgosnell on 2009-04-13
OK, just wondering.  Fortunately I've seen no need to compile it, the .deb works fine on my box.

---

### Post by Kosimo on 2009-04-15
Linux 2.6.30-rc2 Kernel Released 

From Phoronix.com

> Last week Linux 2.6.30-rc1 was released, but this afternoon Linus Torvalds has pushed out the second release candidate for the Linux 2.6.30 kernel series.

The second release candidate introduces a new architecture (called microblaze), an input layer update, a new
Intel virtual networking driver, firmware loading updates, and Intel graphics driver updates. The Microblaze processor architecture is developed by Xilinx for some of their FPGA products and is a 32-bit Harvard RISC architecture.

The Linux 2.6.30-rc2 kernel release announcement can be read at LKML.org.

---

### Post by plun on 2009-04-15
> **Kosimo said:**
> Linux 2.6.30-rc2 Kernel Released 


Yup....

This kernel gave me kerneloops and a crashed gnome-panel.
Just to killall gnome-panels and everything seems to work
after that. (1 hours running)

The nvidia driver must still be a patched one, "unknown owner" error

---

### Post by Kosimo on 2009-04-15
> **plun said:**
> Yup....

This kernel gave me kerneloops and a crashed gnome-panel.
Just to killall gnome-panels and everything seems to work
after that. (1 hours running)

The nvidia driver must still be a patched one, "unknown owner" error

Really?
Doesn't looks good then...  How about performance? Any improvement?

---

### Post by plun on 2009-04-15
> **Kosimo said:**
> Really?
Doesn't looks good then...  How about performance? Any improvement?

Its "snappy" as always with a new kernel....;)

I send my Kerneloops report and haven't looked deeper what causes it.
Works just fine after fixing the gnome-panel.

---

### Post by zika on 2009-04-15
2.6.30-rc2 is in mainline. :)

---

### Post by DougieFresh4U on 2009-04-15
I just put .30rc2 on my machine and I was actually able to boot as I can not get .30rc1 to boot.  It seems pretty quick and stable so far. I do not get the 'loading bar' but 'login' screen pops up after a few sec's and I can log in.
Now, I am afraid to attempt installing the 'fglrx' as I have had no luck with .29 installing it and I think that is what 'borked' .30rc1.
Can any one guide me on that?

---

### Post by TheExplorer on 2009-04-16
> **plun said:**
> The nvidia driver must still be a patched one, "unknown owner" error

Try this one: [http://www.nvnews.net/vbulletin/showthread.php?t=131597](http://www.nvnews.net/vbulletin/showthread.php?t=131597)
;)

---

### Post by plun on 2009-04-16
> **TheExplorer said:**
> Try this one: [http://www.nvnews.net/vbulletin/showthread.php?t=131597](http://www.nvnews.net/vbulletin/showthread.php?t=131597)
;)

This is better....;)

ver 180.50 is out

[http://www.nvnews.net/vbulletin/showthread.php?p=1984723](http://www.nvnews.net/vbulletin/showthread.php?p=1984723)

No need for a patch !

---

### Post by Kosimo on 2009-04-16
> **plun said:**
> This is better....;)

ver 180.50 is out

[http://www.nvnews.net/vbulletin/showthread.php?p=1984723](http://www.nvnews.net/vbulletin/showthread.php?p=1984723)

No need for a patch !

Cool, gotta try with 2.6.30rc2 !

---

### Post by Hero of Time on 2009-04-19
Those who want the ATi fglrx driver, it's now as early look for Jaunty. Since that driver didn't work with 2.6.28 either, it might actually work on 2.6.29. One can only hope. I will install Jaunty and 2.6.29.1 on my laptop next week, when Jaunty is final.

Edit:
Only downside, they removed quite a lot of cards from the supported list, including my X1400 Mobility Radeon. Curse them, that card isn't that old! ](*,)
Edit2:
Reading some more, others have tried it on 2.6.29, didn't work. So screw ATi, no support or whatsoever for cards older than 2 years and recent kernels.

---

### Post by Kosimo on 2009-04-19
> **Hero of Time said:**
> Those who want the ATi fglrx driver, it's now as early look for Jaunty. Since that driver didn't work with 2.6.28 either, it might actually work on 2.6.29. One can only hope. I will install Jaunty and 2.6.29.1 on my laptop next week, when Jaunty is final.

Edit:
Only downside, they removed quite a lot of cards from the supported list, including my X1400 Mobility Radeon. Curse them, that card isn't that old! ](*,)
Edit2:
Reading some more, others have tried it on 2.6.29, didn't work. So screw ATi, no support or whatsoever for cards older than 2 years and recent kernels.



nVidia drivers have perfect support for x.org 1.6 since more than two months, and also the newest 2.6.30 kernel with almost all cards at least 4 years old. Definitely when talking about drivers support, nVidia is years ahead, and I won't ever consider buying AMD cards.

---

### Post by plun on 2009-04-19
nVidia driver ver 180.51 is also out now.

[http://www.nvnews.net/vbulletin/showthread.php?p=1985816](http://www.nvnews.net/vbulletin/showthread.php?p=1985816)

---

### Post by rudenko_ruslan on 2009-04-22
Another RC... (2.6.30-rc3)
[QUOTE=Linus Torvalds]Another week, another -rc.

The patch is even bigger, since we ended up doing the renaming of the m32r 
header files (last architecture to use the old include/asm-xyz format) and 
the caiaq sound driver also renamed it's files. And this time I actually 
checked that my patches are old-style patches without git rename 
information, so they should all apply properly on the first try!

But apart from that, there shouldn't be a lot of huge excitement. Things 
do seem to be calming down, knock wood.

The diffstat really shows lots of small one-liners and two-liners, 
although there are areas that are getting bigger patches (ignoring the 
bulky but uninteresting arm defconfig updates): some x86 updates, some 
block IO scheduling fixes, splice cleanups and fixes, and a number of 
driver changes (sound, networking, staging, usb).

CIFS and btrfs updates also show up pretty clearly.

And hopefully all the embarrassing and trivial regressions get fixed. 

Which leaves us the more interesting ones, and making us ask people to 
test more, of course.[/QUOTE]
[http://lkml.org/lkml/2009/4/21/596](http://lkml.org/lkml/2009/4/21/596)

Maybe after some time, this RC will be there - [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by sgosnell on 2009-04-22
Rc3 is out, and it seems to work on my machine.  Rc1 & rc2 didn't boot.  The boot time was much longer than with .29 for some reason.

---

