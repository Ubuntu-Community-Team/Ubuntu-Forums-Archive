---
title: "Kubuntu, deleted all Kernels - now no boot"
date: 2016-10-19
forum: Installation &amp; Upgrades
---

### Post by jaak39 on 2016-10-19
Hello,

any help with this problem is appreciated.

Delete all Kernels on Kubuntu 16.04, now grub 2 only shows "windwos 10" as an boot-option.

This tips are already tried, but at some point there are erros and progress is halted.
[http://askubuntu.com/questions/254491/failed-to-get-canonical-path-of-cow](http://askubuntu.com/questions/254491/failed-to-get-canonical-path-of-cow)
[http://askubuntu.com/questions/140254/how-to-install-newer-versions-of-the-linux-kernel](http://askubuntu.com/questions/140254/how-to-install-newer-versions-of-the-linux-kernel)
[http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels](http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels)

Ubuntu live is started from an usb-device.

When "fdisk -l" is being executed, it displays:
[[IMG]http://www2.pic-upload.de/thumb/31937958/new1.png[/IMG]]("http://www.pic-upload.de/view-31937958/new1.png.html")

Disk /dev/sda: 111.8 GiB is where Kubuntu is installed.

Executing "sudo df -h" shows:
[[IMG]http://www2.pic-upload.de/thumb/31937989/new2.png[/IMG]]("http://www.pic-upload.de/view-31937989/new2.png.html")

Someone told that " / " is where ther Kernels are in. In this case the filesystem is /cow.
Actually I never heard of /cow and dont know where to find this on the harddisk.

I think "/dev/sda3 is /media/kubuntu/499b0ce6-94c2-44ab-9232-9ca98e93313d/" the 18,6 GiB Hard Drive
/dev/sda3        19G  1.2G   17G   7% /mnt
[[IMG]http://www2.pic-upload.de/thumb/31938190/new3.png[/IMG]]("http://www.pic-upload.de/view-31938190/new3.png.html")




So I tried the usual commands found:
sudo mount /dev/sda3 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys

sudo chroot /mnt

Whenever I put "sudo chroot /mnt", the line changes from "kubuntu@kubuntu:~$" to "root@kubuntu:/#".
Additonally it displays "bash: groups: command not found"
So Im stuck and cant use "sudo" "apt-get" etc. (bash: sudo: command not found)

So I really dont know what to do. Why I cant use sudo, what is this "~/.bash_profile" and where I need to install this Kernel.
Id like to install the new 4.8.2.

If I just type "apt-get install linux-image-generic" in the  "kubuntu@kubuntu:~$ " -line, it displays at the end "/usr/sbin/grub-probe: error: failed to get canonical path of `/cow'."

:confused: :frown: ](*,)

---

### Post by deadflowr on 2016-10-20
You don't need sudo in a chroot environment, as you are doing what sudo is designed to do, run as root.
And a chroot is always running as root.

Just run the commands in the root@kubuntu# chroot environment without sudo.

---

### Post by sisco311 on 2016-10-20
It seems to me that you need to set the PATH environment variable in the chroot:
```
export PATH=/usr/sbin:/usr/bin:/sbin:/bin
```
or you have to use the full path to the commands
```
/usr/bin/apt-get update
...
```

It is also advisable to do a "bind" /dev/pts in order to prevent error messages like:   *Must be connected to a terminal* or *Can not access '/dev/pts/0*
```
sudo mount --bind /dev/pts /mnt/dev/pts
```

---

### Post by jaak39 on 2016-10-23
Thanks for the answers.

"Sudo" isn't used anymore.

Now I tried the commands as mentioned above, but changed "sudo mount --bind /dev /mnt/dev" to "sudo mount --bind /dev/pts /mnt/dev/pts".
In the chroot environement I executed "export PATH=/usr/sbin:/usr/bin:/sbin:/bin" - there was no error or message shown, just a new blank line began " root@kubuntu:/# "

Using "/usr/bin/apt-get update", I get the message "bash: /usr/bin/apt-get: No such file or directory".

So from "(bash: apt-get: command not found)", now I get  "bash: /usr/bin/apt/get: No such file or directory".
:confused:

---

