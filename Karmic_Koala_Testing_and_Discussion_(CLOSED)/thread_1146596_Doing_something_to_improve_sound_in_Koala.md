---
title: "Doing something to improve sound in Koala"
date: 2009-05-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by gnomeuser on 2009-05-02
People like to blame Pulseaudio for all kinds of problems, so for a bit I have given thought on what we can do to make the audio experience nicer for everyone.

The problem seems to break down to several parts, the one I concern myself with is making sure we collect data to indicate which drivers are causing the biggest amount of problems. I consider this the most important problem to deal with since in my experience most problems people experience with Pulseaudio is due to ALSA driver bugs. To fix an issue though we must first know it is there and what the scope is. Pulseaudio already is kind enough to tell us what the problem is in it's logs and we know what hardware and configuration the machine has. We also have apport to help us report problems.

So the proposed solution for this step of the journey towards perfect sound from where I stand would be making it a goal early in the Koala cycle to implement hooks to apport to catch common driver issues like snd_pcm_avail() overflows and get them reported.

Here is the idea on brainstorm:
[[IMG]http://brainstorm.ubuntu.com/idea/19594/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/19594/)

My mantra for the Koala cycle will be no more Pulseaudio hatred threads. I am tired of them, let's fix those issues and bring joy to the world.

*edit*

There seems to be some confusion, this is not intended to be a thread to debate the wider subject of Pulseaudio. This is about a select subset of issues that crash Pulseaudio. It is about creating a stable foundation upon which we can solve those other issues. I will do further postings which will attempt to address those problems later. I think it is important that we focus on as small a set of problems in each thread, it makes it easier to identify a suitable solution.

---

### Post by mdurham on 2009-05-02
May I suggest a bit of rationality. See attached pic. I find it all a bit confusing.

---

### Post by Nullack on 2009-05-02
Yeah good stuff, apport should collect any and all information it needs to diagnose audio problems.

---

### Post by BwackNinja on 2009-05-02
I agree entirely, what probably makes audio problems the worst is that they are so disorganized. That's just looking at pulseaudio and alsa, then theres everything else, all the other layers that can go on top of that.

At least its moving forward, but it would be nice for everything to be able to be configured in _one_ place, and especially if that configuration dialog didn't miss out on any important options. A lower latency kernel would be nice too, right now I can't use "glitch-free" and I liked that a lot more when it was working well.

---

### Post by pbpersson on 2009-05-03
When I had sound problems I went through some tutorial on the forum and I had to adjust things in six different places and three of them had not even been installed.

Now those control panels are scattered all throughout my system.  There are four system sound control panels in "Sound and Video" main menu.

I agree that all this should be in one control panel, it should all be installed by default, and it should be in a logical place such as System-->Administration-->Sound

---

### Post by gnomeuser on 2009-05-03
> **mdurham said:**
> May I suggest a bit of rationality. See attached pic. I find it all a bit confusing.

I am unsure what your point is. You open up a series of programs with redundant functionality.. so?

Including some that aren't even installed by default, eventually once Pulseaudio is stable (in reality ALSA) is stable for everyone we will be able to just ship the new volume controller.

---

### Post by mdurham on 2009-05-03
> **gnomeuser said:**
> I am unsure what your point is. You open up a series of programs with redundant functionality.. so?

Including some that aren't even installed by default, eventually once Pulseaudio is stable (in reality ALSA) is stable for everyone we will be able to just ship the new volume controller.
Hi gnomeuser, which are redundant? All I wanted to do was record my voice from the usb mic. I followed varios forum advice and ended up with all this. If they aren't necessary and are redundant, why are they in the repo?

So two questions gnomeuser, if you wouldn't mind answering:
1: which are redundant?
2: why are they in the repo?

Cheers, Mike

---

### Post by crjackson on 2009-05-03
> **gnomeuser said:**
> I am unsure what your point is. You open up a series of programs with redundant functionality.. so?

Including some that aren't even installed by default, eventually once Pulseaudio is stable (in reality ALSA) is stable for everyone we will be able to just ship the new volume controller.

This is what I really pray for. I'm really not that great at tweaking sound and it's a laborious process for me. I just spent hours figuring out how to get a mic to record using Audacity. Finally got it sorted... But what a chore...

I don't mind so much if it's on my own machine but I'm shipping this system 2K miles next week and pressed to get it working. Sound used to be easier in my opinion.

---

### Post by golusweet on 2009-05-03
I agree, Audio Experience should be improved in koala.

---

### Post by taavikko on 2009-05-03
@gnomeuser,

Shouldn't this idea serve more purpose when forwarded to ubuntu-devel mailing-list?

As to my understanding, when brainstorm idea gathers enough points it is just then presented to dev's?


But agree on fixing audio issues once and for all.
most issues seems to be with laptops, might be some idea to add some rules to udev, that when it detects model it creates a rules
that users don't have to modify alsa-base.conf 

since ALSA provides documentation "/usr/share/doc/alsa-base/driver/ALSA-Configuration-txt-gz"

---

### Post by gnomeuser on 2009-05-03
> **taavikko said:**
> @gnomeuser,

Shouldn't this idea serve more purpose when forwarded to ubuntu-devel mailing-list?


The sad fact is that a very large part of the developers have been scared off the public mailing list by users who increase the signal to noise ratio with pointless flamewars and issuing support requests. People who treated the mailing lists like these forums.

You can thus no longer be guaranteed that the correct developer will actually be listening if you post on the mailing lists. The mailing lists are also painfully quiet, I am on pretty much every single one of them and it's like watching tumbleweeds in a ghost town. Only the kernel list actually has any meaningful activity and still only a few mails a day.

It tends to anger me when stupidity hurts openness.

---

### Post by taavikko on 2009-05-03
> **gnomeuser said:**
> The sad fact is that a very large part of the developers have been scared off the public mailing list by users who increase the signal to noise ratio with pointless flamewars and issuing support requests. People who treated the mailing lists like these forums.

.
.
It tends to anger me when stupidity hurts openness.

Devel-list is moderated, so not much cruft shouldn't go through.
Haven't seen much of this stupidity in which you referred,
Though, ubuntu-members are free to post, so maybe members are the ones to misuse it? 
Maybe we have different standards..

Such as the brainstorm is moderated, your's still waiting for acceptance
But as for your idea, I'm all for it. Sad that for now, only few people will see it, and fewer will click it. And as this dev-cycle continues, this thread will probably fade in the midst of oblivion :(
So might take a while for it to grow popular enough.
when the issue needs to addressed as much as possible. Hence my comment on forwarding it "also" to devel-list.

---

### Post by BwackNinja on 2009-05-03
I disagree that they are all entirely redundant, each properties and preferences dialog can do something that none of the others can, other than gnome-volume-control-settings (the new pulseaudio volume control).

-gnome-volume-control-settings encompasses much of what all the others do, but
-gnome-sound-properties allows you to choose which tracks the volume control keys on your keyboard control and choose your own sounds for a sound theme
-pavucontrol allows you to switch between different sound outputs, such as 5.1, stereo, and 4.0 surround sound and can change which output a particular application goes to, unlike gnome-volume-control-settings
-gnome-volume-control allows you to change the volume of different tracks and add mic boost among other settings, and allows you to use various surround sound setups if you're using pure alsa.
-paprefs allows for some configuration of pulseaudio that would otherwise have to be done in the files.
-pavumeter, even though it isn't shown in the screenshot, would show how sound is going out of each speaker, and in conjunction with a rousing run of a nice, terminal-only utility speaker-test would make you realize that downmixing of lfe is off by default, so in my 4.0 surround sound setup, which is comprised of 2 sets of 2.1 speakers, I didn't get the bass that I should've.
-daemon.conf, which I had to edit because, despite the vast number of configuration dialogs, none of them exposed that option

I wish they were all simply redundant, but each one does things others don't, with the exception being the one that we're hoping will do everything. What's worse is that some of the dialogs have options that you're likely to set only _once_.

---

### Post by Reiger on 2009-05-03
Ugh just seen that screenshot... Then I guess that's handled rather better in KDE using the KMix plasmoid/applet thing: simple series of tabs per I/O device (if you have for instance a HDMI port on your Graphics card it'll be listed too), and you can from the Configure menu -> Configure Channels select which channels you want to show or hide. Adjusting volumes becomes easy as pie. :P

