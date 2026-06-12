---
title: "Enable Nouveau NVIDIA driver on Ubuntu 18"
date: 2021-12-01
forum: Installation &amp; Upgrades
---

### Post by net-alexander on 2021-12-01
I have some problems in the graphics part, I did something by copying and pasting code (I really don't know what I did) it was a step to install an emulator to play. If someone understands the codes and helps me restore what I did, it would be helpful:


Here what I did:


How to disable Nouveau nvidia driver on Ubuntu 18.04 Bionic Beaver Linux.
Instructions
Blacklist Nvidia nouveau driver
Open up terminal and enter the following linux commands:


```
 $ sudo bash -c "echo blacklist nouveau> /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
 
```


```
$ sudo bash -c "echo options nouveau modeset = 0 >> /etc/modprobe.d/blacklist-nvidia-nouveau.conf"



```




Confirm the content of the new modprobe config file:


```
$ cat /etc/modprobe.d/blacklist-nvidia-nouveau.conf



```




it should show something like this:
blacklist nouveau
options nouveau modeset = 0








Update kernel initramfs
Enter the following linux command to regenerate initramfs:


```
$ sudo update-initramfs -u



```


Reboot
All should be ready now. Reboot your system:


```
$ sudo reboot



```

:?::confused: [COLOR=#202124][FONT=inherit]Help[/FONT][/COLOR][COLOR=#202124][FONT=arial]



*[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABQAAAAUCAQAAAAngNWGAAAA/0lEQVR4AYXNMSiEcRyA4cfmGHQbCZIipkuxnJgMStlMNmeyD2dwmc8 sZgxYJd9ErIZFHUyYYD7fkr6l4/rnvmtl7 KitrqV/fq2Y5eLY3Z9S48eRLe7BmVZ9qhTLhQ0algzZWQOVKSsCF8OjAnwbxDTWFDUhPK/jMr1H6HE/IqRky2DyvCefuwItwZzodVoYRiLqMkVCXrwpJ9twZ sgfDYEFYl8wIWxZ9uFf7zkallxlJh4YrLGsKjZRx7VGHhLqwgFUN45DGdb8MeXGpgB4ABZdeDcpZEY51A hyLKz4S1W4MQWm3AibWtgWmk6dyISa1pSdyWTOlLXVp0 eL9D/ZPfBTNanAAAAAElFTkSuQmCC[/IMG]*


[COLOR=#70757A]
[/COLOR][COLOR=#70757A]
[/COLOR]











[/FONT][/COLOR]

---

### Post by MAFoElffen on 2021-12-02
To reverse that...

Since you did that and are having problems graphically, boot in recovery  mode from the "other options:" in the Grub Boot menu, then drop down to  a root prompt.

Edit the /etc/modprobe.d/blacklist-nvidia-nouveau.conf file and remove the lines that say:
```
blacklist nouveau
options nouveau modeset = 0

```
...from that file, then rebuilt your intrafs file
```
sudo update-initramfs -u
sudo reboot

```

---

### Post by KBar on 2021-12-02
```
sudo bash -c "echo blacklist nouveau> /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
```

This command created that file file through the means of redirection. You can just delete it and update initramfs. 

How we can do it is another question. Tell us exactly what you're seeing when you boot up your machine. Does it at least start the graphical interface and present the login page, or do you only see a black screen with a blinking cursor?

---

### Post by ActionParsnip on 2021-12-02
Add the boot option "nouveau.blacklist=1" should do it

---

### Post by MAFoElffen on 2021-12-02
Actually the first question should have been what Video GPU do you have?

Then second question should have been where do you get your instructions? Because what you posted would have failed, just basedon the extra spaces around thwe equals sign, so if it did fail, it would have been a false negative. There are no spaces in those parameters.

Yes, deleting it would have also reversed it...

---

### Post by net-alexander on 2021-12-02
Hi, thanks at this time I was able to start the operating system normally, my problem occurs when important updates of 'ubuntu' are installed and because I also download and install the graphics drivers manually from the 'nvidia' page. I already have a list of steps to follow, if there are doubts (I hope not) I will return to the support forum .. Thank you

G: NVIDIA GK208B [GeForce GT 710]

---

### Post by MAFoElffen on 2021-12-02
> **net-alexander said:**
> Hi, thanks at this time I was able to start the operating system normally, my problem occurs when important updates of 'ubuntu' are installed and because I also download and install the graphics drivers manually from the 'nvidia' page. I already have a list of steps to follow, if there are doubts (I hope not) I will return to the support forum .. Thank you 

G: NVIDIA GK208B [GeForce GT 710]

So this is 'Solved'? If so, then go to the Thread Tools and remember to mark the thread as "solved" so others can find your solution to help them...

---

### Post by wildmanne39 on 2021-12-02
Hello net-alexander, you have posted in an English specking forum only, please translate all posts in the future or post in one of our sub-forums in your own language.

Thanks

---

