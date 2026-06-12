---
title: "Vmware Server 2.0.2 install error ubuntu 12.04"
date: 2012-06-07
forum: Installation &amp; Upgrades
---

### Post by fire_blade on 2012-06-07
Help !!

how can i install vmware server 2.0.2 on ubuntu 12.04 . i tryed install but get error installing. 


Ubuntu kernel version 3.2.0.24
gcc version 4.6.3

error code :

     Code:
    ```
The installation of VMware Server 2.0.2 build-203138 for Linux completed 
successfully. You can decide to remove this software from your system at any 
time by invoking the following command: "/usr/bin/vmware-uninstall.pl".

Before running VMware Server for the first time, you need to configure it by 
invoking the following command: "/usr/bin/vmware-config.pl". Do you want this 
program to invoke the command for you now? [yes] 

Making sure services for VMware Server are stopped.

Stopping VMware autostart virtual machines:
   Virtual machines                                                   failed
Stopping VMware management services:
   VMware Virtual Infrastructure Web Access
   VMware Server Host Agent                                           failed
Stopping VMware services:
   VMware Authentication Daemon                                        done
   Virtual machine monitor                                             done


Do you accept? (yes/no) y

Thank you.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Your kernel was built with "gcc" version "4.6.3", while you are trying to use 
"/usr/bin/gcc" version "4.6". This configuration is not recommended and VMware 
Server may crash if you'll continue. Please try to use exactly same compiler as
one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.6" anyway? [no] 

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and 
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.

mgok@ubuntupc:~/Desktop/vmware/vmware-server-distrib$ None of the pre-built vmmon modules for VMware Server is suitable for your 
No command 'None' found, did you mean:
 Command 'one' from package 'opennebula' (universe)
 Command 'cone' from package 'cone' (universe)
None: command not found
mgok@ubuntupc:~/Desktop/vmware/vmware-server-distrib$ running kernel.  Do you want this program to try to build the vmmon module for 
running: command not found
mgok@ubuntupc:~/Desktop/vmware/vmware-server-distrib$ your system (you need to have a C compiler installed on your system)? [yes] 
bash: syntax error near unexpected token `('
mgok@ubuntupc:~/Desktop/vmware/vmware-server-distrib$ 
mgok@ubuntupc:~/Desktop/vmware/vmware-server-distrib$ Using compiler "/usr/bin/gcc". Use environment variable CC to override.
Using: command not found
mgok@ubuntupc:~/Desktop/vmware/vmware-server-distrib$ 
mgok@ubuntupc:~/Desktop/vmware/vmware-server-distrib$ Your kernel was built with "gcc" version "4.6.3", while you are trying to use 
Your: command not found
mgok@ubuntupc:~/Desktop/vmware/vmware-server-distrib$ "/usr/bin/gcc" version "4.6". This configuration is not recommended and VMware 
gcc: error: version: No such file or directory
gcc: error: 4.6.: No such file or directory
gcc: error: This: No such file or directory
gcc: error: configuration: No such file or directory
gcc: error: is: No such file or directory
gcc: error: not: No such file or directory
gcc: error: recommended: No such file or directory
gcc: error: and: No such file or directory
gcc: error: VMware: No such file or directory
gcc: fatal error: no input files
compilation terminated.
mgok@ubuntupc:~/Desktop/vmware/vmware-server-distrib$ Server may crash if you'll continue. Please try to use exactly same compiler as
> one used for building your kernel. Do you want to go with compiler 
> "/usr/bin/gcc" version "4.6" anyway? [no] 
> 
> For more information on how to troubleshoot module-related problems, please 
> visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and 
> "http://www.vmware.com/go/unsup-linux-tools".
> 
> Execution aborted.



```
help me
thnx!!

---

### Post by adglife on 2012-08-15
Am having same exact problem! Please help.

---

### Post by weitau on 2012-10-29
I found this thread through search.
I know this is old, but I am trying to do this too.  
Any help will be appreciated!

---

