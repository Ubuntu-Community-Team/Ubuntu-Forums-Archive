---
title: "Notifications too low"
date: 2009-09-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sashin on 2009-09-28
Anyone else have this problem?

---

### Post by TrueTom on 2009-09-28
Yes, and it's on purpose.

---

### Post by Sophont on 2009-09-28
I don't think it's a problem. Looks like that on all my machines.

Likely on purpose.

---

### Post by Sashin on 2009-09-28
Why would it be on purpose? It really looks out of place to me.

---

### Post by hikaricore on 2009-09-28
Looks out of place to me as well, should be much higher.

---

### Post by OliW on 2009-09-28
You say it's on purpose but sometimes I still get notifications right at the top (like it was).

On top of that, banshee's notifications are forced to queue so if you skip a few tracks, it can take several minutes for the message queue to clear.

---

### Post by Bou on 2009-09-28
> **TrueTom said:**
> Yes, and it's on purpose.

What would be the reason?

---

### Post by uBeer on 2009-09-28
It looks really inconsistent now. Very out of place. But it is probably so that the minimize, maximize and close buttons stay visible of fullscreen applications. Don't like it!

---

### Post by ricsi-pontaz on 2009-09-28
> **Bou said:**
> What would be the reason?

I would like to know it too.

---

### Post by graaant on 2009-09-28
I can't remember the Launch Pad bug number, but apparently it's to test different notification types. Things like volume, brightness and stuff take the first level and other stuff like Pidgin etc get the second level.
I believe it's just a UI test/experiment, I'm sure it'll be sorted soon.

---

### Post by dasunst3r on 2009-09-28
I have been looking for a place where I can change up the libnotify settings for a pretty long time now.  Any ideas as to where those are if they even exist?

---

### Post by ELD on 2009-09-28
> **dasunst3r said:**
> I have been looking for a place where I can change up the libnotify settings for a pretty long time now.  Any ideas as to where those are if they even exist?

From the conversation we had before complaining about them sticking the damn things in the middle of the screen (stupid!) they won't allow us to edit it easily.

There is a config file somewhere i think, but no UI for it.

---

### Post by zekopeko on 2009-09-28
> **ELD said:**
> From the conversation we had before complaining about them sticking the damn things in the middle of the screen (stupid!) they won't allow us to edit it easily.

There is a config file somewhere i think, but no UI for it.

From a coders perspective it's far better to less options and instead sane defaults. Less code means less bugs.

---

### Post by ELD on 2009-09-28
> **zekopeko said:**
> From a coders perspective it's far better to less options and instead sane defaults. Less code means less bugs.

I can understand that from a certain point of view but seriously think about what your saying. Most other apps are able to move around freely, gnome panels included.

How can a small application allowing you to select a position for the notifications introduce many more bugs, any bugs introduced can be squashed qucikly, after all it is simply moving a notification from one area to another.
I highly doubt it can introduce new bugs as they tested other areas during karmic cycle.

So yes a sane default is required but not at the expense of removing options for configuration, that said i doubt it will be too long before someone adds a ppa with a configuration app. Hint hint.

---

### Post by mdurham on 2009-09-28
Is there any way to turn them off?

---

### Post by Eestlane on 2009-09-28
It's interesting that when I change the volume with my keyboard media keys, the notification will be after the panel without the gap other notifications have.

---

### Post by coldReactive on 2009-09-28
This has also happened in jaunty (IE: For Firefox libnotify extension)

So it's not just Karmic (Where this topic is.)

Edit: No wait, it's probably because I added the gastly PPA: [https://launchpad.net/~gastly/+archive/gastly-main](https://launchpad.net/~gastly/+archive/gastly-main)

---

### Post by andrewabc on 2009-09-28
Are notifications customizable yet? They were not in Jaunty.
Can you pick it to be anywheres on screen? Transparency? Font size/colour?

---

### Post by tjeremiah on 2009-09-28
I dont have a problem with it.

---

### Post by Kazade on 2009-09-28
> **andrewabc said:**
> Are notifications customizable yet? They were not in Jaunty.
Can you pick it to be anywheres on screen? Transparency? Font size/colour?

No.

This conversation keeps coming up.. this is what happens:

1. A change is made to some visible part of the desktop (notify-osd, update-notifier etc.) which many users don't like
2. Confused users ask if it can be reverted
3. DX team/Canonical/Mark says that it's by design
4. Users ask if it can be at least be configurable
5. Users are told that all configuration is bad and people complaining are the minority.
6. Bug is marked as Invalid - Won't Fix.
7. Go to 1.

