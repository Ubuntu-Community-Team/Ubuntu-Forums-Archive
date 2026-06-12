---
title: "Strange results when installing new updates"
date: 2017-08-07
forum: Installation &amp; Upgrades
---

### Post by jjhudak on 2017-08-07
Ubuntu server 17.04 LTS
This is basically a 'out of the box' install on a clean 250GB HD.  I basically specified a LAMP package when I did the install.....fast fwd about 4 months,  the OS informs me that 27 packages can be updated, 7 updates are security upgrades.....and I do a apt-get upgrade, then apt-get install. 

First I get this, something about unmet dependencies (what ever they are???):

```

  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done

  You might want to run 'apt-get -f install' to correct these.
  The following packages have unmet dependencies:
   linux-image-extra-4.4.0-75-generic : Depends: linux-image-4.4.0-75-generic but it is not installed
   linux-image-extra-4.4.0-87-generic : Depends: linux-image-4.4.0-87-generic but it is not installed
   linux-image-extra-4.4.0-89-generic : Depends: linux-image-4.4.0-89-generic but it is not installed
   linux-image-generic : Depends: linux-image-4.4.0-89-generic but it is not installed
                         Recommends: thermald but it is not installed
  E: Unmet dependencies. Try using -f.
```
   
  Then I issue : 

