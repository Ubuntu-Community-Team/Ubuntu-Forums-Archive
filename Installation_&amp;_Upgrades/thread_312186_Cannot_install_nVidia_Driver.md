---
title: "Cannot install nVidia Driver"
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by vze4p6c2 on 2006-12-04
Hello comrads,

I have a little problem with installation of nVidia driver.  It was simple with SuSE but not with Ubuntu.  Basically, I downloaded the .run file, and attempted to use sh command in shell to install, as instructed in the install maual at nvidia.com.  I get however the message that I am running the "x server".  I'm not sure what that is, but I tried to run it in emulator and in real shell (Alt + Ctrl + F1) and still get the same message.  I've attached that picture of an emulator (can't take snapshot of real shell).  Please help me out installing the driver.  I have nVidia 4000MX (old)

Thanks, Vlad

attachment

---

### Post by Jimmey on 2006-12-04
It's easier to install the driver from the repositories.

First, check that the multiverse repository is enabled. 

Once you have made sure that it is, you can 
> sudo apt-get install linux-restricted-modules-$(uname -r); sudo apt-get install nvidia-glx-legacy; nvidia-glx-config enable

[EDIT]
You said your card's old, so it's probably supported by the legacy driver. If it's in [this list]("http://download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-a.html"), then the commands I posted above should work perfectly.

Once that's complete, if you press "CTRL + ALT + BACKSPACE" and an nVidia splash screen comes up, you're all done.

---

### Post by deeptingler on 2006-12-04
try this if you have probs with the above as it didnt work for me due to deprecation

sudo apt-get install nvidia-glx
sudo nvidia-xconfig

then reboot or restart X as above like Jimmey says and look for the nvidia logo to flash up

---

### Post by ickyfeet on 2006-12-04
if you want to install it manually you've got to stop X before you install the driver.  download the driver, then hit ctrl+alt+f1, login then:

sudo /etc/init.d/gdm stop

now you can run your driver installation file.  after it has been installed then you can restart x by typing

sudo /etc/init.d/gdm start

i had to use this method to get beryl to work on my system.
if X crashes and you can't get back to the gui then run

sudo apt-get install nvidia-glx

from the terminal then try restarting x again

---

### Post by vze4p6c2 on 2006-12-04
I almost got it to work, but something awry has gone....

I've attached some of the messages it sent out to me.

(Because of 2MB per pic I had to use my FTP server)

Here are the pictures in order:

[URL="http://familytess.org/P1010841.JPG"]PIC1
[/URL]
[PIC2]("http://familytess.org/P1010842.JPG")
[URL="http://familytess.org/P1010843.JPG"]PIC3
[/URL]
[PIC4]("http://familytess.org/P1010844.JPG")

Sorry guys to make you open all that.

Thx

---

### Post by Simon4tk on 2006-12-10
> **deeptingler said:**
> try this if you have probs with the above as it didnt work for me due to deprecation

sudo apt-get install nvidia-glx
sudo nvidia-xconfig

then reboot or restart X as above like Jimmey says and look for the nvidia logo to flash up

I tried this to resolve problems with my FX5500 and it worked fine...until I rebooted when I am back with only 640x480 resolution. Is there another step I am missing?

---

