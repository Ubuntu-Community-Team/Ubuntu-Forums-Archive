---
title: "How to properly install Kernel Source?"
date: 2005-04-23
forum: Installation &amp; Upgrades
---

### Post by nemini on 2005-04-23
Hi all.. im abit new to the world of linux but im not a completely hopeless chap after all. I´ve recently evaluated a bunch of different linux distributions to see if it could actually fit me in my everyday work. Amongst all the distributions i´ve tested, SUSE and Ubuntu has been the ones i have liked the most and found rather easy to use for someone with limited linux knowledge.

However, ruuning ubuntu i get the same problem evertime i try to install any of my 3:rd party linux programs, Acronis Trueimage or NOD32 For linux for example, then need to build modules but since the kernel sources arent installed the installer will always quit with the message that it cant find the kernel source. Running apt-get kernel-source does pretty much the same thing as getting the kernerl source package from the SPM, it places a tarball in /usr/src , but i dont know what to do next :p

The installers also seems to by default look for the kernel source in /lib/modules/2.6.11-1-amd64-k8/build


Anyone who could help me with this i would greatly appreciate. If i can get this part sorted it would make it alot easier for me to actually use the system :)

---

### Post by Dr Gonzo on 2005-04-23
Well, you don't actually need the kernel source, just the headers.

I'd suggest doing a search like this:```
apt-cache search linux headers
``` Look for the headers for the kernel you're running and install the package you need.

This should install the headers to a directory under /usr/src.

You could also just unpack the tarball in the /usr/src directory.  This will contain the headers as well, but unless you're planning to compile a kernel yourself, you really don't need the whole thing, just the /usr/src/linux-source-blah/include directory.```
cd /usr/src; sudo tar xvjf linux-source-blah.tar.bz2
```man tar will tell you all about tar and the flags to use.  Note that 'blah' should be replaced with your kernel version.  You can see this by typing 'uname -a' in bash.

---

### Post by az on 2005-04-23
There is a typo in the above post that may cause you a problem.

The package is linux-headers-(whatever version)

If you need the whole source, use linux-tree (apt-cache search linux-tree)

---

### Post by nemini on 2005-04-23
well.. i just did, but not sure im getting any smarter hehe. Running the installer again says "Cant find kernel source" /lib/modules/2.6.11-1-amd64-k8/build doesnt exist

Just copying the files there didnt do the trick either , anyone?

---

### Post by elbondo on 2005-04-23
I'm lucky I happened to stumble across this thread and figure out what to do for my ndiswrapper install.

I did the > apt-cache search linux headers, and searched around for what I needed. A few kernel source tries and header tries werent successful, and in the make install i was running it, it showed it was asking for"/lib/modules/2.6.10-5-386/build". So I changed the apt-get I did for 'linux-headers-2.6.10-5' to 'linux-headers-2.6.10-5-386', and it worked fine.

I don't know exactly which apt-get to run to get the full source though, but headers work fine for most things.

---

### Post by nemini on 2005-04-23
Ok.. well, i found some documentation for the snapapi module that trueimega requires. And solved it. The thing is that the Acronis installer automatically trie to build the module, and by some odd reason it takes fo granted to find the headers in /lib/modules/currentkernel whilst its actually located elsewhere

However, when the installer exists, i found it put the src files for the snapapi26 module in /usr/src

so running the following:

root@proxymabnc:/usr/src/snapapi26-0.6.3 # dkms build -m snapapi26 -v 0.6.3 --configfile /usr/src/snapapi26-0.6.3/dkms.conf --kernelsourcedir /usr/src/linux-source-2.6.11
Preparing kernel 2.6.11-1-amd64-k8 for module build:
(This is not compiling a kernel, only just preparing kernel symbols)
Running Generic preparation routine
make mrproper......
using /usr/src/snapapi26-0.6.3/dkms.conf
make oldconfig............................................................................................................................................................................................................................. ................................................................................ 


Its been 20 mins now.. and that progress bar still is working.. is that normal?


Another quickie, how to stop the running sshd service/daemon? i want to edit the sshd config but cant save it when the service is running

/etc/ssh$ sshd stop
sshd re-exec requires execution with an absolute path

---

### Post by nemini on 2005-04-23
hmm, no cant be right.. its still progressing.. *sigh* ... hehe

---

### Post by axb on 2005-04-27
Have you had any success?

Regards,
axb

---