---

### Post by | MM | on 2009-05-04
Going by what has been said on p.go. i think a lot of the PA issues are to do with kernel compile-time configuration and subsequent latencies that PA does not like.

As for the GUI, i agree the functionality needs to be merged into a single utility that covers all audio related configuration, i.e, specify hardware settings, speaker settings, surround sound, volume/recording levels etc.

---

### Post by Gina on 2009-05-04
Yes, I think until we get just the one unified sound control dialog, sound will always be a problem in Ubuntu.  I believe this is the one thing above all others that needs to be addressed.

---

### Post by Geekkit on 2009-05-04
> **gnomeuser said:**
> People like to blame Pulseaudio for all kinds of problems, ...


While I don't have a hatred for pulse audio (or any other software component for that matter), I do find it a disappointing addition for two reasons: 

1) It has done something funky to Skype which is to make the sound lag horribly making the chat from me look like a poorly dubbed movie.

2) Not having to perform extra configuration (in the form of downloads including the pulse audio applet) for inputs/outputs which I had to do in order to be able to record voice.

While I have no proof that it was pulse audio, it seems to be one of the things that changed from the previous version of Ubuntu.

---

### Post by galileon on 2009-05-04
> **mdurham said:**
> Hi gnomeuser, which are redundant? All I wanted to do was record my voice from the usb mic. I followed varios forum advice and ended up with all this. If they aren't necessary and are redundant, why are they in the repo?

