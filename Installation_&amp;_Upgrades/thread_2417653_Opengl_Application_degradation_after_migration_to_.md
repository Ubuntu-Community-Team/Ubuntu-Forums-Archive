---
title: "Opengl Application degradation after migration to Disco"
date: 2019-04-25
forum: Installation &amp; Upgrades
---

### Post by fulezi on 2019-04-25
Hi everyone,

I was working on an OpenGL application that were working well, while it has been asked to me to migrate to Ubuntu 19 (disco). I accepted and the migration went to the end.
However, since that the OpenGL application does not display correctly anymore. In addition it start to freeze after some inputs from the keyboard or the mouse and finally exit with an error on the console:

```
    i965: Failed to submit batchbuffer: Input/output error
```

This error message was not present previously (on the exact same hardware and code-base).
I've tried with a simple GLFW and it does not work with an OpenGL version > 3.0 (while the graphic card can accept 4.5)

I've a HP ENVY 13-d023nf with an integrated chipset GPU HD 520.
Here is my glxinfo: [https://paste.ubuntu.com/p/yxYpmZg5Qt/](https://paste.ubuntu.com/p/yxYpmZg5Qt/)

Any idea what I can check?

Thanks,
Florian

---

### Post by fulezi on 2019-05-02
After a fresh install of Ubuntu 19 Disco Dingo, I've still the same issue. I've also noticed that VLC can't play a video (the image is broken).
So I reverted to Ubuntu 18.04.2, it works... On Ubuntu 18.

Do you know where I could report this issue?

Thanks,
Florian

---

### Post by wildmanne39 on 2019-05-02
Hello, here is a link to how you can report a bug and the procedure to do so.

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

