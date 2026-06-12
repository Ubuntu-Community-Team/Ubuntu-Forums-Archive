---
title: "After upgrade, boot hangs at &quot;Mounting remote filesystems...&quot;"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by darkrad on 2006-06-02
Hello, i have a wifi laptop with ati card, and i upgraded last night to stable dapper release from an unstable dapper version.
After dist-upgrade got completed i rebooted, and boot sequence hangs after the line "Mounting remote file system", and after some secs the dos-like termin show up listing last command executed, hanging there for ever:


```
....
Starting raid devices...                                       [ok]
Setting up LVM Volume Groups...                          [ok]
Starting Enterprise Volumen Management System... [ok]
...done.
Traceback (most recent call last): 
    File "/etc/rcS.d/S37displayconfig-hwprobe.py", line 27, in ?
         import ScanPCI ImportError: No module named ScanPCI
Configuring network interfaces...                          [ok]
```

plus i can't connect via ssh from another pc and if i pusch alt+canc+F* i can't have a login screen
Anybody has a clue of what to do?
thanks in advance

---

### Post by darkrad on 2006-06-02
i don't even know how to give you more information since i can't login with ssh or have a shell to see logs.. can you say me how to provide you any more information about it please?

---

### Post by ubuntu_demon on 2006-06-02
try booting in the recovery mode and use my guide here :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

---

### Post by darkrad on 2006-06-02
thanks for reply, but recovery mode acts exactly as the normal one, so it still hangs at same point and i can't get a shell access :( any other hint?

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=darkrad]thanks for reply, but recovery mode acts exactly as the normal one, so it still hangs at same point and i can't get a shell access :( any other hint?[/QUOTE]
Yeah I've also explained how to do it from live-cd there.

---

### Post by darkrad on 2006-06-02
after have chroot it, every sudo i try i get: sudo: unable to lookup ubuntu via gethostbyname(). any way i can solve it?

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=darkrad]after have chroot it, every sudo i try i get: sudo: unable to lookup ubuntu via gethostbyname(). any way i can solve it?[/QUOTE]
You don't have to use sudo in a chroot because you are root.

---

### Post by darkrad on 2006-06-02
ya but i have to do sudo for the apt-get update.. so i need to fix that thing =(

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=darkrad]ya but i have to do sudo for the apt-get update.. so i need to fix that thing =([/QUOTE]
No you don't. That's not necessary since you are root.

So it's just :
$apt-get update

good luck!

---

### Post by ubuntu_demon on 2006-06-02
here's an example of my guide in action (his problems aren't solved yet) :
[http://www.ubuntuforums.org/showthread.php?t=186565](http://www.ubuntuforums.org/showthread.php?t=186565)

---

### Post by darkrad on 2006-06-02
yes thanks.
i followed your guide and i finally got it working.
after have done dist-upgrade, i ran again sudo "dpkg --configure -a" just to be sure.. cupsys couldn't get installed so i just removed it with "apt-get remove cupsys". after reboot all just worked fine as before the upgrade. thanks again to ubuntu_demon for the great guide.

---

### Post by ubuntu_demon on 2006-06-02
Don't forget to issue these commands :
$sudo apt-get install ubuntu-minimal
$sudo apt-get install ubuntu-base
$sudo apt-get install ubuntu-desktop

---

### Post by darkrad on 2006-06-03
yea, i did them thanks

---

### Post by ubuntu_demon on 2006-06-03
[QUOTE=darkrad]yea, i did them thanks[/QUOTE]
great!

---

