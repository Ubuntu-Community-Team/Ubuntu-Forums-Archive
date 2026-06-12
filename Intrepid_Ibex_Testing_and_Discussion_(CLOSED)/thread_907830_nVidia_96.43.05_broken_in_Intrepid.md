---
title: "nVidia: 96.43.05 broken in Intrepid"
date: 2008-09-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by dawynn on 2008-09-01
I know there's a few other threads open generic to nVidia issues.  But the ones I was seeing dealt with general nVidia issues, or issues specific to the later nVidia glx modules (e.g., 173).

My beef is specific to the 96.43.05 module.  My experience:

Athlon Classic (Thunderbird) 1.4 Ghz machine.  Using an nVidia FX 5700LE card.  

The card itself should be supported under the 173.14.12, according to nVidia.  This module works, somewhat.  I at least have basic video.  But if I try to run anything with 3D, I get a message indicating that this glx needs SSE instructions, which were not available in the Athlon Classic.  Fine.  On my Hardy system, I can't use the nvidia-glx-new module because of messages indicating "invalid instruction".  So, probably the same issue.

But on Hardy, the nvidia-glx module works fine for the purposes I need it for.  I can run Neverwinter Nights without graphics issues.  So, I'm OK with just the 96.43.05 module (Hardy's nvidia-glx).

But I cannot for the life of me get the 96.43.05 module to work in Intrepid.  Odd.  Its not a general nvidia issue -- I can get basic video working with 173.14.12.  I just can't get 96.43.05 working.

Any ideas why the 96 module is causing problems in Intrepid, but not Hardy?

---

### Post by Nullack on 2008-09-01
Not sure if that driver has been patched to work with .27

---

### Post by Elfy on 2008-09-03
I don't think there has been any change since I read this on alberto milone's blog [http://albertomilone.com/wordpress/](http://albertomilone.com/wordpress/)

> The xserver was updated to version 1.5, which broke the ABI compatibility. As a result, drivers 96 and 71 (and fglrx) dont&#8217; work with the new xserver and unfortunately the -IgnoreABI option of Xorg doesn&#8217;t solve the problem. This is something that only NVIDIA can solve. (177 and 173 work well) 

I'm in the same boat - and there are some in similar on the nvidia site

---

### Post by dawynn on 2008-09-11
So, are the folks at Ubuntu preparing a proper October release press statement?

"Ubuntu 8.10 -- Intrepid Ibex is Out!  Ubuntu moving forward: no longer supporting legacy hardware!"

Sorry, went into a bit of panic mode there.  But if we mandate depending on others to fix our problems, then we might as well print something like the above when we put out the next release.

Let's be frank.  Many of us (not all, granted) use Linux to keep life flowing through older computers.  When our favorite distros stop supporting the older hardware, we're stranded.  Those who have either older nVidia cards, or motherboards that do not support SSE instructions (my Athlon Thunderbird, 1.4ghz machine does not support SSE) must use the older nVidia drivers, and we still want to have full opengl support.

Now, we're under a bit of a timeline.  Let's take a look:
Dapper Drake (latest Kubuntu LTS release) expires June 2009 (Desktop)
Hardy Heron (latest LTS for everyone else)
    LTS version expires April 2011.
    KDE version evidently expires October 2009.

So, for Kubuntu, the game is up next year, if we don't come out with some viable alternative.  They will no longer have a supported Ubuntu release that works with older hardware.

Here's the solutions we can either create or wait to see created:

1) nVidia may decide to support their legacy products and put out a version that is compatible with the latest Xorg server.  Have we seen any indication yet that nVidia plans to do this?  I personally am uncomfortable with relying on an outside company that has no business incentive to change their legacy drivers.

2) The nouveau project may see some major breakthroughs.  Personally, I tried the nouveau driver, and couldn't even get basic 2D functionality to work.  And that's something that the nv driver already had under control.  This solution is more in line with open source architecture, but again, we're relying on another project to provide a solution.

3) Change xorg to support legacy nVidia drivers.  A thought -- but I have a feeling that the xorg folks won't be too happy about taking steps backward.

4) Support an alternate version of Xorg for legacy hardware.  I'm not sure how this would all play out, but this may arguably be *the* solution that Ubuntu can implement to attack this problem.  Instead of waiting on other companies or projects to provide a working solution, we could allow for a user to install either the new xorg or an "xorg-legacy" that would be compatable with the legacy nVidia drivers.

