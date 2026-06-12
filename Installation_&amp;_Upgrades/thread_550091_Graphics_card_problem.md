---
title: "Graphics card problem"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by Orfeus on 2007-09-13
When i tried to boot to the Ubuntu partition i got the message that xserver couldn't start. I tried reinstalling the nvidia drivers but i couldn't find nvidia from the list provided. I tried nv and vesa with no luck. Before that i installed compiz

any help?

---

### Post by w4ett on 2007-09-13
From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Blue"]"vesa"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This will get you to a GUI desktop. 

There are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager.

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

To use Envy navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:

```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to remove the old attempted driver installation and then install the correct Nvidia proprietary driver.

Good Luck

---

### Post by Orfeus on 2007-09-14
I ll try that but i think envy causes me other problems. I ll try it though...

Thanks

---

### Post by Orfeus on 2007-09-14
After ```
 startx 
``` that screen goes black then the terminal sreen reappears and it says that there has been a fatal error

---

### Post by w4ett on 2007-09-14
A few questions:

1. What Nvidia card are you using?  Post the output of :
```

lspci
```

2. Can you boot into safe graphics mode?

3.  Does the card work iwith the "vesa'" driver?

---

### Post by Eriksmits596 on 2007-09-14
When you're in GRUB, choose the "Safe Mode" entry. Then type:
> nvidia-xconfig Then restart. It worked for me;) Hope it works for you too.

---

### Post by Eriksmits596 on 2007-09-28
Have you tried it yet?

---

