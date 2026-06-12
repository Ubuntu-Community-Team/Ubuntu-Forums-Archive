---
title: "Regression: Can't mouse under notifications"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jrothwell97 on 2010-03-28
Have Lucid installed with all the latest updates as of 15:44 GMT on Sunday.

For the last few days, I've noticed that mousing under notify-osd notifications doesn't work properly any more - they'll still blur and go transparent when I mouse over them, but I can't click or drag beneath them.

I'm using the NVIDIA 96 driver and notify-osd 0.9.27-0ubuntu1.

Is anyone else getting this problem, and if so, is it happening on all hardware configurations or just under the NVIDIA binaries?

---

### Post by Nickedynick on 2010-03-28
Yeah, I'm having the same issue but I've got an ATI card...

---

### Post by jrothwell97 on 2010-03-28
I'd say that's very definitely a bug in notify-osd, then.

I'll check Launchpad, come back with a link to the report.

---

### Post by Sam on 2010-03-28
Ditto here, using Nvidia.

EDIT: Found the bug report: [#546650](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/546650)

---

### Post by jrothwell97 on 2010-03-28
Thanks, Sam. I've marked myself as being affected.

Now let's hope it gets fixed soon, because it's a real pain... :)

---

### Post by Sam on 2010-03-28
It's planned for beta 2.

---

