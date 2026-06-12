---
title: "Manual connect in network manager?"
date: 2008-09-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bubba_169 on 2008-09-22
Im enjoying my time with intrepid overall but I have a few annoyances :( The main one, hence the post title is that network manager will no longer auto connect to my hidden network on sign in. Pre-Intrepid, I used to turn off roaming and use a manual connection to auto-connect but I can't find any way to do this in Intrepid. My network works fine once I connect through "Connect to other wireless network" and it seems to remember the SSID as it shows in the list, just it wont connect without me telling it to?

Any ideas on this? Its not a major problem but is annoying having to reconnect every time... Perhaps installing another package to replace the "manual" connection mode in Hardy?

---

### Post by jackocleebrown on 2008-09-22
Does network manager remember the network keys correctly? I have to manually put mine in everytime! v.annoying. It does auto connect to networks that I have used before. There are some pretty comprehensive settings if you right click on the icon and choose "edit connections" I believe that there is an "auto" setting there that might help you.

---

### Post by bubba_169 on 2008-09-22
I have tried playing with every setting (including those and taking all security off) I can find but no luck. Right now Im looking at writing a shell script to run at startup that uses iwconfig and dhclient to set up my wireless and using the network monitor applet for the gnome panel to watch over it? Seems to work so far and might work as a temporary fix in hope this gets some attention before intrepids final release :-|

---

### Post by Nullack on 2008-09-22
> **bubba_169 said:**
> I have tried playing with every setting (including those and taking all security off) I can find but no luck. Right now Im looking at writing a shell script to run at startup that uses iwconfig and dhclient to set up my wireless and using the network monitor applet for the gnome panel to watch over it? Seems to work so far and might work as a temporary fix in hope this gets some attention before intrepids final release :-|

You can help ensure it "gets attention" by contributing to the bug process :)

---

