---
title: "Places open with firefox"
date: 2008-08-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by shafin on 2008-08-28
Under the Places menu,whenever I click on Home, Desktop, on my favorite folders or on a Drive, it opens in firefox instead of in nautilus. Only Computer icon opens Nautilus. 

How can I fix this?
Thanks in advance.

---

### Post by ubulette on 2008-08-28
Right click on any directory in Nautilus, select "Open With", what do you see?

It should be "Open Folder" to have nautilus. If you see Firefox or a browser, something set that for you.

---

### Post by shafin on 2008-08-30
Yeah, That was the problem .Thanks.

Now another minor inconvenience. When I enter one of my drives, Nautilus keeps showing "These files are on a Picture CD" along with a button to open F-spot photo manager, even if the drive is a hard drive and not a picture CD. I can find no way to remove this notification. I want to be able to use this feature on a CD,but I want a way to remove it from that drive. 

Thanks in advance.

---

### Post by cjchand on 2008-10-20
> **ubulette said:**
> Right click on any directory in Nautilus, select "Open With", what do you see?

It should be "Open Folder" to have nautilus. If you see Firefox or a browser, something set that for you.

Thanks for the pointer. Simple, yet hard to find at the same time ;)

One bit of clarification in my instance (8.10 beta): I had to do the following to make the suggested change:
[LIST=1]
[*]As mentioned by ubulette, open Nautilus (by clicking Places -> Computer, for example) and navigate to any folder
[*]There was no "Open With..." in my menu, so I chose Properties.
[*]In the Properties dialog, click the "Open With" tab and select "Open Folder" (instead of Firefox)
[/LIST]

Hope that helps someone in the future :)

Cheers,
CJC

---

### Post by cjchand on 2008-10-20
> **shafin said:**
> Yeah, That was the problem .Thanks.

Now another minor inconvenience. When I enter one of my drives, Nautilus keeps showing "These files are on a Picture CD" along with a button to open F-spot photo manager, even if the drive is a hard drive and not a picture CD. I can find no way to remove this notification. I want to be able to use this feature on a CD,but I want a way to remove it from that drive. 

Thanks in advance.

My understanding is that Nautilus will scan the media (drive, CD, etc) for any media (pictures, MP3s, etc) and pop up a dialog asking if you want to run the default application for that media type.

This is controlled by the "Browse media when inserted" checkbox in the following location in Nautilus: Edit -> Preferences -> Media. 

If you're getting the "Picture CD" prompt, it is likely that there is a picture of some sort on that drive - not necessarily that Ubuntu thinks it's a Picture CD.

Unfortunately, I am not aware of a way to selectively apply this to different media types (e.g.: scan CDs but not hard drives). I believe it is an "all-or-nothing" situation. 

Keep in mind I'm an Ubuntu n00b, so hopefully my post will pull a more seasoned veteran out of the woodwork to find you a solution ;)

Cheers,
CJC

---

