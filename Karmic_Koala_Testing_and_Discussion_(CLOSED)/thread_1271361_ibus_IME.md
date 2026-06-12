---
title: "ibus IME"
date: 2009-09-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zeimusu on 2009-09-20
I'm not getting much from ibus, the input method in Karmic. Has anyone had sucess? I've installed Japanese Language support, and chosed ibus as the input method. I've added lines to my .bashrc to set up environment variables and I've added the anthy convertion as the default in the ibus settings tool.

On running the settings tool I am told that the ibus daemon isn't running. I start the daemon but after that I don't get anything much. I certainly can't type japanese, I get no sign that pressing the zenkaku/hankaku key is doing anything.

Help please?

---

### Post by Quikee on 2009-09-21
> **zeimusu said:**
> I'm not getting much from ibus, the input method in Karmic. Has anyone had sucess? I've installed Japanese Language support, and chosed ibus as the input method. I've added lines to my .bashrc to set up environment variables and I've added the anthy convertion as the default in the ibus settings tool.

On running the settings tool I am told that the ibus daemon isn't running. I start the daemon but after that I don't get anything much. I certainly can't type japanese, I get no sign that pressing the zenkaku/hankaku key is doing anything.

Help please?

Don't add lines to .bashrc. Use im-switch command instead. It works fine for me.

---

### Post by Longinus00 on 2009-09-21
> **zeimusu said:**
> I'm not getting much from ibus, the input method in Karmic. Has anyone had sucess? I've installed Japanese Language support, and chosed ibus as the input method. I've added lines to my .bashrc to set up environment variables and I've added the anthy convertion as the default in the ibus settings tool.

On running the settings tool I am told that the ibus daemon isn't running. I start the daemon but after that I don't get anything much. I certainly can't type japanese, I get no sign that pressing the zenkaku/hankaku key is doing anything.

Help please?

From the ibus icon in the notification area I can enable and disable languages. Then, by clicking on the icon, I can switch input methods.

---

### Post by cororok on 2009-09-21
Administration -> Language support 
     "keyboard input method system" <---- change it to ibus. 


reboot.

you can see ibus icon on the tray icons

---

### Post by zeimusu on 2009-09-23
> **Quikee said:**
> Don't add lines to .bashrc. Use im-switch command instead. It works fine for me.

Thanks, running im-switch showed the problem: There were old and broken sym-links in my home directory, left over from my Jaunty installation. The system was refusing to overwrite them. Deleting them, and re-running im-switch, got ibus working.:)

---

