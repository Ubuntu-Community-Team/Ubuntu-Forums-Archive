---
title: "Convert 7.04 standard -&gt; UbuntuStudio?"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by Suthern on 2007-06-04
I bought a Dell 1505N with Ubuntu Feisty 7.04 installed. I'd like to convert it to UbuntuStudio (in other words, real-time support, all the tools..etc) without loosing my WiFi.

So far I've run across [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation) , but that dosen't seem to apply directly to Feisty. Plus, I'd rather not rebuild the kernel as that could break the WiFi support.

Can someone point me to the correct repository and program list to install? perhaps even a detailed How-to? ;-)

I'd really appreciate this. The main use of this machine will be to record multiple tracks of talking and instraments.

Thanks!
-Suthern

---

### Post by Suthern on 2007-06-05
And for anyone else who couldn't find it using the same search I did, but happens upon my post, here's a quote from "ep2011":

To "Upgrade" from feisty just run the 2 commands:

```

sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update
```
Then install the following packages with your favorite installer (apt-get, synaptic, aptitude, etc):

# ubuntustudio-desktop
# ubuntustudio-audio
# ubuntustudio-audio-plugins
# ubuntustudio-graphics
# ubuntustudio-video
# ubuntustudio-artwork
# ubuntustudio-gdm-theme
# ubuntustudio-icon-theme
# ubuntustudio-look
# ubuntustudio-session-splashes
# ubuntustudio-sounds
# ubuntustudio-screensaver
# ubuntustudio-theme
# ubuntustudio-wallpapers
# usplash-theme-ubuntustudio
# wired

---

### Post by gizmoarena on 2007-06-05
i tried those commands and getting this messages ...

> gizmo@ubuntu:~$ sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
gizmo@ubuntu:~$ wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update
OK
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:2 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
Get:3 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release [1304B]                   
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages                         
Get:4 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages [8822B]             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
Fetched 10.3kB in 22s (455B/s)
Reading package lists... Done
[COLOR="Red"]W: GPG error: [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release: The following signatures were invalid: BADSIG A361B38AB6A4EB33 Joseph Jackson IV (joejaxx) <jjacksoniv@fluxbuntu.org>
W: You may want to run apt-get update to correct these problems
[/COLOR]

now what??

[COLOR="Blue"]By the way, I have downloaded ubuntustudio-7.04-alternate-i386.iso but as I do not have any DVD burner, I can't burn it into a DVD. I can mount the iso file by Gmount-iso, but the I can't add it on repository. Is there any way of doing this?[/COLOR]

---

### Post by zvacet on 2007-06-05
You allready have some of these packages in synaptic.

---

### Post by gizmoarena on 2007-06-05
well i'm doing a trick ...
im copying all the .deb packages of ubuntustudio main folder into var/cache/apt/archives ...
this might save the time of downloading.

hope this would work.

---

### Post by gizmoarena on 2007-06-05
well it worked! :D 
i didn't need to download anything at all :D:D:D

lets see what happens next.

---

### Post by Suthern on 2007-06-05
I haven't acutally tried it yet (being at work), but intend to tonight.

I wonder if there's a way to add the GPG key via Synaptic. I think I'll search through the regular repos before adding more, and see what I come up with.

Let us know how it turns out gizmoarena.
-Suthern

---

### Post by Suthern on 2007-06-05
The update finished peacefully, and I was able to log out and back in again. Unfortunately it also updated the kernel to 2.6.20-16

That means that when I reboot, I get "Error 17: Cannot mount selected partition" on no matter what kernel I try from the grub list. Even the old 2.6.20-15-generic kernel gives me the same error.

The only way I can think of fixing it is to do a SYSTEM RESTORE from the grub, and that's NOT something I look forward too. It's not hard, but then I'd have to redownload everything, easyUbuntu, the whole works.

Isn't there some way to fix this stupid grub messup? I'm surprised more people have not run into it.

-Suthern

P.S. Even the Ubuntu, memtest86+ entry gives me the same error.. *sigh*

---

### Post by Suthern on 2007-06-06
And of course how to fix it? Change it to (hd0,2), and presto, it works!!!
Next I modified /boot/grub/menu.lst so that they all said (hd0,2) instead of 0,0. I did leave the "system restore" one alone at 0,1.

Then my WiFi didn't work, but was easy to fix. Fire up synaptic and download the restricted-modules-2.6.20-16-realtime thing, install, restart, and presto, my wireless works!

Conclusion: My INSPIRON E1505N is now running UbuntuStudio, latest kernel, with WiFi! Success at last.

Now to get JACK setup correctly.... ;-)

-Suthern

---

### Post by gizmoarena on 2007-06-20
oops, i didn't check this thread within last 2 weeks. sorry suthern.
I didn't had these problems. and I found the gpg keys from ubuntu studios official web's download section.

everything worked fine.

---