So two questions gnomeuser, if you wouldn't mind answering:
1: which are redundant?
2: why are they in the repo?

Cheers, Mike

+1 for that. Also, Alsa worked fine after years of OSS suffering.

---

### Post by gnomeuser on 2009-05-04
> **Geekkit said:**
> While I don't have a hatred for pulse audio (or any other software component for that matter), I do find it a disappointing addition for two reasons: 

1) It has done something funky to Skype which is to make the sound lag horribly making the chat from me look like a poorly dubbed movie.

2) Not having to perform extra configuration (in the form of downloads including the pulse audio applet) for inputs/outputs which I had to do in order to be able to record voice.

While I have no proof that it was pulse audio, it seems to be one of the things that changed from the previous version of Ubuntu.

1) is most certainly Skype using the ALSA API wrong, this problem is well documented, however Skype as company doesn't care about Linux as is evident from the lack of updates and the fact that the Linux version is trailing the Windows one.

2) Should be handled in the new volume controller in GNOME, however Ubuntu has decided that isn't ready yet. I agree this is unfortunate.

However what EVERYONE here is seems to be not doing is reading the OP, this is SOLELY about handling the ALSA driver bugs PA exposes. It is not about configuration GUIs, it's not about all the corner cases that aren't handled. Why isn't it? Simple, because to handle all of those issues (if they indeed are issues, which largely depends on how you look at it) we need people to be able to rely on PA to work in it's preferable configution (namely glitch free operation mode). To do this there are a ton of driver bugs to work out.

Once the driver situation is under control, and only then, do we have a reasonable chance of designing a solution that will be remotely workable.

So Everyone please make an effort to understand the exact topic of interest. It is a step by step problem and we need to first get everyone on Pulseaudio without having the daemon be crashed by some ALSA bug (and I have spotted these in every driver I have the ability to test). Once we have a solid foundation then we can more easily address other issues. This is why PA exists, and to even find all these real world problems and decide on the greatest common benefactor solution to them - widespread testing is important, to do this.. NOT crashing seems important.

Whipping the audio stack properly into shape is going to take a long time, it is not something we can do on the side and it is going to be painful.

---

### Post by plun on 2009-05-04
> **gnomeuser said:**
> 

Whipping the audio stack properly into shape is going to take a long time, it is not something we can do on the side and it is going to be painful.

No I don't think so.....

Alsa 1.0.19 is delivered today for Karmic and 1.0.20 is coming.

Alsa bugs are known  (HDA Intel issues)

PA 9.0.15 was delayed until its was too late to use it within Jaunty....:confused:  Nevertheless a big improvement.

I believe that within a few weeks we have a much more stable sound-stack including Skype....

This is mainly a giant upstream mess with **stubbard developers without coordination**.

But now all puzzle pieces fits better.... (also no debian freeze)


PS Kernel issues with timings and delays must also be checked DS

---

### Post by gnomeuser on 2009-05-04
> **plun said:**
> No I don't think so.....

Alsa 1.0.19 is delivered today for Karmic and 1.0.20 is coming.

Alsa bugs are known  (HDA Intel issues)


If you think the issue of ALSA driver bugs is solved then you are mistaken. I have bugs pending against several ALSA drivers for the very same problem.

