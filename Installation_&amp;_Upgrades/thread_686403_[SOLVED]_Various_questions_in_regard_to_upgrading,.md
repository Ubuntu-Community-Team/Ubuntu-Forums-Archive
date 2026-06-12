---
title: "[SOLVED] Various questions in regard to upgrading, backup, home partition and synapti"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by the8thstar on 2008-02-03
Hello,

I have several questions to ask about backing up data, the /home partition and whether I should perform upgrades or clean installs. So here it goes...
[B]
1. Data backup[/B]

I have set Ubuntu 7.10 to have a separate /home partition. It has been recommended several times on the forums so I took the advice. This partition runs on the same disk as the rest of the filesystem and my Vista partition too. Just in case, is an incremental backup of /home a good option? Is it worth doing since we're talking about the same disk here (80Gb)? Should I get an external USB2.0 drive?

**2. Home partition**

My home partition contains work documents, and folders that set some of the aspect and behavior of Ubuntu (look and feel mostly). When I upgrade or perform a clean install, will these settings remain the same or will they be erased? How can I make sure I'm not going to zap my /home partition when I use a liveCD to perform a fresh install?

**3. Using synaptics or a "harvest" script**

Instead of backing up the data and the programs I have installed, I was wondering if there is a command on the CLI or a GUI app that could make a list for me and bundle it as a script if I need to reinstall everything. Ideally the list would contain all the info in the wget http: and/or apt-get form. It could be linked to synaptics. Is this doable?

**4. Fine tuning the system... can this be saved too?**

In order to make myself clear, I'll use a few examples. Let's say I want to set the usplash screen with a resolution of 1280x800 instead of the 1024x768, I want the processor to run "on demand" to save power, I want xorg.conf to recognize my s-video port and I want to use the "no-writeback" option on my ext3 partitions... Can these settings be saved? If so, how?

Thank you very much in advance. As always, I hope that my questions will answer other users' concerns too.

---

### Post by wwzulu on 2008-02-04
Yep, that's exactly what I want to know too :) . I have had several months of trying out many distros and when I stay on a distro I like to experiment with installing it several times. It is annoying, however that after each install I have to fine tune quite a few settings/ install favourite programs etc. Now if there's a way to keep all those within several upgrades/ install. That is important now that I seem to have found the most suitable distro which will be upgraded soon. 

Please help :confused:

---

### Post by zvacet on 2008-02-04
1. Yes,backing up home is good optionand if you can put it on external even better.
2.It will be safe,just during upgrade don´t format it.In home are all your setting so it will be big lost for you.

3. I will take **aptoncd** (it is in synaptic) because it is program to copy your var/cache/apt/archives and there are all you installed with apt-get or synaptic.Other solution is to type 

```
dpkg --get-selections > installed-software
```

That will create file in your home directory with list of all installed software.You can send it to yourself by e-mail if you think that is safe place.When it comes to reinstall you will put that file in comp and run

```
dpkg --set-selections < installed-software
``` 

and after that 

```
dselect
```

4. I don´t know.

---

### Post by the8thstar on 2008-02-05
Thank you both very much guys. I believe that covers my questions very well! :)

---

