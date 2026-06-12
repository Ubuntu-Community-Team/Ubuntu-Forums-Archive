---
title: "Broken package refuses to be replaced/upgraded"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by mrund on 2008-11-14
Right before Ibex was launched, my Hardy installation developed a spontaneous glitch: the gnome-applets package crapped out and the machine started to act erratically. Upgrading to Ibex didn't fix the problem: the upgrade killed the machine entirely.

After Caljohnsmith helped me resurrect the thing, it turned out that I had upgraded from a crippled Hardy to an equally crippled Ibex. The gnome-applets package is still broken and Synaptic appears unable to overwrite it with a fresh copy. I get the error message:

E: /var/cache/apt/archives/gnome-applets_2.24.1-0ubuntu1_i386.deb: could not read status for "./usr/lib/gnome-applets/charpick_applet2" (which was what I was going to install)

Removing this package (later to reinstall it) would take another package with it: ubuntu-desktop. I don't quite know what that is, but I know that without a working GUI, I'd be completely unable to use a linux system. So I haven't tried the extermination route.

What gives? Any suggestions?

---

### Post by inobe on 2008-11-14
i don't know if this will help.

have you tried fixing the broken packages with synaptic ?

---

### Post by mrund on 2008-11-14
You mean "reinstallation"? Greyed out in the menu. Not available. I tried "upgrade", didn't work.

---

### Post by inobe on 2008-11-14
open synaptic, click edit> fix broken packages ..

---

### Post by mrund on 2008-11-14
Ah, that was more convenient! But sadly it didn't work. Same error message. :(

---

### Post by inobe on 2008-11-14
have you tried updating all packages ?

a link explaining synaptic

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by mrund on 2008-11-15
That action isn't available before you've repaired all broken packages...

---

### Post by Kevbert on 2008-11-15
Have you tried the following in terminal ?
```
sudo apt-get install -f
sudo dpkg --configure -a
```
These commands will repair a damaged package and repair an interrupted install.

---

### Post by mrund on 2008-11-15
Same error message. Sorry that some of the following is in Swedish:

martin@martin-laptop:~$ sudo apt-get install -f
[sudo] password for martin: 
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
Korrigerar beroenden.... Färdig
Följande paket har installerats automatiskt och är inte längre nödvändiga:
  libopenal1 ispell ibritish libmtp7 libopenal0a libavutil1d python-pexpect
  libdc1394-13 python-twisted-web libxmmsclient4 python-pycurl libopenexr2ldbl
  libdns32 libdns35 libcamel1.2-11 libpostproc1d libtotem-plparser10
  libgtkhtml3.16-cil libsmbios1 libisccc30 libavformat1d
  linux-restricted-modules-2.6.17-10-generic linux-image-2.6.17-10-generic
  libalut0 dhcdbd libhunspell-1.1-0 liblwres30 bluez-audio libpoppler2
  libbind9-30 libedataserver1.2-9 libisccfg30 libavcodec1d libgucharmap6
  python-smartpm linux-restricted-modules-2.6.22-14-generic libisc32 libisc35
  iamerican linux-headers-2.6.24-16-generic linux-headers-2.6.24-16 libnss3-0d
  libxmmsclient-glib1 libltdl3 libpoppler-glib2 o3read libntfs-3g23
Använd "apt-get autoremove" för att ta bort dem.
Följande ytterligare paket kommer att installeras:
  gnome-applets
Följande paket kommer att uppgraderas:
  gnome-applets
1 uppgraderade, 0 nyinstallerade, 0 att ta bort och 19 ej uppgraderade.
Behöver hämta 0B/187kB arkiv.
Efter denna opeation kommer ytterligare 57,3kB utrymme användas på disken.
Vill du fortsätta [J/n]? 
Förkonfigurerar paket ...
(Läser databasen ... 215153 filer och kataloger installerade.)
Förbereder att ersätta gnome-applets 2.22.2-0ubuntu2 (med .../gnome-applets_2.24.1-0ubuntu1_i386.deb) ...
Packar upp ersättande gnome-applets ...
dpkg: fel vid hantering av /var/cache/apt/archives/gnome-applets_2.24.1-0ubuntu1_i386.deb (--unpack):
 kunde inte läsa status för "./usr/lib/gnome-applets/charpick_applet2" (vilket var vad jag just skulle installera): Stale NFS file handle
Hanterar utlösare för man-db ...
Fel uppstod vid hantering:
 /var/cache/apt/archives/gnome-applets_2.24.1-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
