---
title: "Problem installing from live USB, looks linked to GParted"
date: 2015-11-20
forum: Installation &amp; Upgrades
---

### Post by zakrapovic on 2015-11-20
Hello everyone,

After a random nvidia update I had some issues and fragged my whole system in a desperate backup attempt
It was sad, but it went worse as I am not even able to install any kind of unbuntu from a live USB anymore

1. I can boot on ubuntu and then initialize the installation process, but then it fail in a non stop loading process. It happens at the end of the step that should lead to the partitioning one.
2. If I run GParted directly from the live distribution, it fail by scanning forever.
3. From an other UNIX (dual boot with elementaryOS) if I run GParted it works and display my partitions properly.

I wasted a lot of time already trying to figure out what goes wrong. 

Any help would be great.
Thanks

---

### Post by yancek on 2015-11-20
You forgot to post the GParted output from Elementary.  Not much anyone can suggest without that information.

---

### Post by sudodus on 2015-11-21
Welcome to the Ubuntu Forums, zakrapovic :-)

The more you tell us about your computer, what system you had running, and what you want to install, the better we can help you.

So after answering *yancek's* question, please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

What operating system and version were you running before the problem with the nvidia update? (example Ubuntu 14.04 LTS).

Are there any particular programs or tasks that are important for you?

The flavour of Ubuntu - Kubuntu, Lubuntu, ... Xubuntu - can make a difference, and it depends on the computer hardware and the programs and tasks.

---

### Post by zakrapovic on 2015-11-21
Solved!

GParted was endlessly scanning my HDD data. 

WORKAROUND : To avoid it to be scanned during installation procedure, mount the disk first then launch the installation, it will be omitted at the partitioning step.

I still do not know why it was failing...

Thank you very much for your help

---

