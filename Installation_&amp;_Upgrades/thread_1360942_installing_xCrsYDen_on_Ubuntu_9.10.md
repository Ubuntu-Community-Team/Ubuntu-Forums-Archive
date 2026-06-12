---
title: "installing xCrsYDen on Ubuntu 9.10"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by didntpickaname on 2009-12-21
Hi,

I am really absolute beginner to Ubuntu. I have been using ubuntu for academic purposes for 2 years. But, since i have changed my computer i couldn't run the Xcrysden. I need your help.

I have been using a laptop with Nvidia 8800M GS graphic accelerator. My OS was Ubuntu 8.10 and Xcrsyden didnt even crash for once.

Now i have a desktop with ATI HD 5850 and I installed Ubuntu 9.10. But now i couldnt install the Xcrsyden. I have extracted the files that i downloaded from its website and i double-clicked the xcrysden file to open the program and clicked 'run' in new window; but nothing happened. It was the way i use the program when i was using my laptop. Since i am totally newbie, i dont know what else to do.

So, please I need your help! I must see the atomic structures with this program, that i have been creating on Octave . I can't use any other software such as Pymol or Xmakemol.

Please show me a way how to install xCrsyden properly.

Thanks...

---

### Post by dannyx on 2010-04-01
I have the same problem. Couldn't run xcryden either for binary or source one. 
I ran xcrysden from terminal window and it just flashed up and then disappeared no error or warning message. Just don't work. 
Any idea?

---

### Post by dannyx on 2010-05-28
Hi, 
I solved the problem. 
What I did was:

I compiled Xcrysden from source code

1. I went to terminal window type in

```
xcryden -d 
```and found that my problem was with libGL.so
so I go to synaptic and mark to install libgl1-mesa-swx11-i686. By that the package libgl1-mesa-glx would be replaced by libgl1-mesa-swx11-i686. 

After that I editted Make.sys

add the line
```
-L/usr/lib/mesa 
```into
```
X_lib = 
```go to terminal 
```

make clean
make all

```Try it and see if you solve the problem. If not send us the result of 

```
xcryden -d
```

---

