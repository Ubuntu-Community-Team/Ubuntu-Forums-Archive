---
title: "Lucid-Plymouth.  What is it (and why am I getting an error message from it on boot?)"
date: 2010-01-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emarkay on 2010-01-18
Searched but didn't see any "soundbytes" on this.

The error doesn't seem to affect anything - next time I boot into recovery I'll transcribe it.

---

### Post by emarkay on 2010-01-18
Error text on boot: 
"Mountall: could not connect to Plymouth."

---

### Post by VMC on 2010-01-18
My guess is, it will go away once you install Plymouth.

---

### Post by emarkay on 2010-01-18
> **VMC said:**
> My guess is, it will go away once you install Plymouth.

Hmm, so it looks for something by default that it hasn't installed...
Wow, just like the early days of Windows...  :)

Oh and "[Plymouth]("http://www.phoronix.com/scan.php?page=search&q=Plymouth") is a Red Hat innovation that came around last year to provide a new, attractive boot graphical splash screen"
[http://www.phoronix.com/scan.php?page=news_item&px=Nzc5Mw](http://www.phoronix.com/scan.php?page=news_item&px=Nzc5Mw)

---

### Post by autocrosser on 2010-01-18
I get the error even though I have Plymouth installed---nvidia driver issue/problem in my case....

---

### Post by AllRadioisDead on 2010-01-18
I'm using an ati card and I get the same problem, then again I haven't managed to get display drivers working properly in lucid yet so that may be it.

---

### Post by DougieFresh4U on 2010-01-18
I am getting the same error with onboard intel i810 graphic.
Synaptic says Plymouth installed.

---

### Post by sgosnell on 2010-01-18
Remember, this is still an alpha, not yet even a beta, version.  Stuff happens.  And doesn't happen.

---

### Post by TerminX on 2010-01-18
Plymouth only works if its binary exists in your initrd, similar to something like v86d being required for uvesafb.

---

### Post by ranch hand on 2010-01-19
I have only had that problem on one of seven installs of 10.04 on the same drive.

I ran;
[sudo apt-get install --reinstall mountall
[/code]
and it went away.

I do have plymouth installed on all OS'.

Do not know if this is a general fix or just for my box.  Can't hurt to try it.

---

### Post by VMC on 2010-01-19
> **ranch hand said:**
> I have only had that problem on one of seven installs of 10.04 on the same drive.

I ran;
[sudo apt-get install --reinstall mountall
[/code]
and it went away.

I do have plymouth installed on all OS'.

Do not know if this is a general fix or just for my box.  Can't hurt to try it.

You mean you reinstalled mountall and the plymouth error went away?
BWT, I just noticed that plymouth is installed on my system as well. I guess its been installed by default. I surely didn't do it.


====================== slow loading ==============
Right now I'm having issues with Ubuntu Forums and Google Chrome.
Either slow or takes forever to load a page Only happens on Ubuntu Forums. I looked else where to report this but couldn't find a spot to ask about this.

---

### Post by ranch hand on 2010-01-19
Yes, I mean I reinstalled mountall and the messages went away and the plymouth logo started running as and when it should.

---

### Post by emarkay on 2010-01-19
> **ranch hand said:**
> I have only had that problem on one of seven installs of 10.04 on the same drive.
I ran;
[sudo apt-get install --reinstall mountall
[/code]
and it went away.

I got this:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 47.5kB of archives.
After this operation, 0B of additional disk space will be used.

Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main mountall 2.4 [47.5kB]

(Reading database ... 138066 files and directories currently installed.)
Preparing to replace mountall 2.4 (using .../archives/mountall_2.4_i386.deb) ...
Unpacking replacement mountall ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Setting up mountall (2.4) ..."

Will reboot and see...

Nope - 
"Plymouth-log main process (651) terminated with status 111."

---

### Post by ranch hand on 2010-01-19
Well that is a bummer.  That message has been around for a long time.  As long as you are booting just ignore it.  Updates will get it eventually.

---

