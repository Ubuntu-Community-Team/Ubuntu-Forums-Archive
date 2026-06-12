---
title: "Not enough space to update/upgrade"
date: 2015-07-28
forum: Installation &amp; Upgrades
---

### Post by Rolandl on 2015-07-28
Can't find how to start a new thread so will try here. 
Now my boot partition has only 1% free space and it's not taking kernel updates.
What can I do? 

There's a suggestion to  '[COLOR=#333333][FONT=monospace]Remove unused kernels using computer janitor or manually free space on your partition containing the /boot file system' But I can't find it.[/FONT][/COLOR]

---

### Post by bapoumba on 2015-07-28
Post moved to its own thread and title changed.
Please post the output to 
```
uname -r
dpkg --list | grep linux-image
```
First one will tell you which kernel you are running on, the second all the installed kernels. The idea is to remove all but the one you are using (of course) and maybe the one before that with the following command :
```
dpkg -P linux-image-<version>
```

---

### Post by tomasrey88 on 2015-07-28
If no space on HD, do full install on USB. 
Boot from disc. Plug in USB. Note what drive it is in. (sdf ?) Usually, the HD is sda.
Click "install"
Do not click on "format HD and install." Click on "Other Installation" instead.
Format your USB, ext4+/+format 12GB, ext4+home+format XGB, swap+format YGB
XGB = the anticipated space you'll need to save your files
YGB = the same as your RAM if <2GB, if more then it is 2GB. Some sources suggest 1.5 x your RAM. Really old computers may need 2 x RAM. 
Install. voila! 

shameless plug: 
please answer my question. thanks
[http://ubuntuforums.org/showthread.php?t=2288606](http://ubuntuforums.org/showthread.php?t=2288606)

---

### Post by bapoumba on 2015-07-28
Why recommending to install on an usb drive when it could be that bug ?
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)

---

### Post by Rolandl on 2015-07-28
I did what bapoumba suggested and first two codes worked but 3rd one: 
[COLOR=#000000]Code:[/COLOR]
dpkg -P linux-image-<version> 

this came up:   'bash: syntax error near unexpected token `newline'

---

### Post by oldfred on 2015-07-28
The <version> is supposed to be the exact version of the kernel you showed with previous command. If you run with the literal <version> you get that error.
 
I prefer to use synaptic, but if you cannot run updates, then you probably cannot install it.
       Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# kernels, shows older also?
dpkg --list | grep linux-image
sudo apt-get -s autoremove
# one line purge
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
I prefer synatic and keeping 2 kernels, current and one known working older on.
[http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu](http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu)

---

### Post by bapoumba on 2015-07-29
This one liner from CharlesA is the one I used to use : [http://ubuntuforums.org/showthread.php?t=1658648&p=11075299#post11075299](http://ubuntuforums.org/showthread.php?t=1658648&p=11075299#post11075299)
Now I purge on a regular basis.

@Rolandl : if you paste the outputs of the first two commands, we can walk you through with the third one :)

---

### Post by Rolandl on 2015-07-30
Am having same issue. "a program error". Master Boot Record shows the Boot partition is 99.2 % full. What can I do? Can I somehow make the partition larger to take more data? Thank you.

I just now restarted and this came up: 'The volume boot has only 0 bytes disk space remaining.'
It suggests I can move files to another disk or partition. What to do?

Also, I have several times 'reported the problem'. Does that really help? I haven't received any info from anyone about it.

---

### Post by bab1 on 2015-07-30
> **Rolandl said:**
> I just now restarted and this came up: 'The volume boot has only 0 bytes disk space remaining.'
It suggests I can move files to another disk or partition. What to do?

Also, I have several times 'reported the problem'. Does that really help? I haven't received any info from anyone about it.

What is in /boot?  Post the output of ```
ls -l /boot
```

Edit:  It will also help to see the output of this```

df -h | grep sd
```

---

### Post by Rolandl on 2015-07-30
```
total 230157
-rw-r--r-- 1 root root  1269284 May 19 12:45 abi-3.19.0-18-generic
-rw-r--r-- 1 root root  1269462 May 29 04:02 abi-3.19.0-20-generic
-rw-r--r-- 1 root root  1269462 Jun 14 12:44 abi-3.19.0-21-generic
-rw-r--r-- 1 root root  1269462 Jun 16 11:30 abi-3.19.0-22-generic
-rw-r--r-- 1 root root  1270417 Jul  7 13:05 abi-3.19.0-23-generic
-rw-r--r-- 1 root root  1270417 Jul 22 13:14 abi-3.19.0-24-generic
-rw-r--r-- 1 root root  1270417 Jul 24 16:35 abi-3.19.0-25-generic
-rw-r--r-- 1 root root   177700 May 19 12:45 config-3.19.0-18-generic
-rw-r--r-- 1 root root   177700 May 29 04:02 config-3.19.0-20-generic
-rw-r--r-- 1 root root   177700 Jun 14 12:44 config-3.19.0-21-generic
-rw-r--r-- 1 root root   177705 Jun 16 11:30 config-3.19.0-22-generic
-rw-r--r-- 1 root root   177771 Jul  7 13:05 config-3.19.0-23-generic
-rw-r--r-- 1 root root   177771 Jul 22 13:14 config-3.19.0-24-generic
-rw-r--r-- 1 root root   177771 Jul 24 16:35 config-3.19.0-25-generic
drwxr-xr-x 5 root root     1024 Jul 28 07:34 grub
-rw-r--r-- 1 root root 21774621 May 31 10:04 initrd.img-3.19.0-18-generic
-rw-r--r-- 1 root root 21774853 Jun 15 13:08 initrd.img-3.19.0-20-generic
-rw-r--r-- 1 root root 21769753 Jun 17 10:12 initrd.img-3.19.0-21-generic
-rw-r--r-- 1 root root 21772029 Jun 24 19:17 initrd.img-3.19.0-22-generic
-rw-r--r-- 1 root root 21778367 Jul 10 11:17 initrd.img-3.19.0-23-generic
-rw-r--r-- 1 root root 21778181 Jul 25 08:08 initrd.img-3.19.0-24-generic
-rw-r--r-- 1 root root 21774564 Jul 28 07:34 initrd.img-3.19.0-25-generic
drwx------ 2 root root    12288 May 31 09:02 lost+found
-rw-r--r-- 1 root root   164216 Mar  6 08:23 memtest86+.bin
-rw-r--r-- 1 root root   165892 Mar  6 08:23 memtest86+.elf
-rw-r--r-- 1 root root   166396 Mar  6 08:23 memtest86+_multiboot.bin
-rw------- 1 root root  3616263 May 19 12:45 System.map-3.19.0-18-generic
-rw------- 1 root root  3617303 May 29 04:02 System.map-3.19.0-20-generic
-rw------- 1 root root  3617303 Jun 14 12:44 System.map-3.19.0-21-generic
-rw------- 1 root root  3617446 Jun 16 11:30 System.map-3.19.0-22-generic
-rw------- 1 root root  3617597 Jul  7 13:05 System.map-3.19.0-23-generic
-rw------- 1 root root  3617597 Jul 22 13:14 System.map-3.19.0-24-generic
-rw------- 1 root root  3617653 Jul 24 16:35 System.map-3.19.0-25-generic
-rw------- 1 root root  6614144 May 19 12:45 vmlinuz-3.19.0-18-generic
-rw------- 1 root root  6616960 May 29 04:02 vmlinuz-3.19.0-20-generic
-rw------- 1 root root  6617408 Jun 14 12:44 vmlinuz-3.19.0-21-generic
-rw------- 1 root root  6616448 Jun 16 11:30 vmlinuz-3.19.0-22-generic
-rw------- 1 root root  6616320 Jul  7 13:05 vmlinuz-3.19.0-23-generic
-rw------- 1 root root  6616192 Jul 22 13:14 vmlinuz-3.19.0-24-generic
-rw------- 1 root root  6616704 Jul 24 16:35 vmlinuz-3.19.0-25-generic

```

To your second request:   /dev/sda1                    236M  234M     0 100% /boot

Does this help?

---

### Post by bab1 on 2015-07-30
> **Rolandl said:**
> ```
total 230157
-rw-r--r-- 1 root root  1269284 May 19 12:45 abi-3.19.0-18-generic
-rw-r--r-- 1 root root  1269462 May 29 04:02 abi-3.19.0-20-generic
-rw-r--r-- 1 root root  1269462 Jun 14 12:44 abi-3.19.0-21-generic
-rw-r--r-- 1 root root  1269462 Jun 16 11:30 abi-3.19.0-22-generic
-rw-r--r-- 1 root root  1270417 Jul  7 13:05 abi-3.19.0-23-generic
-rw-r--r-- 1 root root  1270417 Jul 22 13:14 abi-3.19.0-24-generic
-rw-r--r-- 1 root root  1270417 Jul 24 16:35 abi-3.19.0-25-generic
-rw-r--r-- 1 root root   177700 May 19 12:45 config-3.19.0-18-generic
-rw-r--r-- 1 root root   177700 May 29 04:02 config-3.19.0-20-generic
-rw-r--r-- 1 root root   177700 Jun 14 12:44 config-3.19.0-21-generic
-rw-r--r-- 1 root root   177705 Jun 16 11:30 config-3.19.0-22-generic
-rw-r--r-- 1 root root   177771 Jul  7 13:05 config-3.19.0-23-generic
-rw-r--r-- 1 root root   177771 Jul 22 13:14 config-3.19.0-24-generic
-rw-r--r-- 1 root root   177771 Jul 24 16:35 config-3.19.0-25-generic
drwxr-xr-x 5 root root     1024 Jul 28 07:34 grub
-rw-r--r-- 1 root root 21774621 May 31 10:04 initrd.img-3.19.0-18-generic
-rw-r--r-- 1 root root 21774853 Jun 15 13:08 initrd.img-3.19.0-20-generic
-rw-r--r-- 1 root root 21769753 Jun 17 10:12 initrd.img-3.19.0-21-generic
-rw-r--r-- 1 root root 21772029 Jun 24 19:17 initrd.img-3.19.0-22-generic
-rw-r--r-- 1 root root 21778367 Jul 10 11:17 initrd.img-3.19.0-23-generic
-rw-r--r-- 1 root root 21778181 Jul 25 08:08 initrd.img-3.19.0-24-generic
-rw-r--r-- 1 root root 21774564 Jul 28 07:34 initrd.img-3.19.0-25-generic
drwx------ 2 root root    12288 May 31 09:02 lost+found
-rw-r--r-- 1 root root   164216 Mar  6 08:23 memtest86+.bin
-rw-r--r-- 1 root root   165892 Mar  6 08:23 memtest86+.elf
-rw-r--r-- 1 root root   166396 Mar  6 08:23 memtest86+_multiboot.bin
-rw------- 1 root root  3616263 May 19 12:45 System.map-3.19.0-18-generic
-rw------- 1 root root  3617303 May 29 04:02 System.map-3.19.0-20-generic
-rw------- 1 root root  3617303 Jun 14 12:44 System.map-3.19.0-21-generic
-rw------- 1 root root  3617446 Jun 16 11:30 System.map-3.19.0-22-generic
-rw------- 1 root root  3617597 Jul  7 13:05 System.map-3.19.0-23-generic
-rw------- 1 root root  3617597 Jul 22 13:14 System.map-3.19.0-24-generic
-rw------- 1 root root  3617653 Jul 24 16:35 System.map-3.19.0-25-generic
-rw------- 1 root root  6614144 May 19 12:45 vmlinuz-3.19.0-18-generic
-rw------- 1 root root  6616960 May 29 04:02 vmlinuz-3.19.0-20-generic
-rw------- 1 root root  6617408 Jun 14 12:44 vmlinuz-3.19.0-21-generic
-rw------- 1 root root  6616448 Jun 16 11:30 vmlinuz-3.19.0-22-generic
-rw------- 1 root root  6616320 Jul  7 13:05 vmlinuz-3.19.0-23-generic
-rw------- 1 root root  6616192 Jul 22 13:14 vmlinuz-3.19.0-24-generic
-rw------- 1 root root  6616704 Jul 24 16:35 vmlinuz-3.19.0-25-generic
```

BOTH outputs please.  

When posting text please use [noparse]```

```[/noparse] code blocks.  The easiest way is to click on the [SIZE=6]**#**[/SIZE] icon at the top of the advanced editor that you use to reply and past the output between the code blocks.

---

### Post by bab1 on 2015-07-30
> **Rolandl said:**
> To your second request:   /dev/sda1                    236M  234M     0 100% /boot

Does this help?I need the output I requested.   So, once again, post the output of ```
df -h | grep sd
```

Using the code blocks of course.  ;-)

---

### Post by bapoumba on 2015-07-30
@Rolandl : moved your posts and bab1's replies to your original thread.

Can you please paste the outputs of the commands in post #2 ? Thanks.

---

### Post by Rolandl on 2015-07-30
Re: Just found a handy command:If you are using a recent version of Ubuntu, you have to run:

Code:
sudo update-grub
to remove the unsued kernel entries

 ***

I did that and this came up: 
```

Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found linux image: /boot/vmlinuz-3.19.0-24-generic
Found initrd image: /boot/initrd.img-3.19.0-24-generic
Found linux image: /boot/vmlinuz-3.19.0-23-generic
Found initrd image: /boot/initrd.img-3.19.0-23-generic
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-21-generic
Found initrd image: /boot/initrd.img-3.19.0-21-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done

```



Does this mean that Grub has updated the kernel and all should be ok now? or should I create more space in /boot? repartition?

---

### Post by bab1 on 2015-07-30
> **Rolandl said:**
> [h=2]Re: Just found a handy command:[/h][COLOR=#000000][INDENT]If you are using a recent version of Ubuntu, you have to run:

Code:
sudo update-grub
to remove the unsued kernel entries

 ***

I did that and this came up: 

Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found linux image: /boot/vmlinuz-3.19.0-24-generic
Found initrd image: /boot/initrd.img-3.19.0-24-generic
Found linux image: /boot/vmlinuz-3.19.0-23-generic
Found initrd image: /boot/initrd.img-3.19.0-23-generic
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-21-generic
Found initrd image: /boot/initrd.img-3.19.0-21-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done




Does this mean that Grub has updated the kernel and all should be ok now? or should I create more space in /boot? repartition?




[/INDENT]
[/COLOR]
Answer our questions and all will be revealed.  If you don't it would only be a guess.  I do not guess.

My own pet peeve is that folks don't follow simple instructions.  Such as using code blocks for text output.  Your excuse is....

---

### Post by PaulW2U on 2015-07-30
Rolandl, please use code tags for terminal output as they improve the readability of your posts by separating output from the main text and also preserve spacing.

If you are using New Reply button - highlight text and use the # button in the text box header. If you are using Quick Reply then add [noparse]```
 at the beginning of the section and 
```[/noparse] at the end.

Please help others to help you. :)

---

### Post by bapoumba on 2015-07-31
@Rolandl : from post #11, we can gather that you have kernels 3.19.0-18, 20, 21, 22, 23, 24 and 25 installed.
We still do not know which kernel you are running on, or if you have cleared space on /boot or not.

As to what update-grub does, you can have a look here for ex : [http://manpages.ubuntu.com/manpages/raring/man8/update-grub.8.html](http://manpages.ubuntu.com/manpages/raring/man8/update-grub.8.html)
Basically, it looks at installed kernels and lists them in a file for you to boot on them. It does not remove anything, it does not clear space. Removing kernels sometimes requires you update grub so that your changes are available at next boot.

So please, answer the questions and post the outputs to **all** of the following commands ([in code tags]("http://ubuntuforums.org/faq.php?faq=vb3_reading_posting#faq_vb3_basic_bb_code")):
```

df- h
df -h | grep sd
df -i
uname -r
dpkg --list | grep linux-image
```

As bab1 said, we can only guess so much.

---

### Post by Rolandl on 2015-07-31
I apologise for the inconvenience. I have no excuses. Kindly bear with me of you will. I am age 79 with couple health issues taking my energy so brain isn't as sharp, but this is good work for it. I appreciate your assistance.

3.19.0-25-generic
```
rolandl@rolandl-desktop:~$ dpkg --list | grep linux-image
rc  linux-image-3.19.0-15-generic                        3.19.0-15.15                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-18-generic                        3.19.0-18.18                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-20-generic                        3.19.0-20.20                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-21-generic                        3.19.0-21.21                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-22-generic                        3.19.0-22.22                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-23-generic                        3.19.0-23.24                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-24-generic                        3.19.0-24.25                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-25-generic                        3.19.0-25.26                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-15-generic                  3.19.0-15.15                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-18-generic                  3.19.0-18.18                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-20-generic                  3.19.0-20.20                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-21-generic                  3.19.0-21.21                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-22-generic                  3.19.0-22.22                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-23-generic                  3.19.0-23.24                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-24-generic                  3.19.0-24.25                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
iF  linux-image-extra-3.19.0-25-generic                  3.19.0-25.26                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
iU  linux-image-generic                                  3.19.0.25.24                                amd64        Generic Linux kernel image

```

I've done what you asked for now I think.
```

rolandl@rolandl-desktop:~$ df- h
No command 'df-' found, did you mean:
 Command 'dff' from package 'dff' (universe)
 Command 'df' from package 'coreutils' (main)
 Command 'dfo' from package 'dfo' (universe)
 Command 'dfc' from package 'dfc' (universe)
df-: command not found

rolandl@rolandl-desktop:~$ df -h | grep sd
/dev/sda1                    236M  234M     0 100% /boot
 ***
rolandl@rolandl-desktop:~$ df -i
Filesystem                   Inodes  IUsed   IFree IUse% Mounted on
udev                         244872    543  244329    1% /dev
tmpfs                        247771    694  247077    1% /run
/dev/mapper/ubuntu--vg-root 9658368 392654 9265714    5% /
tmpfs                        247771    171  247600    1% /dev/shm
tmpfs                        247771      7  247764    1% /run/lock
tmpfs                        247771     17  247754    1% /sys/fs/cgroup
/dev/sda1                     62248    332   61916    1% /boot
cgmfs                        247771     13  247758    1% /run/cgmanager/fs
tmpfs                        247771    100  247671    1% /run/user/1000
/dev/sr0                          0      0       0     - /media/rolandl/Mar 16 2014 vari
 ***
rolandl@rolandl-desktop:~$ uname -r
3.19.0-25-generic
 ***
/sda1                    236M  234M     0 100% /boot
rolandl@rolandl-desktop:~$ df -i
Filesystem                   Inodes  IUsed   IFree IUse% Mounted on
udev                         244872    543  244329    1% /dev
tmpfs                        247771    694  247077    1% /run
/dev/mapper/ubuntu--vg-root 9658368 392654 9265714    5% /
tmpfs                        247771    171  247600    1% /dev/shm
tmpfs                        247771      7  247764    1% /run/lock
tmpfs                        247771     17  247754    1% /sys/fs/cgroup
/dev/sda1                     62248    332   61916    1% /boot
cgmfs                        247771     13  247758    1% /run/cgmanager/fs
tmpfs                        247771    100  247671    1% /run/user/1000
/dev/sr0                          0      0       0     - /media/rolandl/Mar 16 2014 vari
rolandl@rolandl-desktop:~$ uname -r
3.19.0-25-generic
rolandl@rolandl-desktop:~$ uname -rdpkg --list | grep linux-image
uname: invalid option -- 'd'
Try 'uname --help' for more information.
rolandl@rolandl-desktop:~$ uname -rdpkg --list | grep linux-image
uname: invalid option -- 'd'
Try 'uname --help' for more information.

```

---

### Post by oldfred on 2015-07-31
Please use codes tags, easy to use with Forum's Advanced Editor and # icon.

Also better to copy & paste commands from forum. Where a space or - is, is vital with terminal commands. 

We now know you  are booting with -25 and your /boot is 100% full which was the original question asked in post #2.

       cd /boot
ls vmlinuz*
sudo ls -l /boot/vmlinuz*

sudo apt-get purge  linux-image-[version]-generic 
Example with [version] as 3.19.0.18
sudo apt-get purge vmlinuz-3.19.0-18-generic


You can repeat for several of the older kernels. Do not delete -25 and often best to keep one known working old one. Perhaps -24 if you used it and know it also works.

Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.19.0-{XX,XX,XX,XX,XX,XX}-generic
Example, if you use this double check that [version] is correct and each -XX is one you want to remove:
sudo apt-get purge linux-image-3.19.0-{18,20,21,22,23}-generic

---

### Post by bab1 on 2015-07-31
[QUOTE=Rolandl]
Should I create more space in /boot? repartition? 
```
/dev/mapper/ubuntu--vg-root [COLOR="#FF0000"]** /**[/COLOR]
/dev/sda1        [COLOR="#FF0000"]**/boot**[/COLOR]

```
[/QUOTE]
After looking at what data you did supply, I would say you should backup all your data and reinstall the entire OS.  I would use a single ext4 root partition (/) .  There is no need for the added complexity of a separate small boot partition (/boot) with a LVM root partition.  LVM is really great for data storage volumes.  Not so great for system volumes.

---

### Post by Rolandl on 2015-08-01
I been trying to remove some programs to make more disk space but that doesn't work either.

---

### Post by oldfred on 2015-08-01
It is only /boot which has kernels. Other programs are in your install in the LVM. So you need to houseclean kernels. And maintain only two kernels whenever another is added.

It is very difficult to resize an LVM, then resize the physical partition the LVM is in, then resize the /boot partition. If real knowledgeable with LVM & partitions you may be able to do it.

Was there some reason you chose the LVM. It is an advanced partitioning. 

I think bab1's suggestion of backing up & reinstalling without LVM is best.

---

### Post by bapoumba on 2015-08-01
Sorry, there is a typo in my previous post, I should have copy/pasted from post #2 and bab1's..

Anyway, if we go with oldfred's suggestion (using apt-get), please run :
```
sudo apt-get purge vmlinuz-3.19.0-15-generic
sudo apt-get purge vmlinuz-3.19.0-18-generic
sudo apt-get purge vmlinuz-3.19.0-20-generic
sudo apt-get purge vmlinuz-3.19.0-21-generic
sudo apt-get purge vmlinuz-3.19.0-22-generic
sudo apt-get purge vmlinuz-3.19.0-23-generic

```

That should get you back on tracks.

+1 to the suggestion to reinstall without using LVM. The default /boot partition is way too small on these setups. Please backup anything you'd cry for if you'd loose. Keeping up to date backups is the best idea in the universe if you ask me, even is you choose not to reinstall.

---

### Post by Rolandl on 2015-08-01
```

```
in terminal:
E: Unable to locate package vmlinuz-3.19.0-15-generic
E: Couldn't find any package by regex 'vmlinuz-3.19.0-15-generic'
same with 3.19.0-18
same with the rest. unable to locate.
```

```

Can't even uninstall unneeded programs.
How about if I load my ubuntu 15.04 disk and reinstall from there?
Should that work?

:?

```

```

Can't backup files either. Somewhere on-line for that?

```

```

---

### Post by bapoumba on 2015-08-01
The -15 kernel has the rc flag, sorry I overlooked that. It means it is removed but some config files are still there. We can treat that later on.
Please try the same command with the other kernels (18 and onward). 

I have never used apt-get in that situation. I know dpkg will do the job. So please try the above commands, if they do not work, we'll do it with dpkg.

What do you mean that you cannot backup files, is that because you do not have any usb drive to back them up to ?
You can save stuff online, but that would mean using the web interface of cloud services (such as dropbox, copy.com, mega, these are the ones I use, there are others) as you may not be able to install a client.

---

### Post by bab1 on 2015-08-01
> **Rolandl said:**
> ```

```
in terminal:
E: Unable to locate package vmlinuz-3.19.0-15-generic
E: Couldn't find any package by regex 'vmlinuz-3.19.0-15-generic'
same with 3.19.0-18
same with the rest. unable to locate.
```

```

Can't even uninstall unneeded programs.
How about if I load my ubuntu 15.04 disk and reinstall from there?
Should that work?

:?

The correct command is ```
sudo apt-get purge linux-image-<image-number>-generic
```
Insert the specific image number (e.g. 3.19.0-15) in place of the <image-number> notation in the command.

---

### Post by bab1 on 2015-08-01
> **bapoumba said:**
> The -15 kernel has the rc flag, sorry I overlooked that. It means it is removed but some config files are still there. We can treat that later on.
Please try the same command with the other kernels (18 and onward).

I have never used apt-get in that situation. I know dpkg will do the job. So please try the above commands, if they do not work, we'll do it with dpkg.

I suppose either way will work.  I removed an image last night using the command I just described.  The OP can use ```
sudo apt-get autoremove
``` ...to remove any leftover files.
> 
What do you mean that you cannot backup files, is that because you do not have any usb drive to back them up to ?
You can save stuff online, but that would mean using the web interface of cloud services (such as dropbox, copy.com, mega, these are the ones I use, there are others) as you may not be able to install a client.
Good luck advising the OP.  It's going to be a struggle.  I'm away for the next few hours.

---

### Post by Rolandl on 2015-08-02
```

E: Unable to locate package vmlinuz-3.19.0-23-generic
E: Couldn't find any package by regex 'vmlinuz-3.19.0-23-generic'

E: Unable to locate package vmlinuz-3.19.0-22-generic
E: Couldn't find any package by regex 'vmlinuz-3.19.0-22-generic'

```

I'm lost again. I will try again to backup the files to DVD I want to keep and try reinstall. and see what happens.

Thank you.

```

E: Unable to locate package vmlinuz-3.19.0-23-generic
E: Couldn't find any package by regex 'vmlinuz-3.19.0-23-generic'

E: Unable to locate package vmlinuz-3.19.0-22-generic
E: Couldn't find any package by regex 'vmlinuz-3.19.0-22-generic'

```

---

### Post by bapoumba on 2015-08-02
Please try :
```
sudo dpkg -P linux-image-3.19.0-18-generic
sudo dpkg -P linux-image-3.19.0-20-generic
sudo dpkg -P linux-image-3.19.0-21-generic
sudo dpkg -P linux-image-3.19.0-22-generic
sudo dpkg -P linux-image-3.19.0-23-generic
```

---

### Post by Rolandl on 2015-08-05
ls -l /boot  (total 0)

df -h | grep sd  (nothing came up)

Brasero won't copy files to cd or dvd. neither doc's or mp3s.

---

### Post by bapoumba on 2015-08-07
Hmm, which steps did you use to get to these last outputs ?
At least you should have -24 and -25 in /boot..

---

### Post by Rolandl on 2015-08-08
```

~$ sudo dpkg -P linux-image-3.19.0-25-generic
[sudo] password for rolandl: 
dpkg: dependency problems prevent removal of linux-image-3.19.0-25-generic:
 linux-image-extra-3.19.0-25-generic depends on linux-image-3.19.0-25-generic.

dpkg: error processing package linux-image-3.19.0-25-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-3.19.0-25-generic
```

and this:
```

~$ $ sudo dpkg -P linux-image-3.19.0-26-generic
$: command not found
```

Would it help if I showed what is in /boot now? How to do that?

Oh, by the way, I never chose LVM, it just happened.

---

### Post by oldfred on 2015-08-08
You posted contents of /boot in Post #10.

---

### Post by Rolandl on 2015-08-08
What do you think I need to do next?

I looked at this but too much for my brain.
[COLOR=Navy]For info on UEFI boot install & repair - Updated Mar 2015:
[/COLOR] [URL="http://ubuntuforums.org/showthread.php?t=2147295"]http://ubuntuforums.org/showthread.php?t=2147295



[/URL]

---

### Post by Rolandl on 2015-08-08
Also tried to install dropbox so I could save my files but no space in /boot to install.

PS: I really appreciate your patient attitude.
Roland

---

### Post by oldfred on 2015-08-08
My signature is just for those with UEFI that want to know more, or have issues and are willing to review lots of detail. Not for your issues.

Can you post current contents of /boot as you did in Post #6?
Have you managed to delete any to make more room?

---

### Post by Rolandl on 2015-08-09
No haven't removed any. I tried but didn't work.
Thought I was working with generic -26 but apparently not.

-rw-r--r-- 1 root root 21769753 Jun 17 10:12 initrd.img-3.19.0-21-generic
-rw-r--r-- 1 root root 21772029 Jun 24 19:17 initrd.img-3.19.0-22-generic
-rw-r--r-- 1 root root 21778367 Jul 10 11:17 initrd.img-3.19.0-23-generic
-rw-r--r-- 1 root root 21778181 Jul 25 08:08 initrd.img-3.19.0-24-generic
-rw-r--r-- 1 root root 21774564 Jul 28 07:34 initrd.img-3.19.0-25-generic
drwx------ 2 root root    12288 May 31 09:02 lost+found
-rw-r--r-- 1 root root   164216 Mar  6 08:23 memtest86+.bin
-rw-r--r-- 1 root root   165892 Mar  6 08:23 memtest86+.elf
-rw-r--r-- 1 root root   166396 Mar  6 08:23 memtest86+_multiboot.bin
-rw------- 1 root root  3616263 May 19 12:45 System.map-3.19.0-18-generic
-rw------- 1 root root  3617303 May 29 04:02 System.map-3.19.0-20-generic
-rw------- 1 root root  3617303 Jun 14 12:44 System.map-3.19.0-21-generic
-rw------- 1 root root  3617446 Jun 16 11:30 System.map-3.19.0-22-generic
-rw------- 1 root root  3617597 Jul  7 13:05 System.map-3.19.0-23-generic
-rw------- 1 root root  3617597 Jul 22 13:14 System.map-3.19.0-24-generic
-rw------- 1 root root  3617653 Jul 24 16:35 System.map-3.19.0-25-generic
-rw------- 1 root root  6614144 May 19 12:45 vmlinuz-3.19.0-18-generic
-rw------- 1 root root  6616960 May 29 04:02 vmlinuz-3.19.0-20-generic
-rw------- 1 root root  6617408 Jun 14 12:44 vmlinuz-3.19.0-21-generic
-rw------- 1 root root  6616448 Jun 16 11:30 vmlinuz-3.19.0-22-generic
-rw------- 1 root root  6616320 Jul  7 13:05 vmlinuz-3.19.0-23-generic
-rw------- 1 root root  6616192 Jul 22 13:14 vmlinuz-3.19.0-24-generic
-rw------- 1 root root  6616704 Jul 24 16:35 vmlinuz-3.19.0-25-generic

---

### Post by oldfred on 2015-08-09
Until you delete some of those kernels you will  have the issues.

Are you still able to boot into system?

Have you gone back thru this thread which has several posts on how to delete a kernel or several kernels? I can repeat them all if necessary.

---

### Post by Rolandl on 2015-08-09
> 
just now tried this:  sudo dpkg -P linux-image-3.19.0-18-generic 

and it said this:  dpkg: dependency problems prevent removal of linux-image-3.19.0-18-generic:
 linux-image-extra-3.19.0-18-generic depends on linux-image-3.19.0-18-generic.

dpkg: error processing package linux-image-3.19.0-18-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-3.19.0-18-generic
> 

---

### Post by Rolandl on 2015-08-09
and this:  dpkg -P linux-image-3.19.0-19-generic 
dpkg: error: requested operation requires superuser privilege

I thought I'm supposed to have superuser privilege already.
How can I get it?
> 

---

### Post by bab1 on 2015-08-09
It appears you have this added package```
linux-image-**[COLOR="#FF0000"]extra[/COLOR]**-3.19.0-18-generic
```

You need to remove this package before you can remove the package ```
linux-image-3.19.0-18-generic
```
If you added the extra package each time then you will have to remove that extra package before you can remove the standard image (eg. as below)```
sudo apt-get purge linux-image-**[COLOR="#FF0000"]extra[/COLOR]**-3.19.0-18-generic

sudo apt-get purge linux-image-3.19.0-18-generic
```

The *linux-image-[COLOR="#FF0000"]**extra**[/COLOR]* package is dependant on the *linux-image* ; so you can't remove the image until you remove the extras.

---

### Post by Rolandl on 2015-08-10
> 
I just now did this:  sudo apt-get purge linux-image-extra-3.19.0-18-generic
[sudo] password for rolandl: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-3.19.0-26-generic : Depends: linux-image-3.19.0-26-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.19.0-26-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
rolandl@rolandl-desktop:~$ sudo apt-get purge linux-image-3.19.0-18-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-3.19.0-18-generic : Depends: linux-image-3.19.0-18-generic but it is not going to be installed
 linux-image-extra-3.19.0-26-generic : Depends: linux-image-3.19.0-26-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.19.0-26-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

rolandl@rolandl-desktop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
rolandl@rolandl-desktop:~$ 

I'm not getting anywhere. why don't I have superuser privilege? and how can I get it?
> 

---

### Post by oldfred on 2015-08-10
Anytime I run a command and it complains I know I forgot the sudo.
You ran:
apt-get -f install

Should be
sudo apt-get -f install

---

### Post by bab1 on 2015-08-11
> **oldfred said:**
> Anytime I run a command and it complains I know I forgot the sudo.
You ran:
apt-get -f install

Should be
sudo apt-get -f install
I wouldn't blindly run that command.  It will try and fix the dependencies.  Since the OP wants to delete all of that, it might be better to think about it for a second and then run this instead```
sudo apt-get **[COLOR="#FF0000"]autoremove[/COLOR]** 
```That will remove any unresolved dependencies.

My guess here is that at one time the OP felt he needed the extra's package which contains some modules that are not normally in the standard module package by default. I feel that these should be removed not repaired.

So the question here @Rolandl; did you add extra modules for some reason after the normal install?  I think you should return the system back to its default state ( or at least as close as possible).  That means you should continue purging the Linux image packages with ```

sudo apt-get purge linux-image- <the next number> -generic
```
...and if you get another error do this```
sudo apt-get autoremove
```
.. then just keep going until you have only the latest 2 images in /boot.

If at that point you have problems with modules, we can see if you really need to add back the extras package.

---

### Post by Rolandl on 2015-08-11
> 
sudo apt-get purge linux-image- <the next number> -generic 
bash: the: No such file or directory

I've tried several times now all that you guys have suggested and still ends with this:
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)

seems I need more space in /boot yet no way to create more space so am going to take Bab suggestion and reinstall with no partitions. guess will lose my files. hope I can get superuser status this time.

And, as stated earlier, Brasero won't copy any files to a DVD RW.
> 

---

### Post by oldfred on 2015-08-11
are you literally typing "<the next number>"?
That is supposed to be the specific kernel by number.

I stopped using DVDs as major backup as flash drives are reusable and rewritable.

---

### Post by bab1 on 2015-08-11
> **Rolandl said:**
> sudo apt-get purge linux-image- <the next number> -generic 
bash: the: No such file or directory
@Rolandl, you need to do a little bit thinking here.  As @oldfred said, you can't just expect us to provide all the commands for you to purge each and every package you have installed in /boot.  This exercise should have some two way conversation other than you telling us that; "This didn't work"

You need to add the next package number to the basic command for it to work.
> 

I've tried several times now all that you guys have suggested and still ends with this:
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)

seems I need more space in /boot yet no way to create more space so am going to take Bab suggestion and reinstall with no partitions. guess will lose my files. hope I can get superuser status this time.

And, as stated earlier, Brasero won't copy any files to a DVD RW.
Forget the DVD,  Forget any "backup" solution.  Just copy all the files you want to save to a USB stick drive as @oldfred has suggested.  Then you can just move them from the USB stick after you have reinstalled.

---

### Post by Rolandl on 2015-08-11
[/QUOTE][/QUOTE]
I just now did it again to make sure I do it correctly:

$ sudo apt-get purge linux-image-extra-3.19.0-18-generic
[sudo] password for rolandl: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-3.19.0-26-generic : Depends: linux-image-3.19.0-26-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.19.0-26-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
rolandl@rolandl-desktop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


I tried flashdrive this morning with Brasero and wouldn't copy files. it said successful image created.. but there's nothing on the flashdrive.

---

### Post by Rolandl on 2015-08-11
Okay, I've done my best. have spent a lot of time thinking and working on this. I'm not the kind of idiot you might think I am. going to reinstall and if it's no better I will go back to Windows. This is 3 versions of linux I've bought and installed the cd. solydxk, linux mint and now ubuntu. I thank you all for your trying anyway.

PS: I am no 'spring chicken'.

---

### Post by oldfred on 2015-08-11
I suggest standard partitions not LVM, unless you require the full drive encryption.

---

### Post by bab1 on 2015-08-11
> **Rolandl said:**
> 

I tried flashdrive this morning with Brasero and wouldn't copy files. it said successful image created.. but there's nothing on the flashdrive.
This is the kind of thing I am talking about.  You SHOULD NOT be making images of your data.  Just copy the folders and files to the flash drive using the file manager.  There is no need to use Brasero at all. 

I wouldn't use age as an excuse.  I'm almost 70 years old myself.  I wonder if you truly understand the instructions we have tried to convey.

---

### Post by Rolandl on 2015-08-12
> 
I'm not using age as excuse. I don't know if I understand all the instructions but I do know that I've done everything suggested several times. I hope you are well Bab. at 70 my brain functioned quite well too. After a stroke it slowed down and I had to really focus on doing things that would help it, like Right exercise Right thinking and Right food. It has recovered a lot. working on computer and self-observation in the Gurdjieff tradition is good for my body-mind organism and for I, the Conscious-awareness behind it. I have to admit though, I am an idiot. :D
> 

---

### Post by PaulW2U on 2015-08-12
> **Rolandl said:**
> E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
rolandl@rolandl-desktop:~$ [COLOR="#FF0000"]**apt-get -f install**[/COLOR]
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Rolandl, I've looked though several posts in this thread and I'm thinking that what you have missed and may be what some of the helpers have not pointed out to you is that in general apt-get commands need the sudo prefix.

I think I'm right in saying that if an apt-get command is requesting information then sudo is **not** needed. But if changes are being made then sudo **is** needed.

In the output that you posted 
```
apt-get -f install
``` 
should be input as 
```
sudo apt-get -f install
```
as you are asking for system files to be updated.

Please stay with us :)

Oh, and you are not an idiot!

---

### Post by Rolandl on 2015-08-12
> 
I used file mngr to copy files to flash and seems to have worked well. and surprisingly fast.
:KS

---

### Post by Rolandl on 2015-08-12
> 
Thanks for the encouraging remark Paul. I just did this again: 
sudo apt-get -f install 

and this came up: 
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  account-plugin-tools accountsservice-ubuntu-schemas
  accountsservice-ubuntu-touch-schemas address-book-service
  dbus-property-service gir1.2-gconf-2.0 gir1.2-vte-2.90 history-service
  libboost-locale1.55.0 libboost-program-options1.55.0
  libboost-serialization1.55.0 libcapnp-0.4.0 libconnectivity-qt1 libdbus-cpp4
  libhistoryservice0 libhybris libhybris-utils libjsoncpp0 libmedia1
  libmediascanner-2.0-3 libmirplatform6 libmirserver30 libnet-cpp1
  libofono-qt1 libpay2 libpgm-5.1-0 libphonenumber6 libpoppler-qt5-1
  libprocess-cpp2 libqdjango-db0 libqgsttools-p1 libqmenumodel0
  libqofono-qt5-0 libqt5concurrent5 libqt5contacts5 libqt5keychain0
  libqt5location5 libqt5location5-plugins libqt5multimedia5-plugins
  libqt5multimediaquick-p5 libqt5multimediawidgets5 libqt5positioning5-plugins
  libqt5quickparticles5 libqt5script5 libqt5sensors5 libqt5systeminfo5
  libqt5versit5 libqt5versitorganizer5 libqt5websockets5 libqt5xmlpatterns5
  libsodium13 libsystemsettings1 libtelepathy-qt5-0 libthumbnailer0
  libtrust-store1 libu1db-qt5-3 libubuntu-location-service2
  libubuntuoneauth-2.0-0 libudm-priv-common0 libunity-api0 libunity-scopes3
  libusermetricsinput1 libusermetricsoutput1 libvte-2.90-9 libvte-2.90-common
  libzmq3 libzmqpp3 mediascanner2.0 mir-platform-graphics-mesa1
  packagekit-tools pay-service python-compizconfig python3-gnupg
  qmenumodel-qml qml-module-qt-websockets qml-module-qtlocation
  qml-module-qtmultimedia qml-module-qtorganizer qml-module-qtpositioning
  qml-module-qtquick-particles2 qml-module-qtquick-xmllistmodel
  qml-module-qtsensors qml-module-qtsysteminfo qml-module-ubuntu-connectivity
  qmlscene qtcontact5-galera qtdeclarative5-folderlistmodel-plugin
  qtdeclarative5-gsettings1.0 qtdeclarative5-ofono0.2
  qtdeclarative5-particles-plugin qtdeclarative5-poppler1.0
  qtdeclarative5-qtmir-plugin qtdeclarative5-qtorganizer-plugin
  qtdeclarative5-systeminfo-plugin qtdeclarative5-u1db1.0
  qtdeclarative5-ubuntu-mediascanner0.1 qtdeclarative5-ubuntu-push-plugin
  qtdeclarative5-ubuntu-settings-components
  qtdeclarative5-ubuntu-syncmonitor0.1
  qtdeclarative5-ubuntu-telephony-phonenumber0.1
  qtdeclarative5-ubuntu-telephony0.1 qtdeclarative5-ubuntu-thumbnailer0.1
  qtdeclarative5-ubuntuone1.0 qtdeclarative5-unity-notifications-plugin
  qtdeclarative5-usermetrics0.1 qtdeclarative5-xmllistmodel-plugin
  qtmir-desktop sqlite3 system-image-common system-image-dbus telepathy-ofono
  telephony-service thumbnailer-common thumbnailer-service tone-generator
  ubuntu-download-manager ubuntu-html5-container ubuntu-html5-ui-toolkit
  ubuntu-keyboard-data ubuntu-sdk-libs ubuntuone-credentials-common
  unity-plugin-scopes unity-scope-click-departmentsdb
  unity-scope-mediascanner2 unity-scope-scopes unity8-common unity8-private
  urfkill usermetricsservice
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.19.0-26-generic
Suggested packages:
  fdutils linux-doc-3.19.0 linux-source-3.19.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.19.0-26-generic
0 upgraded, 1 newly installed, 0 to remove and 31 not upgraded.
4 not fully installed or removed.
Need to get 0 B/16.9 MB of archives.
After this operation, 47.9 MB of additional disk space will be used.
Do you want to continue? [Y/n] 

```
I entered this:  sudo apt-get autoremove
Abort.
> 

---

### Post by bab1 on 2015-08-12
> **Rolandl said:**
> I'm not using age as excuse. I don't know if I understand all the instructions but I do know that I've done everything suggested several times. I hope you are well Bab. at 70 my brain functioned quite well too. After a stroke it slowed down and I had to really focus on doing things that would help it, like Right exercise Right thinking and Right food. It has recovered a lot. working on computer and self-observation in the Gurdjieff tradition is good for my body-mind organism and for I, the Conscious-awareness behind it. I have to admit though, I am an idiot. :D
If you don't understand please ask for a clearer explanation.  These kinds of instructions are not that hard.  Granted, they are not always intuitive to the casual user (of sound mind or not).  I only mentioned age so that you understand that not all of us are youthful, prime of life types.

In simple terms, you need to delete a whole series of Linux kernel packages for the system to work correctly.  When you installed Ubuntu and allowed it to use LVM (the Logical Volume Manager) for the main data partition it had to make a /boot file system that is not part of the Logical Volume.  It is now full and that has stopped the system from working correctly.  My suggestion to reinstall is the simplest way to overcome the problem.  If you need to save your data then the simplest way is to use the GUI (Graphical User Interface) file manager to just drag your home directory folder onto a USB stick.

If you need clarification on any of the terms used or need specific instructions, just ask.  If you want a description of why you are having trouble deleting the Linux image packages we can do that too.

I think the best way to start is to save the data to a USB stick regardless of whether you reinstall or repair what you have.  What do you think.

---

### Post by bab1 on 2015-08-12
I think at this point you are getting conflicting instructions.  I don't think it was wise to use this command at all```
sudo apt-get install -f
```
Why?  Because it adds Linux images back to the /boot file system.  
See this```
The following NEW packages will be installed:
  linux-image-3.19.0-26-generic
```

That is why I suggested this command instead```
sudo apt-get autoremove
```This command removes all not needed dependent libraries.  

What do you mean by this?> I entered this: sudo apt-get autoremove
Abort.

Since there seems to be 2 ideas of what to do here.  You need to follow one or the other and not combine both.

---

### Post by Rolandl on 2015-08-12
> 
Am thinking of doing what you suggested here Tomas, install to flash first then go from there.
Will follow your directions. Will this way get rid of unneeded partitions that are taking space on the HD?
Maybe as Bap said, no need for swap and boot partitions. I don't foresee installing anything else.
> 

---

### Post by bab1 on 2015-08-12
> **Rolandl said:**
> 
Maybe as Bap said, no need for swap and boot partitions. I don't foresee installing anything else.
It's BAB1 :-(

I never said "no swap".  Only no separate /boot partition.

---

### Post by Rolandl on 2015-08-12
> 
I think I will as i stated to him, follow Tomasrey's suggestion to full install on a flash drive first and go from there. what do you think Bab? I think getting different info from people plus all the info that comes up in terminal has confused my brain. not blaming anyone, just stating what seems to be the fact.
> 

---

### Post by Rolandl on 2015-08-12
> 
 Only no separate /boot partition.?? need clarification.

do you mean no boot partition separate from the Ubuntu OS? that would create 2 partitions then, sda1 and swap instead of the 3 present ones? which I understand /swap is free usable space?
> 

---

### Post by bab1 on 2015-08-12
> **Rolandl said:**
> I think I will as i stated to him, follow Tomasrey's suggestion to full install on a flash drive first and go from there. what do you think Bab? I think getting different info from people plus all the info that comes up in terminal has confused my brain. not blaming anyone, just stating what seems to be the fact.

USB flash drives are not very reliable for daily use.  They are designed for data storage only.  The flash drive will fail in a relatively short time from all the read/write actions of normal use.  I think it is okay If you are going to use the flash drive as a practice only device so you become familiar with how to install Ubuntu.  In the end you will have to install the Ubuntu OS on either a HDD (hard drive) or a SSD (solid state drive).  Note:  SSD's are NOT the same as flash drives.

What ever you do; DO NOT use the flash drive that you just put all of your data on it. 

To summarize:  Use a flash drive only for practice as it is not durable.  In the end you will need to install on a HDD or a SSD for daily use.

---

### Post by oldfred on 2015-08-12
With most desktop installs a /boot is a disadvantage. Another partition to manage. But LVM with encryption requires a /boot partition. Perhaps some server type installs can use one.

If drive is larger I prefer a smaller, but generous / (root) and either /home or /mnt/data partition. For newer users a /home is easier to manager.
You should have some swap, but if you have 4GB or more of RAM, you may never use it. Still good to have some.

Default installs are just / & swap.
       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Rolandl on 2015-08-12
> 
idiot: I see it as G Gurdieff suggested, we all are basically 2 kinds of 'idiot'.. an objective one that is learning to be Master of self and to 'Awaken', and subjective one that thinks it already knows enough and is operating on 'auto-pilot'. :p
> 

---

### Post by bab1 on 2015-08-12
> **Rolandl said:**
> idiot: I see it as G Gurdieff suggested, we all are basically 2 kinds of 'idiot'.. an objective one that is learning to be Master of self and to 'Awaken', and subjective one that thinks it already knows enough and is operating on 'auto-pilot'. :p
It might be best if we leave Mr Gurdieff out of the discussion about installing Ubuntu.
> 
Only no separate /boot partition.?? need clarification.

do you mean no boot partition separate from the Ubuntu OS? that would create 2 partitions then, sda1 and swap instead of the 3 present ones? which I understand /swap is free usable space?

Without getting too deep into "techie talk", I am saying you do not need a separate partition to install the files that reside at /boot.  The files can reside on the / partition.  This means that the entire OS resides on the same partition (e.g. sda)  The only partitions are for the OS (including all the files in /boot) and the swap partition.  Swap is a specific size and is used by the OS to move data that is in RAM to the disk on a temporary basis.  It is managed by the Linux kernel.  You don't need to do anything after you create it when you install the OS.   I can't see any reason to encrypt anything at this time.  Encryption also adds complexity that is not warranted in most cases.  I have a few files that I encrypt, but that's all.  I don't take a laptop out in public so I don't encrypt my data partitions on those either.

The reason for the simple methods like this is so you eliminate the problem you have right now with a limited amount of space on the partition you have for /boot.  Partitions are containers for parts of the file system.  When you fill up a partition The OS halts.  This is what you are being alerted to right now.  You created a partition too small for /boot.  Since you have a disk with enough room for all of the OS, I suggest you just use the single partition (e.g. sda1) for the entire OS plus some for  the swap partition.

---

### Post by Rolandl on 2015-08-12
> 
Bab, are you saying that it will work best if I simply reinstall Ubuntu from the original install disk and forget all other options? Will it automatically create 2 partitions? the OS partition and a swap partition? just insert the disk, reboot, and it should load, then click on 'install ubuntu'? it will ask me about  LVM (the Logical Volume Manager) and I need to bypass it or say no? I don't remember anything referring to that when I installed it from the disk. > 

---

### Post by bab1 on 2015-08-12
> **Rolandl said:**
> Bab, are you saying that it will work best if I simply reinstall Ubuntu from the original install disk and forget all other options? Will it automatically create 2 partitions? the OS partition and a swap partition? just insert the disk, reboot, and it should load, then click on 'install ubuntu'? it will ask me about  LVM (the Logical Volume Manager) and I need to bypass it or say no? I don't remember anything referring to that when I installed it from the disk.
I have to say that I always customize the installation of my installs.  But you should be able to install Ubuntu on a single partition + a swap partition.  NO LVM, NO ENCRYPTION.

Yo may have to install it more than once in the beginning.  I think LVM might be a default rather than an option.  If you want to you could select **other** at the disk partitioning section and make a partition that is mounted at / plus a swap.  Once again NO LVM, NO ENCRYPTION.  So you can try automatic or you can do it manually.

---

### Post by Rolandl on 2015-08-13
> 
Okay, I reinstalled with no LVM or encryption. so far working good. I guess you guys are glad I finally made decision to do it haha. It seems Bab's suggestions for install has worked. 
Love to y'all for your help.
Roland
> 

---

### Post by bab1 on 2015-08-13
> **Rolandl said:**
> Okay, I reinstalled with no LVM or encryption. so far working good. I guess you guys are glad I finally made decision to do it haha. It seems Bab's suggestions for install has worked. 
Love to y'all for your help.
Roland
How about showing us the results of our efforts.  Post the output of this command```
df -h
```

If we have solved your problem then mark this thread SOLVED!  You can do that by following [**[SIZE=3]these steps[/SIZE]**]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by Rolandl on 2015-08-13
> 

rolandl@rolandl-desktop:~$ sudo df -h
[sudo] password for rolandl: 
Filesystem      Size  Used Avail Use% Mounted on
udev            957M     0  957M   0% /dev
tmpfs           194M  5.0M  189M   3% /run
/dev/sda1       145G  4.5G  133G   4% /
tmpfs           968M  256K  968M   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           968M     0  968M   0% /sys/fs/cgroup
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           194M   96K  194M   1% /run/user/1000
/dev/sdg1       3.8G  1.2G  2.7G  31% /media/rolandl/F9CE-F3E0
rolandl@rolandl-desktop:~$ 

I keep having an issue not able to post because it's "too short". 
never had that problem with Chromium so will go back to it.

---

### Post by bab1 on 2015-08-13
> **Rolandl said:**
> ```
rolandl@rolandl-desktop:~$ sudo df -h
[sudo] password for rolandl: 
Filesystem      Size  Used Avail Use% Mounted on
udev            957M     0  957M   0% /dev
tmpfs           194M  5.0M  189M   3% /run
/dev/sda1       145G  4.5G  133G   4% /
tmpfs           968M  256K  968M   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           968M     0  968M   0% /sys/fs/cgroup
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           194M   96K  194M   1% /run/user/1000
/dev/sdg1       3.8G  1.2G  2.7G  31% /media/rolandl/F9CE-F3E0
rolandl@rolandl-desktop:~$ 
```

I keep having an issue not able to post because it's "too short". 
never had that problem with Chromium so will go back to it.

Perfect install.  The reason it you are getting the error is due to ou not saying enough.

Don't forget to mark this **[SIZE=4]SOLVED[/SIZE]** !!!

It only took 70 odd exchanges, but we finnaly got 'er done!  :D

---

### Post by Rolandl on 2015-08-13
am I slow or what! YES!! but this is good work for my brain.

---

