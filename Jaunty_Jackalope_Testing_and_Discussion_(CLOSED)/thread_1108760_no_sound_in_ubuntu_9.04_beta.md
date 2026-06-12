---
title: "no sound in ubuntu 9.04 beta"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sparkythewondersquid on 2009-03-28
I just installed ubuntu 9.04 beta (jaunty jackolope) and it looks great!!:P there were updates available (of course) when I rebooted there was no sound :confused: I have been able to get my music to play I changed all my sound settings but internet sound does not work (youtube etc) any one else have this happen? any help out there?

---

### Post by SunnyRabbiera on 2009-03-28
It is a beta, so I would expect unstability.
I would use Intrepid instead or even hardy if you want to sacrifice "latest and greatest" for stability

---

### Post by feelshift on 2009-03-28
Beta is by definition unstable. As SunnyRabbiera suggested, you should use 8.10 if you want to have a stable system. You can also fill a bug report :)

---

### Post by RadicalRaid on 2009-03-28
Same problem here, linuxant driver for my system isn't working :(.
I know it's unstable, I just couldn't wait until the release next month :P.

Should anyone have any suggestions, I'll be happy to hear them!

Cheers!

---

### Post by RadicalRaid on 2009-03-28
Just saying:
[http://ubuntuforums.org/showthread.php?t=1013750](http://ubuntuforums.org/showthread.php?t=1013750)

Worked like a charm for me!
It's got my vote :).

Cheers!

---

### Post by sparkythewondersquid on 2009-03-29
well I am getting all sound except the theme music (when ubuntu starts up) and internet (youtube, google video, etc.) my music plays the login (card shuffle) plays how strange is that any ideas?

---

### Post by xsstevec on 2009-04-14
> **SunnyRabbiera said:**
> It is a beta, so I would expect unstability.
I would use Intrepid instead or even hardy if you want to sacrifice "latest and greatest" for stability

I had a math teacher in high school who responded to a student who said he should multiply the equation by zero and that would solve it. He responded with "while that is technically correct, it is a trivial answer".

This response reminded me of it. If I wanted 8.10, I would have installed 8.10. The whole point of coming to the forums is to get answers to problems we are facing trying to make Ubuntu more user-friendly for everyone and spread the gospel. But this and all responses like are are as stupid as the person who wrote it.

If you can't help, or suggest anything more than "you shouldn't be using it", then shut your trap and leave the forums to those who are serious about all this.

---

### Post by dasme on 2009-04-14
> **xsstevec said:**
> I had a math teacher in high school who responded to a student who said he should multiply the equation by zero and that would solve it. He responded with "while that is technically correct, it is a trivial answer".

This response reminded me of it. If I wanted 8.10, I would have installed 8.10. The whole point of coming to the forums is to get answers to problems we are facing trying to make Ubuntu more user-friendly for everyone and spread the gospel. But this and all responses like are are as stupid as the person who wrote it.

If you can't help, or suggest anything more than "you shouldn't be using it", then shut your trap and leave the forums to those who are serious about all this.

well said xsstevec ;)

BTW i have RTL268 sound card and it works perfectly :)

---

### Post by Claus7 on 2009-04-14
Hello,

there are a lot of things that might go wrong. In my case I had two sound cards and this was causing you tube and flash in general not to have sound. I do not know what is faulty, yet reading my journey to configure sound, might solve your problems:
[http://ubuntuforums.org/showthread.php?t=1108518](http://ubuntuforums.org/showthread.php?t=1108518)

Regards!

---

### Post by crimsun on 2009-04-14
> **sparkythewondersquid said:**
> I just installed ubuntu 9.04 beta (jaunty jackolope) and it looks great!!:P there were updates available (of course) when I rebooted there was no sound :confused: I have been able to get my music to play I changed all my sound settings but internet sound does not work (youtube etc) any one else have this happen? any help out there?

Please install pavucontrol and make sure that the Flash streams are being routed to the intended audio device.

---

### Post by Zorael on 2009-04-14
> **Claus7 said:**
> In my case I had two sound cards and this was causing you tube and flash in general not to have sound. I do not know what is faulty,
Had a look at [http://ubuntuforums.org/showthread.php?p=6883063#post6883063?](http://ubuntuforums.org/showthread.php?p=6883063#post6883063?)

---

### Post by xerosis on 2009-04-14
I think I'm seeing this. Jaunty has been the first version that lets my flash sound work, I'm running kubuntu but since the last update flash sound has stopped again. I installed pavucontrol and the flash is going to the right stream. Any ideas?

---

### Post by daboroe on 2009-04-14
is it like anything like this: [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/349633](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/349633) ?

---

### Post by xerosis on 2009-04-14
> **daboroe said:**
> is it like anything like this: [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/349633](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/349633) ?

Nope, mine's just purely a flash/pulse issue.

---

### Post by Claus7 on 2009-04-14
Hello,

> **Zorael said:**
> Had a look at [http://ubuntuforums.org/showthread.php?p=6883063#post6883063?](http://ubuntuforums.org/showthread.php?p=6883063#post6883063?)
I think that this post refers to me. Thank you for your answer Zorael, yet I was able to solve my problem. The "I do not know" expression goes to the thread starter and the problem he is facing.

> **xerosis said:**
> I think I'm seeing this. Jaunty has been the first version that lets my flash sound work, I'm running kubuntu but since the last update flash sound has stopped again. I installed pavucontrol and the flash is going to the right stream. Any ideas?

The answer I'll give you won't enlighten you a lot, yet I would advice you to take the test that jaunty provides and send feedback to the developers explaining in the sound section what in not ok. If you made it working it is supposed to work in the final version. Always have in mind that it is still beta. I do know that this is not the answer you might expect, yet an update cause my entire system to collapse. 

Does also my previous link say anything to you? Trying to fix my problem I came across many different flash player issues. I hope that the latest updates will fix your issue.

Regards!

---

