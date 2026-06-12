---
title: "Installing Ingen"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by the_king_of_mars on 2010-02-17
Im using 9.04 jaunty. Also since i saw posts about installing skype and a bunch of other programs I just assumed this was the right place too put this thread. Also, if you're wondering, neither site has a forum I can post in and google didnt turn up much of use.

The program is from here [http://drobilla.net/software/ingen/](http://drobilla.net/software/ingen/)

I have followed the instructions here [http://dev.drobilla.net/wiki/IngenInstallation](http://dev.drobilla.net/wiki/IngenInstallation)

After installing the minimal, recommended, GUI requirements, the ./waf configure command outputs this;

```
:~/drobilla-lad$ ./waf configure
Checking for program gcc,cc                 : ok /usr/bin/gcc 
Checking for program cpp                    : ok /usr/bin/cpp 
Checking for program ar                     : ok /usr/bin/ar 
Checking for program ranlib                 : ok /usr/bin/ranlib 
Checking for gcc                            : ok  
Checking for program g++,c++                : ok /usr/bin/g++ 
Checking for g++                            : ok  
SLV2 Configuration 
Checking for redland >= 1.0.6               : ok 
Checking for jack >= 0.107.0                : ok 

Global configuration 
Install prefix                              : /usr/local 
Debuggable build                            : False 
Strict compiler flags                       : False 
Build documentation                         : False 

Jack clients                                : True 
Unit tests                                  : False 
Dynamic Manifest Support                    : False 

Raul Configuration 
Checking for glib-2.0 >= 2.2                : ok 
Checking for gthread-2.0 >= 2.14.0          : ok 
Checking for header boost/shared_ptr.hpp    : ok 
Checking for header boost/weak_ptr.hpp      : ok 
Checking for header boost/utility.hpp       : ok 

Unit tests                                  : False 

FlowCanvas Configuration 
Checking for libgvc >= 2.8                  : fail 
Checking for gtkmm-2.4 >= 2.10.0            : ok 
Checking for libgnomecanvasmm-2.6 >= 2.6.0  : ok 

Auto-arrange                                : False 
Anti-Aliasing                               : True 

Patchage Configuration 
Checking for dbus-1                         : not found 
Checking for dbus-glib-1                    : not found 
Checking for libglademm-2.4 >= 2.6.0        : ok 
Checking for gtkmm-2.4 >= 2.11.12           : ok 
Checking for alsa                           : not found 

Install name                                : 'patchage' 
App human name                              : 'Patchage' 
Jack (D-Bus)                                : False 
LASH (D-Bus)                                : False 
Jack (libjack)                              : True 
Alsa Sequencer                              : False 

Redlandmm Configuration 
Checking for raptor >= 1.4.18               : ok 
Checking for redland >= 1.0.8               : ok 

Ingen Configuration 
Checking for gtkmm-2.4 >= 2.14.0            : ok 
Checking for jack >= 0.109.0                : ok 
Checking for libxml-2.0 >= 2.6.0            : ok 
Checking for libsoup-2.4 >= 2.4.0           : fail 
Checking for header ladspa.h                : not found 
Checking for liblo >= 0.25                  : fail 
Checking for function posix_memalign        : ok 

Jack                                        : True 
OSC                                         : False 
HTTP                                        : False 
LV2                                         : True 
LADSPA                                      : False 
GUI                                         : True 

'configure' finished successfully (1.081s)
```Afterwards the ./waf command returns;

```
Waf: Entering directory `/home/daniel/drobilla-lad/build'
[ 49/203] cxx: ingen/src/engine/ConnectionImpl.cpp -> build/default/ingen/src/engine/ConnectionImpl_1.o
[ 51/203] cxx: ingen/src/engine/DuplexPort.cpp -> build/default/ingen/src/engine/DuplexPort_1.o
../ingen/src/engine/ConnectionImpl.cpp: In member function &#8216;void Ingen::ConnectionImpl::apply_poly(Raul::Maid&, uint32_t)&#8217;:
../ingen/src/engine/ConnectionImpl.cpp:100:17: error: &#8216;class boost::intrusive_ptr<Ingen::Buffer>&#8217; has no member named &#8216;reset&#8217;
Waf: Leaving directory `/home/daniel/drobilla-lad/build'
Build failed
 -> task failed (err #1): 
    {task: cxx ConnectionImpl.cpp -> ConnectionImpl_1.o}
```I have no idea what this means.

I'm assuming the problem has something too do with me not setting any option in the configuration part of the steps but, nothing really stands out too me as something that should be activated.

---

