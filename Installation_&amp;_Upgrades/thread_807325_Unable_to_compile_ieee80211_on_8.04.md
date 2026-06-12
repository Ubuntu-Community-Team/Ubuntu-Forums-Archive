---
title: "Unable to compile ieee80211 on 8.04"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by khh on 2008-05-25
I've got Kubuntu 8.04, fully updated, on my laptop.
Yes, I've installed the kernel headers. Yes, I've installed the kernel source.
I've been able to build many other applications, so that's not it.
I've got the build-essentials package (only spelled correctly). 
Under I've copied the content from the terminal when trying to build iee80211.
```
[COLOR="Red"]khh@Unknown:~/ieee80211-1.2.18$ make
Makefile:17:
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21:
Checking in /lib/modules/2.6.24-16-generic for ieee80211 components...
make -C /lib/modules/2.6.24-16-generic/build M=/home/khh/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
/home/khh/ieee80211-1.2.18/Makefile:17:
/home/khh/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/khh/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/khh/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/khh/ieee80211-1.2.18/Makefile:21:
  CC [M]  /home/khh/ieee80211-1.2.18/ieee80211_module.o
/home/khh/ieee80211-1.2.18/ieee80211_module.c: In function &#8216;ieee80211_init&#8217;:
/home/khh/ieee80211-1.2.18/ieee80211_module.c:268: error: &#8216;proc_net&#8217; undeclared (first use in this function)
/home/khh/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/home/khh/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/home/khh/ieee80211-1.2.18/ieee80211_module.c: In function &#8216;ieee80211_exit&#8217;:
/home/khh/ieee80211-1.2.18/ieee80211_module.c:297: error: &#8216;proc_net&#8217; undeclared (first use in this function)
{standard input}: Assembler messages:
{standard input}:9: Warning: can't open .lst: Permission denied
GAS LISTING                     page 1


   1                    .file "ieee80211_module.c"
   9                    .Ltext0:

GAS LISTING                     page 2


DEFINED SYMBOLS
                            *ABS*:0000000000000000 ieee80211_module.c

NO UNDEFINED SYMBOLS
make[2]: *** [/home/khh/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/khh/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2[/COLOR]

[COLOR="green"]khh@Unknown:~/ieee80211-1.2.18$ make SHELL=/bin/bash
Checking in /lib/modules/2.6.24-16-generic for ieee80211 components...
make -C /lib/modules/2.6.24-16-generic/build M=/home/khh/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/khh/ieee80211-1.2.18/ieee80211_module.o
/home/khh/ieee80211-1.2.18/ieee80211_module.c: In function &#8216;ieee80211_init&#8217;:
/home/khh/ieee80211-1.2.18/ieee80211_module.c:268: error: &#8216;proc_net&#8217; undeclared (first use in this function)
/home/khh/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/home/khh/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/home/khh/ieee80211-1.2.18/ieee80211_module.c: In function &#8216;ieee80211_exit&#8217;:
/home/khh/ieee80211-1.2.18/ieee80211_module.c:297: error: &#8216;proc_net&#8217; undeclared (first use in this function)
{standard input}: Assembler messages:
{standard input}:9: Warning: can't open .lst: Permission denied
GAS LISTING                     page 1


   1                    .file "ieee80211_module.c"
   9                    .Ltext0:

GAS LISTING                     page 2


DEFINED SYMBOLS
                            *ABS*:0000000000000000 ieee80211_module.c

NO UNDEFINED SYMBOLS
make[2]: *** [/home/khh/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/khh/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2[/COLOR]

[COLOR="Red"]khh@Unknown:~/ieee80211-1.2.18$ sudo make
[sudo] password for khh:
Makefile:17:
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21:
Checking in /lib/modules/2.6.24-16-generic for ieee80211 components...
make -C /lib/modules/2.6.24-16-generic/build M=/home/khh/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
/home/khh/ieee80211-1.2.18/Makefile:17:
/home/khh/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/khh/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/khh/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/khh/ieee80211-1.2.18/Makefile:21:
  CC [M]  /home/khh/ieee80211-1.2.18/ieee80211_module.o
/home/khh/ieee80211-1.2.18/ieee80211_module.c: In function &#8216;ieee80211_init&#8217;:
/home/khh/ieee80211-1.2.18/ieee80211_module.c:268: error: &#8216;proc_net&#8217; undeclared (first use in this function)
/home/khh/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/home/khh/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/home/khh/ieee80211-1.2.18/ieee80211_module.c: In function &#8216;ieee80211_exit&#8217;:
/home/khh/ieee80211-1.2.18/ieee80211_module.c:297: error: &#8216;proc_net&#8217; undeclared (first use in this function)
make[2]: *** [/home/khh/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/khh/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2[/COLOR]

[COLOR="green"]khh@Unknown:~/ieee80211-1.2.18$ sudo make SHELL=/bin/bash
Checking in /lib/modules/2.6.24-16-generic for ieee80211 components...
make -C /lib/modules/2.6.24-16-generic/build M=/home/khh/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/khh/ieee80211-1.2.18/ieee80211_module.o
/home/khh/ieee80211-1.2.18/ieee80211_module.c: In function &#8216;ieee80211_init&#8217;:
/home/khh/ieee80211-1.2.18/ieee80211_module.c:268: error: &#8216;proc_net&#8217; undeclared (first use in this function)
/home/khh/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/home/khh/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/home/khh/ieee80211-1.2.18/ieee80211_module.c: In function &#8216;ieee80211_exit&#8217;:
/home/khh/ieee80211-1.2.18/ieee80211_module.c:297: error: &#8216;proc_net&#8217; undeclared (first use in this function)
make[2]: *** [/home/khh/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/khh/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2
khh@Unknown:~/ieee80211-1.2.18$[/COLOR]
```

