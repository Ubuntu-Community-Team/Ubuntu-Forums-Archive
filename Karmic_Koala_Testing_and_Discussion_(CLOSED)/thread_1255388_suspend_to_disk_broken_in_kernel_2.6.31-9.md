---
title: "suspend to disk broken in kernel 2.6.31-9"
date: 2009-09-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jithin1987 on 2009-09-01
After my laptop wakes up from sleep its has a desktop with no plasma.

Not exactly, the place where plasma used to be is blank. But right clicking on it shows the context menu, but nothing is displayed there. Only thing I can do is restart or log out.

Please take a look at the picture. Windows have lost the border and in bottom place plasma is missing.
[IMG]http://farm4.static.flickr.com/3522/3878609686_289b1d9d0f.jpg[/IMG]

---

### Post by jithin1987 on 2009-09-01
sorry the title should have been suspend to ram. I havent tried suspend to disk yet

---

### Post by jithin1987 on 2009-09-01
Any other kubuntu users out there having the same issue ?

---

### Post by buzzmandt on 2009-09-02
sorry, my K's working with suspend to ram.  Actually better than it was, comes back quite a bit quicker.

---

### Post by jithin1987 on 2009-09-02
Thats strange. Mine used to work also. No idea whats happening.

---

### Post by andresmh on 2009-09-02
recovering from suspend is failing sometimes on my system too. The screen comes up but the mouse and the keyboard don't seem to respond at all. What I end up doing is a hard reboot.

---

### Post by jithin1987 on 2009-09-02
Its different in my case. My mouse and keyboard works. Though none one plasma interfaces work folder view was working and I was able to launch ksnapshot.

After that I am able to logout.Few days back it was even worse. Though keyboard work the login prompt wont appear. No matter what I do and I could only reset.

---

### Post by zoomy942 on 2009-09-02
> **jithin1987 said:**
> Its different in my case. My mouse and keyboard works. Though none one plasma interfaces work folder view was working and I was able to launch ksnapshot.

After that I am able to logout.Few days back it was even worse. Though keyboard work the login prompt wont appear. No matter what I do and I could only reset.


I have a thread about this too. Already filed a bug. I think the thread is on the second page by now.

---

### Post by jithin1987 on 2009-09-02
@zoomy I cpuld not find ur topic Can you post a link

---

### Post by jithin1987 on 2009-09-02
I am seeing one more behavior. If the system is in sleep for more that say half an hour, then the kdm login screen does not even appear. Its pure black. But if I enter my password based on an assumption, it seems to be working then when I move my cursor it changes when it passes my notes in desktop. But at this point I cannot even log out. Only thing I can do is do a VT switch and reboot.

---

### Post by zoomy942 on 2009-09-02
here ya go :)

[http://ubuntuforums.org/showthread.php?t=1252048]("http://ubuntuforums.org/showthread.php?t=1252048")

---

