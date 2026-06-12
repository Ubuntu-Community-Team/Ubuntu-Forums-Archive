---
title: "Low screen resolution after update in 22.04"
date: 2022-12-09
forum: Installation &amp; Upgrades
---

### Post by iconoklastic on 2022-12-09
I have been using 22.04 for months after upgrading the OS from 20.04. at 2560x1440. Following yesterday's update, however, the screen came up in 1024x768 and could not be changed. Since I have an Nvidia card (GTX970), I suppose the driver is no longer properly installed and a vesa mode is being used. I rolled the system back to a pre-update state for now, but would like to solve this problem, since it will probably preclude updates until I do. Does anyone have advice for getting a suitable driver properly installed?

---

### Post by TheFu on 2022-12-09
Did you try just reinstalling the driver, post-update?
I have to do that with nvidia drivers for my 1030GT a few times every year.

Have to say, the system with an AMD GPU never has this issue.

---

### Post by MAFoElffen on 2022-12-10
+1... At least a few times a year with my NVidia drivers. It's become expected and second nature to reinstall them.

With Intel and AMD GPU's... Both are now opensource and provide their source to kernel. So every time their is a kernel update, the GPU drivers get updated. NVidia is still closed third-party source. It  got better with dkms, but still hickups some times.

---