As things stand, we have a month to go before Intrepid releases.  Instead of planning statements about why people just messed up their system by trying to install Intrepid on legacy hardware, I would think we could allow for alternate xorg choices that would allow Intrepid to work on the same architectures that Ubuntu has always supported.  This is a choice that Ubuntu can make, without any changes from other projects.

I still like my games, but I'm not ready to purchase a new PC.  I use Linux because, until this time, it supported my technology choices.  I've enjoyed following the Ubuntu release schedule, but unless one of these organizations budges, I won't be able to be "Intrepid".

---

### Post by RAOF on 2008-09-11
> **dawynn said:**
> So, are the folks at Ubuntu preparing a proper October release press statement?

"Ubuntu 8.10 -- Intrepid Ibex is Out!  Ubuntu moving forward: no longer supporting legacy hardware!"

Sorry, went into a bit of panic mode there.  But if we mandate depending on others to fix our problems, then we might as well print something like the above when we put out the next release.
...

In fact, we *don't* suggest depending on others to fix our problems.  We go to a fair bit of effort to tell people that are using the binary drivers that we can't fix them!

> **dawynn said:**
> 
1) nVidia may decide to support their legacy products and put out a version that is compatible with the latest Xorg server. Have we seen any indication yet that nVidia plans to do this? I personally am uncomfortable with relying on an outside company that has no business incentive to change their legacy drivers.

Then, basically, you should have bought ATI.  I know that's not helpful at this point, but there it is.  nVidia have never had open-source 3d support, ATI has.

> **dawynn said:**
> 
2) The nouveau project may see some major breakthroughs. Personally, I tried the nouveau driver, and couldn't even get basic 2D functionality to work. And that's something that the nv driver already had under control. This solution is more in line with open source architecture, but again, we're relying on another project to provide a solution.

We're *always* relying on another project to provide a solution.  That's (essentially) all we do - we aggregate the solutions that upstream projects have developed, and integrate them so they work together in a (hopefully) cohesive whole.  The problem with proprietary drivers is not that the solution comes from an external project - it's that we have no ability to make even trivial fixes (and this would be, and has been, trivial for an open-source driver!).

With a full-time developer or two, I'd be confident that nouveau could become a useful 3d driver in a year or so.  It should work with 2d for you now; if it doesn't, filing a bug on their bugzilla (freedesktop.org bugzilla, project xserver, component driver/nouveau) would be useful.

> **dawynn said:**
> 
4) Support an alternate version of Xorg for legacy hardware. I'm not sure how this would all play out, but this may arguably be *the* solution that Ubuntu can implement to attack this problem. Instead of waiting on other companies or projects to provide a working solution, we could allow for a user to install either the new xorg or an "xorg-legacy" that would be compatable with the legacy nVidia drivers.


While this is technically possible, it's an awful, awful lot of work.  You'd get an old, buggy, xserver.  Which wouldn't support features that the newer software in Intrepid depends upon.  It would be a maintenance nightmare.

Yes, it sucks that nvidia hasn't released a driver that supports your hardware and the new X server, although I fully expect them to.  Basically, thems the breaks.  Proprietary drivers suck.

If you have nvidia hardware not currently supported, and need 3d support, stay on Hardy until nvidia support your hardware again.  While we could do something about this (munging in an old video ABI into our Xserver, keeping an old Xserver around), it would be such a monumental effort that I'd be surprised if we did.

---

### Post by alienexplorers on 2008-09-11
Tried installing the 96.43.07 and it came back with an error about not finding xorg kernel.  Then it tried to build one and it then spit up another message stating it could not set up xorg kernel.

---

### Post by obx-jdt on 2008-09-12
> **RAOF said:**
> In fact, we *don't* suggest depending on others to fix our problems.  We go to a fair bit of effort to tell people that are using the binary drivers that we can't fix them!



Then, basically, you should have bought ATI.  I know that's not helpful at this point, but there it is.  nVidia have never had open-source 3d support, ATI has.


We're *always* relying on another project to provide a solution.  That's (essentially) all we do - we aggregate the solutions that upstream projects have developed, and integrate them so they work together in a (hopefully) cohesive whole.  The problem with proprietary drivers is not that the solution comes from an external project - it's that we have no ability to make even trivial fixes (and this would be, and has been, trivial for an open-source driver!).

With a full-time developer or two, I'd be confident that nouveau could become a useful 3d driver in a year or so.  It should work with 2d for you now; if it doesn't, filing a bug on their bugzilla (freedesktop.org bugzilla, project xserver, component driver/nouveau) would be useful.



