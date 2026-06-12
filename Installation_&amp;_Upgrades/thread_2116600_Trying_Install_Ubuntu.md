---
title: "Trying Install Ubuntu"
date: 2013-02-16
forum: Installation &amp; Upgrades
---

### Post by testescp on 2013-02-16
Hi Forum.


I'm trying to install Ubuntu on a old machine with the following hardware:
Intel P4 2,6
Asus p4 v800-x
Nvidia geforce fx 5200
crt monitor Samtron 76E

I always got the same message box "out of range". 

I already tried to install using CD and using windows installer.

Even when i selected "try without install" from cd i got that message.


Really need help. Please post answers with full steps (windows user without knowledge on linux).


Ty in advance

---

### Post by carl4926 on 2013-02-16
As soon as the cd boots press Esc and
[https://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_boot/2013-02-10%2008.43.17.jpg](https://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_boot/2013-02-10%2008.43.17.jpg)

Then after selecting lang
Press F6 and
[https://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_boot/2013-02-10%2008.44.40.jpg](https://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_boot/2013-02-10%2008.44.40.jpg)

select nomodeset

see if that helps

---

### Post by testescp on 2013-02-16
Carl4926,


Yes, it did worked, at least selecting "try without install". Now it's time to lunch, so will install it during the afternoon.

Ty for the help.

---

### Post by ajgreeny on 2013-02-16
Once you have installed you will possibly still need to boot with the nomodeset option in order to get to a GUI.

You can do that most easily by keeping the live system booted, then double clicking the newly installed root partition, which you will see in nautilus's left hand pane just as a partition, it will not tell you it's Ubuntu, but open it up and if it contains bin, boot, dev, etc, home, etc etc, it is the right one.

You will need to open the /etc/default/grub file on that partition with root permissions (You will have to find the partitionname yourself, I'm afraid, as it could be a long UUID string) by using a terminal command```
gksudo gedit /media/***partitionname***/etc/default/grub
``` and edit the line ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` to read ```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset quiet splash"
```
You should now be able to boot to your installed system the same as you did the live system.

---

### Post by sudodus on 2013-02-16
> **testescp said:**
> Hi Forum.

I'm trying to install Ubuntu on a old machine with the following hardware:
Intel P4 2,6
Asus p4 v800-x
Nvidia geforce fx 5200
crt monitor Samtron 76E
...

Welcome to the Ubuntu Forums :-)

I see that you have managed to run a live session using the boot option nomodeset. It is also worth considering which version (12.04 or 12.10) and flavour [vanilla] Ubuntu, Kubuntu, Lubuntu or Xubuntu, that would be the best.

Lubuntu has the ultra light-weight desktop environment LXDE
Xubuntu has the light-weight desktop environment XFCE

and these flavours are good alternatives for aging computers.
--
How much RAM is there in your computer?

If you get problems during installation, Maybe you have too little memory to install in graphics mode. In that case you can download the alternate installer, that will need less RAM to work.

---

### Post by testescp on 2013-02-16
> **ajgreeny said:**
> Once you have installed you will possibly still need to boot with the nomodeset option in order to get to a GUI.

You can do that most easily by keeping the live system booted, then double clicking the newly installed root partition, which you will see in nautilus's left hand pane just as a partition, it will not tell you it's Ubuntu, but open it up and if it contains bin, boot, dev, etc, home, etc etc, it is the right one.

You will need to open the /etc/default/grub file on that partition with root permissions (You will have to find the partitionname yourself, I'm afraid, as it could be a long UUID string) by using a terminal command```
gksudo gedit /media/***partitionname***/etc/default/grub
``` and edit the line ```
GRUB_CMDLINE_LINUX_DEFAULT=&quot;quiet splash&quot;
``` to read ```
GRUB_CMDLINE_LINUX_DEFAULT=&quot;nomodeset quiet splash&quot;
```You should now be able to boot to your installed system the same as you did the live system.

    Sorry for the late answer, but only got time to install it at this time. 

ajgreeny,    
Yes you was right, i had to change the grub file after installation.   I had to do a little diferent from what you said, instead of using gksudo...... i used sudo gedit then opened the file, saved the changes and run sudo update-grub. Now i can run ubuntu without problems.       


Sudodus, 
 2GB ram, what you think? Right now ubuntu runs a little slow. Thought it would be much faster.


 Ty all for the help im getting.



 Now, i need help on 2 more things: 

1-Ubuntu runs a little slow, tweaks, ways to improve, other vanilla? 
  2- I already read some threads/tutorial about linux and ubuntu. Wich tutorials/threads/websites you can advice for me to start learning linux in depth.       
Ty again

---

### Post by sudodus on 2013-02-16
> **testescp said:**
> 
Sudodus, 
 2GB ram, what you think? Right now ubuntu runs a little slow. Thought it would be much faster.

2 GB is enough. I think the cpu is a bottleneck. Or the graphics. What graphics driver are you running (is it nouveau, or a proprietary nvidia driver)? Check with ***jockey-gtk*** if it is installed.
>  ...
 Now, i need help on 2 more things: 

1-Ubuntu runs a little slow, tweaks, ways to improve, other vanilla? 
  2- I already read some threads/tutorial about linux and ubuntu. Wich tutorials/threads/websites you can advice for me to start learning linux in depth.       
Ty again
Lubuntu and Xubuntu will run faster on your computer. I suggest that you try them. The clean way is to download their iso files and make boot CD/USB drives and test them live. It is also possible to install these desktop environments into your present Ubuntu installed system. Then you can select desktop environment at the log in screen.

```
sudo apt-get install lubuntu-desktop
```
```
sudo apt-get install xubuntu-desktop
```

If you want the get a pure flavour, use the tips at this link

[[COLOR="Red"]http://www.psychocats.net/ubuntu/index[/COLOR]]("http://www.psychocats.net/ubuntu/index")

This link has also several links to other web-sites describing linux and Ubuntu.

It is rather easy to browse the internet for good ***linux tutorials*** and ***linux books***. If you specify details, what you want to learn about (in a reply here), you can get more specific tips.

---

### Post by testescp on 2013-02-16
> **sudodus said:**
> 2 GB is enough. I think the cpu is a bottleneck. Or the graphics. What graphics driver are you running (is it nouveau, or a proprietary nvidia driver)? Check with ***jockey-gtk*** if it is installed.

Lubuntu and Xubuntu will run faster on your computer. I suggest that you try them. The clean way is to download their iso files and make boot CD/USB drives and test them live. It is also possible to install these desktop environments into your present Ubuntu installed system. Then you can select desktop environment at the log in screen.

```
sudo apt-get install lubuntu-desktop
``````
sudo apt-get install xubuntu-desktop
```If you want the get a pure flavour, use the tips at this link

[[COLOR=Red]http://www.psychocats.net/ubuntu/index[/COLOR]]("http://www.psychocats.net/ubuntu/index")

This link has also several links to other web-sites describing linux and Ubuntu.

It is rather easy to browse the internet for good ***linux tutorials*** and ***linux books***. If you specify details, what you want to learn about (in a reply here), you can get more specific tips.

   Sudodus,   jockey-gtk wasnt installed so i installed it, however after saying installaction done i rerun the command and says it isnt installed. I installed for second time, and the problem continues. Already searched and seems to be a bug on the 12.10 version ([https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/1028361](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/1028361))     About lubuntu and xubuntu i will try to install them tomorrow or monday night. I have been reading comparisons betweeen the 2, and i will try first xubuntu.

---

### Post by carl4926 on 2013-02-16
If you still have nomodeset in action, we have to ask...
What graphics device do you have?

---

### Post by testescp on 2013-02-17
The device is Nvidia geforce fx5200. However cant use the commmand jockey-gtk to know what drivers are installed.

---

### Post by sudodus on 2013-02-17
> **testescp said:**
> Sudodus,   jockey-gtk wasnt installed so i installed it, however after saying installaction done i rerun the command and says it isnt installed. I installed for second time, and the problem continues. Already searched and seems to be a bug on the 12.10 version ([https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/1028361](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/1028361))     About lubuntu and xubuntu i will try to install them tomorrow or monday night. I have been reading comparisons betweeen the 2, and i will try first xubuntu.
That is a good idea :-)

Instead of jockey-gtk you might try either jockey-text or glxinfo

```
sudo apt-get install jockey-common
```
Post the output of the following command
```
jockey-text -l

```or if the jockey-text version is also affected by the bug
```
sudo apt-get install mesa-utils
```
Post the output of the following command
```
glxinfo|grep -i opengl
```

*Edit*: By the way, on your computer, I think there will be more advantages than disadvantages to run the version 12.04 instead of 12.10. Jockey works, and there are many more things, more important ones, that are debugged and working in 12.04

---

### Post by testescp on 2013-02-17
Post the output of the following command
[CODE]jockey-text -l
  Output of command:  kmod:nvidia_173 - NVIDIA binary Xorg driver, kernel module and VDPAU library (Proprietary, Disabled, Not in use) kmod:nvidia_173_updates - NVIDIA binary Xorg driver, kernel module and VDPAU library (Proprietary, Disabled, Not in use)     Seems to be nvidia driver installed but not in use.   Ty

---

### Post by sudodus on 2013-02-17
See ```
jockey-text -help
``` to get help how to install a proprietary driver.

You might need superuser privileges so use sudo. I suggest that you try

```
sudo jockey-text -e 'driver-name'
```

Try first the driver-name without updates, and if it is good, use that one. Try with and without the prefix kmod: (I did it once long ago, but don't remember exactly.)

kmod:nvidia_173
kmod:nvidia_173_updates

This might work well, but it might also break your graphics. Then you have the possibility to reset it to the built-in graphics driver running in text mode, and go for light-weight desktop environments instead.

---

### Post by testescp on 2013-02-17
By the way, on your computer, I think there will be more advantages than disadvantages to run the version 12.04 instead of 12.10. Jockey works, and there are many more things, more important ones, that are debugged and working in 12.04[/QUOTE]
  Nice to know.   But Xubuntu will run smoother than the ubuntu version 12.04, right?  What i want for this old pc, is a fast OS, and a way to start learning linux.  I have a good laptop with windows 7 64bits, and for now i dont want to put linux on the laptop. I want to learn first on the old pc before changing my laptop OS.

---

### Post by testescp on 2013-02-17
```
sudo jockey-text -e 'driver-name'
```Try first the driver-name without updates, and if it is good, use that one. Try with and without the prefix kmod: (I did it once long ago, but don't remember exactly.)

kmod:nvidia_173
kmod:nvidia_173_updates

  Done, i used the prefix kmod, with the driver without the updates (kmod:nvidia_173), Run the command jockey-text -l, and now the driver is enabled. however its says not in use  Output of command jockey-text -l kmod:nvidia_173 - NVIDIA binary Xorg driver, kernel module and VDPAU library (Proprietary, Enabled, Not in use)

---

### Post by sudodus on 2013-02-17
> **testescp said:**
> ```
sudo jockey-text -e 'driver-name'
```Try first the driver-name without updates, and if it is good, use that one. Try with and without the prefix kmod: (I did it once long ago, but don't remember exactly.)

kmod:nvidia_173
kmod:nvidia_173_updates

  Done, i used the prefix kmod, with the driver without the updates (kmod:nvidia_173), Run the command jockey-text -l, and now the driver is enabled. however its says not in use  Output of command jockey-text -l kmod:nvidia_173 - NVIDIA binary Xorg driver, kernel module and VDPAU library (Proprietary, Enabled, Not in use)

I think you need to restart X (at least) or to be sure reboot the computer.

---

### Post by sudodus on 2013-02-17
> But Xubuntu will run smoother than the ubuntu version 12.04, right? 

 Yes :-)

---

### Post by carl4926 on 2013-02-17
> **sudodus said:**
> But Xubuntu will run smoother than the ubuntu version 12.04, right?

Yes :-)

I'm using xubuntu 12.10 on a netbook and it's wonderful

---

### Post by manishiitg on 2013-04-30
you need to install [COLOR=#000000]jockey-gtk from apt[/COLOR]

---

