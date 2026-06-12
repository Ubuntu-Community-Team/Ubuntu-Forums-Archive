---
title: "Boot failure 'Serious issue' with new Trusty kernel"
date: 2016-08-11
forum: Installation &amp; Upgrades
---

### Post by Xiguus on 2016-08-11
Hi all,

Last update cycle installed kernel 3.13.0-93-generic, now my boot fails at the purple screen with a message 'Serious errors were found while checking the disk drive for /' and giving me options to 'Ignore, Skip, Manual'. I can still boot 3.13.0-92. What's happening? any advice?

Thanx,

Xiguus.

---

### Post by kurt18947 on 2016-08-12
This is not from a recognized source but it seems pretty reasonable to me:

[http://bitsofmymind.com/2014/03/14/how-to-fix-fsck-your-root-file-system-that-you-have-to-boot-into-on-linux/](http://bitsofmymind.com/2014/03/14/how-to-fix-fsck-your-root-file-system-that-you-have-to-boot-into-on-linux/)

It involves using a live session to check the file system on your hard drive. I suspect it would be a good idea to use the same version - current Trusty - to run fsck. I would also use the live session to copy any important data files to another storage destination if possible. That way if the subject file system were to get irretrievably scrambled you could restore the O.S. then data files.

---

### Post by Xiguus on 2016-08-13
Hi kurt18947,

Thanks for your response, much appreciated.
I don't think this is a filesystem integrity issue as kernel 3.13.0-92 still boots and the message comes up on the purple screen, which (by my understanding) tells us that plymouth is loaded.
It's probably relevant that the failed system is a wubi. I know that wubi is no longer supported, so there are no new (official) fixes. I would like to keep using the wubi for as long as I can for obvious reasons of convenience. My question becomes, therefore, what has happened between 3.13.0-92 and 3.13.0-93 that causes a previously working system to fail? I have found this: [http://lwn.net/Articles/696922/](http://lwn.net/Articles/696922/), which gives a hint, but no indications of a solution for my problem. Is there something I can do, and do these new features effect upgrades, to eg 16.04?

Thankx again,

Xiguus

---

### Post by kurt18947 on 2016-08-13
Ahhh, WUBI. That was never intended to be more than a means to 'test drive' an Ubuntu distro, kind of like a live DVD/USB. If your machine is up to it, have you considered a Virtual Machine? Or dual boot? With the advent of SSDs, I don't find dual boot that onerous. I have Ubuntu-Gnome as a host and Windows 10 as a guest on one machine - Intel Core i5 w/ 6 GB. RAM. It works pretty well but I'm not a gamer. Windows gaming running in a VM probably isn't going to cut it unless there's a means to implement GPU pass-through so the guest OS has access to the hardware GPU rather than a virtual GPU. I guess one could do Windows Host *buntu guest but for my purposes I figured the more solid less resource intensive O.S. should be the host.

---

### Post by Xiguus on 2016-08-13
Hi kurt18947,

Thanx for your response.
Yes, it's often said that 'wubi was never intended to be...', but it's also pretty obvious that it's taken on a life of it's own - too successful, perhaps? I'll keep the wubi running for as long as I can because I've built up a lot of software and a lot of my user files are there. I also have a stand-alone Trusty partitiion and a Manjaro partition, which are both good in their own ways, but I'll often try software on the wubi and then install it on one or other of the other two if I decide to keep it.
It seems that 3.13.0-93 spits it on the wubi for some reason. If I can't find a fix I'll try an upgrade to 16.04. Maybe the issues with the current Trusty kernel won't apply and all will be well again. In the meantime I can still use the 3.13.0-92 kernel.

Thanx again,

Xiguus.

---

### Post by Bucky Ball on 2016-08-13
[QUOTE=Xiguus]... it's also pretty obvious that it's taken on a life of it's own[/QUOTE]

Not that we've noticed. A user pops up a few times a year using Wubi and they are generally advised to forget it and dual-boot. 

Whatever it's life may currently be, Wubi is not and has not been supported officially by Canonical for quite a while now, we no longer officially support it here (we once had a section specifically for Wubi) and you will have a hard time getting support for such an archaic version.

There is a member or two that still remembers something about it, so you might get lucky, but it was never widely popular around here even when it was supported (as, as you know, never intended as a permanent solution) so you are largely on your own. Just to make one very important point: it does not work with UEFI.

Having said all that, maybe that other Wubi user will pop up and help. Good luck.

---

### Post by Xiguus on 2016-08-14
Hi all,

Advantages of reading your own threads, Part I...:oops:
My mistake was in thinking that because I had successfully updated kernels previously, and because the error message was different, that I had a new problem, which isn't the case. The fix is the same as that for my previous thread, 'update wubi 14.04, initramfs boot fail'. It seems that the cause is an update to initramfs-tools, now 0.103ubuntu4, which has overwritten (?) the previous fix, carried up to 3.13.0-92.
So, to boot the new kernel:[INDENT]Select Ubuntu from the windows Boot Menu, as normal
Select 'Additional options for ubuntu'; the new kernel (3.13.0-93) should be highlighted
Press 'e'; the grub load script will display
Edit the line[/INDENT]
[INDENT=2]linux    /boot/vmlinuz-3.13.0-93-generic root=UUID=SOMEHEXNO loop=/ubuntu/disks/root.disk **ro**   quiet splash $vt_handoff[/INDENT]
[INDENT]to read[/INDENT]
[INDENT=2]linux    /boot/vmlinuz-3.13.0-93-generic root=UUID=SOMEHEXNO loop=/ubuntu/disks/root.disk **rw**   quiet splash $vt_handoff[/INDENT]
[INDENT]Press F10; the kernel will boot.
[/INDENT]
 
Now, in the terminal:
```
gksudo gedit /usr/share/initramfs-tools/script/local
```

for (in my machine) ln 148:
```
mount ${roflag} -o loop -t ${FSTYPE} ${LOOPFLAGS} "/host/${LOOP#/}" ${rootmnt}
```

put:

```
loopdev=`losetup -f` 

losetup ${loopdev} "/host/${LOOP#/}"

mount ${roflag} -t ${FSTYPE} ${LOOPFLAGS} ${loopdev} ${rootmnt}
```

Save & exit


and, again in the terminal:

```
sudo update-initramfs -u
```

Reboot when ready...

Best Regards,

Xiguus

PS: Some useful links:[URL="https://https://code.launchpad.net/~noorez-kassam/ubuntu/utopic/initramfs-tools/fix-for-1317437/+merge/219927"]
[/URL][https://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-tmp-could-not-be-mounted](https://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-tmp-could-not-be-mounted)
[https://code.launchpad.net/~noorez-kassam/ubuntu/utopic/initramfs-tools/fix-for-1317437/+merge/219927]("https://code.launchpad.net/%7Enoorez-kassam/ubuntu/utopic/initramfs-tools/fix-for-1317437/+merge/219927")
[URL="https://github.com/hakuna-m/wubiuefi/wiki"]https://github.com/hakuna-m/wubiuefi/wiki



[/URL]

---

### Post by hakuna_matata on 2016-08-15
If you fix **/usr/share/initramfs-tools/scripts/local **manually every update of package **initramfs-tools** (14.04) or **initramfs-tools-core** (16.04) overwrites your changes. Because of more frequent updates of these packages, maybe it is helpful for you to use a script which fixes **/usr/share/initramfs-tools/scripts/local **automatically.   
see [here]("https://github.com/hakuna-m/wubiuefi/issues/5#issuecomment-211083990"):
```
sudo wget https://raw.githubusercontent.com/hakuna-m/wubiuefi/master/data/custom-installation/patch/loop-remount -O /etc/initramfs-tools/hooks/loop-remount
sudo chmod +x /etc/initramfs-tools/hooks/loop-remount
sudo update-initramfs -u
```

---

### Post by kurt18947 on 2016-08-15
> **Xiguus said:**
> Hi all,

Advantages of reading your own threads, Part I...:oops:
My mistake was in thinking that because I had successfully updated kernels previously, and because the error message was different, that I had a new problem, which isn't the case. The fix is the same as that for my previous thread, 'update wubi 14.04, initramfs boot fail'. It seems that the cause is an update to initramfs-tools, now 0.103ubuntu4, which has overwritten (?) the previous fix, carried up to 3.13.0-92.
So, to boot the new kernel:[URL="https://github.com/hakuna-m/wubiuefi/wiki"]

[/URL]

I'm glad you got it working. A VM seems simpler and will be supported for the foreseeable future. Is there a reason to prefer WUBI over a VM?

---

### Post by Bucky Ball on 2016-08-15
Nice work, thanks for sharing and marking solved. ;)

---

### Post by Xiguus on 2016-08-16
Hi all,

Thanx for your responses.

Regarding the VM:[INDENT]I don't use the windows very often at all, so a capability to run two operating systems simultaneously and swap files between them is pretty much out of the frame.
The machine is a (very modest) ASUS laptop. ASUS isn't the most linux-friendly hardware base but I've got it doing most of what I want without too much trouble. I don't game, for example. Whether it can handle two OS's simultaneously, one of them being the behemoth, and manage the hardware reliably, isn't something I need to find out just yet. 
At some stage the wubi will no longer be viable and I will probably turn the partition into a shared home for my linux installations.
[/INDENT]

Thanx to hakuna_matata for your permanent fix. 
Can I suggest that you amend the download command to point to eg **~/Downloads**, and put in a line for manual move to **/etc/initramfs-tools/hooks**? This would give users the opportunity to view the script before they were committed to installing it. 
In my case, I commented out the line 
```
mount ${roflag} -o loop -t ${FSTYPE} ${LOOPFLAGS} "/host/${LOOP#/}" ${rootmnt}
```
in my **/usr/share/initramfs-tools/scripts/local** file, so it is still there. My understanding is that the hook-script will only be run if there is a trigger, which in this case would be a new initramfs-tools version. I assume this would restore this line to match 'oldvalue' and the script will then perform as expected, but I am a little bit uneasy as to what will happen if I make the file executable and run '**update-initramfs**' on my present local file. Do I need to delete the line, or will the hook-script remain dormant until it is triggered?

Thanx again to all,

Best Regards,

Xiguus.

---

### Post by hakuna_matata on 2016-08-16
> **Xiguus said:**
> This would give users the opportunity to view the script before they were committed to installing it. 

You can view the script before downloading: [https://raw.githubusercontent.com/hakuna-m/wubiuefi/master/data/custom-installation/patch/loop-remount](https://raw.githubusercontent.com/hakuna-m/wubiuefi/master/data/custom-installation/patch/loop-remount)
It is also possible to view the script after downloading without executing: e.g.:
```
cat /etc/initramfs-tools/hooks/loop-remount
```
You can also delete it before executing:
```
sudo rm /etc/initramfs-tools/hooks/loop-remount
```
If you execute it with
```
sudo update-initramfs -u
```
and you think the result in **/usr/share/initramfs-tools/scripts/local **is not as expected you can edit the script e.g. with
```
gksudo gedit /etc/initramfs-tools/hooks/loop-remount

```
and replace 
```
oldvalue='mount ${roflag} -o loop -t ${FSTYPE} ${LOOPFLAGS} "/host/${LOOP#/}" ${rootmnt}'
newvalue='loopdev=`losetup -f`; losetup ${loopdev} "/host/${LOOP#/}"; mount ${roflag} -t ${FSTYPE} ${LOOPFLAGS} ${loopdev} ${rootmnt}'
```
with 
```
newvalue='mount ${roflag} -o loop -t ${FSTYPE} ${LOOPFLAGS} "/host/${LOOP#/}" ${rootmnt}'
oldvalue='loopdev=`losetup -f`; losetup ${loopdev} "/host/${LOOP#/}"; mount ${roflag} -t ${FSTYPE} ${LOOPFLAGS} ${loopdev} ${rootmnt}'

```
and execute it again with
```
sudo update-initramfs -u
```

> Do I need to delete the line, or will the hook-script remain dormant until it is triggered?
You do not need to delete the outcommented line. It will replace 
```
mount ${roflag} -o loop -t ${FSTYPE} ${LOOPFLAGS} "/host/${LOOP#/}" ${rootmnt} 
```
also within outcommented lines but it doesn't matter. Every time the old line appears it will replace it again. Of course, a trigger is needed but an install of new initramfs-tool packages triggers the execution of the script automatically.

Note: The script does not only change **/usr/share/initramfs-tools/scripts/local**, it also changes **/scripts/local** within initramfs image:
 ```
lsinitramfs -l /initrd.img | grep scripts/local$ 

```
**/scripts/local** within initramfs image is the file which is executed during booting.

---

### Post by Xiguus on 2016-08-17
Hi hakuna_matata,  Thanx for this, very comprehensive, I will execute the script as it stands,  BR,  Xig.

---

