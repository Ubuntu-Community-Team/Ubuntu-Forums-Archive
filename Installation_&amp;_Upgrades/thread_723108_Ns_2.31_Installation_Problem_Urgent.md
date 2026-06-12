---
title: "Ns 2.31 Installation Problem Urgent"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by moblav on 2008-03-13
hello, while i was installing NS-2.31 following the instructions from the page:
[http://nsnam.isi.edu/nsnam/index.php/Installing_ns2.31_on_Ubuntu7.04](http://nsnam.isi.edu/nsnam/index.php/Installing_ns2.31_on_Ubuntu7.04)
i type "ns", and then a "%" should appear on the screen, meaning that i entered the program! But the following error occured:

$ ns
Usage:      host [-v] [-a] [-t querytype] [options]  name  [server]
Listing:    host [-v] [-a] [-t querytype] [options]  -l zone  [server]
Hostcount:  host [-v] [options] -H [-D] [-E] [-G] zone
Check soa:  host [-v] [options] -C zone
Addrcheck:  host [-v] [options] -A host
Listing options: [-L level] [-S] [-A] [-p] [-P prefserver] [-N skipzone]
Common options:  [-d] [-f|-F file] [-I chars] [-i|-n] [-q] [-Q] [-T] [-Z]
Other options:   [-c class] [-e] [-m] [-o] [-r] [-R] [-s secs] [-u] [-w]
Special options: [-O srcaddr] [-j minport] [-J maxport]
Extended usage:  [-x [name ...]] [-X server [name ...]]
$ 




Then i tryed to run one example, and again an error came up:

$ ls
bin            install        ns-2.31        sgb             tk8.4.14
cweb           INSTALL.WIN32  ns-simple.tcl  tcl8.4.14       xgraph-12.1
**_example1a.tcl_**  lib            otcl           tclcl           zlib-1.2.3
gt-itm         man            otcl-1.13      tclcl-1.19
include        nam-1.13       README         tcp-veno-1.0.2
$ ns example1a.tcl
example1a.tcl does not exist, try again
$ 


Can you help me? what is the problem?
thanks!!!

---

