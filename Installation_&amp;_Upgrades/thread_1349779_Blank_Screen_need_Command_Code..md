---
title: "Blank Screen need Command Code."
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by Timby on 2009-12-08
[COLOR=#003333][SIZE=2]I am useing Ubuntu 9.10 Karmic and have just installed a download, now I have a black screen with a little white window that expects a command.[/SIZE][/COLOR]
 
[FONT=Arial][SIZE=2][COLOR=#003333]I cant navagate away from the window, can someone help me with a command please.[/COLOR][/SIZE][/FONT]

---

### Post by lisati on 2009-12-08
Knowing what you would like to do would help us know which command to tell you about. For starters, were you expecting a GUI (Graphical User Interface)? If so, the following *might* help:
```
startx
```
If it doesn't please let us know what error messages (if any) you get, and someone might be able to guide you through what you need to do.

---

### Post by Timby on 2009-12-08
Hi, Screen comes up on start up and will not go farther.
 
I have just tried "startx" and I have got the message "user not autherised to run the x server. "

---

### Post by darkod on 2009-12-08
> **Timby said:**
> [COLOR=#003333][SIZE=2]I am useing Ubuntu 9.10 Karmic and have just installed a download, now I have a black screen with a little white window that expects a command.[/SIZE][/COLOR]
 
[FONT=Arial][SIZE=2][COLOR=#003333]I cant navagate away from the window, can someone help me with a command please.[/COLOR][/SIZE][/FONT]

You have a command prompt or white window? What sort of window, any title, any text?

---

### Post by 6630 on 2009-12-08
i have the same problem.

---

### Post by darkod on 2009-12-08
> **6630 said:**
> i have the same problem.

Well, you saw my questions. How about supplying some info? Do we have to guess here?

---

### Post by Timby on 2009-12-09
When I  start up I get a black screen with a  little white window that expects a command.

The message says,   bill@bill - desktop:" $ []

 
I cant navagate away from the window, I guess that I need a command that will get me up and running.

---

### Post by Timby on 2009-12-10
> **Timby said:**
> When I  start up I get a black screen with a  little white window that expects a command.

The message says,   bill@bill - desktop:" $ []

 
I cant navigate away from the window, I guess that I need a command that will get me up and running.


I have got a bit farther now,  I can make the system shut down by using the Command,   " [FONT=Verdana][FONT=Courier New][SIZE=2]sudo shutdown -h now"

But when I restart I get back to the same window as before.

[/SIZE][/FONT][/FONT]  [FONT=arial] [FONT=Verdana][FONT=arial, sans-serif][SIZE=2][FONT=Verdana][SIZE=2]can someone please tell me the the Commands  needed to get into the working desktop?

I am a Newbie and I am not familiar with the system or the Commands.
[/SIZE][/FONT][/SIZE][/FONT][/FONT] [/FONT]

---

### Post by lisati on 2009-12-10
> **Timby said:**
> I have got a bit farther now,  I can make the system shut down by using the Command,   " [FONT=Verdana][FONT=Courier New][SIZE=2]sudo shutdown -h now"

But when I restart I get back to the same window as before.

[/SIZE][/FONT][/FONT]  [FONT=arial] [FONT=Verdana][FONT=arial, sans-serif][SIZE=2][FONT=Verdana][SIZE=2]can someone please tell me the the Commands  needed to get into the working desktop?[/SIZE][/FONT][/SIZE][/FONT][/FONT]
[/FONT]

1. Did you install the server edition? If so you will need to install a GUI.
2. Does typing in the following give you any clues? Come back to us with any error messages that appear.```
startx
```


Edit: Oh, just noticed, OP had a message about not being authorised to run x-server. I'm not able to help on that one...... Anyone else have a suggestion?

---

### Post by darkod on 2009-12-10
Hmmm... what was the package called? ubuntu-desktop?

Try:
sudo apt-get install ubuntu-desktop

It seems like you have a working system but in text mode only. Try installing the desktop package and reboot:
sudo reboot

---

### Post by Timby on 2009-12-11
The system worked  after the download but when I later restarted, it only loaded up to a login window.

I was asked to login (I don't usually get that) but could not,  it was when I was trying to cure this that I got to where I am now.

I clicked on something below the login window  but I cant remember what it was called.

---

### Post by Timby on 2009-12-13
There must be a way out of this?

Or do I have to reload 9.4 again?

---

### Post by Timby on 2009-12-14
I am still looking for help with this problem.

---

