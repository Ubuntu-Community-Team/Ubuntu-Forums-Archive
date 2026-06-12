---
title: "Icons in systray"
date: 2009-09-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by !nkubus on 2009-09-26
I really love the new icons in the systray. But when an application, that is not in the default systray it looks odd to have it in color. Do you think an update to the theme will be made to make every built in software with a grey icon?

---

### Post by Keyper7 on 2009-09-26
Impossible. Some applications, like aMule, hardcode their tray icons and do not allow customization. 

The ones in the repositories could be patched, but there's not much to do about third-party ones like Skype.

---

### Post by gexi on 2009-09-26
this won’t always be possible, as far as i know. reason is: some of the applications hardcode their sys-tray-icons, so changing them is not possible without changing the application itself…

nevertheless, i’d also like to see a more consistent look in the tray, especially given those gorgeous new monochrome icons :)

---

### Post by Sophont on 2009-09-26
Am I the only one who dislikes the new monochrome icons?

I want the colors back in my battery and NM icons.

There seems to be a weird assumption going around that those panel icons should be close to unnoticable. That sounds weird to me as that defeats the purpose of having them there in the first place.

Those icons are the only reason I keep a panel on the screen. Gnome-Do Docky provides a very nice app lancher. So I only keep a panel there because I want have stuff like CPU/GPU temps, NM status, Battery level etc visible at all times.

---

### Post by tretle on 2009-09-26
For karmic the tray icons being concentrated on are system ones. Any third party apps will be further investigated in lucid. 
In my personal opinion the notification area should be used for system icons only so I am not too pushed about this.

---

### Post by tretle on 2009-09-26
> **Sophont said:**
> Am I the only one who dislikes the new monochrome icons?

I want the colors back in my battery and NM icons.

There seems to be a weird assumption going around that those panel icons should be close to unnoticable. That sounds weird to me as that defeats the purpose of having them there in the first place.

Those icons are the only reason I keep a panel on the screen. Gnome-Do Docky provides a very nice app lancher. So I only keep a panel there because I want have stuff like CPU/GPU temps, NM status, Battery level etc visible at all times.

The viability is being worked on at the moment. And I am sure your not the only one that does not like them but the majority of reviews and remarks about them both on the forums and on the blogosphere have been positive.

Some of the panel icons in my view should be as unnoticeable as possible unless it is trying to grab your attention(a new im for example), atm they are being worked on to better grab your attention when necessary by making them lighter or darker depending on whether the panel is light or dark but its complex as two themes need to be made, one for light panels and one for dark.

And if you don't like them the old human set of icons remains installed so you can switch back at any time.

---

### Post by Keyper7 on 2009-09-26
> **tretle said:**
> In my personal opinion the notification area should be used for system icons only so I am not too pushed about this.

I agree, but some applications like Rhythmbox and Skype do not give you a choice.

---

### Post by tretle on 2009-09-26
I know and thats bad as the notification area was never meant to be used for that purpose.

Another issue is that metacity itself does not currently allow application specific options which means that if you have say rhythmbox open and right click on the task on the bottom panel you wont get any option to play/pause etc. You only have generic options.
The guy who maintains metacity brainstormed publicly about this issue and asked the community what they thought should be done for mutter and it looks like we will have app specific options soon which in my view completely removes any argument for having applications show up in the notification area.

---

### Post by QwUo173Hy on 2009-09-26
I'm really happy with the change. I found the colors very distracting. For rhythmbox, the icon is located at /usr/share/pixmaps/rhythmbox-small.xpm

If you really want you can edit this in gimp, as I am going to do. I also agree with tretle that applications shouldn't be using this area at all. This release has really impressed me.

---

### Post by Regenweald on 2009-09-26
I love the new look, very crisp and professional.

---

### Post by Merk42 on 2009-09-26
> **gexi said:**
> this won’t always be possible, as far as i know. reason is: some of the applications hardcode their sys-tray-icons, so changing them is not possible without changing the application itself…

nevertheless, i’d also like to see a more consistent look in the tray, especially given those gorgeous new monochrome icons :)

