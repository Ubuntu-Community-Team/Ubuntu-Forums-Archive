---
title: "E: Could not get lock /var/lib/dpkg/lock - how do i fix this?"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by slashwannabe94 on 2010-11-25
Can someone explain to me, what this error message means, and how i can fix it ? 

i was running an 'apt-get install' command earlier, and cancelled it with ctrl+z. 

i know tried to run 'sudo apt-get install python3', 

and i received the error message 

E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Thanks, 

SlashWannabe94

---

### Post by b0b138 on 2010-11-25
There can only be one instance of apt-get running at a time. This also includes synaptic. So if synaptic is open, you can't run apt-get commands. Or when you stopped an install suddenly, the process is still running. Check system monitor for an open terminal.

Logging off and back on or a reboot should clear it up

---

### Post by slashwannabe94 on 2010-11-25
is there not a way i could kill the process ? 

top - does not show it

---

### Post by sikander3786 on 2010-11-25
A simple reboot should fix it.

Already mentioned that 2 instances of apt-get cannot run simultaneously. Also note that any other package manager like Synaptic, Update-manager, Software Center or aptitude should also not be running.

---

### Post by sgosnell on 2010-11-25
Synaptic, gdebi, dpkg, apt-get, aptitude, all are frontends for dpkg.  Only one instance can run at a time, so it seems you have one of these running somewhere, perhaps on another workspace, but running somewhere.  To see what processes are actually running, you can run System Monitor and kill it.

---

### Post by b0b138 on 2010-11-25
yes, you just have to figure out which process.

---

### Post by susema on 2010-11-25
Try this please;

```
sudo rm /var/lib/apt/lists/lock
```

---

### Post by d3v1150m471c on 2010-11-25
it's probably update-manager.

---

### Post by d3v1150m471c on 2010-11-25
> **susema said:**
> Try this please;

```
sudo rm /var/lib/apt/lists/lock
```

eh? no offense but that just looks like possible trouble. I think he should reboot first.

---

### Post by eng.amr19 on 2010-11-25
hi 
it is me . i am amr from egypt . and i am new to ubuntu . and ubuntu is the most greatest "os" operating system in the whole world .

the same problem i have (the problem of "apt-get")
and i try the all solutions have been intorduce buy other 
and finally the same problem

---

### Post by slashwannabe94 on 2010-11-26
sudo rm /var/lib/apt/lists/lock

that would remove the file....

i doubt that is useful, but thanks for your help anyway.
I'm trying to kill the process, not remove the file completely.

---

### Post by susema on 2010-11-26
> **slashwannabe94 said:**
> sudo rm /var/lib/apt/lists/lock
I'm trying to kill the process, not remove the file completely.

Ok. Firstly, learn running programs in terminal:

```
ps aux
```Then kill it:

 ```
sudo killall synaptic
``` &#304;nstead of synaptic may be 'apt-get'.

---

