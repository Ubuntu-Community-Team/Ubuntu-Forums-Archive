---
title: "linking against gtest library cannot find pthread symbols"
date: 2013-10-13
forum: Installation &amp; Upgrades
---

### Post by martin-goodwin-e on 2013-10-13
Hi Gurus of the cloud

I have got a problem since upgrading to 13.10 (Kubuntu, but in this case i think that is irrelevant)

My project no longer builds the test suite.

We build gtest locally, to ensure that changes only appear when we want them, and to allow different distributions to build. Gtest is autoconfigure, and I notice in the output that it says:
```
checking for the pthreads library -lpthreads... no
checking whether pthreads work without any flags... no
checking whether pthreads work with -Kthread... no
checking whether pthreads work with -kthread... no
checking for the pthreads library -llthread... no
checking whether pthreads work with -pthread... yes
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE
checking if more special flags are required for pthreads... no
checking whether to check for GCC pthread/shared inconsistencies... yes
checking whether -pthread is sufficient with -shared... yes

```
and subsequently has "-pthread -DGTEST_HAS_PTHREAD=1" in the build lines.

The resulting gtest.o does however not have the symbols for pthread defined:
```
# nm libgtest.o[INDENT=2]w pthread_cancel
U pthread_getspecific
U pthread_key_create
U pthread_key_delete
U pthread_mutex_destroy@@GLIBC_2.2.5
U pthread_mutex_init@@GLIBC_2.2.5
U pthread_mutex_lock@@GLIBC_2.2.5
U pthread_mutex_unlock@@GLIBC_2.2.5
U pthread_self@@GLIBC_2.2.5
U pthread_setspecific[/INDENT]

```  
When I link I use
```
"gcc" gwr_gtest.o   -L../lib -Wl,-rpath=../lib -lgwr_gtest -lgtest -lgmock -lpthread -lstdc++ -o gtest

```
thus trying to add pthread directly, but this does not seem to satisfy the linker, which complains that 
```
../lib/libgtest.so: undefined reference to `pthread_key_create'

```Everything worked fine in 13.04. I have configured the system to use gcc-4.7 (like 13.04) rather than the default gcc-4.8

---

### Post by martin-goodwin-e on 2013-10-13
OK - there is a bug [https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/1228201](https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/1228201) with a workaround: add -Wl,--no-as-needed to the linker line.

---