I'm sure those applications will be encouraged to either not hardcode their icons or hardcode them grey.  I'm sure Skype for example has already had the issue brought to them as Windows 7 has done the same thing (albeit white).

---

### Post by Keyper7 on 2009-09-26
> **jarlath said:**
> I'm really happy with the change. I found the colors very distracting. For rhythmbox, the icon is located at /usr/share/pixmaps/rhythmbox-small.xpm

If you really want you can edit this in gimp, as I am going to do. I also agree with tretle that applications shouldn't be using this area at all. This release has really impressed me.

Yeah, for rhythmbox is not difficult.

But I said it once and I'll say it again:

DAMN YOU, SKYPE, AND YOUR UGLY HARDCODED ICONS
(even worse in 2.1, where besides ugly they are huge)

---

### Post by Luffield on 2009-09-26
Do you guys think it would be possible to force the icons in the notification area to be grouped by their color (i.e grey and coloured)? Right now my notification area looks like this:

grey grey grey PURPLE grey

I agree that it would probably be impossible to get all icons to conform with the new grey theme, but even re-ordering them could look much better IMHO.

---

### Post by Darkshade on 2009-09-26
There should be an option to hide chosen icons with a default setup to hide everything except the ones using monochrome icons.

---

### Post by gexi on 2009-09-26
> **Darkshade said:**
> There should be an option to hide chosen icons with a default setup to hide everything except the ones using monochrome icons.

+

sounds great!

---

### Post by psyke83 on 2009-09-26
It would seem like a better idea to patch the notification area to desaturate the icons - this would fix even the worst offenders such as Skype. However, it's not clear if all icons would look acceptable when shaded to grey.

---

### Post by blakamin on 2009-09-26
The one that annoys me the most is empathy with its big green circle (or crappy triangle).

---

### Post by yzarc on 2009-09-26
I think we could do better by adding some outline and making the icons less square more rounded or smooth. it's possible to be discret without going monochromatic.

---

### Post by !nkubus on 2009-09-27
> **blakamin said:**
> The one that annoys me the most is empathy with its big green circle (or crappy triangle).

+1

this is the main reason for starting this thread :)

---

### Post by cyberkilla on 2009-09-27
The tray icons have always been an annoyance of mine.

You can't rely on every application behaving; the best workaround is to allow users to hide certain icons.

KDE supports this. Windows supports this. I don't know about OS X.

It can't be that hard to achieve. Personally, I don't care too much about the colour of the icons (although monochrome is very neat/neutral).

The other thing that really needs to be addressed is the size of tray icons. If you have your panel any larger than the default 24px, strange things happen.

Some icons scale up nicely. Some scale up and become aliased. Some don't scale at all, remaining the original size. My personal preference is for them not to scale at all. They should remain the same size, regardless of the width of my gnome-panel.

Vista puts them onto multiple rows. It is a useful feature that really should be looked into by GNOME.

Lastly, I must point out that the tray area is annoying even at the default panel size, because many of the icons (whilst being the same resolution) do not APPEAR to be the same resolution. It's a battle in vain:P

My solution has been to use the Humanity and set any application which uses tray icons to, well, not.

GaJim lets you do it via gconf. Pidgin has a preference available to set it. Banshee implements it via a plug-in, so you just have to disable it.

Those are the only tray applications I still use. I stopped using Tomboy notes because it wouldn't let me remove the icon. Instead, I use something called Zim, which is quite brilliant for note-taking.

---

### Post by Amaranth on 2009-09-27
I kind of like the idea that the ones that are there by default are monochromatic and the ones added later are full color. Makes the application ones very distinct so they aren't lost in a sea of color.

Also, empathy shouldn't even have a notification area icon, it uses the indicator applet.

---

### Post by Arlanthir on 2009-09-27
Can anyone post a screenshot for those of us who bricked their laptops with a stupid official BIOS update, please? :P

---

