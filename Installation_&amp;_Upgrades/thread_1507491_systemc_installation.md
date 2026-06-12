---
title: "systemc installation"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by nohnny on 2010-06-11
Hi can anybody help me out here....... PLEASE

I'm struck in installing systemc in ubuntu 9.10. After running  "make install" I got these errors.
THE ERRORS ARE AS FOLLOWS...

nohnny@ubuntu:~/systemc-2.2.0$ make install
Making install in src
make[1]: Entering directory `/home/nohnny/systemc-2.2.0/src'
Making install in sysc
make[2]: Entering directory `/home/nohnny/systemc-2.2.0/src/sysc'
Making install in kernel
make[3]: Entering directory `/home/nohnny/systemc-2.2.0/src/sysc/kernel'
make[4]: Entering directory `/home/nohnny/systemc-2.2.0/src/sysc/kernel'
make[4]: Nothing to be done for `install-exec-am'.
/bin/bash ../../../config/mkinstalldirs /home/nohnny/systemc-2.2.0/include/sysc/kernel
for file in sc_attribute.h sc_boost.h sc_cmnhdr.h sc_constants.h sc_cor.h sc_dynamic_processes.h sc_event.h sc_except.h sc_externs.h sc_join.h sc_kernel_ids.h sc_macros.h sc_module.h sc_module_name.h sc_object.h sc_process.h sc_process_handle.h sc_reset.h sc_runnable.h sc_sensitive.h sc_spawn.h sc_spawn_options.h sc_simcontext.h sc_time.h sc_ver.h sc_wait.h sc_wait_cthread.h ; do \
      /usr/bin/install -c -m 644 ./$file /home/nohnny/systemc-2.2.0/include/sysc/kernel/$file; \
    done
ar cru ../../../src/libsystemc.a \
       sc_attribute.o sc_cor_fiber.o sc_cor_pthread.o sc_cor_qt.o sc_cthread_process.o sc_event.o sc_join.o sc_main.o sc_main_main.o sc_method_process.o sc_module.o sc_module_name.o sc_module_registry.o sc_name_gen.o sc_object.o sc_object_manager.o sc_process.o sc_reset.o sc_sensitive.o sc_simcontext.o sc_thread_process.o sc_time.o sc_ver.o sc_wait.o sc_wait_cthread.o
make[4]: Leaving directory `/home/nohnny/systemc-2.2.0/src/sysc/kernel'
make[3]: Leaving directory `/home/nohnny/systemc-2.2.0/src/sysc/kernel'
Making install in qt
make[3]: Entering directory `/home/nohnny/systemc-2.2.0/src/sysc/qt'
make[4]: Entering directory `/home/nohnny/systemc-2.2.0/src/sysc/qt'
make[4]: Nothing to be done for `install-exec-am'.
/bin/bash ../../../config/mkinstalldirs /home/nohnny/systemc-2.2.0/include/sysc/qt
for file in qt.h qtmd.h; do \
      /usr/bin/install -c -m 644 ./$file /home/nohnny/systemc-2.2.0/include/sysc/qt/$file; \
    done
/bin/bash ../../../config/mkinstalldirs /home/nohnny/systemc-2.2.0/include/sysc/qt/md
list=`echo md/*`; \
      for file in $list; do \
        /usr/bin/install -c -m 644 ./$file /home/nohnny/systemc-2.2.0/include/sysc/qt/$file; \
      done
ar cru ../../../src/libsystemc.a \
       qt.o qtmdc.o qtmds.o
