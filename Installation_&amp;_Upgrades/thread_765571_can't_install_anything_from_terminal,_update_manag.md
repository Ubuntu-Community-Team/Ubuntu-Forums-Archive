---
title: "can't install anything from terminal, update manager, etc"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by cbo_x on 2008-04-24
Hi

I'm behind a proxy server at my college dorm. I dont know much about how they work but usually I enter it as www-cache.une.edu.au port 8080 or as an automatic configuration script at [http://proxy.une.edu.au/proxy](http://proxy.une.edu.au/proxy).

I put the first one with username and password in the Network Proxy settings under System > Administration but whenever I try to install anything via the terminal or through the update manager it doesn't work.

Any help would be greatly appreciated.

---

### Post by ssam on 2008-04-24
there are quite a few bugs reported about this
[https://launchpad.net/ubuntu/+bugs?field.searchtext=update-manager%20proxy&orderby=-priority%2C-severity](https://launchpad.net/ubuntu/+bugs?field.searchtext=update-manager%20proxy&orderby=-priority%2C-severity)

you could try [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/21536/comments/2](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/21536/comments/2)

or you could use the CD update method
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by Peter09 on 2008-04-24
what symptoms?

Is this just today?

PC

---

### Post by cbo_x on 2008-04-24
thanks for your replies, yes this is today after I installed hardy over my old gutsy partition. I tried the CD upgrade before but it couldn't install, i dont really remember the message. So I tried the installation from scratch. It used to work fine under gutsy. 

I can now install from the terminal but not from synaptic or anything else. How do i put the proxy settings into apt.conf, as suggested in the bug report?

Also when I go into hardware drivers and look at my wireless (BC4318) it says 'in use' even though its not enabled.

thanks again for your help

---

### Post by ssam on 2008-04-24
i have not used proxy settings for apt before, but the documentation seems to be in

```
man apt.conf
```

to get broadcom working i think you just need to install the package.

bcm43xx-fwcutter

but you'll need to do it with network working, so that it can grap the firmware from the web. i don't know how you set it's proxy. otherwise you will have to manually download the firmware, and run the fwcutter on it.

---

### Post by cbo_x on 2008-04-24
hi thanks again for your reply, I tried a few times to install the bcm43xx-fwcutter from the hardy CD but like you said it needed to download the firmware from the web but I should be able to look up how to do it manually.

as for the synaptic, I opened the apt.conf file and it seems to have my proxy settings in it but I still can't get anything off synaptic.

my apt.conf file says
```

Acquire::http::Proxy "http://www-cache.une.edu.au:8080@bhaniffa:password/";

```

Is this problem solvable for the update managager at all or will I just have to use workarounds? If so I might have to move back to gutsy, though according to the launchpad note it was a bug in previous releases as well, so I dont know why its stopped working on this one when it worked on feisty and gutsy? But anyway its only a day out.

---

### Post by Peter09 on 2008-04-25
just to check, can you use sudo ok? If you do sudo <any command> what happens.

There is a bug to do with having a long (multi-word) hostname in /etc/hostname.

If you do get a problem with this go to recovery mode and edit your hostname to a single word.

PC

---

