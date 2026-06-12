---
title: "Horribly broken video playback with nvidia"
date: 2009-03-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Mr. Picklesworth on 2009-03-22
Running nvidia with the 180 series drivers (which provide hardware accelerated video decoding when supported). Video playback is impossibly useless. Video frequently freezes for long periods, occasionally audio does as well and the two become completely out of sync even against the system's best efforts to fix the situation. Mplayer claims my system is too slow in its output. My 2.20 gHz T7500 processor and 8600M GT should not be too slow.

I have tried Totem and Mplayer and all sorts of things in between, and they all exhibit the exact same problem.

Anyone else experienced this? Is it an nvidia problem or something else?

Edit:
In typical fashion (realizing a solution RIGHT AFTER posting) I went to sound preferences and changed to OSS for sound playback in music and movies. Seems to have fixed the problem. Waiting hopefully for the fix to Jaunty's PulseAudio issues :)

---

### Post by Darkshade on 2009-03-22
Are you also running compiz or metacity with compositing?

---

### Post by phenest on 2009-03-22
I too am having the same issues. I'm using Metacity instead of Compiz for compositing, but I don't think that's the issue. I don't think it's the driver neither. I am having problems with sound and I think it's due to Pulse Audio. If I play a video with no audio, it plays perfectly.

---

### Post by ronacc on 2009-03-22
running the 180.37 driver here on amd64 with a 7600gs , I just played a video (wmv) with movie player and both sound and video were flawless , no freezes ,skips, frame drops or stuttering .

---

### Post by olskar on 2009-03-22
I have the same problem with nvidia and it indeed looks like pulseaudio is to blame

---

### Post by plun on 2009-03-22
> **olskar said:**
> I have the same problem with nvidia and it indeed looks like pulseaudio is to blame

If possible can you please give a URL for a test ?

Within nVidias forum there are a lot of "trolling" and "mission impossible" bugs, easy to recognise.

Or file a bug:
[http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678)

---

### Post by zekopeko on 2009-03-22
here is the bug report. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627)

if you have an account on launchpad mark that the bug is affecting you.

---

### Post by Mr. Picklesworth on 2009-03-22
Thanks for the link, zekopeko!

I suspected that bug wasn't the same as mine since it describes slightly different symptoms, but reading it again I think it is.

---

### Post by Darkshade on 2009-03-22
> **phenest said:**
> I too am having the same issues. I'm using Metacity instead of Compiz for compositing, but I don't think that's the issue.

