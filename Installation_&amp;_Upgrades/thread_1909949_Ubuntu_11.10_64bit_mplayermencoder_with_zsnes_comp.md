---
title: "Ubuntu 11.10 64bit mplayer/mencoder with zsnes compability problem"
date: 2012-01-16
forum: Installation &amp; Upgrades
---

### Post by Spekkio83 on 2012-01-16
Hello!
 
I run Ubuntu 11.10 64bit version, and I have many questions [IMG]http://board.zsnes.com/phpBB3/images/smilies/icon_smile.gif[/IMG]

When I install zsnes with "apt-get install zsnes" it wants to remove some libraries, also mplayer and mencoder

The following packages will be REMOVED:
  libsdl1.2-dev libsdl1.2debian libsdl1.2debian-alsa mplayer mencoder
The following NEW packages will be installed:
  libsdl1.2debian:i386 libsdl1.2debian-alsa:i386 zsnes:i386

So I cannot use movie recorder and dump a movie. I was thinking, maybe I can compile mplayer and mencoder myself
and  then install zsnes. But it still wont work to compile a 64bit  version  of mencoder, because it wants 64bit version of all the  libraries too,  libsdl1.2 wich also zsnes needs.

I have also tried to compile zsnes myself, I had to add -march=i686 -m32 to CFLAGS. But I still couldn't compile it correctly.

Is  it possible to build a version of zsnes with static libraries ? Or  will  that cause problems with compability when using a 64bit version of   libsdl and other libraries simultaniously?

I also got a response from the zsnes forums, that 32bit libraries and  64bit libraries should bort be installed but in different paths. They do  that in debian, why not ubuntu? Or just a problem with only these libs ?

Also trying to install mencoder will remove the zsnes:i386 package, vice  versa. They should both be able to install since zsnes is using  mencoder for a feature.

---

### Post by Spekkio83 on 2012-01-16
No answers at all!?!?!

---

### Post by Spekkio83 on 2012-01-19
I want to bump, still no idea how to fix this problem.

Take on the terribly difficult task to port zsnes to 64bit? :)

Or how to have multiple libraries installed, both 64bit and 32bit version in different paths.

---

### Post by mips on 2012-01-19
Download/install: [lib32ao.deb]("http://www.linuxtotal.org/download/file.php?id=10") & [zsnes_1.510-2.1ubuntu1.1_amd64.deb]("http://www.linuxtotal.org/download/file.php?id=9")




.

---

### Post by minorgroove on 2013-01-14
someone addressed a similar issue here:

[http://askubuntu.com/questions/91959/why-does-vlc-media-player-uninstall-when-zsnes-is-installed-through-terminal](http://askubuntu.com/questions/91959/why-does-vlc-media-player-uninstall-when-zsnes-is-installed-through-terminal)

which instructed:

```
sudo add-apt-repository ppa:smaxein/ppa && sudo apt-get update && sudo apt-get install zsnes

```


that appeared to have solved it for me, as I have both zsnes and mplayer

---

