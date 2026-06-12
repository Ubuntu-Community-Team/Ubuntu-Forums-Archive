---
title: "Cannot install nvidia drive for ubuntu 14.04"
date: 2015-06-15
forum: Installation &amp; Upgrades
---

### Post by lee_3 on 2015-06-15
I am using Ubuntu 14.04 (64 bit) with kernel version is 3.19.0-20-generic. And my nvidia is

```
    01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107M [GeForce GT 650M] [10de:0fd1] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Samsung Electronics Co Ltd Device [144d:c0d1]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at f7000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
```

That mean it is GeForce GT 650M. Hence, I went to [nvidia search][1] to check which nvidia is good for my laptop. I found version 346.72. However, when I install it. I cannot log-in my computer. It allway repeat log-in screen when I login. I need to uninstall it. Then it can log-in again. What is my problem? How to resolve it?
I also tried do with other method such as

```
    $ sudo add-apt-repository ppa:xorg-edgers/ppa -y
    $ sudo apt-get update
    # install the latest version
    $ sudo apt-get install nvidia-current
```

But it shown that (Note that I install 304 version is lastest version). If i install 304 version, I can used it and login my computer. Otherwise, when I used newest version such as 346. My computer is only black screen, I must go to Ctrl+Alt+F1 to delete it 

So, My problem is how to install the newest driver version for my computer? Thanks you in advance



  [1]: [http://www.nvidia.com/Download/index.aspx](http://www.nvidia.com/Download/index.aspx)
  [2]: [http://i.stack.imgur.com/onbUc.png](http://i.stack.imgur.com/onbUc.png)

---

### Post by lee_3 on 2015-06-16
I am installing nvidia version 340. My ubuntu version 14.04 with kernel is 3.19.0-20-generic. My nvidia is GeForce GT 650M. I install that nvidia version because I have schedule to install CUDA 6.5 and that cuda only work for that nvidia version.I have one problem that is after installing nvidia and restart. After login. I cannot go to main GUI( It appears black screen). However, when I uninstall it. It can go to my GUI. Have any way to resolve it. I tried step by step as following
[COLOR=#111111][FONT=Ubuntu]
First of all I removing all nvidia drivers.
[/FONT][/COLOR]```

sudo apt-get purge nvidia*

```  
[COLOR=#111111][FONT=Ubuntu]For Ubuntu 14.04 the default and preferred driver is nvidia-331.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]It can be installed by
[/FONT][/COLOR]```
  
 sudo apt-get install nvidia-340

```  
[COLOR=#111111][FONT=Ubuntu]As an option I can upgrade kernel and install newer drivers.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Upgrade kernel to 3.19
[/FONT][/COLOR]```
  
sudo apt-get install linux-generic-lts-vivid

```  
[COLOR=#111111][FONT=Ubuntu]reboot[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Then install nvidia-340 from xorg-edgers
[/FONT][/COLOR]```
  
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-346 nvidia-prime nvidia-settings
sudo add-apt-repository -r ppa:xorg-edgers/ppa
```  

This is my `dkms status`


```
    bbswitch,0.7, 3.19.0-20-generic , x86_64: installed
    nvidia-340, 340.76, 3.19.0-20-generic, x_86_64: installed

```

Thanks

---

### Post by howefield on 2015-06-16
Threads merged, one on the same topic really is sufficient.

---

### Post by lee_3 on 2015-06-16
Can you see my problem and resolve help me?

---

### Post by NoWayWin8 on 2015-06-17
I'm guessing the problem is caused by ownership of the .Xauthority or .xinputrc in the Home directory getting changed to root instead of the user.

Fix it from the terminal:
 (replace "USER" with your username)
```

$ cd /home/USER
$ sudo chown USER *
$ sudo reboot

```

---

