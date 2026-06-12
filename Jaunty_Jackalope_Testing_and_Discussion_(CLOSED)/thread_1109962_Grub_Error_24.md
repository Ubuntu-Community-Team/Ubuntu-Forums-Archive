---
title: "Grub Error 24"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by FuturePilot on 2009-03-29
So far this has happened on 2 Jaunty computers of mine. When I boot up I get ```
Error 24: Attempt to access block outside partition
```
Both have been converted to Ext4. I though it might be something with the file system so I booted the live CD and ran fsck on all my partitions. It didn't find any errors and when I rebooted I was still getting Error 24. I fixed it on one computer by reinstalling grub with
```
sudo grub-install /dev/sda --root-directory=/ --recheck
```
in a chroot from the live CD.

Now that this has happened on a second computer and I know it probably wasn't some random failure, I'd like to try and debug this, but I don't know where to start. Is this a Grub issue or is it something with Ext4? Has this happened to anyone else?

---

### Post by Polygon on 2009-03-29
is your /boot still ext3? because grub does not support ext4, and if you install jaunty, i think it forces you to have a /boot partition that is ext3.

---

### Post by FuturePilot on 2009-03-29
> **Polygon said:**
> is your /boot still ext3? because grub does not support ext4, and if you install jaunty, i think it forces you to have a /boot partition that is ext3.

I don't have a separate /boot. Grub was patched for Ext4 support in Jaunty and it was working fine all day yesterday. I shut it down last night and now it won't boot this morning.

---

### Post by cariboo on 2009-03-29
> **Polygon said:**
> is your /boot still ext3? because grub does not support ext4, and if you install jaunty, i think it forces you to have a /boot partition that is ext3.

Grub does support ext4, I've been running ext4 since alpha 3 with no problems. No need to have a seperate /boot partition formatted to ext3.

Edit: see bug# [lpbug]314350[/lpbug]

Jim

---

### Post by binbash on 2009-03-31
I am getting same error today! Im using ext 4

---

### Post by FuturePilot on 2009-03-31
> **binbash said:**
> I am getting same error today! Im using ext 4

Hmmm. Interesting. Did you happen to convert from Ext3 to Ext4? I'm thinking it might be something funny that happens when you convert. I also have Jaunty in a VM that I installed with Ext4 and so far nothing bad has happened with the VM.

---

### Post by Kow on 2009-03-31
> **FuturePilot said:**
> Hmmm. Interesting. Did you happen to convert from Ext3 to Ext4? I'm thinking it might be something funny that happens when you convert. I also have Jaunty in a VM that I installed with Ext4 and so far nothing bad has happened with the VM.

I can confirm that initially ext4 formatted filesystems work fine with grub. Done this over and over in virtualbox and on two separate computers. I guess I can try starting with ext3 and converting to ext4 if that is causing problems.

---

### Post by Nizarus on 2009-04-01
same here too :/
is there any workaround ?

---

### Post by FuturePilot on 2009-04-02
Found a bug here if anyone has anything useful they can add if they've had this problem too.

[https://bugs.launchpad.net/ubuntu/+bug/353071]("https://bugs.launchpad.net/ubuntu/+bug/353071")

---

### Post by binbash on 2009-04-02
I had to do a clean install damn bug :/

---

### Post by whoop on 2009-04-08
I think this error happens with upgraded intrepid to jaunty machines which you later convert to ext4. This error happens because the update process does not install the new grub stage (and I am not sure if it is going to be fixed because it's not really a bug).

So to solve this problem is to upgrade grub after you did the file system conversion.
I did this from a live-cd:
```

sudo bash
mount /dev/sda1 /mnt
grub-install /dev/sda --root-directory=/mnt --recheck

```
which is about the same as FuturePilot's solution.

---

### Post by FuturePilot on 2009-04-08
> **whoop said:**
> I think this error happens with upgraded intrepid to jaunty machines which you later convert to ext4. This error happens because the update process does not install the new grub stage (and I am not sure if it is going to be fixed because it's not really a bug).

So to solve this problem is to upgrade grub after you did the file system conversion.
I did this from a live-cd:
```

sudo bash
mount /dev/sda1 /mnt
grub-install /dev/sda --root-directory=/mnt --recheck

```
which is about the same as FuturePilot's solution.

Yeah, that seems to be what happens. It only seems to happen if you've upgraded from an earlier version of Ubuntu. It's actually mentioned [here]("http://www.ubuntu.com/testing/jaunty/beta") that you need to reinstall Grub after you convert. So I don't really think it's a bug either. The problem is this isn't really documented anywhere. That's the first source I've seen that's mentioned reinstalling Grub after converting. The guides for converting like the one on [kernel.org]("http://ext4.wiki.kernel.org/index.php/Ext4_Howto")  don't mention anything about reinstalling Grub.

---