While this is technically possible, it's an awful, awful lot of work.  You'd get an old, buggy, xserver.  Which wouldn't support features that the newer software in Intrepid depends upon.  It would be a maintenance nightmare.

Yes, it sucks that nvidia hasn't released a driver that supports your hardware and the new X server, although I fully expect them to.  Basically, thems the breaks.  Proprietary drivers suck.

If you have nvidia hardware not currently supported, and need 3d support, stay on Hardy until nvidia support your hardware again.  While we could do something about this (munging in an old video ABI into our Xserver, keeping an old Xserver around), it would be such a monumental effort that I'd be surprised if we did.

Perhaps you could leave the old xserver in the repositories for those of us that use older hardware. Or we could find another distro that still keeps in line with the Linux simplicity...
Maybe this is why Linus Torvalds doesn't use (K)Ubuntu....:lolflag:
As far as "Maybe you should have bought an ATI card" goes, Linux and ATI didn't like to play together till AMD bought ATI. Kind of a crappy/smart-*** reason/comment!
 I've been using (K)Ubuntu since 5.04, but if this is how you plan to handle issues (telling users they bought the wrong hardware), then another distro might be the correct choice.
[DreamLinux]("http://www.dreamlinux.com.br/") looks promising...

---

### Post by inportb on 2008-09-12
Well, how else are they supposed to handle it? They cannot fix bugs in proprietary software, and they cannot let proprietary software slow their progress.

---

### Post by RAOF on 2008-09-12
> **obx-jdt said:**
> Perhaps you could leave the old xserver in the repositories for those of us that use older hardware.

We could do that, yes.  But I'd guess that you'd probably like some input drivers built against it, so that means we'd need to duplicate all the driver packages, too.  Then we need to make sure that none of our packages fail to work without the new features in the new X server.  And backport fixes to the old server, and it's basically a huge amount of work that would be really, really frustrating because if only nvidia had open source drivers this would require a **rebuild** - not even any source changes - to fix.

Don't expect any developer to be wild about the idea of supporting an entirely parallel, *obsolete*, Xorg system.

> **obx-jdt said:**
> 
 Or we could find another distro that still keeps in line with the Linux simplicity...

I'm not entirely sure what you mean by "simplicity" here, given that you're proposing a tremendously complicated solution ;).

Of course, you can stay on Hardy until nvidia supports the new X server.  Or you can try another distribution.  As far as I'm aware, Ubuntu has the best support for non-free drivers of the major distributions (Fedora for example doesn't even have the driver in their repositories).

> **obx-jdt said:**
> 
As far as "Maybe you should have bought an ATI card" goes, Linux and ATI didn't like to play together till AMD bought ATI. Kind of a crappy/smart-*** reason/comment!

Yeah.  It wasn't meant to be entirely serious.  Of course, if you *really* wanted good support you'd've bought Intel.  Although not if you wanted to play cutting-edge games.  ATI has had open-source 3d support (for oldish cards, admittedly) in the radeon drivers for quite some time, though, which could have influenced the decision.

Perhaps what I really meant was:
> 
I personally am uncomfortable with relying on an outside company that has no business incentive to change their legacy drivers.
This was the situation *at the moment you bought the card* (even if you weren't aware of it).  It shouldn't come as a huge surprise.  It sucks that (until recently) there wasn't a high-performance option which *doesn't* lock you into hoping a company with little incentive to update your drivers does so.

I should probably say that I fully expect nvidia to release 96 and 78 series drivers that support Xserver 1.5, just as I expect ATI will release a fglrx driver supporting 1.5.

You're welcome to try other distros.  But I'd be amazed if you could find a distro which is prepared to maintain two different versions of X.  Maintaining *one* version of X is work enough!

---

### Post by Elfy on 2008-09-12
> **forestpixie said:**
> I don't think there has been any change since I read this on alberto milone's blog <snip>I'm in the same boat - and there are some in similar on the nvidia site

mmmm... well I probably wouldn't have posted this if I thought it was going to cause an argument.

It was obvious to me where the problem lay and so I posted so.

As is the fix - don't install Intrepid until it does work, after nvidia have fixed the problem with their hardware.

Personally I'm expecting it to be fixed eventually, if it isn't before release there are going to be many threads I think :D

Who actually reads the caveats on the release page :) (no that this was there when I last looked)

---

