---
title: "problem with sdl and ffmpeg"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by jann364 on 2010-02-03
hi...
i am beginner in ubuntu. i wish to run the programs that will display a picture which use the ffmpeg,sdl and lame.. when i type*** gcc -o exercise exercise1.c 'sdl-config --cflags --libs' ***to compile the program it give this such of error :gcc: sdl-config --cflags --libs: No such file or directory. I have installed the gcc packages, SDL ,FFMPEG, LAME but still cannot display the output. any one can help with this problems?? what should i do with the gcc packages? 
thank you..

---

### Post by drurowin on 2011-03-15
> **jann364 said:**
> when i type*** gcc -o exercise exercise1.c 'sdl-config --cflags --libs' ***to compile the program it give this such of error :gcc: sdl-config --cflags --libs: No such file or directory.

Make sure you're using backticks ` (next to "1" on most keyboards). Those will execute the command inside them. What you did is single-quoted the string, which treats everything inside it as a literal filename.

$ **gcc -o exercise exercise1.c `sdl-config --cflags --libs`**

---