Intel HDA is fixed and that was a big pain point since it's so widely deployed but e.g. the snd_usb_audio driver has the very same problem. Since pulseaudio tells us what the problem is putting apport hooks into the codebase will not only tell us what drivers need fixing now but ensure that regressions are caught during development cycles once the initial problems are fixed.

It is going to be painful, lots of applcations need fixing, lots of drivers. Pulseaudio itself is a surprisingly stable codebase but the whole ecosystem around audio really is in a sorry state. You are making a misjudgement if you think it is all going to be fixed in Koala. A lot will be, perhaps to the point where things will be usable for most people but the journey to the day when audio just works will take much longer.

---

### Post by tawmas on 2009-05-04
> **gnomeuser said:**
> You are making a misjudgement if you think it is all going to be fixed in Koala. A lot will be, perhaps to the point where things will be usable for most people but the journey to the day when audio just works will take much longer.

OTOH, it looks like the powers that be are taking a stance to finally fix sound issues. I mean, Canonical posted a  job position for a [Desktop Architect - Sound Experience]("http://webapps.ubuntu.com/employment/canonical_DASE/"):

> You want sound to Just Work on the Ubuntu desktop, and you want it to stay working for all of your friends and family, release after release, without any issues. You want to be able to improve the sound configurations in widespread use even after a release, and you want to make it very easy for people to use the system, diagnose problems and recover when things break. As a member of the Desktop Experience Team, the role consists in designing and developing the sound software stack for the Linux desktop, from drivers to audio applications, with a particular focus on providing the user with a consistent set of configuration interfaces.

The job was posted in April... Let's hope it bears some fruits in time for KK, although perhaps LL is a more plausible target.

---

### Post by plun on 2009-05-04
> **gnomeuser said:**
> 
It is going to be painful, lots of applcations need fixing, lots of drivers. Pulseaudio itself is a surprisingly stable codebase but the whole ecosystem around audio really is in a sorry state. You are making a misjudgement if you think it is all going to be fixed in Koala. A lot will be, perhaps to the point where things will be usable for most people but the journey to the day when audio just works will take much longer.

The last year has been a version-mismatch between the kernel, alsa, pulseaudio and in the end Gnome....

For Ubuntu also "the sleeping old lady, Debian "....:)

Involved devs seems to have missed to communicate between these projects..


I am rather sure that its possible now to make something much better.

Lets see...:)

---

### Post by taavikko on 2009-05-04
C'mon guys, 600< views on this topic, and only 10 votes on brainstorm.

I strongly suggest that any ubuntu member that reads this, should raise this on ubuntu-devel list?

Thanks, off to watch Finns beat Canucks in hockey :)

---

### Post by Maduroutmb on 2009-05-04
The ironic thing for me is that I have had more luck with hardware (mainly sound, but also Wacom tablets) in Ubuntu than in Vista.  I have used M2N32-SLI onboard sound and M-Audio Revolution 5.1 sound without issue.  My only problem has been in getting recording to work.  Again, I find that ironic because the final straw that led me to adopt Ubuntu was the fact that my Creative card would not let me record sounds in Vista despite the fact that it was officially supported (i.e. buttons from the web tutorial simply were not present in the actual pop up boxes).

My point is that hardware support in Ubuntu is actually very good compared with Vista, and it's nothing short of amazing considering that the hardware makers care if their stuff works with Microsoft's one "distribution".  I realize that if your sound won't work, the percentage of happy users doesn't matter because the problem affects 100% of you.  However, given the success that Ubuntu already enjoys, I think that the next step really depends upon adoption and subsequent hardware support.

---

### Post by smbm on 2009-05-04
> **taavikko said:**
> C'mon guys, 600< views on this topic, and only 10 votes on brainstorm.

Voted

---

### Post by Slug71 on 2009-05-04
Voted :P

---