### Post by Who on 2008-09-12
> **forestpixie said:**
> I don't think there has been any change since I read this on alberto milone's blog [http://albertomilone.com/wordpress/](http://albertomilone.com/wordpress/)

 

I'm in the same boat - and there are some in similar on the nvidia site
From the blog "

The xserver was updated to version 1.5, which broke the ABI compatibility. As a result, drivers 96 and 71 (and fglrx) dont’ work with the new xserver and unfortunately the -IgnoreABI option of Xorg doesn’t solve the problem. This is something that only NVIDIA can solve. (177 and 173 work well)

"

Me too.

I think perhaps we should email nVidia about this. The only time I emailed nvidia with a driver bug, they got back to me within 24 hours and were really helpful. Real people read the linux-bugs thingy, and this IS a linux bug - so we should report it.

[email]linux-bugs@nvidia.com[/email]

BUT PLEASE:

Be polite. Don't SPAM, just report your bug!

EXPLAIN the problem, your hardware, etc, ask NICELY for a solution, or ask when one will be available. Remember they're Engineers paid to do a job and they're probably doing the best they can in the corporate framework they're in. (I'd guess the folks that write the driver would love to OS it but some legal team somewhere thinks otherwise...)

So, start up your email apps. They did promise a solution to Fedora 9 users a while back.

---

### Post by dawynn on 2008-09-12
And that was my basic point.  If nVidia does not fix the problem (which is the solution we're relying on), we're going to have a lot of people asking why we released when the older nVidia cards are known to not work.  A *lot* of frustrated people, spewing out a lot of forum posts and bugs.

I personally was not offended by RAOF's original respose, only because it was in keeping with the tone of my response.

I would however encourage a change to the page that RAOF lists in his signature.  He has a link to a PPA that has packages to test the nouveau drivers.  For those not in the know, nouveau is attempting to replace the nv drivers with open-source drivers that *fully* support nVidia cards -- including 3D.  (Project in progress, 3D part not implemented yet)

I included the repository listed and tried to add in the nouveau drivers.  That won't work directly.  I had to do some more searching to find out how to handle these packages.  There was another forum post that gave these instructions:

sudo aptitude install drm-modules-source module-assistant
sudo module-assistant auto-install drm-modules
sudo aptitude install xserver-xorg-video-nouveau

It would be nice to have these simple instructions included on the page announcing the PPA.

---

### Post by alienexplorers on 2008-09-12
96.43.07 is out and still does not work correctly withkernel 2.6.27-3-generic.....

---

### Post by Elfy on 2008-09-12
> I think perhaps we should email nVidia about this.I did in fact start to do so - but when I read this and couldn't get it to work didn't bother, the thinking being that it was just an excuse to not bothere - if you follow my drift..

> When emailing [email]linux-bugs@nvidia.com[/email], please attach an nvidia-bug-report.log, which is generated by running "nvidia-bug-report.sh".

However, perhaps I should just do so and will :)

Further I has more or less given up on intrepid because of the nvidia thing, it being one of 2 bugs I actually had, the other having now- other than the shutdown which appeared at the time to be more or less universal.

I will now perhaps have another go and try the nouveau driver, I am likely to be put off by the lack of 3d - all I actually use the nvidia driver for is to get a tv out working..

---

### Post by RAOF on 2008-09-12
> **dawynn said:**
> ...

I would however encourage a change to the page that RAOF lists in his signature.  He has a link to a PPA that has packages to test the nouveau drivers.  For those not in the know, nouveau is attempting to replace the nv drivers with open-source drivers that *fully* support nVidia cards -- including 3D.  (Project in progress, 3D part not implemented yet)
...

That's a good point; I've updated my signature to point to the nouveau wiki page about those packages.

Some of the 3d part is implemented, but it's not complete enough for anyone to want bugs or feedback other than "mm, it works, cool".

---

### Post by angel.ramirez.isea on 2008-09-16
Bummer. I used to recommend nVidia for all the systems I assembled/sold. Now I know better.

Thanks for the insight, RAOF.

I will email nVidia, anyway.

---

### Post by Elfy on 2008-10-03
Update on the legacy driver, quote from the nvidia forums today - 

> I know many users have been waiting for updated legacy drivers for a while, and I can only assure you that I am working on them.

---

### Post by obx-jdt on 2008-10-09
> **forestpixie said:**
> Update on the legacy driver, quote from the nvidia forums today -

Holy tits!!!:mad: I just tried to summit a novel about this Nvidia issue, just to find out I didn't have "No Script" set right for this forum, and lost my novel...
Now I'll put it in a nutshell. Win-2000Pro still supports my system, but Linux doesn't? What's wrong with this picture??? When will this issue be resolved?