### Post by Amaranth on 2009-09-27
[http://www.realistanew.com/random/desktop20090925.png](http://www.realistanew.com/random/desktop20090925.png)

---

### Post by taavikko on 2009-09-27
> **Amaranth said:**
> I kind of like the idea that the ones that are there by default are monochromatic and the ones added later are full color. Makes the application ones very distinct so they aren't lost in a sea of color.


+1 

But is there any plans to make BT icon monochromatic?
It should be one of those icons, IMHO.

---

### Post by Amaranth on 2009-09-27
I agree but currently it uses the same icon for the notification area as the menus and such so I'm not sure what they'll do there.

---

### Post by Arlanthir on 2009-09-27
> **Amaranth said:**
> [http://www.realistanew.com/random/desktop20090925.png](http://www.realistanew.com/random/desktop20090925.png)

Thank you :)

It gives a little windows 7 feel to it, but a bit less polished in my opinion... They're so gray it's hard to see (at least on that dark panel)!

I like them messing with the tray, though. I liked what they did with the notifications, so I'm keeping an open mind ;)

---

### Post by taavikko on 2009-09-27
> **Amaranth said:**
> I agree but currently it uses the same icon for the notification area as the menus and such so I'm not sure what they'll do there.

Should this be filed as a bug?
Since if you have BT devices and enabled, icon will automatically be presented in notification area.
They could remove the menu entry then, from excess clutter :)

---

### Post by piotrekp on 2009-09-27
Amaranth, I "borrowed" your part of panel for short experiment with GIMP and made a Bluetooth icon. Feel free to comment.

---

### Post by gexi on 2009-09-27
> **piotrekp said:**
> Amaranth, I "borrowed" your part of panel for short experiment with GIMP and made a Bluetooth icon. Feel free to comment.

i like :)

---

### Post by VMC on 2009-09-27
> **cyberkilla said:**
> ...I stopped using Tomboy notes because it wouldn't let me remove the icon. Instead, I use something called Zim, which is quite brilliant for note-taking.Right-cleck quit. Removes the icon, but I'm guessing you mean they won't allow you to change the icon. 

You stopped using Tomboy just because of the icon!? 

I use Tomboy a lot, although I'll have to check out Zim now that you mentioned it. I never heard of it before.

---

### Post by ELD on 2009-09-27
From what i can see it looks great in a light panel and rather bad in a dark panel, we need the opposite in gamma for the darker panels?

---

### Post by QwUo173Hy on 2009-09-27
Compiz currently has the ability to change the colors of a window or the entire screen (negative, sepia etc.). If such a filter existed to desaturate the icons in the system tray, third party / hard-coded apps would be less of a problem.

---

### Post by ELD on 2009-09-27
If that was a reply to what i posted, i simply ment a set of icons with the opposite so we can switch if we have darker panels. I don't want to have to have compiz to use a different colour set.

---

### Post by Copernicus1234 on 2009-09-27
I love the new look too. Great work!

---

### Post by Copernicus1234 on 2009-09-27
> **Arlanthir said:**
> Thank you :)

It gives a little windows 7 feel to it, but a bit less polished in my opinion... They're so gray it's hard to see (at least on that dark panel)!

I like them messing with the tray, though. I liked what they did with the notifications, so I'm keeping an open mind ;)

That picture doesnt quite do them justice. They looked far better for me with the default karmic theme after installation. Unfortunately karmic only worked once in virtual box. After installing guest additions, it no longer boots. I hope there are updates to virtual box soon.

---

### Post by NCLI on 2009-09-27
> **Chauncellor said:**
> Problem! *I* don't use the indicator applet.
Then you're not using the default setup, and it's(technically) not something for Canonical to worry about ;)

---

### Post by Merk42 on 2009-09-27
> **Chauncellor said:**
> You're right. Well, then, why don't we just start making things not work for people that don't want to have two panels? How dare they not like the default setup!

Look, I don't like the two panel thing either but that's a pretty silly complaint.

You could put the indicator applet on the one panel you have.

Secondly, you really can't blame Canoncial/Ubuntu when something doesn't work that you remove.

That's like if I removed the window list and then complained I couldn't see where I minimized windows.


