---
title: "Recent kernel update failed"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mister_pink on 2008-10-11
This morning I updated to 2.6.27-7. However the installation doesn't seem to have worked properly, and it's only just now that I understand why.

I was having trouble with the previous kernel that meant only / was being mounted on boot. The new kernel couldn't install properly as /boot wasn't mounted.

However now I have mounted and tried to do a dpkg --configure, and get the following:
```

Setting up linux-image-2.6.27-7-generic (2.6.27-7.10) ...
Internal Error: Could not find image (/boot/vmlinuz-2.6.27-7-generic)
dpkg: error processing linux-image-2.6.27-7-generic (--configure):
 subprocess post-installation script returned error exit status 2

```

Suggestions on how to get it to do this properly would be much appreciated.

Edit: Got bored and decided that doing it "properly" is overrated, so I just removed it and installed it again (--reinstall didn't work) along with a load of other kernel stuff that it wanted to remove. Seems to have fixed it. Guess this thread is pretty pointless now.....

---

