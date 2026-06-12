---
title: "How to Install from a Root?"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by Thieflock on 2006-12-14
Im still learning Ubuntu and have boughten a book on it. Ive been trying to install drivers for my Ubuntu and when I run them in a terminal I get the message "Run installation from root". My book can't seem to help me and I cant seem to find a forum to answer the question. Thank you.

---

### Post by meng on 2006-12-14
You probably need root privileges to install the drivers, in which case you should just prefix your commands with "sudo"

---

### Post by Thieflock on 2006-12-14
What would the command line be for that?
If tried sudo install "file name", ect. What am I supposed to type?

---

### Post by meng on 2006-12-14
Let's go back one step. What command did you type in originally, the one that got the error message "Run installation from root"?

---

### Post by Thieflock on 2006-12-14
I didn't type a command, I clicked on the file and it auto started in a terminal. Then I tried doing it manually and I cant get the prompt right.

---

### Post by meng on 2006-12-14
In that case, I suggest you go right back to the very beginning and tell us what you're installing drivers for, where you got the drivers and where you saved them. Perhaps we can find an easier way.

---

### Post by Thieflock on 2006-12-14
It's a driver for my wireless card on in my laptop, I can't remember the website I got it off of but I have the file on my desktop named "dldrinstall.run" if this information helps in helping me.

---

### Post by meng on 2006-12-14
> **meng said:**
> In that case, I suggest you go right back to the very beginning and tell us what you're installing drivers for, where you got the drivers and where you saved them. Perhaps we can find an easier way.
Providing _more_ detail can only help you get assistance faster. Right now, for example, I don't know which wireless card you're talking about (make/model), and I have to do a web search to get a merest idea of what's going on. You didn't tell me where the file is saved, so I have to assume. At some point, I'm going to decide that I've wasted too much time on this thread and I'll give up, but hopefully someone else will have volunteered to help you by then.

That said, I'm going to GUESS/ASSUME that you have the correct file and that this is the easiest way to install drivers. Furthermore, I'm going to GUESS/ASSUME that your file is in ~/Desktop. Drop to the command line/terminal and type:
cd ~/Desktop
sudo sh ./dldrinstall.run

---

