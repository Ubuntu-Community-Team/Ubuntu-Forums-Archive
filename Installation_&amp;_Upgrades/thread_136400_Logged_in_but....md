---
title: "Logged in but..."
date: 2006-02-25
forum: Installation &amp; Upgrades
---

### Post by FZ1 on 2006-02-25
Hi all, I just installed and logged in. However, the following screen looks like this:
[[IMG]http://img110.imageshack.us/img110/5760/img14801nk.th.jpg[/IMG]](http://img110.imageshack.us/my.php?image=img14801nk.jpg)
:-k :-k 

I'm guessing a video driver issue? I am using a 7800GT Nvidia card. I can move the cursor around the screen fine but nothing else. Sorry I'm a noob with this and lost!

---

### Post by o_fortuna on 2006-02-25
[QUOTE=FZ1]
I'm guessing a video driver issue? I am using a 7800GT Nvidia card. I can move the cursor around the screen fine but nothing else. Sorry I'm a noob with this and lost![/QUOTE]
You probably need to install the official nVidia drivers -- that fixed several problems for me. To install the drivers without a working graphical environment:

Press Ctrl-Alt-F1 on your keyboard. You will be brought to a black-and-white basic terminal. Log in by typing your username/password. Then you will see the command line. Enter this command:
```
sudo apt-get install nvidia-glx
```
The drivers are installed, so you have to enable them.
```
sudo nvidia-glx-config-enable
```
Now you have to edit xorg.conf:
```
sudo nano /etc/X11/xorg.conf
```
Scroll down untill you see this:
```
Section "Device"
```
Change the line that says 
```
Driver     "nv"
```
to
```
Driver     "nvidia"
```
Now press Ctrl-Alt-Del (like in Windows) to restart. You can always restart from the terminal consoles (Ctrl-Alt-F1-F6) like this.

---

### Post by FZ1 on 2006-02-25
Hey, thanks for the advice...I'll give it a shot and see what happens:)

---

### Post by FZ1 on 2006-02-26
OK, first part worked but when I type "sudo nvidia-glx-config-enable" I get a "command not found" response.:confused:

---

### Post by aysiu on 2006-02-26
[QUOTE=FZ1]OK, first part worked but when I type "sudo nvidia-glx-config-enable" I get a "command not found" response.:confused:[/QUOTE] That's because the command is actually ```
sudo nvidia-glx-config enable
``` See this page for more details: [http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

---

### Post by FZ1 on 2006-02-26
Nice, I actually found some info [HERE]("http://www.ubuntuforums.org/showthread.php?t=75074&highlight=sudo+apt-get+install+nvidia-glx") and although the last command didn't seem to work I restarted and I'm golden now. WOOT \\:D/

---

### Post by o_fortuna on 2006-02-26
[QUOTE=FZ1]OK, first part worked but when I type "sudo nvidia-glx-config-enable" I get a "command not found" response.:confused:[/QUOTE]
Whoops, typo. Sorry :oops: aysiu has it right.

---

