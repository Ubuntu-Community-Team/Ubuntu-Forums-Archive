---
title: "Computer 'clicking' in karmic koala?"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jokerface on 2009-10-13
Does anybody else's computer 'click' periodically in karmic koala? It always happens during start-up, and sometimes during use.

---

### Post by tchoklat on 2009-10-13
it may be how you have setup the system sounds.

---

### Post by jokerface on 2009-10-13
I think it's my actual computer making the sound (I know, duh).
I have the sound muted, but it still happens.
Any idea, still?

---

### Post by XCan on 2009-10-13
My first guess was your head being parked all the time, but I can't understand why it would park itself during the hdd-intensive boot period.

---

### Post by P4man on 2009-10-13
Does it sound anything like this:

[http://upload.wikimedia.org/wikipedia/en/a/a9/WD_bad_heads_click_of_death.ogg](http://upload.wikimedia.org/wikipedia/en/a/a9/WD_bad_heads_click_of_death.ogg)

?

If so, make a backup asap, and prepare mentally for a harddrive failure any moment.

---

### Post by jokerface on 2009-10-13
That's not the sound, no. 
It's just one 'click' that happens at random moments.
I would compare it to flicking your fingernail on a hardwood table.
I'm thinking it has something to do with Koala, based on how it never did it when my laptop had Vista on it.
It doesn't really bother me, I'm just trying to find out whether it's 'bad' or not.

---

### Post by DeMus on 2009-10-13
> **jokerface said:**
> That's not the sound, no. 
It's just one 'click' that happens at random moments.
I would compare it to flicking your fingernail on a hardwood table.
I'm thinking it has something to do with Koala, based on how it never did it when my laptop had Vista on it.
It doesn't really bother me, I'm just trying to find out whether it's 'bad' or not.

When I tried karmic I also had the sounds at boot and shutdown. I believe it is the moment the audio-card is enabled and disabled. I don't have that in Jaunty.
During normal operation I didn't have the clicking sounds.

---

### Post by jokerface on 2009-10-13
> **DeMus said:**
> When I tried karmic I also had the sounds at boot and shutdown. I believe it is the moment the audio-card is enabled and disabled. I don't have that in Jaunty.
During normal operation I didn't have the clicking sounds.

That's funny, I was just searching for one of your older posts regarding a 'clicking sound'.
That must be the problem, although it still makes me wonder why it does it randomly throughout normal operation.
It's no biggie really, as long as it doesn't blow up in my face :)

If anyone finds a solution after running into the same problem though, feel free to let me know!

---

### Post by P4man on 2009-10-13
Im still guessing its the harddrive. But you could try blacklisting the pcspkr module to make sure its not somehow from the speaker, and disable onboard sound if you can (bios?). then have your cd tray open, and if it still makes noise, its something mechanical and its gotta be the drive.

---

### Post by DeMus on 2009-10-13
> **P4man said:**
> Im still guessing its the harddrive. But you could try blacklisting the pcspkr module to make sure its not somehow from the speaker, and disable onboard sound if you can (bios?). then have your cd tray open, and if it still makes noise, its something mechanical and its gotta be the drive.

Sorry to say this but it is not the hard drive.
I have my PC standing on the floor, underneath the table. I have 2 speakers next to my monitor and the sound definitely came from the speakers.
During operation could be that the speakers pick-up a glitch in the line voltage (220 or maybe 110V). When the cables pick up a high frequency you might hear it also in the speakers.

---

### Post by Abandon on 2009-10-13
> **jokerface said:**
> Does anybody else's computer 'click' periodically in karmic koala? It always happens during start-up, and sometimes during use.

If you mean a popping sound from you're speakers then yes. And if so..we are not alone :(

---

### Post by BXCracer on 2009-10-13
You probably have a HDA audio card. If so then those clicks is caused by the power saving option introduced in karmic. You can solve this problem by commenting out the last line in the /etc/modprobe.d/alsa-base.conf

---

### Post by Longinus00 on 2009-10-13
> **Abandon said:**
> If you mean a popping sound from you're speakers then yes. And if so..we are not alone :(

If you hear a popping sound then it's because of the new power saving code in pulseaudio. It basically tries to power down your soundcard whenever you're not using it to save power. The downside is that we get the popping sound when it turns back on, until they figure out a fix that is.

---

### Post by Abandon on 2009-10-13
> **BXCracer said:**
> You probably have a HDA audio card. If so then those clicks is caused by the power saving option introduced in karmic. You can solve this problem by commenting out the last line in the /etc/modprobe.d/alsa-base.conf


Thx...I'm using HDA audio and this works for me :-)

---

### Post by jokerface on 2009-10-13
> **BXCracer said:**
> You probably have a HDA audio card. If so then those clicks is caused by the power saving option introduced in karmic. You can solve this problem by commenting out the last line in the /etc/modprobe.d/alsa-base.conf

I found the last line in /etc/modprobe.d/alsa-base.conf
could you explain what you mean by 'commenting out?

---

### Post by Abandon on 2009-10-13
> **jokerface said:**
> I found the last line in /etc/modprobe.d/alsa-base.conf
could you explain what you mean by 'commenting out?

Put an # in front of that line

---

### Post by emarkay on 2009-10-13
> **jokerface said:**
> I found the last line in /etc/modprobe.d/alsa-base.conf
could you explain what you mean by 'commenting out?


This needs to get int o the Karmic FAQ and documentation....

---

### Post by jokerface on 2009-10-13
Thanks alot!!! It worked!

---

### Post by jmmL on 2009-10-13
Thread here with info [http://ubuntuforums.org/showthread.php?p=8098189](http://ubuntuforums.org/showthread.php?p=8098189)
And also links to some LP bugs.

---

### Post by wildweathel on 2009-10-13
Daniel Chen has asked people to file bugs if the new power-saving feature causes popping sounds.    So, if your computer clicks when its not playing sound and changing /etc/modprobe.d/alsa-base.conf fixes it, please follow the directions here to file a bug report.  [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-May/008239.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-May/008239.html)  Unless your computer model has been reported already, you should file a new report.    Thanks.

---

### Post by NJC on 2009-10-13
> **P4man said:**
> Does it sound anything like this:

[http://upload.wikimedia.org/wikipedia/en/a/a9/WD_bad_heads_click_of_death.ogg](http://upload.wikimedia.org/wikipedia/en/a/a9/WD_bad_heads_click_of_death.ogg)

Could use that loop in a hip-hop song... that's a nasty sound though, esp when data is needed off of that drive.

---

### Post by mdurham on 2009-10-13
> **BXCracer said:**
> You probably have a HDA audio card. If so then those clicks is caused by the power saving option introduced in karmic. You can solve this problem by commenting out the last line in the /etc/modprobe.d/alsa-base.conf

Thanks, that fixed it.

---

### Post by FormerSlacker on 2009-10-14
> **Abandon said:**
> If you mean a popping sound from you're speakers then yes. And if so..we are not alone :(

I thought I was the only one, its so bloody annoying. When an application accesses the sound device after a certain period of inactivity, POP right at the beginning, then all is well.

---

### Post by FormerSlacker on 2009-10-14
> **BXCracer said:**
> You probably have a HDA audio card. If so then those clicks is caused by the power saving option introduced in karmic. You can solve this problem by commenting out the last line in the /etc/modprobe.d/alsa-base.conf

Thank you very much. Problem solved.

---

