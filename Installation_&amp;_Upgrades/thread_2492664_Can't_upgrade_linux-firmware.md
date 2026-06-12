---
title: "Can't upgrade linux-firmware"
date: 2023-11-19
forum: Installation &amp; Upgrades
---

### Post by josefranw on 2023-11-19
Hello, I had been installing all updates to my xubuntu system as they became available normally... but recently there's been a package that hasn't been able to get upgraded as every time I update the system, I get an error message. And this archive is no other than the linux-firmware (which as far as a I know, is the kernel of the system...)

This is the error I get:

```
sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  linux-firmware
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/281 MB of archives.
After this operation, 3,149 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
(Reading database ... 223693 files and directories currently installed.)
Preparing to unpack .../linux-firmware_20230323.gitbcdcfbcf-0ubuntu1.8_all.deb ...
Unpacking linux-firmware (20230323.gitbcdcfbcf-0ubuntu1.8) over (20230323.gitbcdcfbcf-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/linux-firmware_20230323.gitbcdcfbcf-0ubuntu1.8_all.deb (--unpack):
 trying to overwrite '/lib/firmware/ath9k_htc/htc_7010-1.4.0.fw', which is also in package firmware-ath9k-htc 1.4.0-108-gd856466+dfsg1-1.2
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
update-initramfs: Generating /boot/initrd.img-6.2.0-36-generic
update-initramfs: Generating /boot/initrd.img-6.2.0-35-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-firmware_20230323.gitbcdcfbcf-0ubuntu1.8_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I don't know how to solve this problem. Please, keep in mind that I'm just a regular linux user with no specific knowledge of technicalities...

I hope someone can help me out here.

---

### Post by MAFoElffen on 2023-11-19
What happens if you try
```

sudo cp /lib/firmware/ath9k_htc/htc_7010-1.4.0.fw $HOME/Downloads/htc_7010-1.4.0.fw.old
sudo rm /lib/firmware/ath9k_htc/htc_7010-1.4.0.fw
sudo apt install --reinstall linux-firmware