notify-osd likely won't have any user configuration. At the moment you can configure whether it's top-right, or middle-right. But this is just a temporary gconf key which Mark Shuttleworth said is there to facilitate testing.

The only way to get configuration in notify-osd is to patch it, but I wouldn't count on your patches being accepted upstream, if I thought they would, I would have done it by now. I'm just glad the default is still top-right (although bottom-right would be more suitable IMO, then it wouldn't get in the way of the search box in FF).

---

### Post by buzzmandt on 2009-09-28
not trying to flame (honestly) but isn't that the way of gnome?  less user configuration is preferred?

---

### Post by Kazade on 2009-09-28
> **buzzmandt said:**
> not trying to flame (honestly) but isn't that the way of gnome?  less user configuration is preferred?

There is *less* configuration (which I happen to agree with) and then there is *no* configuration.

The position of notifications is something that can not please everyone (think people with accessibility issues, people with differently configured desktops etc.). There is no "default" that will be usable for all, yes there will be a position that pleases the majority of people (e.g. top right versus the screen centre) though.

---

### Post by Cenotaph on 2009-09-28
> **buzzmandt said:**
> not trying to flame (honestly) but isn't that the way of gnome?  less user configuration is preferred?

doesnt gnome allow you to configure the corner in each notifications pop up?

---

### Post by cyberkilla on 2009-09-28
> **Kazade said:**
> There is *less* configuration (which I happen to agree with) and then there is *no* configuration.

The position of notifications is something that can not please everyone (think people with accessibility issues, people with differently configured desktops etc.). There is no "default" that will be usable for all, yes there will be a position that pleases the majority of people (e.g. top right versus the screen centre) though.

I agree with you - it can't be that hard to change the location of the notification. Also, is there some sort of image(s) that can be swapped out to change the way the notification looks?

I'm not personally interested in theming the thing, but it stands to reason that it will look out of place on some GTK themes.

---

### Post by lucazade on 2009-09-28
There was a gconf-setting (apps/notify-osd/gravity) to tune the placement but it doesn't work anymore :(

---

### Post by Kazade on 2009-09-28
> **cyberkilla said:**
> I agree with you - it can't be that hard to change the location of the notification. 

No it's not, well sort of... I've been through the code. The problem with fixing it to be configurable is the whole thing has been sort of hard coded with one position in mind (top right). Really, the bubbles should use a relative position from some configurable central point, rather than absolute screen positions. If the program had been written from the outset with position configuration in mind, it wouldn't have been much larger (SLOC-wise).

> 
Also, is there some sort of image(s) that can be swapped out to change the way the notification looks?

No, I don't believe so. I think the background colour is stored in the source.

> 
I'm not personally interested in theming the thing, but it stands to reason that it will look out of place on some GTK themes.

+1

---

### Post by Leighman on 2009-09-28
I also am not a fan of the two different placements.
Also Banshee seems to alternate between using the top slot and the second slot which is definitely stupid.

---

### Post by ninjapirate89 on 2009-09-28
My only complaint with the notifications is that since I have an old battery for my laptop, karmic insists on notifying me about it every time I restart.

---

### Post by coldReactive on 2009-09-28
> **lucazade said:**
> There was a gconf-setting (apps/notify-osd/gravity) to tune the placement but it doesn't work anymore :(

in fact, the entire notify-osd is missing from apps/ for me

---

### Post by hanzomon4 on 2009-09-28
Could you add your picture to this bug report [https://bugs.launchpad.net/notify-osd/+bug/420514]("https://bugs.launchpad.net/notify-osd/+bug/420514")

Oh and +1... This is so obviously wrong that I never even considered that it might be on purpose

---

### Post by LKjell on 2009-09-28
Feels good on my laptop.

---

### Post by MilesRdz on 2009-09-28
It annoys me (the placement) especially since I have one bar.

---

### Post by pelle.k on 2009-09-28
> **hanzomon4 said:**
> Could you add your picture to this bug report 
I borrowed it (blurred out username and details) and attached it to my comment in that bug report. Hope you don't mind Sashin!

---

### Post by kansasnoob on 2009-09-28
Well, I've been nonchalant about this because I customize the hell out of my desktop anyway.

Look here:

[http://ubuntuforums.org/showthread.php?t=1251100&page=9](http://ubuntuforums.org/showthread.php?t=1251100&page=9)

Post #82 (from me):


> 
Being visually impaired, my situation is just the opposite, I need the notifications to remain until I've had time to focus on and read them.

Thus the need for notify-osd to be user configurable. No one position or length of time displayed will suit every individual.

I got a reply in post #83 and didn't follow thru:

> This. We need to make sure that Mark et. al. understand it's not just about what people want, it's what they *need* to make use of the notifications. I would suggest that anyone with concerns about this reply to this email thread: [https://lists.launchpad.net/ayatana/msg00589.html](https://lists.launchpad.net/ayatana/msg00589.html)

I don't think anyone from the team reads the forums.

(If you aren't signed up to the ayatana list, sign up then make sure your subject line is "Re: [Ayatana] Notify OSD: Talk about giving the user preferences" and the online threader will understand that it's part of the thread). 

Anyway I never followed thru because in Jaunty I simply reinstalled 'notification-daemon' and removed 'notify-osd' (which also removes the meta-package ubuntu-desktop so I don't recommend that in Karmic at this point in development - **in fact I haven't even tried in Karmic!**).

So I guess I should read and possibly reply to the aforementioned email and look into signing up on that "ayatana list". If it's purely email I should be OK, but due to my vision problems I don't do IRC or any form of chat.

---

### Post by Sashin on 2009-09-28
well if it'll help the bug get fixed of course I don't mind.

---

### Post by kansasnoob on 2009-09-28
Errrm, I guess I'm stupid, where do I reply to this:

[https://lists.launchpad.net/ayatana/msg00589.html](https://lists.launchpad.net/ayatana/msg00589.html)

---

### Post by nzjrs on 2009-09-28
> **Sashin said:**
> well if it'll help the bug get fixed of course I don't mind.

[https://bugs.launchpad.net/notify-osd/+bug/436975](https://bugs.launchpad.net/notify-osd/+bug/436975)

---

### Post by kansasnoob on 2009-09-28
> **Sashin said:**
> well if it'll help the bug get fixed of course I don't mind.

Well, it's not truly a "bug", it's a feature we'd like to see changed. In both Jaunty and Karmic if you look in Main Menu > Pref. you'll find a Pop-up Notifications gui:

[ATTACH]130104[/ATTACH]

It doesn't work, but it shows there has been some thought about making it configurable.

---

### Post by coldReactive on 2009-09-28
> **kansasnoob said:**
> Well, it's not truly a "bug", it's a feature we'd like to see changed. In both Jaunty and Karmic if you look in Main Menu > Pref. you'll find a Pop-up Notifications gui:

[ATTACH]130104[/ATTACH]

It doesn't work, but it shows there has been some thought about making it configurable.

Invalid attachment

---

### Post by kansasnoob on 2009-09-28
Well I did it:

[ATTACH]130106[/ATTACH]

And I was approved to get mailings so when I see these threads pop up I'll try my best to keep folks informed.

Hopefully that will help.

EDIT: On the lighter side: I guess being a blind old fart ain't so bad sometimes ;^)

---

### Post by Kazade on 2009-09-29
> **kansasnoob said:**
> Errrm, I guess I'm stupid, where do I reply to this:

[https://lists.launchpad.net/ayatana/msg00589.html](https://lists.launchpad.net/ayatana/msg00589.html)

Make sure you are subscribed to the mailing list ([here]("https://launchpad.net/~ayatana")). Then send an email to [email]ayatana@lists.launchpad.net[/email] with the subject I mentioned (Re: [Ayatana] Notify OSD: Talk about giving the user preferences).

---

### Post by coldReactive on 2009-09-29
> **kansasnoob said:**
> Well I did it:

[ATTACH]130106[/ATTACH]

And I was approved to get mailings so when I see these threads pop up I'll try my best to keep folks informed.

Hopefully that will help.

EDIT: On the lighter side: I guess being a blind old fart ain't so bad sometimes ;^)

Invalid Attachment

---

### Post by Mr. Picklesworth on 2009-09-29
If I recall correctly, the two slots are more tightly defined for synchronuous (like getting an email) and asynchronous notifications (like adjusting the volume). In this way, they should jump around *less* than before, not more :/


The pop-up notifications GUI was for the previous notification-daemon. The configurable notification placements were for notification-daemon. Notification-daemon is the one with the giant yellow bubbles that fly all over the screen.

(Personally, I think the notification area applet should itself act as a notification daemon and notifications should be attached firmly to it, since so many notifications reference system tray applets...)

---

### Post by zekopeko on 2009-09-29
> **Mr. Picklesworth said:**
> If I recall correctly, the two slots are more tightly defined for synchronuous (like getting an email) and asynchronous notifications (like adjusting the volume). In this way, they should jump around *less* than before, not more :/

The problem is that it looks broken. I'm expecting something to fill the empty space and it's not there.

---

### Post by kansasnoob on 2009-09-29
Well, I received a positive reply:

> Thanks for your feedback on notify-osd.

Notify-osd has been recently updated to provide some configuration keys
to help with a11y. See [https://bugs.launchpad.net/notify-osd/+bug/420514](https://bugs.launchpad.net/notify-osd/+bug/420514)
and for related bug reports:
[https://bugs.launchpad.net/notify-osd/+bugs?field.tag=a11y](https://bugs.launchpad.net/notify-osd/+bugs?field.tag=a11y)

The best way to voice this concern is to discuss it on the Ayatana list,
and based on the result, open a new bug report if the system has to be
changed.

See [https://launchpad.net/~ayatana](https://launchpad.net/~ayatana) <https://launchpad.net/%7Eayatana>

My thought is that this will eventually be fixed, so it's just a matter of being patient.

Oh and provide helpful feedback in the bug reports.

---

### Post by motang on 2009-09-29
> **graaant said:**
> I can't remember the Launch Pad bug number, but apparently it's to test different notification types. Things like volume, brightness and stuff take the first level and other stuff like Pidgin etc get the second level.
I believe it's just a UI test/experiment, I'm sure it'll be sorted soon.
Oh I see, that is why wifi connection, volume control are higher up and track change and friends loggin in and out are lower...hmm!

---

### Post by Darkshade on 2009-09-29
I think the purpose of the whole thing is to keep notifications triggered by the user like volume or brightness on top, where they don't disturb so much since you already know you're changing the volume or adjusting the brightness and expect them to appear.
Others, like contacts logging in or new messages are placed lower in order to make them easier to see.
I have to admit that I used to miss many chat notifications back when they were on top because of using a maximized dark themed window (Dust in that case).

Of course this is just the way I see things, it might have nothing to do with the original idea.

---

### Post by johnl on 2009-09-29
Hi,

I fairly recently attached a patch here ([https://bugs.launchpad.net/bugs/346095](https://bugs.launchpad.net/bugs/346095)) that allows you to specify top-right/left, middle-right/left, or bottom-right/left as the preferred notification location.  It uses the apps/notify-osd/gravity gconf key that was mentioned previously (You may need to create this tree by hand).

If you build the bzr version of notify-osd and apply the patch, you can set the gconf key to one of the following values:
```

0:       GRAVITY_NONE,       // default position
1:       GRAVITY_NORTH_EAST, // top-right of screen
2:       GRAVITY_EAST,       // vertically centered at right of screen
3:       GRAVITY_SOUTH_EAST, // bottom-right of screen
4:       GRAVITY_SOUTH_WEST, // bottom-left of screen
5:       GRAVITY_WEST,       // vertically centered at left of screen
6:       GRAVITY_NORTH_WEST, // top-left of screen

```

I have also built a patch to allow you to change color via gconf, but it looks like the notify-osd team is going to add that on their own, so I haven't posted it anywhere.

---

### Post by lucazade on 2009-09-29
> **johnl said:**
> Hi,

I fairly recently attached a patch here ([https://bugs.launchpad.net/bugs/346095](https://bugs.launchpad.net/bugs/346095)) that allows you to specify top-right/left, middle-right/left, or bottom-right/left as the preferred notification location.  It uses the apps/notify-osd/gravity gconf key that was mentioned previously (You may need to create this tree by hand).

If you build the bzr version of notify-osd and apply the patch, you can set the gconf key to one of the following values:
```

0:       GRAVITY_NONE,       // default position
1:       GRAVITY_NORTH_EAST, // top-right of screen
2:       GRAVITY_EAST,       // vertically centered at right of screen
3:       GRAVITY_SOUTH_EAST, // bottom-right of screen
4:       GRAVITY_SOUTH_WEST, // bottom-left of screen
5:       GRAVITY_WEST,       // vertically centered at left of screen
6:       GRAVITY_NORTH_WEST, // top-left of screen

```

I have also built a patch to allow you to change color via gconf, but it looks like the notify-osd team is going to add that on their own, so I haven't posted it anywhere.

great stuff!

---

### Post by teh'p3nsi0n3r on 2009-10-15
Hi john, ive managed to open the patch in gedit, where/how do i apply this?. 
Thanks.



> **johnl said:**
> Hi,

I fairly recently attached a patch here ([https://bugs.launchpad.net/bugs/346095](https://bugs.launchpad.net/bugs/346095)) that allows you to specify top-right/left, middle-right/left, or bottom-right/left as the preferred notification location.  It uses the apps/notify-osd/gravity gconf key that was mentioned previously (You may need to create this tree by hand).

If you build the bzr version of notify-osd and apply the patch, you can set the gconf key to one of the following values:
```

0:       GRAVITY_NONE,       // default position
1:       GRAVITY_NORTH_EAST, // top-right of screen
2:       GRAVITY_EAST,       // vertically centered at right of screen
3:       GRAVITY_SOUTH_EAST, // bottom-right of screen
4:       GRAVITY_SOUTH_WEST, // bottom-left of screen
5:       GRAVITY_WEST,       // vertically centered at left of screen
6:       GRAVITY_NORTH_WEST, // top-left of screen

```

I have also built a patch to allow you to change color via gconf, but it looks like the notify-osd team is going to add that on their own, so I haven't posted it anywhere.

---

### Post by Joe_Bishop on 2009-10-15
> **teh'p3nsi0n3r said:**
> hi john, ive managed to open the patch in gedit, where/how do i apply this?. 
Thanks.
> managed
lol
man patch

---

### Post by teh'p3nsi0n3r on 2009-10-17
> **Joe_Bishop said:**
> lol
man patch

Personally failed to see the humor?, nor answer my original question.
thanks.

---

### Post by pelle.k on 2009-10-17
> **teh'p3nsi0n3r said:**
> Personally failed to see the humor?, nor answer my original question.
thanks.

Don't be offended. It was all in good fun, and i'm quite sure he did not think any less of you because you didn't know what to do with a patch. The fact of the matter is that it is simply a text file, so the fact that you made it sound like took some effort to open it up in gedit was kind of amusing.

That said, patching notify-osd may be a little much for you to take on before you know some of the basics of compiling and packaging debian software. Basically, you download the source (vanilla or debianized) and run the "patch" utility on the source directory. It's not like i can give you a one liner of code to complete the whole process of building notify-osd, so maybe someone who has recently done just that can give you a step by step guide or so.

---

### Post by teh'p3nsi0n3r on 2009-10-17
> **pelle.k said:**
> Don't be offended. It was all in good fun, and i'm quite sure he did not think any less of you because you didn't know what to do with a patch. The fact of the matter is that it is simply a text file, so the fact that you made it sound like took some effort to open it up in gedit was kind of amusing.

That said, patching notify-osd may be a little much for you to take on before you know some of the basics of compiling and packaging debian software. Basically, you download the source (vanilla or debianized) and run the "patch" utility on the source directory. It's not like i can give you a one liner of code to complete the whole process of building notify-osd, so maybe someone who has recently done just that can give you a step by step guide or so.

I didn't take offence, and I understood the 'joke', I said I failed to see the humor. :)
And thanks for explaining that pelle.k, yes it might be alittle over my head. It will be good when or if Canonical or someone release a gui option. :P

---

### Post by staticsage on 2009-10-24
If you're feeling brave, there is a guide on how to apply the patch here:

[http://forums.linuxmint.com/viewtopic.php?f=42&t=30857&p=178376](http://forums.linuxmint.com/viewtopic.php?f=42&t=30857&p=178376)

---

### Post by kansasnoob on 2009-10-24
Same patch here (look at post #50):

[https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/438536](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/438536)

More configurability coming but Shuttleworth hates it! (Wish I could find the quote.)

Open sorce is a bitch, if people don't like something they "hack" or "fork" it!

If Ubuntu ever starts making that impossible then they're done!

---

### Post by cyberkilla on 2009-10-25
I'm not keen on this behaviour either. Note: one of the users on that bug report links you to a PPA with a patched version of notify-osd, so no need to apply the patch yourself.

I haven't tried it yet. I find it disheartening that a lot of the new software is being stripped of any customisation features and the defaults are not sane.

---

