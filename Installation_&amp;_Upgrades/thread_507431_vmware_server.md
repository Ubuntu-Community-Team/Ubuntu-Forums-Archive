---
title: "vmware server"
date: 2007-07-23
forum: Installation &amp; Upgrades
---

### Post by foots2015 on 2007-07-23
Hello

I am interested in getting the newest version of vmware 1.02 server installed on feisty fawn 7.04. I found this so far. [http://www.howtoforge.com/ubuntu_vmware_server]("http://www.howtoforge.com/ubuntu_vmware_server")

Would it be safe to follow these instructions despite the fact that these are for earlier versions of both programs? or is there another way i should follow?

many thanks

---

### Post by gvoima on 2007-07-23
Yes, that should work on all 1.0.x vmware server versions. The newest one at the moment is 1.0.3 and I don't see any difference with the install.

However, there are some kernel module problems with Feisty Fawn and VMware server (they don't compile right). I haven't tested it yet, because I don't need vmware on my laptop and have Edgy on my desktop. But you should do a search of vmware server and feisty on this forum.

And if I remember correct, there's even a patch for it somewhere on the VMware forums. You should check those out too. And please report back if you get it working :)

Thanks.

---

### Post by upthelum on 2007-07-23
Im trying to install vmware and getting problems with C header files which is preventing installation, if you get it working post it here.

---

### Post by upthelum on 2007-07-23
I got it to work with this
sudo apt-get install linux-headers-`uname -r` build-essential
after that it installed no probs...
Oh those aren't apostrophes.

---

### Post by foots2015 on 2007-07-24
OOPS

well i have found a page on the same site detailing exactly how to install on feisty fawn. For those interested here is the link [http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto]("http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto")

I will let you guys know if i get it working

---

### Post by gvoima on 2007-07-24
Yes, that's the patch I was talking about. Atleast I got it working with Feisty Fawn.

Just follow the steps on the page posted above.

---

### Post by foots2015 on 2007-07-24
well i am in the process of installing and i get to here
```

root@tim-laptop:/home/tim/vmware-server-distrib# vmware-install.pl
bash: vmware-install.pl: command not found

```

I don't know what to do from here. I have checked the directory and the file does exist. I am following the order of directions given on the website on my last post. Sorry that i don't know much about linux yet but i am learning.

peace

---

### Post by foots2015 on 2007-07-25
well i have decided to try and install vmware server using synaptic, I will post back on the update.

---

### Post by veloce on 2007-07-25
> **foots2015 said:**
> well i have decided to try and install vmware server using synaptic, I will post back on the update.

This is by far the best way.  All those out of date "howto"s should be deleted!

---

### Post by foots2015 on 2007-07-25
Ok, i guess the HOWTO isn't needed after all. I got the Vmware to install correctly using the one from the ubuntu repository. It installed without a problem.

---

