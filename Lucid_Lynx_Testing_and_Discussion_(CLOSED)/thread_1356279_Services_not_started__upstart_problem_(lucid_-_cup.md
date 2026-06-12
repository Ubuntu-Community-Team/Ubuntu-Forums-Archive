---
title: "Services not started / upstart problem? (lucid - cups, sshd)"
date: 2009-12-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by nicoseb on 2009-12-15
I upgraded to lucid last weekend. A few things don't work properly, but that is to be expected.

Nevertheless there is something that I cannot figure out and did not find anything about it. 
I have different services, at least ssh and cups server, that are not started during boot. If I do a "sudo /etc/init.d/{service} start" it starts without complaining and it works fine. I have a feeling that other weird behaviors are linked to the same problem but I am not sure what that one is.

During startup, right before getting gdm to start, the line output changes (so I cannot see what else was written) but at least I have time to see (plus I can go back to it with ALT+CTRL+F1) 
"init networking main process (xxx) terminated with status 1"

Moreover, after breaking grub earlier, I rebooted on my partition from a SystemRescueCD and I saw "upstart-udev-bridge main process (xxx) terminated with status 1"

Also, when I first start the pc I usually see "gdm main process (xxx) terminated with status 1", GDM does not start and I just get a black screen. After reboot it always works again...

In a nutshell there is something wrong during boot, but I could not find anything in my logs...

If someone knows what is going on or have any debugging idea, I will love to hear them!

Just tried this:
```
sudo start --verbose  networking
start: Job failed to start
```
no explanation at all...
FYI: uname -a
Linux brainless 2.6.32-8-generic #12-Ubuntu SMP Sat Dec 12 12:54:44 UTC 2009 x86_64 GNU/Linux

---

### Post by nicoseb on 2009-12-16
I also have to do
```
sudo /etc/init.d/vboxdrv setup
```

In order to get Virtual Box to start my virtual machines...

I guess nothing is started during the boot! No one?!
I might just open an upstart bug on launch pad!

---

### Post by Aikon- on 2009-12-16
I am experiencing a very similar issue, however I haven't moved to Lucid yet, I am on Karmic. Of the ones I've noticed so far, I have to manually start:
[LIST]
[*]MPD
[*]BOINC client
[*]SSH server
[/LIST]

If anyone has any suggestions, I would be glad to hear them.

-Aikon

---

### Post by sad1sm0 on 2009-12-22
I too am having the same issue on Karmic.  Right now, Almost none of my services are starting. I have dnsmasq, ddclient, apache, mysql, nfs, and cups not working.  Not sure what else, but I have had to manually restart each of these service each time I reboot for a couple of days now.  I have had this happen to me in previous installations, and I eventually gave up and reinstalled the system to correct the problem.  I would like to figure out why this happens and be able to avoid having to re-install.  I don't know anything really about upstart or initv to be quite honest, so I'm kind of at a loss.  I have found that some services that start have upstart utilities to start, stop and check status, but not the ones listed above.  I don't really know if that makes any difference or not, just an observation.

Also, just as mentioned in the posts above, If I manually start these services, they startup without any errors and nothing is showing up in my logs.

---

### Post by nicoseb on 2009-12-22
Yeap sounds right, same thing that for me.

So I guess Karmic is broken too... that su**s

---

### Post by simonbp on 2009-12-23
Daemons also not working for me in a fresh install of 32-bit Karmic on real hardware.

I installed via debootstrap/chroot because of a scratched install CD; is that the method you guys used for the virtual machine installs? If so, that may the source of error...

---

### Post by meonkeys on 2009-12-23
Anyone know if there is an open bug about this?

I'm experiencing the same problem: mysql server and ssh daemon do not start automatically.

My /home dir is an encrypted partition (LUKS/ext3). I have to put in a password during boot to unlock it. Not sure if that makes any difference.

---

### Post by MrGrey1 on 2009-12-23
Same problem here on 9.10. sshd not starting on boot. Has to be manually started.
Is there another method or workaround to start sshd without having to login to the box locally?

Solution:
Got sshd starting again on boot by downgrading Upstart 0.6.3-11 to 0.6.3-10.
[http://ubuntuforums.org/showthread.php?t=1305226&page=2](http://ubuntuforums.org/showthread.php?t=1305226&page=2)

---

### Post by ElHeineken on 2009-12-29
A bug report has been created about this issue:
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/500520](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/500520)

---

### Post by sad1sm0 on 2009-12-30
It should probably be noted that you can lock the version within synaptic once you downgrade to prevent future upgrades.  Click Package -> Lock Version.  You can also pin the version in apt by editing /etc/apt/preferences and adding the following lines

```

Package: upstart
Pin: version 0.6.3-10
Pin-Priority: 900

```

There is a howto on pinning and holding packages [here]("https://help.ubuntu.com/community/PinningHowto")

---

