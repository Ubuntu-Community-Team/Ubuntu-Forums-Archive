---
title: "Kubuntu: Hang after progress bar upon boot"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by Albright on 2006-06-20
I tried to install Kubuntu from the regular Live CD, but the system would hang right after the progress bar upon booting. After the progress bar was finished, the screen would go black, then display some text too quickly to read, then return back to the progress bar screen, but with no "Doing this... ok" messages; nothing would happen.

So I downloaded the non-live CD and installed Kubuntu from there. The text-only installation went fine, but sure enough, when I went to boot Kubuntu from my hard drive, the same hangage occurred as did with the Live CD.

I know that it's hanging around the time that X should start, so I tried putting in a video card, thinking that might be the problem. (I was previously using the MB's onboard video.) But the same problem occurred.

Any ideas?

---

### Post by Winblowz on 2006-06-20
Have you tried booting Kubuntu from the hard drive in Recovery mode? That  should solve the problem of it hanging, and from there you can find out what the real problem is.

---

### Post by Albright on 2006-06-20
[QUOTE=Winblowz]Have you tried booting Kubuntu from the hard drive in Recovery mode? That  should solve the problem of it hanging, and from there you can find out what the real problem is.[/QUOTE]

Well, it gets me to a CLI prompt. However, that hardly helps me find out what the problem is. Any hints on what to do from there?

(Something that I forgot to mention in my first post is that, if I press the power button on the case after it "hangs," the system seems to shut down normally, with its own backwards-ish progress bar and its own "blah blah... ok" text. So I guess it's not really technically hanging.)

For all the big push there is to get Linux on the desktop, installing it has invariably been varying degrees of hassle for me, when it's even been possible at all...

---

### Post by Winblowz on 2006-06-20
In Recovery mode you should be in the command promt (terminal). Type
```
startx
```
to see if your video is working.

---

