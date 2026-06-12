---
title: "Lucid: Audio playback skipping very bad"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by roberthr on 2010-04-08
Did anybody else experienced this issue. I can't seem to listen anything for a long time with Lucid since audio is constantly skipping/repeating. It doesn't matter what program I use and what sound output I select (Pulse or Alsa), altough Alsa test with multimedia selector didn't go so well. 

It's onboard audio card with lspci: Audio device: ATI Technologies Inc RS780 Azalia controller

---

### Post by roberthr on 2010-04-12
So I guess nobody experience this issue?

I was trying to debug PulseAudio to see what happens when skipping occurs. Debug gave me this (all during skipping):

```

D: alsa-sink.c: Wakeup from ALSA!
I: alsa-sink.c: Underrun!
I: alsa-sink.c: Increasing wakeup watermark to 50,00 ms
D: protocol-native.c: Underrun on ''The Racing Rats' by 'Editors'', 0 bytes in queue.
D: protocol-native.c: Requesting rewind due to rewrite.
D: alsa-sink.c: Requested to rewind 39124 bytes.
D: alsa-sink.c: Limited to 6836 bytes.
D: alsa-sink.c: before: 1709
D: alsa-sink.c: after: 1709
D: alsa-sink.c: Rewound 6836 bytes.
D: sink.c: Processing rewind...
D: sink-input.c: Have to rewind 6836 bytes on render memblockq.
D: sink-input.c: Have to rewind 13672 bytes on implementor.
D: source.c: Processing rewind...
D: protocol-native.c: Requesting rewind due to rewrite.
D: alsa-sink.c: Requested to rewind 39376 bytes.
D: alsa-sink.c: Limited to 7036 bytes.
D: alsa-sink.c: before: 1759
D: alsa-sink.c: after: 1759
D: alsa-sink.c: Rewound 7036 bytes.
D: sink.c: Processing rewind...
D: sink-input.c: Have to rewind 7036 bytes on render memblockq.
D: sink-input.c: Have to rewind 14072 bytes on implementor.
D: source.c: Processing rewind...
D: protocol-native.c: Requesting rewind due to rewrite.
D: alsa-sink.c: Requested to rewind 35700 bytes.
D: alsa-sink.c: Limited to 6708 bytes.
D: alsa-sink.c: before: 1677
D: alsa-sink.c: after: 1677
D: alsa-sink.c: Rewound 6708 bytes.
D: sink.c: Processing rewind...
D: sink-input.c: Have to rewind 6708 bytes on render memblockq.
D: sink-input.c: Have to rewind 13416 bytes on implementor.
D: source.c: Processing rewind...
D: protocol-native.c: Requesting rewind due to rewrite.
D: alsa-sink.c: Requested to rewind 36076 bytes.
D: alsa-sink.c: Limited to 7024 bytes.
D: alsa-sink.c: before: 1756
D: alsa-sink.c: after: 1756
D: alsa-sink.c: Rewound 7024 bytes.
D: sink.c: Processing rewind...
D: sink-input.c: Have to rewind 7024 bytes on render memblockq.
D: sink-input.c: Have to rewind 14048 bytes on implementor.
D: source.c: Processing rewind...
D: protocol-native.c: Requesting rewind due to rewrite.
D: alsa-sink.c: Requested to rewind 31524 bytes.
D: alsa-sink.c: Limited to 7000 bytes.
D: alsa-sink.c: before: 1750
D: alsa-sink.c: after: 1750
D: alsa-sink.c: Rewound 7000 bytes.
D: sink.c: Processing rewind...
D: sink-input.c: Have to rewind 7000 bytes on render memblockq.
D: sink-input.c: Have to rewind 14000 bytes on implementor.
D: source.c: Processing rewind...
D: protocol-native.c: Requesting rewind due to rewrite.
D: alsa-sink.c: Requested to rewind 31604 bytes.
D: alsa-sink.c: Limited to 7028 bytes.
D: alsa-sink.c: before: 1757
D: alsa-sink.c: after: 1757
D: alsa-sink.c: Rewound 7028 bytes.
D: sink.c: Processing rewind...
D: sink-input.c: Have to rewind 7028 bytes on render memblockq.
D: sink-input.c: Have to rewind 14056 bytes on implementor.
D: source.c: Processing rewind...
D: protocol-native.c: Requesting rewind due to rewrite.
D: alsa-sink.c: Requested to rewind 27048 bytes.
D: alsa-sink.c: Limited to 7008 bytes.
D: alsa-sink.c: before: 1752
D: alsa-sink.c: after: 1752
D: alsa-sink.c: Rewound 7008 bytes.
D: sink.c: Processing rewind...
D: sink-input.c: Have to rewind 7008 bytes on render memblockq.
D: sink-input.c: Have to rewind 14016 bytes on implementor.
D: source.c: Processing rewind...
D: protocol-native.c: Requesting rewind due to rewrite.
D: alsa-sink.c: Requested to rewind 27120 bytes.
D: alsa-sink.c: Limited to 7032 bytes.
D: alsa-sink.c: before: 1758
D: alsa-sink.c: after: 1758
D: alsa-sink.c: Rewound 7032 bytes.
D: sink.c: Processing rewind...
D: sink-input.c: Have to rewind 7032 bytes on render memblockq.
D: sink-input.c: Have to rewind 14064 bytes on implementor.
D: source.c: Processing rewind...
D: protocol-native.c: Requesting rewind due to rewrite.
D: alsa-sink.c: Requested to rewind 22560 bytes.
D: alsa-sink.c: Limited to 7004 bytes.
D: alsa-sink.c: before: 1751
D: alsa-sink.c: after: 1751
D: alsa-sink.c: Rewound 7004 bytes.
D: sink.c: Processing rewind...
D: sink-input.c: Have to rewind 7004 bytes on render memblockq.
D: sink-input.c: Have to rewind 14008 bytes on implementor.
D: source.c: Processing rewind...
D: protocol-native.c: Requesting rewind due to rewrite.
D: alsa-sink.c: Requested to rewind 22640 bytes.
D: alsa-sink.c: Limited to 7028 bytes.
D: alsa-sink.c: before: 1757
D: alsa-sink.c: after: 1757
D: alsa-sink.c: Rewound 7028 bytes.
D: sink.c: Processing rewind...
D: sink-input.c: Have to rewind 7028 bytes on render memblockq.
D: sink-input.c: Have to rewind 14056 bytes on implementor.
D: source.c: Processing rewind...
D: protocol-native.c: Requesting rewind due to rewrite.
D: alsa-sink.c: Requested to rewind 18084 bytes.
D: alsa-sink.c: Limited to 6992 bytes.
D: alsa-sink.c: before: 1748
D: alsa-sink.c: after: 1748
D: alsa-sink.c: Rewound 6992 bytes.
D: sink.c: Processing rewind...
D: sink-input.c: Have to rewind 6992 bytes on render memblockq.
D: sink-input.c: Have to rewind 13984 bytes on implementor.
D: source.c: Processing rewind...
D: protocol-native.c: Requesting rewind due to rewrite.
D: alsa-sink.c: Requested to rewind 18176 bytes.
D: alsa-sink.c: Limited to 7036 bytes.
D: alsa-sink.c: before: 1759
D: alsa-sink.c: after: 1759
D: alsa-sink.c: Rewound 7036 bytes.
D: sink.c: Processing rewind...
D: sink-input.c: Have to rewind 7036 bytes on render memblockq.
D: sink-input.c: Have to rewind 14072 bytes on implementor.
D: source.c: Processing rewind...
D: protocol-native.c: Requesting rewind due to rewrite.
D: alsa-sink.c: Requested to rewind 13612 bytes.
D: alsa-sink.c: Limited to 6904 bytes.
D: alsa-sink.c: before: 1726
D: alsa-sink.c: after: 1726
D: alsa-sink.c: Rewound 6904 bytes.
D: sink.c: Processing rewind...
D: sink-input.c: Have to rewind 6904 bytes on render memblockq.
D: sink-input.c: Have to rewind 13808 bytes on implementor.
D: source.c: Processing rewind...
D: protocol-native.c: Requesting rewind due to rewrite.
D: alsa-sink.c: Requested to rewind 13792 bytes.
D: alsa-sink.c: Limited to 7040 bytes.
D: alsa-sink.c: before: 1760
D: alsa-sink.c: after: 1760
D: alsa-sink.c: Rewound 7040 bytes.
D: sink.c: Processing rewind...
D: sink-input.c: Have to rewind 7040 bytes on render memblockq.
D: sink-input.c: Have to rewind 14080 bytes on implementor.
D: source.c: Processing rewind...
D: protocol-native.c: Requesting rewind due to rewrite.
D: alsa-sink.c: Requested to rewind 9228 bytes.
D: alsa-sink.c: Limited to 6964 bytes.
D: alsa-sink.c: before: 1741
D: alsa-sink.c: after: 1741
D: alsa-sink.c: Rewound 6964 bytes.
D: sink.c: Processing rewind...
D: sink-input.c: Have to rewind 6964 bytes on render memblockq.
D: sink-input.c: Have to rewind 13928 bytes on implementor.
D: source.c: Processing rewind...
D: protocol-native.c: Requesting rewind due to rewrite.
D: alsa-sink.c: Requested to rewind 9348 bytes.
D: alsa-sink.c: Limited to 7036 bytes.
D: alsa-sink.c: before: 1759
D: alsa-sink.c: after: 1759
D: alsa-sink.c: Rewound 7036 bytes.
D: sink.c: Processing rewind...
D: sink-input.c: Have to rewind 7036 bytes on render memblockq.
D: sink-input.c: Have to rewind 14072 bytes on implementor.
D: source.c: Processing rewind...
D: protocol-native.c: Underrun on ''The Racing Rats' by 'Editors'', 0 bytes in queue.
D: protocol-native.c: Requesting rewind due to rewrite.
D: alsa-sink.c: Requested to rewind 4784 bytes.
D: alsa-sink.c: Limited to 4784 bytes.
D: alsa-sink.c: before: 1196
D: alsa-sink.c: after: 1196
D: alsa-sink.c: Rewound 4784 bytes.
D: sink.c: Processing rewind...

```

