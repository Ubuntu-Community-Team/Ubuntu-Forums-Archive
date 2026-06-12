---
title: "Keyboard input broken on upgrade to lucid"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by Slates on 2010-07-27
There are several posts about this, but the two solutions I see arent helping ! 


[LIST=1]
[*]previosuly installed products that mapped keys, but I dont have and have never had any of them.
[*]reset the keyboard to default settings, which I happily did to no avail.
[/LIST]
So for me, since I upgraded, keyboard input (either local or via VNC, so it isnt hardware) does nothing for either the caps lock key or the shift key. Kinda makes it imnpossible to eneter @ or any uppercase character, for example !

I stumped as to how I fix this (save downgrading), unless I have missed the point on the other solutions as per above.

Can anyoine help me please, I miss uppercase and the @ symbol much more that I realise !

---

### Post by lechien73 on 2010-07-28
If you open a terminal window and type:

```
sudo dpkg-reconfigure console-setup
```

Does this help with the proper keyboard mapping?

---

### Post by Slates on 2010-07-28
Unfortunately no, it has made no difference, even after a reboot. And that's accessing via VNC. Of course there a re a whole heap of different options, but I ran with defaults which all looked sensible and, to my thinking, shouldn't change things so much as to stop the caps/shift keys from working.

On the bright side it did give me some amusement to see that Australia wasnt listed as a country, unlike most other places in the world ! I mean it is a relatively large continent in the scheme of things ... but I doubt this has anything to do with my issue, which seems directly related to my upgrade from Ubuntu 9 to 10 :D.

Im open to any ideas, Im stumped . . .

---

### Post by lechien73 on 2010-07-28
I presume that you're not using Ubuntu in a virtual machine? What hardware are you using? Does running:

```
setxkbmap
```

do anything? When I went off and did a bit of research on this problem for you, NVidia's proprietary drivers seemed to be causing an issue. Have you tried disabling them?

---

### Post by Slates on 2010-07-28
Thankyou verymuch for your time. It pains me I have to ask for help, but Im stumped !

No, Im not using a virtual machine. Im running on a DELL D600 Latitude laptop (which as I said happily ran Ubuntu 9), accessing it primarily through VNC. 

Yes, running setxkbmap was part of one of the above solutions I tried - I could have highlighted that, sorry. 

I didnt pick the possible link with NVidia's proprietary drivers when I was researching - thanks for that tip. But looking at a few threads, some are talking about a video driver, not a keyboard. It then occurred to me I shouldnt try uninstalling or downgrading anything until I kow what Im doing :-) ???

---

### Post by Slates on 2010-07-30
OK, now this is strange, but its what happened.

I finally plugged in a USB keyboard (I mostly use the server via VNC). Even though the standard keyboard will no longer generate capital letters, the USB one does no problem.

I then tried VNC. That also permits uppercase character entry. Somewhat puzzled, I reboot. Same. Capitalisation works. 

So, it must be somethng to do with the USB keyboard ? So I unplug it. Caps stay. So I reboot (without the USB keyboard). Caps stay.

Now that is indeed strange.

It pains me to mark the thread as solved, because I dont know the root cause. And it could come back any time. But I dont think anyone (especially not me) is going to be discovering the root cause ....

perhaps this will help someone else with the same issue - I see similar posts going back as far as Ubuntu 7, although mostly tey get solved with the soltuons offered.

thanks for everyone's help. Onto my disappearing Samba on Lucid upgrade post (gees these upgrades are painful sometimes ! However it did get zoneminder working with the Logitec STX webcam, so it wasnt witout cause :-)

---

### Post by monsterRobot9876 on 2010-08-02
hi. i'm having the same problem. however, i access my ubuntu machine from a laptop and it would be really annoying having to connect a usb keyboard to it.

after the upgrade from 9.10 to 10.04 i was not able to send capital letters via VNC, although i have checked i am able to send the shift key (checked with /usr/bin/xev)

any ideas of what is going on? i have tried the proposed solutions above already.

cheers.
salomon.

---

### Post by Slates on 2010-08-03
No unfortunately I have no idea why this strage bug appears, all I iknow is there are various reports of it across different Ubuntu uggrades stretching back quite some time.

I use my laptop in the same way as you, and attaching a keyboard is not convenient at all. However, just to be clear, I only had to attached the usb keyboard the once and the problemwas immediately resolved. Now I do not need the USB keyboard at all, I simply use VNC which now has full operation of the shift and caps lock keys.

Soundslike a tal story, but that is truly all I did - plug in the USB keyboard. Type a bit into a terminal window, unplug it and the problem was gone. Even survives reboots :D

---

