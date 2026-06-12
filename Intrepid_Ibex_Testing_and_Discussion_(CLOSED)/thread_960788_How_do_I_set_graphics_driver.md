---
title: "How do I set graphics driver?"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by SveinT on 2008-10-27
Hi,

I recently installed Intrepid beta and updated it, so it should be release candidate now. After a quite long list of problems (but, hey it's beta), I am now just stuck with a few. One is that at first the intel video driver worked perfectly aswell as compiz. After some updates it now doesn't, but I don't know how to fix it. But my main issue is, how on earth to I select display driver? displayconfig-gtk is no more, so what are my options? It's ridiculous that it's so hard to find out how to do such a task. I have after all been using linux for 1.5 years and know somewhat my way around the system. Is xorg.conf still used, as I thought it was supposed to be deprecated?

Hardware Drivers as it's so nicely called is quite misleading seeing as it only has to do with restricted drivers.

---

### Post by xnerdx on 2008-10-27
I'm suprised I have much more support for Intel but either way I would expect that xorg.conf is still in use, although when I used the xorg.conf my system didn't seem to enjoy my desires :).

Go ahead and try
Device:           "Whatever"
Drive:            "Intel"
BusID:            "00:00:00 (your bus id)"

---

### Post by SveinT on 2008-10-27
> **xnerdx said:**
> I'm suprised I have much more support for Intel but either way I would expect that xorg.conf is still in use, although when I used the xorg.conf my system didn't seem to enjoy my desires :).

Go ahead and try
Device:           "Whatever"
Drive:            "Intel"
BusID:            "00:00:00 (your bus id)"

Thanks for your answer. I might try that, but that can't possibly be the "official" way to do this? How is a new user (even skilled technically) supposed to know this? Isn't there a new displayconfig somewhere?

dpkg-reconfigure xserver-xorg gives no video options anymore.

---

### Post by phidia on 2008-10-27
xorg has been changed since hardy and the Ubuntu wiki has not been fully updated to reflect that. There is however a note to that change see the wiki page [here]("https://help.ubuntu.com/community/Video") and the note on xorg.

You can also look at the [xorg 7.4 features]("http://www.x.org/wiki/Releases/7.4") page.

It's actually fairly frustrating to try to help people with xorg problems because there isn't enough clear documentation on how to fix xorg issues.

---

### Post by phidia on 2008-10-27
> **SveinT said:**
> Thanks for your answer. I might try that, but that can't possibly be the "official" way to do this? How is a new user (even skilled technically) supposed to know this? Isn't there a new displayconfig somewhere?

dpkg-reconfigure xserver-xorg gives no video options anymore.

You can try > sudo dpkg-reconfigure -phigh xserver-xorg
See if that configures your card & monitor correctly. 

Note: You will not get the questions about cards & resolution that use to be there-that's gone now.

---

### Post by SveinT on 2008-10-27
> **phidia said:**
> xorg has been changed since hardy and the Ubuntu wiki has not been fully updated to reflect that. There is however a note to that change see the wiki page [here]("https://help.ubuntu.com/community/Video") and the note on xorg.

You can also look at the [xorg 7.4 features]("http://www.x.org/wiki/Releases/7.4") page.

It's actually fairly frustrating to try to help people with xorg problems because there isn't enough clear documentation on how to fix xorg issues.

Thanks for the answer, things are a bit clearer now. While I guess the automatic detection is nice, when it breaks it's kinda horrible. Why remove a quite nice tool like displayconfig? Documentations shouldn't be a necessity imho, as it should be so easy that it's not needed (like on hardy, and believe me I had to config that many times on my other computer due to nvidia).

In my case I guess I have to debug why the intel driver doesn't work. It shows no errors in the log and it seems to be loaded. glxinfo only shows VESA so I guess not.

---

### Post by SveinT on 2008-10-27
Thanks a lot for the reconfigure tip, I tried it and for some reason things work like a charm again.

My original question still stand though.

---

### Post by wgrant on 2008-10-27
Why would you need to manually alter the video driver? The only instances in which that is required are for enabling proprietary drivers, and jockey does that fine.

---

### Post by super.rad on 2008-10-28
I was looking for how to do this aswell, seems KDE4 isn't working well with the SiS driver so I need to change it to vesa to see if that works better but couldn't find anything on how to change it.

---

