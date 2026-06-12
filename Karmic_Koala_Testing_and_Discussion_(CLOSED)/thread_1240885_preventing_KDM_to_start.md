---
title: "preventing KDM to start"
date: 2009-08-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ilna on 2009-08-15
Kubuntu Karmic is in use (up to date). I have tried to find a way to prevent X (more strictly, KDM) loading after power on. All refs wrt default run level I have found deal with /etc/inittab or /etc/event.d, but these ones don't exist at all in Karmic installation.

Please, point me to right direction to further digging in.

---

### Post by xebian on 2009-08-15
> **ilna said:**
> Kubuntu Karmic is in use (up to date). I have tried to find a way to prevent X (more strictly, KDM) loading after power on. All refs wrt default run level I have found deal with /etc/inittab or /etc/event.d, but these ones don't exist at all in Karmic installation.

Please, point me to right direction to further digging in.

Look in /etc/init.d/kdm

---

### Post by ilna on 2009-08-15
> **xebian said:**
> Look in /etc/init.d/kdm
Why? I need to prevent this service starting rather to modify started service :-)

---

### Post by xebian on 2009-08-15
> **ilna said:**
> Why? I need to prevent this service starting rather to modify started service :-)

You asked for directions??  
But you look like you know what you are doing.:P

---

### Post by ilna on 2009-08-15
> **xebian said:**
> You asked for directions??  
But you look like you know what you are doing.:PNo, I don't :-) I'd want to know "legal, official" place where this script is configured to be started on boot. /etc/defaults/ contains  kdm.d dir, and last one is empty - nothing to configure :confused:

---

### Post by dentaku65 on 2009-08-15
If you need it to do this not permanently
```
sudo init 1
```

---

### Post by jocko on 2009-08-15
Well, the script that starts kdm is /etc/init.d/kdm.
To stop it, remove any links to /etc/init.d/kdm in the /etc/rc*.d/ folders, with this command:
```
sudo update-rc.d -f kdm remove
```To add it back:
```
sudo update-rc.d kdm defaults
```

---

### Post by ilna on 2009-08-15
> **dentaku65 said:**
> If you need it to do this not permanently
```
sudo init 1
```I'd want to boot to console in a regular way.

---

### Post by dentaku65 on 2009-08-15
> **ilna said:**
> I'd want to boot to console in a regular way.
So... you can install 
```
sudo apt-get install sysv-rc-conf
```
then
```
sudo sysv-rc-conf
```
then de-select the init levels of kdm daemon

---

### Post by jocko on 2009-08-15
> **dentaku65 said:**
> So... you can install 
```
sudo apt-get install sysv-rc-conf
```then
```
sudo sysv-rc-conf
```then de-select the init levels of kdm daemon
Or just do what I've already said. It's one command and nothing new needs to be installed.

---

### Post by ilna on 2009-08-15
> **jocko said:**
> Well, the script that starts kdm is /etc/init.d/kdm.
To stop it, remove any links to /etc/init.d/kdm in the /etc/rc*.d/ folders, with this command:
```
sudo update-rc.d -f kdm remove
```To add it back:
```
sudo update-rc.d kdm defaults
```
**jocko**, thanks!  update-rc.d is just that script I was looking for.

---

