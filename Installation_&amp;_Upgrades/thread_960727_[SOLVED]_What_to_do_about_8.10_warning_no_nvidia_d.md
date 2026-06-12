---
title: "[SOLVED] What to do about 8.10 warning no nvidia drivers?"
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by rsnow on 2008-10-27
Using update manager to update to 8.10 I get the message that "Upgrading may reduce desktop effects and performance in games and other graphically intensive programs." Then it says, "This computer is currently using the NVIDIA 'nvidia' graphics driver. No version of this driver is available that works with your video card in Ubuntu 8.10"

Should I

1. Wait until a driver is available?
2. Go ahead with the update and see how bad my graphics are?
3. Buy an ATI Radeon graphics card?

In other words is the 8.10 version worth doing #3 or will they eventually make an nvidia driver available? Would #2 leave me with having only 800x600 screen?

---

### Post by lemming465 on 2008-10-28
It will downgrade you from an old "nvidia" binary driver which fully supports the hardware to an open source "nv" driver which partially supports the hardware.  You will be able to do 2D stuff at whatever resolutions the card's memory and pixel clock support, but 3D games and compiz effects would suffer.  The problem is that the new X server isn't compatible with the old binary driver, and since it isn't open source, no one at X.org or canonical can port it.  The "nv" driver is ported, but due to lack of documentation and cooperation by nvidia, it hasn't got support for all of the hardware features yet.

Which option to pick depends on your situation.  Nothing important is lost by waiting, and the nvidia driver situation will eventually improve, if only by the 9.04 release.  If you don't need high speed 3D performance, you can upgrade when you like.  I'm running OK myself on the "nv" driver, but I don't play fancy games or dvd's.  If you desparately want some software update which is in 8.10, and need 3D performance, then a new card would solve your problem, yes.

---

### Post by alt3rn1ty on 2008-10-29
Thats my laptop stuffed for upgrading then. Dammit, I was looking forward to this release. Is their no way at all we can use the old driver we are using now with 8.04?, everything works fine just now so I think I will have to give this release a miss if the old nvidia card is no longer supported, I cant replace that in the laptop, its a cut down gforce series 4 MX.

---

### Post by cariboo on 2008-10-29
I'd email Nvidia about no longer suppoerting older graphics adapters. It was their choice, that they no longer provide drivers that work with Xorg 7.4

Jim

---

### Post by rsnow on 2008-10-29
Hey, Thanks! That is the info I needed. I think I will go ahead and do the upgrade as I am not currently using that machine for anything graphically intensive. Then, later, if needed I can add a new card. I just didn't want to wind up with only being able to have an 800x600 screen and 16 colors.

---

### Post by alt3rn1ty on 2008-10-29
Wow, it really is bad news. Anyone know what part/department of nvidia to have a restrained rant at, I'm sure a lot of effort has already gone into doing just that but would like to add my voice aswell.

Also what is now the oldest geforce series that will work (about time I had a new laptop anyway), or is this a full stop for nvidia completely for 8.10?. 
(Edit: Sorry guys found the answer .... nVidia "legacy" video support. The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration. Users of other nVidia chipsets that are supported by the 173 or 177 driver series will be transitioned to the nvidia-glx-173 or nvidia-glx-177 package instead. However, unlike drivers 96 and 71, drivers 173 and 177 are only compatible with CPUs that support SSE (e.g. Intel Pentium III, AMD Athlon XP or higher). Systems with older CPUs will also be transitioned to the nv driver on upgrade. ) Oh well at least I get to install it on the desktop for now.

---

### Post by Elfy on 2008-10-29
a beta became available today - which is a good start

[http://www.nvnews.net/vbulletin/showthread.php?t=122139](http://www.nvnews.net/vbulletin/showthread.php?t=122139)

it will show up in intrepid at somepoint

---

### Post by alt3rn1ty on 2008-10-29
* Added preliminary support for X.Org server 1.5.
    * Improved compatibility with recent Linux 2.6 kernels.
    * Fixed a texture corruption problem seen when running GoogleEarth on some GeForce 4 MX GPUs.
    * Fixed a bug that resulted in AGP FW/SBA settings and overrides being applied incorrectly when using the Linux kernel's AGP GART driver.

So thats the open source version being worked on right?
support for x.org server 1.5 - still not compatible with 7.4?

The way this looks by the time my laptops geforce4 is supported again it will be landfill or the athlon 64 wont be supported anymore :).

