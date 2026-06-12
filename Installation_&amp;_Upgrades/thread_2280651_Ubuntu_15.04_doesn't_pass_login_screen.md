---
title: "Ubuntu 15.04 doesn't pass login screen"
date: 2015-06-01
forum: Installation &amp; Upgrades
---

### Post by mtilhan on 2015-06-01
Hi,
Its been a while since I used linux (last time I used it was 9 or 10 series at Ubuntu). Today, I installed Ubuntu 15.04 my lab pc since all guys recommended that to me. After installation first thing I did was 
```
sudo apt-get update
``` and ```
sudo apt-get upgrade
```,

after it package manager told me there is an update (another one aside from the ones at terminal). I updated that too.

Then since I will work on OpenCL, according to this link:
[http://askubuntu.com/questions/541114/how-to-make-opencl-work-on-14-10-nvidia-331-89-drivers](http://askubuntu.com/questions/541114/how-to-make-opencl-work-on-14-10-nvidia-331-89-drivers)
I used
```
sudo apt-get install nvidia-346 nvidia-346-uvm nvidia-opencl-dev nvidia-modprobe
```
but now in secure mod or normal opening login screen has low resolution than before and even the password is correct screen goes to black and again it is login screen. It doesn't warn me as "incorrect password" but it doesn't open either. I can't even open guest session. Can anybody help me with that? If there is any information more you need, I will try to post it tomorrow after I went to lab (I just got home to my pc and writing this from it).

Thanks for your help.

---

### Post by sandyd on 2015-06-01
What video card do you have?
If you don't know, you can press control +alt+f1, and login.

Type in the command ```

lspci| grep -i VGA
```

and your video card should show up.

---

### Post by mtilhan on 2015-06-01
Nvidia GTX 260 if I don't remember wrong.

---

### Post by sandyd on 2015-06-01
You're using the wrong version of the Nvidia drivers.

Unfortunately, the proper drivers (nvidia-340) are not available in the default Ubuntu repositories.

Try running the following in the terminal (Assuming you have wired internet)
```

sudo add-apt-repository ppa:mamarley/nvidia
sudo apt-get update
sudo apt-get purge nvidia-346 nvidia-346-uvm nvidia-modprobe
sudo apt-get install nvidia-graphics-drivers-340 nvidia-settings nvidia-opencl-dev
```

---

### Post by mtilhan on 2015-06-01
How can i open terminal? Because I couldn't pass login screen and I don't know a way to open terminal without passing login screen. Thanks for your help and one more thing. According to that post nvidia-331 also use nvidia-modprobe so why we purge that too or why not install again?

---

### Post by grahammechanical on 2015-06-01
When you get to the login screen press Ctrl+Alt+F1 or F2 and then login and go from there. Afterwards type

```
sudo shutdown -r now
```

and that will restart the machine.

Regards.

---

### Post by mtilhan on 2015-06-02
> **sandyd said:**
> You're using the wrong version of the Nvidia drivers.

Unfortunately, the proper drivers (nvidia-340) are not available in the default Ubuntu repositories.

Try running the following in the terminal (Assuming you have wired internet)
```

sudo add-apt-repository ppa:mamarley/nvidia
sudo apt-get update
sudo apt-get purge nvidia-346 nvidia-346-uvm nvidia-modprobe
sudo apt-get install nvidia-graphics-drivers-340 nvidia-settings nvidia-opencl-dev
```
At first line it said [Errno -3] Temporary failure in name resolution
I tought it was nothing and passed to second line it did update but give again exception.
Then I passed to third lane which worked.
Then I passed to fourth lane which said "there is no nvidia-graphics-drivers-340" so I tried nvidia-340 which found but when I said Y to installation it said E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

What should I do?

Edit: Now I tried again, and it worked, I think it was related to my network service. Though again it didn't accepted nvidia-graphics-drivers-340 so i used nvidia-340 now it's installing.

---