I know I know. You're going to respond with something like "well I've always used it there to change status/etc". I'm guessing Ubuntu wants to go in the direction of Windows 7 (and maybe OSX not as familiar with them) where that area is only for showing status and not something that is directly interacted with.

---

### Post by MilesRdz on 2009-09-27
> **jarlath said:**
> Compiz currently has the ability to change the colors of a window or the entire screen (negative, sepia etc.). If such a filter existed to desaturate the icons in the system tray, third party / hard-coded apps would be less of a problem.

Not all people have/want compiz enabled. We need something that works either way. Compositing enabled or not.

---

### Post by Merk42 on 2009-09-27
> **MilesRdz said:**
> Not all people have/want compiz enabled. We need something that works either way. Compositing enabled or not.

I figured jarlath's point was that it would be some way of a patch.

If a program refuses to change its hardcoded icon, what really can Ubuntu do about it?

---

### Post by QwUo173Hy on 2009-09-27
> **ELD said:**
> If that was a reply to what i posted, i simply ment a set of icons with the opposite so we can switch if we have darker panels. I don't want to have to have compiz to use a different colour set.

No, I was just brainstorming :)

MilesRdz - that's true. We don't want to limit ourselves to compiz'd machines.

---

### Post by Merk42 on 2009-09-27
> **Chauncellor said:**
> My point was that if they're going to use a half-baked applet, they might as well make everything work and conform in one go. Jaunty's indicator applet was the poorest excuse of change for the sake of it, and I'm not liking Karmic's either.
What is half-baked about it? Also, I'm sure if they could just snap their fingers and have it all conform in one go they would. However, it's up to the makers of the individual programs to do it too, something Ubuntu has no control over.

> **Chauncellor said:**
> I have no need of a dropdown notification bar. As you can see, the notification area is as "cluttered" as I ever have it. All I want is basic functionality and customization, that's all.
Well you do use Indicator Applet *Session*, so exactly what functionality is half-baked and lost without Indicator Applet?

> **Chauncellor said:**
> 
Looks like Linus was right, and I'll be using KDE soon enough.
Just because Linus can program a kernel, doesn't mean he knows UI.  Hell he recently said Linux is bloated, guess you should just stop using it altogether.

And using KDE instead? Who's your beef with Canonical or GNOME?
For better or worse GNOME doesn't seem to care about Canonical's ideas when it comes to GNOME Shell.

---

### Post by Keyper7 on 2009-09-27
> **Chauncellor said:**
> My point was that if they're going to use a half-baked applet, they might as well make everything work and conform in one go. Jaunty's indicator applet was the poorest excuse of change for the sake of it, and I'm not liking Karmic's either.

Don't use it, then. Removing it from the panel doesn't break anything as far as I know.

---

### Post by cyberkilla on 2009-09-27
> **VMC said:**
> Right-cleck quit. Removes the icon, but I'm guessing you mean they won't allow you to change the icon. 

You stopped using Tomboy just because of the icon!? 

I use Tomboy a lot, although I'll have to check out Zim now that you mentioned it. I never heard of it before.

Thanks, but I know how to quit Tomboy. I wanted to remove the tray icon, so I can simply minimise the main window to the dock:)

Zim is rather good. It is a hybrid of a wiki and a notepad. You can have to-do lists and notes, linked together.

It's hard to explain. The interface is very simple.

[http://zim-wiki.org/](http://zim-wiki.org/)

---

### Post by Keyper7 on 2009-09-27
> **Chauncellor said:**
> But that was the entire point of my original post. I was rebuked for wanting to remove it in the first place. I'd be fine with it being there as long as I can get rid of it.

But you *can* get rid of it. Like I said, it won't break anything. If you are referring to this post,

> **NCLI said:**
> Then you're not using the default setup, and it's(technically) not something for Canonical to worry about ;)

NCLI simply meant that Canonical cannot acount for an optimal performance of every possible use case, this is impossible. But they don't *forbid* you from removing the indicator-applet, nothing breaks if you do. Yes, it's true that the Empathy tray icon is not consistent with Humanity, but you can change it manually (I think).

