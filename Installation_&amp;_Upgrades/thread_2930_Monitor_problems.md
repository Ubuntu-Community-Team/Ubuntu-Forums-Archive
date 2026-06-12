---
title: "Monitor problems"
date: 2004-11-01
forum: Installation &amp; Upgrades
---

### Post by PaulaDawn on 2004-11-01
I have managed to intall Ubantu, but when I get to the log on screen there is like four of them and the enter user name and password is REALLY small and there are four of them as well. 
What is going on? I am trying to install on an older computer for my kids. 
It only has 62RAM and I am not to sure what else. 
Any ideas?
Thanks

---

### Post by FLeiXiuS on 2004-11-01
[QUOTE=PaulaDawn]I have managed to intall Ubantu, but when I get to the log on screen there is like four of them and the enter user name and password is REALLY small and there are four of them as well. 
What is going on? I am trying to install on an older computer for my kids. 
It only has 62RAM and I am not to sure what else. 
Any ideas?
Thanks[/QUOTE]

This sounds really bizar.  Open up a terminal:

Then from there you would want to edit your /etc/X11/X86Config-4 with your favorite text editor..
```

sudo $EDITOR /etc/X11/X86Config-4

```

Then paste back the config.

---

### Post by PaulaDawn on 2004-11-02
[QUOTE=FLeiXiuS]This sounds really bizar.  Open up a terminal:

Then from there you would want to edit your /etc/X11/X86Config-4 with your favorite text editor..
```

sudo $EDITOR /etc/X11/X86Config-4

```

Then paste back the config.[/QUOTE]
 Thanks I hope this works, I hate the kids using my computer.

---

### Post by FLeiXiuS on 2004-11-02
you will have to change '$EDITOR' to your favorite text editor.  

Example: 
-vi
-gedit
-pico
-namo

---

