---
title: "Driver Installation"
date: 2012-04-02
forum: Installation &amp; Upgrades
---

### Post by cbennett926 on 2012-04-02
Hello,

I have found a driver for my graphics card, a NVIDIA Quadro 2000m, on their website and I know to run the installer in the terminal, however it says that it must be ran as root. Can anyone help me as to how I can run it as root. 

The driver was found here:

[http://www.nvidia.com/object/linux-display-amd64-295.33-driver.html](http://www.nvidia.com/object/linux-display-amd64-295.33-driver.html)

---

### Post by jonnyboysmithy on 2012-04-02
First we open a terminal. 
If the file is on your desktop then ```
sudo /home/yourusernamehere/Desktop/the-file-you-want-to-run
``` (press enter)

 If you type / and press tab on the keyboard twice it will list what is in the folder.
So if you type```
sudo /home/yourusernamehere/Desktop/
``` and press tab twice it will list what is there.
If you do ```
sudo /home/yourusernamehere/Desktop/A
``` it will only list files beginning with A.
It is case sensitive so watch your capital letters.
Normally you could just run the file without sudo in front of it , but we want to run it runs as root so we put sudo in front of it.

---

### Post by wojox on 2012-04-02
Ctrl + Alt + F1 will put you in a virtual terminal.

```
sudo service gdm stop
```

Will kill X-Server so you can install the driver.

---

### Post by cbennett926 on 2012-04-02
> **wojox said:**
> Ctrl + Alt + F1 will put you in a virtual terminal.

```
sudo service gdm stop
```Will kill X-Server so you can install the driver.

Hi, I did this and it said that "gdm command not found"

---

### Post by Bucky Ball on 2012-04-02
Have you gotten your updates? You might want to check in 'Additional Drivers'. There could be one in there already, but disabled.

---

### Post by cbennett926 on 2012-04-02
> **Bucky Ball said:**
> Have you gotten your updates? You might want to check in 'Additional Drivers'. There could be one in there already, but disabled.

Hello,

There are two drivers available, NVIDIA accelerated graphics driver (version current) [Recommended]

as well as:

NVIDIA accelerated graphics driver (post-release updates) (version current-updates)

I currently am running the latter of the two, both of which indicate Tested by the Ubuntu developers. 

The one I am running right now seems to work better than the other, however the system resume from being suspended takes FOREVER sometimes, others not so much, it seems to take longer the longer the lid is closed. I actually had to reboot because it would not come back from being suspended.

---

### Post by Bucky Ball on 2012-04-02
Might be an idea to use the stable version, then, but the other is post-release which means there will be a stable version of that eventually. ;)

---

### Post by wojox on 2012-04-02
That right, it's lightdm now.

```
sudo service lightdm stop
```

---

### Post by cbennett926 on 2012-04-02
> **wojox said:**
> That right, it's lightdm now.

```
sudo service lightdm stop
```

What exactly does this mean?

---

### Post by wojox on 2012-04-02
> **cbennett926 said:**
> What exactly does this mean?

It kills x-server so you can install your video driver.

---

### Post by cbennett926 on 2012-04-02
I don't know what I am doing wrong, I ran 

```

sudo service lightdm stop

```[FONT=monospace]

As well as running

```
 

```[/FONT]```
sudo /home/cody/Documents/NVIDIA-Linux-x86_64-295.33.run

```

and it just sits there on a black screen.

---

### Post by wojox on 2012-04-02
Did you remember to Ctrl + Alt + F1 to switch to a virtual console?

There is also a ppa with that driver you want.
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
```

---

### Post by cbennett926 on 2012-04-02
> **wojox said:**
> Did you remember to Ctrl + Alt + F1 to switch to a virtual console?

There is also a ppa with that driver you want.
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
```

You are amazing!! THANK YOU!!

---

