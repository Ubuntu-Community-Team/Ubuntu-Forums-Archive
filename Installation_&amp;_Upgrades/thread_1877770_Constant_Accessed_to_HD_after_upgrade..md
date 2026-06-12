---
title: "Constant Accessed to HD after upgrade."
date: 2011-11-08
forum: Installation &amp; Upgrades
---

### Post by Ifaistos on 2011-11-08
Hello everyone :-)

I have experienced since the upgrade to 11.10 that my HD access is almost constant.
In the beginning I thought that the memory was loaded and had to access the swap file. However when I closed a couple of programs and memory was freed, it still did the same.

I see that my HD access led is being continuously (almost constantly) lit.
I am already searching for a couple of Geil PC3200 chips to increase my memory to 4GB. I have installed the 64bit version so I will be able to access it all.

However I think that the constant accessing to the HD should be caused by smt else and not memory inadequacy. I think that 11.10 is much more demanding on my rig, and I have experienced significant decrease in the performance of my PC.

I will test it again when I find the memory and upgrade it to 4GB. However I would like to explore the possibility that smt else is responsible for the deterioration of performance. Any ideas?

I am attaching one picture.  The orange part is the HD access.  I can't understand why Ubuntu keeps accessing my HD.  It did not do that in 11.04.

Thanks everyone in advance...

---

### Post by Ifaistos on 2011-11-08
bump :-)

---

### Post by 23dornot23d on 2011-11-09
I was thinking the same as you ..... memory .....

That would cause the disk usage - but you seem to rule that out ....

The things that I might consider doing is checking HTOP .... to see what activities are
taking place at the time .....

---

### Post by Ifaistos on 2011-11-09
Hello and thank you for your answer.
Could you please be more specific?

What is HTOP, and how do I use it?

Thanks :-)

---

### Post by Ifaistos on 2011-11-10
bump :-)

---

### Post by e79 on 2011-11-10
Htop is an interactive process viewer for Linux. It is a text-mode application (for console or X terminals).

```
sudo apt-get install htop
```

[SIZE=2]
Comparison between htop and top

[/SIZE] 
[LIST]
[*]In 'htop' you can scroll the list vertically and horizontally    to see all processes and complete command lines.
[*]In 'top' you are subject to a delay for each unassigned    key you press (especially annoying when multi-key escape    sequences are triggered by accident).
[*]'htop' starts faster ('top' seems to collect data for a while    before displaying anything).
[*]In 'htop' you don't need to type the process number to    kill a process, in 'top' you do.
[*]In 'htop' you don't need to type the process number or    the priority value to renice a process, in 'top' you do.
[*]'htop' supports mouse operation, 'top' doesn't
[*]'top' is older, hence, more used and tested.
[/LIST]

To use it, type it from a Terminal :

```
htop
```

---

### Post by Ifaistos on 2011-11-10
I have installed htop and it runs just fine.
It looks like a text version of the System Monitor.

Is there something specific I should be looking for in order to find out which program(s) is constantly accessing my HD?

---

### Post by e79 on 2011-11-10
I think I misunderstood the question at first, sorry. If you are trying to see which process reads/writes to your disk, you'll need 'iotop'.

to install:
```
sudo apt-get install iotop
```

to use:
```
sudo iotop
```

It ressemble top and htop, but only for IOs activity.

Hope this helps

---

### Post by Ifaistos on 2011-11-12
I installed Iotop.

It seems that there is only one thing constantly accessing my HD's.
Picture attached.

Can anyone understand what this is, and how do I stop it?

---

### Post by Ifaistos on 2011-11-13
bump :-)

---

### Post by xcal8bur on 2011-11-13
did anybody find a solution to this problem? my system seems to be affected as well, I thought it was because of my RAID setup.
 
do you have a RAID setup Ifaistos?

---

### Post by Ifaistos on 2011-11-13
Hello xcal8bur :-)

Nope, no solution yet.
If you do have the same problem, could you please follow the same procedure as me and post the results of the iotop?

I think that would be helpful to anyone who would try to address the issue.

I don't have raid on my system.
I have only what is mentioned in my signature.

Thanks.

---

### Post by Ifaistos on 2011-11-14
bump :-)

---

### Post by e79 on 2011-11-14
> **Ifaistos said:**
> I installed Iotop.

It seems that there is only one thing constantly accessing my HD's.
Picture attached.

Can anyone understand what this is, and how do I stop it?

Referring to your screenshot I see nothing suspicious here, other than this --enable-print-preview (which is not doing a lot of IOs as far as I can see).

What if you kill/stop the process, does your disk activity lowers ?

---

### Post by Ifaistos on 2011-11-14
It is the only process doing the io.
It does a little bit each time, but constantly...

What is this procedure?
How do I kill it?

---

### Post by e79 on 2011-11-14
Fire up **htop** now that you might have a clue about which process(name) is giving you these IOs and search for it; you can scroll down with your arrows if you don't see it at first. Once selected, press F9 to kill it and see if your IOs spikes stops.

or 

I'm not sure this is the real name of the process but if so, you could do something like this to discover its PID (process ID)

```
pidof --enable-print-preview
```  (but again, I doubt it is the real name)

If it works, it would simply return a random number, which would be the PID of the said process. So let's say the command returns you the number 12225.

You would then

```
kill 12225
```to terminate the process.

hope this helps

---

### Post by Ifaistos on 2011-11-14
Hello e79 :)

Thank you for your suggestions.
htop is not needed.  iotop has the pid of the process.
I killed it and immediately the io accesses have stopped.

As soon as I killed it Tampermonkey (an extension to chrome) crashed.
I got an error : Tampermonkey has crashed.  Click this balloon to reload the extension.

Once I click on the ballon, another process is started and accesses to the HD started again.  As soon as I kill the new process it, tampermonkey crashes again, and io to the HD stops.

So it is now obvious that this is what was creating the problem.
How would you go about fixing it?
I want tampermonkey, but I don't want the process.
Could this be an Ubuntu, Chrome or Tampermonkey bug?
I had the same extension in Chrome before I upgraded and didn't have that problem...

Whatever the case, thank you very much for your help and support!!

---

### Post by Ifaistos on 2011-12-14
I just wanted to let everyone know, if they have the same problem with me that I "solved" the case.

The problem was with two tampermonkey scripts.
I also noticed that those same tampermonkey scripts were doing the same HD accesses on windows as well.

Once I disable them everything is fine.
That was a tricky bug...

Thank you everyone for your time and help :-)

---

