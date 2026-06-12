---
title: "Notify-osd with location hints branch"
date: 2009-02-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Mr. Picklesworth on 2009-02-24
One thing currently missing in notify-osd is location hints! The old notification daemon could place notifications so that they were pointing at particular things, for example panel applets. This makes a TON of sense for notify-osd, since we are expecting the user to use the functions available elsewhere instead of chasing after buttons on notification bubbles.

Thus, I implemented location hints for notify-osd. Notifications can now be tied to specific places on the screen so people immediately know where to go after reading them. I kept in mind the fact that notifications must be awesomely simple, so they aren't actually *placed* differently.
I just have them glide into different places when they fade out. I'm avoiding any kind of scaling effect for now, unless it's absolutely necessary. (If it's absolutely necessary, it will probably be easier and cooler to have the bubble fade out with a radial alpha effect, so that one point remains more visible than the others, forming a sort of arrow).

Here is my bug report:
[https://bugs.edge.launchpad.net/notify-osd/+bug/333517](https://bugs.edge.launchpad.net/notify-osd/+bug/333517)
And the code!
[https://code.edge.launchpad.net/~dylanmccall/notify-osd/position-hints](https://code.edge.launchpad.net/~dylanmccall/notify-osd/position-hints)

I need to find out how well this actually works, so I'd really appreciate it if people could download my branch and give it a shot.

Just use this command to get the source:
bzr branch lp:~dylanmccall/notify-osd/position-hints

Then cd position-hints. If you don't have a ton of development packages on your system, use sudo apt-get build-dep notify-osd (sorry, I can't guarantee if that works since I'm not running Jaunty).

Then run...
```

./autogen.sh
./configure
make
killall notification-daemon; killall notify-osd; ./src/notify-osd
```

Now wait a few seconds and enjoy your new notifications! (Play something in Rhythmbox and you'll see the additional awesome fairly quickly).

Note that we aren't installing this or doing anything as root; it can just be run safely in place.

I would really like to know, first of all, if the animations as they are make the source of a notification clear enough. Do you ever find them extra distracting? Has this *broken* anything? Is it indeed awesome as I claim? What can be done to improve it? Etc :)

---

### Post by | MM | on 2009-02-24
Screenshot?  I am not sure they will support this change as they are trying to simplify the notification system.

---

### Post by Mr. Picklesworth on 2009-02-24
> **| MM | said:**
> Screenshot?  I am not sure they will support this change as they are trying to simplify the notification system.

Good thinking. Even better, here's a screencast!
Even though this change adds more movement, I think it *simplifies* the system since if gives the user a visual hint of where a notification came from instead of expecting him to somehow know which icon to click.

[http://dylanmccall.googlepages.com/notify-osd-pos-hints-screencast.ogv](http://dylanmccall.googlepages.com/notify-osd-pos-hints-screencast.ogv)

---

### Post by Jay_Bee on 2009-02-24
Hmm... good work but with all those icons I still can't quite make out where are those notifications "going" to.

---

### Post by smbm on 2009-02-24
> **Jay_Bee said:**
> Hmm... good work but with all those icons I still can't quite make out where are those notifications "going" to.

Ditto, I thought the notifications were going to pop out of the icons in the sys tray.

---

### Post by Mr. Picklesworth on 2009-02-24
> **smbm said:**
> Ditto, I thought the notifications were going to pop out of the icons in the sys tray.
I decided not to add to the fade in motion since the user is likely to only see that from his peripheral vision anyway, so it would just be an unnecessary distraction to give position-hinting notifications a competitive advantage.

So extra pointy it shall be, then :/

(Another thing that may help is a curved acceleration for the glide movement so that it's more visible at the start and end of motion... maybe a longer animation, though that could get me shot :P)

One issue with being *too* pointy is that these things often end up wrongly positioned, and we can't actually be sure about the size of what the notification is pointing at anyway. (All it gets is an X and Y coordinate). If it is wrong but appears Completely Convinced that it's right, people get confused. The hint that "this is hereabouts in the notification area" (eg: directing one's eyes to the general area to help him along) could be a bit more powerful, with some work.

---

### Post by smbm on 2009-02-24
> **Mr. Picklesworth said:**
> I decided not to add to the fade in motion since the user is likely to only see that from his peripheral vision anyway, so it would just be an unnecessary distraction to give position-hinting notifications a competitive advantage.

So extra pointy it shall be, then :/

(Another thing that may help is a curved acceleration for the glide movement so that it's more visible at the start and end of motion... maybe a longer animation, though that could get me shot :P)

One issue with being *too* pointy is that these things often end up wrongly positioned, and we can't actually be sure about the size of what the notification is pointing at anyway. (All it gets is an X and Y coordinate). If it is wrong but appears Completely Convinced that it's right, people get confused. The hint that "this is hereabouts in the notification area" (eg: directing one's eyes to the general area to help him along) could be a bit more powerful, with some work.

True about them not always pointing to the right thing.

To go slightly off topic I think the notification area is abused somewhat these days, I like to keep it as an area for notifications, ie I use cgmail but the icon only pops up if I have mail rather than just sits there. 

Pidgin doesn't need to sit there the whole time it is running especially not since it's also part of the shutdown applet now too

Banshee, Rhythmbox (etc) and most torrent clients I have used are guilty of this too, they're not actually notifying you of anything.

Wow, sorry about that rant.

I like what you're doing with the notification stuff though, you're right that to the casual observer it isn't immediately obvious which notifications respond to which programs.

---

### Post by Jay_Bee on 2009-02-24
I looked at Mark's mockup again and I saw that sliding notifications don't fade, they just scale, maybe you could try that out.

---

### Post by TechWizrd on 2009-03-07
This works well (I like eyecandy :) ). I haven't noticed any bugs or usability regressions yet, but I still can't really tell where they came from. 

I second Jay_Bee's scaling suggestion. I liked the mockup.

EDIT: After using it for an hour, I am really liking these location-aware notifications. They're really nice. Thanks.

---

### Post by funkyhat on 2009-03-07
I'd like it if they did that magic lamp thing which is blocked from Compiz by default because of worries of patent issues from Apple... Slick and informative :-)

---

### Post by jmmL on 2009-03-07
I'd second funkyhat. Even just minimising to the icon would be quite cool I reckon. Although, I will admit that I haven't actually tried it; I've just watched the screencast.

---

### Post by funkyhat on 2009-03-07
Yeah minimise would be almost as good :-)
I think magic lamp would be better because as the window shrinks at the top it will be pointing directly at the icon the notification relates to, the minimise action doesn't make it quite so clear where it's pointing.

---

### Post by Mr. Picklesworth on 2009-03-07
I'll experiment with scaling effects soon. Just wasted a bunch of time trying to draw arrows, and tonight goes to Empire Total War, so tomorrow afternoon probably :P
If anyone else wants to give it a try (the project has REALLY easy to follow source code) feel free to. I won't complain!

Quick test case:
Make sure you experiment with position-hinting bubbles both by paying attention to them and trying to ignore them. One of the great things with notify-osd is being really quiet, and too significant an animation would draw a lot of attention, harming that effect.

---

### Post by deathsshadow77 on 2009-03-07
yeah, having some effect like "vacuum" would be awesome and would work nicely.

---

### Post by zekopeko on 2009-03-08
just don't turn this into compizconfig nightmare ;)

---

