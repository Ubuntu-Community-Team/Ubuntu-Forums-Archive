---
title: "Feisty and Nvidia problem!"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by zooounds on 2007-04-20
I had an Edgy with custom installed Nvidia glx modules.

Now after the upgrade I wanted to replace the custom installed with the ones you can install with the propreitary driver handler.

I removed the custom installed files with "--uninstall" to the Nvidia installer. After some struggles to get everything to work I ended up disabling the nvidia from the proprietary handlar as well.

Now I cant enable it again! It has dissapeared.Trying to install the drivers from Nvidias hompage also fails...

So now I have no GLX support at all and my scound mointor is black...

what should I do?

---

### Post by eyelessfade on 2007-04-20
try apt-get install nvidia-glx

---

### Post by zooounds on 2007-04-20
Of course I have tried that onw. But it doesn't work.

This Feisty upgrade seems more and more an misstake.

---

### Post by zooounds on 2007-04-20
A total reinstall of all restricted modules packages and the restricted driver handler and it worked. Puh :)

---

