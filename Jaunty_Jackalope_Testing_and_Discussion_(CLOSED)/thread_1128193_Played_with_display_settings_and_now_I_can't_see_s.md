---
title: "Played with display settings and now I can't see screen in Gnome"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by poit on 2009-04-17
I did something stupid. It's on Jaunty using Gnome on an old ATI graphics card. (Thinkpad T30)

I've been using Jaunty for about a week now with no problems, so I had to screw it up! I started playing with the display settings and clicked on the rotate display option. The display immediately went blank. Now when I boot up, once I log on I have no display. I've tried the Xorg rebuild option on boot but it doesn't help. I'm sure there is some file I can edit in text mode to fix this, I just don't know where to look. HELP!

Edit: I just installed icewm, which works fine. The problem is definitely in Gnome. And, it works with other logins, so it's definitely an options setting. If only I knew where to look.

Thanks

PS, sorry for the cross-post in general help.

---

### Post by poit on 2009-04-17
Fixed! deleted the ~/.config/monitors.xml file.

---

