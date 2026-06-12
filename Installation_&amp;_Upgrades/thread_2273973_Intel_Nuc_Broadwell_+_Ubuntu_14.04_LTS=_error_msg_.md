---
title: "Intel Nuc Broadwell + Ubuntu 14.04 LTS= error msg about driver i915"
date: 2015-04-16
forum: Installation &amp; Upgrades
---

### Post by furioususer on 2015-04-16
I have just recently bought an Intel Nuc Broadwell 2.5" I5-5250U/5i5RYH and I am trying to install Ubuntu 14.04 LTS, but it's not going so well. 

I receive the following error message: **"Error: driver i915 is already registered, aborting... hda-intel error request power-well från i915"**

I have both googled and searched on this site for the error msg but couldn't find anyone offering any real solutions to this problem (someone suggested trying Ubuntu 15.04 for example and that to me sounds like avoiding the issue). So I am wondering if this is it. It doesn't work: either move on (send the NUC back) or settle for another OS?

---

### Post by oldfred on 2015-04-16
Not your model, but Broadwell & very new Intel Video:
Broadwell (future) fix for use with 14.04's 3.13 kernel. Fixes really in 3.15 kernel
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0ODY](http://www.phoronix.com/scan.php?page=news_item&px=MTY0ODY)

 Dell XPS13 - New Broadwell, not yet fully supported Feb 2015
[http://major.io/2015/02/03/linux-support-dell-xps-13-9343-2015-model/](http://major.io/2015/02/03/linux-support-dell-xps-13-9343-2015-model/)
[http://askubuntu.com/questions/395743/how-to-install-ubuntu-on-xps-15-platinum-2014-version-properly](http://askubuntu.com/questions/395743/how-to-install-ubuntu-on-xps-15-platinum-2014-version-properly)

Intel is pretty good about creating updates to kernel, support software & new video drivers. But kernel updates take a while to get incorporated into a new kernel and then into new distributions.

So with very new hardware you have to use a very new distribution and may have to add ppa's to update to even newer kernels & drivers.

      
 All the current drivers xorg-edgers PPA
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages)
Oibaf PPA discusion
 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1)
New kernels ppa
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)
Ubuntu Kernel Mainline PPA
[http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1)
[https://launchpad.net/~kernel-ppa/+archive/ubuntu/pre-proposed](https://launchpad.net/~kernel-ppa/+archive/ubuntu/pre-proposed)

---

### Post by furioususer on 2015-04-17
Thanks for finding all those links. I appreciate it! Especially the first article answered a few questions of mine.

But I am still unsure how to solve this issue. The article mentioned that I could keep my Ubuntu 14.04 LTS installation and only upgrade the kernel to 3.14, but how do I do that? It provides two links at the bottom of the article, but I don't know what to do from there (I'm not very good with the terminal or Ubuntu unfortunately).[B] Anyone care to give me very specific instructions? Preferably providing the instructions in numbered steps (1. open terminal, 2. write x etc).