Well I only asked because sometimes when I'm watching a movie with Compiz on it freezes for a couple of seconds and then continues playing, which doesn't happen with Metacity (without compositing, haven't tried with).

---

### Post by zekopeko on 2009-03-22
> **Mr. Picklesworth said:**
> Thanks for the link, zekopeko!

I suspected that bug wasn't the same as mine since it describes slightly different symptoms, but reading it again I think it is.

perhaps we should change the title summary. any suggestions?

Something like: "Pulseaudio brakes audio/video with desyncing,crackling sound and termination of streams on seek"

it would be nice if people that have LP accounts would flag the bug as "it affects me" and would provide alsa output (read this post for the script: [http://ubuntuforums.org/showpost.php?p=6922491&postcount=36](http://ubuntuforums.org/showpost.php?p=6922491&postcount=36)).

The bug still has undecided importance and i don't know if anybody is looking at it. or it could be that the bug report i posted here is a duplicate. but nobody flagged it as such.

anyway, any ubuntu devs here to shed some light on this crippling bug?

---

### Post by plun on 2009-03-22
Well. I am on Alsa 1.0.19 from the Musos ppa and it works just fine.

I don't know if its a Debian problem (again) or whats keeping Ubuntu from upgrading to this version....:confused: 

Or to be stubbard....;)

---

### Post by Nullack on 2009-03-22
Can someone host a sample for me to try and replicate? You can use the DD command to cut down a video into a small section.

I havent experienced any problems so far.

---

### Post by vishalrao on 2009-03-22
You fine folks answered dtchen/crimsun's call for testing? See bug [lpbug]330814[/lpbug] for a test kernel at [http://kernel.ubuntu.com/~dtchen](http://kernel.ubuntu.com/~dtchen) which fixes the crackling/dropping sound for me :)

---

### Post by Mr. Picklesworth on 2009-03-23
Running that kernel now. Audio is much better. I still seem to get the occasional pop. Could be placebo effect. Video playback still completely broken, but slightly less so (since it doesn't crackle). This confirms these are distinct problems. Now the video playback just gets out of sync after jumping to a point in the video and gstreamer struggles helplessly to keep it organized.

Edit:
I take back my claim that audio was improved. It crackles whenever there is a spike in CPU consumption in a way that doesn't feel acceptable. Granted, this could also be blamed on the fact that programs these days are taking way too many liberties with their CPU time.

On this line of thinking, I just set my CPU policy to Performance (cpufreq applet is awesome!) instead of ondemand, which someone on Planet GNOME claims is broken.
Indeed, that acted as a workaround. Slightly scary... clock is ticking.

Seeking in videos still causes major synchronization issues, but it doesn't behave in quite as panicced a way when it has unconditionally full-powered CPUs to work with. Feels a bit more normal. Hm...

---

### Post by Nullack on 2009-03-23
We cant help you unless you host a specific sample your having problems with

---

### Post by phenest on 2009-03-23
> **Nullack said:**
> We cant help you unless you host a specific sample your having problems with

Well, for me, it's all my videos. And lots of different formats.

---

### Post by Nullack on 2009-03-23
Right, so the container type is? the codec is? it uses what type of stream options? Your using gstreamer and totem? etcetc

---

### Post by Mr. Picklesworth on 2009-03-23
Okay, this happens with everything, as phenest says. There is no pattern in my videos. For bigger ones it's noticeable. One example is any of the TED talks, for example:
[http://www.ted.com/index.php/talks/bruce_mccall_s_faux_nostalgia.html](http://www.ted.com/index.php/talks/bruce_mccall_s_faux_nostalgia.html)
Just download the MP4 (it's what I have) and enjoy :)

(I'm sure you can understand it took me a while; I had to think of something where sharing would not break copyright laws).

---

### Post by Nullack on 2009-03-23
In most countries its legal to distribute small samples for engineering purposes.

Anyway, can you please install the current nvidia pre-release 180.41 to start off debugging. It fixes known issues in the current release.

---

### Post by phenest on 2009-03-23
Why are we targeting the video driver? This is a Pulse issue. When video playback is problematic, it's the sound that is screwed up. I get problems with Rhythmbox, event sounds, even espeak. If I kill pulseaudio, the issue vanishes.

---

### Post by Mr. Picklesworth on 2009-03-23
Indeed, as I mentioned in my first post, switching temporarily to OSS (or otherwise skipping PulseAudio) worked around the problem.

Thanks for the interest, Nullack!

---

### Post by Mr. Picklesworth on 2009-03-23
Oookay, the comments are rather interesting: [http://jasondclinton.livejournal.com/72910.html](http://jasondclinton.livejournal.com/72910.html)
I'm suspicious now, although it may be completely unrelated.

Sorry, I guess this thread has turned into duplicate "pulseaudio issue" discussion.

---

### Post by morryis on 2009-03-23
I could not find any pattern in the videos which cause that stuttering or slow-motion playback, nor in the situations in which this bug occurs. A certain video might be played several times without complaint, the next time this video crackles again. This bug is very difficult to reproduce.

---

### Post by Nullack on 2009-03-23
The thing is guys, that the NVIDIA driver is much more than a video driver. It replaces large portions of X, and sets up GPU memory management, a whole bunch of things including tainting the kernel.

As I said there is changes in the 180.41 driver which might be related and I suggest its worth a shot. Especially considering I also have this hardware yet I dont replicate the problems you all are reporting.

---

### Post by Mutiny32 on 2009-03-23
The only issue I'm having is that Sync to VBlank doesn't seem to work as evidenced by tearing in full-screen video playback.

---

### Post by phenest on 2009-03-25
> **Nullack said:**
> The thing is guys, that the NVIDIA driver is much more than a video driver. It replaces large portions of X, and sets up GPU memory management, a whole bunch of things including tainting the kernel.

As I said there is changes in the 180.41 driver which might be related and I suggest its worth a shot. Especially considering I also have this hardware yet I dont replicate the problems you all are reporting.

I just happened to have a copy of nVidia's driver version 185.13, so I've installed it. Result: The problem persists.

---

### Post by amano on 2009-03-25
That doesn't necessarily mean that the fix isn't included within 180.41 since that is the latest kernel shipped by nvidia.

The (much) higher number doesn't mean that it includes the most current fixes.

---

### Post by phenest on 2009-03-25
I realise that. But that was just the driver I had to hand. I've since downloaded and installed 180.41 and will report shortly.

---

### Post by phenest on 2009-03-25
With the 180.41 driver, there is no change.

I am still not convinced this is a video problem, but is a Pulse issue. Perhaps you have a different audio setup to me, Nullack?

---

### Post by taavikko on 2009-03-25
+1 For the audio problem causing this.

Seems to me that when ever audio get's lost and tries to sync it, image goes choppy and cpu usage jumps through the roof...

Just a side note:
While using smplayer (audio : pulse, video : xv)
Everytime I press pause, and play again, audio stops.

Should suspect that when PA issues are sorted, this issue is solved? :)

---

### Post by Hairy_Palms on 2009-03-25
i see the same issues in multimedia playback in addition it also happens when seeking in audio players banshee and rhythmbox, which in my understanding writes the video driver out of the equation, and as confirmed above a complete purge of all pulseaudio packages from synaptic + a reboot fixed it.

Nvidia 7600GS and core2duo

---

### Post by morryis on 2009-03-27
Yes, it happens with all applications which play back audio. If the video starts to jump i.e. goes choppy, there is usually a scratching noise at first. And it happens regardless of the used video driver.

Beside applications using gstreamer I also noticed errors with flashplugin-nonfree, zattoo, vlc and audacious.

---

### Post by aamukahvi on 2009-04-13
I have the same problem with video playback: out of sync, lagginess. Audio doesn't scratch though. I have tried it with Compiz on/off, Geforce 7600GT (nvidia-glx), Radeon HD 3870 (both radeon & fglrx).

killall pulseaudio seems to fix Totem playback but Flash is still laggy.

---

### Post by gnomeuser on 2009-04-13
The ALSA developers have provided a fix for the Intel HDA type cards (and once again, their bugs caused PA to crash and behave strangely.. who did people blame the root cause? No, they went right after PA.. again).

Regardless, people who believe they are affected can try this:

[http://kernel.ubuntu.com/~dtchen/](http://kernel.ubuntu.com/~dtchen/)

and report back here (remember only if your machine has a HDA card):

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627)

There are also other problems that can cause latency in playback. First up is the nvidia driver, it is known to add a ton of latency to the audio pipeline. Another problem is the current issues we have with latency in the filesystem, T'so has some patches for ext3 but I don't know if they have gone into the Jaunty kernel yet.

In general though, somehow Linux slipped into a very bad state lately. A lot of setups have this type of problem and I doubt it is one cause. To me it sounds more like a lot of bad behaviour was uncovered little by little but it has turned into a situation where Linux just isn't smooth on the desktop.

We definitely need to work on this, I believe that tracking down the cause of this should be a primary concern for Koala as well as writing regression test suites to make sure it never ever happens again.

---

### Post by Mr. Picklesworth on 2009-04-13
Thanks for the informative post, gnomeuser :)

---

### Post by t-mo_ on 2009-04-17
> **Mr. Picklesworth said:**
> 
On this line of thinking, I just set my CPU policy to Performance (cpufreq applet is awesome!) instead of ondemand, which someone on Plaeenet GNOME claims is broken.
Indeed, that acted as a workaround. Slightly scary... clock is ticking

This worked for me, too. See Bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337429]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337429")

---

