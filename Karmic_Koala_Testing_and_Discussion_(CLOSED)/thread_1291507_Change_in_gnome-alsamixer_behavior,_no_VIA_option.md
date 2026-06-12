---
title: "Change in gnome-alsamixer behavior, no VIA option?"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2009-10-14
In order to get acceptable sound with my VIA VT8237 sound card I've always had to tweak the VIA toggles as shown here:

[ATTACH]131953[/ATTACH]

or optionally by changing preferences in volume control:

[ATTACH]131954[/ATTACH]

New behavior in gnome-alsamixer:

[ATTACH]131955[/ATTACH]

And of course you can right click your volume control and see the options no longer exist to tweak the VIA controls, nor do they exist by running alsamixer from terminal.

So, how do I adjust that?

Is it a bug?

Or does Ubuntu now hate my hardware?

---

### Post by kansasnoob on 2009-10-14
Well, I did find a way to get sound working acceptably. It involves downloading and installing the Linux drivers here:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=23&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=23&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false)

Still seems like a regression though since the AC97 cards have been supported since at least Gutsy.

EDIT: That's not so good either. It actually downgrades alsa-utils and alsa-lib to 1.0.14 from 1.0.20 and results in muted sound on reboot. So it's back to the drawing board.

---

### Post by kansasnoob on 2009-10-14
Filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/451813](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/451813)

Many thanks to 23meg for having the patience to teach me how to file a bug report!

---

### Post by VMC on 2009-10-14
Unrelated to your problem, but for the first time I couldn't get any sound out of my music. alsamixer show everything off.

 After playing around with various things, last resort I checked the audio icon and sure enough it was muted. 

I wondered if something recent alter audio. Maybe that's why you can't play your via stuff.

---

### Post by kansasnoob on 2009-10-14
> **VMC said:**
> Unrelated to your problem, but for the first time I couldn't get any sound out of my music. alsamixer show everything off.

 After playing around with various things, last resort I checked the audio icon and sure enough it was muted. 

I wondered if something recent alter audio. Maybe that's why you can't play your via stuff.

I've had that happen several times throughout the development process and I can usually get it working again using gnome-alsamixer and the volume control.

The VIA controls were still present in earlier versions of Karmic. I filed the bug against alsa-utils but it may actually have something to do with a tweak to one of the graphics tools.

They'll get it sorted out:)

That's why it's important to file bug reports.

---

### Post by kansasnoob on 2009-10-23
Thought I'd bump this to see if others notice the same.

It's a very common sound card. Even still a lot of the Atom mini-ITX knockoffs use it!

The total lack of VIA controls wrecks the sound quality!

---

### Post by jblackhall on 2009-10-23
Where's the bug report?  Have you gotten any response on it?  You may try to get ahold of crimsun aka dtchen (dan chen) either on the forums or irc.  He's very helpful with audio stuff.  He may know more about what happened to the controls you're looking for.  In the end, I think they'd like to make it so you wouldn't need to adjust anything in alsa mixer to get good sound.

Also, have you checked this in Karmic recently to see if there's any progress?  The reason I ask is because I had an issue with mic volume not being adequate last week and an update to alsa-utils a few days ago fixed that.

---

### Post by kansasnoob on 2009-10-24
> **jblackhall said:**
> Where's the bug report?  Have you gotten any response on it?  You may try to get ahold of crimsun aka dtchen (dan chen) either on the forums or irc.  He's very helpful with audio stuff.  He may know more about what happened to the controls you're looking for.  In the end, I think they'd like to make it so you wouldn't need to adjust anything in alsa mixer to get good sound.

Also, have you checked this in Karmic recently to see if there's any progress?  The reason I ask is because I had an issue with mic volume not being adequate last week and an update to alsa-utils a few days ago fixed that.

All but one question you ask is answered in previous posts in this thread!

I don't do IRC because of physical liabilities that make responding difficult and slow. But I have worked with Crimsun before in April, and he solved the problem.

I'm sure I'm just being impatient about a response to my bug report:

[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/451813](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/451813)

---