Now, this makes it look as if there's something wrong with the source code of this application, but this is not the case. I've got a server running 7.10 (fully updated), and when I tried compiling the exact same package (copied over the very tar.gz file i've used on my laptop), it compiled without any errors what so ever.
Any help would be greatly appriciated.

---

### Post by khh on 2008-05-26
bump

---

### Post by jstoney on 2008-08-20
To solve this problem open the module.o file and type init_net.proc_net instead of just proc_net

---

### Post by vertago1 on 2008-08-22
> **jstoney said:**
> To solve this problem open the module.o file and type init_net.proc_net instead of just proc_net

Thanks this helped a lot. The file is really called ieee80211_module.c

Now I am stuck at:
> sudo make
Makefile:17:
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21:
Checking in /lib/modules/2.6.24-19-generic for ieee80211 components...
make -C /lib/modules/2.6.24-19-generic/build M=/media/sda1/downloads/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
/media/sda1/downloads/ieee80211-1.2.18/Makefile:17:
/media/sda1/downloads/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/media/sda1/downloads/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/media/sda1/downloads/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/media/sda1/downloads/ieee80211-1.2.18/Makefile:21:
  CC [M]  /media/sda1/downloads/ieee80211-1.2.18/ieee80211_module.o
  CC [M]  /media/sda1/downloads/ieee80211-1.2.18/ieee80211_tx.o
  CC [M]  /media/sda1/downloads/ieee80211-1.2.18/ieee80211_rx.o
  CC [M]  /media/sda1/downloads/ieee80211-1.2.18/ieee80211_wx.o
  CC [M]  /media/sda1/downloads/ieee80211-1.2.18/ieee80211_geo.o
  LD [M]  /media/sda1/downloads/ieee80211-1.2.18/ieee80211.o
  CC [M]  /media/sda1/downloads/ieee80211-1.2.18/ieee80211_crypt.o
  CC [M]  /media/sda1/downloads/ieee80211-1.2.18/ieee80211_crypt_wep.o
/media/sda1/downloads/ieee80211-1.2.18/ieee80211_crypt_wep.c: In function ‘prism2_wep_encrypt’:
/media/sda1/downloads/ieee80211-1.2.18/ieee80211_crypt_wep.c:190: error: ‘struct scatterlist’ has no member named ‘page’
/media/sda1/downloads/ieee80211-1.2.18/ieee80211_crypt_wep.c: In function ‘prism2_wep_decrypt’:
/media/sda1/downloads/ieee80211-1.2.18/ieee80211_crypt_wep.c:238: error: ‘struct scatterlist’ has no member named ‘page’
make[2]: *** [/media/sda1/downloads/ieee80211-1.2.18/ieee80211_crypt_wep.o] Error 1
make[1]: *** [_module_/media/sda1/downloads/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2

I am running x86_64 and I traced the problem to scatterlist.h in /usr/src/linux-headers-2.6.24-19-generic/include/asm/scatterlist.h

which contains:
#ifdef CONFIG_X86_32
# include "scatterlist_32.h"
#else
# include "scatterlist_64.h"
#endif

I was able to get it to compile by changing
editing ieee80211_crypt_wep.c ieee80211_crypt_tkip.c
tp replace:
*#include<asm/scatterlist.h>* with *#include<asm/scatterlist_32.h>*
*.page* with *.page_link*

I used the 32bit scatter list because of a length issue I got otherwise. I do not know if I should try and report this somewhere on the ieee80211.sourceforge.net site or not.

---

### Post by Bakerconspiracy on 2008-09-10
This post has saved the day for me. What happened there? Did they change the class member function names in the headers / the header names too? I don't understand why I had to have so many problems. Anyways, THANKS!

---

### Post by ex.hav0k on 2008-09-12
i tried changing the file to scatterlist_32.c, but it didn't work... i keep getting this when i try any form of sudo make:

```
giacomo@ex:~/Downloads/ipw2200_patching/ieee80211-1.2.18$ sudo make SHELL=/bin/bash
Checking in /lib/modules/2.6.24-19-generic for ieee80211 components...
make -C /lib/modules/2.6.24-19-generic/build M=/home/giacomo/Downloads/ipw2200_patching/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/giacomo/Downloads/ipw2200_patching/ieee80211-1.2.18/ieee80211_module.o
/home/giacomo/Downloads/ipw2200_patching/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_init’:
/home/giacomo/Downloads/ipw2200_patching/ieee80211-1.2.18/ieee80211_module.c:268: error: ‘proc_net’ undeclared (first use in this function)
/home/giacomo/Downloads/ipw2200_patching/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/home/giacomo/Downloads/ipw2200_patching/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/home/giacomo/Downloads/ipw2200_patching/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_exit’:
/home/giacomo/Downloads/ipw2200_patching/ieee80211-1.2.18/ieee80211_module.c:297: error: ‘proc_net’ undeclared (first use in this function)
make[2]: *** [/home/giacomo/Downloads/ipw2200_patching/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/giacomo/Downloads/ipw2200_patching/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
```

can anyone help with this?  im afraid to restart my computer as im guessing it won't work if i do.

---

### Post by astjohn on 2008-09-19
The above solution worked well for me.  Again:

1. Replace proc_net with init_net.proc_net in module.o 

2. Replace #include<asm/scatterlist.h> with #include<asm/scatterlist_32.h> in ieee80211_crypt_wep.c

3. Replace .page with .page_link in ieee80211_crypt_wep.c

Repeat steps 2 and 3 with ieee80211_crypt_tkip.c


Thanks!

---

### Post by Rubainte on 2009-03-08
Hellow,

I'm new in ubuntu, and i'm still searching a little bit...
The method you showed changing proc_net worked well !
But now I've got another problem, when i start make he keeps repeating
  CC [M]  /home/rubainte/Bureaublad/ieee80211-1.2.18/ieee80211_wx.o
/home/rubainte/Bureaublad/ieee80211-1.2.18/ieee80211_wx.c: In function ‘ieee80211_translate_scan’:
/home/rubainte/Bureaublad/ieee80211-1.2.18/ieee80211_wx.c:61: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/rubainte/Bureaublad/ieee80211-1.2.18/ieee80211_wx.c:61: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type

I suggest i will have to change something else ... But don't know what ...

Thanks,
Rubain

---

### Post by soraver on 2009-03-13
> **astjohn said:**
> The above solution worked well for me.  Again:

1. Replace proc_net with init_net.proc_net in module.o 

2. Replace #include<asm/scatterlist.h> with #include<asm/scatterlist_32.h> in ieee80211_crypt_wep.c

3. Replace .page with .page_link in ieee80211_crypt_wep.c

Repeat steps 2 and 3 with ieee80211_crypt_tkip.c


Thanks!

thank you very very much for this information
i am using debian squeeze right now with 2.6.26-1-686 kernel and those instructions worked for me too. with the small difference that i didnt need to do step 2. So i believe its the same deal with non 64bits kernel in ubuntu too.

@Rubainte you dont have to worry about warnings if it does compile :)

---

### Post by Neonlajt on 2009-03-15
I am still having troubles compiling it, it seems that whatever I try I get this error

```
ieee80211-1.2.18/ieee80211_crypt_wep.c:190: error: âvirt_tâ undeclared (first use in this function)
/ieee80211-1.2.18/ieee80211_crypt_wep.c:190: error: (Each undeclared identifier is reported only once
/ieee80211-1.2.18/ieee80211_crypt_wep.c:190: error: for each function it appears in.)
/ieee80211-1.2.18/ieee80211_crypt_wep.c:191: error: âoffset_iâ undeclared (first use in this function)
/ieee80211-1.2.18/ieee80211_crypt_wep.c:191: error: (Each undeclared identifier is reported only once
ieee80211-1.2.18/ieee80211_crypt_wep.c:191: error: for each function it appears in.)
/ieee80211-1.2.18/ieee80211_crypt_wep.c: In function âprism2_wep_decryptâ:
/ieee80211-1.2.18/ieee80211_crypt_wep.c:238: error: âvirt_tâ undeclared (first use in this function)
/ieee80211-1.2.18/ieee80211_crypt_wep.c:239: error: âoffset_iâ undeclared (first use in this function)]
```

The problem seems to be with the declaring of virt_t and offset_i, I reckon they are custom structures, but I can`t find them or what their purpose is anywhere. Though I`m suspecting virt_t to be virt_to_page(smt smt in here) from io_32.h (or io.h), but I`m uncertain what ioffset_i is all about.

```
sg.page_link = virt_t.page_link(pos);
        sg.offset = offset_i.page_link(pos);

```


If you do have any answers, pleas do reply :)

---

### Post by Hendrik0 on 2009-03-20
Hi,
I had the same problem as Rubainte. Here‘s how I resolved it.
Seemingly, net/iw_handler.h introduced the new struct iw_request_info, which I have the impression is not yet used. It is passed as first argument to all those functions. So I just defined

struct iw_request_info info;

in the function ieee80211_translate_scan in ieee80211_wx.c and added the first argument &info to all the calls in question. That felt quite dirty but worked out well.

Finally, I have to point out that I have no idea whether my assumption that the struct is not yet used is correct, or whether this hack can severely break anything … But I can tell my wireless device is working.

---