> **Chauncellor said:**
> @Merk: As of Jaunty, the indicator applet works for basically two programs: Pidgin and Evolution. All it is right now is a substitute for an already working mechanic: a drop-down notification area, if you will.

Empathy and Gwibber both work with it as well.

---

### Post by MilesRdz on 2009-09-27
> **Merk42 said:**
> I figured jarlath's point was that it would be some way of a patch.

If a program refuses to change its hardcoded icon, what really can Ubuntu do about it?
In all honesty I think they should only really be responsible for application that are already installed. For example, if you install a new program on Windows and the systray icon looks like s**t; is it MS's job to make sure it looks good? No. It pretty much is MS's job to have the applications it comes with to look good. You don't see the audio icon looking like complete garbage. With Humanity icon set they pretty much fixed that.

---

### Post by zekopeko on 2009-09-27
> **MilesRdz said:**
> In all honesty I think they should only really be responsible for application that are already installed. For example, if you install a new program on Windows and the systray icon looks like s**t; is it MS's job to make sure it looks good? No. It pretty much is MS's job to have the applications it comes with to look good. You don't see the audio icon looking like complete garbage. With Humanity icon set they pretty much fixed that.

Agreed. They patched applications that come in the default install or are part of main/repo.

---

### Post by hblaw on 2009-09-27
> **MilesRdz said:**
> With Humanity icon set they pretty much fixed that.

I am not sure whether the icon set is the only issue. I do not think the current setup is good enough. I am wondering why the following two points are so difficult to achieve:

1. Leave SOME MARGIN between icons and the panel borders. Individual icons can be poorly designed; but if there is some margin between the borders and between the icons, they look better.

2. Ability to hide icons. As simple as windows xp does. At least we can avoid seeing trash for most of the time, even if we need to see them sometimes (like for 10 seconds if you want to check aMule downloading progress). Making people see the ugly amule icon all the time is equivalent to torturing (for anyone with any aesthetic taste).

---

### Post by joey-elijah on 2009-09-27
i spent a large chunk of this evening editing application icons to grey. Then decided it just looked weird and gave up.

Love the BT icon someone posted a while back - i do hope there's a nice svg/png being shared of it cos the colour is spot on!

---

### Post by Eestlane on 2009-09-27
I think it would be a good idea that if there's unread mail or new im messages, the corresponding icon will have some colour for attention.
(Let's say your going away for a 30minute khm sht, and when you come back you see the e-mail icon is green - something libnotifyosd wouldn't work for).

---

### Post by Mr. Picklesworth on 2009-09-27
> **hblaw said:**
> 1. Leave SOME MARGIN between icons and the panel borders. Individual icons can be poorly designed; but if there is some margin between the borders and between the icons, they look better.For what it's worth, that is finally being done in GNOME Shell.

> 2. Ability to hide icons. As simple as windows xp does. At least we can avoid seeing trash for most of the time, even if we need to see them sometimes (like for 10 seconds if you want to check aMule downloading progress). Making people see the ugly amule icon all the time is equivalent to torturing (for anyone with any aesthetic taste).No, no... a million times, NO! Aaaagh!
:(

---

### Post by Cenotaph on 2009-09-27
> No, no... a million times, NO! Aaaagh!

Why not? It's optional, it doens't hurt anyone that would like to see all the icons at all time.

---

### Post by Amaranth on 2009-09-27
If hiding is added it will only legitimize the abuse of the notification area.

---

### Post by hblaw on 2009-09-27
> **Amaranth said:**
> If hiding is added it will only legitimize the abuse of the notification area.

Lets ditch American Constitution for sure because it gives so much freedom to ppl.

Edit: Oh, I forgot, let's ditch linux as well. And no need for customization; let's applause for Microsoft. :)

---

### Post by Merk42 on 2009-09-27
> **hblaw said:**
> Lets ditch American Constitution for sure because it gives so much freedom to ppl.

Edit: Oh, I forgot, let's ditch linux as well. And no need for customization; let's applause for Microsoft. :)

You.. you're a troll right? You can't possibly think that makes any sense.

