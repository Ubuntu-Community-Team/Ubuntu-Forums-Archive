---
title: "Dependencies of plymouth"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ShadowDragon on 2010-04-07
I'm reading up on the new stuff in Lucid and I can't figure out the rationale behind the [dependencies of plymouth](http://packages.ubuntu.com/lucid/x11/plymouth).

> dep: libdrm-intel1 (>= 2.4.9)
    Userspace interface to intel-specific kernel DRM services -- runtime 
dep: libdrm-nouveau1 (>= 2.4.11-1ubuntu1~)
    Userspace interface to nouveau-specific kernel DRM services -- runtime 
dep: libdrm-radeon1 (>= 2.4.17)
    Userspace interface to radeon-specific kernel DRM services -- runtime

Why is it obliged to have all three libraries?

I for instance, only have an integrated Nvidia-card in my system, so why would I need the other libraries for? Finding other use-cases is trivial.

---

### Post by IanW on 2010-04-07
I guess Plymouth depends on all 3 of those because it has no idea which it will need at install time.
The alternative would require 3 different packages on the install disk:- plymouth-intel plymouth-nouveau plymouth-radeon.

---

### Post by ShadowDragon on 2010-04-07
Can't it be solved by using a virtual package? Plymouth just depends on that virtual package and each of the libdrm's provides that virtual package. So you only need the install the libs you need, correct?
```
                                       /-- libdrm-intel1
Plymouth ---> libdrm-specific-virtual <--- libdrm-nouveau1
                                       \-- libdrm-radeon1
```

---

### Post by djchandler on 2010-04-07
> **ShadowDragon said:**
> I'm reading up on the new stuff in Lucid and I can't figure out the rationale behind the [dependencies of plymouth]("http://packages.ubuntu.com/lucid/x11/plymouth").



Why is it obliged to have all three libraries?

I for instance, only have an integrated Nvidia-card in my system, so why would I need the other libraries for? Finding other use-cases is trivial.

Those are basic video drivers integrated into the kernel. Xorg drivers are on your system too in the event you need or want to change your video card. Changing drivers from radeon to fglrx really fouls things up on my laptop. There's more stuff going on that that. Whatever you do, don't try removing Plymouth for the time being. It triggers a removal of way more stuff than it should be. The critical dependency seems to be that mountall now wants to see what plymouth is doing.

See this thread, especially [this post from Mr. Picklesworth]("http://ubuntuforums.org/showpost.php?p=9087062&postcount=629"). He explains how to reduce any negative impact Plymouth has on your system at the current time.

---

### Post by ShadowDragon on 2010-04-08
> **djchandler said:**
> The critical dependency seems to be that mountall now wants to see what plymouth is doing.
Making mountall (a mounter) hard-dependent on plymouth (something that has to do with graphics)? Seriously? Bad smell, anyone?

Ah, found the source of the smell...
```
mountall  reads  fstab(5)  and calls fsck(8), mount(8) and swapon(8) in
       the correct order to mount filesystems once the underlying devices have
       been created by udevd(8)

       [b]This is a temporary tool until init(8) itself gains the necessary flex&#8208;
       ibility to perform this processing[/b]; you should not rely on  its  behav&#8208;
       iour.
```
Both the same author.
Come on init! We all depend on you!

---

### Post by utUtu on 2010-04-08
> **ShadowDragon said:**
> Can't it be solved by using a virtual package? Plymouth just depends on that virtual package and each of the libdrm's provides that virtual package. So you only need the install the libs you need, correct?
```
                                       /-- libdrm-intel1
Plymouth ---> libdrm-specific-virtual <--- libdrm-nouveau1
                                       \-- libdrm-radeon1
```

I guess the packager is lazy?  The depends should have been *intel  or *nvidia  or *radeon.  I could rebuild it but the best for me is get rid of *plymouth alltogether.

---

### Post by glasen on 2010-04-08
All of the three packages together are only about 1MB in disk size. They don't use any RAM when the system is booted, so where is the problem?

---

### Post by cariboo on 2010-04-08
What about all the other unneeded drivers installed, by my count there is at least 22 drivers installed that I don't need. :)

---

### Post by xebian on 2010-04-08
> **glasen said:**
> All of the three packages together are only about 1MB in disk size. They don't use any RAM when the system is booted, so where is the problem?

The OP's not complaining of disk space nor RAM usage, is (s)he? 

Why even bother make 3 separate libdrm* when all are required even though you don't have the other video card? 3x more work.

---

### Post by xebian on 2010-04-08
> **IanW said:**
> I guess Plymouth depends on all 3 of those because it has no idea which it will need at install time.
The alternative would require 3 different packages on the install disk:- plymouth-intel plymouth-nouveau plymouth-radeon.

Or just 1 libdrm.

---

### Post by MacUntu on 2010-04-08
> **cariboo907 said:**
> What about all the other unneeded drivers installed, by my count there is at least 22 drivers installed that I don't need. :)

If you're talking about video drivers: you'll only uninstall xserver-xorg-video-all - not the whole system like with libdrm-*. :D

---

### Post by seeker5528 on 2010-04-09
> **ShadowDragon said:**
> Can't it be solved by using a virtual package? Plymouth just depends on that virtual package and each of the libdrm's provides that virtual package. So you only need the install the libs you need, correct?
```
                                       /-- libdrm-intel1
Plymouth ---> libdrm-specific-virtual <--- libdrm-nouveau1
                                       \-- libdrm-radeon1
```



I think what you meant was have a non-hardware specific virtual package that depends on the other three, then have plymouth depend on that virtual package or blah or blah.....

```
librdm-virutal-package | libdrm-virtuallibdrm-intel1 | libdrm-nouveau1 | libdrm-radeon1
```

So those who don't know or don't care would most likely end up with all of them and those who don't have 1 MB to spare can get rid of all but one of them.

But for 1 MB it seems like wasted effort to me.

Later, Seeker

---

### Post by djchandler on 2010-04-10
> **cariboo907 said:**
> What about all the other unneeded drivers installed, by my count there is at least 22 drivers installed that I don't need. :)

And that's not a bad thing. Because of that, it's possible to do a motherboard swap without a fresh install. Ideally you would want a fresh install with a new set of hardware eventually, but in the event of a hardware failure, such as blown capacitors on a motherboard, recovering your data is a snap. And the savings in time spent to recover that data could be huge.

This has actually happened to me, so I know it can be done, even with entirely different MB chipsets and graphics chips. The only limitation is if the original install is 64-bit, a different CPU must support 64-bit too. And that's becoming less and less of an issue.

Yes, I know I am supposed to back up my data. How many of us do it in practice on a regular basis? I find myself copying important data to a networked computer at the time of its creation all the time. But do I actually do scheduled back-ups at home? Not very often.

I like that basic drivers are available by default. Over customizing your installation takes options out of your hands. For very little disk space, near zero RAM overhead and near zero increase in boot time, what is there to complain about? To me the possible benefit and elimination of some risk far outweighs any benefit, especially a benefit that would hardly be perceivable.

---

### Post by cariboo on 2010-04-10
@djchandler

I fully agree  that it is a good idea to have all the video drivers included in the basic install, it's just that so may people seem to focus on one or two things, and don't even realize what else is installed on their system.

---

### Post by MacUntu on 2010-04-10
The question was why plymouth depends on all three, not why all three get installed - different topic. :P

It shouldn't depend on the possible savings whether or not dependencies are kept simple and clean. Either there's a reason for the current state or it should be changed.

---

### Post by Longinus00 on 2010-04-10
If you guys are so worried about having extra cruft on your system, just download the source for plymouth and make a new package with different dependencies. Problem solved!

---

### Post by seeker5528 on 2010-04-10
> **MacUntu said:**
> The question was why plymouth depends on all three, not why all three get installed - different topic. :P

It shouldn't depend on the possible savings whether or not dependencies are kept simple and clean. Either there's a reason for the current state or it should be changed.

Reasons to do it might be....

They factor in to the boot experience.
They are small.
They cover the hardware the majority of people have.
The most reliable way to make sure people have the one they need is to depend on all of them.

Reasons not to do the metapackage thing where you depend on 'metapackage or package or package'.....

Messing around with meta-packages creates extra (unnecessary in this case, IMHO) potential for human error on the packaging end of things.

Extra potential for strange things to happen with dependency calculations during upgrades, possibly leading to the package you actually need for your hardware to be removed, if any one of the packages could satisfy the dependency.

Extra potential for user error leading to the removal of the package they actually need for their hardware.

Possible reason for not having plymouth depend on libdrm-driver and having all the libdrmX-XXX packages set to provide libdrm-driver.

If plymouth depends on something packages provide instead of the actual packages, then again you have additional complexity with dependency calculations which could be an issue for some people during upgrades or if something gets goes wonky while updating or you purge all the libdrm packages for troubleshooting and have no libdrm packages installed, then 'apt-get -f install' won't be able to fix it unless you specify a package to install and even if you specify a package then it still might fail in situations where it would succeed by depending on all 3.

And again you may end up with a situation where a person got the dependency satisfied, but not with the package they actually need for their hardware.

Later, Seeker

---

### Post by ShadowDragon on 2010-04-11
> **utUtu said:**
> [...] but the best for me is get rid of *plymouth alltogether.
Yeah, me too. I do have systems where I absolutely don't need something graphical during booting. But removing plymouth has a huge cascading effect. But that's another discussion. ;)

