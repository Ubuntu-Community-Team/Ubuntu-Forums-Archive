---
title: "Desktop size completely wrong before and after installation"
date: 2021-02-12
forum: Installation &amp; Upgrades
---

### Post by angelo16 on 2021-02-12
History:

I have a Dell1525 (Core2 duo) laptop without the screen which was removed after been damaged 5 years ago. Last month, I decided to give some chance to this laptop in order to run octoprint on it. Without the original screen, I've just connected it to a external display, an LG E2241 (native resolution 1980x1080). Then I flashed a USB stick with Lubuntu 20.04 and tried to install. Here started the issue.

The Lubuntu installation goes trough a initial boot to a linux in a GUI mode. Once there, I noticed that no icon was diplayed on the desktop, although it had  desktop wallpaper. The problem was the desktop size/resolution which was larger then my display and  all icons were at the left side of the screen, which I do not have access to them. CTRL+ALT+T did open the qterminal, but also on the same left region, so I could not access. CTRL+ALT+DEL  did open the task manager and I could confirm that qterminal was running. Some other key combination on the keyboard did open the file manager in the region of the screen that I could see it and then I could open the desktop folder and click on the Install icon.

The installation was smooth and fast.

The system rebooted and Lubuntu login screen appeared. I noticed the image on the screen did not fit perfectly as the "20.04" is cut on the bottom right corner, see image

[IMG]https://ibb.co/KyQZ5Ls[/IMG]
[IMG]https://ibb.co/KyQZ5Ls[/IMG]
[IMG]https://i.ibb.co/j4xK8Ww/fotox1.jpg[/IMG]


Then I log in, but I do not have the lubuntu desktop, now I black screen, with mouse icon. It is the same previous behavior before the installation, except for wallpaper, the screen is black now, see image below


[IMG]https://i.ibb.co/ZffqgGN/Untitledj.jpg[/IMG]



 The desktop size seems to be larger then my external display, qterminal opens outside the screen, I can't move it because keyboards shorcuts does not work, and I am stuck.


If this can help to help me, below is the vbeinfo 

[IMG]https://i.ibb.co/DkjXbfT/image.jpg[/IMG]

How can I fix this ?

---

### Post by angelo16 on 2021-02-12
Just found the solution !!:D:popcorn:

Here it is:

First let's see if your case is the same as mine:

1) open a terminal pressing CTRL+ALT+F2
2) Log in
3) type the following commands

```
export DISPLAY=:0

xrandr --listactivemonitors
```

check the last two lines that xandr has output. 

In my case, I had removed the old laptop screen, but the output of xrandr said that I had two monitors active, LVDS-1 and VGA-1. 


LVDS-1  is the original laptop screen
VGA-1 is the external display, which I am using !!

The problem was that Lubuntu was using the LVDS-1 which is the original laptop screen with  higher resolution than my LG display. To fix the problem,  I had to disable the LVDS-1. How ? I simply edited grub configuration.

```
sudo nano /etc/default/grub

```
then added "[FONT=Consolas]video=LVDS-1:d" to the [/FONT]line [FONT=Consolas]GRUB_CMDLINE_LINUX_DEFAULT.

It was
[/FONT]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and now it is


GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **video=LVDS-1:d**"

save the configuration and exit nano.

Now,  you have to update grub with the command:

```
sudo update-grub 

```

Now you need to reboot for the changes to be applied, for this  just type :

```
reboot
```

and voi-la....

---

