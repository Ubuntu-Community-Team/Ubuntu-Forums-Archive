---
title: "Problem With Code In Ubuntu ,please Help Me"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by krisvamc on 2007-04-12
****

Hi,

I am trying to install **MCC (Multicast Control Client) source code ** in linux ubuntu system and I got errors while compiling by **./compile.**.

Could anybody please tell me how to rectify the errors or any solution to the problem. Please help as I am desperate for the solution.

**The error is **:

root@vamsi-laptop:/home/vamsi/Desktop/mcop/mcc# ./compile
rm -f ../../obj/c_vector.o ../../obj/sample.o
rm -f *~
rm -f \#*
rm -f *.a
rm -f c_vector
gcc -c -gstabs -I/usr/local/lib -I. -I../parser  -o c_vector.o c_vector.c
mv c_vector.o ../../obj
make: *** No rule to make target `sample.o', needed by `c_vector'.  Stop.
rm -f *.o
rm -f ../../obj/parser.o
rm -f *~
rm -f \#*
rm -f *.a
gcc -gstabs -Wall -pg -c parser.c
parser.c: In function ‘fprint_MCOP_message’:
parser.c:805: warning: pointer targets in passing argument 1 of ‘fopen’ differ in signedness
mv parser.o ../../obj
**./compile: line 9: cd: ../testclient: No such file or directory**
rm -f *.o
rm -f ../../obj/parser.o
rm -f *~
rm -f \#*
rm -f *.a
gcc -gstabs -Wall -pg -c parser.c
parser.c: In function ‘fprint_MCOP_message’:
parser.c:805: warning: pointer targets in passing argument 1 of ‘fopen’ differ in signedness
mv parser.o ../../obj
rm -f *.o
rm -f *~
rm -f \#*
rm -f *.a
rm -f mcopd
rm ../../obj/mcopd.o ../../obj/igmp.o ../../obj/netif.o ../../obj/connection.o ../../obj/handling.o ../../obj/perl.o ../../obj/repository.o ../../obj/config.o ../../obj/logfile.o ../../obj/usr_cmd.o
rm: cannot remove `../../obj/mcopd.o': No such file or directory
rm: cannot remove `../../obj/igmp.o': No such file or directory
rm: cannot remove `../../obj/netif.o': No such file or directory
rm: cannot remove `../../obj/connection.o': No such file or directory
rm: cannot remove `../../obj/handling.o': No such file or directory
rm: cannot remove `../../obj/perl.o': No such file or directory
rm: cannot remove `../../obj/repository.o': No such file or directory
rm: cannot remove `../../obj/config.o': No such file or directory
rm: cannot remove `../../obj/logfile.o': No such file or directory
rm: cannot remove `../../obj/usr_cmd.o': No such file or directory
make: *** [clean] Error 1
gcc -c -O2 -D__NO_LOG -I/usr/local/lib -I. -I../parser -I/usr/include/libipq -I../c_vector  -o iptables_handler.o iptables_handler.c
iptables_handler.c: In function ‘ipth_list_entry_child’:
[B]iptables_handler.c:291: error: ‘struct iptables_match’ has no member named ‘used’
iptables_handler.c:300: error: ‘struct iptables_match’ has no member named ‘used’[/B]
make: *** [iptables_handler.o] Error 1
root@vamsi-laptop:/home/vamsi/Desktop/mcop/mcc# 

testclient is not available in the code.How to rectify that.

Thanks,

vamsi.

---

