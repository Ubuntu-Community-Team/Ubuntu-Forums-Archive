---
title: "No sound after install"
date: 2005-02-14
forum: Installation &amp; Upgrades
---

### Post by lfierro on 2005-02-14
I installed the latest version of Ubuntu.  It was very easy and quite fast....but I have no sound (I used to have it before...).  My  PC is a PC clone with a VIA celeron 600.  The sound is integrated AC 97 and is VIA 82C686A/B rev 50.  When I put a CD in the CD Rom drive,  the desktop shows that the CD is advancing and music is playing,  but nothing really comes out.   The volume is up ???  Help would be greatly appreciated.

---

### Post by cblack on 2005-02-14
Make sure that your alsa channels are unmuted. Run sudo alsamixer in a terminal window.  If that doesn't work check via lsmod that your sound modules are getting loaded.

---

### Post by lfierro on 2005-02-14
[QUOTE=cblack]Make sure that your alsa channels are unmuted. Run sudo alsamixer in a terminal window.  If that doesn't work check via lsmod that your sound modules are getting loaded.[/QUOTE]

O.K....so how do I do that.... (sorry but I come straight from MS Windows)
There is no application or system tools called ALSA so I assume I must use the Root Termnail.  What do I type.  ?  :roll:

---

### Post by cblack on 2005-02-14
In a terminal type sudo alsamixer. Or in the root terminal just type alsamixer.

---

### Post by DJ_Max on 2005-02-14
Don't use the "root terminal", just use the standard "terminal". The do.
```
sudo alsamixer
``` 
It should ask for your password.

---

### Post by lfierro on 2005-02-14
There are 2 terminal windows:

Option # 1
When I go sudo alsamixer in System Tools>Terminal, I get the following message:

alsamixer: function snd_ctl_open failed for default: no such file or directory

I guess this was no the right thing to do.


Option # 2:   within Applications>Run Application>with the option Run in Terminal clicked.   I ran what you told me and got a series of bars indicating correctly my sound card.  Do I have to increase the size of the bars until it reaches the red, or just the green (I suspect the green).  I put the CD rom inside but got no sound.
I rebooted the PC and still no sound. 

I went to the Volume Control Option.
I found two tabs:  

1) Realtek ALC 101 (OSS Mixer) and
2) VIA 82C686A/B Rev50 (Alsa Mixer).

I have checked OUT (not checked) Mute on all of the options (is that correct ?)

Result:  no sound yet.  When I put the speakers VERY loud, I can hear some hissing from the volume alone, but no music or anything else.

I  try *sudo ismod*.   I get asked for my password, run it but nothing happens.  I see nothing new on the screen.
I try *sudo Ismod * (capital " I" ) . Result: >sudo: Ismod command not found

I try ismod (alone).  Result: " The specified location is invalid." 

There MUST be a way........

---

### Post by lfierro on 2005-02-18
[QUOTE=DJ_Max]Don't use the "root terminal", just use the standard "terminal". The do.
```
sudo alsamixer
``` 
It should ask for your password.[/QUOTE]

I think I have found the problem....and it is not with Ubuntu...it is with my hardware.  I re-intalled the old Linux OS with which my PC worked well in the past, and it does not have working sound anymore.

Sorry for the time you guys wasted trying to help me.  I guess it is time for another motherboard.  Any advise on that area ?  Should I go AMD or Pentium ?

Thanks

---

### Post by bored2k on 2005-02-20
[QUOTE=lfierro]I think I have found the problem....and it is not with Ubuntu...it is with my hardware.  I re-intalled the old Linux OS with which my PC worked well in the past, and it does not have working sound anymore.

Sorry for the time you guys wasted trying to help me.  I guess it is time for another motherboard.  Any advise on that area ?  Should I go AMD or Pentium ?

Thanks[/QUOTE]
 Unless you are planning on an AMD64 mobo [wich would be GREAT], its what u want/what ur money can buy. That sort of question could go forever unanswered cuz ppl like both.

personally, i like intel cuz i have been using intel back from the days i had a 386 computer [about 44mhz and 66on turbo lol], and overall i have been pleased, ive used pentium, before pentium, i hav had pentium 1,3,celeron, currently own a 4, so, i love it .... amd is very good tho

---

### Post by DJ_Max on 2005-02-20
> Should I go AMD or Pentium ? 
Oh no, you shouldb't have said that, you'll get a 10 page threadwith such comments as "AMD pwns" & "Intel is better then AMD because it sounds better", etc..

Put the names in a hat, and pull one. Thats the best advice I can give you.

But, if you need a new motherboard, and have a Intel Celeron processor, then you have no choice but to get a Intel motherboard.

---

### Post by LongTooth on 2005-02-20
DJ Max hit the nail right on the head. Its a never ending question. AMD or Intel. I perfer AMD. The gauntlet has been thrown down.  Let the war begin!

---

