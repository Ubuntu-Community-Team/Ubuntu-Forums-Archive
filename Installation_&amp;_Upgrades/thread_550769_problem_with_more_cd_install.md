---
title: "problem with more cd install"
date: 2007-09-14
forum: Installation &amp; Upgrades
---

### Post by m4rku5 on 2007-09-14
Please i have problem with installation games with more than 1 cd, it writes: An application is preventing the volume 'My Disc' from being ejected. Please help me some1, i'm new user of Ubuntu, real amateur.

---

### Post by Pumalite on 2007-09-14
Explain better what you are trying to do.

---

### Post by raijinsetsu on 2007-09-14
Are you manually mounting the CDs? Gnome (and KDE) have a media automounter. If it is telling you the device is busy, you can try several things:
First, right click on the volume (on your desktop) and click "unmount" or "force unmount", see if that works.
Secondly, rip the CDs to your disk, and then use:
"sudo mount -o loop -t iso9660 /home/UserName/SomeCDName.iso /media/cdrom"
If you don't umount it, you can simply run the same command with the ISO for the second disk. Then, when you're all done, "sudo unmount /media/cdrom" until there are no more mounts on cdrom. Capiche?

---

### Post by m4rku5 on 2007-09-17
Thank you, image works well. But I still have a lot of problems, when I Install same game and start it, there's not any sounds. Some games like San Andreas doesn't work without audio and San Andreas writes: No audio card installed. Don't you know something about that?

---

### Post by Pumalite on 2007-09-17
Try Multimedia & Video

---

### Post by raijinsetsu on 2007-09-17
> **m4rku5 said:**
> Thank you, image works good. But I still have a lot of problems, when I Install same game and start it, there's not any sounds. Some games like San Andreas doesn't work without audio a and San Andreas writes: No audio card installed. Don't you know something about that?

Are you using wine? Check out the audio tab in the Wine configuration GUI. See if it's using ALSA, eSound, or OSS. Try using ALSA; if that doesn't work, try OSS. You probably don't have eSound installed... :)

---

### Post by m4rku5 on 2007-09-17
> **raijinsetsu said:**
> Are you using wine? Check out the audio tab in the Wine configuration GUI. See if it's using ALSA, eSound, or OSS. Try using ALSA; if that doesn't work, try OSS. You probably don't have eSound installed... :)

Thanx again, I tell you again I'm absolute amateur with Linux. But I've very big problem. When the game load new game or something like that, it fall down (I try everything with NFS: U2, with them don't work keyboard, everything is different with Linux, I didn't want Linux, but there was no choice, my hdd refuses XP, so please show me that Linux is genius)

---

### Post by raijinsetsu on 2007-09-17
According to [this link]("http://appdb.winehq.org/appview.php?iVersionId=2846") from WineHQ, NFS:U2 doesn't work.
You could try Cedega. [This link]("http://cedegawiki.sweetleafstudios.com/wiki/Need_For_Speed_Underground_2") is about NFS:U2 compatibility in Cedega.

You have to realize, running Windows programs in Linux is never guaranteed to work. Sometimes, it takes a lot of work to get things going correctly.

---

### Post by m4rku5 on 2007-09-19
Cedega wants some user name and serial, where can I take it, or where can I download crack. Can you help me?

---

### Post by Pumalite on 2007-09-19
To use a crack is illegal. We don't condone that here.

---

### Post by m4rku5 on 2007-09-19
Fine my next problem is: My second disc is SATA, when I try to copy something there. System writes: You do not have permissions to write to this folder. I tried to change read-only option in preferences, but it writes: Sorry, couldn't change the permissions of "149,0 GB Volume: disk". I hope you will know how I can change it.

---

### Post by Pumalite on 2007-09-19
You are probably trying to copy among two different formats (Ubuntu to Windows or Windows to Ubuntu). Be more explicit in your problem, State formats and OS's

---

### Post by m4rku5 on 2007-09-19
I installed San Andreas with Wine, it worked only with no-full screen - it's very intersting, when I had full screen, game didn't work or keyboard dind't work. Game was really unstable. Please, you surely have some experience with Linux gaming, tell me which of these games 100% work on Ubuntu with wine (GTA: 3, GTA: VC, GTA: SA :), NFS: Carbon, Test drive Unlimited, Diablo 2) Games are like drugs.

---

### Post by Pumalite on 2007-09-19
Sorry. I'm not a gamer. Someone will chime in.

---

