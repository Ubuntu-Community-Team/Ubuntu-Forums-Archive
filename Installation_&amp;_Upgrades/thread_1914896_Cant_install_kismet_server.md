---
title: "Cant install kismet server"
date: 2012-01-25
forum: Installation &amp; Upgrades
---

### Post by rmortim on 2012-01-25
Hi
I am trying to Install a kismet drone on my wrt54gl and the server on ubuntu 11.10 using kismet-2005-06-R1.I have got the drone working and running(as seen below).

But have a issue when trying to install the server package. Not to sure if its still having a problem with configure or the make commands. I do apologise as im a noob with linux and still trying to learn my ways


root@DD-WRT:~# /tmp/kismet_drone
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Disabling channel hopping.
Source 0 (Kismet-Drone): Enabling monitor mode for wrt54g source interface prism0 channel 0...
Source 0 (Kismet-Drone): Opening wrt54g source interface prism0...
NOTICE: bind address not specified, using INADDR_ANY.
Kismet Drone 2005.06.R1 (Kismet)
Listening on port 3501 (protocol 9).
Allowing connections from 127.0.0.1/255.255.255.255
Allowing connections from 10.0.0.0/255.255.255.0



Below is the configure and make results from terminal




checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... yes
checking how to run the C preprocessor... gcc -E
checking for platform-specific compiler flags... none needed
checking whether byte ordering is bigendian... no
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking for unistd.h... (cached) yes
checking for sys/types.h... (cached) yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking for an ANSI C-conforming const... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for ANSI C header files... (cached) yes
checking return type of signal handlers... void
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking for gettimeofday... yes
checking for memset... yes
checking for select... yes
checking for socket... yes
checking for strcasecmp... yes
checking for strftime... yes
checking for strstr... yes
checking for system-level getopt_long()... yes
checking for stdint.h... (cached) yes
checking for accept() addrlen type... socklen_t
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking for _LARGE_FILES value needed for large files... no
checking for group 'root'... yes
checking for group 'man'... checking for initscr in -lncurses... yes
checking for new_panel in -lpanel... yes
checking for assume_default_colors in -lncurses... yes
checking for linux/netlink.h... no
configure: WARNING: *** Missing Linux netlink headers.  wlanng_legacy source will not be built. ***
checking for linux/wireless.h... no
configure: WARNING: *** Missing Linux Wireless kernel extentions.  The majority of packet sources on Linux require this support and will not work without it.  Make sure your kernel header packages are installed.  If all else fails, try the --with-linuxheaders directive. ***
checking for radiotap support... checking for setuid ... yes
checking for glib-config... no
configure: WARNING: Could not find glib-config in /usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games.  glib is required to link to wiretap.
configure: WARNING: *** Wiretap support disabled.  While Kismet will function without wiretap, it will limit the log reading and writing abilities. ***
checking for XML_GetCurrentLineNumber in -lexpat... no
configure: WARNING: *** Missing Expat XML library.  gpsmap will not be built. ***
checking gmp.h usability... no
checking gmp.h presence... no
checking for gmp.h... no
configure: WARNING: *** Missing GMP math library.  gpsmap will not be built. ***
checking for wget... yes
checking for Magick-config... no
configure: WARNING: *** Missing Magick-config (or it is not in the path).  gpsmap will not be built. ***
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for pthread_create in -lpthread... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating scripts/kismet
config.status: creating extra/buzzme/Makefile
config.status: creating extra/Makefile
config.status: creating conf/kismet.conf
config.status: creating conf/kismet_ui.conf
config.status: creating config.h
configure: configuring in libpcap-0.9.1-kis
configure: running /bin/bash './configure' --prefix=/usr/local  --cache-file=/dev/null --srcdir=.
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking gcc version... 4
checking for inline... inline
checking for __attribute__... no
checking for u_int8_t using gcc... yes
checking for u_int16_t using gcc... yes
checking for u_int32_t using gcc... yes
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking sys/ioccom.h usability... no
checking sys/ioccom.h presence... no
checking for sys/ioccom.h... no
checking sys/sockio.h usability... no
checking sys/sockio.h presence... no
checking for sys/sockio.h... no
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for netinet/if_ether.h... yes
checking for ANSI ioctl definitions... yes
checking for strerror... yes
checking for strlcpy... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for library containing gethostbyname... none required
checking for library containing socket... none required
checking for library containing putmsg... none required
checking for ether_hostton... yes
checking whether ether_hostton is declared... no
checking netinet/ether.h usability... yes
checking netinet/ether.h presence... yes
checking for netinet/ether.h... yes
checking whether ether_hostton is declared... yes
checking if --disable-protochain option is specified... enabled
checking packet capture type... linux
checking for getifaddrs... yes
checking ifaddrs.h usability... yes
checking ifaddrs.h presence... yes
checking for ifaddrs.h... yes
checking if --enable-ipv6 option is specified... no
checking whether to build optimizer debugging code... no
checking whether to build parser debugging code... no
checking Linux kernel version... 3
checking if if_packet.h has tpacket_stats defined... yes
checking whether we have /proc/net/dev... yes
checking whether we have DAG API headers... no (/usr/local/include)
checking for ranlib... ranlib
checking if sockaddr struct has sa_len member... no
checking if sockaddr_storage struct exists... yes
checking if dl_hp_ppa_info_t struct has dl_module_id_1 member... no
checking if unaligned accesses fail... no
checking for a BSD-compatible install... /usr/bin/install -c
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h

