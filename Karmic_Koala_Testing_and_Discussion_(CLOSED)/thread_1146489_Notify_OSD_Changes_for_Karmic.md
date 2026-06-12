---
title: "Notify OSD Changes for Karmic"
date: 2009-05-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ghindo on 2009-05-02
It looks like Notify OSD is going to change a bit for Karmic; or at the very least, changes will be discussed at UDS.  Here's what they're saying on the Ayatana mailing list:> At UDS Karmic this month, there will be a session for discussing
improvements to the Notify OSD notification server.
<https://blueprints.launchpad.net/ubuntu/+spec/dx-karmic-notify-osd>

Topics for discussion will include:
*   experimenting with better positioning for the notification bubbles
*   improving the appearance and behavior (making composited bubbles
    more obviously unclickable, and non-composited bubbles classier)
*   implementing the duration rules, so that notifications with longer
    text are shown for longer
*   better handling of long backlogs of notifications
*   investigating whether we can use non-critical priorities for
    anything useful
*   helping to get the FreeDesktop.org notifications specification to
    1.0
*   a Qt implementation
*   investigating a "do-not-disturb" mode
*   accessibility, e.g. sound theme compliance and maybe alt text for
    icons
*   media key confirmation bubbles (Play, Pause, Previous, Next)
*   suppressing bubbles when any window is full-screen
*   a test suite for the rendering layer.

If you want to take part in the discussion, keep an eye on the schedule
<http://summit.ubuntu.com/uds-karmic/> to find out when the session will
be. If you can't attend (either physically or virtually) but have
suggestions you'd like considered, please add them to the Notify OSD
comments page. <https://wiki.ubuntu.com/NotifyOSD/Comments>[https://lists.launchpad.net/ayatana/msg00051.html](https://lists.launchpad.net/ayatana/msg00051.html)

---

### Post by miwaypet on 2009-05-02
Yeh. It actually gave a notification for updates yesterday. Cool.

---

### Post by hanzomon4 on 2009-05-03
I just want it to stop crashing my computer when I have hulu.com/ or any web video at full screen

---

### Post by ktp on 2009-05-03
> **hanzomon4 said:**
> I just want it to stop crashing my computer when I have hulu.com/ or any web video at full screen

That seems like reasonable thing to ask. :P

---

### Post by mc4100 on 2009-05-03
> **hanzomon4 said:**
> I just want it to stop crashing my computer when I have hulu.com/ or any web video at full screen
If it's crashing *anything* then bugs need to be filed, but as for general interruptions just like this, [Shuttleworth's comments on the Ayatana mailinglist]("https://lists.launchpad.net/ayatana/msg00003.html") seem to fit perfectly.

---

### Post by CarpKing on 2009-05-04
I hope they get rid of the Update Manager popunder business.  I like the bubbles, but opening windows like that is aggravating.

---

### Post by Gourgi on 2009-05-04
> **CarpKing said:**
> I hope they get rid of the Update Manager popunder business.  I like the bubbles, but opening windows like that is aggravating.

