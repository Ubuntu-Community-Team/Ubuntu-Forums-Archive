---
title: "Nouveau General Discussion"
date: 2010-02-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by plun on 2010-02-13
Can we PLEASE skip this crap until maybe Lucid +1 or +2 ???

Include highly unstable code into a LTS, sound stupid !

Or show me a bullet-proof "blacklist" for Nouveau  !


--

---

### Post by SevenMachines on 2010-02-13
> **plun said:**
> Can we PLEASE skip this crap until maybe Lucid +1 or +2 ???

Include highly unstable code into a LTS, sound stupid !

Or show me a bullet-proof "blacklist" for Nouveau  !


--
i take it you've had a few bad experiences with nouveau then :)
i'm guessing when you think of LTS as a 3 year release it makes more sense to default to nouveau in that case, nv is fairly inactive, nouveau is now in the kernel main tree and replaces nv. For the next 3 years nouveau will be the one getting the fixes and improvements that can be backported.

---

### Post by 23meg on 2010-02-13
> **plun said:**
> Can we PLEASE skip this crap until maybe Lucid +1 or +2 ???

Include highly unstable code into a LTS, sound stupid !

Or show me a bullet-proof "blacklist" for Nouveau  !


--

The point of testing is to determine whether switching from nv to Nouveau is feasible. Calling it "crap" (which you've taken every opportunity to in numerous threads) will not disqualify it; reproducible negative test results can. If you're not interested in testing or using it, please be so kind as to refrain from posting to related threads.

---

### Post by plun on 2010-02-13
> **SevenMachines said:**
> i take it you've had a few bad experiences with nouveau then :)
i'm guessing when you think of LTS as a 3 year release it makes more sense to default to nouveau in that case, nv is fairly inactive, nouveau is now in the kernel main tree and replaces nv. For the next 3 years nouveau will be the one getting the fixes and improvements that can be backported.

Yes, its crap IMHO.......

and Lucid is a LTS.

(no Fedora disasters please ! )

;)

---

### Post by plun on 2010-02-13
@sevenmachines

Can you play a 1080p movie without trouble... ?

---

### Post by donniezazen on 2010-02-13
> **plun said:**
> Can we PLEASE skip this crap until maybe Lucid +1 or +2 ???

Include highly unstable code into a LTS, sound stupid !

Or show me a bullet-proof "blacklist" for Nouveau  !


--

+1

I would love to have Nouveau but i do call it crap. There have been several thread calling for testing but all of them have failed to help other people who are facing problems with Nouveau. What to test when i am just not able to start the X? How can you include such a driver in LTS when no one has got idea of how to fix it.

---

### Post by MacUntu on 2010-02-13
> **soham_1207 said:**
> There have been several thread calling for testing

Exactly one. :D

> **soham_1207 said:**
> but all of them have failed to help other people who are facing problems with Nouveau.

Cause that's not the point?

[https://wiki.ubuntu.com/X/Testing/NouveauEvaluation](https://wiki.ubuntu.com/X/Testing/NouveauEvaluation)

**Evaluation**. ;)

---

### Post by SevenMachines on 2010-02-13
> **soham_1207 said:**
> +1

I would love to have Nouveau but i do call it crap. There have been several thread calling for testing but all of them have failed to help other people who are facing problems with Nouveau. What to test when i am just not able to start the X? How can you include such a driver in LTS when no one has got idea of how to fix it.
this is why the possibility of a nouveau change is being tested in the ppa. as mentioned before by 23meg, the only way to work through the bugs and establish if its a workable option is to test the state of nouveau. with nouveau entering the kernel, over the next 3 years its more likely nouveau will be more actively supported and developed than the current default of nv will be

Reverse engineering is also a bit of a dark art, theres a lot of hard work gone in, whether or not its reached a useful status for most people yet. Thats why I prefer the terms ready/not-ready rather than crap/not-crap :)

I would also mention that not all X bugs are nouveau related, plymouth  for example is undergoing a lot of work to deal with a few problems at  the moment, thats the joy of a development cycle! I've  had the problem of changing from nvidia to nouveau and finding crashes/freezes and so on, only to find its because plymouth doesnt really run properly (graphically on a framebuffer) on the binary driver but does on nouveau, so the plymouth bug only shows up on the change to nouveau

---

