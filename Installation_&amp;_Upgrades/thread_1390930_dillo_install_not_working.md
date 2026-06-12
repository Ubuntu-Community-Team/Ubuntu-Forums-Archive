---
title: "dillo install not working"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by bdws1975 on 2010-01-26
hi all,

tried to install dillo with the following command
 and keep getting the lines in the attached screenshot.  Any ideas?

thanks,
Brett
sudo apt-get update && sudo apt-get install dillo

---

### Post by Sef on 2010-01-26
Try going to the [packages repository]("http://packages.ubuntu.com") and installing what you need by command line.

---

### Post by bdws1975 on 2010-01-26
> **Sef said:**
> Try going to the [packages repository]("http://packages.ubuntu.com") and installing what you need by command line.

Thanks, but I didn't see anything for dillo the web browser.

any other ideas?  Or did I do it wrong?  I'm new but want to learn to use the force (command line)

thanks,
Brett

---

### Post by bdws1975 on 2010-01-26
Got it!!!!!!!!!!!!!!!!!!!!!!!!!!  I was adding the wrong source .

thanks!

brett

---

### Post by ameyo on 2011-03-25
In case anyone (like me) is wondering what source he's talking about...

* Karmic is the release I'm using, so google search for site: packages.ubuntu.com dillo karmic
  * That leads to [http://packages.ubuntu.com/search?keywords=dillo](http://packages.ubuntu.com/search?keywords=dillo)
*   Click "*hardy*" at the top left (as it's the latest release mentioned), which leads to [http://packages.ubuntu.com/hardy/dillo](http://packages.ubuntu.com/hardy/dillo)
*   Click i386 at the bottom left under the "*Download dillo section*", which leads to [http://packages.ubuntu.com/hardy/i386/dillo/download](http://packages.ubuntu.com/hardy/i386/dillo/download)
*   If I try to download and install it manually (by double clicking it), it tells me I'm missing some dependencies (libgtk1.2), so it would be easier to let synaptic install it and sort out the dependencies. The page tells you to add *deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) hardy main universe* to your /etc/apt/sources.list file. 
*   Back up /etc/apt/sources.list then add that line to is, and then run *sudo aupt-get update*
*   Load synaptic and search for dillo and you will now see it in the list and you can install it (or run sudo apt-get install dillo)

tl:dr - add *deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) hardy main universe* to your /etc/apt/sources.list file. You can replace *[ubuntu.mirror.cambrium.nl/ubuntu/]("http://ubuntu.mirror.cambrium.nl/ubuntu/") with any other mirror listed at *[http://packages.ubuntu.com/hardy/i386/dillo/download](http://packages.ubuntu.com/hardy/i386/dillo/download)

---

### Post by Jamina1 on 2011-04-04
> **ameyo said:**
> In case anyone (like me) is wondering what source he's talking about...

tl:dr - add *deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) hardy main universe* to your /etc/apt/sources.list file. You can replace *[ubuntu.mirror.cambrium.nl/ubuntu/]("http://ubuntu.mirror.cambrium.nl/ubuntu/") with any other mirror listed at *[http://packages.ubuntu.com/hardy/i386/dillo/download](http://packages.ubuntu.com/hardy/i386/dillo/download)

Thank you for being thorough, I HATE replies like "I figured it out" with no extrapolation.

---

