---
title: "The Plymouth Thread"
date: 2009-04-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Slug71 on 2009-04-27
Another big feature im looking forward to. Hopefully we will see it soon.

---

### Post by Triggerhapp on 2009-04-28
Seconded!

---

### Post by steeleyuk on 2009-04-28
And another one. The look of Usplash in Jaunty is a bit of a fail.

---

### Post by Neon Lights on 2009-04-28
+1
I'm really excited about Plymouth. (:  Hopefully (haha, wayy big hopes) nVidia will get KMS in some form or another too.

---

### Post by ghindo on 2009-04-28
> **steeleyuk said:**
> And another one. The look of Usplash in Jaunty is a bit of a fail.Really?  I much preferred it to the previous Usplash themes.

Nonetheless, I'm really looking forward to Plymouth :)

---

### Post by kpkeerthi on 2009-04-28
+1 to Plymouth.

Or atleast something Plymounth-like with better, smoother transition from usplash to desktop and vice versa. :)

---

### Post by ilovebrownies on 2009-04-28
What's the best way to get this suggestion through? A poll on these forums, or Brainstorm?

---

### Post by plun on 2009-04-28
Just some facts from Jaunty......

Plymouth works just fine also with nVidia, the kernel must just
be correct configured.


Jaunty thread:
[http://ubuntuforums.org/showthread.php?t=1083584](http://ubuntuforums.org/showthread.php?t=1083584)


Plymouth ppa
[https://launchpad.net/~plymouth-dev/+archive/ppa](https://launchpad.net/~plymouth-dev/+archive/ppa)


Important settings/commands

- using vga=795 as setting.

vga=ask can also be used


Set solar as plugin:

```
sudo plymouth-set-default-plugin solar
```

Configure grub

```
sudo dpkg-reconfigure linux-image-`uname -r`
```



Credits, several users involved in Jaunty, noone forgotten .....:)


Kernel setting for nVidia and kernel 2.6.30

```
# Frame buffer hardware drivers
#
CONFIG_FB_CIRRUS=m
CONFIG_FB_PM2=m
CONFIG_FB_PM2_FIFO_DISCONNECT=y
CONFIG_FB_CYBER2000=m
CONFIG_FB_ARC=m
CONFIG_FB_ASILIANT=y
CONFIG_FB_IMSTT=y
CONFIG_FB_VGA16=m
[B]CONFIG_FB_UVESA=y
CONFIG_FB_VESA=y[/B]
CONFIG_FB_EFI=y
CONFIG_FB_N411=m
CONFIG_FB_HGA=m
# CONFIG_FB_HGA_ACCEL is not set
```

---

### Post by SunnyRabbiera on 2009-04-28
Plymouth sucks for intel cards though...

---

### Post by steeleyuk on 2009-04-28
> **ghindo said:**
> Really?  I much preferred it to the previous Usplash themes.

For whatever reason, the 'Ubuntu' text on mine is very blocky... It doesn't bother me personally, due to the boot speed of Jaunty its only on screen for about 10 seconds.

---

### Post by MacUntu on 2009-04-28
My boot time is too short for the ultimate Plymouth experience. :(:lolflag:

---

### Post by gnomeuser on 2009-04-28
> **Neon Lights said:**
> +1
I'm really excited about Plymouth. (:  Hopefully (haha, wayy big hopes) nVidia will get KMS in some form or another too.

The proprietary nvidia will not get KMS, adding that support would make it fall under the GPLv2's definition of derivative work and must therefore be released on the same license. They would like to add such support but do not want to release source code.

The good news is that the nouveau driver does have KMS, for GeForce8 series cards and support is being expanded. You should be able to rely on it out of the box in Koala for these cards (and hopefully more). 

For others unsupported cards, plymouth has an ascii fallback which admittedly isn't that pretty but it works and there is an unsupported VESA fallback which will give you the roughly same visuals as KMS but with other technical drawbacks.

---

### Post by ronacc on 2009-04-28
since I generaly run with quiet and splash removed from my bootline plymouth dosen't hold much attration for me .

---

### Post by gnomeuser on 2009-04-28
> **MacUntu said:**
> My boot time is too short for the ultimate Plymouth experience. :(:lolflag:

Moblin uses plymouth, not for the graphical splash since they don't need one but for other reasons. Even if we make the machine boot in less than 20 secs there are reasons to investigate plymouth

---

### Post by plun on 2009-04-28
> **MacUntu said:**
> My boot time is too short for the ultimate Plymouth experience. :(:lolflag:

Well, eyecandy for a few seconds....:popcorn:

I am still using autocrossers gdm-stylish bootscreen.

Works perfect with nVidia.....  but with blue "lava"....:lolflag:

---

### Post by MacUntu on 2009-04-28
> **gnomeuser said:**
> Moblin uses plymouth, not for the graphical splash since they don't need one but for other reasons. Even if we make the machine boot in less than 20 secs there are reasons to investigate plymouth

Don't make it a mystery - tell us more. ;)

---

### Post by go7Ul1ai on 2009-04-28
Can Intel chipsets run Plymouth?

---

### Post by mdurham on 2009-04-28
I'd like it to boot so fast that there would be no time to display any flash!

---

### Post by VMC on 2009-04-28
> **SunnyRabbiera said:**
> Plymouth sucks for intel cards though...

Why so? Which Intel cards? I have an integrated Intel chip, 82865G. There are several fixes. I used the rollback method. Now it appears there's even a better fix at [ppa]("https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/").

---

### Post by ghindo on 2009-04-28
> **gnomeuser said:**
> Moblin uses plymouth, not for the graphical splash since they don't need one but for other reasons. Even if we make the machine boot in less than 20 secs there are reasons to investigate plymouth...go on. :)

---

### Post by gnomeuser on 2009-04-28
> **ghindo said:**
> ...go on. :)

Very well, since you are unwilling to research on your own.

They use plymouth because it enables KMS during bootup with shaves some off the total boot time. This is because the time it takes of X to configure itself and start up is cut.

So yes, plymouth itself can be part of the equations that makes for a magically short boot. It is not just "pointless bling".

Additonally even for setups that do not benefit from the boot speedup, but also doesn't want the pretty graphics because those deployments favor a quick auto login experience via KMS you gain a flicker free start up.

---

### Post by Gina on 2009-04-28
Thank you for that :)  A shorter boot time without any flicker would certainly be good :)

---

### Post by ghindo on 2009-04-28
> **gnomeuser said:**
> Very well, since you are unwilling to research on your own.Interacting with the community seems like a pretty good way to research to me. :)

---

### Post by gnomeuser on 2009-04-28
> **ghindo said:**
> Interacting with the community seems like a pretty good way to research to me. :)

Rather it seems like making me do the work, bestove my wisdom upon you followed by you trembling fearful in the shadow of my superiorly informed mind. :)

So why not skip to step 3 directly and just accept my informed opinion as fact from now on. It's not like people actually listen when I give references and spend hours forming an informed posting on this forums. As an experiment I have started just asserting my opinion and when people ask me to back it up answer without references to the best of my knowledge. One reason is that I read a lot of blogs, mailings lists and so on, I can't really remember where I suck up every little detail, let alone come up with the exact reference on command. The information is out there, and everyone can take me up on my word - I can and have apologized for being wrong in the past. You are most welcome to keep me and others honest, this is why I encourage independent research.

In case you think you didn't just accept my opinion without questioning, look at the fact that not once did I give any references you could check and you did not complain.

However in the interest of truthfulness, here is plymouth in moblin source tree. They do indeed use a modified version to allow a KMS enabled boot up. KMS does shave off a little time for them enabling moblin to come closer to the ambitious 2 sec boot goal (as stated amongst other places in Arjans presentation of Moblin).

[http://repo.moblin.org/moblin/development/core/source/plymouth-lite-0.6.0-5.2.moblin2.src.rpm](http://repo.moblin.org/moblin/development/core/source/plymouth-lite-0.6.0-5.2.moblin2.src.rpm)

---

### Post by Neon Lights on 2009-04-28
> **gnomeuser said:**
> The proprietary nvidia will not get KMS, adding that support would make it fall under the GPLv2's definition of derivative work and must therefore be released on the same license. They would like to add such support but do not want to release source code.

The good news is that the nouveau driver does have KMS, for GeForce8 series cards and support is being expanded. You should be able to rely on it out of the box in Koala for these cards (and hopefully more). 

For others unsupported cards, plymouth has an ascii fallback which admittedly isn't that pretty but it works and there is an unsupported VESA fallback which will give you the roughly same visuals as KMS but with other technical drawbacks.
I figured something like that would be holding back the proprietary one. We can always hope for the absolute miracle that they'll open-source though, eh? Hahahahaha.

and that is good news, I have a GeForce8 series card! XD haha. Thanks for the info.

---

### Post by gnomeuser on 2009-04-28
> **Neon Lights said:**
> I figured something like that would be holding back the proprietary one. We can always hope for the absolute miracle that they'll open-source though, eh? Hahahahaha.

and that is good news, I have a GeForce8 series card! XD haha. Thanks for the info.

They can't open source it, or at least it would take a few thousand man years of lawyer time. Not all of the IP (let it be noted I use the term with an air of disgust) in the drivers belongs to nvidia in such a way that they would be able to open source it. 

I think instead we will see the same thing that happened with the forcedeth nvidia ethernet driver, when it reached maturity nvidia started contributing to it instead of open sourcing their own work. Most likely because that codebase was cleanly implemented and thus everyone back was clear from roaming patent troll lawyers. I think we might see the same with nouveau, at best they might continue to offer things like specific codec acceleration proprietary somehow since that remains a legal minefield. 

Nouveau is doing very well, Fedora recently held a test day and the response was overwhelming. Most cards seemed to work really well for the scope. 3D support will still take some time but it is getting there.

I am very positive about the whole thing, work is progressing very well.

---

### Post by lamalex on 2009-04-28
> **ronacc said:**
> since I generaly run with quiet and splash removed from my bootline plymouth dosen't hold much attration for me .

These are usplash options, so they actually dont have much to do with plymouth, iirc.

---

### Post by ghindo on 2009-04-29
> **gnomeuser said:**
> Rather it seems like making me do the work, bestove my wisdom upon you followed by you trembling fearful in the shadow of my superiorly informed mind. :)

So why not skip to step 3 directly and just accept my informed opinion as fact from now on. It's not like people actually listen when I give references and spend hours forming an informed posting on this forums. As an experiment I have started just asserting my opinion and when people ask me to back it up answer without references to the best of my knowledge. One reason is that I read a lot of blogs, mailings lists and so on, I can't really remember where I suck up every little detail, let alone come up with the exact reference on command. The information is out there, and everyone can take me up on my word - I can and have apologized for being wrong in the past. You are most welcome to keep me and others honest, this is why I encourage independent research.

In case you think you didn't just accept my opinion without questioning, look at the fact that not once did I give any references you could check and you did not complain.You generally seem to be a well-informed fellow, so I assume that I can trust what you post.  I also assume that other well-informed members will correct any misinformation posted on the forums

I always approach information online with a bit of skepticism, but if I had to independently research all the claims I found on the internet, I wouldn't have much free time :lolflag:

Anyway, thank you for elaborating.  Sorry for causing you any trouble.

---

### Post by loomsen on 2009-04-29
> **gnomeuser said:**
> Nouveau is doing very well, Fedora recently held a test day and the response was overwhelming. Most cards seemed to work really well for the scope. 3D support will still take some time but it is getting there.

Yup, worked for me booting a live CD of F11-alpha a couple of days ago, 8600M GT here.

---

### Post by Tom Mann on 2009-04-29
Probably sound like an idiot now... But I like the text mode Plymouth! It's minimal and a serious non-waste of resources in getting from A to B when you want to do it quickly :KS

---

