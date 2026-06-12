---
title: "Update problem -Package Manager"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by robdashu on 2011-01-15
When I click "Install" in Package Manager I get a popup box with the error:

"Failed to lock the Package Manager"

Details: The package indexes are currently changed by apt-get.


I had been having the problem that apt-get wanted to run forever.  After 10 seconds or so I would end the process apt-get, and package manager would finish up.  Now I have this new, different problem.

Help!

---

### Post by Ad@m on 2011-01-15
Reboot your system and try again.

---

### Post by dino99 on 2011-01-15
the indexes are corrupted, so close each opened app first. Then into a terminal, run:

sudo rm /var/cache/apt/archives/*

then update upgrade again

note: inside synaptic (system admin synaptic) check that "main" server is used (for better experience)

---

### Post by robdashu on 2011-01-15
Tried your suggestions dino99, with same problem still occurring.

Further text in the error message "Failed to lock ",etc:

Failed to lock the package manager

"Check if you are currently running another software management tool, e.g. Synaptic or aptitude. Only one tool is allowed to make changes at a time."

Are there keys somewhere telling which apps can access db?

I've been running Synaptic right along, but only on occasion, and it's certainly not actively running at the moment.  Can't these two get along?

---

### Post by gnu_bee on 2011-01-16
[robdashu]("http://ubuntu-virginia.ubuntuforums.org/member.php?u=718100"), I just resolved a similar problem with my Ubuntu 10.10 installation. I've been playing with it for the past two weeks and today I decided to check for updates. I opened the update manager and when I clicked the install button, I got the same error "  **Failed to lock the Package Manager**". Earlier I had modified the system/administration menu to add **"Software Sources". **Once I uninstalled the "Software Sources" menu item, I was able to use the Update Manager to install the latest updates. That's what worked for me, and I hope I have been some help in resolving your problem.

---

### Post by robdashu on 2011-01-18
Thanks,gnu_bee.  I am unable to find that "Software sources" option.  I did figure out that the Synaptic Package Manager will perform the same function (apparently) as the Update Manager if one selects "Recommended updates" (or something to that effect).

So I'm just going to use the Synaptic Package Manager instead of update manager.

Does anyone know of any problems I might create going this way?

---

### Post by cx1964 on 2011-02-15
I just experienced the same problem as robdashu

"When I click "Install" in Package Manager I get a popup box with the error:

"Failed to lock the Package Manager""



I am also now forced to use Synaptic to apply new updates.

---

### Post by fr0d0 on 2011-03-21
I have just created an empty /var/lib/apt/lists/lock file and everything is ok!:guitar:
Fedor Biryukov.

---

### Post by HaRabAS on 2011-04-10
is this solved already?

---

### Post by zodiacdm on 2011-04-23
> **fr0d0 said:**
> I have just created an empty /var/lib/apt/lists/lock file and everything is ok!:guitar:
Fedor Biryukov.

Yep, just had this problem, and Fedor's solution worked for me too.

sudo rm /var/lib/apt/lists/lock
sudo touch /var/lib/apt/lists/lock

---

### Post by Robert Lutken on 2011-09-07
> **fr0d0 said:**
> I have just created an empty /var/lib/apt/lists/lock file and everything is ok!:guitar:
Fedor Biryukov.

This worked for me too 

Thanks all

---

### Post by escorpionmex on 2012-01-04
I hope this helps but this is how i fixed my problem
do : ubu@Asus:~$ sudo pgrep -l apt-get 
if apt-get is running is gonna give you the process id number then do: ubu@Asus:~$ sudo kill -9 25189
in my case that was the id number of apt-get then try again doing the update it should work now it work for me

---

