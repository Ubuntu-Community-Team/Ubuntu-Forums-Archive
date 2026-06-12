---
title: "Synaptic Pakcage Manager? (or...Limewire FUBAR)"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by stargirl51 on 2008-10-09
I attempted to download and install limewire. But halfway throughout the installation, I quit the program. So now...it seems like the synaptic package manager that was installing limewire is running somewhere but it's not available for me to find. And I can't install any other program since it's busy apparently installing limewire.

Any and all help is appreciated!

PS: I've found that gtkpod supports (for the most part) the iPod Nano 4G. Just an extra little tidbit.

cheers,
stargirl

---

### Post by rishabh on 2008-10-09
If you quit the program halfway, it's either 
1. Still running. 
   You can find that out by going to a terminal and typing 
```
ps -ef | grep synaptic
```
   If you get any output, it's still running.

2. Or the lock file is messed up.
   Type 
```
sudo rm /var/lib/dpkg/lock
```
   to remove the lock file.

---

### Post by oldos2er on 2008-10-09
> **stargirl51 said:**
> I attempted to download and install limewire. But halfway throughout the installation, I quit the program. So now...it seems like the synaptic package manager that was installing limewire is running somewhere but it's not available for me to find. And I can't install any other program since it's busy apparently installing limewire.

Any and all help is appreciated!

PS: I've found that gtkpod supports (for the most part) the iPod Nano 4G. Just an extra little tidbit.

cheers,
stargirl

 Open a terminal and run the command "sudo dpkg --configure -a". If it shows any errors, please copy & paste them here.

---

### Post by stargirl51 on 2008-10-09
> **oldos2er said:**
> Open a terminal and run the command "sudo dpkg --configure -a". If it shows any errors, please copy & paste them here.

I ran that in terminal and it returned with this:

Setting up java-common (0.28ubuntu3) ...

Setting up odbcinst1debian1 (2.2.11-16build1) ...

Setting up unixodbc (2.2.11-16build1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

---

### Post by stargirl51 on 2008-10-09
> **rishabh said:**
> If you quit the program halfway, it's either 
1. Still running. 
   You can find that out by going to a terminal and typing 
```
ps -ef | grep synaptic
```
   If you get any output, it's still running.

2. Or the lock file is messed up.
   Type 
```
sudo rm /var/lib/dpkg/lock
```
   to remove the lock file.


When I typed in teh first one in terminal, it returned this:

       6704  6678  0 16:49 pts/0    00:00:00 grep synaptic


I have no idea what that means.

---

### Post by stargirl51 on 2008-10-09
Apparently, when I run update manager, it says I have a broken package.

---

### Post by rishabh on 2008-10-09
Try a quick 
```
sudo apt-get install -f
```

---

### Post by stargirl51 on 2008-10-09
> **rishabh said:**
> Try a quick 
```
sudo apt-get install -f
```

Nothing happened. On top of that, what does that install?

---

### Post by rishabh on 2008-10-09
Well, your original problem was that synaptic was running in the background...
If that was indeed the case, "sudo apt-get install -f" would complain "Unable to lock the administration directory" (the actual purpose of that command is to fix broken packages).
Since this is not happening, I would presume that your problem is now a half-installed limewire package? Try forcing it out like this:
```
sudo dpkg --remove --force-remove-reinstreq limewire
```
And first of all, how are you using Synaptic to install Limewire? It's not in the repos, I think...

---

### Post by stargirl51 on 2008-10-09
> **rishabh said:**
> Well, your original problem was that synaptic was running in the background...
If that was indeed the case, "sudo apt-get install -f" would complain "Unable to lock the administration directory" (the actual purpose of that command is to fix broken packages).
Since this is not happening, I would presume that your problem is now a half-installed limewire package? Try forcing it out like this:
```
sudo dpkg --remove --force-remove-reinstreq limewire
```
And first of all, how are you using Synaptic to install Limewire? It's not in the repos, I think...

I tried that code and this returned:

```

dpkg - warning: ignoring request to remove limewire which isn't installed.

```

---

### Post by rishabh on 2008-10-10
Erm, so you don't have limewire installed. What exactly is the problem you're experiencing, then?

---

### Post by stargirl51 on 2008-10-10
Huh...whatever it was, it seems to have disappeared. I was able to update my system and install various dvd programs.

Don't know whose code did it but thank you, all of you!

cheers,
stargirl

---

### Post by rishabh on 2008-10-10
> **stargirl51 said:**
> Huh...whatever it was, it seems to have disappeared. I was able to update my system and install various dvd programs.

Don't know whose code did it but thank you, all of you!

cheers,
stargirl

You're welcome, but I still don't see how you were installing limewire through Synaptic :P
I think your problem got solved when you restarted your computer, anyway :)

---

### Post by stargirl51 on 2008-10-10
I downloaded the .deb and it ran through teh installation process and I tried to quit it in the middle of installing something (think it was the sun java something). So I think that resulted in a broken package.

cheers,
stargirl

---

