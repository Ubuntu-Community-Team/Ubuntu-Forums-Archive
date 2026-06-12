---
title: "Mate terminal 1.14.1 colour"
date: 2017-09-09
forum: MINT
---

### Post by Kevin McCready on 2017-09-09
The preferences in the terminal don't allow me to set up white text on black background despite that being an option . That's all I want. ALL text, all results everything white text on black background. No grey no blue no red no yellow. Just white on black.

---

### Post by vasa1 on 2017-09-09
Which distro? Maybe there are some distro-specific tweaks.

---

### Post by Kevin McCready on 2017-09-10
Mint 18

---

### Post by deadflowr on 2017-09-10
*Thread moved to **MINT***

---

### Post by vasa1 on 2017-09-10
So you want your prompt, commands you enter, and output of folder listing all to have the same color of text?

Have you looked at modifying your *~/.bashrc*?

---

### Post by Kevin McCready on 2017-09-10
How should I modify the bash file to achieve what I need?

---

### Post by Kevin McCready on 2017-09-11
Help. I can't see the red in my terminal.

---

### Post by Kevin McCready on 2017-09-16
I'm beating myself up black and blue over this and still seeing red. I'll be green with envy if anyone can help.

---

### Post by vasa1 on 2017-09-16
See [http://askubuntu.com/a/271362/](http://askubuntu.com/a/271362/)

Once you've got your own ~/.dircolors, you can edit it to make everything white on black or just replace red with some other color.

---

### Post by Kevin McCready on 2017-09-17
Thanks vasa1. I now have a ~/.dircolors file, but I don't know how to edit it to get white on black for everything.

---

### Post by vasa1 on 2017-09-17
Take a little time to read the instructions which are in the file itself:
```
# Below are the color init strings for the basic file types. A color init
# string consists of one or more of the following numeric codes:
# Attribute codes:
# 00=none 01=bold 04=underscore 05=blink 07=reverse 08=concealed
# Text color codes:
# 30=black 31=red 32=green 33=yellow 34=blue 35=magenta 36=cyan 37=white
# Background color codes:
# 40=black 41=red 42=green 43=yellow 44=blue 45=magenta 46=cyan 47=white

```

If you still have problems, I suggest using another terminal such as *lxterminal*. Installing it won't pull in many dependencies.

---

### Post by vasa1 on 2017-09-17
Back-up *.dircolors* somewhere and then use a text editor to replace all instances of *;31*, *;32*, *;33*, *;34*, *;35*, *;36* with *;37*. After this both *konsole* and *lxterminal* show only white text.

If your terminal doesn't, wait for someone else to help you or dump your terminal in favor of a terminal that allows you to do what you need.

---

### Post by Kevin McCready on 2017-09-17
Thanks again.
As I was doing the replacing of all instances of *;31*, *;32*, *;33*, *;34*, *;35*, *;36* with *;37, I noticed that some were for SOCK or other things which might not be right*. Are you sure?

---

### Post by vasa1 on 2017-09-17
> **Kevin McCready said:**
> Thanks again.
As I was doing the replacing of all instances of *;31*, *;32*, *;33*, *;34*, *;35*, *;36* with *;37, I noticed that some were for SOCK or other things which might not be right*. Are you sure?
What specific problem are you facing now? I've posted images to show it works for me.

---

### Post by Kevin McCready on 2017-09-18
I didn't save the file in case it would really muck things up. I tried both lxterminal and konsole, neither of which have preferences to change the color.

---

