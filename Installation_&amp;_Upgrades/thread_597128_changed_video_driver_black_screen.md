---
title: "changed video driver: black screen"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by killerwhale65 on 2007-10-30
hi,

I am trying to change the default VESA video driver to Nvidia, but my screen went black, also after a restart. What should i do?

thanks!

Matt

---

### Post by taurus on 2007-10-30
Did you install nVidia driver first before you made that change in /etc/X11/xorg.conf?  Otherwise, try running

```
sudo nvidia-xconfig
```

---

### Post by killerwhale65 on 2007-10-30
now thats fast!

but how do i type a command on a black screen?

---

### Post by taurus on 2007-10-30
Press <Ctrl><Alt>F2 to get to a console.  Log in with your username and password.  Then, try to run that command from a prompt.  Again, did you install nVidia driver for your nVidia graphic card?

---

### Post by killerwhale65 on 2007-10-30
ok will try that.

No i didnt install anything. I selected a generic nvidia driver from the list. It showed that the system determined the name of my graphics card, and i could press select, then a nvidia driver was selected (before, it was a vesa driver). Then i click aply, and i must restart the x-server by logging out and selecting the appropriate option in the menu. As soon as i did that, the light went out.

Oh, and i also got a warning when i clicked apply, that the situation could not be tested, and if i was sure to continue.

---

### Post by taurus on 2007-10-30
Again, you do have an nVidia graphic card on your machine, right?  For now, you should use **nv** instead of nvidia until you have actually installed nVidia driver for your card.

---

### Post by killerwhale65 on 2007-10-30
yes i do have an nvidia card.

I will look for nv instead.

But how do i install the nvidia driver, is that just by selecting it in the restricted drivers?

---

### Post by taurus on 2007-10-30
Yes, just _enable_ it in System -> Administration -> Restricted Drivers Manager.

---

### Post by killerwhale65 on 2007-10-30
ok will do that.

thanks!

---

### Post by killerwhale65 on 2007-10-30
hi,

I have first started in recovery mode, and ran nvidia-xconfig, but it says the packages are not installed and the command is unknown.
Restart now in normal mode untill my pc keeps quite (black screen so i don't see anything). With CTRL-ALT-F1 to a console, but i get a screen full of lines and rectangles? CTRL-ALT-F7 and then CTRL-ALT-BACKSPACE to restart x, still blank. Again CTRL-ALT-F1, and now i see a black screen (i do not see the prompt, only a blinking cursor). I seem to be able to type, but it does not appear on the screen, only the cursor moves. What is wrong?

---

### Post by killerwhale65 on 2007-10-31
Can anyone help me further please?

thanks!

Matt

---