### Post by plun on 2009-04-29
> **gnomeuser said:**
> Very well, since you are unwilling to research on your own.

They use plymouth because it enables KMS during bootup with shaves some off the total boot time. This is because the time it takes of X to configure itself and start up is cut.

So yes, plymouth itself can be part of the equations that makes for a magically short boot. It is not just "pointless bling".

Additonally even for setups that do not benefit from the boot speedup, but also doesn't want the pretty graphics because those deployments favor a quick auto login experience via KMS you gain a flicker free start up.

Well.. my research ends up with a recall about an Phoronix article 

[http://www.phoronix.com/scan.php?page=news_item&px=NzEzNw](http://www.phoronix.com/scan.php?page=news_item&px=NzEzNw)

**Why Is Moblin's X.Org Stack Faster Than In Ubuntu?**


Scott James Remnant was investigating this diff between Moblin and a Ubuntu box.

I have not seen any conlusion about this X-delay. :confused:

---

### Post by gnomeuser on 2009-04-29
> **plun said:**
> Well.. my research ends up with a recall about an Phoronix article 

[http://www.phoronix.com/scan.php?page=news_item&px=NzEzNw](http://www.phoronix.com/scan.php?page=news_item&px=NzEzNw)

**Why Is Moblin's X.Org Stack Faster Than In Ubuntu?**


Scott James Remnant was investigating this diff between Moblin and a Ubuntu box.

I have not seen any conlusion about this X-delay. :confused:

find Arjans Linux plumbers talk slides

---

### Post by Nullack on 2009-04-29
Theres lots of things needing to be done before I see this as an NVIDIA user:

KMS patches in the kernel
Installing Novuea driver
Fixing Novuea driver so I can realistically use it for my desktop needs (this will take years probably at the current glacial dev pace)

---

### Post by MacUntu on 2009-04-30
I'd rather have good 3D performance and working standby/resume than KMS and Plymouth. Sad, but I'm not altruistic on this one.

---

### Post by Kevbert on 2009-04-30
Can I run Plymouth on an old ATI Radeon 9000 card ?

---

### Post by coolen on 2009-04-30
Another Nvidia user here staring dreamily at the stars with tears in his eyes, hoping for some brave knight to come along and rescue him from the tyranny of proprietary drivers.

I like the idea that Nvidia may start contributing to Nouveau. I'd love a full-featured open source experience.

I've been hearing much more about Nouveau lately, and they have one major distro using their driver by default. All seem like good signs for the future of this project.

Also, regarding Usplash in Jaunty, I'm not fond of the theme. The text does seem kind of blocky, and the new progress bar fails. I get that they were going for a more professional look, but it's kind of at odds with the rest of the system look and feel (except the GDM theme) and honestly doesn't seem that professional to me anyway.

---

### Post by gnomeuser on 2009-04-30
> **Nullack said:**
> Theres lots of things needing to be done before I see this as an NVIDIA user:

KMS patches in the kernel
Installing Novuea driver
Fixing Novuea driver so I can realistically use it for my desktop needs (this will take years probably at the current glacial dev pace)

I have no idea where you get the idea that nouveau development is slow, clearly you are not following the same project I am.

---

### Post by loomsen on 2009-04-30
Currently it really isn't slow at all, I'm following too. But I still think they won't manage to get 3D/DRI working in the next couple of months. Mind, the nvidia driver is a running binary creating the interface to control and ineract with your kernel. That's the reason why it can't really be built into the kernel...

But hopefully this will work in the future. However, the devs at nvidia are pushing new driver pretty often, nouveaus dev is promissing too. So maybe we can make use of some neat stuff soon.

But, as I said, I didn't have to install anything with a live CD recently. Just added nouveau.modeset=1 to my the kerneloptions at boot time and it worked. 

With newer spins it didn't tho. Maybe it has been disabled for some reason.

---

### Post by the8thstar on 2009-04-30
Questions from a profane:

1- What is the diference b/w usplash and plymouth? Is the latter better?

2- What is nouveau?

Thanks for your clarification.

---

### Post by ghindo on 2009-04-30
> **the8thstar said:**
> Questions from a profane:

1- What is the diference b/w usplash and plymouth? Is the latter better?

2- What is nouveau?

Thanks for your clarification.2.  Nouveau is the open source Nvidia driver project.

Not sure how to answer the first question.

---

### Post by gnomeuser on 2009-04-30
> **the8thstar said:**
> Questions from a profane:

1- What is the diference b/w usplash and plymouth? Is the latter better?

2- What is nouveau?

Thanks for your clarification.


1. Plymouth is a modern bootsplash that supports kernel modesetting as well as advanced theming. Being superior depends on your definition, it supports new stuff and allows for us to do very interesting theming. It also gives us multiple levels of fallback (KMS, VESA and finally ASCII).

2. Nouveau is an open driver for the nvidia videocards. Currently it has no 3D support but it does support kernel modesetting (for some models) and things like accelerated XV which makes it a good upgrade to the nv driver. Progress on this driver is rapid and it is very actively maintained.

---

### Post by Nullack on 2009-04-30
> **gnomeuser said:**
> I have no idea where you get the idea that nouveau development is slow, clearly you are not following the same project I am.

While I think certain individuals like Ben Skeggs are doing a superhuman effort on the open source driver..........The reality is that having a paid group of full time developers doing driver development day in and day out is far ahead of a smaller group. NVIDIA has teams of developers, each consisting of many devs.

The code base across NVIDIA drivers is largely the same for BSD, Unix and Windows. It is a massive code base. For example the VDPAU code is largely the same as the windows DXVA code.

In comparison the open source driver does not have the resources and it has not existed as long as NVIDIAs code. Its broken for end users who expect their desktop to just work with video acceleration, graphics acceleration etcetc.

---

### Post by gnomeuser on 2009-05-01
> **Nullack said:**
> While I think certain individuals like Ben Skeggs are doing a superhuman effort on the open source driver..........The reality is that having a paid group of full time developers doing driver development day in and day out is far ahead of a smaller group. NVIDIA has teams of developers, each consisting of many devs.

The code base across NVIDIA drivers is largely the same for BSD, Unix and Windows. It is a massive code base. For example the VDPAU code is largely the same as the windows DXVA code.

In comparison the open source driver does not have the resources and it has not existed as long as NVIDIAs code. Its broken for end users who expect their desktop to just work with video acceleration, graphics acceleration etcetc.

Remember that staff is also duplicating Gallium3D, KMS and DRI2, so there goes the largest part of your development team.

Nouveau is also larger than Skeggs, there are people working on Video acceleration as well as a 3D driver using Gallium.

---

### Post by alphacrucis2 on 2009-05-01
Anyone know how ATI cards fit alongside Plymouth?

---

### Post by gnomeuser on 2009-05-01
> **alphacrucis2 said:**
> Anyone know how ATI cards fit alongside Plymouth?

They should work fine, Dave Airlie has been doing an awful lot of work on the ati driver. It is my understanding, no longer being the owner of a computer with an ati card *sob why did it have to die* that it works out of the box. You can grab a live image of Fedora 11 and see, that should give you an idea.

R600/700 cards may not be covered, I am unsure if that support has reached the drivers yet as we only just recently got the specifications from ATI.

---

### Post by alphacrucis2 on 2009-05-01
> **gnomeuser said:**
> They should work fine, Dave Airlie has been doing an awful lot of work on the ati driver. It is my understanding, no longer being the owner of a computer with an ati card *sob why did it have to die* that it works out of the box. You can grab a live image of Fedora 11 and see, that should give you an idea.

R600/700 cards may not be covered, I am unsure if that support has reached the drivers yet as we only just recently got the specifications from ATI.

Mine is in a Lenovo laptop with the mobility HD 3400. Under Jaunty I find that I didn't get good performance from either the ati or radeonhd driver when I tried them, although I didn't spend much time to figure out if they could be tweaked. I ended up settling on the proprietary fglrx (catalyst 9.4) driver which still supports my card. I'll probably leave trying Karmic to my old desktop machine which has pretty basic hardware.

---

### Post by super.rad on 2009-05-02
> **gnomeuser said:**
> They should work fine, Dave Airlie has been doing an awful lot of work on the ati driver. It is my understanding, no longer being the owner of a computer with an ati card *sob why did it have to die* that it works out of the box. You can grab a live image of Fedora 11 and see, that should give you an idea.

R600/700 cards may not be covered, I am unsure if that support has reached the drivers yet as we only just recently got the specifications from ATI.

My old computer with a Radeon Xpress 200m works fine with the Radeon driver and plymouth on fedora 11, my new computer with Radeon HD3200 doesn't yet though so R600/R700 aren't covered yet.

---

### Post by gnomeuser on 2009-05-02
> **super.rad said:**
> My old computer with a Radeon Xpress 200m works fine with the Radeon driver and plymouth on fedora 11, my new computer with Radeon HD3200 doesn't yet though so R600/R700 aren't covered yet.

We got early work on acceleration in the ati driver for those cards about a week ago if I understand Airlie correctly. I doubt this has reached any of the distros yet. Fedora is in deep freeze for F11 and Koala is still early with lots of backlogged builds.

Patience young grasshopper

---

### Post by super.rad on 2009-05-02
I'm in no rush, just glad I don't have to use the fglrx driver as that has always caused more problems for me. I have xv working fine so thats enough to keep me happy for now

---

### Post by Sense on 2009-05-02
Is the driver used for Plymouth also the driver used for X.org? 
I don't think everyone is going to use the open source driver, not matter how much better it might be, and giving NVidia users, whose(?) products were supported quite reasonably, an ASCII boot screen wouldn't be a good idea.
Using nouveau for the boot process and the closed driver for the desktop could solve this.

(Although I'd love to see Nouveau in such a good state that it's officially recommended.)

---

### Post by Simian Man on 2009-05-02
> **Sense said:**
> I don't think everyone is going to use the open source driver, not matter how much better it might be, and giving NVidia users, whose(?) products were supported quite reasonably, an ASCII boot screen wouldn't be a good idea.
Using nouveau for the boot process and the closed driver for the desktop could solve this.


Plymouth has a VGA fallback, so even if you use Nvidia's own driver, like I do, you don't need to have an ASCII boot screen.

---

### Post by gnomeuser on 2009-05-02
> **Sense said:**
> Is the driver used for Plymouth also the driver used for X.org? 
I don't think everyone is going to use the open source driver, not matter how much better it might be, and giving NVidia users, whose(?) products were supported quite reasonably, an ASCII boot screen wouldn't be a good idea.
Using nouveau for the boot process and the closed driver for the desktop could solve this.

(Although I'd love to see Nouveau in such a good state that it's officially recommended.)

two words for you:
Vesa fallback

I personally don't care one bit for users who elect to to install the nvidia driver, it causes so many problems it's unbelievable and I am personally tired of triaging bugs that lead back that path.. Regardless if someone should elected to continue using them even after the ATI and Nouveau drivers mature for whatever reasons we have a vesa fallback. They will have the same visual experience (minus of course the flicker free stuff on account of those drivers not ever utilizing KMS).

for your question, look up how Kernel Modesetting works. It will give you a far better understanding of the way the puzzle fits together than I would be able to explain.

---

### Post by Sense on 2009-05-02
> **gnomeuser said:**
> two words for you:
Vesa fallback

I personally don't care one bit for users who elect to to install the nvidia driver, it causes so many problems it's unbelievable and I am personally tired of triaging bugs that lead back that path.. Regardless if someone should elected to continue using them even after the ATI and Nouveau drivers mature for whatever reasons we have a vesa fallback. They will have the same visual experience (minus of course the flicker free stuff on account of those drivers not ever utilizing KMS).

for your question, look up how Kernel Modesetting works. It will give you a far better understanding of the way the puzzle fits together than I would be able to explain.

OK, thanks for your explanations. 

The reason I'm using the closed driver is that I'd like to have working 3D support, something that unfortunately requires you to use the closed driver.

---

### Post by Gina on 2009-05-02
When I tred a little while back, only the nvidia proprietry driver would work with my monitor.  Admittedly, I haven't tried again recently.

---

### Post by taavikko on 2009-05-09
Does anyone have any info if plymouth will be in karmic, or when uploaded to repos?
Searched around [https://blueprints.edge.launchpad.net/sprints/uds-karmic/+specs?start=0](https://blueprints.edge.launchpad.net/sprints/uds-karmic/+specs?start=0)
to find info, but wasn't able to find none.

I know that UDS will address what will be in final release, but if Leonidas is going to ship with it, why wouldn't Karmic?

---

### Post by meeples on 2009-05-10
> **taavikko said:**
> Does anyone have any info if plymouth will be in karmic, or when uploaded to repos?
Searched around [https://blueprints.edge.launchpad.net/sprints/uds-karmic/+specs?start=0](https://blueprints.edge.launchpad.net/sprints/uds-karmic/+specs?start=0)
to find info, but wasn't able to find none.

I know that UDS will address what will be in final release, but if Leonidas is going to ship with it, why wouldn't Karmic?


yea we know it will be in karmic, they've already said that, i dont hink its in the repos yet, i tried to install it manually but i couldnt get i tworking so i guess i'll just have to wait till its official.

---

### Post by taavikko on 2009-05-10
> **meeples said:**
> yea we know it will be in karmic, they've already said that, i dont hink its in the repos yet, i tried to install it manually but i couldnt get i tworking so i guess i'll just have to wait till its official.

No, it isn't in the repos yet, but where's the discussion this hitting the Karmic. 
There was one for Jaunty [https://blueprints.edge.launchpad.net/ubuntu/+spec/plymouth](https://blueprints.edge.launchpad.net/ubuntu/+spec/plymouth)
No talk at the mailing lists for ubuntu-devel.


but that's it...

All though I'm confident this will be hitting Karmic...

---

### Post by meeples on 2009-05-11
> We're eagerly following the development of
kernel mode setting, which promises a smooth and flicker-free startup.
We'll consider options like Red Hat's Plymouth, for graphical boot on
all the cards that support it. We made a splash years ago with Usplash,
but it's time to move to something newer and shinier. So the good news
is, boot will be beautiful.
[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000536.html]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000536.html")


sounds promising for plymouth, seems to be there only option for a beautiful startup isnt it?

---

### Post by Merk42 on 2009-05-11
> **meeples said:**
> [https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000536.html]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000536.html")


sounds promising for plymouth, seems to be there only option for a beautiful startup isnt it?

Well under the same section, "Desktop" he also talks about the new look which has yet again been canceled.  So take what he says with a grain of salt.

---

### Post by ghindo on 2009-05-11
> **Merk42 said:**
> Well under the same section, "Desktop" he also talks about the new look which has yet again been canceled.  So take what he says with a grain of salt.You're really harping on this point, aren't you? ;)

---

### Post by Starks on 2009-05-11
> **ghindo said:**
> You're really harping on this point, aren't you? ;)

Doing a new look with Gnome 3 all but guaranteed for Lucky Liger or Mighty Manx is a pretty bold move.

I just don't see it happening.

---

### Post by loomsen on 2009-05-12
This development is imho cruicially wrong. 

More than ever jaunty disappointed with a too high focus on mass compatibility, which, from my point of view isn't desirable but actually the point which made me leave MS back then.

Further, I don't think dist-maintainers have the moral and social responsibility to protect their users. Deciding to go with an osOS is usually following up a critic, dialectic dispute concerning the available options.
Besides the obvious reasonability of chosing the better and free OS, I used to enjoy the freedom and self-reliance linux distributions offer. 
And this is what I miss in jaunty the most, the feeling of autonomy and sovereignty I expect from any unix based distro.

I'm not willing to bug around like the dontzap option does, it sucks, but it is fixed with one line, so that's ok (tho I don't understand, why it wasn't realised the other way round - who want's it may specify it...)
However, there are other rather serious issues with jaunty, like the revival of the high load cycle bug (which actually was fixed in hardy... Some nice guy thought it would be fun to reintroduce it tho... There aren't many sounds I know which can hurt, terrify and threaten you that much. And although I remembered how to fix it, every single CLACK could have been the last for my hdd. 
Every other bug feels like a joke compared to this bug. Ntl, I won't ever get the reason for building IPv6 into the kernel, nor why someone would find it smart porting a higher version to a lower one. This could be continued inifinitely, why ignore the big evolutionary steps and focus on obsolete versions?

I think ubuntu will fall behind fedora in the near future. Even debian ships the 2.6.29 kernel.
But that's probably ubuntus destiny. Can't expect to win gold if you go for bronze from the start.

However, due to the reasons above and some other I don't even remember, I built my kernel myself to bypass the time till leo roars, and decided to go with it from day 1 of the stable release. 
If I have to review and fix everything after each release myself anyway, it doesn't make much of a difference which distro I use at all.

Actually I just finished building 2.6.30-rc4, which works significantly smoother than 2.6.29 does. 
The KMS adds a lot of cream too imho, worth the trouble if you enjoy using your shell, not worth it if you prefer a DE anyway. Not as obsolete as a splash at boottime tho, it offers really useful features. 

Just do it yourself guys. Not much to be done wrong. Take your old config, disable IPv6 if your country doesn't have IPv6 neither, disable amateur radio, isdn, and some debug messages you most likely won't make use of, enable btrfs (tho it's experimental, it adds some VERY useful features imo --> 
[I like: no1](http://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices)
[I like: no2](http://btrfs.wiki.kernel.org/index.php/Conversion_from_Ext3)

Plus improved allocation of files, dynamic inode allocation, snapshots, online fsck and so forth.

Btw, the warnings aren't bugs. It is unstable, as for now, tho it can be used as a tool to reallocate ressources as shown in the links above. 
I usually need the space on a hd where there is no space. Dynamically increasing partitions and multiple hd support solve many many issues, at least for me.

I'm sorry for the OT, but tbh I find Plymouth stands interchangeably for the (r)evolutionary step from 28 to 29. Bummer this is ignored imo. 
At least I prefer enjoying new features and fixing bugs to making one step forward and two steps back, just to make sure every win user is able to keep up. (I also think it's grotesque even offering stuff like WuBi or  how the windows installer is called. Waste of time, but thats just my humble op.)

Just my 2 ct.

---

### Post by seeker5528 on 2009-05-13
> **loomsen said:**
> 
I'm not willing to bug around like the dontzap option does, it sucks, but it is fixed with one line, so that's ok (tho I don't understand, why it wasn't realised the other way round - who want's it may specify it...)

This was an upstream change, not Ubuntu specific.

A little (very little) googling and......

Alt+SysRq+K

works for me without having to "fix" anything.

In the process I also found:

Alt+SysRq+B

I'm going to have to find a listing of all these SysRq key combos, I like it. Not sure how accessable these SysRq combos are on some laptops though.

Later, Seeker

---

### Post by olskar on 2009-05-13
> **seeker5528 said:**
> This was an upstream change, not Ubuntu specific.

A little (very little) googling and......

Alt+SysRq+K

works for me without having to "fix" anything.

In the process I also found:

Alt+SysRq+B

I'm going to have to find a listing of all these SysRq key combos, I like it. Not sure how accessable these SysRq combos are on some laptops though.

Later, Seeker

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key) ;)

---

### Post by coolen on 2009-05-13
Be careful with Alt+SysRq+B. Automatic reboot, very bad. It's the last step in the clean shutdown, after Alt+SysRq+[R E I S U] have taken care of everything else.

---

### Post by loomsen on 2009-05-13
I think I'd get another infraction if I'd answer you.

> A little (very little) 

Try a little bit more next time, and, if it doesn't hurt you too much, yet a little bit more the time after next time. Maybe you'll be able to figure out the difference then.

---

### Post by puccaso on 2009-05-13
on the up note..

i installed plymouth and just typed in vga=0x317 at the grup prompt.. kept the splash there too

and even though i'm using ATI (which usually sucks with this stuff) it worked..

was quite neet if i say so myself!

---

### Post by zekopeko on 2009-05-13
> **Merk42 said:**
> Well under the same section, "Desktop" he also talks about the new look which has yet again been canceled.  So take what he says with a grain of salt.

if i remember correctly mark hasn't said anything about a complete new look. he said that KK would have "designer fingerprint".
so complete theme revamp != "designer fingerprints".

---

### Post by zekopeko on 2009-05-13
> **loomsen said:**
> This development is imho cruicially wrong. 

More than ever jaunty disappointed with a too high focus on mass compatibility, which, from my point of view isn't desirable but actually the point ...

You are using the wrong distro i would say. the kernel is the most important part of the system and considering the ubuntu dev cycle choosing 2.6.28 was the best choice at the time.

---

### Post by seeker5528 on 2009-05-13
> **coolen said:**
> Be careful with Alt+SysRq+B. Automatic reboot, very bad. It's the last step in the clean shutdown, after Alt+SysRq+[R E I S U] have taken care of everything else.

If I've gone through other stuff and lost hope, the power button is my first preference in attempting to shut down cleanly, if it looks like that is not working, Alt+SysRq+B is quicker than holding the power button in for 5 seconds if it works, and not much time spent on it if it doesn't.

Definitely worth having a list of the SysRq combos handy, don't know how many are useful to me personally being a non-developer type but I do see patterns in things sometimes that give me ideas on what to search for.


> **loomsen said:**
> Try a little bit more next time, and, if it doesn't hurt you too much, yet a little bit more the time after next time. Maybe you'll be able to figure out the difference then.

You mean difference between Ctrl+Alt+Backspace and Alt+SysRq+K or the difference between a last resort and an orderly shutdown?

Or maybe the difference between stopping once you've found what you need versus attempting to find a full explanation. 

Later, Seeker

---

### Post by loomsen on 2009-05-13
> **seeker5528 said:**
> 
You mean difference between Ctrl+Alt+Backspace and Alt+SysRq+K 

Yes.

Usually I try and avoid using any of them two, nevertheless... 

It's a very evil low level emergency ignition interrupt, and if you like your data, you DO want to avoid it whereever this is possible. If you don't care, I don't bother explaining why you should care.

Zap isn't really harmful at all (as harmful as logging out can be)
This doesn't mean I always logged out like that, and I'm not afraid of hacking my xorg.conf, nor am I afraid of a shell. 
I even enjoy using the shell or terminals to do things (cause it's just a lot faster)

Zap was more like a tool for me, while SysRq has been the _lifeline facing death_

Anyway, this was just annoying to me, not even a bug facing some serious hardware issues like I had to deal with

> You are using the wrong distro i would say. the kernel is the most important part of the system

I used to use the right distro until jaunty imo.

Further I'm aware of the kernels importance, thats why I build several custom kernels, right now this is:

docter[~] uname -rm
2.6.30-rc4~loom-2060300-rev3 x86_64

I just wanted to share my thoughts, and I think I pointed out which issues especially made me suffer. 

> --- the ubuntu dev cycle choosing 2.6.28 was the best choice at the time

OK, if you read my post above again you'll get the idea why I think this was the wrong decision. 
I used to join development releases between alpha3 and 4 since hardy. So, I already ran the kernel when the decision was made. And even then - being the most recent release at that time - the kernel lacked performance as well as features. 
Just read some of the upstream discussions on improvements shipped in 2.6.29, which actually was a huge evolutionary step.

This, what I posted above, what I experienced so far and all the discussions bout it on IRC, online and offline just didn't leave me any choice than considering to switch to RH for now. I'll probably still have ubuntu up and running on some partition, it will just lose its current state as my _main_ distro.

I assume you didn't follow the latest development too much right? 

My points still remain the same:
    1) I have to suffer from mass compatibility
    2) I like my hardware, and I know my hardware. I don't need anyone to take care of me. So why in devils name would it be reasonable cooking drivers in, while a major part of the whole world isn't even able to use it.
Why would it be reasonable to revive long fixed bugs? Where's the reason on backporting upstream drivers, causing more trouble and weird posts on here than any advantage would have had a hard deal with. Expecially if there is no reasonable advantage.

Maybe taking a closer look at the release dates from the base directory will show what can be done in 6 months. And, hence any chance is accompanied by an equal risk, I really doubt ubuntu will be able to make up for it just like that. (as basically others have to do the work anyway)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Common ubuntu users behavior tho, criticizing the distro DOES NOT include the users. I'm happy for everyone who enjoies jaunty, and I also wish you good luck and all the best for future "development" cycles.

I even joined the 3rd consecutive after hardy and intrepid haven't been to cruel with me.
I think I explained my point pretty well, when did you join the development and how was it for you?

If you wanna discuss this, do it right please. Destructivism is easy, everyone can be destructive. But if it was the right approach we'd probably still ride horses and go to bed from dusk til dawn.

I just wonder, if everything works just fine and you think it was the completely right decision to NOT ship the current stable release, why do you even care about plymouth?
Don't get me wrong, I don't want to offend you...

>  choosing 2.6.28 was the best choice at the time

This is a fatal sentence demanding a lot explaination what makes you think so tho. I explained why I think the decision was wrong, and what could have been avoided or done better to actually improve things.

Your turn.

---

### Post by coolen on 2009-05-14
> **seeker5528 said:**
> If I've gone through other stuff and lost hope, the power button is my first preference in attempting to shut down cleanly, if it looks like that is not working, Alt+SysRq+B is quicker than holding the power button in for 5 seconds if it works, and not much time spent on it if it doesn't.

Definitely worth having a list of the SysRq combos handy, don't know how many are useful to me personally being a non-developer type but I do see patterns in things sometimes that give me ideas on what to search for.

Alt+SysRq+B is little better than pulling the power cable out of the back of your computer (or removing your battery if you're on a laptop).

If it's going to do anything for you, so are the other commands. It won't save the data you're working on and not saved in a while, but it'll ensure the rest of your data is safe.

If you want, use it. Chances are you won't have any problems, most of the time. I just thought I'd warn you that it's not a magical solution, it's ruder than a SIGKILL.

---

### Post by seeker5528 on 2009-05-14
> **loomsen said:**
> 
Zap isn't really harmful at all (as harmful as logging out can be)
This doesn't mean I always logged out like that, and I'm not afraid of hacking my xorg.conf, nor am I afraid of a shell. 
I even enjoy using the shell or terminals to do things (cause it's just a lot faster)

Zap was more like a tool for me, while SysRq has been the _lifeline facing death_


If everything you care about in the VT that the xsession is running in will be killed when the xsession is killed, I fail to see the difference between killing the xsession and killing everything in the VT.

Either way unsaved data in running applications will be lost, configuration changes potentially unsaved, lock files potentially left behind.

Personally I never heard anything about anybody hitting Ctrl+Alt+Backspace by accident until after this change had been made, but that has been argued to death by people who care about it way more than I do. It's a non-issue to me.

Later, Seeker

---

### Post by coolen on 2009-05-14
> **seeker5528 said:**
> Personally I never heard anything about anybody hitting Ctrl+Alt+Backspace by accident until after this change had been made

I hate to end a streak, but I did it once. I like to have System Monitor bound to Ctrl+Alt+Del, and one day...whoops.

---

### Post by Kareeser on 2009-05-21
> **coolen said:**
> I hate to end a streak, but I did it once. I like to have System Monitor bound to Ctrl+Alt+Del, and one day...whoops.

... but I bet you learned your lesson for next time... ;)

In any case, this isn't the time nor place to be talking about Zap... but like others have said, I wouldn't use AltGr-SysRq-B on its own... definitely chain it with the rest (R E I S and U)... makes for a handy acronym, don't you think?

The REISUB combo has gotten me out of a couple pickles already, that Ctrl-Alt-BkSp (once re-enabled) couldn't get me out of.

---

### Post by super.rad on 2009-05-22
damn, got excited hoping there was some more news about plymouth in karmic...

---

### Post by autocrosser on 2009-05-22
Me too---I got a interesting splash from the Plymouth list the other day--am thinking about modding it a bit for Ubuntu---Its a glowing circle---anyone interested I'll post the link & info and if I do the mod work on it I'll post ASAP.........

---

### Post by Slug71 on 2009-05-22
Got me too. Hopefully we will hear something during UDS or soon after.

---

### Post by super.rad on 2009-05-28
> **whiprush said:**
> 
Also on the plymouth thing Scott James Remnant told me that they are probably not going to go with it and instead just make boot speed so fast (the announced goal is 10 seconds on a mini9 netbook) that it'll just be a splash for a few seconds and then your desktop.



Looks like this one's not happening aswell.
Although personally I'd rather have a 10 second boot with usplash than a 20 second with plymouth

---

### Post by Jay_Bee on 2009-05-28
if Usplash gets KMS support (and it will) then I really don't care about Plymouth.

---

### Post by plun on 2009-05-28
> **autocrosser said:**
> Me too---I got a interesting splash from the Plymouth list the other day--am thinking about modding it a bit for Ubuntu---Its a glowing circle---anyone interested I'll post the link & info and if I do the mod work on it I'll post ASAP.........

I missed this "Call"....  please post...:D

(Even if it takes 10 seconds.)

---

### Post by autocrosser on 2009-05-28
I've got red_team working on making a .so---so I hope to have it ready this weekend/early next week---will look like this: Black background--glowing circle as a progress bar--when it gets close to complete it will have a rotating then rotating/pulsing ubuntu logo in the centre........as least that is the starting plan........

---

### Post by Starks on 2009-05-28
So... Plymouth is getting dropped too?

Karmic is shaping up to be a major upset in the experimental front.

I'd jumpship to Rawhide if it wasn't for Fedora's inferior packaging and interface.

---

### Post by MacUntu on 2009-05-28
If Plymouth gets dropped because boot times are too short - isn't that a good thing?

---

### Post by Starks on 2009-05-28
I'd prefer Plymouth+Upstart+KMS over Usplash+svinit+KMS.

---

### Post by ghindo on 2009-05-28
> **Starks said:**
> I'd prefer Plymouth+Upstart+KMS over Usplash+svinit+KMS.I thought that Upstart was making it into Karmic?

---

### Post by super.rad on 2009-05-28
> **MacUntu said:**
> If Plymouth gets dropped because boot times are too short - isn't that a good thing?

Well fast bootimes are good, but fast boot + plymouth would be better

---

### Post by davideotape on 2009-05-28
> **super.rad said:**
> Well fast bootimes are good, but fast boot + plymouth would be better

Can we really get a 10s boot with eyecandy? What I'd really like is a graphical boot that icorporated all the boot text you get without usplash

---

### Post by MacUntu on 2009-05-28
> **davideotape said:**
> Can we really get a 10s boot with eyecandy?

Let's say we can. How long do we see the eyecandy?

Here is a 9.20s boot with Usplash: [http://www.youtube.com/watch?v=crCAkFESyD8](http://www.youtube.com/watch?v=crCAkFESyD8)

Pretty short six seconds of bling bling that adds 1.5s to the boot time.

I'd rather see a nice static image that fades flicker-free to GDM which again fades to the desktop.

---

### Post by autocrosser on 2009-05-28
> **plun said:**
> I missed this "Call"....  please post...:D

(Even if it takes 10 seconds.)

Here is the raw file from one of the Plymouth developers......[http://myweb.tiscali.co.uk/theholyettlz/plymouth-theme-glowring-0.1.tar.bz2](http://myweb.tiscali.co.uk/theholyettlz/plymouth-theme-glowring-0.1.tar.bz2)

I'll contact red_team to see where he's with the .so.....

---

### Post by plun on 2009-05-29
> **autocrosser said:**
> Here is the raw file from one of the Plymouth developers......[http://myweb.tiscali.co.uk/theholyettlz/plymouth-theme-glowring-0.1.tar.bz2](http://myweb.tiscali.co.uk/theholyettlz/plymouth-theme-glowring-0.1.tar.bz2)

I'll contact red_team to see where he's with the .so.....

Thanks !

Yes the so file is needed....
```

plun@plun:~$ sudo plymouth-set-default-plugin glowring
/usr/lib/plymouth/glowring.so does not exist
```

Build manual
[http://ubuntuforums.org/showpost.php?p=6880312&postcount=54](http://ubuntuforums.org/showpost.php?p=6880312&postcount=54)

;)

---

### Post by MadsRH on 2009-05-29
Can anyone confirm what **tgpraveen** wrote in *['Karmic 9.10 planned features']("http://ubuntuforums.org/showpost.php?p=7359991&postcount=1")*.

> Also it seems that plymouth wont be in karmic atleast to make way for 10s boot, dont know about KMS??

With Mark talking about a slick boot in his [ UDS opening speech]("http://anotherubuntu.blogspot.com/2009/05/eavesdrop-on-karmic-koala-uds.html"), I doubt that this can be true :confused:

---

### Post by MacUntu on 2009-05-29
I'm sure we'll know more facts and less guessing next week. ;)

---

### Post by autocrosser on 2009-05-29
> **plun said:**
> Thanks !

Yes the so file is needed....
```

plun@plun:~$ sudo plymouth-set-default-plugin glowring
/usr/lib/plymouth/glowring.so does not exist
```Build manual
[http://ubuntuforums.org/showpost.php?p=6880312&postcount=54](http://ubuntuforums.org/showpost.php?p=6880312&postcount=54)

;)

Ya--I tried that & couldn't seem to make something workable---so I handed the artwork to him ---have yet to hear back.....He knows more than I to quite a degree about building them....

---

### Post by plun on 2009-05-29
> **autocrosser said:**
> Ya--I tried that & couldn't seem to make something workable---so I handed the artwork to him ---have yet to hear back.....He knows more than I to quite a degree about building them....

OK.... I manage to build a shared object file...;)

Dont ask me how :D

Also found this....

[http://ubuntuforums.org/showpost.php?p=6892088&postcount=83](http://ubuntuforums.org/showpost.php?p=6892088&postcount=83)


Testing....

---

### Post by Gourgi on 2009-05-29
> **MacUntu said:**
> Let's say we can. How long do we see the eyecandy?

Here is a 9.20s boot with Usplash: [http://www.youtube.com/watch?v=crCAkFESyD8](http://www.youtube.com/watch?v=crCAkFESyD8)

Pretty short six seconds of bling bling that adds 1.5s to the boot time.

I'd rather see a nice static image that fades flicker-free to GDM which again fades to the desktop.

really impressive !
+1 for a static image and a rocket boot!

---

### Post by autocrosser on 2009-05-29
> **plun said:**
> OK.... I manage to build a shared object file...;)

Dont ask me how :D

Also found this....

[http://ubuntuforums.org/showpost.php?p=6892088&postcount=83](http://ubuntuforums.org/showpost.php?p=6892088&postcount=83)


Testing....

If you've got a .so working I can shoot you the modified image files--going to work in a few minutes, so it would have to be this evening 8+hrs from now.....

---

### Post by jsmidt on 2009-05-29
Sorry guys, no [Plymouth either]("http://www.phoronix.com/scan.php?page=news_item&px=NzI5NQ"). :)

---

### Post by plun on 2009-05-29
> **autocrosser said:**
> If you've got a .so working I can shoot you the modified image files--going to work in a few minutes, so it would have to be this evening 8+hrs from now.....

Yup, but its a "black screen" again...:---)

MacUntu and I discussed it earlier, the Vesa challenge

[http://ubuntuforums.org/showpost.php?p=7017508&postcount=130](http://ubuntuforums.org/showpost.php?p=7017508&postcount=130)

Using latest nVidia driver from thefirstm ppa

---

### Post by davideotape on 2009-05-29
> **jsmidt said:**
> Sorry guys, no [Plymouth either]("http://www.phoronix.com/scan.php?page=news_item&px=NzI5NQ"). :)

Not to bothered as long as the 10 second boot times are delivered. Currently I'm at 45 sec. (albeit with a usb external hard drive)

---

### Post by gnomeuser on 2009-05-29
> **davideotape said:**
> Not to bothered as long as the 10 second boot times are delivered. Currently I'm at 45 sec. (albeit with a usb external hard drive)

10 sec boot will very likely only be on a SSD equiped machine. Regardless Plymouth isn't just a bootsplash, Moblin uses it to setup KMS for a quicker X startup and thus a lowered total boottime. 

I think without some measure to do KMS, it will be hard to reach 10 secs even on mythical hardware. I am guessing instead of using the plymouth version found in moblin the ubuntu team will do their own KMS work effective I suspect duplicating the code. NIH syndrome?

Regardless there are other advantages aside a quick boot, one gets a nice visual unlocking thing for dm-crypt and the option to have a bootsplash which, kid you not, will still be needed on a significant amount of setups which can't make it to gdm in a reasonable amount of time.

I don't really see the argument that lowering boottime magically removes the need or usefulness of plymouth. Sure lowered boottime is nice but plymouth is more than a bootsplash and can help in reaching that goal.

---

### Post by Slug71 on 2009-05-29
> **jsmidt said:**
> Sorry guys, no [Plymouth either]("http://www.phoronix.com/scan.php?page=news_item&px=NzI5NQ"). :)

This is just BS now!! I'm sooo ticked!!!

---

### Post by davideotape on 2009-05-29
gnomeuser: I asked one of the devs, and they said it was on a normal, 7200rpm, IDE hard drive

slug71: If you don't like it, use another distro. The devs have good reasons for not including it, and if you don't agree with those reasons, you're free to use another distro at any time.

---

### Post by autocrosser on 2009-05-29
Well--I've been tracking Plymouth for some time now & it's disappointing that it won't be used--but I am all for short boot-times.........let us see if it can be done...

---

### Post by Slug71 on 2009-05-29
> **davideotape said:**
> gnomeuser: I asked one of the devs, and they said it was on a normal, 7200rpm, IDE hard drive

slug71: If you don't like it, use another distro. The devs have good reasons for not including it, and if you don't agree with those reasons, you're free to use another distro at any time.

Thank you i will.

---

### Post by gnomeuser on 2009-05-29
> **davideotape said:**
> gnomeuser: I asked one of the devs, and they said it was on a normal, 7200rpm, IDE hard drive

I assume boot in 10 secs is defined as grub to usable gnome interface, and in the name of honesty for marketing it should work on pretty much any machine you walk up and install Ubuntu on.

That will be a hard goal to hit, not impossible I am sure. Still you have to content with the fact that many (if not most) laptop drives are 5200 RPM. They definitely might sweat a lot to hit that target.

I will remain unconvinced they can do this on most machines in 6 months, but feel free to show me the action plan I would be honestly very interested. Faster boot is always nice and will surely expose a boat load of issues for everyone to hack away on. Which is the fun part for me, boot time isn't that big an issue to me, my machine halts during boot anyways for me to unlock my dm-crypt but it is appealing in a number of settings and it demos very well.

That though all strayed some from the point of my original post. I still believe that Plymouth would help hit that goal, it sure did for Moblin. Thus is seems some what nonsensical to dismiss Plymouth specifically based on a boot time requirement.

---

### Post by Slug71 on 2009-05-29
> **davideotape said:**
> gnomeuser: I asked one of the devs, and they said it was on a normal, 7200rpm, IDE hard drive

slug71: If you don't like it, use another distro. The devs have good reasons for not including it, and if you don't agree with those reasons, you're free to use another distro at any time.

> **Slug71 said:**
> Thank you i will.


Hmm, F11 or Foresight :-k

---

### Post by ktp on 2009-05-29
> **gnomeuser said:**
> I assume boot in 10 secs is defined as grub to usable gnome interface, and in the name of honesty for marketing it should work on pretty much any machine you walk up and install Ubuntu on.

That will be a hard goal to hit, not impossible I am sure. Still you have to content with the fact that many (if not most) laptop drives are 5200 RPM. They definitely might sweat a lot to hit that target.

I will remain unconvinced they can do this on most machines in 6 months, but feel free to show me the action plan I would be honestly very interested. Faster boot is always nice and will surely expose a boat load of issues for everyone to hack away on. Which is the fun part for me, boot time isn't that big an issue to me, my machine halts during boot anyways for me to unlock my dm-crypt but it is appealing in a number of settings and it demos very well.

That though all strayed some from the point of my original post. I still believe that Plymouth would help hit that goal, it sure did for Moblin. Thus is seems some what nonsensical to dismiss Plymouth specifically based on a boot time requirement.

I have to say...this is going to be hard goal to hit this on most machine.  9.04 improved boot time...but I know for sure different people had different experience (extreme ranges).  So if there is under 10 sec boot on my system, which is boot at around 24-27 sec, I would be so happy.  But I would think giving an option to have plymouth wouldn't hurt either...the boot might even feel faster since I might not be bored during it.

---

### Post by ktp on 2009-05-29
> **Slug71 said:**
> Hmm, F11 or Foresight :-k

F11 :p

---

### Post by vishalrao on 2009-05-29
> **gnomeuser said:**
> I assume boot in 10 secs is defined as grub to usable gnome interface

I'd like to know what the devs define as boot time too, I thought it was just grub menu to only the GDM login/greeter screen. At least that's what the Jaunty 20 second boot articles (phoronix etc) were rejoicing about :)

Even if its 10 sec for just grub to only gdm/kdm on my Core2 Quad 2.4 ghz with 7200 RPM SATA HDD I will be very happy/impressed!

I don't care for Plymouth too much if the boot is so fast. I believe KMS is still planned for flicker free transitions, I hope it works for my nvidia 8800gt since they picked kernel .31.

But then I read that they plan to load (fade in) GDM much earlier in the boot process (3sec) so that you can login and get to a useable desktop faster... that might give the illusion of faster boot.

So the 10 sec goal might include the "pre load" illusion - the devs are also maybe trying to be magicians!

---

### Post by loomsen on 2009-05-30
> **Slug71 said:**
> Hmm, F11 or Foresight :-k

F11...

I'd suggest a netinstall image, you'll be able to alter the whole configuration upon installation, like using the packagemanager to chose which pkges  you want to be installed, partitioning (if you enable btrfs even this will work), kms per default (only thing I had to do was adding vga=<my res> to the kernel-line), choose your repos and so on.

[Go here for 64bit isos](http://download.fedora.redhat.com/pub/fedora/linux/development/x86_64/os/images/)

[32bit](http://download.fedora.redhat.com/pub/fedora/linux/development/386/os/images/)

---

### Post by olskar on 2009-05-30
> **vishalrao said:**
> I'd like to know what the devs define as boot time too, I thought it was just grub menu to only the GDM login/greeter screen. At least that's what the Jaunty 20 second boot articles (phoronix etc) were rejoicing about :)


Yes, I think they count that way. However I hope gnomeuser is right, booting with the speed of light in ~10 seconds, login and then sit and wait for the gnome desktop to load would kind of kill the speed experience.

---

### Post by Jay_Bee on 2009-05-30
Some things from the Gobby document suggest that total grub-to-finished-gnome time would be 15 seconds (on Dell Mini 9).

> 
* Mini 9 for reference platform
* Jaunty target was 25 seconds
* Essentially only remaining I/O after 25 seconds was NetworkManager
* initramfs size linearly increases boot time

* Half of time is desktop is login to desktop - approx 12 seconds

* The 3 pieces for gnome login that are "really" slowing things down
 - Compiz
 - Gnome panel
 - Nautilus

* What should be the new target time actually be?
 - So initramfs and kernel should be able to complete in 2 seconds
 - Approx 2 seconds for the rest of the boot if we take out apparmor from the
   equation
 - 1 second for X to start

 - gnome-panel, nautilus and compiz all need serious work

 - 5-6 is the kernel and gdm target
 - 15 is the new total target number


---

### Post by MacUntu on 2009-05-30
> **Jay_Bee said:**
> Mini 9 for reference platform.

Don't know if that's a good choice for a reference platform but that's a very important point to mention.

---

### Post by coolen on 2009-05-30
I think it's no coincidence that they chose a Moblin-compatible system for their reference.

---

### Post by gnomeuser on 2009-05-30
> **Slug71 said:**
> Hmm, F11 or Foresight :-k

It depends on what you want out of a distro, if you want lots of developers, bureaucracy but also early access to interesting technology then Fedora might be for you. Having been part of the development team I can say that pretty much every part of Fedora is maintained by the active upstream developers or people who care passionately about that software. They do tend to be pro lots of flamewars and pointless policies.

Foresight is really interesting, they have few developers but still manage to do a lot of cool things mostly thanks to how easy Conary makes packaging for the maintainer. The developers are friendly and the IRC channel is always good fun. Foresight has much more the feel of Linux as the community was 5 years ago, it's an exploration of technology.

I have personal reason to dislike Fedora, I will though warmly recommend it. They do great work and further the Linux desktop with every release. Personally I favor Foresight, but for reasons relating more with personal passion than with reason.

I would recommend trying out both, F11 is out any day now and Foresight is a rolling release so once you have it installed you will always get a constant trickle of new software and version upgrades are smooth as silk.

Sorry for taking this a bit off topic, but slug asked.

---

### Post by gnomeuser on 2009-05-30
> **olskar said:**
> Yes, I think they count that way. However I hope gnomeuser is right, booting with the speed of light in ~10 seconds, login and then sit and wait for the gnome desktop to load would kind of kill the speed experience.

I think the important thing in setting such a goal is:

1) the goal as to be from the time we take control till the time we present a working functional desktop. In the common case this would be from grub till GNOME is fully loaded.

2) It must work on actual hardware, we can't promise 10 sec booting and then set the hardware requirements out of line with what is in the hands of our users.

3) Lazy loading is cheating, you can't present a desktop that is then unusable for the first minute because things are still loading. Loading on demand is fine but deferring just to get to GUI is cheating.

4) Disallow any functionality regressions, decreasing boot time by disabling services is also cheating, the desktop needs to be functional at the time it is presented except for cases where loading on demand can be done.

I think given those restraints going from grub to GNOME on an off the shelf affordable laptop in 10 sec is going to be hard.

Lots of work has been done and looking at Moblins very ambitious goal of hitting a 2 sec boot from grub to workable GUI I think a general purpose OS like Ubuntu might be able to do 10 secs on most hardware. It will take some clever thinking and some hard optimization. 

One question is if it is worth it doing that work to GNOME now that GNOME 3 is coming around the corner and will change the equation (DConf e.g. makes the recent GConf optimzations obsolete). The GNOME panel is also supposedly going away in favor of the GNOME-Shell and the big performance bottleneck we call Compiz is being replaced with Mutter. Is it worth 6 months effort when all of it will be replaced 6 months later?

For the actual boot and start up of X I would wager that it is worth it but to optimize GNOME startup this late in it's lifetime seems a wasted effort. Except for the fact that it will give us a chance to develop tools to measure boot time and have them integrated into the new frameworks so that we an ensure against regressions from day one.

Lots of problem areas, lots of fun to be had.

---

### Post by ronacc on 2009-05-30
one area that conflicts with a fast startup is Ubuntu's desire to have a "minimal interaction required" install . If the installer does not ask for guidence , you end up with services and software being loaded at startup that you MAY need but also may not, this slows down the startup and increases overhead wastefuly. refering to your point 4 one mans regression is another mans "cleanup". Refering to your point 3 "lazy loading" might be a good thing for some services/apps that are not truly universialy required .

---

### Post by Swarms on 2009-05-30
> **ronacc said:**
> one area that conflicts with a fast startup is Ubuntu's desire to have a "minimal interaction required" install . If the installer does not ask for guidence , you end up with services and software being loaded at startup that you MAY need but also may not, this slows down the startup and increases overhead wastefuly. refering to your point 4 one mans regression is another mans "cleanup". Refering to your point 3 "lazy loading" might be a good thing for some services/apps that are not truly universialy required .

If they are not universally required, they should be included at startup.

---

### Post by gnomeuser on 2009-05-30
> **ronacc said:**
> one area that conflicts with a fast startup is Ubuntu's desire to have a "minimal interaction required" install . If the installer does not ask for guidence , you end up with services and software being loaded at startup that you MAY need but also may not, this slows down the startup and increases overhead wastefuly. refering to your point 4 one mans regression is another mans "cleanup". Refering to your point 3 "lazy loading" might be a good thing for some services/apps that are not truly universialy required .

Then that would be ondemand loading. Lazy loading would be defering needed services till the GUI is loaded. This is similar to what Windows XP does.

Now there are cases where on demand loading cannot be done currently to the best of my knowledge. Say you want to print, this requires CUPS, typically one could do on demand loading if a printer was inserted but what if it is a network printer. One could perhaps load it when the print button is pressed but then we have no knowledge of available printers and starting up CUPS and doing discovery presumably takes a significant amount of time.

There are situations where the easy solution is to load services on bootup, the more sane approach might be lazy loading it some time after login is completed. The "right" solution is a little harder to think up if it is at all possible under the current technical limitations.

So how do we do we handle cases like print support without regressing functionality nor imposing a boot time penalty or cheating. Maybe for a 6 month target cheating is the only option but long term we have to be able to do something more clever.

---

### Post by ktp on 2009-05-30
> **gnomeuser said:**
> Then that would be ondemand loading. Lazy loading would be defering needed services till the GUI is loaded. This is similar to what Windows XP does.

This and boot time not possible on general hardware is my biggest worry...but only time will tell.  In any case I really hope they consider having plymouth as option to install if you want.  I don't think i would install it, specially if the boot is ~10 sec, but I know a lots of people want it so it would be nice to see it.

---

### Post by inportb on 2009-05-30
Hmm... or have the option to play a DVD while the OS loads; this'd buy an hour or two of boot time ;)

---

### Post by davideotape on 2009-05-30
> **inportb said:**
> Hmm... or have the option to play a DVD while the OS loads; this'd buy an hour or two of boot time ;)

Good idea. Or how about playing a game of pong whilst it's booting?

---

### Post by ronacc on 2009-05-30
@ gnomeuser
I will accept your terminology of demand loading , and btw your example of cups being loaded on demand would suit me , I print something less than once in 10 sessions so a small delay in getting the first ( and infrequent) page out would eaisly be offset by faster boots , The point I was trying to make is that a newbe friendly install and a lighting fast boot may be mutualy exclusive .

---

### Post by gnomeuser on 2009-05-30
> **davideotape said:**
> Good idea. Or how about playing a game of pong whilst it's booting?

I remember that Corel Linux I believe it was let you play solitaire while it installed.. would that work, you have to win a game of solitaire to boot your machine.

---

### Post by inportb on 2009-05-30
Well that would suck. How about making the game of pong progressively harder, such that you would *have* to lose by the time the system's all booted?

---

### Post by ktp on 2009-05-30
> **gnomeuser said:**
> I remember that Corel Linux I believe it was let you play solitaire while it installed.. would that work, you have to win a game of solitaire to boot your machine.

:lolflag:

---

### Post by CarpKing on 2009-05-31
Ten seconds is plenty of time to display a bootsplash, and far too long to leave a black screen.  Just count out ten seconds to yourself (preferably with a clock).  It's longer than it sounds like.  A text boot just doesn't fit in the streamlined modern experience that I'm assuming Canonical wants.  Actually, the shorter the boot time, the less useful a text boot becomes, because the information goes by too fast.

---

### Post by taavikko on 2009-05-31
Plymouth would been nice thing to have to give professional looks to boot process in the form of flicker free.

Is the current plan to start services on parallel... ?
To achieve the "fast boot"

doesn't really matter to me is the boot process 10s or 50s
as long as there are more important things beneath, (e.g) battery power consumption on laptops, system not responding after login to desktop for few seconds.

but at this rate of devel, these issues may soon be in the history :)

---

### Post by ad_267 on 2009-05-31
> **gnomeuser said:**
> I remember that Corel Linux I believe it was let you play solitaire while it installed.. would that work, you have to win a game of solitaire to boot your machine.

I always end up playing solitaire while installing Ubuntu. Anyways I quite like the idea of Plymouth, it makes everything look more professional and smooth.

---

### Post by coolen on 2009-05-31
Just a quick reality check:

It wasn't that long ago that booting Ubuntu took well over a minute, often two or more. Now we're discussing ways to get it under ten seconds.

Progress much?

---

### Post by red_team316 on 2009-05-31
plun/autocrosser:
I've downloaded the latest plymouth source with git and found there are several other files included that are not in the PPA. In short, the glowring plugin probably won't work with the PPA package due to API/ABI changes. The only way someone would get it working is to build and install from the latest git source. I tried, but so far haven't had any luck getting it to display any plugin. I can fire up plymouth, but it falls back to the 3-colorbar/text boot.

It might be possible to mod the plugin source enough to get it to work with the PPA packages, but that would be taking a step back rather than moving forward.

I'm really disappointed that Plymouth wont be making it into karmic. The 10-second boot time sounds great and all, but that is a really lame excuse to drop Plymouth. Plymouth is superior to usplash all the way around. What they could have said was "Sorry, but Plymouth development hasn't stabilized enough for us to consider including it at this point in time". Hopefully it is just a delay rather than dropping plymouth altogether.

gnomeuser: plymouth pong should be possible. I certainly wouldn't think anyone would want to hold up the boot process until you win/lose though, more of a play until the boot is done. :P I actually asked whether something like this would even be possible on the mailing list at one point.

---

### Post by MadsRH on 2009-05-31
> **ad_267 said:**
> ...Anyways I quite like the idea of Plymouth, it makes everything look more professional and smooth.

**+1**
Windows 7 will look so smooth and slick, while Ubuntu will look _SO_ outdated :(

10sec or 15sec? Doesn't really matter as long as it's not 60sec

---

### Post by loomsen on 2009-06-01
> **MadsRH said:**
> **+1**
while Ubuntu will look _SO_ outdated :(


It IS outdated.

Using btrfs is a massive step ahead, I'm currently using it on a testsystem (w/o any problems so far, adding disks, removing disks, reallocating files, fsck, shrinkin growing whatever, everything worked in a fractional amount of time compared to ext3 and/or ext4.
Not to mention this all happens while the partition is online and serving as / partition...

I can only enforce everyone to resize some partition and give it a try. Some more testing and I might even consider switching my production OS using btr soon.

However, you'll love the "grow fs up to " feature, at least I do...

---

### Post by Swarms on 2009-06-01
> **loomsen said:**
> It IS outdated.

Using btrfs is a massive step ahead, I'm currently using it on a testsystem (w/o any problems so far, adding disks, removing disks, reallocating files, fsck, shrinkin growing whatever, everything worked in a fractional amount of time compared to ext3 and/or ext4.
Not to mention this all happens while the partition is online and serving as / partition...

I can only enforce everyone to resize some partition and give it a try. Some more testing and I might even consider switching my production OS using btr soon.

However, you'll love the "grow fs up to " feature, at least I do...

Would btrfs be ready to be installed with Karmic as an option? Like ext3 was for Jaunty.

---

### Post by MacUntu on 2009-06-01
This is "The Plymouth Thread", not "The BTRFS Thread". Thanks! ;)

---

### Post by superfoor on 2009-06-01
I have to say as a Fedora User Plymouth is useless wow less flashing on boot. Believe it or not that isn't what i want out of my PC. I don't care if my monitor starts flashing like a strobe If they can get a 10 second boot on karmic.

---

### Post by coolen on 2009-06-01
Not everyone Ubuntu's targeted at feels the same. Some of us would like a flicker-free boot, and others might be less put off by it when considering adopting Ubuntu.

---

### Post by automaton26 on 2009-06-01
I can't be the only one here who disables usplash, and doesn't care about flicker - just give us the fastest boot that's technically possible. This applies to _any_ electronic consumer device.

If 9.10 can do this (and simultaneously make Hibernate irrelevant) then it gets my vote.

---

### Post by TrueTom on 2009-06-01
Flicker DOES slow down the boot process.

---

### Post by loomsen on 2009-06-01
> **TrueTom said:**
> Flicker DOES slow down the boot process.

Very true.

Btw, dmesg, bootlogd and Xorg.log provide a lot of additional information as well (which you might want to make use of)
Further, I use to work a lot in the shell, so running at my native resolution is an enourmous advantage there as well.


> just GIVE us

This is the main issue... You already HAVE the ability to configure it as much as possible to perfectly fit your needs. You can't ask for gold if you want everybody else to win gold as well. 
custom &#8592; - &#8594; generic

If you're just into a short boot time you should be able to achieve the shortest possible, if you prefer restarting your PC once a week this might not be what you want, but rather make sure everything is brought up correctly.

---

### Post by camper365 on 2009-06-18
I think that new users of Ubuntu coming from Windows will have problems with the terminal popping up and think that Ubuntu is poorly designed. In order to get users to stay, they have to see a nice boot splash because appearances matter. If Ubuntu is ever to be displayed, we will have to show a nice bootsplash without flickering.

---

### Post by super.rad on 2009-06-18
> **camper365 said:**
> I think that new users of Ubuntu coming from Windows will have problems with the terminal popping up and think that Ubuntu is poorly designed. In order to get users to stay, they have to see a nice boot splash because appearances matter. If Ubuntu is ever to be displayed, we will have to show a nice bootsplash without flickering.
but what if it boots so fast they'll barely see it, thats the plan for karmic and karmic +1
I'm sure new users would be more impressed if it boots to a fully working desktop in 10 seconds than if it takes 30 seconds but looks pretty

---

### Post by camper365 on 2009-06-18
> **super.rad said:**
> but what if it boots so fast they'll barely see it, thats the plan for karmic and karmic +1
I'm sure new users would be more impressed if it boots to a fully working desktop in 10 seconds than if it takes 30 seconds but looks pretty

If you've been reading the entire thread, you would know that plymouth actually makes boot time shorter because it reduces the flicker and speeds up boot time.

---

### Post by super.rad on 2009-06-18
> **camper365 said:**
> If you've been reading the entire thread, you would know that plymouth actually makes boot time shorter because it reduces the flicker and speeds up boot time.
I have been reading the entire thread, and canonical/ubuntu dev's decided that they could make it boot in 10 seconds without plymouth.
You were saying that Ubuntu should have plymouth as it looks better for new users, I think new users will be more impressed if ubuntu manages to boot to a fully working desktop in 10 seconds than if it looks good while booting.
(personally I would prefer it if it booted in 10 seconds with plymouth but theres always fedora for that)

---

### Post by camper365 on 2009-06-18
> **super.rad said:**
> I have been reading the entire thread, and canonical/ubuntu dev's decided that they could make it boot in 10 seconds without plymouth.
You were saying that Ubuntu should have plymouth as it looks better for new users, I think new users will be more impressed if ubuntu manages to boot to a fully working desktop in 10 seconds than if it looks good while booting.
(personally I would prefer it if it booted in 10 seconds with plymouth but theres always fedora for that)

I think that if we were to add plymouth, it might lower boot time by another 2-3 seconds, so a 7-8 second boot time would be there instead of a 10 second boot time.

---

### Post by robert.rankin.jr on 2009-06-18
Regardless of whether Plymouth will speed or slow the boot process, I do think it's needed. Computers are not moving in the processing power direction, or the efficiency direction -- rather, they move towards aesthetics if they want to go far. Mac's market share is not improving as quickly as it is by improving boot speed. They're making the boot look nice.

I think users, especially new users, would be far more impressed by a 13 second boot that looks beautiful than a 10 second boot that looks like crap. Even better would be a 10 second boot that looks great, or a 7 second boot. One thing we need to understand, though, is that most people are very different than everyone who posts in the Testing forum. They don't care how fast their computer is - they just want it to look cool.

---

### Post by camper365 on 2009-06-18
> **robert.rankin.jr said:**
> Regardless of whether Plymouth will speed or slow the boot process, I do think it's needed. Computers are not moving in the processing power direction, or the efficiency direction -- rather, they move towards aesthetics if they want to go far. Mac's market share is not improving as quickly as it is by improving boot speed. They're making the boot look nice.

I think users, especially new users, would be far more impressed by a 13 second boot that looks beautiful than a 10 second boot that looks like crap. Even better would be a 10 second boot that looks great, or a 7 second boot. One thing we need to understand, though, is that most people are very different than everyone who posts in the Testing forum. They don't care how fast their computer is - they just want it to look cool.

+1
People who are used to Linux don't mind the slight flicker, but any new user will think that showing a text only screen is like BIOS from the 1990s or computers from 1980. It's already the general opinion (at least to the people I've talked to) that Linux is just a tty that you can't do anything with (of course the general opinion is false).

---

### Post by Amaranth on 2009-06-18
Plymouth makes your boot time longer. You're thinking of kernel mode setting. Plymouth was designed to be used with kernel mode setting but you don't have to use one to get the other. The moblin fast boot system (boot to desktop on a netbook in 5 seconds) uses kernel mode setting but does not use plymouth for just this reason.

---

### Post by camper365 on 2009-06-18
> **Amaranth said:**
> Plymouth makes your boot time longer. You're thinking of kernel mode setting. Plymouth was designed to be used with kernel mode setting but you don't have to use one to get the other. The moblin fast boot system (boot to desktop on a netbook in 5 seconds) uses kernel mode setting but does not use plymouth for just this reason.

and is Karmic planning to use kernel mode setting?

---

### Post by BwackNinja on 2009-06-18
> **camper365 said:**
> and is Karmic planning to use kernel mode setting?

KMS isn't exactly all here. Intel KMS works and is in the kernel, R100-R500 KMS works and is going in as a staging driver in linux 2.6.31 and you can get a 2.6.30 kernel with Radeon KMS in a ppa, and Nouveau works but isn't yet into a state to be merged.

---

### Post by coolen on 2009-06-18
If they can leverage KMS, it'd be a step in the right direction. Although I found their last aesthetic addition to Usplash to be kind of ugly. I hate the thin bar with the dark colours. Last splash screen matched my desktop. It felt like part of the system. Then you get to that god-awful login screen...

In short, I don't really trust Ubuntu to make a good-looking boot. If they used Plymouth, it would at least look cool.

---

### Post by novafluxx on 2009-06-19
> **coolen said:**
> If they can leverage KMS, it'd be a step in the right direction. Although I found their last aesthetic addition to Usplash to be kind of ugly. I hate the thin bar with the dark colours. Last splash screen matched my desktop. It felt like part of the system. Then you get to that god-awful login screen...

In short, I don't really trust Ubuntu to make a good-looking boot. If they used Plymouth, it would at least look cool.

I think the new USplash screen is nicer then the previous ones, and I think 9.04's login screen (Ubuntu, not Kubuntu) is very hot looking. IMO of course

---

### Post by coolen on 2009-06-19
They strike me as dark-for-dark's-sake. Dark themes are fine, bit the GDM theme in particular looks like they took an Ubuntu-themed room, then dimmed the lights as far as they could and took a picture.

My main complaint is that it contrasts so heavily with the desktop. The aim is to make the boot process seem like a part of the broader Ubuntu experience, but we have these very dark GDM and Usplash themes taking us to a comparatively light desktop.

Ubuntu's theme has always seemed kind of fun and quasi-cartoonish to me. The pervious Usplash, and, to a lesser extent, GDM, theme just seemed to fit in better with that.

My .02 cents.

---

### Post by camper365 on 2009-06-19
> **coolen said:**
> 
My .02 cents.

don't you mean my 2 cents, or my $.02? I don't think you want to put in a fraction of a cent;).

> **coolen said:**
> 
	 		They strike me as dark-for-dark's-sake. Dark themes are fine, bit the GDM theme in particular looks like they took an Ubuntu-themed room, then dimmed the lights as far as they could and took a picture.

My main complaint is that it contrasts so heavily with the desktop. The aim is to make the boot process seem like a part of the broader Ubuntu experience, but we have these very dark GDM and Usplash themes taking us to a comparatively light desktop.

Ubuntu's theme has always seemed kind of fun and quasi-cartoonish to me. The pervious Usplash, and, to a lesser extent, GDM, theme just seemed to fit in better with that.


I think that if they enabled darkroom by default, it would match well. However, the human theme and the default gdm and usplash theme don't match. I use the darkroom theme, so the default gdm and usplash theme in Jaunty does work for me.

---

### Post by 23meg on 2009-06-19
> **camper365 said:**
> and is Karmic planning to use kernel mode setting?

Yes. It's already working for some drivers.

Refer to [the blueprint detailing the Karmic X plans]("https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-xorg") for more detail.

---

### Post by camper365 on 2009-06-19
> **23meg said:**
> Yes. It's already working for some drivers.

Refer to [the blueprint detailing the Karmic X plans]("https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-xorg") for more detail.

do you know what drivers?

---

### Post by 23meg on 2009-06-19
> **camper365 said:**
> do you know what drivers?

Currently, the Intel driver (possibly not all chipsets). [Radeon]("https://launchpad.net/~xorg-edgers/+archive/radeon-kms") and Nouveau are coming along too, but may not make it to the final Karmic kernel.

---

### Post by camper365 on 2009-07-02
I think I'm seeing KMS in the new kernel (2.6.31-1-generic) :)

There's a few problems when I log in though (I can't see any panels and there are black boxes where I should see startup windows).

---

### Post by Merk42 on 2009-07-02
Is KMS = Plymouth?

If not, has it be decided if Karmic will use Plymouth?  I'm thinking no, but I'd like to know an official word.

---

### Post by taavikko on 2009-07-02
> **Merk42 said:**
> Is KMS = Plymouth?

If not, has it be decided if Karmic will use Plymouth?  I'm thinking no, but I'd like to know an official word.

KMS doesn't equal to plymouth.
Plymouth will not be part of Karmic 9.10.

Not from more official source but will this do?

---

### Post by coolen on 2009-07-03
> **camper365 said:**
> don't you mean my 2 cents, or my $.02? I don't think you want to put in a fraction of a cent;).

If you look at it on paper, they're the same thing...

---

### Post by loomsen on 2009-07-03
> **23meg said:**
> Currently, the Intel driver (possibly not all chipsets). [Radeon]("https://launchpad.net/~xorg-edgers/+archive/radeon-kms") and Nouveau are coming along too, but may not make it to the final Karmic kernel.

LOL.

This _must_ be a joke

>  
* Upcoming technology changes for drivers (KMS, UXA, et al) [color=red]UPCOMING?[/color]
 * What problems will KMS cause and how can we mitigate?
[color=red]WHUT?[/color]
 * Choose xorg version for Karmic  # OK, give this about 2 months

 * Estimate versions for key libraries and video/input drivers 
 * Notable pending merges? [color=red]# --> YES [/color]

 * Involving community in improving support on 8xx Intel hardware
 [color=red]Again you must be joking... KMS for i915 built in, DRM config M for i810,830,910
Obviously the community improved support already  [/color]


What? o.O
>    + Bulletproof-X - ideas for improving?
How about... renaming Ubuntu to Ubuntu7?

---

### Post by RAOF on 2009-07-03
> **loomsen said:**
> LOL.

This _must_ be a joke


I don't see why.  At the time that was written (the start of the Karmic dev cycle), Intel KMS wasn't in mainline, Intel still supported EXA, and UXA would leak kernel memory at a rate of > 100MB/hr.  Given the serious Intel performance regressions in Jaunty, it's not unreasonable to ask what could go wrong this cycle!

Kernel modesetting isn't the most important feature of drivers, and certainly isn't the be-all and end-all of "community support".

Radeon kernel modesetting appears to have made it into 2.6.31.  The nouveau drivers aren't even in the upstream kernel yet, nor are there any concrete plans for their inclusion.

Nouveau will soon "support" kms in Karmic, for values of "support" equal to "you can turn it on, but don't necessarily expect X to work".

---

### Post by kingborel on 2009-07-03
> **loomsen said:**
> LOL.

This _must_ be a joke



What? o.O

How about... renaming Ubuntu to Ubuntu7?

How about you check the date that all of that was posted ;)

EDIT: Damn, beaten by RAOF

---

### Post by loomsen on 2009-07-03
> **RAOF said:**
> I don't see why.  At the time that was written (the start of the Karmic dev cycle), Intel KMS wasn't in mainline, Intel still supported EXA, and UXA would leak kernel memory at a rate of > 100MB/hr.  Given the serious Intel performance regressions in Jaunty, it's not unreasonable to ask what could go wrong this cycle!


Well, I gotta admit I left just after finishing the JJ final due to these statements. 
I was running sidux, fedora, openSuSe factory and bluewhite64 (F11 and bw64 currently)
Each of the above provide at least a 2.6.29 kernel with the _imo_ pretty important features such as KMS and BTRFS. OK, btr is experimental, I agree, however, who isn't able to accept responsibility probably isn't bothering anyway. 
Yet, in those old days I remember F11 had a big testing day and the nouveau module worked very well. 

> Kernel modesetting isn't the most important feature of drivers, and certainly isn't the be-all and end-all of "community support".

I think it is a pretty big step forward, as this is the lowest implementation of DRI access so far, isn't it? I'm not arguing because of a fancier bootsplash but because I'm using the shell rather often. 
Prior, I found it wasn't very handy switching from a graphical RL to a shell and back, ugly flickering, display gets powered off and on again (which isn't prelonging a displays life neither) and sometimes it just totally screwed and blanked out.
All of this has become pretty smooth already, more seamless I'd have ever expected.
Anyway, I see the huge advantage in getting very close to actually usable NoDisk/NoMachine distributed desktops running entirely from RAM. GPM and KMS are the only reasonable way to go at the current state of macroeconomical development. 
_IMHO_ chasing btrfs bugs in order to get it implemented as soon as possible is at least twice as productive as maintaining and supporting a rather unlucky, temporary "enhancement" to ext3... 

