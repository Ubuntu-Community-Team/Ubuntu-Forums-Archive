---
title: "Conky in Jaunty Kubuntu"
date: 2009-02-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2009-02-18
I'm not sure if this is a conky problem or a Jaunty problem. I have transferred my conky script from Hardy (Ubuntu) to Jaunty (Kubuntu). Hardy version was 1.51 and the Jaunty version of conky is 1.61. I've never tried conky in Kubuntu so there could be a problem there.
When conky is displayed my background (which is not default) shows up as the grey default splash screen (behind conky - see attached).
Conky was installed from the repos and my display driver is Nvidia 180.29.

---

### Post by Chrisj303 on 2009-02-18
What happens if you killall conky, then restart it?

---

### Post by Kevbert on 2009-02-18
Tried that. Desktop wallpaper covers the whole screen, but as soon as conky is restarted the problem is back again.

---

### Post by Chrisj303 on 2009-02-18
Weird.

I sometimes have conky take a few seconds to update the background when I change wallpapers - but it has never stuck like that. 

It sounds like a Jaunty issue, especailly if it was running fine on your machine with Ibex.

Hope it gets sorted. Don't think I can upgrade without Conky!

---

### Post by Kevbert on 2009-02-18
I'll raise this as a Jaunty bug against the Nvidia package and see what happens. The Nvidia driver caused the x-server to hang and just the grey splash screen was displayed.
Bug is LP #331269.

---

### Post by krazyd on 2009-02-18
This is a known problem with conky and KDE4. It has to do with the 'fake' transparency of conky not working correctly with the composited plasma desktop. For details, see [here]("http://conky.sourceforge.net/faq.html"), question 6.

There are two options to work around this issue. First, similar to the suggestion in the link above, install 'feh' and set it to autostart in KDE systemsettings with: ```
feh --bg-scale /path/to/background_image.jpg
``` I had this going for a while, but basically conky just doesn't fit in with the rest of the plasma desktop. Also, it doesn't work if your background is anything other than 'scaled'.

The other option, which I'm now using, is to have system monitor plasmoids instead of conky. There's even a [STDIN plasmoid]("http://www.kde-look.org/content/show.php/STDIN+Plasmoid?content=92309") now which lets you display the results of any console command. eg. My desktop:
[[img]http://omploader.org/tMTlvNQ[/img]](http://omploader.org/vMTlvNQ)

---

### Post by Kevbert on 2009-02-19
Thanks for that krazyd.

---