And so on and on and on, until at some point it plays ok for few minutes, then starts skipping again. I never had such problem on this machine with previous Ubuntu versions.

---

### Post by gnomeuser on 2010-04-12
You can try installing the linux-modules-backports-alsa-<flavor> package to see if the bug is present in newer versions of your driver.

You can also install the -preempt flavor kernel which could allow for smoother audio playback.

At any rate you should file a bug.

---

### Post by roberthr on 2010-04-12
I finally found a bug report from long time ago:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/388081](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/388081)

It seems it is present for quite some time.

---

### Post by gnomeuser on 2010-04-12
> **roberthr said:**
> I finally found a bug report from long time ago:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/388081](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/388081)

It seems it is present for quite some time.

You should file a new bug instead since this is regarding a different driver so far as I can tell. Thus this is a different bug.

Since it didn't happen with earlier stable releases you should set the correct regression tag (ubuntu-bug will walk you through this). That way the developers can track it and since this is an LTS release it will be high priority.

Unfortunately the action you took in updating the existing bug is likely to have caused additional work and will not lead to your bug getting fixed. Please read for the rationale:

[http://drowninginbugs.blogspot.com/2010/04/public-service-announcement-when-in.html](http://drowninginbugs.blogspot.com/2010/04/public-service-announcement-when-in.html)

[http://drowninginbugs.blogspot.com/2010/04/public-service-announcement-read.html](http://drowninginbugs.blogspot.com/2010/04/public-service-announcement-read.html)

Since Daniel is an unpaid hard working volunteer anyone filing bugs on audio would benefit from reading those posts to make his life a bit easier.

Once you filed a new bug, please update this post and I will track the bug as well. Hopefully we can manage to get your problem fixed in time for the final release, or at the very least as a post release update.

Thank you.

---

### Post by gnomeuser on 2010-04-12
As a little trick to improve the bug report you may want to try the daily snapshot PPA of the ALSA stack to see if the problem has been fixed. ppa-purge will help you revert to stock Lucid once you have tested if you do not want to continue using daily snapshots.

[https://edge.launchpad.net/~ubuntu-audio-dev/+archive/ppa](https://edge.launchpad.net/~ubuntu-audio-dev/+archive/ppa)

---

### Post by roberthr on 2010-04-15
After thorough investigation and when I ran out of all ideas, I have decided to update motherboard BIOS. After that, all audio problems were gone!

---

### Post by fmo on 2010-04-17
I have the same problem with the same card, I have update my BIOS to the latest version but it doesn't help.

I am going to try the Alsa PPA, I don't think it's BIOS related.

---

### Post by fmo on 2010-04-18
I have updated Lucid using this PPA, it is better but it is still skipping, it drives me crazy!

I don't have any problem with my laptop it only does it on my main PC which makes it even more anoying!

---

### Post by gruntlips_ on 2010-04-21
I have this skipping problem in karmic and the only way I got rid of it was by removing pulse audio entirely.

---

### Post by andrewabc on 2010-04-21
What do you guys mean by skipping? sound garbled, sound gets 'muted', crackling sound or somehow skips to parts of song it isn't supposed to?

I know in Karmic I had bug where it was a power saving feature that would turn on/off sound every couple minutes and would screw up the sound.

If crackling sound (power saving), try
[crackling sound](http://ubuntuforums.org/showthread.php?p=8193272)
I don't know if this bug is still in 10.04, but happened often in 9.10

EDIT:
Seems this problem is unrelated. So only try what I linked if you think it might be the problem.

---

### Post by SergeiFranco on 2010-04-22
I would like to report that I am getting too this problem.
```

D: sink-input.c: Have to rewind 1856 bytes on render memblockq.
D: sink-input.c: Have to rewind 1856 bytes on render memblockq.

```

The bytes varies.
This is very annoying. It sounds like it pauses for 1/10 of a second ever 1-2seconds, like youtube on bad connection sort of thing.

It is extremely frustrating, it does that in amarok, kaffeine etc.

I am using kubuntu 9.10 64bit. latest kernel from repo.

The reason why I am using pulse audio with kubuntu is because there is no way I can have volume control and multiple sounds playing without pulse, while outputting to digital out. This is extremely stupid as 10 years ago Windows already had that capability (and more).


I am using hda-intel ALC888, and I am amazed of capabilities in windows for same sound card. Of course I am not going to change to windows becuase of sound, I am linux person, as I like to tweak config etc. I had perfectly working asound.conf with softvol and dmix doing what I needed until 9.10 came out. I am using KDE as it is not stupified as gnome, but because of phonon, I cannot have softvol+dmix+digital out at same time (no matter what I tried and I searched).

I am happy with pulse (especially it will be integrated in kmix) but stuttering is something that should be fixed.

I just noticed it is a [SOLVED] thread, do I start new one?

---

