---
title: "A humonogus problem when upgrading to Hardy."
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by emshains on 2008-04-26
I was installing Hardy, I had gone up to the stage where the installer installed/configured new software. It made some pop-ups to configure the new soft's, and then samba poped up and asked something, I dont remeber the question, but the answer was set to stay with the config thats present now, but I picked the one that configures a new one depending on the "situation". I clicked "Next" and it hung up, after 5 seconds the windows disapeared and the installation stopped at the middle.
     
Now I dont know what to do, its half installed but the computer is idle, it just sits on 5% of resources. I am afraid to do a reboot, I dont want to screw up. PLEASE HELP!!!

P.S. Check the s-shot.



Now after 30 minutes I will try to do a reboot and see if that changes anything. I will rport my actions later.

---

### Post by pmorton on 2008-04-26
> **emshains said:**
>  samba poped up and asked something, I dont remeber the question, but the answer was set to stay with the config thats present now, but I picked the one that configures a new one depending on the "situation".

Not as humonogus as you think. The worst that can happen is that you've overwritten your /etc/samba/smb.config file, so that if you were sharing folders/printers with windows machines on a network, you might need to set up your Samba shares again. If you weren't, once you're all settled, you should 'sudo apt-get remove samba' as you don't need it. There's probably  a backup file made  for you to revert to in any case, if you do need your Samba setup.  Just carry on installing.

---

### Post by emshains on 2008-04-26
> **pmorton said:**
> Not as humonogus as you think. The worst that can happen is that you've overwritten your /etc/samba/smb.config file, so that if you were sharing folders/printers with windows machines on a network, you might need to set up your Samba shares again. If you weren't, once you're all settled, you should 'sudo apt-get remove samba' as you don't need it. There's probably  a backup file made  for you to revert to in any case, if you do need your Samba setup.  Just carry on installing.

Not as humoungous you say ? 

I rebooted and it said it cant load the nvidia drivers for my 7300gt and it couldnt load my safe login, that has no desktop effects enabled. It just stays with the orangy brownish color all over the screen and it only responds to ctrl+alt+bckspace. After that I booted into recovery mode and ran> sudo install nvidia-control-center after that it said it couldnt do it automaticly and adviced me to > dpkg --configure -a  after running that the first time it installed all the stuff including samba like it tried to do when I was upgrading to Hardy automaticly through the update manager. I rebooted and still no luck. Again with the recovery mode and still apt-get cant do anything and advices me to run the > dpkg --configure -a  I run the command again, it runs through a list of programs and from what I can see is that it lacks some dependencies but I cant do anything about it. 



From X I cant log on through foolproof or fail-safe session of gnome ( dont know how to translate the term so I made it straight forward).

Now I can see two kernel versions through grub: Ubuntu 8.04, kernel 2.6.24-16-generic and Ubuntu 8.04., kernel 2.6.24-16-generic. 




I am now posting from another machine and that is pretty anoying right now.

---

### Post by emshains on 2008-04-26
Now after scooping the net, I cant find any way of succseeding in fixing my problem/s. I am thinking of a fresh install, but I want to keep my wine directory safe and reusable. 

I think my goal now is changed from "fix the damn problem" to "get it working as I would a day ago". I am really annoyed because of the damn instalation problems. I had no problem going from feisty to gutsy, it was ,hmmmm, like doing an every day task. Just run wait and use. 

I am going to ditch Ubuntu Hardy Heron (8.04), but I am not going to ditch ubuntu in general.

---

### Post by daengbo on 2008-04-26
If your computer was configuring updates and died in the middle, all dependencies should have been downloaded before that stage. Dpkg is returning an error somewhere and not finishing the job.

Try
> apt-get install -f
It will probably return an error and ask you to run dpkg
> dpkg --configure -a|less
and note any errors. Press Q to exit.

Upgrade problems happen, especially when packages are installed outside of the normal repositories. It's no one's fault, Hardy is no different than any other Ubuntu release on this matter.

Stay calm. Package manager problems suck, but they can be remedied.

---

### Post by emshains on 2008-04-26
Umm, the > apt-get install -f doesnt do anything unnusual, it just says that yo must run the "dpkg -- configure -a" again.
I will "copy" by hand, what the 2nd command spits out: >  dpkg: dependency problems prevent configuration of eog:
eog depends on libgnome2-0 (.+ 2.17.3); however:
Package libgnome2-0 is not configured yet.
dpkg: error procesing eog (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-system-monitor:
gnome system monitor depends on libgnomevfs2-0(.1:2.17.90);however
Package libgnomevfs2-0 is not configured yet And so on and so on and so on till
>  dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion '!queuelen' failed. 

Thats how it ends.

P.S.Only at the end I realize that I could press S and then post the log through slax.


He he he, only got 1 page of useless (flawless) text, that is no good for you. (its about how it succseded in installing/confurating java.

---

### Post by daengbo on 2008-04-26
OK, so your problem is libgnome2-0. We'll need to see the error message for it.

> dpkg -i /var/cache/apt/archives/libgnome2-0-YOURVERSIONHERE.deb
That will spit out the error. We can go from there.

---

### Post by pmorton on 2008-04-29
> Not as humoungous you say ? I rebooted and it said it cant load the nvidia drivers for my 7300g

Ah.. you didn't mention NVidia in your original post. You've joined a big club. See
[http://ubuntuforums.org/showthread.php?t=766515](http://ubuntuforums.org/showthread.php?t=766515).

---

