---
title: "Hardy Heron freezes while doing certain tasks"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by exidez on 2008-06-12
Even since upgrading this problem has been persisting. I thought these were just random cases but it seems it is not.
It always freezes when i click that information light bulb on the top right when it comes up. 
It also always freezes when i use the terminal for over 2 minutes.. i have never used the terminal for more that 5 minutes before it freezes on me. 

I cannot Alt Ctrl Backspace, i have to hard reset. I can leave my laptop idling and it wont freeze it is just if i do certain tasks...
Any help? What information do you require?

should i do a clean install?

Thanks

---

### Post by hal8000 on 2008-06-13
> **exidez said:**
> Even since upgrading this problem has been persisting. I thought these were just random cases but it seems it is not.
It always freezes when i click that information light bulb on the top right when it comes up. 
It also always freezes when i use the terminal for over 2 minutes.. i have never used the terminal for more that 5 minutes before it freezes on me. 

I cannot Alt Ctrl Backspace, i have to hard reset. I can leave my laptop idling and it wont freeze it is just if i do certain tasks...
Any help? What information do you require?

should i do a clean install?

Thanks


It is better to do a fresh install than an upgrade. As you had the problem before you upgraded it is something inherited from the previous install.

How much physical RAM do you have and how much swapspace?

free -m
sudo swapon -s

these commands will show memeory usage in megabtes, and the amount of swap space used.

You could also do with removing services you never need.
sudo apt-get install sysv-rc-conf

will install a services utility. Hadry boots to runlevel 2, however you have to be careful what you uncheck as some services may be dependant on others.

A safer utility is found in system, admin, services.

Gnome desktop itself, also has a number of running programs, different for each user, system, preferences, sessions will show you whats running.

You dont say what youre running or what hardware, so first thing is if youre running compiz fusion to disable graphical effects and see if that helps, if no better, systematically break down what youre running.

Gnome-system-monitor is a greta utility for CPU usage, memory stats and resources, but you can also use top from a terminal.

Your load average should also be an indication fow your system is performing displayed in gnome system monitor.

---

### Post by exidez on 2008-06-15
my laptop has only freezed since i have installed hardy heron. This never happened with Gutsy.
```

$ free -m
             total       used       free     shared    buffers     cached
Mem:           755        471        284          0         15        275
-/+ buffers/cache:        180        575
Swap:         1953          0       1953

$ sudo swapon -s
Filename				Type		Size	Used	Priority
/dev/sda2                               partition	2000084	0	-1

```

Also, i just did a fresh install today and it still freezes

---

### Post by exidez on 2008-06-21
it even freezes at the login screen sometimes...
please, anyone? i dont want to download gutsy again as my connection is already shaped!

---

### Post by exidez on 2008-07-12
this is how i can reproduce the freezing. What can i do to find out what is wrong????

Every time i load up GNU cash (my finance program) and it load the tip of the day information box it freezes.

Hardy also freezes when i open up a terminal and press the down arrow to move to a more recently used command. It will only freeze if there are no more future commands to cycle through...
ie. i can press up 4 times to cycle through to the forth recently used command and then i can cycle down three times to cycle to the last used command. I can then press down again to get a clear line where i started from but if i press down again (5th time) it will freeze (there are no more commands beyond this point anyway).

---

### Post by oxman on 2008-07-12
Hello exidez,

You are not the only one having these freeze up and lock up problems. I saw a bug report and many complaints in a few threads. Do "Hardy freezes" or similar search and you will catch up to the discussion. 

Sorry and I know it can be frustrating but hang in there. The bugs will get ironed out.

---

