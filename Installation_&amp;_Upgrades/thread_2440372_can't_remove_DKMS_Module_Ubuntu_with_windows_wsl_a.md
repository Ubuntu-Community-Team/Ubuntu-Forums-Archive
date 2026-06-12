---
title: "can't remove DKMS Module: Ubuntu with windows wsl and failed nvidia-440 installation"
date: 2020-04-09
forum: Installation &amp; Upgrades
---

### Post by diallobakary4 on 2020-04-09
Hello,

I am using ubuntu 16 on Windows wsl. 
I tried to install the cuda toolkit which include nvidia-440 driver but the installation failed.
Now I can't install any other package. Every new installation trying to install nvidia-440 ```
Setting up nvidia-440 (440.33.01-0ubuntu1) ...
```.
I am retrying to remove all dependencies associated with.
So I tried the command ```
sudo apt-get purge 
dpkg --purge --force-remove-reinstreq 
``` and its freezed at ```
Removing all DKMS Modules
``` for "ever" similarly to this [thread]("https://ubuntuforums.org/showthread.php?t=1431234").
I have tried as root without success.

Any help will be appreciated.
Best regards

---

### Post by deadflowr on 2020-04-09
Did they magically fix it to even allow cuda on WSL?
That said,
I would think the benefit of WSL is the ability to simply reset or revert the subsystem.
Perhaps nuke it and start over.
Does this still apply:
[https://askubuntu.com/questions/761360/how-do-i-reset-my-installation-of-ubuntu-on-windows]("https://askubuntu.com/questions/761360/how-do-i-reset-my-installation-of-ubuntu-on-windows")

(I don't use windows, so obviously  I don't use WSL either.)

---

### Post by diallobakary4 on 2020-04-10
I first tried repairing it which did not work. Now about reset, I hope this won't remove all already installed packages and configurations in the bashrc?

---

### Post by QIII on 2020-04-10
My guess is that doing that would clear everything.

Take note of all the packages you have installed (I'm not sure how wsl works, but you should be able to look at /var/log/dpkg.log at the very least) and copy the text of your .bashrc to save it.

---

### Post by diallobakary4 on 2020-04-11
Ok thank you. I am saving the .bashrc file.
Is there a way to save the system as image.
I am thinking about installing ubuntu 18 and load packages, configurations and the current conda environment from the 16.

---

### Post by diallobakary4 on 2020-04-21
It was finally solved using the approach here : [https://askubuntu.com/questions/603295/how-to-fix-dpkg-error-2](https://askubuntu.com/questions/603295/how-to-fix-dpkg-error-2)
In the case here the entries to clean were related to cuda and nvidia. After what everything seems to work fine now.
Thanks

---

