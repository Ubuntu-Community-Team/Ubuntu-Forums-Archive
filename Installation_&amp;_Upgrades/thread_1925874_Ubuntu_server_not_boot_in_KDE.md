---
title: "Ubuntu server not boot in KDE"
date: 2012-02-15
forum: Installation &amp; Upgrades
---

### Post by abdzohbi on 2012-02-15
hi
Dear
  I install Ubuntu server and after install Kubuntu KDE and success
  but not boot from KDE is boot from console 
  why ?
Thanks You?

---

### Post by SeijiSensei on 2012-02-15
The default for Ubuntu Server is a text-mode desktop.  That means you need to log in then run "startx".

Try editing /home/yourusername/.profile and adding "startx" to the bottom of the file.  You'll still need to log in to the text-mode prompt, but KDE should launch after you do so.

---

### Post by abdzohbi on 2012-02-15
thanks but how launche KDE?

---

### Post by sanderj on 2012-02-15
Mabye easier to just install Kubuntu (Ubuntu with KDE)? All server stuff is included.

---

### Post by darkod on 2012-02-15
The post #2 has the instruction how to make it start automatically.
Did you open the /home/username/.profile file and adding 'startx' at the bottom as advised?

Why would you want a GUI running on the server all the time anyway? You can always start it with the manual command when you need it.

But if you are sure you want this, that post has the information. Try it and report if it worked.

---

### Post by abdzohbi on 2012-02-15
how??????

---

### Post by darkod on 2012-02-15
You mean you don't know how to open files for editing?

I use the nano text editor for example, you can use other if you want.

At the command prompt type:
sudo nano /home/username/.profile

In this command replace username with your username on the server.

The file will be opened in the editor. With the arrows move the cursor to the end and type in new line
startx

Press Ctrl + O and Enter to save the changes. Then press Ctrl + X to exist the editor. (the commands for the editor are on the bottom of the screen when it is open).

That should be it. Restart and see if it worked.

---

