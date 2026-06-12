---
title: "Ubiquity Crashes, cannot install."
date: 2009-04-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by yugge on 2009-04-19
So I thought I'd give the new Jaunty a spin. Fired up the livecd and hit install. Nothing happends (well, except the system recognizing it as a crash and told me ubiquity had crashed). I then tried to run it from command line for some more information about the crash and this is the output:
```
ubuntu@ubuntu:~$ ubiquity --desktop %k gtk_ui
Traceback (most recent call last):  File "/usr/bin/ubiquity", line 132, in <module>
    main()
  File "/usr/bin/ubiquity", line 39, in main
    if osextras.find_on_path('hal-lock'):
AttributeError: 'module' object has no attribute 'find_on_path'

```

So, what would be the easiest way for me to proceed?

---

### Post by markbuntu on 2009-04-19
Check the disk for errors?

---

