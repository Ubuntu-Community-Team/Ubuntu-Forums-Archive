---
title: "Install problems =("
date: 2006-05-23
forum: Installation &amp; Upgrades
---

### Post by BlackOcellaris on 2006-05-23
Trying to load either Ubuntu or Kubuntu onto a HP Pavilion laptop.  After I get to the

boot:

screen I press enter to do the base setup.  It goes through the motions and loads up some files, then the screen just goes blank.  The mouse doesnt appear, and the screen remains on, but there is nothing to look at/do.  Just a blank screen :X

Anyone have any ideas how to get around this?  I've tried to do it with Gentoo installed, nothing installed, etc.. with no luck at all.  I've downloaded fresh copies of the cd, burned them several times, with no luck ](*,) 

Gentoo installed on my computer fine (but I cant get the network setup).  openSUSE and MEPIS both failed to install at all.  Ubuntu (which was my first choice) looked nice and easy for myself but I cant get past the blank screen of death :X

Any help is much appreciated.  Thank you in advance.

---

### Post by r4ik on 2006-05-23
Try this one please,

desktop apci=off, hw-detect/start_pcmcia=false, vga=771

If X give's you trouble,

From the command-line type youre usrname and passwwrd hit enter.
Do a,

sudo dpkg-reconfigure xserver-xorg and hit enter,

just follow the defaults until you get to youre grapics card section select "nv" for Nvidia or "vesa" (ATI)

continue and finish with,

sudo /etc/init.d/gdm stop =>enter

sudo /etc/init.d/gdm start =>enter

This is what basicly seemed to help on this thread,

[http://www.ubuntuforums.org/showthread.php?t=171320](http://www.ubuntuforums.org/showthread.php?t=171320)


Hope it helps,

Good luck !

---

### Post by BlackOcellaris on 2006-05-24
Thanks for the help, I'm going to give it a shot a little later on :)

*excited*

*Edit:

everything works.  I took out the "server" part of the beginning since I was having trouble at the prompt post installation.  Everything works nice and dandy (except my wireless, but I'll figure that out later).  Thanks, I'm extremely happy to be running Ubuntu now and look forward to learning a bit more about linux :)

Cheers

---

### Post by Wrkcncanter on 2006-05-24
I'm very new to Ubuntu, and I have no idea where to type that in, so could you please spell out exactly how to solve the problem?

It's basically the same thing: I've finished installing and configuring (eveything execpt the network which I skipped). Now when I turn it on, it goes up to the brown splash screen where says "ubuntu" and has a progress bar and modules that are loading. The only thing that fails is the clock syncronization. After it finishes though, random horizontal white line segments flash on a black screen for about 2 seconds and then the little light on the monitor turns yellow instead of green, and you can't see anything. It makes a konga drum noise, and then stops. If I press enter it makes more drum noises. If I press the power button, it says "login username:" except when I try typing the password, only some of the keys work. Then it turns off.

Could someone give me a step by step thing to try?
Thanks

---

### Post by r4ik on 2006-05-25
[QUOTE=BlackOcellaris]Thanks for the help, I'm going to give it a shot a little later on :)

*excited*

*Edit:

everything works.  I took out the "server" part of the beginning since I was having trouble at the prompt post installation.  Everything works nice and dandy (except my wireless, but I'll figure that out later).  Thanks, I'm extremely happy to be running Ubuntu now and look forward to learning a bit more about linux :)

Cheers[/QUOTE]

Good to hear it worked thanks for the reply.

---

