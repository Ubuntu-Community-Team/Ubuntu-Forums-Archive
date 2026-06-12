---
title: "Sending files from bluetooth phone to computer"
date: 2009-09-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by isecore on 2009-09-05
Just a minor question, but how does one go about enabling incoming filetransfers?

Previously on Jaunty (and everyone before) I'd install something called gnome-obex-whatever which would enable Gnome to understand incoming filetransfers using bluetooth. Seemingly this package/application no longer exists in Karmic.

When I try sending a file from my bluetooth-phone to my computer, it simply says it can't connect - or, lately it's simply not finding my computer, even though it's set to being visible.

Any thoughts on this?

---

### Post by Darkshade on 2009-09-05
I can't find my PC with my phone either and I have it set as always visible. What I did was pair the phone with the PC and then just browse my phone from the PC which turned to be so much more comfortable for me that I forgot to look for a solution :lol:

---

### Post by isecore on 2009-09-05
Yes, that works fine for me too, but in my opinion it's a bit unwieldy.

---

### Post by Jay_Bee on 2009-09-05
You need to install "gnome-user-share" as stated in the gnome-bluetooth help file (FAQ section)

---

### Post by isecore on 2009-09-05
> **Jay_Bee said:**
> You need to install "gnome-user-share" as stated in the gnome-bluetooth help file (FAQ section)

I refuse to install that, since it depends on Apache. Why would I want Apache2 running on my workstation? It's useless.

---

### Post by walmis on 2009-09-06
[Blueman]("http://blueman-project.org") supports obex server and much more.
[https://edge.launchpad.net/~blueman/+archive/blueman-dailies]("https://edge.launchpad.net/%7Eblueman/+archive/blueman-dailies")

I suggest using daily builds for now, because there are many fixes for karmic since version 1.10.

PS. It's intended to replace gnome bluetooth applet.

---

### Post by isecore on 2009-09-06
> **walmis said:**
> [Blueman]("http://blueman-project.org") supports obex server and much more.
[https://edge.launchpad.net/~blueman/+archive/blueman-dailies]("https://edge.launchpad.net/%7Eblueman/+archive/blueman-dailies")

I suggest using daily builds for now, because there are many fixes for karmic since version 1.10.

PS. It's intended to replace gnome bluetooth applet.

Thanks, that was a useful tip. Blueman is very nice, is it supposed to become an official part of Gnome in the future or what? Just wondering, works excellent.

---

### Post by Darkshade on 2009-09-06
Thanks walmis, Blueman is totally awesome!

---