Heck while we're at it let's just pull Godwin and say Canonical is a bunch of Nazis.

---

### Post by hblaw on 2009-09-28
> **Merk42 said:**
> You.. you're a troll right? You can't possibly think that makes any sense.

Heck while we're at it let's just pull Godwin and say Canonical is a bunch of Nazis.

Yes I am exaggerating.

I am just responding to the comment that BECAUSE people will abuse the notification area if we can hide the icons, THEREFORE we should not develop the feature of hiding icons. (Is there any other easier alternative to solve the problem of program-hard-coded ugly icons?)

So far, I feel that the BAD things in linux generally come from "monopolizing" developers. E.g. the notification area. E.g. pulseaudio (devs think that there are cool features, and FORCES people to use that while it is still very buggy).

Something are good for somebody. Nothing is good for all. That's why we need "freedom" and that's why Linux remains attractive. Every time some "WE" deem anything better for everyone (as in "we think it is the future of technology") and impose it on the community, such thing fails.

See the debate in this forum - how many times people say "this is better for you" and "YOU" should change rather than the SOFTWARE should change. I probably have done this multiple times, but when the debate has settled, people/community should realize that when it is possible, the best option is to provide choices rather than eliminate them.

kaka

---

### Post by MilesRdz on 2009-09-28
> **hblaw said:**
> I am not sure whether the icon set is the only issue. I do not think the current setup is good enough. I am wondering why the following two points are so difficult to achieve:

1. Leave SOME MARGIN between icons and the panel borders. Individual icons can be poorly designed; but if there is some margin between the borders and between the icons, they look better.

2. Ability to hide icons. As simple as windows xp does. At least we can avoid seeing trash for most of the time, even if we need to see them sometimes (like for 10 seconds if you want to check aMule downloading progress). Making people see the ugly amule icon all the time is equivalent to torturing (for anyone with any aesthetic taste).

The folks over at the Fedora project do that with the icons (the margins). Something I think they (Ubuntu devs) should implement into Ubuntu.

---

### Post by walmis on 2009-09-28
Here's a grey bluetooth icon i edited for blueman.

---

### Post by OliW on 2009-09-28
I don't see any reason why the Notification Area couldn't do graphical transformations on the icons itself, turning an otherwise unchangable icon into a monochrome version.

Might seem a little ugly (it is) but it would give the tray some consistency.

---

### Post by Keyper7 on 2009-09-28
> **OliW said:**
> I don't see any reason why the Notification Area couldn't do graphical transformations on the icons itself, turning an otherwise unchangable icon into a monochrome version.

Here's a reason: people who are not using Humanity.

---

### Post by cyberkilla on 2009-09-28
> **Amaranth said:**
> If hiding is added it will only legitimize the abuse of the notification area.

They're already committing heinous acts of visual torture. At least we would be able to hide them from our delicate eyes.

---

### Post by Wise Ferret on 2009-09-28
I really wish that humanity, being so beautiful, will give us a version that looks well on dark themes. I use a humble shiki variant and have a lot of difficulties trying to decipher the systray icons. It is very hard for me to get volume or wireless signal information like that.

---

### Post by joey-elijah on 2009-09-28
> **OliW said:**
> I don't see any reason why the Notification Area couldn't do graphical transformations on the icons itself, turning an otherwise unchangable icon into a monochrome version.

Might seem a little ugly (it is) but it would give the tray some consistency.

It's not quite the same, but on Ubuntu Netbook Remix any open applications that aren't "focused" have their icons "greyed out" which matches the notification tray icons beautifully.

---

### Post by 3rdalbum on 2009-09-28
> **hblaw said:**
> Lets ditch American Constitution for sure because it gives so much freedom to ppl.

If you don't like it, you're free to create your own patchset or fork to implement that functionality. But if the Ubuntu developers want to limit some options in the interests of excluding one of the most annoying things about Windows, then I'm all for it.

In fact I'd probably go the other direction and ask for a way to create a blocklist for notification area icons, because Opera's notification area icon is utterly pointless.

