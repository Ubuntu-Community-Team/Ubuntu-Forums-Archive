---
title: "Nvidia and Plymouth dont seem to work in sync."
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by praveenthivari on 2010-03-28
I have been noticing this with the nvidia that until u dont install them , the boot screen(Plymouth) seems to show the default screen with those modified fonts and those 5 dots moving across, but on installing them the logo beside the word 'Ubuntu' is gone and the dots are reduced to 4. Even the font rendering and overall quality of that screen decreases. 

How do I overcome this?

Thanks in advance.

---

### Post by jfernyhough on 2010-03-28
You can't yet. The nvidia driver doesn't provide the correct features for Plymouth to work correctly. If you want Plymouth you'll have to use nouveau instead.

---

### Post by praveenthivari on 2010-03-28
> **jfernyhough said:**
> You can't yet. The nvidia driver doesn't provide the correct features for Plymouth to work correctly. If you want Plymouth you'll have to use nouveau instead.

Thanks for the info:p

---

### Post by 23meg on 2010-03-28
> **jfernyhough said:**
> You can't yet. The nvidia driver doesn't provide the correct features for Plymouth to work correctly. If you want Plymouth you'll have to use nouveau instead.

That's not quite correct; Plymouth should work fine with the NVIDIA proprietary driver. It just doesn't do high-color graphics during boot (only VGA and VESA modes are available) or support KMS, since the driver doesn't provide such functionality. The VGA mode currently used should work fine; if it doesn't, you probably have a bug waiting to be filed.

---

