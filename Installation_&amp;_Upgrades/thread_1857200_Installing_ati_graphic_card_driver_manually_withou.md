---
title: "Installing ati graphic card driver manually without internet connection"
date: 2011-10-09
forum: Installation &amp; Upgrades
---

### Post by maizuddin35 on 2011-10-09
Hello everyone.

I just want your help on this ...
I want to remove my nvidia driver from my ubuntu
and install an ati driver manually without an internet connection.
Well I already downloaded the driver from ati website 
this is the file name , "ati-driver-installer-11-9-x86.x86_64.run"
how can I actually install this driver without any internet connection. Right now Im at my work place and for the time being I can download and access to the internet .

Thank you in advance :)

p/s : Im using ubuntu 11.04 classic mode, ati radeon hd 5770

---

### Post by maizuddin35 on 2011-10-09
can you guys tell me, what should I do first, the procedure on making it right?
I'm not quite understand when I check this out , here [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by maizuddin35 on 2011-10-11
well, the procedure was not hard at all ,unlike installing nvidia driver.
I just download the latest driver at the ati/amd website. and then make the download file executable, and run it in the terminal. and make sure that there are no graphic driver installed if you do, you'll need to remove it first or force to overwrite the current driver .solved

---

### Post by Dear.Devil on 2011-10-22
hey dude, we have the same problem about that graphic.
can you tell how to install that binary in ubuntu? seriously, i'm a new comer in ubuntu. i don't know what to do.
thank's before.

---

### Post by MAFoElffen on 2011-10-22
> **Dear.Devil said:**
> hey dude, we have the same problem about that graphic.
can you tell how to install that binary in ubuntu? seriously, i'm a new comer in ubuntu. i don't know what to do.
thank's before.
Full instruvctions here on my sticky:
[http://ubuntuforums.org/showpost.php?p=10950714&postcount=334](http://ubuntuforums.org/showpost.php?p=10950714&postcount=334)

---

### Post by Dear.Devil on 2011-10-23
well, i've installed ati driver in this machine, but it's still can't enable desktop effect. what i have to else dude?
sorry if out of topic, i really need somehelp here :(

---

### Post by registerkar on 2011-10-23
Well I too have a ATI Card...I have installed with internet connection...i was shown 2 options...ATI Driver & ATI driver (post release updates)...1st gets installed...post released updates does not get...it shows a error...so i switch back to 1st...prob is it still shows VESA M92 as drivers but even the ATI Panel shows...so ATI Driver is installed, but is not used maybe...dont know whats happening

---

### Post by Dear.Devil on 2011-10-23
^
that's it.
**It's installed, but nothing happen.**

---

### Post by maizuddin35 on 2011-10-23
well sorry for the delay. 
my problem is solved now actually.

well, what I did was..I remove the current graphic driver in my system by : 
```
sudo apt-get remove --purge fglrx
```

and then, make an 'ati' folder, just do this in your terminal
```

cd
mkdir ati
cd ati
wget http://www2.ati.com/drivers/linux/ati-driver-installer-11-9-x86.x86_64.run

```

wait till the download to finish 
and do this 
```

sudo sh ati-driver-installer-11-9-x86.x86_64.run --buildpkg Ubuntu/oneiric
sudo dpkg -i ati*.deb
sudo aticonfig --initial -f

```

this will extract the .deb packages from the .run file , at the end of "--buldpkg" you need to specify your ubuntu version.

then try to 
sudo update-grub

then reboot your system.

---

