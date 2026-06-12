---
title: "Fullscreen Video"
date: 2005-09-22
forum: Installation &amp; Upgrades
---

### Post by Blazer on 2005-09-22
Hi!

I hava a problem. I cant watch fullscreen Video, because when i go in fullscreenmode the movie is "cutting", it is not smooth video. 
I have VLC and Mplayer. 
And i have a Ati Radeon card and use "vesa" driver.

---

### Post by michael_salcher on 2005-11-05
what video mode are using? if you want to have fullscreen you should use "xv" as your video output mode (-vo=xv on the command line, or you can set it in preferences gui)

---

### Post by manicka on 2005-11-05
You might also need dma enabled if you are watching a dvd

[http://doc.gwos.org/index.php/DMA](http://doc.gwos.org/index.php/DMA)

---

### Post by ashrack on 2005-12-07
[QUOTE=Blazer]Hi!

I hava a problem. I cant watch fullscreen Video, because when i go in fullscreenmode the movie is "cutting", it is not smooth video. 
I have VLC and Mplayer. 
And i have a Ati Radeon card and use "vesa" driver.[/QUOTE]

Have the same problem. Have U fixed it?

I've xv set, and DMA enabled. Installed all the drivers from [http://help.ubuntu.com/starterguide/C/faqguide-all.html#codecs](http://help.ubuntu.com/starterguide/C/faqguide-all.html#codecs), and also Win32 codecs. Tried KAFFEINE, MPLAYER, TOTEM.But DIVX/XVID movies are still cutting in fullscreen. Although they work fine in Windowed mode. Using UBUNTU BREZY
Are there any fix?

---

### Post by Pablo_Escobar on 2005-12-07
What type of graphics card do You have ?
Did You enable 3D support ?

---

### Post by ashrack on 2005-12-07
[QUOTE=Pablo_Escobar]What type of graphics card do You have ?
Did You enable 3D support ?[/QUOTE]
Its a GF MOBILITY FX5500
Don't know about 3D SUPPORT but am sure I haven't changed anything since I only installed UBUNTU 3days ago and am not quite familiar with it --> first time user and a linux newbie

---

### Post by Pablo_Escobar on 2005-12-07
Then please, follow these instructions :
[http://ubuntuguide.org/#installnvidiadriver]("http://ubuntuguide.org/#installnvidiadriver")
and when Your done (or have a problem) report back.

---

### Post by ashrack on 2005-12-07
HAHA works now. Tanx man.
Have been strugling for a fix in this thread for 3days now:
[http://ubuntuforums.org/showthread.php?p=551519#post551519](http://ubuntuforums.org/showthread.php?p=551519#post551519)

---

### Post by Pablo_Escobar on 2005-12-07
Glad to be of service ashrack :)
Feel free to ask more questions if You encounter problems but Ubuntuguide is a good place to start looking for answers :)

---

### Post by ashrack on 2005-12-27
Why does FULLSCREEN video work so badly if I don't have NVIDIA installed?

---

### Post by manicka on 2005-12-29
[QUOTE=ashrack]Why does FULLSCREEN video work so badly if I don't have NVIDIA installed?[/QUOTE]

Do you have dma enabled?

What driver are you using?

---

### Post by ashrack on 2005-12-30
DMA is enabled. 
Am using the native "nv" drivers that came along with ubuntu. But with those drivers full screen is choopy. 
I would gladly switch to NVIDIA drivers, but they **** up hibernation and suspend.

---