```
apt-get -f install
```
   
  During the process, I get some strange messages, one of which I am out of diskspace (Hard to believe with 250GB on a headless server install...
So here is a partial list of the errors:

```

  signal (Broken pipe)
  Examining /etc/kernel/postrm.d .
  run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
  run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
  Preparing to unpack .../linux-image-4.4.0-87-generic_4.4.0-87.110_i386.deb ...
  Done.
  Unpacking linux-image-4.4.0-87-generic (4.4.0-87.110) ...
  dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-87-generic_4.4.0-87.110_i386.deb (--unpack):
   cannot copy extracted data for './boot/abi-4.4.0-87-generic' to '/boot/abi-4.4.0-87-generic.dpkg-new': failed to write (No space left on device)
  No apport report written because the error message indicates a disk full error
                                                                                dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
  Examining /etc/kernel/postrm.d .
  run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
  run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
  Errors were encountered while processing:
   /var/cache/apt/archives/linux-image-4.4.0-89-generic_4.4.0-89.112_i386.deb
   /var/cache/apt/archives/linux-image-4.4.0-75-generic_4.4.0-75.96_i386.deb
   /var/cache/apt/archives/linux-image-4.4.0-87-generic_4.4.0-87.110_i386.deb
  E: Sub-process /usr/bin/dpkg returned an error code (1)
```
   
  I then do: df -H and get:

```

  Filesystem                          Size  Used Avail Use% Mounted on
  udev                                2.1G     0  2.1G   0% /dev
  tmpfs                               423M  6.4M  417M   2% /run
  /dev/mapper/pluto--server--vg-root  232G  5.7G  214G   3% /
  tmpfs                               2.2G     0  2.2G   0% /dev/shm
  tmpfs                               5.3M     0  5.3M   0% /run/lock
  tmpfs                               2.2G     0  2.2G   0% /sys/fs/cgroup
  /dev/sda1                           495M  491M     0 100% /boot
  tmpfs                               423M     0  423M   0% run/user/1000
```
   
  I am not sure I know what all this is telling me &#8211; sda1 which is mounted /boot has zero space??? (why?)

  And what is /dev/mapper/pluto have  232GB and only 5.7GB used but agt-get says disk is full?  I am very confused at all of this &#8211; any suggestions? Explanations?
  Thanks,
  J

---

### Post by QIII on 2017-08-07
Hello!

Please use the default font.  Also enclose all commands and output in code tags.  Please also include ALL output associated with their commands.  A partial list may leave out important details.

You may do one of the following:

1.  Click the # button above the text entry box, place your cursor between the code tags that appear and type or paste your text.

2.  Type or paste your text, highlight it and press the # button.

3.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text.  The square brackets are required.

---

### Post by ubfan1 on 2017-08-07
What filled up is the boot partition, /dev/sda1, which is mounted at /boot.    You need to get rid of some old kernels, which will be made difficult by the lack of disk space, and you have uninstalled kernels queued up to install as soon as you make some room. There are lots of answered questions at askubuntu.com and threads here on "/boot full", take a look around.

---

### Post by vocx on 2017-08-07
> **jjhudak said:**
> ...
I then do: df -H and get:

```

  Filesystem                          Size  Used Avail Use% Mounted on
  udev                                2.1G     0  2.1G   0% /dev
  tmpfs                               423M  6.4M  417M   2% /run
  /dev/mapper/pluto--server--vg-root  232G  5.7G  214G   3% /
  tmpfs                               2.2G     0  2.2G   0% /dev/shm
  tmpfs                               5.3M     0  5.3M   0% /run/lock
  tmpfs                               2.2G     0  2.2G   0% /sys/fs/cgroup
  /dev/sda1                           495M  491M     0 100% /boot
  tmpfs                               423M     0  423M   0% run/user/1000
```
   
  I am not sure I know what all this is telling me – sda1 which is mounted /boot has zero space??? (why?)

  And what is /dev/mapper/pluto have  232GB and only 5.7GB used but agt-get says disk is full?  I am very confused at all of this – any suggestions? Explanations?
  Thanks,
  J
Is that the entire output? I find it strange that you only seem to have one physical partition, "/dev/sda1", which corresponds to "/boot". Maybe you are using something like a LVM to manage your root folder, that is, "/". I don't know because I haven't used that before, but that is not a problem itself.

Running out of space in "/boot" is a common problem lately, and it occurs because you update continuously but don't remove the old kernels. Each kernel takes around 50 MB, so after 10 kernel upgrades you fill around 500 MB of space in "/boot". It seems many users follow a standard system installation that creates a small "/boot" partition, and it ends up filling up.

See other threads with the solutions:
[https://ubuntuforums.org/showthread.php?t=2368028&p=13673328#post13673328](https://ubuntuforums.org/showthread.php?t=2368028&p=13673328#post13673328)
[https://ubuntuforums.org/showthread.php?t=2367547&p=13671564#post13671564](https://ubuntuforums.org/showthread.php?t=2367547&p=13671564#post13671564)

My solution is to try to "apt purge" or "dpkg -P" old kernels that you are currently not using. If that procedure fails, you can "rm" the old kernels manually. You just need to liberate enough space in "/boot" so that further installations and updates with the "apt" command succeed. Once this is done, you can go back and cleanly "sudo apt purge" the old kernels.
```

# check which kernels are installed, they will have a "ii"
dpkg -l linux-image*

# try to purge the old kernels that you don't currently use
sudo apt purge linux-image-4.4.0-66-generic
sudo dpkg -P linux-image-4.4.0-66-generic

# if that fails use the brute force method
sudo rm /boot/vmlinuz-4.4.0-66-generic
sudo rm /boot/initrd.img-4.4.0-66-generic
sudo rm /boot/abi-4.4.0-66-generic

# be careful!
# don't remove the kernel that you are currently using, double check
uname -r

# if apt doesn't show more errors about "/boot", clean the old packages
sudo apt autoremove

# keep your system updated
sudo apt update
sudo apt upgrade

```

---

### Post by jjhudak on 2017-08-07
Thank you for the reply....now I understand a bit more.  I didn't realize I had to manually remove older kernels.  I tried "apt purge" and "dpkg -P" but no joy.  So I figured  that I should do manual purges....First see what kernel(s) I am not using...

```

jjh@pluto-server:~$ dpkg -l linux-image*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                          Version             Architecture        Description
+++-=============================-===================-===================-================================================================
un  linux-image                   <none>              <none>              (no description available)
ii  linux-image-4.4.0-31-generic  4.4.0-31.50         i386                Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-57-generic  4.4.0-57.78         i386                Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-59-generic  4.4.0-59.80         i386                Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-62-generic  4.4.0-62.83         i386                Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-64-generic  4.4.0-64.85         i386                Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-65-generic  4.4.0-65.86         i386                Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-66-generic  4.4.0-66.87         i386                Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-70-generic  4.4.0-70.91         i386                Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-71-generic  4.4.0-71.92         i386                Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-72-generic  4.4.0-72.93         i386                Linux kernel image for version 4.4.0 on 32 bit x86 SMP
in  linux-image-4.4.0-75-generic  <none>              i386                (no description available)
in  linux-image-4.4.0-87-generic  <none>              i386                (no description available)
in  linux-image-4.4.0-89-generic  <none>              i386                (no description available)
ii  linux-image-extra-4.4.0-31-ge 4.4.0-31.50         i386                Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-57-ge 4.4.0-57.78         i386                Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-59-ge 4.4.0-59.80         i386                Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-62-ge 4.4.0-62.83         i386                Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-64-ge 4.4.0-64.85         i386                Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-65-ge 4.4.0-65.86         i386                Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-66-ge 4.4.0-66.87         i386                Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-70-ge 4.4.0-70.91         i386                Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-71-ge 4.4.0-71.92         i386                Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
iF  linux-image-extra-4.4.0-72-ge 4.4.0-72.93         i386                Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
iU  linux-image-extra-4.4.0-75-ge 4.4.0-75.96         i386                Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
iU  linux-image-extra-4.4.0-87-ge 4.4.0-87.110        i386                Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
iU  linux-image-extra-4.4.0-89-ge 4.4.0-89.112        i386                Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
iU  linux-image-generic           4.4.0.89.95         i386                Generic Linux kernel image
jjh@pluto-server:~$



```
Since this is new territory for me, I'll ask for some assistance in reading this table...How do I know which kernel(s) I should remove?
What is the CL to remove them?
Is there any particular order for removal?
Thanks
J

---

### Post by vocx on 2017-08-08
> **jjhudak said:**
> Thank you for the reply....now I understand a bit more.  I didn't realize I had to manually remove older kernels.  I tried "apt purge" and "dpkg -P" but no joy.  So I figured  that I should do manual purges....First see what kernel(s) I am not using...

```

||/ Name                          Version             Architecture        Description
+++-=============================-===================-===================-================================================================
un  linux-image                   <none>              <none>              (no description available)
ii  linux-image-4.4.0-31-generic  4.4.0-31.50         i386                Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-57-generic  4.4.0-57.78         i386                Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-59-generic  4.4.0-59.80         i386                Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-62-generic  4.4.0-62.83         i386                Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-64-generic  4.4.0-64.85         i386                Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-65-generic  4.4.0-65.86         i386                Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-66-generic  4.4.0-66.87         i386                Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-70-generic  4.4.0-70.91         i386                Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-71-generic  4.4.0-71.92         i386                Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-72-generic  4.4.0-72.93         i386                Linux kernel image for version 4.4.0 on 32 bit x86 SMP
in  linux-image-4.4.0-75-generic  <none>              i386                (no description available)
in  linux-image-4.4.0-87-generic  <none>              i386                (no description available)
in  linux-image-4.4.0-89-generic  <none>              i386                (no description available)

```
Since this is new territory for me, I'll ask for some assistance in reading this table...How do I know which kernel(s) I should remove?
What is the CL to remove them?
Is there any particular order for removal?
Thanks
J
As I said in my previous post, those that have "ii" at the beginning are installed. The kernel version is the number 4.4.0-31, for example. The higher the number the more recent the kernel is, so 4.4.0-72 is more recent than 4.4.0-31.

Which kernels should you remove? Typically, the older ones. So, you should remove 4.4.0-31, -57, -59, etc., before -70, -71, -72, etc.

Normally you should be using the newest kernel. For 16.04 versions of Ubuntu the latest kernel should be 4.4.0-89, however, the output you provided indicates that the last three kernels, -75, -87, -89 are not installed. Maybe your system tried to install them but since your "/boot" is full, the operation failed.

Then, probably the kernel that you are currently using is the next one in line, 4.4.0-72. As mentioned in my previous post, check this with the "uname" command.
```

uname -r

```
You should not delete this kernel, as this is the one you currently use. You may delete the older kernels to free space in "/boot".
```

sudo dpkg -P linux-image-4.4.0-31-generic
sudo dpkg -P linux-image-4.4.0-57-generic
sudo dpkg -P linux-image-4.4.0-59-generic
sudo dpkg -P linux-image-4.4.0-62-generic

```
If this operation fails, then you may use the brute force approach.
```

sudo rm /boot/initrd.img-4.4.0-31-generic

sudo rm /boot/initrd.img-4.4.0-57-generic

sudo rm /boot/initrd.img-4.4.0-59-generic

```

You can check the exact names of the kernels by listing the contents of the "/boot" directory.
```

ls -alh /boot

```

Try removing only one kernel at first, the oldest one. Then try running the "apt" commands, such as "apt purge", or "apt autoremove". If they still fail because of lack of space in "/boot", then try removing another kernel, and so on. As I said in the previous post, you need to free enough space in "/boot" so that "apt" doesn't fail any more. Once "apt" doesn't fail, you can "apt autoremove" to cleanly remove the old kernels.

It seems you are currently using the 4.4.0-72 kernel. When you free space in "/boot", the system will probably want to install the newer kernels, -75, -87, -89. So even if you remove some space at first, you may actually end up with a full "/boot" again. So, you should keep removing older kernels, until you have enough space.

Obviously, if you manage to install 4.4.0-89 correctly, you should reboot, and boot with that kernel, and then you will be using the newest kernel for the system. Only then you should be able to remove the older 4.4.0-72 version.

---

### Post by ubfan1 on 2017-08-08
If you actually use a "rm" command, better to then use the "sudo touch <the file you removed>"  to leave a zero length file of the same name, to keep the package manager happy when it finally gets around to purging the unwanted packages.

---

### Post by #&amp;thj^% on 2017-08-08
> **ubfan1 said:**
> If you actually use a "rm" command,**_ better to then use the "sudo touch <the file you removed>"  to leave a zero length file of the same name_**, to keep the package manager happy when it finally gets around to purging the unwanted packages.
+100 good point :D
>  A FILE argument that does not exist is created empty, unless -c  or  -h
       is supplied.


---

### Post by jjhudak on 2017-08-08
Thank you!  I followed your guidance and have made progress, perhaps even with some success!   
I had to forceably remove -31,57,59,62,64,65,66,70, 71 and 72.
I tried to remove -75,87, and 89 but got "no such file or directory"
so then I tried apt purge and apt purge -f with no success, complaining about 75,87, and 89.

I then issued
```

dpkg -P

```
and it went through and fixed the kernel structure, removing 2+GB of old files.
Then it told me there were some damaged links......which I think I fixed by running update grub (but if IRC, grub would have been updated by the package manager?  anyway if it was fixed, refixing it should do no harm....

```

The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old
 you may need to re-run your boot loader[grub]
jjh@pluto-server:~$ dpkg -l linux-image*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                    Version          Architecture     Description
+++-=======================-================-================-====================================================
un  linux-image             <none>           <none>           (no description available)
rc  linux-image-4.4.0-31-ge 4.4.0-31.50      i386             Linux kernel image for version 4.4.0 on 32 bit x86 S
rc  linux-image-4.4.0-57-ge 4.4.0-57.78      i386             Linux kernel image for version 4.4.0 on 32 bit x86 S
rc  linux-image-4.4.0-59-ge 4.4.0-59.80      i386             Linux kernel image for version 4.4.0 on 32 bit x86 S
rc  linux-image-4.4.0-62-ge 4.4.0-62.83      i386             Linux kernel image for version 4.4.0 on 32 bit x86 S
rc  linux-image-4.4.0-64-ge 4.4.0-64.85      i386             Linux kernel image for version 4.4.0 on 32 bit x86 S
rc  linux-image-4.4.0-65-ge 4.4.0-65.86      i386             Linux kernel image for version 4.4.0 on 32 bit x86 S
rc  linux-image-4.4.0-66-ge 4.4.0-66.87      i386             Linux kernel image for version 4.4.0 on 32 bit x86 S
rc  linux-image-4.4.0-70-ge 4.4.0-70.91      i386             Linux kernel image for version 4.4.0 on 32 bit x86 S
rc  linux-image-4.4.0-71-ge 4.4.0-71.92      i386             Linux kernel image for version 4.4.0 on 32 bit x86 S
ii  linux-image-4.4.0-72-ge 4.4.0-72.93      i386             Linux kernel image for version 4.4.0 on 32 bit x86 S
rc  linux-image-4.4.0-75-ge 4.4.0-75.96      i386             Linux kernel image for version 4.4.0 on 32 bit x86 S
ii  linux-image-4.4.0-87-ge 4.4.0-87.110     i386             Linux kernel image for version 4.4.0 on 32 bit x86 S
ii  linux-image-4.4.0-89-ge 4.4.0-89.112     i386             Linux kernel image for version 4.4.0 on 32 bit x86 S
rc  linux-image-extra-4.4.0 4.4.0-31.50      i386             Linux kernel extra modules for version 4.4.0 on 32 b
rc  linux-image-extra-4.4.0 4.4.0-57.78      i386             Linux kernel extra modules for version 4.4.0 on 32 b
rc  linux-image-extra-4.4.0 4.4.0-59.80      i386             Linux kernel extra modules for version 4.4.0 on 32 b
rc  linux-image-extra-4.4.0 4.4.0-62.83      i386             Linux kernel extra modules for version 4.4.0 on 32 b
rc  linux-image-extra-4.4.0 4.4.0-64.85      i386             Linux kernel extra modules for version 4.4.0 on 32 b
rc  linux-image-extra-4.4.0 4.4.0-65.86      i386             Linux kernel extra modules for version 4.4.0 on 32 b
rc  linux-image-extra-4.4.0 4.4.0-66.87      i386             Linux kernel extra modules for version 4.4.0 on 32 b
rc  linux-image-extra-4.4.0 4.4.0-70.91      i386             Linux kernel extra modules for version 4.4.0 on 32 b
rc  linux-image-extra-4.4.0 4.4.0-71.92      i386             Linux kernel extra modules for version 4.4.0 on 32 b
ii  linux-image-extra-4.4.0 4.4.0-72.93      i386             Linux kernel extra modules for version 4.4.0 on 32 b
rc  linux-image-extra-4.4.0 4.4.0-75.96      i386             Linux kernel extra modules for version 4.4.0 on 32 b
ii  linux-image-extra-4.4.0 4.4.0-87.110     i386             Linux kernel extra modules for version 4.4.0 on 32 b
ii  linux-image-extra-4.4.0 4.4.0-89.112     i386             Linux kernel extra modules for version 4.4.0 on 32 b
ii  linux-image-generic     4.4.0.89.95      i386             Generic Linux kernel image
jjh@pluto-server:~$
jjh@pluto-server:~$ uname -r
4.4.0-72-generic
jjh@pluto-server:~$
jjh@pluto-server:~$ sudo update-grub
[sudo] password for jjh:
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-89-generic
Found initrd image: /boot/initrd.img-4.4.0-89-generic
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found initrd image: /boot/initrd.img-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-72-generic
Found initrd image: /boot/initrd.img-4.4.0-72-generic
done
jjh@pluto-server:~$

```

So now I have to ask for more guidance...As I read the table, I have a number of kernels installed but run -72. 
I rebooted the machine now it is running a different kernel...
```

jjh@pluto-server:~$ uname -r
4.4.0-89-generic

```


There are also a number of kernels designated 'rc'.
So what should I do now?   I'd like to keep 2-3 recent kernels but run the most recent one.  What is the best way to proceed?
You help so far has been invaluable...ty!

forgot to add:
```

jjh@pluto-server:~$ df -H
Filesystem                          Size  Used Avail Use% Mounted on
udev                                2.1G     0  2.1G   0% /dev
tmpfs                               423M  6.3M  417M   2% /run
/dev/mapper/pluto--server--vg-root  232G  2.9G  217G   2% /
tmpfs                               2.2G     0  2.2G   0% /dev/shm
tmpfs                               5.3M     0  5.3M   0% /run/lock
tmpfs                               2.2G     0  2.2G   0% /sys/fs/cgroup
/dev/sda1                           495M  154M  316M  33% /boot
tmpfs                               423M     0  423M   0% /run/user/1000
jjh@pluto-server:~$

```

So the boot directory has been cleaned by about 33%...but the structure looks strange..e.g. one physical partition sda1 that corresponds to boot seems weird...IIRC, during the install, I pretty much just accepted the defaults...(anyway, thats another thread).  I just want to get my boot directory disk space under control...
J

---

### Post by vocx on 2017-08-08
> **jjhudak said:**
> Thank you!  I followed your guidance and have made progress, perhaps even with some success!   
**I had to forceably remove -31,57,59,62,64,65,66,70, 71 and 72.**
I tried to remove -75,87, and 89 but got "no such file or directory"
so then I tried apt purge and apt purge -f with no success, complaining about 75,87, and 89.


I repeat, **you should not attempt to remove the kernel you are currently using**. If you remove the kernel you are currently using, and then reboot, you may end up without a kernel, and thus unable to boot and use your machine.

According to what you wrote above, you tried to remove the -72 kernel. Apparently you were also running that kernel. Why did you try removing that kernel, when I told you to no do it? Why?

> 
I then issued
    Code:
```

dpkg -P

```

and it went through and fixed the kernel structure, removing 2+GB of old files.
Then it told me there were some damaged links......which I think I fixed by running update grub (but if IRC, grub would have been updated by the package manager?  anyway if it was fixed, refixing it should do no harm....

The fact that it cleared 2 GB of data means you had a lot of clutter (old packages) in your system. You need to pay more attention to your system and not let it sit there accumulating garbage.

> 
```

The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old
 you may need to re-run your boot loader[grub]

```

These broken links are not a big issue, as long as you can free the space in "/boot", so "apt" runs okay, they will be automatically fixed when the new kernels install correctly, which you seemingly did.

> 
```

ii  linux-image-4.4.0-72-ge 4.4.0-72.93      i386             Linux kernel image for version 4.4.0 on 32 bit x86 S
ii  linux-image-4.4.0-87-ge 4.4.0-87.110     i386             Linux kernel image for version 4.4.0 on 32 bit x86 S
ii  linux-image-4.4.0-89-ge 4.4.0-89.112     i386             Linux kernel image for version 4.4.0 on 32 bit x86 S

```
...

So now I have to ask for more guidance...As I read the table, I have a number of kernels installed but run -72. 
I rebooted the machine now it is running a different kernel...
```

jjh@pluto-server:~$ uname -r
4.4.0-89-generic

```


There are also a number of kernels designated 'rc'.
So what should I do now?   I'd like to keep 2-3 recent kernels but run the most recent one.  What is the best way to proceed?
You help so far has been invaluable...ty!


As I mentioned in the previous posts, the kernels starting with "ii" in the table are installed, the rest are not installed, and therefore they are not of concern to you. They don't take space in your system. The package manager is intelligent enough to keep track of the different kernels available in the repositories, so it shows you which are installed and which are not.

Since you have -72, -87, and -89, and you are running the latter after the reboot, you are already running the newest kernel, and already have two back up kernels.

In the future you will probably get further kernel updates, say, for -93. When this happens, you will accept the install, and after the install a message will say "the following packages (the old kernel packges) were automatically installed, you can remove them with apt autoremove". So, you should do that at that time.
```

sudo apt autoremove

```
This will guarantee that you have the most recent kernel and two backup kernels, and if there is an older one, it will be removed, thus making sure your "/boot" has enough free space.

> 
forgot to add:
```

jjh@pluto-server:~$ df -H
Filesystem                          Size  Used Avail Use% Mounted on
udev                                2.1G     0  2.1G   0% /dev
tmpfs                               423M  6.3M  417M   2% /run
/dev/mapper/pluto--server--vg-root  232G  2.9G  217G   2% /
tmpfs                               2.2G     0  2.2G   0% /dev/shm
tmpfs                               5.3M     0  5.3M   0% /run/lock
tmpfs                               2.2G     0  2.2G   0% /sys/fs/cgroup
/dev/sda1                           495M  154M  316M  33% /boot
tmpfs                               423M     0  423M   0% /run/user/1000
jjh@pluto-server:~$

```

So the boot directory has been cleaned by about 33%...but the structure looks strange..e.g. one physical partition sda1 that corresponds to boot seems weird...IIRC, during the install, I pretty much just accepted the defaults...(anyway, thats another thread).  I just want to get my boot directory disk space under control...
J
Your system looks fine.

If you just accepted the defaults the system probably created some sort of logical volume manager (LVM), or set up encryption of your hard drive. That is why you see the "/dev/mapper/..." line there for your root "/" mount point, and the small "/boot" partition. The "/boot" partition was required in the past so you could boot your system and then, in a separate step, decrypt your main "/" directory. I think this is not required nowadays. See here [https://unix.stackexchange.com/questions/256/is-it-good-to-make-a-separate-partition-for-boot](https://unix.stackexchange.com/questions/256/is-it-good-to-make-a-separate-partition-for-boot)

The only way to change that would be to reinstall the system and manually change the options of the installer so that "/boot" is larger, or not created separately, or your main partition is not encrypted, or so on. You can change the options during install as you see fit. However, reinstalling means your data will be erased and you have to start from scratch setting your system, so you probably don't want that. If you want just backup your data and reinstall, otherwise, since you don't seem particularly experienced with Linux, you can just leave it like that and it should be fine.

In summary, I think you were extremely lucky by deleting the running kernel. You installed a new kernel, and thus upon reboot you were running a newer kernel, so there was no problem. In the future, please don't be reckless, and please follow instructions.

Keep your system in good shape and up to date by running regularly.
```

sudo apt update
sudo apt upgrade
sudo apt autoremove

```

---

### Post by jjhudak on 2017-08-09
Thanks again for the feedback.  I actually mistyped the list....I wrote down the versions I deleted and I also noted I was running version 72.  When I wrote the description above, I mistakenly wrote that I removed 72 when I really should have written I was running 72.  Sorry about the confusion...and yes, I did read and follow what you said.
 
You are somewhat correct...I am a linux novice when it comes to this aspect of the OS.  I do (and teach) embedded system design (digital logic/FPGA and sw) and control theory. Back in the day, I did hard disk controller design and wrote drivers under UNIX V6,V7BSD and RT11. Things have changed a bit, and I've forgotten much more.  In any case, can you point me to a  good description of care and feeding of ubuntu kernels and management?  (yes, I've read some of the ubuntu guides and man pages but translating that to efficient/correct maintenance is not always clear.
Thanks again and best regards,
J

---

### Post by vocx on 2017-08-09
> **jjhudak said:**
> Thanks again for the feedback.  I actually mistyped the list....I wrote down the versions I deleted and I also noted I was running version 72.  When I wrote the description above, I mistakenly wrote that I removed 72 when I really should have written I was running 72.  Sorry about the confusion...and yes, I did read and follow what you said.

So you did not actually remove it?! That's great. I was having a bit of a stroke after reading that.

> 
You are somewhat correct...I am a linux novice when it comes to this aspect of the OS.  I do (and teach) embedded system design (digital logic/FPGA and sw) and control theory. Back in the day, I did hard disk controller design and wrote drivers under UNIX V6,V7BSD and RT11. Things have changed a bit, and I've forgotten much more.  In any case, can you point me to a  good description of care and feeding of ubuntu kernels and management?  (yes, I've read some of the ubuntu guides and man pages but translating that to efficient/correct maintenance is not always clear.
Thanks again and best regards,
J
There is no particular guide you should follow to "manage" the kernels. It's rather simple actually. Whenever I turn on my computer, I run two commands
```

sudo apt update
sudo apt upgrade

```
That's it. Next day, same, and the day after that, same, and after that, same, etc. Basically, just keep your system regularly updated. Running the commands once per week is also fine.

And you want to run them manually and pay attention to the terminal output in case it tells you something important.

As I mentioned before, sometimes it tells you to run "autoremove" to remove unnecessary packages. So you just do that.
```

sudo apt autoremove

```

---

### Post by jjhudak on 2017-08-10
The issue appears to be resolved, /boot has over 3 GB free and system seems to be running fine, no issues in the sys error logs, and the services I've installed seem to be working.  On to other dragons to slay...
I do appreciate your help in this, especially following thorugh since the first post.
Best,
J

---

### Post by vocx on 2017-08-10
> **jjhudak said:**
> The issue appears to be resolved, /boot has over 3 GB free and system seems to be running fine, no issues in the sys error logs, and the services I've installed seem to be working.  On to other dragons to slay...
I do appreciate your help in this, especially following thorugh since the first post.
Best,
J

According to your output, your "/boot" is 495 MB in size, so you cannot have 3 GB of free space there. You should really confirm this so you don't run into the surprise that you are out of space again, thinking you have more space than you actually have. Maybe you meant you liberated 3 GB of old files in total. Most files are not installed in "/boot", but in "/usr", and "/var".

> **jjhudak said:**
> 
  I then do: df -H and get:

```

  Filesystem                          Size  Used Avail Use% Mounted on
  udev                                2.1G     0  2.1G   0% /dev
  tmpfs                               423M  6.4M  417M   2% /run
  /dev/mapper/pluto--server--vg-root  232G  5.7G  214G   3% /
  tmpfs                               2.2G     0  2.2G   0% /dev/shm
  tmpfs                               5.3M     0  5.3M   0% /run/lock
  tmpfs                               2.2G     0  2.2G   0% /sys/fs/cgroup
 ** /dev/sda1                           495M  491M     0 100% /boot**
  tmpfs                               423M     0  423M   0% run/user/1000
```
   

---

