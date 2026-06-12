---
title: "White Frame"
date: 2010-01-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tad1073 on 2010-01-12
anybody notice a white frame around the edge of the desktop, or is it just me?

---

### Post by Vanishing on 2010-01-12
> **tad1073 said:**
> anybody notice a white frame around the edge of the desktop, or is it just me?

Sometime I have it too, it has something to do with nautilus.
If you go :
> sudo killall nautilus
it will be gone..

---

### Post by MacUntu on 2010-01-12
Is this reported yet? No bug report, no fix. I'm seeing this too, but credit where credit is due. :P

---

### Post by tad1073 on 2010-01-12
> **Vanishing said:**
> Sometime I have it too, it has something to do with nautilus.
If you go :

it will be gone..

thanks, that fixed it

---

### Post by mdurham on 2010-01-13
> **tad1073 said:**
> thanks, that fixed it

For me it didn't, it reappears after a while.

---

### Post by hugmenot on 2010-01-13
> **Vanishing said:**
> > sudo killall nautilus

Why sudo killall? nautilus -q works too.

I happens here when I rename a file on the desktop.

---

### Post by taavikko on 2010-01-13
> **hugmenot said:**
> 
I happens here when I rename a file on the desktop.

Here when connecting external monitor and using display-properties.
Edit: creating a folder on desktop will trigger this one also.

anyone filed a bug on this one yet?

---

### Post by VMC on 2010-01-13
Were talking about, for example using Nautilus to create a folder then the "white screen" appears?

I just created a folder on desktop using Nautilus (Nautilus 2.29.1), and no "white screen". Wonder it its hardware related. I'm using integrated Intel i865 video.

---

### Post by taavikko on 2010-01-13
> **VMC said:**
> 
I just created a folder on desktop using Nautilus (Nautilus 2.29.1), and no "white screen". Wonder it its hardware related. I'm using integrated Intel i865 video.

Right click on desktop -->> create folder

Radeon HD3450

---

### Post by tad1073 on 2010-01-13
> **VMC said:**
> Were talking about, for example using Nautilus to create a folder then the "white screen" appears?

I just created a folder on desktop using Nautilus (Nautilus 2.29.1), and no "white screen". Wonder it its hardware related. I'm using integrated Intel i865 video.

It is not a white screen, it is a white frame around the boarder of the screen.

---

### Post by zika on 2010-01-13
In my case this happens when doing upgrade, Terminal window (in which I'm doing upgrade) goes dimmer and white frame occurs on left side of my screen (rotated to the left (90 degrees)). It goes away if I kill nautilus. It doesn't happen always, just when upgrade works with fonts or something similar.

---

### Post by Jordanwb on 2010-01-13
> **VMC said:**
> Were talking about, for example using Nautilus to create a folder then the "white screen" appears?

Also when renaming a folder.

> **VMC said:**
> I just created a folder on desktop using Nautilus (Nautilus 2.29.1), and no "white screen". Wonder it its hardware related. I'm using integrated Intel i865 video.

I have a Radeon x1200 in my laptop and this occurs.

---

### Post by jfernyhough on 2010-01-13
Same on Nvidia 9600GT (195.30 beta).

---

### Post by VMC on 2010-01-13
Ok, I don't have a "white border" around anything, but as mentioned above when I use a terminal to do updates that screen goes reverse video with green lettering. Unrelated but I think it still has to do with video chip. Unless someone comes along with an Intel i865 and has the "white border".

I tried creating this all kinds of ways without problems.

---

### Post by mc4man on 2010-01-13
definitely shows up on nvidia, though if I extend the desktop a few pixels horizontly then don't notice.
( changing themes will also create the lines, it's as if the desktop 'shrinks' slightly and the lines appear.

much easier to see with a dark background, choosing thru a few, this one shows fairly well

---

### Post by MacUntu on 2010-01-13
> **VMC said:**
> I don't have a "white border" around anything

You aren't using a CRT monitor by any chance, are you? The border is only 1px so it could be off-screen.

---

### Post by MacUntu on 2010-01-13
Well, someone had to do it:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/507263](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/507263)

Please confirm and do a "This bug affects you". Thanks!

---

### Post by dagrump on 2010-01-13
I confirmed it also, but I only made 3. I can recreate it on a laptop w/ intel 945 & nvidia w/ the current drivers. I use a plain grey background, so it's fairly noticeable.

---

### Post by VMC on 2010-01-13
> **MacUntu said:**
> You aren't using a CRT monitor by any chance, are you? The border is only 1px so it could be off-screen.

Ok, now I get it. I think I now get it because I turned on visual effects. mac's screenshot gave me a hint. 

Now to go and "effects me too"...

---

### Post by angularsofty on 2010-01-18
Interesting... For me, the border thickness changes depending on what GTK widget theme I have selected. Amaranth is 2 pixels & white, Clearlooks is 1 pixel & blue, etc. With the Elementary theme, the left & right borders are 8 pixels -- the screenshot attached is my desktop's lower-right corner using Elementary, including the corner of a nautilus browser window showing the same 8px right border.

---

### Post by Rallg on 2010-02-10
The border happens on my Asus EEE 1005HA, after I do something such as create a new document or folder. Once it appears, it usually remains. I have not noticed any difficulties. At first, I thought maybe it was a new decorative feature that didn't appear at initial login.

Not sure if the frame is really white. It might be the same light gray color as my Gnome panel.

---

### Post by DanRabbit on 2010-02-14
If anyone finds what is causing it in the theme, please let me know. I'll be looking into the problem seeing as my theme has one of the worst results for some reason.

---

