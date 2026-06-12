---
title: "Hidd? Interprid"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Depressed Man on 2008-10-18
I'm testing out the new beta on my laptop and it's running like a charm so far. Only minor problems such as the scale plugin with the keypress not operating correctly. For example, I had it set in Hardy so I could press F10 for scale and it would pop up and let me choose the window without holding down the key. Which I have to hold down now for some reason (if I wanna use the keypress method).

But other then that, things have been smooth. I'm trying to use hidd but it seems the command doesn't register. 

For example..

```
vforviktor@vendetta-laptop:~$ sudo hidd
[sudo] password for vforviktor: 
sudo: hidd: command not found
vforviktor@vendetta-laptop:~$ 

```

I do have bluez (comes with system). And  I know I need the bluetooth address, but my point is it doesn't seem to even register  hidd as a command.

---

### Post by exactt on 2008-10-20
i am also missing hidd in Intrepid AMD64. what is happening here?

edit: i just found [https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/283735](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/283735)

---

### Post by Mr. Picklesworth on 2008-10-20
Any guess how I can convince this new GUI tool to treat my N810 like a human input device on occasion? Naturally, it's a handheld computer, so it does more than *just* human input. I have a program on the N810 that makes it act as a Bluetooth remote control, but at the point of telling Ubuntu to treat it as such I'm stumped. (The device is known and trusted in Bluetooth preferences).

What happened to that dialog where you choose bluetooth services to enable and disable?! I'm assuming it's automagic now. I hope it is, anyway...


> **Depressed Man said:**
> HIDD profile is gone, kinda stinks since I was going try out bluemaemo (let's me use my n800 as a HIDD input device for my computers)

I tried installing the KDE equivilant but it doesn't seem to load when I click the icon.
Woah, we're in the exact same boat! Small world :P

---

### Post by Bruno Abinader on 2008-10-21
> **Mr. Picklesworth said:**
> Any guess how I can convince this new GUI tool to treat my N810 like a human input device on occasion? Naturally, it's a handheld computer, so it does more than *just* human input. I have a program on the N810 that makes it act as a Bluetooth remote control, but at the point of telling Ubuntu to treat it as such I'm stumped. (The device is known and trusted in Bluetooth preferences).

What happened to that dialog where you choose bluetooth services to enable and disable?! I'm assuming it's automagic now. I hope it is, anyway...



Woah, we're in the exact same boat! Small world :P

Same stuff here... seems like bluez-utils package, which should have 'hidd' binary for default, misses it on Ubuntu :(

---

### Post by PinkFloyd102489 on 2008-10-21
You dont need it. It appears that the bluetooth stack has been overhauled. Every bluetooth device I have is able to be connected at the same time now. Even my bt mouse and touchpad work in tandem now.

---

### Post by Depressed Man on 2008-10-27
Hmm, I read about the changes. It's just connecting the hidd device actually involves using the hidd command. A workaround was found Mr. Picklesworth on the internettablettalk forum in the thread for bluemaemo. The problem is the device doesn't support HIDD by default, the program enables HIDD so maybe when connecting the device if the program runs.. hmm

---

### Post by maschnitz on 2008-10-27
[This]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/281580") is an Ubuntu bug on Bluetooth issues.  There are several interesting things here.

One is that there's a "bluez-compat" package reintroduced that gives you back hidd.  Should be useful for some people.

The other is that someone had some success deleting/moving everything in /var/lib/bluetooth/[uid]/ and restarting bluetooth.

Neither worked right away for me, though.

**EDIT** - Got it working, finally, with "bluez-compat" installed, by adding HIDD_ENABLED=1 etc to /etc/default/bluetooth, as described [here]("http://sudan.ubuntuforums.com/showthread.php?t=432013").

---

