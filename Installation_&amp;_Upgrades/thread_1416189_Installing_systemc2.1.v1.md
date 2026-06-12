---
title: "Installing systemc2.1.v1"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by Malik_2009 on 2010-02-25
[SIZE=3]Hi All
When I try to install systemc2.1.v1 and write thsi command in the terminal of ubuntu9.10 ../configure, I get this result( even I have gcc4.4.1:
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/sysc/Makefile
config.status: creating src/sysc/communication/Makefile
config.status: creating src/sysc/datatypes/Makefile
config.status: creating src/sysc/datatypes/bit/Makefile
config.status: creating src/sysc/datatypes/fx/Makefile
config.status: creating src/sysc/datatypes/int/Makefile
config.status: creating src/sysc/datatypes/misc/Makefile
config.status: creating src/sysc/kernel/Makefile
config.status: creating src/sysc/tracing/Makefile
config.status: creating src/sysc/qt/Makefile
config.status: creating src/sysc/utils/Makefile
config.status: creating src/sysc/packages/Makefile
config.status: creating src/sysc/packages/boost/Makefile
config.status: creating src/sysc/packages/boost/bind/Makefile
config.status: creating src/sysc/packages/boost/config/Makefile
config.status: creating src/sysc/packages/boost/config/compiler/Makefile
config.status: creating src/sysc/packages/boost/config/platform/Makefile
config.status: creating src/sysc/packages/boost/config/stdlib/Makefile
config.status: creating src/sysc/packages/boost/detail/Makefile
config.status: creating src/sysc/packages/boost/utility/Makefile
config.status: creating examples/Makefile
config.status: creating examples/sysc/Makefile
config.status: creating examples/sysc/fir/Makefile
config.status: creating examples/sysc/fft/Makefile
config.status: creating examples/sysc/fft/fft_flpt/Makefile
config.status: creating examples/sysc/fft/fft_fxpt/Makefile
config.status: creating examples/sysc/pipe/Makefile
config.status: creating examples/sysc/pkt_switch/Makefile
config.status: creating examples/sysc/rsa/Makefile
config.status: creating examples/sysc/simple_bus/Makefile
config.status: creating examples/sysc/simple_fifo/Makefile
config.status: creating examples/sysc/simple_perf/Makefile
config.status: creating examples/sysc/2.1/Makefile
config.status: creating examples/sysc/2.1/dpipe/Makefile
config.status: creating examples/sysc/2.1/forkjoin/Makefile
config.status: creating examples/sysc/2.1/reset_signal_is/Makefile
config.status: creating examples/sysc/2.1/sc_export/Makefile
config.status: creating examples/sysc/2.1/sc_report/Makefile
config.status: creating examples/sysc/2.1/scx_barrier/Makefile
config.status: creating examples/sysc/2.1/scx_mutex_w_policy/Makefile
config.status: creating examples/sysc/2.1/specialized_signals/Makefile
config.status: executing depfiles commands
abdalmalik@ubuntu:~/programs/systemc-2.1.v1/objdir$ make
Making all in src
make[1]: Entering directory `/home/abdalmalik/programs/systemc-2.1.v1/objdir/src'
Making all in sysc
make[2]: Entering directory `/home/abdalmalik/programs/systemc-2.1.v1/objdir/src/sysc'
Making all in kernel
make[3]: Entering directory `/home/abdalmalik/programs/systemc-2.1.v1/objdir/src/sysc/kernel'
g++ -I. -I. -I../../../../src/sysc/kernel -I../../../../src    -Wall -DSC_INCLUDE_FX -O3 -c -o sc_attribute.o `test -f '../../../../src/sysc/kernel/sc_attribute.cpp' || echo '../../../../src/sysc/kernel/'`../../../../src/sysc/kernel/sc_attribute.cpp
g++ -I. -I. -I../../../../src/sysc/kernel -I../../../../src    -Wall -DSC_INCLUDE_FX -O3 -c -o sc_cor_fiber.o `test -f '../../../../src/sysc/kernel/sc_cor_fiber.cpp' || echo '../../../../src/sysc/kernel/'`../../../../src/sysc/kernel/sc_cor_fiber.cpp
g++ -I. -I. -I../../../../src/sysc/kernel -I../../../../src    -Wall -DSC_INCLUDE_FX -O3 -c -o sc_cor_pthread.o `test -f '../../../../src/sysc/kernel/sc_cor_pthread.cpp' || echo '../../../../src/sysc/kernel/'`../../../../src/sysc/kernel/sc_cor_pthread.cpp
g++ -I. -I. -I../../../../src/sysc/kernel -I../../../../src    -Wall -DSC_INCLUDE_FX -O3 -c -o sc_cor_qt.o `test -f '../../../../src/sysc/kernel/sc_cor_qt.cpp' || echo '../../../../src/sysc/kernel/'`../../../../src/sysc/kernel/sc_cor_qt.cpp
g++ -I. -I. -I../../../../src/sysc/kernel -I../../../../src    -Wall -DSC_INCLUDE_FX -O3 -c -o sc_event.o `test -f '../../../../src/sysc/kernel/sc_event.cpp' || echo '../../../../src/sysc/kernel/'`../../../../src/sysc/kernel/sc_event.cpp
g++ -I. -I. -I../../../../src/sysc/kernel -I../../../../src    -Wall -DSC_INCLUDE_FX -O3 -c -o sc_join.o `test -f '../../../../src/sysc/kernel/sc_join.cpp' || echo '../../../../src/sysc/kernel/'`../../../../src/sysc/kernel/sc_join.cpp
g++ -I. -I. -I../../../../src/sysc/kernel -I../../../../src    -Wall -DSC_INCLUDE_FX -O3 -c -o sc_lambda.o `test -f '../../../../src/sysc/kernel/sc_lambda.cpp' || echo '../../../../src/sysc/kernel/'`../../../../src/sysc/kernel/sc_lambda.cpp
../../../../src/sysc/kernel/sc_lambda.cpp: In destructor ‘sc_core::sc_lambda_rand::~sc_lambda_rand()’:
../../../../src/sysc/kernel/sc_lambda.cpp:273: warning: dereferencing type-punned pointer will break strict-aliasing rules
../../../../src/sysc/kernel/sc_lambda.cpp: In member function ‘int sc_core::sc_lambda_rand::int_read() const’:
../../../../src/sysc/kernel/sc_lambda.cpp:302: warning: dereferencing type-punned pointer will break strict-aliasing rules
../../../../src/sysc/kernel/sc_lambda.cpp: In member function ‘sc_dt::sc_logic sc_core::sc_lambda_rand::sc_logic_read() const’:
../../../../src/sysc/kernel/sc_lambda.cpp:318: warning: dereferencing type-punned pointer will break strict-aliasing rules
../../../../src/sysc/kernel/sc_lambda.cpp:324: warning: dereferencing type-punned pointer will break strict-aliasing rules
../../../../src/sysc/kernel/sc_lambda.cpp: In member function ‘bool sc_core::sc_lambda_rand::bool_read() const’:
../../../../src/sysc/kernel/sc_lambda.cpp:348: warning: dereferencing type-punned pointer will break strict-aliasing rules
../../../../src/sysc/kernel/sc_lambda.cpp: In member function ‘void sc_core::sc_lambda_rand::replace_ports(void (*)(sc_core::sc_port_registry*, sc_core::sc_lambda_rand*), sc_core::sc_port_registry*)’:
../../../../src/sysc/kernel/sc_lambda.cpp:367: warning: dereferencing type-punned pointer will break strict-aliasing rules
g++ -I. -I. -I../../../../src/sysc/kernel -I../../../../src    -Wall -DSC_INCLUDE_FX -O3 -c -o sc_main.o `test -f '../../../../src/sysc/kernel/sc_main.cpp' || echo '../../../../src/sysc/kernel/'`../../../../src/sysc/kernel/sc_main.cpp
g++ -I. -I. -I../../../../src/sysc/kernel -I../../../../src    -Wall -DSC_INCLUDE_FX -O3 -c -o sc_main_main.o `test -f '../../../../src/sysc/kernel/sc_main_main.cpp' || echo '../../../../src/sysc/kernel/'`../../../../src/sysc/kernel/sc_main_main.cpp
g++ -I. -I. -I../../../../src/sysc/kernel -I../../../../src    -Wall -DSC_INCLUDE_FX -O3 -c -o sc_module.o `test -f '../../../../src/sysc/kernel/sc_module.cpp' || echo '../../../../src/sysc/kernel/'`../../../../src/sysc/kernel/sc_module.cpp
g++ -I. -I. -I../../../../src/sysc/kernel -I../../../../src    -Wall -DSC_INCLUDE_FX -O3 -c -o sc_module_name.o `test -f '../../../../src/sysc/kernel/sc_module_name.cpp' || echo '../../../../src/sysc/kernel/'`../../../../src/sysc/kernel/sc_module_name.cpp
g++ -I. -I. -I../../../../src/sysc/kernel -I../../../../src    -Wall -DSC_INCLUDE_FX -O3 -c -o sc_module_registry.o `test -f '../../../../src/sysc/kernel/sc_module_registry.cpp' || echo '../../../../src/sysc/kernel/'`../../../../src/sysc/kernel/sc_module_registry.cpp
g++ -I. -I. -I../../../../src/sysc/kernel -I../../../../src    -Wall -DSC_INCLUDE_FX -O3 -c -o sc_name_gen.o `test -f '../../../../src/sysc/kernel/sc_name_gen.cpp' || echo '../../../../src/sysc/kernel/'`../../../../src/sysc/kernel/sc_name_gen.cpp
g++ -I. -I. -I../../../../src/sysc/kernel -I../../../../src    -Wall -DSC_INCLUDE_FX -O3 -c -o sc_object.o `test -f '../../../../src/sysc/kernel/sc_object.cpp' || echo '../../../../src/sysc/kernel/'`../../../../src/sysc/kernel/sc_object.cpp
g++ -I. -I. -I../../../../src/sysc/kernel -I../../../../src    -Wall -DSC_INCLUDE_FX -O3 -c -o sc_object_manager.o `test -f '../../../../src/sysc/kernel/sc_object_manager.cpp' || echo '../../../../src/sysc/kernel/'`../../../../src/sysc/kernel/sc_object_manager.cpp
g++ -I. -I. -I../../../../src/sysc/kernel -I../../../../src    -Wall -DSC_INCLUDE_FX -O3 -c -o sc_process_base.o `test -f '../../../../src/sysc/kernel/sc_process_base.cpp' || echo '../../../../src/sysc/kernel/'`../../../../src/sysc/kernel/sc_process_base.cpp
g++ -I. -I. -I../../../../src/sysc/kernel -I../../../../src    -Wall -DSC_INCLUDE_FX -O3 -c -o sc_process_int.o `test -f '../../../../src/sysc/kernel/sc_process_int.cpp' || echo '../../../../src/sysc/kernel/'`../../../../src/sysc/kernel/sc_process_int.cpp
../../../../src/sysc/kernel/sc_process_int.cpp: In member function ‘virtual void sc_core::sc_thread_process::prepare_for_simulation()’:
../../../../src/sysc/kernel/sc_process_int.cpp:441: error: ‘sc_thread_cor_fn’ was not declared in this scope
../../../../src/sysc/kernel/sc_process_int.cpp: In member function ‘virtual void sc_core::sc_cthread_process::prepare_for_simulation()’:
../../../../src/sysc/kernel/sc_process_int.cpp:630: error: ‘sc_cthread_cor_fn’ was not declared in this scope
make[3]: *** [sc_process_int.o] Error 1
make[3]: Leaving directory `/home/abdalmalik/programs/systemc-2.1.v1/objdir/src/sysc/kernel'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/abdalmalik/programs/systemc-2.1.v1/objdir/src/sysc'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/abdalmalik/programs/systemc-2.1.v1/objdir/src'
make: *** [all-recursive] Error 1
abdalmalik@ubuntu:~/programs/systemc-2.1.v1/objdir$ cd ..
abdalmalik@ubuntu:~/programs/systemc-2.1.v1$ cd ..
abdalmalik@ubuntu:~/programs$ export CXX
abdalmalik@ubuntu:~/programs$ export CC
abdalmalik@ubuntu:~/programs$ cd systemc-2.1.v1/
abdalmalik@ubuntu:~/programs/systemc-2.1.v1$ cd objdir/
abdalmalik@ubuntu:~/programs/systemc-2.1.v1/objdir$ ../configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/abdalmalik/programs/systemc-2.1.v1/config/missing: Unknown `--run' option
Try `/home/abdalmalik/programs/systemc-2.1.v1/config/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/sysc/Makefile
config.status: creating src/sysc/communication/Makefile
config.status: creating src/sysc/datatypes/Makefile
config.status: creating src/sysc/datatypes/bit/Makefile
config.status: creating src/sysc/datatypes/fx/Makefile
config.status: creating src/sysc/datatypes/int/Makefile
config.status: creating src/sysc/datatypes/misc/Makefile
config.status: creating src/sysc/kernel/Makefile
config.status: creating src/sysc/tracing/Makefile
config.status: creating src/sysc/qt/Makefile
config.status: creating src/sysc/utils/Makefile
config.status: creating src/sysc/packages/Makefile
config.status: creating src/sysc/packages/boost/Makefile
config.status: creating src/sysc/packages/boost/bind/Makefile
config.status: creating src/sysc/packages/boost/config/Makefile
config.status: creating src/sysc/packages/boost/config/compiler/Makefile
config.status: creating src/sysc/packages/boost/config/platform/Makefile
config.status: creating src/sysc/packages/boost/config/stdlib/Makefile
config.status: creating src/sysc/packages/boost/detail/Makefile
config.status: creating src/sysc/packages/boost/utility/Makefile
config.status: creating examples/Makefile
config.status: creating examples/sysc/Makefile
config.status: creating examples/sysc/fir/Makefile
config.status: creating examples/sysc/fft/Makefile
config.status: creating examples/sysc/fft/fft_flpt/Makefile
config.status: creating examples/sysc/fft/fft_fxpt/Makefile
config.status: creating examples/sysc/pipe/Makefile
config.status: creating examples/sysc/pkt_switch/Makefile
config.status: creating examples/sysc/rsa/Makefile
config.status: creating examples/sysc/simple_bus/Makefile
config.status: creating examples/sysc/simple_fifo/Makefile
config.status: creating examples/sysc/simple_perf/Makefile
config.status: creating examples/sysc/2.1/Makefile
config.status: creating examples/sysc/2.1/dpipe/Makefile
config.status: creating examples/sysc/2.1/forkjoin/Makefile
config.status: creating examples/sysc/2.1/reset_signal_is/Makefile
config.status: creating examples/sysc/2.1/sc_export/Makefile
config.status: creating examples/sysc/2.1/sc_report/Makefile
config.status: creating examples/sysc/2.1/scx_barrier/Makefile
config.status: creating examples/sysc/2.1/scx_mutex_w_policy/Makefile
config.status: creating examples/sysc/2.1/specialized_signals/Makefile
config.status: executing depfiles commands
Please if anyone can help me, it would be so nice
Thanks for all
[/SIZE]

---

