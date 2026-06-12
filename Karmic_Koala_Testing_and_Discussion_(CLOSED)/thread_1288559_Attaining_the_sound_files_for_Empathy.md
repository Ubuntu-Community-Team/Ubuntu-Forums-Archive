---
title: "Attaining the sound files for Empathy?"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Grimhound on 2009-10-11
How do I go about giving Empathy its sound files, as I am to understand they were not included with the 9.10 alpha/beta builds. Is this because they're working on custom Ubuntu-themed sounds to replace them, or merely an oversight?

---

### Post by Grimhound on 2009-10-11
Anyone?

---

### Post by Nerd_bloke on 2009-10-11
The bug report on launchpad is [here]("https://bugs.launchpad.net/bugs/400485")

---

### Post by tgpraveen on 2009-10-12
they have just fixed it. so upgrade and then tell me how you like the new sounds.

/me still on jaunty.

---

### Post by Grimhound on 2009-10-12
> **tgpraveen said:**
> they have just fixed it. so upgrade and then tell me how you like the new sounds.

/me still on jaunty.
Still getting nothing.

---

### Post by joey-elijah on 2009-10-12
I noticed a new "ubuntu sounds" update when updating earlier, but i can't say i've heard anything new..

EDIT: Oh no! I heard them! Haha! They're... tiny...

I posted it on my blog - hit up the sig

---

### Post by novafluxx on 2009-10-12
I have latest updates, and I still hear nothing from Empathy...volume is at 100% right now...let me test it again...

Negative, nothing...I even enabled sounds while away/busy, and still hear nothing.

So, whats wrong?

EDIT: Just tried a game at armorgames.com and the flash game had sound just fine, so my system's sound setup is working.

---

### Post by Grimhound on 2009-10-12
> **novafluxx said:**
> I have latest updates, and I still hear nothing from Empathy...volume is at 100% right now...let me test it again...

Negative, nothing...I even enabled sounds while away/busy, and still hear nothing.

So, whats wrong?

EDIT: Just tried a game at armorgames.com and the flash game had sound just fine, so my system's sound setup is working.

What they added was nothing to call home about. Like a .3 second ping sound that selectively plays. Fail update.

---

### Post by novafluxx on 2009-10-13
I do believe I'll be sticking with pidgin upon final release of 9.10.:confused:

Will it be possible to remove Empathy and its dependencies?:guitar:

---

### Post by joey-elijah on 2009-10-13
> **novafluxx said:**
> I do believe I'll be sticking with pidgin upon final release of 9.10.:confused:

Will it be possible to remove Empathy and its dependencies?:guitar:
Poor empathy! Once facebook chat works stable in it it's bye bye pidgin for me! 

Errm yes you can - but it shares stuff with pidgin so be careful NOT to blitz every last trace of empathy incase it takes something purple with it..

---

### Post by joey-elijah on 2009-10-13
> **Grimhound said:**
> What they added was nothing to call home about. Like a .3 second ping sound that selectively plays. Fail update.

it was a bit... pointless. The sound is the same as in kopote KDE apaprently.. so double fail for not coming up with something new!

---

### Post by novafluxx on 2009-10-13
So...how do I obtain these sounds you type of?

---

### Post by SqRt7744 on 2009-10-23
The empathy sound that is played when you receive a new message is contained in this file:
/usr/share/sounds/ubuntu/stereo/message-new-instant.ogg

which is in the ubuntu-sounds package. To see all the sounds in this file you can type, in a terminal, 

```

dpkg -L ubuntu-sounds

```

I found the message-new-instant.ogg to be much to 'quiet' to be useful, especially since it often blends in with background music. Personally I like the 'drip' sound better, so I changed the the message-new-instant.ogg to /usr/share/sounds/gnome/default/alerts/drip.ogg by issuing the following command in a terminal:

```

sudo cp /usr/share/sounds/gnome/default/alerts/drip.ogg /usr/share/sounds/ubuntu/stereo/message-new-instant.ogg

```

*[COLOR="Red"]NOTE[/COLOR]*
[COLOR="Red"]This is not the "right" way to do things, since you are overwriting /usr/share/sounds/ubuntu/stereo/message-new-instant.ogg irreversibly.[/COLOR] ... but I couldn't find the proper way (changing the setting with gconf-editor) and I'm sure I never want to change the sound back. If you're want to change it back, either back-up the sound first, or reinstall the ubuntu-sounds package.

---

### Post by Aries K on 2009-10-23
Has anyone got a message-sent sound to work? I assigned a message-sent.ogg since one was not included and it will not play because the window is focused as the message-receive sound will not play because the window is not focused. Is there a way to enable sounds when the window is focused? Thanks in advance.

---

