---
title: "Problem with update-initramfs after upgrade"
date: 2010-02-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zika on 2010-02-10
```
Current status: 6 updates [+5].
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be upgraded:
  initramfs-tools initramfs-tools-bin libgudev-1.0-0 libudev0 
  python-central udev 
6 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 860kB of archives. After unpacking 28.7kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://archive.ubuntu.com lucid/main libudev0 151-1 [118kB]
Get:2 http://archive.ubuntu.com lucid/main udev 151-1 [452kB]                   
Get:3 http://archive.ubuntu.com lucid/main initramfs-tools 0.92bubuntu64 [85.6kB]
Get:4 http://archive.ubuntu.com lucid/main initramfs-tools-bin 0.92bubuntu64 [51.1kB]
Get:5 http://archive.ubuntu.com lucid/main python-central 0.6.11ubuntu13 [46.1kB]
Get:6 http://archive.ubuntu.com lucid/main libgudev-1.0-0 1:151-1 [107kB]       
Fetched 860kB in 49s (17.5kB/s)                                                 
(Reading database ... 158688 files and directories currently installed.)
Preparing to replace libudev0 149-5 (using .../libudev0_151-1_amd64.deb) ...
Unpacking replacement libudev0 ...
Setting up libudev0 (151-1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 158688 files and directories currently installed.)
Preparing to replace udev 149-5 (using .../archives/udev_151-1_amd64.deb) ...
Adding `local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
Unpacking replacement udev ...
Preparing to replace initramfs-tools 0.92bubuntu63 (using .../initramfs-tools_0.92bubuntu64_all.deb) ...
Unpacking replacement initramfs-tools ...
Preparing to replace initramfs-tools-bin 0.92bubuntu63 (using .../initramfs-tools-bin_0.92bubuntu64_amd64.deb) ...
Unpacking replacement initramfs-tools-bin ...
Preparing to replace python-central 0.6.11ubuntu12 (using .../python-central_0.6.11ubuntu13_all.deb) ...
Unpacking replacement python-central ...
Preparing to replace libgudev-1.0-0 1:149-5 (using .../libgudev-1.0-0_1%3a151-1_amd64.deb) ...
Unpacking replacement libgudev-1.0-0 ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up initramfs-tools-bin (0.92bubuntu64) ...
Setting up python-central (0.6.11ubuntu13) ...

Setting up libgudev-1.0-0 (1:151-1) ...

Setting up udev (151-1) ...
udev start/running, process 4327
Removing `local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
update-initramfs: deferring update (trigger activated)

Setting up initramfs-tools (0.92bubuntu64) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.33-999-generic
cpio: ./lib/udev/firmware.sh: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.33-999-generic
dpkg: subprocess installed post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
Setting up initramfs-tools (0.92bubuntu64) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.33-999-generic
[COLOR=Red]cpio: ./lib/udev/firmware.sh: Cannot stat: No such file or directory[/COLOR]
update-initramfs: failed for /boot/initrd.img-2.6.33-999-generic
dpkg: subprocess installed post-installation script returned error exit status 1
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: Could not regain the system lock!  (Perhaps another apt or dpkg is running?)
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

Current status: 0 updates [-6].
~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu64) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.33-999-generic
[COLOR=Red]cpio: ./lib/udev/firmware.sh: Cannot stat: No such file or directory[/COLOR]
update-initramfs: failed for /boot/initrd.img-2.6.33-999-generic
dpkg: subprocess installed post-installation script returned error exit status 1
```There was no other dpkg running. There is no /lib/udev/firmware.sh anymore... It used to be there...

---

### Post by tito_torrisi on 2010-02-10
Same problem here after update a few minutes ago. Will this prevent us from restarting?

---

