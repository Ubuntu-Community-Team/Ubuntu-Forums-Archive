---
title: "Update manager always shows &quot;Downloading 0B of 1B&quot;"
date: 2011-04-09
forum: Installation &amp; Upgrades
---

### Post by duk3r on 2011-04-09
The title of the thread says it all. Don't know why, the update manager keeps getting 0B of 1B since yesterday morning. Found some other references to this problem but couldn't locate an answer to this problem.

Does anyone know the reason why I keep getting this? Don't know if there are any updates released since yesterday, but can't find anything with this message.

---

### Post by dabl on 2011-04-09
It sounds like your system is not getting a response from the repository servers.  Are other networking things (i.e. browser) working correctly?

---

### Post by duk3r on 2011-04-09
Yes that's the odd thing... Everything works as it should. But update manager keeps getting this 0B of 1B.
Bars fill for many times and then it says there is no new updates.

I don't mind not having new updates of course, but before that I could see actual download rate of packages there...

---

### Post by dabl on 2011-04-09
Can you pop open a terminal and do this:

```
sudo dpkg --configure -a
```

```
sudo apt-get update
```

and post back with any errors that you get.

---

### Post by duk3r on 2011-04-10
No errors :/

---

### Post by dabl on 2011-04-10
OK.

In the terminal:

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

What do you see?  Did it run and install the updates?

---

### Post by hawthornso23 on 2011-05-26
I'm seeing this too. Note that update manager seems fully functional. I believe this to be a cosmetic error - namely failing to display the correct download rate in the GUI.

---

### Post by farpost on 2011-06-01
I am also seeing this.  Did clean install 64bit 11.04 and was doing software update when system went to sleep.  When woke up system am now always getting "Downloading 0B of 1B" when I do a system update.  Tried using synaptic but no help.  Went to 64bit due 32bit installed always bombed out and hung at: "Kernel_thread_helper+0x6/0x10"
Using MSI 890GXM-G65 (MS-7642) 1.0 mainboard w/latest BIOS & AMD Phenom II X6 1055T.

---

