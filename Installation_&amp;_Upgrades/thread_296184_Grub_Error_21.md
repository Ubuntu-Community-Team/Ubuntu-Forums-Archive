---
title: "Grub Error 21"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by meenfreem on 2006-11-09
I'm starting to think I really ffed up my Ubuntu install here... here comes my story :D

We have a Dell 1950 server. The tech guys there installed Ubuntu server for us and from that point on we've been having problems. 
Turned out that Ubuntu was installed, but on start-up GRUB would try to boot wrongly. Kept on getting error 21: disk does not exist. And after hitting enter (I'm on DRAC5 console, remote login from Dell) it would show me the GRUB menu and let me pick the Ubuntu 6.06 LTS from sda0. 
So I was trying to fix GRUB. And now on start up I only get this: GRUB loading, please wait; Error 21 ... and then nothing. 
What I did was in terminal, sudo grub-install /dev/sda and then rebooted ](*,) 

Now if I go into the Dell Boot Menu I get to pick from *normal. *virtual floppy * ide cd-rom * virtual cdrom * hard drive c: * embedded nic 1 mba

Not sure what to do next, besides reinstalling... if that would be the case, what is the best way to reinstall remotely, without cdrom just the internet. 

Thanks for any and all help!

---

### Post by Najand on 2006-11-09
Are you able to edit your grub menu?

---

### Post by meenfreem on 2006-11-09
not anymore... when the error 21 message comes, the system stalls (it seems anyways, nothing happens for minutes in any case). Before it gave me a different Error 21 message btw.

---

### Post by Najand on 2006-11-09
Hmm, can you see the menu or can you edit it using key "e", "c" or whatever, before getting the error?

---

### Post by meenfreem on 2006-11-09
no, I just get to see this:
GRUB loading stage 1,5
Grub lolading, please wait
Error 21

---

### Post by Najand on 2006-11-09
Hmm... Seems there is no way to restore it... Maybe some other people may help you configuring it correctly.

---

### Post by meenfreem on 2006-11-09
thanks for your time anyways... I fear that I have really bollocked it up this time...

---

### Post by Najand on 2006-11-09
Actualy if you are able to use the Virtual CD-ROM (I am not aware of how they works, better to check your documentations), you can use your cd-rom as a remote cd-rom to boot your system with it; can't you?

---

### Post by meenfreem on 2006-11-10
To be quite honest, I have no idea how to procede from here... or how to point a virtual CDrom to anywhere?! Any ideas on something that might work? (besides physically heading out there to stuff a cd in or forking out €90 for a reinstall by the same tech guys who ffed it up in the first place)

---

### Post by Sef on 2006-11-10
Read [Restoring GRUB]("http://doc.gwos.org/index.php/Restore_Grub").

---

### Post by meenfreem on 2006-11-10
problem is: it's remote :S

But I have a good mind in heading over to the server park and sitting down at the machine to fix... 

Thanks for the link in any case!

---

### Post by MianoSM on 2007-08-24
I'm experiencing the same issue at the moment - and so far have been very unsuccessful in correcting the GRUB Error.

One of the steps requests that you try to use Windows to FIXMBR, yet windows doesn't even see the hard disks at this point.

The Dell Server Assistant is not Ubuntu friendly.

A fiesty fawn install works perfectly - odd at best.

Tryign to do yet another 64 bit 6.06 install - and still getting an Error 21.

Super Grub Disk all over again.....

---

