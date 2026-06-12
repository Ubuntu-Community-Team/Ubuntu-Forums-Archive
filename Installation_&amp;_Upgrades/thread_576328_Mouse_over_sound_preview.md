---
title: "Mouse over sound preview"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by GhostZrydA on 2007-10-15
What packages to i have to have installed for mouse over sound previews in nautilus, im using the RC of Gutsy Gibbon.

I've tried "mpg321" & "mpg123" but no go.

Thanks
GhostZrydA

---

### Post by GhostZrydA on 2007-10-15
Sorry for "bumping", but someone must know how to get this working under gutsy, it's a feature i used under feisty all the time, so i would hate to lose it.

Anyone...:confused:

GhostZrydA

---

### Post by vgrisham on 2007-10-20
In addition to installing mpg123, try installing mpg123-alsa & esound. You may have to reboot. It worked for me.

---

### Post by GhostZrydA on 2007-10-20
Thank you, thank you :guitar:, that did the trick, had to reboot like you said, now have mouse over previews again.

Thanks also for the PM, i wasn't subscribed to the thread, so i would of missed your reply.

Cheers
GhostZrydA :)

---

### Post by vgrisham on 2007-10-20
> **GhostZrydA said:**
> Thank you, thank you :guitar:, that did the trick, had to reboot like you said, now have mouse over previews again.

Thanks also for the PM, i wasn't subscribed to the thread, so i would of missed your reply.

Cheers
GhostZrydA :)

You're welcome. Enjoy.

---

### Post by n77 on 2007-10-20
Packages you need to get the mouseover preview working -

mpg321
ubuntu-restricted-extras
PulseAudio
PulseAudo-esound-compat
libasounds2-plugins

The mp3 preview works.  You don't need to reboot

---

### Post by loko on 2007-10-22
Mh,

with the suggested packages installed, sound preview works, but it is still messed up.

for me it only plays with maximum volume, i cannot get the volume lower. this is annoying!

---

