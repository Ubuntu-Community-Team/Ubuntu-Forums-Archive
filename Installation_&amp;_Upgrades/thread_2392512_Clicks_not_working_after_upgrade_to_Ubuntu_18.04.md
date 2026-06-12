---
title: "Clicks not working after upgrade to Ubuntu 18.04"
date: 2018-05-22
forum: Installation &amp; Upgrades
---

### Post by kinsomicrote on 2018-05-22
Since I upgraded from Ubuntu 17.10 to 18.04, the Left and Right clicks have not been working.
I installed gnome-tweak-tools and followed the instructions here [https://askubuntu.com/questions/1028113/right-click-on-touchpad-not-working-after-update-to-18-04-lts](https://askubuntu.com/questions/1028113/right-click-on-touchpad-not-working-after-update-to-18-04-lts), but it still doesn't work.

On the logon screen, both buttons work well.
How do I resolve this?
So far all the solutions I've found from Google Search mention the use of gnome-tweak-tools, and that doesn't work.

---

### Post by Autodave on 2018-05-23
Is this a desktop or laptop? Did you do a clean install or did you upgrade what you already had installed?

---

### Post by kinsomicrote on 2018-05-25
It's a laptop, I did an upgrade from Ubuntu 17.10.
The clicks actually work when I make use of Unity, instead of the others.

---

### Post by monkeybrain20122 on 2018-05-26
Try
```

sudo apt install xserver-xorg-input-synaptics
```

If it says it is already installed, do
```

sudo apt remove xserver-xorg-input-synaptics
```

Then reboot and see if it works now.

---

### Post by kinsomicrote on 2018-05-30
It still didn't work.

---

### Post by luks911 on 2018-05-30
Hi, I have the same problem with a 18.04 fresh install on a HP Omen 15 :( 

I made a downgrade to 17.10 because of this issue, but I'd like to find a solution and be able to use 18.04.

---

### Post by monkeybrain20122 on 2018-05-31
kernel issue perhaps? Maybe grab 4.16.x and see how it works [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Make a new folder, say call it linux in the  Downloads directory (it doesn't matter what you call it and where you put it, just for easy reference here) Download three deb packages (linux-headers-all amd64, linux headers generic amd64, linux image generic amd64) into linux

then
```

cd ~/Downloads/linux

sudo dpkg -i *.deb
```

Then  reboot. 

If new kernel breaks something or doesn't work, just boot back to the old kernel and uninstall the packages you just installed (it is easy if you have synaptic package manager installed. so 
```
sudo apt install synaptic
``` 

To boot into old kernel, reboot and keep hitting the esc key (in some machine maybe shift key) then you will see the grub menu, choose advanced options and you can pick the old kernel (4.15.xx ) once booted into ubuntu, open synaptic. Click reload, then search for the packages you just installed and uninstall them.

---

### Post by luks911 on 2018-05-31
It's worth trying. Though, at least in my case, the problem didn't happen using Ubuntu from a pendrive in live mode.

---

### Post by kinsomicrote on 2018-06-02
Thanks for the suggestion, I tried it but it didn't resolve the issue.

> **monkeybrain20122 said:**
> kernel issue perhaps? Maybe grab 4.16.x and see how it works [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Make a new folder, say call it linux in the Downloads directory (it doesn't matter what you call it and where you put it, just for easy reference here) Download three deb packages (linux-headers-all amd64, linux headers generic amd64, linux image generic amd64) into linux

then
```

cd ~/Downloads/linux

sudo dpkg -i *.deb
```

Then reboot. 

If new kernel breaks something or doesn't work, just boot back to the old kernel and uninstall the packages you just installed (it is easy if you have synaptic package manager installed. so 
```
sudo apt install synaptic
``` 

To boot into old kernel, reboot and keep hitting the esc key (in some machine maybe shift key) then you will see the grub menu, choose advanced options and you can pick the old kernel (4.15.xx ) once booted into ubuntu, open synaptic. Click reload, then search for the packages you just installed and uninstall them.

---

### Post by kinsomicrote on 2018-06-02
How did you go about the downgrade?

> **luks911 said:**
> Hi, I have the same problem with a 18.04 fresh install on a HP Omen 15 :( 

I made a downgrade to 17.10 because of this issue, but I'd like to find a solution and be able to use 18.04.

---

### Post by luks911 on 2018-06-02
> **kinsomicrote said:**
> How did you go about the downgrade?

I have my /home in a separate partition, so I just took my old 17.10 iso image, put into a pendrive and installed it over 18.04.

The odd thing is that I didn't have the touchpad issue when I probed 18.04 in live mode :-k

---

### Post by monkeybrain20122 on 2018-06-02
> **luks911 said:**
> I have my /home in a separate partition, so I just took my old 17.10 iso image, put into a pendrive and installed it over 18.04.

The odd thing is that I didn't have the touchpad issue when I probed 18.04 in live mode :-k

17.10 expires in ~ a month. If you are downgrading may as well go 16.04 which is supported til 2021.

---

### Post by luks911 on 2018-06-02
Ouch... Thanks for the information

---

