---
title: "Update Manager and Synaptic"
date: 2009-07-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tad1073 on 2009-07-01
Updates broke update manager, synaptic package manager and software sources.

have to do every thing from the command line.

---

### Post by FarJumper on 2009-07-01
Confirm. 
When synaptic is invoked from System -> Administration only prompt for root password appears and that's all. 
It works ok from the command line.

---

### Post by descendent87 on 2009-07-01
starting syanptic from terminal works fine
[http://ubuntuforums.org/showthread.php?t=1201413]("http://ubuntuforums.org/showthread.php?t=1201413")

---

### Post by tad1073 on 2009-07-01
Bug reported.

> **davideotape said:**
> Rebooted fine, but synaptic still isn't working. [https://bugs.edge.launchpad.net/ubuntu/+bug/394210](https://bugs.edge.launchpad.net/ubuntu/+bug/394210) is the bug I've filed, so please could someone confirm it :D

---

### Post by tjeremiah on 2009-07-01
have to do everything via terminal now.

---

### Post by dino99 on 2009-07-01
Fix commited (debian dev answer on launchpad)

problem in libgtk

Just wait and see ):P

---

### Post by jppr on 2009-07-01
just updatet libgksu2-0 (2.0.12-1ubuntu1) to 2.0.12-1ubuntu2 and solved the problem :)

---

### Post by tjeremiah on 2009-07-01
> **jppr said:**
> just updatet libgksu2-0 (2.0.12-1ubuntu1) to 2.0.12-1ubuntu2 and solved the problem :)

yup, same. They are quick to fix things :)

---

### Post by jppr on 2009-07-01
> **tjeremiah said:**
> yup, same. They are quick to fix things :)


  yup, but... there are still a few other small problem with the system :)

---

### Post by rudenko_ruslan on 2009-07-01
> **jppr said:**
> yup, but... there are still a few other small problem with the system :)
Like what? I've only encountered problems with Update Manager & Synaptic.

---

### Post by tad1073 on 2009-07-01
They jumped on that fast.

---

### Post by jppr on 2009-07-01
> **rudenko_ruslan said:**
> Like what? I've only encountered problems with Update Manager & Synaptic.

i must run system 2.6.30 kernel, i upgraded the morning of 2.6.31 but it does not work...

---

### Post by rudenko_ruslan on 2009-07-01
> **jppr said:**
> i must run system 2.6.30 kernel, i upgraded morning 2.6.31 but that don´t works...
Hmm... I upgraded to that kernel, and it didn't work for me too (because of NVIDIA Driver's, I suppose). Something with DKMS :-k

---

### Post by jppr on 2009-07-01
when i did the kernel update came some nvidia error

---

### Post by ronacc on 2009-07-01
the new kernel is working fine with a patched Nvidia driver compiled with gcc-4.2 . see this thread [http://ubuntuforums.org/showthread.php?t=1197084](http://ubuntuforums.org/showthread.php?t=1197084)

---

### Post by davideotape on 2009-07-01
> **rudenko_ruslan said:**
> Hmm... I upgraded to that kernel, and it didn't work for me too (because of NVIDIA Driver's, I suppose). Something with DKMS :-k

Same here, see this: [https://bugs.edge.launchpad.net/ubuntu/+bug/394343/+edit](https://bugs.edge.launchpad.net/ubuntu/+bug/394343/+edit)

---

### Post by dino99 on 2009-07-01
new libgksu2-0 in the repo

with it , update manager & synaptic work again without trouble

---

### Post by dino99 on 2009-07-09
bad thing this morning:

update-manager find new packages but screen turn greyed & resume never ended: closing update-manager & reopen it allow to update

---

### Post by rudenko_ruslan on 2009-07-09
> **dino99 said:**
> bad thing this morning:

update-manager find new packages but screen turn greyed & resume never ended: closing update-manager & reopen it allow to update
Have this issue too. I'm updating through Terminal for now ;)

---

### Post by tad1073 on 2009-07-09
I have a similar issue, the busy mouse icon keeps spinning, but I am able to install updates.

---

### Post by dino99 on 2009-07-09
i've run dpkg-reconfigure update-manager to see if it resolve the problem but don't. Curiously i don't known which recent update can do that .

---

