---
title: "Upgrade Problem with Ubuntu 12.04 - No icons"
date: 2012-05-17
forum: Installation &amp; Upgrades
---

### Post by Babyzilla on 2012-05-17
Hello everybody, I would like to ask a help with my problem:

I am newbie with Ubuntu. I installed Ubuntu 11.10 in my laptop side by side with Windows 7. So I spare around 50 GB for Ubuntu, and I used the rest for my windows. Several months after, come a notification said that a new version is avalaible.

I chose to upgrade the Ubuntu version to 12.04, and the terminal showed me a lot of things. After the process is finished, it asked me to restart my computer. I did the restart, then I encountered these problem:

1. In the log in screen, I am only able to type my password to log in, but the other icon are not exist. So, what I can do there is just look at the calendar, time, shut down and log in.
(Attachment Trouble_1 and Trouble_2 shows the display)

2. After I logged in, the screen only give me a blue screen as shown in attachment Trouble_3 without anything. I couldn't access terminal nor have access to anything. What I can do is just pressing Ctrl+Alt+Del to log out, and I will meet the log in screen again.

My questions are:
1. How to solve this problem? I don't have any button to be pressed, nor any option to be chosen on the screen.

2. If I need to reinstall the Ubuntu, how can I reinstall it in the space that is occupied by the previous version? (The 50GB that I used for version 11.10, so that I don't need to spare more space from my Hard Disk) And how to reinstall it? Boot from installation CD or do it from terminal?

Additional info:
My laptop is: ACER Aspire Timeline X
Intel core i5-460, 64 bit, ATI Mobility Radeon HD 5650.

Thank you for your help with my problem ..

Regards,
Babyzilla

---

### Post by jadtech on 2012-05-17
very familar your not alone  try switching to ubuntu 2d this may boot with  the unity launcher and graphics and all it may not what has happened is the update is not complete there is uninstaled libraries ..

other wise if you have internet connection and can get to  a terminal ..

try typeing these codes

```
 sudo apt-get update

sudo apt-get upgrade -f


```

there may be some packages already down loaded that couldnt install 

if things still arent  good try  these codes  sudo apt-get install -f and configure -a ..

someone else might have other options to help in this but if this dont work you can use a live cd to boot and then copy files and such then do a new clean install, this happen to 2 upgrades I did nad I just  reinstalled ...

---

### Post by Babyzilla on 2012-05-17
thank you jadtech for your reply.

I would like to try to put that command, but do you have any idea how can I access the terminal? Since the screen leave me with no options avalaible..

---

### Post by jadtech on 2012-05-17
well if its anything like what I had once logged in the mouse  works but there is no keyboard which is why I just surrendered and re instaled .. 

there is no top bar or Icons to get a menu and click even before loggin 

funny thing was I could right click on the desktop and create a new document and  folder but  couldnt figure out how to get to a terminal ..

like I said if you can switch to 2d you might get a unity desk top 
click the top of the box where you type your password a menu should open choose ubuntu 2d  loggin maybe the desk top will be there :)

---

### Post by Babyzilla on 2012-05-18
Hi Jadtech, thanks again for your reply...

I couldn't find the "2D" option.. So, I have decided to try reinstall it from beginning.

The good news is: The problem is solved!^^ I am able to use 12.04 now.. =D
What I did to fix this problem:

[LIST=1]
[*]Download the wubi installer from ubuntu website.
[*]Run the installer ---  This isntaller will ask you automatically to deinstall the previous version.
[*]I deinstall the broken 12.04 version in my lappy.
[*]I installed the 12.04 as a new installation.
[/LIST]

And.. It succeed.. =D Thank you very much for your help, and hopefully my experience can be useful also for others.. :)

Regards, Babyzilla

---

### Post by Viszketeg on 2012-05-22
> **Babyzilla said:**
> thank you jadtech for your reply.

I would like to try to put that command, but do you have any idea how can I access the terminal? Since the screen leave me with no options avalaible..

I had the same issue. It was possible to switch to the text based terminal with Ctrl-Alt-F1 after login. There I logged in with my userid and password. I was able to fix the installation with the apt-get commands.

---

