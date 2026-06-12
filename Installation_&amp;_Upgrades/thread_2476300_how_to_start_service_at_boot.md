---
title: "how to start service at boot"
date: 2022-06-22
forum: Installation &amp; Upgrades
---

### Post by chat-4432 on 2022-06-22
i want to start service at boot 
because when server is down
i must do the manually start every time  
```

[COLOR=#000000][FONT=Consolas]sudo /etc/init.d/apache2 start[/FONT][/COLOR]
sudo /etc/init.d/mysql start
```
how ??

---

### Post by MAFoElffen on 2022-06-23
Before answering: Which Release of Ubuntu Server? (That matters)

Since your commands (posted above) assume working init scripts in /etc/init.d/, then this should work:
```

sudo update-rc.d apache2 defaults
sudo update-rc.d mysql defaults

```
But that would assume that you are not starting them as a Service under systemd...

If new/current Releases, then to start as a systemd service
```

sudo systemctl status apache2
# check to see if it is enabled or disabled... To enable, then
sudo systemctl enable --now apache2
# Then the same for mysql
sudo systemctl status mysql
sudo systemctl enable --now mysql

```
But that assumes that there are systemd service files for each...

---

### Post by chat-4432 on 2022-06-23
not work 
do you know how to auto restart this ?
i use 20.04 [URL="https://proot-me.github.io/"]**PRoot**
[/URL]can't use systemctl
bash: systemctl: command not found

---

### Post by chat-4432 on 2022-06-23
can i ask more question if i want to auto start at boot on 22.04 wsl
like this one
[https://github.com/microsoft/WSL/issues/8207](https://github.com/microsoft/WSL/issues/8207)
what should i do ??

---