```
What that did was to copy it to your Downloads folder as a backup. Remove it from where it was causing trouble. Then try to reinstall 'linux-firmware'

---

### Post by josefranw on 2023-11-19
Thanks...

still the same thing...

```
sudo cp /lib/firmware/ath9k_htc/htc_7010-1.4.0.fw /home/josefranw/Downloads/htc_7010-1.4.0.fw.old
josefranw@laptop-pachico:~$ sudo rm /lib/firmware/ath9k_htc/htc_7010-1.4.0.fw
josefranw@laptop-pachico:~$ sudo apt install --reinstall linux-firmware
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be upgraded:
  linux-firmware
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/281 MB of archives.
After this operation, 3,149 kB of additional disk space will be used.
(Reading database ... 223693 files and directories currently installed.)
Preparing to unpack .../linux-firmware_20230323.gitbcdcfbcf-0ubuntu1.8_all.deb ...
Unpacking linux-firmware (20230323.gitbcdcfbcf-0ubuntu1.8) over (20230323.gitbcdcfbcf-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/linux-firmware_20230323.gitbcdcfbcf-0ubuntu1.8_all.deb (--unpack):
 trying to overwrite '/lib/firmware/ath9k_htc/htc_7010-1.4.0.fw', which is also in package firmware-ath9k-htc 1.4.0-108-gd856466+dfsg1-1.2
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
update-initramfs: Generating /boot/initrd.img-6.2.0-36-generic
update-initramfs: Generating /boot/initrd.img-6.2.0-35-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-firmware_20230323.gitbcdcfbcf-0ubuntu1.8_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by #&amp;thj^% on 2023-11-19
I was lucky enough to re-install when this happened to me:
First:
```
sudo apt clean
```
I'm not sure if you need this but I did so:
```
sudo apt install python-is-python3
### And now run
sudo apt install --reinstall linux-firmware

```
It ran fine for me:
```
 Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 408 MB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu noble/main amd64 linux-firmware amd64 20230919.git3672ccab-0ubuntu2.2 [408 MB]
Fetched 408 MB in 1min 12s (5,639 kB/s)                                        
(Reading database ... 442632 files and directories currently installed.)
Preparing to unpack .../linux-firmware_20230919.git3672ccab-0ubuntu2.2_amd64.deb
 ...
Unpacking linux-firmware (20230919.git3672ccab-0ubuntu2.2) over (20230919.git367
2ccab-0ubuntu2.2) ...
Setting up linux-firmware (20230919.git3672ccab-0ubuntu2.2) ...
Processing triggers for initramfs-tools (0.142ubuntu17) ...
update-initramfs: Generating /boot/initrd.img-6.5.0-10-generic
I: The initramfs will attempt to resume from /dev/dm-1
I: (/dev/mapper/vglinux-swap_1)
I: Set the RESUME variable to override this.
needrestart is being skipped since dpkg has failed

```
Good Luck
EDIT: Please try the above first, and let us know, I have a very harsh method as well: [https://tutorialforlinux.com/2021/01/11/how-to-update-linux-firmware-on-xubuntu-guide/2/](https://tutorialforlinux.com/2021/01/11/how-to-update-linux-firmware-on-xubuntu-guide/2/)
Please have back-ups in place first, if it's not done correctly it will finish your system off. (broke)

---

### Post by MAFoElffen on 2023-11-19
I've written two tutorials for doing it that way (git), and from downloading the latest blob from Kernel.org, then extracting it into the /lib/firmware directory. Both work.

Even more aggressive = Then there is this
```

sudo apt-get --download-only linux-firmware
sudo mv /usr/lib/firmware /usr/lib/firmware-bak
sudo mkdir /usr/lib/firmware
sudo dpkg -i linux-firmware*.deb

```

---

### Post by josefranw on 2023-11-20
I tried 

```
[COLOR=#000000][FONT=&quot]sudo apt clean[/FONT][/COLOR][COLOR=#000000][FONT=&quot]
[/FONT][/COLOR][COLOR=#000000][FONT=&quot]sudo apt install --reinstall linux-firmware[/FONT][/COLOR]
```

but it did not work. :(

---

### Post by josefranw on 2023-11-20
Can I delete linux-firmware without breaking the system?

I had thought about it and opened sysnaptics to search for linux-firmware and marked it for complete removal and it suggested also removing something like linux-generic and linux-generic-image so I cancelled that.

---

### Post by Rubi1200 on 2023-11-20
You should definitely NOT delete that package. Doing so will break your system.

Wait for either **1fallen **or **MAFoElffen **to advise you on the next steps.

---

### Post by #&amp;thj^% on 2023-11-20
> **josefranw said:**
> Can I delete linux-firmware without breaking the system?
No as Rubi1200 already said.
> **josefranw said:**
> 
I had thought about it and opened sysnaptics to search for linux-firmware and marked it for complete removal and it suggested also removing something like linux-generic and linux-generic-image so I cancelled that.
Good choice to not do that.
BTW Did you ever give MAFoElffen's post suggestion a try yet?

---

### Post by MAFoElffen on 2023-11-20
It is risky, because if involved in an update, 'linux-firmware' has to be there. Those are binary files used to compile/build the modules for each kernel...

But if your download the package, or the git, or the blog, then you have those files to get back there...

Let me ammend my answer on how to do that "safer"... I am going to give you two different methods... Make sure you have a few GB's free first. 

Before doing that, do this first...
```

mkdir $HOME/Downloads/firmware
cd $HOME/Downloads/firmware
wget -N -t 5 -T 10 https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/snapshot/linux-firmware-20231111.tar.gz
sudo apt-get --download linux-firmware # It's going to be a .deb file name to these conventions: linux-firmware-<version>.deb 

```
That way, you have two chances at fall-backs for that on your system...

Then look at the amended instructions here: [https://ubuntuforums.org/showthread.php?t=2492664&p=14166076#post14166076](https://ubuntuforums.org/showthread.php?t=2492664&p=14166076#post14166076)

Try that first...

---

### Post by josefranw on 2023-11-22
Hello. I haven't done anything because I'm currently using the laptop because I work with it and I don't want to break anything. So, I'm waiting for the weekend when I have more free time and can get the time to fix anything that might break.

---

### Post by MAFoElffen on 2023-11-22
Okay

---

### Post by josefranw on 2023-11-26
```
wget -N -t 5 -T https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/snapshot/linux-firmware-20231111.tar.gz
wget: --timeout: Invalid time period &#8216;https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/snapshot/linux-firmware-20231111.tar.gz&#8217;
```

---

### Post by #&amp;thj^% on 2023-11-26
Yep I get the same:
```
wget -N -t 5 -T https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/snapshot/linux-firmware-20231111.tar.gz
wget: --timeout: Invalid time period &#8216;https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/snapshot/linux-firmware-20231111.tar.gz&#8217;
```
EDIT Just paste the URL in your browser it will start the Download.
Copy URL:  [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/snapshot/linux-firmware-20231111.tar.gz](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/snapshot/linux-firmware-20231111.tar.gz)

It will take a little time depending on your Internet speed:
```
*cd Downloads && ls
"1.ALL DL's"   linux-firmware-20231111.tar.gz

```

---

### Post by MAFoElffen on 2023-11-26
Dang... Omitted something there. Edited. Should have been
```

wget -N -t 5 -T [COLOR=#ff0000]10[/COLOR]  https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/snapshot/linux-firmware-20231111.tar.gz

```

---

### Post by josefranw on 2023-12-11
I really need another solution. I can't download that big file with my Internet connection. [COLOR=#000000][FONT=&quot]https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/snapshot/linux-firmware-20231111.tar.gz
[/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-12-11
??? 

I call BS on that. I just downloaded it (from [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/)). The compressed file size of the latest (uploaded less than 5 hours ago) is only 518 MiB. If you cannot download that size of a file, then you cannot do any updates to your system either. 

It is an archive (compressed) file that contains the exact same binary files as in the linux-firmware package. Which the linux-firmware deb package is also a compress archive file. Because of the install/remove scripts and other included files in that .deb install package file, the size of it would actually be larger!

I feel like if you need either, those are your two options. And since your computer has problems with installing the linux-firmware package, you are down to that one option.

If you can't do either, I'm out of practical answers. There is another repo there , where you can download each file individually, and each file is small... But there are thousands of individual files there. Manually, that would result in more overall bandwidth, would take you over a year to do, and you would have to keep track of each file you downloaded, so you didn't skip any of those. That is just not a practical solution.

---

### Post by #&amp;thj^% on 2023-12-11
> **MAFoElffen said:**
> ??? 

I call BS on that. I just downloaded it (from [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/)). The compressed file size of the latest (uploaded less than 5 hours ago) is only 518 MB. If you cannot download that size of a file, then you cannot do any updates to your system either. 

It is an archive (compressed) file that contains the exact same binary files as in the linux-firmware package. Which the linux-firmware deb package is also a compress archive file. Because of the install/remove scripts and other included files in that .deb install package file, the size of it would actually be larger!

I feel like if you need either, those are your two options. And since your computer has problems with installing the linux-firmware package, you are down to that one option.

If you can't do either, I'm out of practical answers. There is another repo there , where you can download each file individually, and each file is small... But there are thousands of individual files there. Manually, that would result in more overall bandwidth, would take you over a year to do, and you would have to keep track of each file you downloaded, so you didn't skip any of those. That is just not a practical solution.

+1
less that 90 seconds for me:
```
cd Downloads && ls
"1.ALL DL's"   linux-firmware-20231211.tar.gz

```
```
gzip -l linux-firmware-20231211.tar.gz

         compressed        uncompressed  ratio uncompressed_name
          543112403          1118341120  51.4% linux-firmware-20231211.tar

```
Actual Download size as reported by MAFoElffen 
```
518.0*MiB (543,112,403 bytes)
```

---

### Post by josefranw on 2023-12-13
8-[

Well, the thing is I didn't exactly know how big the file was. The truth is that I tried downloading it several times, but my internet connection is not as stable as it should be and it kept dropping... and would never completely download the file...

To this point, I don't know if I'll be able to solve this issue which I don't exactly understand how it came to happen as it is a system update, not just any app I'm trying to install. How come the linux-firmware has conflicts with "another package" and can't be installed? and how come it happens only to me, apparently, if I am supposed to have and require the same files as any other person running the same version of xubuntu as me?

Well, I'll continue to try... and I appreciate your help.

---

### Post by MAFoElffen on 2023-12-13
Possibly, that might have been a problem with the original update <-- That your connection is bad, and when it did the update, that the package there was corrupted(?)

To retry that, you could do
```

sudo apt-get --download-only   -o Dir::Cache:archives=$HOME/Downloads/ install linux-firmware
ls $HOME/Downloads/linux-firmware*.deb
#use that full name in the next command
sudo dpkg -i $HOME/Downloads/<Deb_Full_Name>

```

---

### Post by josefranw on 2023-12-14
ls: cannot access '/home/josefranw/Downloads/linux-firmware*.deb': No such file or directory

---

### Post by josefranw on 2023-12-14
> **MAFoElffen said:**
> Possibly, that might have been a problem with the original update <-- That your connection is bad, and when it did the update, that the package there was corrupted(?)


If it were a cache thing, is there a way to delete that cache?

---

### Post by jeremy31 on 2023-12-14
Try removing firmware-ath9k-htc and then see if linux-firmware updates

---

### Post by MAFoElffen on 2023-12-14
> **jeremy31 said:**
> Try removing firmware-ath9k-htc and then see if linux-firmware updates
I recommended similar to that in post #2.

His system then error'ed with "another" file in the output in Post #4... It was like it just "adapted" the error. LOL

He was warned against removing linux-firmware (completely) as a package... but if he downloaded either the firmware blob from kernel.org, or the linux-firmware .deb archive file... I think he could actually delete all of the files & sub-directories /lib/firmware > replace them with the files from those... And get around this.

^^^ That is fairly much what we have been recommending since Post #5... In different ways. I different perspectives.

One on my published work-around for that is to just change the /linux/firmware folder name to anything else, un-archive the compressed firmware blob file as /lib/firmware.

If he had the linux-firmware-*.deb file downloaded, he could do the same and populate it again, with that...

---

### Post by jeremy31 on 2023-12-14
> **MAFoElffen said:**
> I recommended similar to that in post #2.

His system then error'ed with "another" file in the output in Post #4... It was like it just "adapted" the error. LOL

He was warned against removing linux-firmware (completely) as a package... but if he downloaded either the firmware blob from kernel.org, or the linux-firmware .deb archive file... I think he could actually delete all of the files & sub-directories /lib/firmware > replace them with the files from those... And get around this.

^^^ That is fairly much what we have been recommending since Post #5... In different ways. I different perspectives.

One on my published work-around for that is to just change the /linux/firmware folder name to anything else, un-archive the compressed firmware blob file as /lib/firmware.

If he had the linux-firmware-*.deb file downloaded, he could do the same and populate it again, with that...

What was in post #2 still left the package in the system and that is what I think is causing the problem as one file should only be in one package, but I could be way out in left field or even outside the stadium
I would figure that firmware-ath9k-htc contains firmware for some older Atheros USB wifi devices and if josefranw isn't using USB wifi there is no reason for that package to be installed.

---

### Post by MAFoElffen on 2023-12-14
> **jeremy31 said:**
> What was in post #2 still left the package in the system and that is what I think is causing the problem as one file should only be in one package, but I could be way out in left field or even outside the stadium
I would figure that firmware-ath9k-htc contains firmware for some older Atheros USB wifi devices and if josefranw isn't using USB wifi there is no reason for that package to be installed.
That is a different perspective and might work there... Very good idea!

---

### Post by josefranw on 2023-12-16
> **jeremy31 said:**
> Try removing firmware-ath9k-htc and then see if linux-firmware updates

It worked. Thanks. :KS

---

