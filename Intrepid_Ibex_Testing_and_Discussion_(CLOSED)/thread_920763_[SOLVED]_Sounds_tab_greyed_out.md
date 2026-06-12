---
title: "[SOLVED] Sounds tab greyed out"
date: 2008-09-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ubername on 2008-09-05
Hi 

I have sound working in applications but I don't get the system sounds (I like the logon / logoff sounds in particular). When I go to the Sounds tab from properties>sound, all options are greyed out.

I saw this [http://ubuntuforums.org/showthread.php?t=887302](http://ubuntuforums.org/showthread.php?t=887302)

I note the bug report at the end but I am sure I have had system sounds working on this Intrepid install before.

but it doesn't help with what to do when I get 

~$ gnome-sound-properties

(gnome-sound-properties:8961): libglade-WARNING **: could not find glade file 'sound-properties.glade'

(gnome-sound-properties:8961): sound-properties-WARNING **: Bad setup, install the freedesktop sound theme

I have found sound-properties.glade in /usr/share/gnome-control-center/glade

Any Clues?

TIA

---

### Post by ubername on 2008-09-14
> **ubername said:**
> Hi 

I have sound working in applications but I don't get the system sounds (I like the logon / logoff sounds in particular). When I go to the Sounds tab from properties>sound, all options are greyed out.

I saw this [http://ubuntuforums.org/showthread.php?t=887302](http://ubuntuforums.org/showthread.php?t=887302)

I note the bug report at the end but I am sure I have had system sounds working on this Intrepid install before.

but it doesn't help with what to do when I get 

~$ gnome-sound-properties

(gnome-sound-properties:8961): libglade-WARNING **: could not find glade file 'sound-properties.glade'

(gnome-sound-properties:8961): sound-properties-WARNING **: Bad setup, install the freedesktop sound theme

I have found sound-properties.glade in /usr/share/gnome-control-center/glade

Any Clues?

TIA

Sort of a bump

But also this might be connected with why my speakers work until I plug in the headphones, then the speakers stop working (after I unplug the headphones - I would of course expect them to stop working when the headphones were in!) and over the course of about ten seconds the sound fades to zero in my headphones.

I now get (from gnome-sound-properties)


(gnome-sound-properties:7980): sound-properties-WARNING **: Bad setup, install the freedesktop sound theme

How would I install the freedesktop sound theme?

---

### Post by nowin4me on 2008-09-14
> **ubername said:**
> Hi 

I have sound working in applications but I don't get the system sounds (I like the logon / logoff sounds in particular). When I go to the Sounds tab from properties>sound, all options are greyed out.

Hi there,

I have the same problem but I have sound all the time apart from loging in and out I am using Ubuntu 8:10 Intrepid alpha 5. Kind of annoying since I love the start up sound.

Maybe you could tell us what version of Ubuntu your using?
And the name of the sound card..... I don't no mine thought.

As for the sound fading away try this:

```
~$ gnome-sound-properties
```

Then go right down to the bottom there should be something called **Audio Conferencing** where it says sound capture try chaning it and then press test to see if that helps.

---

### Post by ubername on 2008-09-14
> **nowin4me said:**
> Hi there,

I have the same problem but I have sound all the time apart from loging in and out I am using Ubuntu 8:10 Intrepid alpha 5. Kind of annoying since I love the start up sound.

Maybe you could tell us what version of Ubuntu your using?
And the name of the sound card..... I don't no mine thought.

As for the sound fading away try this:

```
~$ gnome-sound-properties
```

Then go right down to the bottom there should be something called **Audio Conferencing** where it says sound capture try chaning it and then press test to see if that helps.

Thanks.

I have sorted the 'greyed out' bit by installing the freedesktop theme ([https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/258703](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/258703)). I tried the 'Audio conferencing' thing, set it to Pulse Audio - Same thing.

I'm using kernel 2.6.27-3, Gnome 2.23.92

---

### Post by nowin4me on 2008-09-14
> **ubername said:**
> Thanks.

I have sorted the 'greyed out' bit by installing the freedesktop theme ([https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/258703](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/258703)). I tried the 'Audio conferencing' thing, set it to Pulse Audio - Same thing.

I'm using kernel 2.6.27-3, Gnome 2.23.92

Great......... Now all I got to do is log into root.

Thanks.

---

### Post by cariboo on 2008-09-14
In the future post your comments and questions here:

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

You are more then likey to get a quicker answer concerning Intrepid.

Jim

---

### Post by ubername on 2008-09-14
> **cariboo907 said:**
> In the future post your comments and questions here:

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

You are more then likey to get a quicker answer concerning Intrepid.

Jim

Thanks Jim

Is there a way of moving a thread from one forum to another?

---

### Post by nowin4me on 2008-09-15
> **ubername said:**
> Thanks Jim

Is there a way of moving a thread from one forum to another?

You could ask a moderator to move it for you.

[Look here]("http://ubuntuforums.org/index.php")

Scrool down to the bottom until you see **What's Going On?**
And you see the people with [COLOR="Red"]red writing[/COLOR] They are mods PM one of them and tell them that you would like this moved.

---

