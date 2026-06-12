---
title: "Autoinstall include big files"
date: 2023-05-26
forum: Installation &amp; Upgrades
---

### Post by benibunny on 2023-05-26
I have successfully configured autoinstall. Now I would like to include some files and chown chmod them in the late commands. 

I have tried many many variants of the write_files vaiable, but the files were never written. Logfiles said 'skipping modules ... , write_files, ... ‘
Now I tried 'echo content > filename' but this only works for small files. For a 600kb file I end up with the error 'argument list too long'.

What is the way to write a file during autoinstall?
Kind regards

---

### Post by TheFu on 2023-05-26
Might help if you included which OS and version?

We use **ansible** post-install to configure most things and keep the initial install really trivial ... with just 1 deployment account and ssh. If you are shipping systems to disconnected locations, ansible won't work ... well, not very well, though you can run it locally.  Doing that sorta defeats the reason for using a DevOPS tool, right?

---

### Post by benibunny on 2023-05-27
I am using Ubuntu Server 22.04

Maybe also runcmd is an option (if it works)

---

### Post by benibunny on 2023-05-29
I do everything with runcmd now. whoever might come across this thread in the future: don't waste time with write_files in an autoinstall context.

[FONT=courier new]  user-data:[/FONT]
[FONT=courier new]    runcmd:[/FONT]
[FONT=courier new]      - echo "let's get the party going"[/FONT]

---

