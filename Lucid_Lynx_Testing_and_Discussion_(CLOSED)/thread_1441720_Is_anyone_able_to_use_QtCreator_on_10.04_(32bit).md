---
title: "Is anyone able to use QtCreator on 10.04? (32bit)"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mdurham on 2010-03-29
I haven't been able to use QtCreator for weeks now. When I try to run it, it permanently hogs the CPU and nothing ever appears on the screen. There is no output when run from a console either. I can't believe that a major piece of software like this will be ignored with the Ubuntu final Beta due for release within a few days.
Cheers, Mike

---

### Post by alexfish on 2010-03-29
Hi

On my system the QT creator is acting very strange

the first load hangs , no window ,the system monitor shows 2 bins one sleeping and one zombie

clicked for another Qt creator , and one fired up, then a while later another window

the system monitor shows 2 zombies and 3 sleeping

now got 3 windows of qt creator on the desktop (Cripes), clicked them all off and the system monitor shows one sleeping and one zombie

going to try a killall,

also used the Package cleaner in Ubuntu tweak, Now works :EDIT doing it again  + all CPU when CPU is on Demand

forgot , had qtdesigner in ubuntu 9.10 then upgraded to Lucid beta

---

### Post by mdurham on 2010-03-29
Thanks for replying alexfish, it's good to know that I'm not alone.
I reported this as a bug several weeks ago but I don't think it's been taken seriously as it hasn't been assigned to anyone yet.
You could add to the bug report if you like, it's [here.]("https://bugs.launchpad.net/bugs/517364")
Cheers, Mike

---

### Post by SevenMachines on 2010-03-29
I thought it was hanging but if i leave it for a couple of minutes it starts, it also takes a couple of minutes for the process to die on close. somethings wrong somewhere obviously. this is on quite a fast computer so i imagine it might take even longer on others

---

### Post by SevenMachines on 2010-03-29
seems to be waiting on a lock for a long time (.config/Nokia/qtcreator/.helpcollection/lucene-...-write.lock) ?

i only guess at that because this lockfile isnt removed on program exit. are either of your problems similar?

---

### Post by mdurham on 2010-03-29
> **SevenMachines said:**
> I thought it was hanging but if i leave it for a couple of minutes it starts, it also takes a couple of minutes for the process to die on close. somethings wrong somewhere obviously. this is on quite a fast computer so i imagine it might take even longer on others
Thanks SevenMachines, I've never left it for that long. It took 3-4 mins before appearing on the desktop. Problem is, it constantly uses 90+% CPU. I hope they fix it soon, I'm fed up booting back to Karmic to use it.
Cheers, Mike

---

### Post by SevenMachines on 2010-03-29
the problem here is definitely the age qtcreator is taking to generate the help collection. if left for a while running the generation completes and then qtcreator starts and stops quickly. i can't imagine program start should be being held up by the help info generating thread though

---

### Post by SevenMachines on 2010-03-29
mdurham: I think if you leave it running for a while the help creation stage finishes and it shouldnt max out your cpu, its broken in some way though

---

### Post by mdurham on 2010-03-29
> **SevenMachines said:**
> seems to be waiting on a lock for a long time (.config/Nokia/qtcreator/.helpcollection/lucene-...-write.lock) ?

i only guess at that because this lockfile isnt removed on program exit. are either of your problems similar?

Where did you see this message? I get nothing in the console. Also, if it were waiting on a lock, would it use 90% CPU whilst doing so? V strange!

---

### Post by SevenMachines on 2010-03-29
its not waiting on the lock, the lock is the sign that the process thats using up the cpu and delaying start is the help collection generation. the file disapears when this process is finished. you can see this if you run
$ gdb qtcreator.bin

---

### Post by SevenMachines on 2010-03-29
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=572493](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=572493)
looks like it, seems its known upstream

---

### Post by SevenMachines on 2010-03-29
temporary workarounds
* disable the help system by running 'qtcreator -noload Help'
or
* leave qtcreator running until the help collection has finished  generating (may take several minutes. the next start should then no  longer have a delay

---

### Post by mdurham on 2010-03-29
> **SevenMachines said:**
> temporary workarounds
* disable the help system by running 'qtcreator -noload Help'
or
* leave qtcreator running until the help collection has finished  generating (may take several minutes. the next start should then no  longer have a delay

Thanks for that.

Edit:
disabling the help system: allows it to start but can't open any projects

leaving qtcreator running until the help collection has finished: works until I have to reboot.

Cheers, Mike

---

