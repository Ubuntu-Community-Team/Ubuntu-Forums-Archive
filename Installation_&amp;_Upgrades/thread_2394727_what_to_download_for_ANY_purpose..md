---
title: "what to download? for ANY purpose."
date: 2018-06-20
forum: Installation &amp; Upgrades
---

### Post by idkwhatimdoing1.0 on 2018-06-20
Hey, I'm quite new with Ubuntu and I was wondering if anyone had any programs they personally think are useful or good in ANY situations? I prefer to code with my laptop on Ubuntu and I have installed already NetBeans, Geany and CodeBlocks... And I kinda just discovered how to download things with chmod, so I was wondering if anyone thought about any things they like? Whether its secure or not its ok, I dont have anything personall that I keep on my coding laptop... Thank you

---

### Post by deadflowr on 2018-06-20
> And I kinda just discovered how to download things with chmod,
New to me.
chmod is for changing permissions for files/folders.
People use it post-download to reset erred permission settings.
But I've never seen or heard it used to download anything before.

How does that work?

---

### Post by idkwhatimdoing1.0 on 2018-06-20
sofar Ive used it for two downloads. I used it first with katoolin but now you can just do it from the terminal. What I used it for now is for NetBeans. So I went on the NetBeans webpage and I did the download button and it downloaded a script with the file name finishing a .sh   so after that I went into my files > downloads > and clicked open in new terminal. The from there I wrote chmod+x <and the name of the file> then just pressed ./<name of file> and it ran the setup wizard. So two steps in total and always the same commands... chmod +x <name of file> and then ./<name of file>.

---

### Post by QIII on 2018-06-20
You are not downloading with chmod.  You are downloading a script and then making it executable with chmod.

The script may then download further files when you run it.

It may be instructional to consult 

```
man chmod
```

Some excerpts here:

> This manual page documents the GNU version of chmod. chmod changes the file mode bits of each given file according to mode, which can be either a symbolic representation of changes to make, or an octal number representing the bit pattern for the new mode bits.

...

read (r), write (w), execute (or search for directories) (x)

---

