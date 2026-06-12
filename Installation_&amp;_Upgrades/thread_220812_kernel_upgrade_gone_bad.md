---
title: "kernel upgrade gone bad"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by bassMonkey on 2006-07-22
Hi, I upgraded my kernel yesterday, unfortunately there wasn't enough room on /boot to fit the new (2.6.15-26) kernel so it didn't finish nicely (don't know if it's related to my current problem). I removed the new (half installed) one and a few older ones. Then reinstalled the new one + kernel headers + restricted modules, rebooted and loaded the new one, removed all the older kernels, headers and restricted modules. Then tried to make acer_acpi (I need it for wlan). Here's the result:

```
fgrano@fgrano-laptop:~/Downloads/Firefox/acer_acpi-0.3$ make
awk: cannot open /lib/modules/2.6.15-26-k7/build/include/linux/version.h (No such file or directory)
gcc -I/lib/modules/`uname -r`/build/include -c -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fomit-frame-pointer -fno-strict-aliasing -fno-common -pipe -DMODVERSIONS -DMODULE -D__KERNEL__ -o acer_acpi.o acer_acpi.c
In file included from /usr/include/linux/sched.h:16,
                 from /usr/include/linux/module.h:9,
                 from acer_acpi.c:41:
/usr/include/linux/signal.h:2:2: warning: #warning "You should include <signal.h>. This time I will do it for you."
In file included from /usr/include/linux/resource.h:4,
                 from /usr/include/linux/sched.h:79,
                 from /usr/include/linux/module.h:9,
                 from acer_acpi.c:41:
/usr/include/linux/time.h:9: error: redefinition of ‘struct timespec’
/usr/include/linux/time.h:15: error: redefinition of ‘struct timeval’
/usr/include/linux/time.h:20: error: redefinition of ‘struct timezone’
/usr/include/linux/time.h:47: error: redefinition of ‘struct itimerval’
In file included from acer_acpi.c:41:
/usr/include/linux/module.h:41: error: field ‘attr’ has incomplete type
/usr/include/linux/module.h:49: error: field ‘kobj’ has incomplete type
In file included from acer_acpi.c:44:
/usr/include/linux/proc_fs.h:4:24: error: linux/slab.h: No such file or directory
In file included from acer_acpi.c:44:
/usr/include/linux/proc_fs.h:245: error: field ‘vfs_inode’ has incomplete type
/usr/include/linux/proc_fs.h: In function ‘PROC_I’:
/usr/include/linux/proc_fs.h:250: error: syntax error before ‘struct’
acer_acpi.c:45:25: error: linux/delay.h: No such file or directory
In file included from /usr/include/linux/suspend.h:7,
                 from acer_acpi.c:46:
/usr/include/linux/swap.h:5:26: error: linux/mmzone.h: No such file or directoryIn file included from /usr/include/linux/suspend.h:7,
                 from acer_acpi.c:46:
/usr/include/linux/swap.h: In function ‘current_is_kswapd’:
/usr/include/linux/swap.h:16: error: ‘current’ undeclared (first use in this function)
/usr/include/linux/swap.h:16: error: (Each undeclared identifier is reported only once
/usr/include/linux/swap.h:16: error: for each function it appears in.)
/usr/include/linux/swap.h:16: error: ‘PF_KSWAPD’ undeclared (first use in this function)
/usr/include/linux/swap.h: At top level:
/usr/include/linux/swap.h:44: error: variable-size type declared outside of any function
In file included from acer_acpi.c:46:
/usr/include/linux/suspend.h:10:22: error: linux/pm.h: No such file or directoryacer_acpi.c:47:25: error: asm/uaccess.h: No such file or directory
acer_acpi.c:49:31: error: acpi/acpi_drivers.h: No such file or directory
acer_acpi.c:76: error: syntax error before ‘u32’
acer_acpi.c:76: warning: no semicolon at end of struct or union
acer_acpi.c:77: warning: type defaults to ‘int’ in declaration of ‘ebx’
acer_acpi.c:77: warning: data definition has no type or storage class
acer_acpi.c:78: error: syntax error before ‘ecx’
acer_acpi.c:78: warning: type defaults to ‘int’ in declaration of ‘ecx’
acer_acpi.c:78: warning: data definition has no type or storage class
acer_acpi.c:79: error: syntax error before ‘edx’
acer_acpi.c:79: warning: type defaults to ‘int’ in declaration of ‘edx’
acer_acpi.c:79: warning: data definition has no type or storage class
acer_acpi.c:80: warning: type defaults to ‘int’ in declaration of ‘WMAB_args’
acer_acpi.c:80: warning: data definition has no type or storage class
acer_acpi.c:91: error: syntax error before ‘acpi_handle’
acer_acpi.c:91: warning: no semicolon at end of struct or union
acer_acpi.c: In function ‘is_valid_acpi_path’:
acer_acpi.c:99: error: ‘acpi_handle’ undeclared (first use in this function)
acer_acpi.c:99: error: syntax error before ‘handle’
acer_acpi.c:100: error: ‘acpi_status’ undeclared (first use in this function)
acer_acpi.c:102: error: ‘status’ undeclared (first use in this function)
acer_acpi.c:102: warning: implicit declaration of function ‘acpi_get_handle’
acer_acpi.c:102: error: ‘handle’ undeclared (first use in this function)
acer_acpi.c:103: warning: implicit declaration of function ‘ACPI_FAILURE’
acer_acpi.c: At top level:
acer_acpi.c:107: error: syntax error before ‘WMAB_execute’
acer_acpi.c:107: error: syntax error before ‘*’ token
acer_acpi.c:108: warning: return type defaults to ‘int’
acer_acpi.c:108: warning: function declaration isn’t a prototype
acer_acpi.c: In function ‘WMAB_execute’:
acer_acpi.c:109: error: storage size of ‘input’ isn’t known
acer_acpi.c:110: error: array type has incomplete element type
acer_acpi.c:112: error: ‘acpi_status’ undeclared (first use in this function)
acer_acpi.c:112: error: syntax error before ‘status’
acer_acpi.c:116: error: ‘ACPI_TYPE_INTEGER’ undeclared (first use in this function)
acer_acpi.c:121: error: ‘ACPI_TYPE_BUFFER’ undeclared (first use in this function)
acer_acpi.c:123: error: ‘u8’ undeclared (first use in this function)
acer_acpi.c:123: error: syntax error before ‘)’ token
acer_acpi.c:125: error: ‘status’ undeclared (first use in this function)
acer_acpi.c:125: warning: implicit declaration of function ‘acpi_evaluate_object’
acer_acpi.c:125: error: ‘result’ undeclared (first use in this function)
acer_acpi.c:110: warning: unused variable ‘params’
acer_acpi.c:109: warning: unused variable ‘input’
acer_acpi.c: At top level:
acer_acpi.c:158: warning: ‘struct file’ declared inside parameter list
acer_acpi.c:158: error: syntax error before ‘*’ token
acer_acpi.c:159: warning: function declaration isn’t a prototype
acer_acpi.c: In function ‘dispatch_write’:
acer_acpi.c:168: warning: implicit declaration of function ‘kmalloc’
acer_acpi.c:168: error: ‘count’ undeclared (first use in this function)
acer_acpi.c:168: error: ‘GFP_KERNEL’ undeclared (first use in this function)
acer_acpi.c:168: warning: assignment makes pointer from integer without a cast
acer_acpi.c:169: warning: implicit declaration of function ‘copy_from_user’
acer_acpi.c:169: error: ‘buffer’ undeclared (first use in this function)
acer_acpi.c:173: error: ‘item’ undeclared (first use in this function)
acer_acpi.c:175: warning: implicit declaration of function ‘kfree’
acer_acpi.c: In function ‘read_mled’:
acer_acpi.c:185: warning: implicit declaration of function ‘sprintf’
acer_acpi.c:185: warning: incompatible implicit declaration of built-in function ‘sprintf’
acer_acpi.c: In function ‘write_mled’:
acer_acpi.c:193: error: syntax error before ‘args’
acer_acpi.c:195: warning: implicit declaration of function ‘sscanf’
acer_acpi.c:195: warning: incompatible implicit declaration of built-in function ‘sscanf’
acer_acpi.c:197: warning: implicit declaration of function ‘memset’
acer_acpi.c:197: warning: incompatible implicit declaration of built-in function ‘memset’
acer_acpi.c:197: error: ‘args’ undeclared (first use in this function)
acer_acpi.c: In function ‘read_bt’:
acer_acpi.c:213: warning: incompatible implicit declaration of built-in function ‘sprintf’
acer_acpi.c: In function ‘write_bt’:
acer_acpi.c:221: error: syntax error before ‘args’
acer_acpi.c:223: warning: incompatible implicit declaration of built-in function ‘sscanf’
acer_acpi.c:225: warning: incompatible implicit declaration of built-in function ‘memset’
acer_acpi.c:225: error: ‘args’ undeclared (first use in this function)
acer_acpi.c: In function ‘read_wlan’:
acer_acpi.c:241: warning: incompatible implicit declaration of built-in function ‘sprintf’
acer_acpi.c: In function ‘write_wlan’:
acer_acpi.c:249: error: syntax error before ‘args’
acer_acpi.c:251: warning: incompatible implicit declaration of built-in function ‘sscanf’
acer_acpi.c:253: warning: incompatible implicit declaration of built-in function ‘memset’
acer_acpi.c:253: error: ‘args’ undeclared (first use in this function)
acer_acpi.c:257: error: ‘KERN_INFO’ undeclared (first use in this function)
acer_acpi.c:257: error: syntax error before string constant
acer_acpi.c: In function ‘read_version’:
acer_acpi.c:267: warning: incompatible implicit declaration of built-in function ‘sprintf’
acer_acpi.c: At top level:
acer_acpi.c:281: warning: type defaults to ‘int’ in declaration of ‘acpi_status’acer_acpi.c:281: error: syntax error before ‘add_proc_entries’
acer_acpi.c:286: error: syntax error before ‘for’
acer_acpi.c:301: warning: type defaults to ‘int’ in declaration of ‘acpi_status’acer_acpi.c:301: error: syntax error before ‘remove_proc_entries’
acer_acpi.c:314: error: syntax error before ‘handle’
acer_acpi.c:315: warning: function declaration isn’t a prototype
acer_acpi.c: In function ‘acer_acerkeys_notify’:
acer_acpi.c:316: error: ‘data’ undeclared (first use in this function)
acer_acpi.c:320: error: ‘KERN_ERR’ undeclared (first use in this function)
acer_acpi.c:320: error: syntax error before string constant
acer_acpi.c: In function ‘acpi_acerkeys_add’:
acer_acpi.c:329: error: syntax error before ‘status’
acer_acpi.c:334: error: invalid application of ‘sizeof’ to incomplete type ‘struct acer_hotk’
acer_acpi.c:334: error: ‘GFP_KERNEL’ undeclared (first use in this function)
acer_acpi.c:337: warning: incompatible implicit declaration of built-in function ‘memset’
acer_acpi.c:337: error: invalid application of ‘sizeof’ to incomplete type ‘struct acer_hotk’
acer_acpi.c:338: error: dereferencing pointer to incomplete type
acer_acpi.c:338: error: dereferencing pointer to incomplete type
acer_acpi.c:339: warning: implicit declaration of function ‘strcpy’
acer_acpi.c:339: warning: incompatible implicit declaration of built-in function ‘strcpy’
acer_acpi.c:339: warning: implicit declaration of function ‘acpi_device_name’
acer_acpi.c:339: warning: passing argument 1 of ‘strcpy’ makes pointer from integer without a cast
acer_acpi.c:340: warning: implicit declaration of function ‘acpi_device_class’
acer_acpi.c:340: warning: passing argument 1 of ‘strcpy’ makes pointer from integer without a cast
acer_acpi.c:341: warning: implicit declaration of function ‘acpi_driver_data’
acer_acpi.c:341: error: invalid lvalue in assignment
acer_acpi.c:342: error: dereferencing pointer to incomplete type
acer_acpi.c:344: error: ‘status’ undeclared (first use in this function)
acer_acpi.c:344: warning: implicit declaration of function ‘acpi_install_notify_handler’
acer_acpi.c:344: error: dereferencing pointer to incomplete type
acer_acpi.c:344: error: ‘ACPI_SYSTEM_NOTIFY’ undeclared (first use in this function)
acer_acpi.c:347: error: ‘KERN_ERR’ undeclared (first use in this function)
acer_acpi.c:347: error: syntax error before string constant
acer_acpi.c: In function ‘acpi_acerkeys_remove’:
acer_acpi.c:354: error: syntax error before ‘status’
acer_acpi.c:361: error: ‘status’ undeclared (first use in this function)
acer_acpi.c:361: warning: implicit declaration of function ‘acpi_remove_notify_handler’
acer_acpi.c:361: error: dereferencing pointer to incomplete type
acer_acpi.c:361: error: ‘ACPI_SYSTEM_NOTIFY’ undeclared (first use in this function)
acer_acpi.c:364: error: ‘KERN_ERR’ undeclared (first use in this function)
acer_acpi.c:364: error: syntax error before string constant
acer_acpi.c: At top level:
acer_acpi.c:370: error: variable ‘acpi_acerkeys’ has initializer but incomplete type
acer_acpi.c:371: error: unknown field ‘name’ specified in initializer
acer_acpi.c:371: warning: excess elements in struct initializer
acer_acpi.c:371: warning: (near initialization for ‘acpi_acerkeys’)
acer_acpi.c:372: error: unknown field ‘class’ specified in initializer
acer_acpi.c:372: warning: excess elements in struct initializer
acer_acpi.c:372: warning: (near initialization for ‘acpi_acerkeys’)
acer_acpi.c:373: error: unknown field ‘ids’ specified in initializer
acer_acpi.c:373: warning: excess elements in struct initializer
acer_acpi.c:373: warning: (near initialization for ‘acpi_acerkeys’)
acer_acpi.c:374: error: unknown field ‘ops’ specified in initializer
acer_acpi.c:374: error: extra brace group at end of initializer
acer_acpi.c:374: error: (near initialization for ‘acpi_acerkeys’)
acer_acpi.c:377: warning: excess elements in struct initializer
acer_acpi.c:377: warning: (near initialization for ‘acpi_acerkeys’)
acer_acpi.c: In function ‘acer_acpi_init’:
acer_acpi.c:383: error: syntax error before ‘args’
acer_acpi.c:386: error: ‘KERN_INFO’ undeclared (first use in this function)
acer_acpi.c:386: error: syntax error before string constant
acer_acpi.c:387: error: ‘acpi_disabled’ undeclared (first use in this function)
acer_acpi.c:388: error: ‘KERN_ERR’ undeclared (first use in this function)
acer_acpi.c:388: error: syntax error before string constant
acer_acpi.c:396: warning: incompatible implicit declaration of built-in function ‘memset’
acer_acpi.c:396: error: ‘args’ undeclared (first use in this function)
acer_acpi.c:399: error: ‘status’ undeclared (first use in this function)
acer_acpi.c:401: error: syntax error before string constant
acer_acpi.c:405: error: ‘acpi_root_dir’ undeclared (first use in this function)
acer_acpi.c:407: error: ‘AE_ERROR’ undeclared (first use in this function)
acer_acpi.c:410: warning: implicit declaration of function ‘add_proc_entries’
acer_acpi.c:415: warning: implicit declaration of function ‘ACPI_SUCCESS’
acer_acpi.c:416: warning: implicit declaration of function ‘acpi_bus_register_driver’
acer_acpi.c:418: warning: implicit declaration of function ‘remove_proc_entries’acer_acpi.c:421: error: syntax error before string constant
acer_acpi.c:424: error: syntax error before string constant
acer_acpi.c: In function ‘acer_acpi_exit’:
acer_acpi.c:432: warning: implicit declaration of function ‘acpi_bus_unregister_driver’
acer_acpi.c:437: error: ‘KERN_INFO’ undeclared (first use in this function)
acer_acpi.c:437: error: syntax error before string constant
make: *** [acer_acpi.o] Error 1
fgrano@fgrano-laptop:~/Downloads/Firefox/acer_acpi-0.3$ 
```

It did work on 2.6.15-25 so i installed that again but it results in the same thing now. ](*,) 
I've made a mess, please help me!

---

