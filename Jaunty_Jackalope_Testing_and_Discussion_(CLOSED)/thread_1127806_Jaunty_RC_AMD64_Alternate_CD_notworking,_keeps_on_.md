---
title: "Jaunty RC AMD64 Alternate CD notworking, keeps on asking for valid mirror..."
date: 2009-04-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hotweiss on 2009-04-16
I just tried the Jaunty RC AMD64 alternate CD, and had little success getting past the mirror step. It keeps on asking me to choose a valid mirror - I've tried 30 with no luck. Does any one have a solution for this?

---

### Post by hotweiss on 2009-04-17
Is it me who just has this problem?

---

### Post by SketchyClown on 2009-04-17
If the install CD set up DHCP successfully during setup it should be able to set up the update mirror. I have never had it ask me for a "valid mirror" before. Very odd indeed.

This is not really a big deal if you cannot get past this part.

Just unplug your ethernet and select "do not configure DHCP at this time" and then it will skip setting up the mirror during the install. When the installation completes, you can plug it back in and manually select your mirror in **Software Sources** after you boot into Gnome.

HTH.

---

### Post by hotweiss on 2009-04-17
...but I did not configure DHCP. Do you think it has something to do with the fact that I used unetbootin to run the image of a USB stick?

---

### Post by SketchyClown on 2009-04-18
> **hotweiss said:**
> ...but I did not configure DHCP. Do you think it has something to do with the fact that I used unetbootin to run the image of a USB stick?

I suppose thats possible. You didn't mention that in your initial post.

---

