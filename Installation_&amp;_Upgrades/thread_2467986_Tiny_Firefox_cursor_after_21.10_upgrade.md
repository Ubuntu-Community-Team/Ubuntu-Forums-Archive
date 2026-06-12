---
title: "Tiny Firefox cursor after 21.10 upgrade?"
date: 2021-10-14
forum: Installation &amp; Upgrades
---

### Post by csete on 2021-10-14
I upgraded my Dell XPS 15 laptop from 21.04 to 21.10 today.  In general, things are working pretty well.  However, while I have the cursor scaled up on my desktop (hidpi screen), the cursor does not appear to be honored by Firefox.  It is super tiny and does not appear to be the same theme as I'm using elsewhere.  I'm assuming this has something to do with the switch to a Snap package, but I have to believe there is a way to get this working?

Any suggestions?
Thanks,
Craig

---

### Post by grahammechanical on 2021-10-14
You could be right about the switch to the snap package version of Firefox. I do know that the snap packaged version uses Gnome 38 whereas Ubuntu 21.10 has Gnome 40. Try searching for Firefox in Ubuntu Software. You might find some options that you can change. 

Regards

---

### Post by csete on 2021-10-15
I gave the Flatpak version a try, but seeing the same behavior.  Any other ideas?

---

### Post by Dennis N on 2021-10-15
Try login with "Ubuntu on Xorg" option instead of "Ubuntu". The "Ubuntu" choice starts the Wayland display manager. Does this make a difference?

---

### Post by csete on 2021-10-15
> **Dennis N said:**
> Try login with "Ubuntu on Xorg" option instead of "Ubuntu". The "Ubuntu" choice starts the Wayland display manager. Does this make a difference?

Yes.  That does improve the situation.  Is there anything I'm missing by using X11 versus Wayland?

---

### Post by Dennis N on 2021-10-15
> **csete said:**
> Yes.  That does improve the situation.  Is there anything I'm missing by using X11 versus Wayland?

Actually, from the user point of view, I think we are missing things by choosing Wayland. I use Xorg because some applications I use don't work with Wayland - xscreensaver and plank are two examples of things I want to use. Also, I had a different cursor problem on a virtual machine with Wayland, but it does not happen with Xorg.

Wayland is still a work in progress (and has been for years), so until these things are cleared up, I steer clear of Wayland.

---

### Post by VMC on 2021-10-15
> **csete said:**
> I gave the Flatpak version a try, but seeing the same behavior.  Any other ideas?

You could try [Nightly]("https://www.mozilla.org/en-US/firefox/channel/desktop/"), see if that helps, and yes 21.10 now has Snap for Firefox. I removed Snap and all its children and use Nightly instead.

---

### Post by csete on 2021-10-15
> **Dennis N said:**
> Actually, from the user point of view, I think we are missing things by choosing Wayland. I use Xorg because some applications I use don't work with Wayland - xscreensaver and plank are two examples of things I want to use. Also, I had a different cursor problem on a virtual machine with Wayland, but it does not happen with Xorg.

Wayland is still a work in progress (and has been for years), so until these things are cleared up, I steer clear of Wayland.

One thing that is missing that I actually miss is 3-finger gestures.  I have a Mac for work and I really miss the 3 finger swipe gesture there and in Ubuntu.  That is working in Wayland on 21.10, but not on X11.

---

### Post by csete on 2021-10-15
For anyone checking in on this.  While I think Wayland is smoother, the best combination *for me* is X11 plus [https://extensions.gnome.org/extension/4033/x11-gestures/](https://extensions.gnome.org/extension/4033/x11-gestures/) for the moment.  It seems to be the best compromise of things I care about.

---

