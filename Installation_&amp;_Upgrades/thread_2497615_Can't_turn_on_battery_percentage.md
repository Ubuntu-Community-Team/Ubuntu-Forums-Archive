---
title: "Can't turn on battery percentage"
date: 2024-05-12
forum: Installation &amp; Upgrades
---

### Post by seattle vic on 2024-05-12
I've just installed ubuntu 24.04 on 4 of my home machines and I can't figure out how to enable the little battery % icon to the right of the battery in the top panel.  I realize that if you click on the battery it shows in the box that appears but I'd like to see it at a glance like it used to be.  The power section of settings used to have a way to turn it on toward the bottom but it's gone now.   I've tried the dconf-editor and gnome-tweaks with no luck.  To make it a bit more frustrating I was able to turn it on with one of my machines but now I don't remember where I found the way to do that.

What am I missing?

Thanks in advance...

---

### Post by grahammechanical on 2024-05-12
Have you tried? System Settings>Power - scroll down to General and move the slider labelled Show Battery Percentage. It works on 24.04 for me.

Regards

---

### Post by seattle vic on 2024-05-12
That area is no longer there.  Here's what my settings-power page looks like:
[IMG]https://drive.google.com/file/d/11scENuzhAUKoUUez62DIqfLsO33q1MR-/view?usp=sharing[/IMG]

Well, I hope you can see that URL.  If not, all that is on the page are the following sections: 

Battery Level
Connected Devices
Power Mode
Power Saving

i remember that box you're talking about but it's not showing up on my power page.

---

### Post by seattle vic on 2024-05-12
i can't seem to get an image into this post, either by a paste or by insertine a url...

---

### Post by seattle vic on 2024-05-12
Here's the url of the image:

[https://drive.google.com/file/d/11scENuzhAUKoUUez62DIqfLsO33q1MR-/view?usp=drive_link](https://drive.google.com/file/d/11scENuzhAUKoUUez62DIqfLsO33q1MR-/view?usp=drive_link)
.

---

### Post by mmwelt on 2024-11-01
If anyone is still looking for the solution, it's this:

- Open dconf-editor (if not already installed, install it with `sudo apt install dconf-editor`).
- Navigate to `org/gnome/desktop/interface` and enable `show-battery-percentage`.

---

