---
title: "No sound - Via AC97"
date: 2005-06-03
forum: Installation &amp; Upgrades
---

### Post by mindstage on 2005-06-03
Ive been through about 3 dozen threads, done all the suggested fixes, and still have no sound. The correct module is loading for my onboard sound card. The speakers work (tested with a live CD of Knoppix). When I run any sound device - XMMS, CD player, etc, sound appears to play, but nothing is heard.

Here's the results of a  sudo lsmod |grep snd*


snd_via82xx            25248  1
snd_ac97_codec         64608  1 snd_via82xx
snd_pcm_oss            47652  0
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_via82xx,snd_pcm
gameport                4608  1 snd_via82xx
snd_mpu401_uart         7168  1 snd_via82xx
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  1 snd_rawmidi
snd                    50276  9 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  2 snd

Any help, please?

---

### Post by Martin Witte on 2005-06-03
Maybe you tried this already, but anyway: my sound worked after running 'alsamixer', then muting channel 'IEC 958 Capture Monitor'.

---

### Post by mingus on 2005-06-03
Not knowing all that you have tried . . .

And when you go to System/Preferences/Multimedia Systems Selector, and Test?  And switch from ESD to ALSA there?

---

### Post by dwkreutzer on 2005-06-03
[QUOTE=Martin Witte]Maybe you tried this already, but anyway: my sound worked after running 'alsamixer', then muting channel 'IEC 958 Capture Monitor'.[/QUOTE]


Martin,

Thank you very much.  I also have gone through gobs of threads on "no sound."  I installed a sound card, messed around with bios settings, downloaded a different driver, made burnt offerings, etc.  Nothing worked and I was going crazy.

Just out of curiosity, can you tell me what the EC 958 Capture Monitor does and why did muting it fix my problem?

In any event, thanks much,

David

---

### Post by mindstage on 2005-06-06
Three hearty huzzahs and he's a jolly good fellow to Martin! Blessings on you and every offspring of your offspring! Muting the IEC958 Capture on alsamixer did the trick. I now have great sound and Ubuntu!  Life is good.

---

### Post by dalert0140 on 2005-06-23
hi,

I just installed Ubuntu but I'm at a completely loss. I seem to have the same audio chipset AC97. I've been searching for the problem for about two days now and I seem to have the same problem atht you guys have.Can anyone tell me where and how to mute channel 'IEC 958 Capture Monitor'. I'm a complete newb to Linux and (as dumb as it sounds) I can't find it.

I did :

"sudo alsamixer" but i can't find channel 'IEC 958 Capture Monitor' Can anyone tell me where is it? and how to mute it? 
[/list]

---

### Post by Martin Witte on 2005-06-24
I think you can run alsamixer without sudo. With the arrow keys you can move to left/right in the list of channels, with up/down arrows you can set a volume, and with 'm' you can mute a channel.

Hope this helps, good luck

---

### Post by orudie on 2007-08-09
I am also new, and having the same problem, no one seem to know of this issue in #ubuntu on freenode. Going to try to ask here. 
I have the Nforce4 Nvidia chipset, and also have the AC97 internal sound card. It was detected as Nvidia CK804 AC97 . audio files (mp3s) seem play to play in VLC media player, but i can not hear anything. After reading this thread i thought i will be able to fix this, however when i type alsamixer in terminal, i can not find IEC 958 Capture Monitor. I only see the IEC 958 Playback. Same options in the Volume Control CK804 ubuntu Alsa Mixer. here is a screenshot. Guys, if anyone knows, please let me know how can i find the IEC 958 Capture Monitor The only place where i can actually find IEC958 Capture Monitor is in Volume Control  - Edit - Preferences under Select Tracks to be visible. Cant see it anywhere else.. Please help..

Here is a screenshot:

[http://img405.imageshack.us/my.php?image=iec958nx1.png](http://img405.imageshack.us/my.php?image=iec958nx1.png)

---

### Post by orudie on 2007-08-19
Its been a week since i asked, i tried everything, still no sound..... please help

---

### Post by MenZa on 2007-08-20
> **orudie said:**
> I am also new, and having the same problem, no one seem to know of this issue in #ubuntu on freenode. Going to try to ask here. 
I have the Nforce4 Nvidia chipset, and also have the AC97 internal sound card. It was detected as Nvidia CK804 AC97 . audio files (mp3s) seem play to play in VLC media player, but i can not hear anything. After reading this thread i thought i will be able to fix this, however when i type alsamixer in terminal, i can not find IEC 958 Capture Monitor. I only see the IEC 958 Playback. Same options in the Volume Control CK804 ubuntu Alsa Mixer. here is a screenshot. Guys, if anyone knows, please let me know how can i find the IEC 958 Capture Monitor The only place where i can actually find IEC958 Capture Monitor is in Volume Control  - Edit - Preferences under Select Tracks to be visible. Cant see it anywhere else.. Please help..

Here is a screenshot:

[http://img405.imageshack.us/my.php?image=iec958nx1.png](http://img405.imageshack.us/my.php?image=iec958nx1.png)

That's the same issue I'm having presently.

---

### Post by Scorpuis on 2007-08-23
Seems AC97 on board sound is giving lots of grief. 
Same deal searched all the forums I could understand and tried new drivers, upgrade BIOS [ASUS P4S800], even reinstalling Ubuntu & latest ALSA drivers but still no sound.

Gave up trying in the end - pulled out an old soundblaster sound card from my box of old bits and disabled the on-board sound - hey presto! instant sound. 
Happy now. good luck to those still trying. :-)

---

### Post by MenZa on 2007-08-24
> **Scorpuis said:**
> Seems AC97 on board sound is giving lots of grief. 
Same deal searched all the forums I could understand and tried new drivers, upgrade BIOS [ASUS P4S800], even reinstalling Ubuntu & latest ALSA drivers but still no sound.

Gave up trying in the end - pulled out an old soundblaster sound card from my box of old bits and disabled the on-board sound - hey presto! instant sound. 
Happy now. good luck to those still trying. :-)

Yeah, I don't really have that option, seeing as I'm on a laptop. :/

---

### Post by madtinkerer on 2007-09-15
Hi Everyone,

i've been struggling with this issue for a few days on my p4p800-vm.  I took a look at my motherboard's jumper settings and I noticed a problem.  The front-panel audio jumpers which should have been shorted by default were open.  Once I shorted them out with jumper plugs, my sound worked.  Well, almost.  I'm only getting sound from one channel but I'll have to take a look at that.  Anyway, take a look at your jumpers.

---

### Post by downhillgames on 2007-10-12
> **madtinkerer said:**
> Hi Everyone,

i've been struggling with this issue for a few days on my p4p800-vm.  I took a look at my motherboard's jumper settings and I noticed a problem.  The front-panel audio jumpers which should have been shorted by default were open.  Once I shorted them out with jumper plugs, my sound worked.  Well, almost.  I'm only getting sound from one channel but I'll have to take a look at that.  Anyway, take a look at your jumpers.

dear lord, man is that dangerous.

**the problem is in ubuntu's kernel**. Fedora doesn't give me this problem but this 2.6.20-15-generic kernel does. I'll try -26-generic but, heh... yeah right. I wonder what's disabled... I guess I'll have to recompile it to figure it out.

---

### Post by downhillgames on 2007-10-12
updating to 2.6.16-lowlatency (prolly -generic would be the same) fixed it for me.

---

