---
title: "apt-get upgrade question"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by pwaugh on 2010-05-13
Just installed Ubuntu 10.04 LTS on my HP multi-touch tx2-1025dx laptop, and installation was smooth.

After running:

```

patrick@patrick:~$ sudo apt-get update
blah... blah... blah

<snip>

patrick@patrick:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
patrick@patrick:~$ 

```

Now, having installed "apticron" I get an email with this:

```

apticron has detected that some packages need upgrading on:

       patrick
       [ 127.0.1.1 192.168.1.101 2002:62f0:1f6a:0:221:ff:febd:a1d0 ]

The following packages are currently pending an upgrade:

       linux-generic 2.6.32.22.23
       linux-headers-2.6.32-22 2.6.32-22.33
       linux-headers-2.6.32-22-generic 2.6.32-22.33
       linux-headers-generic 2.6.32.22.23
       linux-image-2.6.32-22-generic 2.6.32-22.33
       linux-image-generic 2.6.32.22.23

```

and I'm wondering, how I upgrade "kept back" packages, and if I really should do so in this case.

Thanks for you thoughts/assistance.

Patrick

---

### Post by User3k on 2010-05-13
Did you type sudo apt-get update or sudo apt-get install update or sudo apt-get upgrade?

---

### Post by pwaugh on 2010-05-13
> **User3k said:**
> Did you type sudo apt-get update or sudo apt-get install update or sudo apt-get upgrade?

 sudo apt-get upgrade

---

### Post by User3k on 2010-05-13
I am not completey sure but try

Sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade


and see if that helps. I also wonder if sudo apt-get dist-upgrade would work or if that is just for upgrading from one Ubuntu version, like 9.10, to another, like 10.04. Hopefully someone else can give better advice then me, lol.

Edit: This link might help as well with apt-get commands
[http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)

---

### Post by Partyboi2 on 2010-05-13
Hi, open a terminal and do a partial upgrade
```
sudo apt-get - dist-upgrade
``` Hopefully this will install those packages being kept back.

---

### Post by MSPdwalt on 2010-05-13
I assume being you're on a multi-touch you are using the GUI?  When using the GUI I've found it's best to use the update manager.  This will apply all the updates without crashing anything you're working on. This will also apply the updates that require a reboot (the kept back packages, in your case new kernels)

apt-get works best from the console outside of X or in a server scenario with no GUI.  Because when you tell it to upgrade it applies all updates that don't require a reboot and it does it right now.  If a service needs restarting it does it (like X), if a process needs to get killed it happens (Firefox, open office).

If you insist on doing this from the command line  do like [Partyboi2]("http://ubuntuforums.org/member.php?u=221279") says and..

```
apt-get dist-upgrade
```

---

