---
title: "Pidgin changes shutdown icon"
date: 2009-03-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Yumi on 2009-03-20
When I open Pidgin, the red shutdown icon in the top right corner changes to a green circle. Also and quite normal Pidgin opens a "Process icon" in the middle of the toolbar. When I quit Pidgin, I get my red icon back. Add How can I avert this?

Michael

---

### Post by Tich666 on 2009-03-20
You can disable the system tray icon in preferences (first tab, first option).

As for the shutdown icon changing to reflect your pidgin status, I don't know if you can disable that feature, but it's quite practical especially if you chose to disable the tray icon and want to change your status frequently.

---

### Post by tad1073 on 2009-03-20
You can always remove the shut down icon and have it your menu.

---

### Post by buixuanduong1983 on 2009-03-20
You can change this behavior of power button with Pidgin, you can change in gconf-editor, turn off /apps/fast-user-switch-applet/show_presence_info.

---

### Post by Yumi on 2009-03-20
Thank you buixuanduong, this is working. And thanks for the other replies. I use the QQ protocol in China and have low frequency chats. So the system-tray icon is sufficient for me.

Michael

---

### Post by Yumi on 2009-03-22
Unfortunately changing the show_presence_info setting helps - but only for a short time. Maybe after 10 Minutes, latest after restarting Pidgin the button turns to a green circle again.

Michael

---

### Post by gbrandel on 2009-03-22
I too dislike the shutdown ui component being connected to the im status.  If an application is going to repurpose and/or augment the functionality of an existing (and unrelated) ui component it would be nice if there was a corresponding straight forward configuration option to disable the integration.  Is this a native feature of pidgin on Gnome or something Ubuntu adds?

Regards,
Griffith

---

### Post by btdown on 2009-03-22
I dislike this too..It really annoys me......to the point that I want to get rid of pidgin....

I pretty much hate pidgin, but there isn't much else out there.

---

### Post by TrueTom on 2009-03-22
> **btdown said:**
> I dislike this too..It really annoys me......to the point that I want to get rid of pidgin....

I pretty much hate pidgin, but there isn't much else out there.

It's not Pidgin's fault, though...

---

### Post by Mr. Picklesworth on 2009-03-22
Or if you just need the FUSA applet for shutting down the computer, remove that applet and add the "Shut Down" applet in its place.

And this isn't Pidgin. This is a feature of the Fast User Switch applet, and it applies when you run any IM software that is well integrated with the desktop.
The green circle (or red triangle, etc.) represents your status. It will make a lot more sense when we get the whole People thing rolling.

---

### Post by mihai.ile on 2009-03-23
this is the shutdown applet problem, it should have an option for this.

P.S: I also dislike icon changing on by default

---

### Post by Polygon on 2009-03-24
i have reported a bug about this, feel free to contribute.

[https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/343349](https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/343349)

---

### Post by novafluxx on 2009-03-24
I don't really like it either, nor do I like/need/want fast user switching.

I wish there were an EASY obvious way to disable that.

---

### Post by mihai.ile on 2009-03-24
> **Polygon said:**
> i have reported a bug about this, feel free to contribute.

[https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/343349](https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/343349)

Done so, thanks.

---

### Post by TrueTom on 2009-03-24
> **novafluxx said:**
> I wish there were an EASY obvious way to disable that.

There is: Recompile gnome-panel...

---

### Post by Mr. Picklesworth on 2009-03-24
> **TrueTom said:**
> There is: Recompile gnome-panel...

Uhm... no, just remove the panel applet.

---

