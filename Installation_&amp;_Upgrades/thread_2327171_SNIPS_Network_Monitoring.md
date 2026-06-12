---
title: "SNIPS Network Monitoring"
date: 2016-06-08
forum: Installation &amp; Upgrades
---

### Post by adam_hemsley on 2016-06-08
Hi All,

I'm very new to Ubuntu, however have chosen the OS due to the fact I needed a free Unix style platform to run a network monitor I'm trying out on ([http://www.netplex-tech.com/snips/](http://www.netplex-tech.com/snips/)).

I've been following this installation guide: [http://www.drdobbs.com/snips/199101437](http://www.drdobbs.com/snips/199101437)

When I try to run make I get: Makefile:16: *** missing separator. Stop.

I've included the full "./Configure" dialogue below.

Can anyone assist :) ?

Kind regards,

Adam

[EMAIL="adam@adam-ThinkPad-T440:/usr/local/src/snips-1.2$"]adam@adam-ThinkPad-T440:/usr/local/src/snips-1.2$[/EMAIL] sudo ./Configure [sudo] password for adam:
 
SET INSTALLATION DIRECTORY
  It is advisable to put all the SNIPS files under one directory
  tree with further sub-directories like bin/ etc/ lib/ man/
  This will allow easy upgrades and replacements of this software
  without leaving old unsed files lying around.
 
  However, the DATA and LOG directories will have files which are constantly
  updated by the monitors, and you might want to keep them separately under
  a VAR directory (or alternately create soft links to these directories).
Enter top level directory [/usr/local/snips]: /usr/local/snips Enter location of man pages [/usr/local/snips/man]: /usr/local/snips/man Enter extension for man pages [n]: n
 
  SNIPS sends regular operational email messages when a device goes
  critical, etc. It is advised to create a "snips-ops" email alias in
  your mail system.
  It also needs to send ADMIN messages (in case of wrong directory
  permissions, etc.) - preferably to a system administrator. An email
  alias such as "snips-admin" should be created.
 
Where is your MAIL program located? [/usr/bin/mail] :/usr/bin/thunderbird Where should the operational email go? [snips-ops@adam-ThinkPad-T440] :x.x@x.co.uk 
Where should the admin email go? [snips-admin@adam-ThinkPad-T440] :x.x@x.co.uk
 
Which compiler would you like to use? [gcc]: gcc What compiler options do you want (-DDEBUG)? [-O]: -DDEBUG What linker options do you want (-L/local/lib -lbind)? []: [] yacc NOT FOUND Enter an alternative to yacc [bison -y]: [bison -y]
 
                     RRDtool Graphing Support Do you have RRDtool installed ([www.caida.org]("http://www.caida.org"))? [n]: n
 
Detecting operating system dependencies for Linux 4.2.0-27-generic...
      OS=Linux 4.2.0-27-generic is not a supported or detected operating system. Try setting
      the value of OS manually to the type of your system or set the
      OS_CFLAGS and OS_LIBS value manually in the Makefile if compile fails.
 
         OS_CFLAGS =
         OS_LIBS   =
 
Saving all values in Config.cache...
Editing various Makefiles...
 
Done editing Makefiles.
 
               Type   "make"  to start building  SNIPS
 
[EMAIL="adam@adam-ThinkPad-T440:/usr/local/src/snips-1.2$"]adam@adam-ThinkPad-T440:/usr/local/src/snips-1.2$[/EMAIL] make
Makefile:16: *** missing separator. Stop.
[EMAIL="adam@adam-ThinkPad-T440:/usr/local/src/snips-1.2$"]adam@adam-ThinkPad-T440:/usr/local/src/snips-1.2$[/EMAIL]

---

### Post by Lea_Pulsen on 2016-06-09
Adam, I think you are missing some libraries, or maybe the gcc compilator itself?

Just my opinion here: I recommend not going into this direction, compiling your own monitoring software is somehow outdated. I'm not saying it's not useful, but you can really speed up the process by trying other Community alternatives such as Pandora FMS, their network and server monitoring features [http://pandorafms.com/monitoring-solutions/server-monitoring/](http://pandorafms.com/monitoring-solutions/server-monitoring/) are just outstanding.

However, what version of Ubuntu are you running? I suggest going to 14.04, it's not that new but it's a rock solid piece of OS :)[URL="http://pandorafms.com/monitoring-solutions/server-monitoring/"]

[/URL]

---