martin@martin-laptop:~$ sudo dpkg --configure -a
martin@martin-laptop:~$

---

### Post by mrund on 2008-11-15
Could this be due to some problem with the hard drive's organisation that just happens to touch upon the file in question? How do I check the disk's integrity?

---

### Post by Kevbert on 2008-11-16
The answer is [[COLOR="Red"]here[/COLOR]]("https://answers.launchpad.net/ubuntu/+source/dpkg/+question/40321"). First you need to delete the cache file /var/cache/apt/pkgcache.bin as it has been corrupted.

---

### Post by mrund on 2008-11-16
Sorry, I don't quite understand how to apply what they recommend there to my own situation. I did the following:

rm /var/cache/apt/pkgcache.bin

and

echo -en '\n' | sudo tee -a /var/cache/apt/pkgcache.bin

But the problem remained unchanged. Perhaps I applied the latter magic words to the wrong file?

---

### Post by Kevbert on 2008-11-16
> **Kevbert said:**
> Have you tried the following in terminal ?
```
sudo apt-get install -f
sudo dpkg --configure -a
```
These commands will repair a damaged package and repair an interrupted install.

It looks like you've removed the correct file. I think you need to do the above again...

---

### Post by mrund on 2008-11-16
I made very sure that pkgcache.bin was obliterated, then ran those two commands and got the same error message. :(

---

### Post by mrund on 2008-11-18
Any further ideas? I have this little red "no passage" sign sitting top right on my menu bar now, and I can't update my system as long as there's a broken package in it. Also, I have no mixer applet and no trash can.

---

### Post by tqzxzjhu on 2008-11-18
[&#27927;&#25163;&#27744;&#30095;&#36890;](http://classad.dahangzhou.com/223685.html)[&#28020;&#32568;&#30095;&#36890;](http://classad.dahangzhou.com/223685.html)[&#38452;&#27807;&#30095;&#36890;](http://classad.dahangzhou.com/223685.html)[&#19978;&#22478;&#21306;&#31649;&#36947;&#30095;&#36890;](http://classad.dahangzhou.com/223685.html)[&#19979;&#22478;&#21306;&#31649;&#36947;&#30095;&#36890;](http://classad.dahangzhou.com/223685.html)

---

### Post by mrund on 2008-11-22
Amazing! Turns out I seem to have been right. I asked,

"Could this be due to some problem with the hard drive's organisation that just happens to touch upon the file in question? How do I check the disk's integrity?"

Just now when I booted the machine up, it went into the periodical "scan disk for structural errors" routine and immediately found loads of errors. It dropped me to the prompt and had me run fsck by hand for some reason. And after I had accepted (by hand) tens of fsck's suggestions for how the disk might be repaired, and then turned off the machine, Ibex booted cleanly and I ran Synaptic without a hitch. The broken package is now repaired.

---

### Post by mrund on 2008-11-22
Err... It sort of fixed itself. After installing the latest upgrades, the machine spontaneously decided to *write-protect the hard drive*. I'm not kidding. What do I do now?

---

### Post by kostkon on 2008-11-22
> **mrund said:**
> Err... It sort of fixed itself. After installing the latest upgrades, the machine spontaneously decided to *write-protect the hard drive*. I'm not kidding. What do I do now?
What do you mean? What happens, please describe.

---

### Post by mrund on 2008-11-22
Firefox and Thunderbird crash as soon as they try to write to the disk. They just disappear instantly at a key press. When I try to delete a file I've got sitting on my desktop, I get a message to the effect that "I can't put that file into the trash can, because the drive is write-protected. OK if I just delete it irrevocably?"

---

### Post by Berneri on 2008-11-26
Is your whole hard disk protected or just your root partition ? First of all, what you could do is a memory test on the boot: when your booting, press ESC, then go to MEMTEST86 with the keyboard arrows.
In order to get more precise help, you could post your logs, like kern.log, syslogs... In these logs, look for I/O errors pointing to your hard disk or partition and tell us what you see.

---

### Post by mrund on 2008-11-26
It fixed itself after another bout of disk structure checking. All that remains of the weirdness now is a slightly longer boot process. And an inability to run Wifi Radar. What software should I use to find wifi now?

---

### Post by Berneri on 2008-11-27
Do you have the smartctl package installed ? If your hard disk is SMART enabled, this allows you to check for the integrity of your hard disk. I would recommend to install it and then run a: sudo smartctl -a /dev/your-hard-disk
Then look for errors.

---