As I said, in my humble oppinion the overall gain of getting used to clusterFSs, logFSs, CoWs and such as early as possible will probably succeed the losses due to LTS'ing a rather rough release.
Bummer most users still seem to find "shell" equals a menace2society.

Basically like using vs being abused. My main point when I switched to Linux was the freedom it is offering with the user as the only limit.
JJ however is the first Ubuntu release which constraints my expected freedom in a non tolerable way.
So, besides my HW dependant issues demanding the 2.6.29 release, the above shows my general, economic doubts on Ubuntus way2go if you want it like that.

PLEASE NOTE: This post isn't meant to be destructive, but constructive criticism. Please beware of one-liner-no-brain-flame-posts, this isn't my intention.
Moreover I'm seriously interested in a discussion [SIZE="1"](discutio (-quatio)=interactive investigation, editor's note)[/SIZE]
and the actual reasons why Ubu is heading this way. 
I doubt it's the anticipation of Win7 which is causing this "productional leak based on short-term calculations" (as I'd denote it from my economic point of view)

> The nouveau drivers aren't even in the upstream kernel yet, nor are there any concrete plans for their inclusion.
Well, the 2D infrastructure actually works pretty well. DRI probably won't be achieved in the near future, I agree. This is partly due to nvidia not opening their source, and mainly because the nvidia proprietary driver creates an interface to communicate with the kernel (as opposed to non binary modules the linux kernel usually uses) So obviously nvidias code takes over the part the kernel should play here, so the implementation (= actual code) probably is the result of oligopolistic, rational, economic consideration of a commercial company.
In my eyes, these are enough restrictions, I don't need further artificial restraints.