> **seeker5528 said:**
> I think what you meant was have a non-hardware specific virtual package that depends on the other three, then have plymouth depend on that virtual package or blah or blah.....

```
librdm-virutal-package | libdrm-virtuallibdrm-intel1 | libdrm-nouveau1 | libdrm-radeon1
```[...]
Yeah, something like that, sorta. I had issues getting the though -> text. ;)

> **seeker5528 said:**
> [...]So those who don't know or don't care would most likely end up with all of them and those who don't have 1 MB to spare can get rid of all but one of them.[...]
Indeed, no change for the people who don't care, but giving the chose / possibility / freedom to the people who don't want the unnecessarily packages for their situation.

> **glasen said:**
> All of the three packages together are only about 1MB in disk size. They don't use any RAM when the system is booted, so where is the problem?
> **xebian said:**
> The OP's not complaining of disk space nor RAM usage, is (s)he? [...]
> **seeker5528 said:**
> 
[...] But for 1 MB it seems like wasted effort to me.

> **Longinus00 said:**
> If you guys are so worried about having extra cruft on your system, [...]
I must admit, I'm sort of a tweaker, and I like to minimize / optimize my system. But putting that all aside, on this particular topic, I'm just interested in the rationale behind choosing dependencies, the line of thought, not resource usage, but it can of course be part of the rationale, I don't know. That's what I'm asking. Why this approach of choosing dependencies? :)

