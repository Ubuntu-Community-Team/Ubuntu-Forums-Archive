---
title: "Battery Status Applet removed?"
date: 2009-09-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by locovaca on 2009-09-10
From the looks of [this thread]("http://www.******************/ubuntu-desktop/345346-trimming-down-gnome-applets-removing-hal-dependency.html") the long standing battery status applet is being removed in Karmic.  While I disagree with the decision, what valid replacement is there for it?  I want an applet which calculates and displays the remaining battery life in hours:minutes (ala OS X), which the default battery icon does not provide.  

Can someone point me to a Karmic applet which will provide this functionality?

---

### Post by Giwex on 2009-09-11
> **locovaca said:**
> From the looks of [this thread]("http://www.******************/ubuntu-desktop/345346-trimming-down-gnome-applets-removing-hal-dependency.html") the long standing battery status applet is being removed in Karmic.  While I disagree with the decision, what valid replacement is there for it?  I want an applet which calculates and displays the remaining battery life in hours:minutes (ala OS X), which the default battery icon does not provide.  

Can someone point me to a Karmic applet which will provide this functionality?

Link not working. Can you please fix it? 
On my system updated 1 hour ago the battery status indicator is still present.

---

### Post by mattduckman on 2009-09-11
here's a link: [http://tinyurl.com/n7flab](http://tinyurl.com/n7flab)

gnome-power-manager provides me estimates in hours and mintues, so I'm not sure why you're saying it doesn't. I've never used the battstatus (and now I can't lol) so I can't really say how it compares though.

---

### Post by steeleyuk on 2009-09-11
This applet was marked as deprecated for quite a while along with the old volume control applet. As has been said, gnome-power-manager is configured to display an icon in the notification area displaying the power/battery status.

---

### Post by locovaca on 2009-09-11
> **steeleyuk said:**
> This applet was marked as deprecated for quite a while along with the old volume control applet. As has been said, gnome-power-manager is configured to display an icon in the notification area displaying the power/battery status.

I get that, however, I want it to display (without user interaction) the actual calculated time remaining, like OS X.  I cannot find a way to configure the remaining applet to do that.

Remaining Applet: [http://projects.gnome.org/gnome-power-manager/gpm.html](http://projects.gnome.org/gnome-power-manager/gpm.html)

Original Applet (screenshot is percentage, I had configured mine for time): [IMG]http://www.thinkwiki.org/images/8/88/Bildschirmfoto-BatteryApplet.png[/IMG]

So I guess there is nothing in Karmic to display the status like OS X then, correct?  [IMG]http://farm3.static.flickr.com/2030/2397099409_2a255a7553.jpg?v=0[/IMG]

---

### Post by cyberkilla on 2009-09-12
The entire notification area needs sorted out. If you're dumping volume, battery and network icons into the same area as everything else, you really should:

#1. Sort them so they don't appear at random positions. E.G. In Vista, the network, battery and volume icons are sorted to the end of the list, with a small gap to separate them from the normal tray icons.

#2. Provide a way to hide them. Sometimes programs put horrific icons in there, with no way of hiding them. YES, it is the program's fault, but GNOME still needs to sort it out. You can't rely on every application being good.

For example, nm-applet needn't be there all of the time for me. I only connect to one network, so I'll only find it useful if there is a problem with connecting. Vista allows you to hide them, exposing them when you click the arrow. Why can't that be done in GNOME? Are there technical restrictions, or simply a lack of interest/motivation?

---

