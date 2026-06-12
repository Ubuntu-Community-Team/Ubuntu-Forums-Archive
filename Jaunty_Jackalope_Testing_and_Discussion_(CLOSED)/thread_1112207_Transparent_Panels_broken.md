---
title: "Transparent Panels broken?"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kzip on 2009-03-31
Hi,

I've recently upgraded to the Jaunty beta, I used to have my top panel semi-transparent so the wallpaper partly showed through. This worked well on Hardy but in Jaunty only the central section will go transparent, the sections under the "Applications, Places, System" menu and the tray/clock remain solid (which looks odd). Any ideas?

Other than that and the ATI driver issue though everything is working great :)

---

### Post by BGFG on 2009-03-31
Try restarting X. Maybe the relevant daemon hasn't hit it yet.Transparent works here.

---

### Post by kzip on 2009-03-31
This happens every time, even if I reboot etc. I even tried it on the liveCD and it didn't work there either :/ maybe it's something to do with the xserver-xorg-video-ati driver I have to use at the moment (as the FGLRX driver crashes as soon as the GDM loads) I'm on a Thinkpad T60 with the X1300 ATI graphics card.

---

### Post by taavikko on 2009-03-31
Might also be related to theme in use.

some themes don't work very well.
Try using alternate theme, does that help?

---

### Post by kzip on 2009-03-31
Ah ha! Yes that worked. I was using the Shiki-Colours theme (which I love!) and the LiveCD I used was made using remastersys so I that somehow caused the problem to be on the liveCD too (though it was using the default theme when it logged in as the "custom" user).

Cheers, I'll have to either wait for Shiki-Colours to be updated to support Jaunty or use a different theme (any recommendations?)

Thanks again!

---

### Post by taavikko on 2009-03-31
Havent used shiki themes but i'll suspect that gtkrc includes 

include panel.rc

So try commenting it out, that should fix it... For time being...

---

### Post by kzip on 2009-03-31
I've narrowed it down a bit more;

Under Appearance > Theme > Customize > Controls

If I select any of the Shiki entries (Wine/Brave etc) then it breaks the transparency. I'll use one of the default Control setups for now - at least I get to keep the rest of the setup :)

---

