---
title: "Problem with installation of OpenGL"
date: 2012-11-09
forum: Installation &amp; Upgrades
---

### Post by PinkPanther1 on 2012-11-09
Hi everybody!

I'm new here so I hope my post follows the guidelines that you have here; if not, please let me know and I'll fix it...

So I am experiencing a problem that I do not seem to find a solution on any other forum. The following is happening:
I am using Linux on a virtual box, I'm using Ubuntu 12.04.1.
I got the OS from a friend who is attending a lecture that uses the same distribution. I want to use it more or less only to learn to code a bit.
So I started to learn c++, which worked just fine, until I decided that I wanted to get into game programming. Now the "weird" stuff started. I first searched for some libraries, which I found (for example allegro, sdl).

I tried to install/download them via apt-get. First I got allegro, which wanted me to use the cmaker command to be able to install some stuff. I had to download cmaker for that and then I tried running the command, which then gave me an error message that I do not have OpenGL installed. So I tried installing that.
Now this as well as the SDL library afterwards got the same error(s):

Depends: libglu1-mesa (= 8.0.2-0ubuntu3) but 8.0.3+8.0.2-0ubuntu3.2 is to be installed
                    Depends: libgl1-mesa-dev but it is not going to be installed or
                             libgl-dev
 libsdl1.2-dev : Depends: libsdl1.2debian (= 1.2.14-6.4ubuntu3) but it is not going to be installed
                 Depends: libasound2-dev
                 Depends: libpulse-dev but it is not going to be installed
                 Depends: libcaca-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I am unsure whether it was always the same file that was not able to install, but it was always an error containing the 8.0.3+8.0.2 Oubuntu thing. Also, it always had to do with other libraries, although not the same ones. For the sdl, you see the error above, for the allegro, the error was with the Freeglust library. I tried downloading things first and then installing them, which did not work either, giving me the same error message.

I did not find any solution to that problem on any other website and I am kind of desperate right now, since I would really like to be able to do something, but can't since I don't know how to solve that error. I don't need a solution for both allegro and sdl, but to get at least one of them working would be great.

I have this OS for about 2 months now, and I did never update it or anything.

Does anybody have an idea on how to solve this? I'd greatly appreciate it!
Thanks for reading everything, I am sorry I wrote that much....

---

### Post by dannyboy79 on 2012-11-09
first and foremost make sure you're all updated.

```
sudo apt-get update && apt-get upgrade
```

---

### Post by PinkPanther1 on 2012-11-09
Wow, thanks for the fast reply!
I updated everything, but I get still the exact same error. The updates seemed to be running fine, did not get any error messages at least.

---

