---
title: "login &amp; password problem"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by craigcheek on 2010-12-19
After trialling ubuntu 10.10 from a USB drive I installed it onto my hard drive. When I power up I am now asked for Login and then a password. I set a password during the installation, but not a login. No matter what I try I cant get in. I get the same when using the Windows option. I can now only use the computer (Tosihba equium)  from the usb. How do I get rid of the login and password.

Craig

---

### Post by sikander3786 on 2010-12-19
The password you setup during installation is the same that is needed to log in.

> I get the same when using the Windows option.

What does that mean? I couldn't understand.

You mean the password you setup during the installation is not being accepted at the login screen? If yes, you can reset it.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by craigcheek on 2010-12-19
Thanks for that - password problem sorted.
Now I am left with a screen of text and a command prompt. There is no ubuntu graphic. [IMG]http://ubuntuforums.org/images/icons/icon11.gif[/IMG]

---

### Post by sikander3786 on 2010-12-19
How did you solve the password problem?

Regarding the graphics issue, which graphics card is there and were any drivers installed? We need to see the output of these commands.

```
lspci | grep VGA
```

```
glxifo | grep vendor
```

```
cat /etc/X11/xorg.conf
```

Note capital 'X' for X11.

---

### Post by craigcheek on 2010-12-19
I fixed the password problem with the help of the link included in your first reply.

I entered the commands on your second reply, but I cant enter the vertical character in the first two. The last command returns a not recognised. When I boot off the USB everything works well.

I dont know which graphics card the toshiba equium has and I don't know which drivers were loaded.[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

---

### Post by sikander3786 on 2010-12-19
No problem. Check if your home directory is there. This command should return the same folder name as your user name.

```
ls /home
```

If yes, try reconfiguring your graphics and reboot.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo shutdown -r now
```

If it still doesn't take you to the desktop, we need to know about hardware specs of the machine in question. Specially RAM, processor and graphics card.

On my keyboard, vertical character '|' is on the same button as backslash. Shift + \ = |

---

### Post by craigcheek on 2010-12-19
entered ls /home and it returns my user name

entered your first sudo command and it returns dpkg : confliting actions -e and -r
entered your 2nd sudo command and it returns : invalid option -0

my processor is a intel pentium M processor 1.6 GHz
1Gb ram
display adapter  mobile intel 915GH/GMS, 910GML express chip set

everything works well off the USB and I installed from the usb.

---

### Post by sikander3786 on 2010-12-19
> dpkg : confliting actions -e and -r

Make sure the command is typed as is here. No spaces, no capital characters.

Else, everything seems fine.

---

### Post by craigcheek on 2010-12-19
Okay - ran those two commands and they were accepted, but things are just the same and I end up with a command prompt and not the graphic display

---

### Post by sikander3786 on 2010-12-19
Try to start the gui this way.

```
sudo service gdm stop
```

```
sudo service gdm start
```

Or,

```
startx
```

Please post any errors reported there.

---

### Post by craigcheek on 2010-12-19
typed the 2 sudo command and got returned
gdm start/running, process 1202  and then nothing but the command prompt

when I entered the startx command I got a fatal server error and no screen found.

---

### Post by sikander3786 on 2010-12-19
I am running out of ideas here.

As this thread is titled login $ password problem, not many experienced members on your current issue i.e, no gui, would be looking at this thread. I would suggest to start a new thread with a title something like "no gui" or "ubuntu boots to terminal" as that would attract the experienced members on that specific problem.

And as you mentioned it was a fresh install, you can also try a re-install to save you time and effort.

Good Luck!

---

### Post by craigcheek on 2010-12-19
Many thanks for your time and effort.

Craig

---