Configuration complete: 
         Compiling for: linux-gnu (x86_64)
   Installing as group: root
    Man pages owned by: man
       Installing into: /usr/local
        Setuid capable: yes
         Zaurus extras: no
      Terminal Control: ncurses
      Curses interface: yes
      Panels interface: yes
 Linux Netlink capture: no
       Linux wireless : no
 Linux wireless v.22+ : no
          pcap capture: yes
           pcap source: libpcap-0.9.1-kis
        WSP100 capture: no
          Viha capture: no
      Radiotap headers: no
 Using local dump code: yes
Using ethereal wiretap: no
   Imagemagick support: no
         Expat Library: no
           GMP Library: no
       PThread Support: yes
      libz compression: no
*** WARNING ***
Linux Wireless Extentions were not found.  This means that they are not
turned on in your kernel or that your kernel source include paths on your
distribution are broken (namely, that linux/wireless.h didn't exist or
was unuseable).  Without wireless extentions, most of the commonly used
packet sources (such as Cisco, Orinoco, Madwifi, Prism54, and others)
WILL NOT BE BUILT.
*** WARNING ***

Configuration complete.  Run 'make dep' to generate dependencies
and 'make' followed by 'make install' to compile and install.

gunners@AFC:~/Downloads/kismet-2005-06-R1$ make dep
Makefile:371: .depend: No such file or directory
Generating dependencies... 
make[1]: Entering directory `/home/gunners/Downloads/kismet-2005-06-R1'
make[2]: Entering directory `/home/gunners/Downloads/kismet-2005-06-R1'
make[2]: `.depend' is up to date.
make[2]: Leaving directory `/home/gunners/Downloads/kismet-2005-06-R1'
make[1]: Leaving directory `/home/gunners/Downloads/kismet-2005-06-R1'



gunners@AFC:~/Downloads/kismet-2005-06-R1$ make
g++ -Ilibpcap-0.9.1-kis -O2 -Wall -DVERSION_MAJOR=\"2005\" -DVERSION_MINOR=\"06\" -DVERSION_TINY=\"R1\" -DTIMESTAMP=\"`cat TIMESTAMP`\" -g -O2 -g -O2 -c util.cc -o util.o 
In file included from util.cc:21:0:
util.h:68:2: warning: ‘typedef’ was ignored in this declaration [enabled by default]
util.cc: In function ‘int Hex2UChar(unsigned char*, unsigned char*)’:
util.cc:116:57: error: ‘memset’ was not declared in this scope
util.cc: In function ‘int RunSysCmd(char*)’:
util.cc:251:19: warning: ignoring return value of ‘int system(const char*)’, declared with attribute warn_unused_result [-Wunused-result]
make: *** [util.o] Error 1



Thank you for taking the time to read through this, Any help would be greatly appreciated as im not sure where the issue is lying.

Thanks again :)

---

### Post by lukeiamyourfather on 2012-01-25
Don't double post. Especially don't triple post. [-X

---

### Post by rmortim on 2012-01-25
Sorry was not sure which section to post in? Ill try remove the other posts

---

### Post by Elfy on 2012-01-25
Thread closed. Please do not post duplicates, it dilutes community effort.

---