maybe this is what you need
[http://www.ubuntu.com/getubuntu/releasenotes/904#Change%20in%20notifications%20of%20available%20updates](http://www.ubuntu.com/getubuntu/releasenotes/904#Change%20in%20notifications%20of%20available%20updates) ;)

---

### Post by kpkeerthi on 2009-05-04
> * media key confirmation bubbles (Play, Pause, Previous, Next)
This is a much needed improvement.

---

### Post by CarpKing on 2009-05-05
> **Gourgi said:**
> maybe this is what you need
[http://www.ubuntu.com/getubuntu/releasenotes/904#Change%20in%20notifications%20of%20available%20updates](http://www.ubuntu.com/getubuntu/releasenotes/904#Change%20in%20notifications%20of%20available%20updates) ;)

Thanks for that, but I do think they need to find a better solution for update notifications than the one they came up with for Jaunty.  I liked the old system a lot, but I do see their point about it not being intuitive.  I just don't think that popping up a window is an improvement.

---

### Post by victorche on 2009-05-05
> Notify OSD notification server

How serious it sounds... Well, guys here is what I think:

I was shocked even in the Jaunty forums how a topic about "notification rocket/server/system" can grow that fast. These notification bubbles were one of the "major/super/mega/cool" new features in Ubuntu... :lolflag:

Notification server sounds... so stupid! What is this?! Just a bubble showing the next mp3 song. And can this be the "new/ultra/big" feature?!?

Don't make me laugh!

Besides, how can someone do "improving the appearance", when the new theme is not even 10% done?

I am a web designer and it sounds like "hey, we don't have the site design yet, but we already made the HOME button"... How can you improve the appearance of something on the user's screen, when you still don't know the look of the whole screen?!

---

### Post by mpt on 2009-05-05
> **victorche said:**
> Notification server sounds... so stupid! What is this?! Just a bubble showing the next mp3 song. And can this be the "new/ultra/big" feature?!?

It’s called a notification server because it shows notifications and is implemented as a server. It’s used by dozens of programs, not just music players. And no, nobody in the Design or Desktop Experience teams ever claimed it was a big feature. We deliberately started small.

> *Don't make me laugh!*

As you wish.

> *Besides, how can someone do "improving the appearance", when the new theme is not even 10% done?*

That’s a fair question. The answer is that the notification bubbles are pretty much unique in behavior: they’re the only things in the interface that can be “clicked through” to work with whatever is underneath. So we can adjust the appearance to make that behavior more obvious, without being too concerned about how elements that behave in other ways should look.

(Thanks for starting this thread, ghindo.)

---

### Post by ktp on 2009-05-05
> **CarpKing said:**
> Thanks for that, but I do think they need to find a better solution for update notifications than the one they came up with for Jaunty.  I liked the old system a lot, but I do see their point about it not being intuitive.  I just don't think that popping up a window is an improvement.

I wouldn't hold my breath on no more popups...the notify OSD spec basically says if you need user interaction popup a window.

---

### Post by victorche on 2009-05-06
> **mpt said:**
> ...And no, nobody in the Design or Desktop Experience teams ever claimed it was a big feature. We deliberately started small...


It is not true... In every news/page/info about the release, it was announced as a major new feature ;)

> A new integrated notification system appears in Ubuntu 9.04 for the first time. This system combines the notification methods of various applications and presents that information in a simple, unobtrusive manner.

[http://www.ubuntu.com/news/ubuntu-9.04-desktop](http://www.ubuntu.com/news/ubuntu-9.04-desktop)

You can check it for yourself. And yes, I know why it is called a "server". Anyway, it sounds too strange. And I also know that it is not just for the music players. But no matter if it shows me the new updates, or it shows me who's online in my ICQ list... It is still just a dark bubble. Please, don't announce it as an OS revolution ;) Bubbles were invented a long time ago ;)

And next time, please announce something bigger, like a new look for example. Because, no matter how powerful and stable Ubuntu is, it still looks like Win 98 ages. Especially for the new users, believe me ;)

---

### Post by tom56 on 2009-05-06
> **victorche said:**
> It is not true... In every news/page/info about the release, it was announced as a major new feature ;)



[http://www.ubuntu.com/news/ubuntu-9.04-desktop](http://www.ubuntu.com/news/ubuntu-9.04-desktop)

You can check it for yourself. And yes, I know why it is called a "server". Anyway, it sounds too strange. And I also know that it is not just for the music players. But no matter if it shows me the new updates, or it shows me who's online in my ICQ list... It is still just a dark bubble. Please, don't announce it as an OS revolution ;) Bubbles were invented a long time ago ;)

And next time, please announce something bigger, like a new look for example. Because, no matter how powerful and stable Ubuntu is, it still looks like Win 98 ages. Especially for the new users, believe me ;)

What new feature are you writing for Karmic then?

---

### Post by Merk42 on 2009-05-06
> **tom56 said:**
> What new feature are you writing for Karmic then?

Hey did you see that new blockbuster movie? You **have** to like it, because you're not allowed to be disappointed in it unless you've made your own movie.

How about that new reality show that the same as all the others? Great huh? Because since you didn't make a reality show you can't say it's bad.

---

### Post by tom56 on 2009-05-06
> **Merk42 said:**
> Hey did you see that new blockbuster movie? You **have** to like it, because you're not allowed to be disappointed in it unless you've made your own movie.

How about that new reality show that the same as all the others? Great huh? Because since you didn't make a reality show you can't say it's bad.