---

### Post by pelle.k on 2009-09-28
> **hblaw said:**
> 1. Leave SOME MARGIN between icons and the panel borders. Individual icons can be poorly designed; but if there is some margin between the borders and between the icons, they look better.


> **MilesRdz said:**
> The folks over at the Fedora project do that with the icons (the margins). Something I think they (Ubuntu devs) should implement into Ubuntu.

The notification area having no padding (spacing) at all, and applets having weird spacing is something that has irritated me since way back. That goes for launchers on the panel as well.
Ever tried making the gnome panel use another size than 24 pixels? say 34 pixels or what have you? Looks ridiculous.
I think this guy has some great ideas (his mockup attached); [http://www.bomahy.nl/hylke/blog/ugly-notification-area-in-gnome/](http://www.bomahy.nl/hylke/blog/ugly-notification-area-in-gnome/)

---

### Post by zacbarton on 2009-09-29
Here's a custom_format for the clock that tries to blend with the new notification icons. The panel in the screenshot is 28px.

---

### Post by !nkubus on 2009-09-29
Wow awesome clock format thanks :)

---

### Post by joey-elijah on 2009-09-29
> **zacbarton said:**
> Here's a custom_format for the clock that tries to blend with the new notification icons. The panel in the screenshot is 28px.

That is gorgeous! Never knew you could customize the tray clock... so forgive the n0ob question but how do you use this?

edit: I now know how :)

Lanuch gconf-editor 
Go to /apps/panel/applets/clock_screen0/prefs 
Right-Click on “format” and select “Edit Key” and set to “custom” 
Right-Click on “custom_format” and select “Edit Key” and paste in the code from attached txt.

---

### Post by Mr. Picklesworth on 2009-09-29
> **zacbarton said:**
> Here's a custom_format for the clock that tries to blend with the new notification icons. The panel in the screenshot is 28px.

!!
Thank you. That is delicious :)

Now if only that padding above the clock was shrunken a bit so this could fit on a 24px panel...

---

### Post by Eestlane on 2009-09-29
> **Merk42 said:**
> I figured jarlath's point was that it would be some way of a patch.

If a program refuses to change its hardcoded icon, what really can Ubuntu do about it?

Adding black and white effect could be possible theoretically.

---

### Post by maKA28 on 2009-09-29
> **zacbarton said:**
> Here's a custom_format for the clock that tries to blend with the new notification icons. The panel in the screenshot is 28px.

Nice!! Now if only this could be made default!

---

### Post by Kazade on 2009-09-29
> **maKA28 said:**
> Nice!! Now if only this could be made default!

+1 !! Perhaps someone could post this to the ayatana list?

---

### Post by Arlanthir on 2009-09-29
Well, looks good but it only works on larger panels :S

---

