---
title: "Cannot start chmsee on Hardy"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by NoteB on 2008-06-08
Hi, 

i installed chmsee via the synaptics-paket manager and installation was fine. But when in try to start chmsee, nothing happens. In the tray i only see that it trys to open it, but then nothing happens. 

Best regards and thanks for help, 

NoteB

---

### Post by loell on 2008-06-08
it still is buggy, there are workaround for this bug, something like linking mozilla, imho not worth it, if you just like a useful and stable chm viewer,  **xchm** will do.

---

### Post by Partyboi2 on 2008-06-08
Open a terminal (Applications>Accessories>Terminal) and try starting it from there. If you get a message like this:
> chmsee: error while loading shared libraries: libxul.so: cannot open shared object file: No such file or directory
 you will need to create some symlinks
```
sudo ln -s /usr/lib/xulrunner-1.9b5/libxul.so /usr/lib/libxul.so
sudo ln -s /usr/lib/xulrunner-1.9b5/libxpcom.so /usr/lib/libxpcom.so
sudo ln -s /usr/lib/xulrunner-1.9b5/libsqlite3.so /usr/lib/libsqlite3.so
sudo ln -s /usr/lib/xulrunner-1.9b5/libmozjs.so /usr/lib/libmozjs.so

```then after that try starting the program again.
If it is a different message displayed post what it is.

---

### Post by NoteB on 2008-06-09
Hi guys, 

if i try to start chmsee via Terminal, this messages shows up: 

chmsee: symbol lookup error: chmsee: undefined symbol: gtk_moz_embed_set_comp_path


i googled it and yeah .. it is still a bugreport which is not solved yet. 

I installed xchm and this is fine for me!!!

Thanks for your help!!!!

Regards!

---

