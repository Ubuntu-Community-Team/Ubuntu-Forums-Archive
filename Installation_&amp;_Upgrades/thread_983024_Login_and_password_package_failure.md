---
title: "Login and password package failure"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by Largaroth on 2008-11-15
Hi, after an upgrade to the latest Kernel in Hardy, it seems my login and password pckages are damaged or failed to upgrade. The login screen just reloads constantly, resetting the fields and mouse position every second or so.

I have run the recovery mode several times in an attempt to correct this problem by running things like apt-get update. But no go. It always fails to get the packages I need.

Even by running wget [http://security.ubuntu.com/ubuntu/pool/main/s/shadow/login_4.0.18.2-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/shadow/login_4.0.18.2-1ubuntu2.1_i386.deb) (which is one of the packages i need) I get "could not resolve 'security.ubuntu.com' " I assume this is down to not having an internet connection... Due to I don't know, drivers not beeing loaded in the recovery mode or something.

Does anybody have any suggestions on how to resolve this problem ? (I assume that these packages need to be configured by the system, and simply downloading them and copying them over with a live CD into the correct folder wouldn't do the job ?)

---

### Post by taurus on 2008-11-15
At the GUI login screen, press <Ctrl><Alt>F2 to get to a console.  Now, can you log in with your username and password?

---

### Post by Largaroth on 2008-11-15
Okay, so once I've got the console access I can login, yes, I get the "largaroth@Mikinamo". So I did a :

$sudo apt-get upgrade

The problem wasn't solved, so I tried :

$sudo apt-get install login passwd

Again, the process went finem and the packages seem to have been installed, but the problem with the login screen hasn't gone away... I'm wondering if I shouldn't reconfigure Xorg to see what effect that has... Though I can't seem to find the shell code any longer ^^'...

---

### Post by taurus on 2008-11-15
What's the output of this command?

```
tail ~/..xsession-errors
```

---

### Post by ageilers on 2008-11-15
I just did an update on my Kubuntu (7.10) system with the same effect. I go to login, X restarts and I am back at the login screen. If I enter the wrong password, it lets me know the password is wrong. I can login to console with no problem. I have been searching for answers, but have not found anything yet. Will post my progress.

---

### Post by Largaroth on 2008-11-15
I get this :

```
tail: cannot open '/home/largaroth/..xsession-errors' for reading : No such file or directory.
```

---

### Post by taurus on 2008-11-15
What is the output of this command then?

```
ls -la ~
```

---

### Post by ageilers on 2008-11-15
Mine shows the file size to be zero. 

```
-rw------- 1 adam adam     0 2008-11-15 11:56 ..xsessions-errors
```

I wonder if it has to do with the Kernel update? Mine updated as well. Same problem going on.

---

### Post by Largaroth on 2008-11-15
By running ```
ls -la ~
``` I got a list of programs and dates, I assume it is a display of my last activities on the computer. most of the program names were blue... But the very last entrym and this I suppose is the one we're interested in since the others were several days older than this one :

```
-w-r--r--  1 largaroth largaroth  31787 2008-11-13 21:17 .xsession-errors
```

which allowed me to realise that I shouldn't have beem typing ```
tail ~/..xsession-errors
``` 

And so I typed ```
tail }~/.xsession-errors
```

And got this output :
```
gnome-system-monitor: symbol lookup error: /usr/lib/libcairo.so.2: FT_library_SetLcdFilter

**(gnome-system-monitor: 13618) WARNING **: SELinux was found but not enabled.

gnome-system-monitor: symbol lookup error: /usr/lib/libcairo.so.2: FT_library_SetLcdFilter
Gconf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge.
Settings from this path won't be read. Try to remove that value so that operation can continue properly.

(evolution: 32354): e-utils- WARNING**: Lock destroy: failed to unlink file: '/home/largaroth/.evolution/.running'!
*Message: Got disconnected from the session message bus; retrying to reconnect every 10 seconds
Dbus connection has been lost, trackerd will now shutdown.
```

Should I try removing compiz to see how that affects it ?

Edit (Strange how Ageilers has a ..xsessions-errors whereas I don't, but do have a .xsession-errors ^^)

---

### Post by taurus on 2008-11-15
I just want to see if the permissions and ownership of your $HOME are right.  That's the reason I asked for that command, the second one.

---

### Post by Largaroth on 2008-11-15
ah... and I suppose that that indormation is at the beginning of the output (which is quite long)

The length of the output brings the beginning out of the screen... And impossible to scroll back up :/
The first line I can read is "essful" :S

---

### Post by Largaroth on 2008-11-15
[quote="Largaroth"]Gconf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge.
Settings from this path won't be read. Try to remove that value so that operation can continue properly.[/quote]

Unless I am mistaken, I should be able to edit this file via shell cammands, but I'm wondering wether it wouldn't be easier to just remove Compiz all together...

---

