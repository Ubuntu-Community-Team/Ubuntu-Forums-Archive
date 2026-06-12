---
title: "LiveCD has no &quot;Reinstall&quot; option"
date: 2017-03-02
forum: Installation &amp; Upgrades
---

### Post by mv55 on 2017-03-02
Hello,

I'm currently daul booting Ubuntu 16.04.02 and Windows 7 and I must have made a mistake somwhere: ive been having a bunch of proformance isues on the Ubuntu side. 

So I booted my liveCD from usb and went to reinstall, but only "erase and install" options are available.

What conditions would cause this, and how can I fix it?

---

### Post by QIII on 2017-03-02
Hello!

What sort of performance issues are you encountering?  Nuking from orbit with a re-install is not likely necessary.

---

### Post by mv55 on 2017-03-02
It's sluggish. Even when booting LibreOffice. It'll have hang-ups when typing. An hour ago, I had a word processor open and 9 chrome tabbs and the thing completely froze, when to a black screen with lines referencing "orphaned nodes" and shut off.

Do you have tips for detecting memory leaks or optimizing system performance?

---

### Post by oldrocker99 on 2017-03-02
How much RAM do you have? Chrome is a memory hog; 9 tabs will use up ~900 MB. This (if you have ~2-4 MB) will cause the swap file to be hit a **LOT**. You can either buy more RAM, or just use Libre Office alone.

---

### Post by mv55 on 2017-03-02
4GB. I'm running a MSI FX603, i5, 4gb ram, 1gb M425 dedicated graphics card: It should be able to handle chrome and office.

---

### Post by ubfan1 on 2017-03-02
You are lucky the option was removed, it didn't work the way people expected (see bug [lpbug]1265192[/lpbug]), and did the "wipe disk and install".  To reinstall, select the "something else", and select the partitions you want to use.

---

### Post by oldos2er on 2017-03-02
> **mv55 said:**
> It's sluggish. Even when booting LibreOffice. It'll have hang-ups when typing. An hour ago, I had a word processor open and 9 chrome tabbs and the thing completely froze, when to a black screen with lines referencing "orphaned nodes" and shut off.

That sounds like a file system issue. I would try running fsck on your system partitions from the LiveCD.

---

