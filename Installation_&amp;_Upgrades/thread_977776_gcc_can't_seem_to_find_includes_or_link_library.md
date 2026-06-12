---
title: "gcc can't seem to find includes or link library"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by EEed on 2008-11-10
gcc can't seem to find includes or link library
I am very new to this!!! I just set up a dual boot Ubuntu laptop using 8.10, truly a very exciting system!!!

While I can compile and run a very simple program, I have now been several days trying to run the first program in the Bluetooth Essentials for Programmers book.

The source: simplescan.c:

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/socket.h>
#include <bluetooth/bluetooth.h>
#include <bluetooth/hci.h>
#include <bluetooth/hci_lib.h>
#include <bluetooth.h>
#include <hci.h>
#include <hci_lib.h>


int main(int argc, char **argv)
{
inquiry_info *devices = NULL;
int max_rsp, num_rsp;
int adapter_id, sock, len, flags;
int i;
char addr[19] = { 0 };
char name[248] = { 0 };

adapter_id = hci_get_route(NULL);
sock = hci_open_dev( adapter_id );
if (adapter_id < 0 || sock < 0) {
perror("opening socket");
exit(1);
}

len = 8;
max_rsp = 255;
flags = IREQ_CACHE_FLUSH;
devices = (inquiry_info*)malloc(max_rsp * sizeof(inquiry_info));

num_rsp = hci_inquiry(adapter_id, len, max_rsp, NULL, &devices,
flags);
if( num_rsp < 0 ) perror("hci_inquiry");

for (i = 0; i < num_rsp; i++) {
ba2str(&(devices+i)->bdaddr, addr);
memset(name, 0, sizeof(name));
if (0 != hci_read_remote_name(sock, &(devices+i)->bdaddr,
sizeof(name), name, 0)) {
strcpy(name, "[unknown]");
}
printf("%s %s\n", addr, name);
}

free( devices );
close( sock );
return 0;
}

Trying to run:

myusername@ubuntu:~$ gcc -o simplescan simplescan.c -lbluetooth
simplescan.c:5:33: error: bluetooth/bluetooth.h: No such file or directory
simplescan.c:6:27: error: bluetooth/hci.h: No such file or directory
simplescan.c:7:31: error: bluetooth/hci_lib.h: No such file or directory
simplescan.c:8:23: error: bluetooth.h: No such file or directory
simplescan.c:9:17: error: hci.h: No such file or directory
simplescan.c:10:21: error: hci_lib.h.h: No such file or directory
simplescan.c: In function 'main':
simplescan.c:15: error: 'inquiry_info' undeclared (first use in this function)
simplescan.c:15: error: 'devices' undeclared (first use in this function)
simplescan.c:31: error: 'IREQ_CACHE_FLUSH' undeclared (first use in this function)
simplescan.c:32:error: expected expression before ')' token
simplescan.c:40: warning: incompatible implicit declaration of builtin function "memset"
simplescan.c:43: warning: incompatible implicit declaration of builtin function "strcpy"

I am guessing I may need builtin-essentials or ??? (I can't find if 8.10 needs it.) But if I could get some help from a genius, that would be great and make me feel even better!

Help Help please!!! My fourth day of modifying source and crossing fingers!!! Thank you,

EEed

Thank you.

EEed

---

### Post by gpsmikey on 2008-11-10
Typically, you do need to install "build-essential" (note there is no "s" on the end of it).  That brings in all sorts of stuff the compiler usually wants to see.  Note that the man pages are separate from the rest of the install - I think they are under the "manpages-dev" title, but I am busy *trying* to organize my desk and the current state is somewhat like a full file system with no directory :lolflag:

mikey

---

### Post by EEed on 2008-11-10
Mikey,

Thank you:).  Do you have any idea how I can install it? I can't find it in the Synaptic Package Manager.

Thanks,

Ed

---

### Post by gpsmikey on 2008-11-10
In the Synaptic package manager, select the Development section - "build-essential" should be listed there (I had to go look and I just did it last night on a new install - it's tough getting old !! ).

mikey

---

### Post by EEed on 2008-11-10
Mikey,

I am probably older than you (65). I knew this right away because you were kind enough to tell me where to look and I still couldn't find it:KS!


I did find binutils; that was the closest I found!!!

Thanks!

I will still be trying; please let me know if you think of anything else!

Thanks again,

Ed

---

### Post by gpsmikey on 2008-11-10
Not by much (58+).  Couple of things to try -- in the synaptic package manager try the refresh which should download the current list of packages (I think).  You might also find the following links helpful (I'm not sure what you are running into since I can see it in mine although, I think I did hit refresh last night before looking).
[http://www.linuxquestions.org/questions/ubuntu-63/installing-build-essential-with-no-cd-668845/](http://www.linuxquestions.org/questions/ubuntu-63/installing-build-essential-with-no-cd-668845/)
[http://www.ubuntux.org/how-to-install-basic-compilers-build-essential](http://www.ubuntux.org/how-to-install-basic-compilers-build-essential)
Number 5 on this page also may help:
[http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch03s08.html](http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch03s08.html)

See if one of those helps.
mikey

---

### Post by EEed on 2008-11-12
Mikey,

I have followed your suggestions, and I now have build-essential on my HP laptop. Unfortunately, I still get the same result. I think it is a path problem. Perhaps my source is in the wrong place?

Thanks! I'm still trying to make this happen!

Ed

HELP HELP!!!!

---

### Post by gpsmikey on 2008-11-12
Hopefully someone else here can provide the answer, you have sort of run off the edge of what I have done so far on my system (I did do a test compile of the basic "Hello World" routine and it worked fine, but that is as far as I have really gone).  Try asking in the programming section and be sure to point out that you do have the "build-essential" installed.  You might want to try the basic "Hello World" type compile just to make sure that you have the basics working - helps pin down just where the problem is (or isn't).

mikey

---

