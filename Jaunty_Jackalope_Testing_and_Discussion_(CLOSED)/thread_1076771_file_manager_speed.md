---
title: "file manager speed"
date: 2009-02-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2009-02-21
Is the Jaunty file manager faster than Ibex?
I am experiencing very slow response times. Takes a minute to open 
the list, navigating between folders is nightmarishly slow, etc...

---

### Post by ugkbunb on 2009-02-21
try installing thunar... i have always found it to be more snappier/responsive on my system...

---

### Post by todak on 2009-02-22
Your slow response times bug may be related to [this thread]("http://ubuntuforums.org/showthread.php?t=1074757"). Use an older kernel at boot and see if you notice any difference.

---

### Post by fut21 on 2009-02-22
Or use PCMan File Manager.

Read this to implament:
[http://linuxondesktop.blogspot.com/search/label/PCMan%20File%20Manager](http://linuxondesktop.blogspot.com/search/label/PCMan%20File%20Manager)

---

### Post by OliW on 2009-02-22
> **ugkbunb said:**
> try installing thunar... i have always found it to be more snappier/responsive on my system...We should probably attempt to fix things rather than abandon them.

---

### Post by orethrius on 2009-02-22
> **OliW said:**
> We should probably attempt to fix things rather than abandon them.

"We" probably should, so the end product is more refined.  A "quick fix" is just fine for the average user.

---

### Post by cl333r on 2009-02-22
> **sdowney717 said:**
> Is the Jaunty file manager faster than Ibex?
I am experiencing very slow response times. Takes a minute to open 
the list, navigating between folders is nightmarishly slow, etc...

boy do I understand you, but the other (gnome) file managers while solving this issue introduce their own ones (including thunar).
and btw. Nautilus is not slow because of the cpu.

---

### Post by orethrius on 2009-02-22
Well, right, and the end result here needs to be that the access times are addressed.  Thunar is a "quick fix", and that implies taking hold of its inherent flaws as well.

---

### Post by Starks on 2009-02-22
Yes. Lets dump Nautilus! </sarcasm>

<_________<

---

### Post by sdowney717 on 2009-02-22
PCMan File Manager is very responsive, thanks very much!

I am running a single core 2.4ghz p4 with 1 gb ram and 200 gb 7200 rpm drive and Nautilus has gotten so slow it is click and walk away, get a drink and perhaps it is displaying the list. Switching directories is awful, try to go back to my home directory is like starting over again. 
It became unusable. I have 17gb of stuff in my home folder and I noticed it slowing down as more was placed in there.

off hand. none of the file managers will display the configuration files in the list

I simply opened as 'gksudo gedit'

then I was able to locate and change 

    For nautilus-computer.desktop: Exec=pcmanfm /

and

    For nautilus-folder-handler.desktop: Exec=pcmanfm %U 


Why is this, what are the priveliges? they are not hidden files. Even opening filemanagers as root does not show these files.

---