I think I will just stick with 8.04 until they release the laptop I want (with an led screen, no more inverter problems :)), dual core (at last!), solid state HD and an nvidia card with a bit more longevity (god forbid I have to go ati or intel). Edit.. Oh AND easy access to the fans so I dont have to invalidate the warranty just to clean out friggin dust.

Edit: Or maybe buy a new washing machine instead, better life expectancy of 9 years, I can watch that go round in circles instead. 
Signed.... Disillusioned with computer industry.

---

### Post by paule100 on 2008-10-30
I think alt3rn1ty did mix up version numbers. 

The newly provided nvidia drivers seem to work with ubuntu 8.10, see

[bug 251107]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107/")

[But don't miss the package maintainers comment]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107/comments/40").

And nvidia provided new beta drivers for both mentioned problematic drivers 71.xxx 96.xxx
see:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14")

 Still, I feel :twisted: about nvidia waiting till 8.10 was out. This tells me a strong position of Ubuntu helped, but 
nvidia has still some way to go. LGPL for their drivers ....:rolleyes:\\:D/=D>:biggrin:

---

### Post by Otto42 on 2008-10-30
:( :( :(

I decided to try Ubuntu on my old Laptop now that 8.10 was out, I figured it would be worth a shot. So I installed it, and couldn't get it working properly. Now I come here only to find out that Ubuntu doesn't support my laptop's GeForce2 Go chipset?

Not a good user experience, people. Very lame indeed. Not a great way to introduce a newbie to Ubuntu, by not having it work on their hardware. So now I have to go and erase the thing and switch over to some other flavor of Linux instead.

So, I guess thanks for the effort, but it's extremely disappointing to find out that I basically wasted 4 hours of my time trying your broken product. You could at least warn people or something, you know?

---

### Post by solitaire on 2008-10-30
> **Otto42 said:**
> :( :( :(

I decided to try Ubuntu on my old Laptop now that 8.10 was out, I figured it would be worth a shot. So I installed it, and couldn't get it working properly. Now I come here only to find out that Ubuntu doesn't support my laptop's GeForce2 Go chipset?

Not a good user experience, people. Very lame indeed. Not a great way to introduce a newbie to Ubuntu, by not having it work on their hardware. So now I have to go and erase the thing and switch over to some other flavor of Linux instead.

So, I guess thanks for the effort, but it's extremely disappointing to find out that I basically wasted 4 hours of my time trying your broken product. You could at least warn people or something, you know?


Your issue is with Nvidia NOT Ubuntu.

Nvidia released Beta drivers that should work with the latest Linux versions a few days ago.  If you were having issues you should come here and ask for help, you should find a large number of people who could help you out.

---

### Post by Sigshane on 2008-10-30
> **Otto42 said:**
> :( :( :(
Not a good user experience, people. Very lame indeed. Not a great way to introduce a newbie to Ubuntu, by not having it work on their hardware. So now I have to go and erase the thing and switch over to some other flavor of Linux instead.

You know, you *could* use the Hardy version...

---

### Post by paule100 on 2008-10-30
Otto42: We are talking here about 3D hardware support. As much as I understand the matter, Ubunut 8.10 shuld work with your graphics card, since there is the free "nv" driver that should work. The proprietary "nvidia" driver is needed for 3d hardware accelaration.  I do not understand from your post, what did not work for you? Did Ubuntu fail to start? 

As I understand the discussions on [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14") the same issue cames with other distros (Fedora is explicitely mentioned). 

Conerning **"at least warn people" **: The [release notes]("http://www.ubuntulinux.org/getubuntu/releasenotes/810#nVidia "legacy" video support") of Ubuntu 8.10 explicitly state:

> The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04 LTS, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration.

I do not understand why the "transition to the free nv driver" did not work in your case.  [Filing a bug report on launch pad]("https://bugs.launchpad.net/ubuntu/") would help other people to not waste another 4 hours or more ...

---

### Post by exXP on 2008-10-30
I don't have nvidia drivers - just the on-board Intel 845 Graphic Controller  -  but I've tried the 81.0 Beta, RC, and today's offering and I can only get as far as the Ubuntu theme music when the whole thing freezes up.  The screen goes black leaving a movable 'wait' pointer on the screen.  There is no activity on either the HD or the DVD.  I've had no trouble with previous versions going back to 6.06.  Any suggestions?
exXP

---

### Post by Otto42 on 2008-10-31
> **solitaire said:**
> Your issue is with Nvidia NOT Ubuntu.
I didn't install "NVidia", I installed "Ubuntu". If Windows didn't work properly on my very much commonplace hardware, I'd blame Microsoft, not NVidia.

> **solitaire said:**
> Nvidia released Beta drivers that should work with the latest Linux versions a few days ago.  If you were having issues you should come here and ask for help, you should find a large number of people who could help you out.
I am here. That's what I'm doing right now. Why are those drivers not in Ubuntu 8.10? The fact that it released without them boggles my mind. 

Same problem with OpenOffice, when I noticed it didn't have 3.0 in it, I was shocked. It's simply an extreme disappointment to me, as a first time Ubuntu user. I've heard such good things about this operating system, and to find that it lacks major, deal-breaker, functionality on a brand new release is, well, shocking to say the least. I'm simply floored by the shoddyness here.

> **Sigshane said:**
> You know, you *could* use the Hardy version...
What is "the Hardy version"? I don't know really Ubuntu's terminology all that well. I used 8.10, because it was new and on all the sites as the big new release.

> **paule100 said:**
> Otto42: We are talking here about 3D hardware support. As much as I understand the matter, Ubunut 8.10 shuld work with your graphics card, since there is the free "nv" driver that should work.
A Linux distro without working 3d support is ridiculous, outdated, and weak, at best. The nv drivers, to put it mildly, are sub-par. I'm sorry, but a Linux distribution that can't do all the cool effects and have a usable workspace is not something I'm interested in trying. There's too many other distros that work just fine.

> **paule100 said:**
> As I understand the discussions on [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14") the same issue cames with other distros (Fedora is explicitely mentioned). 
Fedora 10 beta worked fine. I had to run a few commands from their forums to add some extra repository, but it works without much trouble.

> **paule100 said:**
> Conerning **"at least warn people" **: The [release notes]("http://www.ubuntulinux.org/getubuntu/releasenotes/810#nVidia "legacy" video support") of Ubuntu 8.10 explicitly state:
Who the heck reads release notes? It could have been made more clear that Ubuntu is incapable of working properly with older hardware. That would have been fine, I would not have bothered to try to use it in that case. However, it's been my experience that most Linux installs have vast amounts of backwards compatibility, and so I didn't think to consider for a moment that this one would not work properly on an only 6 year old laptop.

The reason I came back is that I saw a post on another site saying that the legacy drivers nvidia released made it into Ubuntu's repositories. Is this true? Where can one check the repository listings to see what versions are in there? I'm willing to give Ubuntu another shot if I know it's going to work properly this time.

---

### Post by vinnie on 2008-10-31
> **exXP said:**
> I don't have nvidia drivers - just the on-board Intel 845 Graphic Controller  -  but I've tried the 81.0 Beta, RC, and today's offering and I can only get as far as the Ubuntu theme music when the whole thing freezes up.  The screen goes black leaving a movable 'wait' pointer on the screen.  There is no activity on either the HD or the DVD.  I've had no trouble with previous versions going back to 6.06.  Any suggestions?
exXP

From the release notes:

Hangs with desktop effects on Intel 830MG and 845G video cards

There is a bug in the Intel video driver for the older intel 830 and 845 integrated video cards that are used on laptops like the IBM R30. Desktop effects with compiz will not work on those chips and will freeze the system. For new installations, please install using the safe graphics mode (press F4 in the startup screen) on these systems and disable desktop effects via System -> Preferences -> Appearance, clicking on "Visual effects" and choosing "None".

---

### Post by solitaire on 2008-10-31
[quote=Otto42] 			 		 	 	 I am here. That's what I'm doing right now. Why are those drivers not in Ubuntu 8.10? The fact that it released without them boggles my mind. 

Same problem with OpenOffice, when I noticed it didn't have 3.0 in it, I was shocked. It's simply an extreme disappointment to me, as a first time Ubuntu user. I've heard such good things about this operating system, and to find that it lacks major, deal-breaker, functionality on a brand new release is, well, shocking to say the least. I'm simply floored by the shoddyness here.
[/quote]

You could be a bit more civil since you did not ask for help in your origional post. 

The Open Office 3 will be avalible in 8.10 sometime soon. There was a lot of internal discussion (from what i've heard) regarding the addittion of OO3, but since it's release was too close to the finalised 8.10. It was felt best to leave till after the release. (Sometimes having the latest / Greatest version is not the best way to go, a more stable version is usually prefered) 

As for the Drivers... Ubuntu can only work with what Nvidia release. Nvidia released the "BETA" drivers after the Ubuntu 8.10 was finalised. Canonical (The people behind Ubuntu) have no control over Nvidia and when or if Nvidia release drivers.

Please can you let us know the make model of Laptop and we should be able to help you to get the drivers to work.

I'm currently in the same position as yourself. I have an old Dell Inspiron 8200, the graphics card also does not have 3D support at the moment and the Nvidia Beta drivers don't work. But it does not impact my usage of the laptop. 

Their is a currently someone working on fixing this issue from within the Ubuntu community:

See: [https://bugs.launchpad.net/bugs/251107](https://bugs.launchpad.net/bugs/251107)

This WILL be fixed either by Nvidia releasing new drivers or by the Ubuntu comminty finding a workaround.

---

### Post by Otto42 on 2008-10-31
> **solitaire said:**
> You could be a bit more civil since you did not ask for help in your origional post. 
How exactly is saying that I find this system to be extremely disappointing in any way "uncivil"? 

> **solitaire said:**
> The Open Office 3 will be avalible in 8.10 sometime soon. There was a lot of internal discussion (from what i've heard) regarding the addittion of OO3, but since it's release was too close to the finalised 8.10. It was felt best to leave till after the release.
Seems like a rather dumb move to me, but of course that's my opinion.

> **solitaire said:**
> (Sometimes having the latest / Greatest version is not the best way to go, a more stable version is usually prefered)
If that is truly the case, then perhaps I should forget Ubuntu. Sticking with old or outdated software for long periods of time is simply unacceptable to me.

> **solitaire said:**
> As for the Drivers... Ubuntu can only work with what Nvidia release. Nvidia released the "BETA" drivers after the Ubuntu 8.10 was finalised. Canonical (The people behind Ubuntu) have no control over Nvidia and when or if Nvidia release drivers.
Given that it was finalized with broken hardware support and given your earlier comments, I've made my decision. I'll stay away from Ubuntu from now on.

Sorry for the inconvenience, everybody, but given these facts, I cannot use Ubuntu. Thanks for the information anyway! :)

---

### Post by negativ on 2008-10-31
> **Otto42 said:**
> If that is truly the case, then perhaps I should forget Ubuntu. Sticking with old or outdated software for long periods of time is simply unacceptable to me.


Given that it was finalized with broken hardware support and given your earlier comments, I've made my decision. I'll stay away from Ubuntu from now on.

You don't like to read documentation, and you even actively refuse to  understand the nature of the problem you're having.  Maybe you should try [Arch]("http://www.archlinux.org/").  You should have no trouble getting it exactly the way you want it.

---

### Post by solitaire on 2008-10-31
> **Otto42 said:**
> How exactly is saying that I find this system to be extremely disappointing in any way "uncivil"? 


Seems like a rather dumb move to me, but of course that's my opinion.


If that is truly the case, then perhaps I should forget Ubuntu. Sticking with old or outdated software for long periods of time is simply unacceptable to me.


Given that it was finalized with broken hardware support and given your earlier comments, I've made my decision. I'll stay away from Ubuntu from now on.

Sorry for the inconvenience, everybody, but given these facts, I cannot use Ubuntu. Thanks for the information anyway! :)

All version need a cut off point where no new additions or changes can be made. If they did not then no new version would be released.  It is standard good business practice.

Hardy Heron (Ubuntu 8.04) is only 6 months old. Ubuntu release a new version every 6 months. so I think it's unfair to say that older versions are 'Old and Outdated'. they are Tried and tested and stable.

But if you prefer to use Windows then go ahead it's a free country. (except you pay for it). 

To be fair Microsoft Vista had more issues when it was released than Ubuntu's ever had. Ubnutu routinely get praise for it's ease of the "out-of-the-box" experience when installed.  But since Ubuntu is a community effort, where people give their time, skills and experience for free, i think it's done 100 times better than Microsoft has recently.

Please don't give up so easy it's worth it in the long run...

This is my last word on this.

peace

---

### Post by luispa on 2008-11-01
Hi,

I recently upgraded to 8.10 and I'm having the same problem you have. I downloaded the BETA package 71.86.07 (The one ending with pkg1, Do you know the differences between this and the one ending with pkg0?) from the nvidia website and I successfully compiled and installed the new driver. I followed all the instructions in the nvidia Linux Forum. The problem is when I reboot my computer, GDM don't start and give me this message:

(EE) Failed to load /usr/lib/xorg/modules/drivers//nvidia_drv.so
(EE) Failed to load module "nvidia" (loader failed, 7)
(EE) No drivers available

I have a TNT2 card. Does anybody know how to solve this?

Thank you very much in advance.

---

### Post by paule100 on 2008-11-01
> **Otto42 said:**
> 
Fedora 10 beta worked fine. I had to run a few commands from their forums to add some extra repository, but it works without much trouble.


The link to [bug 251107]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107/") also has post that tell you to run a few commands ...

But from your comments about OO 3.0 I think you might be better of with Fedora. Thats what so many distros are for, there is always some that fits your needs. And Fedora does a great job beeng fast(er than ubuntu). Those  many distros are a great advantage of free software (not that it does not cast you a dime) and my main point to use an operating system thats free. And the first competitive graphic cards vendor with free (i.e. LGPL or something) drives will get my money (the second one will already need to fight hard to get me). 

> **Otto42 said:**
> 
Who the heck reads release notes? 



Oh, I did, and did not upgrade. I don't mind staying for a while with the long term support version 8.04. The release notes are really a fast read, with very specific headlines and all ..


> **Otto42 said:**
> 
The reason I came back is that I saw a post on another site saying that the legacy drivers nvidia released made it into Ubuntu's repositories. Is this true? 


Look at [bug 251107]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107/")

I'm sure that Alberto Milone will post there as soon as the beta drivers are available through Ubuntu package manager.

---

### Post by Roger2hk on 2008-11-02
> **luispa said:**
> Hi,

I recently upgraded to 8.10 and I'm having the same problem you have. I downloaded the BETA package 71.86.07 (The one ending with pkg1, Do you know the differences between this and the one ending with pkg0?) from the nvidia website and I successfully compiled and installed the new driver. I followed all the instructions in the nvidia Linux Forum. The problem is when I reboot my computer, GDM don't start and give me this message:

(EE) Failed to load /usr/lib/xorg/modules/drivers//nvidia_drv.so
(EE) Failed to load module "nvidia" (loader failed, 7)
(EE) No drivers available

I have a TNT2 card. Does anybody know how to solve this?

Thank you very much in advance.

I'm facing the same problem.
And I saw the screen saying: "Nvidia (71.86.07)      [[COLOR="Red"]Failed[/COLOR]]"
I really don't know what to do. I have reinstalled that for a few times, but it just doesn't work. It still allows me to use the GNOME in low-graphics mode.
Should I do any configuration? like /etc/X11/xorg.conf?

---

### Post by paule100 on 2008-11-03
In [comment #47]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107/comments/47") of [bug 251107]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107/") you will find 10 steps how to make your own debian package suitable for ubuntu and how to install it. Does that work for you? 

I'm sure it won't take so long till the package will be available through the update manager (since the issue affects so many users. As I need 3d in my daily work (and do not have a computer to test things) I will wait till this happens.

---

### Post by luispa on 2008-11-03
> **paule100 said:**
> In [comment #47]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107/comments/47") of [bug 251107]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107/") you will find 10 steps how to make your own debian package suitable for ubuntu and how to install it. Does that work for you?

No, it doesn't. The driver I used was the 71.86.07 BETA which I downloaded from the nvidia website. I followed all the steps mentioned in the nvidia website. I replaced the Xorg.conf file with one which worked before.

---

### Post by shawfield on 2008-11-03
Hi

I have Nvidia driver problems after upgrading to Intrepid.

I have the GEforce 6100 graphics on the motherboard, with an AMD Athlon x2 .

After installing & booting, I got only 640x480 resolution & attempting to invoke the Nvidia driver via preferences, showed me that the nvidia driver was disabled. It would not allow me to enable it.

After 5 or 6 reboots, my machine managed to find a driver to use ( clever machine ! ) & I now have 1440 x 900 resolution, but clearly not with an Nvidia driver, as the quality on screen is poor & text is barely readable. 

Tried to use the Ubuntu update which tells me there are 652 updates available, & its only possible to do a partial upgrade ; but when I try to install them, I am told that "an upgrade from intrepid to Hardy is not supported with this tool"

So - bottom line - Do I need to re-try my Intrpid upgrade or can I update via the command line with a specific nvidia driver update request ?

Many Thanks

---

### Post by paule100 on 2008-11-03
Now [there are]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107/comments/51") packages for testing available. People are explicitly ask to test and give feedback.

---

