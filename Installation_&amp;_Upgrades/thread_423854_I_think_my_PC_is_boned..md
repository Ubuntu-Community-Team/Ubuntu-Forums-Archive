---
title: "I think my PC is boned."
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by crimson90 on 2007-04-26
Just so there will be no confusion, I'm typing this from school.

I popped in the CD and started installing Ubuntu. When it was installing the base system files, a few were corrupted, and I couldn't go on, so I aborted. After my computer shut down, I turned it back on and got the most dreadful thing in the world--"Missing operating system_"

I thought to myself, thinking, No big deal. I can just pop in my recovery CD and fix it good-as-new. I went through all of the steps and whatnot. When it was done, it told me to eject the disc and then press any key to continue. I obliged, and the computer proceeded to reboot. After the Toshiba boot up screen, rather than starting up Windows XP, I get this message--"Missing operating system_"

Is my PC boned or can I still salvage Windows?

P.S.: Please, no one say "Ubuntu is better anyway!" or "Down with Gates!" because I've got a lot of software that cost me good money and I don't want it all to go down the drain. I love Windows, and I don't want to loose it.

---

### Post by bashologist on 2007-04-26
If you're having problems with Feisty maybe you would want to try Debian. Maybe you can burn another cd somehow then run the test which you can find when you boot with the cd in. Did you try the test?

You should manually mount your windows partition and personal files and check if they still exist.
```
sudo fdisk -l
sudo mkdir /mnt/windows
sudo mount /dev/sda1 /mnt/windows
```
Change sda1 with whatever you think your windows is on based on the fdisk command.

---

### Post by crimson90 on 2007-04-26
I'm sorry, but I understood none of what you said. Could you explain it to me in n00b terms? :)

---

### Post by bigken on 2007-04-26
ok what you need to do is boot from windows xp disc

at the prompt select R for repair 

this takes you to a console 

type **fix mbr** then hit enter 

then type **fix boot** hit enter 

then type** exit **

your pc should then boot back into win xp :)

---

### Post by crimson90 on 2007-04-26
I don't have a Windows XP disc. Am I supposed to get one with a computer from a manufacturer? If it helps, I have a Toshiba laptop.

---

### Post by bashologist on 2007-04-26
> **crimson90 said:**
> I'm sorry, but I understood none of what you said. Could you explain it to me in n00b terms? :)
Aight, wh4t j00 d0 i$ b00t j0ur linx Cd, th3n Wh3n UbUntU $t4rt$ y0u G0 Int0 4 t3rmIn4l 4nd p4$t3. n_n

Jk, you goto the -> applications -> accessories -> terminal -> then paste the above command. If they won't let you use sudo for some reason then try the below command:
```
sudo su
fdisk -l
mkdir /mnt/windows
mount /dev/sda1 /mnt/windows
nautilus /mnt/windows || konqueror /mnt/windows
```Then you'll see if your files are nice and safe.

---

### Post by hyperair on 2007-04-26
Go get the Windows XP setup boot diskettes from the instructions here: [http://support.microsoft.com/kb/310994/](http://support.microsoft.com/kb/310994/)

Then somehow get to your recovery console, and log into your Windows installation with your admin password and whatnot, and then run this command: 
```

fixboot C:

```

---

### Post by rillip on 2007-04-26
If you don't have an XP cd, then Toshiba probably provided some sort of recovery disk that will do the same thing.  You can probably fix your MBR from there

---

### Post by bigken on 2007-04-28
any windows xp cd will do the job cant you borrow one 

if you run the master cds that came with your laptop they will delete everything

---

