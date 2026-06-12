---
title: "uninstalling and reintalling ubuntu"
date: 2011-03-29
forum: Installation &amp; Upgrades
---

### Post by qtsushigirl on 2011-03-29
I was relieved to read online that I'm not the only first-time Ubuntu user to destroy their system beyond repair and wish to uninstall and reinstall Ubuntu. However, all the tutorials I can find on how to do it are for users who have a dual operating system on their computer, especially XP and Vista. Ubuntu is my sole operating system (I decided to give it a try when my computer crashed and needed to be rebooted with a new operating system). 

Is there a way to just remove my entire Ubuntu operating system from my laptop and reinstall it? I've already downloaded Ubuntu onto my jump drive and it's all set to reinstall. Tutorials claim that restarting my laptop with the jump drive inserted in my laptop will automatically startup the Ubuntu installation process but it doesn't, and I'm sure it's because I still have Ubuntu on my laptop. 

Thank you in advance! 

Sincerely,

qtsushigirl

P.S.

Stats: 

Gateway NV52

Formerly Windows Vista, but that was removed and Ubuntu (Linux) is now the sole operating system

Gnome

Ubuntu 10.04 LTS

---

### Post by Jechem on 2011-03-29
Set the boot order in BIOS so that the first to boot would be your removable device. Some need to press esc or F11 in order to access the boot options. Once the LiveUSB boots you can then run the installer and wipe the whole hard drive.

---

### Post by Dutch70 on 2011-03-29
You shouldn't have to do anything except boot up the live cd/usb stick and install Ubuntu. No need to uninstall. 
Just select "use entire disk" when you get to that option.

---

### Post by ajgreeny on 2011-03-29
An even better way to proceed is set out in detail at [Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome")

If you do it this way, next time you completely kill your system, you will be able to keep your home files and folders intact and save a lot of the time spent resetting your configurations.

Of course, if it's your configurations that are broken, you would have to deal with that, but it is quite easy to do, if that is your problem; just ask here and answers will appear like magic.

---

### Post by qtsushigirl on 2011-03-29
> **Jechem said:**
> Set the boot order in BIOS so that the first to boot would be your removable device. Some need to press esc or F11 in order to access the boot options. Once the LiveUSB boots you can then run the installer and wipe the whole hard drive.

I've been looking up what BIOS and "boot" are and I'm guessing it's an option in the startup menu. I won't be surprised if I'm wrong. If that is the case though I haven't seen a startup menu since getting Ubuntu. It just goes straight to my desktop whenever I turn it off and on or restart. 

Thank you everyone for the help! Sorry to be a handful, I'm a beginner.

Also - I've been pressing the ESC key and F11 when the screen in still black when it's starting up and it doesn't do anything. It still goes straight to my desktop.

---

### Post by garvinrick4 on 2011-03-29
You have to be quick and a lot of times it is F10 or F2

---

### Post by qtsushigirl on 2011-03-29
> **garvinrick4 said:**
> You have to be quick and a lot of times it is F10 or F2

Thank you! It was F2 and I got to that setup screen. I adjusted the settings so it goes to my USB drive first, but then it goes to a black screen where it asks for a command. Is it a problem that there are other files on my USB drive besides the Ubuntu system download? I'm going to go put those extra files onto another computer and see if it'll work then.

---

### Post by qtsushigirl on 2011-03-29
> **qtsushigirl said:**
> Thank you! It was F2 and I got to that setup screen. I adjusted the settings so it goes to my USB drive first, but then it goes to a black screen where it asks for a command. Is it a problem that there are other files on my USB drive besides the Ubuntu system download? I'm going to go put those extra files onto another computer and see if it'll work then.

Nope, still asks for a command. Specifically it says " boot: " and says "cannot find kernel" for whatever I type in. 

I'm going to download Ubuntu onto my USB drive one more time and see if it'll work.

---

### Post by Dutch70 on 2011-03-29
Type in "live" without the quotes and hit enter.

---

### Post by qtsushigirl on 2011-03-30
Before receiving the above message I was getting all antsy and played around with my Synaptic Package Manager and found a "history" option when right-clicked it. I started reinstalling everything I had uninstalled in the last few days (assuming I didn't need them or something - don't repeat my mistakes!) and most of the problems were fixed! After a few hours I managed to find online help for the other remaining problems (sound not working, etc.) and everything is all better!

I do not doubt my ability to mess things up again in the near future so I'm still very grateful for everyone's input. I'm so glad I have my jump drive all ready to go if I ever do mess up my Ubuntu beyond repair!

---

### Post by mörgæs on 2011-03-30
Good, please mark the thread 'solved' using 'thread tools'.

---

