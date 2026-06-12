---
title: "Xubuntu 14.04 freeze/hangs/borks at grub screen during boot (photos)"
date: 2014-09-03
forum: Installation &amp; Upgrades
---

### Post by finny388 on 2014-09-03
Screen borks at grub2.
I just set up a crappy Asus X55U laptop (was a gift) for my niece for school using Xubuntu 14.04 with open source drivers. (Win8 was a joke)

I had initially used proprietary graphics drivers but on occasion screen would distort and be unresponsive after a login. Didn't happen with the OS drivers so I went with them.  (AMD 7290m) (from addit. drivers in Settings)
I used this laptop and rebooted many times to run it through paces to 'ensure' stability and it appeared to be rock solid. I handed it over to her two days ago and when we booted it was fine.

She powered it down last night and upon powering up today she gets these screens and it doesn't respond to keystrokes. The last image is a custom image I set up with Grub Customizer (it is supposed to be black background with white graphic)
The screen actually looks physically torn but it just the image on the screen.

Are the graphic drivers here the prime suspect or could it be grub, or other? She lives an hour and half away. I'm not sure how soon I can get to it.

[IMG]http://i.imgur.com/rBFjr8n.jpg[/IMG]
[IMG]http://i.imgur.com/eO1Pvup.jpg[/IMG]
[IMG]http://i.imgur.com/YSRPbz5.jpg[/IMG]

---

### Post by moore.bryan on 2014-09-03
My wife got similar looking visual artifacts after dropping the laptop and cracking the screen... I know that's out-there, but maybe?

---

### Post by QIII on 2014-09-03
Hello!

At that point the graphics driver would not even have been loaded.

That looks like a hardware issue to me.

---

### Post by finny388 on 2014-09-03
Good points
She insists she didn't hurt/drop it (but something could have happened; there's pets and she may not be admitting it)

But, yeah, it occurred to me (after posting) this was before drivers would even load

Could it be the grub image? ... but it worked before.

What can I really try? If it's hardware, dust blowing, would removing and re-inserting battery do anything?

---

### Post by moore.bryan on 2014-09-04
If she has access to another computer, she could burn a livecd to usb and see if that works; that, at least, would identify if it's an install issue...

---

