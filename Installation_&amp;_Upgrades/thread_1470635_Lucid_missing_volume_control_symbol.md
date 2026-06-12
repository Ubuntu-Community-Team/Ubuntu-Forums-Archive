---
title: "Lucid missing volume control symbol?"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2010-05-03
Upgraded to Lucid and there is no volume control on the upper panel just to the left of the date calendar/time like there was on Karmic and earlier versions. Searched but can't find it. How can I put it back on the upper panel? It looked like a speaker with sound waves coming out of the speaker. I always used it on other versions before.

---

### Post by tixrus on 2010-05-03
> **cybrsaylr said:**
> Upgraded to Lucid and there is no volume control on the upper panel just to the left of the date calendar/time like there was on Karmic and earlier versions. Searched but can't find it. How can I put it back on the upper panel? It looked like a speaker with sound waves coming out of the speaker. I always used it on other versions before.
Same problem here.  Looking for it in right click on task bar and choose add to panel.  It's not there.  Now what?

---

### Post by kansasnoob on 2010-05-03
It's part of Indicator Applet now whch means you'll have the "envelope" whether you like it or not. I use just one panel at the bottom, look next to my clock:

[ATTACH]155279[/ATTACH]

If I clicked "about" it's indicator applet! Really :)

---

### Post by cybrsaylr on 2010-05-03
kansasnoob,
Thanks got it back up there as before. I see what you mean about having to accept the envelope also, which I would rather delete. Oh well, at least the volume can easily be controlled again....:D

---

### Post by joshzam on 2010-05-05
I found this in another thread and it works great. No unnecessary envelopes:

go to System > Preferences > Startup Applications

in the startup tab, look for 'Volume Control' and check it if its unchecked.

If its not there, 'Add' it using the following parameters:

Name: Volume Control
Command: gnome-volume-control-applet
Comment: Show desktop volume control

...and then restart...

---

### Post by zeusrock1 on 2010-05-05
> **joshzam said:**
> I found this in another thread and it works great. No unnecessary envelopes:

go to System > Preferences > Startup Applications

in the startup tab, look for 'Volume Control' and check it if its unchecked.

If its not there, 'Add' it using the following parameters:

Name: Volume Control
Command: gnome-volume-control-applet
Comment: Show desktop volume control

...and then restart...

Worked perfect for me.  Much better than the 'Indicator Applet'.  Thanks.:guitar:

---

### Post by Jackie999 on 2010-05-05
Thanks ..just what I was looking for.. what the heck is that envelope for anyway?

---

### Post by cybrsaylr on 2010-05-05
Thanks. I like this look better with no envelope.
The envelope is linked to running Empathy IM client.

---

### Post by Jackie999 on 2010-05-06
Thanks..the envelope useless to me then..I prefer pidgin over empathy.

---

### Post by cybrsaylr on 2010-05-06
I agree, empathy seems buggy.
Pidgin ran better.

---

### Post by PlaidRadish on 2010-05-14
I thought the "envelope" was an Evolution icon?

---

### Post by SunfireSSR on 2010-05-16
I followed the directions above to add Volume Control back to the Startup Apps. Still don't have a Volume Control in the top or bottom bars. Any other ideas ?

My problem started with Assistive Icons showing up in the top bar, removing the volume and the Evolution Icons -after- using this command which I thought was to help me change the purple splash screen. all I wanted was another color.

gksu -u gdm dbus-launch gnome-appearance-properties

---

### Post by _Smiler_ on 2010-05-17
> **kansasnoob said:**
> It's part of Indicator Applet now whch means you'll have the "envelope" whether you like it or not. I use just one panel at the bottom, look next to my clock:

[ATTACH]155279[/ATTACH]

If I clicked "about" it's indicator applet! Really :)

I like how you've done that! Could I ask you to tell me how? Thank you in advance!! :KS

---

### Post by Tootler on 2010-07-02
> **Jackie999 said:**
> Thanks ..just what I was looking for.. what the heck is that envelope for anyway?

I couldn't see any use for it either so I removed it. I didn't want any of the chat facilities, I never use them, and I don't use evolution for email, so it was of no use to me.

There doesn't seem any logical reason why the volume control should be tied to the other facilities linked to the envelope but I have had to put the envelope back so I can use the volume control.

Geoff

---

### Post by arturic on 2010-07-17
Hi, I'm reading this thread now and **SunfireSSR** kind of confirms my suspicion about why this happened, see my post (#10) in a very similar thread: [audio icon missing]("http://ubuntuforums.org/showthread.php?p=9601321"), also check there other possible solutions.

Cheers! :)

---

### Post by joshzam on 2010-11-04
An alternate solution to removing the envelope icon from the panel while leaving the volume control would be to enter the following in the terminal:
```
sudo apt-get purge indicator-messages
```

If it doesn't take effect right away, just remove the indicator applet and then add it again. The envelope will be gone.

---

### Post by Motorhead Kaze on 2010-11-17
Joshzam, you rule. Thanks buddy!:KS

---

### Post by fofo412 on 2010-11-26
> **joshzam said:**
> I found this in another thread and it works great. No unnecessary envelopes:

go to System > Preferences > Startup Applications

in the startup tab, look for 'Volume Control' and check it if its unchecked.

If its not there, 'Add' it using the following parameters:

Name: Volume Control
Command: gnome-volume-control-applet
Comment: Show desktop volume control

...and then restart...

I had to take the time to say THANKS, for this!!!!!

---

### Post by ozone702 on 2011-03-27
> **joshzam said:**
> I found this in another thread and it works great. No unnecessary envelopes:

go to System > Preferences > Startup Applications

in the startup tab, look for 'Volume Control' and check it if its unchecked.

If its not there, 'Add' it using the following parameters:

Name: Volume Control
Command: gnome-volume-control-applet
Comment: Show desktop volume control

...and then restart...

Thank you!  Worked like a charm :)

---

### Post by cris91music on 2012-09-14
> **joshzam said:**
> I found this in another thread and it works great. No unnecessary envelopes:

go to System > Preferences > Startup Applications

in the startup tab, look for 'Volume Control' and check it if its unchecked.

If its not there, 'Add' it using the following parameters:

Name: Volume Control
Command: gnome-volume-control-applet
Comment: Show desktop volume control

...and then restart...

that worked for me in Ibook G4 14 with ubuntu 10.10
great thanks:D

---

