---
title: "Undervolt AMD Turion X2 64bit RM-72"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by francismorales on 2010-10-09
I'm a windows 7 user. I have ubuntu 10.10 on dual boot.
      Specifications: Turion X2 RM-72, 4gb ram, ATI Mobility 3200

I'm looking for a way to undervolt my Turion in Ubuntu 10.10

I've downloaded TPC (Turion Power Control) but don't know how to use the tar.gz file.

Steps taken:

1. I have the build essentials installed

2. I've been to tutorials on using ./configure, make, and checkinstall, but the extracted folder (tpc-0.29pa.tar.gz) doesn't have that configure file
           
        List of Files 

AthlonQL.h
Griffin.cpp       
scaler.cpp
compile_i386.sh    
K10.h             
scaler.h
compile.sh~        
K10Processor.cpp  
TurionPowerControl.cpp
compile_x86-64.sh  
OlsApi.h          
TurionPowerControl.cpp~
config.cpp         
OlsDef.h          
TurionPowerControl.h
config.cpp~        
Processor.cpp     
TurionRM.h
config.h           
Processor.cpp~    
TurionZM.h
cpuPrimitives.cpp  
Processor.h
cpuPrimitives.h    
Processor.h~

 
3. The tutorials i've been too is more on _how to make it work_ ( [http://www.phoronix.com/scan.php?page=news_item&px=ODY2MA](http://www.phoronix.com/scan.php?page=news_item&px=ODY2MA) ), but _no step by step usage on the tar.gz file_. 

4. I've been googled my way into this for the last 5 days, but can't find any.

..I'm a newbie (5 days old in ubuntu), 13 years in windows using k10stat for undervoltin. so i think i just don't know what i'm looking for.

Can somebody point me to the right direction? I'd be more than greatful.

---

### Post by andrewthomas on 2010-10-09
> To compile a AMD64 (or x86-64, 64 bit) version, put yourself in src folder and issue:
chmod +x compile_x86*64.sh
./compile_x86*64.sh
Then you'll find a nice and compiled TurionPowerControl executable inside ./bin directory.
If you find troubles or strange errors when you launch the software, keep in mind you have to be
superuser to access and manipulate processor features.
You may also encounter errors about retrieving CPUID informations or access to cpu MSRs, so be
sure that your system has the required cpuid and cpumsr modules loaded (if they are not yet
compiled inside your kernel). You can load them issuing (always as a superuser):
modprobe cpuid
modprobe msr
If you still can't load these modules, check that your distribution come with them, else I think you
can download them using your distribution favourite package manager.
I've been told also of some compiling errors, expecially in function perfCounterMonitor about
printf function. I'm not sure, but it may be related to the specific version of gcc you're running
(4.4.1), so please update your gcc compiler suite and retry compilation.


I attached the .pdf

---

### Post by francismorales on 2010-10-10
I'm getting these warnings.


Griffin.cpp: In member function &#8216;virtual void Griffin::perfCounterGetValue(int, int)&#8217;:
Griffin.cpp:999: warning: format &#8216;%lld&#8217; expects type &#8216;long long int&#8217;, but argument 4 has type &#8216;uint64_t&#8217;
Griffin.cpp: In member function &#8216;virtual void Griffin::perfMonitorCPUUsage()&#8217;:
Griffin.cpp:1026: warning: spurious trailing &#8216;%&#8217; in format
Griffin.cpp: In member function &#8216;virtual void Griffin::perfCounterMonitor(int, int)&#8217;:
Griffin.cpp:1045: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217;
Griffin.cpp:1069: warning: format &#8216;%llu&#8217; expects type &#8216;long long unsigned int&#8217;, but argument 4 has type &#8216;uint64_t&#8217;
Griffin.cpp:1069: warning: format &#8216;%llu&#8217; expects type &#8216;long long unsigned int&#8217;, but argument 5 has type &#8216;uint64_t&#8217;
K10Processor.cpp: In member function &#8216;virtual void K10Processor::perfCounterGetValue(int, int)&#8217;:
K10Processor.cpp:1091: warning: format &#8216;%lld&#8217; expects type &#8216;long long int&#8217;, but argument 4 has type &#8216;uint64_t&#8217;
K10Processor.cpp: In member function &#8216;virtual void K10Processor::perfMonitorCPUUsage()&#8217;:
K10Processor.cpp:1117: warning: spurious trailing &#8216;%&#8217; in format
K10Processor.cpp: In member function &#8216;virtual void K10Processor::perfCounterMonitor(int, int)&#8217;:
K10Processor.cpp:1136: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217;
K10Processor.cpp:1160: warning: format &#8216;%llu&#8217; expects type &#8216;long long unsigned int&#8217;, but argument 4 has type &#8216;uint64_t&#8217;
K10Processor.cpp:1160: warning: format &#8216;%llu&#8217; expects type &#8216;long long unsigned int&#8217;, but argument 5 has type &#8216;uint64_t&#8217;
/usr/bin/ld: cannot open output file ../bin/TurionPowerControl: No such file or directory
collect2: ld returned 1 exit status

And i'm not sure where the .bin directory is

If bin director in File System folder, then I don't see a Turion Power COntrol executable. I might be doing it wrong.

---

### Post by francismorales on 2010-10-11
i wish there was something that worked out of the box or a step by step on what to do and what packages they need for windows switchers to make it easier.:(

---

### Post by playcat on 2010-10-12
Hello,

Started it as root, compiled without problems (except for those warnings, but things still work as expected). 
I've been using undervolting for quite a while now on windows, and overheating has beed a real problem under ubuntu (been trying with cpu freq scaling, but with little success).

Thank you guys!

p.s. I used root for compiling.

Dan

---

### Post by andrewthomas on 2010-10-12
> **francismorales said:**
> I'm getting these warnings.



And i'm not sure where the .bin directory is

If bin director in File System folder, then I don't see a Turion Power COntrol executable. I might be doing it wrong.
Did you compile it in your a folder in your /home directory?

You shouldn't have to compile as root.  Post the configure.log (it should be in the folder you did the configure from.)

---