### Post by Slug71 on 2009-05-04
Wow, 728 views and only 16 votes :(:confused:

Not cool! 
Everyone that has viewed this thread should go and vote.
This is to better Ubuntu/Linux.

---

### Post by markbuntu on 2009-05-04
Including pavucontrol in the desktop seed would go a long way to soothing a lot of the anger at pulseaudio. It would probably also help a lot if the sound was actually configured to use puseaudio OOB which has not been done in the last three releases.

It is really sort of amazing to me that this was not done in Intrepid or Jaunty.

---

### Post by gnomeuser on 2009-05-05
> **markbuntu said:**
> Including pavucontrol in the desktop seed would go a long way to soothing a lot of the anger at pulseaudio. It would probably also help a lot if the sound was actually configured to use puseaudio OOB which has not been done in the last three releases.

It is really sort of amazing to me that this was not done in Intrepid or Jaunty.

This is NOT what this is about, this is about getting the foundation on which we lay PA stable and ensure that regressions are caught in the future.

Please read the OP. This is NOT a Pulseaudio bashing thread, it is NOT a thread for airing your ideas to fix volume sliders. This IS a thread for dealing with a specific set of bugs that crash Pulseaudio.

Once it has been assessed if this will work, I will do further threads that are more end user minded (the topics will be Applications and User Experience) but it is not the time to unleash those yet.

---

### Post by tawmas on 2009-05-05
> **taavikko said:**
> C'mon guys, 600< views on this topic, and only 10 votes on brainstorm.

I'd like to vote, but it asks me to create yet another account. I guess I'll participate in Brainstorm when it will accept my Launchpad login. :-(

---

### Post by Gina on 2009-05-05
Maybe it needs a separate registration - just use your usual name and Launchpad password and create an account if you haven't got one :)

I've just voted in favour :)  Had to redo my password but that was simple enough :)

---

### Post by taavikko on 2009-05-05
> **Gina said:**
> Maybe it needs a separate registration - just use your usual name and Launchpad password and create an account if you haven't got one :)



Think canonical needs to push it's idea of openid login more.
LP account should be sufficient, but this needs to be raised in appropriate channels, since atm it isn't.

---

### Post by Gina on 2009-05-05
Agreed!!  I thought they were the same but evidently not - it's some time since I created my accounts.

---

### Post by taavikko on 2009-05-05
totally offtopic, after the upgrade to alsa 1.0.19
my hp-dv5 laptop no longer needs quirks to work
(modding alsa-base.conf)

But still, this audio mess that linux suffers needs to be sorted out all together.

---

### Post by melalcoolique on 2009-05-05
Voted.

On a side note, Pulseaudio has been updated this morning.

[https://lists.ubuntu.com/archives/karmic-changes/2009-May/000482.html]("https://lists.ubuntu.com/archives/karmic-changes/2009-May/000482.html")

---

### Post by Saint Angeles on 2009-05-05
i have an M-Audio Fasttrack USB external audio interface. until Jaunty, I would always have to set-up my sound with ALSA (pulseaudio did not work). the problem with the ALSA config was I couldn't play more than one sound source at a time, and sometimes, a program would steak sound focus.

what i mean is, if i opened a website with flash and i got lucky and the sound actually worked, to use my sound in rhythmbox or something, i would have to close firefox so it would "let go" of the sound, then open up rhythmbox.

but with Jaunty, pulseaudio works beautifully. I can play several sounds at once (youtube videos, rhythmbox, totem...) and zero configuration was needed. it even worked off the live CD. so did my ATI card and madwifi wireless card for that matter.

this is super duper progress.

---

### Post by Geekkit on 2009-05-05
> **gnomeuser said:**
> 1) is most certainly Skype using the ALSA API wrong, this problem is well documented, however Skype as company doesn't care about Linux as is evident from the lack of updates and the fact that the Linux version is trailing the Windows one.

The problem with this perspective though is that not all software companies are interested in a six-month development cycle - especially for what they might consider a public service for the squeaky wheels of the bunch.

You have to remember, they are a corporation and they are trying to make money. If this public service looks like too much of a money pit because how they plug into the sound framework has now been completely revamped (i.e. from ALSA to Pulse Audio), they'll just stop playing ball as it were.

Just my two cents. I'll shut up now since this is off topic.

---

### Post by tawmas on 2009-05-05
> **Gina said:**
> Maybe it needs a separate registration - just use your usual name and Launchpad password and create an account if you haven't got one :)

Indeed, it needs a separate registration, and I already have more accounts than I feel like I can manage... Besides, it asks for your "Ubuntu QA" password, which initially made me think I just wasn't entitled to vote as I'm not a member of the Ubuntu QA Team. Only on my second visit did I realize I could actually sign up for an account.

But that's just off-topic noise, for which I apologize. If anybody can suggest me a more appropriate place to open a useful discussion on these topics, please feel free to PM me.

Going back to waiting for alpha 1 :-)

---

### Post by amano on 2009-05-05
What do you think?

I would give the glitch-free mode of pulseaudio another chance for this cycle and if still too many drivers break, they shall turn it off for the beta again. 

But if it's not tested, the Alsa drivers won't get fixed...

---

### Post by zekopeko on 2009-05-05
> **Geekkit said:**
> The problem with this perspective though is that not all software companies are interested in a six-month development cycle - especially for what they might consider a public service for the squeaky wheels of the bunch.

You have to remember, they are a corporation and they are trying to make money. If this public service looks like too much of a money pit because how they plug into the sound framework has now been completely revamped (i.e. from ALSA to Pulse Audio), they'll just stop playing ball as it were.

Just my two cents. I'll shut up now since this is off topic.

what are you talking about??? skype could be fixed if ebay cared for skype to work in linux.

---

### Post by ktp on 2009-05-05
> **tawmas said:**
> I'd like to vote, but it asks me to create yet another account. I guess I'll participate in Brainstorm when it will accept my Launchpad login. :-(

I was wondering the samething...yet another login.  Why isn't it integrated with Launchpad login system?

---

### Post by vishalrao on 2009-05-05
I remember late during Jaunty dev cycle in the discussion forums it was mentioned Fedora has low-latency (?) enabled in their kernel which helps pulseaudio (glitch-free?) work better. It was too late to enable it for Jaunty, but I wonder if devs will think about it for Karmic for some sound goodness... and I believe the user desktop is also more "responsive" with this option?

edit: ah found the mailing list post by lennart: [https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-February/003150.html](https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-February/003150.html)

> Apparently OpenSUSE ships a kernel (2.6.27.7-9-pae) that causes
scheduling latencies of > 210ms. That is a lot. That is really really
really a lot. Other non-Fedora distributions apparently do something similar.

The parameters in the glitch-free logic are tuned for Fedora-kernels
that easily give latencies of 5ms or so.

---

### Post by plun on 2009-05-06
Pulseaudio 9.0.15 was uploaded today to Karmic.:)

I am also testing alsa 1.0.20 without trouble.


Maybe we also needs better test-routines for audio  ??
(like a protocol)


I can "see the light"....

---

### Post by markbuntu on 2009-05-06
> **vishalrao said:**
> I remember late during Jaunty dev cycle in the discussion forums it was mentioned Fedora has low-latency (?) enabled in their kernel which helps pulseaudio (glitch-free?) work better. It was too late to enable it for Jaunty, but I wonder if devs will think about it for Karmic for some sound goodness... and I believe the user desktop is also more "responsive" with this option?

edit: ah found the mailing list post by lennart: [https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-February/003150.html](https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-February/003150.html)

As of the pulse0.9.15 that was accepted it appears that this will not happen since tsched=0 is set. This disables glitch free which means the kernel is not up to it. Hopefully something will be done bit I am skeptical since setting HZ=1000 and PREEMPT in the kernel will probably break a lot of stuff.

---

### Post by rockin_goliath on 2009-05-06
I totally agree with you, gnomeuser. It's time to hammer out these alsa bugs once and for all so we can move forward with audio on the linux desktop!

---

### Post by Starks on 2009-05-06
> **plun said:**
> Pulseaudio 9.0.15 was uploaded today to Karmic.:)