[/B]> [COLOR=#000000]So with very new hardware you have to use a very new distribution and may have to add ppa's to update to even newer kernels & drivers.
[/COLOR] 
What new distribution are you referring to?

And did I understand the article correctly: **this will be standardized in coming Ubuntu versions? **So I don't have to worry about "special installations" in the future when I re-installing Ubuntu?

---

### Post by furioususer on 2015-04-17
Btw, I read that [COLOR=#000000][FONT=Tahoma]*Ubuntu 14.04.2 is out now and there was some speculation that it might have the new required kernel update to make it work with the new Broadwell?*[/FONT][/COLOR]

---

### Post by oldfred on 2015-04-17
I create multiple 25GB partitions for / (root) so I can have several installs to test. 
So you can install both 14.04.2 and 15.04 to see if one works better than the other.

I have never had to use ppa. But you just add the new repository and do an update to system. The update process finds the newest version to install, so the ppa having a newer version then is the version installed. If using the ppa, you may need one for kernels & one for everything else.


This has the three commands you need with && between to actually make it one line to copy.
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1)

> Enabling and upgrading the open-source graphics drivers for Intel, AMD Radeon,  and Nouveau (NVIDIA) can be as easy as running **sudo apt-add-repository  ppa:oibaf/graphics-drivers && sudo apt-get update && sudo apt-get  dist-upgrade**. It's as easy as that.

---

### Post by furioususer on 2015-04-17
Ok. I will try to do the following: 

1. Make a live USB with 14.04.2 for starters and try booting up with that (I will also try 15.04). 
2. If that works, nothing else has to be done. But if not, I will try the command [B]sudo apt-add-repository ppa:oibaf/graphics-drivers && sudo apt-get update && sudo apt-get dist-upgrade.

[/B]Have I understood you correctly? The command you suggested is enough to add the instructed repository? I don't need to do tinker with repositories in any other way?

---

### Post by furioususer on 2015-04-17
Btw, what is the difference between 14.04 LTS and 15.04?

---

### Post by oldfred on 2015-04-17
I believe 14.04 & 14.04.1 used kernel 3.13.0.xxx as I still have 3.13.0-49 as current.
       Ubuntu 14.04.2 (Trusty Tahr) Uses 3.16 kernel

 The Ubuntu 14.10 release delivers a v3.16 based kernel.
      
 Ubuntu 15.04 has the Linux 3.19 kernel, systemd 219, Mesa 10.5, X.Org Server 1.17, GCC 4.9

That is a graphics driver (many versions) ppa. There is another ppa for kernels if needed.

Of course it is not just the kernel, but all the other support software, newer drivers, and newer applications that each release includes. But development time, release into kernel, release of kernel and then incorporation of newer kernel into a distribution takes time.

Also realize that using a ppa is not always a good solution. You then are testing the newer software just as one of the Ubuntu developers is doing. And may get into needing lots of other support software. Be sure to have good backups of your data & configuration, so you can reinstall if necessary. 
I have 14.04 as my main working install as it is LTS, but typically install the newest Ubuntu just to see what the differences are, but in a separate / (root) partition.

---

### Post by furioususer on 2015-04-18
If both 14.04.2 and 14.10 uses 3.16 kernel, then there is no need to test them both. Right? 
As I did test 14.04.2 on a live USB right now, and it didn't make any difference. 

I also tested 15.04 and it failed with the following error msg: not a COM32R image.


This seems hopeless :/

---

### Post by oldfred on 2015-04-18
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/1342626](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/1342626)

Did you try the press tab and type live?

---

