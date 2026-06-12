---
title: "[SOLVED] 'update-mime'  process 100%CPU during package installation."
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by kverkind on 2008-06-17
Ubuntu version 8.04 

When I use package manager the installation is very slow(download is OK). 'top' shows that the 'update-mime' process is using 100% CPU.

example of 'top':

top - 21:42:49 up  1:10,  3 users,  load average: 1.48, 0.79, 0.90
Tasks: 139 total,   4 running, 135 sleeping,   0 stopped,   0 zombie
Cpu(s): 52.1%us,  0.3%sy,  0.0%ni, 43.1%id,  3.8%wa,  0.0%hi,  0.7%si,  0.0%st
Mem:    515340k total,   507520k used,     7820k free,     4156k buffers
Swap:  1511960k total,    76316k used,  1435644k free,   150160k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
7687 root      20   0 23392  20m 1576 R  100  4.0   0:35.51 update-mime        
5507 root      20   0  112m  33m 7500 S    3  6.7   3:46.38 Xorg               
6636 kverkind  20   0  119m  21m  12m R    1  4.3   0:04.82 gnome-terminal     
7633 root      20   0  117m  43m  24m R    1  8.7   0:11.02 synaptic           
6133 kverkind  20   0 84632  23m 7080 S    1  4.6   1:21.18 compiz.real        
7676 kverkind  20   0  2308 1128  848 R    1  0.2   0:00.16 top                
6781 kverkind  20   0  221m  69m  22m S    0 13.7   1:50.52 firefox            
    1 root      20   0  2844 1652  508 S    0  0.3   0:01.24 init      

The detailed message in the package manager shows:

Unpacking replacement ....

I have one portable where the installation goes very fast while the installation on my desktop takes ages. The versions of Ubuntu are identical. The problem already existed since version 7. 

Any idea what could be the cause of this ? Is there a way to check/debug de update-mime process.

                               Thx.

---

### Post by kverkind on 2008-06-20
Solved the problem myself (not a lot of reactions :( ).

The /usr/lib/mime/packages library contained a binary file. As a result of this the /etc/mailcap file included that binary information (update-mime took a long time in order to build).

After removing the binary, removing the /etc/mailcap file an then starting the package manager the update-mime generated a good /etc/mailcap file on the spot.

=D>

---