make[4]: Leaving directory `/home/nohnny/systemc-2.2.0/src/sysc/qt'
make[3]: Leaving directory `/home/nohnny/systemc-2.2.0/src/sysc/qt'
Making install in communication
make[3]: Entering directory `/home/nohnny/systemc-2.2.0/src/sysc/communication'
make[4]: Entering directory `/home/nohnny/systemc-2.2.0/src/sysc/communication'
make[4]: Nothing to be done for `install-exec-am'.
/bin/bash ../../../config/mkinstalldirs /home/nohnny/systemc-2.2.0/include/sysc/communication
for file in sc_buffer.h sc_clock.h sc_clock_ports.h sc_communication_ids.h sc_event_finder.h sc_event_queue.h sc_export.h sc_fifo.h sc_fifo_ifs.h sc_fifo_ports.h sc_interface.h sc_mutex.h sc_mutex_if.h sc_port.h sc_prim_channel.h sc_semaphore.h sc_semaphore_if.h sc_signal.h sc_signal_ifs.h sc_signal_ports.h sc_signal_resolved.h sc_signal_resolved_ports.h sc_signal_rv.h sc_signal_rv_ports.h ; do \
      /usr/bin/install -c -m 644 ./$file /home/nohnny/systemc-2.2.0/include/sysc/communication/$file; \
    done
ar cru ../../../src/libsystemc.a \
       sc_clock.o sc_event_finder.o sc_event_queue.o sc_export.o sc_interface.o sc_mutex.o sc_port.o sc_prim_channel.o sc_semaphore.o sc_signal.o sc_signal_ports.o sc_signal_resolved.o sc_signal_resolved_ports.o
make[4]: Leaving directory `/home/nohnny/systemc-2.2.0/src/sysc/communication'
make[3]: Leaving directory `/home/nohnny/systemc-2.2.0/src/sysc/communication'
Making install in tracing
make[3]: Entering directory `/home/nohnny/systemc-2.2.0/src/sysc/tracing'
make[4]: Entering directory `/home/nohnny/systemc-2.2.0/src/sysc/tracing'
make[4]: Nothing to be done for `install-exec-am'.
/bin/bash ../../../config/mkinstalldirs /home/nohnny/systemc-2.2.0/include/sysc/tracing
for file in sc_trace.h sc_vcd_trace.h sc_wif_trace.h; do \
      /usr/bin/install -c -m 644 ./$file /home/nohnny/systemc-2.2.0/include/sysc/tracing/$file; \
    done
ar cru ../../../src/libsystemc.a \
       sc_trace.o sc_vcd_trace.o sc_wif_trace.o
make[4]: Leaving directory `/home/nohnny/systemc-2.2.0/src/sysc/tracing'
make[3]: Leaving directory `/home/nohnny/systemc-2.2.0/src/sysc/tracing'
Making install in utils
make[3]: Entering directory `/home/nohnny/systemc-2.2.0/src/sysc/utils'
g++ -I. -I. -I../../../src    -Wall -DSC_INCLUDE_FX -O3 -MT sc_utils_ids.o -MD -MP -MF .deps/sc_utils_ids.Tpo -c -o sc_utils_ids.o sc_utils_ids.cpp
sc_utils_ids.cpp: In function ‘int sc_core::initialize()’:
sc_utils_ids.cpp:110: error: ‘getenv’ is not a member of ‘std’
sc_utils_ids.cpp:111: error: ‘strcmp’ was not declared in this scope
sc_utils_ids.cpp: At global scope:
sc_utils_ids.cpp:119: warning: ‘sc_core::forty_two’ defined but not used
make[3]: *** [sc_utils_ids.o] Error 1
make[3]: Leaving directory `/home/nohnny/systemc-2.2.0/src/sysc/utils'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/nohnny/systemc-2.2.0/src/sysc'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/nohnny/systemc-2.2.0/src'
make: *** [install-recursive] Error 1
nohnny@ubuntu:~/systemc-2.2.0$ 





I've lot of work to do in systemc. I'm not able to do it in my college. So anybody help me to install SYSTEMC......       



Thank you in advance..

---

### Post by amigabill on 2010-08-09
Same problem. Using Kubuntu 9.10 amd64 and systemc-2.2.0 as well.

There seems to be some info here
[http://ubuntuforums.org/showthread.php?p=10129510#post10129510](http://ubuntuforums.org/showthread.php?p=10129510#post10129510)

and more here
[http://ubuntuforums.org/showthread.php?t=1257173](http://ubuntuforums.org/showthread.php?t=1257173)

---