### Post by pelle.k on 2009-09-29
> The panel in the screenshot is 28px.
Quite nice! That downside is that at 28 pixels, when using the humanity theme, the networkmanager icons grows, while the volume icon, battery icon, and bluetooth icon does not. Also, at 28 pixels the networkmanager icon is scaled (if you look closely it's blurry) from a "native" size. Too bad.

---

### Post by cyberkilla on 2009-09-29
> **pelle.k said:**
> Quite nice! That downside is that at 28 pixels, when using the humanity theme, the networkmanager icons grows, while the volume icon, battery icon, and bluetooth icon does not. Also, at 28 pixels the networkmanager icon is scaled (if you look closely it's blurry) from a "native" size. Too bad.

If it wasn't for the blur, I was quite prepared to use that panel size. Very nice clock layout.

---

### Post by zacbarton on 2009-09-29
It's a shame the networkmanager icon scales and looks blury on a 28px panel :-(

Here's a custom_format for a 24px panel. It looks a little small for my taste but maybe others will like it.

---

### Post by pelle.k on 2009-09-29
> **zacbarton said:**
> It's a shame the networkmanager icon scales and looks blury on a 28px panel :-(
I wonder if there's a bug reported about it. I've reported several bugs on "polish" issues such as this - they mostly go unnoticed though.

> **zacbarton said:**
> 
Here's a custom_format for a 24px panel. It looks a little small for my taste but maybe others will like it.
Good job, however, i noticed that the placement on the panel is somewhat broken with this modification.

---

### Post by zacbarton on 2009-09-29
Yea there seems to be some top padding that I couldnt overcome.

---

### Post by zacbarton on 2009-09-30
I reported a bug for the blurry nm-applet icon - [https://bugs.launchpad.net/humanity/+bug/439172](https://bugs.launchpad.net/humanity/+bug/439172)

---

### Post by oomingmak on 2009-09-30
When I looked at the screenshot earlier in this thread which showed the grey notification icons, I thought they looked 'non-functioning'.

'Greying out' is a standard way of showing that something is not available, so to me it just makes the icons look broken.

---

### Post by Framli on 2009-09-30
Sometimes, greying things out, just means driving them -IMHO- toward the way of discretion and elegance.

---

### Post by coffeecat on 2009-10-14
Sorry to bump this thread after 1 week, but...

> **oomingmak said:**
> When I looked at the screenshot earlier in this thread which showed the grey notification icons, I thought they looked 'non-functioning'.

'Greying out' is a standard way of showing that something is not available, so to me it just makes the icons look broken.

Agreed 101%. I've been gritting my teeth for the last couple of weeks or so hoping that an update would do something about these "broken" icons (I'd missed this thread), and wasted an hour or so this morning trying to fix something I thought that perhaps I'd broken, and then I found this thread at last. Honestly, to me these icons look like something that belongs on a mid-90s Apple screen (or even - shock, horror! - Windows 95 :shock: :wink:) - it's a real retro look, but without any finesse. Imho.

Yes, I know I can install a 3rd party icon set but that doesn't fix the Network Manager icon or any of the others that are hard-coded, so they stick out like extremely sore thumbs.

This is one unhappy bunny. :(

---

### Post by cyberkilla on 2009-10-14
> **coffeecat said:**
> Yes, I know I can install a 3rd party icon set but that doesn't fix the Network Manager icon or any of the others that are hard-coded, so they stick out like extremely sore thumbs.

No they aren't hard coded. Any icon theme can replace them if the author cares to.

---

### Post by pelle.k on 2009-10-14
> Yes, I know I can install a 3rd party icon set but that doesn't fix the Network Manager icon or any of the others that are hard-coded, so they stick out like extremely sore thumbs.
cyberkilla is actually right, you may replace them using an icon theme. But you may have to restart the "applets" to change icon(s) on the panel.

---

### Post by coffeecat on 2009-10-14
> **pelle.k said:**
> But you may have to restart the "applets" to change icon(s) on the panel.

Ah yes, that does work with the NM applet icon. Thanks. When I was fiddling about with other icon sets I was sometimes getting the faded grey icon and sometimes the sort of icon I prefer. I was puzzled by this but that explains it.

However, this rather distracts from the main point I was making. I respect what seems to be the majority view that likes these washed-out 2-dimensional ghostly grey things. I don't, and was merely stating my view, but it's not big issue. I can live with it - albeit with gritted teeth :wink: - because otherwise I rather like the Karmic Human icon set.

---

### Post by pelle.k on 2009-10-14
> I can live with it - albeit with gritted teeth  - because otherwise I rather like the Karmic Human icon set.
I feel your pain man. I happen to think just the same thing. But i'm rather disappointed with the actual shape and size of the icons.
I guess they can't make everyone happy :/

---

### Post by cyberkilla on 2009-10-14
> **pelle.k said:**
> I feel your pain man. I happen to think just the same thing. But i'm rather disappointed with the actual shape and size of the icons.
I guess they can't make everyone happy :/

Now that's something I can agree with. I don't like the size of the tray icons. However, that isn't entirely a fault of the icon theme. 

The notification area applet needs bit of a clean up, it seems. When I increase the size of my panel to make the window list occupy two rows, I don't expect some the tray icons to balloon up to 40px+.

It's a shame I can't edit some obscure config file and force them all to stay the same size.

---