> **cariboo907 said:**
> What about all the other unneeded drivers installed, by my count there is at least 22 drivers installed that I don't need. :)
I have the same question, but I though it would be better to start with 1 application, and a quite popular, to get the discussion started and to see if the responses / argumentations could be projected on the other drivers as well.

> **MacUntu said:**
> If you're talking about video drivers: you'll only uninstall xserver-xorg-video-all - not the whole system like with libdrm-*. :D
Hmm, xserver-xorg-video-all, interesting point.
```
$ aptitude show xserver-xorg-video-all
[...]
Description: the X.Org X server -- output driver metapackage
 This package depends on the full suite of output drivers for the X.Org X server
 (Xorg).  It does not provide any drivers itself, and may be removed if you wish
 to only have certain drivers installed.

$ aptitude why xserver-xorg-video-all
i   xserver-xorg Depends xserver-xorg-video-all | xserver-xorg-video-5

$ aptitude show xserver-xorg-video-5
No current or candidate version found for xserver-xorg-video-5
Package: xserver-xorg-video-5
State: not a real package
Provided by: nvidia-glx-173, nvidia-glx-185, nvidia-glx-96,
             virtualbox-ose-guest-x11, xserver-xorg-video-apm,
             xserver-xorg-video-ark, xserver-xorg-video-chips,
             xserver-xorg-video-cirrus, xserver-xorg-video-dummy,
             xserver-xorg-video-fbdev, xserver-xorg-video-glint,
             xserver-xorg-video-i128, xserver-xorg-video-i740,
             xserver-xorg-video-intel, xserver-xorg-video-ivtv,
             xserver-xorg-video-mach64, xserver-xorg-video-mga,
             xserver-xorg-video-neomagic, xserver-xorg-video-nouveau,
             xserver-xorg-video-nv, xserver-xorg-video-openchrome,
             xserver-xorg-video-r128, xserver-xorg-video-radeon,
             xserver-xorg-video-radeonhd, xserver-xorg-video-rendition,
             xserver-xorg-video-s3, xserver-xorg-video-s3virge,
             xserver-xorg-video-savage, xserver-xorg-video-siliconmotion,
             xserver-xorg-video-sis, xserver-xorg-video-sisusb,
             xserver-xorg-video-tdfx, xserver-xorg-video-trident,
             xserver-xorg-video-tseng, xserver-xorg-video-v4l,
             xserver-xorg-video-vesa, xserver-xorg-video-vmware,
             xserver-xorg-video-voodoo

```
I like that idea. xserver-xorg depends on either a meta-package to provide all drivers or one or more drivers you choose. It's elegant, not hard to understand and it satisfies all type of users: the users who want to be sure they have everything or don't know much about it, check; the users who want to be able to have a configuration that still works without the need to make adjustments when replacing / changing the hardware of the system, check; the users who only want what they need, check; ... Hmm, I starting to really like that idea. :D
Why isn't this done for plymouth? Is there a something fundamental that makes plymouth different, which makes the above idea non-applicable for plymouth?

> **djchandler said:**
> And that's not a bad thing. Because of that, it's possible to do a motherboard swap without a fresh install. Ideally you would want a fresh install with a new set of hardware eventually, but in the event of a hardware failure, such as blown capacitors on a motherboard, recovering your data is a snap. And the savings in time spent to recover that data could be huge.

[...]

I like that basic drivers are available by default. Over customizing your installation takes options out of your hands. For very little disk space, near zero RAM overhead and near zero increase in boot time, what is there to complain about? To me the possible benefit and elimination of some risk far outweighs any benefit, especially a benefit that would hardly be perceivable.
I can fully understand your use-case and on some systems I would also like to be able to still do that, but on other systems I want to customize it.
If we would change the dependencies like how it's done above in xserver-xorg, your use-case is still possible isn't it? And others can customize when they want, so nobody looses, right?

> **cariboo907 said:**
> @djchandler
I fully agree  that it is a good idea to have all the video drivers included in the basic install, it's just that so may people seem to focus on one or two things, and don't even realize what else is installed on their system.
Me too, but it shouldn't be at the dispense of other use-case, should it?

> **MacUntu said:**
> [...] Either there's a reason for the current state or it should be changed.
Exactly.

> **seeker5528 said:**
> Reasons to do it might be....
[Post with plausible argumentations, if you want to read it just look for the start of this post and scroll just a little bit up]

What's your opinion on the xserver-xorg idea?

---

