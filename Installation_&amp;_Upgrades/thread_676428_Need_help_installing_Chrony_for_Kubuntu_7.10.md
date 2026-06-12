---
title: "Need help installing Chrony for Kubuntu 7.10"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by klw1026 on 2008-01-23
[COLOR="Blue"]** Where to begin?  First I tried using adept to install chrony.  This did not do what I think it should of, missing files etc (well I think so).  Then I went and got the source code and followed the instructions to install.  Here is what I did:[/COLOR]

tar -zxvf chrony-1.16.tar.gz

./configure --prefix /usr/local

make

[COLOR="Blue"]** This is were I started getting some errors.  So then I remembered about the previous installation of chrony via adept and tried to remove it.  This did not work since some file the remover (aptitude) was looking for was not there.  So I simply added a blank document to this location and it appeared to remove chrony.  Then tried installing form the source code again but ran into the same problems.  Needless to say I have done this several times and right now I am currently supposed to have chrony installed via adept, which doesn't work, and trying to install from the source code.  I did however see others having problems with read-line (or something like that) and to use --[/COLOR]

./configure --disable-readline

[COLOR="Blue"]** and this is what I got back[/COLOR]
| klw1026 ~/desktop/chrony-1.23 > ./configure --disable-readline
./configure: 293: EXTRA_OBJECTS+= rtc_linux.o: not found
./configure: 293: EXTRA_DEFS+= -DFEAT_RTC=1: not found
Configuring for  Linux-i686
Checking if sqrt() needs -lm : Yes
Checking for <stdint.h> : Yes
Checking for <inttypes.h> : Yes

[COLOR="Blue"]** then i tried[/COLOR]

make

[COLOR="Blue"]** and this is what i got back[/COLOR]
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H  -c client.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c getdate.c
getdate.y:634: warning: ‘gd_error’ was used with no prototype before its definition
getdate.y:808: warning: ‘gd_lex’ was used with no prototype before its definition
gcc -O2 -g  -o chronyc client.o md5.o nameserv.o getdate.o cmdparse.o pktlength.o  -lm

[COLOR="Blue"]** can anyone please help.  Thanks[/COLOR]

---

### Post by zvacet on 2008-01-24
Go to the folder from wich you are trying to compile and run 

```
sudo make clean
```

That will remove all you done and you can start fresh.Maybe tis command will help you 

```
auto-apt run ./configure --prefix /usr/local
```

---

### Post by klw1026 on 2008-01-24
[COLOR="Blue"]** Thanks for the suggestion.  So I went into the chrony-1.23 directory and typed[/COLOR]

sudo make clean

[COLOR="Blue"]** and this is what happened[/COLOR]
rm -f *.o *.s chronyc chronyd core *~

[COLOR="Blue"]** Then I had to get auto-apt since it was not installed.  So, after typing sudo apt-get install auto-apt, I typed the command[/COLOR]

auto-apt run ./configure --prefix /usr/local

[COLOR="Blue"]** and got this back[/COLOR]
Entering auto-apt mode: ./configure --prefix /usr/local
Exit the command to leave auto-apt mode.
Unrecognized option :  --prefix
Unrecognized option :  /usr/local
./configure: 293: EXTRA_OBJECTS+= rtc_linux.o: not found
./configure: 293: EXTRA_DEFS+= -DFEAT_RTC=1: not found
Configuring for  Linux-i686
Checking if sqrt() needs -lm : Yes
Checking for <stdint.h> : Yes
Checking for <inttypes.h> : Yes

[COLOR="Blue"]** So, maybe a good question would be why it does not recognize the option --prefix /usr/local?  I have seen many places say to use this option but it soes not work for me.  I think that if I use --prefix=/usr/local that it does work, well i don't get the same message[/COLOR]

auto-apt run ./configure --prefix=/usr/local

[COLOR="Blue"]** and it says this[/COLOR]
Entering auto-apt mode: ./configure --prefix=/usr/local
Exit the command to leave auto-apt mode.
./configure: 293: EXTRA_OBJECTS+= rtc_linux.o: not found
./configure: 293: EXTRA_DEFS+= -DFEAT_RTC=1: not found
Configuring for  Linux-i686
Checking if sqrt() needs -lm : Yes
Checking for <stdint.h> : Yes
Checking for <inttypes.h> : Yes

[COLOR="Blue"]** I have no idea what the two EXTRA things are that it cannot find.  Maybe this is the problem.  Anyway I went ahead a tried to install.  Next I typed [/COLOR]

ls

