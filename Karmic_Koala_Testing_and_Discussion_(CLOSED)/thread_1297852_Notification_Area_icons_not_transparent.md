---
title: "Notification Area icons not transparent"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cyberkilla on 2009-10-22
Has anybody noticed the following behaviour in several applications..

With gnome-panel set to "transparent" or "image background", many notification icons have a solid background (the colour of the panel).

I have seen this with GaJim, Pidgin, Banshee and a few others.

It discourages the customisation of gnome-panel because it looks odd with anything but the default preferences. Take a look at this screenshot:)

The first panel in the screenshot is the Dust theme's panel background (it comes as a separate image that can be applied to the panel).

The second panel is set to have "system" default. As you can see, the icons look okay when there is no transparency or image setting on the panel. The moment you change that, you notice that the icons are no longer transparent and have taken on the colour of the panel itself.

This is a regression.

**Update:** This bug report appears to address it: [https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/403135](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/403135)

---

### Post by simmeson on 2009-10-24
Can confirm this. Works fine on all apps I use except Pidgin, thought it was just me at first.

---

### Post by NRDNick on 2009-10-24
I've been trying out a lot of different themes and I've noticed this behaviour with some of the themes I have tried out. I just tested it out and confirmed that I get the same behaviour using the clear-looks controls in my customized theme The solid color even appeared behind my Applications/Places/System menu. 

Not sure what's causing it, but I've worked around it by creating a customized theme. From there you can pick and choose options from the installed themes, or download the some new ones. 

I recommend grabbing the community-themes from the repos as well. I currently use the Hanso theme's Controls and Window Border from the community package and do not see the issues you are experiencing

---

### Post by cyberkilla on 2009-10-24
> **NRDNick said:**
> I've been trying out a lot of different themes and I've noticed this behaviour with some of the themes I have tried out. I just tested it out and confirmed that I get the same behaviour using the clear-looks controls in my customized theme The solid color even appeared behind my Applications/Places/System menu. 

Not sure what's causing it, but I've worked around it by creating a customized theme. From there you can pick and choose options from the installed themes, or download the some new ones. 

I recommend grabbing the community-themes from the repos as well. I currently use the Hanso theme's Controls and Window Border from the community package and do not see the issues you are experiencing

I use the community themes. I use Dust. It happens for me regardless of the theme. It is a problem with the notification icons, it seems.

---

### Post by Aero-Z on 2009-10-24
It sounds more like "working as intended" to me.

---

### Post by inportb on 2009-10-24
Well, Pidgin is the last icon on my KDE desktop that shows the non-transparent background. I figured it's something to do with the notification API.

---

### Post by cyberkilla on 2009-10-24
> **Aero-Z said:**
> It sounds more like "working as intended" to me.

It worked fine in Jaunty. This is a regression. Some icons are transparent when you use "transparent" or "image background" on the panel. Some of them aren't.

The tray icons that fail to adopt the correct background are misbehaving. Don't just post something like that without elaborating. What exactly is working as intended? Did you see my screenshot?

Edit: All I know is, several tray icons have suddenly lost their transparency, as a result of karmic updates. Unless they all decided to change their code together, it suggests that something they depend on has changed its behaviour.

Could be the GTK toolkit, or something different with gnome-panel's notification area applet. Something has changed though.

Update: From what I've seen, the issue has to be fixed in each application, though there was presumably a change to GTK which triggered this. I wish I could find more reliably information about this bug.

---