### Post by furioususer on 2015-04-19
Now I did, and it worked! Thank you so much! But there is a big issue with the NUC and the graphics (I think it's the graphics causing it) that I haven't gone in to yet. See the next post please for more details.

If I'm now gonna settle for Ubuntu 15.04, how about compatibility with all the programs and setting adjustment I did on the 14.04 LTS? Do you think that will be an issue? Or will a user like me barely notice the version upgrade?

---

### Post by furioususer on 2015-04-19
I would like to direct your attention to a video recording I made of something odd happening during the boot: 
[https://www.dropbox.com/s/r5cpg2iwmg4uetz/Sound.mp4?dl=0](https://www.dropbox.com/s/r5cpg2iwmg4uetz/Sound.mp4?dl=0)

Notice how the video starts to shake during a moment? Notice also the loud noise during that same moment? Well, that loud noise is coming from or created by the NUC scaring me to death! I thought something was gonna explode.
When I connect it to the TV via the HDMI then that sound appears when it boots up. When I disconnect the HDMI and just let it boot on its own (with no picture), then that sound is not present. It isn't either present when I connect the NUC to my computer screen. The sound was also present now with 15.04 when I went to Display settings and tinkered with the resolution settings.

**So it seems that my TV and Intel Nuc doesn't like each other? But what and why is that sound? It seems like the TV or NUC is gonna explode.**

---

### Post by oldfred on 2015-04-19
Is it the Ubuntu drum sound and you have volume real high?
I have sometimes had speakers too high as some site was soft, but then back to normal was way loud.

---

### Post by grahammechanical on 2015-04-19
> **jhf85 said:**
> Btw, what is the difference between 14.04 LTS and 15.04?

There is another difference that I do not think has been explained to you. Ubuntu 14.04 is called a Long Term Support (LTS) release because it has 5 years support lasting up to April 2019. Whereas, Ubuntu 14.10 only has support until July 2015 and Ubuntu 15.04 will only have support until January 2016.

So, if you upgrade to 14.10 you will have to upgrade to 15.04 in a few weeks and then upgrade to 15.10 in about 8 or 9  months and then to 16.04 the next LTS release when it comes out in April 2016. That is a lot of upgrading and some of use recommend doing a fresh install each time to avoid the problems that some people have.

If you stay on 14.04 you can upgrade to 16.04 when it comes out. As you have noticed 14.04.2 now has the same hardware stack (kernel and stuff) as 14.10. In August 2015 Ubuntu 14.04.3 will be released and it will have the same hardware stack as 15.04. At that time you will be able to update/upgrade 14.04.2 to 14.04.3. People on this forum will give advice on doing this at the time.

Regards.

---

### Post by furioususer on 2015-04-19
> **oldfred said:**
> Is it the Ubuntu drum sound and you have volume real high?
I have sometimes had speakers too high as some site was soft, but then back to normal was way loud.

Nope. The speakers weren't even connected to the NUC. Although when I boot with the live **USB** I think that the volume is at maximum by default (doesn't HDMI carry audio as well?)... if that can have anything to do with what you are describing? 

What is the "Ubuntu drum sound" btw?

---

### Post by oldfred on 2015-04-19
It used to be just drums, but now seems to be this:
[http://www.techgainer.com/how-to-disable-or-change-ubuntu-startup-sound-at-login-screen/](http://www.techgainer.com/how-to-disable-or-change-ubuntu-startup-sound-at-login-screen/)

---

### Post by furioususer on 2015-04-19
> **grahammechanical said:**
> There is another difference that I do not think has been explained to you. Ubuntu 14.04 is called a Long Term Support (LTS) release because it has 5 years support lasting up to April 2019. Whereas, Ubuntu 14.10 only has support until July 2015 and Ubuntu 15.04 will only have support until January 2016.

So, if you upgrade to 14.10 you will have to upgrade to 15.04 in a few weeks and then upgrade to 15.10 in about 8 or 9  months and then to 16.04 the next LTS release when it comes out in April 2016. That is a lot of upgrading and some of use recommend doing a fresh install each time to avoid the problems that some people have.

If you stay on 14.04 you can upgrade to 16.04 when it comes out. As you have noticed 14.04.2 now has the same hardware stack (kernel and stuff) as 14.10. In August 2015 Ubuntu 14.04.3 will be released and it will have the same hardware stack as 15.04. At that time you will be able to update/upgrade 14.04.2 to 14.04.3. People on this forum will give advice on doing this at the time.

Regards.

Thank you for that explanation! I really appreciate it as a new-beginner. I must admit though that I have read on what LTS means, but I haven't asked the questions I need to ask to fully understand it. So I'll take the chance now if you don't mind.


[LIST=1]
[*]What does this "support" consist of exactly and what is the extent of it? Is it forums like these? Is it a customer service where you call in or mail? And what are the limitations of help after the dates you listed?

I tried 14.10 for example and I stumbled on some bugs (that were reported by others) so I changed back quickly to 14.04. The support I used was Google and asking some questions on sites like these - just like any technical issues really. So I question if this limited support is of consequence to me and others like me? I always imagined it was companies that took advantage of this offered support.
[*]Why offer long term support to one version and not others? I mean, besides the logistic reasons, what is the purpose of releasing new versions and then give them a shorter time-frame for support than you do for an older version? That doesn't make sense from my POV. Are 14.10 and 15.04 supposed to be valued as beta (test versions) or something like that?
[*]Is that it? Is that the only difference between 14.04 and 15.04? One has LTS and the other does not (besides the upgrades of kernel etc). Compatibility issues with older programs and settings that I have set will not be affected negatively by upgrading (or re-installing as you suggested) to 15.04? I seem to recall when I first upgraded to 14.10 some programs didn't keep up... Can this be true? If so, how big an issue/how common is it that you'll run in to these problems when upgrading? So I know what to look forward to if I am to solve the issue I have with the NUC by upgrading permanently to 15.04.
[/LIST]

> In August 2015 Ubuntu 14.04.3 will be released and it will have the same hardware stack as 15.04.
Just to make it perfectly clear for me. With oldfred's help I have understood that 15.04 carried some upgrades that I needed with my very new computer - 14.04.2 and 14.10 didn't have this. When 14.04.3 arrives in August 2015, I will have a LTS version with at least the same upgrades as 15.04?

---

### Post by furioususer on 2015-04-19
> **oldfred said:**
> It used to be just drums, but now seems to be this:
[http://www.techgainer.com/how-to-disable-or-change-ubuntu-startup-sound-at-login-screen/](http://www.techgainer.com/how-to-disable-or-change-ubuntu-startup-sound-at-login-screen/)

Aha. Like I wrote before, I didn't encounter this sound when the HDMI cable was unplugged, and I encountered the sound when I changed the resolution in display. Besides, there isn't a login window when you boot up with a live USB. However I think there is a sound when you change resolution... So I do still wonder if you are on to something. I have to check this one more time. I will report back here.

---

### Post by oldfred on 2015-04-19
[https://wiki.ubuntu.com/VividVervet/ReleaseNotes](https://wiki.ubuntu.com/VividVervet/ReleaseNotes)

As I understand support it means that security fixes and bugs are back-ported to that version. It used to be that the kernel would not have any major version updates with a LTS version, but now they offer the hardware enablement stack or new kernel & support software. But then you still have to keep upgrading that. But then someone with newer hardware can use the last LTS version that may need all those updates.
[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes)

And it used to be that you got no newer versions of any installed software. But I notice with Firefox & Thunderbird instead of backporting security fixes they just install the newer version. But most software is not updated, until you decide to install a newer version. Has to do with lots of testing of newer software with kernels, support software, and all the various configurations of hardware that users have.

---

### Post by furioususer on 2015-04-21
Ok, I tried booting up with 15.04 again, with a live USB, and I lowered the volume and changed the resolution like last time when the thumping sound/noise appeared... and the noise changed... I mean, it's still there but it's lower in volume. I tried muting the audio to see if it would go away completely, it didn't. There's still a noise but less louder, and this is triggered when I change the resolution (I can't say for how long as I turn it off after a minute or so). So the loud noise decreases when I lower the volume (it affects) but is still present when I mute the audio (unaffected)? Eh...? :confused:

What the hell is going on? It's really uncomfortable not knowing what's happening, and will the problem cause any damages to the hardware (and the TV it's connected to)? Did I really solve anything when I lowered the volume and thus lowered the noise or did I just partially hide the problem?

---

### Post by furioususer on 2015-04-21
Btw, what can you expect of the Intel NUC with Ubuntu? Is it "use at your own risk"? In the technical information it says: 
*** Requires an Intel® Ready Mode Technology-enabled system or motherboard, agenuine Intel® processor, and Windows* 7 or Windows 8 OS. Results dependent***

---

### Post by furioususer on 2015-05-30
I wrote earlier: 
*loud noise is coming from or created by the NUC scaring me to death! I thought something was gonna explode.**When I connect it to the TV via the HDMI then that sound appears when it boots up. When I disconnect the HDMI and just let it boot on its own (with no picture), then that sound is not present. It isn't either present when I connect the NUC to my computer screen. The sound was also present now with 15.04 when I went to Display settings and tinkered with the resolution settings.*

*So it seems that my TV and Intel Nuc doesn't like each other? But what and why is that sound? It seems like the TV or NUC is gonna explode."*
[COLOR=#3D3D3D][FONT=intel-clear][B]


AN UPDATE:

[/B][/FONT][/COLOR][COLOR=#3D3D3D][FONT=intel-clear]I returned the device recently. But not before I figured out that the issue was probably with the sound drivers for the new Nuc (even the sound card is a brand new model for the series). Why do I say that? Well, because of 3 reasons:[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]
[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]1. I adjusted the volume on the TV (I don't have a TV-signal and use external speakers so the TV-volume doesn't affect anything normally, so that is why I hadn't thought of it) and the exploding sound turned to a whimper. Up until that point I always plugged in either my headphones to the NUC's 3.5 mm port or my external speakers. I never tried without,** to see if the HDMI cable would deliver sound on its own**. BUT despite me muting the sound with the mute button the whimper was still there... Logically, if the exploding sound was lowered by me lowering the volume, it should have disappeared completely when the sound was muted, but strangely it didn't. 

2. It turns out that the HDMI doesn't carry sound to the TV as it should. There is no audio at all if I don't plug in headphones or external speakers. And yes; I did try another HDMI-cable and HDMI-port on the TV with the same results.[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]
[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]3. I tried an older NUC model (DN2820FYKH) and it worked fine. I put on a youtube video and the sound came out beautifully through the HDMI and in to the TV-speakers, without any external speakers or headphones.[/FONT][/COLOR]


[COLOR=#3D3D3D][FONT=intel-clear]**So my conclusion is that the audio drivers_ through HDMI_ is not working (despite me upgrading to Ubuntu 15.04 and got some other issues solved as displayed in this thread). It works fine through external speakers and headphones though. **[/FONT][/COLOR][COLOR=#3D3D3D][FONT=intel-clear][B]Does this make any sense to some technical person out there? If so, mind explaining it? 
[/B][/FONT][/COLOR]

---

