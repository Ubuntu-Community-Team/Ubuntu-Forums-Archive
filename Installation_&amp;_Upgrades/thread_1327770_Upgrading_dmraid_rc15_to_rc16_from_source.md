---
title: "Upgrading dmraid rc15 to rc16 from source"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by giyad on 2009-11-15
I have the .tar.bz2 of dmraid rc16 that I got from [here ]("http://people.redhat.com/%7Eheinzm/sw/dmraid/")and I already have rc15 installed.  I want to know how to upgrade the package from this source file?

I got these steps from [here ]("http://people.redhat.com/heinzm/sw/dmraid/readme")
> to build in an empty directory and install from source

tar jxvf dmraid-1.0.0.rc16.tar.bz2
./configure	# see ./configure --help for options
make
make install


but I'm running into problems, can someone simplify them for me? (Linux noob here)

---

### Post by giyad on 2009-11-16
In case this helps, its my output from following the commands above:

```
ziyad@DesktopzUbuntu:~/Desktop/dmraid/1.0.0.rc16$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for gawk... no
checking for mawk... mawk
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... yes
checking for ranlib... ranlib
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking for unistd.h... (cached) yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for off_t... yes
checking for pid_t... yes
checking for size_t... yes
checking for struct stat.st_rdev... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether to enable debugging... 
no
checking whether to enable malloc debugging... 
no
checking whether to disable native metadata logging... 
yes
checking whether to disable testing with mapped devices... 
no
checking whether gcc needs -traditional... no
checking return type of signal handlers... void
checking for vprintf... yes
checking for _doprnt... no
checking for mkdir... yes
checking for rmdir... yes
checking for uname... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
configure: creating ./config.status
config.status: creating include/Makefile
config.status: creating lib/Makefile
config.status: creating man/Makefile
config.status: creating tools/Makefile
config.status: creating tools/version.h
config.status: creating Makefile
config.status: creating make.tmpl
config.status: WARNING:  make.tmpl.in seems to ignore the --datarootdir setting
ziyad@DesktopzUbuntu:~/Desktop/dmraid/1.0.0.rc16$ make
make -C include
make[1]: Entering directory `/home/ziyad/Desktop/dmraid/1.0.0.rc16/include'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/ziyad/Desktop/dmraid/1.0.0.rc16/include'
make -C lib
make[1]: Entering directory `/home/ziyad/Desktop/dmraid/1.0.0.rc16/lib'
gcc -MM -MF activate/devmapper.d -I. -I../include -I../lib -O2 -DDMRAID_NATIVE_LOG -DHAVE_GETOPTLONG -fPIC -Wall -Wundef -Wcast-align -Wwrite-strings -Winline -DDMRAID_TEST -DDMRAID_AUTOREGISTER -O2 -D_LARGEFILE64_SOURCE activate/devmapper.c; \
    gcc -c -I. -I../include -I../lib -O2 -DDMRAID_NATIVE_LOG -DHAVE_GETOPTLONG -fPIC -Wall -Wundef -Wcast-align -Wwrite-strings -Winline -DDMRAID_TEST -DDMRAID_AUTOREGISTER -O2 -D_LARGEFILE64_SOURCE activate/devmapper.c -o activate/devmapper.o
activate/devmapper.c:15:26: error: libdevmapper.h: No such file or directory
activate/devmapper.c: In function ‘mkdm_path’:
activate/devmapper.c:34: warning: implicit declaration of function ‘dm_dir’
activate/devmapper.c:34: warning: initialization makes pointer from integer without a cast
activate/devmapper.c: In function ‘_init_dm’:
activate/devmapper.c:55: warning: implicit declaration of function ‘dm_log_init’
activate/devmapper.c: At top level:
activate/devmapper.c:60: warning: ‘struct dm_task’ declared inside parameter list
activate/devmapper.c:60: warning: its scope is only this definition or declaration, which is probably not what you want
activate/devmapper.c: In function ‘_exit_dm’:
activate/devmapper.c:63: warning: implicit declaration of function ‘dm_task_destroy’
activate/devmapper.c:65: warning: implicit declaration of function ‘dm_lib_release’
activate/devmapper.c:66: warning: implicit declaration of function ‘dm_lib_exit’
activate/devmapper.c: In function ‘get_target_list’:
activate/devmapper.c:79: warning: implicit declaration of function ‘dm_task_create’
activate/devmapper.c:79: error: ‘DM_DEVICE_LIST_VERSIONS’ undeclared (first use in this function)
activate/devmapper.c:79: error: (Each undeclared identifier is reported only once
activate/devmapper.c:79: error: for each function it appears in.)
activate/devmapper.c:79: warning: assignment makes pointer from integer without a cast
activate/devmapper.c:80: warning: implicit declaration of function ‘dm_task_run’
activate/devmapper.c:80: warning: implicit declaration of function ‘dm_task_get_versions’
activate/devmapper.c:80: warning: pointer/integer type mismatch in conditional expression
activate/devmapper.c: In function ‘valid_ttype’:
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:104: error: dereferencing pointer to incomplete type
activate/devmapper.c: At top level:
activate/devmapper.c:117: warning: ‘struct dm_task’ declared inside parameter list
activate/devmapper.c: In function ‘handle_table’:
activate/devmapper.c:141: warning: implicit declaration of function ‘dm_task_add_target’
activate/devmapper.c: At top level:
activate/devmapper.c:151: warning: ‘struct dm_task’ declared inside parameter list
activate/devmapper.c: In function ‘parse_table’:
activate/devmapper.c:153: warning: passing argument 2 of ‘handle_table’ from incompatible pointer type
activate/devmapper.c: In function ‘run_task’:
activate/devmapper.c:194: warning: assignment makes pointer from integer without a cast
activate/devmapper.c:194: warning: implicit declaration of function ‘dm_task_set_name’
activate/devmapper.c:196: warning: passing argument 2 of ‘parse_table’ from incompatible pointer type
activate/devmapper.c:199: error: ‘DM_DEVICE_CREATE’ undeclared (first use in this function)
activate/devmapper.c:201: warning: implicit declaration of function ‘dm_task_set_uuid’
activate/devmapper.c:206: warning: passing argument 1 of ‘_exit_dm’ from incompatible pointer type
activate/devmapper.c: In function ‘dm_create’:
activate/devmapper.c:217: error: ‘DM_DEVICE_CREATE’ undeclared (first use in this function)
activate/devmapper.c: In function ‘dm_suspend’:
activate/devmapper.c:234: error: ‘DM_DEVICE_SUSPEND’ undeclared (first use in this function)
activate/devmapper.c: In function ‘dm_resume’:
activate/devmapper.c:242: error: ‘DM_DEVICE_RESUME’ undeclared (first use in this function)
activate/devmapper.c: In function ‘dm_reload’:
activate/devmapper.c:252: error: ‘DM_DEVICE_RELOAD’ undeclared (first use in this function)
activate/devmapper.c: In function ‘dm_remove’:
activate/devmapper.c:269: error: ‘DM_DEVICE_REMOVE’ undeclared (first use in this function)
activate/devmapper.c: In function ‘dm_status’:
activate/devmapper.c:279: error: storage size of ‘info’ isn’t known
activate/devmapper.c:284: error: ‘DM_DEVICE_STATUS’ undeclared (first use in this function)
activate/devmapper.c:284: warning: assignment makes pointer from integer without a cast
activate/devmapper.c:286: warning: implicit declaration of function ‘dm_task_get_info’
activate/devmapper.c:287: warning: passing argument 1 of ‘_exit_dm’ from incompatible pointer type
activate/devmapper.c:279: warning: unused variable ‘info’
activate/devmapper.c: In function ‘dm_version’:
activate/devmapper.c:303: error: ‘DM_DEVICE_VERSION’ undeclared (first use in this function)
activate/devmapper.c:303: warning: assignment makes pointer from integer without a cast
activate/devmapper.c:305: warning: implicit declaration of function ‘dm_task_get_driver_version’
activate/devmapper.c:306: warning: passing argument 1 of ‘_exit_dm’ from incompatible pointer type
make[1]: *** [activate/devmapper.o] Error 1
make[1]: Leaving directory `/home/ziyad/Desktop/dmraid/1.0.0.rc16/lib'
make: *** [lib] Error 2