I've never criticised a movie by complaining that making a movie isn't that big of a deal. I've never implied that making a reality show was easy.

He was saying that the feature was over-hyped, as though it wasn't hard work to do. Which I'm sure it was. And if it's that easy then he can do better himself.

The anonymity of a forum makes it very easy to criticise in a way that is not only unhelpful, but also rude. Do you think he would talk that way to the faces of the people who worked hard on that project. I doubt it.

EDIT: Just noticed MPT posted above. Thank you for the work you guys did! I think this stuff looks great and really helps contribute to that "polished" feel.

---

### Post by el_itur on 2009-05-06
Can we stop feeding the trolls and have a real discussion or this thread closed?

---

### Post by dirtylobster on 2009-05-06
Just wanted to chime in and say I love notify-osd and how it integrates different application to create a more unified desktop feel.

---

### Post by mister_pink on 2009-05-06
I'm also going to chime in and say I love the bubbles, but please, please, please come up with something better than bringing the update manager up. I'd argue that popups for things that really do need interaction _right now_ is fine, but is the update manager really important enough to warrent bringing up the whole interface? After all its never vital that they are handled right now.

I really think its one example of something that should be left with a pop up bubble and a thing in the notification area. I know notification area clutter was the main point of all this but... well one exception cant be that bad!

---

### Post by CarpKing on 2009-05-07
> **mister_pink said:**
> I really think its one example of something that should be left with a pop up bubble and a thing in the notification area. I know notification area clutter was the main point of all this but... well one exception cant be that bad!

Somewhere else someone pointed out the ironic fact that Update Notifier is the only program most people have ever seen that uses the notification area properly (e.g. places an icon there to notify you of something but never otherwise).

---

### Post by ktp on 2009-05-07
> **carpking said:**
> somewhere else someone pointed out the ironic fact that update notifier is the only program most people have ever seen that uses the notification area properly (e.g. Places an icon there to notify you of something but never otherwise).

+1

---

### Post by mpt on 2009-05-08
> **victorche said:**
> It is not true... In every news/page/info about the release, it was announced as a major new feature ;)

Read closer: I said “nobody **in the Design or Desktop Experience teams** ever claimed it was a big feature”. What journalists or marketers latch on to is pretty much out of our control.

> *[http://www.ubuntu.com/news/ubuntu-9.04-desktop](http://www.ubuntu.com/news/ubuntu-9.04-desktop)*

Whoo, two sentences in a 26-sentence press release. :rolleyes:

> *And next time, please announce something bigger, like a new look for example.*

I can’t promise a new look, but there will be [other interesting stuff]("https://blueprints.launchpad.net/ubuntu/+spec/software-library").

> **mister_pink said:**
> I'd argue that popups for things that really do need interaction _right now_ is fine, but is the update manager really important enough to warrent bringing up the whole interface?

You have a good point. I’ll see if we can make the Update Manager window much smaller by default when it comes up automatically. Just “There are updates available, would you like to install them”, or something like that, where you can expand it if you want to see the list of updates.

---

### Post by kansasnoob on 2009-05-08
The biggest thing to me is making the notifications GUI configurable.

I'm visually impaired and I need to be able to relocate them and change the amount of time they're displayed.

---

### Post by TrueTom on 2009-05-08
> Sam is a college student who has recently migrated from to Windows XP to Ubuntu because he was fed up with adult sites installing spyware on his computer. The reason he had so much trouble with spyware was that XP kept on popping up balloons in the corner of the screen to tell him about security updates, but he closed them because that was the easiest thing to do.

The theistic approach to software engineering: State your use cases in a way so your prefered solution fits best... :)

---

### Post by tom56 on 2009-05-08
> **mpt said:**
> You have a good point. I&#8217;ll see if we can make the Update Manager window much smaller by default when it comes up automatically. Just &#8220;There are updates available, would you like to install them&#8221;, or something like that, where you can expand it if you want to see the list of updates.

The PackageKit update window is great for this I think, how about for 9.10 Update Manager is altered to look more like PackageKit in preparation for including PackageKit in a later release.

[http://www.packagekit.org/img/gpk-updates-overview.png](http://www.packagekit.org/img/gpk-updates-overview.png)

I think people would take less issue with Update Manager popping up if it looked less like a full-blown application.

---