I am also testing alsa 1.0.20 without trouble.


Maybe we also needs better test-routines for audio  ??
(like a protocol)


I can "see the light"....
Is there an alsa 1.0.20 ppa?

---

### Post by 23meg on 2009-05-07
There's already [an Apport hook for PulseAudio]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/357913").

---

### Post by plun on 2009-05-07
> **Starks said:**
> Is there an alsa 1.0.20 ppa?

I haven't seen any yet but its a standard compilation for Alsa.

driver, lib and utils is enough for the majority.

--------

about "hammering" alsa bugs... changelog for 1.0.20 is a big one.

[http://www.alsa-project.org/main/index.php/Changes_v1.0.19_v1.0.20](http://www.alsa-project.org/main/index.php/Changes_v1.0.19_v1.0.20)

Hopefully Debian is fast with an unstable upgrade.

---

### Post by Bios Element on 2009-05-07
> **zekopeko said:**
> what are you talking about??? skype could be fixed if ebay cared for skype to work in linux.

No one said they couldn't...It's a matter of caring and they don't. Thus I propose we don't care about skype and push for a better native solution.

---

### Post by gnomeuser on 2009-05-07
> **23meg said:**
> There's already [an Apport hook for PulseAudio]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/357913").

It does not appear to catch the situations I am concerned about, namely the cases where the underlying ALSA driver gives us wrong information.

---

### Post by 23meg on 2009-05-07
> **gnomeuser said:**
> It does not appear to catch the situations I am concerned about, namely the cases where the underlying ALSA driver gives us wrong information.

Do you have any concrete examples of cases it fails to catch? If I'm reading you correctly (you've not been very specific), such things are more likely to be addressed by the ALSA hook. You can have that hook run on an existing PulseAudio bug and have the information automatically posted to it too, by instructing the tester to issue ```
apport-collect -p alsa-base #bugnumber
```.

