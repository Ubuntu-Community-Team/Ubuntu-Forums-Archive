---
title: "Module raid456 not found."
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by jstroot on 2007-05-02
Hey all,

I upgraded my home computer to feisty using the official method. After I started the process, another emergency came up and I had to leave the house. When I came back, the computer was at the login screen, which was blue with some flowers on it. Not the normal 'human' themed Ubuntu login. 
I tried to login, the computer hung, so I did a hard reboot.

Now, ubuntu will not load. The screen eventually displays

```
modprobe: FATAL: Module raid456 not found.
```

I loaded a dapper live cd, and am able to easily mount the drives. 

Do I just need to get the raid456 module to load? If so, can you do that with a live cd?

Not sure what to do to fix this.

Any ideas welcome.

thanks

---

### Post by jeromio on 2007-05-03
I´m in the same boat. Except I have a Kubuntu system. Patiently awaiting some sage advice...

---

### Post by jstroot on 2007-05-06
**Bump**

---

### Post by kuja on 2007-05-08
Well, seeing as it supposedly works on some of the older live cds. Why not just install a kernel from Edgy or Dapper? It's definitely a fast and easy fix. The only problem that could crop up is if you were using the restricted-modules package, in which case you'll need to grab the restricted-modules package from Edgy or Dapper also.

If you're unable to boot, try this method:

Boot from a livecd

pull up a terminal and type:
sudo mkdir /target

wget [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-image-2.6.17-10-generic_2.6.17.1-10.34_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-image-2.6.17-10-generic_2.6.17.1-10.34_i386.deb)
sudo mv linux-image-2.6.17-10-generic_2.6.17.1-10.34_i386.deb /target

Now, mount your filesystem on that directory: (assuming your broken feisty installation partition is /dev/hda1 (first IDE drive, first partition))
sudo mount -t ext3 /dev/hda1 /target

Now, still in the terminal, type:
sudo chroot /target
dpkg --install /linux-image-2.6.17-10-generic_2.6.17.1-10.34_i386.deb




This should be all it takes, if not, let me know.

---

### Post by jeromio on 2007-05-09
Here's the problem I have now: I cannot see my fakeraid partition when booting from the livecd. My /boot is also under fakeraid. When I first installed, I wanted to put boot on a regular, non fake raided part, but apparently that's just not possible.

So if I pull up qparted or any other util, the 2 drives that comprise my mirrored set show up with unknown partitions. So I need a livecd that has fakeraid support on it. 

What I'm wondering right now is, back when I set-up this system, how did I do it? I see all these posts about Ubuntu not having dmraid in the livecd. Yet I, not any kind of a power-user, managed to set-up my box with fakeraid. It had to have been some easy, wizard-y thing.

---

### Post by kuja on 2007-05-09
Yeah ... I had posted here because someone else said he was having this problem. Funny thing was, with him, anyhow, he wasn't even using raid at all. Crazy huh? Anyhow, seeing as you are, this is what you need to do Jeremio:

First, in the live cd, before doing anything else, enable universe, sudo apt-get update, sudo apt-get install dmraid. Voila, dmraid on the live cd ;)
If it's still not picking up the partition setup in /dev/mapper, try running sudo /etc/init.d/dmraid stop; sudo /etc/init.d/dmraid start. If that still doesn't do it, try "sudo dmraid -ay"

When you set it up, I bet you used the FakeRaidHowto. It's not wizardly at all, but it's still pretty clear.

---

### Post by jeromio on 2007-05-09
Seems like it was part of the install wizard, b ut it was awhile ago - who knows. I have terrible luck with HD failures though, so I had to use raid.

SO, for some reason I thought the dmraid had to be actually part of the system on the livecd - thought installing it would require a reboot. But, you were right - installing it was easy. Then installed lvm and was able to mount my drive(s). So now, at the very least, I can make sure to copy my files to the external hd.

Here's something really strange though: the /boot folder is empty. I have 2 volgroups: one for swap, and one for everything else. I don't know where the boot part is. I guess I should've taken notes when I set this system up.

It's a shame to have to re-image this whole system. It's gonna take me a day to get the email services up and running. On the other hand, I have little confidence that there will be any other way to resolve this.

---

### Post by kuja on 2007-05-10
Better check that it's not on one of the other /dev/mapper/[insert gibberish here]_[insert number here] partitions.

---