### Post by plun on 2010-02-13
> **soham_1207 said:**
> +1

 How can you include such a driver in LTS when no one has got idea of how to fix it.

For software religious reasons.....;)


Fedora is just a "blessed" mess with unhappy users.

[http://www.google.se/search?q=fedora+blacklist+nouveau&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.se/search?q=fedora+blacklist+nouveau&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Next Ubuntu !

---

### Post by SevenMachines on 2010-02-13
just a quick addition, it might be a good idea to separate the 'should nouveau be default' and the 'how to test and report on nouveau bugs' discussions into different threads. this should really be a practical testing thread to try and generate good information on the situation for various cards

---

### Post by 23meg on 2010-02-13
I've moved the off-topic posts from the testing thread to this new one.

---

### Post by 23meg on 2010-02-13
> **plun said:**
> For software religious reasons.....;)

How is replacing a free software driver with another free software driver a "software religious" act?

---

### Post by cicoandcico on 2010-02-13
i just tried fedora 12 with nouveau (will try ubuntu as soon as there's a bootable cd). i've got a quadro NVS 140m in my laptop.

well, i'm so impressed. i've never had supposed this thing was in this shape. i've tested only the 2D capabilities, but i had no (zero) problem. nor with xvideo, nor with xrandr, nor with anything else. flashplayer was running fullscreen smoothlessly, while hanging with the binary driver. metacity compositing was fine. 
gtkperf benchmark completed in 9 seconds, compared to the 5 sec with the nvidia driver.

and what 've tested is 5 months old! i can't imagine what will come in 10.10 (i guess stable 3D support).

so far, GO NOUVEAU GO!!! i'll stay tuned!

---

### Post by SnowRider on 2010-02-13
GeForce 7000M / nForce 610M...Tried nouveau but couldn't get to log-in screen...just black screen...had to revert back to nvidia.

---

### Post by ronacc on 2010-02-13
getting better , passed most tests , glxinfo crashed and xrandr threw a bad request error . laggy opening/closing/min/max windows , some icons fuzzy and text not sharp . back to the -13 kernel and nvidia 195.36  .

---

### Post by gnomeuser on 2010-02-13
> **plun said:**
> Can we PLEASE skip this crap until maybe Lucid +1 or +2 ???

Include highly unstable code into a LTS, sound stupid !

Or show me a bullet-proof "blacklist" for Nouveau  !


--

These are very valid concerns, if expressed in a hostile manner. However I believe I can make a case for the opposing view.

Currently the testing is being done in a separate ppa and no matter what happens the nv driver is still the default driver for the lucid installs. 

This is a wider call for further testing in this manner with the goal of deciding to merge. This decision is desired to be yes and hopeully soon, if testing even for a time defaulting lucid installs to nouveau. It is a development release and provided that we document and publish documentation on how to switch back even from a dreaded thing like a non starting X. This will help with forum goers with problems and prevention.

While the code in Lucid is backported, the upcoming .33 kernel has merged nouveau and development is active. Fedora has shipped it in their latest and has commited fulltime workers to making it solid. Mandriva has switched in their developmet release. openSUSE so far hasn't commited to nouveau as the only major distro to a nouveau switch for multiple technical and otherwise important bug handling enhancements over nv. 

Add to this that most nvidia users will likely react to the install option to switch to the proprietary drivers because lets face it nouveau nor nv are providing effects and other enhancement options yet. Nouveau is though showing promise and a shiping configuration as of today in the Fedora 13 Rawhide build can run Quake 3 on a nouveau driver. In other words the potential is there as is the work being done. 

For an LTS release it is important not just to provide a solid release but also a release we have to make smart decisions abut for long term supportability. Short term nouveau might not make the cut, or we might be able to fix it up. If we fix it up we are in line to do updates for the next 3½ based on work being done by a large group of developers and companies are investing in it for their upcoming enterprise solutions. The same goes for the underlying stack. Long term commiting to wider testing of nouveau is a low cost, reversable decision that does not take from the experience we already ship in Lucid today and in Karmic before it (nv is the default and changes rarely, nvidia's driver is often optionally installed and will thus have to take action to partake in testing, they are not being switched to nouveau.

If wider testing shows that we have problems on certain revisions of the updated driver we could possibly use statistics from the launchpad bug reports to us handle this, hopefully in time launchpad will expand on this functionality to make it more useful and easy. Right now our current data will still show us dangerous spikes in certain bugs and will let us script lots of standard interactions with reporters. While lacking in the human touch department it gets the job done and maintainers are still at hand under the same rules as usual. There are only so many hours in the day, there are also probably more of you than of me - forgive me for not reaching all of you. Huge spikes could be considered triggers to issue a rollback to pre-spike or a switch to nv.

After we have some wider testing and decide if it ready to be in main Lucid then we can see from a few weeks if nouveau is a worthwhile investment for the future. We should realistically expect regressions (possibly some we cannot responsible promote for post release updating, at least not without serious and commited testing) but we should also expect massive gains for lots of users. 

I believe it is a worthwhile decision to test nouveau, if it doesn't pan out after a few weeks nothing stops us from making a decision for the nouveau roadmap. Perhaps that will turn out to be Lucid+1 and with no plans to use it in LTS, or a decision to perhaps in a 1 or so decide to call for testing again and using the results from lucid+1 and beyond to see if a post release update process is worth investigating.

---

### Post by plun on 2010-02-14
> **23meg said:**
> How is replacing a free software driver with another free software driver a "software religious" act?

Well...."the nVidia binary" isn't free but it works great for everything a normal user wants to do with a PC, playing game, watch HD movies including using VDPAU), 3D etc.  

Replacing this driver with something which works badly in different areas is for me a "software reloigious act".

Fedora is just a mess with users struggling with blacklisting Nouveau

[http://forums.fedoraforum.org/showthread.php?t=204752](http://forums.fedoraforum.org/showthread.php?t=204752)

Also includes a part  "If nouveau refuses to die try"

```
su
yum erase xorg-x11-drv-nouveau
mv  /lib/modules/$(uname -r)/kernel/drivers/gpu/drm/nouveau/nouveau.ko /lib/modules/$(uname -r)/kernel/drivers/gpu/drm/nouveau/nouveau.txt
mv /boot/initramfs-$(uname -r).img /boot/initramfs-$(uname -r)-nouveau.img
dracut /boot/initramfs-$(uname -r).img $(uname -r)

```


Make this to a Jockey option please ! or skip it until Lucid+1 or +2

Maybe its time to move on to W7......???:^o:frown:

--

---

### Post by ronacc on 2010-02-14
while I am willing to , and do , test noveau and will gladly use it when it provides all the functionality that the nvidia proprietary driver does . I will be extremely upset  if we go through another bunch of crap like a few releases back where jockey was actualy blocking the installation of the nvidia proprietary driver . I like , Plun , call that "software religion" ( use only "pure" software or Ubuntu will smite thee with the black screen of death ).

---

### Post by uBeer on 2010-02-14
> **plun said:**
> ...

Replacing this driver with something which works badly in different areas is for me a "software reloigious act".
...
--

It is not replacing anything at all (yet), so what is the problem? And if it is going to replace anything it will be the nv driver, not the nvidia binary. That shouldn't be that much of a problem right?

---

### Post by plun on 2010-02-14
> **uBeer said:**
> It is not replacing anything at all (yet), so what is the problem? And if it is going to replace anything it will be the nv driver, not the nvidia binary. That shouldn't be that much of a problem right?

Please READ  !!!   

Howto blacklist Nouveau and install a binary nVidia driver.

[http://forums.fedoraforum.org/showthread.php?t=204752](http://forums.fedoraforum.org/showthread.php?t=204752)

For Fedora it ended up in a mess which just drives users to abandon Linux...

Compare this with the Gnash-crap story ...

---

### Post by uBeer on 2010-02-14
But Fedora is a whole different story compared to Ubuntu. Especially with closed source drivers. In Fedora it is not really encouraged to install anything that isn't open source. In Ubuntu it is made sure that the proprietary stuff can be turned on easily without too much hassle.

So I still don't see a problem for Ubuntu (besides some bugs that can be easily fixed) as they already made the installation of restricted drivers easy/easier.

---

### Post by plun on 2010-02-14
> **uBeer said:**
> 
So I still don't see a problem for Ubuntu (besides some bugs that can be easily fixed) as they already made the installation of restricted drivers easy/easier.

No,  I don't see the difference, Nouveau must be blacklisted and I haven't seen **any "Call for testing" or changes within Jockey**.

This can end up exactly as with Fedora in a giant mess....;)

---

### Post by uBeer on 2010-02-14
Ah, ok. So what should happen is that Jockey and Nouveau should be tested so that changing between them actually works.

That's not an impossible problem, right? But it will probably be more complicated then I think because the fedora page is over 50 pages long...

But I still think that Nouveau should not be seen as an evil product because the integration with the distributions is not yet seamless. That was what I tried to say. And of course, if the developers do not manage to make the integration nice and sweet before some deadline it shouldn't be default (as I am sure it won't be anyways).

Now let's hope that the developers can sort it out!

---

### Post by plun on 2010-02-14
> **uBeer said:**
> 

Now let's hope that the developers can sort it out!

Yes... "Bulls eye"....:D

Time is running out and I am scared that this can be a disaster for Ubuntu.  I also don't find Nouveau as evil, "the timing" is just wrong, IMHO.

---

### Post by dino99 on 2010-02-14
> **plun said:**
> Yes... "Bulls eye"....:D

Time is running out and I am scared that this can be a disaster for Ubuntu.  I also don't find Nouveau as evil, "the timing" is just wrong, IMHO.

you are right Plun, Lucid is LTS, so i can't understand that choice of uncluded such beta app as default, kind of silly design. Don't want the karmic's nightmare again. :o

---

### Post by MacUntu on 2010-02-14
What's the problem with switching between Nouveau and Nvidia's BLOB? Have done it a couple of times now.

---

### Post by plun on 2010-02-14
> **MacUntu said:**
> What's the problem with switching between Nouveau and Nvidia's BLOB? Have done it a couple of times now.

Someone must code Jockey..... !!!

Personally I have no problem with this but I am a "nerd"....;)

It must also be a bullet-proof upgrade to Lucid from Karmic and Hardy. without any disturbance from a Nouveau module which first must be blacklisted.....

---

### Post by dino99 on 2010-02-14
> **MacUntu said:**
> What's the problem with switching between Nouveau and Nvidia's BLOB? Have done it a couple of times now.

as said before: timing, should not be "default" till final Nouveau release.

---

### Post by Slug71 on 2010-02-14
We really should have another separate daily build or something with 2.6.33 and Nouveau and even possibly FF 3.7 by default if we are to begin testing for +1 releases. Nouveau will not ship with Lucid nor the 2.6.32 kernel. 
We are suppose to be focusing on this release.

This would also give us an extra month of testing between a release and when the 1st Alpha is out for the next release.

Even if devs do not pay much attention to this build, at least bugs can be filed and feedback given.

---

### Post by gnomeuser on 2010-02-14
> **plun said:**
> Well...."the nVidia binary" isn't free but it works great for everything a normal user wants to do with a PC, playing game, watch HD movies including using VDPAU), 3D etc.  

We are aiming to let nouveau replace the nv driver, not the proprietary nvidia driver. Nv even today is the default driver for nvidia cards till such a time as the user decides to install an alternative such as the support challenged closed source nvidia offering.

Nouveau is emperically superior to nv in a number of ways, it's not obfuscated code for one, it's actively developed and built on the same stack as the rest of our currently in development drivers for many other cards such as those from intel and ati. Finally it is also more featureful, supports a wider range of cards will already today has budding but working support for advanced 3d use cases (e.g. current snapshots can run quake 3 and TA: Spring on a limited range of cards today).

---

### Post by ronacc on 2010-02-14
I think what plun is worried about is that when the developers believe noveau is ready , it will be pushed rather more aggressively than just being made the default , for instance will the choice of the proprietary drivers be dropped from "hardware drivers" ? Will the installation of the proprietary driver require esoteric "monkey motion" as with fedora currently ? these are valid concerns .

---

### Post by MacUntu on 2010-02-14
No monkey motion: 'sudo apt-get install nvidia-current' - done.

---

### Post by gnomeuser on 2010-02-14
> **ronacc said:**
> I think what plun is worried about is that when the developers believe noveau is ready , it will be pushed rather more aggressively than just being made the default , for instance will the choice of the proprietary drivers be dropped from "hardware drivers" ? Will the installation of the proprietary driver require esoteric "monkey motion" as with fedora currently ? these are valid concerns .

That is a slippery slope argument. 

There are no such plans, in fact while nouveau has been pushed the packaging of the proprietary driver has also been made more robust as well as updating the driver to the latest stable branch from nvidia. On the same day as the call for testing of nouveau went out we had a call for testing of the nvidia driver work.

Long term nouveau is sure to become a sufficient driver for most people, providing an accelerated experience for users in every general case and the proprietary driver would thus be less vital to providing a reliable experience. In such a long term scenerio it would be entirely reasonable to consider demoting jockey at least from running notification on installs known to run reliably with a certain feature set. This however is not even remotely being discussed at present.

---

### Post by SevenMachines on 2010-02-14
just to emphasize, the question is whether nouveau should replace nv as default, not anything to do with the proprietary driver. its a comparison between the state (and future development) of the open source drivers. nouveau supports more cards and will be actively worked on over the coming years, the testing is to see if its relatively stable enough to make the change. nvidia's own driver will be just as easily installable as it was previously through jockey. as far as i remember theres even a reminder that theres a proprietary driver available when you boot into a fresh install.

---

### Post by ronacc on 2010-02-14
are you implying that the "hardware drivers" method WILL disapear ? I ask not for myself , I was installing the driver from cli before Ubuntu existed , What concerns me is are we going to make it harder for new users to do so ? That I believe would be a very bad thing .

---

### Post by gnomeuser on 2010-02-14
> **ronacc said:**
> are you implying that the "hardware drivers" method WILL disapear ? I ask not for myself , I was installing the driver from cli before Ubuntu existed , What concerns me is are we going to make it harder for new users to do so ? That I believe would be a very bad thing .

No, it has now been clearly explained twice that this is not the case.

---

### Post by SevenMachines on 2010-02-14
> **ronacc said:**
> are you implying that the "hardware drivers" method WILL disapear ? I ask not for myself , I was installing the driver from cli before Ubuntu existed , What concerns me is are we going to make it harder for new users to do so ? That I believe would be a very bad thing .
No need to worry!, jockey isnt going anywhere, it will be just as easy to install nvidia's driver as before, its a simple nv/nouveau comparison and doesnt effect the way the binary driver is dealt with

---

### Post by ronacc on 2010-02-14
that is satisfactory .

---

### Post by plun on 2010-02-14
> **ronacc said:**
> I think what plun is worried about is that when the developers believe noveau is ready , it will be pushed rather more aggressively than just being made the default , for instance will the choice of the proprietary drivers be dropped from "hardware drivers" ? Will the installation of the proprietary driver require esoteric "monkey motion" as with fedora currently ? these are valid concerns .

Yes I am worried.....

This is "State of the art" for a free nVidia driver... also 3D with Gallium.

Please read.
[http://www.phoronix.com/scan.php?page=news_item&px=Nzk4MQ](http://www.phoronix.com/scan.php?page=news_item&px=Nzk4MQ)

;)

---

### Post by 23meg on 2010-02-14
No need for scaremongering and conspiracy theories. Your beloved proprietary driver and the ability to easily install it aren't going anywhere, as has been said 3877923 times. The first person to ever mention that possibility out of thin air was plun, who didn't base it on any existing plan or discussion.

As for whether it's going to be a good idea to replace nv with Nouveau, and in the case that it will, providing a good blacklist and fallbacks for possibly problematic hardware, I hate to repeat myself but **that's what [the current testing]("http://ubuntuforums.org/showthread.php?t=1405575") is for**. If you're "worried" about potential problems, you'd better hurry and start testing Nouveau with whatever NVIDIA hardware you have.

---

### Post by ronacc on 2010-02-14
I'll ask this again here since I'm not getting an answer on the testing thread , how do I add my results to the wiki page ? I sign in with my launchpad ID but all it wants to do is let me edit the whole page and that don't seem right .

---

### Post by darco on 2010-02-26
I went ahead and reformatted my A2 and installed A3. I was previously running the .33 kernel but wanted a clean install to try out Nouveau. So far no issues except my Conky script can no longer grabs the GPU temps. Says "nvidia-settings not found". I understand since I am not running an nvidia driver.
My script calls for this:

```
 GPU Temp: ${color green}${execi 60 nvidia-settings -query GPUCoreTemp | perl -ne 'print $1 if /GPUCoreTemp.*?: (\d+)./;'}°C$voffset  ${color #FFFFFF}
```

Is there something buried in the nouveau driver that I can extract the GPU temp?

thxs

---

### Post by ricsi-pontaz on 2010-03-11
I use Lucid Lynx (up-to-date) on my desktop with a GeForce GTS 250 graphical card. Yesterday I decided I tried Nouveau with my card, so I deactivated NVIDIA driver at Jockey. A lot of things work fine, I've got only one problem. With this driver my computer's fan (CPU or GPU - I don't know) always work full speed. 

I searched this problem on Launchpad (fan, full, speed) and found some outdated bugs with same things. Anyone know something about this?

---

### Post by jmmL on 2010-03-11
> **darco said:**
> I went ahead and reformatted my A2 and installed A3. I was previously running the .33 kernel but wanted a clean install to try out Nouveau. So far no issues except my Conky script can no longer grabs the GPU temps. Says "nvidia-settings not found". I understand since I am not running an nvidia driver.
My script calls for this:

```
 GPU Temp: ${color green}${execi 60 nvidia-settings -query GPUCoreTemp | perl -ne 'print $1 if /GPUCoreTemp.*?: (\d+)./;'}°C$voffset  ${color #FFFFFF}
```Is there something buried in the nouveau driver that I can extract the GPU temp?

thxs
I discovered recently that ```
sudo nvclock -T
``` will get the GPU temperature with the nouveau driver.

---

### Post by mattman on 2010-03-11
My GTS 250 is not supported by nvclock yet. It shows the temp at -391 C.

---

### Post by ronacc on 2010-03-11
> **mattman said:**
> My GTS 250 is not supported by nvclock yet. It shows the temp at -391 C.

write up a paper on that thing and you'll get a nobel prize , you have achieved a temperature below absolute zero.

---

### Post by dino99 on 2010-03-11
> **ricsi-pontaz said:**
> I use Lucid Lynx (up-to-date) on my desktop with a GeForce GTS 250 graphical card. Yesterday I decided I tried Nouveau with my card, so I deactivated NVIDIA driver at Jockey. A lot of things work fine, I've got only one problem. With this driver my computer's fan (CPU or GPU - I don't know) always work full speed. 

I searched this problem on Launchpad (fan, full, speed) and found some outdated bugs with same things. Anyone know something about this?

As i remember, i've read somewhere that Nouveau dont deal yet with fan's speed, might wait devs include that feature in.

---

### Post by xir_ on 2010-03-11
I have to say that i agree that nouveau is a great thing and don't share the OP sentiments.

1. If you have problems, bug report.
2. The Nvidia blob isn't going anywhere.
3. Nv will still be about for back up, even in your worse case scenario.


If you really are having a tiff about the state of the driver put the energy into bug reporting like mad.


There are things missing, like fan control and 3d, but these will come faster if the massive ubuntu community can help debug.

---

### Post by ricsi-pontaz on 2010-03-12
> **dino99 said:**
> As i remember, i've read somewhere that Nouveau dont deal yet with fan's speed, might wait devs include that feature in.

Oh, okay, thanks for the reply.
But unfortunately this way I can't use my computer with Nouveau, because the fan's noise is very frustrating

---

### Post by xir_ on 2010-03-12
> **ricsi-pontaz said:**
> Oh, okay, thanks for the reply.
But unfortunately this way I can't use my computer with Nouveau, because the fan's noise is very frustrating

Well it doesn't have power control and this means it would be a bad idea to have the fan spin down (seeing as the gpu is always going full pelt).


This feature will be available for ati cards in the .34 mainline kernel with any luck. But Nouveau may be some time off. (Nvidia wont release any specs)

---

### Post by Ichtyandr on 2010-03-12
a noob question, as I understand the GPU fan prevents the nvidia card from burning out, so apart from noise considerations, why would anyone intentionally slow it down? does it kinda serve environment friendly purposes or perhaps simply prolongs the life of your hardware?

---

### Post by dudude on 2010-03-13
> **Ichtyandr said:**
> a noob question, as I understand the GPU fan prevents the nvidia card from burning out, so apart from noise considerations, why would anyone intentionally slow it down? does it kinda serve environment friendly purposes or perhaps simply prolongs the life of your hardware?

It, along with lowering the power usage of the card, helps lower power usage which may not be all that noticeable on a desktop, but could mean a significantly better battery life on a laptop.

Also, the Nouveau driver at this point is primarily intended to be used for people that want exclusively open-source software and/or as a replacement for the NV driver. The Nvidia binary is still required if you need 3D in many cases or power scaling.

---

