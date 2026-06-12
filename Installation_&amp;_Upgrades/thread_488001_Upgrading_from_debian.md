---
title: "Upgrading from debian"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by srikantmarakani on 2007-06-29
Sorry in advance if this has been adressed before but I would like to know if there is any guide to a fast upgrade from debian amd64 testing? I just installed Ubuntu on my laptop and was quite impressed with the painless installation (couldn't get wireless to work but the wireless card is still not supported by linux) which is the easiest installation I have ever had for -any- OS or linux distribution, having tried almost all the other big distros like redhat, mandrake, debian, gentoo, suse etc. etc. over the last 12 years. I have some cool new hardware :D which includes a gigabyte mb with the amd 690g/sb600 chipset which requires 2.6.20 and rather than compile a new kernel which is not yet a debian package, I am considering the switch to ubuntu. The main question I have is whether there is any particularly easy way to switch from debian since it uses deb too or do I have to do it from scratch? I would like to skip reinstalling all my optional packages if at all possible.

TIA for your help.

---

### Post by bapoumba on 2007-07-01
I would do a fresh install. Upgrading or dist-upgrading just changing the sources.list would most probably not work.

---

### Post by kerry_s on 2007-07-01
> **srikantmarakani said:**
> Sorry in advance if this has been adressed before but I would like to know if there is any guide to a fast upgrade from debian amd64 testing? I just installed Ubuntu on my laptop and was quite impressed with the painless installation (couldn't get wireless to work but the wireless card is still not supported by linux) which is the easiest installation I have ever had for -any- OS or linux distribution, having tried almost all the other big distros like redhat, mandrake, debian, gentoo, suse etc. etc. over the last 12 years. I have some cool new hardware :D which includes a gigabyte mb with the amd 690g/sb600 chipset which requires 2.6.20 and rather than compile a new kernel which is not yet a debian package, I am considering the switch to ubuntu. The main question I have is whether there is any particularly easy way to switch from debian since it uses deb too or do I have to do it from scratch? I would like to skip reinstalling all my optional packages if at all possible.

TIA for your help.

Okay, if i got this right. your using debian testing and you want to switch to another debian based distro so you can get a better kernel. you know distros a made differently right?

anyways there's a easier solution to your problem. ubuntu just takes applications from debian unstable and screws them all up to work in ubuntu.

so all you have to do is simply upgrade your install from testing to lenny/unstable and you will have access to a 2.6.21.*.* that is currently in unstable.
make sure you have theses 2 line in /etc/apt/sources.list

deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) lenny main contrib non-free 

deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) sid main contrib non-free  

then open a terminal and> su & apt-get dist-upgrade
then
reboot
done

i don't use that kernel because the older one works better for my old laptop,but here's a pic->

---

### Post by srikantmarakani on 2007-07-02
Thanks. I was aware of that option but I also liked the overall smoothness of the ubuntu distro better and the final solution was actually quite obvious in retrospect - I just saved the output of dpkg -l on the debian system and used a one line script to apt-get install the first column of that file after the basic ubuntu install (of course, minor differences made it a bit more involved, but really rather painless). 

I was thinking of an apt-get dist-upgrade first but as you and bapoumba rightly point out, that might not have worked at all.

I suppose switching to ubuntu continues my progression of distros as I first switched to debian from redhat to escape from rpm dependency hell which got so absurd on my system that I ended up having a package depend upon itself! Debian's debs were just so much better maintained even though the initial config was painful atleast in the earlier releases. Ubuntu has now largely gotten rid of that problem as well.

As an aside, I actually used to enjoy taking the trouble to configure and compile everything (and this was before gentoo) for added performance a decade ago on my linux boxes but given the speed of modern hardware, and I suppose increased age :rolleyes:, I no longer enjoy it all that much and just want stuff to work. I still use a gentoo box for my mythtv box but will probably change that to ubuntu as well after having to reconfigure and compile the kernel several times over the course of a long and frustrating night when trying to get an air2pc tv tuner to work.

---