---

### Post by plun on 2009-05-07
Perhaps its also possible to make the Alsa info-script even easier
for users with trouble  ?

[http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)

A binary/deb-file with a launcher....

---

### Post by 23meg on 2009-05-07
> **plun said:**
> Perhaps its also possible to make the Alsa info-script even easier
for users with trouble  ?

[http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)

A binary/deb-file with a launcher....

The ALSA Apport hook provides nearly all the information provided by that script. That's "even easier".

---

### Post by plun on 2009-05-07
> **23meg said:**
> The ALSA Apport hook provides nearly all the information provided by that script. That's "even easier".

OK....

It would be nice to have comments from Crimsum and/or TheMuso about this.

I believe that the situation now is better then for a long time.  

Just to find a good way to find bugs and also most important, **bring bugs upstream from Ubuntu.**

---

### Post by gnomeuser on 2009-05-07
> **23meg said:**
> Do you have any concrete examples of cases it fails to catch? If I'm reading you correctly (you've not been very specific), such things are more likely to be addressed by the ALSA hook. You can have that hook run on an existing PulseAudio bug and have the information automatically posted to it too, by instructing the tester to issue ```
apport-collect -p alsa-base #bugnumber
```.

My setup has been known to experience death by snd_pcm_avail() overflow and apport hasn't caught it and popped up to let me inform the fine ALSA developers. So either this is not in Jaunty (or early versions of Koala - I haven't updated in a few days) or it doesn't work as I intended in the proposal.

While this is not a crasher as such, the actual crash in PA will typically occure long after the snd_pcm_avail overflow. We do not want to report the crash but the overflow.

---

### Post by markbuntu on 2009-05-09
> **gnomeuser said:**
> My setup has been known to experience death by snd_pcm_avail() overflow and apport hasn't caught it and popped up to let me inform the fine ALSA developers. So either this is not in Jaunty (or early versions of Koala - I haven't updated in a few days) or it doesn't work as I intended in the proposal.

While this is not a crasher as such, the actual crash in PA will typically occure long after the snd_pcm_avail overflow. We do not want to report the crash but the overflow.

I don't think that apport is really capable of catching anything but an actual crash. You would need to run pulse with gdm and catch the snd_pcm_avail() overflow with a backtrace. Lennart would definitely be interested in that.

---

### Post by fballem on 2009-05-09
If I'm totally off base here, then please let me know. I have been using ubuntu for about a year, currently using ubuntu 9.04.

In order to get Pulse audio working correctly, and get the correct control installed in my panel, I had to do all of the stuff that is described in this post:

[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html#more-1301](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html#more-1301)

For koala, I would want this to be a whole lot simpler. If the powers that be have decided the Pulse Audio is the way to go, then that's fine. It has to be simple for the rest of us!

I like the idea of catching the bugs at the various layers. I understand the need for various layers. For koala, as an end user, the setup and configuration of sound has to be very easy.

Thanks,

---

### Post by gnomeuser on 2009-05-10
> **markbuntu said:**
> I don't think that apport is really capable of catching anything but an actual crash. You would need to run pulse with gdm and catch the snd_pcm_avail() overflow with a backtrace. Lennart would definitely be interested in that.

I can't really think of any good reason that would prevent us from adding a bit of code to pulseaudio when the overflow situation happens to signal apport - it should be technically possible. After all you don't have to be a crash to be interesting and I hope that has been taken into account. If Apport absolutely requires us to crash then we add a crasher there and grab the information we need (not as insane as it sounds, considering the fact that pulseaudio is near guaranteed to crash moments later).

---

