---
title: "No sound in jaunty upgrade just weird beep"
date: 2009-02-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ghostandmachine on 2009-02-08
so i upgraded to jaunty and now I have no sound (in totem, firefox, etc.)

but what I do have is a really weird scratch sound like when I hold the backspace key in the terminal. And it comes from my speakers so it's not the PC beep. 

I've looked through the forums and haven't found anything. Some say it's a bug but I would think it would be fixed now.

in alsamixer all of the levels are to the max, and none of them are muted. I even tried to remove pulseaudio but it also wants to remove my ubuntustudio-desktop as well so I left it alone.

Any advice would be great.

Edit: So I was able to get sound to work. I reinstalled alsa-utils and rebooted. Not sure why it was acting the way it was but it's fixed. I hear sound on both totem, vlc, mplayer and firefox flash.

---