---

### Post by RAOF on 2008-10-09
On a similar note, Ubuntu 8.04.1 still supports your system.

The problem will be resolved when nvidia deign to release a driver that supports Intrepid.  Welcome to the wonderful world of proprietary drivers.  This is why we say things like
[quote=Hardware Drivers]
Proprietary drivers do not have public source code that Ubuntu developers are free to modify.  They represent a risk to you because they are only available on the types of computer chosen by the manufacturer, and security updates to them depend solely on the responsiveness of the manufacturer.  Ubuntu cannot fix or improve these drivers.
[/quote]
before we let you install one of them :).

---

### Post by shane19174 on 2008-10-20
I've got an old laptop that needs the 96 series driver, and I don't want to hold my breath waiting. I know I could stick with Hardy, but I have other reasons for moving to Intrepid...if I can get graphics working reasonably! I don't need (and I don't think my machine would support) 3D, so I was thinking about trying the nouveau drivers. I read this up above: 

> I included the repository listed and tried to add in the nouveau drivers. That won't work directly. I had to do some more searching to find out how to handle these packages. There was another forum post that gave these instructions:

sudo aptitude install drm-modules-source module-assistant
sudo module-assistant auto-install drm-modules
sudo aptitude install xserver-xorg-video-nouveau

It would be nice to have these simple instructions included on the page announcing the PPA.

My question: is this complete? Will this automatically remove the patched 96.43.07 driver I downloaded and installed from nvidia's website (that doesn't really work, of course)? Any thing else I need to bear in mind?

Thanks in advance,
Shane

---

### Post by Elfy on 2008-10-20
You also need to add the nouvea driver to xorg 

```
gksudo gedit /etc/X11/xorg.conf
```

> Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nouveau"

My card allows for a resolution of 1152x864 with the nv driver, if that is sufficient for your laptop I would try that first before the nouveau driver.

If it is possible I would make a new partition for intrepid and dual boot hardy and intrepid to make sure that it doesn't cause any showstoppers

---

### Post by shane19174 on 2008-10-20
Forestpixie, thanks for the helpful reply. Just to clarify: is 1152x864 the maximum possible with nv, or just the max on your equipment? If I recall correctly, the old laptop is designed for 1280x1024. Do you still think I should try nv first?

And here's the really stupid question: how do I install the nv driver?

Thanks again,
Shane

---

### Post by Elfy on 2008-10-20
nv is installed - just add the driver to xorg and it should fire up ok- as above replace nouveau with nv

I have 2 xorg's myself - one for when I get fedup with nouveau

1152x is the maximum for me with nv

I would try nv first if thta's ok for you then use it, you won't get 3d with either so nothing lost there.

In fact if I could higher resolution I would probably just stay with nv for ever not using the tvout nor 3d.

Good luck

---

### Post by shane19174 on 2008-10-20
Thanks again. I'll give it a try when I get the chance.
Shane

---

### Post by Aearenda on 2008-10-20
I am using the nouveau driver with a Geforce4 on my laptop because I need to use an external display, and nv won't do that. I did not have the patched Nvidia driver installed, so I can't comment on whether it is automatically removed. The installation went smoothly following the instructions as quoted above. 

I find nouveau slower than the proprietary driver on Hardy (not surprisingly) and it won't standby or hibernate for me; but it is easy to control from the command line for quick internal/external switching, and works fine at 1280x1024.

---

### Post by kindofabuzz on 2008-10-23
So are they fixed yet?

---

### Post by FuturePilot on 2008-10-23
> **kindofabuzz said:**
> So are they fixed yet?

