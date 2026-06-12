---
title: "Process kill (see list)"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by jorgerosa on 2008-02-11
If I want to kill (stop, close) an application (process)...
So if i run it in terminal, i see his PID: 345 so, i type: **kill 345**
If I run an application (process) and i didnt use terminal to run it, (i dunno his PID) i do now: **killall programname**
To see full list all running process, i type:  **ps aux | less**

But, i dont want to use terminal all the time, so there is a GUI or application that can do the same like the above command line (ps aux | less)
in a visual way? with "stop" buttons on it? or whatever?.... Thanks guys.

---

### Post by luisromangz on 2008-02-11
Gnome's System Monitor should do the trick.

---

### Post by jorgerosa on 2008-02-11
Just what i needed!

Ok, guys do: **sudo apt-get install gnome-system-monitor** (But you shouldnt need to install it anyway...)
And / Or go to:
** "System" --> "Administration" --> "System Monitor"**, and select **"processes"** tab there.
Still, cant find your process there? (i was looking for Apache 2 Server and other stuff that i instaled...) i found how! Very simple:
With **processes** tab selected, go to **"View"** and select[B] "All processes"

[/B]EDIT:
Now, how about assign **shortcut keys **to gnome-system-monitor? in this example i'll use Ctrl+Q
** first, type:**  gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control>Q"
** then, type:** gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
More info about key shortcuts: [here]("http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/") , [here]("http://ubuntuforums.org/archive/index.php/t-484389.html") and [here]("http://ubuntuforums.org/showthread.php?t=119534")

BIG Thanks **luisromangz**!! Cya.

---

