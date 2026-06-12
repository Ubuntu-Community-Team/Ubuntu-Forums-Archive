---
title: "Battery Icon"
date: 2012-09-17
forum: Installation &amp; Upgrades
---

### Post by Wer Bn on 2012-09-17
Hello guys
I have Ubuntu 12.04.

Today I used my laptop battery and the icon doesn't show up.
I already chose "Show battery status when battery's plugged in"

It doesn't show up.
Thanks in advance.

---

### Post by Wer Bn on 2012-09-18
Hello!!!

---

### Post by newb85 on 2012-09-18
Try this:

```
$ gsettings list-recursively | grep settings-daemon.*.power\ active
```

The resulting line should end in *true*.  If it doesn't

```
$ gsettings set org.gnome.settings-daemon.plugins.power active true
```

should set things straight.

---

### Post by Wer Bn on 2012-09-18
Nop.
Nothing happens :(

---

### Post by newb85 on 2012-09-18
> **Wer Bn said:**
> Nop.
Nothing happens :(

What was the result of the first command?

---

### Post by Wer Bn on 2012-09-18
> **newb85 said:**
> What was the result of the first command?
iT WAS TRUE

---

### Post by Wer Bn on 2012-09-18
Cmon.
No one?
Please.
I wanna know how my battery's holding!!!

---

### Post by Laiquendi on 2012-09-18
Try changing it to some other options like "when charging", it's quite strange.

---

### Post by Wer Bn on 2012-09-18
Already did that
*sigh*
This is annoying.
Only happens to me.

---

### Post by newb85 on 2012-09-18
You haven't provided a lot of information.  Is your 12.04 setup an upgrade from a previous release, or a fresh install?  Has the power indicator ever worked correctly, and if so, can you think of anything you changed/installed/removed right before it stopped working?

Please post the output of the following

```
$ sudo lshw -C power
```

Also, make sure indicator-power is installed (and post the output of the following)

```
$ sudo apt-get install indicator-power
```

---

### Post by newb85 on 2012-09-18
> **Wer Bn said:**
> Only happens to me.

Not true.
[http://ubuntuforums.org/showthread.php?t=2055512&highlight=indicator-power]("http://ubuntuforums.org/showthread.php?t=2055512&highlight=indicator-power")
[http://ubuntuforums.org/showthread.php?t=1999971&highlight=power+indicator+missing]("http://ubuntuforums.org/showthread.php?t=1999971&highlight=power+indicator+missing")
[http://ubuntuforums.org/showthread.php?t=2052156&highlight=power+indicator+missing]("http://ubuntuforums.org/showthread.php?t=2052156&highlight=power+indicator+missing")

---

### Post by Wer Bn on 2012-09-19
It shows :
"sudo: incapaz de resolver máquina Extensa-5635G"

Translated to english: incapable of solving machine Extensa-5635G


And the indicator was already installed

---

### Post by Wer Bn on 2012-09-19
So, no solution?

---

### Post by newb85 on 2012-09-19
> **Wer Bn said:**
> It shows :
"sudo: incapaz de resolver máquina Extensa-5635G"

Translated to english: incapable of solving machine Extensa-5635G

This wasn't the output of

```
sudo lshw -C power
```

was it?

---

### Post by Wer Bn on 2012-09-21
CPUID
PCI (sysfs)

---

### Post by newb85 on 2012-09-21
Your battery is going undetected.  Please answer the questions in post #10 and tell what kind of machine it is.

---

### Post by Wer Bn on 2012-09-21
Sorry.
The moment I did the command the battery wasn't in the computer.

It's a Acer Extensa 5635G
It's a fresh 12.04 install

The computer detects the battery. I'm pretty sure.
It detected in Win 7 and showed the icon.

I've runned the computer in Ubuntu with the battery only and it worked.
Problem was I didn't know the percentage of it.

The output of the command with the battery in:
CPUID
PCI (sysfs) 	
SCSI

Just a curious fact: it's not a normal output... its really fast and then vanishes.
The next prompt goes right into the next line.

---

### Post by newb85 on 2012-09-21
The question isn't whether the physical machine detects the battery, it's whether the OS detects it.   The machine should be able to run on battery power without the OS doing anything.

What is the output of
```
sudo lshw -short
```

---

### Post by Wer Bn on 2012-09-22
Sorry I didn't answer any sooner.
The thing is right now I don't have the laptop.

But I'll answer as soon as possible.
I am aware of your efforts.

Thanks.

---

### Post by Wer Bn on 2012-09-22
Same thing, and then:

[http://i.imgur.com/JIAXm.png](http://i.imgur.com/JIAXm.png)

[http://i.imgur.com/kzQtI.png](http://i.imgur.com/kzQtI.png)

---

### Post by Wer Bn on 2012-09-23
Guys... hello!

---

### Post by Wer Bn on 2012-09-24
Hello. I already posted result of the command

---

### Post by newb85 on 2012-09-24
Yes, and the output indicates that the OS isn't detecting the battery.  The problem isn't the icon or the indicator.

Your best bet is probably to start a new thread in the Hardware & Laptops forum with a title like "sudo lshw -C power doesn't show battery".

By the way, please copy and paste such outputs as text, rather than screenshots, per forums terms of use.

---

### Post by Wer Bn on 2012-09-24
Thank you
I'll do that

---

