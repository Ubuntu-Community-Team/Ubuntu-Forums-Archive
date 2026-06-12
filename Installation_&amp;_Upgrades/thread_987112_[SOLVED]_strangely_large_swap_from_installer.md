---
title: "[SOLVED] strangely large swap from installer"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by ahumin on 2008-11-19
the ubuntu hardy 8.04.1 64bit installer set my swap at 5.75GB!! i only have 2 GB of ram. why is the swap so big to begin with? how could i need so much space? will resizing it from a live cd also shrink the extended partition it's contained in so i can reclaim the space?

---

### Post by Elfy on 2008-11-19
No you would need to resize the swap and then the extended partition as 2 seperate tasks.

If though there is only swap in the extended you could do it without booting the livecd.

---

### Post by DieB on 2008-11-19
you also can use swappoff and use gparted from your normal machine to make your swap smaller. for making the other one bigger you still need a live cd.

---

### Post by Elfy on 2008-11-19
only if the / isn't in the extended partition :)

---

### Post by ahumin on 2008-11-20
thanks all, i just booted up with the ubuntu live cd and used gparted from there. i still had to use swapoff, strange, i didn't expect a live cd would utilise an existing swap. my ubuntu install is on a primary, which i shrunk so i can install another os between it and the extended partition with the swap.

also, i resized the swap first then the extended partition, which left a little empty space preceding the swap (inside the extended). so i resized the swap again to fill it.

---

