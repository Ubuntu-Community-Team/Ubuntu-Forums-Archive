---
title: "no such file of directory"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by badmash on 2007-10-13
hi i am a new to ubuntu and i am using wubi to run ubuntu
the problume i have is that i cant install the latest nvidia drivers 
i have download the latest drivers from the nvida site and when i go to the command line and type "cd home/deskmash/desktop/nvidia-linux-x86-100.14.19-pkg1.run" it says "no such file or Directory" i dont know what is wrong!
i can follow direction but i cant get pass this step:confused:

---

### Post by zidane2 on 2007-10-13
try 
cd /home/deskmash/Desktop/
type that in exactly or copy and paste, if you type ls after typing that it should show the driver

---

### Post by oldos2er on 2007-10-13
You can't cd into a file. Type "cd home/deskmash/desktop/" then "sh nvidia-linux-x86-100.14.19-pkg1.run"

---

### Post by oxenfrogga on 2007-10-13
Hi badmash,

generally, I would recommend installing the drivers from the repository. Depending on the video card, the command would be (in the command line interface):

sudo apt-get install nvidia-glx

and afterwards

sudo nvidia-glx-config enable

Exchange "nvidia-glx" for "nvidia-glx-legacy" when you got an old nvidia card (if in question look at the description with -- for example -- apt-cache show nvidia-glx). Restart your X-server (by hitting CTRL+ALT+Backspace simultaneously or by rebooting) and that's it!

See you,
Harald

P.S.: The mistake you made was that you can't cd into a file (cd means change directory), so the right command line would be

cd /home/deskmash/desktop/

and then

sudo sh nvidia-linux-x86-100.14.19-pkg1.run

but -- as stated above -- sould not be necessary for you.

---

### Post by badmash on 2007-10-13
still when i type i get "-bash: cd: home/deskmash/desktop/: no such file or directory"


my system 
is amd 6000+
2gb ram
and 256 nvidia evga 8600
vista home premium with wubi ubuntu

---

### Post by badmash on 2007-10-13
now i moved the file to /home/deskmash/shared
and still when type "su nvidia-linux-x86-100.14.19-pkg1.run"
it says unknown id: nvidia-linux-x86-100.14.19-pkg1.run

plz help

---

### Post by oldos2er on 2007-10-13
>when i type i get "-bash: cd: home/deskmash/desktop/: no such file or directory">

 You forgot the "/" in front of "home;" should be cd /home/deskmash/desktop/ .

>when type "su nvidia-linux-x86-100.14.19-pkg1.run"<

 Should be sh nvidia-linux-x86-100.14.19-pkg1.run

---

### Post by badmash on 2007-10-13
now i am in the rigfht directory and know how to use cd command thanks. when i try to install teh driver for nvidia it says can't open. 
after when i type "sh nvidia-linux-x86-100.14.19-pkg1.run" ist says it "sh: can't open nvidia-linux-x86-100.14.19-pkg1.run"


am i doing something wrong or missing a step for installing a video driver for pci express 256 evga sli 8600:confused:

---

### Post by badmash on 2007-10-13
thanks for u help i fixed my problume
i found a program called envy with installed the drivers with one click 
envy is grate program for newbees. thanks:popcorn:

---