No :(

---

### Post by wildmanne39 on 2008-10-23
Hi I have a nvidia card in my hp laptop, it was working fine until I started changing my display settings. After boot I get a white screen. I am using kubuntu 8.10 can anyone tell me how to change my display settings when my computer is booting up? Thanks in advance.

---

### Post by FuturePilot on 2008-10-23
> **wildmanne39 said:**
> Hi I have a nvidia card in my hp laptop, it was working fine until I started changing my display settings. After boot I get a white screen. I am using kubuntu 8.10 can anyone tell me how to change my display settings when my computer is booting up? Thanks in advance.

That sounds like a different issue, you might want to start a new thread about that, you will probably get more help that way.

---

### Post by gaspard.leon on 2008-10-23
How to install the Nouveau driver:
[http://nouveau.freedesktop.org/wiki/UbuntuPackages](http://nouveau.freedesktop.org/wiki/UbuntuPackages)

I found it works pretty good but it's still under development so don't expect miracles...

The main reason I'm still using nvidia (173 binary) is for the suspend/hibernate support (when "Option" "NvAGP" "0" is specified.)

Using AGP 5900XT card with Athlon XP

---

### Post by jcottier on 2008-10-24
So which ATI card are we suppose to choose so it will definitely work? The Ubuntu hardware database says:-

"Note: Most nVidia-cards will work if you just install the nvidia-glx ("nvidia-glx-legacy" for older cards) package, and run this command: "sudo nvidia-glx-config enable"

Note: For most 3D requirements the system will work, but slowly unless you install the binary driver for your video card. See the BinaryDriverHowto for information on how to install binary drivers for your video card. This is true for at least ATI, NVIDIA and 3DLabs cards."

So which model of ATI card is actually going to work?, and why is nvidia still mentioned first. I cant see anything suggesting ATI is better here.

This is getting really frustrating for me. My work PC (Nvidia Geforce 7300) has lost 3D drivers on Gutsy and Hardy, my home PC (Nvidia Geforce 2 MX400) lost 3D drivers on Hardy (bugs were filed) and now what?

If its now our fault for choosing the wrong make of card or its too old?, and the only way to fix it is to buy another one? If that true then lets at least see some clear and well published information on what to choose. Personally I am rapidly losing faith here.

---

### Post by Elfy on 2008-10-24
This thread was written about an nvidia card and an nvidia issue so why would I be asking for information for an ati one?

I've never used an ati card and haven't looked at such threads so unfortunately I can't even point you in the right direction :(

As far as nvidia go then I assume that eventually all their cards will be 'legacy' and plagued with the same issue. I don't know what the deal is with ati but I was under the impression it was getting better, but I'm not sure...

---

### Post by shane19174 on 2008-10-24
I don't know how much trust we should put into this, but I haven't seen anyone comment on this remark made Monday (Oct 20) by "zander" from nvidia corp.:

> We hope to release an updated 96.43.xx driver with support for Linux 2.6.27 and X.Org server 1.5 in the near future.

For the sake of completeness, here's the rest of the thread at nvidia Linux forums: [http://www.nvnews.net/vbulletin/showthread.php?t=121444]("http://www.nvnews.net/vbulletin/showthread.php?t=121444"). As you'll see, though, there's no other info to go on.

We'll see....

Shane

---

### Post by Elfy on 2008-10-24
Well it's better than the last one I saw - "I'm not allowed to give estimates" - too a how much longer question ;)

---

### Post by ewproctor on 2008-10-24
All I know is I was downloading and then read:

nVidia "legacy" video support

The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration.

Users of other nVidia chipsets that are supported by the 173 or 177 driver series will be transitioned to the nvidia-glx-173 or nvidia-glx-177 package instead. However, unlike drivers 96 and 71, drivers 173 and 177 are only compatible with CPUs that support SSE (e.g. Intel Pentium III, AMD Athlon XP or higher). Systems with older CPUs will also be transitioned to the nv driver on upgrade. 

And promptly stopped downloading.  I am considering Mandriva's newest to try it out in the meantime.

---

### Post by Elfy on 2008-10-24
Well I am just goig to wait it out, at least hardy is lts and is more or less fine for me.

I do use intrepid but the problems I'm getting with nouveau make it a bit unresponsive for me so it drives me away.

---

### Post by wildmanne39 on 2008-10-24
> **FuturePilot said:**
> That sounds like a different issue, you might want to start a new thread about that, you will probably get more help that way.
Hi, thank you for your suggestion I will try that I am just know figuting out how to leave messages and find replies to them.

---

### Post by nanog on 2008-10-24
> My work PC (Nvidia Geforce 7300) has lost 3D drivers


My geforce 7300 card worked fine in hardy with the nvidia 173 driver. It works even better with 177 in intrepid.

---

### Post by Elfy on 2008-10-25
> While I can't promise that it'll be released before Ubuntu 8.10 comes out, we *are* working on it. [http://www.nvnews.net/vbulletin/showthread.php?t=116555](http://www.nvnews.net/vbulletin/showthread.php?t=116555)

Just chucked this on the end as it appears people are looking here.

---

### Post by dspiteri on 2008-10-25
Moral of this story: Proprietary solutions leave you at the mercy of someone else. Hardy still has 2.5 years of support left, if you're still using a geforce4 in 2011 I'd say you got your money's worth.

---