### Post by gjoellee on 2010-02-10
> **zika said:**
> ```
Current status: 6 updates [+5].
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be upgraded:
  initramfs-tools initramfs-tools-bin libgudev-1.0-0 libudev0 
  python-central udev 
6 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 860kB of archives. After unpacking 28.7kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://archive.ubuntu.com lucid/main libudev0 151-1 [118kB]
Get:2 http://archive.ubuntu.com lucid/main udev 151-1 [452kB]                   
Get:3 http://archive.ubuntu.com lucid/main initramfs-tools 0.92bubuntu64 [85.6kB]
Get:4 http://archive.ubuntu.com lucid/main initramfs-tools-bin 0.92bubuntu64 [51.1kB]
Get:5 http://archive.ubuntu.com lucid/main python-central 0.6.11ubuntu13 [46.1kB]
Get:6 http://archive.ubuntu.com lucid/main libgudev-1.0-0 1:151-1 [107kB]       
Fetched 860kB in 49s (17.5kB/s)                                                 
(Reading database ... 158688 files and directories currently installed.)
Preparing to replace libudev0 149-5 (using .../libudev0_151-1_amd64.deb) ...
Unpacking replacement libudev0 ...
Setting up libudev0 (151-1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 158688 files and directories currently installed.)
Preparing to replace udev 149-5 (using .../archives/udev_151-1_amd64.deb) ...
Adding `local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
Unpacking replacement udev ...
Preparing to replace initramfs-tools 0.92bubuntu63 (using .../initramfs-tools_0.92bubuntu64_all.deb) ...
Unpacking replacement initramfs-tools ...
Preparing to replace initramfs-tools-bin 0.92bubuntu63 (using .../initramfs-tools-bin_0.92bubuntu64_amd64.deb) ...
Unpacking replacement initramfs-tools-bin ...
Preparing to replace python-central 0.6.11ubuntu12 (using .../python-central_0.6.11ubuntu13_all.deb) ...
Unpacking replacement python-central ...
Preparing to replace libgudev-1.0-0 1:149-5 (using .../libgudev-1.0-0_1%3a151-1_amd64.deb) ...
Unpacking replacement libgudev-1.0-0 ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up initramfs-tools-bin (0.92bubuntu64) ...
Setting up python-central (0.6.11ubuntu13) ...

Setting up libgudev-1.0-0 (1:151-1) ...

Setting up udev (151-1) ...
udev start/running, process 4327
Removing `local diversion of /sbin/udevadm to /sbin/udevadm.upgrade'
update-initramfs: deferring update (trigger activated)

Setting up initramfs-tools (0.92bubuntu64) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.33-999-generic
cpio: ./lib/udev/firmware.sh: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.33-999-generic
dpkg: subprocess installed post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
Setting up initramfs-tools (0.92bubuntu64) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.33-999-generic
[COLOR=Red]cpio: ./lib/udev/firmware.sh: Cannot stat: No such file or directory[/COLOR]
update-initramfs: failed for /boot/initrd.img-2.6.33-999-generic
dpkg: subprocess installed post-installation script returned error exit status 1
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: Could not regain the system lock!  (Perhaps another apt or dpkg is running?)
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

Current status: 0 updates [-6].
~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu64) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.33-999-generic
[COLOR=Red]cpio: ./lib/udev/firmware.sh: Cannot stat: No such file or directory[/COLOR]
update-initramfs: failed for /boot/initrd.img-2.6.33-999-generic
dpkg: subprocess installed post-installation script returned error exit status 1
```There was no other dpkg running. There is no /lib/udev/firmware.sh anymore... It used to be there...

Whoops here...I made a duplicate thread

---

### Post by zika on 2010-02-10
> **tito_torrisi said:**
> Same problem here after update a few minutes ago. Will this prevent us from restarting?It might. Who is brave enough to try...?

---

### Post by gjoellee on 2010-02-10
> **zika said:**
> It might. Who is brave enough to try...?

