---
title: "Supertux in Karmic 32bit"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by running_rabbit07 on 2009-12-04
I have tried three times to install Supertux and it will not properly install. It shows as being installed in Synaptic and there is a launcher in the Games menu, but the icon doesn't show up right. When I click to launch the game it starts then immediately stops. I just had it installed in Jaunty on the same machine with no issues. Also, the other games I installed appear to be working fine. Here are the results of trying to start the game via terminal;```
sarah@sarah-desktop:~$ supertux
Datadir: /usr/share/games/supertux
Warning: Unable to open the file "/home/sarah/.supertux/config" for read!!!
Warning: No joysticks are available.
Segmentation fault
sarah@sarah-desktop:~$
``` In Jaunty I had no problems with the lack of a joystick.

Has anyone else had this problem? Does anyone know how to fix this. 

Thanks all for any help. My daughter will be grateful.

---

### Post by running_rabbit07 on 2009-12-07
Can anyone help me with this? Thanks.

---

### Post by presence1960 on 2009-12-07
running_rabbit I installed it via synaptic in 64 bit 9.10. It works fine without a joystick. Maybe mark for complete removal, then remove .supertux2 config directory from /home. Reinstall.

---

### Post by running_rabbit07 on 2009-12-07
Supertux2 works fine. It is the supertux-stable that refuses to work. I have tried uninstalling and deleting all related hidden files and folders, but it still doesn't work. I am not sure if it has to do with Karmic 32. I did do the kernel upgrade this morning, so I'll give it another try and see if that had anything to do with it. Thanks for replying.

---

### Post by JBAlaska on 2009-12-07
Try creating a supertux-config file, these contents may work:
```
(supertux-config
;; the following options can be set to #t or #f:
(fullscreen #t)
(sound #t)
(music #t)
(show_fps #t)

;; either "opengl" or "sdl"
(video "opengl")

;; joystick number (-1 means no joystick):
(joystick -1)
(joystick-x 0)
(joystick-y 1)
(joystick-a 0)
(joystick-b 1)
(joystick-start 2)
(joystick-deadzone 4096)
(keyboard-jump 273)
(keyboard-duck 274)
(keyboard-left 276)
(keyboard-right 275)
(keyboard-fire 306)
) 
```

---

### Post by derrick81787 on 2010-03-20
supertux segfaults when it uses SDL, which is the default.  If you run it as **supertux --opengl**, then it will work fine.

- Derrick

---

