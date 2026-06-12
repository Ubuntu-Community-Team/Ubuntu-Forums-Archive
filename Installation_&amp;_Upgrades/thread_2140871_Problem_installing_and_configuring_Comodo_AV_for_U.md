---
title: "Problem installing and configuring Comodo AV for Ubuntu 13.04 64b"
date: 2013-04-30
forum: Installation &amp; Upgrades
---

### Post by gorski on 2013-04-30
...Comodo anti-virus for Linux Ubuntu 13.04 64b from here...

[http://www.comodo.com/home/download/download.php?prod=antivirus-for-linux&track=3646&key5sk1=014459d8df16ed39163de29eefde4499013607ba&key5sk2=&key5sk3=1367373740000&key5sk4=3646&key5sk5=1367373760000&key6sk1=&key6sk2=FF200&key6sk3=8&key6sk4=en-us&key6sk5=LU&key6sk6=1&key6sk7=http%3A%2F%2Fwww.comodo.com%2Fhome%2Finternet-security%2Fantivirus-for-linux.php&key6sk8=112202&key6sk9=1366768&key6sk10=false&key6sk11=91c17620bc13254eeb1da8dfa1c563a2787a78cc&key6sk12=2034&key7sk1=204398&key1sk1=dt&key1sk2=http%3A%2F%2Fwww.comodo.com%2Fhome%2Finternet-security%2Fantivirus-for-linux.php](http://www.comodo.com/home/download/download.php?prod=antivirus-for-linux&track=3646&key5sk1=014459d8df16ed39163de29eefde4499013607ba&key5sk2=&key5sk3=1367373740000&key5sk4=3646&key5sk5=1367373760000&key6sk1=&key6sk2=FF200&key6sk3=8&key6sk4=en-us&key6sk5=LU&key6sk6=1&key6sk7=http%3A%2F%2Fwww.comodo.com%2Fhome%2Finternet-security%2Fantivirus-for-linux.php&key6sk8=112202&key6sk9=1366768&key6sk10=false&key6sk11=91c17620bc13254eeb1da8dfa1c563a2787a78cc&key6sk12=2034&key7sk1=204398&key1sk1=dt&key1sk2=http%3A%2F%2Fwww.comodo.com%2Fhome%2Finternet-security%2Fantivirus-for-linux.php)

...gives me the following, once I follow the steps given by the app in the terminal:

```
sudo make -C /lib/modules/`uname -r`/build M=/tmp/driver/redirfs modules
make: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
/usr/src/linux-headers-3.8.0-19-generic/arch/x86/Makefile:103: CONFIG_X86_X32 enabled but no binutils support
scripts/Makefile.build:44: /tmp/driver/redirfs/Makefile: No such file or directory
make[1]: *** No rule to make target `/tmp/driver/redirfs/Makefile'.  Stop.
make: *** [_module_/tmp/driver/redirfs] Error 2
make: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'
```

i.e.

```
sudo make -C /lib/modules/`uname -r`/build M=/tmp/driver/redirfs modules
make: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
scripts/Makefile.build:44: /tmp/driver/redirfs/Makefile: No such file or directory
make[1]: *** No rule to make target `/tmp/driver/redirfs/Makefile'.  Stop.
make: *** [_module_/tmp/driver/redirfs] Error 2
make: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'

sudo make -C /lib/modules/`uname -r`/build M=/tmp/driver/redirfs modules
make: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
scripts/Makefile.build:44: /tmp/driver/redirfs/Makefile: No such file or directory
make[1]: *** No rule to make target `/tmp/driver/redirfs/Makefile'.  Stop.
make: *** [_module_/tmp/driver/redirfs] Error 2
make: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'

make: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
> /usr/src/linux-headers-3.8.0-19-generic/arch/x86/Makefile:103: CONFIG_X86_X32 enabled but no binutils support
> scripts/Makefile.build:44: /tmp/driver/redirfs/Makefile: No such file or directory
> make[1]: *** No rule to make target `/tmp/driver/redirfs/Makefile'.  Stop.
> make: *** [_module_/tmp/driver/redirfs] Error 2
> make: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'
bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 5: syntax error: unexpected end of file
No command 'make:' found, did you mean:
 Command 'makeg' from package 'xutils-dev' (main)
 Command 'make' from package 'make' (main)
make:: command not found
```

OK, I am patient and I do as I'm told - but this is my limit in IT, as I am from Humanities...

Please, guide me carefully towards solving the problem...

Thanx!

---

