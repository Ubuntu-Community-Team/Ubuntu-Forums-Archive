---
title: "Skype can't be installed"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by bastart on 2010-08-13
I downloaded the debian package from Skype.com but when I tried to install them, there's text box appeared saying I'm have to install a later version.

So I tried the terminal method
> sudo apt-get update && sudo apt-get install skype

and still no Skype in my computer. Anyone?

---

### Post by kerry_s on 2010-08-13
does it show skype as installed in synaptic package manager?

---

### Post by bastart on 2010-08-14
Managed to install it thru Synaptic and now Skype won't produce any sound but microphone and webcam are working. Whats wrong?

---

### Post by kerry_s on 2010-08-14
> **bastart said:**
> Managed to install it thru Synaptic and now Skype won't produce any sound but microphone and webcam are working. Whats wrong?

check it's not muted in the skype settings.

---

### Post by bastart on 2010-08-15
Nope. It is still unmuted. Does this have to do with sound driver because my Rhythmbox and Chromium happened to be experiencing the same thing over and over again

---

### Post by kyphi on 2010-08-15
It would be helpful if you would state what equipment you are using Skype on.

---

### Post by kerry_s on 2010-08-15
> **bastart said:**
> Nope. It is still unmuted. Does this have to do with sound driver because my Rhythmbox and Chromium happened to be experiencing the same thing over and over again

use synaptic to uninstall "gstreamer0.10-pulseaudio" it's broken & has been crashing pulseaudio.

log out & back in

press-> alt+f2
type-> gstreamer-properties

change plugin to alsa

press-> alt+f2
type-> gnome-volume-control

make sure your hardware & input & output are correct.

---

### Post by kyphi on 2010-08-15
While the solution proposed by kerry_s may work, I would hesitate to remove gstreamer0.10-pulseaudio.

However, if you do so, you can re-install it again at any time.

Pulseaudio and Skype work fine on four of my computers, two of which are netbooks running the netbook remix.  My netbooks are Asus Eee pcs.

---

### Post by kerry_s on 2010-08-15
> **kyphi said:**
> While the solution proposed by kerry_s may work, I would hesitate to remove gstreamer0.10-pulseaudio.

However, if you do so, you can re-install it again at any time.

Pulseaudio and Skype work fine on four of my computers, two of which are netbooks running the netbook remix.  My netbooks are Asus Eee pcs.

it does not remove pulseaudio. it only removes the problem libs.
pulseaudio is still there & works just fine.

---

### Post by bastart on 2010-08-15
@kyphi im using hp mini 210

I removed pulseaudio and reseted output. Both Chromium and Rhythmbox work just fine but still no audio from Skype

---

### Post by kerry_s on 2010-08-15
it's got to be in skype then.
you clicked that little icon on the bottom left corner & went to options-> sound devices, made sure the output was right?

---

