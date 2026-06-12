---
title: "Human Theme not updating with intrepid"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by zorkerz on 2008-10-21
Ive been testing usb-creator. For this I downloaded the most recent intrepid iso and installed it on my usb. When I booted off the usb I discovered to my horror that it had a different default human theme than the intrepid installed on my harddrive. Notably the panels have become slightly transparent.

Whats up with this? I update religiously too much in fact I worry about my impact on the kind people who run ubuntu repo mirrors.

How else will my intrepid installation be different than the final release when it comes out?

---

### Post by OrangeCrate on 2008-10-21
> **zorkerz said:**
> Ive been testing usb-creator. For this I downloaded the most recent intrepid iso and installed it on my usb. When I booted off the usb I discovered to my horror that it had a different default human theme than the intrepid installed on my harddrive. Notably the panels have become slightly transparent.

Whats up with this? I update religiously too much in fact I worry about my impact on the kind people who run ubuntu repo mirrors.

How else will my intrepid installation be different than the final release when it comes out?

At least I can comment about the new panel transparency. Post #53 in this thread should answer your question:

[http://ubuntuforums.org/showthread.php?t=948538&page=6](http://ubuntuforums.org/showthread.php?t=948538&page=6)

Surprised me a bit, but apparently it won't come through the updates. People will have to install it in the panel,  under Panel Properties > Background > Background Image, then load, /usr/share/themes/human/panel_bg.png.

---

### Post by rockin_goliath on 2008-10-21
I must say, I LOVE the Intrepid Human theme. The transparent panels are PERFECT, especially how about 3-4 pixels on the bottom edge are black, so it makes it much more three dimensional. The work that was done with the gtkrc file is just incredible. The new background is also awesome. Installing gnome-backgrounds also gives you some beautiful backgrounds. Way to go Art Team!!!!

---

### Post by wgrant on 2008-10-21
> **OrangeCrate said:**
> At least I can comment about the new panel transparency. Post #53 in this thread should answer your question:

[http://ubuntuforums.org/showthread.php?t=948538&page=6](http://ubuntuforums.org/showthread.php?t=948538&page=6)

Surprised me a bit, but apparently it won't come through the updates. People will have to install it in the panel,  under Panel Properties > Background > Background Image, then load, /usr/share/themes/human/panel_bg.png.

We can't touch user configuration on upgrades. That would be very bad, and there's no easy way to do it.

For important changes such as the new FUSA applet, we have update-notifier pop up a window and run a Python script to migrate if the user asks for it. But the panel background image change won't cause old installations to look strange or break.

---

### Post by zorkerz on 2008-10-21
Thank you OrangeCrate panel_bg.png advice that is perfect for making my human theme look how new installs do. I still have a problem, however, Ive been switching back and forth between the human and dark room themes. Now when I switch back to dark room I need to go to properties in each panel and set the background image to default and when I switch back to human i must again manually select panel_bg.png.

There must be some way to update my human theme. I tried customizing it but there did not seem to be the right options.

Also Im still wondering if there is any other stuff on my system that is not really getting updated or cruft that is left over?

---

### Post by OrangeCrate on 2008-10-21
> **zorkerz said:**
> Thank you OrangeCrate panel_bg.png advice that is perfect for making my human theme look how new installs do. I still have a problem, however, Ive been switching back and forth between the human and dark room themes. Now when I switch back to dark room I need to go to properties in each panel and set the background image to default and when I switch back to human i must again manually select panel_bg.png.

There must be some way to update my human theme. I tried customizing it but there did not seem to be the right options.

I'm sorry, but I can't help you on any dark themes. I don't like them, nor use them. Maybe someone else will come along with a solution for you...

> Also Im still wondering if there is any other stuff on my system that is not really getting updated or cruft that is left over?

Found something new. "System Cleaner". Install it from Synaptic, and it'll show up under system tools in the Menu. Cleans up all the "cruft". Read more about it here:

[https://wiki.ubuntu.com/CleanupCruft](https://wiki.ubuntu.com/CleanupCruft)

---

### Post by OrangeCrate on 2008-10-21
> **wgrant said:**
> We can't touch user configuration on upgrades. That would be very bad, and there's no easy way to do it.

For important changes such as the new FUSA applet, we have update-notifier pop up a window and run a Python script to migrate if the user asks for it. But the panel background image change won't cause old installations to look strange or break.

Thanks for the explanation. Very interesting.

---

### Post by mc4100 on 2008-10-21
> **wgrant said:**
> We can't touch user configuration on upgrades. That would be very bad, and there's no easy way to do it.

For important changes such as the new FUSA applet, we have update-notifier pop up a window and run a Python script to migrate if the user asks for it. But the panel background image change won't cause old installations to look strange or break.

Can you clarify this?

Changing configuration = bad 
... if a user has explicitly configured the panel to use a certain background image, then it is indeed a bad thing to override that.

But can't the new image be set as default for the "None (Use System Theme)" option, ie., it will only be shown if the Human theme is in use, and the user has not changed the panel image manually.

---

### Post by zorkerz on 2008-10-21
I agree with you mc4100 it seems that if the defaults are still used then they could be updated safely. I do see though how this is a very tricky issue if mistakes were made bad news bears could follow. 

As for the new dark room theme. I have never in the past been much into dark themes. The one I like most in the past was ubuntustudio's theme. But dark room has been really pleasing to me. Part of it is just he change of pace and there are still some downsides like having a hard time telling which firefox tab I have selected but overall im very impressed.

---

