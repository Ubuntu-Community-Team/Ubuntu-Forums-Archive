---
title: "How to boot with non-responding keyboard at the password prompt"
date: 2020-07-03
forum: Installation &amp; Upgrades
---

### Post by ffrr on 2020-07-03
Hi all,
      
A package management function (autoremove) corrupted the bootstrap process of my ubuntu (18.04 LTS). Starting up the next day I got stuck at the login prompt, because the keyboard didn't respond. No password entered, no access. The recovery mode didn't help. "Repair broken packages" failed to read a bunch of "http"s. "Drop to root shell prompt" worked. The keyboard worked (temporarily alas) "update" and "upgrade" fared no better than "Repair...". I believe that with a few appropriate shell commands, the problem could be diagnosed and cured. After all, before GUIs, everything was done with shell commands. Hoping to receive advice on working from the recovery root-shell prompt, I have been directed by dedicated helpers on this forum to an alternative approach: install and start a second system, mount the inaccessible file system and chroot it. Done, this is what "apt-get update" produces:

Err:1 [http://ch.archive.ubuntu.com/ubuntu](http://ch.archive.ubuntu.com/ubuntu) bionic InRelease
  Temporary failure resolving 'ch.archive.ubuntu.com'
Err:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
  Temporary failure resolving 'security.ubuntu.com'
Err:3 [https://packagecloud.io/AtomEditor/atom/any](https://packagecloud.io/AtomEditor/atom/any) any InRelease
  Temporary failure resolving 'packagecloud.io'
Err:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease
  Temporary failure resolving 'archive.canonical.com'
Err:5 [http://ppa.launchpad.net/jonathonf/vim/ubuntu](http://ppa.launchpad.net/jonathonf/vim/ubuntu) bionic InRelease
  Temporary failure resolving 'ppa.launchpad.net'
Err:6 [http://ch.archive.ubuntu.com/ubuntu](http://ch.archive.ubuntu.com/ubuntu) bionic-updates InRelease
  Temporary failure resolving 'ch.archive.ubuntu.com'
Err:7 [http://ch.archive.ubuntu.com/ubuntu](http://ch.archive.ubuntu.com/ubuntu) bionic-backports InRelease
  Temporary failure resolving 'ch.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/dists/bionic/InRelease](http://ch.archive.ubuntu.com/ubuntu/dists/bionic/InRelease)  Temporary failure resolving 'ch.archive.ubuntu.com'
W: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease](http://ch.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease)  Temporary failure resolving 'ch.archive.ubuntu.com'
W: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease](http://ch.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease)  Temporary failure resolving 'ch.archive.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease](http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease)  Temporary failure resolving 'security.ubuntu.com'
W: Failed to fetch [https://packagecloud.io/AtomEditor/atom/any/dists/any/InRelease](https://packagecloud.io/AtomEditor/atom/any/dists/any/InRelease)  Temporary failure resolving 'packagecloud.io'
W: Failed to fetch [http://ppa.launchpad.net/jonathonf/vim/ubuntu/dists/bionic/InRelease](http://ppa.launchpad.net/jonathonf/vim/ubuntu/dists/bionic/InRelease)  Temporary failure resolving 'ppa.launchpad.net'
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/bionic/InRelease](http://archive.canonical.com/ubuntu/dists/bionic/InRelease)  Temporary failure resolving 'archive.canonical.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.

Despite working in a fully functional environment with Firefox and Thunderbird up and running. An experimental download with "wget" of the first "http" in the above list succeeds. 

I now see two solution paths:

1. Diagnose and cure the malfunction at boot time in the recovery-mode root-shell terminal, so that, resuming the boot, the keyboard works by the time the password prompt appears: what diagnostic and remedial commands?

2. Making "apt-get" work on the currently unbootable file system chrooted in the functioning parallel system: what diagnostic and remedial package management commands?

I will gratefully receive any advice, comments, suggestions.

Frederic

---

### Post by grahammechanical on 2020-07-03
I do not know if you are aware of this but Recovery mode>Root Shell prompt does not have internet access. If we want to update/upgrade or install packages we must first select Network at the Recovery Mode menu and then select Root shell prompt.

The keyboard should work with the Grub boot menu and in recovery mode because the machine is using basic drivers that are part of the motherboard BIOS/UEFI settings utility. The mouse will not work.

Regards

---

### Post by ffrr on 2020-07-03
grahammechanical - Confirming your info. Thanks a lot. I'll act on it tomorrow. At 10:30 pm I have to call it a day.

---

### Post by ffrr on 2020-07-04
New day, sleeves rolled up, played around some more with the grub menu and the recovery menu. Good idea to select "Enable networking" before going to the "Root shell prompt". Once there, "apt-get update" still fails the same way, though. So it's not the network. In fact, apt-get update" also fails the same way, if called from the functional side-by-side system, where Firefox is open and where I can fetch with "wget" the files "apt-get update" can't. Which fact suggest the idea that I could "wget" them all--they're only six or seven--and put them where "apt-get" would find them, provided this is how it works and I find out where to put the "wget"ted files. Anyway, some manual package repair seems indicated, with dpkg, I guess. Tips more than welcome.
 
Back to the first strategy: booting via "recovery mode, root shell prompt": I would try to identify irregularities with the keyboard driver. If it is a (missing) process, what is its name, how would I start it? "fork" or "service"? I suspect that the solution is trivial for someone familiar with the inner workings.

Tips more than welcome, about solutions or literature

Frederic

---

### Post by webaake on 2020-07-04
A mystery indeed! You might want to take a look at the file '/etc/apt/sources.list' Here is guide for the formatting of that file: [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

While there you could comment out the non essential repos with a '#' sign. Keep the original Ubuntu repos active while error searching.

You could also take a look in apt's log file /var/log/apt/history.log for further info. 

I've never seen that "Temporarily failure to resolve.." but it might even be your providers DNS. Therefore you could try to change the repos to another country. I see you try to contact repos in 'ch' - try US instead like "http://us.archive.ubuntu.com......". You just have to change the ch to us.


Here's an old thread with your exact problem: [https://askubuntu.com/questions/91543/apt-get-update-fails-to-fetch-files-temporary-failure-resolving-error](https://askubuntu.com/questions/91543/apt-get-update-fails-to-fetch-files-temporary-failure-resolving-error)

It seems interesting and might be applicable. Good Luck!

PS Don't forget to 'apt update' after editing sources.list. And, you could have more repos defined in the directory /etc/apt/sources.list.d/

---

### Post by tea for one on 2020-07-04
In order to select the Recovery option in the grub screen, your keyboard was working?

Next time you try to log in, when you reach the password prompt , can you activate the **on-screen keyboard** (assuming your mouse/pointer is working)

Hopefully, you can then use your mouse to complete your password.

---

### Post by ffrr on 2020-07-06
tea for one, webaake! Thank you both. I promptly answered your posts two days ago. Today I don't see my asnwer. Must have not been sent. So I try again.

tea for one:
The keyboard works at the "grub" menu and at the "recovery" menu. At the login it doesn't work, regardless of what I do before that in the recovery menu. The mouse is not in effect. So no on-screen keyboard. (I wasn't aware of the feature. Good to know.)

webaake:
1. I take note of the repository lists in "/etc/apt".
2. I take note of "/var/log/apt/history.log". It is empty. I also find "/var/log/boot.log", a list of 500 starting actions. 
3. The fact that I operate from a fully functional OS (18.04), failing to "update", "upgrade" the "mounted" and "chrooted" file system which currently is unbootable, while having an operational internet connection and being perfectly able to "wget" the repositories out of reach for "apt-get", rather lets providers off the hook.
4. I shall concentrate on your reference "Here's an old thread with your exact problem: https://askubuntu.com/questions/9154...esolving-error". It strikes me as the most relevant. I just discover that Google finds a whole bunch of similar stories.

Frederic

---

### Post by ffrr on 2020-07-08
After three weeks of fiddling with "update" and "upgrade" to no avail, I decided to shift my focus to keyboard drivers. Google obliging I came upon this:

apt-get  install xserver-xorg-input-all

Run at the recovery root-shell prompt, shut down, restarted and at the password prompt the keyboard worked! Why I couldn't say, but so what? By the way I took notice of a few concurring remarks saying that upgrades from one LTS to the next would cause problems most of the time.

Thanking again all participants I close this thread.

Frederic

---

### Post by uninvolved on 2020-07-08
> **ffrr said:**
> Why I couldn't say, but so what?

The other day, to help someone's confidence level, I remarked that we'd all lost data before and that it was a chance to learn something new, like good backup practices.

Today, I'm not sure it's a confidence booster - but I'm pretty sure we've all also somehow "fixed" our systems without knowing exactly how or why it was fixed. More than once has the 'poke and hope' method worked. Fortunately, that's seldom an issue these days, but we've all been there! (Or at least I have, but I'm betting quite a few of us have been there.)

---

