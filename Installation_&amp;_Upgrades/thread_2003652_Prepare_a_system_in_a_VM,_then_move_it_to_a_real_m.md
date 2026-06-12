---
title: "Prepare a system in a VM, then move it to a real machine?"
date: 2012-06-14
forum: Installation &amp; Upgrades
---

### Post by KenSharp on 2012-06-14
Hi,

I basically want to do this:

1. Install an Ubuntu Server system in a VM.
2. Set up all the required packages and options.
3. Move the VM partition to a physical partition on a real server.

Can this be done?  I have Googled around for an answer but most the answers I find are disappointing or plain ludicrous.

The VirtualBox manual offers no help.

Any help much appreciated!

---

### Post by Lauscher on 2012-06-20
Hello,

there are some experimental features of vboxmanage: type in your  terminal 'vboxmanage internalcommands' and you find useful commands like  '[createrawvmdk]("http://www.virtualbox.org/manual/ch09.html#rawdisk")' and 'converttoraw'  that should help you.

At the moment I don't find converttoraw in the manual, but maybe you have more luck. Otherwise, you can use createrawvmdk to get access on a physical hard disk, and copy your files.

You may have problems with the rights to get access; one possibility to solve them is to get member of the group 'disk'. But you shouldn't be member of 'disk' all time, it's not sure.

---

### Post by SeijiSensei on 2012-06-20
I'd use rsync after you've created the machine image you want.

Start by installing the identical version of Ubuntu on the new machine.    Make sure the image is up-to-date by running:
```

sudo apt-get update
sudo apt-get upgrade

```
after installation.

Now make sure you can see the new machine over the network from inside the VM.  Make sure it's also up-to-date then transfer the files by running:

```

cd /
sudo apt-get update
sudo apt-get upgrade
sudo rsync -av . newserver_ip_address:/

```

All the files in the VM will be copied over to the new server.  I'd probably exclude /boot and the transient directories like /proc and /sys by using

```
sudo rsync -av . newserver_ip_address:/ --exclude=/boot --exclude=/proc --exclude=/sys
```

---

