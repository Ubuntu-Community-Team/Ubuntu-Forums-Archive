---
title: "audacious"
date: 2009-07-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kaitwospirit on 2009-07-21
Are we still waiting for audacious-plugins and audacious-plugins-extra, or have they been replaced by the new things that audacious wants to install?

---

### Post by dino99 on 2009-07-21
cant find news

---

### Post by dino99 on 2009-07-21
After googling a little, audacious 2.1-1 is accepted in karmic & is already in the repo; but when trying to install it a warning concern the plugins drop it down. If i use the ftp.debian site, a different warning appear about libaudclient2 2.1-1 dependency not satisfied, curious all seem good but it is not.

Maybe i file a bug  :confused:

---

### Post by ronacc on 2009-07-21
audacious plugins and plugins-extra haven't caught up yet, wait for them .they are still at 2.01-3 and depend on audacious <2.1 .

---

### Post by zika on 2009-07-22
> **ronacc said:**
> audacious plugins and plugins-extra haven't caught up yet, wait for them .they are still at 2.01-3 and depend on audacious <2.1 .I have audacious 2.1.0 and plugins from dupondje-ppa ...

---

### Post by lithorus on 2009-07-22
> **zika said:**
> I have audacious 2.1.0 and plugins from dupondje-ppa ...
That ppa only has 2.0 not 2.1

---

### Post by zika on 2009-07-22
> **lithorus said:**
> That ppa only has 2.0 not 2.1Oops, You're right. I have (installed)```
audacious
libaudclient2
libsad2
libaudcore1
libaudutil1
libaudid3tag2
```of 2.1-1ubuntu1 and ```
audacious-plugins{,-extra}
```of 2.1-0ubuntu2~dupondje ...
Things change in this testing process  that (sometimes) I can't track them ... this dupondje mark lead to my wrong conclusion ... Sorry.
But, all of them are 2.1 and not 2.0 ...

---

### Post by lithorus on 2009-07-22
> **zika said:**
> Oops, You're right. I have (installed)```
audacious
libaudclient2
libsad2
libaudcore1
libaudutil1
libaudid3tag2
```of 2.1-1ubuntu1 and ```
audacious-plugins{,-extra}
```of 2.1-0ubuntu2~dupondje ...
Things change in this testing process  that (sometimes) I can track them ... this dupondje mark lead to my wrong conclusion ... Sorry.
But, all of them are 2.1 and not 2.0 ...
Then they must have been removed from the PPA again, weird...

---

### Post by papangul on 2009-07-23
My installed audacious(1.5) had become Audacious 2  after upgrading to karmic. After todays upgrade audacious has disappeared altogether.

---

### Post by papangul on 2009-07-23
Good news on audacious front. After todays update the dependency problems have been sorted out, audacious can be intalled now together with plugins and plugins extra version 2.1.

Edit:The bad news is that the quality of sound output of Vlc and rhythmbox is much better compared to audacious2. In fact whenever I play vlc or rbx after playing audacious, I am forced to say 'wow'.

---

### Post by oomingmak on 2009-07-24
> **papangul said:**
> The bad news is that the quality of sound output of Vlc and rhythmbox is much better compared to audacious2.
Do you happen to know why the audio quality for Audacious is not so good?

---

### Post by papangul on 2009-07-24
I don't know but something is fishy here. I had installed audacious 2 from a third party repo and the output then was quite good.

---

### Post by dino99 on 2009-07-25
I've installed it from synaptic (not ppa) and sound is good with vlc too.

---

### Post by zika on 2009-07-25
Try, among Preferences (Audio), "use fast floating-point conversion" ... That might improve Your perception of audacious-sound ...

---

### Post by papangul on 2009-07-25
Amazing solution...thanks a lot..:D

---

### Post by zika on 2009-07-25
> **papangul said:**
> Amazing solution...thanks a lot..:DBeware, turning on that option does not improve quality in all cases. It depends of Your equipment and the difference in quality might be masked by gain difference ... In my tests it proved better to turn all re-sampling and other transformations in audacious off and let pulse-audio and my HW to do that stuff. That might be the reason that other players sounded better that audacious ... You might be noticing just replay difference in gain... But that is the kind of stuff that is not for Ubuntu forum but for Hi-Fi ... I'm always mixing my interests ....

---