NOT me :(


Kidding...I will do it....I will be back in a sec...

---

### Post by zika on 2010-02-10
> **gjoellee said:**
> NOT me :(


Kidding...I will do it....I will be back in a sec...Will You be back...?

---

### Post by gjoellee on 2010-02-10
> **zika said:**
> Will You be back...?

I am back, and the system boots :p

---

### Post by zika on 2010-02-10
> **gjoellee said:**
> I am back, and the system boots :pThank You for Your brave act. Now we just have to find how to re-generate firmware.sh.

---

### Post by tito_torrisi on 2010-02-10
> **gjoellee said:**
> I am back, and the system boots :p

thank you ;-)

---

### Post by ylar34 on 2010-02-10
I just got the same problem:(

---

### Post by kklimonda on 2010-02-10
you can apply [http://launchpadlibrarian.net/39011493/udev-firmware.patch](http://launchpadlibrarian.net/39011493/udev-firmware.patch) and run dpkg --configure -a or wait for the update

---

### Post by jppr on 2010-02-10
> **gjoellee said:**
> I am back, and the system boots :p

Yes, boots work but problem is still same. i can´t update system anymore.

---

### Post by twelve on 2010-02-10
effect me too :(

---

### Post by stiV on 2010-02-10
still - this seems to be broken. i've installed a system from alternate CD and for some reason grub-install in the installer is not working for me. At least it has a problem when running in xenserver. I then installed w/o bootloader, fired up a livecd and repaired the system by hand - no problem there.

then i wanted to use lvm ... and getting update-grub to recognize the (default ubuntu installer) lvm setup does not seem to work. i then realized that i had no initrd at all, so i just made a full-upgrade a gew minutes ago, i have that very same problem and still no initrd. maybe someone threw away that "firmware.sh" from a package!?

---

### Post by Toe on 2010-02-10
The patch from post #11 worked. Thanks! :-)

---

### Post by zika on 2010-02-10
> **kklimonda said:**
> you can apply [http://launchpadlibrarian.net/39011493/udev-firmware.patch](http://launchpadlibrarian.net/39011493/udev-firmware.patch) and run dpkg --configure -a or wait for the updateWaiting for update doesn't help since we can not upgrade!

---

### Post by VMC on 2010-02-10
I restarted because I have another lucid install from just yesterday. 

But it rebooted ok even after the initramfs errors. What I'm thinking is its still using the old initramfs, since it tried it twice and failed both times.


edit/ ok, I see. the initramfs does fail.

I'm wondering why the developers release updates into the wild without at least trying them first?! Since all of us are having errors, any pc would have the initramfs errors. I guess they don't even test the updates. It seems they throw them on the wall and see what sticks.

---

### Post by jppr on 2010-02-10
> **Toe said:**
> The patch from post #11 worked. Thanks! :-)

Can you tell how and what to do?

---

### Post by zika on 2010-02-10
> **kklimonda said:**
> you can apply [http://launchpadlibrarian.net/39011493/udev-firmware.patch](http://launchpadlibrarian.net/39011493/udev-firmware.patch) and run dpkg --configure -a or wait for the updateGreat hint! Thank You!

---

### Post by stiV on 2010-02-10
> **zika said:**
> Waiting for update doesn't help since we can not upgrade!

yeah you can ... edit /usr/sbin/update-initramfs and add a "exit 0" directly after set -e

this won't give you a initrd, but it will let you use aptitude/apt-get again ;) (after running dpkg --configure -a)

---

### Post by gjoellee on 2010-02-10
> **Toe said:**
> The patch from post #11 worked. Thanks! :-)

How to apply the patch?

---

### Post by kklimonda on 2010-02-10
you can do it like that:
```

cd /
sudo wget http://launchpadlibrarian.net/39011493/udev-firmware.patch
sudo patch -Np0 < udev-firmware.patch
sudo rm udev-firmware.patch

```

---

### Post by stiV on 2010-02-10
> **gjoellee said:**
> How to apply the patch?


open "/usr/share/initramfs-tools/hooks/udev", search for "firmware.sh" and replace the one occurance of "firmware.sh" with "firmware". just remove the ".sh" part - done

---

### Post by tito_torrisi on 2010-02-10
> **gjoellee said:**
> How to apply the patch?

hehe, also waiting in both threads for an answer to that :D

---

### Post by zika on 2010-02-10
> **gjoellee said:**
> How to apply the patch?**sudo nano /usr/share/initramfs-tools/hooks/udev** so that ```
# 50-udev-default.rules
 # 50-firmware.rules
[COLOR=Red]copy_exec /lib/udev/firmware[COLOR=Magenta].sh[/COLOR] /lib/udev[/COLOR]
# 60-persistent-storage.rules
 copy_exec /lib/udev/ata_id /lib/udev
 copy_exec /lib/udev/usb_id /lib/udev

```reads
```
# 50-udev-default.rules
 # 50-firmware.rules
[COLOR=Red]copy_exec /lib/udev/firmware /lib/udev[/COLOR]
# 60-persistent-storage.rules
 copy_exec /lib/udev/ata_id /lib/udev
 copy_exec /lib/udev/usb_id /lib/udev

```

---

### Post by VMC on 2010-02-10
> **zika said:**
> **sudo nano /usr/share/initramfs-tools/hooks/udev** so that ```
# 50-udev-default.rules
 # 50-firmware.rules
[COLOR=Red]copy_exec /lib/udev/firmware[COLOR=Magenta].sh[/COLOR] /lib/udev[/COLOR]
# 60-persistent-storage.rules
 copy_exec /lib/udev/ata_id /lib/udev
 copy_exec /lib/udev/usb_id /lib/udev

```reads
```
# 50-udev-default.rules
 # 50-firmware.rules
[COLOR=Red]copy_exec /lib/udev/firmware /lib/udev[/COLOR]
# 60-persistent-storage.rules
 copy_exec /lib/udev/ata_id /lib/udev
 copy_exec /lib/udev/usb_id /lib/udev

```

Your right, that's not a script file but a binary one.

---

### Post by ylar34 on 2010-02-10
> **kklimonda said:**
> you can do it like that:
```

cd /
sudo wget [http://launchpadlibrarian.net/39011493/udev-firmware.patch](http://launchpadlibrarian.net/39011493/udev-firmware.patch)
sudo patch -Np0 < udev-firmware.patch
sudo rm udev-firmware.patch

```

thanks this fixed my glitch.

---

### Post by opengonzo on 2010-02-10
thanks!!

---

### Post by MacUntu on 2010-02-10
If such "no such file" things happen, I usually just do 'sudo touch <file-not-found>'. Of course that doesn't fix anything, but at least I can continue doing updates.

---

### Post by zika on 2010-02-10
> **MacUntu said:**
> If such "no such file" things happen, I usually just do 'sudo touch <file-not-found>'. Of course that doesn't fix anything, but at least I can continue doing updates.Yes, I've thought of that, but kept that just for the case if patch didn't come before sleep-time... That's a cool trick...

---

### Post by VMC on 2010-02-10
> **MacUntu said:**
> If such "no such file" things happen, I usually just do 'sudo touch <file-not-found>'. Of course that doesn't fix anything, but at least I can continue doing updates.
Oh I see. You create an empty file so it continues. At first I wasn't sure what you were doing.

---

### Post by VMC on 2010-02-10
> **stiV said:**
> yeah you can ... edit /usr/sbin/update-initramfs and add a "exit 0" directly after set -e

this won't give you a initrd, but it will let you use aptitude/apt-get again ;) (after running dpkg --configure -a)

I did the above so I could continue with updates and forgot it.

So after patching udev, running 'sudo update-initramfs -u', came back with a cursor. That "exit 0" needs removing since we now have the correct file name.

---

### Post by Rallg on 2010-02-10
My system complained that
./lib/udev/firmware.sh
was not there. So I used
sudo nautilus
to go into
/lib/udev/
and located the firmware file (which had no .sh extension), and created a link to it, named
firmware.sh.
Then, running
sudo dpkg --configure -a
solved the problem.

---

### Post by tad1073 on 2010-02-10
I filed a bug report earlier this morning.

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/519865](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/519865)

---

### Post by zenarcher on 2010-02-10
Same happened to me.  Thanks so much for the fix!

Cheers,
zenarcher

---

### Post by ranch hand on 2010-02-10
> **tad1073 said:**
> I filed a bug report earlier this morning.

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/519865](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/519865)
I think you need t ogo back to the bug page and mark it "public".  I was given the message that I I could not access the page because I was logged in as myself.

---

### Post by ranch hand on 2010-02-10
Well, a little excitement in 10.04 for a change.  This got the old blood pumping.

Made me glad for multi installs.   I ran may updates and then upgraded 2 trow away installs.  Then looked at the forum.  Geeze, what a moron.

Life is easier if you run the patch preemptively.

I had never known, what a shocker, about the  'sudo touch <file-not-found>' command posted by MacUntu.  I ran it on one install just to see what happens.   That is cool.  I will wait on an upgrade to fix that one.

---

### Post by durand on 2010-02-10
> **kklimonda said:**
> you can do it like that:
```

cd /
sudo wget http://launchpadlibrarian.net/39011493/udev-firmware.patch
sudo patch -Np0 < udev-firmware.patch
sudo rm udev-firmware.patch

```

Thanks a lot!

---

### Post by aviramof on 2010-02-10
> **Rallg said:**
> My system complained that
./lib/udev/firmware.sh
was not there. So I used
sudo nautilus
to go into
/lib/udev/
and located the firmware file (which had no .sh extension), and created a link to it, named
firmware.sh.
Then, running
sudo dpkg --configure -a
solved the problem.

thanks you very much the patch did not worked for me for some reason but this does:)

---

### Post by tad1073 on 2010-02-10
> **ranch hand said:**
> I think you need t ogo back to the bug page and mark it "public".  I was given the message that I I could not access the page because I was logged in as myself.

done...my report was a duplicate of [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/519882](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/519882)

---

### Post by ranch hand on 2010-02-10
Thanks.

I went to the link you posted just now and joined in.  They seem unsure that this is a bug.  Folks should jump on one or the other of these bug reports.

---

