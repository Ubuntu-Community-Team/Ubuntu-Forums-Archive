---
title: "terminal will not let me login as root"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by jjb945025 on 2010-10-26
when i attempt logging in as root i get this message...su: Authentication failure. are there any experienced users out there that can help me overcome this problem; i'm trying to install my video drivers and need to login as root before i can attempt this. thanks.

---

### Post by DaithiF on 2010-10-27
In Ubuntu we use sudo rather than su.

see [https://help.ubuntu.com/community/RootSudo#sudo](https://help.ubuntu.com/community/RootSudo#sudo)
for more info

---

### Post by jjb945025 on 2010-10-27
i typed in sudo and this is what i got: joe@joe-desktop:~$ sudo
usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-p prompt]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U username] [-u
            username|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...


sorry to bug ya bro but what does all this mean, i just want to get the video drivers installed. shouldn't terminal ask me for a password after i type in "sudo"  ?

---

### Post by deanjm1963 on 2010-10-27
just type sudo before the command you wish to use for root, e.g. this is what I would do to copy icons to my /usr/share/icons folder

```
sudo cp iconname.png /usr/share/icons/
```

it then asks for your user password

---

### Post by oldos2er on 2010-10-27
```
sudo -i
``` will give you a persistent root terminal.

---

### Post by coffeecat on 2010-10-27
> **jjb945025 said:**
> i typed in sudo and this is what i got: joe@joe-desktop:~$ sudo

....

sorry to bug ya bro but what does all this mean, i just want to get the video drivers installed. shouldn't terminal ask me for a password after i type in "sudo"  ?

DaithiF posted you a link which explains all you need to know about using sudo and the Ubuntu security model. Did you not read it?

---

### Post by jjb945025 on 2010-10-27
hey i got it. thanks for all your help everyone! now i gotta do some more **** b4 i can install the drivers. i'm gonna figure this out on my own though, you guys have done enough for me. thanks again.

---

### Post by jjb945025 on 2010-10-28
ok i'm back. linux is a real pain in the *** ya know? i like it because it does all windows did for me but when it comes to installing ****... thats a whole different story. i'm not giving up though, i just need more help because after reading installation instructions, nothing worked at all; anything i was told to do that is. do ya think this may be why i'm getting discouraged? ok down to business i guess.. i'm trying to instal nvidia driver "nvidia-linux-x86-96.43.18.pkg1.run" and after shutting down the x server and logging in as root, which you guys taught me to do, i got some ******** message, oh " cannot open nvidia-linux-x86-96.43.18.pkg1.run. lol, great i thought. do you guys think i have a bad install or something.. i mean wtf could possibly be wrong now? i've followed all instructions. however  i do have a question...after i shut down x, what environment am i in? and if by some mysteriuos rare occurrance i do happen to get the nvidia drivers to install , does anyone know what happens next? like if im still in the "environment", whatever it is how do i get out of it and back into the graphical ubuntu environment.i dont know what to do now.. any suggestions?

---

### Post by coffeecat on 2010-10-28
I think you're making life  difficult for yourself. If you want to install the proprietary driver, just go to System > Administration > Hardware Drivers (in Lucid) - or Additional Drivers (in Maverick) and let Ubuntu do it for you.

Similarly, if you want to install extra software, don't commit the newbie mistake of downloading source code and wondering why it's more difficult than in Windows. Use Applications > Software Centre, or System > Adminstration > Synaptic and learn how much easier it is than in Windows.

---

### Post by sisco311 on 2010-10-28
[uhelp]community/BinaryDriverHowto/Nvidia[/uhelp]
[uhelp]community/NvidiaManual[/uhelp]

---

