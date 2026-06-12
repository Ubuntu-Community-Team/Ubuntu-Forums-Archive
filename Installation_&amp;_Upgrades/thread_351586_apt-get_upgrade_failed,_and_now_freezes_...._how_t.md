---
title: "apt-get upgrade failed, and now freezes .... how to fix?"
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by benlumley on 2007-02-02
Hello to you all.

Hoping someone can give me some pointers here.

I'm relatively new to linux/ubuntu, but have managed to get a web server up and running for development, with a few other things to help us out, using the edgy server distro of ubuntu. All is working well, generally pleased with it so far and how well it's working.

But now I have a problem that I'm stuck on.

Yesterday it did an apt-get update, followed by apt-get upgrade.

The apt-get upgrade stopped for ages (several hours) on 

```
update-initramfs: Generating /boot/initrd.img-2.6.17-10-generic

```

eventually i quit it, figuring it must have gone wrong. apt-get now tells me to run dpkg --configure -a because dpkg was interrupted.

When i run this, it gets to the same update-initramfs message and stops again.

Can someone give me some pointers on how to sort this out please? Happy to provide any other info you might need.

Also ... is it going to refuse to boot if shut down? Scared to turn it off in case it does.

Ta.

---

### Post by benlumley on 2007-02-02
Had another bash at this and still can't make any headway with it .....

---

### Post by benlumley on 2007-02-03
In case anyone else is reading this because they have the same problem ....

Rebooting worked fine.

And I solved the problem by doing

```
dpkg -C

```
which showed a list of the problem packages:
```

udev
mdadm
linux-image-2.6.17-10-general
initramfs-tools
volumeid
```

I downloaded all of these from [http://packages.ubuntu.com/edgy/allpackages](http://packages.ubuntu.com/edgy/allpackages) (so presumably the original versions for edgy, or else a set that work together properly).

I downloaded them to a folder (with wget), cd'd to that folder in terminal and did

```
dpkg -i -r ./
```

and all seems good again.

I won't be trying apt-get upgrade again in a hurry, at least not without learning more first.

---

### Post by benlumley on 2007-02-05
[IMG]http://z.about.com/d/phoenix/1/0/r/K/tumbleweeds01.jpg[/IMG]

(tumble weed)

---

