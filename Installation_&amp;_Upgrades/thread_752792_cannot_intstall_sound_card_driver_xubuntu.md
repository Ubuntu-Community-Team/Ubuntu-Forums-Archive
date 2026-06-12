---
title: "cannot intstall sound card driver xubuntu"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by rebekah on 2008-04-12
Have just installed Xubuntu 7.10 on my old laptop, but there is no sound. Help!

"aplay -l "   results in "no sound card found" but details of the card come up when I try "lspci -v". From previous posts it seems that this might mean I need to install the driver for my soundcard? It's a Magic Media 256AV.

 I tried following the instructions [here]("http://ubuntuforums.org/showthread.php?t=205449&highlight=build+module+shell")
and at the [Alsa page]("http://www.alsa-project.org/main/index.php/Matrix:Module-nm256") but came to a dead-end in both cases.

Following the instructions on the Alsa page I get stuck at "cp /downloads/alsa-* ." because it results in "missing destination file operand".

On the other helpful-looking instructions "sudo modprobe snd-nm256." gives me "FATAL model snd-nm256 not found." 

I'm a complete linux newbie.  Any help or ideas appreciated.

---

### Post by Partyboi2 on 2008-04-12
> On the other helpful-looking instructions "sudo modprobe snd-nm256." gives me "FATAL model snd-nm256 not found."  mean its failed to find the driver the how-to then gives you two options:
> [SIZE=2]**Getting the ALSA drivers from a *fresh* kernel**[/SIZE] or
> [SIZE=2]**ALSA driver Compilation**[/SIZE] What happens when you continue with alsa driver compilation?

---

### Post by rebekah on 2008-04-12
Thank you. I went on and did the alsa driver compilation.  Then continued with the [instructions]("http://ubuntuforums.org/showthread.php?t=205449&highlight=build+module+shell") (ie step 4 of general help) to try and find a driver that matches the one I need, ie typed "sudo modprobe snd-" and pressed tab. 

The driver (nm256) was on the list.

Then I wasn't sure from the instructions what to do next.  

Tried "sudo modprobe snd-nm256" and got no response (ie the same username :~$ prompt came up again).

Tried  "sudo nano /etc/modules" and the file "etc/modules" opened. However, when I typed "snd-nm256" and tried to save it (the following process)
^X 
SAVE MODIFIED BUFFER?
Y
FILE NAME TO WRITE: etc/modules
pressed enter

I got an error message "Error writing etc/modules: no such file or directory"

I'm stuck again - please help :confused:

---

### Post by Partyboi2 on 2008-04-12
To add the module so it loads on all sessions (refer to step 4 of general help) In a terminal type
```
gksudo gedit /etc/modules
```then the file will open at the bottom of the file add 
```
snd-nm256
``` then save and exit.  [SIZE=2]Then play music using your favorite media player while moving onto the "alsamixer section" of the instructions, then after that finish with "saving sound setting" sections. (Just below alsamixer section). Hopefully all going well you will have sound!

[/SIZE]

---

### Post by rebekah on 2008-04-13
> To add the module so it loads on all sessions (refer to step 4 of general help) In a terminal type
Code:

gksudo gedit /etc/modules

then the file will open at the bottom of the file 

Thanks for your help but that didn't work either.   Nothing happened when I typed that into the terminal.

Wish I knew more about this OS...
](*,)

---

### Post by Partyboi2 on 2008-04-13
my apologies I just realized you are using xubuntu. gedit is the gnome text editor, for xubuntu you should try mousepad.
```
gksudo mousepad /etc/modules
```

---

### Post by rebekah on 2008-04-14
Thank you.  Editing /etc/modules in mousepad worked and I could save the file.  But my sound card still isn't loading.  Looking around at some other posts it seems there might be a problem with this particular driver...
:(

---

