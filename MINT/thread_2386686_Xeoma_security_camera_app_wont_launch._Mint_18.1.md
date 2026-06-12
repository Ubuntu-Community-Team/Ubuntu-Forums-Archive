---
title: "Xeoma security camera app wont launch. Mint 18.1"
date: 2018-03-08
forum: MINT
---

### Post by edward210 on 2018-03-08
I'm testing software for viewing IP cameras and this has me puzzled.

Using Xeoma from here: [http://www.tucows.com/preview/1378229/Xeoma-Video-Surveillance-Software-For-Linux](http://www.tucows.com/preview/1378229/Xeoma-Video-Surveillance-Software-For-Linux)

The instructions state that the xeoma.app file should launch by double-clicking it, but it does nothing.

What would cause this?

---

### Post by monkeybrain20122 on 2018-03-08
Right click > Properties and give it permission to execute, or if you prefer command line

```
chmod +x /path/to/your/file
```

---

### Post by edward210 on 2018-03-08
Under Properties, Permissions, it has all read-write permissions, plus the Execute is checked.
Once it opened an 'Open with what application' dialog.

I chmod +x it also.

Now ignores double-click.   Would it matter that I'm using Mint?

---

### Post by monkeybrain20122 on 2018-03-08
Can you run it in the terminal and post the outputs? Maybe some runtime libraries are missing. Mint is Ubuntu rebranded basically, won't make any difference.

---

### Post by edward210 on 2018-03-08
[FONT=arial]You called it:[/FONT]
/home/ed/Downloads/xeoma.app: error while loading shared libraries: libudev.so.0: cannot open shared object file: No such file or directory

[FONT=arial]Trying: [/FONT][COLOR=#111111][FONT=Consolas][FONT=arial]sudo apt-get install libudev0:i386[/FONT]

[/FONT][/COLOR]E: Unable to locate package libudev0:i386

---

### Post by monkeybrain20122 on 2018-03-08
Well Ubuntu 16.04 doesn't have libudev0, so you have to install libudev1:i386 and that make a symlink to /lib/i386-linux-gnu/libudev.so.1

```
sudo apt install libudev1:i386

sudo ln -s  /lib/i386-linux-gnu/libudev.so.1  /lib/i386-linux-gnu/libudev.so.0

sudo ldconfig

```

Edited: so you are using Mint 18.1, but these should work the same.

---

### Post by edward210 on 2018-03-08
That worked!!!

Thank you So Much.  Thank you So Much.
Thanks for your time.

---

### Post by monkeybrain20122 on 2018-03-08
You are welcome, now please kindly go to thread tools and mark the thread as "solved"

---

### Post by wildmanne39 on 2018-03-08
*Thread moved to **MINT, a more appropriate forum**.*

---

