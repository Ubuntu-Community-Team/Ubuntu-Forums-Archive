---
title: "Ubuntu total confusion"
date: 2023-02-19
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2023-02-19
Ubuntu has so many types.
Ubuntu
Kubuntu
Xubuntu
Lubuntu
Ubuntu Mate
Ubuntu Budgie
Ubuntu Studio
Ubuntu Kylin
witch one is the best to use for programming ??
The mostly use so one can google to get answer to questions ??
Thanks

---

### Post by ajgreeny on 2023-02-19
See the thread at  [https://ubuntuforums.org/showthread.php?t=2415676](https://ubuntuforums.org/showthread.php?t=2415676) lots more information about those different desktop environment (DE) versions.

There is no one single answer for you as different users prefer different desktops but underneath, they all use the same basics and you can install any of the available pacages in any and all of those different versions.

---

### Post by MAFoElffen on 2023-02-19
+1

For me, I install Ubuntu, then 2 Desktops... Ubuntu has more than i need to do whatever I need as a base platform. The DE's I use are Gnome Sessions and i3. From day to day, I use Gnome Sessions. When I'm doing a project, I use i3. While I'm programming, it just easier for me to change workspaces in i3 and organize it how I want or need it to be. And i can easily customize hot-keys to get back and forth between things I do. I can customize macro's to take care of repetitive tasks.

The first question you want to ask yourself, is what do you do and what do you need? Programming (coding) is advanced text editing. From there, do you need to compile or use an interpreter? When testing, what do you need to run and debug what you have written? And how easy is it to switch between? (Testing and changing the code when you find something that needs changing.)

Linux makes that all easy, because you can mix and match 'pieces' you want and need, to do what you want.

Whether that is for Java, Javascript, HTML5/CSS3, C, C++, C#, Perl, Python, BASH, etc, etc, etc.

For what I do, I do most of my testing on KVM Virtual Machines first, so that I can vary the OS'es, and the hardware platforms.

For me, requirements change, but Linux makes it easy to be flexible and adaptable.

---

### Post by Impavidus on 2023-02-19
You can program in any of them. It doesn't really matter.

Now, if you like making programs that use a particular framework, it may be best to use a flavour with the same. So, if you like programming KDE stuff, Kubuntu may be best; if you like programming gnome stuff, Ubuntu; Qt stuff, Kubuntu or Lubuntu; etc. If you like using a particular IDE (but note that many programmers on Linux have never touched one), you may want a matching flavour. So Kubuntu or Lubuntu if it's Qt, Xubuntu or Ubuntu if it's GTK. But really, you don't have to; it's just slightly more efficient and better looking.

So just take one you like. Under the hood, they're very similar.

---

### Post by TheFu on 2023-02-19
> **hoboy said:**
>  
witch one is the best to use for programming ?? 

It doesn't matter.  Which one you like or which one already has the GUI toolkit libraries you plan to use could matter, but ever that doesn't really matter.

I'm one of the people who doesn't use an IDE when programming. It wasn't how I was taught.  We used X/Windows as our IDE with a few different terminals open.  I'm not old enough to have needed to use emacs as an OS, thankfully.
If you google "Unix as an IDE", you can learn more about a method very similar to mine. [https://blog.sanctum.geek.nz/unix-as-ide-introduction/](https://blog.sanctum.geek.nz/unix-as-ide-introduction/)

If the class you are in uses a specific IDE, you'll probably choose to use that.  In the class, you'll learn that incorrect settings in an IDE will completely break your project, which is why understanding what is really happening underneath matters.  My first use of an IDE was Borland Turbo C, which would run from a single floppy disk. It was pretty amazing.  I took a C++ class that used Turbo C++ a year later - basically the same IDE. It was a nice little environment for creating MS-DOS programs, but every once in a while, a programming error would happen and I'd overwrite the OS, causing it to crash.  

Eventually, I got a job programming for Unix systems in addition to MS-Windows and MacOS.  That's were I learned to use Unix as an IDE and that model has stuck with me for the simple elegance and efficiency it provides.  I have 4 windows open.
[LIST]
[*]Editor
[*]Build
[*]Debugger
[*]Reference lookup
[/LIST]
My desktop is set so that window focus is under the mouse, but doesn't change which window is on top. The Z-order remains. By a little nudge and up-arrow, I can re-run that last command very fast. My editor is usually about 45% of the screen. At the bottom, below the editor is a tiny 'build' terminal that uses gmake.  To the right are the debugger and a terminal with manpage lookups for different function parameters and caveats for using the function.  The debugger is set to auto-load any new code and retain my breakpoints.
For the last 15 yrs or so, I've been using TDD, so I have tests written to provide coverage of the program features.  If a specific test fails, I put that failure into the source code where the fix would go with a :TODO: tag, so it isn't forgotten.  

When I'm coding, I start with high-level comments describing what needs to happen.  As more and more of the code is designed, I fill in more and more comments with explanations for what the code that will be added does.  Eventually, I just need to put code under each of the comments to get a working module/program.  

I try to keep each function less than 1 screen. This makes is easy to test and ensure all possible inputs to every function are valid.  Sometimes I'll just have a bad input crash the program when it is first seen using an ASSERT() function/macro. It is better to crash during my development than it is for a user to ever see any crash.  I program defensively when I'm being paid to code.  Gracefully handling errors is probably 85% of all code.  15% actually does what we hope to accomplish.

---

