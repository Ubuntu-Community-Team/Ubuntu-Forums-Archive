---
title: "Install GUI in Ubuntu Server 18.04 LTS"
date: 2019-07-30
forum: Installation &amp; Upgrades
---

### Post by Peter Alien on 2019-07-30
Hello,

Can anyone tell me how to install Gnome or other GUI in Ubuntu Server 18.04 LTS, but without the amount of apps that gets intalled? Only the GUI and Console for example.


Many thanks.

---

### Post by deadflowr on 2019-07-30
The best you can do to get a bare gnome is to install gnome-shell.
You might even install it sans recommended packages
```
sudo apt-get install --no-install-recommends gnome-shell
```

Other then that you might look at a light window manager such as ones suggested here:
[https://ubuntuforums.org/showthread.php?t=2415676&p=13848098#post13848098]("https://ubuntuforums.org/showthread.php?t=2415676&p=13848098#post13848098")

---

### Post by cruzer001 on 2019-07-30
Another route would be OpenBox.  Its pretty barebones

[http://openbox.org/wiki/Main_Page](http://openbox.org/wiki/Main_Page)

```
sudo apt install openbox obconf synaptic
```

Added a package manager

---

### Post by Peter Alien on 2019-08-01
Ok, thanks guys. I will look for your answers.

---

### Post by sudodus on 2019-08-01
I have used Fluxbox for such tasks.

See [this link](https://askubuntu.com/questions/1118453/is-there-any-gui-with-terminals-only/1118506#1118506) and [that link](https://askubuntu.com/questions/937097/ubuntu-16-04-lts-how-is-the-x-server-started/987945#987945).

---

### Post by mastablasta on 2019-08-02
icewm is also an easy to use and perhaps more familiar windows manager. well, familiar to those used to windows.

---

### Post by cruzer001 on 2019-08-02
> **sudodus said:**
> I have used Fluxbox for such tasks.

See [this link](https://askubuntu.com/questions/1118453/is-there-any-gui-with-terminals-only/1118506#1118506) and [that link](https://askubuntu.com/questions/937097/ubuntu-16-04-lts-how-is-the-x-server-started/987945#987945).
Hello sudodus
I like that, Fluxbox better fits the OP's request.

---

### Post by cruzer001 on 2019-08-02
My preferred minimal  WM is spectrwm it comes with xrandr, tiling/stacking built in.  Shift/Alt/Enter will tile up terminals.

---

