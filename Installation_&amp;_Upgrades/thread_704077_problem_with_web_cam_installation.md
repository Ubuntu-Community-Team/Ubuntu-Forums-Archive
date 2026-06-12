---
title: "problem with web cam installation"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by aju_1112 on 2008-02-22
hi'
i am new to linux and i am installing logitech rightlight webcam which is working in xp and vista,
i am trying to install it but i don't know how to install and how to unzip the file of it in linux,so please tell me how can i do that

Thanks in advance guys:

confused:

---

### Post by linuxwizard on 2008-02-22
Have you tried using the webcam with any programs ? Try using Ekiga to see if cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.

---

### Post by Pumalite on 2008-02-22
You can also try installing ·"camorama"

---

### Post by aju_1112 on 2008-02-22
thnaks for reply i already going to install camaroma but it told me unpack the file but i don't now exactly how to unpack that and second think is that i have logitech web cam so i have to intall driver first or what i don't know exact how to do

Thanks in advance

---

### Post by Pumalite on 2008-02-22
Camorama is in the repos.

---

### Post by linuxwizard on 2008-02-22
aju_1112
Alot of Logitech webcams & other webcams just works out of the box. You may not have to install any drivers. You need to try using it first. Ekiga is already installed by default and works very well. That is why I asked you to try it, you didn't need to install anything else.

---

### Post by aju_1112 on 2008-02-22
i use ekiga but web cam is not working i don't know because it nothin show me any thing please advice i install carmon but i don't know how to unzip the file of camon i send u side from wherte i am using this 


[http://www.debianadmin.com/how-to-configure-webcam-in-debian-linux.html](http://www.debianadmin.com/how-to-configure-webcam-in-debian-linux.html)

in this i don't know how to unpack that file

---

### Post by linuxwizard on 2008-02-22
What are you still trying to install Camorama ? If you do like Pumalite said it is in the repo. Go to System > Administration > Synaptic Package Manager > click on search type >  Camorama. IMO you have a better chance getting your cam to work with Ekiga than Camorama.

---

### Post by Pumalite on 2008-02-22
Once you install camorama through Synaptic, go to the Terminal and type camorama. Your camera will light up instantly.

---

### Post by roxie on 2008-02-28
ok i am not sure how this works but am trying it. i bought a logitech BuddyCam webcam but it doesnt work and i dont know why. i installed everything from the cd, did exactly what they said to do.when it reached the part where it said to plug in the webcam, the program wasnt seeing it but the computer was....i tried exchanging the webcam but still the same thing happens....if u know what to do to solve this, please help. thank you

---

### Post by linuxwizard on 2008-02-28
First off the installation cd that came with your webcam with drivers is for windows not Linux. Plug the webcam in than go to Applications > Internet > Ekiga Softphone you cam should just work. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.

---

### Post by drworm01 on 2008-03-01
I'm likewise having trouble getting my webcam to function, only I don't know what kind it is. It came pre-installed on my laptop and the documentation I have for the machine is vague at bes Ekiga wouldn't show anything no matter how much fiddling I did and Camorama (from repos) gave me no love as well. Google didn't help much either. Best I could get was to run dmesg which produced this:

```
[   55.719050] uvcvideo: Found UVC 1.00 device USB2.0 Camera (0402:5606)
[   55.781027] usbcore: registered new interface driver uvcvideo
[   55.781030] USB Video Class driver (v0.1.0)
```

and shortly thereafter:

```
[   99.586033] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp. 26)

```

for about 20 lines.
Google brought up a mailing list discussion about uvcvideo development and advancements (or lack thereof) on 0402:5606, but a search for uvcvideo only led me to a German development page with SVN archives. 
I'm clearly in over my head. Can anyone help me or tell me what further details I need to provide to get help? 

Thanks for your time.

---

### Post by linuxwizard on 2008-03-01
drworm01
Post results of the command > lsusb

---

### Post by drworm01 on 2008-03-02
```
Bus 005 Device 002: ID 0402:5606 ALi Corp. 
Bus 005 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by linuxwizard on 2008-03-02
I can't find anything on your cam > Bus 005 Device 002: ID 0402:5606 ALi Corp. > only thing I can suggest is look in here > [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) > maybe give this driver a try it may or not work.

---

