---
title: "After latest update: screen goes black after logging in"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by Stef@n on 2007-04-06
Guys,

I updated Ubuntu (edgy) two days ago. Shut down my system. Powered up today, logged in and the screen goes black and throws me back to the login screen again. I think it has something to do with Beryl loading on startup or something. This keeps repeating itself and I am unable to get to the desktop.

Anybody have any clue what going on?

---

### Post by Msvictim on 2007-04-06
Hey, 

  Just to let you know, I've got the same problem.  This past Wednesday (4-4-07) I  got some updates  then powered off  came back to the machine this morning and yep logs in like it should but before it starts throwing icons up on the desktop it wipes to a blank screen with a cursor. I then login on text display then after a few moments it goes back to the graphic login screen goes through same thing then dumps me back to my text display and repeats the process. So how can I find out what the last updates were, and uninstall them?

thanks in advance.

MSV

***Update, after I remove beryl I was able to move about my desktop however I found my desktop still wiping when I tried to run applications that requires opengl. It appears to be a video driver issue so looks like it might need the latest Nvidia opengl drivers.

*** Update, well after examining other threads and little googling I was suspicious of Beryl so I found out how to remove beryl and once I did my Desktop came back to me.  

Heres a link to that site [http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html](http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html)

And if you can't get to there here are the steps they listed:

sudo aptitude remove --purge-unused beryl emerald emerald-themes
sudo aptitue autoclean
rm -r ~/.beryl
rm -r ~/.emerald
rm ~/.beryl-managerrc

too bad for beryl =(

---

### Post by Stef@n on 2007-04-07
Thanks Msvictim for your info.

But it didn't resolve my problem. I think it didn't remove beryl properly, because when i'm in recoverymode and type startx, beryl-manager and emerald are still showing up under 'applications'  and 'system'.

I read somewhere to reinstall the nvidiadrivers. So I used the 'envy'-script, but with no succes.

Tips anyone?

---

### Post by bigken on 2007-04-07
you could try sudo apt-get update the sudo apt-get upgrade

if this dont work try sudo dpkg-reconfigure -phigh xserver-xorg and select vesa as your driver this should at least get you to a desktop

---

### Post by Wolfiger on 2007-04-08
I had the exact same problem but was able to fix it quickly fallowing the steps on this forum...
[http://ubuntuforums.org/showthread.php?t=403164&highlight=uninstall+nvidia+driver](http://ubuntuforums.org/showthread.php?t=403164&highlight=uninstall+nvidia+driver)

Just had to restore nvidia's libglx.so file.

---

