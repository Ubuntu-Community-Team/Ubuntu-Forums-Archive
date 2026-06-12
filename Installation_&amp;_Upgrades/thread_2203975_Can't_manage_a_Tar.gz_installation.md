---
title: "Can't manage a Tar.gz installation"
date: 2014-02-06
forum: Installation &amp; Upgrades
---

### Post by eli_fabrikant on 2014-02-06
Hallo Forum,

I'm trying to update the Alsamixer on my system (Ubuntu 13.10) (because the internal mic is not functioning and I hope it's a driver problem). I went to the alsa project and found the appropriate daily feed package for my release:

[https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages](https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages)
 
It's a tar.gz file, which I tried to instal using the instructions from this seemingly helpful link :
[http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file](http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file)
But I just can't seem to find any 'Install' file in this package.
 
and the command 

./configure

just doesn't work, although I am in the right folder and I extracted the tar.gz.

I've tried searching for answers on the forums but couldn't find any good sollution.

Any ideas ?

thanks in advance !
Eli

---

### Post by TheFu on 2014-02-06
a) Use **Adv Reply** and "code" tags. If things don't line up, it makes it difficult to read - hard to read means fewer people will read it.
b) copy/paste the exact command and exact output from the attempts. Be certain the PWD is displayed too.

In general, you'll need the basic C development setup before you can start.  That is in the **build-essentials** package - install it.
Next open a terminal, cd into the correct directory where the files are de-tar'd.
Run **./configure | tee /tmp/log.alsa**
The "tee" command will clone output from the screen to a file ... easier to copy/paste later and post here.
If it works fine (the output isn't missing any programs), then run **make** to build the software.

---

