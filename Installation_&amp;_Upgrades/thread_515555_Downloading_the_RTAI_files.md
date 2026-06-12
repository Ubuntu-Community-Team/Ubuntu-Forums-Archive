---
title: "Downloading the RTAI files"
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by green_gal on 2007-08-02
hello. i could not find how to install **rtai-3.1.tar.bz2** . the website provided ([www.rtai.org](www.rtai.org)) have that installation. but when i installed and run it in terminal using this command **bunzip2 rtai-3.1.tar.bz2**  i received this message **bunzip2: Can't open input file rtai-3.1.tar.bz2: No such file or directory.** why is it that? i have put it under my directory.

can anybody help me?

---

### Post by dreadlord_chris on 2007-08-02
> **green_gal said:**
> hello. i could not find how to install **rtai-3.1.tar.bz2** . the website provided ([www.rtai.org](www.rtai.org)) have that installation. but when i installed and run it in terminal using this command **bunzip2 rtai-3.1.tar.bz2**  i received this message **bunzip2: Can't open input file rtai-3.1.tar.bz2: No such file or directory.** why is it that? i have put it under my directory.

can anybody help me?

you're not runnung that command from where you downloaded the file too:
```

ls -la | grep rtai

```
is there any output from that command?

---

### Post by green_gal on 2007-08-02
thanks for the reply!

i tried that command already. anyway, let me show you what i type:

manet@manet-desktop:~$ cd /home/manet/kernel/
manet@manet-desktop:~/kernel$ ls
linux-2.6.8.1  rtai-3.1.tar-3
manet@manet-desktop:~/kernel$ ls -la | grep rtai
-rw-------  1 manet manet 21452800 2007-08-02 17:39 rtai-3.1.tar-3
manet@manet-desktop:~/kernel$ bunzip2 rtai-3.1.tar.bz2
bunzip2: Can't open input file rtai-3.1.tar.bz2: No such file or directory.
manet@manet-desktop:~/kernel$


is the commands i typed correct? if its not, can you tell me what commands to type? because i really don't understand linux commands that well. thanks.

---

### Post by dreadlord_chris on 2007-08-02
> **green_gal said:**
> thanks for the reply!

i tried that command already. anyway, let me show you what i type:

manet@manet-desktop:~$ cd /home/manet/kernel/
manet@manet-desktop:~/kernel$ ls
linux-2.6.8.1  rtai-3.1.tar-3
manet@manet-desktop:~/kernel$ ls -la | grep rtai
-rw-------  1 manet manet 21452800 2007-08-02 17:39 rtai-3.1.tar-3
manet@manet-desktop:~/kernel$ bunzip2 rtai-3.1.tar.bz2
bunzip2: Can't open input file rtai-3.1.tar.bz2: No such file or directory.
manet@manet-desktop:~/kernel$


is the commands i typed correct? if its not, can you tell me what commands to type? because i really don't understand linux commands that well. thanks.

well first off there is no file in that folder named **rtai-3.1.tar.bz2**, which tells you why your bunzip2 command gives you the error message it does...
but there is a file called **rtai-3.1.tar-3** - are you sure you didn't already bunzip2 the file? I suspect that you have - try this:
```

tar xvf rtai-3.1.tar-3

```

if that works then:
```

cd rtai-3.1/
less README.INSTALL

```

---

### Post by green_gal on 2007-08-03
i have tried the commands you gave me. 

yes, it worked but what commands do i type after **less README.INSTALL**? i still couldn't put in **bunzip2 rtai-3.1.tar.bz2**? 

i wannted to follow these steps and as you can see i am stuck at the **bunzip** part. why is it?

                     **Unpack and uncompress the files (section 3.5)**
cd /home/ks/kernel/RTAI
bunzip2 rtai-3.1.tar.bz2
bunzip2 linux-2.6.8.1.tar.bz2
tar –xf rtai-3.1.tar
tar –xf linux-2.6.8.1.tar

                  **Apply the RTAI patch to the Linux source (section 3.6)**
cd linux-2.6.8.1
patch –p1 < ../rtai-3.1/rtai-core/arch/i386/patches/hal7-2.6.8.1.patch
                         
                  **Configure the Linux kernel (section 3.7)**
cp arch/i386/defconfig .config
make oldconfig
make xconfig

                           **Build the Linux kernel (section 3.8)**
make clean
make bzImage
make modules

                           **Install the Linux kernel (section 3.9)**
su
make modules-install
mkinitrd /boot/initrd-2.6.8.1-adeos.img 2.6.8.1-adeos
cp arch/i386/boot/bzImage /boot/vmlinuz-2.6.8.1-adeos
cp System.map /boot/System.map-2.6.8.1-adeos
ln –s /boot/System.map-2.6.8.1-adeos /boot/System.map
cd /boot/grub
vi menu.lst
exit

                              **Configure RTAI (section 3.10)**
cd /home/ks/kernel/RTAI
mkdir rtai-build
cd rtai-build
make –f ../rtai-3.1/makefile xconfig

                                **Build RTAI (section 3.11)**
make

                             **   Install RTAI (section 3.12)**
su
make install

                                    **Reboot (section 3.13)**
shutdown –r now

                                ** Test RTAI (section 3.14)**
su
cd /usr/realtime/testsuite/kern/latency
./run

---

### Post by dreadlord_chris on 2007-08-03
Again, you already bunzip2'd the files - at some point in your attempts you were sucessful. The file **rtai-3.1.tar-3 and linux-2.6.8.1** are the results of that command. The next step is to untar those files.
First off, if you don't know what a command does you can find out by (from a terminal):
```

man commandname

```
i.e.
**man bunzip2** will open the manual page for the bunzip2 command, where it tells you that bunzip2 is a compression program (similiar to WinZip in Windows)

I got to tell you - it's really not a good idea to be running commands in the terminal when you don't understand what they or you are doing. The issues you are having are fairly basic and could be avoided with a little reading on your part:
[http://www.linuxcommand.org/learning_the_shell.php]("http://www.linuxcommand.org/learning_the_shell.php")

Honestly, what your trying to do is a fairly advanced process (recompiling your kernel) - it really shouldn't even be attempted without a thourough understanding of what's involved (this includes **all** the steps)

---