ziyad@DesktopzUbuntu:~/Desktop/dmraid/1.0.0.rc16$ sudo make
make -C include
make[1]: Entering directory `/home/ziyad/Desktop/dmraid/1.0.0.rc16/include'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/ziyad/Desktop/dmraid/1.0.0.rc16/include'
make -C lib
make[1]: Entering directory `/home/ziyad/Desktop/dmraid/1.0.0.rc16/lib'
gcc -MM -MF activate/devmapper.d -I. -I../include -I../lib -O2 -DDMRAID_NATIVE_LOG -DHAVE_GETOPTLONG -fPIC -Wall -Wundef -Wcast-align -Wwrite-strings -Winline -DDMRAID_TEST -DDMRAID_AUTOREGISTER -O2 -D_LARGEFILE64_SOURCE activate/devmapper.c; \
    gcc -c -I. -I../include -I../lib -O2 -DDMRAID_NATIVE_LOG -DHAVE_GETOPTLONG -fPIC -Wall -Wundef -Wcast-align -Wwrite-strings -Winline -DDMRAID_TEST -DDMRAID_AUTOREGISTER -O2 -D_LARGEFILE64_SOURCE activate/devmapper.c -o activate/devmapper.o
activate/devmapper.c:15:26: error: libdevmapper.h: No such file or directory
activate/devmapper.c: In function ‘mkdm_path’:
activate/devmapper.c:34: warning: implicit declaration of function ‘dm_dir’
activate/devmapper.c:34: warning: initialization makes pointer from integer without a cast
activate/devmapper.c: In function ‘_init_dm’:
activate/devmapper.c:55: warning: implicit declaration of function ‘dm_log_init’
activate/devmapper.c: At top level:
activate/devmapper.c:60: warning: ‘struct dm_task’ declared inside parameter list
activate/devmapper.c:60: warning: its scope is only this definition or declaration, which is probably not what you want
activate/devmapper.c: In function ‘_exit_dm’:
activate/devmapper.c:63: warning: implicit declaration of function ‘dm_task_destroy’
activate/devmapper.c:65: warning: implicit declaration of function ‘dm_lib_release’
activate/devmapper.c:66: warning: implicit declaration of function ‘dm_lib_exit’
activate/devmapper.c: In function ‘get_target_list’:
activate/devmapper.c:79: warning: implicit declaration of function ‘dm_task_create’
activate/devmapper.c:79: error: ‘DM_DEVICE_LIST_VERSIONS’ undeclared (first use in this function)
activate/devmapper.c:79: error: (Each undeclared identifier is reported only once
activate/devmapper.c:79: error: for each function it appears in.)
activate/devmapper.c:79: warning: assignment makes pointer from integer without a cast
activate/devmapper.c:80: warning: implicit declaration of function ‘dm_task_run’
activate/devmapper.c:80: warning: implicit declaration of function ‘dm_task_get_versions’
activate/devmapper.c:80: warning: pointer/integer type mismatch in conditional expression
activate/devmapper.c: In function ‘valid_ttype’:
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:104: error: dereferencing pointer to incomplete type
activate/devmapper.c: At top level:
activate/devmapper.c:117: warning: ‘struct dm_task’ declared inside parameter list
activate/devmapper.c: In function ‘handle_table’:
activate/devmapper.c:141: warning: implicit declaration of function ‘dm_task_add_target’
activate/devmapper.c: At top level:
activate/devmapper.c:151: warning: ‘struct dm_task’ declared inside parameter list
activate/devmapper.c: In function ‘parse_table’:
activate/devmapper.c:153: warning: passing argument 2 of ‘handle_table’ from incompatible pointer type
activate/devmapper.c: In function ‘run_task’:
activate/devmapper.c:194: warning: assignment makes pointer from integer without a cast
activate/devmapper.c:194: warning: implicit declaration of function ‘dm_task_set_name’
activate/devmapper.c:196: warning: passing argument 2 of ‘parse_table’ from incompatible pointer type
activate/devmapper.c:199: error: ‘DM_DEVICE_CREATE’ undeclared (first use in this function)
activate/devmapper.c:201: warning: implicit declaration of function ‘dm_task_set_uuid’
activate/devmapper.c:206: warning: passing argument 1 of ‘_exit_dm’ from incompatible pointer type
activate/devmapper.c: In function ‘dm_create’:
activate/devmapper.c:217: error: ‘DM_DEVICE_CREATE’ undeclared (first use in this function)
activate/devmapper.c: In function ‘dm_suspend’:
activate/devmapper.c:234: error: ‘DM_DEVICE_SUSPEND’ undeclared (first use in this function)
activate/devmapper.c: In function ‘dm_resume’:
activate/devmapper.c:242: error: ‘DM_DEVICE_RESUME’ undeclared (first use in this function)
activate/devmapper.c: In function ‘dm_reload’:
activate/devmapper.c:252: error: ‘DM_DEVICE_RELOAD’ undeclared (first use in this function)
activate/devmapper.c: In function ‘dm_remove’:
activate/devmapper.c:269: error: ‘DM_DEVICE_REMOVE’ undeclared (first use in this function)
activate/devmapper.c: In function ‘dm_status’:
activate/devmapper.c:279: error: storage size of ‘info’ isn’t known
activate/devmapper.c:284: error: ‘DM_DEVICE_STATUS’ undeclared (first use in this function)
activate/devmapper.c:284: warning: assignment makes pointer from integer without a cast
activate/devmapper.c:286: warning: implicit declaration of function ‘dm_task_get_info’
activate/devmapper.c:287: warning: passing argument 1 of ‘_exit_dm’ from incompatible pointer type
activate/devmapper.c:279: warning: unused variable ‘info’
activate/devmapper.c: In function ‘dm_version’:
activate/devmapper.c:303: error: ‘DM_DEVICE_VERSION’ undeclared (first use in this function)
activate/devmapper.c:303: warning: assignment makes pointer from integer without a cast
activate/devmapper.c:305: warning: implicit declaration of function ‘dm_task_get_driver_version’
activate/devmapper.c:306: warning: passing argument 1 of ‘_exit_dm’ from incompatible pointer type
make[1]: *** [activate/devmapper.o] Error 1
make[1]: Leaving directory `/home/ziyad/Desktop/dmraid/1.0.0.rc16/lib'
make: *** [lib] Error 2

ziyad@DesktopzUbuntu:~/Desktop/dmraid/1.0.0.rc16$ sudo make install
make -C include
make[1]: Entering directory `/home/ziyad/Desktop/dmraid/1.0.0.rc16/include'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/ziyad/Desktop/dmraid/1.0.0.rc16/include'
make -C lib
make[1]: Entering directory `/home/ziyad/Desktop/dmraid/1.0.0.rc16/lib'
gcc -MM -MF activate/devmapper.d -I. -I../include -I../lib -O2 -DDMRAID_NATIVE_LOG -DHAVE_GETOPTLONG -fPIC -Wall -Wundef -Wcast-align -Wwrite-strings -Winline -DDMRAID_TEST -DDMRAID_AUTOREGISTER -O2 -D_LARGEFILE64_SOURCE activate/devmapper.c; \
    gcc -c -I. -I../include -I../lib -O2 -DDMRAID_NATIVE_LOG -DHAVE_GETOPTLONG -fPIC -Wall -Wundef -Wcast-align -Wwrite-strings -Winline -DDMRAID_TEST -DDMRAID_AUTOREGISTER -O2 -D_LARGEFILE64_SOURCE activate/devmapper.c -o activate/devmapper.o
activate/devmapper.c:15:26: error: libdevmapper.h: No such file or directory
activate/devmapper.c: In function ‘mkdm_path’:
activate/devmapper.c:34: warning: implicit declaration of function ‘dm_dir’
activate/devmapper.c:34: warning: initialization makes pointer from integer without a cast
activate/devmapper.c: In function ‘_init_dm’:
activate/devmapper.c:55: warning: implicit declaration of function ‘dm_log_init’
activate/devmapper.c: At top level:
activate/devmapper.c:60: warning: ‘struct dm_task’ declared inside parameter list
activate/devmapper.c:60: warning: its scope is only this definition or declaration, which is probably not what you want
activate/devmapper.c: In function ‘_exit_dm’:
activate/devmapper.c:63: warning: implicit declaration of function ‘dm_task_destroy’
activate/devmapper.c:65: warning: implicit declaration of function ‘dm_lib_release’
activate/devmapper.c:66: warning: implicit declaration of function ‘dm_lib_exit’
activate/devmapper.c: In function ‘get_target_list’:
activate/devmapper.c:79: warning: implicit declaration of function ‘dm_task_create’
activate/devmapper.c:79: error: ‘DM_DEVICE_LIST_VERSIONS’ undeclared (first use in this function)
activate/devmapper.c:79: error: (Each undeclared identifier is reported only once
activate/devmapper.c:79: error: for each function it appears in.)
activate/devmapper.c:79: warning: assignment makes pointer from integer without a cast
activate/devmapper.c:80: warning: implicit declaration of function ‘dm_task_run’
activate/devmapper.c:80: warning: implicit declaration of function ‘dm_task_get_versions’
activate/devmapper.c:80: warning: pointer/integer type mismatch in conditional expression
activate/devmapper.c: In function ‘valid_ttype’:
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:100: error: dereferencing pointer to incomplete type
activate/devmapper.c:104: error: dereferencing pointer to incomplete type
activate/devmapper.c: At top level:
activate/devmapper.c:117: warning: ‘struct dm_task’ declared inside parameter list
activate/devmapper.c: In function ‘handle_table’:
activate/devmapper.c:141: warning: implicit declaration of function ‘dm_task_add_target’
activate/devmapper.c: At top level:
activate/devmapper.c:151: warning: ‘struct dm_task’ declared inside parameter list
activate/devmapper.c: In function ‘parse_table’:
activate/devmapper.c:153: warning: passing argument 2 of ‘handle_table’ from incompatible pointer type
activate/devmapper.c: In function ‘run_task’:
activate/devmapper.c:194: warning: assignment makes pointer from integer without a cast
activate/devmapper.c:194: warning: implicit declaration of function ‘dm_task_set_name’
activate/devmapper.c:196: warning: passing argument 2 of ‘parse_table’ from incompatible pointer type
activate/devmapper.c:199: error: ‘DM_DEVICE_CREATE’ undeclared (first use in this function)
activate/devmapper.c:201: warning: implicit declaration of function ‘dm_task_set_uuid’
activate/devmapper.c:206: warning: passing argument 1 of ‘_exit_dm’ from incompatible pointer type
activate/devmapper.c: In function ‘dm_create’:
activate/devmapper.c:217: error: ‘DM_DEVICE_CREATE’ undeclared (first use in this function)
activate/devmapper.c: In function ‘dm_suspend’:
activate/devmapper.c:234: error: ‘DM_DEVICE_SUSPEND’ undeclared (first use in this function)
activate/devmapper.c: In function ‘dm_resume’:
activate/devmapper.c:242: error: ‘DM_DEVICE_RESUME’ undeclared (first use in this function)
activate/devmapper.c: In function ‘dm_reload’:
activate/devmapper.c:252: error: ‘DM_DEVICE_RELOAD’ undeclared (first use in this function)
activate/devmapper.c: In function ‘dm_remove’:
activate/devmapper.c:269: error: ‘DM_DEVICE_REMOVE’ undeclared (first use in this function)
activate/devmapper.c: In function ‘dm_status’:
activate/devmapper.c:279: error: storage size of ‘info’ isn’t known
activate/devmapper.c:284: error: ‘DM_DEVICE_STATUS’ undeclared (first use in this function)
activate/devmapper.c:284: warning: assignment makes pointer from integer without a cast
activate/devmapper.c:286: warning: implicit declaration of function ‘dm_task_get_info’
activate/devmapper.c:287: warning: passing argument 1 of ‘_exit_dm’ from incompatible pointer type
activate/devmapper.c:279: warning: unused variable ‘info’
activate/devmapper.c: In function ‘dm_version’:
activate/devmapper.c:303: error: ‘DM_DEVICE_VERSION’ undeclared (first use in this function)
activate/devmapper.c:303: warning: assignment makes pointer from integer without a cast
activate/devmapper.c:305: warning: implicit declaration of function ‘dm_task_get_driver_version’
activate/devmapper.c:306: warning: passing argument 1 of ‘_exit_dm’ from incompatible pointer type
make[1]: *** [activate/devmapper.o] Error 1
make[1]: Leaving directory `/home/ziyad/Desktop/dmraid/1.0.0.rc16/lib'
make: *** [lib] Error 2

```

---

### Post by giyad on 2009-11-16
no one can help me out?

---

### Post by giyad on 2009-11-17
seriously.. no one knows how to install from source...

---

### Post by giyad on 2009-11-24
bump

---

### Post by Ralf.P on 2009-12-12
You have the answer in the output. Check the lines where an error occures. At first glance I noticed the line

activate/devmapper.c:15:26: error: libdevmapper.h: No such file or directory

so the Header-File(s) of the essential devicemapper can't be found.
First make shure that all source packages are installed. Use the package manager and search for devmapper. Normally the sources are not installed by default.
 I have no Linux here, but I think you then find it in /usr/lib or just run a find command. Now you can copy them to the lib (include) directory you are using in the Makefile  ../dmraid/1.0.0.rc16/include/dmraid or you advise the Makefile to use the existing directory.

The next problem you would run into is, that the Header-Files are there but the Objects-Files not. Just do the same, copy them to ../dmraid/1.0.0.rc16/lib or include the existing directory.

You will need the libdevmapper and libdevmapper-event Header- and Object-Files to succesfully finish the recompilation

I will look this over when I'am back on a Linux on Monday, Excuse if there are any errors. I've done this by heart. Just follow the output error messages and you'll get through.

---

