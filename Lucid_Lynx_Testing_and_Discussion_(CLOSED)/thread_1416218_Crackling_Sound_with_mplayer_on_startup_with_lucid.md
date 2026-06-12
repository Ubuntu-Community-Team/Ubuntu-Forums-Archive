---
title: "Crackling Sound with mplayer on startup with lucid lynx on an AC97 chipset"
date: 2010-02-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by hsiyao on 2010-02-25
Hi,

I keep on following the nice beta process of lucid lynx since the first day and have to say that it's really interesting, never did this before ;)

One weird thing that happens to me and that I can't solve anyhow is the following (I searched about one hour for a solution now via google and through the ubuntuforums, so it's not like I just post this without looking in advance):
when starting a movie with mplayer I get a crackling sound at the startup (about 2-3 cracks). I tried all possible -ao drivers but the problem persists. the weird thing is that when I stopped a movie and play another one within approx. 3 seconds I have no cracks, with none of the drivers (really reproducable). this problem pretty much reminds me on the power-saving problem on hda soundchips, but since I have an AC97 chipset there is no commenting out the last line of /etc/modprobe.d/alsa-base.conf possible, since it ain't there 

and here is the really interesting thing: when I start a movie with totem I don't have this crackling, but there I notice that when starting up a movie the sound is muted at the beginning and unmuted when actually playing (it isn't unmuted automatically in the firefox plugin though which is a different topic ;) ) 

since it's rather a problem of a perfectionist instead of a really BIG DEAL it pretty much falls in the category of "would be nice to be solved" but if anybody got an idea, please post it!! 

and just in case, this is the complete lspci output for my soundchip
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)


thx in advance for any new ideas!!!

---

### Post by Vermind on 2010-04-16
I have the same problem. Starting an audio application after an audio idle period results in loud pops and crackles which last for a very short time (0.1 seconds) and then the regular audio of the program starts.
Example programs: scorched3d, gnome-mplayer.

I have Creative Labs SB Live! EMU10k1 ( rev 08 )

Have you reported a bug of this?

---

### Post by hsiyao on 2010-04-17
Hi,

cool that at least there is one other person, who is annoyed by this or at least noticed it ;)

I try to get into it as far as possible with my knowledge and this doesn't seem to be a bug, rather it's idea is to conserver energy, by switching off the sound card everytime it is idle for 10 seconds. 

I even found a file back than, where you could set a 0 in place for a 1 that was responsible for that energysaving feature on ac97 cards, but wasn't possible to me to change it, not by "echo 1 >" what you e.g. do when enabling ip-forwarding nor other. sorry but I can't find out anymore where that file was located. 

Anyhow what is strange for me, that when you have a HDA Intel Soundchip, you just can switch off this feature over a line in alsa.conf (there was a big problem, that the card wouldn't switch on again, what also could fixed by this.)

I allready filed a bug but there are tons of different bugs containing "crackling sound", many of them actualy with different 
problems. 

But nevertheless if anybody reading this got the energysaving feature of an ac97 card switched-off PLEASE POST!!!! (Post also if my idea that it's connected to energy saving is completely wrong ;) )

cyaa

jens.

---

