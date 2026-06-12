---
title: "Problem in installation omnet3.4b2 on ubuntu9.04"
date: 2010-07-11
forum: Installation &amp; Upgrades
---

### Post by imz76 on 2010-07-11
I have problem in installation of omnet3.4b2 on ubuntu9.04.

./configure was successful

however after i typed, make, i got the following errors

cd /home/ikrami/downloads/omnetpp-3.4b2/src/sim && make
make[1]: Entering directory `/home/ikrami/downloads/omnetpp-3.4b2/src/sim'
g++ -c -O2 -DNDEBUG=1   -DWITH_PARSIM -DWITH_NETBUILDER -I/home/ikrami/downloads/omnetpp-3.4b2/include -I. -DBUILDING_SIM -I /usr/include  -I../nedxml -o sim_std_m.o sim_std_m.cc
In file included from sim_std_m.cc:13:
/home/ikrami/downloads/omnetpp-3.4b2/include/carray.h:59: warning: ‘cBag’ is deprecated (declared at /home/ikrami/downloads/omnetpp-3.4b2/include/carray.h:43)
/home/ikrami/downloads/omnetpp-3.4b2/include/carray.h:77: warning: ‘cBag’ is deprecated (declared at /home/ikrami/downloads/omnetpp-3.4b2/include/carray.h:43)
/home/ikrami/downloads/omnetpp-3.4b2/include/carray.h:77: warning: ‘cBag’ is deprecated (declared at /home/ikrami/downloads/omnetpp-3.4b2/include/carray.h:43)
/home/ikrami/downloads/omnetpp-3.4b2/include/carray.h: In member function ‘virtual cPolymorphic* cBag::dup() const’:
/home/ikrami/downloads/omnetpp-3.4b2/include/carray.h:87: warning: ‘cBag’ is deprecated (declared at /home/ikrami/downloads/omnetpp-3.4b2/include/carray.h:43)
In file included from sim_std_m.cc:14:
/home/ikrami/downloads/omnetpp-3.4b2/include/ctypes.h: At global scope:
/home/ikrami/downloads/omnetpp-3.4b2/include/ctypes.h:472: warning: ‘cLinkType’ is deprecated (declared at /home/ikrami/downloads/omnetpp-3.4b2/include/ctypes.h:452)
/home/ikrami/downloads/omnetpp-3.4b2/include/ctypes.h:482: warning: ‘cLinkType’ is deprecated (declared at /home/ikrami/downloads/omnetpp-3.4b2/include/ctypes.h:452)
/home/ikrami/downloads/omnetpp-3.4b2/include/ctypes.h:482: warning: ‘cLinkType’ is deprecated (declared at /home/ikrami/downloads/omnetpp-3.4b2/include/ctypes.h:452)
/home/ikrami/downloads/omnetpp-3.4b2/include/ctypes.h: In member function ‘virtual cPolymorphic* cLinkType::dup() const’:
/home/ikrami/downloads/omnetpp-3.4b2/include/ctypes.h:492: warning: ‘cLinkType’ is deprecated (declared at /home/ikrami/downloads/omnetpp-3.4b2/include/ctypes.h:452)
In file included from /home/ikrami/downloads/omnetpp-3.4b2/include/omnetpp.h:45,
                 from sim_std_m.h:8,
                 from sim_std_m.cc:23:
/home/ikrami/downloads/omnetpp-3.4b2/include/cpacket.h: At global scope:
/home/ikrami/downloads/omnetpp-3.4b2/include/cpacket.h:54: warning: ‘cPacket’ is deprecated (declared at /home/ikrami/downloads/omnetpp-3.4b2/include/cpacket.h:36)
/home/ikrami/downloads/omnetpp-3.4b2/include/cpacket.h:60: warning: ‘cPacket’ is deprecated (declared at /home/ikrami/downloads/omnetpp-3.4b2/include/cpacket.h:36)
/home/ikrami/downloads/omnetpp-3.4b2/include/cpacket.h:60: warning: ‘cPacket’ is deprecated (declared at /home/ikrami/downloads/omnetpp-3.4b2/include/cpacket.h:36)
/home/ikrami/downloads/omnetpp-3.4b2/include/cpacket.h: In member function ‘virtual cPolymorphic* cPacket::dup() const’:
/home/ikrami/downloads/omnetpp-3.4b2/include/cpacket.h:70: warning: ‘cPacket’ is deprecated (declared at /home/ikrami/downloads/omnetpp-3.4b2/include/cpacket.h:36)
sim_std_m.cc: In member function ‘virtual bool cPacketDescriptor::doesSupport(cPolymorphic*)’:
sim_std_m.cc:2801: warning: ‘cPacket’ is deprecated (declared at /home/ikrami/downloads/omnetpp-3.4b2/include/cpacket.h:36)
sim_std_m.cc: In member function ‘virtual int cPacketDescriptor::getArraySize(void*, int)’:
sim_std_m.cc:2893: warning: ‘cPacket’ is deprecated (declared at /home/ikrami/downloads/omnetpp-3.4b2/include/cpacket.h:36)
sim_std_m.cc:2893: warning: ‘cPacket’ is deprecated (declared at /home/ikrami/downloads/omnetpp-3.4b2/include/cpacket.h:36)
sim_std_m.cc: In member function ‘virtual bool cPacketDescriptor::getFieldAsString(void*, int, int, char*, int)’:
sim_std_m.cc:2907: warning: ‘cPacket’ is deprecated (declared at /home/ikrami/downloads/omnetpp-3.4b2/include/cpacket.h:36)
sim_std_m.cc:2907: warning: ‘cPacket’ is deprecated (declared at /home/ikrami/downloads/omnetpp-3.4b2/include/cpacket.h:36)
sim_std_m.cc: In member function ‘virtual bool cPacketDescriptor::setFieldAsString(void*, int, int, const char*)’:
sim_std_m.cc:2923: warning: ‘cPacket’ is deprecated (declared at /home/ikrami/downloads/omnetpp-3.4b2/include/cpacket.h:36)
sim_std_m.cc:2923: warning: ‘cPacket’ is deprecated (declared at /home/ikrami/downloads/omnetpp-3.4b2/include/cpacket.h:36)
sim_std_m.cc: In member function ‘virtual void* cPacketDescriptor::getFieldStructPointer(void*, int, int)’:
sim_std_m.cc:2952: warning: ‘cPacket’ is deprecated (declared at /home/ikrami/downloads/omnetpp-3.4b2/include/cpacket.h:36)
sim_std_m.cc:2952: warning: ‘cPacket’ is deprecated (declared at /home/ikrami/downloads/omnetpp-3.4b2/include/cpacket.h:36)
sim_std_m.cc: In member function ‘virtual void* cDensityEstBaseDescriptor::getFieldStructPointer(void*, int, int)’:
sim_std_m.cc:3742: warning: taking address of temporary

The errors show cBag, cPacket, cLinkType are deprecated. I tried putting these declarations on each problematic cc files

#include <fstream>
#include <iostream>
#include <sstream>
#include <cstdlib>
#include <cstring>
#include <iterator>
#include <algorithm>
#include <memory>

It works on some files but not on sim_std_m.cc. gcc version is 4.4.3.3-1ubuntu1, please help.

---