### Post by phenest on 2007-10-23
I have 2 machines, one with a fresh install and I can get sound previews (apart from mp3's), the other is an upgrade which the most I've achieved is the little mouse-over bubble.

EDIT: The properties of any sound file says 0 channels!

---

### Post by vgrisham on 2007-10-23
> **phenest said:**
> 
EDIT: The properties of any sound file says 0 channels!

Eewww. That doesn't sound good.

The only thing I can recommend is to make sure that mpg123, mpg123-alsa & esound are installed. If it still doesn't work, I'd try reinstalling all three of those. I don't know what to tell you though on the "0 channels" thing though.

---

### Post by phenest on 2007-10-24
I've tried purging, reinstalling of all suggested packages with no luck. If I try with the LiveCD, it works except for mp3's.

---

### Post by vgrisham on 2007-10-24
> **phenest said:**
> I've tried purging, reinstalling of all suggested packages with no luck. If I try with the LiveCD, it works except for mp3's.

Are you able to play music in Rhythmbox (or Totem)?

---

### Post by phenest on 2007-10-25
> **vgrisham said:**
> Are you able to play music in Rhythmbox (or Totem)?

Yep. No problems there.

---

### Post by Chazall1 on 2007-10-25
> Packages you need to get the mouseover preview working -

mpg321
ubuntu-restricted-extras
PulseAudio
PulseAudo-esound-compat
libasounds2-plugins

The mp3 preview works. You don't need to reboot

I did this and it worked fine 2 days ago. Today I do not have the mouse over priview working?

---

### Post by vgrisham on 2007-10-25
> **Chazall1 said:**
> I did this and it worked fine 2 days ago. Today I do not have the mouse over priview working?

Try installing esound and mpg123-alsa

---

### Post by vgrisham on 2007-10-25
> **phenest said:**
> Yep. No problems there.

Dang. I'm stumped. I'm going to PM a heavy hitter and see if he'll visit this thread.

---

### Post by Mrs Twaddle on 2007-10-26
Don't know if it works for you, but i found i had to highlight the file (click once) and then hover to get it to preview.

Discovered this by accident when i was installing other packages mentioned in this thread.

They won't preview for me unless i do that.

---

### Post by vgrisham on 2007-10-26
> **Mrs Twaddle said:**
> Don't know if it works for you, but i found i had to highlight the file (click once) and then hover to get it to preview.

Discovered this by accident when i was installing other packages mentioned in this thread.

They won't preview for me unless i do that.

That's a good point. I noticed that as well.

---

### Post by DarkDancer on 2007-10-27
Have you tried installing mpg123-esd? worked for me....so far.....

---

### Post by phenest on 2007-10-27
> **DarkDancer said:**
> Have you tried installing mpg123-esd? worked for me....so far.....

Woo hoo! I can now preview mp3's! But... wave, ogg, and flac files still refusing.

---

### Post by vgrisham on 2007-10-27
> **phenest said:**
> Woo hoo! I can now preview mp3's! But... wave, ogg, and flac files still refusing.

make sure mp3-alsa and esound are installed

---

### Post by isaacj87 on 2007-10-27
I installed every packaged suggested...

Interesting, I never noticed that ogg, wav and others don't work...

Mp3 is fine though thanks for that!

---

### Post by isaacj87 on 2007-10-27
found it...

make sure mpg321 and vorbis-tools are installed...

ogg files now have mouse over sound previews..

[http://ubuntu-tutorials.com/2007/03/06/how-to-install-audio-preview-for-nautilus/]("http://ubuntu-tutorials.com/2007/03/06/how-to-install-audio-preview-for-nautilus/")

More info in the link.

---

### Post by phenest on 2007-10-28
> **isaacj87 said:**
> found it...

make sure mpg321 and vorbis-tools are installed...

ogg files now have mouse over sound previews..

[http://ubuntu-tutorials.com/2007/03/06/how-to-install-audio-preview-for-nautilus/]("http://ubuntu-tutorials.com/2007/03/06/how-to-install-audio-preview-for-nautilus/")

More info in the link.

Not here they don't.

---

### Post by loko on 2007-10-29
> **loko said:**
> Mh,

with the suggested packages installed, sound preview works, but it is still messed up.

for me it only plays with maximum volume, i cannot get the volume lower. this is annoying!

i solved this problem by uninstalling pulseaudio and pulseaudio-esound-compat

---

### Post by phenest on 2007-10-29
Ok. Ogg files preview but only if you highlight them first. Mp3's don't require this. And flac files do not preview at all.

---

### Post by loadeddreams on 2007-11-05
> **phenest said:**
> Ok. Ogg files preview but only if you highlight them first. Mp3's don't require this. And flac files do not preview at all.

phenest, did you figure this out?
I also have to highlight the files before they will preview.. which is strange because a week ago before format/reinstall I didn't have to.
I've installed mpg123-esd and esound (removed pulseaudio because of a LOT of problems) and it seems to work well except I have to highlight the file first.

Any ideas?

---

### Post by cchevy on 2007-11-05
> **loadeddreams said:**
> phenest, did you figure this out?
I also have to highlight the files before they will preview.. which is strange because a week ago before format/reinstall I didn't have to.
I've installed mpg123-esd and esound (removed pulseaudio because of a LOT of problems) and it seems to work well except I have to highlight the file first.

Any ideas?

yeah mine too...it does not work like with pulseaudio, but u have to highlite it.

anyone?

---

### Post by loadeddreams on 2007-11-06
> **cchevy said:**
> yeah mine too...it does not work like with pulseaudio, but u have to highlite it.

anyone?

Mine apparently fixed itself. I didn't really mess with it any more because I was getting my console back, and used the method [described here.]("https://bugs.launchpad.net/ubuntu/+bug/152089/comments/1")

I then installed ubuntu-restriced-extras to get some other various things working.

After an eventual reboot it seemed to be working fine.. I'm thinking the reboot fixed it.

I don't have pulseaudio installed (messes up my ALSA).. I have esound and mpg123-esd installed to playback the sounds.. hope this helps

---

### Post by phenest on 2007-11-16
This is very inconsistent! I'm thinking this is a focus problem in Nautilus. Perhaps to launch something in Launchpad if no-one has already.

Fresh install of Gutsy, packages installed:
ubuntu-restricted-extras
esound
libasound2-plugins
sox
vorbis-tools
mpg123-esd

With this, I can preview mp3, wave, and ogg files. I haven't tested with any other audio files. But even with this, you don't always get a preview, neither does the play emblem appear. Sometimes I have to highlight the file first and sometimes I have to click in an empty space (in between files) to gain 'focus', but sometimes I need do nothing. And sometimes, I move the cursor off a highlighted file onto another app, and it starts playing! Very strange.

Have Gnome moved from using Alsa to using Esound? Is this the problem?

---

### Post by Turin Turambar on 2007-11-27
Esound & mpg123 did the trick for me. You must install esound in order to preview MP3 files.

---

### Post by phenest on 2008-01-06
I just installed Linux Mint 4.0 which is basically Gutsy.

```
sudo apt-get install sox vorbis-tools mpg123-alsa
```

This was all I needed to get mouse over previews working. That's the same as I did for Feisty. So what is wrong with Gutsy? Hardy Alpha 2 is just a complicated as Gutsy too.

---

### Post by phenest on 2008-02-24
Since Pulse Audio is now being used in Hardy, is these another way to get this working without using esound?

---

### Post by bedbug on 2008-02-24
for hardy: try this

sudo update-alternatives --quiet --install /usr/bin/totem-audio-preview totem-audio-preview   /usr/bin/totem-gstreamer-audio-preview  40

---

### Post by phenest on 2008-02-25
> **bedbug said:**
> for hardy: try this

sudo update-alternatives --quiet --install /usr/bin/totem-audio-preview totem-audio-preview   /usr/bin/totem-gstreamer-audio-preview  40

Wow! Fantastic! That worked a treat.

Could you please explain what that command does?

---

### Post by phenest on 2008-02-25
I also think this feature should be working as default in Ubuntu instead of having to do it manually. How do I go about suggesting this for Hardy?

---

### Post by bedbug on 2008-02-25
please just look at : man update-alternatives

all that we need is a  link:
/usr/bin/totem-audio-preview -> /usr/bin/totem-gstreamer-audio-preview 

alternatively that we can do in the terminal : (I guess)
:guitar:
sudo ln -s /usr/bin/totem-gstreamer-audio-preview /usr/bin/totem-audio-preview

---

