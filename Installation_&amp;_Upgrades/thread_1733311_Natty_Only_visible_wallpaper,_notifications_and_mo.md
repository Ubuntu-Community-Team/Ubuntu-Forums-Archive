---
title: "Natty: Only visible wallpaper, notifications and mouse cursor"
date: 2011-04-19
forum: Installation &amp; Upgrades
---

### Post by jorgenlidholm on 2011-04-19
I'm running Natty on a Dell Precision M65 with a NVidia Quadro FX 350M graphics card.

My problem is that I see no panels or applications, I'm able to start
applications using the run dialog by pressing Alt+F2 and they start,
but I can't see them.

Unity -- Fails
Gnome Classic -- Fails
Gnome Classic (No effects) -- works
Unity-2D -- works

So I guess this is compiz related, I created a new user but it didn't help.
I'm running the nvidia-current 270.41.03 driver.

Any ideas on what the problem is?
Is my graphics card to old and not supported?

/Jörgen

---

### Post by Dutch70 on 2011-04-19
Try other boot options, such as nomodeset.
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

If that doesn't work and you still think it's related to compiz, check the link in my sig. I'ts not specific to the video card listed in the post. It worked wonders with my computer on nearly 10 different distro's.

---

### Post by jorgenlidholm on 2011-04-20
Thank you for your suggestions, unfortunately neither of them
worked. I'm starting to believe that the problem is in
either the nvidia driver or compiz with the current nvidia driver.

I tried both unity and classic gnome with the nouveau driver and
it works, however unity is slightly buggy (the launcher bar 
doesn't hide correctly).

---

### Post by Dutch70 on 2011-04-20
Yeah, Unity is a little buggy, but it is getting a little better everyday. Hopefully they'll have most of it worked out before it's officially released.

---

