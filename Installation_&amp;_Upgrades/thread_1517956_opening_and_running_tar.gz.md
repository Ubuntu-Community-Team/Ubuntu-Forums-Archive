---
title: "opening and running tar.gz"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by alperkayisi on 2010-06-25
Hey guys,

I am new at using ubuntu. I have a proble w installing and running tar.gz files. I found some article about tar.gz files all says that I have to extract it with this command "  tar -xvfz gtk+-2.20.0.tar.gz " ( my file name is gtk+-2.20.0.tar.gz )
but I got this error. 

tar: z: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

When I check the location of my file, I see that under "/" . I also tried to with this command " cd / " and then " tar -xvfz gtk+-2.20.0.tar " but still doesn't work 

and can u describe how can I run it. What does ./configure mean . How ubuntu understand that I want to run gtk+-2.20.0.tar.gz file . Because according to my information when I extract the files I have follow this command 

$ ./configure
$ make
$ sudo make install
can u help me out . By the way, sorry about my silly question. I am new at using ubuntu as I said u before :)

---

### Post by darkod on 2010-06-25
It's easier to do the extracting in graphical mode. Just use Places and navigate to the folder where the downloaded tar.gz is. Right-click on it and select Open with Archive Manager. In the new window you will have Extract button.

Usually when it extracts it will create new folder similar to the filename. Depending on the full instructions, you would usually have to use the terminal and go inside this new folder and there you execute the commands you wrote. 
That is how it will know what you want to run. You will already be in the folder where the files have extracted.

---

### Post by alperkayisi on 2010-06-25
OK I extract it. It is located under /home/al/indirilenler and then I go to terminal and type

al@ubuntu:~$ cd /home/al/&#304;ndirilenler
al@ubuntu:~/&#304;ndirilenler$ ./configure
bash: ./configure: No such file or directory
al@ubuntu:~/&#304;ndirilenler$ ./configure                    
bash: ./configure: No such file or directory                ./configure didn't work I just skip it
al@ubuntu:~/&#304;ndirilenler$ make
make: *** No targets specified and no makefile found.  Stop.
al@ubuntu:~/&#304;ndirilenler$ sudo make install
[sudo] password for al: 
make: *** No rule to make target `install'.  Stop.

---

### Post by darkod on 2010-06-25
Did you install the packages needed for building like that? I think you need to do first:

sudo apt-get install build-essentials

That will install everything needed. Try again after that. I don't know that much about compiling like this.

---

### Post by alperkayisi on 2010-06-25
I see my fault I go inside my folder and then I run ./configure command It works but I got this error ; I want to run waterfall-0.11

al@ubuntu:~/&#304;ndirilenler/waterfall-0.11$ ./configure
loading cache ./config.cache
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking host system type... Invalid configuration `x86_64-unknown-linux-gnu': machine `x86_64-unknown' not recognized

checking build system type... Invalid configuration `x86_64-unknown-linux-gnu': machine `x86_64-unknown' not recognized

checking for ranlib... (cached) ranlib
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for ld used by GCC... (cached) /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... (cached) yes
checking for BSD-compatible nm... (cached) /usr/bin/nm -B
checking whether ln -s works... (cached) yes
loading cache ./config.cache within ltconfig
ltconfig: you must specify a host type if you use `--no-verify'
Try `ltconfig --help' for more information.
configure: error: libtool configure failed
alper@ubuntu:~/&#304;ndirilenler/waterfall-0.11$ make  **** I try to use make command But I got error *******
make: *** No targets specified and no makefile found.  Stop.
al@ubuntu:~/&#304;ndirilenler/waterfall-0.11$

---

