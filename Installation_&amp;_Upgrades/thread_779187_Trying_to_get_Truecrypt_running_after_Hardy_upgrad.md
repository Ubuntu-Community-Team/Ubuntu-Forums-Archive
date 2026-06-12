---
title: "Trying to get Truecrypt running after Hardy upgrade"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by bpont on 2008-05-02
I've just completed a successful in-place upgrade to Hardy Heron, but now when I try to mount a truecrypt volume, I get this error:

```
FATAL: Module truecrypt not found.
Failed to load TrueCrypt kernel module
```

Please help...thanks

---

### Post by NIT006.5 on 2008-05-08
I'm having the same issue after Hardy upgrade.... thoughts please anyone?

---

### Post by capink on 2008-05-10
I believe both of you have the old version of truecrypt (version 4.3a). This version contain a kernel module that work only on the kernel it was compiled for. So a truecrypt 4.3a packages compiled for gutsy for example is not going to work for hardy because it has different kernel. And since truecrypt is not present in the ubuntu repositories, it is not updated with the rest of packages. There are two solutions to this situation:

1. Install the latest version of truecrypt. You can get the deb from the truecrypt site. The main advantage of the new version apart from having a GUI, is that it is not tied to specific kernel anymore (they have done away with the kernel module since they are using fuse now). So the next time you dist-upgrade Ubuntu you will not face this problem.

2. If you want to use the same version you have installed now for whatever reason (a lot of people complain of a slow write speed as well as other annoyances), you will have to recompile it against your current kernel source. You can get the source code of older versions form the truecrypt site. However, Before you compile it you need to install packages and apply a patch. Here is an outline of the steps (Note: I have not tried these steps myself):

[COLOR="Red"]Note: The steps below are for hardy or any other version using kernel 2.6.24[/COLOR]

[LIST]Install some packages:

```
sudo apt-get install build-essential dmsetup linux-source-2.6.24
```[/LIST]


[LIST]Unpack the kernel sources

```
cd /usr/src
```

```
sudo tar -xvjpf linux-source-2.6.24.tar.bz2
```

```
sudo ln -s linux-source-2.6.24 /usr/src/linux
```

```
sudo cp -av /boot/config-2.6.24-16-generic /usr/src/linux-source-2.6.24/.config
```

```
cd
```[/LIST]

[LIST]Download the truecrypt 4.3a source from [this page]("http://www.truecrypt.org/pastversions.php") to your home directory[/LIST]


[LIST]Extract the truecrypt source:

```
tar xvf ~/TrueCrypt4.3aSource.tar.gz -C ~
```

[COLOR=Red]Note: Modify the filename above to that of archive you downloaded[/COLOR][/LIST]

[LIST]Download the patch to your home directroy:

```
wget -c http://sources.gentoo.org/viewcvs.py/*checkout*/gentoo-x86/app-crypt/truecrypt/files/truecrypt-4.3a-2.6.24.patch?rev=1.2 -O ~/patch
```[/LIST]


[LIST]Apply the patch to the truecrypt source:

```
sudo patch -p0 -i ~/patch ~/truecrypt-4.3a-source-code/Linux/Kernel/Dm-target.c
```[/LIST]


[LIST]Compile and install truecrypt:

```
~/truecrypt-4.3a-source-code/Linux/build.sh
```

```
~/truecrypt-4.3a-source-code/Linux/install.sh
```[/LIST]

---

### Post by woliveirajr on 2008-06-06
It can be even easier: in the Truecrypt site, [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php) , you can download the last version (5.1a), which is kernel version independent.

You download it, extracts the files from the .tar.gz, and install it by clicking twice over truecrypt_5.1a-0_i386.deb .

---