[COLOR="Blue"]** to have a look at the files and got this back (sorry don't know how to align in table format)[/COLOR]
acquire.c       client.c     INSTALL      memory.h       reference.c    sys.c
acquire.h       clientlog.c  io_linux.h   mkdirpp.c      reference.h    sys.h
addressing.h    clientlog.h  keys.c       mkdirpp.h      regress.c      sysincl.h
addrfilt.c      cmdmon.c     keys.h       mkversion      regress.h      sys_linux.c
addrfilt.h      cmdmon.h     local.c      nameserv.c     reports.h      sys_linux.h
broadcast.c     cmdparse.c   local.h      nameserv.h     rtc.c          sys_netbsd.c
broadcast.h     cmdparse.h   localp.h     NEWS           rtc.h          sys_netbsd.h
candm.h         conf.c       logging.c    ntp_core.c     rtc_linux.c    sys_solaris.c
chrony.1        conf.h       logging.h    ntp_core.h     rtc_linux.h    sys_solaris.h
chronyc.1       configure    main.c       ntp.h          sched.c        sys_sunos.c
chrony.conf.5   contrib      main.h       ntp_io.c       sched.h        sys_sunos.h
chronyd.8       COPYING      Makefile     ntp_io.h       sources.c      util.c
chrony.lsm      examples     Makefile.in  ntp_sources.c  sources.h      util.h
chrony.spec     faqgen.pl    manual.c     ntp_sources.h  sourcestats.c  version.h
chrony.texi     faq.txt      manual.h     pktlength.c    sourcestats.h  version.txt
chrony_timex.h  getdate.c    md5.c        pktlength.h    srcparams.h    wrap_adjtimex.c
chrony.txt      getdate.h    md5.h        README         strerror.c     wrap_adjtimex.h

[COLOR="Blue"]** Then i typed[/COLOR]

make

[COLOR="Blue"]** and got this back[/COLOR]
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c util.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c sched.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c regress.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c local.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c sys.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c main.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c ntp_io.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c ntp_core.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c ntp_sources.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c sources.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c sourcestats.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c reference.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c logging.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c conf.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c cmdmon.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c md5.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c keys.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c nameserv.c
nameserv.c: In function ‘DNS_Name2IPAddress’:
nameserv.c:49: warning: pointer targets in assignment differ in signedness
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c acquire.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c manual.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c addrfilt.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c cmdparse.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c mkdirpp.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c rtc.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c pktlength.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c clientlog.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c broadcast.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c sys_linux.c
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -c wrap_adjtimex.c
gcc -O2 -g  -o chronyd util.o sched.o regress.o local.o sys.o main.o ntp_io.o ntp_core.o ntp_sources.o sources.o sourcestats.o reference.o logging.o conf.o cmdmon.o md5.o keys.o nameserv.o acquire.o manual.o addrfilt.o cmdparse.o mkdirpp.o rtc.o pktlength.o clientlog.o broadcast.o sys_linux.o wrap_adjtimex.o -lm
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -DFEAT_READLINE=1  -c client.c
client.c:44:31: error: readline/readline.h: No such file or directory
client.c:45:30: error: readline/history.h: No such file or directory
client.c: In function ‘read_line’:
client.c:117: warning: implicit declaration of function ‘readline’
client.c:117: warning: assignment makes pointer from integer without a cast
client.c:124: warning: implicit declaration of function ‘add_history’
make: *** [client.o] Error 1

[COLOR="Blue"]** So then I tagain yped[/COLOR]

make

[COLOR="Blue"]** And got this back[/COLOR]
gcc -Wmissing-prototypes -Wall -O2 -g  -DLINUX -DHAS_STDINT_H -DHAS_INTTYPES_H -DFEAT_READLINE=1  -c client.c
client.c:44:31: error: readline/readline.h: No such file or directory
client.c:45:30: error: readline/history.h: No such file or directory
client.c: In function ‘read_line’:
client.c:117: warning: implicit declaration of function ‘readline’
client.c:117: warning: assignment makes pointer from integer without a cast
client.c:124: warning: implicit declaration of function ‘add_history’
make: *** [client.o] Error 1

[COLOR="Blue"]** Finally I tried[/COLOR]

sudo install

[COLOR="Blue"]** and it said[/COLOR]
install: missing file operand
Try `install --help' for more information.

[COLOR="Blue"]** Don't know what to try next.[/COLOR]

---

### Post by zvacet on 2008-01-24
> This did not do what I think it should of, missing files etc (well I think so). 

If you have all repos open (chek in system<administration>software sources>chek all under Ubuntu software and under updates tab.Reload.)Find chrony in adept and install it.You can see [here](http://packages.ubuntu.com/) all chrony dependencies(of course you will type chrony in search box and select your version).

---

### Post by klw1026 on 2008-01-24
[COLOR="Blue"]** I made sure that I had all the dependencies and then went and had all Kubuntu software and updates checked and then I installed chrony.  Now, when I give the shell the command chronyc it comes up but I can't get it to do anything.  If I give it a command that it recognizes then it just gives a blank line and then no matter what I type as soon as I hit return it just gives another blank line.  This was happening before when I had previously tried to install it.  Then I went back to the source code and again tried to install and it gave the same errors for the make command.  What should I do next.  Thanks.[/COLOR]

---

### Post by zvacet on 2008-01-24
You can try with typing** man chrony** or **chrony --help** to see how it works.

---

### Post by klw1026 on 2008-01-24
[COLOR="Blue"]** I think that something has gone completely wrong.  I went into man chrony, man chronyc, and man chronyd.  The man chronyc told me were to find the list commands supported by chronyc but could not find this file and when I typed locate chronyc it came back blank.  Then man chronyd told me where to find and run chronyd but when I went there it was not there and locate chronyd found nothing as well.  Have you tried to install chrony?  If so was it with Kubuntu 7.10?  Also, if you were successful were did you get the package or source code?  Thanks for the help and I apologize for being so computer illiterate.[/COLOR]

---

### Post by zvacet on 2008-01-24
No,I never used that package,but from descrription in synaptic chronyd is a deamon runing in background.

> Thanks for the help and I apologize for being so computer illiterate

No need for apologize,and for illiterate it looks that at least are two of us.Sorry,if I´m not much of help.Maybe someone else will give you informations you need.

---

### Post by klw1026 on 2008-01-25
[COLOR="Blue"]** UPDATE:  Well maybe.  So I tried another time to install chrony on my machine that is running Kubuntu 7.10 (Gusty).  I went and downloaded the source from the chrony homepage.  Then expanded it and cd into the directory where I typed ./configure then the dreaded make command.  This time I think I got the same problems but instead of typing just install I type sudo make install and got[/COLOR]

[ -d /usr/local ] || mkdir -p /usr/local
[ -d /usr/local/sbin ] || mkdir -p /usr/local/sbin
[ -d /usr/local/bin ] || mkdir -p /usr/local/bin
[ -d /usr/local/doc ] || mkdir -p /usr/local/doc
[ -d /usr/local/man/man1 ] || mkdir -p /usr/local/man/man1
[ -d /usr/local/man/man5 ] || mkdir -p /usr/local/man/man5
[ -d /usr/local/man/man8 ] || mkdir -p /usr/local/man/man8
[ -d /usr/local/doc/chrony ] || mkdir -p /usr/local/doc/chrony
if [ -f /usr/local/sbin/chronyd ]; then rm -f /usr/local/sbin/chronyd ; fi
if [ -f /usr/local/bin/chronyc ]; then rm -f /usr/local/bin/chronyc ; fi
cp chronyd /usr/local/sbin/chronyd
chmod 555 /usr/local/sbin/chronyd
cp chronyc /usr/local/bin/chronyc
chmod 555 /usr/local/bin/chronyc
cp chrony.txt /usr/local/doc/chrony/chrony.txt
chmod 444 /usr/local/doc/chrony/chrony.txt
cp COPYING /usr/local/doc/chrony/COPYING
chmod 444 /usr/local/doc/chrony/COPYING
cp README /usr/local/doc/chrony/README
chmod 444 /usr/local/doc/chrony/README
cp chrony.1 /usr/local/man/man1
chmod 444 /usr/local/man/man1/chrony.1
cp chronyc.1 /usr/local/man/man1
chmod 444 /usr/local/man/man1/chronyc.1
cp chronyd.8 /usr/local/man/man8
chmod 444 /usr/local/man/man8/chronyd.8
cp chrony.conf.5 /usr/local/man/man5
chmod 444 /usr/local/man/man5/chrony.conf.5

[COLOR="Blue"]** Then I went and typed chronyc and password and I kept getting the command line that does not echo anything back and just lets you type whatever you want without saying anything, been here before.  Then for some reason before I typed chronyc again in a new shell I typed chronyd then chronyc.  Now it seems to be working however I can't get the password to work.  I have the /etc/chrony/chrony.conf file with the proper commands and the /etc/chrony/chrony.keys file.  But when I try password this is what happens[/COLOR]

> chronyc
chrony version 1.23, copyright (C) 1997-2002 Richard P. Curnow
chrony comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions.
See the GNU General Public License version 2 for details.

chronyc> password
Password:
501 Not authorised --- Reply not authenticated
chronyc> password
Password:
501 Not authorised --- Reply not authenticated
chronyc> password
Password:
501 Not authorised --- Reply not authenticated
chronyc>   

[COLOR="Blue"]** Any suggestions would be greatly appreciated.[/COLOR]

---

