---
title: "Ubuntu boot problem TX2010"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by Olsber on 2008-04-20
Just installed Ubuntu 7.10 on my tx2010 pavilion. I'm running a dual boot with Vista on the machine, and the problem is that Ubuntu takes aprox. 10min to start. It's all works fine when it's finally comes up, everything works as it should. The Vista installation also works fine. The boot prosess seems to work, I get the Boot loader, and can pick the both the OS'es. The Vista boot have no trouble, but the Ubuntu takes 10min to start... the screen just go black and nothing happens for at least 10mins.. and then suddenly the disk starts spinning and I get the logon screen. 

Welll got the most of it to work, haven't yet got the touchscreen to work. I installed manually the broadcom wireless network adaptor, just followd this thread: [http://ubuntuforums.org/showpost.php?p=4411351&postcount=1](http://ubuntuforums.org/showpost.php?p=4411351&postcount=1) and it worked fine.

But why it takes 10mins to boot, I really should like to know.. any suggestions??

- gemba

---

### Post by Partyboi2 on 2008-04-21
try checking the usplash settings.
```
gksudo gedit /etc/usplash.conf
```you should see something like
xres=1024                                                                                                                    
yres=768 
which is 1024x768 screen resolution.
Make sure that your screen can support these settings if not change to the correct settings for your screen and save.
then
```
sudo update-usplash-theme usplash-theme-ubuntu
```
You could also try [this]("http://ubuntuforums.org/showthread.php?t=89491") to speed up the boot process.

---

### Post by Olsber on 2008-04-21
Thanks.. it was the graphics to blame.. 

It turned out that I had to enable the nvidia graphics driver from the restricted drivers section first.. and there it was.. Next boot all worked fine, took 30sec..

A bit strange, had the same thing happen when I started the installation with the boot Live-CD..the screen went black for 10mins and suddenely it woke up and I could contiune the installation.. didnt think it worked at all..  Well, next problem is to get the audio working and the rest to function....

-g

---

