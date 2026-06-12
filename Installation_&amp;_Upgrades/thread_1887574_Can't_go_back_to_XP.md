---
title: "Can't go back to XP?"
date: 2011-11-27
forum: Installation &amp; Upgrades
---

### Post by Mastiff37 on 2011-11-27
Okay, I'm a reasonably computer savvy guy, but now I'm just confused.  I gave Ubuntu a shot, then Mint, and now I want to go back to XP.  I insert the XP CD and the machine simply refuses to boot from it.  Did the linux installs actually change the machine at such a level that I can't boot to a windows CD anymore?  I have two XP disks laying around and neither of them work.  The machine happily boots to Ubuntu or Mint CDs.  Any advice here would be great, thanks.

---

### Post by surfer on 2011-11-27
are you sure the computer tries to boot from CD? that's a BIOS setting. a modern BIOS also lets you choose a one-time boot device.

---

### Post by Mastiff37 on 2011-11-27
Positive. It pings it for a second and then moves on - for the XP CD's.  It works for the Mint CD.

---

### Post by Hakunka-Matata on 2011-11-27
can we see a graphic of your partitioning scheme please?  
The output of this 
```
sudo fdisk -l && sudo sfdisk -luS
```would help also, please post output between **#code# tags**, it maintains the formattting of the stdio, easier to read.

---

### Post by darkod on 2011-11-27
Booting from CDs has absolutely nothing to do with the OS on the hdd. As you are aware yourself, it tries the CD before even looking at the hdd. Hell, you can boot with a cd without even having a hdd.

That being said, very strange. You say it does boot ubuntu and mint, so all looks fine with the boot options and the cd drive.
Any chance to try the XP CDs in another pc just for boot?

---

### Post by Hakunka-Matata on 2011-11-27
> **darkod said:**
> Booting from CDs has absolutely nothing to do with the OS on the hdd. As you are aware yourself, it tries the CD before even looking at the hdd. Hell, you can boot with a cd without even having a hdd.

That being said, very strange. You say it does boot ubuntu and mint, so all looks fine with the boot options and the cd drive.
Any chance to try the XP CDs in another pc just for boot?
hey, come on darkod, first off it's XP, ya know?  I agree everything you write with the exception of the first sentence, ..............

---

### Post by Mastiff37 on 2011-11-27
Okay, I stumbled on the answer while in the process of getting the partition info you asked for...

The Linux CD's boot automatically.  The XP CD says "press a key to boot from CD" and you have to do it within a small window of time.  I was trying to use my TV as a monitor, and I wasn't seeing the text for whatever reason (it doesn't start working for a while).  I switched to a regular monitor and was able to see the text and press a key in time.

Thanks for trying to help.

---

### Post by Hakunka-Matata on 2011-11-27
That's good to hear, it never hurts to 'poke' around a bit, just because the answer is often "something simple", yadda-yadda-blahblah


so where's the command line stuff I asked you to display, if you don't mind I'd like to see the drive, information.

---

### Post by Mastiff37 on 2011-11-27
Sorry, I already wiped everything and put XP on.  It was just weirdness with the monitor.  

I really wanted to go with Ubuntu, but it was having problems with the video and NVIDIA drivers I just couldn't figure out.  In all other ways the Ubuntu install was way easier than XP.  It took about 1/4 the time and the wireless adapter worked right out of the chute.  XP gave me all kinds of hell.

Thanks again.

---

### Post by Hakunka-Matata on 2011-11-27
> **Mastiff37 said:**
> Sorry, I already wiped everything and put XP on.  It was just weirdness with the monitor.  

I really wanted to go with Ubuntu, but it was having problems with the video and NVIDIA drivers I just couldn't figure out.  In all other ways the Ubuntu install was way easier than XP.  It took about 1/4 the time and the wireless adapter worked right out of the chute.  XP gave me all kinds of hell.

Thanks again.
Thanks for coming back with a reply.  

Sorry the vid drivers were such a hassle.

It is good and fun, the hear other people's opinions of how easy/hard ubuntu installed, and how much they did/didnot like ubuntu, and you caught the drift, with that in mind.

Have you considered dual booting and taking your time to get past the driver conundrum.  I resolved the vary same problem with a machine of mine when installing a GEForce 9500 PCIE card very recently.  That 'nouveau' appearance in error logs is familiar, on my machine I had to blacklist certain nouveau and install another, but it worked just jolly (of course) once I got the right driver in the right order in the right place, ...................................................

---

### Post by Mastiff37 on 2011-11-27
It sounds like there is an NVIDIA problem with just the latest Ubuntu release.  Maybe I'll wait and try again later.  I didn't give it that long really, my help thread sort of dried up so I decided to move on.  Overall I was really impressed with how easy Ubuntu was.  Everything but the TV-as-monitor worked right away.

---

