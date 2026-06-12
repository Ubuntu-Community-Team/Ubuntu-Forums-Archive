---
title: "Update notifier not working?"
date: 2009-03-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by chazh on 2009-03-07
I've just installed a fresh system from the Alpha5 CD, and as far as I can tell, update notifier isn't working. It seems to be running, but never tells me about any updates - nothing ever appears in the systray, despite aptitude telling me that there are lots of packages to update.

Is this a known issue at the moment?

Thanks,
Chaz

---

### Post by DougieFresh4U on 2009-03-07
I don't know if it's a known issue, but I seem to have the same problem. Haven't seen 'update notifier' for about a week now.

---

### Post by JohnJackson on 2009-03-07
Isn't this because of the new notification system? The update manager is supposed to pop up every so often when there are updates instead.

---

### Post by DougieFresh4U on 2009-03-07
> **JohnJackson said:**
> Isn't this because of the new notification system? The update manager is supposed to pop up every so often when there are updates instead.
Exactly, there have been many updates in the past week and 'update notifier'** has not shown up at all**

---

### Post by dBuster on 2009-03-07
Same thing here, at first I thought it might have had something to do with the broken packages but now I am updating manually again and did not get notified of it.  However this update is updating the notifier as well so we shall see...

---

### Post by Elfy on 2009-03-12
I hadn't bothered to look here for this - thought it was just me.

I've not had an update notification for a long time.

---

### Post by trot2millah on 2009-03-12
Been a problem with me as well, all the other notifications have worked fine.  How strange.

---

### Post by Elfy on 2009-03-12
Indeed - but I'm not sure whether it's a bug or it's supposed to work like this ...

There is a bug for it [https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/338501/](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/338501/)

---

### Post by aldeby on 2009-03-20
It must be a bug, and I still have the same problem!

It seems to be a (silly) new feature being discussed here> [https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945)

---

### Post by Elfy on 2009-03-20
I don't think that it is a bug, it's doing what is supposed to do :(

[https://wiki.ubuntu.com/NotifyOSD#Update](https://wiki.ubuntu.com/NotifyOSD#Update) Manager

I think that if you didn't look at updates for a week then eventually show up, you can put comments here - whether any one bothers to look or take notice is another thing altogether

[https://wiki.ubuntu.com/NotifyOSD/Comments](https://wiki.ubuntu.com/NotifyOSD/Comments)

---

### Post by Kazade on 2009-03-20
I've just read through all of the emails to ubuntu-devel about the update manager. Seriously, what are the guys at Canonical smoking?

[ rant ]
Opening a window automatically whether it's in the background or not is so obviously a terrible idea. If I see a window in the window list flashing I have to switch to it just to stop the irritation out of the corner of my eye. Also, if a new user sees a random window open all by itself they are more likely to either close it without reading it, or think they are infected with some virus. There is never a suitable time to pop up a window for updates because chances are I'm going to be busy with something else.

Removing the notification icon is the icing on the cake of the sheer lunacy of the whole thing. I want to know if my computer is up-to-date all the time, not when the update manager wants to tell me by popping up a window. So now even though I've TURNED OFF the stupid auto-launching I still have to manually run apt-get update/upgrade to find out if I have updates. 

What was wrong with the old behaviour? Canonical seem to think that people aren't installing updates. Erm right so because some people apparently can't read, or hover or click an icon, I should be punished for that?

But, despite all the above, the real thing that has me completely pissed off is that the guys from Canonical, the DX team and even Mark Shuttleworth did not ONCE say "we'll consider reverting" or anything those lines, they just basically came across like they stuck their fingers in their ears and just keep saying "trust us, this way is awesome" or "this was discussed at UDS".

[ /rant ]

Sorry, I've been trying to not comment on this change for ages, but after reading the emails from the mailing list I got a bit wound up about the whole thing.

P.S I'm in no way dissing the new notifications. What I am attacking is an implemented change that affects everyone, but is targeted at the tiny percentage of people that are refusing/ignoring the current update system anyway.

---

