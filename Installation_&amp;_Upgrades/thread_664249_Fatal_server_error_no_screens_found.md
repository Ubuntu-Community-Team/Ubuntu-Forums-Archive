---
title: "Fatal server error: no screens found"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by Quijibo on 2008-01-11
Hi, new here.  I saw other threads on this topic from a couple years ago up until maybe 3 or 4 weeks ago but a solution was not found.  Here's my problem:

I used wubi to install ubuntu, everything was going fine (it installed, gave me the option to boot into ubuntu or Windows, etc.) until it came to a screen where I believe it said there was an error.  I was given the option of seeing what the error was, so I chose to see what it was/is.  It said:

[I]Failed to start the x server

Screen(s) found, but none have a usable configuration

Fatal server error:  no screens found
[/I]
(not in italics)
I don't know what to do, I'm a complete noob.

My graphics card is an NVIDIA GeForce 8400M GS, running on windows XP.  Its a Dell Vostro 1500.

I also saw in other threads that you have to enter some sort of code or what have you.  Where does one do this?  Please let me know if any other information is needed and thank you for your help or at least reading!

---

### Post by zvacet on 2008-01-11
ctrl+alt+F2

```
sudo dpkg-reconfigure xserver-xorg
```

When you come to the driver step select vesa driver,and when you finish with reconfiguring restart comp and you should have basic graphic.After that you can go and search for your video driver.Try restricted manager.

---

### Post by Quijibo on 2008-01-11
Thank you for the quick reply zvacet.  I did do what you said but it seems theres another error.

After doing what you said and going through all these questions or what have you, it gave me a new error:

Ubiquity-dm: Fatal I0 error 104 (Connection reset by peer) on x server :0.0.  [fail]

I also think for some reason it wants to be displayed on an LCD or CRT monitor instead of a laptop's monitor because it keeps asking for PCI slot numbers or other information.  Upon typing:  sudo shutdown -r now, it gave me errors concerning a PCI bus but it was too quick for me to write down.

---

### Post by zvacet on 2008-01-11
Try in recovery mode

```
etc/init.d/gdm start
```

---

### Post by Quijibo on 2008-01-11
D'oh, tried that but it did not work.

From before (when I tried the reconfigure), this is what it said before it rebooted:

NetworkManager: nm-dbus_signal_state_change: assertion 'connection ! = NULL' fail

It said that twice, then it said this twice:

NetworkManager: nm_dbus_signal_status_change: assertion 'cb_data->data->dbus connection' failed

Maybe ubuntu/linux simply won't work on this machine or for whatever reason because of the screen or graphics card?

---