> 
Nouveau will soon "support" kms in Karmic, for values of "support" equal to "you can turn it on, but don't necessarily expect X to work".
It works, not 2 well tho, you're completely right there. 
But I think I explained my intentions above, not heading towards X, but the other way round...

---

### Post by Slug71 on 2009-07-11
It seems Plymouth could still be a possibility.

[http://www.techradar.com/news/software/operating-systems/koala-will-be-a-definitive-shift-for-ubuntu-linux-613835](http://www.techradar.com/news/software/operating-systems/koala-will-be-a-definitive-shift-for-ubuntu-linux-613835)

---

### Post by inportb on 2009-07-11
Well, it'll come when it comes.

---

### Post by Swarms on 2009-07-11
> **Slug71 said:**
> It seems Plymouth could still be a possibility.

[http://www.techradar.com/news/software/operating-systems/koala-will-be-a-definitive-shift-for-ubuntu-linux-613835](http://www.techradar.com/news/software/operating-systems/koala-will-be-a-definitive-shift-for-ubuntu-linux-613835)

My fingers remain crossed!

---

### Post by wayne_cat on 2009-07-11
> **Slug71 said:**
> It seems Plymouth could still be a possibility.

[http://www.techradar.com/news/software/operating-systems/koala-will-be-a-definitive-shift-for-ubuntu-linux-613835](http://www.techradar.com/news/software/operating-systems/koala-will-be-a-definitive-shift-for-ubuntu-linux-613835)

Well ... let's have a look at the article ...

- Plymouth ... maybe yes ... maybe no
- a "brown" Koala ... maybe yes ... maybe no 

But ... even if we don't get Plymouth ... there is a minimal chance to get GNU hurd :biggrin:

---

### Post by inportb on 2009-07-11
> **coolen said:**
> [QUOTE=camper365;7485961][QUOTE=coolen;7484330]My .02 cents.don't you mean my 2 cents, or my $.02? I don't think you want to put in a fraction of a cent;).[/QUOTE]If you look at it on paper, they're the same thing...[/QUOTE]

LOL good one
[http://www.youtube.com/watch?v=zN9LZ3ojnxY](http://www.youtube.com/watch?v=zN9LZ3ojnxY)

---

### Post by Slug71 on 2009-07-11
> **Swarms said:**
> My fingers remain crossed!

As are mine. :p

> **wayne_cat said:**
> Well ... let's have a look at the article ...

- Plymouth ... maybe yes ... maybe no
- a "brown" Koala ... maybe yes ... maybe no 

But ... even if we don't get Plymouth ... there is a minimal chance to get GNU hurd :biggrin:

Well, parts of GNU Hurd.

---

### Post by Merk42 on 2009-07-11
I've learned not to believe things Mark Shuttleworth says...

---

### Post by ktp on 2009-07-11
everything that is said is maybe yes maybe no.  Seems like the perfect answer for everything :lolflag:

---

### Post by wayne_cat on 2009-07-11
> **ktp said:**
> everything that is said is maybe yes maybe no.  Seems like the perfect answer for everything :lolflag:

Right ... and he did not say "*I have never had sexual relations with Monica Lewinsky*"

So ... no lies and no risqué scandal :-(

---

### Post by Slug71 on 2009-07-27
Surely there must be some news on this now? Its not too long till Feature Freeze and MadsRH has made some pretty cool ideas to be considered so far.

---

### Post by Amaranth on 2009-07-27
As far as I know the plan is still to not have any bootsplash in 10.04 so there will be no work done on Plymouth in Ubuntu.

---

### Post by RJ12 on 2009-07-28
I just wanted to ask why is Plymouth not going to find its way into Karmic I was really sad to here it isnt comming?:(:confused:

---

### Post by LiquidMeson on 2009-07-28
I believe the Ubuntu Team is working on making it load up to gdm so fast there will be no time for a fancy boot screen. Having plymouth may look nice, but wouldn't it be better to have no loading screen at all?

---

### Post by Swarms on 2009-07-28
> **LiquidMeson said:**
> I believe the Ubuntu Team is working on making it load up to gdm so fast there will be no time for a fancy boot screen. Having plymouth may look nice, but wouldn't it be better to have no loading screen at all?

Let's cross that imaginary bridge when we get there. :)

Nah I am sure we will get there, but this instant?

---

### Post by psyke83 on 2009-07-28
Honestly folks, starting duplicate threads is simply a waste of time. Look [here]("http://ubuntuforums.org/showthread.php?t=1140697").

---

### Post by LiquidMeson on 2009-07-28
Some Compiled info for your viewing pleasure.
Btw, one of the cool main features of plymouth, kms. Will and already is implemented in Karmic (for amd and intel graphics cards)
As well as some new x-server features such as no root startup are on there way.

[http://anotherubuntu.blogspot.com/2009/06/shiny-and-flicker-free-boot-experience.html](http://anotherubuntu.blogspot.com/2009/06/shiny-and-flicker-free-boot-experience.html)

[https://wiki.ubuntu.com/Artwork/Incoming/Karmic/Boot](https://wiki.ubuntu.com/Artwork/Incoming/Karmic/Boot)

[https://blueprints.launchpad.net/ubuntu/+spec/karmic-boot-experience](https://blueprints.launchpad.net/ubuntu/+spec/karmic-boot-experience)

So they are getting rid of usplash, and won't have plymouth. Pretty trippy stuff when you look in to it. Ubuntu is charting a new path.

---

### Post by Slug71 on 2009-07-29
> **LiquidMeson said:**
> Some Compiled info for your viewing pleasure.
Btw, one of the cool main features of plymouth, kms. Will and already is implemented in Karmic (for amd and intel graphics cards)
As well as some new x-server features such as no root startup are on there way.

[http://anotherubuntu.blogspot.com/2009/06/shiny-and-flicker-free-boot-experience.html](http://anotherubuntu.blogspot.com/2009/06/shiny-and-flicker-free-boot-experience.html)

[https://wiki.ubuntu.com/Artwork/Incoming/Karmic/Boot](https://wiki.ubuntu.com/Artwork/Incoming/Karmic/Boot)

[https://blueprints.launchpad.net/ubuntu/+spec/karmic-boot-experience](https://blueprints.launchpad.net/ubuntu/+spec/karmic-boot-experience)

So they are getting rid of usplash, and won't have plymouth. Pretty trippy stuff when you look in to it. Ubuntu is charting a new path.

Honestly the stuff MadsRH has come up with are way better than the mock-ups in that wiki.

---

### Post by gnomeuser on 2009-07-29
* removed *

---

### Post by coolen on 2009-07-29
That is undoubtedly a lot of cool ideas. Running the splash screen on X will be awesome, but I wonder how it will go without KMS. I'm running on Nvidia hardware, and I know I'm not in a minority.

If we can't get support, I hope there's at least a good fallback.

---

### Post by gnomeuser on 2009-07-29
> **coolen said:**
> That is undoubtedly a lot of cool ideas. Running the splash screen on X will be awesome, but I wonder how it will go without KMS. I'm running on Nvidia hardware, and I know I'm not in a minority.

If we can't get support, I hope there's at least a good fallback.

Nouveau already does KMS on the GeForce series 8 cards, it should soon be able to present a fine solution for you poor nvidia owners.

The proprietary driver is never going to support KMS, that would make it a derived product of the kernel and such subject to the GPLv2 something nvidia wants to avoid at all cost. 

For now nvidia owners being the odd man out now of the major cards, are likely to have to have a vesa or text fallback till nouveau can be installed reliably on all setups by default (if you opt-in to nvidias own stupidity afterwards then you are naturally on your own).

---

### Post by coolen on 2009-07-29
In that case, I wonder how difficult it is to install Plymouth in Ubuntu...

---

### Post by ronacc on 2009-07-29
with the current 18 sec boot time grub to DT I really don't get so bored that I need fancy graphics to entertain me :lolflag:

---

### Post by PmDematagoda on 2009-07-29
> **coolen said:**
> That is undoubtedly a lot of cool ideas. Running the splash screen on X will be awesome, but I wonder how it will go without KMS. I'm running on Nvidia hardware, and I know I'm not in a minority.

If we can't get support, I hope there's at least a good fallback.

There is a text fallback for when there isn't any KMS available, but it simply does not compare to the full Plymouth experience with KMS.

---

### Post by coolen on 2009-07-29
> **PmDematagoda said:**
> There is a text fallback for when there isn't any KMS available, but it simply does not compare to the full Plymouth experience with KMS.

I don't think that really counts as a good fallback.

Many may say that, with such a fast boot, it's a small issue, but so is a little flicker. If they're concerned with making Ubuntu look professional, how does having a significant proportion of machines fall back to text mode fit in?

---

### Post by Regenweald on 2009-07-29
I guess it's a matter of opinion. To me the text mode is professional and plymouth is just pretty. I don't need pretty at boot, i much prefer to see what is loading and what may have failed real-time.

---

### Post by PmDematagoda on 2009-07-29
> **coolen said:**
> I don't think that really counts as a good fallback.

Many may say that, with such a fast boot, it's a small issue, but so is a little flicker. If they're concerned with making Ubuntu look professional, how does having a significant proportion of machines fall back to text mode fit in?

I agree, I didn't like that text mode much either, which was why I leap frogged from F9 to F11 where Plymouth did work full blast for me.

The main thing here is KMS, if KMS works then Plymouth can give you the full, slick experience, now some drivers that are KMS-ready or nearing good KMS support are the Intel and open source ATi drivers, nouveau is also getting there, but it still may take a while and one cannot be sure of a date, but it certainly is moving. Ideally, if it could be done, hardware where KMS is possible can run Plymouth but non-KMS hardware could run usplash instead as a fallback, but you need people to work on that and it could be harder than one thinks.

---

### Post by coolen on 2009-07-29
@Regenweald

I respect that, but that's not what we're going for. We're going for a pretty boot, flicker free, fast, good looking.

Unless at least three people in this thread are mistaken, they're reneging on that for every user with a Nvidia card.

---

### Post by amano on 2009-07-29
The new Ubunu startup design has no place for a classic bootsplash since it will try to bring up x as soon as possible (and show off some animation directly in X).

As a fallback usplash will be used (when X is delayed for some reason).

But Colin Watson's new quickboot concepts omits the classic bootsplash by design.

---

### Post by MacUntu on 2009-07-29
> **coolen said:**
> We're going for a pretty boot, flicker free, fast, good looking. [...] they're reneging on that for every user with a Nvidia card.

KMS just helps to top off the boot experience. The absence of KMS doesn't mean that the process has to be ugly or slow.

---

### Post by Regenweald on 2009-07-29
> **coolen said:**
> @Regenweald

I respect that, but that's not what we're going for. We're going for a pretty boot, flicker free, fast, good looking.

Unless at least three people in this thread are mistaken, they're reneging on that for every user with a Nvidia card.

Don't get me wrong though, I like a good looking boot, but I'm one of the binary blob guys so the first time i dropped to text, WTF, came to mind. I've since come to love and depend on a text boot.

I can't wait for an acceptably complete noveau, think with the next kernel, rather than compiling 190.** i'll put noveau on. Development seems to be blazing anyway.

---

