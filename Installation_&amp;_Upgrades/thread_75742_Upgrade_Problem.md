---
title: "Upgrade Problem"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by SeanMC on 2005-10-14
Hi All,

I have run the upgrade routine from Hoary to Breezy last night using apt-get dist-upgrade. All appeared to go well.

I re-booted the pc when the upgrade had completed, it boots fine but comes to a login prompt rather than to a gui login.

Everything appears to be there but if I type startx or sudo startx it fails, any ideas how to fix this behaviour or should I do a clean install?

I don't really want to do a clean install at this stage.

Thanks in advance for any help.

Sean

I should mention I am running Kubuntu.

---

### Post by invalid on 2005-10-14
If you post the error log from X, it might help to debug the problem.

For now, I can tell you that you can reconfigure Xorg with the following command:

sudo dpkg-reconfigure xserver-xorg

This may help you, or may not depending on the source of your problem.

Cheers,
Cb

---

### Post by kiwibird on 2005-10-14
I also ended up in a terminal; trying reconfigure gives me "xserver-xorg is broken or not fully installed", after a bunch of messages about missing locales (but seeing as it falls back on standard locale ("C"), it seems that shouldn't matter?)

---

### Post by randlieb on 2005-10-14
[QUOTE=kiwibird]I also ended up in a terminal; trying reconfigure gives me "xserver-xorg is broken or not fully installed", after a bunch of messages about missing locales (but seeing as it falls back on standard locale ("C"), it seems that shouldn't matter?)[/QUOTE]

ditto

how to install x?

---

### Post by shenki on 2005-10-14
at a guess;

sudo apt-get install xserver-xorg

:D

---

### Post by wgscott on 2005-10-14
The problem arises when the video card driver or security software that interacts with it is installed or upgraded.  Apparently this is considered a feature.  

The problem is it checks the md5sum (fingerprint) of a file on startup, and if it is changed, X doesn't start.  You can still start it from your own account, but it won't behave properly.  The fix is simple enough.


I issued the following commands prior to reboot (I have an nvidia graphics card):

```

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo nvidia-glx-config enable

```

It prevented it from happening the third time around.

---

### Post by randlieb on 2005-10-14
> I have run the upgrade routine from Hoary to Breezy last night using apt-get dist-upgrade. All appeared to go well. I re-booted the pc when the upgrade had completed, it boots fine but comes to a login prompt rather than to a gui login. Everything appears to be there but if I type startx or sudo startx it fails, any ideas how to fix this behaviour or should I do a clean install? 

same scenario. same problem (though running UBUNTU). 

after trying startx i get: 
connection refused (errno 111): unable to connect to Xserver 
no such process (errno 3): server error 
error in locking authority file /home/"username"/.Xauthority 

have also tried the following with no luck: 

sudo apt-get install xserver-xorg 

sudo apt-get install --reinstall xserver-xorg 

sudo dpkg-reconfigure xserver-xorg 

any ideas anybody??

---

### Post by eliteh4xx0r on 2005-10-15
I'm not sure that xserver is the problem. My upgrade went badly as well.  I can start gdm or kdm and get a login window, but i cannot get to a desktop environment.  This has confounded me to no end.

The main problem is that debtags will not configure properly. From what I understand, kubuntu-desktop and other packages depend on this.

Keep in mind that this is speculation.

---

### Post by SeanMC on 2005-10-15
I fixed my problem by typing  sudo apt-get -f install 

Then I realised I had had the forethought to put the home dir in a seperate partition so installed Breezy from scratch.

---

### Post by bkasterm on 2005-10-15
I had the same problem.  But following the suggestions I got when starting X failed (and the suggestions when there were problems with the suggestions) I got it to work.  One useful tidbit in doing this, if you are in a terminal and want t see things that have scrolled of the monitor <shift>+<pageup> and <shift>+<pagedown> allow you to see it anyway.

Best,
Bart

I now have a good running system.  Only problem is that most things are now getting redone.  I used the apt-get procedure described on the update notes page (since there was no synaptic procedure up at the time I started).  After finishing with it, fixing X to get it running, I started synaptic.  It suggested very many updates, this is now running (and looks like it will take a while).

After all is (re)done I'll make a post with my experiences.

---

### Post by agm642 on 2005-10-15
[QUOTE=randlieb]
after trying startx i get: 
connection refused (errno 111): unable to connect to Xserver 
no such process (errno 3): server error 
error in locking authority file /home/"username"/.Xauthority 
[/QUOTE]

I used to get this message too. Until I tried, as some document suggested, to run base-config. It completed successfully, but after that, whenever I tried startx, the system halted. It was running, but the screen was blank and it did nothing with Ctrl+Alt+Backspace. I have tried both "dpkg-reconfigure xserver-xorg" and fglrxconfig, but it stays the same. In the logs, I only see something about dri not finding any cards. :???: :confused:

---

### Post by struan on 2008-05-16
I've just switched from slamd/fluxbox so all these config tools are new for me. I also had the same problem with x-config. I eventually just went to the nvidia site and got the .run file. I started without kdm and ran the .run file.  No problem.

---

