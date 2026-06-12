---
title: "System hangs on Ubuntu 16.04"
date: 2017-03-26
forum: Installation &amp; Upgrades
---

### Post by venujee on 2017-03-26
The desktop system hangs while starting up.
The peculiarity is that it does not happen so when I log in as a guest.
The caps lock and the scroll lock keep blinking.
Can somebody help ?

---

### Post by mörgæs on 2017-03-27
Hi, welcome to the fora.

Which hardware are you using?

---

### Post by RobGoss on 2017-03-27
I recently had this issue on one of my systems running 16.04.2, it would only hang when I restarted my system

I search for a solution and came across this post that fixed my hanging issue it may also solve yours

[http://askubuntu.com/questions/760952/slow-shutdown-on-ubuntu-16-04-lts-stopping-thermal-daemon-running-fit-make-remo](http://askubuntu.com/questions/760952/slow-shutdown-on-ubuntu-16-04-lts-stopping-thermal-daemon-running-fit-make-remo)

I ran this command:
```
 
sudo systemctl disable cups-browsed.service
```

---

### Post by venujee on 2017-03-28
Intel Core 3-2100 CPU @ 3 GHz *4

64 bit
desktop

Thanks .
When I try that, I get the following warning:
[B]current start runlevel(s) (empty) of script `cups-browsed' overrides LSB defaults (2 3 4 5).
insserv: warning: current stop runlevel(s) (0 1 2 3 4 5 6) of script `cups-browsed' overrides LSB defaults (0 1 6)[/B]

---

### Post by RobGoss on 2017-03-28
Are you using **sudo** at the beginning of that command?

Is this a fresh installation of **16.04.2** you've installed?

---

### Post by venujee on 2017-03-29
No, this is not due to fresh installation.
I have been using 16.04 LTS for quite some time.
The problem started all of a sudden.
> **RobGoss said:**
> Are you using **sudo** at the beginning of that command?

Is this a fresh installation of **16.04.2** you've installed?

Yes, of course I am using sudo.

---

### Post by RobGoss on 2017-03-29
It may also be do to a kernel update I've been reading a few others having this same issue and choose to use a older kernel, in some cases it may fix the issues but I can't be 100% sure what's causing it

I ran that same command on one of my machines running 16.04 and it booted right up with out any problems

---

### Post by venujee on 2017-04-09
I tried kernel update.
I used boot repair.
But now I am in serious distress.
I am not able to start Ubuntu.
All I have is grub command line.
Not able to load kernel.
can somebody help ?

---

### Post by mörgæs on 2017-04-11
What happens if you boot into an older kernel?

---

### Post by venujee on 2017-04-13
No, it was not permitting anything other than grub command line.
Finally I could solve it without losing the data and without having to reformat.
The lessons learnt are as follows:
1. One should never go for Boot repair software. The app is not only dangerous but the chaps are quite unfriendly. After I landed into the deep trouble when I just could not boot, the guys replied at Boot repair replied to me saying that they only respond to people who pay them the contribution. They advised me to use paypal.
2. There was no need in my case to go for kernet update. The advice given above by RobGoss did not work for me.
3. There is a need to develop a tutorial on how to use grub command line for booting and for performing other system related tasks.
Thanks, everybody for their inputs.

---

### Post by mörgæs on 2017-04-14
> **venujee said:**
> 
Finally I could solve it without losing the data and without having to reformat.


Good, please post the solution for others to follow.

---

