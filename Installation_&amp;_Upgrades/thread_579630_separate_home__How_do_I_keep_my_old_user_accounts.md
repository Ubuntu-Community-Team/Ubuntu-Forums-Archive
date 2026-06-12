---
title: "separate /home:  How do I keep my old user accounts?"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by hanzomon4 on 2007-10-18
I'm doing a clean install and I have separate /home partition. How do I keep my old user accounts?

---

### Post by dc. on 2007-10-18
Your User accounts are not stored in your home-partition

---

### Post by maybeway36 on 2007-10-18
Yes they are...

---

### Post by ebichete on 2007-10-18
Have you tried pointing the migration-assistant at your seperate /home partition?

- Edward -

---

### Post by hanzomon4 on 2007-10-18
No, I haven't even tried the disk yet. I hoped some one would have a clear answer.

---

### Post by earobinson on 2007-10-18
Im pretty sure as you install you can point it to your home partition. I would also copy your home partition to a seperate drive that way if something goes wrong you can just copy it back in.

---

### Post by hanzomon4 on 2007-10-18
I'll give it a shot, can't do a backup cause I got over 200gb. But careful I shall be....

---

### Post by Dafydd on 2007-10-18
> **hanzomon4 said:**
> I'll give it a shot, can't do a backup cause I got over 200gb. But careful I shall be....

Buy a LACIE or something. If you have my luck, something will go wrong...

daf

---

### Post by hanzomon4 on 2007-10-18
> **earobinson said:**
> Im pretty sure as you install you can point it to your home partition. I would also copy your home partition to a seperate drive that way if something goes wrong you can just copy it back in.

Ok, that won't work. Migrate Assistant doesn't pickup my feisty. I mounted my old feisty /home as my new gutsy /home unformatted. It's now asking me to create my login user, do I just put in my old user from feisty?

---

### Post by hanzomon4 on 2007-10-18
Hell, I'm just going to go for it. If it works I'll post back.

---

### Post by rbmorse on 2007-10-18
I'm sorry I did n't see this sooner.  When the installer asks you to create a user and user account, use the same information you used for one of your existing user accounts.  Complete the installation.  If the partitioning step lets you chose another partition for /home select your existing /home, otherwise just let it run normally and fix fstab afterwards. 

When the system restarts the first time after you mount your exisiting /home as /home (!)  you can log in as your old user, then recreate any other user accounts using the same credientials.

---

### Post by hanzomon4 on 2007-10-18
Yeah that's what I did and it worked, aside from some strangeness. My themes didn't work, I lost my wallpapers(stored in the /usr/share/backgrounds), I have old apps in my menus that are no longer installed, the slab-menu has extra crap in the places section and it tries to launch urxvt when I click on the terminal icon(my preferred terminal is set as gnome-terminal). 

Other then the residual settings it went great, a lesson learned.

---

