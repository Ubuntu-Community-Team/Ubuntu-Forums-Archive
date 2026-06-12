---
title: "Installing compiling and installing TOR software on Xubuntu 6.10 problem"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by RedStickHam on 2007-02-06
I'm a Linux newbie trying out the OS for the first time.  After much research, I went with Xubuntu 6.10 because of the lightweight XFCE desktop.  Anyway, here is my question:

I found a more recent version of TOR than was in the repositories available directly from EFF in a tar.gz, aka tarball file.  I downloaded and uncompressed it and attempted to complie and/or install it and I keep getting error messages.  I tried as both a regular user and under SUDO and had no luck.  The issues seem to be with openSSL and makeinfo.  openSSL is installed on my system, but I can't find makeinfo in the repository using Synaptic if that is indeed the problem.

I could just go with the older version for now I know, but I really want to learn how to do this.  I'm currently a Windows XP user and not knowing how long my OS will be supported and seeing what they've done with Vista, I'm seriously considering a switchover to Linux.

The output from the terminal is below and I would appreciate any guidance.  Thank you.

kb5iav@kb5iav:~$ cd /home/kb5iav/Desktop/tor-0.1.1.26 
kb5iav@kb5iav:~/Desktop/tor-0.1.1.26$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking build system type... i586-pc-linux-gnu
checking host system type... i586-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking whether make sets $(MAKE)... (cached) yes
checking for ranlib... ranlib
checking for library containing socket... none required
checking for library containing gethostbyname... none required
checking for library containing dlopen... -ldl
checking for library containing pthread_create... -lpthread
checking for library containing pthread_detach... none required
checking for libevent directory... (system)
checking whether we need extra options to link libevent... (none)
checking for OpenSSL directory... configure: error: Could not find a linkable OpenSSL. You can specify an explicit path using --with-ssl-dir
kb5iav@kb5iav:~/Desktop/tor-0.1.1.26$ ./configure && make
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking build system type... i586-pc-linux-gnu
checking host system type... i586-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking whether make sets $(MAKE)... (cached) yes
checking for ranlib... ranlib
checking for library containing socket... none required
checking for library containing gethostbyname... none required
checking for library containing dlopen... -ldl
checking for library containing pthread_create... -lpthread
checking for library containing pthread_detach... none required
checking for libevent directory... (system)
checking whether we need extra options to link libevent... (none)
checking for OpenSSL directory... configure: error: Could not find a linkable OpenSSL. You can specify an explicit path using --with-ssl-dir
kb5iav@kb5iav:~/Desktop/tor-0.1.1.26$

---

### Post by emattic on 2007-02-06
Hi, I have been thinking about installing Tor in the next few days on Edgy 6.10 and have been doing some research here in the forums. I have not come up with much info. I am new to Linux also and am interested in how this turns out for you.

I don't know if this will help you but look in the Synaptic Package Manager for a package called "automake" take note there are a few different versions listed.

As for ssl all I know is that it means Secure Socket Layer. How do you know that you have it installed? Is the package you have called "openssl" thats what was preconfigured on my Ubuntu install.

I would install the automake packgage then try to install Tor maybe it will also solve your ssl problem.

What version did you download from Eff?

Good Luck let me know the outcome

---

